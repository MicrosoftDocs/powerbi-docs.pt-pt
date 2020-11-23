---
title: Utilizar a Lista de Campos no Power BI Desktop (pré-visualização)
description: Utilize a Lista de Campos para modelar dados e criar relatórios no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/11/2020
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: a314ba3faedf463c7b92977aad1792d9f37b2f28
ms.sourcegitcommit: 029aacd09061a8aa45b57f05d0dc95c93dd16a74
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/12/2020
ms.locfileid: "94571853"
---
# <a name="using-the-field-list-in-power-bi-desktop-preview"></a>Utilizar a Lista de Campos no Power BI Desktop (pré-visualização)

A partir da atualização de novembro de 2020, iremos unificar as Listas de **Campos** na Vista de Modelo, Vista de Dados e Vista de Relatório no Power BI Desktop. A unificação destas vistas irá criar consistência para a funcionalidade e para a interface do utilizador (IU) em todas as vistas e abordar o feedback de clientes.

As alterações que irá notar nas vistas incluem as seguintes:

* Iconografia
* Funcionalidade de pesquisa
* Itens do menu de contexto
* Comportamento de arrastar e largar semelhante
* Descrições
* Melhorias de acessibilidade

A intenção é melhorar a utilização do Power BI Desktop. As alterações devem ter um impacto mínimo sobre o fluxo de trabalho de dados típico.

## <a name="enabling-the-new-field-list-preview"></a>Ativar a nova Lista de Campos (pré-visualização)

A Lista de Campos unificada começa com a vista de **Modelo** e, subsequentemente, será ativada para outras vistas. No Power BI Desktop, navegue para **Ficheiro > Opções e definições > Opções** e, em seguida, selecione **Funcionalidades de pré-visualização** no painel da esquerda para ativar a vista de Campos unificada. Na secção Funcionalidades de pré-visualização, selecione a caixa de verificação ao lado de **Nova lista de campos**.

![Ativar a nova lista de campos](media/desktop-field-list/field-list-01.png)

Ser-lhe-á pedido que reinicie o Power BI Desktop para a seleção entrar em vigor.

## <a name="field-list-changes"></a>Alterações da lista de campos

As tabelas seguintes mostram as atualizações à lista de campos. 


|**Lista de campos original (vista de Modelo)**  | **Nova lista de campos (vista de Modelo)**  |
|:---------:|:---------:|
|**Original** |**Novo** |
|**Ícones e IU**       ||
|![lista de campos original](media/desktop-field-list/field-list-01a.png)     |![nova lista de campos](media/desktop-field-list/field-list-01b.png)    |
|**Menu de contexto – Campo**       ||
|![menu de contexto original para Campo](media/desktop-field-list/field-list-02a.png)     |![novo menu de contexto para Campo](media/desktop-field-list/field-list-02b.png)    |
|**Menu de contexto – Tabela**       ||
|![menu de contexto original para tabelas](media/desktop-field-list/field-list-03a.png)     |![novo menu de contexto para tabelas](media/desktop-field-list/field-list-03b.png)    |
|**Descrições**       ||
|![descrição original](media/desktop-field-list/field-list-04a.png)     |![nova descrição](media/desktop-field-list/field-list-04b.png)    |

Também existem novos ícones da Lista de campos. A tabela seguinte mostra os ícones originais e o seu novo equivalente e fornece uma breve descrição de cada um. 


|Ícone original  |Novo ícone  |Description  |
|:---------:|:---------:|:---------|
|![ícone original da pasta](media/desktop-field-list/field-list-05a.png)     |![novo ícone da pasta](media/desktop-field-list/field-list-05b.png)           |Pasta na lista Campos         |
|![ícone original do campo numérico](media/desktop-field-list/field-list-06a.png)     |![novo ícone do campo numérico](media/desktop-field-list/field-list-06b.png)         |Campo numérico: os campos numéricos são agregações cuja soma ou média pode ser calculada, por exemplo. As agregações são importadas com os dados e definidas no modelo de dados no qual se baseia o seu relatório. Para obter mais informações, consulte [Agregados em relatórios do Power BI](../create-reports/service-aggregates.md).         |
|![ícone original da coluna calculada](media/desktop-field-list/field-list-07a.png)     |![novo ícone da coluna calculada](media/desktop-field-list/field-list-07b.png)         |Coluna calculada com um tipo de dados não numérico: uma nova coluna não numérica que cria com uma fórmula Data Analysis Expressions (DAX) que define os valores da coluna. Saiba mais sobre as [colunas calculadas](desktop-calculated-columns.md).        |
|![ícone original da coluna calculada numérica](media/desktop-field-list/field-list-08a.png)     |![novo ícone da coluna calculada numérica](media/desktop-field-list/field-list-08b.png)          |Coluna calculada numérica: uma nova coluna que cria com uma fórmula Data Analysis Expressions (DAX) que define os valores da coluna. Saiba mais sobre as [colunas calculadas](desktop-calculated-columns.md).         |
|![ícone original da medida](media/desktop-field-list/field-list-09a.png)     |![novo ícone da medida](media/desktop-field-list/field-list-09b.png)          |Medida: uma medida tem a sua própria fórmula codificada. Os visualizadores do relatório não podem alterar o cálculo; por exemplo, se for uma soma, só poderá ser uma soma. Os valores não são armazenados numa coluna. São calculados dinamicamente, dependendo apenas da sua localização num elemento visual. Para obter mais informações, leia a secção [Noções básicas sobre medidas](desktop-measures.md).         |
|![ícone original do grupo de medidas](media/desktop-field-list/field-list-10a.png)     |![novo ícone do grupo de medidas](media/desktop-field-list/field-list-10b.png)         |Grupo de medidas.         |
|![ícone original do kpi](media/desktop-field-list/field-list-11a.png)     |![novo ícone do kpi](media/desktop-field-list/field-list-11b.png)         |KPI: uma indicação visual que comunica a quantidade de progresso feito em relação a um objetivo mensurável. Saiba mais sobre os elementos visuais do [Indicador Chave de Desempenho (KPI)](../visuals/power-bi-visualization-kpi.md).         |
|![ícone original da hierarquia de campos](media/desktop-field-list/field-list-12a.png)     |![novo ícone da hierarquia de campos](media/desktop-field-list/field-list-12b.png)           |Hierarquia de campos: selecione a seta para ver os campos que constituem a hierarquia. Veja este vídeo do Power BI no YouTube, intitulado [Creating and working with hierarchies](https://www.youtube.com/watch?v=q8WDUAiTGeU) (Criar e trabalhar com hierarquias), para obter mais informações.         |
|![ícone original dos dados de áreas geográficas](media/desktop-field-list/field-list-13a.png)     |![novo ícone dos dados de áreas geográficas](media/desktop-field-list/field-list-13b.png)         |Dados de áreas geográficas: estes campos de localização podem ser utilizados para criar visualizações de mapas.         |
|![ícone original do campo de identidade](media/desktop-field-list/field-list-14a.png)     |![novo ícone do campo de identidade](media/desktop-field-list/field-list-14b.png)          |Campo de identidade: Os campos com este ícone são campos exclusivos, definidos para mostrar todos os valores, mesmo se tiverem duplicados. Por exemplo, os seus dados podem ter registos para duas pessoas diferentes chamadas Guilherme Sarmento e cada um dos registos será tratado como exclusivo. Os registos não serão somados.         |
|![ícone original do parâmetro](media/desktop-field-list/field-list-15a.png)     |![Novo ícone do parâmetro](media/desktop-field-list/field-list-15b.png)          |Parâmetro: defina parâmetros para fazer com que várias partes dos seus relatórios e modelos de dados (como um filtro de consulta, uma referência de origem de dados, uma definição de medida, etc.) dependam de um ou mais valores de parâmetros. Veja esta mensagem de blogue do Power BI sobre [parâmetros de consultas](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/) para obter mais informações.         |
|![ícone original do campo de data do calendário](media/desktop-field-list/field-list-16a.png)     |![novo ícone do campo de data do calendário](media/desktop-field-list/field-list-16b.png)         |Campo de data do calendário com uma tabela de datas incorporada.         |
|![ícone original da tabela calculada](media/desktop-field-list/field-list-17a.png)     |![novo ícone da tabela calculada](media/desktop-field-list/field-list-17b.png)          |Tabela calculada: uma tabela criada com uma fórmula DAX (Data Analysis Expressions) baseada em dados já carregados para o modelo. Funcionam melhor para cálculos intermédios e o ideal é que os armazene como parte do modelo.         |
|![ícone original de aviso](media/desktop-field-list/field-list-18a.png)     |![novo ícone de aviso](media/desktop-field-list/field-list-18b.png)         |Aviso: um campo calculado com um erro. Por exemplo, a sintaxe da expressão DAX pode estar incorreta.         |
|![ícone original do grupo](media/desktop-field-list/field-list-19a.png)     |![novo ícone do grupo](media/desktop-field-list/field-list-19b.png)         |Grupo: os valores nesta coluna baseiam-se em valores de agrupamento de outra coluna ao utilizar a funcionalidade grupos e discretização. Pode saber mais sobre como [Utilizar o agrupamento e discretização](../create-reports/desktop-grouping-and-binning.md).         |
| sem ícone original    |![novo ícone de alterar medida de deteção](media/desktop-field-list/field-list-20b.png)          |Medida de deteção de alteração: ao configurar uma página para que atualize automaticamente, pode configurar uma [medida de deteção de alteração](../create-reports/desktop-grouping-and-binning.md). Esta será consultada para determinar se os elementos visuais do resto da página devem ser atualizados.         |


## <a name="next-steps"></a>Próximos passos

Poderá também estar interessado nos seguintes artigos:

* [Criar colunas calculadas no Power BI Desktop](desktop-calculated-columns.md)
* [Utilizar agrupamento e discretização no Power BI Desktop](../create-reports/desktop-grouping-and-binning.md)
* [Utilizar linhas de grelha e ajustar à grelha em relatórios do Power BI Desktop](../create-reports/desktop-gridlines-snap-to-grid.md)

