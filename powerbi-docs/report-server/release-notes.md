---
title: "Notas de versão do Power BI Report Server"
description: "Este tópico descreve as limitações e os problemas relacionados com o Power BI Report Server."
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.date: 11/01/2017
ms.author: maghan
ms.openlocfilehash: aa0f8870396980edfdb85739e0459c365d1e2163
ms.sourcegitcommit: eec6b47970bf69ed30638d1a20051f961ba792f2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/06/2018
---
# <a name="power-bi-report-server-release-notes"></a>Notas de versão do Power BI Report Server
Este tópico descreve as limitações e os problemas relacionados com o Power BI Report Server.

Para transferir o Power BI Report Server e o Power BI Desktop otimizado para o Power BI Report Server, aceda a [Relatórios no local com o Power BI Report Server](https://powerbi.microsoft.com/report-server/).

## <a name="october-2017"></a>Outubro de 2017
* Suporte para dados importados nos relatórios do Power BI
* Capacidade para ver os livros do Excel no portal Web. Isto é feito ao configurar o Office Online Server.
* Suporte dos novos elementos visuais de tabelas e matrizes do Power BI.
* Suporte da API REST

## <a name="june-2017"></a>Junho de 2017
* Não existem novos itens para junho de 2017.

## <a name="may-2017"></a>Maio de 2017
* Os relatórios do Power BI têm de ser criados com o Power BI Desktop otimizado para o Power BI Report Server para funcionarem com o Power BI Report Server. Pode transferir o Power BI Desktop a partir da ligação de transferência na parte superior desta página.
* Os relatórios do Power BI só suportam ligações em direto ao Analysis Services (tabulares ou multidimensionais).
* Não existe suporte para elementos visuais R.

**Impacto do problema e no cliente:** se tiver o SQL Server Reporting Services e o Power BI Report Server no mesmo computador e desinstalar um deles, já não poderá ligar ao servidor de relatórios restante com o Gestor de Configuração do Servidor de Relatórios.

**Solução** Para contornar este problema, tem de efetuar as seguintes operações após a desinstalação de um dos servidores.

1. Inicie uma linha de comandos no modo de Administrador.
2. Aceda ao diretório onde está instalado o servidor de relatórios restante.
   
    *Localização predefinida do Power BI Report Server: C:\Programas\Microsoft Power BI Report Server*
   
    *Localização predefinida do SQL Server Reporting Services: C:\Programas\Microsoft SQL Server Reporting Services*
3. Em seguida, avance para a pasta seguinte. Será *SSRS* ou *PBIRS*, consoante a restante.
4. Aceda à pasta WMI.
5. Execute o seguinte comando:
   
    ```
    regsvr32 /i ReportingServicesWMIProvider.dll
    ```
   
    Pode ignorar o erro seguinte, se o vir.
   
    ```
    The module "ReportingServicesWMIProvider.dll" was loaded but the entry-point DLLInstall was not found. Make sure that "ReportingServicesWMIProvider.dll" is a valid DLL or OCX file and then try again.
    ```

## <a name="next-steps"></a>Próximos passos
[Novidades no Power BI Report Server](whats-new.md)  
[Manual do utilizador](user-handbook-overview.md)  
[Manual do administrador](admin-handbook-overview.md)  
[Início rápido: instalar o Power BI Report Server](quickstart-install-report-server.md)  
[Instalar o Report Builder](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Transferir o SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

