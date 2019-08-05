---
title: Data view mappings (Mapeamentos de vista de dados)
description: Como o Power BI transforma os dados antes de os transmitir aos elementos visuais
author: asander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: ff70b2f12921694617a736164484df1326471eea
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425189"
---
# <a name="data-view-mappings-in-power-bi-visuals"></a>Mapeamentos de vista de dados em elementos visuais do Power BI

Um `dataViewMappings` descreve como as funções de dados se relacionam entre si e permitem-lhe especificar requisitos condicionais.
Há uma seção para cada um dos `dataMappings`.

Cada mapeamento válido produzirá um `DataView`, mas atualmente só suportamos a execução de uma consulta por elemento visual, pelo que, na maioria das situações, só obterá uma `DataView`. No entanto, pode fornecer múltiplos mapeamentos de dados com diferentes condições, que permitem o seguinte:

```json
"dataViewMappings": [
    {
        "conditions": [ ... ],
        "categorical": { ... },
        "single": { ... },
        "table": { ... },
        "matrix": { ... }
    }
]
```

> [!NOTE]
> É importante ter em atenção que o Power BI apenas cria um mapeamento para um DataView se o mapeamento válido estiver preenchido nos `dataViewMappings`.

Por outras palavras, se `categorical` estiver definido em `dataViewMappings`, mas outros mapeamentos como `table` e `single` não estiverem como no exemplo a seguir:
```json
"dataViewMappings": [
    {
        "categorical": { ... }
    }
]
```

O Power BI produzirá um `DataView` com um único mapeamento `categorical` (`table` e outros mapeamentos estarão `undefined`):
```javascript
{
    "categorical": {
        "categories": [ ... ],
        "values": [ ... ]
    },
    "metadata": { ... }
}
```

## <a name="conditions"></a>Condições

Descreve as condições para um mapeamento de dados específico. Pode fornecer múltiplos conjuntos de condições e, se os dados corresponderem a um dos conjuntos de condições descritos, o elemento visual aceitará os dados como válidos.

De momento, pode especificar um valor mínimo e um valor máximo para cada campo. Isto representa o número de campos que podem ser vinculados a essa função de dados. 

> [!NOTE]
> Se uma função de dados for omitida na condição, esta poderá ter qualquer número de campos.

### <a name="example-1"></a>Exemplo 1

Pode arrastar múltiplos campos para cada função de dados. Neste exemplo, limitamos a categoria a um campo de dados e medimos para dois campos de dados.

```json
"conditions": [
    { "category": { "max": 1 }, "y": { "max": 2 } },
]
```

### <a name="example-2"></a>Exemplo 2

Neste exemplo, é necessária uma de duas condições. Exatamente um campo de dados de categoria e exatamente duas medidas, ou exatamente duas categorias e exatamente uma medida.

```json
"conditions": [
    { "category": { "min": 1, "max": 1 }, "measure": { "min": 2, "max": 2 } },
    { "category": { "min": 2, "max": 2 }, "measure": { "min": 1, "max": 1 } }
]
```

## <a name="single-data-mapping"></a>Mapeamento de dados únicos

O mapeamento de dados únicos é a forma mais simples de mapeamento de dados. Aceita um único campo de medida e dá-lhe o total. Se o campo for numérico, dar-lhe-á a soma. Caso contrário, dar-lhe-á uma contagem de valores únicos.

Para utilizar o mapeamento de dados únicos, tem de definir o nome da função de dados que pretende mapear. Este mapeamento só funcionará com um único campo de medida. Se for atribuído um segundo campo, não será gerada nenhuma vista de dados. Desta forma, também é uma boa prática incluir uma condição que limite os dados a um único campo.

> [!NOTE]
> Este mapeamento de dados não pode ser utilizado em conjunto com outros mapeamentos de dados. Destina-se a reduzir os dados a único valor numérico.

### <a name="example-3"></a>Exemplo 3

```json
"dataViewMappings": {
    "conditions": [
        { "Y": { "max": 1 } }
    ],
    "single": {
        "role": "Y"
    }
}  
```

A vista de dados resultante continuará a conter os outros tipos (tabela, categórico, etc.), mas cada mapeamento conterá apenas o valor único. Recomenda-se aceder simplesmente ao valor único.

```JSON
{
    "dataView": [
        {
            "metadata": null,
            "categorical": null,
            "matrix": null,
            "table": null,
            "tree": null,
            "single": {
                "value": 94163140.3560001
            }
        }
    ]
}
```

## <a name="categorical-data-mapping"></a>Mapeamento de dados categóricos

O mapeamento de dados categóricos é utilizado para obter um ou dois agrupamentos independentes de dados.

### <a name="example-4"></a>Exemplo 4

Eis a definição do nosso exemplo anterior relativo a DataRoles.

```json
"dataRole":[
    {
        "displayName": "Category",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Y Axis",
        "name": "measure",
        "kind": "Measure"
    }
]
```

Agora o mapeamento:

```json
"dataViewMappings": {
    "categorical": {
        "categories": {
            "for": { "in": "category" }
        },
        "values": {
            "select": [
                { "bind": { "to": "measure" } }
            ]
        }
    }
}
```

Trata-se de um exemplo simples que, em português, indica o seguinte: "Mapear a minha DataRole `category` de forma a que, para cada campo que arrastar para `category`, os respetivos dados sejam mapeados a `categorical.categories`. Mapear também a minha DataRole `measure` a `categorical.values`".

* **for... in** – incluir todos os itens desta função de dados na consulta de dados.
* **bind... to** – produz o mesmo resultado de "for... in", mas espera-se que DataRole tenha uma condição que o restringe a um único campo.

### <a name="example-5"></a>Exemplo 5

Neste exemplo, utilizaremos as duas primeiras funções de dados do exemplo anterior, além de definir `grouping` e `measure2`.

```json
"dataRole":[
    {
        "displayName": "Category",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Y Axis",
        "name": "measure",
        "kind": "Measure"
    },
    {
        "displayName": "Grouping with",
        "name": "grouping",
        "kind": "Grouping"
    },
    {
        "displayName": "X Axis",
        "name": "measure2",
        "kind": "Grouping"
    }
]
```

Agora o mapeamento:

```json
"dataViewMappings":{
    "categorical": {
        "categories": {
            "for": { "in": "category" }
        },
        "values": {
            "group": {
                "by": "grouping",
                "select":[
                    { "bind": { "to": "measure" } },
                    { "bind": { "to": "measure2" } }
                ]
            }
        }
    }
}
```

Neste caso, a diferença está na forma como estamos a mapear categorical.values. Estamos a dizer "Mapear as minhas DataRoles `measure` e `measure2` para que sejam agrupadas pela DataRole `grouping`".

### <a name="example-6"></a>Exemplo 6

Aqui estão as DataRoles.

```json
"dataRoles": [
    {
        "displayName": "Categories",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Measures",
        "name": "measure",
        "kind": "Measure"
    },
    {
        "displayName": "Series",
        "name": "series",
        "kind": "Measure"
    }
]
```

Aqui está o dataViewMapping.

```json
"dataViewMappings": [
    {
        "categorical": {
            "categories": {
                "for": {
                    "in": "category"
                }
            },
            "values": {
                "group": {
                    "by": "series",
                    "select": [{
                            "for": {
                                "in": "measure"
                            }
                        }
                    ]
                }
            }
        }
    }
]
```

O `dataview` categórico poderia ser visualizado desta forma.

| Categorical |  |  | | | |
|-----|-----|------|------|------|------|
| | Ano | 2013 | 2014 | 2015 | 2016 |
| País | | |
| EUA | | x | x | 125 | 100 |
| Canadá | | x | 50 | 200 | x |
| México | | 300 | x | x | x |
| REINO UNIDO | | x | x | 75 | x |

O Power BI irá apresentá-lo como vista de dados categóricos. É o conjunto de categorias.

```JSON
{
    "categorical": {
        "categories": [
            {
                "source": {...},
                "values": [
                    "Canada",
                    "Mexico",
                    "UK",
                    "USA"
                ],
                "identity": [...],
                "identityFields": [...],
            }
        ]
    }
}
```

Cada categoria também mapeia a um conjunto de valores. Cada um destes valores é agrupado por série, ou seja, por ano.

Por exemplo, as vendas do Canadá em 2013 são nulas, as vendas do Canadá em 2014 são 50.

```JSON
{
    "values": [
        {
            "source": {...},
            "values": [
                null,
                300,
                null,
                null
            ],
            "identity": [...],
        },
        {
            "source": {...},
            "values": [
                50,
                null,
                150,
                null
            ],
            "identity": [...],
        },
        {
            "source": {...},
            "values": [
                200,
                null,
                null,
                125
            ],
            "identity": [...],
        },
        {
            "source": {...},
            "values": [
                null,
                null,
                null,
                100
            ],
            "identity": [...],
        }
    ]
}
```

## <a name="table-data-mapping"></a>Mapeamento de dados em tabela

A vista de dados em tabela é um mapeamento de dados simples. Essencialmente, é uma lista de pontos de dados onde os pontos de dados numéricos podem ser agregados.

### <a name="example-7"></a>Exemplo 7

Com as capacidades fornecidas:

```json
"dataRoles": [
    {
        "displayName": "Values",
        "name": "values",
        "kind": "Measure"
    }
]
```

```json
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                }
            }
        }
    }
]
```

A `dataview` em tabela poderia ser visualizada desta forma.  

| País| Ano | Vendas |
|-----|-----|------|
| EUA | 2016 | 100 |
| EUA | 2015 | 50 |
| Canadá | 2015 | 200 |
| Canadá | 2015 | 50 |
| México | 2013 | 300 |
| REINO UNIDO | 2014 | 150 |
| EUA | 2015 | 75 |

O Power BI irá apresentá-lo como vista de dados em tabela. Não parta do princípio de que há uma ordenação.

```JSON
{
    "table" : {
        "columns": [...],
        "rows": [
            [
                "Canada",
                2014,
                50
            ],
            [
                "Canada",
                2015,
                200
            ],
            [
                "Mexico",
                2013,
                300
            ],
            [
                "UK",
                2014,
                150
            ],
            [
                "USA",
                2015,
                100
            ],
            [
                "USA",
                2015,
                75
            ],
            [
                "USA",
                2016,
                100
            ]
        ]
    }
}
```

Os dados podem ser agregados ao selecionar o campo pretendido e clicar em soma.  

![Agregação de dados](./media/data-aggregation.png)

## <a name="matrix-data-mapping"></a>Mapeamento de dados em matriz

O mapeamento de dados em matriz é semelhante ao mapeamento de dados em tabela, mas as linhas são apresentadas hierarquicamente. Além disso, um dos valores de `dataRole` pode ser utilizado como valor de cabeçalho de coluna.

```json
{
    "dataRoles": [
        {
            "name": "Category",
            "displayName": "Category",
            "displayNameKey": "Visual_Category",
            "kind": "Grouping"
        },
        {
            "name": "Column",
            "displayName": "Column",
            "displayNameKey": "Visual_Column",
            "kind": "Grouping"
        },
        {
            "name": "Measure",
            "displayName": "Measure",
            "displayNameKey": "Visual_Values",
            "kind": "Measure"
        }
    ],
    "dataViewMappings": [
        {
            "matrix": {
                "rows": {
                    "for": {
                        "in": "Category"
                    }
                },
                "columns": {
                    "for": {
                        "in": "Column"
                    }
                },
                "values": {
                    "select": [
                        {
                            "for": {
                                "in": "Measure"
                            }
                        }
                    ]
                }
            }
        }
    ]
}
```

O Power BI cria uma estrutura de dados hierárquica. A raiz da árvore inclui os dados da primeira coluna da função de dados `Category` com elementos subordinados da segunda coluna da função de dados.

Conjunto de dados:

| Elementos principais | Elementos subordinados | Elementos secundários | Colunas | Valores |
|-----|-----|------|-------|-------|
| Elemento principal1 | Elemento subordinado1 | Elemento secundário1 | Col1 | 5 |
| Elemento principal1 | Elemento subordinado1 | Elemento secundário1 | Col2 | 6 |
| Elemento principal1 | Elemento subordinado1 | Elemento secundário2 | Col1 | 7 |
| Elemento principal1 | Elemento subordinado1 | Elemento secundário2 | Col2 | 8 |
| Elemento principal1 | Elemento subordinado2 | Elemento secundário3 | Col1 | 5 |
| Elemento principal1 | Elemento subordinado2 | Elemento secundário3 | Col2 | 3 |
| Elemento principal1 | Elemento subordinado2 | Elemento secundário4 | Col1 | 4 |
| Elemento principal1 | Elemento subordinado2 | Elemento secundário4 | Col2 | 9 |
| Elemento principal1 | Elemento subordinado2 | Elemento secundário5 | Col1 | 3 |
| Elemento principal1 | Elemento subordinado2 | Elemento secundário5 | Col2 | 5 |
| Elemento principal2 | Elemento subordinado3 | Elemento secundário6 | Col1 | 1 |
| Elemento principal2 | Elemento subordinado3 | Elemento secundário6 | Col2 | 2 |
| Elemento principal2 | Elemento subordinado3 | Elemento secundário7 | Col1 | 7 |
| Elemento principal2 | Elemento subordinado3 | Elemento secundário7 | Col2 | 1 |
| Elemento principal2 | Elemento subordinado3 | Elemento secundário8 | Col1 | 10 |
| Elemento principal2 | Elemento subordinado3 | Elemento secundário8 | Col2 | 13 |

O elemento visual de matriz nuclear do Power BI faz a composição sob a forma de tabela.

![Elemento visual Matriz](./media/matrix-visual-smaple.png)

O elemento visual obtém a estrutura de dados conforme descrito abaixo (só são apresentadas as duas primeiras linhas):

```json
{
    "metadata": {...},
    "matrix": {
        "rows": {
            "levels": [...],
            "root": {
                "childIdentityFields": [...],
                "children": [
                    {
                        "level": 0,
                        "levelValues": [...],
                        "value": "Parent1",
                        "identity": {...},
                        "childIdentityFields": [...],
                        "children": [
                            {
                                "level": 1,
                                "levelValues": [...],
                                "value": "Child1",
                                "identity": {...},
                                "childIdentityFields": [...],
                                "children": [
                                    {
                                        "level": 2,
                                        "levelValues": [...],
                                        "value": "Grand child1",
                                        "identity": {...},
                                        "values": {
                                            "0": {
                                                "value": 5 // value for Col1
                                            },
                                            "1": {
                                                "value": 6 // value for Col2
                                            }
                                        }
                                    },
                                    ...
                                ]
                            },
                            ...
                        ]
                    },
                    ...
                ]
            }
        },
        "columns": {
            "levels": [...],
            "root": {
                "childIdentityFields": [...],
                "children": [
                    {
                        "level": 0,
                        "levelValues": [...],
                        "value": "Col1",
                        "identity": {...}
                    },
                    {
                        "level": 0,
                        "levelValues": [...],
                        "value": "Col2",
                        "identity": {...}
                    },
                    ...
                ]
            }
        },
        "valueSources": [...]
    }
}
```

## <a name="data-reduction-algorithm"></a>Algoritmo de redução de dados

É possível aplicar um `DataReductionAlgorithm` se quiser controlar a quantidade de dados recebidos em DataView.

Por predefinição, todos os elementos visuais personalizados têm o DataReductionAlgorithm "top" aplicado com "count" definida como 1000 dataPoints. Isto é equivalente a definir as seguintes propriedades em capabilities.json:

```json
"dataReductionAlgorithm": {
    "top": {
        "count": 1000
    }
}
```

Pode mudar o valor de "count" para qualquer valor inteiro até 30 000. Os elementos visuais personalizados baseados em R conseguem suportar até 150 000 linhas.

## <a name="data-reduction-algorithm-types"></a>Tipos de algoritmo de redução de dados

Existem quatro tipos de definições de `DataReductionAlgorithm`:

* `top` – se quiser limitar os dados a valores extraídos da parte superior do conjunto de dados. Os primeiros valores de "count" serão retirados do conjunto de dados.
* `bottom` – se quiser limitar os dados a valores extraídos da parte inferior do conjunto de dados. Os últimos valores de "count" serão retirados do conjunto de dados.
* `sample` – para reduzir o conjunto de dados através de um algoritmo de amostragem simples limitado a um número de itens de "count". Isto significa que o primeiro e o último itens estão incluídos e que um número de itens de "count" tem intervalos iguais entre eles.
Por exemplo, se tiver obtido um conjunto de dados [0, 1, 2,... 100] e uma `count: 9`, receberá os valores [0, 10, 20... 100].
* `window` – carrega uma "window" de datapoints de cada vez com elementos "count". De momento, `top` e `window` são equivalentes. Estamos a trabalhar no sentido de suportarmos totalmente uma configuração de janelas.

## <a name="data-reduction-algorithm-usage"></a>Utilização do algoritmo de redução de dados

`DataReductionAlgorithm` pode ser utilizado em mapeamentos de `dataview` categórico, em tabela ou em matriz.

Pode ser definido em `categories` e/ou na secção de grupo de `values` para mapeamento de dados categóricos.

### <a name="example-8"></a>Exemplo 8

```json
"dataViewMappings": {
    "categorical": {
        "categories": {
            "for": { "in": "category" },
            "dataReductionAlgorithm": {
                "window": {
                    "count": 300
                }
            }  
        },
        "values": {
            "group": {
                "by": "series",
                "select": [{
                        "for": {
                            "in": "measure"
                        }
                    }
                ],
                "dataReductionAlgorithm": {
                    "top": {
                        "count": 100
                    }
                }  
            }
        }
    }
}
```

É possível aplicar o algoritmo de redução de dados à secção `rows` do mapeamento de `dataview` em tabela.

### <a name="example-9"></a>Exemplo 9

```json
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "top": {
                        "count": 2000
                    }
                } 
            }
        }
    }
]
```

É possível aplicar o algoritmo de redução de dados à secção `rows` e/ou `columns` do mapeamento de `matrix` em `dataview`.
