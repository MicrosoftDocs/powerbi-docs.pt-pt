---
title: Utilizar o SAP HANA no Power BI Desktop
description: Utilizar o SAP HANA no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 9b205a0ae9b58acf054a9afe43196e77ee404c84
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83289126"
---
# <a name="connect-to-sap-hana-databases-in-power-bi-desktop"></a>Ligar às bases de dados SAP HANA no Power BI Desktop

Com o Power BI Desktop, agora pode aceder a bases de dados do *SAP HANA*. Para utilizar o SAP HANA, tem de ter o controlador ODBC do SAP HANA instalado no computador de cliente local para que a ligação de dados do SAP HANA ao Power BI Desktop funcione corretamente. Pode transferir as ferramentas de Cliente SAP HANA nas [Ferramentas de Desenvolvimento SAP](https://tools.hana.ondemand.com/#hanatools), que contêm o controlador ODBC necessário. Em alternativa, pode obtê-las no [Centro de Transferências de Software SAP](https://support.sap.com/en/my-support/software-downloads.html). No portal de Software, procure os *SAP HANA CLIENT* para computadores Windows. Visto que o Centro de Transferências de Software SAP muda a sua estrutura com frequência, não estão disponíveis orientações mais específicas para navegar no site.

Para ligar a uma base de dados SAP HANA, selecione **Obter Dados**, selecione **Base de dados** > **Base de Dados do SAP HANA** e, em seguida, selecione **Ligar**:

![Base de dados SAP HANA, caixa de diálogo Obter Dados, Power BI Desktop](media/desktop-sap-hana/sap-hana-1.png)

Ao ligar a uma base de dados SAP HANA, especifique o nome do servidor. Em seguida, no menu pendente e na caixa de entrada, especifique a porta.

Nesta, versão o SAP HANA no modo [DirectQuery](desktop-directquery-sap-hana.md) é suportado no Power BI Desktop e no serviço Power BI. Pode publicar e carregar relatórios que utilizam SAP HANA no modo DirectQuery para o serviço Power BI. Também pode publicar e carregar relatórios no serviço Power BI quando não estiver a utilizar o SAP HANA no modo DirectQuery.

## <a name="supported-features-for-sap-hana"></a>Funcionalidades suportadas para SAP HANA

Esta versão contém vários recursos para o SAP HANA, como mostrado na lista seguinte:

* O conector do Power BI para o SAP HANA utiliza o controlador ODBC do SAP, para fornecer a melhor experiência ao utilizador.

* O SAP HANA suporta as opções de Importação e do DirectQuery.

* O Power BI suporta modelos de informação HANA (como as Vistas de Análise e de Cálculo) e tem uma navegação otimizada.

* Com o SAP HANA, também pode utilizar o recurso direto do SQL para ligar-se às Tabelas de Linhas e Colunas.

* O Power BI inclui Navegação Otimizada para Modelos HANA.

* O Power BI suporta parâmetros de Variáveis e Entrada do SAP HANA.

* O Power BI suporta Vistas de Cálculo baseadas em contentores de HDI.

  * O suporte de Vistas de Cálculo baseadas em contentores de HDI está em pré-visualização pública na versão de agosto de 2019 do Power BI Desktop. Para aceder às Vistas de Cálculo baseadas em contentores de HDI no Power BI, certifique-se de que os utilizadores da base de dados HANA que utiliza com o Power BI têm permissão para aceder ao contentor de runtime de HDI que armazena as vistas a que pretende aceder. Para conceder este acesso, crie uma Função que permita acesso ao seu contentor de HDI. Em seguida, atribua a função ao utilizador da base de dados HANA que vai utilizar com o Power BI. (Este utilizador também terá de ter permissão de leitura nas tabelas do sistema no esquema \_SYS\_BI como habitualmente.) Veja a documentação de SAP oficial para obter instruções detalhadas sobre como criar e atribuir funções de bases de dados. [Esta mensagem de blogue do SAP](https://blogs.sap.com/2018/01/24/the-easy-way-to-make-your-hdi-container-accessible-to-a-classic-database-user/) pode ser um bom ponto de partida.

  * Atualmente, existem algumas limitações para variáveis de HANA anexadas a Vistas de Cálculo baseadas em HDI. Estas limitações devem-se a erros do lado do HANA.
  
    Em primeiro lugar, não é possível aplicar uma variável de HANA a uma coluna partilhada de uma Vista de Cálculo baseada em contentores de HDI. Para corrigir esta limitação, atualize para a versão 37.02 e posterior, ou para a versão 42 e posterior do HANA 2. Em segundo lugar, os valores predefinidos de múltiplas entradas para variáveis e parâmetros não são atualmente apresentados na IU do Power BI. Um erro no SAP HANA causa esta limitação, mas a SAP ainda não anunciou uma correção.

## <a name="limitations-of-sap-hana"></a>Limitações do SAP HANA

Também há algumas limitações com a utilização do SAP HANA, conforme apresentado abaixo:

* As cadeias NVARCHAR são truncadas para o comprimento máximo de 4000 carateres Unicode.
* SMALLDECIMAL não é suportado.
* VARBINARY não é suportado.
* As Datas Válidas estão entre 30/12/1899 e 31/12/9999.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre o DirectQuery e o SAP HANA, veja os seguintes recursos:

* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)
* [Utilizar o DirectQuery no Power BI](desktop-directquery-about.md)
* [Origens de dados do Power BI](power-bi-data-sources.md)
* [Enable encryption for SAP HANA](desktop-sap-hana-encryption.md) (Ativar encriptação para o SAP HANA)
