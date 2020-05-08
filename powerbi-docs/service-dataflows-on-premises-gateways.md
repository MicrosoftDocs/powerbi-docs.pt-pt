---
title: Utilizar fluxos de dados com origens de dados no local
description: Saiba como utilizar os dados no local nos fluxos de dados
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/08/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: efd110ad73b1bd72813d418a1f641613c88dc0d5
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "75762583"
---
# <a name="using-dataflows-with-on-premises-data-sources"></a>Utilizar fluxos de dados com origens de dados no local

Com os **fluxos de dados**, pode criar uma coleção de dados de várias origens, limpar os dados, transformá-los e, em seguida, carregá-los para o armazenamento do Power BI. Ao criar o fluxo de dados pode querer utilizar origens de dados no local. Este artigo esclarece sobre os requisitos associados à criação de fluxos de dados e sobre como o seu **Gateway de Empresa** tem de ser configurado para ativar essas ligações.

![Fluxos de dados e gateways](media/service-dataflows-onpremises-gateways/onpremises-gateways_01.png)

## <a name="configuring-an-enterprise-gateway-for-use-with-dataflows"></a>Configurar um Gateway de Empresa para utilização com os fluxos de dados

Para criar um fluxo de dados com um gateway, o utilizador tem de ser administrador do Gateway de Empresa ou o administrador tem de ter partilhado a origem de dados que planeia utilizar com o utilizador. 


> [!NOTE]
> Os fluxos de dados são apenas suportados através de Gateways de Empresa.

## <a name="using-an-on-premises-data-source-in-a-dataflow"></a>Utilizar uma origem de dados no local num fluxo de dados

Ao criar um fluxo de dados, selecione uma origem de dados no local na lista de origens de dados, conforme mostrado na imagem seguinte.

![Escolher uma origem de dados no local](media/service-dataflows-onpremises-gateways/onpremises-gateways_02a.png)

Depois de fazer a sua seleção, é-lhe pedido para indicar os detalhes da ligação do Gateway de Empresa, que será utilizado para aceder aos dados no local. Tem de selecionar o próprio gateway e indicar as credenciais do gateway selecionado.

![Indicar detalhes da ligação](media/service-dataflows-onpremises-gateways/onpremises-gateways_03.png)

## <a name="monitoring-your-gateway"></a>Monitorizar o gateway

Pode monitorizar o Gateway de Empresa para um fluxo de dados da mesma forma que monitoriza gateways para um conjunto de dados.

No ecrã de definições do fluxo de dados do Power BI, pode monitorizar o estado do gateway de um fluxo de dados e atribuir um gateway para o fluxo de dados, conforme mostrado na imagem seguinte.

![Monitorizar o gateway](media/service-dataflows-onpremises-gateways/onpremises-gateways_01.png)

## <a name="changing-a-gateway"></a>Alterar um gateway

Pode alterar o Gateway de Empresa utilizado para um determinado fluxo de dados de duas formas:

1. **Na ferramenta de criação** – pode alterar o gateway atribuído a todas as suas consultas com a ferramenta de criação de fluxos de dados.

    > [!NOTE]
    > O fluxo de dados tentará localizar ou criar as origens de dados necessárias com o novo gateway. Se não for possível, não será capaz de alterar o gateway até que todos os fluxos de dados necessários estejam disponíveis no gateway selecionado.

2. **No ecrã de definições** – pode alterar o gateway atribuído com o ecrã de definições do fluxo de dados do serviço Power BI.

Para saber mais sobre os Gateways de Empresa, veja [Gateway de dados no local](service-gateway-onprem.md).

## <a name="considerations-and-limitations"></a>Considerações e limitações

Existem algumas limitações conhecidas sobre a utilização de Gateways de Empresa e de fluxos de dados:

* Cada fluxo de dados pode utilizar apenas um gateway. Como tal, todas as consultas devem ser configuradas com o mesmo gateway.
* Alterar o gateway tem impacto sobre todo o fluxo de dados.
* Se forem necessários vários gateways, a prática recomendada será criar vários fluxos de dados (um para cada gateway) e utilizar as capacidades de referência de entidade ou de computação para unificar os dados.
* Os fluxos de dados são apenas suportados através de gateways de empresa. Os gateways pessoais não estarão disponíveis para seleção nas listas pendentes nem nos ecrãs de definições.


## <a name="next-steps"></a>Passos Seguintes

Este artigo fornece informações sobre a utilização da origem de dados no local para fluxos de dados e sobre como utilizar e configurar gateways para aceder a esses dados. Os seguintes artigos também podem ser úteis

* [Preparação personalizada de dados com fluxos de dados](service-dataflows-overview.md)
* [Criar e utilizar fluxos de dados no Power BI](service-dataflows-create-use.md)
* [Utilizar entidades calculadas no Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Recursos para programadores para fluxos de dados do Power BI](service-dataflows-developer-resources.md)

Para obter mais informações sobre o Power Query e a atualização agendada, pode ler estes artigos:
* [Descrição geral de consulta no Power BI Desktop](desktop-query-overview.md)
* [Configurar a atualização agendada](refresh-scheduled-refresh.md)

Para obter mais informações sobre o Common Data Service, pode ler o seguinte artigo de descrição geral:
* [Common Data Service – descrição geral](https://docs.microsoft.com/powerapps/common-data-model/overview)

