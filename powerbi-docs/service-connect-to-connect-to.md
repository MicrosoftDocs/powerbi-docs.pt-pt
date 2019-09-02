---
title: Ligue-se a comScore Digital Analytix com o Power BI
description: comScore Digital Analytix para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: aab2d62265300787f99116aade7ec16aaf1b0f86
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185585"
---
# <a name="connect-to-comscore-digital-analytix-with-power-bi"></a>Ligue-se a comScore Digital Analytix com o Power BI
Visualize e explore os seus dados do comScore Digital Analytix no Power BI com o pacote de conteúdos do Power BI. Os dados serão atualizados automaticamente uma vez por dia.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Ligue-se ao [pacote de conteúdos da comScore para o Power BI](https://app.powerbi.com/getdata/services/comscore).

>[!NOTE]
>Para se ligar ao pacote de conteúdos, precisa de uma conta de utilizador do comScore DAx e ter acesso à API da comScore. Mais [detalhes](#Requirements) abaixo.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione Obter Dados na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-connect-to/getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-connect-to/services.png)
3. Selecione **comScore Digital Analytix** \> **Obter**.
   
   ![](media/service-connect-to-connect-to/comscore.png)
4. Forneça o datacenter, o ID de Cliente comScore e o Site aos quais gostaria de se ligar. Para obter mais detalhes sobre como encontrar estes valores, veja [Encontrar os parâmetros do comScore](#FindingParams) abaixo.
   
   ![](media/service-connect-to-connect-to/parameters.png)
5. Forneça o seu nome de utilizador e palavra-passe comScore para se ligar. Veja detalhes sobre como encontrar este valor abaixo.
   
   ![](media/service-connect-to-connect-to/creds.png)
6. O processo de importação será iniciado automaticamente. Quando concluído, um novo dashboard, relatório e modelo aparecerão no Painel de Navegação. Selecione o dashboard para ver os seus dados importados.

**O que se segue?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento das atualizações ou tentar atualizá-lo a pedido através da opção **Atualizar Agora**

<a name="Requirements"></a>

## <a name="system-requirements"></a>Requisitos de sistema
São necessários uma conta de utilizador de DAx comScore e acesso ao comScore DAx API para estabelecer a ligação. Contacte o administrador do comScore DAx para confirmar a sua conta.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Parâmetros de localização
Veja abaixo detalhes sobre como encontrar cada um dos parâmetros comScore.

**Data Center**

O datacenter ao qual se liga é determinado pelo URL para o qual navega no comScore.

![](media/service-connect-to-connect-to/comscore_url.png) 

**Cliente**

O Cliente é o mesmo que forneceu ao entrar no comScore DAx.

![](media/service-connect-to-connect-to/comscore_signin.png) 

**Site**

O site comScore determina o site cujos dados gostaria de ver. Pode encontrar a lista de sites a partir da sua conta comScore.

![](media/service-connect-to-connect-to/comscore_sites.png)

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Obter dados no Power BI](service-get-data.md)

