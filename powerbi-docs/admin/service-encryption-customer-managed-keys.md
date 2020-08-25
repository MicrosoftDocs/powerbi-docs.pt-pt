---
title: Utilizar chaves geridas pelo cliente no Power BI
description: Saiba como utilizar chaves geridas pelo cliente no Power BI.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 08/12/2020
LocalizationGroup: Premium
ms.openlocfilehash: 8d13cc7a24486fada7f8d428ba52abeaa49d2518
ms.sourcegitcommit: b60063c49ac39f8b28c448908ecbb44b54326335
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/12/2020
ms.locfileid: "88160946"
---
# <a name="use-customer-managed-keys-in-power-bi"></a>Utilizar chaves geridas pelo cliente no Power BI

O Power BI encripta dados inativos e em processamento. Por predefinição, o Power BI utiliza chaves geridas pela Microsoft para encriptar os seus dados. As organizações podem optar por utilizar chaves próprias para encriptação de conteúdos de utilizadores em inatividade no Power BI, de imagens de relatórios a conjuntos de dados importados em capacidades Premium. 

## <a name="why-use-customer-managed-keys"></a>Porquê utilizar as chaves geridas pelo cliente
Com as chaves geridas pelo cliente (CMK) do Power BI, as organizações podem cumprir requisitos de conformidade em encriptação de dados inativos com o seu fornecedor de serviços cloud (neste caso, a Microsoft). As CMK permitem que as organizações encriptem os seus conteúdos de utilizadores do Power BI com uma chave que elas fornecem e gerem. Revogar uma chave gerida pelo cliente torna os conteúdos no Power BI ilegíveis para todos, incluindo a Microsoft, dentro de uma hora. Face à oferta BYOK, as CMK também abrangem conteúdos de utilizadores fora das capacidades Power BI Premium, impõem políticas de colocação em cache mais rigorosas e, por predefinição, ativam BYOK em todas as capacidades. 
 
## <a name="how-to-use-customer-managed-keys"></a>Como utilizar as chaves geridas pelo cliente
Para optar por receber as chaves geridas pelo cliente do Power BI, a sua organização tem de cumprir os requisitos de tamanho. O administrador global da sua organização tem de enviar um pedido de suporte para a Microsoft, ou pode contactar o gestor de conta Microsoft da sua organização para saber mais sobre o processo.  


## <a name="next-steps"></a>Passos seguintes

As seguintes ligações disponibilizam informações que podem ser úteis para chaves geridas pelo cliente:

* [Chaves de encriptação por BYOK (Bring Your Own Key) para o Power BI](service-encryption-byok.md)
* [Configurar o suporte da Multi-Geo para o Power BI Premium](service-admin-premium-multi-geo.md)
* [Como funcionam as capacidades](service-premium-what-is.md#how-capacities-function)
* [Atualização incremental](service-premium-incremental-refresh.md).
