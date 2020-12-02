---
title: Ligar a Azure Search ao Power BI
description: Azure Search para Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
LocalizationGroup: Connect to services
ms.openlocfilehash: 5c2c5d3b6382fdb85125a71829d62624dab31e83
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403381"
---
# <a name="connect-to-azure-search-with-power-bi"></a>Ligar a Azure Search ao Power BI
A Análise de Tráfego do Azure Search permite que monitorize e compreenda o tráfego para o serviço de Azure Search. O pacote de conteúdos do Azure Search para o Power BI fornece informações detalhadas sobre os seus dados de pesquisa, incluindo Search, Indexação, Estado do Serviço e a Latência dos últimos 30 dias. Podem ser encontrados mais detalhes na [mensagem de blogue do Azure](https://azure.microsoft.com/blog/analyzing-your-azure-search-traffic/).

[!INCLUDE [include-short-name](../includes/service-deprecate-content-packs.md)]

Ligue-se ao [pacote de conteúdo do Azure Search](https://app.powerbi.com/getdata/services/azure-search) para o Power BI.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação.
   
   ![Captura de ecrã a mostrar a opção Obter Dados no Power B I Desktop, com o botão no painel do navegador.](media/service-connect-to-azure-search/pbi_getdata.png) 
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![Captura de ecrã a mostrar a caixa de diálogo Serviços com o botão Obter.](media/service-connect-to-azure-search/pbi_getservices.png) 
3. Selecione **Azure Search** \> **Obter**.
   
   ![Captura de ecrã a mostrar a caixa de diálogo Serviços do Azure com a ligação Obter.](media/service-connect-to-azure-search/azuresearch.png)
4. Forneça o nome da conta de armazenamento de tabelas na qual a sua análise do Azure Search está armazenada.
   
   ![Captura de ecrã a mostrar a caixa de diálogo Ligar do Azure Search, com o campo de nome da conta de armazenamento do Azure.](media/service-connect-to-azure-search/params.png)
5. Selecione **Chave** como Mecanismo de Autenticação e forneça a chave da conta de armazenamento. Clique em **Iniciar Sessão** para iniciar o processo de carregamento.
   
   ![Captura de ecrã a mostrar a caixa de diálogo Ligar do Azure Search, com a Chave que é introduzida no campo de método de Autenticação.](media/service-connect-to-azure-search/creds.png)
6. Quando o carregamento estiver concluído, um novo dashboard, relatório e modelo aparecem no painel de navegação. Selecione o dashboard para ver os seus dados importados.
   
    ![Captura de ecrã a mostrar o painel de navegação com o dashboard, relatório e modelo.](media/service-connect-to-azure-search/dashboard2.png)

**O que se segue?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](../consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](../create-reports/service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](../consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento das atualizações ou tentar atualizá-lo a pedido através da opção **Atualizar Agora**

## <a name="system-requirements"></a>Requisitos de sistema
O pacote de conteúdos do Azure Search exige que a Análise de Tráfego do Azure Search esteja ativada na conta.

## <a name="troubleshooting"></a>Resolução de problemas
Certifique-se de que o nome da conta de armazenamento seja fornecido corretamente com a chave de acesso completo. O nome da conta de armazenamento deve corresponder à conta configurada com a Análise de Tráfego do Azure Search.

## <a name="next-steps"></a>Próximos passos
[O que é o Power BI?](../fundamentals/power-bi-overview.md)

[Conceitos básicos para designers no serviço Power BI](../fundamentals/service-basic-concepts.md)
