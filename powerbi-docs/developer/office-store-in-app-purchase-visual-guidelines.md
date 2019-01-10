---
title: Pode ser necessária uma compra adicional – Diretrizes de Elementos Visuais do Power BI
description: Saiba como pode publicar o seu elemento visual personalizado no AppSource para que outros o possam encontrar e utilizar através de uma compra.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 11/26/2018
ms.openlocfilehash: 2b7a71baafd8ec2ef839aaca95529221c642357f
ms.sourcegitcommit: c09241803664643e1b2ba0c150e525e1262ca466
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54072181"
---
# <a name="guidelines-for-power-bi-visuals-with-additional-purchases"></a>Diretrizes para elementos visuais do Power BI com compras adicionais

Até recentemente, o **Marketplace (AppSource)** aceitava apenas elementos visuais do Power BI gratuitos. Esta política está a mudar para que os elementos visuais com a etiqueta "pode ser necessária uma compra adicional" também possam ser enviados para o **AppSource**. Os elementos visuais com possibilidade de compra adicional são semelhantes às compras de suplementos na aplicação (IAP) na loja do Office. Os programadores também podem submeter estes elementos visuais para obter uma certificação depois de a equipa do **AppSource** os aprovar e se certificar de que estão em conformidade com os requisitos de certificação, conforme descrito no [artigo sobre elementos visuais personalizados certificados](../power-bi-custom-visuals-certified.md).

> [!Note]
> Para o elemento visual ser certificado, não deve aceder a serviços externos ou recursos.

## <a name="whats-changing-in-the-submission-process"></a>O que está a ser alterado no processo de submissão?

Os programadores carregam os elementos visuais de IAP no AppSource através do Dashboard de Vendedor, conforme têm vindo a fazer com os elementos visuais gratuitos. Para indicar que o elemento visual submetido tem funcionalidades de IAP, os programadores devem escrever nas notas do dashboard do vendedor: "Elemento visual com compra na aplicação". Além disso, os programadores necessitam de fornecer um token ou chave de licença para que a equipa de validação possa validar as funcionalidades de IAP. Quando o elemento visual estiver validado e aprovado, a listagem do AppSource para os estados dos elementos visuais de IAP apresentará a informação "Pode ser necessária uma compra adicional" sob as opções de preços.

## <a name="what-is-a-power-bi-visual-with-iap-features"></a>O que é um elemento visual do Power BI com funcionalidades de IAP?

Um elemento visual de IAP oferece funcionalidades gratuitas e ainda funcionalidades adicionais que podem exigir custos extra para serem utilizadas. Os programadores têm de notificar os utilizadores na descrição do elemento visual sobre as funcionalidades que exigem compras adicionais para poderem ser utilizadas. Atualmente, a Microsoft não fornece interface de programação de aplicações (APIs) nativas para suportar as compras via aplicação e suplementos. Os programadores podem utilizar qualquer sistema de pagamento externo para essas compras. Consulte a [política](https://docs.microsoft.com/office/dev/store/validation-policies#2-apps-or-add-ins-can-display-certain-ads) da nossa loja.

## <a name="logo-guidelines"></a>Diretrizes de logótipo

Esta secção descreve as especificações para adicionar logótipos aos elementos visuais.

> [!NOTE]
> Os logótipos só são permitidos no modo de edição. Os logótipos não podem ser apresentados no modo de visualização.

![definições](media/office-store-in-app-purchase-visual-guidelines/definitions.png)

![coisas-a-manter](media/office-store-in-app-purchase-visual-guidelines/things-to-keep-in-mind.png)

![coisas-para](media/office-store-in-app-purchase-visual-guidelines/things-to-avoid.png)

![tamanho-e-formato ](media/office-store-in-app-purchase-visual-guidelines/size-and-format.png)

![margens- e](media/office-store-in-app-purchase-visual-guidelines/margins-and-sizes.png)

![modo-de-edição](media/office-store-in-app-purchase-visual-guidelines/logos-in-edit-mode.png)

## <a name="best-practices"></a>Melhores práticas

### <a name="visual-landing-page"></a>Página de destino da aplicação

Utilize a página de destino para esclarecer aos utilizadores como podem utilizar o elemento visual e onde comprar a licença. Não inclua vídeos acionados automaticamente. Adicione apenas material que ajude a melhorar a experiência do utilizador, tais como informações ou ligações nos detalhes da compra da licença e como utilizar as funcionalidades de IAP.

### <a name="license-key-and-token"></a>Chave de licença e token

Para comodidade do utilizador, adicione campos relativos à chave de licença ou token na parte superior do painel de formatação, para ficarem numa localização mais conveniente para os utilizadores.

## <a name="faq"></a>PERGUNTAS FREQUENTES

Para obter mais informações e respostas a perguntas, aceda às [Perguntas frequentes sobre os elementos visuais com compras adicionais](https://docs.microsoft.com/en-us/power-bi/power-bi-custom-visuals-faq#visuals-with-additional-purchases).

## <a name="next-steps"></a>Próximos passos

Saiba como pode publicar o seu elemento visual personalizado no [AppSource](office-store.md) para que outros o possam encontrar e utilizar.
