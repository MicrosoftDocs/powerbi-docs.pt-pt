---
title: Adicionar parâmetros de relatórios do Power BI através do URL
description: Filtre um relatório através de parâmetros de cadeias de consulta de URL e, se pretender, filtre com base em mais de um campo.
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/18/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: aeaea6d14cf8f4fd62fbbf5098e68429fe40b96a
ms.sourcegitcommit: 2b9ef93bbff5c741ba55ea0502f642632683d593
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/24/2018
---
# <a name="filter-a-report-using-query-string-parameters-in-the-url"></a>Filtrar um relatório usando parâmetros de cadeia de consulta no URL
Quando abrir um relatório no serviço Power BI, cada página do relatório tem um URL exclusivo. Para filtrar essa página de relatório, pode utilizar o painel Filtros na tela de relatório.  Também pode adicionar parâmetros de cadeia de consulta ao URL para filtrar o relatório. Pode ter um relatório que pretenda mostrar aos colegas e pré-preenchê-lo para os mesmos. Uma forma de o fazer é começar pelo URL predefinido do relatório, adicionar os parâmetros do filtro ao URL e, em seguida, enviar-lhes todo o URL por e-mail.

![relatório do Power BI no serviço](media/service-url-filters/power-bi-report2.png)

<iframe width="640" height="360" src="https://www.youtube.com/embed/WQFtN8nvM4A?list=PLv2BtOtLblH3YE_Ycas5B1GtcoFfJXavO&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="query-string-parameter-syntax-for-filtering"></a>Sintaxe de parâmetros de cadeia de consulta para filtragem
A sintaxe é relativamente simples. Comece pelo URL do relatório, adicione um ponto de interrogação e, em seguida, adicione a sua sintaxe de filtro.

URL?filter=***Tabela***/***Campo*** eq '***valor***'

![URL com um filtro](media/service-url-filters/power-bi-filter-urls7b.png)

* Os nomes de **Tabela** e **Campo** são sensíveis a maiúsculas e minúsculas, ao contrário de **valor**.
* Os campos que são ocultados da vista de relatórios também podem ser filtrados.
* **Valor** tem de estar entre plicas.
* O tipo de campo tem de ser um número ou uma cadeia de carateres
* Os nomes de tabela e campo não podem conter espaços.

Se estas informações forem confusas, continue a ler para obter uma explicação mais detalhada.  

## <a name="filter-on-a-field"></a>Filtrar num campo
Vamos assumir que o URL do nosso relatório é o seguinte.

![URL inicial](media/service-url-filters/power-bi-filter-urls6.png)

Na nossa visualização de mapa (acima), reparamos que temos lojas na Carolina do Norte.

>[!NOTE]
>Este exemplo baseia-se no [exemplo de Análise de Revenda](sample-datasets.md).
> 

Para filtrar o relatório de forma a mostrar dados apenas para lojas na Carolina do Norte ("NC"), anexe o seguinte ao URL:

?filter=Store/Territory eq 'NC'

![URL com um filtro](media/service-url-filters/power-bi-filter-urls7.png)

>[!NOTE]
>*NC* é um valor armazenado no campo **Territory** (Território) da tabela **Store** (Loja).
> 
> 

O nosso relatório está filtrado para a Carolina do Norte. Todas as visualizações na página de relatório mostram dados apenas para a Carolina do Norte.

![](media/service-url-filters/power-bi-report4.png)

## <a name="filter-on-multiple-fields"></a>Filtrar em múltiplos campos
Pode também filtrar em múltiplos campos ao adicionar mais parâmetros ao seu URL. Voltemos ao nosso parâmetro de filtro original.

```
?filter=Store/Territory eq 'NC'
```

Para filtrar em campos adicionais, adicione um `and` e outro campo no mesmo formato que o anterior. Eis um exemplo.

```
?filter=Store/Territory eq 'NC' and Store/Chain eq 'Fashions Direct'
```

<iframe width="640" height="360" src="https://www.youtube.com/embed/0sDGKxOaC8w?showinfo=0" frameborder="0" allowfullscreen></iframe>


### <a name="using-dax-to-filter-on-multiple-values"></a>Utilizar DAX para filtrar em múltiplos valores
Outra forma de filtrar em múltiplos campos é criar uma coluna calculada que concatena dois campos para um valor único. Depois, pode filtrar nesse valor.

Por exemplo, temos dois campos: Territory (Território) e Chain (Cadeia). No Power BI Desktop, [crie uma nova coluna Calculada](desktop-tutorial-create-calculated-columns.md) (Campo) intitulada TerritoryChain (CadeiaTerritório). Lembre-se de que o nome de **Campo** não pode ter espaços. Eis a fórmula DAX dessa coluna.

TerritoryChain = [Território] & " - " & [Cadeia]

Publique o relatório no serviço Power BI e, em seguida, utilize a cadeia de consulta de URL para filtrar de forma a mostrar dados apenas de lojas Lindseys no estado NC.

    https://app.powerbi.com/groups/me/reports/8d6e300b-696f-498e-b611-41ae03366851/ReportSection3?filter=Store/TerritoryChain eq 'NC–Lindseys'

## <a name="pin-a-tile-from-a-filtered-report"></a>Afixar um mosaico de um relatório filtrado
Após filtrar o relatório através de parâmetros de cadeia de consulta, pode afixar visualizações desse relatório ao seu dashboard. O mosaico no dashboard mostra os dados filtrados e selecionar esse mosaico de dashboard abre o relatório que foi utilizado para criá-lo.  No entanto, a filtragem que fez através do URL não é guardada com o relatório e, quando o mosaico do dashboard é selecionado, o relatório permanece no seu estado não filtrado.  Isto significa que os dados apresentados no mosaico de dashboard não corresponderão aos dados apresentados na visualização de relatório.

Isto pode ser útil em certos casos em que pretender ver resultados diferentes; filtrado no dashboard e não filtrado no relatório.

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
Existem alguns elementos a ter em conta ao utilizar os parâmetros da cadeia de consulta.

* No Servidor de Relatórios do Power BI, pode [transmitir parâmetros de relatório](https://docs.microsoft.com/sql/reporting-services/pass-a-report-parameter-within-a-url?view=sql-server-2017.md) ao incluí-los num URL de relatório. Estes parâmetros de URL não têm prefixos porque são transmitidos diretamente para o motor de processamento de relatórios. 
* A filtragem de cadeia de consulta não funciona com a opção [Publicar na Web](service-publish-to-web.md) nem no Power BI Embedded.   
* O tipo de campo tem de ser um número ou uma cadeia de carateres.
* Os nomes de tabela e campo não podem conter espaços.

## <a name="next-steps"></a>Próximos passos
[Afixar uma visualização num dashboard](service-dashboard-pin-tile-from-report.md)  
[Experimente, é gratuito!](https://powerbi.com/)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

