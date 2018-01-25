---
title: Ligar ao ServiceNow com o Power BI
description: ServiceNow para o Power BI
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
ms.openlocfilehash: 662b5e094a38aafad9a87593b9c5b797e2db7870
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/19/2018
---
# <a name="connect-to-servicenow-with-power-bi-for-incident-reporting"></a>Ligar ao ServiceNow com o Power BI para relatórios de incidentes
O ServiceNow oferece vários produtos e soluções, incluindo gestão de empresas, operações e TI para melhorar o seu negócio. Este pacote de conteúdos inclui vários relatórios e informações sobre os seus incidentes abertos, resolvidos recentemente e fechados recentemente.  

Ligue ao pacote de conteúdos do Power BI para obter os [Incidentes do ServiceNow](https://app.powerbi.com/getdata/services/servicenow).

## <a name="how-to-connect"></a>Como ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-servicenow/pbi_getdata.png) 
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-servicenow/pbi_getservices.png) 
3. Selecione **Incidentes do ServiceNow** \>  **Obter**.
   
   ![](media/service-connect-to-servicenow/connect.png)
4. Forneça o URL da sua instância do ServiceNow e o intervalo de dias/registos a obter. Tenha em atenção que a importação irá parar assim que um limite for atingido.
   
   ![](media/service-connect-to-servicenow/params.png)
5. Quando solicitado, introduza as suas credenciais **Básicas** do ServiceNow. Tenha em atenção que o início de sessão único não é suportado atualmente. Pode obter mais detalhes sobre os requisitos de sistema abaixo.
   
   ![](media/service-connect-to-servicenow/creds.png)
6. Quando o fluxo de início de sessão estiver concluído, o processo de importação será iniciado. Quando concluído, um novo dashboard, relatório e modelo aparecem no Painel de Navegação. Selecione o dashboard para ver os seus dados importados.
   
    ![](media/service-connect-to-servicenow/dashboard.png)

**O que se segue?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](power-bi-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento de atualização ou tentar atualizá-lo a pedido através de **Atualizar Agora**

## <a name="system-requirements"></a>Requisitos de sistema
Para ligar, irá precisar de:  

* Uma conta que possa aceder a yourorganization.service-now.com, com autenticação básica (o Início de Sessão Único não é suportado nesta versão)  
* A conta deve ter a função rest_service e acesso de leitura à tabela de incidentes  

## <a name="troubleshooting"></a>Resolução de Problemas
Se estiver a obter um erro de credenciais durante o carregamento, consulte os requisitos de acesso acima. Se tiver as permissões corretas e continuar a ter problemas, consulte o seu administrador do ServiceNow para garantir que tem quaisquer permissões adicionais que possam ser necessárias para a instância personalizada.

Se estiver a ver tempos de carregamento longos, reveja o número de incidentes e o número de dias que especificou durante a ligação, e considere a respetiva redução.

## <a name="next-steps"></a>Passos seguintes
[Introdução ao Power BI](service-get-started.md)

[Power BI - Conceitos Básicos](service-basic-concepts.md)

