---
title: URLs do Power BI
description: Os clientes que utilizam o Power BI devem conseguir ligar aos pontos finais
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/13/2018
ms.openlocfilehash: 8e29fa0c9471bb865619102247f38776208c3d87
ms.sourcegitcommit: 8990028a348b642ba5c96f001fe3a4280f0166ee
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/14/2018
ms.locfileid: "40101145"
---
# <a name="power-bi-urls"></a>URLs do Power BI

**O serviço online do Power BI**, também denominado Power BI SaaS (Software como Serviço), necessita de conectividade à Internet. Os clientes que utilizam o serviço online do Power BI devem conseguir ligar aos pontos finais abaixo.

Para utilizar o serviço online do Power BI, tem de ter acesso para se ligar aos pontos finais marcados como **obrigatório** nas tabelas abaixo e todos os pontos finais marcados como **obrigatório** nos sites ligados. Se a ligação para um site externo o direcionar para uma secção específica, só precisará de rever os pontos finais nessa secção.

Os pontos finais marcados como **opcional** também podem ser **adicionados à lista de permissões** para que uma funcionalidade específica funcione.

O serviço online do Power BI só necessita que a Porta TCT 443 esteja aberta para os pontos finais listados.

Os carateres universais (*) representam todos os níveis sob o domínio de raiz e utilizamos N/D quando as informações não estão disponíveis. A coluna **Destino(s)** é uma lista de domínios FQDN e ligações para sites externos que contêm mais informações de pontos finais.

>[!Important]
>As informações nas tabelas abaixo não representam a **cloud da Administração Pública dos Estados Unidos**, **a cloud da Alemanha** e **a cloud da China**.

## <a name="authentication"></a>Autenticação

O Power BI depende dos pontos finais obrigatórios nas secções de autenticação e identidade do Office 365. Para utilizar o Power BI, tem de conseguir ligar-se aos pontos finais no site apresentado abaixo.

| Linha | Objetivo | Destino(s) | Porta(s) |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obrigatório:** autenticação e identidade | Veja a [secção Autenticação e identidade do Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_identity) no site de lista de permissões do Office 365 | N/D |

## <a name="general-site-usage"></a>Utilização geral do site

Para a utilização geral do Power BI, tem de conseguir ligar-se aos pontos finais na tabela e nos sites apresentados abaixo.

| Linha | Objetivo | Destino(s) | Porta(s) |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obrigatório:** APIs de back-end | *.analysis.windows.net | TCP 443 |
| 2 | **Obrigatório:** integração do Office 365 | Veja a [secção Portal e serviços partilhados do Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_portal-identity) no site de lista de permissões do Office 365 | N/D |
| 3 | **Obrigatório:** Portal | app.powerbi.com | TCP 443 |
| 4 | **Obrigatório:** telemetria do serviço | dc.services.visualstudio.com | TCP 443 |
| 5 | **Opcional:** mensagens informativas | dynmsg.modpim.com | TCP 443 |
| 6 | **Opcional:** inquéritos do NPS | nps.onyx.azure.net | TCP 443 |

## <a name="administration"></a>Administração

Para efetuar funções administrativas no Power BI, tem de conseguir ligar-se aos pontos finais nos sites ligados abaixo.

| Linha | Objetivo | Destino(s) | Porta(s) |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obrigatório:** para gerir utilizadores e ver registos de auditoria | Veja a [secção Portal e serviços partilhados do Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_portal-identity) no site de lista de permissões do Office 365 | N/D |

## <a name="get-data"></a>Obter Dados

Para conseguir obter dados de origens de dados específicas, como o OneDrive, tem de conseguir ligar-se aos pontos finais na tabela abaixo.

| Linha | Objetivo | Destino(s) | Porta(s) |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obrigatório:** AppSource (aplicações internas ou externas no Power BI) | appsource.microsoft.com | TCP 443 |
| 2 | **Opcional:** importar ficheiros do OneDrive pessoal | Veja o site [Required URLs and ports for OneDrive](https://support.office.com/en-ie/article/required-urls-and-ports-for-onedrive-ce15d2cc-52ef-42cd-b738-d9c6f9b03f3a) (URLs e portas obrigatórios para o OneDrive) | N/D |
| 3 | **Opcional:** tutorial em vídeo Power BI in 60-Seconds (O Power BI em 60 Segundos) | *.doubleclick.net </br> *.ggpht.com </br> *.google.com </br> *.googlevideo.com </br> *.youtube.com </br> *.ytimg.com </br> fonts.gstatic.com | TCP 443 |
| 4 | **Opcional:** origens de dados de transmissão em fluxo do PubNub | Veja a [documentação do PubNub](https://support.pubnub.com/support/solutions/articles/14000043522) | N/D |

## <a name="dashboard-and-report-integration"></a>Integração de dashboards e relatórios 

O Power BI depende de determinados pontos finais para suportar os seus dashboards e relatórios. Tem de conseguir ligar-se aos pontos finais na tabela e nos sites ligados abaixo.

| Linha | Objetivo | Destino(s) | Porta(s) |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obrigatório:** integração do Excel | Veja a [secção Office Online](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_officeonline) no site de lista de permissões do Office 365 | N/D |

## <a name="custom-visuals"></a>Elementos visuais personalizados

O Power BI depende de determinados pontos finais para conseguir ver e aceder aos elementos visuais personalizados. Tem de conseguir ligar-se aos pontos finais na tabela e nos sites ligados abaixo.

| Linha | Objetivo | Destino(s) | Porta(s) |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obrigatório:** importar um elemento visual personalizado da interface do Microsoft Azure Marketplace e um ficheiro | *.microsoft.com </br> *.bing.com </br> *.msecnd.net </br> *.osi.office.net </br> *.azureedge.net </br> ajax.aspnetcdn.com </br> nexus.ensighten.com </br> store.office.com | TCP 443 |
| 2 | **Opcional:** Mapas Bing | bing.com </br> platform.bing.com </br> *.dynamic.tiles.virtualearth.net </br> *.virtualearth.net | TCP 443 |
| 3 | **Opcional:** PowerApps | Veja a [secção Serviços necessários](https://docs.microsoft.com/powerapps/maker/canvas-apps/limits-and-config#required-services) no site de requisitos de sistema do PowerApps | N/D |
| 4 | **Opcional:** Visio | Veja a [secção Office Online](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_officeonline) no site de lista de permissões do Office 365 | N/D |