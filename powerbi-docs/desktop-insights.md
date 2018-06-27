---
title: Utilizar as informações no Power BI Desktop (Pré-visualização)
description: Obter facilmente informações sobre aumentos ou diminuições no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 2b5959049b65d32eebf7f484e8485ff59a10f459
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/26/2018
ms.locfileid: "34286089"
---
# <a name="use-insights-in-power-bi-desktop-preview"></a>Utilizar as informações no Power BI Desktop (Pré-visualização)
Pode indicar ao **Power BI Desktop** que explique aumentos ou diminuições em gráficos e obter análises rápidas, automatizadas e informativas sobre os seus dados. Basta clicar com o botão direito do rato num ponto de dados e selecionar **Analisar > Explicar a diminuição** (ou aumento, se a barra anterior era mais baixa), e as informações são-lhe entregues numa janela fácil de utilizar.

![](media/desktop-insights/insights_01.png)

A funcionalidade de informações é contextual e baseia-se no ponto de dados imediatamente anterior (como a barra ou coluna anterior).

> [!NOTE]
> Esta funcionalidade encontra-se em pré-visualização e encontra-se sujeita a alterações. A funcionalidade de informações está ativada por predefinição (não precisa de assinalar uma caixa de Pré-visualização para ativá-la) a partir da versão do **Power BI Desktop** de setembro de 2017.
> 
> 

## <a name="using-insights"></a>Utilizar informações
Para utilizar as informações, clique com o botão direito do rato num ponto de dados num visual de barra ou linha e selecione **Analisar > Explicar o aumento** (ou *Explicar a diminuição*, uma vez que todas as informações se baseiam na alteração face ao ponto de dados anterior).

![](media/desktop-insights/insights_02.png)

Depois, o **Power BI Desktop** executa algoritmos de aprendizagem automática nos dados e preenche uma janela com um visual e uma descrição que descreve quais as categorias que mais influenciaram o aumento ou a diminuição. Por predefinição, as informações são apresentadas como visual de *cascata*, conforme mostrado na seguinte imagem.

![](media/desktop-insights/insights_03.png)

Ao selecionar os pequenos ícones na parte inferior do visual de cascata, pode optar por ter as informações apresentadas em gráfico de dispersão, gráfico de colunas empilhadas ou gráfico de friso.

![](media/desktop-insights/insights_04.png)

Os ícones de *polegar para cima* e *polegar para baixo* na parte inferior da página são fornecidos para que possa dar feedback sobre o visual e a funcionalidade.

Uma nota importante: o botão **+** na parte superior do visual permite-lhe adicionar o visual selecionado ao relatório, como se tivesse criado o visual manualmente. Depois, pode formatar ou ajustar de outra forma o visual adicionado, como faria com outros visuais no seu relatório. Só pode adicionar um visual de informação selecionado quando estiver a editar um relatório no **Power BI Desktop**.

Pode utilizar as informações quando o seu relatório estiver em modo de leitura ou de edição, tornando-o versátil para analisar dados e para criar visuais que poderá facilmente adicionar aos seus relatórios.

## <a name="considerations-and-limitations"></a>Considerações e limitações
Uma vez que as informações baseiam-se na alteração face ao ponto de dados anterior, não estão disponíveis quando selecionar o primeiro ponto de dados num visual. 

A lista seguinte é a coleção de cenários atualmente não suportados para **informações**:

* Filtros de Primeiros N
* Filtros de inclusão/exclusão
* Filtros de medição
* Agregados e medidas não cumulativas
* Mostrar valor como
* Medidas filtradas (o novo elemento que utilizamos para gráficos de dispersão em informações)
* Colunas categóricas no eixo X, a menos que defina uma ordenação por coluna escalar. Se utilizar uma hierarquia, todas as colunas na hierarquia ativa terão de cumprir esta condição
* Medidas não numéricas

Além disso, os seguintes tipos de modelos e origens de dados não são atualmente suportados para informações:

* DirectQuery
* Ligação em direto
* Reporting Services no local
* Incorporação

## <a name="next-steps"></a>Próximos passos
Para obter mais informações sobre o **Power BI Desktop**, e sobre como começar, consulte os seguintes artigos.

* [Introdução ao Power BI Desktop](desktop-getting-started.md)
* [Descrição Geral das Consultas no Power BI Desktop](desktop-query-overview.md)
* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Ligar a Dados no Power BI Desktop](desktop-connect-to-data.md)
* [Moldar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tarefas Comuns de Consulta no Power BI Desktop](desktop-common-query-tasks.md)   

