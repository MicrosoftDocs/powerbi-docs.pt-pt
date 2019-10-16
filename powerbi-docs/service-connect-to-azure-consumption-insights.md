---
title: Ligar ao Microsoft Azure Consumption Insights com o Power BI
description: Microsoft Azure Consumption Insights para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 09/25/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: e51f936e44e8c8ee3442aedfb2389675774c0a47
ms.sourcegitcommit: 5e277dae93832d10033defb2a9e85ecaa8ffb8ec
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/07/2019
ms.locfileid: "72020429"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>Ligar ao Microsoft Azure Consumption Insights com o Power BI
Explore e monitorize os dados de consumo do Microsoft Azure no serviço Power BI com o pacote de conteúdos do Power BI. Os dados são atualizados automaticamente uma vez por dia.

Ligue-se ao [Pacote de conteúdos Microsoft Azure Consumption Insights](https://app.powerbi.com/getdata/services/azureconsumption) do serviço Power BI.

> [!NOTE]
> Para uma configuração mais personalizada, experimente o [Conector do Azure Consumption Insights](desktop-connect-azure-consumption-insights.md) no Power BI Desktop.

## <a name="how-to-connect"></a>Como se ligar
1. No serviço Power BI, selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
    ![Obter Dados](media/service-connect-to-azure-consumption-insights/getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![Obter serviços](media/service-connect-to-azure-consumption-insights/services.png)
3. Selecione **Microsoft Azure Consumption Insights** \> **Obter agora**. 
   
   ![Obter agora](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. Forneça o número de meses de dados que deseja importar e o seu número de registo do Azure Enterprise. Veja detalhes sobre [como encontrar estes parâmetros](#FindingParams) abaixo.
   
    ![Ligar ao Microsoft Azure Consumption Insights](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. Forneça a sua Chave de Acesso para se ligar. Encontrará a chave de inscrição no Azure EA Portal. 
   
    ![Microsoft Azure Consumption Insights: chave](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. O processo de importação é iniciado automaticamente. Quando concluído, serão apresentados no Painel de Navegação um novo dashboard, um novo relatório e um novo modelo. Selecione o dashboard para ver os seus dados importados.
   
   ![Dashboard do Microsoft Azure Consumption Insights](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**O que se segue?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Apesar de o seu conjunto de dados estar agendado para atualizações diárias, pode alterar a atualização agendada ou tentar atualizá-la a pedido através da opção **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
O pacote de conteúdos do Microsoft Azure Consumption Insights inclui dados de relatórios mensais relativos ao intervalo de meses fornecido durante a ligação. O intervalo é uma janela móvel, pelo que as datas incluídas serão atualizadas à medida que o conjunto de dados for atualizado.

## <a name="system-requirements"></a>Requisitos de Sistema
O pacote de conteúdos exige acesso às funcionalidades empresariais no portal do Azure. 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Parâmetros de localização
Os relatórios do Power BI estão disponíveis para Clientes EA Diretos, Parceiros e Indiretos que possam ver as informações de faturação. Veja a seguir para obter detalhes sobre a localização de cada um dos valores esperados pelo fluxo de ligação.

**Número de Meses**

* O número de meses (1-36) de dados a contar da data atual que quer importar.

**Número da Inscrição**

* O número da inscrição do Azure Enterprise, que pode encontrar no ecrã principal do [Azure Enterprise Portal](https://ea.azure.com/) em **Detalhes da Inscrição**.
  
    ![Número de Inscrição](media/service-connect-to-azure-consumption-insights/params2.png)

**Chave de Acesso**

* Encontrará a chave de acesso no Azure Enterprise Portal, em **Transferir Utilização** > **Chave de Acesso à API**.
  
    ![Chave de Acesso](media/service-connect-to-azure-consumption-insights/creds2.png)

**Ajuda Adicional**

* Para obter ajuda adicional na configuração do Pacote Power BI do Azure Enterprise, inicie a sessão no Azure Enterprise Portal e veja o Ficheiro de Ajuda da API em **Ajuda**. Também pode encontrar instruções adicionais em **Relatórios** -> **Transferir Utilização** -> **Chave de Acesso à API**.
* Para uma configuração mais personalizada, experimente o [Conector do Azure Consumption Insights](desktop-connect-azure-consumption-insights.md) no Power BI Desktop.

## <a name="next-steps"></a>Próximos passos

[Conector do Azure Consumption Insights](desktop-connect-azure-consumption-insights.md) no Power BI Desktop

[Obter dados no Power BI](service-get-data.md)

