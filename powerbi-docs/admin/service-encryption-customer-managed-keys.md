---
title: Utilizar chaves geridas pelo cliente no Power BI
description: Saiba como utilizar chaves geridas pelo cliente no Power BI.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 10/21/2020
LocalizationGroup: Premium
ms.openlocfilehash: fc93ae0f54bfe4f72ec18687829e9eb78dfaedd7
ms.sourcegitcommit: 3ddfd9ffe2ba334a6f9d60f17ac7243059cf945b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/22/2020
ms.locfileid: "92349374"
---
# <a name="use-customer-managed-keys-in-power-bi"></a>Utilizar chaves geridas pelo cliente no Power BI

O Power BI encripta dados inativos e em processamento. Por predefinição, o Power BI utiliza chaves geridas pela Microsoft para encriptar os seus dados. As organizações podem optar por utilizar chaves próprias para encriptação de conteúdos de utilizadores em inatividade no Power BI, de imagens de relatórios a conjuntos de dados importados em capacidades Premium. 

## <a name="why-use-customer-managed-keys"></a>Porquê utilizar as chaves geridas pelo cliente

Com as chaves geridas pelo cliente (CMK) do Power BI, as organizações podem cumprir requisitos de conformidade em encriptação de dados inativos com o seu fornecedor de serviços cloud (neste caso, a Microsoft). A CMK só é oferecida para novos clientes do Power BI Premium e permite que as organizações encriptem os respetivos conteúdos de utilizadores do Power BI com uma chave que elas fornecem e gerem. Revogar uma chave gerida pelo cliente torna os conteúdos no Power BI ilegíveis para todos, incluindo a Microsoft, dentro de uma hora. Face à oferta BYOK, as CMK também abrangem conteúdos de utilizadores que são gerados pelo serviço, além dos dados do cliente que são importados em relatórios e conjuntos de dados alojados em capacidades Premium, impõem políticas de colocação em cache mais rigorosas e só podem aplicar uma única chave para encriptar todos os dados.


## <a name="how-to-use-customer-managed-keys"></a>Como utilizar as chaves geridas pelo cliente
Para permitir as chaves geridas pelo cliente do Power BI, a sua organização tem de contactar o respetivo gestor de conta da Microsoft para confirmar se cumpre determinados requisitos de tamanho que são necessários para ativar a CMK.  


## <a name="next-steps"></a>Passos seguintes

As seguintes ligações disponibilizam informações que podem ser úteis para chaves geridas pelo cliente:

* [Chaves de encriptação por BYOK (Bring Your Own Key) para o Power BI](service-encryption-byok.md)
* [Configurar o suporte da Multi-Geo para o Power BI Premium](service-admin-premium-multi-geo.md)
* [Como funcionam as capacidades](service-premium-what-is.md#how-capacities-function)
* [Atualização incremental](service-premium-incremental-refresh.md).
