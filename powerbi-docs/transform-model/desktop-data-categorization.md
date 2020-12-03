---
title: Categorização de dados no Power BI Desktop
description: Categorização de dados no Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 01/15/2020
LocalizationGroup: Model your data
ms.openlocfilehash: d99eb0355d414a9e1627da0b5629eaf45cbaf18d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415801"
---
# <a name="specify-data-categories-in-power-bi-desktop"></a>Especificar categorias de dados no Power BI Desktop
No Power BI Desktop, pode especificar a *categoria de dados* de uma coluna para que o Power BI Desktop saiba como tratar esses valores numa visualização.

Quando o Power BI Desktop importa dados, obtém outras informações além dos próprios dados, tais como os nomes de tabelas e colunas, e se os dados são uma chave primária. Com essas informações, o Power BI Desktop faz algumas suposições sobre como lhe proporcionar uma boa experiência predefinida quando criar uma visualização.
Por exemplo, quando uma coluna tem valores numéricos, é provável que o utilizador queira agregá-la de algum modo para que o Power BI Desktop a coloque na área **Valores** do painel **Visualizações**. Por outro lado, no caso de uma coluna com valores de data e hora num gráfico de linhas, o Power BI Desktop pressupõe que a utilizará provavelmente como um eixo de hierarquia de tempo.

No entanto, existem alguns casos que são um pouco mais difíceis, como geografia. Considere a seguinte tabela de uma folha de cálculo do Excel:

![Captura de ecrã a mostrar o Excel, com dados tabulares que vão ser importados para o Power B I Desktop.](media/desktop-data-categorization/datacategorizationtable.png)

O Power BI Desktop deve tratar os códigos na coluna **GeoCode** como uma abreviatura de um País ou um Estado dos EUA?  Não é claro, porque um código como este pode significar qualquer uma dessas opções. Por exemplo, AL pode significar Alabama ou Albânia, AR pode significar Arkansas ou Argentina, CA pode significar Califórnia ou Canadá. Isto faz diferença quando vamos criar um gráfico do campo GeoCode num mapa. 

O Power BI Desktop deve mostrar uma imagem do mundo com países realçados? Ou deve mostrar uma imagem dos Estados Unidos com estados realçados?  Pode especificar uma categoria de dados para dados como estes. A categorização de dados refina ainda mais as informações que o Power BI Desktop pode utilizar para fornecer as melhores visualizações.  

**Para especificar uma categoria de dados**

1. Na Vista de **Relatório** ou de **Dados**, na lista **Campos**, selecione o campo que pretende ordenar por uma categorização diferente.
2. No friso, na área **Propriedades** do separador **Modelação**, selecione a seta pendente ao lado de **Categoria de Dados**.  Esta lista mostra as categorias de dados que pode escolher para a coluna. Algumas seleções podem ser desativadas se não funcionarem com o tipo de dados atual da coluna.  Por exemplo, se uma coluna for um tipo de dados de data ou hora, o Power BI Desktop não permite que selecione categorias de dados geográficos. 
3. Selecione a categoria que pretende.

   ![Captura de ecrã a mostrar o Power B I Desktop com o filtro Categoria de Dados.](media/desktop-data-categorization/desktop-data-categorization.png)

Pode também ter interesse em conhecer a [filtragem geográfica para aplicações móveis do Power BI](desktop-mobile-geofiltering.md).