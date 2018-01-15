---
title: Ligar ao Microsoft Azure Consumption Insights com o Power BI
description: Microsoft Azure Consumption Insights para o Power BI
services: powerbi
documentationcenter: 
author: joeshoukry
manager: kfile
backup: maggies
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
ms.openlocfilehash: 99f6f4b9159e2ab7261ab179811154ee2ef4929e
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>Ligar ao Microsoft Azure Consumption Insights com o Power BI
Explore e monitorize os seus dados de consumo do Microsoft Azure no Power BI com o pacote de conteúdos do Power BI. Os dados serão atualizados automaticamente uma vez por dia.

Ligue-se ao [pacote de conteúdos Microsoft Azure Consumption Insights](https://app.powerbi.com/getdata/services/azureconsumption) para o Power BI.

## <a name="how-to-connect"></a>Como ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
    ![](media/service-connect-to-azure-consumption-insights/getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-azure-consumption-insights/services.png)
3. Selecione **Microsoft Azure Consumption Insights** \> **Obter**. 
   
   ![](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. Forneça o número de meses de dados que deseja importar e o seu número de registo do Azure Enterprise. Veja detalhes sobre [como encontrar estes parâmetros](#FindingParams) abaixo.
   
    ![](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. Forneça a sua Chave de Acesso para se ligar. A chave para a sua inscrição pode ser encontrada no Portal EA do Azure. 
   
    ![](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. O processo de importação será iniciado automaticamente. Quando concluído, um novo dashboard, relatório e modelo aparecerão no Painel de Navegação. Selecione o dashboard para ver os dados importados.
   
   ![](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de Perguntas e Respostas](service-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento de atualização ou tentar atualizá-lo a pedido através de **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
O pacote de conteúdos do Microsoft Azure Consumption Insights inclui dados de relatórios mensais para o intervalo de meses que fornece durante o fluxo de ligação. O intervalo é uma janela móvel, portanto as datas incluídas são atualizadas à medida que o conjunto de dados é atualizado.

## <a name="system-requirements"></a>Requisitos de Sistema
O pacote de conteúdos exige acesso às funcionalidades do Enterprise no Portal do Azure. 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Localizar parâmetros
Os relatórios do Power BI estão disponíveis para EA Direto, Parceiros e Clientes Indiretos que podem ver as informações de faturação. Leia abaixo para obter detalhes sobre a localização de cada um dos valores esperados pelo fluxo de ligação.

**Número de Meses**

* Deve ser um número entre 1 e 36, que representa o número de meses de dados (a partir de hoje) que quer importar.

**Número da Inscrição**

* Este é o número de inscrição do Azure Enterprise que pode ser encontrado no ecrã inicial do [Azure Enterprise Portal](https://ea.azure.com/) em "Detalhes da Inscrição".
  
    ![](media/service-connect-to-azure-consumption-insights/params2.png)

**Chave de Acesso**

* A chave pode ser encontrada no portal do Azure Enterprise, em "Transferir Utilização" > "Chave de Acesso da API"
  
    ![](media/service-connect-to-azure-consumption-insights/creds2.png)

**Ajuda Adicional**

* Para ter ajuda adicional na configuração do pacote Power BI do Azure Enterprise, inicie a sessão no Azure Enterprise Portal para ver o ficheiro de ajuda da API em "Ajuda" e as instruções adicionais em Relatórios -> Transferir Utilização -> Chave de Acesso da API. 

## <a name="next-steps"></a>Passos seguintes
[Introdução ao Power BI](service-get-started.md)

[Obter dados no Power BI](service-get-data.md)

