---
title: "Exportar dados de uma visualização do Power BI"
description: "Exporte dados de uma visualização de relatório e visualização de dashboard e veja-os no Excel."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: jtlLGRKBvXY
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/20/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: b5e5463f19c95106a026770ad987f013f472e541
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="export-data-from-visualizations"></a>Exportar dados de visualizações
Se pretende ver os dados que são utilizados para criar uma visualização, pode [apresentar os dados no Power BI](service-reports-show-data.md) ou exportar esses dados para o Excel como um ficheiro .xlsx ou .csv.   

Veja o Will a exportar os dados a partir de uma das visualizações no seu relatório, a guardá-los como um ficheiro .xlsx e a abri-lo no Excel. Em seguida, siga as instruções passo-a-passo abaixo do vídeo para experimentar.

<iframe width="560" height="315" src="https://www.youtube.com/embed/KjheMTGjDXw" frameborder="0" allowfullscreen></iframe>

## <a name="from-a-visualization-on-a-power-bi-dashboard"></a>A partir de uma visualização num dashboard do Power BI
1. Selecione as reticências no canto superior direito da visualização.
   
    ![](media/power-bi-visualization-export-data/pbi-export-tile3.png)
2. Escolha o ícone **Exportar dados**.
   
    ![](media/power-bi-visualization-export-data/pbi_export_dash.png)
3. Os dados são exportados para um ficheiro .csv. Se o elemento visual estiver filtrado, os dados transferidos também estarão filtrados.
4. O browser pedirá para guardar o ficheiro.  Depois de guardado, abra o ficheiro .csv no Excel.
   
    ![](media/power-bi-visualization-export-data/pbi-export-to-excel.png)

## <a name="from-a-visualization-in-a-report"></a>A partir de uma visualização num relatório
Para acompanhar, abra o [relatório de Exemplo de análise de aprovisionamento](sample-procurement.md) na [Vista de edição](service-reading-view-and-editing-view.md). [Adicione uma nova página em branco do relatório](power-bi-report-add-page.md). Em seguida, siga os passos abaixo para adicionar uma agregação e um filtro de nível de visualização.

1. Crie um novo gráfico de colunas.  No painel Campos, selecione **Localização > Cidade** e **Fatura > Percentagem de desconto**.  Poderá ter de mover o campo **Percentagem de Desconto** para o conjunto de campos Valor. 
   
    ![](media/power-bi-visualization-export-data/power-bi-export-data3.png)
2. Altere a agregação para **Percentagem de desconto** de **Contagem** para **Média**. Na área Valor, selecione a seta à direita de **Percentagem de desconto** (poderá dizer **Contagem de Percentagem de Desconto**) e escolha **Média**.
   
    ![](media/power-bi-visualization-export-data/power-bi-export-data6.png)
3. Adicione um filtro a **Cidade** para remover **Atlanta**.
   
   ![](media/power-bi-visualization-export-data/power-bi-export-data4.png)
   
   Agora, estamos prontos para experimentar ambas as opções para exportar dados.
4. Selecione as reticências no canto superior direito da visualização. Escolha **Exportar dados**.
   
   ![](media/power-bi-visualization-export-data/power-bi-export-data2.png)
5. Se a visualização tiver uma agregação (um exemplo seria se tivesse alterado **Contagem** para *média*, **soma** ou *mínimo*), terá duas opções: **Dados resumidos** e **Dados subjacentes**. Para o ajudar a compreender as agregações, veja [Agregações no Power BI](service-aggregates.md).
   
    ![](media/power-bi-visualization-export-data/power-bi-export-data5.png)
6. Selecione **Dados resumidos** > **Exportar** e escolha .xlsx ou .csv. O Power BI exporta os dados.  Se tiver aplicado filtros à visualização, os dados exportados irão exportar como filtrados. Quando seleciona **Exportar**, o browser pede-lhe para guardar o ficheiro. Depois de guardado, abra o ficheiro no Excel.
   
   **Dados resumidos**: selecione esta opção se não tiver uma agregação ou se tiver uma agregação, mas não quiser ver a divisão completa. Por exemplo, se tiver um gráfico de barras que mostra 4 barras, irá obter 4 linhas de dados. Os dados resumidos estão disponíveis como .xlsx e .csv.
   
   Neste exemplo, a nossa exportação de Excel mostra um total para cada cidade. Uma vez que filtrámos Atlanta, este campo não está incluído nos resultados.  A primeira linha da nossa folha de cálculo mostra os filtros que foram utilizados quando extraímos os dados do Power BI.
   
   ![](media/power-bi-visualization-export-data/power-bi-export-data7.png)
7. Agora, experimente selecionar **Dados subjacentes** > **Exportar** e escolher .xlsx. O Power BI exporta os dados. Se tiver aplicado filtros à visualização, os dados exportados irão exportar como filtrados. Quando seleciona **Exportar**, o browser pede-lhe para guardar o ficheiro. Depois de guardado, abra o ficheiro no Excel.
   
   >[!WARNING]
   >Exportar dados subjacentes permite aos utilizadores ver todos os dados detalhados – todas as colunas nos dados. Os administradores do serviço Power BI podem desativar esta definição para a sua organização. Se for proprietário de um conjunto de dados, pode definir as colunas proprietárias como "ocultas", para que não sejam apresentadas na lista de campos no Desktop ou no serviço Power BI.
   
   
   **Dados subjacentes**: selecione esta opção se a visualização tiver uma agregação e pretender ver todos os detalhes subjacentes. Basicamente, selecionar *Dados subjacentes* remove a agregação. Quando seleciona **Exportar**, os dados são exportados para um ficheiro .xlsx e o browser pede-lhe para guardar o ficheiro. Depois de guardado, abra o ficheiro no Excel.
   
   Neste exemplo, a nossa exportação de Excel mostra uma linha para cada linha de Cidade no nosso conjunto de dados e a percentagem de desconto para essa entrada individual. Por outras palavras, os dados são simplificados e não agregados. A primeira linha da nossa folha de cálculo mostra os filtros que foram utilizados quando extraímos os dados do Power BI.  
   
   ![](media/power-bi-visualization-export-data/power-bi-export-data8.png)

## <a name="limitations-and-considerations"></a>Limitações e considerações
* O número máximo de linhas que podem ser exportadas do **Power BI Desktop** e do **serviço Power BI** para .csv é 30 000.
* O número máximo de linhas que podem ser exportadas para .xlsx é 150.000.
* Exportar com os *Dados subjacentes* não irá funcionar se a origem de dados for uma ligação em direto do Analysis Services e a versão for mais antiga que 2016 e as tabelas no modelo não tiverem uma chave exclusiva.  
* Exportar com os *Dados subjacentes* não irá funcionar se a opção *Mostrar itens sem dados* estiver ativada para a visualização a ser exportada.
* Ao utilizar DirectQuery, a quantidade máxima de dados que podem ser exportados é 16 MB. Esta limitação pode ter como consequência exportar menos do que o número máximo de linhas, sobretudo se existirem muitas colunas, os dados serem difíceis de comprimir e outros fatores que aumentam o tamanho do ficheiro e diminuem o número de linhas exportadas.
* O Power BI suporta apenas a exportação em elementos visuais que utilizam agregações básicas. A exportação não está disponível para os elementos visuais que utilizam medidas de relatório ou modelo.
* Atualmente, não são suportados elementos visuais personalizados e elementos visuais R.
* A exportação de dados não está disponível para utilizadores fora da sua organização que utilizem um dashboard que foi partilhado com os mesmos. 
* Se existir um caráter unicode no ficheiro .csv, o texto no Excel pode não aparecer corretamente. Contudo, se abrir o ficheiro no Bloco de notas, o texto será apresentado corretamente. Exemplos de carateres unicode são símbolos de moeda e palavras estrangeiras. A solução para este problema consiste em importar o ficheiro csv para o Excel, em vez de abrir o csv diretamente. Para tal:
  
  1. Abrir o Excel
  2. No separador **Dados**, selecione **Obter dados externos** > **Do texto**.
* Os administradores do Power BI têm a capacidade de desativar a exportação de dados.

## <a name="next-steps"></a>Passos seguintes
[Dashboards no Power BI](service-dashboards.md)  
[Relatórios no Power BI](service-reports.md)  
[Power BI - Conceitos Básicos](service-basic-concepts.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

