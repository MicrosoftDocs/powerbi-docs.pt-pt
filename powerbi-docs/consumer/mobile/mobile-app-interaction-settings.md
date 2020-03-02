---
title: Configurar definições de interação em relatórios
description: Saiba como anular as predefinições de interação em relatórios.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 01/21/2020
ms.author: painbar
ms.openlocfilehash: fee89c65328b70e1f312b39fbad75d7148bd92f2
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/23/2020
ms.locfileid: "76542295"
---
# <a name="configure-report-interaction-settings"></a>Configurar definições de interação em relatórios

## <a name="overview"></a>Descrição geral

A aplicação móvel do Power BI tem uma série de definições de "interação" configuráveis que lhe permitem controlar a forma como interage com os seus dados e definir o comportamento de determinados elementos na aplicação. Atualmente, existem definições para
* [Interação com toque único ou duplo em elementos visuais de relatórios](#single-tap)
* [Rodapé de relatório ancorado ou dinâmico](#docked-report-footer-android-phones) (Android)
* [Atualização de relatório por botão ou puxar para atualizar](#report-refresh-android-phones) (Android)

Para aceder às definições de interação, toque na imagem do perfil para abrir o [painel lateral](./mobile-apps-home-page.md#header), selecione **Definições** e procure a secção **Interação**.

![Definições de interação](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-section.png)

>[!NOTE]
>As definições de interação para o botão de atualização e para ancorar o rodapé do relatório não têm atualmente efeito em relatórios do Report Server. Isto vai mudar com a versão do Report Server de janeiro de 2020.

## <a name="interaction-settings"></a>Definições de interação

### <a name="single-tap"></a>Toque único
Quando transfere a aplicação móvel do Power BI, a mesma encontra-se definida para interação com toque único. Isto significa que, quando toca num elemento visual para fazer algo, como selecionar um item de segmentação de dados, realces cruzados, clicar numa ligação ou num botão, etc., o toque seleciona o elemento visual e executa a ação que pretende.

Se preferir, pode desativar a interação com toque único. Tem também a interação com duplo toque. Na interação com duplo toque, começa por tocar num elemento visual para o selecionar e depois toca novamente no mesmo para executar a ação pretendida.

### <a name="docked-report-footer-android-phones"></a>Rodapé de relatório ancorado (telemóveis Android)

A definição de rodapé do relatório ancorado determina se o rodapé do relatório permanece ancorado (ou seja, fixo e sempre visível) na parte inferior do relatório ou se é ocultado e reaparece com base nas suas ações no relatório, como o deslocamento.

Em telemóveis Android, a predefinição de rodapé de relatório ancorado é **ativado**, o que significa que o rodapé do relatório fica ancorado e sempre visível na parte inferior do relatório. Coloque a definição em **desativado** se preferir um rodapé de relatório dinâmico que apareça e desapareça, consoante as suas ações no relatório.

### <a name="report-refresh-android-phones"></a>Atualização do relatório (telemóveis Android)

A definição de atualização do relatório define a forma como inicia atualizações em relatórios. Pode optar por ter um botão de atualização em todos os cabeçalhos de relatórios ou utilizar a ação de puxar para atualizar (puxar ligeiramente de cima para baixo) na página do relatório para atualizar o mesmo. A imagem abaixo ilustra as duas alternativas. 

![Botão de atualização versus puxar para atualizar](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-refresh-button-versus-pull.png)

Em telemóveis Android, é adicionado um botão de atualização por predefinição.

Para alterar a definição de atualização do relatório, aceda ao item de atualização de relatórios nas definições de interação. Será mostrada a definição atual. Toque no valor para abrir um pop-up onde poderá escolher um novo valor.

![Definir atualização](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-set-refresh.png)

## <a name="remote-configuration"></a>Configuração remota

Podem também ser configuradas interações remotamente por um administrador, através de uma ferramenta MDM com um ficheiro de configuração de aplicação. Desta forma, é possível uniformizar a experiência de interação dos relatórios em toda a organização ou para grupos específicos de utilizadores na organização. Veja [Configurar interação com a gestão de dispositivos móveis](./mobile-app-configuration.md) para obter detalhes.


## <a name="next-steps"></a>Próximos passos
* [Interagir com relatórios](./mobile-reports-in-the-mobile-apps.md#interact-with-reports)
* [Configurar interação com a gestão de dispositivos móveis](./mobile-app-configuration.md)
