---
title: Ligar ao Microsoft Azure Enterprise com o Power BI
description: Microsoft Azure Enterprise para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 4cedeac37a47ffaa41ff9088c9ef36c37b4c784e
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54008287"
---
# <a name="connect-to-microsoft-azure-enterprise-with-power-bi"></a>Ligar ao Microsoft Azure Enterprise com o Power BI
Explore e monitorize os seus dados do Microsoft Azure Enterprise no Power BI com o pacote de conteúdos do Power BI. Os dados são atualizados automaticamente uma vez por dia.

Ligue-se ao [pacote de conteúdos do Microsoft Azure Enterprise](https://app.powerbi.com/getdata/services/azure-enterprise) para o Power BI.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
    ![](media/service-connect-to-azure-enterprise/getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-azure-enterprise/services.png)
3. Selecione **Microsoft Azure Enterprise** \> **Obter**.
   
   ![](media/service-connect-to-azure-enterprise/mazureenterprise.png)
4. Forneça o URL do Ambiente do Azure, o número de meses de dados que deseja importar e o seu número de inscrição do Azure Enterprise. O URL do Ambiente do Azure vai ser `https://ea.azure.com` ou `https://ea.windowsazure.cn`. Veja detalhes sobre [como encontrar os parâmetros](#FindingParams) abaixo.
   
    ![](media/service-connect-to-azure-enterprise/params.png)
5. Forneça a sua Chave de Acesso para se ligar. A chave para a sua inscrição pode ser encontrada no Portal EA do Azure.
   
    ![](media/service-connect-to-azure-enterprise/creds.png)
6. O processo de importação será iniciado automaticamente. Quando concluído, um novo dashboard, relatório e modelo aparecerão no Painel de Navegação. Selecione o dashboard para ver os seus dados importados.
   
   ![](media/service-connect-to-azure-enterprise/dashboard.png)

**O que se segue?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento das atualizações ou tentar atualizá-lo a pedido através da opção **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
O pacote de conteúdos do Azure Enterprise inclui dados de relatórios mensais para o intervalo de meses que fornecer durante o fluxo de ligação. O intervalo é uma janela móvel, portanto as datas incluídas são atualizadas à medida que o conjunto de dados é atualizado.

## <a name="system-requirements"></a>Requisitos de Sistema
O pacote de conteúdos exige acesso às funcionalidades do Enterprise no Portal do Azure.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Localizar parâmetros
Os relatórios do Power BI estão disponíveis para EA Direto, Parceiros e Clientes Indiretos que podem ver as informações de faturação. Leia abaixo para obter detalhes sobre a localização de cada um dos valores esperados pelo fluxo de conexão.

**URL de Ambiente do Azure**

* Normalmente, o valor é https://ea.azure.com. No entanto, pode confirmar ao iniciar sessão e, em seguida, verificar o URL.
  
    ![](media/service-connect-to-azure-enterprise/params3.png)

**Número de Meses**

* Deve ser um número entre 1 e 36, que representa o número de meses de dados (a partir de hoje) que quer importar.

**Número da Inscrição**

* Este é o número de inscrição do Azure Enterprise que pode ser encontrado no ecrã inicial do [Azure Enterprise Portal](https://ea.azure.com/) em "Detalhes da Inscrição".
  
    ![](media/service-connect-to-azure-enterprise/params2.png)

**Chave de Acesso**

* A chave pode ser encontrada no portal do Azure Enterprise, em "Transferir Utilização" > "Chave de Acesso da API"
  
    ![](media/service-connect-to-azure-enterprise/creds2.png)

**Ajuda Adicional**

* Para ter ajuda adicional na configuração do pacote Power BI do Azure Enterprise, inicie a sessão no Azure Enterprise Portal para ver o ficheiro de ajuda da API em "Ajuda" e as instruções adicionais em Relatórios -> Transferir Utilização -> Chave de Acesso da API.

## <a name="next-steps"></a>Passos seguintes
[Introdução ao Power BI](service-get-started.md)

[Obter dados no Power BI](service-get-data.md)

