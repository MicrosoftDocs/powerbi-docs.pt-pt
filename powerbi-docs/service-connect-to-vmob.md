---
title: Ligar VMob com o Power BI
description: VMob para Power BI
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
ms.openlocfilehash: fc0c8bc1ea177e20c25a614ed1de274f70056578
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-vmob-with-power-bi"></a>Ligar VMob com o Power BI
É fácil acompanhar e explorar dados do VMob com o Power BI e o pacote de conteúdos do VMob. O Power BI devolve os seguintes dados: Estatísticas do Utilizador para todas as horas e nos últimos 30 dias, KPI de Varejo nos últimos 30 dias e Desempenho da Campanha nos últimos 30 dias.

Ligue-se ao [pacote de conteúdo do VMob](https://app.powerbi.com/getdata/services/vmob) para o Power BI.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
    ![](media/service-connect-to-vmob/getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-vmob/services.png)
3. Selecione **VMob** \> **Obter**.
   
   ![](media/service-connect-to-vmob/vmob.png)
4. Quando solicitado, insira o URL do VMob e clique no botão Avançar. Este URL é fornecido pelo VMob em separado.
   
    ![](media/service-connect-to-vmob/params.png)
5. Escolha a opção **Básico** no menu suspenso do Método de autenticação, introduza o nome de utilizador do VMob e a palavra-passe e clique no botão **Iniciar Sessão**.
   
    ![](media/service-connect-to-vmob/creds.png)
6. O processo de importação é iniciado automaticamente e o Power BI devolve os dados do VMob para criar um relatório e dashboard prontos para utilizar.
   
   ![](media/service-connect-to-vmob/dashboard2.png)

**O que se segue?**

* Tente [fazer uma pergunta na caixa de Perguntas e Respostas](service-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Enquanto o seu conjunto de dados vai ser agendado para ser atualizado diariamente, pode alterar o agendamento de atualização ou tentar atualizá-lo sob pedido em **Atualizar Agora**

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Obter dados no Power BI](service-get-data.md)
