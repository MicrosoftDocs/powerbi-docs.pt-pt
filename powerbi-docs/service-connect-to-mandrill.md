---
title: Ligar-se ao Mandrill com o Power BI
description: Mandrill para o Power BI
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
ms.openlocfilehash: 976ca32f0c43f6d8412f9468dc9f61ab9768fa4c
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-mandrill-with-power-bi"></a>Ligar-se ao Mandrill com o Power BI
O pacote de conteúdos do Power BI extrai dados da sua conta do Mandrill e gera um dashboard, um conjunto de relatórios e um conjunto de dados para permitir que explore seus dados. Utilize a análise do Mandrill para obter informações rapidamente sobre a sua campanha de newsletter e de marketing. Os dados são configurados para serem atualizados diariamente, o que garante que os dados que está a monitorizar são atuais.

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

* Tente [fazer uma pergunta na caixa de Perguntas e Respostas](service-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Enquanto o seu conjunto de dados vai ser agendado para ser atualizado diariamente, pode alterar o agendamento de atualização ou tentar atualizá-lo sob pedido em **Atualizar Agora**

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Power BI - Conceitos Básicos](service-basic-concepts.md)
