---
title: Adicionar URLs do Power BI à lista de permissões
description: Este artigo lista as portas e os pontos finais dos URLs para adicionar à lista de permissões a conectividade com o Power BI.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 06/25/2020
ms.custom: seodec18
ms.openlocfilehash: 433b3d53ccb653e1a945a83176ab9ebc19ccac5d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96409246"
---
# <a name="add-power-bi-urls-to-your-allow-list"></a>Adicionar URLs do Power BI à lista de permissões
[//]: # "suparnap, miwehnia e natham são contactos para manter esta lista"

O serviço Power BI requer conectividade com a Internet. Os pontos finais listados nas tabelas deste artigo devem estar acessíveis para os clientes que utilizam o serviço Power BI.

Para utilizar o serviço Power BI, tem de ser capaz de se ligar aos pontos finais marcados como **obrigatórios** nas tabelas abaixo e a todos os pontos finais marcados como **obrigatórios** nos sites ligados. Se a ligação para um site externo o direcionar para uma secção específica, só precisará de rever os pontos finais nessa secção.

Os pontos finais marcados como **opcionais** também podem ser adicionados à lista de permissões para que uma funcionalidade específica funcione.

O serviço Power BI apenas requer que a Porta TCP 443 esteja aberta para os pontos finais listados.

Os carateres universais (*) representam todos os níveis sob o domínio de raiz e utilizamos N/D quando as informações não estão disponíveis. A coluna **Destino(s)** lista os nomes de domínio e ligações para sites externos que contêm mais informações de pontos finais.

>[!Important]
>As informações nas tabelas abaixo não se aplicam ao Power BI Alemanha, ao Power BI China operado pela 21Vianet ou ao Power BI for US Government. Leia [Ligar serviços cloud do Azure globais e da administração pública](service-govus-overview.md#connect-government-and-global-azure-cloud-services) para saber mais sobre a comunicação entre serviços cloud.

## <a name="authentication"></a>Autenticação

O Power BI depende dos pontos finais obrigatórios nas secções de autenticação e identidade do Microsoft 365. Para utilizar o Power BI, tem de conseguir ligar-se aos pontos finais no site apresentado abaixo.

| Linha | Objetivo | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** Autenticação e identidade | Veja a seguinte documentação: [Microsoft 365 Common and Office Online URLs](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) (URLs do Microsoft 365 Common e Office Online)  | N/D |

## <a name="general-site-usage"></a>Utilização geral do site

Para a utilização geral do Power BI, tem de conseguir ligar-se aos pontos finais na tabela e nos sites apresentados abaixo.

| Linha | Objetivo | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** APIs de back-end | api.powerbi.com | TCP 443 |
| 2 | **Obrigatório:** APIs de back-end | *.analysis.windows.net | TCP 443 |
| 3 | **Obrigatório:** APIs de back-end | *.pbidedicated.windows.net | TCP 443 |
| 4 | **Obrigatório:** Rede de Entrega de Conteúdos (CDN) | content.powerapps.com | TCP 443 |
| 5 | **Obrigatório:** Integração do Microsoft 365 | Veja a seguinte documentação: [Microsoft 365 Common and Office Online URLs](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) (URLs do Microsoft 365 Common e Office Online) | N/D |
| 6 | **Obrigatório:** Portal | *.powerbi.com | TCP 443 |
| 7 | **Obrigatório:** Telemetria do serviço | dc.services.visualstudio.com | TCP 443 |
| 8 | **Opcional:** Mensagens informativas | dynmsg.modpim.com | TCP 443 |
| 9 | **Opcional:** Inquéritos do NPS | nps.onyx.azure.net | TCP 443 |
| | | |

## <a name="administration"></a>Administração

Para realizar funções administrativas no Power BI, tem de conseguir ligar-se aos pontos finais nos sites ligados abaixo.

| Linha | Objetivo | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** Para gerir utilizadores e ver registos de auditoria | Veja a seguinte documentação: [Microsoft 365 Common and Office Online URLs](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) (URLs do Microsoft 365 Common e Office Online) | N/D |
| | | |

## <a name="getting-data"></a>Obter dados

Para obter dados de origens de dados específicas, como o OneDrive, tem de conseguir ligar-se aos pontos finais na tabela abaixo. Poderá ser necessário o acesso a URLs e domínios de Internet adicionais para origens de dados específicas utilizadas na sua organização.

| Linha | Objetivo | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** AppSource (aplicações internas ou externas no Power BI) | appsource.microsoft.com <br> *.s-microsoft.com  | TCP 443 |
| 2 | **Opcional:** Iniciar sessão e obter dados de pacotes de conteúdos | Depende dos pacotes de conteúdos utilizados | Depende dos pacotes de conteúdos utilizados |
| 3 | **Opcional:** Importar ficheiros do OneDrive pessoal | Veja o site [Required URLs and ports for OneDrive](/onedrive/required-urls-and-ports) (URLs e portas obrigatórios para o OneDrive) | N/D |
| 4 | **Opcional:** Tutorial em vídeo Power BI in 60-Seconds (O Power BI em 60 Segundos) | *.doubleclick.net <br> *.ggpht.com <br> *.google.com <br> *.googlevideo.com <br> *.youtube.com <br> *.ytimg.com <br> fonts.gstatic.com | TCP 443 |
| 5 | **Opcional:** Origens de dados de transmissão em fluxo do PubNub | Veja a [documentação do PubNub](https://support.pubnub.com/support/solutions/articles/14000043522) | N/D |
| | | |

## <a name="dashboard-and-report-integration"></a>Integração de dashboards e relatórios

O Power BI depende de determinados pontos finais para suportar os seus dashboards e relatórios. Tem de conseguir ligar-se aos pontos finais na tabela e nos sites ligados abaixo.

| Linha | Objetivo | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** Integração do Excel | Veja a seguinte documentação: [Microsoft 365 Common and Office Online URLs](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) (URLs do Microsoft 365 Common e Office Online) | N/D |
| | | |

## <a name="power-bi-visuals"></a>Elementos Visuais do Power BI

O Power BI depende de determinados pontos finais para ver e aceder aos elementos visuais do Power BI. Tem de conseguir ligar-se aos pontos finais na tabela e nos sites ligados abaixo.

| Linha | Objetivo | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Obrigatório:** Importar um elemento visual personalizado da interface do Marketplace ou de um ficheiro | *.azureedge.net <br> *.blob.core.windows.net <br> *.osi.office.net <br> *.msecnd.net <br> store.office.com <br> web.vortex.data.microsoft.com <br> store-images.s-microsoft.com | TCP 443 |
| 2 | **Opcional:** Mapas Bing | bing.com <br> platform.bing.com <br> *.virtualearth.net | TCP 443 |
| 3 | **Opcional:** PowerApps | Veja a [secção Serviços necessários](/powerapps/maker/canvas-apps/limits-and-config#required-services) no site de requisitos de sistema do PowerApps | N/D |
| 4 | **Opcional:** Visio | Veja a seguinte documentação: [Microsoft 365 Common and Office Online URLs](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) (URLs do Microsoft 365 Common e Office Online) e [SharePoint Online and OneDrive for Business](/office365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business) (SharePoint Online e OneDrive para Empresas) | N/D |
| | | |

## <a name="related-external-sites"></a>Sites externos relacionados

Ligações do Power BI para outros sites relacionados. Estes sites alojam a documentação, o suporte, os novos pedidos de funcionalidades e muito mais. O acesso a estes sites não afetará a funcionalidade do Power BI, pelo que a adição a listas de permissões é opcional.

| Linha | Objetivo | Destino(s) | Porta(s) |
| --- | --- | --- | --- |
| 1 | **Opcional:** Site da Comunidade | community.powerbi.com <br> oxcrx34285.i.lithium.com | TCP 443 |
| 2 | **Opcional:** Site de documentação | docs.microsoft.com <br> img-prod-cms-rt-microsoft-com.akamaized.net <br> statics-uhf-eas.akamaized.net <br> cdnssl.clicktale.net <br> ing-district.clicktale.net | TCP 443 |
| 3 | **Opcional:** Site de Transferências (para o Power BI Desktop, etc.) | download.microsoft.com | TCP 443 |
| 4 | **Opcional:** Redirecionamentos externos | aka.ms <br> go.microsoft.com | TCP 443 |
| 5 | **Opcional:** Site de feedback de ideias| ideas.powerbi.com <br> powerbi.uservoice.com | TCP 443 |
| 6 | **Opcional:** Site do Power BI – página de destino, ligações para saber mais, site do suporte, ligações para transferências, demonstração de parceiros, etc. | powerbi.microsoft.com | TCP 443 |
| 7 | **Opcional:** Centro para Programadores do Power BI | dev.powerbi.com | TCP 443 |
| 8 | **Opcional:** Site de suporte | support.powerbi.com <br> s3.amazonaws.com <br> *.olark.com <br> logx.optimizely.com <br> mscom.demdex.net <br> tags.tiqcdn.com | TCP 443 |
| | | |