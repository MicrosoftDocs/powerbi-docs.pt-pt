---
title: Capacity and SKUs in Power BI embedded analytics (Capacidade e SKUs na análise incorporada do Power BI)
description: Compreenda a capacidade e os SKUs na análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/11/2020
ms.openlocfilehash: f8c3bdf3e3f92d570205551a97389def2921fe98
ms.sourcegitcommit: 17aad73762579d6822383b27b96b1b63f87f2d6f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2020
ms.locfileid: "77260463"
---
# <a name="capacity-and-skus-in-power-bi-embedded-analytics"></a>Capacity and SKUs in Power BI embedded analytics (Capacidade e SKUs na análise incorporada do Power BI)

Ao passar para a produção, a análise incorporada do Power BI necessita de uma capacidade dedicada (SKU *A*, *EM* ou *P*) para publicar conteúdos incorporados do Power BI.

A capacidade é um conjunto dedicado de recursos de utilização exclusiva. Permite-lhe publicar dashboards, relatórios e conjuntos de dados para utilizadores sem ter de comprar licenças para os mesmos. Além disso, oferece um desempenho fiável e consistente para os seus conteúdos.

>[!NOTE]
>Para poder publicar conteúdos, terá de ter uma conta do Power BI Pro.

## <a name="what-is-embedded-analytics"></a>O que é a análise incorporada?

A análise incorporada do Power BI inclui duas soluções:
* *Power BI Embedded* – oferta do Azure
* Incorporar o Power BI como parte do *Power BI Premium* – oferta do Office

### <a name="power-bi-embedded"></a>Power BI Embedded

O Power BI Embedded destina-se a ISVs e programadores que pretendem incorporar elementos visuais nas respetivas aplicações.

As aplicações que utilizam o Power BI Embedded permitem que os utilizadores consumam conteúdos armazenados na capacidade do Power BI Embedded.

### <a name="power-bi-premium"></a>Power BI Premium

O [Power BI Premium](../service-premium-what-is.md) destina-se às empresas que pretendem uma solução completa de BI que forneça uma vista única da respetiva organização, parceiros, clientes e fornecedores.

O Power BI Premium é um produto SaaS que permite aos utilizadores consumirem conteúdos através de aplicações móveis e aplicações desenvolvidas internamente ou no portal do Power BI (serviço Power BI). Isto permite ao Power BI Premium fornecer uma solução para aplicações para o cliente externas e internas.

## <a name="capacity-and-skus"></a>Capacidade e SKUs

Cada capacidade oferece uma seleção de SKUs e cada SKU fornece vários escalões de recursos de memória e computação. O tipo de SKU necessário depende do tipo de solução que pretende implementar.

Antes de decidir qual o SKU que deve adquirir, reveja as informações nesta secção.
* Para saber quais as cargas de trabalho suportadas para cada escalão, consulte o artigo [Configurar cargas de trabalho numa capacidade Premium](../service-admin-premium-workloads.md)
* Utilize esta ligação para [definir e testar a sua capacidade](../service-premium-capacity-optimize.md#testing-approaches)

### <a name="power-bi-embedded-skus"></a>SKUs do Power BI Embedded

O Power BI Embedded é enviado com um SKU *A*.
* [Know what your Power BI Embedded capacity can handle](https://powerbi.microsoft.com/blog/power-bi-developer-community-june-july-update/#Capacity-Plan) (Saiba o que a sua capacidade do Power BI Embedded pode suportar)
* [Comprar um SKU *A*](../service-admin-premium-purchase.md#purchase-a-skus-for-testing-and-other-scenarios)

### <a name="power-bi-premium-skus"></a>SKUs do Power BI Premium

O Power BI premium oferece dois SKUs: o *P* e o *EM*.
* [Conheça as diferenças entre os SKUs *P* e *EM*](../service-premium-what-is.md#subscriptions-and-licensing)
* [Comprar um SKU Premium](../service-admin-premium-purchase.md)

### <a name="which-sku-should-i-use"></a>Qual é o SKU que devo utilizar?

Esta tabela fornece um resumo das funcionalidades, bem como da capacidade e do SKU específico necessário para cada uma. 

</br>
<table>
<col width="20%">
<col width="20%">
<col width="20%">
<col width="20%">
<col width="20%">
<tbody>
<tr>
<td style="text-align: center"; colspan="2"><p><b>Funcionalidade</b></p></td>
<td style="text-align: center">
<p><b>Power BI Embedded</b></p>
</td>
<td style="text-align: center"; colspan="2">
<p><b>Power BI Premium</b></p>
</td>
</tr>
<tr>
<td><p><em>O que é consumido?</em><p></td>
<td><p><em>O que é o consumo?</em><p></td>
<td style="text-align: center"><p><em> SKUs A</br>(Azure)</em></p></td>
<td style="text-align: center"><p><em>SKUs EM</br>(Office)</em></p></td>
<td style="text-align: center"><p><em>SKUs P</br>(Office)</em></p></td>
</tr>
<tr>
<td>Incorporar artefactos de uma área de trabalho do Power BI</td>
<td>
</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td rowspan="2">Relatórios do Power BI</td>
<td>Uma aplicação incorporada para a sua organização</br>(os dados pertencem ao utilizador)</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>Uma aplicação incorporada para os seus clientes</br>(os dados pertencem à aplicação)</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td rowspan="3">Conteúdos do Power BI<br>(com uma licença gratuita do Power BI)</td>
<td>Serviço Power BI</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>Power BI para dispositivos móveis</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>Aplicações do MS Office</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
</tbody>
</table>

### <a name="capacity-considerations"></a>Considerações de capacidade

A tabela abaixo apresenta considerações de pagamento e utilização por capacidade.

</br>
<table>
<tbody>
<tr>
<td></td>
<td style="text-align: center;"><p><strong>Power BI Embedded</strong></p></td>
<td style="text-align: center;" colspan="2"><p><strong>Power BI Premium</strong></p></td>
</tr>
<tr>
<td><p><strong>Oferta</strong></p></td>
<td style="text-align: center;"><p>Azure</p></td>
<td style="text-align: center;" colspan="2"><p>Office</p></td>
</tr>
<tr>
<td><p><strong>SKU</strong></p></td>
<td style="text-align: center;"><p>A</p></td>
<td style="text-align: center;"><p>EM</p></td>
<td style="text-align: center;"><p>P</p></td>
</tr>
<tr>
<td><p><strong>Faturação</strong></td>
<td style="text-align: center;">Hora a hora</td>
<td style="text-align: center;">Mensal</td>
<td style="text-align: center;">Mensal</td>
</tr>
<tr>
<td><p><strong>Alocação</strong></td>
<td style="text-align: center;">Nenhum</td>
<td style="text-align: center;">Mensal ou anual</td>
<td style="text-align: center;">Mensal ou anual</td>
</tr>
<tr>
<td valign="top"><p><strong>Utilização</strong></td>
<td style="text-align: center;">Os recursos do Azure podem ser:</br>- <a href="azure-pbie-scale-capacity.md">Aumentados ou reduzidos verticalmente</a></br>- <a href="azure-pbie-pause-start.md">Colocados em pausa ou retomados</a>
</td>
<td style="text-align: center;">Incorporados em aplicações e em</br> aplicações da Microsoft</td>
<td style="text-align: center;">Incorporados em aplicações e</br> no serviço Power BI</td>
</tr>
</tbody>
</table>

### <a name="sku-memory-and-computing-power"></a>Memória de SKU e poder de computação

A seguinte tabela descreve os recursos e limites de cada SKU.

| Nós de Capacidade | Núcleos virtuais totais | Núcleos virtuais de back-end | RAM (GB) | Núcleos virtuais de front-end | DirectQuery/Ligação em Direto (por segundo) | Paralelismo de Atualização do Modelo |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| P4 | 64 | 32 | 200 | 32 | 240 | 48 |
| P5 | 128 | 64 | 400 | 64 | 480 | 96 |
| | | | | | | |

## <a name="next-steps"></a>Próximos passos

> [!div class="nextstepaction"]
>[Incorporar para os seus clientes](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Incorporar para a sua organização](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Incorporar a partir de aplicações](embed-from-apps.md)