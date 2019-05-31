---
title: Ligar ao Microsoft Azure Consumption Insights com o Power BI
description: Microsoft Azure Consumption Insights para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 089f8c31a0b1eb11f6871268f2f848949be95d9b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222134"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>Ligar ao Microsoft Azure Consumption Insights com o Power BI
Explore e monitorize os seus dados de consumo do Microsoft Azure no Power BI com o pacote de conteúdos do Power BI. Os dados são atualizados automaticamente uma vez por dia.

Ligue-se ao [pacote de conteúdos Microsoft Azure Consumption Insights](https://app.powerbi.com/getdata/services/azureconsumption) para o Power BI.

## <a name="how-to-connect"></a>Como ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
    ![](media/service-connect-to-azure-consumption-insights/getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-azure-consumption-insights/services.png)
3. Selecione **Microsoft Azure Consumption Insights** \> **obter agora**. 
   
   ![](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. Forneça o número de meses de dados que deseja importar e o seu número de registo do Azure Enterprise. Veja detalhes sobre [como encontrar estes parâmetros](#FindingParams) abaixo.
   
    ![](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. Forneça a sua Chave de Acesso para se ligar. Pode encontrar a chave de inscrição no Portal de EA do Azure. 
   
    ![](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. O processo de importação é iniciado automaticamente. Quando terminar, um novo dashboard, relatório e modelo aparecem no painel de navegação. Selecione o dashboard para ver os seus dados importados.
   
   ![](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**O que se segue?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Enquanto o conjunto de dados está agendado para serem atualizadas diariamente, pode alterar a agenda de atualização ou tentar atualizá-lo a pedido através de **atualizar agora**

## <a name="whats-included"></a>O que está incluído
O pacote de conteúdos do Microsoft Azure Consumption Insights inclui dados para o intervalo de meses que forneceu ao ligar-se de relatórios mensais. O intervalo é uma janela móvel, para que as datas incluídas são atualizadas conforme o conjunto de dados é atualizada.

## <a name="system-requirements"></a>Requisitos de Sistema
O pacote de conteúdos requer acesso a funcionalidades do Enterprise no portal do Azure. 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Parâmetros de localização
Relatórios do Power BI estão disponíveis para EA direto, parceiros e clientes Indiretos que pode ver informações de faturação. Leia abaixo para obter detalhes sobre como encontrar cada um dos valores que espera o fluxo de ligação.

**Número de Meses**

* O número de meses (1 e 36) de dados de hoje que pretende importar.

**Número da Inscrição**

* Seu número de inscrição do Azure Enterprise, que pode ser encontrado no [Azure Enterprise Portal](https://ea.azure.com/) ecrã principal, sob **detalhes da inscrição**.
  
    ![](media/service-connect-to-azure-consumption-insights/params2.png)

**Chave de Acesso**

* Pode encontrar a chave de acesso no portal do Azure Enterprise, em **transferir utilização** > **chave de acesso de API**.
  
    ![](media/service-connect-to-azure-consumption-insights/creds2.png)

**Ajuda Adicional**

* Para obter ajuda adicional configurar o pacote do Azure Enterprise para o Power BI, inicie sessão no Azure Enterprise Portal e ver o arquivo de ajuda de API em **ajudar**. Também pode encontrar as instruções adicionais em **relatórios** -> **transferir utilização** -> **chave de acesso de API**.

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Obter dados no Power BI](service-get-data.md)

