---
title: Capacidade e SKUs na análise incorporada do Power BI que permitem obter melhores informações de BI incorporadas
description: Compreenda a capacidade e os SKUs na análise incorporada do Power BI. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/14/2021
ms.openlocfilehash: b37182cbdf030e8b32fdfe307d0a652fef678b9b
ms.sourcegitcommit: c33e53e1fab1f29872297524a7b4f5af6c806798
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/04/2021
ms.locfileid: "99533033"
---
# <a name="capacity-and-skus-in-power-bi-embedded-analytics"></a>Capacity and SKUs in Power BI embedded analytics (Capacidade e SKUs na análise incorporada do Power BI)

Ao passar para a produção, a análise incorporada do Power BI necessita de uma capacidade (SKU *A*, *EM* ou *P*) para publicar conteúdos incorporados do Power BI.

A capacidade é um conjunto dedicado de recursos de utilização exclusiva. Permite-lhe publicar dashboards, relatórios e conjuntos de dados para utilizadores sem ter de comprar licenças para os mesmos. Além disso, oferece um desempenho fiável e consistente para os seus conteúdos.

>[!NOTE]
>Para poder publicar conteúdos, terá de ter uma conta do Power BI Pro.

## <a name="what-is-embedded-analytics"></a>O que é a análise incorporada?

A análise incorporada do Power BI inclui duas soluções:

* *Power BI Embedded* – oferta do Azure

* Incorporar o Power BI como parte do *Power BI Premium* – oferta do Microsoft Office

### <a name="power-bi-embedded"></a>Power BI Embedded

O Power BI Embedded destina-se a ISVs e programadores que pretendem incorporar elementos visuais nas respetivas aplicações.

As aplicações que utilizam o Power BI Embedded permitem que os utilizadores consumam conteúdos armazenados na capacidade do Power BI Embedded.

>[!NOTE]
>O Power BI Embedded lançou recentemente uma nova versão, designada **Embedded Gen2**. O Embedded Gen2 irá simplificar a gestão de capacidades incorporadas e melhorar a experiência do Power BI Embedded. Para obter mais informações, veja [Power BI Embedded Generation 2](power-bi-embedded-generation-2.md).

### <a name="power-bi-premium"></a>Power BI Premium

O [Power BI Premium](../../admin/service-premium-what-is.md) destina-se às empresas que pretendem uma solução completa de BI que forneça uma vista única da respetiva organização, parceiros, clientes e fornecedores.

O Power BI Premium é um produto SaaS que permite aos utilizadores consumirem conteúdos através de aplicações móveis e aplicações desenvolvidas internamente ou no portal do Power BI (serviço Power BI). Isto permite ao Power BI Premium fornecer uma solução para aplicações para o cliente externas e internas.

## <a name="capacity-and-skus"></a>Capacidade e SKUs

Cada capacidade oferece uma seleção de SKUs e cada SKU fornece vários escalões de recursos de memória e computação. O tipo de SKU necessário depende do tipo de solução que pretende implementar.

Para saber quais as cargas de trabalho suportadas para cada escalão, consulte o artigo [Configurar cargas de trabalho numa capacidade Premium](../../admin/service-admin-premium-workloads.md)

Utilize estas ligações para planear e testar a capacidade:
* [Planeamento de capacidade](embedded-capacity-planning.md)
* [Abordagens de teste](../../admin/service-premium-capacity-optimize.md#testing-approaches)

### <a name="power-bi-embedded-skus"></a>SKUs do Power BI Embedded

O Power BI Embedded é enviado com um [SKU *a*](../../admin/service-admin-premium-purchase.md#purchase-a-skus-for-testing-and-other-scenarios).

### <a name="power-bi-premium-skus"></a>SKUs do Power BI Premium

O Power BI premium oferece dois SKUs: o *P* e o *EM*.
* [Conheça as diferenças entre os SKUs *P* e *EM*](../../admin/service-premium-what-is.md#subscriptions-and-licensing)
* [Comprar um SKU Premium](../../admin/service-admin-premium-purchase.md)

### <a name="which-sku-should-i-use"></a>Qual é o SKU que devo utilizar?

A tabela abaixo apresenta um resumo das funcionalidades, bem como da capacidade e do SKU específico necessário para cada uma.

Nesta tabela, uma aplicação personalizada refere-se a uma aplicação Web criada com uma análise incorporada. Quando incorpora uma aplicação Web personalizada como um desenvolvedor (com os SDKs JavaScript ou .NET, ou as APIs REST), tem a capacidade de controlar e personalizar a experiência do utilizador. Esta capacidade não está disponível quando utiliza outras opções de incorporação, como o serviço Power BI e o Power BI Mobile.

| Cenário | Azure   | Office          |
|----------|---------|-----------------|
|          | (SKU A) | (SKUs P e EM) |
|[Incorporar para os seus clientes](embed-sample-for-customers.md)</br>(os dados pertencem à aplicação)     |✔        |✔        |
|[Incorporar para a sua organização](embed-sample-for-your-organization.md)</br>(os dados pertencem ao utilizador)     |✖        |✔         |
|Aplicações do Microsoft 365</br>(anteriormente conhecidas como aplicações do Office 365)<ul><li>[Incorporar no Teams](../../collaborate-share/service-embed-report-microsoft-teams.md)</li><li>[Incorporar no SharePoint](../../collaborate-share/service-embed-report-spo.md)</li></ul>     |✖        |✔        |
|[Incorporação de URLs seguros](../../collaborate-share/service-embed-secure.md)</br>(incorporar a partir do serviço Power BI)     |✖        |✔        |

>[!NOTE]
>* É necessária uma [licença do Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md) para publicar conteúdos numa área de trabalho da aplicação Power BI.
>* Apenas o **SKU P** permite que os utilizadores gratuitos do Power BI consumam aplicações e conteúdos partilhados do Power BI, no serviço Power BI.

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
<td style="text-align: center"><p>Azure</p></td>
<td style="text-align: center" colspan="2"><p>Office</p></td>
</tr>
<tr>
<td><p><strong>SKU</strong></p></td>
<td style="text-align: center"><p>A</p></td>
<td style="text-align: center"><p>EM</p></td>
<td style="text-align: center"><p>P</p></td>
</tr>
<tr>
<td><p><strong>Faturação</strong></td>
<td style="text-align: center">Hora a hora</td>
<td style="text-align: center">Mensal</td>
<td style="text-align: center">Mensal</td>
</tr>
<tr>
<td><p><strong>Alocação</strong></td>
<td style="text-align: center">Nenhum</td>
<td style="text-align: center">Anual</td>
<td style="text-align: center">Mensal ou anual</td>
</tr>
<tr>
<td valign="top"><p><strong>Utilização</strong></td>
<td style="text-align: center">Os recursos do Azure podem ser:<li><a href="azure-pbie-scale-capacity.md">Aumentados ou reduzidos verticalmente</a></li><li><a href="azure-pbie-pause-start.md">Colocados em pausa ou retomados</a>
</td></li>
<td style="text-align: center">Incorporados em aplicações e em</br> aplicações da Microsoft</td>
<td style="text-align: center">Incorporados em aplicações e</br> no serviço Power BI</td>
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

#### <a name="embedded-gen-2-memory-enhancements-preview"></a>Melhorias de memória da Gen 2 incorporadas (pré-visualização)

Com [o Power BI Incorporado Geração 2](power-bi-embedded-generation-2.md) (também conhecido como Embedded Gen 2), a quantidade de memória disponível em cada tamanho do nó é definida para o limite de pegada de memória de um único item Power BI (como um relatório ou um dashboard), e não para o consumo cumulativo de memória. Por exemplo, numa capacidade Incorporada gen2 A4, apenas um único tamanho de conjunto de dados é limitado a 25 GB, em comparação com a capacidade original de Power BI Incorporado, onde a pegada total de memória dos conjuntos de dados a ser tratados ao mesmo tempo é limitada a 25 GB.

## <a name="next-steps"></a>Próximos passos

> [!div class="nextstepaction"]
>[Incorporar para os seus clientes](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Incorporar para a sua organização](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Incorporar a partir de aplicações](./index.yml)