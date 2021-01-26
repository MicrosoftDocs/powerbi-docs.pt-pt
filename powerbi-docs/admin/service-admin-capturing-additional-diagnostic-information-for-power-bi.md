---
title: Capturar informações de diagnóstico para suporte
description: Instruções para recolher manualmente informações de diagnóstico do serviço Power BI. Envie esta informação para apoiar para ajudá-los a resolver problemas.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/21/2021
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 59e434d571c5b8d10c944bc385fb4e18ed89963c
ms.sourcegitcommit: 84f0e7f31e62cae3bea2dcf2d62c2f023cc2d404
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/26/2021
ms.locfileid: "98781194"
---
# <a name="capture-diagnostic-information-from-the-power-bi-service"></a>Captar informações de diagnóstico do serviço Power BI

Antes de contactar o Microsoft Support para obter ajuda com um problema que está a ter com o serviço Power BI, pode recolher ficheiros que nos ajudarão a resolver o seu problema. Recomendamos que obtenha um rastreio de navegador da sessão do seu navegador. Um rastreio de navegador é um ficheiro de diagnóstico que pode fornecer detalhes importantes sobre o que está a acontecer no serviço Power BI quando o problema ocorre.

Os administradores do Power BI podem utilizar a experiência **de suporte Help +** no centro de [administração](https://admin.powerplatform.microsoft.com/) da Plataforma De Energia para obter soluções de autoajuda e contactar o Support. Os ficheiros de diagnóstico que recolhe usando os passos abaixo podem ser anexados ao seu pedido de apoio para ajudar na resolução de problemas. Para obter mais opções de suporte, consulte [as opções de suporte power BI](service-support-options.md).

Para recolher vestígios de navegador e outras informações de sessão, siga os passos abaixo para o navegador que utiliza.

## <a name="collect-a-browser-trace"></a>Recolher vestígios de navegador

> [!IMPORTANT]
>Inicie sação no [serviço Power BI](https://app.powerbi.com) *antes* de começar a recolher informações sobre os vestígios do navegador, independentemente do navegador que utilize. Este passo é importante para garantir que as informações de rastreio não incluem informações sensíveis relacionadas com o seu início de sôr.000.

#### <a name="google-chrome-or-microsoft-edge"></a>[Google Chrome ou Microsoft Edge](#tab/google-chrome-or-microsoft-edge)

O Google Chrome e o Microsoft Edge (Chromium) são ambos baseados no [projeto Chromium open source](https://www.chromium.org/Home). Os passos a seguir mostram como usar as ferramentas de desenvolvimento, que são semelhantes nos dois navegadores. Para obter mais informações, consulte as ferramentas de desenvolvimento [do Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) e [Microsoft Edge (Chromium).](/microsoft-edge/devtools-guide-chromium)

1. Depois de iniciar sessão, prima F12 no seu teclado. Ou, no Microsoft Edge selecione **Definições e muito mais (...)**  >  **Mais ferramentas**  >  **Ferramentas de desenvolvimento**. No Google Chrome, **selecione Personalizar e controlar o** menu de definições do Google Chrome Google :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/chromium-icon-settings.png" alt-text="Chrome." border="false"::: > **Mais ferramentas**  >  **Ferramentas de desenvolvimento**.
1. Prepare-se para recolher o rastreio do navegador definindo as opções de rastreio. Também vai parar e limpar qualquer informação que tenha sido recolhida antes de começar a reproduzir o problema. Por padrão, o navegador mantém a informação de rastreio apenas para a página que está atualmente carregada. Siga estes passos para configurar o navegador para manter todas as informações de rastreio, mesmo que a sua repro vá para mais de uma página:
    1. Na janela **ferramentas do Desenvolvedor,** selecione o separador **'Rede'.** Em seguida, selecione **Registo de Preservação**.
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-preserve-log.png" alt-text="Ferramentas de desenvolvimento com separador de rede e conservar o registo selecionado." :::

     2. Selecione o separador **Consola** e, em seguida, selecione **Definições**  >  **Preservar o registo**. 
   
           :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-console-settings.png" alt-text="Ferramentas de desenvolvimento com separador de consola e conservar registo selecionado." :::

        Selecione **novamente Definições** para fechar as **definições da Consola**.

3. Em seguida, pare e limpe qualquer gravação em andamento. Selecione o separador **'Rede',** **selecione Parar de registar o registo de rede** e, em seguida, **Limpar**.
   
   :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-stop-recording.png" alt-text="Ferramentas de programação com separador de rede e opções de gravação claras selecionadas." :::
     
2. Agora, vais reproduzir o problema que estavas a ter no serviço de Bi-Energia. Para começar, nas **ferramentas developer** selecione o separador **'Rede'.** Selecione **registo de rede de registo**.

    > [!IMPORTANT]
    >Refresque a página do navegador no serviço Power BI antes de começar a reproduzir o problema para que os vestígios sejam corretamente capturados.

   Reproduza os passos que resultaram no problema com que precisa de ajuda.

     :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-record-network-log.png" alt-text="Ferramentas de desenvolvedor com separador de rede e registo de registo de registo selecionado." :::

    À medida que reproduz o problema, verá uma saída semelhante à seguinte na janela **de ferramentas do Desenvolvedor.**

    :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-output.png" alt-text="Ferramentas de desenvolvedor com saída de sessão de exibição do separador de rede." :::
    
3. Depois de reproduzir o comportamento do problema, precisa de guardar os ficheiros de registo e anexá-los ao seu pedido de suporte.
    1. Para exportar o registo de rede, nas **ferramentas developer** selecione o **separador 'Rede'.** Selecione **Parar de gravar o registo de rede**. Então, selecione **Export HAR...** e guarde o ficheiro.

         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-export-har.png" alt-text="Ferramentas de desenvolvedor com separador de rede, parar de gravar e exportar opções DE HAR selecionadas." :::

    2. Para exportar a saída da consola, nas **ferramentas do Desenvolvedor** selecione o **separador Consola.** Clique com o botão direito numa mensagem visualizada e, em seguida, **selecione Save as...** e guarde a saída da consola para um ficheiro de texto.
    
         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-save-as.png" alt-text="Ferramentas de desenvolvedor com separador de consola selecionadas e guardam como opção mostrada." :::

   Embale o ficheiro HAR guardado, a saída da consola e a gravação do ecrã num formato comprimido, como .zip, e anexe o ficheiro ao seu pedido de suporte.

#### <a name="apple-safari"></a>[Apple Safari](#tab/apple-safari)

Os passos a seguir mostram como usar as ferramentas de desenvolvimento no Apple Safari. Para mais informações, consulte a [visão geral do Safari Developer Tools.](https://support.apple.com/guide/safari-developer/safari-developer-tools-overview-dev073038698/11.0/mac)

1. Depois de iniciar a sessão, ative as ferramentas de desenvolvimento no Apple Safari:
    1. A partir do cabeçalho da página, selecione  >  **Preferências do** Safari .
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-preferences.png" alt-text="Menu Apple Safari com preferências selecionadas." :::

    2. Selecione **Advanced**, em seguida, selecione **o menu Show Develop na barra** de menu para ativar as ferramentas do desenvolvedor.
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-show-develop-menu.png" alt-text="Menu avançado do Safari com menu de desenvolvimento de show na barra de menu selecionada." :::

2. Em seguida, irá definir opções no **Web Inspetor** para permitir que o seu navegador mantenha todas as informações de rastreio. Por padrão, o navegador mantém a informação de rastreio apenas para a página que está atualmente carregada. Estas definições garantem que as informações de rastreio são recolhidas mesmo que a sua repro exija ir a mais de uma página.

    1. Selecione **Develop**  >  **Show Web Inspetor**.
    
        :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-web-inspector.png" alt-text="Desenvolva o menu com o Show Web Inspetor selecionado." :::

    2. Selecione **registo**  >  **de preservação de** rede
       
         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-network-preserve-log.png" alt-text="Menu web Inspetor com Registo de Rede e Reserva selecionado." :::

    1. Selecione **registo**  >  **de preservação de consolas**
   
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-console-preserve-log.png" alt-text="Menu web Inspetor com Console e Registo de Reserva selecionados." :::

3. Depois de definidas as opções, selecione **Itens** de rede de rede de rede  >   para se certificar de que os seus registos contêm apenas detalhes sobre o problema.

    :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-clear-network-items.png" alt-text="Menu web Inspetor com Itens de Rede e Rede Limpa selecionados." :::


4. Agora estás pronto para reproduzir o problema. 
    > [!IMPORTANT]
    >Refresque a página do navegador no serviço Power BI antes de começar a reproduzir o problema para que os vestígios sejam corretamente capturados.

    Passe pelos passos para reproduzir o problema que está tendo. À medida que reproduz o problema, verá uma saída semelhante à seguinte na janela **da Rede.**

    :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-session-output.png" alt-text="Janela de rede que mostra a saída da amostra." :::

5. Depois de reproduzir o comportamento do problema, precisa de guardar os ficheiros de registo e anexá-los ao seu pedido de suporte.

    1. Para exportar o registo de rede, a partir do separador **Rede,** selecione **Export** e guarde o ficheiro em formato HAR.

         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-export.png" alt-text="Separador de rede com opção de exportação selecionada." :::

    2. Para exportar a saída da consola, no painel de ferramentas **Develop,** selecione o **separador Consola** e expanda a janela. Coloque o cursor no início da saída da consola e, em seguida, arraste e selecione todo o conteúdo da saída. Utilize o Comando C para copiar a saída e guarde-a num ficheiro de texto.

   Embale o ficheiro HAR guardado, a saída da consola e a gravação do ecrã num formato comprimido, como .zip, e anexe o ficheiro ao seu pedido de suporte.

#### <a name="firefox"></a>[Firefox](#tab/firefox)

Os passos a seguir mostram como utilizar as ferramentas de desenvolvimento no Firefox. Para obter mais informações, consulte as [ferramentas do Firefox Developer](https://developer.mozilla.org/docs/Tools).

1. Depois de iniciar sessão, prima F12 no seu teclado. Ou, no Firefox **selecione o** ícone do menu :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-menu.png" alt-text="Open Firefox." border="false"::: > **Desenvolvedor web**  >  **Ferramentas de toggle**. As ferramentas aparecem na parte inferior do ecrã.

1. Em seguida, você definirá opções no **Inspetor** para permitir que o seu navegador mantenha todas as informações de rastreia. Por padrão, o navegador mantém a informação de rastreio apenas para a página que está atualmente carregada. Estas definições garantem que as informações de rastreio são recolhidas mesmo que a sua repro exija ir a mais de uma página.

    1. Na janela do **Inspetor,** selecione o **separador 'Rede'.** Em seguida, **selecione Registos de Persistência**.
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-network-persist-logs.png" alt-text="Ferramentas de inspetor com separador de rede e registos de persistência selecionados." :::

     2. Selecione o separador **Consola** e, em seguida, selecione **as definições de consola** Persist  >  **Logs**. 
   
           :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-console-persist-logs.png" alt-text="Ferramentas de inspetor com separador de consola e registos de persistência selecionados." :::

3. Depois de definidas as opções, limpe qualquer gravação em curso. Selecione o separador **'Rede'** e, em seguida, **Limpe**.
   
   :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-stop-recording.png" alt-text="Ferramentas de programação com separador de rede e opções de gravação claras selecionadas." :::
     
2. Agora estás pronto para reproduzir o problema. 
    > [!IMPORTANT]
    >Refresque a página do navegador no serviço Power BI antes de começar a reproduzir o problema para que os vestígios sejam corretamente capturados.
 
    Passe pelos passos para reproduzir o problema que está tendo.
    
3. Depois de reproduzir o comportamento do problema, precisa de guardar os ficheiros de registo e anexá-los ao seu pedido de suporte.
    1. Para exportar o registo de rede, selecione **Network**  >  **HAR Export/Import e, em** seguida, **Guarde Tudo como HAR**.

         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-save-har.png" alt-text="Separador de rede com menu de exportação/importação DE HAR e guardar todas as opções selecionadas." :::

    2. Para exportar a saída da consola, selecione o **separador Consola.** Clique com o botão direito numa mensagem visualizada e, em seguida, selecione **Export Visible Messages To** e guarde a saída da consola para um ficheiro de texto.
    
         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-export-visible-messages.png" alt-text="Aa guia de consola selecionada e a opção de envio de mensagens visíveis mostradas." :::

   Embale o ficheiro HAR guardado, a saída da consola e a gravação do ecrã num formato comprimido, como .zip, e anexe o ficheiro ao seu pedido de suporte.

---

Depois de recolher os ficheiros de diagnóstico, anexe-os ao seu pedido de apoio para ajudar o engenheiro de suporte a resolver o seu problema. O ficheiro HAR conterá todas as informações sobre pedidos de rede entre a janela do navegador e o serviço Power BI, incluindo:

* Os IDs de atividade para cada pedido.

* O carimbo de data/hora preciso para cada pedido.

* Quaisquer informações de erro devolvidas ao cliente.

Este rastreio também conterá os dados utilizados para povoar os elementos visuais mostrados no ecrã.

## <a name="next-steps"></a>Próximos passos

* [Controlar o estado de funcionamento do serviço Power BI no Microsoft 365](service-admin-health.md)
* [Ativar as notificações de interrupção do serviço](service-interruption-notifications.md)
* [Junte-se à Comunidade Power BI](https://community.powerbi.com/)
