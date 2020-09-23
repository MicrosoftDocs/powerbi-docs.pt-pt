---
title: Origens de dados de relatórios paginados no Power BI Report Server
description: Saiba mais sobre as origens de dados às quais os relatórios paginados (.rdl) podem estabelecer ligação no Power BI Report Server.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 06/26/2020
ms.author: maggies
ms.openlocfilehash: fcf0a286487922fcfc217b4d293aa731ad1564a6
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861228"
---
# <a name="paginated-report-data-sources--in-power-bi-report-server"></a>Origens de dados de relatórios paginados no Power BI Report Server
Os relatórios paginados do Reporting Services no Power BI Report Server suportam as mesmas origens de dados que são suportadas no SQL Server Reporting Services. Veja a lista de [Origens de dados suportadas pelo Reporting Services](/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs).

## <a name="connect-to-oracle-data-sources-with-useinstalleduiculture"></a>Ligar a origens de dados do Oracle com UseInstalledUICulture

Para ligar às origens de dados do Oracle, o Power BI Report Server utiliza o Oracle Data Provider para .NET (ODP.NET), com NLS desconhecido.

Por predefinição, o servidor de relatórios utiliza a cultura da IU do primeiro cliente para carregar o ODP.NET.  Como resultado, todas as ligações subsequentes ao Oracle a partir do servidor de relatórios estarão nessa cultura inicial da IU até ao reinício do serviço.  Esta abordagem pode causar problemas na composição de relatórios devido a incompatibilidades na formatação da cultura da IU.

Para proporcionar uma melhor experiência no Power BI Report Server, introduzimos uma definição de configuração chamada UseInstalledUICulture. Quando a definição UseInstalledUICulture está definida como verdadeira, o servidor de relatórios carrega sempre o ODP.NET na Cultura da IU do servidor em vez da cultura do primeiro cliente.
Esta definição está disponível no Power BI Report Server a partir da Versão do Serviço de março de 2020.

Para ativar a funcionalidade, modifique o ficheiro rsreportserver.config de entrada de extensão ORACLE, conforme indicado abaixo.
```xml
<Extension Name="ORACLE" Type="Microsoft.ReportingServices.DataExtensions.OracleClientConnectionWrapper,Microsoft.ReportingServices.DataExtensions">
    <Configuration>
        <UseInstalledUICulture>true</UseInstalledUICulture>
    </Configuration>
</Extension>
```

## <a name="next-steps"></a>Próximos passos
Agora que estabeleceu ligação à sua origem de dados, [crie um relatório paginado](quickstart-create-paginated-report.md).  


Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)