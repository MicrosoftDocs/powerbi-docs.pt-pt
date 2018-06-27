---
title: Categorização de dados no Power BI Desktop
description: Categorização de dados no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 9fa7310b3d0a20a588b2cc26fc0df177f3d0ab70
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/26/2018
ms.locfileid: "34285422"
---
# <a name="data-categorization-in-power-bi-desktop"></a>Categorização de dados no Power BI Desktop
No **Power BI Desktop**, pode especificar a Categoria de Dados para uma coluna de modo a que o Power BI Desktop saiba como deve tratar os respetivos valores numa visualização.

Quando o Power BI Desktop importa dados, não obtém apenas os dados em si, mas também informações como os nomes de tabela e coluna, se é ou não uma chave primária, etc.  Com essas informações, o Power BI Desktop faz algumas suposições sobre como lhe proporcionar uma boa experiência predefinida quando criar uma visualização. 

Eis um exemplo: quando o Power BI Desktop deteta que uma coluna tem valores numéricos, é provável que o utilizador deseje agregá-la de algum modo, para que ela seja colocada na área Valores. Ou, para uma coluna com valores de data e hora, assume que a utilizará provavelmente como um eixo de hierarquia de tempo num gráfico de linhas.

No entanto, existem alguns casos que são um pouco mais difíceis, como geografia. Considere a seguinte tabela de uma folha de cálculo do Excel:

![](media/desktop-data-categorization/datacategorizationtable.png)

O Power BI Desktop deve tratar os códigos na coluna GeoCode como uma abreviatura de um País ou um Estado dos EUA?  Não é claro, porque um código como este pode significar qualquer uma dessas opções.  Por exemplo, AL pode significar Alabama ou Albânia, AR pode significar Arkansas ou Argentina, CA pode significar Califórnia ou Canadá. Isto faz diferença quando vamos criar um gráfico do campo GeoCode num mapa.  O Power BI Desktop deve mostrar uma imagem do mundo com os países realçados ou uma imagem dos Estados Unidos com os estados realçados?  Pode especificar uma Categoria de Dados para dados exatamente como estes. A categorização de dados refina ainda mais as informações que o Power BI Desktop pode utilizar para fornecer as melhores visualizações.  

**Para especificar uma Categoria de Dados**

1. Na Vista de Relatório ou de Dados, na lista **Campos**, selecione o campo que deseja classificar por uma categorização diferente.
2. No friso, no separador **Modelação**, clique na lista pendente **Categoria de Dados:**.  Isto mostra a lista de categorias de dados possíveis que pode escolher para a coluna.  Algumas seleções podem estar desativadas se não funcionarem com o tipo de dados atual da coluna.  Por exemplo, se uma coluna for um tipo de dados binário, o Power BI Desktop não permite que escolha categorias de dados geográficos. 

![](media/desktop-data-categorization/datacategorization.gif)

E já está!  Qualquer comportamento que se acumule normalmente para um elemento visual funcionará agora automaticamente.  

Pode também ter interesse em conhecer a [filtragem geográfica para aplicações móveis do Power BI](desktop-mobile-geofiltering.md).

