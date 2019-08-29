---
title: Utilizar o SAP HANA no Power BI Desktop
description: Utilizar o SAP HANA no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f40ed1b3950ace0b3cb362a22670e98c3ef83112
ms.sourcegitcommit: e62889690073626d92cc73ff5ae26c71011e012e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69985670"
---
# <a name="use-sap-hana-in-power-bi-desktop"></a>Utilizar o SAP HANA no Power BI Desktop
Com o Power BI Desktop, agora pode aceder a bases de dados do **SAP HANA**. Para usar o **SAP HANA**, o controlador ODBC do SAP HANA deve ser instalado no computador de cliente local para que a ligação de dados do **SAP HANA** ao Power BI Desktop funcione corretamente. Pode transferir o controlador ODBC do SAP HANA a partir do [Centro de Transferências de Software SAP](https://support.sap.com/swdc). A partir daí, procure os SAP HANA CLIENT para computadores Windows. Visto que o **Centro de Transferências de Software SAP** muda a estrutura com frequência, não estão disponíveis orientações mais específicas para navegar no site.

Para ligar-se a uma base de dados **SAP HANA**, selecione **Obter Dados > Base de Dados > Base de Dados do SAP HANA**, como apresentado na imagem seguinte:

![](media/desktop-sap-hana/sap-hana-1.png)

Ao ligar-se a uma base de dados do SAP HANA, especifique o nome do servidor e a porta no formato *servidor:porta* - a imagem a seguir apresenta um exemplo com um servidor chamado *ServerXYZ* e a porta *30015*.

![](media/desktop-sap-hana/sap-hana-2.png)

Nesta versão, há suporte para o **SAP HANA** no modo [DirectQuery](desktop-directquery-sap-hana.md) no Power BI Desktop e no serviço Power BI e é possível publicar e carregar relatórios que utilizam o **SAP HANA** no modo DirectQuery para o serviço Power BI. Também pode publicar e carregar relatórios no serviço Power BI quando não estiver a utilizar o **SAP HANA** no modo DirectQuery.

## <a name="supported-features-for-sap-hana"></a>Funcionalidades suportadas para SAP HANA
Esta versão contém vários recursos para o **SAP HANA**, como mostrado na lista seguinte:

* O conector do Power BI para o **SAP HANA** utiliza o controlador ODBC do SAP, para fornecer a melhor experiência ao utilizador
* O **SAP HANA** suporta as opções de Importação e do DirectQuery
* O Power BI suporta modelos de informação HANA (como as Vistas de Análise e de Cálculo) e tem uma navegação otimizada.
* Com o **SAP HANA**, também pode utilizar o recurso direto do SQL para ligar-se às Tabelas de Linhas e Colunas
* Inclui Navegação Otimizada para modelos HANA
* O Power BI suporta parâmetros de Variáveis e Entrada do **SAP HANA**
* Vistas de Cálculo baseadas em contentores de HDI
  * O suporte de Vistas de Cálculo baseadas em contentores de HDI está em pré-visualização pública na versão de agosto de 2019 do Power BI Desktop. Para aceder às Vistas de Cálculo baseadas em contentores de HDI no Power BI, certifique-se de que os utilizadores da base de dados HANA que utiliza com o Power BI têm permissão para aceder ao contentor de runtime de HDI que armazena as vistas a que pretende aceder. Para conceder este acesso, tem de criar uma Função que permita o acesso ao seu contentor de HDI e atribuir a função ao utilizador da base de dados HANA que irá utilizar com o Power BI (este utilizador também tem de ter permissão para ler a partir das tabelas do sistema no esquema de BI \_SYS\_, como é habitual). Veja a documentação de SAP oficial para obter instruções detalhadas sobre como criar e atribuir funções de bases de dados. [Esta mensagem de blogue do SAP](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fblogs.sap.com%2F2018%2F01%2F24%2Fthe-easy-way-to-make-your-hdi-container-accessible-to-a-classic-database-user%2F&data=02%7C01%7Cv-adbold%40microsoft.com%7Cf7e0a405fe334598ba0608d7096ef5b4%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636988244476739316&sdata=PuRu61GPRYp34mLuGbQk6gdbRikdgbxfqo8q1RBQtm0%3D&reserved=0) pode ser um bom ponto de partida.
  * Tenha em atenção que, atualmente, existem algumas limitações para variáveis de HANA anexadas a Vistas de Cálculo baseadas em HDI. Estas limitações devem-se a erros de HANA e serão abordadas em versões futuras do SAP HANA. Em primeiro lugar, não é possível aplicar uma variável de HANA a uma coluna partilhada de uma Vista de Cálculo baseada em contentores de HDI. Esta limitação pode ser corrigida ao atualizar para a versão 37.02 e posterior, ou a versão 42 e posterior do HANA 2. Em segundo lugar, os valores predefinidos de múltiplas entradas para variáveis e parâmetros não são atualmente apresentados na IU do Power BI. Esta situação também se deve a um erro no SAP HANA, mas a SAP ainda não anunciou uma correção.

## <a name="limitations-of-sap-hana"></a>Limitações do SAP HANA
Também há algumas limitações com a utilização do **SAP HANA**, conforme apresentado abaixo:

* As cadeias NVARCHAR são truncadas para o comprimento máximo de 4000 carateres Unicode
* SMALLDECIMAL não é suportado
* VARBINARY não é suportado
* As Datas Válidas estão entre 30/12/1899 e 31/12/9999


## <a name="next-steps"></a>Próximos passos
Para obter mais informações sobre o DirectQuery e o SAP HANA, veja os seguintes recursos:

* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)
* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Data sources supported by DirectQuery](desktop-directquery-data-sources.md) (Origens de Dados que o DirectQuery suporta)
* [Enable encryption for SAP HANA](desktop-sap-hana-encryption.md) (Ativar encriptação para o SAP HANA)


