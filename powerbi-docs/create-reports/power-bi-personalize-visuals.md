---
title: Permitir que os utilizadores personalizem elementos visuais num relatório
description: Permita que os leitores do relatório criem uma vista própria para o relatório sem o editarem.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/21/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 0fdee37f682774e1dac2b1ac6a4fc7a6e8dabe91
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85238091"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>Permitir que os utilizadores personalizem elementos visuais num relatório

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Quando partilha um relatório com uma audiência alargada, alguns utilizadores podem querer ver vistas ligeiramente diferentes de elementos visuais específicos. Poderão querer trocar os dados no eixo, alterar o tipo de elemento visual ou adicionar algo à descrição. É difícil criar um elemento visual que satisfaça os requisitos de todos. Com esta nova capacidade, permite aos seus consumidores explorar e personalizar elementos visuais, tudo na vista de leitura do relatório. Podem ajustar o elemento visual conforme preferirem e guardá-lo como marcador para consulta posterior. Não precisam de ter permissão de edição no relatório nem de contactar o autor do relatório para fazer alterações.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="Personalizar um elemento visual":::
 
## <a name="what-report-consumers-can-change"></a>O que os consumidores de relatórios podem alterar

Esta funcionalidade permite aos consumidores obter mais informações através de uma exploração ad-hoc dos elementos visuais num relatório do Power BI. Para saber mais sobre como utilizar esta funcionalidade como cliente, veja [Personalizar os elementos visuais nos seus relatórios](../consumer/end-user-personalize-visuals.md). Esta funcionalidade é ideal para criadores de relatórios que pretendem permitir cenários básicos de exploração para os leitores dos seus relatórios. Eis as modificações que os leitores de relatórios podem fazer:

- Alterar o tipo de visualização
- Trocar uma medida ou dimensão
- Adicionar ou remover uma legenda
- Comparar duas ou mais medidas
- Alterar agregações, etc.

Esta funcionalidade permite novas capacidades de exploração, além de incluir formas de os consumidores capturarem e partilharem as suas alterações:

- Capturar as suas alterações
- Partilhar as suas alterações
- Repor todas as suas alterações a um relatório
- Repor todas as suas alterações a um elemento visual
- Limpar as suas alterações recentes

## <a name="turn-on-the-preview-feature"></a>Ativar a funcionalidade de pré-visualização

Uma vez que esta funcionalidade está em pré-visualização, terá de ativar o botão da funcionalidade primeiro. Aceda a **Ficheiro** > **Opções e Definições** > **Opções**. Em **Definições** globais > **Funcionalidades de pré-visualização**, certifique-se de que **Elementos visuais personalizados** está selecionado.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-preview-personalize-visual.png" alt-text="Ativar Personalizar elementos visuais":::

Poderá ter de reiniciar o Power BI Desktop para o ver nas definições do ficheiro atual.

## <a name="enable-personalization-in-a-report"></a>Ativar a personalização num relatório

Depois de ativar o interruptor de pré-visualização, terá de o ativar especificamente para os relatórios para os quais pretende que os consumidores possam personalizar elementos visuais.

A funcionalidade pode ser ativada no Power BI Desktop ou no serviço Power BI.

### <a name="in-power-bi-desktop"></a>No Power BI Desktop

Para ativar a funcionalidade no Power BI Desktop, aceda a **Ficheiro** > **Opções e Definições** > **Opções** > **Ficheiro atual** > **Definições de relatórios**. Certifique-se de que a opção **Personalizar elementos visuais (pré-visualização)** está ativada.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-settings-personalize-visual.png" alt-text="Ativar a personalização num relatório":::

### <a name="in-the-power-bi-service"></a>No serviço Power BI

Para ativar a funcionalidade no serviço Power BI, aceda às **Definições** do seu relatório.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-settings-personalize-visual.png" alt-text="Definições de relatórios no serviço Power BI":::

Ative a opção **Personalizar elementos visuais (pré-visualização)**  > **Guardar**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-personalize-visual.png" alt-text="Ativar Personalizar elementos visuais no serviço":::

## <a name="select-visuals-that-can-be-personalized"></a>Selecionar elementos visuais que possam ser personalizados

Quando ativa esta definição para um determinado relatório, por predefinição, todos os elementos visuais nesse relatório podem ser personalizados. Se não quiser que todos os elementos visuais sejam personalizados, pode ativar ou desativar a definição por elemento visual.

Selecione o elemento visual > selecione **Formatar** no painel **Visualizações** > expanda **Cabeçalho de elemento visual**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-header-personalize.png" alt-text="Selecionar Cabeçalho de elemento visual":::
 
Deslize a opção **Personalizar elemento visual** para a posição  >  **Ativado** ou **Desativado**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-personalize-on-off.png" alt-text="Deslizar a opção Personalizar elemento visual para a posição ativado ou desativado":::


## <a name="limitations-and-known-issues"></a>Limitações e problemas conhecidos

Atualmente, a funcionalidade tem algumas limitações que devem ser tidas em conta.

- Esta funcionalidade não é suportada em cenários de incorporação, incluindo publicar na Web.
- As explorações de utilizadores não persistem automaticamente. Tem de guardar a sua vista como um marcador pessoal para capturar as alterações.
- Esta funcionalidade é suportada nas aplicações móveis do Power BI para tablets iOS e Android e na aplicação Windows do Power BI; não é suportada nas aplicações móveis do Power BI para telemóveis. No entanto, qualquer alteração a um elemento visual que guardar num marcador pessoal enquanto está no serviço Power BI vai ser respeitada em todas as aplicações móveis do Power BI.

Também existem problemas conhecidos que estamos a resolver:

- A adição de hierarquias não é suportada. Tem de adicionar os itens subordinados individuais.
- Não pode alterar uma hierarquia de data para uma data ou vice-versa. 
- Com os marcadores pessoais, poderá obter resultados ligeiramente diferentes consoante a sequência que selecionar. É possível que haja discrepâncias, porque não capturamos o estado completo do relatório, apenas as modificações efetuadas. Para contornar esta situação, selecione **Repor para predefinição** e, em seguida, selecione o marcador que pretende ver. 

## <a name="next-steps"></a>Passos seguintes

[Personalizar os elementos visuais nos seus relatórios](../consumer/end-user-personalize-visuals.md).     

Experimente a nova experiência de personalização de elementos visuais. Envie-nos os seus comentários sobre esta funcionalidade e indique-nos como a podemos continuar a melhorar no [site Power BI Ideas](https://ideas.powerbi.com/forums/265200-power-bi). 

Mais perguntas? [Tente a Comunidade do Power BI](https://community.powerbi.com/)
