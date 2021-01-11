---
title: Dimensionar a sua capacidade do Power BI Embedded para a solução de BI incorporada da análise incorporada do Power BI
description: Este artigo explica como dimensionar uma capacidade do Power BI Embedded no Microsoft Azure para a sua solução de BI incorporada da análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
services: power-bi-embedded
editor: ''
tags: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 01/31/2019
ms.openlocfilehash: 19dfff03e2ec17c2b969a80c9fe0d2087c189184
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887322"
---
# <a name="scale-your-power-bi-embedded-capacity-in-the-azure-portal"></a>Dimensionar a sua capacidade do Power BI Embedded no portal do Azure

Este artigo explica como dimensionar uma capacidade do Power BI Embedded no Microsoft Azure. O dimensionamento permite-lhe aumentar ou diminuir o tamanho da sua capacidade.

Isto pressupõe que criou uma capacidade do Power BI Embedded. Se ainda não o fez, veja [Create Power BI Embedded capacity in the Azure portal](azure-pbie-create-capacity.md) (Criar capacidade do Power BI Embedded no portal do Azure) para começar.

> [!NOTE]
> Uma operação de dimensionamento pode demorar cerca de um minuto. Durante este período de tempo, a capacidade não estará disponível. Os conteúdos incorporados poderão não ser carregados.

## <a name="scale-a-capacity"></a>Dimensionar uma capacidade

1. Inicie sessão no [portal do Azure](https://portal.azure.com/).

2. Selecione **Todos os serviços** > **Power BI Embedded** para ver as suas capacidades.

    ![Todos os serviços no portal do Azure](media/azure-pbie-scale-capacity/azure-portal-more-services.png)

3. Selecione a capacidade que pretende dimensionar.

    ![Lista de capacidades do Power BI Embedded no portal do Azure](media/azure-pbie-scale-capacity/azure-portal-capacity-list.png)

4. Selecione **Escalão de preço** em **Dimensionar** na sua capacidade.

    ![Opção Escalão de preço em Dimensionar](media/azure-pbie-scale-capacity/azure-portal-scale-pricing-tier.png)

    O seu escalão de preço atual está destacado a azul.

    ![O escalão de preço atual tem um contorno a azul](media/azure-pbie-scale-capacity/azure-portal-current-tier.png)

5. Para aumentar ou diminuir o dimensionamento, selecione o novo escalão que pretende utilizar. Selecionar um novo escalão coloca um contorno azul à volta da seleção. Clique em **Selecionar** para dimensionar para o novo escalão.

    ![Selecionar o novo escalão](media/azure-pbie-scale-capacity/azure-portal-select-new-tier.png)

    O dimensionamento da sua capacidade poderá demorar um ou dois minutos até estar concluído.

6. Confirme o seu escalão ao verificar o separador da Descrição Geral. Estará apresentado o escalão de preço atual.

    ![Confirmar o escalão atual](media/azure-pbie-scale-capacity/azure-portal-confirm-tier.png)

## <a name="next-steps"></a>Próximos passos

Para colocar em pausa ou iniciar a sua capacidade, veja [Colocar em pausa e iniciar a sua capacidade do Power BI Embedded no portal do Azure](azure-pbie-pause-start.md).

Para começar a incorporar conteúdos do Power BI na sua aplicação, veja [Como incorporar os seus dashboards, relatórios e mosaicos do Power BI](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/).

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
