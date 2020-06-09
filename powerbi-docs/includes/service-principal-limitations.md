---
title: Limitações do principal de serviço
description: Limitações do principal de serviço
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 06/06/2020
ms.custom: include file
ms.openlocfilehash: 8e50a529bfd398a4075ebf049ee4aec1bcf48b4d
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315848"
---
## <a name="considerations-and-limitations"></a>Considerações e limitações

* O principal de serviço só funciona com as [novas áreas de trabalho](../collaborate-share/service-create-the-new-workspaces.md).
* **A Minha Área de Trabalho** não é suportada quando utilizar o principal de serviço.
* É necessária capacidade dedicada quando avançar para a produção.
* Não pode iniciar sessão no portal do Power BI com o principal de serviço.
* São necessários direitos de administrador do Power BI para ativar o principal de serviço nas definições de programador no portal de administração do Power BI.
* As aplicações [Incorporar para a sua organização](../developer/embedded/embed-sample-for-your-organization.md) não podem utilizar o principal de serviço.
* A gestão de [fluxos de dados](../transform-model/service-dataflows-overview.md) não é suportada.
* O principal de serviço atualmente não suporta APIs de administração.
* Quando utilizar o principal de serviço com uma origem de dados do [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-overview), o principal de serviço tem de ter permissões de instância do Azure Analysis Services. Não é possível utilizar um grupo de segurança que contém o principal de serviço para este efeito.