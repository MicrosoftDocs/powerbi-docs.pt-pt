---
title: Ligue-se ao Project Online com o Power BI
description: Project Online para o Power BI
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
ms.openlocfilehash: 509b75d91611de827b236e45dc25ef893aff8177
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-project-online-with-power-bi"></a>Ligue-se ao Project Online com o Power BI
Microsoft Project Online é uma solução online flexível para PPM (gestão de portefólios de projetos) e para o trabalho quotidiano. O Project Online permite que as organizações comecem, atribuam prioridades a investimentos de portefólio de projetos e entreguem o valor comercial pretendido. O pacote de conteúdos do Project Online para o Power BI permite que explore os seus dados de projetos com métricas prontas para uso, como estado do portefólio e conformidade do projeto.

Ligue-se ao [pacote de conteúdo do Project Online](https://app.powerbi.com/getdata/services/project-online) para o Power BI.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
    ![](media/service-connect-to-project-online/getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-project-online/services.png)
3. Selecione **Microsoft Project Online** \> **Obter**.
   
   ![](media/service-connect-to-project-online/mproject.png)
4. Na caixa de texto **URL do Project Web App**, introduza o URL para o PWA (Project Web Add) ao qual pretende ligar-se e clique em **Avançar**. Observe que isso pode ser diferente do exemplo, caso tenha um domínio personalizado.
   
    ![](media/service-connect-to-project-online/params.png)
5. Como Método de Autenticação, selecione **oAuth2** \> **Iniciar Sessão**. Quando solicitado, insira as suas credenciais do Project Online e siga o processo de autenticação.
   
    ![](media/service-connect-to-project-online/creds.png)
6. Vai ver uma notificação a indicar que os dados estão a ser carregados. Dependendo do tamanho da sua conta, pode levar algum tempo. Após o Power BI importar os dados, verá novos elementos (dashboard, relatório e conjunto de dados) no painel de navegação esquerdo. Esse é o dashboard padrão criado pelo Power BI para exibir os seus dados. Pode alterar este dashboard para ver os seus dados de qualquer modo que queira.
   
   ![](media/service-connect-to-project-online/dashboard2.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de Perguntas e Respostas](service-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Enquanto o seu conjunto de dados vai ser agendado para ser atualizado diariamente, pode alterar o agendamento de atualização ou tentar atualizá-lo sob pedido em **Atualizar Agora**

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Obter dados no Power BI](service-get-data.md)

