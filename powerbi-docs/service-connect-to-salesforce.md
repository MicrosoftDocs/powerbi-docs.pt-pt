---
title: Ligar-se ao Salesforce com o Power BI
description: Salesforce para o Power BI
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
ms.openlocfilehash: 6998f273a7e40cae2c7a50f043f79eec540b4789
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-salesforce-with-power-bi"></a>Ligar-se ao Salesforce com o Power BI
Com o Power BI, pode ligar-se facilmente à sua conta do Salesforce.com. A criação dessa ligação devolver os dados, além de fornecer automaticamente um dashboard e relatórios relacionados com base nesses dados.

Ligue-se ao [pacote de conteúdos do Salesforce](https://app.powerbi.com/getdata/services/salesforce) para o Power BI ou leia mais sobre a [integração do Salesforce](https://powerbi.microsoft.com/integrations/salesforce) com o Power BI.

## <a name="how-to-connect"></a>Como se Ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-salesforce/pbi_getdata.png) 
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-salesforce/pbi_getservices.png) 
3. Clique em **Salesforce** e selecione **Obter**.  
   
   ![](media/service-connect-to-salesforce/salesforce.png)
4. Selecione **Iniciar Sessão** para iniciar o fluxo de início de sessão.
   
    ![](media/service-connect-to-salesforce/dialog.png)
5. Quando pedido, insira as suas credenciais do Salesforce. Clique em **Permitir** para que o Power BI possa aceder às suas informações e dados básicos do Salesforce.
   
   ![](media/service-connect-to-salesforce/sf_authorize.png)
6. Configure o que deseja importar para o Power BI com a opção de lista pendente:
   
   * **Dashboard**
     
     Selecione um dashboard predefinido com base numa persona (como **Gestor de Vendas**). Esses dashboards trazem um conjunto específico de dados standard do Salesforce e não incluem nenhum campo personalizado.
     
     ![](media/service-connect-to-salesforce/pbi_salesforcechooserole.png)
   * **Relatórios**
     
     Selecione um ou mais relatórios personalizados da conta do Salesforce. Esses relatórios correspondem às visualizações no Salesforce, podendo incluir dados de objetos ou campos personalizados.
     
     ![](media/service-connect-to-salesforce/pbi_salesforcereports.png)
     
     Se não vir quaisquer relatórios, adicione ou crie-os em sua conta do Salesforce e tente ligar-se novamente.
7. Clique em **Conectar** para iniciar o processo de importação. Durante a importação, verá uma notificação a mostrar que a importação está em andamento. Depois de concluída a importação, verá um dashboard, relatório e conjunto de dados para os dados do Salesforce listados no painel de navegação esquerdo.
   
   ![](media/service-connect-to-salesforce/pbi_getdatasalesforcedash.png)

Pode alterar esse dashboard para mostrar os dados de qualquer modo que desejar. É possível fazer perguntas com Perguntas e Respostas ou clicar num bloco para [abrir o relatório subjacente](service-dashboard-tiles.md) e [alterar os blocos](service-dashboard-edit-tile.md) no dashboard.

**O que se segue?**

* Tente [fazer uma pergunta na caixa de Perguntas e Respostas](service-q-and-a.md) na parte superior do dashboard
* [Alterar os blocos](service-dashboard-edit-tile.md) no dashboard
* [Selecionar um bloco](service-dashboard-tiles.md) para abrir o relatório subjacente
* Enquanto o seu conjunto de dados vai ser agendado para ser atualizado diariamente, pode alterar o agendamento de atualização ou tentar atualizá-lo sob pedido em **Atualizar Agora**

## <a name="system-requirements"></a>Requisitos do sistema
* Estar conectado a uma conta do Salesforce que tenha acesso ativado à API
* Permissão concedida à aplicação Power BI durante o início de sessão
* A conta ter chamadas à API suficientes disponíveis para efetuar pull dos dados e atualizá-los
* Um token de autenticação válido é necessário para a atualização. Certifique-se de que importou no máximo cinco conjuntos de dados do Salesforce, já que o Salesforce tem um limite de cinco tokens de autenticação por aplicação

## <a name="troubleshooting"></a>Resolução de problemas
Se encontrar algum erro, reveja os requisitos acima. Observe também que não há suporte para a capacidade de início de sessão num domínio personalizado de área atualmente restrita.

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Obter Dados](service-get-data.md)
