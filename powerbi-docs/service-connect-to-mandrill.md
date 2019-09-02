---
title: Ligar-se ao Mandrill com o Power BI
description: Mandrill para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 7440fb6dfcd181b6b1164260626cd0bfa7cda991
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185425"
---
# <a name="connect-to-mandrill-with-power-bi"></a>Ligar-se ao Mandrill com o Power BI
O pacote de conteúdos do Power BI extrai dados da sua conta do Mandrill e gera um dashboard, um conjunto de relatórios e um conjunto de dados para permitir que explore seus dados. Utilize a análise do Mandrill para obter informações rapidamente sobre a sua campanha de newsletter e de marketing. Os dados são configurados para serem atualizados diariamente, o que garante que os dados que está a monitorizar são atuais.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Ligue-se ao [pacote de conteúdo do Mandrill para o Power BI.](http://app.powerbi.com/getdata/services/mandrill)

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
    ![](media/service-connect-to-mandrill/getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
    ![](media/service-connect-to-mandrill/services.png)
3. Selecione **Mandrill** > **Obter**.
   
    ![](media/service-connect-to-mandrill/mandrill.png)
4. Como **Método de Autenticação**, selecione **Chave** e forneça chave de API. Pode encontrar a chave no separador **Configurações** no dashboard do Mandrill. Selecione **Iniciar Sessão** para iniciar o processo de importação, que pode levar alguns minutos dependendo do volume de dados na conta.
   
    ![](media/service-connect-to-mandrill/auth.png)
5. Após o Power BI importar os dados, verá novos elementos (dashboard, relatório e conjunto de dados) no painel de navegação esquerdo. Esse é o dashboard padrão criado pelo Power BI para exibir os seus dados.
   
    ![](media/service-connect-to-mandrill/mandrill-dashboard1.jpg)

**E agora?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento das atualizações ou tentar atualizá-lo a pedido através da opção **Atualizar Agora**

## <a name="next-steps"></a>Próximos passos
[O que é o Power BI?](power-bi-overview.md)

[Conceitos básicos para designers no serviço Power BI](service-basic-concepts.md)

