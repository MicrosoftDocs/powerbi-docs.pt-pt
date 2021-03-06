---
title: Suporte da Multi-Geo para a análise incorporada do Power BI, que permite melhores informações de BI incorporadas
description: Saiba como pode implementar conteúdos em datacenters em regiões diferentes da região base da sua solução de análise incorporada do Power BI. Utilize o suporte da Multi-Geo para permitir melhores informações de BI incorporadas para os seus clientes.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: nishalit
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 02/05/2019
ms.openlocfilehash: 4b9aacb460966f633161238cae82ba6731196ed4
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888288"
---
# <a name="multi-geo-support-for-power-bi-embedded"></a>Suporte da Multi-Geo para o Power BI Embedded

**Suporte da Multi-Geo para o Power BI Embedded** significa que os ISVs e as organizações que criam aplicações com o Power BI Embedded para incorporar análises nas suas aplicações podem agora implementar os seus dados em diferentes regiões em todo o mundo.

Agora, os clientes que utilizam o **Power BI Embedded** podem configurar uma **Capacidade A** através das opções **Multi-Geo**, com base nas mesmas funcionalidades e limitações que o [Power BI Premium suporta através da Multi-Geo](../../admin/service-admin-premium-Multi-Geo.md).

## <a name="creating-new-power-bi-embedded-capacity-resource-with-multi-geo"></a>Criar o novo recurso da Capacidade do Power BI Embedded com a Multi-Geo

No ecrã **Criar recurso**, tem de escolher a localização da sua capacidade. Até agora, estava limitada apenas à localização do seu inquilino do Power BI, ou seja, só estava disponível uma única localização. Com a Multi-Geo, pode escolher entre diferentes regiões para implementar a capacidade.

![Configuração da Multi-Geo do Power BI Embedded](media/embedded-multi-geo/pbie-multi-geo-setup.png)

Repare que, ao abrir o menu pendente de localizações, o inquilino principal está selecionado por predefinição.
  
![Localização predefinida da Multi-Geo do Power BI Embedded](media/embedded-multi-geo/pbie-multi-geo-default-location.png)

Ao escolher uma localização diferente, é apresentada uma mensagem para confirmar a sua seleção.

![Alteração da localização](media/embedded-multi-geo/pbie-multi-geo-location-change.png)

## <a name="view-capacity-location"></a>Ver a localização das Capacidades

Poderá ver facilmente a localização das suas capacidades na página de gestão principal do Power BI Embedded do portal do Azure.

![Capacidades com diferentes localizações](media/embedded-multi-geo/pbie-multi-geo-location-different.png)

Também está disponível no Portal de Administração do Powerbi.com. No portal de Administração, selecione "Definições de capacidade" e, em seguida, mude para o separador "Power BI Embedded".

![Ver no portal de administração](media/embedded-multi-geo/pbie-multi-geo-admin-portal.png)

[Saiba mais sobre como criar as capacidades com o Power BI Embedded.](azure-pbie-create-capacity.md)

## <a name="manage-existing-capacities-location"></a>Gerir a localização das capacidades existentes

Não pode alterar a localização de um recurso do Power BI Embedded depois de criar uma nova capacidade.

Para mover o conteúdo do Power BI para uma região diferente, siga estes passos:

1. [Crie uma nova capacidade](azure-pbie-create-capacity.md) numa região diferente.

2. Atribua todas as áreas de trabalho da capacidade existente à nova capacidade.

3. Elimine ou coloque em pausa a capacidade antiga.

É importante realçar que, se optar por eliminar uma capacidade sem reatribuir os respetivos conteúdos, todos os conteúdos nessa capacidade serão movidos para uma capacidade partilhada, localizada na sua região base.

## <a name="api-support-for-multi-geo"></a>Suporte de API para a Multi-Geo

Para suportar a gestão das capacidades com a Multi-Geo através da API, fizemos algumas alterações nas APIs existentes:

1. **[Capacidades Obter](/rest/api/power-bi/capacities/getcapacities)** – a API devolve uma lista de capacidades a que o utilizador tem acesso. A resposta inclui agora uma propriedade adicional chamada "região", que especifica a localização da capacidade.

2. **[Capacidade Atribuir A](/rest/api/power-bi/capacities)** – a API permite atribuir uma área de trabalho específica a uma capacidade. Esta operação não lhe permite atribuir áreas de trabalho a uma capacidade fora da sua região base nem mover as áreas de trabalho entre capacidades em regiões diferentes. Para efetuar esta operação, o [principal de serviço](embed-service-principal.md) ou utilizador ainda precisa de permissões de administrador na área de trabalho e de permissões de administrador ou de atribuição na capacidade de destino.

3. **[API do Azure Resource Manager](/rest/api/power-bi-embedded/capacities)** – todas as operações da API do Azure Resource Manager, incluindo *Criar* e *Eliminar*, suportam a Multi-Geo.

## <a name="limitations-and-considerations"></a>Limitações e considerações

* Confirme que qualquer movimentação que efetuar entre regiões está conforme todos os requisitos de conformidade empresariais e governamentais antes de iniciar a transferência de dados.

* Uma consulta em cache armazenada numa região remota permanece inativa nessa região. No entanto, os outros dados em trânsito podem ir e voltar entre diferentes localizações geográficas.

* Ao mover dados de uma região para outra num ambiente Multi-Geo, os dados de origem pode permanecer na região da qual foram movidos até um máximo de 30 dias. Durante esse período, os utilizadores não terão acesso aos dados. São removidos desta região e destruídos durante esse período de 30 dias.

* A Multi-Geo não resulta num melhor desempenho em geral. O carregamento de relatórios e dashboards ainda envolve pedidos de metadados à região base.

* Numa incorporação para o cenário dos seus clientes, o texto e o resultado da consulta continuam a transitar através do inquilino principal.

## <a name="next-steps"></a>Próximos passos

Saiba mais sobre as capacidades do Power BI Embedded e as opções Multi-Geo para todas as capacidades ao consultar as ligações abaixo.

* [O que é o Power BI Embedded?](azure-pbie-what-is-power-bi-embedded.md)

* [Criar uma capacidade do Power BI Embedded](azure-pbie-create-capacity.md)

* [Multi-Geo nas capacidades do Power BI Premium](../../admin/service-admin-premium-multi-geo.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)