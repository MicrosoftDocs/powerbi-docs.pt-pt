---
title: Ligar ao ServiceNow com o Power BI
description: ServiceNow para o Power BI
author: KesemSharabi
ms.author: sarinas
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
LocalizationGroup: Connect to services
ms.openlocfilehash: 9fc0360ccf2e036cca1c68cf21bb538b30adf7e6
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/23/2019
ms.locfileid: "71191009"
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

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento das atualizações ou tentar atualizá-lo a pedido através da opção **Atualizar Agora**

## <a name="system-requirements"></a>Requisitos de sistema
Para ligar, irá precisar de:  

* Uma conta que possa aceder a yourorganization.service-now.com, com autenticação básica (o Início de Sessão Único não é suportado nesta versão)  
* A conta deve ter a função rest_service e acesso de leitura à tabela de incidentes  

## <a name="troubleshooting"></a>Resolução de Problemas
Se estiver a obter um erro de credenciais durante o carregamento, consulte os requisitos de acesso acima. Se tiver as permissões corretas e continuar a ter problemas, consulte o seu administrador do ServiceNow para garantir que tem quaisquer permissões adicionais que possam ser necessárias para a instância personalizada.

Se estiver a ver tempos de carregamento longos, reveja o número de incidentes e o número de dias que especificou durante a ligação, e considere a respetiva redução.

## <a name="next-steps"></a>Próximos passos
[O que é o Power BI?](power-bi-overview.md)

[Conceitos básicos para designers no serviço Power BI](service-basic-concepts.md)

