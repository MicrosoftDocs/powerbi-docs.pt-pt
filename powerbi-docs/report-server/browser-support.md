---
title: Suporte de browser para o Power BI Report Server
description: Saiba que versões de browser são suportadas para gerir e visualizar o Power BI Report Server e os controlos do Visualizador de Relatórios.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/21/2021
ms.openlocfilehash: 71ee66c6cd531a35a53a3263feaf94115b528114
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/22/2021
ms.locfileid: "98687494"
---
# <a name="browser-support-for-power-bi-report-server"></a>Suporte de browser para o Power BI Report Server
Saiba que versões de browser são suportadas para gerir e visualizar o Power BI Report Server e os controlos do Visualizador de Relatórios.

> [!NOTE]
> O suporte para o navegador Microsoft Edge Legacy deixará de ser a partir de 9 de março de 2021, e o suporte para o Microsoft Internet Explorer 11 irá parar a partir de 17 de agosto de 2021.

## <a name="browser-requirements-for-the-web-portal"></a>Requisitos de browser para o portal Web
Segue-se a lista atual dos browsers suportados para o portal Web.

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

* Apple Safari (+)
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple iOS**  
*iPhone e iPad com iOS 10*

* Apple Safari (+)

**Google Android**  
*Telemóveis e tablets com Android 4.4 (KitKat) ou posterior*

* Google Chrome (+)
  
  **(+)** Versão publicamente disponível mais recente

## <a name="browser-requirements-for-the-report-viewer-web-control-2015"></a>Requisitos de browser para o controlo Web do Visualizador de Relatórios (2015)
Segue-se a lista atual dos browsers suportados com o controlo Web do Visualizador de Relatórios. O visualizador de relatórios suporta a visualização de relatórios desde o portal Web.

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

* Apple Safari (+)
  
  **(+)** Versão publicamente disponível mais recente

### <a name="authentication-requirements"></a>Requisitos de autenticação
Os browsers suportam esquemas de autenticação específicos que têm de ser processados pelo servidor de relatórios para que o pedido do cliente seja efetuado com êxito. A seguinte tabela identifica os tipos de autenticação predefinidos que são suportados por cada browser executado num sistema operativo Windows.

| **Tipo de browser** | **Suporta** | **Predefinição de browser** | **Predefinição de servidor** |
| --- | --- | --- | --- |
| **Microsoft Edge** (+) |Negotiate, Kerberos, NTLM, Basic |Negotiate |Yes. As predefinições de autenticação são compatíveis com o Edge. |
| **Microsoft Internet Explorer** |Negotiate, Kerberos, NTLM, Basic |Negotiate |Yes. As predefinições de autenticação são compatíveis com o Internet Explorer. |
| **Google Chrome**(+) |Negotiate, NTLM, Basic |Negotiate |Yes. As predefinições de autenticação são compatíveis com o Chrome. |
| **Mozilla Firefox**(+) |NTLM, Basic |NTLM |Yes. As predefinições de autenticação são compatíveis com o Firefox. |
| **Apple Safari**(+) |NTLM, Basic |Básico |Yes. As predefinições de autenticação são compatíveis com o Safari. |

 **(+)** Versão publicamente disponível mais recente

### <a name="script-requirements-for-viewing-reports"></a>Requisitos de scripts para ver relatórios
Para utilizar o visualizador de relatórios, configure o seu browser para executar scripts.

Se os scripts não estiverem ativados, verá uma mensagem de erro semelhante a esta ao abrir um relatório:

```
Your browser does not support scripts or has been configured to not allow scripts to run. Click here to view this report without scripts
```

 Se optar por visualizar o relatório sem suporte de scripts, o relatório será composto em HTML sem capacidades de visualizador de relatórios, como a barra de ferramentas de relatórios e o mapa de documentos.

> [!NOTE]
> A barra de ferramentas de relatórios faz parte do componente do visualizador de HTML. Por predefinição, a barra de ferramentas aparece na parte superior de todos os relatórios que são apresentados numa janela de browser. O visualizador de relatórios fornece funcionalidades como a capacidade de procurar informações no relatório, navegar para uma página específica e ajustar o tamanho da página para fins de visualização. Para obter mais informações sobre a barra de ferramentas de relatórios no Visualizador HTML, consulte [HTML Viewer and the Report Toolbar (Visualizador HTML e a Barra de Ferramentas de Relatórios - em inglês)](/sql/reporting-services/html-viewer-and-the-report-toolbar).
> 
> 

## <a name="browser-support-for-report-viewer-web-server-controls-in-visual-studio"></a>Suporte de browser para controlos de servidor Web do Visualizador de Relatórios no Visual Studio
O controlo do servidor Web do Visualizador de Relatórios é utilizado para integrar o funcionamento de relatórios numa aplicação Web ASP.NET. Para obter mais informações sobre como obter o Controlo do Visualizador de Relatórios, consulte [Integrating Reporting Services Using Report Viewer Controls - Get Started (Integração do Reporting Services Através dos Controlos do Visualizador de Relatórios: introdução - em inglês)](/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started).

Utilize um browser que tenha o suporte para scripts ativado. Se o browser não puder executar scripts, o utilizador não poderá ver o relatório.

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)
  
  **(+)** Versão publicamente disponível mais recente

## <a name="next-steps"></a>Próximos passos
[Descrição geral para administradores](admin-handbook-overview.md)  
[Instalar o Power BI Report Server](install-report-server.md)  
[Transferir o Report Builder](https://www.microsoft.com/download/details.aspx?id=53613)  
[Transferir o SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
