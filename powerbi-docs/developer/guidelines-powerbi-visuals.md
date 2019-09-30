---
title: Diretrizes para elementos visuais do Power BI
description: Saiba como pode publicar o seu elemento visual personalizado no AppSource para que outros o possam encontrar e utilizar através de uma compra.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: maghan
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 07/16/2019
ms.openlocfilehash: 71752a635c69e6712befbb00e942189fa4dacc36
ms.sourcegitcommit: e2c5d4561455c3a4806ace85defbc72e4d7573b4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71327739"
---
# <a name="guidelines-for-power-bi-visuals"></a>Diretrizes de elementos visuais do Power BI
Antes de [publicar](https://docs.microsoft.com/power-bi/developer/office-store) o seu elemento visual no AppSource para que outras pessoas o descubram e utilizem, certifique-se de que segue as diretrizes para criar uma ótima experiência para os seus utilizadores. 

## <a name="context-menu"></a>Menu de contexto
O menu de contexto é o menu de clique com o botão direito do rato apresentado quando o utilizador passa o rato sobre um elemento visual.
Todos os elementos visuais do Power BI devem permitir que o menu de contexto proporcione uma experiência unificada. Veja [este artigo](https://github.com/Microsoft/PowerBI-visuals/blob/gh-pages/tutorials/building-bar-chart/adding-context-menu-to-the-bar.md) para saber como adicionar um menu de contexto.


## <a name="logo-guidelines"></a>Diretrizes de logótipo
> [!NOTE]
> A palavra logótipo neste artigo refere-se a qualquer ícone de empresa comercial, conforme descrito nas imagens abaixo. 

Esta secção descreve as especificações para adicionar logótipos aos elementos visuais do Power BI. Os logótipos não são obrigatórios. Se forem adicionados, têm de seguir estas diretrizes. 

> [!IMPORTANT]
> Os logótipos são permitidos no *modo só de edição*. Os logótipos *não podem* ser apresentados no modo de visualização.


![Definições](media/guidelines-powerbi-visuals/definitions.png)

![Aspetos a ter em conta](media/guidelines-powerbi-visuals/things-to-keep-in-mind.png)

![Aspetos a evitar](media/guidelines-powerbi-visuals/things-to-avoid.png)

![Tamanho e formato](media/guidelines-powerbi-visuals/size-and-format.png)

![Margens e dimensionamento](media/guidelines-powerbi-visuals/margins-and-sizes.png)

![Modo de edição](media/guidelines-powerbi-visuals/logos-in-edit-mode.png)


Os ícones informativos, se existirem, no modo de leitura devem estar em conformidade com a cor, o tamanho e o local como logótipos acima.

## <a name="guidelines-for-power-bi-visuals-with-additional-purchases"></a>Diretrizes para elementos visuais do Power BI com compras adicionais

Até recentemente, o Marketplace (AppSource) aceitava apenas elementos visuais do Power BI gratuitos. Esta política foi alterada (dezembro de 2018) para que também possa submeter os elementos visuais para o AppSource com uma etiqueta de preço "Pode ser necessária a compra adicional". 

Os elementos visuais com a etiqueta “Pode ser necessária uma compra adicional” são semelhantes aos suplementos de compras via aplicação (IAP) na Loja Office. Os programadores também podem submeter estes elementos visuais para obter uma certificação depois de a equipa do AppSource os aprovar e confirmar que estão em conformidade com os requisitos de certificação. Para obter mais informações sobre os requisitos, veja [Elementos visuais certificados do Power BI](../power-bi-custom-visuals-certified.md).

> [!NOTE]
> Para o elemento visual ser certificado, não deve aceder a serviços externos ou recursos.

>[!IMPORTANT]  
> Se atualizar o seu elemento visual de gratuito para "Pode ser necessária a compra adicional", os utilizadores têm de receber o mesmo nível de funcionalidades gratuitas como antes da atualização. Opcionalmente, pode adicionar funcionalidades avançadas pagas para além das funcionalidades gratuitas existentes. Recomendamos que submeta os elementos visuais de IAP com as funcionalidades avançadas como novos elementos visuais e que não atualize as funcionalidades gratuitas existentes.

## <a name="what-changed-in-the-submission-process"></a>O que foi alterado no processo de submissão?

Os programadores carregam os elementos visuais de IAP no AppSource através do Dashboard de Vendedor, conforme têm vindo a fazer com os elementos visuais gratuitos. Para indicar que o elemento visual submetido tem funcionalidades de IAP, os programadores devem escrever nas notas do Dashboard de Vendedor: “Elemento visual com compra via aplicação”. Além disso, os programadores necessitam de fornecer um token ou chave de licença para que a equipa de validação possa validar as funcionalidades de IAP. Quando o elemento visual estiver validado e aprovado, a listagem do AppSource para o elemento visual de IAP apresentará a informação “Pode ser necessária uma compra adicional" sob as opções de preços.

## <a name="what-is-a-power-bi-visual-with-iap-features"></a>O que é um elemento visual do Power BI com funcionalidades de IAP?

Um elemento visual de IAP é um elemento visual *gratuito* que oferece *funcionalidades gratuitas*. Também tem algumas funcionalidades avançadas para as quais podem ser aplicados custos adicionais para serem utilizadas. Na descrição do elemento visual, os programadores têm de notificar os utilizadores sobre as funcionalidades que exigem compras adicionais para poderem ser utilizadas. Atualmente, a Microsoft não disponibiliza APIs nativas para suportar a compra de aplicações e suplementos.

Os programadores podem utilizar qualquer sistema de pagamento externo para estas compras. Para obter mais informações, veja a [nossa política de loja](https://docs.microsoft.com/office/dev/store/validation-policies#2-apps-or-add-ins-can-display-certain-ads).

> [!NOTE]
> Não são permitidas marcas d'água nas funcionalidades ou elementos visuais gratuitos. As marcas d'água só podem ser utilizadas em funcionalidades pagas utilizadas sem uma licença válida. Recomendamos que seja apresentada uma janela pop-up com todas as informações relacionadas com a licença, caso as funcionalidades pagas avançadas sejam utilizadas sem uma licença válida.  


## <a name="best-practices"></a>Melhores práticas

### <a name="visual-landing-page"></a>Página de destino da aplicação

Utilize a página de destino para esclarecer aos utilizadores como podem utilizar o elemento visual e onde comprar a licença. Não inclua vídeos acionados automaticamente. Adicione apenas material que ajude a melhorar a experiência do utilizador, tais como informações ou ligações para detalhes da compra da licença e como utilizar as funcionalidades de IAP.

### <a name="license-key-and-token"></a>Chave de licença e token

Para comodidade do utilizador, adicione campos relativos à chave de licença ou token na parte superior do painel de formatação.

## <a name="faq"></a>PERGUNTAS FREQUENTES

Para obter mais informações acerca dos elementos visuais, aceda às [Perguntas frequentes sobre os elementos visuais com compras adicionais](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-faq#visuals-with-additional-purchases).

## <a name="next-steps"></a>Próximos passos

Saiba como pode publicar o seu elemento visual personalizado no [AppSource](office-store.md) para que outros o possam encontrar e utilizar.
