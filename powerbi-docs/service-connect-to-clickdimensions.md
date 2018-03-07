---
title: Ligar ao ClickDimensions com o Power BI
description: ClickDimensions para o Power BI
services: powerbi
documentationcenter: 
author: SarinaJoan
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
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 35b6fd4c2594a29745fe307d804b3f0147d94e43
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="connect-to-clickdimensions-with-power-bi"></a>Ligar ao ClickDimensions com o Power BI
O pacote de conteúdos do ClickDimensions para o Power BI permite que os utilizadores utilizem os dados de marketing do ClickDimensions no Power BI, fornecendo às equipas de gestão mais informações sobre o sucesso dos seus esforços de vendas e marketing. Visualize e analise as interações de e-mail, as visitas na Web e os envios de formulário nos relatórios e dashboards do Power BI.

Ligue-se ao [pacote de conteúdos do ClickDimensions](https://app.powerbi.com/getdata/services/click-dimensions) para o Power BI.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-clickdimensions/getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-clickdimensions/services.png)
3. Selecione **ClickDimensions** \> **Obter**.
   
   ![](media/service-connect-to-clickdimensions/clickdimensions.png)
4. Forneça o local do seu datacenter (EUA, UE ou Austrália) e selecione **Avançar**.
   
   ![](media/service-connect-to-clickdimensions/params.png)
5. Como **Método de Autenticação**, selecione **Básico** \> **Iniciar Sessão**. Quando solicitado, insira as suas credenciais do ClickDimensions. Veja detalhes sobre como [encontrar esses parâmetros](#FindingParams) abaixo
   
    ![](media/service-connect-to-clickdimensions/creds.png)
6. Após a aprovação, o processo de importação é iniciado automaticamente. Quando concluído, um novo dashboard, relatório e modelo aparecerão no Painel de Navegação. Selecione o dashboard para ver os seus dados importados.
   
     ![](media/service-connect-to-clickdimensions/dashboard.png)

**O que se segue?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](power-bi-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento de atualização ou tentar atualizá-lo a pedido através de **Atualizar Agora**

## <a name="system-requirements"></a>Requisitos do sistema
Para se ligar ao pacote de conteúdos do Power BI, é necessário fornecer o datacenter correspondente à sua conta e iniciar a sessão com a sua conta do ClickDimensions. Se não tiver certeza de qual datacenter fornecer, entre em contacto com o administrador.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>A procurar parâmetros
A Chave de Conta pode ser encontrada nas Configurações de CRM \> Configurações do ClickDimensions. Faça uma cópia da Chave de Conta encontrada em Configurações do ClickDimensions e cole-a no campo Nome de utilizador.  

![](media/service-connect-to-clickdimensions/crm.png)  

Faça uma cópia do Token do Power BI encontrado nas Configurações do ClickDimensions e cole-a no campo Palavra-passe. O Token do Power BI pode ser encontrado nas Configurações de CRM \> Configurações do ClickDimensions.  

![](media/service-connect-to-clickdimensions/crm2.png)  

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Obter dados no Power BI](service-get-data.md)

