---
title: Utilizar o analisador de desempenho para examinar o desempenho de elemento de relatório no Power BI Desktop
description: Descubra como os elementos visuais e elementos do relatório estão a efetuar em termos de utilização de recursos e a capacidade de resposta
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1851e0a55bf01073a6591f64de43830a72eca89b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65854419"
---
# <a name="use-performance-analyzer-to-examine-report-element-performance"></a>Utilizar o analisador de desempenho para examinar o desempenho de elemento de relatório

Na **Power BI Desktop** pode encontrar fora como cada um dos elementos do relatório, como os elementos visuais e as fórmulas DAX está a efetuar. Utilizar o **Performance Analyzer**, pode ver e registos de registo que medir a forma como cada um dos elementos do relatório executa quando os utilizadores interagem com eles e quais aspectos do seu desempenho são a maior parte (ou menos) utilizar muitos recursos.

![Analisador de desempenho](media/desktop-performance-analyzer/performance-analyzer-01.png)

Analisador de desempenho inspeciona e apresenta o período necessário para a atualização ou atualizar todos os elementos visuais que interações de utilizador iniciar e apresenta as informações para que pode ver, desagregar ou exportar os resultados. Analisador de desempenho pode ajudá-lo a identificar os elementos visuais que estejam a afetar o desempenho dos seus relatórios e identificar o motivo para o impacto.

## <a name="displaying-the-performance-analyzer-pane"></a>Exibindo o painel do analisador de desempenho

Na **Power BI Desktop** selecione a **vista** faixa de opções. Na **mostrar** área da **vista** faixa de opções, pode selecionar a caixa de verificação junto a **analisador de desempenho** para mostrar o painel do analisador de desempenho.

![Selecione o analisador de desempenho no Friso ver](media/desktop-performance-analyzer/performance-analyzer-02.png)

Depois de selecionada, o analisador de desempenho é apresentado no seu próprio painel, à direita da tela do relatório.

## <a name="using-performance-analyzer"></a>Utilizar o analisador de desempenho

Medidas de analisador de desempenho o tempo de processamento (incluindo o tempo para criar ou atualizar um elemento visual) necessário para atualizar os elementos de relatório iniciados como resultado de qualquer interação do utilizador que resulta na execução de uma consulta. Por exemplo, ajustar uma segmentação de dados requer o visual de segmentação de dados deve ser modificada, uma consulta a serem enviados para o modelo de dados e os elementos visuais afetados que têm de ser atualizados como resultado das novas definições. 

Para que o analisador de desempenho, iniciar a gravação, basta selecionar **iniciar a gravação**

![Iniciar gravação](media/desktop-performance-analyzer/performance-analyzer-03.png)

Todas as ações tomadas durante o relatório são apresentadas e com sessão iniciadas no painel de analisador de desempenho, na ordem em que o elemento visual é carregado pelo Power BI. Por exemplo, talvez tenha um relatório que os utilizadores disseram demora muito tempo a atualizar. Ou, determinados elementos visuais num relatório demoram muito tempo a apresentar quando um controlo de deslize é ajustado. Analisador de desempenho pode informar a o controlo é o culpado e identifica quais aspectos do elemento visual está a demorar a duração mais longa para processar. 

Depois de começar a gravação, o **inicio a gravação** botão está desativado fora (inativa, uma vez que já tenha começado gravação) e o **parar** botão está ativo. 

Analisador de desempenho recolhe e apresenta as informações de medição de desempenho em tempo real. Para que cada vez que clica num elemento visual, mover uma segmentação de dados ou interaja de qualquer outra forma, o analisador de desempenho mostra imediatamente os resultados de desempenho no seu painel.

Se o painel tem mais informações que podem ser apresentados, é apresentada uma barra de rolagem navegar para obter informações adicionais.

Cada interação do utilizador tem um identificador de seção no painel, que descreve a ação que iniciou as entradas de registo. Na imagem seguinte, a interação era que os utilizadores alterada uma segmentação de dados.

![Com base no tipo de interação de secções](media/desktop-performance-analyzer/performance-analyzer-04.png)

Informações de registo de cada elemento visual incluem o tempo gasto (duração) para concluir as seguintes categorias de tarefas:

* **Consulta DAX** -se de uma consulta DAX era necessária, este é o tempo entre o elemento visual enviando a consulta e para o Analysis Services devolver os resultados.
* **Apresentação visual** -tempo necessário para o elemento visual desenhar na tela, incluindo o tempo necessário para obter as imagens de web ou de uma geocodificação. 
* **Outros** -tempo necessário pelo elemento visual para consultas de preparação, à espera de outros elementos visuais concluir ou efetuar outro processamento em segundo plano.

![elementos de informações de registo](media/desktop-performance-analyzer/performance-analyzer-06.png)

Após interagir com elementos do relatório que pretende medir com o analisador de desempenho, pode selecionar o **parar** botão. As informações de desempenho permanecem no painel de depois de selecionar **parar** para analisar.

Para limpar as informações no painel de analisador de desempenho, selecione **limpar**. Todas as informações são apagadas e não são guardadas quando seleciona **clara**. Veja a secção seguinte para aprender a guardar as informações nos registos. 

## <a name="refreshing-visuals"></a>Atualizar os elementos visuais

Pode selecionar **atualizar elementos visuais** no painel de analisador de desempenho para atualizar todos os elementos visuais na página atual do relatório e, deste modo, ter o analisador de desempenho a recolher informações sobre todos esses elementos visuais.

Também pode atualizar os elementos visuais individuais. Quando o analisador de desempenho está gravando, pode selecionar **atualizar este elemento visual** encontrado no canto superior direito de cada elemento visual, para atualizar esse elemento visual e capturar as informações de desempenho.

![atualizar um elemento visual individual](media/desktop-performance-analyzer/performance-analyzer-07.png)

## <a name="saving-performance-information"></a>Ao guardar as informações de desempenho

Pode salvar as informações que cria o analisador de desempenho sobre um relatório ao selecionar o **exportar** botão. Selecionando **exportar** cria um ficheiro. JSON com informações a partir do painel de analisador de desempenho. 

![Guarde o ficheiro de registo para o analisador de desempenho](media/desktop-performance-analyzer/performance-analyzer-05.png)


## <a name="next-steps"></a>Próximos passos
Para obter mais informações sobre o **Power BI Desktop**, e sobre como começar, consulte os seguintes artigos.

* [O que é o Power BI Desktop?](desktop-what-is-desktop.md)
* [Descrição Geral das Consultas no Power BI Desktop](desktop-query-overview.md)
* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Ligar a Dados no Power BI Desktop](desktop-connect-to-data.md)
* [Moldar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tarefas Comuns de Consulta no Power BI Desktop](desktop-common-query-tasks.md)   

