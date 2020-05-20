---
title: Ver relatórios do Power BI otimizados para o seu telemóvel
description: Saiba mais sobre a interação com as páginas de relatórios otimizadas para visualização nas aplicações móveis do Power BI.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: painbar
ms.openlocfilehash: 380057c2c65db3ea659adc39d692d8955201483b
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565129"
---
# <a name="view-power-bi-reports-optimized-for-your-phone"></a>Ver relatórios do Power BI otimizados para o seu telemóvel

Aplica-se a:

| ![iPhone](./media/mobile-apps-view-phone-report/ios-logo-40-px.png) | ![Telemóvel Android](./media/mobile-apps-view-phone-report/android-logo-40-px.png) |
|:--- |:--- |
| iPhones |Telemóveis Android |

Quando abre um relatório do Power BI no seu telemóvel, o Power BI verifica se o relatório foi otimizado para telemóveis. Se tiver sido, o Power BI abre automaticamente o relatório otimizado na vista vertical.

![Relatório no modo vertical](./media/mobile-apps-view-phone-report/07-power-bi-phone-report-portrait.png)

Se não existir um relatório otimizado para telemóvel, o relatório será aberto na mesma, mas nas vistas horizontais não otimizadas. Mesmo num relatório otimizado para telemóveis, se colocar o telemóvel de lado, o relatório será aberto na vista não otimizada com o esquema de relatório otimizado. Se apenas algumas páginas forem otimizadas, irá ver uma mensagem na vista vertical a indicar que o relatório se encontra disponível na vista horizontal.

![Página de relatório não otimizada](./media/mobile-apps-view-phone-report/06-power-bi-phone-report-page-not-optimized.png)

Todas as restantes funcionalidades de relatórios do Power BI continuam a funcionar em relatórios otimizados para telemóveis. Saiba mais sobre o que pode fazer em:

* [Relatórios em iPhones](mobile-reports-in-the-mobile-apps.md). 
* [Relatórios em telemóveis Android](mobile-reports-in-the-mobile-apps.md).

## <a name="filter-the-report-page-on-a-phone"></a>Filtrar a página de relatório num telemóvel
Se um relatório otimizado para telemóvel tiver filtros definidos, quando vir o relatório num telemóvel, pode utilizar esses filtros. O relatório é aberto no seu telemóvel, filtrado com os valores que estão a ser filtrados no relatório na Web. Aparece uma mensagem a indicar que existem filtros ativos na página. Pode alterar os filtros no seu telemóvel.

1. Toque no ícone de filtro ![Ícone de filtro no telemóvel](./media/mobile-apps-view-phone-report/power-bi-phone-filter-icon.png) na parte inferior da página.

2. Utilize a filtragem básica ou avançada para ver os resultados em que está interessado.
   
    ![Filtro avançado de relatórios do Power BI no telemóvel](./media/mobile-apps-view-phone-report/power-bi-iphone-advanced-filter-toronto.png)

## <a name="cross-highlight-visuals"></a>Realce cruzado de visuais
O realce cruzado dos elementos visuais funciona na vista vertical no serviço Power BI e na vista horizontal em telemóveis: quando selecionar dados num elemento visual, este realça dados relacionados noutros elementos visuais nessa página.

Saiba mais sobre [filtrar e realçar no Power BI](../../create-reports/power-bi-reports-filters-and-highlighting.md).

## <a name="select-visuals"></a>Selecionar visuais
Nos relatórios no telemóvel, ao selecionar um visual, o relatório no telemóvel realça esse visual e foca-se no mesmo, neutralizando os gestos de tela.

Com o visual selecionado, pode fazer coisas como deslocar-se no visual. Para desmarcar um visual, basta tocar em qualquer lugar fora da área visual.

## <a name="open-visuals-in-focus-mode"></a>Abrir visuais no modo de detalhe
Os relatórios no telemóvel também disponibilizam um modo de detalhe: obtém uma vista maior de um único elemento visual e explora-o mais facilmente.

* No relatório de telemóvel, toque nas reticências ( **...** ) no canto superior direito de um visual > **Expandir para o modo de detalhe**.
  
    ![Expandir para o modo de foco](media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)

O que for feito no modo de detalhe é aplicado à tela de relatório e vice-versa. Por exemplo, se realçar um valor num elemento visual e depois regressar ao relatório completo, o relatório será filtrado com o valor que realçou no elemento visual.

Algumas ações só são possíveis no modo de detalhe, devido às limitações de tamanho de ecrã:

* **Desagregar** as informações mostradas num visual. Saiba mais sobre [desagregar e agregar](mobile-apps-view-phone-report.md#drill-down-in-a-visual) num relatório de telemóvel, mais abaixo.
* **Ordene** os valores num visual.
* **Reverter**: limpe os passos de exploração que realizou num elemento visual e reverta para a definição estabelecida quando o relatório foi criado.
  
    Para limpar toda a exploração de um visual, toque nas reticências ( **...** ) > **Reverter**.
  
    ![Reverter](media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)
  
    A reversão está disponível ao nível do relatório, ao limpar a exploração de todos os elementos visuais, ou ao nível do elemento visual, ao limpar a exploração do elemento visual selecionado.   

## <a name="drill-down-in-a-visual"></a>Desagregar num visual
Se os níveis de hierarquia estiverem definidos num visual, pode desagregar até às informações detalhadas mostradas num visual e, em seguida, voltar para cima. Pode [adicionar desagregações a um visual](../end-user-drill.md) no serviço Power BI ou no Power BI Desktop.

Existem alguns tipos de desagregação:

### <a name="drill-down-on-a-value"></a>Desagregar um valor
1. Toque sem soltar num ponto de dados num elemento visual.
2. Será apresentada uma descrição e, se estiver definida uma hierarquia, o rodapé da descrição irá apresentar setas para desagregar e agregar.
3. Toque na seta para baixo para desagregar.

    ![Tocar para desagregar](media/mobile-apps-view-phone-report/report-drill-down.png)
    
4. Toque na seta para cima para agregar.

### <a name="drill-to-next-level"></a>Explorar o nível seguinte
1. Num relatório num telemóvel, toque nas reticências ( **...** ) no canto superior direito > **Expandir para o modo de detalhe**.
   
    ![Expandir para o modo de foco](media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)
   
    Neste exemplo, as barras mostram os valores de estados.
2. Toque no ícone Explorar ![Ícone Explorar](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-icon.png) no canto inferior esquerdo.
   
    ![Modo Explorar](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-mode.png)
3. Toque em **Mostrar nível seguinte** ou em **Expandir para o nível seguinte**.
   
    ![Expandir para o nível seguinte](./media/mobile-apps-view-phone-report/power-bi-phone-report-expand-levels.png)
   
    Agora, as barras mostram os valores das cidades.
   
    ![Níveis expandidos](./media/mobile-apps-view-phone-report/power-bi-phone-report-expanded-levels.png)
4. Se tocar na seta no canto superior esquerdo, irá regressar ao relatório de telemóvel com os valores ainda expandidos ao nível inferior.
   
    ![Ainda expandido ao nível inferior](./media/mobile-apps-view-phone-report/power-bi-back-to-phone-report-expanded-levels.png)
5. Para regressar ao nível original, toque nas reticências ( **...** ) novamente > **Reverter**.
   
    ![Reverter](media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)

## <a name="drill-through-from-a-value"></a>Pormenorizar a partir de um valor
A pormenorização liga valores numa página de relatório a outras páginas de relatório. Ao pormenorizar de um ponto de dados para outra página de relatório, os valores do ponto de dados são utilizados para filtrar a página pormenorizada ou o contexto será o dos dados selecionados.
Os autores do relatório podem [definir a pormenorização](https://docs.microsoft.com/power-bi/desktop-drillthrough) ao criarem o relatório.

1. Toque sem soltar num ponto de dados num elemento visual.
2. Será apresentada uma descrição e, se estiver definida a pormenorização, o rodapé da descrição irá apresentar uma seta para pormenorizar.
3. Toque na seta para pormenorizar.

    ![Tocar para pormenorizar](media/mobile-apps-view-phone-report/report-drill-through1.png)

4. Escolha a página do relatório a pormenorizar.

    ![Selecionar a página do relatório](media/mobile-apps-view-phone-report/report-drill-through2.png)

5. Utilize o botão Anterior no cabeçalho da aplicação para voltar à página na qual começou.


## <a name="next-steps"></a>Próximos passos
* [Criar relatórios otimizados para as aplicações móveis do Power BI](../../create-reports/desktop-create-phone-report.md)
* [Criar uma vista de telemóvel de um dashboard no Power BI](../../create-reports/service-create-dashboard-mobile-phone-view.md)
* [Criar visuais responsivos otimizados para qualquer tamanho](../../visuals/power-bi-report-visualizations.md)
* Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
