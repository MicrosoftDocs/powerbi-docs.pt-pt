---
title: Ligue ao Stripe com o Power BI
description: Stripe para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: b0e8739e93d24ba10b0ffc72042b847cce1d5fe9
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060774"
---
# <a name="connect-to-stripe-with-power-bi"></a>Ligue ao Stripe com o Power BI
Visualize e explore os seus dados do Stripe para o Power BI com o pacote de conteúdos para o Power BI. O pacote de conteúdos do Stripe para o Power BI recebe dados por pull sobre Clientes, Encargos, Eventos e Recibos. Os dados incluem os dez mil eventos e as cinco mil despesas mais recentes nos últimos 30 dias. O conteúdo é atualizado automaticamente uma vez por dia numa agenda que controle. 

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Conecte-se ao [pacote de conteúdo do Stripe para o Power BI](https://app.powerbi.com/getdata/services/stripe).

## <a name="how-to-connect"></a>Como se ligar
1. Selecione Obter Dados na parte inferior do painel de navegação esquerdo.  
   
    ![](media/service-connect-to-stripe/getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.  
   
    ![](media/service-connect-to-stripe/services.png)  
3. Selecione **Stripe** &gt; **Obter**.  
   
    ![](media/service-connect-to-stripe/stripe.png)  
4. Forneça sua [chave de API](https://dashboard.stripe.com/account/apikeys) do Stripe para se conectar.  
   
    ![](media/service-connect-to-stripe/creds.png)
5. O processo de importação é iniciado automaticamente. Quando concluído, um novo dashboard, relatório e modelo aparecerão no Painel de Navegação, marcados com um asterisco. Selecione o dashboard para ver os seus dados importados.
   
    ![](media/service-connect-to-stripe/dashboard.png)

**O que se segue?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento das atualizações ou tentar atualizá-lo a pedido através da opção **Atualizar Agora**

## <a name="next-steps"></a>Próximos passos
[O que é o Power BI?](fundamentals/power-bi-overview.md)

[Obter Dados para o Power BI](service-get-data.md)

