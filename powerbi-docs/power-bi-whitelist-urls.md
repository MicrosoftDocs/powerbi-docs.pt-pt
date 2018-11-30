---
title: URLs do Power BI
description: Este artigo descreve os pontos finais que os clientes do Power BI devem conseguir alcançar.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/22/2018
ms.openlocfilehash: e62d39f13e2b171456d667ec9683acd4ebdc5516
ms.sourcegitcommit: 46f1ba3f972f6e64bce05ad0fd527b27c49aedd6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52157132"
---
# <a name="power-bi-urls"></a>URLs do Power BI

**O serviço online do Power BI**, também denominado aplicação SaaS do Power BI (Software como um Serviço), necessita de conectividade à Internet. Os clientes que utilizam o serviço online do Power BI devem conseguir ligar aos pontos finais abaixo.

Para utilizar o serviço online do Power BI, tem de ter acesso para se ligar aos pontos finais marcados como **obrigatório** nas tabelas abaixo e todos os pontos finais marcados como **obrigatório** nos sites ligados. Se a ligação para um site externo o direcionar para uma secção específica, só precisará de rever os pontos finais nessa secção.

Os pontos finais marcados como **opcional** também podem ser **adicionados à lista de permissões** para que uma funcionalidade específica funcione.

O serviço online do Power BI apenas necessita que a Porta TCP 443 esteja aberta para os pontos finais listados.

Os carateres universais (*) representam todos os níveis sob o domínio de raiz e utilizamos N/D quando as informações não estão disponíveis. A coluna **Destino(s)** é uma lista de domínios FQDN e ligações para sites externos que contêm mais informações de pontos finais.

>[!Important]
>As informações nas tabelas abaixo não representam a **cloud de Administração Pública dos Estados Unidos**, **a cloud da Alemanha** e **a cloud da China**.

## <a name="authentication"></a>Autenticação

O Power BI depende dos pontos finais obrigatórios nas secções de autenticação e identidade do Office 365. Para utilizar o Power BI, tem de conseguir ligar-se aos pontos finais no site apresentado abaixo.

| Linha | Objetivo | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** autenticação e identidade | Veja a documentação do Office 365 para o [Office Online e URLs comuns](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online)  | N/D |

## <a name="general-site-usage"></a>Utilização geral do site

Para a utilização geral do Power BI, tem de conseguir ligar-se aos pontos finais na tabela e nos sites apresentados abaixo.

| Linha | Objetivo | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** APIs de back-end | *.analysis.windows.net | TCP 443 |
| 2 | **Obrigatório:** integração do Office 365 | Veja a documentação do Office 365 para o [Office Online e URLs comuns](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N/D |
| 3 | **Obrigatório:** Portal | app.powerbi.com | TCP 443 |
| 4 | **Obrigatório:** telemetria do serviço | dc.services.visualstudio.com | TCP 443 |
| 5 | **Opcional:** mensagens informativas | dynmsg.modpim.com | TCP 443 |
| 6 | **Opcional:** inquéritos do NPS | nps.onyx.azure.net | TCP 443 |
| | | |

## <a name="administration"></a>Administração

Para efetuar funções administrativas no Power BI, tem de conseguir ligar-se aos pontos finais nos sites ligados abaixo.

| Linha | Objetivo | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** para gerir utilizadores e ver registos de auditoria | Veja a documentação do Office 365 para o [Office Online e URLs comuns](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N/D |
| | | |

## <a name="getting-data"></a>Obter dados

Para obter dados de origens de dados específicas, como o OneDrive, tem de conseguir ligar-se aos pontos finais na tabela abaixo. Poderá ser necessário o acesso a URLs e domínios de Internet adicionais para origens de dados específicas utilizadas na sua organização.

| Linha | Objetivo | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** AppSource (aplicações internas ou externas no Power BI) | appsource.microsoft.com </br> *.s-microsoft.com  | TCP 443 |
| 2 | **Opcional:** iniciar sessão e obter dados de pacotes de conteúdos | Depende dos pacotes de conteúdos utilizados | Depende dos pacotes de conteúdos utilizados |
| 3 | **Opcional:** importar ficheiros do OneDrive pessoal | Veja o site [Required URLs and ports for OneDrive](https://docs.microsoft.com/onedrive/required-urls-and-ports) (URLs e portas obrigatórios para o OneDrive) | N/D |
| 4 | **Opcional:** tutorial em vídeo Power BI in 60-Seconds (O Power BI em 60 Segundos) | *.doubleclick.net </br> *.ggpht.com </br> *.google.com </br> *.googlevideo.com </br> *.youtube.com </br> *.ytimg.com </br> fonts.gstatic.com | TCP 443 |
| 5 | **Opcional:** origens de dados de transmissão em fluxo do PubNub | Veja a [documentação do PubNub](https://support.pubnub.com/support/solutions/articles/14000043522) | N/D |
| | | |

## <a name="dashboard-and-report-integration"></a>Integração de dashboards e relatórios

O Power BI depende de determinados pontos finais para suportar os seus dashboards e relatórios. Tem de conseguir ligar-se aos pontos finais na tabela e nos sites ligados abaixo.

| Linha | Objetivo | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** integração do Excel | Veja a documentação do Office 365 para o [Office Online e URLs comuns](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N/D |
| | | |

## <a name="custom-visuals"></a>Elementos visuais personalizados

O Power BI depende de determinados pontos finais para conseguir ver e aceder aos elementos visuais personalizados. Tem de conseguir ligar-se aos pontos finais na tabela e nos sites ligados abaixo.

| Linha | Objetivo | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** importar um elemento visual personalizado da interface do Marketplace ou de um ficheiro | *.azureedge.net </br> *.blob.core.windows.net </br> store.office.com | TCP 443 |
| 2 | **Opcional:** Mapas Bing | bing.com </br> platform.bing.com </br> *.dynamic.tiles.virtualearth.net </br> *.virtualearth.net | TCP 443 |
| 3 | **Opcional:** PowerApps | Veja a [secção Serviços necessários](https://docs.microsoft.com/powerapps/maker/canvas-apps/limits-and-config#required-services) no site de requisitos de sistema do PowerApps | N/D |
| 4 | **Opcional:** Visio | Veja a documentação do Office 365 para o [Office Online e URLs comuns](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online), bem como para o [SharePoint Online e o OneDrive para Empresas](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business) | N/D |
| | | |

## <a name="related-external-sites"></a>Sites externos relacionados

Ligações do Power BI para outros sites relacionados. Estes sites incluem páginas de documentação, suporte, novos pedidos de funcionalidade e mais. Estes sites não afetarão a funcionalidade do Power BI, pelo que podem ser opcionalmente adicionados à lista de permissões, se quiser.

| Linha | Objetivo | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Opcional:** site da Comunidade | community.powerbi.com </br> oxcrx34285.i.lithium.com | TCP 443 |
| 2 | **Opcional:** site de Documentação | docs.microsoft.com </br> img-prod-cms-rt-microsoft-com.akamaized.net </br> statics-uhf-eas.akamaized.net </br> cdnssl.clicktale.neting-district.clicktale.net | TCP 443 |
| 3 | **Opcional:** site de Transferências (para o Power BI Desktop, etc.) | download.microsoft.com | TCP 443 |
| 4 | **Opcional:** redirecionamentos externos | aka.ms </br> go.microsoft.com | TCP 443 |
| 5 | **Opcional:** site de feedback de ideias| ideas.powerbi.com </br> powerbi.uservoice.com | TCP 443 |
| 6 | **Opcional:** site do Power BI – página de destino, ligações Saiba Mais, site de suporte, ligações para transferências, showcase de parceiros, etc. | powerbi.microsoft.com | TCP 443 |
| 7 | **Opcional:** Centro para Programadores do Power BI | dev.powerbi.com | TCP 443 |
| 8 | **Opcional:**  site de suporte | support.powerbi.com </br> s3.amazonaws.com </br> *.olark.com </br> logx.optimizely.com </br> mscom.demdex.net </br> tags.tiqcdn.com | TCP 443 |
| | | |