---
title: Mapas de Manchas (Coropletos) no Power BI
description: Documentação sobre a criação de Mapas de Manchas (Coropletos) no Power BI
author: mihart
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/19/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 9c35e97fba55230277f9f144a5155071656b6add
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73870966"
---
# <a name="filled-maps-choropleths-in-power-bi"></a>Mapas de manchas (coropletos) no Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Um mapa de manchas utiliza sombreado, tonalidade ou padrões para mostrar como um valor difere em proporção numa localização geográfica ou região.  Exiba rapidamente estas diferenças relativas com sombreado que varia de claro (menos frequente/inferior) a escuro (mais frequente/mais).    

![Mapa dos E.U.A.](media/power-bi-visualization-filled-maps-choropleths/large-map.png)

## <a name="what-is-sent-to-bing"></a>O que é enviado ao Bing
O Power BI está integrado no Bing para fornecer coordenadas de mapa predefinidas (um processo denominado geocodificação). Quando cria uma visualização de mapa no serviço Power BI ou Power BI Desktop, os dados nos registos **Localização**, **Latitude** e **Longitude** (que estão a ser utilizados para criar a visualização) são enviados ao Bing.

O utilizador ou o administrador, pode ter que atualizar a sua firewall para permitir o acesso aos URLs que o Bing utiliza para geocodificação.  Os URLs são:
- https://dev.virtualearth.net/REST/V1/Locations    
- https://platform.bing.com/geo/spatial/v1/public/Geodata    
- https://www.bing.com/api/maps/mapcontrol

Para obter mais informações sobre os dados enviados ao Bing e obter sugestões para aumentar o êxito da geocodificação, veja [Sugestões e truques para visualizações de mapas](power-bi-map-tips-and-tricks.md).

## <a name="when-to-use-a-filled-map"></a>Quando utilizar um mapa de manchas
Os mapas de manchas são uma ótima opção:

* para apresentar informações quantitativas num mapa.
* para mostrar as relações e os padrões espaciais.
* quando os dados são padronizados.
* ao trabalhar com dados socioeconómicos.
* quando as regiões definidas são importantes.
* para obter uma visão geral da distribuição entre as localizações geográficas.

### <a name="prerequisites"></a>Pré-requisitos
Este tutorial utiliza o [ficheiro PBIX do Exemplo de Análise de Revenda](https://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix).
1. Na secção superior esquerda da barra de menus, selecione **Ficheiro** > **Abrir**.
   
2. Procure a sua cópia do **ficheiro PBIX do Exemplo de Análise de Revenda**

1. Abra o **Ficheiro PBIX do Exemplo de Análise de Revenda** na vista de relatório ![Captura de ecrã a mostrar o ícone da vista de relatório](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Selecionar ![Captura de ecrã do separador amarelo.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para adicionar uma nova página.


## <a name="create-a-basic-filled-map"></a>Criar um mapa de manchas básico
Neste vídeo, a Rita cria um mapa básico e converte-o num mapa de manchas.
   > [!NOTE]
   > Este vídeo utiliza uma versão anterior do Power BI Desktop.
   > 
   > 

<iframe width="560" height="315" src="https://www.youtube.com/embed/ajTPGNpthcg" frameborder="0" allowfullscreen></iframe>

### <a name="create-a-filled-map"></a>Criar um mapa de manchas
1. No painel Campos, selecione o campo **Geo** \> **Estado**.    

   ![Marca de verificação amarela junto a State](media/power-bi-visualization-filled-maps-choropleths/power-bi-state.png)
2. [Converta o gráfico](power-bi-report-change-visualization-type.md) num mapa de manchas. Repare que o **Estado** está, agora, no grupo **Local**. O Bing Maps usa o campo no grupo **Local** para criar o mapa.  O local pode ser uma variedade de locais válidos: países, estados, condados, cidades, CEPs ou outros códigos postais, etc. O Bing Maps fornece formas de mapa de manchas para locais em todo o mundo. Sem uma entrada válida no painel Localização, o Power BI não pode criar o mapa de manchas.  

   ![Modelos com o ícone de mapa de manchas realçado](media/power-bi-visualization-filled-maps-choropleths/img003.png)
3. Filtre o mapa para apresentar apenas os Estados Unidos.

   a.  Na parte esquerda do painel Visualizações, procure o painel **Filtros**. Expanda-o se estiver minimizado

   b.  Passe o rato sobre **Estado** e selecione a divisa de expansão  
   ![Filtros de nível visual a mostrar State (Tudo)](media/power-bi-visualization-filled-maps-choropleths/img004.png)

   c.  Coloque uma marca de verificação junto a **Todos** e remova a marca de verificação junto a **AK**.

   ![Menu pendente State com as opções Tudo e AK não selecionadas](media/power-bi-visualization-filled-maps-choropleths/img005.png)
4. Selecione o ícone de rolo de tinta para abrir o painel Formatação e selecione **Cores de dados**.

    ![Painel de formatação que mostra a opção de Cores de dados](media/power-bi-visualization-filled-maps-choropleths/power-bi-data-color.png)

5. Selecione o ícone de três pontos verticais e selecione **Formatação condicional**.

    ![Botão de formatação condicional de cores de dados](media/power-bi-visualization-filled-maps-choropleths/power-bi-conditional-formatting.png)

6. Utilize o ecrã **Cor predefinida - Cores de dados** para determinar como é que o mapa de manchas será sombreado. As opções disponíveis incluem o campo no qual o sombreado se irá basear e como o aplicar. Neste exemplo, estamos a utilizar o campo **Sentimento** > **SalesFact** e a definir o valor mais baixo como vermelho e o valor mais alto como verde. Os valores que ficarem entre o número máximo e o mínimo terão tons de vermelho e verde. A ilustração na parte inferior do ecrã mostra a variedade de cores que vai ser utilizada. 

    ![Painel de cor padrão com o Sentimento selecionado](media/power-bi-visualization-filled-maps-choropleths/power-bi-sentiment.png)

7. O mapa de manchas é sombreado a verde e vermelho, com o vermelho a representar os números de sentimento inferiores e o verde a representar o sentimento superior mais positivo.  Para apresentar detalhes adicionais, arraste um campo para a zona das Descrições.  Aqui, adicionei o **Intervalo de Sentimento** e destaquei o estado de Idaho (ID). Podemos ver que o intervalo de sentimento é baixo (6).
   ![mapa de manchas que mostra as descrições de Idaho](media/power-bi-visualization-filled-maps-choropleths/power-bi-filled-map-idaho.png)

10. [Guarde o relatório](../service-report-save.md).

O Power BI permite controlar praticamente todo o aspeto do mapa de manchas. Experimente estes controlos de cores de dados até obter o aspeto desejado. 

## <a name="highlighting-and-cross-filtering"></a>Realce e filtragem cruzada
Para obter informações sobre como utilizar o painel Filtros, veja [Adicionar um filtro a um relatório](../power-bi-report-add-filter.md).

Destacar um local num Mapa de Manchas faz a filtragem cruzada com outras visualizações na página do relatório e vice-versa.

1. Para acompanhar, guarde primeiro este relatório ao selecionar **Ficheiro > Guardar**. 

2. Copie o mapa de manchas através de Ctrl+C.

3. Na parte inferior da tela do relatório, selecione o separador **Sentimento** para abrir a página de relatório de Sentimentos.

    ![Separador Sentimento selecionado](media/power-bi-visualization-filled-maps-choropleths/power-bi-sentiment-tab.png)

4. Mova e redimensione as visualizações na página para libertar algum espaço. Em seguida, utilize Ctrl+V para colar o mapa de manchas do relatório anterior. Veja as seguintes imagens.

   ![Mapa de manchas adicionado à página de Sentimentos](media/power-bi-visualization-filled-maps-choropleths/power-bi-map.png)

5. No mapa de manchas, selecione um estado.  As outras visualizações na página serão apresentadas com realce cruzado e com filtragem cruzada. A seleção de **Texas**, por exemplo, mostra que o Sentimento é 75 e que Texas se encontra no Distrito Central N.º 23.   
   ![Texas selecionado](media/power-bi-visualization-filled-maps-choropleths/power-bi-texas.png)
2. Selecione um ponto de dados no gráfico de linhas VanArsdel – Sentimentos por Mês. Isto filtra o mapa de manchas para mostrar dados de Sentimento para VanArsdel e não para a concorrência de VanArsdel.  
   ![novo sombreado](media/power-bi-visualization-filled-maps-choropleths/power-bi-yes.png)

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
Os dados de mapa podem ser ambíguos.  Por exemplo, existe Paris, França, mas também existe Paris, Texas. Os dados geográficos são, provavelmente, armazenados em colunas separadas – uma coluna de nomes de cidades, uma coluna de nomes de estado ou província, etc. – portanto, o Bing pode não ser capaz de dizer que Paris é. Se o conjunto de dados já contém dados de latitude e longitude, o Power BI tem campos especiais para ajudar a tornar os dados do mapa inequívocos. Basta arrastar o campo que contém os dados de latitude na área Visualizações \> Latitude.  E faça o mesmo para os dados de longitude.    

![Painéis Visualizações e Campos](media/power-bi-visualization-filled-maps-choropleths/pbi-latitude.png)

Se tiver permissões para editar o conjunto de dados no Power BI Desktop, veja este vídeo para ajudar a resolver a ambiguidade do mapa.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Co2z9b-s_yM" frameborder="0" allowfullscreen></iframe>

Se não tiver acesso aos dados de latitude e longitude, mas tiver acesso de edição ao conjunto de dados, [siga estas instruções para atualizar o conjunto de dados](https://support.office.com/article/Maps-in-Power-View-8A9B2AF3-A055-4131-A327-85CC835271F7).

Para obter mais ajuda com visualizações de mapas, veja [Sugestões e truques para visualizações de mapas](../power-bi-map-tips-and-tricks.md).

## <a name="next-steps"></a>Próximos passos

[Mapa de forma](desktop-shape-map.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)