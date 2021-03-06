---
title: Controlo de versões do modelo de dados do Power BI na análise incorporada do Power BI para melhores informações de BI incorporadas
description: Modelo de Dados exposto por um Serviço OData. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 0c645774f7af1a8575ca3c755a74fd65b652031a
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887713"
---
# <a name="data-model-versioning"></a>Controlo de versões do Modelo de Dados

O Modelo de Dados exposto por um Serviço OData, como o modelo de dados do Power BI, define um contrato entre o serviço OData e os seus clientes. Os serviços têm permissão para expandir os modelos apenas até ao ponto em que tal não interrompe os clientes existentes. As alterações interruptivas, como a remoção de propriedades ou a alteração do tipo de propriedades existentes, exigem o fornecimento de uma nova versão do serviço num URL de raiz do serviço diferente para o novo modelo.  
  
As seguintes adições do Modelo de Dados são consideradas seguras e não necessitam de serviços para atribuir uma versão aos pontos de entrada.  
  
* Adicionar uma propriedade que pode ser nula ou que tem um valor predefinido; se tiver o mesmo nome que uma propriedade dinâmica existente, terá de ter o mesmo tipo (ou tipo base) que a propriedade dinâmica existente  
* Adicionar uma propriedade de navegação que pode ser nula ou que tem valor de coleção; se tiver o mesmo nome que uma propriedade de navegação dinâmica existente, terá de ter o mesmo tipo (ou tipo base) que a propriedade de navegação dinâmica existente  
* Adicionar um novo tipo de entidade ao modelo  
* Adicionar um novo tipo complexo ao modelo  
* Adicionar um novo conjunto de entidades  
* Adicionar uma nova singleton  
* Adicionar uma ação, uma função, uma importação de ação ou uma importação de função
* Adicionar um parâmetro de ação que pode ser nulo  
* Adicionar uma definição de tipo ou uma enumeração  
* Adicionar qualquer anotação a um elemento de modelo que não precisa de ser compreendido pelo cliente para interagir com o serviço corretamente  
  
Os clientes ***DEVEM** _ estar preparados para os serviços realizarem estas alterações incrementais aos seus modelos. Especificamente, os clientes devem estar preparados para receber propriedades e tipos derivados que não tenham sido anteriormente definidos pelo serviço.  
  
Os serviços _ *_NÃO DEVEM_** alterar os modelos de dados, consoante o utilizador autenticado. Se o modelo de dados for dependente de um utilizador ou grupo de utilizadores, todas as alterações TERÃO de ser alterações seguras, conforme definido nesta secção ao comparar o modelo completo com o modelo visível para os utilizadores com autorizações limitadas.  
  
Para mais informações acerca das normas do Modelo de Dados OData, veja [OData Version 4.0 Part 1: Protocol Plus Errata 02](https://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html) (OData Versão 4.0 Parte 1: Protocolo mais Errata 02).  
  
## <a name="see-also"></a>Ver também
[Visão geral da API REST do Power BI](/rest/api/power-bi/)