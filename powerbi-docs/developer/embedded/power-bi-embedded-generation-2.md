---
title: Power BI Embedded Generation 2 explicado como parte da análise incorporada do Power BI
description: Conheça a oferta power BI Embedded Generation 2 em análise embutida em Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
ms.date: 02/03/2021
ms.openlocfilehash: fa72ab380cac1a1ac6d12cb431bdacfb5964ee83
ms.sourcegitcommit: c33e53e1fab1f29872297524a7b4f5af6c806798
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/04/2021
ms.locfileid: "99534502"
---
# <a name="power-bi-embedded-generation-2-preview"></a>Power BI Embedded Generation 2 (pré-visualização)

Power BI Embedded lançou recentemente uma nova versão de Power BI Embedded **Generation 2,** referida como **Embedded Gen2** por conveniência. A Embedded Gen2 está atualmente em pré-visualização e está disponível para assinantes incorporados a utilizar durante o período de pré-visualização. Ainda pode criar a versão original do recurso Power BI Embedded, chamado *Embedded Gen 1,* ou criar um novo recurso *Embedded Gen 2.* Durante o período de pré-visualização, pode executar ambos os tipos de capacidades Power BI Embutidas em paralelo, e atribuir qualquer espaço de trabalho a uma gen1 ou a uma capacidade Gen2".

Todas as capacidades power BI Embedded Gen 1, como a pausa e o retomar da capacidade, são preservadas na Gen 2. Além disso, o recurso de capacidade da Gen 2 fornece as seguintes atualizações e experiência melhorada:

* **Melhor desempenho** - Melhor desempenho em qualquer tamanho de capacidade, a qualquer hora. As operações serão sempre executadas na velocidade máxima e não irão abrandar quando a carga na capacidade se aproximar dos limites.

* **Maior escala** - Incluindo as seguintes melhorias:

    * *Sem limites de renovação* - Já não é necessário acompanhar os horários dos conjuntos de dados que estão a ser atualizados sobre a sua capacidade

    * *Menos restrições de memória*

    * *Separação total entre a interação do relatório e as atualizações agendadas*

* **Nível de entrada mais baixo para relatórios paginados e cargas de trabalho de IA** – Comece com um *A1* SKU e cresça como precisar.

* **Dimensionamento instantâneo de um recurso** - Dimensione instantaneamente o seu recurso Power BI Incorporado. Desde escalar um recurso da Gen1 em minutos, até escalar um recurso da Gen2 em segundos.

* **Escala sem tempo de inatividade** - Com a Gen2 Incorporada pode escalar o seu recurso Power BI Incorporado sem experimentar qualquer tempo de inatividade.

* **Métricas melhoradas** - Incluindo dados de utilização clara e normalizada da capacidade, dependendo apenas da complexidade das operações de análise que a capacidade executa. As métricas não são impactadas por outros fatores, como o tamanho da capacidade, e o nível de carga no sistema durante a realização de análises. Ao utilizar as métricas melhoradas, a ferramenta de relatório incorporada permite-lhe ver claramente:
    * Análise de utilização
    * Planeamento orçamental
    * Recuos
    * A necessidade de melhorar a sua capacidade

    >[!NOTE]
    >As métricas melhoradas serão disponibilizadas mais à frente no período de pré-visualização. Os clientes que procuram aceder às métricas de utilização nos últimos sete dias, podem fazê-lo contactando o apoio ao cliente.

## <a name="using-embedded-gen2"></a>Usando o Gen2 incorporado

Crie um recurso de capacidade da Gen2 incorporado para tirar partido das suas atualizações. Para criar um recurso de capacidade Da Gen2 incorporado, siga as instruções na [capacidade de criar o Power BI Incorporado no portal Azure](azure-pbie-create-capacity.md).

## <a name="known-limitations"></a>Limitações conhecidas

* A utilização da capacidade da Gen2 incorporada não pode ser rastreada na [aplicação métricas](../../admin/service-admin-premium-monitor-capacity.md). Para mais informações, consulte [as atualizações do monitor Premium Gen2](../../admin/service-premium-what-is.md#updates-for-premium-gen2-preview-2).

* As definições de atribuição de memória para cargas de trabalho específicas não se aplicam às capacidades da Gen2 incorporada. Para mais informações, consulte [melhorias de memória da Gen 2 incorporadas](embedded-capacity.md#embedded-gen-2-memory-enhancements-preview)

* Se estiver a utilizar o XMLA com o Embedded Gen2, certifique-se de que está a utilizar as versões mais recentes das ferramentas de modelação e gestão de dados.

* Os recursos dos serviços de análise na Embedded Gen2 são suportados apenas nas mais recentes bibliotecas de clientes. As datas de lançamento estimadas para ferramentas dependentes para suportar este requisito estão [listadas em limitações conhecidas na Premium Gen2](../../admin/service-premium-what-is.md#known-limitations-in-premium-gen2).

* Todas as métricas Azure atuais e diagnósticos de registo para Power BI Incorporado, suportam apenas capacidades gen1.

## <a name="next-steps"></a>Passos seguintes

> [!div class="nextstepaction"]
> [Criar capacidade do Power BI Embedded no portal do Azure](azure-pbie-create-capacity.md)

> [!div class="nextstepaction"]
> [Capacidade e SKUs na análise incorporada do Power BI](embedded-capacity.md)

> [!div class="nextstepaction"]
> [O que é o Power BI Premium?](../../admin/service-premium-what-is.md)

> [!div class="nextstepaction"]
>[Incorporar para os seus clientes](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Incorporar para a sua organização](embed-sample-for-your-organization.md)