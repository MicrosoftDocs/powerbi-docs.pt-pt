---
title: Explorar relatórios nas aplicações móveis do Power BI
description: Saiba mais sobre ver e interagir com relatórios nas aplicações móveis do Power BI no seu telemóvel ou tablet. Pode criar relatórios no serviço Power BI ou no Power BI Desktop e, em seguida, interagir com os mesmos nas aplicações móveis.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 04/21/2019
ms.author: mshenhav
ms.openlocfilehash: bee60dd6f3254b049f2445e6e985c625933caf5b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565498"
---
# <a name="explore-reports-in-the-power-bi-mobile-apps"></a>Explorar relatórios nas aplicações móveis do Power BI
Aplica-se a:

| ![iPhone](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![iPad](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![Telemóvel Android](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Tablet Android](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Dispositivos Windows 10](./media/mobile-reports-in-the-mobile-apps/win-10-logo-40-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhones |iPads |Telemóveis Android |Tablets Android |Dispositivos Windows 10 |

Um relatório do Power BI é uma vista interativa dos seus dados, com visuais que representam diferentes descobertas e informações obtidas por meio desses dados. Ver os relatórios nas aplicações móveis do Power BI é o terceiro passo num processo de três passos.

1. [Criar relatórios no Power BI Desktop](../../desktop-report-view.md). Pode mesmo [otimizar um relatório para telemóveis](mobile-apps-view-phone-report.md) no Power BI Desktop. 
2. Publique esses relatórios no serviço Power BI [(https://powerbi.com)](https://powerbi.com) ou [) ou no Power BI Report Server](../../report-server/get-started.md).  
3. Em seguida, interaja com esses relatórios nas aplicações móveis do Power BI.

## <a name="open-a-power-bi-report-in-the-mobile-app"></a>Abrir um relatório do Power BI na aplicação móvel
Os relatórios do Power BI são armazenados em diferentes locais na aplicação móvel, consoante o local onde os obteve. Podem estar em Aplicações, Partilhado comigo, Áreas de trabalho (incluindo A Minha Área de Trabalho) ou num servidor de relatórios. Pode vezes, percorre um dashboard relacionado para chegar a um relatório, e noutras vezes estes estão listados.

Listas e menus, encontrará um ícone junto a um nome de relatório, ajudando-o a compreender que este item é um relatório. 

![relatórios na minha área de trabalho](./media/mobile-reports-in-the-mobile-apps/reports-my-workspace.png) 

Existem dois ícones para relatórios nas aplicações móveis do Power BI:

* ![Ícone Relatório](./media/mobile-reports-in-the-mobile-apps/report-default-icon.png) indica um relatório que será apresentado na horizontal na aplicação e será o mesmo aspeto que ele se parece no browser.

* ![Ícone de relatório de telemóvel](./media/mobile-reports-in-the-mobile-apps/report-phone-icon.png) indica um relatório que tenha, pelo menos, uma página de relatório otimizado de telefone, que será apresentada no retrato. 

Note: Com o seu telemóvel em paisagem, sempre obterá o esquema horizontal, mesmo que a página de relatório tem o esquema de telemóvel. 

Para obter a um relatório a partir de um dashboard, toque nas reticências (...) no canto superior direito de um mosaico > **abrir o relatório**.
  
  ![Abrir relatório](./media/mobile-reports-in-the-mobile-apps/power-bi-android-open-report-tile.png)
  
  Nem todos os mosaicos têm a opção de abrir num relatório. Por exemplo, os mosaicos criados ao fazer uma pergunta na caixa de Perguntas e Respostas não abrem os relatórios ao tocar nos mesmos. 
  
## <a name="interacting-with-reports"></a>Interagir com relatórios
Depois de ter um relatório aberto na aplicação, pode começar a trabalhar com ele. Há muitas coisas que pode fazer com o seu relatório e os respetivos dados. O rodapé de relatório, encontrará ações que pode efetuar no relatório e, ao tocar em e longo tocar nos dados mostrados no relatório, pode também segmentação e decomposição dos dados.

### <a name="using-tap-and-long-tap"></a>Utilizar toque e toque muito tempo
Clique em toque igual a um mouse. Portanto, se quiser um realce cruzado com o relatório com base num ponto de dados, toque nesse ponto de dados.
Tocar num valor de segmentação de dados, faz com que esse valor selecionado e o restante do relatório de fragmentação por esse valor. Tocar num link, botão ou indicador irá ativá-lo com base na ação definida pelo autor.

Provavelmente notou que, quando toca num elemento visual, é apresentado um limite. No canto superior direito do limite, não existe nas reticências (...). Tocar no mesmo trará um menu com as ações que pode fazer desse elemento visual.

![elemento visual do relatório e menu](./media/mobile-reports-in-the-mobile-apps/report-visual-menu.png)

### <a name="tooltip-and-drill-actions"></a>Dica de ferramenta e exploração de ações

Ao longo tocar em (tap e hold) um ponto de dados, uma dica de ferramenta aparecerá apresentar os valores que este ponto de dados representa. 

![Descrição de relatório](./media/mobile-reports-in-the-mobile-apps/report-tooltip.png)

Os autores do relatório podem definir hierarquias nos dados e relações entre as páginas de relatório. Hierarquia permite que a desagregação, exploração de cópia de segurança e de exploração de outra página do relatório de um elemento visual e um valor. Então, ao longo tocar num valor, além de dica de ferramenta, as opções de teste relevantes aparecerá no rodapé. 

![ações de exploração de relatórios](./media/mobile-reports-in-the-mobile-apps/report-drill-actions.png)

Com a *pormenorização*, ao tocar numa parte específica de um elemento visual, o Power BI direciona-o para uma página diferente no relatório, filtrada para apresentar o valor no qual tocou.  O autor de um relatório pode definir uma ou mais opções de pormenorização que encaminhem o utilizador para diferentes páginas. Nesse caso, poderá escolher que página pretende explorar. O botão de retrocesso leva-o novamente para a página de relatório anterior.

Saiba mais sobre como [adicionar a pormenorização no Power BI Desktop](../../desktop-drillthrough.md).
   
   > [!IMPORTANT]
   > Na aplicação do Power BI Mobile, a desagregação em elementos visuais de matriz e tabela está ativada por meio de um valor de célula apenas e não por cabeçalhos de coluna e linha.
   
   
   
### <a name="using-the-actions-in-the-report-footer"></a>Utilizar as ações no rodapé do relatório
O rodapé do relatório tem ações que pode fazer na página do relatório atual, ou em todo o relatório. O rodapé tem acesso rápido às ações mais úteis e todas as ações podem ser o acesso a partir do botão de reticências (...).

![rodapé do relatório](./media/mobile-reports-in-the-mobile-apps/report-footer.png)

As ações que pode efetuar no rodapé são:
1) Repor o filtro de relatório e seleções de volta ao estado original de realce cruzado.
2) Abra o painel de conversação para ver ou adicionar comentários neste relatório.
3) Abra o painel de filtro para ver e modificar o filtro aplicado atualmente no relatório.
4) Liste todas as páginas neste relatório. Tocar no nome da página carregará e apresentar nessa página.
Mover entre páginas de relatórios pode ser feito, passando o dedo do limite do ecrã para o centro.
5) Ver todas as ações de relatório.

#### <a name="all-report-actions"></a>Todas as ações de relatório
Tocar na... opção no rodapé do relatório, será apresentada a todas as ações que pode efetuar num relatório. 

![todas as ações de relatórios](./media/mobile-reports-in-the-mobile-apps/report-all-actions.png)

Algumas das ações podem ser desativadas, pois são dependentes nos recursos de relatório específico.
Por exemplo:
1) **Filtrar por localização atual** é ativada se os dados do relatório foi categorizados pelo autor, com dados geográficos. [Saiba como identificar dados geográficos no relatório](https://docs.microsoft.com/power-bi/desktop-mobile-geofiltering).
2) **Análise para filtrar o relatório por código de barras** só é ativada se o conjunto de dados do relatório foi marcado como código de barras. [Como Etiquetar códigos de barras no Power BI Desktop](https://docs.microsoft.com/power-bi/desktop-mobile-barcodes). 
3) **Convidar** está ativada apenas se tiver permissão para partilhar este relatório com outras pessoas. Terá permissão apenas se for o proprietário do relatório ou se obteve a permissão de voltar a partilhar pelo proprietário.
4) **Anotar e partilhar** poderá ser desativar se houver uma [política de proteção do Intune](https://docs.microsoft.com/intune/app-protection-policies) da sua organização que proibida a partilha de mensagens em fila de aplicação móvel do Power BI. 

## <a name="next-steps"></a>Próximos passos
* [Ver e interagir com relatórios do Power BI otimizados para o seu telemóvel](mobile-apps-view-phone-report.md)
* [Criar uma versão de um relatório otimizada para telemóveis](../../desktop-create-phone-report.md)
* Perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

