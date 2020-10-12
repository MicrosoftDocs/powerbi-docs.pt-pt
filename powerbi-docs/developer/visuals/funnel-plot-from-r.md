---
title: Build a funnel plot from R script to R visual (Criar um gráfico de funil ao transformar um script do R num visual do R)
description: Este artigo descreve como criar um gráfico de funil do script do R para o elemento visual do Power BI R.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 04/02/2020
ms.openlocfilehash: e0bdb5174c1392e1a2f81a101a62798f82e2b191
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/06/2020
ms.locfileid: "91747718"
---
# <a name="tutorial-build-a-funnel-plot-from-r-script-to-r-visual"></a>Tutorial: Build a funnel plot from R script to R visual (Criar um gráfico de funil ao transformar um script do R num visual do R)
Este artigo descreve como criar um gráfico de funil com o script do R no elemento visual do R, passo a passo.

Neste artigo, irá aprender a criar:

> [!div class="checklist"]
>
> * um script do R para RStudio
> * um elemento visual do R no Power BI
> * um Elemento visual *baseado em PNG* e baseado em R no Power BI
> * um Elemento visual *baseado em HTML* e baseado em R no Power BI

O gráfico de funil proporciona uma forma simples de consumir, interpretar e mostrar a quantidade de variação esperada. O **funil** é constituído com limites de confiança e os valores atípicos são representados por pontos fora do funil.

Neste exemplo, o gráfico de funil serve para comparar e analisar os dados de diversos conjuntos.  

> [!NOTE]
> Os ficheiros de origem estão disponíveis para transferência em cada conjunto de passos.

## <a name="build-an-r-script-with-dataset"></a>Criar um script do R com conjuntos de dados

1. Transfira um [script do R mínimo](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/script_R_v1_00.r) e a respetiva tabela de dados, [dataset.csv](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/dataset.csv).

1. Em seguida, edite o script de forma a espelhar [este script](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/script_R_v1_01.r). Isto acrescenta parâmetros de utilizadores e gestão de erros para controlar o aspeto do gráfico.

## <a name="build-a-report"></a>Criar um relatório

Em seguida, edite o script de forma a espelhar [este script](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter2_Rvisual/script_RV_v2_00.r). Isto carrega o ficheiro *dataset.csv* em vez do *read.csv* na área de trabalho do Power BI Desktop e cria uma tabela de **Mortalidade do Cancro**. Veja os resultados no seguinte [ficheiro PBIX](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter2_Rvisual/funnelPlot_Rvisual.pbix).

> [!NOTE]
> O `dataset` é um nome hard-coded para a entrada `data.frame` de qualquer elemento visual do R. 

## <a name="create-an-r-powered-visual-and-package-in-r-code"></a>Criar um elemento visual e pacote baseados em R em código R

1. Antes de começar, certifique-se de que [instala as ferramentas PBIVIZ](./custom-visual-develop-tutorial.md#installing-packages).

1. Execute o seguinte comando para criar um novo elemento visual baseado em R:

   ```bash
   pbiviz new funnel-visual -t rvisual
   cd funnel-visual
   npm install 
   pbiviz package
   ```

   Este comando cria a pasta *funnel-visual* com o elemento visual de modelo inicial (`-t` para **modelo**). O PBIVIZ encontra-se na pasta *dist*, o código do R dentro do ficheiro *script.r*. Experimente importá-lo para o Power BI e veja o que acontece.

1. Edite o ficheiro *script.r* e substitua o conteúdo pelo script anterior.

1. Edite o ficheiro *capabilities.json* e substitua a cadeia `Values` por `dataset`. Isto substitui o nome da "Função" no modelo de forma a igualar o código do R.

   ![Captura de ecrã a mostrar uma comparação de desvio da alteração no ficheiro JSON.](./samples/funnel-plot/chapter-3/funnel-r-visual-v01/capabilities-changes.PNG)

1. *(opcional)* Edite o ficheiro *dependencies.json* e adicione uma secção para cada pacote do R exigido pelo script do R. Isto indica ao Power BI que importe automaticamente estes pacotes quando o elemento visual for carregado pela primeira vez.

   ![Captura de ecrã a mostrar uma comparação de desvio em que os conteúdos foram adicionados aos itens cranPackages.](./samples/funnel-plot/chapter-3/funnel-r-visual-v01/dependencies-changes.PNG)

1. Volte a empacotar o elemento visual com o comando `pbiviz package` e tente importá-lo para o Power BI.

> [!NOTE]
> Veja [PBIX](https://github.com/microsoft/PowerBI-visuals/blob/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) e o [código-fonte](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v01/) para transferir.

## <a name="make-r-based-visual-improvements"></a>Fazer melhorias aos elementos visuais baseados em R

O elemento visual ainda não é simples de utilizar porque o utilizador tem de saber a ordem das colunas na tabela de entrada.

1. Divida o campo de entrada `dataset` em três campos (funções): `Population`, `Number` e `Tooltips`

   ![CV01to02](./media/funnel-plot/diagram-one.PNG)

1. Edite o ficheiro *capabilities.json* e substitua a função `dataset` por três funções novas ou transfira o ficheiro [capabilities.json](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02/capabilities.json).

   Terá de atualizar as secções `dataRoles` e `dataViewMappings`, que definem nomes, tipos, descrições e máximo de colunas para cada campo de entrada.

   ![antes e depois](./samples/funnel-plot/chapter-3/funnel-r-visual-v02/capabilities-before-vs-after.png)
   
   Para obter mais informações, veja [capacidades](./capabilities.md).

1. Edite o ficheiro *script.r* para suportar `Population`, `Number` e `Tooltips` como dataframes de entrada em vez de `dataset` ou transfira o ficheiro [script.r](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02/script.r).

   ![script](./samples/funnel-plot/chapter-3/funnel-r-visual-v02/script-r-before-vs-after.png)

   > [!TIP]
   > Para seguir as alterações no script do R, procure os blocos de comentários: 
   > 
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Added to enable visual fields
   > ...
   > #RVIZ_IN_PBI_GUIDE:END: Added to enable visual fields
   > 
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Removed to enable visual fields 
   > ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Removed to enable visual fields
   > ```

1. Volte a empacotar o elemento visual com o comando `pbiviz package` e tente importá-lo para o Power BI.

> [!NOTE]
> Veja [PBIX](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) e o [código-fonte](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02) para transferir.

## <a name="add-user-parameters"></a>Adicionar parâmetros do utilizador

1. Adicione capacidades para o utilizador controlar as cores e os tamanhos de elementos visuais, incluindo parâmetros internos da IU.

   ![Captura de ecrã a mostrar duas versões do painel de ferramentas, com as opções adicionadas à versão à direita.](./media/funnel-plot/diagram-two.PNG)

1. Edite o ficheiro *capabilities.json* e atualize a secção `objects`. Aqui, definimos os nomes, descrições e tipos de cada parâmetro e decidimos também a divisão dos parâmetros em grupos (neste caso, três grupos).

   transfira o ficheiro [capabilities.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/capabilities.json), veja [propriedades de objetos](./objects-properties.md) para obter mais informações

   ![capacidades](./samples/funnel-plot/chapter-3/funnel-r-visual-v03/capabilities-before-after.PNG)

1. Edite o ficheiro *src/settings.ts* para espelhar o ficheiro [this settings.ts](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/src/settings.ts). Este ficheiro foi escrito em TypeScript.  

   Aqui, encontrará dois blocos do código adicionados para:
   - Declarar a nova interface para reter o valor de propriedade
   - Definir uma propriedade de membro e os valores predefinidos

   ![definições](./samples/funnel-plot/chapter-3/funnel-r-visual-v03/settings-ts-before-after.PNG)

1. Edite o ficheiro *script.r* para espelhar o ficheiro [this script.r](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/script.r). Isto acrescenta suporte para os parâmetros na IU ao adicionar chamadas `if.exists` por parâmetro de utilizador.

   > [!TIP]
   > Para seguir as alterações no script do R, procure os comentários:
   >
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to enable user parameters
   >  ...
   > #RVIZ_IN_PBI_GUIDE:END:Added to enable user parameters
   >
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to enable user parameters 
   >  ...
   > #RVIZ_IN_PBI_GUIDE:END:Removed to enable user parameters
   > ```

   ![script antes e depois](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/script_r_before_after_1.png)

   Pode decidir não expor os parâmetros à IU, como fizemos.  

1. Volte a empacotar o elemento visual com o comando `pbiviz package` e tente importá-lo para o Power BI.

> [!NOTE]
> Veja [PBIX](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) e o [código-fonte](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/) para transferir.

> [!TIP]
> Neste caso, adicionámos parâmetros de diversos tipos (booleano, numérico, cadeia e cor) de uma vez. Para um caso simples, veja [este exemplo](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/PropertiesPane.md) sobre como adicionar um único parâmetro. 

## <a name="convert-visual-to-rhtml-based-visual"></a>Converter elemento visual em elemento visual baseado em RHTML

Uma vez que o elemento visual resultante é baseado em PNG, não é reativo à passagem do cursor, não pode ser ampliado, etc. Por isso, temos de o converter num elemento visual baseado em HTML. Vamos criar um modelo de elemento visual vazio baseado em HTML e R. Em seguida, vamos copiar scripts do projeto baseado em PNG.

1. Execute o comando:

   ```bash
   pbiviz new funnel-visual-HTML -t rhtml
   cd funnel-visual-HTML
   npm install 
   pbiviz package
   ```

1. Abra o ficheiro *capabilities.json* e anote a linha `"scriptOutputType":"html"`.

1. Abra o ficheiro *dependencies.json* e anote os nomes dos pacotes de R listados.

1. Abra o ficheiro *script.r* e anote a estrutura. Pode abrir e executá-lo no RStudio, pois não utiliza dados externos. 

   Isto cria e guarda o ficheiro *out.html*. Este ficheiro é autónomo (sem dependências externas) e define os gráficos dentro do widget HTML. 

   > [!IMPORTANT]
   > Para utilizadores `htmlWidgets`, os utilitários do R são fornecidos na [pasta r_files](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/r_files) para ajudar a converter objetos `plotly` ou objetos `widget` no HTML autónomo. 
   > 
   > Esta versão do elemento visual baseado em R suporta também o comando `source` (ao contrário dos anteriores tipos de elementos visuais), para tornar o seu código mais legível.   
 
1. Substitua o ficheiro *capabilities.json* pelo ficheiro *capabilities.json* do passo anterior ou transfira o ficheiro [capabilities.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/capabilities.json).

   Lembre-se:

   `"scriptOutputType": "html"`

1. Intercale a versão mais recente de *script.r* ao *script.r* do modelo ou transfira [script.r](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/script.r).

   O novo script utiliza o pacote `plotly` para converter o objeto **ggplot** em objeto **plotly** e, em seguida, o pacote `htmlWidgets` para o guardar num ficheiro HTML. 

   A maioria das funções utilitárias é movida para [_r_files/utils.r_](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/r_files/utils.r) e a função `generateNiceTooltips` é adicionada ao aspeto do objeto **plotly**.

   ![1](./samples/funnel-plot/chapter-4/RHTML-v01/script-before-after-1.PNG)
   
   ![2](./samples/funnel-plot/chapter-4/RHTML-v01/script-before-after-2.PNG)

   > [!TIP]
   > Para seguir as alterações no script do R, procure os comentários:
   > 
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to create HTML-based 
   >  ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to create HTML-based
   >
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to create HTML-based  
   > ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to create HTML-based
   > ```

1. Una a versão mais recente do ficheiro *dependencies.json* ao ficheiro *dependencies.json* do modelo, de forma a incluir as novas dependências de pacote de R, ou transfira o ficheiro [dependencies.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/dependencies.json).

1. Edite o ficheiro *src/settings.ts* da mesma forma que nos passos anteriores.

1. Volte a empacotar o elemento visual com o comando `pbiviz package` e tente importá-lo para o Power BI.

> [!NOTE]
> Veja [PBIX e o código-fonte](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01) para transferir.

## <a name="build-additional-examples"></a>Criar exemplos adicionais

1. Execute o seguinte comando para criar um projeto vazio: 

   ```bash
   pbiviz new example -t rhtml
   cd example
   npm install 
   pbiviz package
   ```

1. Utilize o código desta [demonstração](http://www.htmlwidgets.org/showcase_networkD3.html) e efetue as alterações realçadas:

   ![Alterações destacadas](./media/funnel-plot/diagram-three.PNG)

1. Substitua o *script.r* do seu modelo e execute `pbiviz package` novamente. Agora, o elemento visual está incluído no seu relatório do Power BI!

## <a name="tips-and-tricks"></a>Sugestões e truques

* Recomendamos que os programadores editem o ficheiro *pbiviz.json* para armazenar os metadados corretos, como **versão**, **e-mail**, **nome**, **tipo de licença**, etc.

   > [!IMPORTANT]
   > O campo **guid** é o identificador exclusivo de um elemento visual. Se criar um novo projeto para cada elemento visual, o GUID também será diferente. Só é igual quando se utiliza um projeto antigo copiado para um novo elemento visual, algo que não deve fazer.

* Edite o ficheiro [*assets/icon.png*](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/assets/icon.png) para criar ícones exclusivos para o seu elemento visual. 

* Para depurar o código R no RStudio com os mesmos dados que estão no seu relatório do Power BI, adicione o seguinte ao início do script R (edite a variável `fileRda`):

   ```r
   #DEBUG in RStudio
   fileRda = "C:/Users/yourUserName/Temp/tempData.Rda"
   if(file.exists(dirname(fileRda)))
   {
     if(Sys.getenv("RSTUDIO")!="")
       load(file= fileRda)
     else
       save(list = ls(all.names = TRUE), file=fileRda)
   }
   ```

   Isto guarda o ambiente de um relatório do Power BI e carrega-o no RStudio. 

* Não tem de desenvolver elementos visuais baseados em R do zero, graças ao código disponível no [GitHub](https://github.com/Microsoft?utf8=%E2%9C%93&q=PowerBI&type=&language=R). Pode selecionar o elemento visual para utilizar como modelo e copiar o código para um novo projeto.

   Por exemplo, experimente utilizar o [elemento visual personalizado de curva polinomial](https://github.com/Microsoft/PowerBI-visuals-spline).

* Cada elemento visual do R aplica o operador `unique` à sua tabela de entrada. Para evitar a remoção de linhas idênticas, considere adicionar um campo de entrada extra com um ID exclusivo e ignore-o no código do R.   

* Se tiver uma conta do Power BI, utilize o serviço Power BI para desenvolver um elemento visual [no momento](./custom-visual-develop-tutorial.md) em vez de o reempacotar com o comando `pbiviz package`.

### <a name="html-widgets-gallery"></a>Galeria de widgets HTML
Explore elementos visuais na [galeria de widgets HTML](http://gallery.htmlwidgets.org/) para utilizar no seu próximo elemento visual. Para facilitar, criámos um [repositório de projetos de elementos visuais](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/multipleRHTML) com mais de 20 elementos visuais HTML interativos à escolha!

> [!TIP]
> Para mudar entre widgets html, utilize **Formatar** > **Definições** > **Tipo**. Experimente com [este ficheiro PBIX](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/multipleRHTML/assets/sample.pbix). 

#### <a name="to-use-a-sample-for-your-visual"></a>Para utilizar um exemplo para o seu elemento visual

1. Transfira toda a pasta.
1. Edite os ficheiros *script.r* e *dependencies.json* para manter apenas um widget.
1. Edite os ficheiros *capabilities.json* e *settings.ts* para remover o seletor `Type`.
1. Altere `const updateHTMLHead: boolean = true;` para `false` no ficheiro *visual.ts*. *(para melhor desempenho)*
1. Altere os metadados no ficheiro *pbiviz.json*, sendo o campo `guid` o mais importante.
1. Reempacote e continue a personalizar o elemento visual conforme pretendido. 

![Captura de ecrã a mostrar seis widgets mencionados anteriormente neste artigo.](./media/funnel-plot/diagram-four.PNG)

![Captura de ecrã a mostrar mais seis widgets mencionados anteriormente neste artigo.](./media/funnel-plot/diagram-five.PNG)

> [!NOTE]
> Nem todos os widgets neste projeto são suportados pelo serviço.

## <a name="next-steps"></a>Próximos passos

Para saber mais, veja mais tutoriais em [elementos visuais do Power BI](./custom-visual-develop-tutorial.md) e [elementos visuais do R](../../visuals/service-r-visuals.md).

Saiba como [desenvolver e submeter elementos visuais](https://powerbi.microsoft.com/documentation/powerbi-developer-office-store/) para a [Loja Office (galeria)](https://store.office.com/appshome.aspx?ui=en-US&rs=en-US&ad=US&clickedfilter=OfficeProductFilter%3aPowerBI&productgroup=PowerBI) ou, para ver mais exemplos, veja a [demonstração de scripts do R](https://community.powerbi.com/t5/R-Script-Showcase/bd-p/RVisuals)