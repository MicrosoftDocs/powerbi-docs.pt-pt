---
title: Ligue-se a appFigures com o Power BI
description: appFigures para o Power BI
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
ms.openlocfilehash: 502135583f4d62144a2a2bdb908724c4f8e6b579
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-appfigures-with-power-bi"></a>Ligue-se a appFigures com o Power BI
É fácil acompanhar as estatísticas importantes sobre as suas aplicações com o Power BI e com o pacote de conteúdos do appFigures. O Power BI recupera os seus dados, incluindo vendas de aplicações, downloads e estatísticas de anúncios, e cria um dashboard predefinido e relatórios relacionados com base nesses dados.

Ligue-se ao [pacote de conteúdo do appFigures](https://app.powerbi.com/getdata/services/appfigures) ou leia mais sobre a [integração do appFigures](https://powerbi.microsoft.com/integrations/appfigures) com o Power BI.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-appfigures/pbi_getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-appfigures/pbi_getservices.png)
3. Selecione **appFigures** \> **Obter**.
   
   ![](media/service-connect-to-appfigures/appfigures.png)
4. Como **Método de Autenticação**, selecione **oAuth2** \> **Iniciar Sessão**. Quando solicitado, insira as suas credenciais do appFigures e siga o processo de autenticação correspondente.
   
   Na primeira vez que se ligar, o Power BI solicita o acesso de apenas leitura à sua conta. Selecione **Permitir** para iniciar o processo de importação. Isso pode levar alguns minutos, dependendo do volume de dados na sua conta.
   
   ![](media/service-connect-to-appfigures/appfiguresdoc_06.png)
5. Após o Power BI importar os dados, verá novos elementos (dashboard, relatório e conjunto de dados) no painel de navegação esquerdo. Os itens novos são marcados com um asterisco amarelo \*:
   
    ![](media/service-connect-to-appfigures/pbi_appfigures3.png)
6. Selecione o dashboard appFigures. Esse é o dashboard predefinido criado pelo Power BI para exibir seus dados. Pode alterar este dashboard para ver os seus dados de qualquer modo que queira.
   
    ![](media/service-connect-to-appfigures/appfiguresdoc_01.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de Perguntas e Respostas](service-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento de atualização ou tentar atualizá-lo a pedido através de **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
Os dados a seguir estão disponíveis no appFigures no Power BI.

| **Nome da Tabela** | **Descrição** |
| --- | --- |
| Países |Esta tabela fornece informações de nome de país. |
| Datas |Esta tabela contém datas desde hoje até a mais antiga PublishDate (data de publicação) das aplicações que estão Ativas e Visíveis na sua conta do appFigures. |
| Eventos |Esta tabela contém informações de download, vendas e anúncios para cada aplicação, por país, que são fornecidas diariamente. Note que tanto as informações de compras na aplicação quanto as da própria aplicação estão todas nesta única tabela - pode utilizar a coluna <strong>Tipo</strong> para diferenciá-las. |
| Na aplicação |Esta tabela contém dados sobre os diferentes tipos de compras na aplicação que estão associadas com as aplicações Ativas e Visíveis na sua conta do appFigures. |
| Produtos |Esta tabela contém dados sobre as diferentes aplicações que estão Ativas e Visíveis na sua conta do appFigures. |

## <a name="troubleshooting"></a>Resolução de problemas
Se os dados de algumas das aplicações não estão a aparecer no Power BI, certifique-se de que essas aplicações estão Visíveis e Ativas no separador **aplicações** do site do appFigures.

![](media/service-connect-to-appfigures/appfiguresdoc_11.png)

## <a name="next-steps"></a>Próximos passos
* [Introdução ao Power BI](service-get-started.md)
* [Obter dados no Power BI](service-get-data.md)

