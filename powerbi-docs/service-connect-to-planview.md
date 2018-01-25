---
title: Ligar ao Planview Enterprise com o Power BI
description: Planview Enterprise para o Power BI
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
ms.openlocfilehash: cef43b20a6c7fe91ef35567caa511d125c536bf5
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/19/2018
---
# <a name="connect-to-planview-enterprise-with-power-bi"></a>Ligar ao Planview Enterprise com o Power BI
Com o pacote de conteúdos do Planview Enterprise, pode visualizar os seus dados de gestão de trabalho e recursos de formas totalmente novas diretamente no Power BI. Utilize as suas credenciais de início de sessão do Planview Enterprise para visualizar interativamente os seus gastos de investimento de portfólio, perceber em que pontos está acima e abaixo do orçamento e saber em que medida os seus projetos se alinham com as prioridades estratégicas empresariais. Também pode expandir o dashboard e os relatórios integrados para obter as informações que são mais importantes para si.

Ligue-se ao [pacote de conteúdos do Planview Enterprise no Power BI](https://app.powerbi.com/getdata/services/planview-enterprise)

>[!NOTE]
>Para importar dados do Planview Enterprise para o Power BI, tem de ser um utilizador do Planview Enterprise com a funcionalidade Visualizador de Portal de Relatório ativada na sua função. Veja os requisitos adicionais abaixo.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
    ![](media/service-connect-to-planview/get.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
    ![](media/service-connect-to-planview/services.png)
3. Na página do Power BI, selecione **Planview Enterprise** e, em seguida, selecione **Obter**:  
    ![](media/service-connect-to-planview/planview.png)
4. Na caixa de texto URL do Planview Enterprise, introduza o URL do servidor do Planview Enterprise que deseja usar. Na caixa de texto Planview Enterprise Database, introduza o nome da base de dados do Planview Enterprise e clique em Seguinte.  
    ![](media/service-connect-to-planview/params.png)
5. Na lista Método de Autenticação, selecione **Básico** se essa opção ainda não estiver selecionada. Introduza o **Nome de utilizador** e a **Palavra-passe** da sua conta e selecione **Iniciar Sessão**.  
   ![](media/service-connect-to-planview/creds.png)
6. No painel esquerdo, selecione Planview Enterprise na lista de dashboards.  
     O Power BI importa os dados do Planview Enterprise para o dashboard. Tenha em atenção que os dados podem levar algum tempo a carregar.  
    ![](media/service-connect-to-planview/dashboard.png)

**E agora?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](power-bi-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento de atualização ou tentar atualizá-lo a pedido através de **Atualizar Agora**

## <a name="system-requirements"></a>Requisitos de sistema
Para importar dados do Planview Enterprise para o Power BI, tem de ser um utilizador do Planview Enterprise com a funcionalidade Visualizador de Portal de Relatório ativada na sua função. Veja os requisitos adicionais abaixo.

Este procedimento pressupõe que já entrou na home page do Microsoft Power BI com uma conta do Power BI. Se não tiver uma conta do Power BI, crie uma nova conta gratuita do Power BI na home page do Power BI e clique em Obter Dados.

## <a name="next-steps"></a>Próximos passos:

[Introdução ao Power BI](service-get-started.md)

[Obter Dados para o Power BI](service-get-data.md)