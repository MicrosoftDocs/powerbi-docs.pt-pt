---
title: 'Tutorial: Definir alertas de dados nos dashboards do serviço Power BI'
description: Neste tutorial, irá aprender a definir alertas para receber notificações quando os dados nos seus dashboards forem alterados para além dos limites que definiu no serviço Microsoft Power BI.
author: mihart
ms.reviewer: mihart
featuredvideoid: removed
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 08/05/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 22d9baaf50ce32c4a9d3644cff455b474bdd1549
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/29/2020
ms.locfileid: "91525340"
---
# <a name="tutorial-set-alerts-on-power-bi-dashboards"></a>Tutorial: Definir os alertas nos dashboards do Power BI

[!INCLUDE[consumer-appliesto-yynn](../includes/consumer-appliesto-yynn.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Defina alertas no serviço Power BI para receber notificações quando os dados num dashboard forem alterados para cima ou para abaixo dos limites que definiu. Os alertas só podem ser definidos nos mosaicos afixados a partir de elementos visuais de relatório e apenas em medidores, KPIs e cartões. 

![mosaico, cartão, KPI](media/end-user-alerts/card-gauge-kpi.png)

Pode criar alertas nos dashboards:
- que criou e guardou em **A minha área de trabalho**;
- que foram partilhados consigo numa [capacidade Premium](end-user-license.md); 
- em qualquer área de trabalho a que possa aceder, se tiver uma licença do Power BI Pro.    

Os alertas só funcionam em dados que são atualizados. Quando os dados forem atualizados, o Power BI procura alertas definidos para esses dados. Se os dados tiverem atingido um limiar de alerta, será acionado um alerta. 

Esta funcionalidade ainda está em desenvolvimento, por isso veja [abaixo a secção Sugestões e resolução de problemas](#tips-and-troubleshooting).



Só o utilizador pode ver os alertas que definir, mesmo que partilhe o dashboard. Os alertas de dados são totalmente sincronizados entre plataformas; defina e veja alertas de dados [nas aplicações móveis do Power BI](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) e no serviço Power BI. 

> [!WARNING]
> Esses alertas fornecem informações sobre os seus dados. Se vir os dados do Power BI num dispositivo móvel e esse dispositivo for roubado, recomendamos que utilize o serviço Power BI para desativar todos os alertas.
> 

Este tutorial abrange o seguinte.
> [!div class="checklist"]
> * Quem pode definir alertas
> * Quais os elementos visuais que suportam alertas
> * Quem pode ver os meus alertas
> * Os alertas funcionam no Power BI Desktop e no Mobile
> * Como criar um alerta
> * Onde vou receber os meus alertas

## <a name="prerequisites"></a>Pré-requisitos

Se não estiver inscrito no Power BI, [inscreva-se para uma avaliação gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) antes de começar.

1. Este exemplo utiliza um mosaico de cartão do dashboard do exemplo Vendas e Marketing. Abra o serviço Power BI (app.powerbi.com), inicie sessão e abra **A Minha Área de Trabalho**.    
    ![Abrir A Minha Área de Trabalho](media//end-user-alerts/power-bi-my-workspace.png)

2. No canto inferior esquerdo, selecione **Obter dados**.

    ![Selecionar Obter Dados](media//end-user-alerts/power-bi-get-data.png)

3. Na página Obter dados apresentada, selecione **Exemplos**.

4. Selecione o Exemplo de Vendas e Marketing e, em seguida, escolha **Ligar**.

    ![Transferir o exemplo de Vendas e Marketing](media//end-user-alerts/power-bi-sample.png)

5. Depois de o Power BI se ligar ao exemplo, selecione **Ir para o dashboard** na caixa de diálogo apresentada.     
    ![Abrir o exemplo de Vendas e Marketing](media//end-user-alerts/power-bi-go-to-dashboard.png)

## <a name="add-an-alert-to-a-dashboard-tile"></a>Adicionar um alerta a um mosaico do dashboard

1. A partir do medidor do dashboard, KPI ou mosaico do cartão, selecione as reticências.
   
   ![mosaico de cartão](media/end-user-alerts/power-bi-card.png)

2. Selecione o ícone de alerta ![Ícone de alerta](media/end-user-alerts/power-bi-alert-icon.png) ou **Gerir alertas** para adicionar um ou mais alertas ao cartão **Quota de mercado**.

   ![mosaico de cartão com reticências selecionadas](media/end-user-alerts/power-bi-manage.png)

   
1. No painel **Gerir alertas**, selecione **+ Adicionar regra de alerta**.  Certifique-se de que o controlo de deslize está definido como **Ativo**e atribua um título ao alerta. Os títulos ajudam a reconhecer facilmente os alertas.
   
   ![Janela Adicionar regra de alerta](media/end-user-alerts/power-bi-alert-manage.png)
4. Desloque o ecrã para baixo e introduza os detalhes do alerta.  Neste exemplo, vamos criar um alerta que nos notifica uma vez por dia se a nossa quota de mercado aumentar para 40 ou mais. Os alertas serão apresentados no nosso [Centro de notificações](end-user-notification-center.md). E o Power BI também nos envia uma mensagem de e-mail.
   
   ![Janela Gerir alertas, definição de Limiar](media/end-user-alerts/power-bi-manage-alert-detail.png)

5. Selecione **Guardar e fechar**.
 


   > 

## <a name="receiving-alerts"></a>Receber alertas
Quando os dados que estão a ser monitorizados atingirem um dos limiares que definiu, acontecem várias coisas. Em primeiro lugar, o Power BI verifica se passou mais de uma hora ou mais de 24 horas (consoante a opção que selecionou) desde o último alerta enviado. Desde que os dados tenham passado o limiar, receberá um alerta.

Em seguida, o Power BI envia um alerta para o Centro de Notificações e, opcionalmente, por e-mail. Cada alerta contém uma ligação direta para os seus dados. Selecione a ligação para ver o mosaico relevante.  

1. Se tiver definido o alerta para lhe enviar uma mensagem de e-mail, irá encontrar algo deste género na sua Caixa de entrada. Este é um alerta que definimos para o cartão **Sentimento**.
   
   ![E-mail de alerta](media/end-user-alerts/power-bi-email.png)
2. O Power BI também adiciona uma mensagem ao seu **Centro de notificações**.
   
   ![Ícone de notificação no serviço Power BI](media/end-user-alerts/power-bi-task.png)
3. Abra o Centro de notificações para ver os detalhes do alerta.
   
    ![ler o Alerta](media/end-user-alerts/power-bi-notifications.png)
   
  

## <a name="managing-alerts"></a>Gerir alertas

Existem várias formas de gerir os alertas: no próprio mosaico do dashboard, no menu de Definições do Power BI, num mosaico individual na [aplicação móvel do Power BI no iPhone](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) ou na [aplicação móvel do Power BI para Windows 10](mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

### <a name="from-the-tile-itself"></a>No próprio mosaico

1. Se precisar de alterar ou remover um alerta de um mosaico, volte a abrir a janela **Gerir alertas** ao selecionar o ícone de alerta ![Ícone de alerta](media/end-user-alerts/power-bi-alert-icon.png). São apresentados todos os alertas que definiu para esse mosaico.
   
    ![Janela Gerir alertas](media/end-user-alerts/power-bi-manage-alert.png).
2. Para modificar um alerta, selecione a seta para a esquerda do nome do alerta.
   
    ![seta junto ao nome do Alerta](media/end-user-alerts/power-bi-alert-modify.png).
3. Para eliminar um alerta, selecione o recipiente do lixo à direita do nome do alerta.
   
      ![ícone de recipiente do lixo selecionado](media/end-user-alerts/power-bi-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>No menu de definições do Power BI

1. Selecione o ícone de engrenagem na barra de menus do Power BI.
   
    ![ícone de engrenagem](media/end-user-alerts/power-bi-gear-icon.png).
2. Em **Definições**, selecione **Alertas**.
   
    ![Separador Alertas da janela Definições](media/end-user-alerts/power-bi-settings.png)
3. A partir daqui, pode ativar e desativar alertas, abrir a janela **Gerir alertas** para fazer alterações ou eliminar o alerta.

## <a name="tips-and-troubleshooting"></a>Sugestões e resolução de problemas 

* Se não conseguir definir um alerta para um medidor, um KPI ou um cartão, contacte o administrador do Power BI ou o suporte técnico de TI para obter ajuda. Às vezes, os alertas são desativados ou não estão disponíveis no seu dashboard ou para determinados tipos de mosaicos do dashboard.
* Os alertas só funcionam em dados que são atualizados. Não funcionam em dados estáticos. Os exemplos fornecidos pela Microsoft são, em grande parte, estáticos. 
* A capacidade de receber e ver conteúdos partilhados exige uma licença Power BI Pro ou Premium. Para obter mais informações, leia [Qual é a minha licença?](end-user-license.md).
* Os alertas podem ser definidos em elementos visuais criados a partir de fluxos de conjuntos de dados que são afixados de um relatório a um dashboard. Os alertas não podem ser definidos em fluxos de mosaicos criados diretamente no dashboard com **Adicionar mosaico** > **Dados de transmissão em fluxo personalizados**.


## <a name="clean-up-resources"></a>Limpar recursos
As instruções para eliminar alertas são explicadas acima. Em suma, selecione o ícone de engrenagem na barra de menus do Power BI. Em **Configurações** selecione **Alertas** e elimine o alerta.

> [!div class="nextstepaction"]
> [Definir alertas de dados num dispositivo móvel](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)


