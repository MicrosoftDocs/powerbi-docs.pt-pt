---
title: Utilizar o SAP HANA no Power BI Desktop
description: Utilizar o SAP HANA no Power BI Desktop
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
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: 9cbeb0b2504612a9eb32fdad1d95fd90b57e07d9
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2017
---
# <a name="use-sap-hana-in-power-bi-desktop"></a>Utilizar o SAP HANA no Power BI Desktop
Com o Power BI Desktop, agora pode aceder a bases de dados do **SAP HANA**. Para usar o **SAP HANA**, o controlador ODBC do SAP HANA deve ser instalado no computador de cliente local para que a ligação de dados do **SAP HANA** ao Power BI Desktop funcione corretamente. Pode transferir o controlador ODBC do SAP HANA a partir do [Centro de Transferências de Software SAP](https://support.sap.com/swdc). A partir daí, procure os SAP HANA CLIENT para computadores Windows. Visto que o **Centro de Transferências de Software SAP** muda a estrutura com frequência, não estão disponíveis orientações mais específicas para navegar no site.

Para ligar-se a uma base de dados **SAP HANA**, selecione **Obter Dados > Base de Dados > Base de Dados do SAP HANA**, como apresentado na imagem a seguir.

![](media/desktop-sap-hana/sap-hana-1.png)

Ao ligar-se a uma base de dados do SAP HANA, especifique o nome do servidor e a porta no formato *servidor:porta* - a imagem a seguir apresenta um exemplo com um servidor chamado *ServerXYZ* e a porta *30015*.

![](media/desktop-sap-hana/sap-hana-2.png)

Nesta versão, há suporte para o **SAP HANA** no modo [DirectQuery](desktop-use-directquery.md) no Power BI Desktop e no serviço Power BI, e é possível publicar e carregar relatórios que usam o **SAP HANA** no modo DirectQuery para o serviço Power BI. Também pode publicar e carregar relatórios no serviço Power BI quando não estiver a utilizar o **SAP HANA** no modo DirectQuery.

### <a name="supported-features-for-sap-hana"></a>Funcionalidades suportadas para SAP HANA
Esta versão contém vários recursos para o **SAP HANA**, como mostrado na lista seguinte:

* O conector do Power BI para o **SAP HANA** usa o controlador ODBC do SAP, para fornecer a melhor experiência de utilização
* O **SAP HANA** suporta as opções de Importação e do DirectQuery
* O Power BI suporta modelos de informação HANA (como as vistas Análise e Cálculo) e tem uma navegação otimizada
* Com o **SAP HANA**, também pode usar o recurso direto do SQL para ligar-se às Tabelas de Linhas e Colunas
* Inclui Navegação Otimizada para modelos HANA
* O Power BI suporta parâmetros de Variáveis e Entrada do **SAP HANA**

### <a name="installing-the-sap-hana-odbc-driver"></a>Instalar o controlador ODBC do SAP HANA
### <a name="limitations-of-sap-hana"></a>Limitações do SAP HANA
Também há algumas limitações com a utilização do **SAP HANA**, conforme apresentado abaixo:

* As cadeias NVARCHAR são truncadas para o comprimento máximo de 4000 carateres Unicode
* SMALLDECIMAL não é suportado
* VARBINARY não é suportado
* As Datas Válidas estão entre 30/12/1899 e 31/12/9999
