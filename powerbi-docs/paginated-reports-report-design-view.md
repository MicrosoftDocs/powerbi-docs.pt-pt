---
title: Explorar a Vista de Estrutura de Relatório dos relatórios paginados
description: A Vista de Estrutura de Relatório no Report Builder é o espaço de estrutura para a criação de relatórios paginados que pode publicar no serviço Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 11/05/2018
ms.openlocfilehash: a77631cbf2438c00a8c05b196837b73b8dc6bb61
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874692"
---
# <a name="getting-around-in-report-design-view-for-paginated-reports"></a>Explorar a Vista de Estrutura de Relatório dos relatórios paginados

A Vista de Estrutura de Relatório no Report Builder do Power BI é o espaço de estrutura para a criação de relatórios paginados que pode publicar no serviço Power BI. A superfície de desenho está no centro do Report Builder, com o friso e os painéis em seu redor. A superfície de desenho é onde pode adicionar e organizar os seus itens de relatório. Este artigo explica os painéis que utiliza para adicionar, selecionar e organizar os recursos de relatório e alterar as propriedades do item de relatório.  

![Vista de Estrutura de Relatório do Report Builder](media/paginated-reports-report-design-view/power-bi-paginated-report-design-view.png)

1. [Painel Dados do relatório](#1-report-data-pane) 
2. [Superfície de desenho do relatório](#2-report-design-surface)  
3. [Painel Parâmetros](#3-parameters-pane) 
4. [Painel Propriedades](#4-properties-pane) 
5. [Painel Agrupamento](#5-grouping-pane) 
6. [Barra de estado do relatório atual](#6-current-report-status-bar)  
  
## <a name="1-report-data-pane"></a>1 Painel Dados do Relatório  
 No painel Dados do Relatório, vai definir os dados do relatório e os recursos de relatório que precisa para um relatório antes de criar o layout do relatório. Por exemplo, pode adicionar origens de dados, conjuntos de dados, campos calculados, parâmetros de relatórios e imagens ao painel Dados do Relatório.  
  
 Depois de adicionar itens ao painel Dados do Relatório, arraste os campos para os itens de relatório na superfície de desenho para controlar onde os dados são apresentados no relatório.  
  
> [!TIP]  
>  Se arrastar um campo do painel Dados do Relatório diretamente para a superfície de desenho do relatório em vez de o colocar numa região de dados, como uma tabela ou um gráfico, ao executar o relatório, verá apenas o primeiro valor dos dados nesse campo.  
  
 Também pode arrastar campos incorporados do painel Dados do Relatório para a superfície de desenho do relatório. Quando compostos, estes campos proporcionam informações sobre o relatório, como o nome do relatório, o número total de páginas no relatório e o número da página atual.  
  
 Alguns itens são adicionados automaticamente ao painel Dados do Relatório quando adicionar algo à superfície de desenho do relatório. Por exemplo, se incorporar uma imagem no relatório, ela será adicionada à pasta Imagens no painel Dados do Relatório.  
  
> [!NOTE]  
>  Pode utilizar o botão **Novo** para adicionar um novo item ao painel Dados do Relatório. Pode adicionar vários conjuntos de dados da mesma origem de dados ou de outras origens de dados ao relatório. Para adicionar um novo conjunto de dados da mesma origem de dados, clique com o botão direito do rato numa origem de dados > **Adicionar Conjunto de Dados**.  
  
## <a name="2-report-design-surface"></a>2 Superfície de desenho do relatório  
 A superfície de desenho do relatório do Report Builder é a principal área de trabalho para a criação de relatórios. Para colocar os itens de relatório, como regiões de dados, sub-relatórios, caixas de texto, imagens, retângulos e linhas no relatório, adicione-os à superfície de desenho a partir do friso ou da Galeria de Partes do Relatório. Aí, pode adicionar grupos, expressões, parâmetros, filtros, ações, visibilidade e formatação aos itens de relatório.  
  
 Também pode efetuar o seguinte:  
  
-   As propriedades do corpo do relatório, como a cor do limite e do preenchimento, ao clicar com o botão direito do rato na área branca da superfície de desenho, fora dos itens de relatório, e ao selecionar **Propriedades do Corpo**.  
  
-   As propriedades do cabeçalho e do rodapé, como a cor do limite e do preenchimento, ao clicar com o botão direito do rato na área branca da superfície de desenho na área do cabeçalho ou do rodapé, fora dos itens de relatório, e ao selecionar **Propriedades do Cabeçalho** ou **Propriedades do Rodapé**.  
  
-   As propriedades do relatório propriamente dito, como a configuração da página, ao clicar com o botão direito do rato na área cinzenta à volta da superfície de desenho e ao selecionar **Propriedades do Relatório**.  
  
-   As propriedades dos itens de relatório ao clicar com o botão direito do rato neles e ao selecionar **Propriedades**.  
  
### <a name="design-surface-size-and-print-area"></a>Área de impressão e de tamanho da superfície de desenho  
O tamanho da superfície de desenho pode ser diferente da área de impressão do tamanho de página que especificar para imprimir o relatório. Alterar o tamanho da superfície de desenho não mudará a área de impressão do relatório. Não importa qual o tamanho definido para a área de impressão do relatório, o tamanho da área da estrutura completo não será alterado. Para obter mais informações, veja Comportamentos de Composição. 
  
- Para apresentar a régua, no separador **Ver**, selecione a caixa de verificação **Régua**.  
  
## <a name="3-parameters-pane"></a>3 Painel Parâmetros  
 Com os parâmetros do relatório, pode controlar os dados dos relatórios, ligar os relatórios relacionados entre si e variar a apresentação do relatório. O painel Parâmetros fornece um esquema flexível para os parâmetros do relatório.  
  
 Saiba mais sobre os Parâmetros do Relatório   
  
## <a name="4-properties-pane"></a>4 Painel Propriedades
 Todos os itens num relatório, incluindo as regiões de dados, as imagens, as caixas de texto e o corpo do relatório propriamente dito, têm propriedades associadas. Por exemplo, a propriedade BorderColor de uma caixa de texto mostra o valor de cor do limite da caixa de texto e a propriedade PageSize do relatório mostra o tamanho de página do relatório.  
  
 Estas propriedades são apresentadas no painel Propriedades. As propriedades no painel mudam consoante o item de relatório que selecionar.  
  
- Para ver o painel Propriedades, no separador **Ver** no grupo **Mostrar/Ocultar**, selecione **Propriedades**.  
  
### <a name="changing-property-values"></a>Alterar os Valores das Propriedades  
 No Report Builder, pode alterar as propriedades dos itens de relatório de várias formas:  
  
-   Ao selecionar botões e listas no friso.  
  
-   Ao alterar as definições nas caixas de diálogo.  
  
-   Ao alterar os valores das propriedades no painel Propriedades.  
  
 As propriedades geralmente mais utilizadas estão disponíveis nas caixas de diálogo e no friso.  
  
 Dependendo da propriedade, pode definir o valor de uma propriedade numa lista pendente, digitar o valor ou selecionar `<Expression>` para criar uma expressão.  
  
### <a name="changing-the-properties-pane-view"></a>Alterar a Vista do Painel Propriedades  
 Por predefinição, as propriedades apresentadas no painel Propriedades estão organizadas em categorias amplas, como Ação, Limite, Preenchimento, Tipo de Letra e Geral. Cada categoria tem um conjunto de propriedades que lhe estão associadas. Por exemplo, as seguintes propriedades estão listadas na categoria Tipo de letra: Cor, FontFamily, FontSize, FontStyle, FontWeight, LineHeight e TextDecoration. Se preferir, pode alfabetizar todas as propriedades listadas no painel. Este procedimento remove as categorias e apresenta uma lista de todas as propriedades por ordem alfabética, independentemente da categoria.  
  
 O painel Propriedades tem três botões na parte superior do painel: **Categoria**, **Alfabetizar** e **Página de Propriedades**. Selecione os botões Categoria e Alfabetizar para alternar entre as vistas do painel Propriedades. Selecione o botão **Páginas de Propriedades** para abrir a caixa de diálogo de propriedades para um item de relatório selecionado.  
  
  
## <a name="5-grouping-pane"></a>5 Painel Agrupamento

 Os grupos servem para organizar os dados do relatório numa hierarquia visual e para calcular totais. Pode ver os grupos de linhas e de colunas numa região de dados na superfície de desenho e também no painel Agrupamento. O painel Agrupamento tem dois painéis: Grupos de Linhas e Grupos de Colunas. Quando seleciona uma região de dados, o painel Agrupamento apresenta todos os grupos nessa região de dados como uma lista hierárquica: os grupos subordinados são apresentados com avanço sob os grupos principais.  
  
 Pode criar grupos ao arrastar campos do painel Dados do Relatório e ao soltá-los na superfície de desenho ou no painel Agrupamento. No painel Agrupamento, pode adicionar os grupos principais, adjacentes e subordinados, alterar as propriedades dos grupos e eliminar grupos.  
  
 O painel Agrupamento é apresentado por predefinição, mas pode fechá-lo ao desmarcar a caixa de verificação do painel Agrupamento no separador Ver. O painel Agrupamento não está disponível para as regiões de dados do Gráfico ou do Medidor.  
  
 Para obter mais informações, veja Painel Agrupamento e Compreender os Grupos.  
  
## <a name="6-current-report-status-bar"></a>6 Barra de estado do relatório atual

A barra de estado do relatório atual mostra o nome do servidor a que o relatório está ligado ou mostra “Nenhum servidor para o relatório atual”. Pode selecionar **Ligar** para se ligar a um servidor.

## <a name="next-steps"></a>Próximos passos

[O que são relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md) 

  
  
