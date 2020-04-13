---
title: Exemplo de controlo da COVID-19 das autoridades locais e estaduais dos EUA
description: Transfira e modifique o relatório de exemplo com dados locais e estaduais dos EUA para a pandemia da COVID-19.
author: LukaszPawlowski-MS
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/06/2020
ms.author: lukaszp
LocalizationGroup: Samples
ms.openlocfilehash: 66e76c21e7d5171d24ff1518745a35947aa7ca42
ms.sourcegitcommit: e7fda395b47e404c61e961a60816b7a1b0182759
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80979782"
---
# <a name="covid-19-tracking-sample-for-us-state-and-local-governments"></a>Exemplo de controlo da COVID-19 das autoridades locais e estaduais dos EUA

A equipa do Power BI criou um exemplo de controlo da COVID-19 que permite às autoridades locais e estaduais dos EUA publicar ou personalizar um relatório interativo sobre a COVID-19. Com o Power BI Desktop, podem analisar e visualizar dados da COVID-19 para manter as comunidades informadas ao nível da cidade, do distrito, do estado e nacional. Em seguida, com a opção Publicar na Web do Power BI, podem partilhar o relatório publicamente para informar os cidadãos. O artigo oferece opções diferentes para utilizar as visualizações interativas do Power BI na sua própria história pública, blogue ou site.

:::image type="content" source="media/sample-covid-19-us/covid-19-us-tracking-sample.png" alt-text="Exemplo da COVID-19 com dados dos EUA":::

Este artigo aborda como:

- Copiar o código de incorporação e colocá-lo no seu próprio site. 
- Fazer personalizações, como formatação de um estado específico.
- Publicar no serviço Power BI.
- Publicar na Web. 
- Combinar estes dados com dados de outra origem. 

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar a utilizar o Power BI para contar a sua história, precisará destes pré-requisitos:

- Transferir a aplicação do [Power BI Desktop](https://powerbi.microsoft.com/desktop/) gratuita.
- Inscrever-se no [serviço Power BI](https://powerbi.microsoft.com/get-started/).

## <a name="option-1-pre-built-embed-code"></a>Opção 1: Código de incorporação pré-criado

A Microsoft publicou o relatório de exemplo e criou um código de incorporação para publicação na Web. Pode utilizar o código de incorporação para incorporar o exemplo completo, incluindo a vista nacional, e desagregar para o nível estadual e distrital no seu próprio site. Antes de publicar estes dados, recomendamos que reveja as [exclusões de responsabilidade](#disclaimers) neste artigo.

Para incluir o gráfico interativo no site, copie e cole o seguinte código de incorporação onde quer que o gráfico apareça na página Web.  

```
<iframe width="1600" height="900" src="https://app.powerbi.com/view?r=eyJrIjoiMmI2ZjExMzItZTcwNy00YmUwLWFlMTAtYTUxYzVjODZmYjA5IiwidCI6ImMxMzZlZWMwLWZlOTItNDVlMC1iZWFlLTQ2OTg0OTczZTIzMiIsImMiOjF9" frameborder="0" allowFullScreen="true"></iframe>
```

O código de incorporação é um elemento iFrame HTML que pode inserir em qualquer página HTML. Ajuste a largura e a altura do iFrame fornecido para caber dentro do site. O relatório de exemplo é criado com as proporções 16:9, por isso, escolha um tamanho para preservar esta dimensão. Quando implementado corretamente, o gráfico aparece sem limites cinzentos extra. É útil que reveja [as sugestões e truques de dimensões do iFrame](../service-publish-to-web.md#tips-and-tricks-for-iframe-height-and-width) ao fazer estas alterações.

## <a name="option-2-customize-the-sample-power-bi-file"></a>Opção 2: Personalizar o ficheiro do Power BI de exemplo

O ficheiro do Power BI contém os dados e o gráfico interativo num formato de ficheiro .pbix que pode editar no Power BI Desktop.  

Uma personalização típica consiste em filtrar o relatório para um estado específico e, em seguida, criar o seu próprio código de incorporação para publicação na Web para o seu relatório personalizado.

Os dados da USAFacts são fornecidos ao abrigo de uma Licença Creative Commons que requer atribuição. Antes de publicar estes dados, reveja as [exclusões de responsabilidade](#disclaimers).

Para começar, [transfira o ficheiro .pbix (aqui)](https://go.microsoft.com/fwlink/?linkid=2125058).

### <a name="update-your-report"></a>Atualizar o relatório 

1. Transfira a versão mais recente da aplicação gratuita, [Power BI Desktop](https://powerbi.microsoft.com/desktop/), caso ainda não o tenha feito. 

2. Transfira o [ficheiro .pbix](https://go.microsoft.com/fwlink/?linkid=2125058), caso ainda não o tenha feito, e abra-o no Power BI Desktop.

3. Para filtrar o relatório para um estado específico, selecione a seta para expandir o painel Filtros.

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filters-pane.png" alt-text="Expandir o painel Filtros":::

4. Selecione um estado do seu interesse. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filter-selection.png" alt-text="Selecionar um estado":::

5. Para guardar o ficheiro, selecione **Ficheiro** > **Guardar**. 

### <a name="refresh-your-report"></a>Atualizar o relatório 

1. Selecione o botão **Atualizar**.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-refresh-button.png" alt-text="Botão Atualizar":::

2. Selecione **Anónimo**  > **Ligar**. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-azure-blob.png" alt-text="Selecionar Anónimo":::

 
3. Selecione **Ignorar Níveis de Privacidade**, se forem mostrados > **Guardar**. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-privacy-levels.png" alt-text="Selecionar níveis de privacidade":::

### <a name="publish-your-report-to-the-power-bi-service"></a>Publicar o relatório no serviço Power BI

Depois de personalizar o relatório ao seu gosto, [siga os passos aqui indicados para o publicar](../desktop-upload-desktop-files.md) no serviço Power BI.

### <a name="configure-scheduled-refresh"></a>Configurar a atualização agendada

Para manter os dados atualizados no relatório, pode [configurar a atualização programada](../refresh-scheduled-refresh.md) depois de publicar o relatório.

Quando seguir os passos, escolha as seguintes opções:

1. Método de Autenticação de Credenciais de Origem de Dados: Anónimo
2. Definição do nível de privacidade para esta origem de dados: Público

Para testar a definição da atualização, selecione a opção [Atualizar agora](../refresh-data.md#data-refresh), disponível no item do conjunto de dados.

Os dados atualizados são carregados cada vez que o agendamento é executado. Os dados subjacentes são fornecidos pela USAFacts e podem não ser atualizados com a mesma frequência com que o agendamento é atualizado. Veja o [site da USAFacts](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/) para saber quando os dados subjacentes foram atualizados pela última vez. 

Se quiser publicar o relatório personalizado no site, o melhor é configurar a atualização agendada para ser executada pelo menos com a frequência com que os dados da USAFacts são atualizados. Uma vez que a USAFacts pode atualizar os dados em horários diferentes todos os dias, aconselhamos a que configure várias atualizações por dia. 

### <a name="create-a-publish-to-web-embed-code"></a>Criar um código de incorporação para publicação na Web 

Para incorporar o relatório personalizado no seu próprio site, siga as instruções para [criar o seu próprio código de incorporação para publicação na Web](../service-publish-to-web.md#how-to-use-publish-to-web).

Assim que publicar o código de incorporação, utilize o iFrame na caixa de diálogo de confirmação para incorporar no site.

Se fizer alterações ao relatório no Power BI Desktop, poderá publicar e substituir o relatório existente no serviço Power BI. O código de incorporação não muda. Demora aproximadamente uma hora para que as alterações ao relatório ou os dados atualizados apareçam no site. 

## <a name="option-3-mash-up-data-from-another-source"></a>Opção 3: Combinar dados de outra origem 

Também pode combinar os dados deste relatório com dados de outra origem. O exemplo a seguir baseia-se em dados da [Johns Hopkins University](https://github.com/CSSEGISandData/COVID-19). Antes de publicar estes dados, recomendamos que reveja as [exclusões de responsabilidade](#disclaimers) neste artigo.

1. Selecione **Obter Dados** > **Web**.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-get-data.png" alt-text="Botão Obter dados":::

2. Introduza o seguinte URL:

    ```
    https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv
    ```

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-from-web.png" alt-text="Selecionar dados da Web":::

3. Selecione **OK**. 

    > [!NOTE]
    > A ligação publicada pela Johns Hopkins University pode mudar. Veja a [página do GitHub da Johns Hopkins](https://github.com/CSSEGISandData/COVID-19) para obter as informações mais recentes.

4. Selecione **Carregar** para carregar o conjunto de dados do total de casos confirmados em todo o mundo.  

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-load-data.png" alt-text="Carregar dados da Web":::

    Este artigo, [Ligar a páginas Web do Power BI Desktop](../desktop-connect-to-web.md), contém mais informações sobre o carregamento de dados a partir da Web.
    
Em seguida, pode utilizar o Power BI Desktop para visualizar os dados. Por fim, utilize os passos na **Opção 2:** [Publicar o relatório no serviço Power BI](#publish-your-report-to-the-power-bi-service) para publicar o relatório e criar um código de incorporação personalizado. 

## <a name="option-4-use-the-covid-19-us-tracking-template-app"></a>Opção 4: utilizar a aplicação de modelo COVID-19 US Tracking (Rastreio da COVID-19 nos EUA)

Para obter mais uma opção, a equipa do Power BI criou a *aplicação de modelo* COVID-19 US Tracking (Rastreio da COVID-19 nos EUA) para começar imediatamente. As aplicações de modelo são grupos de relatórios, dashboards e conjuntos de dados para uma origem de dados específica. Pode transferi-las a partir do AppSource, utilizá-las ou modificá-las para atender às suas necessidades e distribuí-las aos seus colegas. 

Esta aplicação de modelo COVID-19 US Tracking (Rastreio da COVID-19 nos EUA) contém um relatório pré-criado de métricas da COVID-19 que pode utilizar tal como está, personalizar diretamente no serviço Power BI ou transferir para adicionar outras origens de dados, se quiser. Saiba como instalar a [aplicação de modelo COVID-19 US Tracking (Rastreio da COVID-19 nos EUA)](../connect-data/service-connect-to-covid-19-tracking.md) e começar imediatamente.

## <a name="about-the-data-source-for-this-report"></a>Acerca da origem de dados deste relatório
Este relatório interativo agrega dados dos Centros de Controlo e Prevenção de Doenças (CDC) e das agências de saúde pública a nível estadual e local dos EUA. Os dados a nível distrital são confirmados ao referirem diretamente as agências estaduais e locais (ligação).

Os dados são fornecidos pela USAFacts. Devido à frequência das atualizações dos dados, estes podem não refletir os números exatos relatados pelas organizações governamentais ou pelos meios de comunicação social. Para obter mais informações ou para transferir os dados, visite o [site da USAFacts](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/). 

## <a name="disclaimers"></a>Exclusões de Responsabilidade

Este relatório e respetivos dados são fornecidos “tal como estão”, “com todas as falhas” e sem qualquer tipo de garantia. A Microsoft não oferece garantias nem garantias expressas e exclui expressamente qualquer responsabilidade relativa a garantias implícitas, incluindo de comercialização, de adequação a um fim específico e de não violação de direitos de autor.

Os dados da USAFacts estão disponíveis ao abrigo de uma licença Creative Commons. Para a utilizar, cite a USAFacts como o fornecedor de dados e indique uma ligação para a USAFacts. Para obter os passos de atribuição exatos, veja a secção **#MadewithUSAFacts** da página da USAFacts, [Coronavirus in the United States: Mapping the COVID-19 outbreak in the states and counties](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/) (Coronavírus nos EUA: mapear o surto da COVID-19 nos vários estados e distritos).

Os dados da Johns Hopkins University estão sujeitos aos direitos de autor de 2020 da Johns Hopkins University, todos os direitos reservados. São disponibilizados ao público estritamente para fins de investigação educacional e académica. Seguem-se os [Termos de Utilização](https://github.com/CSSEGISandData/COVID-19/blob/master/README.md) completos dos dados mostrados no exemplo de combinação de dados. Estão disponíveis mais informações no [site da Johns Hopkins University](https://coronavirus.jhu.edu/map-faq.html).

## <a name="next-steps"></a>Próximos passos

[Obter exemplos para o Power BI](../sample-datasets.md)