---
title: Descrição geral das visualizações de relatório no serviço Power BI e no Desktop
description: Descrição geral das visualizações de relatório (elementos visuais) no Microsoft Power BI.
author: mihart
ms.author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: SYk_gWrtKvM
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/28/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: 075985ce2d4eec1244827c65476c81774196a449
ms.sourcegitcommit: 2a61d8b1e2707a24fe1284a8a4034b11c3999842
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/29/2019
ms.locfileid: "73048851"
---
# <a name="visualizations-in-power-bi-reports"></a>Visualizações em relatórios do Power BI

As visualizações (também conhecidas como elementos visuais) apresentam informações que foram descobertas nos dados. Um relatório do Power BI poderá ter uma única página com um elemento visual ou poderá ter páginas repletas de elementos visuais. No serviço Power BI, os elementos visuais podem ser [afixados de relatórios a dashboards](../service-dashboard-pin-tile-from-report.md).

É importante saber distinguir *estruturadores* e *consumidores* de relatórios.  Se for a pessoa que cria ou modifica o relatório, é um estruturador.  Os estruturadores têm permissões de edição para o relatório e o respetivo conjunto de dados subjacente. No Power BI Desktop, isto significa que pode abrir o conjunto de dados na Vista de dados e criar elementos visuais na Vista de relatório. No serviço Power BI, significa que pode abrir o relatório ou conjunto de dados no editor de relatórios na [Vista de edição](../consumer/end-user-reading-view.md). Se um relatório ou dashboard tiver sido [partilhado consigo](../consumer/end-user-shared-with-me.md), você será um *consumidor* do relatório. Poderá ver e interagir com o relatório e os seus elementos visuais, mas não conseguirá fazer tantas alterações como um *estruturador*.

Existem vários tipos de elementos visuais disponíveis diretamente no painel Visualizações do Power BI.

![Painel a mostrar ícones para cada tipo de visualização](media/power-bi-report-visualizations/power-bi-icons.png)

E para ter ainda mais opções, visite o [site da comunidade do Microsoft AppSource](https://appsource.microsoft.com) para procurar e [transferir](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) [elementos visuais personalizados](../developer/visuals/custom-visual-develop-tutorial.md) fornecidos pela Microsoft e pela comunidade.

<iframe width="560" height="315" src="https://www.youtube.com/embed/SYk_gWrtKvM?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>


Se for novo no Power BI, ou se precisar de relembrar alguns aspetos, utilize as ligações abaixo para saber os aspetos básicos de visualizações do Power BI.  Em alternativa, utilize o nosso Índice (no lado esquerdo deste artigo) para procurar ainda mais informações úteis.

## <a name="add-a-visualization-in-power-bi"></a>Adicionar uma visualização no Power BI

[Crie visualizações](power-bi-report-add-visualizations-i.md) nas páginas dos relatórios. Navegue na [lista de visualizações e tutoriais de visualização disponíveis.](power-bi-visualization-types-for-reports-and-q-and-a.md) 

## <a name="upload-a-custom-visualization-and-use-it-in-power-bi"></a>Carregar uma visualização personalizada e utilizá-la no Power BI

Adicione uma visualização personalizada que criou ou que encontrou no [site da comunidade do Microsoft AppSource ](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals). Sente-se criativo? Aprofunde o nosso código fonte e utilize as nossas [ferramentas de programador](../developer/visuals/custom-visual-develop-tutorial.md) para criar um novo tipo de visualização e [partilhá-la com a comunidade](../developer/office-store.md). Para saber mais sobre como desenvolver um elemento visual personalizado, aceda a [Desenvolver um elemento visual personalizado do Power BI](../developer/visuals/custom-visual-develop-tutorial.md).

## <a name="personalize-your-visualization-pane-preview"></a>Personalizar o seu painel de visualização (pré-visualização)

Se utilizar o mesmo elemento visual personalizado em muitos relatórios, pode afixar uma visualização personalizada no seu painel de visualização. Para afixar a visualização, clique com o botão direito do rato no elemento visual para o afixar no painel.

![Afixar no painel de visualização](media/power-bi-report-visualizations/power-bi-pin-custom-visual-option.png)

Quando um elemento visual é afixado, é apresentado junto aos outros elementos visuais incorporados. O elemento visual fica associado à conta com sessão iniciada, pelo que os novos relatórios que criar irão ter este elemento visual automaticamente incluído, partindo do pressuposto de que tem sessão iniciada. Esta situação facilita o estabelecimento de um determinado elemento visual como padrão e evita que tenha de o adicionar a cada relatório.

![Painel de visualização personalizado](media/power-bi-report-visualizations/power-bi-personalized-visualization-pane.png)

Enquanto esta funcionalidade estiver em pré-visualização, só poderá ver os seus elementos visuais afixados no Power BI Desktop. Além disso, tem de ter sessão iniciada para que esta funcionalidade esteja disponível.

## <a name="change-the-visualization-type"></a>Alterar o tipo de visualização

Tente [alterar o tipo de visualização](power-bi-report-change-visualization-type.md) para ver o que funciona melhor com os seus dados.

## <a name="pin-the-visualization"></a>Afixar a visualização

No serviço Power BI, quando a visualização estiver da forma que quer, pode [afixá-la a um dashboard](../service-dashboard-pin-tile-from-report.md) como um mosaico. Se alterar a visualização que está a ser utilizada no relatório depois de a afixar, o mosaico no dashboard não será alterado. Se era um gráfico de linhas, continuará a ser um gráfico de linhas, mesmo que o tenha alterado para um gráfico em anel no relatório.

## <a name="limitations-and-considerations"></a>Limitações e considerações
- Consoante a origem de dados e o número de campos (medidas ou colunas), o carregamento de um elemento visual pode ser mais demorado.  Recomendamos que limite os elementos visuais a um total de 10 a 20 campos, por motivos de legibilidade e desempenho. 

- O limite máximo de elementos visuais é 100 campos (medidas ou colunas). Se o carregamento do seu elemento visual falhar, reduza o número de campos.   

## <a name="next-steps"></a>Próximos passos

* [Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
* [Elementos visuais personalizados](../power-bi-custom-visuals.md)
