---
title: Ligue-se ao Lithium com o Power BI
description: Lithium para o Power BI
services: powerbi
documentationcenter: 
author: joeshoukry
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: yshoukry
ms.openlocfilehash: ed7255df535cf2e6703fe9235b192c85d98d92d3
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-lithium-with-power-bi"></a>Ligue-se ao Lithium com o Power BI
O Lithium cria relações de confiança entre marcas melhor do mundo e os seus clientes, ajudando as pessoas a obter respostas e partilhar as suas experiências. Ao ligar ao pacote de conteúdos do Lithium ao Power BI, pode medir as métricas-chave sobre a sua comunidade online para ajudar a estimular as vendas, reduzir os custos de serviço e aumentar a fidelidade. 

Ligue-se ao [pacote de conteúdo do Lithium](https://app.powerbi.com/getdata/services/lithium) para o Power BI.

>[!NOTE]
>O pacote de conteúdo do Power BI usa a API do Lithium. As chamadas excessivas à API podem resultar em despesas adicionais do Lithium. Confirme com o seu administrador do Lithium.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-lithium/pbi_getdata.png) 
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-lithium/pbi_getservices.png) 
3. Selecione **Lithium** \> **Obter**.
   
   ![](media/service-connect-to-lithium/lithiumconnect.png)
4. Forneça o URL da sua comunidade do Lithium. Será sob a forma de *https://community.yoursite.com*.
   
   ![](media/service-connect-to-lithium/params.png)
5. Quando solicitado, insira as suas credenciais do Lithium. Selecione **oAuth 2** como mecanismo de autenticação, clique em **Iniciar Sessão** e siga o fluxo de autenticação do Lithium.
   
   ![](media/service-connect-to-lithium/creds.png)
   
   ![](media/service-connect-to-lithium/creds2.png)
6. Quando o fluxo de início de sessão estiver concluído, o processo de importação será iniciado. Quando concluído, um novo dashboard, relatório e modelo aparecem no Painel de Navegação. Selecione o dashboard para ver os dados importados.
   
    ![](media/service-connect-to-lithium/lithium.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de Perguntas e Respostas](service-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento de atualização ou tentar atualizá-lo a pedido através de **Atualizar Agora**

## <a name="system-requirements"></a>Requisitos do sistema
O pacote de conteúdo do Lithium exige uma comunidade do Lithium v15.9 ou superior. Entre em contacto com seu administrador do Lithium para confirmar.

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Power BI - Conceitos Básicos](service-basic-concepts.md)

