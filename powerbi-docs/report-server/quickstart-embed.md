---
title: "Incorporar um relatório através de um iFrame"
description: "Instalar o Power BI Report Server é bastante rápido. Deve demorar poucos minutos da transferência à instalação e configuração."
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/09/2017
ms.author: maghan
ms.openlocfilehash: 56835bfb25c8c930099fadf710137f69fa89fc2e
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2018
---
# <a name="quickstart-embed-a-power-bi-report-using-an-iframe-and-url-parameters"></a>Início Rápido: Incorporar um relatório do Power BI através de um iFrame e parâmetros de URL

Pode incorporar qualquer relatório ao utilizar um iFrame na sua aplicação. 

## <a name="url-parameter"></a>Parâmetro de URL

A partir de um URL para um relatório, pode adicionar um parâmetro de cadeia de consulta de `?rs:Embed=true`.

Por exemplo:

```
http://myserver/reports/powerbi/Sales?rs:embed=true
```

Isto funciona em todos os tipos de relatórios no Power BI Report Server.

## <a name="iframe"></a>iFrame

Após ter o seu URL, pode criar um iFrame numa página Web para alojar o relatório.

Por exemplo:

```
<iframe width="800" height="600" src="http://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
```

## <a name="url-filter"></a>Filtro de URL

Pode adicionar um parâmetro de cadeia de consulta ao URL para filtrar os dados que são devolvidos no relatório do Power BI.

A sintaxe é simples. Comece pelo URL do relatório, adicione um ponto de interrogação e, em seguida, esta sintaxe de filtro.

URL?filter=***Tabela***/***Campo*** eq '***valor***'

Tenha em conta o seguinte:

- Os nomes de **Tabela** e **Campo** são sensíveis a maiúsculas e minúsculas, ao contrário de **valor**.
- Pode filtrar um relatório com campos que estão ocultados da vista de relatório.
- **Valor** tem de estar entre plicas.
- O tipo de campo tem de ser uma cadeia.
- Os nomes de tabelas e campos não podem conter espaços.

###  <a name="example-filter-on-a-field"></a>Exemplo: Filtrar num campo

Vejamos o exemplo de [Análise de Revenda](../sample-datasets.md). Suponhamos que este é o URL para o relatório no servidor de relatórios numa pasta intitulada "power-bi":

```
https://report-server/reports/power-bi/Retail-Analysis-Sample
```

Pode ver que a visualização de mapa no exemplo de Análise de Revenda mostra lojas na Carolina do Norte e noutros estados.

![Visualização do mapa exemplo de Análise de Revenda](media/quickstart-embed/report-server-retail-analysis-sample-map.png)

*NC* é o valor da Carolina do Norte armazenado no campo **Territory** (Território) da tabela **Store** (Loja). Por isso, para filtrar o relatório de forma a mostrar dados apenas para lojas na Carolina do Norte, anexe o seguinte ao URL:

?filter=Store/Territory eq 'NC'

Agora, o relatório está filtrado para a Carolina do Norte. Todas as visualizações na página de relatório mostram dados apenas para a Carolina do Norte.

![Visualizações filtradas do exemplo de Análise de Retalho](media/quickstart-embed/report-server-retail-analysis-sample-filtered-map.png)

### <a name="create-a-dax-formula-to-filter-on-multiple-values"></a>Criar uma fórmula DAX para filtrar em múltiplos valores

Outra forma de filtrar em múltiplos campos é criar uma coluna calculada no Power BI Desktop que concatena dois campos para um valor único. Depois, pode filtrar nesse valor.

Por exemplo, Análise de Retalho tem dois campos: Territory (Território) e Chain (Cadeia). No Power BI Desktop, pode [criar uma coluna calculada](../desktop-tutorial-create-calculated-columns.md) (Campo) intitulada TerritoryChain (CadeiaTerritório). Lembre-se de que o nome de **Campo** não pode ter espaços. Eis a fórmula DAX dessa coluna.

TerritoryChain = [Território] & "-" & [Cadeia]

Publique o relatório no Power BI Report Server e, em seguida, utilize a cadeia de consulta de URL para filtrar de forma a mostrar dados apenas de lojas Lindseys no estado NC.

```
https://report-server/reports/power-bi/Retail-Analysis-Sample?filter=Store/TerritoryChain eq 'NC-Lindseys'

```

## <a name="next-steps"></a>Próximos passos

[Início rápido: Criar um relatório do Power BI para o Power BI Report Server](quickstart-create-powerbi-report.md)  
[Início rápido: Criar um relatório paginado para o Power BI Report Server](quickstart-create-paginated-report.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)