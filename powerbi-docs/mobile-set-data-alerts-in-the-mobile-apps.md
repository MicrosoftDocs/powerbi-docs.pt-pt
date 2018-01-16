---
title: "Definir alertas de dados nas aplicações móveis do Power BI"
description: "Saiba como definir alertas de dados na aplicação móvel do Power BI para notificá-lo quando os dados num dashboard são alterados para além dos limites que definiu."
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/18/2017
ms.author: maggies
ms.openlocfilehash: c6406a6d1ad4269352ce8421b91f4304fd35c78f
ms.sourcegitcommit: ea247cb3cfc1cac076d4b076c1ad8e2fc37e15a1
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/19/2017
---
# <a name="set-data-alerts-in-the-power-bi-mobile-apps"></a>Definir alertas de dados nas aplicações móveis do Power BI
Aplica-se a:

| ![iPhone](media/mobile-set-data-alerts-in-the-mobile-apps/iphone-logo-50-px.png) | ![iPad](media/mobile-set-data-alerts-in-the-mobile-apps/ipad-logo-50-px.png) | ![Telemóvel Android](media/mobile-set-data-alerts-in-the-mobile-apps/android-phone-logo-50-px.png) | ![Tablet Android](media/mobile-set-data-alerts-in-the-mobile-apps/android-tablet-logo-50-px.png) | ![Tablet Android](media/mobile-set-data-alerts-in-the-mobile-apps/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhones |iPads |Telemóveis Android |Tablets Android |Dispositivos Windows 10 |

Pode definir alertas nos dashboards nas aplicações móveis do Power BI e no serviço Power BI. Os alertas notificam-no quando os dados num mosaico forem alterados para além dos limites que definiu. Os alertas são compatíveis com mosaicos com um único número, como cartões e medidores, mas não com a transmissão de dados. Pode definir alertas de dados no seu dispositivo móvel e vê-los no serviço Power BI e vice-versa. Só pode ver os alertas de dados que definir, mesmo que partilhe um dashboard ou instantâneo de um mosaico.

Pode definir alertas em mosaicos se tiver uma licença do Power BI Pro ou se tiver uma licença do Power BI gratuita e se o dashboard partilhado estiver dentro da capacidade de Premium. 

> [!WARNING]
> As notificações de alertas com base em dados dão-lhe informações sobre os seus dados. Se o seu dispositivo for roubado, recomendamos que aceda ao serviço Power BI para desativar todas as regras de alertas baseados em dados. 
> 
> Saiba mais sobre [gerir os alertas de dados no serviço Power BI](service-set-data-alerts.md).
> 
> 

## <a name="data-alerts-on-an-iphone-or-ipad"></a>Alertas de dados num iPhone ou iPad
### <a name="set-an-alert-on-an-iphone-or-ipad"></a>Definir um alerta num iPhone ou iPad
1. Toque num número ou mosaico de medidor no dashboard para o abrir no modo de detalhe.  
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-card-visual.png)
2. Toque no ícone de sino ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-alert-icon.png) para adicionar um alerta.  
3. Toque em **Adicionar regra de alerta**.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-add-alert-rule.png)
4. Opte por receber alertas acima ou abaixo de um determinado valor e, em seguida, defina o valor.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-set-alert-threshold.png)
5. Decida se pretende receber alertas horários ou diários e se também pretende receber um e-mail ao receber o alerta.
   
   > [!NOTE]
   > Não receberá alertas todas as horas ou dias, a menos que os dados tenham efetivamente sido atualizados nesse período.
   > 
   > 
6. Também pode alterar o título do alerta.
7. Toque em **Guardar**.
8. Um único mosaico pode ter alertas para valores acima e abaixo dos limiares. Em **Gerir alertas**, toque em **Adicionar regra de alerta**.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-add-another-alert-rule.png)

### <a name="manage-alerts-on-your-iphone-or-ipad"></a>Gerir alertas no seu iPhone ou iPad
Pode gerir alertas individuais no seu dispositivo móvel ou [gerir todos os seus alertas no serviço Power BI](service-set-data-alerts.md).

1. Num dashboard, toque num número ou mosaico de medidor que tenha um alerta.  
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-card-visual.png)
2. Toque no ícone do sino ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-has-alert-icon.png).  
3. Toque no nome do alerta para editá-lo, toque no controlo de deslize para desativar os alertas de e-mails ou toque na lata do lixo para eliminar o alerta.
   
    ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-edit-delete-alert.png)

## <a name="data-alerts-on-an-android-device"></a>Alertas de dados num dispositivo Android
### <a name="set-an-alert-on-an-android-device"></a>Definir um alerta num dispositivo Android
1. Num dashboard do Power BI, toque num número ou mosaico de medidor para abri-lo.  
2. Toque no ícone de sino ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-alert-icon.png) para adicionar um alerta.  
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-tap-alert.png)
3. Toque no ícone de adição (+).
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-plus-alert.png)
4. Opte por receber alertas acima ou abaixo de um determinado valor e escreva o valor.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-tablet-set-alert-condition.png)
5. Toque em **Concluído**.
6. Decida se pretende receber alertas horários ou diários e se também pretende receber um e-mail ao receber o alerta.
   
   > [!NOTE]
   > Não receberá alertas todas as horas ou dias, a menos que os dados tenham efetivamente sido atualizados nesse período.
   > 
   > 
7. Também pode alterar o título do alerta.
8. Toque em **Guardar**.

### <a name="manage-alerts-on-an-android-device"></a>Gerir alertas num dispositivo Android
Pode gerir alertas individuais na aplicação móvel do Power BI ou [gerir todos os seus alertas no serviço Power BI](service-set-data-alerts.md).

1. Num dashboard, toque num cartão ou mosaico de medidor que tenha um alerta.  
2. Toque no ícone de sino sólido ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-filled-alert-bell.png).  
3. Toque no alerta para alterar um valor ou desativá-lo.
   
    ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-manage-alerts.png)
4. Toque no ícone de adição (+) para adicionar outro alerta ao mesmo mosaico.
5. Para eliminar o alerta, toque no ícone da lata de lixo ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-delete-alert-icon.png).

## <a name="data-alerts-on-a-windows-device"></a>Alertas de dados num dispositivo Windows
### <a name="set-data-alerts-on-a-windows-device"></a>Definir alertas de dados num dispositivo Windows
1. Toque num número ou mosaico de medidor no dashboard para o abrir.  
2. Toque no ícone de sino ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-alert-bell-off.png) para adicionar um alerta.  
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-tap-alert.png)
3. Toque no ícone de adição (+).
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-no-alerts-yet.png)
4. Opte por receber alertas acima ou abaixo de um determinado valor e escreva o valor.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-set-alert.png)
5. Decida se pretende receber alertas horários ou diários e se também pretende receber um e-mail ao receber o alerta.
   
   > [!NOTE]
   > Não receberá alertas todas as horas ou dias, a menos que os dados tenham efetivamente sido atualizados nesse período.
   > 
   > 
6. Também pode alterar o título do alerta.
7. Toque na marca de verificação.
8. Um único mosaico pode ter alertas para valores acima e abaixo dos limiares. Em **Gerir alertas**, toque no sinal de adição (+).
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-add-another-alert.png)

### <a name="manage-alerts-on-a-windows-device"></a>Gerir alertas num dispositivo Windows
Pode gerir alertas individuais na aplicação móvel do Power BI ou [gerir todos os seus alertas no serviço Power BI](service-set-data-alerts.md).

1. Num dashboard, toque num cartão ou mosaico de medidor que tenha um alerta.  
2. Toque no ícone do sino ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-alert-bell-on.png).  
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-has-alerts.png)
3. Toque no alerta para alterar um valor ou desativá-lo.
   
    ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-add-another-alert.png)
4. Para eliminar um alerta, clique com o botão direito do rato ou toque e mantenha premido > **Eliminar**.

## <a name="receiving-alerts"></a>Receber alertas
Os alertas são recebidos no [Centro de Notificações](mobile-apps-notification-center.md) do Power BI no seu dispositivo móvel ou no serviço Power BI, juntamente com notificações de novos dashboards que alguém partilhou consigo.

Normalmente, as origens de dados são definidas para serem atualizadas diariamente, apesar de algumas serem atualizadas mais vezes. Quando os dados no dashboard são atualizados, se os dados monitorizados atingirem um dos limiares que selecionou, acontecerão várias coisas.

1. O Power BI verifica se passou mais de uma hora ou mais de 24 horas (consoante a opção selecionada) desde o último alerta enviado.
   
   Desde que os dados tenham passado o limiar, receberá um alerta uma vez por hora ou por cada 24 horas.
2. Se tiver definido o alerta para lhe enviar uma mensagem de e-mail, irá encontrar algo deste género na sua Caixa de entrada.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/powerbi-alerts-email.png)
3. O Power BI adiciona uma mensagem ao seu **Centro de notificações** e adiciona o ícone de novo alerta ao mosaico aplicável ![](media/mobile-set-data-alerts-in-the-mobile-apps/powerbi-alert-tile-notification-icon.png).
4. Toque no botão de navegação global ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-alert-global-nav-button.png) para [abrir o seu **Centro de notificações**](mobile-apps-notification-center.md) e ver os detalhes do alerta.
   
     ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-notifications.png) 

> [!NOTE]
> Os alertas só funcionam em dados que são atualizados. Quando os dados forem atualizados, o Power BI procura alertas definidos para esses dados. Se os dados tiverem atingido um limiar de alerta, será acionado um alerta.
> 
> 

## <a name="tips-and-troubleshooting"></a>Sugestões e resolução de problemas
* Atualmente, os alertas não são suportados para mosaicos do Bing ou mosaicos de cartões com medidas de data/hora.
* Os alertas só funcionam com dados numéricos.
* Os alertas só funcionam em dados que são atualizados. Não funcionam com dados estáticos.
* Os alertas não funcionam com mosaicos que contenham dados de transmissão.

## <a name="next-steps"></a>Passos seguintes
* [Gerir os seus alertas no serviço Power BI](service-set-data-alerts.md)
* [Centro de Notificações Móveis do Power BI](mobile-apps-notification-center.md)
* Perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

