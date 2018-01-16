---
title: "Definir alertas de dados no serviço Power BI"
description: "Aprenda a definir alertas para receber notificações quando os dados nos seus dashboards forem alterados para além dos limites que definiu no serviço Microsoft Power BI."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: JbL2-HJ8clE
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/21/2017
ms.author: mihart
ms.openlocfilehash: 2a4134e1a06933927bd2c5453cd8e7a79394c384
ms.sourcegitcommit: 6ea8291cbfcb7847a8d7bc4e2b6abce7eddcd0ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/21/2017
---
# <a name="data-alerts-in-power-bi-service"></a>Alertas de dados no serviço Power BI
Defina alertas para receber notificações quando os dados nos seus dashboards forem alterados para além dos limites que definiu. 

Os alertas só podem ser definidos nos mosaicos afixados a partir de elementos visuais de relatório e apenas em medidores, KPIs e cartões. Os alertas podem ser definidos em elementos visuais criados a partir de conjuntos de dados de transmissão em fluxo que foram afixados a partir de um relatório a um dashboard, mas não podem ser definidos em mosaicos de transmissão em fluxo criados diretamente no dashboard com a opção **Adicionar mosaico** > **Dados de transmissão em fluxo personalizados**. 

Só o utilizador pode ver os alertas que definir, mesmo que partilhe o dashboard. Os alertas de dados são totalmente sincronizados entre plataformas; defina e veja alertas de dados [nas aplicações móveis do Power BI](mobile-set-data-alerts-in-the-mobile-apps.md) e no serviço Power BI. Não estão disponíveis para o Power BI Desktop. Os alertas podem até ser [automatizados e integrados com o Microsoft Flow](https://flow.microsoft.com) - [experimente](service-flow-integration.md).

![](media/service-set-data-alerts/powerbi-alert-types-new.png)

> [!WARNING]
> As notificações de alertas com base em dados dão-lhe informações sobre os seus dados. Se vir os dados do Power BI num dispositivo móvel e esse dispositivo for roubado, recomendamos que utilize o serviço Power BI para desativar todas as regras de alerta com base em dados.
> 
> 

## <a name="set-data-alerts-in-power-bi-service"></a>Definir alertas de dados no serviço Power BI
Veja a Amanda a adicionar alguns alertas a mosaicos no seu dashboard. Em seguida, siga as instruções passo-a-passo abaixo do vídeo para experimentar.

<iframe width="560" height="315" src="https://www.youtube.com/embed/JbL2-HJ8clE" frameborder="0" allowfullscreen></iframe>

Este exemplo utiliza um mosaico de cartão do dashboard de exemplo de Análise de Revenda.

1. Inicie um dashboard. A partir do medidor do dashboard, KPI ou mosaico do cartão, selecione as reticências.
   
   ![](media/service-set-data-alerts/powerbi-card.png)
2. Selecione o ícone de campainha ![](media/service-set-data-alerts/power-bi-bell-icon.png) para adicionar um ou mais alertas a **Total de lojas**.
   
1. Para começar, selecione **+ Adicionar regra de alerta**, certifique-se de que o controlo de deslize está definido como **Ativo** e atribua um título ao alerta. Os títulos ajudam a reconhecer facilmente os alertas.
   
   ![](media/service-set-data-alerts/powerbi-alert-title.png)
4. Desloque o ecrã para baixo e introduza os detalhes do alerta.  Neste exemplo, vamos criar um alerta que nos notifica uma vez por dia se o número total de lojas ficar acima de 100. Os alertas serão apresentados no nosso Centro de notificações. E o Power BI também nos envia uma mensagem de e-mail.
   
   ![](media/service-set-data-alerts/power-bi-set-alert-details.png)
5. Selecione **Guardar**.

## <a name="receiving-alerts"></a>Receber alertas
Quando os dados que estão a ser monitorizados atingirem um dos limiares que definiu, acontecerão várias coisas. Em primeiro lugar, o Power BI verifica se passou mais de uma hora ou mais de 24 horas (consoante a opção que selecionou) desde o último alerta enviado. Desde que os dados tenham passado o limiar, receberá um alerta.

Em seguida, o Power BI envia um alerta para o Centro de notificação e, opcionalmente, por e-mail. Cada alerta contém uma ligação direta para os seus dados. Selecione a ligação para ver o mosaico relevante, onde pode explorar, partilha e obter mais informações.  

1. Se tiver definido o alerta para lhe enviar uma mensagem de e-mail, irá encontrar algo deste género na sua Caixa de entrada.
   
   ![](media/service-set-data-alerts/powerbi-alerts-email.png)
2. O Power BI adiciona uma mensagem ao seu **Centro de notificações** e adiciona um ícone de novo alerta ao mosaico aplicável.
   
   ![](media/service-set-data-alerts/powerbi-alert-notifications.png)
3. Abra o Centro de notificações para ver os detalhes do alerta.
   
    ![](media/service-set-data-alerts/powerbi-alert-notfication.png)
   
   > [!NOTE]
   > Os alertas só funcionam em dados que são atualizados. Quando os dados forem atualizados, o Power BI procura alertas definidos para esses dados. Se os dados tiverem atingido um limiar de alerta, será acionado um alerta.
   > 
   > 

## <a name="managing-alerts"></a>Gerir alertas
Existem várias formas de gerir os alertas: no próprio mosaico do dashboard, no menu de Definições do Power BI, num mosaico individual na [aplicação móvel do Power BI no iPhone](mobile-set-data-alerts-in-the-mobile-apps.md) ou na [aplicação móvel do Power BI para Windows 10](mobile-set-data-alerts-in-the-mobile-apps.md).

### <a name="from-the-tile-itself"></a>No próprio mosaico
1. Se precisar de alterar ou remover um alerta para um mosaico, volte a abrir a janela **Gerir alertas**, selecionando o ícone de campainha ![](media/service-set-data-alerts/power-bi-bell-icon.png). São apresentados todos os alertas que definiu para esse mosaico.
   
    ![](media/service-set-data-alerts/powerbi-see-alerts.png).
2. Para modificar um alerta, selecione a seta para a esquerda do nome do alerta.
   
    ![](media/service-set-data-alerts/powerbi-see-alerts-arrow.png).
3. Para eliminar um alerta, selecione o recipiente do lixo à direita do nome do alerta.
   
      ![](media/service-set-data-alerts/powerbi-see-alerts-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>No menu de definições do Power BI
1. Selecione o ícone de engrenagem na barra de menus do Power BI.
   
    ![](media/service-set-data-alerts/powerbi-gear-icon.png).
2. Em **Definições**, selecione **Alertas**.
   
    ![](media/service-set-data-alerts/powerbi-alert-settings.png)
3. A partir daqui, pode ativar e desativar alertas, abrir a janela **Gerir alertas** para fazer alterações ou eliminar o alerta.

## <a name="tips-and-troubleshooting"></a>Sugestões e resolução de problemas
* Atualmente, os alertas não são suportados para mosaicos do Bing ou mosaicos de cartões com medidas de data/hora.
* Os alertas só funcionam com tipos de dados numéricos.
* Os alertas só funcionam em dados que são atualizados. Não funcionam em dados estáticos.
* Os alertas só funcionam em conjuntos de dados de transmissão em fluxo se criar um elemento visual de relatório de KPI/cartão/medidor e, em seguida, afixar esse elemento visual ao dashboard.

## <a name="next-steps"></a>Passos seguintes
[Criar um Microsoft Flow que inclui um alerta de dados](service-flow-integration.md)    
[Definir alertas de dados num dispositivo móvel](mobile-set-data-alerts-in-the-mobile-apps.md)    
[Introdução ao Power BI](service-get-started.md)    
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

