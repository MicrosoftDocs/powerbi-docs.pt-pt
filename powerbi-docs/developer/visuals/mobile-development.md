---
title: Mobile development (Desenvolvimento para dispositivos móveis)
description: Como criar elementos visuais do Power BI compatíveis com dispositivos móveis
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/12/2019
ms.openlocfilehash: 38e6ac3be143381304f1fdfc8e1427b91f398a9a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82196635"
---
# <a name="how-to-create-mobile-friendly-power-bi-visuals"></a>Como criar elementos visuais do Power BI compatíveis com dispositivos móveis
O consumo em dispositivos móveis tem um papel importante no Power BI. Uma das suas vantagens é o facto de se manter ligado aos seus dados em qualquer momento e em qualquer lugar.

Enquanto programador que cria elementos visuais do Power BI, devem ser abordadas as restrições únicas de cada dispositivo móvel para alcançar o maior número possível de utilizadores e proporcionar a melhor experiência móvel.

Utilize a [aplicação Power BI para Windows, iOS e Android](/power-bi/consumer/mobile/mobile-apps-for-mobile-devices) para dar aos seus utilizadores empresariais uma visão abrangente dos respetivos dados, em qualquer lado e na ponta dos dedos.

## <a name="requirements"></a>Requirements

Os requisitos seguintes são essenciais para o desenvolvimento de elementos visuais compatíveis com dispositivos móveis:

- Composição

  Os seus elementos visuais do Power BI têm de ser compostos em todos os dispositivos móveis suportados, incluindo browsers e aplicações suportados, sem que ocorram erros nos relatórios e dashboards, ou quando estão a ser executados no **Modo de detalhe**. 

- Interativo

  Deve proporcionar-se funcionalidades interativas da mesma forma que se proporciona para computadores. Todos os eventos processados em browsers de computador têm de ser suportados ou dispor de processadores de eventos semelhantes para dispositivos móveis.
  
  Por exemplo, a navegação básica e a seleção de pontos de dados devem ter as mesmas funcionalidades existentes nos browsers de computador. Se um elemento visual suportar a seleção múltipla com a tecla **Ctrl**, o programador deve considerar adicionar um processador de eventos semelhante para dispositivos móveis.

  A tabela seguinte apresenta uma lista dos eventos correspondentes em dispositivos móveis.

  | Nome do evento de rato | Nome do evento de toque |
  |:----------------:|:----------------:|
  | `click` | `click` |
  | `mousemove` | `touchmove` |
  | `mousedown` | `touchstart` |
  | `mouseup` | `touchend` |
  | `dblclick` | utilizar biblioteca externa |
  | `contextmenu` | utilizar biblioteca externa |
  | `mouseover` | `touchmove` |
  | `mouseout` | `touchmove` (ou biblioteca externa) |
  | `wheel` | `NaN` |

  > [!NOTE]
  > Nem todos os dispositivos móveis ou de ecrã tátil suportam eventos de rato (ou com prefixo de *rato*). Nesses casos, processe os eventos de *rato* e de *toque* ao mesmo tempo.

## <a name="optional"></a>Opcional
Os pontos seguintes são considerados opcionais e são utilizados para criar uma melhor experiência de utilizador final.

- Composição

  Para suportar elementos visuais mais pequenos, experimente adicionar opções de formato que o utilizador pode alterar para ajustar o tamanho de cada elemento. Por exemplo, adicione opções de formato às etiquetas no caso de relatórios e dashboards. Isto permite que os utilizadores personalizem um elemento visual especificamente para o respetivo dispositivo móvel.
  
  Também se podem aplicar as mesmas definições aos elementos visuais nos browsers de computador e, se for necessário, sobrepor para adaptar o elemento visual a ecrãs mais pequenos.

  > [!NOTE]
  > Para otimizar um elemento visual no **Modo de detalhe**, é preciso considerar as orientações de tamanho de ecrã vertical ou horizontal – veja [Display content in Focus mode](/power-bi/consumer/end-user-focus) (Apresentar conteúdos no Modo de detalhe).

- Interativo

  Considere adicionar processadores de eventos específicos de dispositivos móveis, tais como arrastar e deslocar.

- Ativação pós-falha

  Um elemento visual deve apresentar um erro descritivo se não for possível compô-lo no dispositivo móvel.

## <a name="supported-browsers-and-devices"></a>Dispositivos e browsers suportados
Os elementos visuais do Power BI devem ser compostos em todos os dispositivos que suportam aplicações do Power BI. Para obter mais informações, veja [Browsers com suporte para o Power BI](/power-bi/power-bi-browsers) e [Aplicações móveis do Power BI](/power-bi/consumer/mobile/mobile-apps-for-mobile-devices).

O programador tem de considerar a maioria destes aspetos de qualidade quando testa os elementos visuais nos mais recentes modelos de dispositivos Windows, iOS e Android.

## <a name="next-steps"></a>Próximos passos
Para começar, veja [Tutorial: desenvolver um elemento visual do Power BI](/power-bi/developer/visuals/custom-visual-develop-tutorial).