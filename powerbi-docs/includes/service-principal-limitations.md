---
title: Limitações do principal de serviço
description: Limitações do principal de serviço
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 06/06/2020
ms.custom: include file
ms.openlocfilehash: a8dd57b84f016ed798366898f4172ac9379ca26f
ms.sourcegitcommit: 02484b2d7a352e96213353702d60c21e8c07c6c0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/13/2020
ms.locfileid: "91989523"
---
## <a name="considerations-and-limitations"></a>Considerações e limitações

* O principal de serviço só funciona com as [novas áreas de trabalho](../collaborate-share/service-create-the-new-workspaces.md).
* **A Minha Área de Trabalho** não é suportada quando utilizar o principal de serviço.
* É necessária capacidade quando avançar para a produção.
* Não pode iniciar sessão no portal do Power BI com o principal de serviço.
* São necessários direitos de administrador do Power BI para ativar o principal de serviço nas definições de programador no portal de administração do Power BI.
* As aplicações [Incorporar para a sua organização](../developer/embedded/embed-sample-for-your-organization.md) não podem utilizar o principal de serviço.
* A gestão de [fluxos de dados](../transform-model/service-dataflows-overview.md) não é suportada.
* O principal de serviço atualmente não suporta APIs de administração.
* Quando utilizar o principal de serviço com uma origem de dados do [Azure Analysis Services](/azure/analysis-services/analysis-services-overview), o principal de serviço tem de ter permissões de instância do Azure Analysis Services. Não é possível utilizar um grupo de segurança que contém o principal de serviço para este efeito.