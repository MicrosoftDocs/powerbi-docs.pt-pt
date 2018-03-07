---
title: Mapas de Manchas (Coropletos) no Power BI (Tutorial)
description: "Documentação – tutorial sobre a criação de Mapas de Manchas (Coropletos) no Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/19/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: b0d4e1cd766cf5f1b35b5d0a6ca0946820efe9f3
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="filled-maps-choropleths-in-power-bi-tutorial"></a>Mapas de manchas (coropletos) no Power BI (Tutorial)
Um mapa de manchas utiliza sombreado, tonalidade ou padrões para mostrar como um valor difere em proporção numa localização geográfica ou região.  Exiba rapidamente estas diferenças relativas com sombreado que varia de claro (menos frequente/inferior) a escuro (mais frequente/mais).    

![](media/power-bi-visualization-filled-maps-choropleths/large_map.png)

## <a name="what-is-sent-to-bing"></a>O que é enviado ao Bing
O Power BI está integrado no Bing para fornecer coordenadas de mapa predefinidas (um processo denominado geocodificação). Quando cria uma visualização de mapa no serviço Power BI ou Power BI Desktop, os dados nos registos **Localização**, **Latitude** e **Longitude** (que estão a ser utilizados para criar a visualização) são enviados ao Bing.

O utilizador ou o administrador, pode ter que atualizar a sua firewall para permitir o acesso aos URLs que o Bing utiliza para geocodificação.  Os URLs são:
* https://dev.virtualearth.net/REST/V1/Locations
* https://platform.bing.com/geo/spatial/v1/public/Geodata
* https://www.bing.com/api/maps/mapcontrol

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
- Serviço Power BI ou Power BI Desktop
- Exemplo de Vendas e Marketing

Para acompanhar, o tutorial utiliza o serviço Power BI, não o Power BI Desktop.

## <a name="create-a-basic-filled-map"></a>Criar um mapa de manchas básico
Neste vídeo, a Rita cria um mapa básico e converte-o num mapa de manchas.

<iframe width="560" height="315" src="https://www.youtube.com/embed/ajTPGNpthcg" frameborder="0" allowfullscreen></iframe>


1. Para criar o seu próprio mapa de manchas, [transfira o exemplo Vendas e Marketing](sample-datasets.md) ao iniciar sessão no Power BI e ao selecionar **Obter Dados \> Exemplos \> Vendas e Marketing \> Ligar**.
2. Quando aparecer a mensagem de êxito, selecione **Ver conjunto de dados**.

   ![](media/power-bi-visualization-filled-maps-choropleths/power-bi-view-dataset.png)
3. O Power BI abre uma tela do relatório em branco na [Vista de Edição](service-interact-with-a-report-in-editing-view.md).

    ![](media/power-bi-visualization-filled-maps-choropleths/power-bi-blank-canvas.png)
4. No painel Campos, selecione o campo **Geo** \> **Estado**.    

   ![](media/power-bi-visualization-filled-maps-choropleths/img002.png)
5. [Converta o gráfico](power-bi-report-change-visualization-type.md) num mapa de manchas. Repare que o **Estado** está, agora, no grupo **Local**. O Bing Maps usa o campo no grupo **Local** para criar o mapa.  O local pode ser uma variedade de locais válidos: países, estados, condados, cidades, CEPs ou outros códigos postais, etc. O Bing Maps fornece formas de mapa de manchas para locais em todo o mundo. Sem uma entrada válida no painel Localização, o Power BI não pode criar o mapa de manchas.  

   ![](media/power-bi-visualization-filled-maps-choropleths/img003.png)
6. Filtre o mapa para apresentar apenas os Estados Unidos.

   a.  Na parte inferior do painel Visualizações, procure a área **Filtros** .

   b.  Passe o rato sobre **Estado** e clique na divisa de expansão  
   ![](media/power-bi-visualization-filled-maps-choropleths/img004.png)

   c.  Coloque uma marca de verificação ao lado de **Todos** e remova a marca de verificação ao lado de **AK**.

   ![](media/power-bi-visualization-filled-maps-choropleths/img005.png)
7. Selecione **SalesFact** \>  **Sentimento** para adicioná-lo ao painel **Saturação da cor**. O campo no painel **Valores** controla o sombreado do mapa.  
   ![](media/power-bi-visualization-filled-maps-choropleths/power-bi-color-saturation.png)
8. O mapa de manchas é sombreado a verde, com verde claro a representar os números de sentimento inferiores e verde escuro a representar o sentimento superior mais positivo.  Aqui, destacamos o estado de Wyoming (WY) e vemos que o Sentimento é muito bom, 74.  
   ![](media/power-bi-visualization-filled-maps-choropleths/img007.png)
9. [Guarde o relatório](service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Destaque e filtragem cruzada
Para obter informações sobre como utilizar o painel Filtros, veja [Add a filter to a report (Adicionar um filtro a um relatório)](power-bi-report-add-filter.md).

Destacar um local num Mapa de Manchas faz a filtragem cruzada com outras visualizações na página do relatório e vice-versa.

Para acompanhar, copie e cole o mapa de manchas na página **Sentimento** do relatório *Vendas e Marketing*.

1. No mapa de manchas, selecione um estado.  Isto destaca as outras visualizações na página. A seleção de **Texas**, por exemplo, mostra que o Sentimento é de 74, que Texas está no Distrito Central \#n.º 23 e que a maior parte do volume de vendas é proveniente dos segmentos Moderação e Conveniência.   
   ![](media/power-bi-visualization-filled-maps-choropleths/img008.png)
2. No gráfico de linhas, alterne entre **Não** e **Sim**. Isto filtra o Mapa de Manchas para mostrar o Sentimento para VanArsdel e para a concorrência de VanArsdel.  
   ![](media/power-bi-visualization-filled-maps-choropleths/img009.gif)

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
Os dados de mapa podem ser ambíguos.  Por exemplo, existe Paris, França, mas também existe Paris, Texas. Os dados geográficos são, provavelmente, armazenados em colunas separadas – uma coluna de nomes de cidades, uma coluna de nomes de estado ou província, etc. – portanto, o Bing pode não ser capaz de dizer que Paris é. Se o conjunto de dados já contém dados de latitude e longitude, o Power BI tem campos especiais para ajudar a tornar os dados do mapa inequívocos. Basta arrastar o campo que contém os dados de latitude na área Visualizações \> Latitude.  E faça o mesmo para os dados de longitude.  
![](media/power-bi-visualization-filled-maps-choropleths/pbi_latitude.png)

Se tiver permissões para editar o conjunto de dados no Power BI Desktop, veja este vídeo para ajudar a resolver a ambiguidade do mapa.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Co2z9b-s_yM" frameborder="0" allowfullscreen></iframe>

Se não tiver acesso aos dados de latitude e longitude, [siga estas instruções para atualizar o conjunto de dados](https://support.office.com/article/Maps-in-Power-View-8A9B2AF3-A055-4131-A327-85CC835271F7).

Para obter mais ajuda com visualizações de mapas, veja [Sugestões e truques para visualizações de mapas](power-bi-map-tips-and-tricks.md).

## <a name="next-steps"></a>Próximos passos
[Adicionar o mapa de manchas como um mosaico do dashboard (afixar o elemento visual)](service-dashboard-tiles.md)    
 [Adicionar uma visualização a um relatório](power-bi-report-add-visualizations-i.md)  
 [Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)    
 [Alterar o tipo de visualização que está a ser utilizado](power-bi-report-change-visualization-type.md)      
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)
