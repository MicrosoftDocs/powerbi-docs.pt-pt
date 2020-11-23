---
title: Como comprar o Power BI Premium
description: Saiba como pode comprar o Power BI Premium e permitir a toda a sua organização o acesso a conteúdos.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: 2250a93d5fc061ff1e9d67217d021686935a8db7
ms.sourcegitcommit: cc20b476a45bccb870c9de1d0b384e2c39e25d24
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/11/2020
ms.locfileid: "94512729"
---
# <a name="how-to-purchase-power-bi-premium"></a>Como comprar o Power BI Premium

Este artigo descreve como pode comprar a capacidade do Power BI Premium para a sua organização. O artigo abrange os seguintes cenários:

- Utilizar SKUs P para cenários de produção típicos. Os SKUs P exigem um compromisso mensal ou anual e são faturados mensalmente.

Para obter mais informações sobre o Power BI Premium, veja [O que é o Power BI Premium?](service-premium-what-is.md). Para obter informações sobre os planos e preços atuais, veja a [Página de preços do Power BI](https://powerbi.microsoft.com/pricing/) e a [Calculadora Power BI Premium](https://powerbi.microsoft.com/calculator/). Os criadores de conteúdos continuam a precisar de uma [licença do Power BI Pro](service-admin-purchasing-power-bi-pro.md), mesmo que a sua organização utilize o Power BI Premium. Certifique-se de que compra, pelo menos, uma licença do Power BI Pro para a sua organização. Com os SKUs A, _todos os utilizadores_ que consomem conteúdos também necessitam de licenças Pro.

> [!NOTE]
> Se deixar uma subscrição Premium expirar, terá 30 dias de acesso total à sua capacidade. Depois desse período, os seus conteúdos serão revertidos para uma capacidade partilhada. Os modelos com mais de 1 GB não são suportados na capacidade partilhada.

> [!NOTE]
> O Power BI Premium lançou recentemente uma nova versão do Premium, denominada **Premium Gen2**, que está atualmente em pré-visualização. O Premium Gen2 irá simplificar a gestão de capacidades Premium e reduzirá a sobrecarga de gestão. Para obter mais informações, veja [Power BI Premium Generation 2 (pré-visualização)](service-premium-what-is.md#power-bi-premium-generation-2-preview).

## <a name="purchase-p-skus-for-typical-production-scenarios"></a>Comprar SKUs P para cenários de produção típicos

Pode criar um novo inquilino com um SKU P1 do Power BI Premium configurado ou pode comprar uma capacidade de Power BI Premium para uma organização existente. Em ambos os casos, pode então adicionar capacidade, se for necessário.

### <a name="create-a-new-tenant-with-power-bi-premium-p1"></a>Criar um novo inquilino com o Power BI Premium P1

Se não tiver um inquilino existente e pretender criar um, pode comprar o Power BI Premium ao mesmo tempo. A seguinte ligação irá orientá-lo no processo de criação de um novo inquilino e permitir que compre o Power BI Premium: [a oferta Power BI Premium P1](https://signup.microsoft.com/Signup?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1). Quando criar o inquilino, ser-lhe-á automaticamente atribuída a função de Administrador Global do Microsoft 365 para esse mesmo inquilino.

Após comprar capacidade, saiba como [gerir capacidades](service-admin-premium-manage.md#manage-capacity) e [atribuir áreas de trabalho](service-admin-premium-manage.md#assign-a-workspace-to-a-capacity) a uma capacidade.

### <a name="purchase-a-power-bi-premium-capacity-for-an-existing-organization"></a>Comprar uma capacidade do Power BI Premium para uma organização existente

Se tiver uma organização existente (inquilino), tem de ter a função Administrador de Faturação ou Administrador Global do Microsoft 365 para poder comprar subscrições e licenças. Para obter mais informações, consulte [Sobre as funções de administrador do Microsoft 365](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).

Para comprar uma capacidade Premium, siga estes passos.

1. No serviço Power BI, selecione o seletor de aplicações do Microsoft 365 e, em seguida, **Administrador**.

    ![Seletor de aplicações do Microsoft 365](media/service-admin-premium-purchase/o365-app-picker.png)

    Em alternativa, pode navegar para o centro de administração do Microsoft 365.

1. Selecione **Faturação** > **Comprar serviços**.

1. Em **Outros planos**, procure ofertas do Power BI Premium. Serão listadas como P1 a P3, EM3 e P1 (mês a mês).

1. Paire o cursor pelas reticências ( **. . .** ) e, em seguida, selecione **Comprar agora**.

    ![Comprar agora](media/service-admin-premium-purchase/premium-purchase.png)

1. Siga os passos para concluir a compra.

Depois de concluir a compra, a página **Comprar serviços** vai mostrar que o item foi comprado e está ativo.

![Adquiri o Power BI Premium](media/service-admin-premium-purchase/premium-purchased.png)

Após comprar capacidade, saiba como [gerir capacidades](service-admin-premium-manage.md#manage-capacity) e [atribuir áreas de trabalho](service-admin-premium-manage.md#assign-a-workspace-to-a-capacity) a uma capacidade.

### <a name="purchase-additional-capacities"></a>Comprar capacidades adicionais

Agora que possui uma capacidade, pode adicionar mais capacidades conforme as suas necessidades aumentarem. Pode utilizar uma combinação de SKUs com capacidade Premium (P1 a P3) na sua organização. Os vários SKUs oferecem-lhe diferentes capacidades de recursos.

1. No centro de administração do Microsoft 365, selecione **Faturação** > **Comprar serviços**.

1. Procure o item do Power BI Premium do qual pretende comprar mais em **Outros planos**.

1. Passe o cursor sobre **Mais opções** (...) e, em seguida, selecione **Alterar quantidade de licenças**.

    ![Alterar quantidade de licenças](media/service-admin-premium-purchase/premium-purchase-more.png)

1. Altere o número de instâncias que pretende ter para este item. Em seguida, selecione **Submeter** após concluir.

   > [!IMPORTANT]
   > Ao selecionar **Submeter**, o cartão de crédito registado será debitado.

A página **Comprar serviços** irá depois indicar o número de instâncias que tem. No portal de administração do Power BI, em **Definições de capacidades**, os núcleos virtuais disponíveis refletem a nova capacidade comprada.

![Núcleos virtuais disponíveis para a capacidade do Power BI Premium](media/service-admin-premium-purchase/premium-capacities.png)

### <a name="cancel-your-subscription"></a>Cancelar a sua subscrição

Pode cancelar a sua subscrição no centro de administração do Microsoft 365. Para cancelar a sua subscrição Premium, faça o seguinte.

1. Navegue para o centro de administração do Microsoft 365.

1. Selecione **Faturação** > **Subscrições**.

1. Selecione a sua subscrição do Power BI Premium na lista.

1. Selecione **Mais ações** > **Cancelar subscrição**.

1. A página **Cancelar subscrição** irá indicar se é responsável por uma [taxa de cessação antecipada](https://support.office.com/article/early-termination-fees-6487d4de-401a-466f-8bc3-c0beb5cc40d3). Esta página também indica quando os dados da subscrição serão eliminados.

1. Leia as informações e, se pretender avançar, selecione **Cancelar subscrição**.

#### <a name="when-canceling-or-your-license-expires"></a>Quando cancelar ou a licença expirar

Quando cancelar a sua subscrição Premium, ou a licença de capacidade expirar, pode continuar a aceder às suas capacidades Premium durante um período de 30 dias a contar da data de cancelamento ou da expiração da licença. Após 30 dias, deixará de poder aceder às capacidades Premium ou áreas de trabalho nas mesmas.

## <a name="purchase-a-skus-for-testing-and-other-scenarios"></a>Comprar SKUs A para testes e outros cenários

Também pode comprar SKUs A para testes e outros cenários, que fornecem a capacidade Premium por hora. Para obter mais informações e instruções, veja [Comprar o Power BI Premium para testes](service-admin-premium-testing.md).

## <a name="next-steps"></a>Passos seguintes

[Configurar e gerir capacidades no Power BI Premium](service-admin-premium-manage.md)\
[Página de preços do Power BI](https://powerbi.microsoft.com/pricing/)\
[Calculadora do Power BI Premium](https://powerbi.microsoft.com/calculator/)\
[FAQ do Power BI Premium](service-premium-faq.md)\
[Documento técnico sobre Planear uma Implementação Empresarial do Power BI](https://aka.ms/pbienterprisedeploy)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

O Power BI introduziu o Power BI Premium Gen2 como uma oferta de pré-visualização, que melhora a experiência do Power BI Premium nos seguintes aspetos:
* Desempenho
* Licenciamento por utilizador
* Maior dimensionamento
* Métricas melhoradas
* Dimensionamento automático
* Sobrecarga de gestão reduzida

Para obter mais informações sobre o Power BI Premium Gen2, veja [Power BI Premium Generation 2 (pré-visualização)](service-premium-what-is.md#power-bi-premium-generation-2-preview).