---
title: DirectQuery para SAP HANA no Power BI
description: "Considerações ao utilizar o DirectQuery com o SAP HANA"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: 2b2e59371c96928a2b7c6b23bd393a80ecc3041a
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="directquery-and-sap-hana"></a>DirectQuery e SAP HANA
Pode ligar a origens de dados **SAP HANA** diretamente com o **DirectQuery**.

Quando utilizar o **SAP HANA**, é importante compreender alguns aspetos de como são tratadas as ligações para o mesmo, para se certificar de que:

* Os resultados são os esperados, quando a vista do SAP HANA contém medidas não aditivas (por exemplo, contagens distintas, ou médias, em vez de somas simples)
* As consultas resultantes são eficientes

É útil começar por reservar um momento para esclarecer o comportamento de uma origem relacional como o **SQL Server**, quando a consulta definida em **Obter Dados** ou **Editor de Consultas** executa uma agregação. No exemplo que se segue, uma consulta definida no **Editor de Consultas** devolve o preço médio por **ProductID**.

![](media/desktop-directquery-sap-hana/directquery-sap-hana_01.png)

Se os dados estiverem a ser importados para o Power BI (em vez de utilizar o DirectQuery), resultaria o seguinte:

* Os dados são importados ao nível de agregação definido pela consulta criada no **Editor de Consultas**. Por exemplo, preço médio por produto. Isto resulta numa tabela com as duas colunas *ProductID* e *AveragePrice* que podem ser utilizadas em elementos visuais.
* Num elemento visual, qualquer agregação subsequente (tal como *Soma*, *Média*, *Mín.*, entre outras) é executada através desses dados importados.  Por exemplo, incluir *AveragePrice* num elemento visual irá utilizar o agregado da *Soma* por predefinição e irá devolver a soma de *AveragePrice* para cada  *ProductID* – que, neste caso, seria 13,67. O mesmo se aplica a qualquer função de agregação alternativa (tal como *Mín.*, *Média*, etc.) utilizada no elemento visual. Por exemplo, a *Média* de *AveragePrice* devolve a média de 6,66, 4 e 3, o que equivale a 4,56, e *não* a média de *Preço* nos 6 registos na tabela subjacente, que equivale a 5,17.

Se o **DirectQuery** estiver a ser utilizado em vez da opção Importar, aplica-se a mesma semântica e os resultados serão exatamente os mesmos:

* Tendo em conta a mesma consulta, é lógico que são apresentados exatamente os mesmos dados para a camada de relatórios – embora os dados não sejam realmente importados.
* Num elemento visual, qualquer agregação subsequente (*Soma*, *Média*, *Mín.*, entre outras) é novamente executada nessa tabela lógica a partir da consulta. E, mais uma vez, um elemento visual que contenha a *Média* de *AveragePrice* devolve os mesmos 4,56.

Agora, vamos considerar o **SAP HANA**. O Power BI pode trabalhar com as *Vistas Analíticas* e as *Vistas de Cálculo* no SAP HANA, sendo que ambas podem conter medidas. No entanto, atualmente, a abordagem do SAP HANA segue os mesmos princípios descritos anteriormente: a consulta definida em **Obter Dados** ou **Editor de Consultas** irá determinar os dados disponíveis e, em seguida, qualquer agregação subsequente num elemento visual é feita com base nesses dados e o mesmo aplica-se a Importar e DirectQuery.

No entanto, dada a natureza do HANA, a consulta definida na caixa de diálogo **Obter Dados** inicial ou no **Editor de Consultas** é sempre uma consulta de agregação e, normalmente, irá incluir medidas onde a agregação real que será utilizada é definida pela vista do HANA.

O equivalente ao exemplo do SQL Server acima é o facto de existir uma vista do HANA que contém o **ID**, **ProductID**, **DepotID** e as medidas que incluem o **AveragePrice**, definido na vista como **Média de Preço**.

![](media/desktop-directquery-sap-hana/directquery-sap-hana_02.png)

Se, na experiência **Obter Dados**, as seleções feitas foram para **ProductID** e a medida **AveragePrice**, tal consiste em definir uma consulta na vista, pedir esses dados de agregação (no exemplo acima, é utilizado pseudo-SQL para simplificar, o que não corresponde à sintaxe exata de HANA SQL). Em seguida, quaisquer agregações adicionais definidas num elemento visual vão agregar ainda mais os resultados de uma consulta deste tipo. Novamente, conforme descrito acima para o **SQL Server**, isto aplica-se tanto ao cenário de Importação como de DirectQuery. Tenha em atenção que no cenário de DirectQuery, a consulta de **Obter Dados** ou **Editor de Consultas** será utilizada numa única consulta enviada para o HANA e, por conseguinte, não é um cenário onde todos os dados serão lidos, antes de continuar a agregar.

Isto dá origem às seguintes considerações importantes ao utilizar o DirectQuery em HANA:

* Tem de prestar atenção a qualquer outra agregação executada em elementos visuais sempre que a medida no HANA for não aditiva (por exemplo, não for uma *Soma*, *Mín.* ou *Máx.* simples).
* Em **Obter Dados** ou **Editor de Consultas**, apenas devem ser incluídas as colunas necessárias para obter os dados necessários, refletindo o facto de que o resultado será uma consulta, que tem de ser uma consulta razoável que possa ser enviada para o HANA. Por exemplo, se forem selecionadas dezenas de colunas, com a ideia de que poderão ser necessárias em elementos visuais subsequentes, até mesmo para o DirectQuery um elemento visual simples implica que a consulta de agregação utilizada na subseleção irá conter essas dezenas de colunas, cujo desempenho, geralmente, é muito fraco.

Vejamos um exemplo. No exemplo seguinte, a seleção de cinco colunas (CalendarQuarter, Color, LastName, ProductLine, SalesOrderNumber) na caixa de diálogo **Obter Dados**, juntamente com a medida OrderQuantity, significa que a criação posterior de um elemento visual que contenha a OrderQuantity Mín. resultará na seguinte consulta SQL para HANA. A parte sombreada é a subseleção, que contém a consulta de **Obter Dados** / **Editor de Consultas**. Se esta subseleção der um resultado com uma cardinalidade muito elevada, é provável que o desempenho do HANA resultante será fraco.

![](media/desktop-directquery-sap-hana/directquery-sap-hana_03.png)

Por este motivo, é recomendado que os itens selecionados em **Obter Dados** ou **Editor de Consultas** sejam limitados aos itens necessários, o que ainda resultará numa consulta razoável para o HANA.

### <a name="next-steps"></a>Passos seguintes
Para obter mais informações sobre o DirectQuery, consulte os seguintes recursos:

* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Origens de dados suportadas pelo DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [Gateway de dados no local](service-gateway-onprem.md)

