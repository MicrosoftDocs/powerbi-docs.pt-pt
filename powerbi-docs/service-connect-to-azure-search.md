---
title: Ligar a Azure Search ao Power BI
description: Azure Search para Power BI
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
ms.openlocfilehash: eb106547efa67accacd3c955d53bc9ac4d114d8e
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-azure-search-with-power-bi"></a>Ligar a Azure Search ao Power BI
A Análise de Tráfego do Azure Search permite que monitorize e compreenda o tráfego para o serviço de Azure Search. O pacote de conteúdos do Azure Search para o Power BI fornece informações detalhadas sobre os seus dados de pesquisa, incluindo Search, Indexação, Estado do Serviço e a Latência dos últimos 30 dias. Podem ser encontrados mais detalhes na [mensagem de blogue do Azure](https://azure.microsoft.com/en-us/blog/analyzing-your-azure-search-traffic/).

Ligue-se ao [pacote de conteúdo do Azure Search](https://app.powerbi.com/getdata/services/azure-search) para o Power BI.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-azure-search/pbi_getdata.png) 
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-azure-search/pbi_getservices.png) 
3. Selecione **Azure Search** \> **Obter**.
   
   ![](media/service-connect-to-azure-search/azuresearch.png)
4. Forneça o nome da conta de armazenamento de tabelas na qual a sua análise do Azure Search está armazenada.
   
   ![](media/service-connect-to-azure-search/params.png)
5. Selecione **Chave** como Mecanismo de Autenticação e forneça a chave da conta de armazenamento. Clique em **Iniciar Sessão** para iniciar o processo de carregamento.
   
   ![](media/service-connect-to-azure-search/creds.png)
6. Quando o carregamento estiver concluído, um novo dashboard, relatório e modelo aparecem no Painel de Navegação. Selecione o dashboard para ver os dados importados.
   
    ![](media/service-connect-to-azure-search/dashboard2.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de Perguntas e Respostas](service-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Enquanto o seu conjunto de dados vai ser agendado para ser atualizado diariamente, pode alterar o agendamento de atualização ou tentar atualizá-lo sob pedido em **Atualizar Agora**

## <a name="system-requirements"></a>Requisitos do sistema
O pacote de conteúdos do Azure Search exige que a Análise de Tráfego do Azure Search esteja ativada na conta.

## <a name="troubleshooting"></a>Resolução de problemas
Certifique-se de que o nome da conta de armazenamento seja fornecido corretamente com a chave de acesso completo. O nome da conta de armazenamento deve corresponder à conta configurada com a Análise de Tráfego do Azure Search.

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Power BI - Conceitos Básicos](service-basic-concepts.md)
