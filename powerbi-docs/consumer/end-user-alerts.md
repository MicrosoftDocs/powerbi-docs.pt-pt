---
title: 'Tutorial: Definir alertas de dados nos dashboards do serviço Power BI'
description: Neste tutorial, irá aprender a definir alertas para receber notificações quando os dados nos seus dashboards forem alterados para além dos limites que definiu no serviço Microsoft Power BI.
author: mihart
ms.reviewer: mihart
featuredvideoid: removed
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 04/18/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: bb6e874a0ed0c8ce67ff9349f21c5e752ec08b47
ms.sourcegitcommit: c18130ea61e67ba111be870ddb971c6413a4b632
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/09/2020
ms.locfileid: "86162350"
---
# <a name="tutorial-set-alerts-on-power-bi-dashboards"></a>Tutorial: Definir os alertas nos dashboards do Power BI

[!INCLUDE[consumer-appliesto-ynnn](../includes/consumer-appliesto-ynnn.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Defina alertas para receber notificações quando os dados nos seus dashboards forem alterados para cima ou para abaixo dos limites que definiu. Os alertas só podem ser definidos nos mosaicos afixados a partir de elementos visuais de relatório e apenas em medidores, KPIs e cartões. 

*Os consumidores* podem adicionar alertas aos mosaicos nos dashboards que criaram em **A minha área de trabalho**. *Os consumidores* também podem adicionar alertas aos mosaicos nos dashboards que foram partilhados com eles numa [Capacidade premium](end-user-license.md). Se tiver uma licença do Power BI Pro, também pode definir alertas em mosaicos em qualquer outra área de trabalho.
Esta funcionalidade ainda está em desenvolvimento, por isso veja [abaixo a secção Sugestões e resolução de problemas](#tips-and-troubleshooting).

![mosaico, cartão, KPI](media/end-user-alerts/card-gauge-kpi.png)

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

Se não estiver inscrito no Power BI, [inscreva-se para uma avaliação gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) antes de começar.

Este exemplo utiliza mosaico de cartão do dashboard da aplicação de exemplo Vendas e Marketing. Esta aplicação está disponível no [Microsoft AppSource](https://appsource.microsoft.com). Para saber como obter a aplicação, veja [Instalar e utilizar a aplicação de Vendas e Marketing](end-user-app-marketing.md).

1. A partir do medidor do dashboard, KPI ou mosaico do cartão, selecione as reticências.
   
   ![mosaico de cartão](media/end-user-alerts/power-bi-cards.png)
2. Selecione o ícone de campainha ![ícone de alerta](media/end-user-alerts/power-bi-bell-icon.png) ou **Gerir alertas** para adicionar um ou mais alertas a **% Units market share**.

   ![mosaico de cartão com reticências selecionadas](media/end-user-alerts/power-bi-ellipses.png)

   
1. No painel **Gerir alertas**, selecione **+ Adicionar regra de alerta**.  Certifique-se de que o controlo de deslize está definido como **Ativo**e atribua um título ao alerta. Os títulos ajudam a reconhecer facilmente os alertas.
   
   ![Janela Gerir alertas](media/end-user-alerts/power-bi-manage-alert.png)
4. Desloque o ecrã para baixo e introduza os detalhes do alerta.  Neste exemplo, vamos criar um alerta que nos notifica uma vez por dia se a nossa quota de mercado aumentar para 35 ou mais. Os alertas serão apresentados no nosso Centro de notificações. E o Power BI também nos envia uma mensagem de e-mail.
   
   ![Janela Gerir alertas, definição de Limiar](media/end-user-alerts/power-bi-manage-alert-details.png)
5. Selecione **Guardar e fechar**.
 
   > [!NOTE]
   > Os alertas só funcionam em dados que são atualizados. Quando os dados forem atualizados, o Power BI procura alertas definidos para esses dados. Se os dados tiverem atingido um limiar de alerta, será acionado um alerta. 
   > 

## <a name="receiving-alerts"></a>Receber alertas
Quando os dados que estão a ser monitorizados atingirem um dos limiares que definiu, acontecem várias coisas. Em primeiro lugar, o Power BI verifica se passou mais de uma hora ou mais de 24 horas (consoante a opção que selecionou) desde o último alerta enviado. Desde que os dados tenham passado o limiar, receberá um alerta.

Em seguida, o Power BI envia um alerta para o Centro de Notificações e, opcionalmente, por e-mail. Cada alerta contém uma ligação direta para os seus dados. Selecione a ligação para ver o mosaico relevante.  

1. Se tiver definido o alerta para lhe enviar uma mensagem de e-mail, irá encontrar algo deste género na sua Caixa de entrada. Este é um alerta que definimos num dashboard diferente. Este dashboard monitoriza as tarefas concluídas pela equipa de Usabilidade.
   
   ![E-mail de alerta](media/end-user-alerts/power-bi-alert-email.png)
2. O Power BI adiciona uma mensagem ao seu **Centro de notificações** e adiciona um ícone de novo alerta ao mosaico aplicável.
   
   ![Ícone de notificação no serviço Power BI](media/end-user-alerts/power-bi-task-alert.png)
3. Abra o Centro de notificações para ver os detalhes do alerta.
   
    ![ler o Alerta](media/end-user-alerts/power-bi-notification.png)
   
  

## <a name="managing-alerts"></a>Gerir alertas

Existem várias formas de gerir os alteras: No próprio mosaico do dashboard, no menu de Definições do Power BI, num mosaico individual na [aplicação móvel do Power BI no iPhone](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) ou na [aplicação móvel do Power BI para Windows 10](mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

### <a name="from-the-tile-itself"></a>No próprio mosaico

1. Se precisar de alterar ou remover um alerta de um mosaico, volte a abrir a janela **Gerir alertas**, ao selecionar o ícone de campainha ![Ícone de alerta](media/end-user-alerts/power-bi-bell-icon.png). São apresentados todos os alertas que definiu para esse mosaico.
   
    ![Janela Gerir alertas](media/end-user-alerts/power-bi-manage-alerts.png).
2. Para modificar um alerta, selecione a seta para a esquerda do nome do alerta.
   
    ![seta junto ao nome do Alerta](media/end-user-alerts/power-bi-modify-alert.png).
3. Para eliminar um alerta, selecione o recipiente do lixo à direita do nome do alerta.
   
      ![ícone de recipiente do lixo selecionado](media/end-user-alerts/power-bi-alert-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>No menu de definições do Power BI

1. Selecione o ícone de engrenagem na barra de menus do Power BI.
   
    ![ícone de engrenagem](media/end-user-alerts/powerbi-gear-icon.png).
2. Em **Definições**, selecione **Alertas**.
   
    ![Separador Alertas da janela Definições](media/end-user-alerts/power-bi-alert-settings.png)
3. A partir daqui, pode ativar e desativar alertas, abrir a janela **Gerir alertas** para fazer alterações ou eliminar o alerta.

## <a name="tips-and-troubleshooting"></a>Sugestões e resolução de problemas 

* Se não conseguir definir um alerta para um medidor, KPI ou cartão, contacte o administrador do sistema para obter ajuda. Às vezes, os alertas são desativados ou não estão disponíveis no seu dashboard ou para determinados tipos de mosaicos do dashboard.
* Os alertas só funcionam em dados que são atualizados. Não funcionam em dados estáticos. Os exemplos fornecidos pela Microsoft são, em grande parte, estáticos. 
* A capacidade de receber e ver conteúdos partilhados exige uma licença Power BI Pro ou Premium. Para obter mais informações, leia [Qual é a minha licença?](end-user-license.md).
* Os alertas podem ser definidos em elementos visuais criados a partir de fluxos de conjuntos de dados que são afixados de um relatório a um dashboard. Os alertas não podem ser definidos em fluxos de mosaicos criados diretamente no dashboard com **Adicionar mosaico** > **Dados de transmissão em fluxo personalizados**.


## <a name="clean-up-resources"></a>Limpar recursos
As instruções para eliminar alertas são explicadas acima. Em suma, selecione o ícone de engrenagem na barra de menus do Power BI. Em **Configurações** selecione **Alertas** e elimine o alerta.

> [!div class="nextstepaction"]
> [Definir alertas de dados num dispositivo móvel](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)


