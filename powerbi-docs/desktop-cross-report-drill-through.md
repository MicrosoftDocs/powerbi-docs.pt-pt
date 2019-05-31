---
title: Utilizar a análise do relatório no Power BI Desktop
description: Aprenda a pesquisar através de um relatório, para outro no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 45a7cdd3c7b5324f3d618eaba4bdb3968a9549a5
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66375200"
---
# <a name="use-cross-report-drillthrough-in-power-bi-desktop"></a>Utilizar a análise do relatório no Power BI Desktop

Com a funcionalidade de análise do relatório no Power BI Desktop, pode ir contextualmente a partir de um relatório para outro relatório. Isso é verdade, desde que os relatórios são dentro da mesma área de trabalho ou aplicação no serviço Microsoft Power BI. Utilize a análise do relatório em vários para ligar duas ou mais relatórios que têm conteúdos relacionados e passar o contexto de filtro, juntamente com a ligação cruzada-relatório. Neste artigo, saiba como configurar a uma pormenorização em vários relatórios para relatórios do Power BI e o que os utilizadores experiência quando estiverem a utilizar a pormenorização entre-relatório por conta própria.

![Opção de pormenorização de captura de ecrã do Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

As seguintes definições são importantes para entender, antes de começarmos a configuração e utilização entre-relatório de pormenorização:

* **Elemento visual de origem:** O elemento visual que invoca a ação de pormenorização, utilizando o menu de contexto visual.
* **Relatório de origem:** O relatório que contém o elemento visual de origem para a análise do relatório em vários.
* **Página de destino:** A página que um utilizador pousar em após iniciar uma ação de pormenorização.
* **Relatório de destino:** O relatório que contém a página de destino para a análise do relatório em vários.

## <a name="enable-cross-report-drillthrough"></a>Ativar cruzada-relatório pormenorização

Para ativar um relatório para ser o destino de uma análise do relatório de cruzada, tem de ativar a funcionalidade para esse relatório na **opções** janela. Aceda a **arquivo** > **opções e definições** > **opções**e, em seguida, aceda a **comunicar definições** perto o na parte inferior da página à esquerda.

Selecione o **permitir que os elementos visuais neste relatório para usar destinos de pormenorização de outros relatórios** caixa de verificação, como mostrado na imagem seguinte.

![Janela de captura de ecrã das opções, com definições de relatório realçado](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

Cross-relatório pormenorização está agora ativada.

## <a name="set-up-cross-report-drillthrough"></a>Configurar o detalhamento de cross-relatório

Configurar a análise do relatório entre é semelhante ao configurar pormenorização dentro de um relatório. A pormenorização está ativada na página de destino, permitindo que os outros elementos visuais para a página ativada de pormenorização de destino. Para obter os passos criar a pormenorização dentro de um único relatório, consulte [utilizar a pormenorização no Power BI Desktop](desktop-drillthrough.md).

Para iniciar o processo de configuração, terá de efetuar alguns passos iniciais:

* Configure uma página de destino de pormenorização, que, em seguida, pode ser acedida a partir de outros relatórios na área de trabalho ou aplicação.
* Permitir que um relatório ver as páginas de pormenorização de fora do seu próprio relatório.

Encontre opções de pormenorização no **campos** secção a **visualizações** painel, conforme mostrado na imagem seguinte.

![Painel de captura de ecrã de visualizações, com opções de pormenorização realçado](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Habilitando o detalhamento de uma página a primeira etapa é validar os modelos de dados para os relatórios de origem e de destino. Certifique-se de que: 

* Existem campos de que pretende passar em ambos os modelos de dados.
* Os nomes dos campos e os nomes das tabelas ao qual pertencem, são idênticos (as cadeias de caracteres também tem de corresponder ao e diferenciam maiúsculas de minúsculas).

Por exemplo, se quiser passar um filtro no campo *país* dentro de tabela *geografia*, ambos os modelos têm de ter um *geografia* tabela e um *país* campo dentro dessa tabela. Caso contrário, tem de atualizar o nome do campo ou o nome de tabela no modelo subjacente. Simplesmente atualizar o nome a apresentar dos campos não funcionará corretamente para a análise do relatório em vários. (Observe que os esquemas de cada relatório não tem de ser exatamente igual.)

Para começar a utilizar com a configuração, terá de preparar-se a página de destino. No Power BI Desktop, vá para a página e certifique-se a **relatório entre** alternância de pormenorização está definida como **no**. 

![Captura de ecrã do botão de alternar entre-relatório definido como ativado](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Em seguida, arraste os campos que pretende utilizar como o destino de pormenorização para a tela. Selecione se pretende que o campo a ser utilizado como uma categoria ou resumido, como uma medida. Neste momento, pode selecionar se pretende desativar o **manter todos os filtros** alternar para o elemento visual. Se não quiser passar outros filtros aplicados da origem visual para sua pormenorização de destino visual, selecione **desativar**.

> [!NOTE]
> Se estiver a utilizar a página de pormenorização de relatório em vários apenas, deve excluir a **volta** botão que é adicionado automaticamente. O **volta** botão só funciona para nagivation dentro de um único relatório. 

Depois de configurar o elemento visual, certifique-se de guardar o relatório, se estiver no serviço Power BI, ou guardar e publicar o relatório se estiver a utilizar o Power BI Desktop.

A seção anterior descreveu como ativar a análise do relatório entre para o Power BI Desktop (no **opções** janela). Se estiver a utilizar o serviço Power BI para criar um destino de cross-relatório de pormenorização, para ativar a análise do relatório entre tem de: 

1. Selecione a área de trabalho nos quais o relatório de destino e o relatório de origem residem.
2. Selecione **relatórios**.
3. Selecione o **definições** ícone para o relatório de origem.
4. Certifique-se de que o botão de alternar entre-relatório de pormenorização está **no**.
5. Guarde o relatório.

Já está! Seu relatório estiver pronto para a experiência de análise do relatório em vários. 

Na próxima seção, vamos dar uma olhada na experiência da perspectiva do usuário.

## <a name="cross-report-drillthrough-experience"></a>Experiência de análise do relatório entre

Ao configurar a experiência de análise do relatório em vários para um relatório, pode colocar o recurso a utilizar.

Selecione o relatório de origem no serviço Power BI e, em seguida, selecione um elemento visual que utiliza o campo ou campos da forma que especificou quando configurou a página de destino. Em seguida, clique com botão direito um ponto de dados para abrir o menu de contexto visual e selecione **pormenorização**.

![Captura de ecrã do relatório de origem no serviço Power BI, com a pormenorização realçada](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Em seguida, verá os resultados na página de cross-relatório de pormenorização de destino, tal como configurá-los quando criou o destino. Os resultados são filtrados de acordo com as definições de pormenorização.

> [!IMPORTANT]
> O Power BI regista a análise do relatório em vários destinos. Se fizer alterações, certifique-se de que Atualize o browser se não vir os destinos de pormenorização conforme esperado. 

Relatório em vários destinos são formatados da seguinte forma: 

`Target Page Name [Target Report Name]`

Depois de selecionar a página de destino ao qual pretende pormenorizar, o Power BI acede a essa página. Ele passa ao longo do contexto de filtro com base nas definições da página de destino. 

Contexto de filtro de elemento visual de origem pode incluir o seguinte: 

* Relatório, página e filtros de nível visual, que afetam o elemento visual de origem. 
* Filtragem cruzada e realce cruzado que afetam o elemento visual de origem. 
* Segmentações de dados na página e segmentações de dados de sincronização.
* Parâmetros de URL.

Quando é apresentado o relatório de destino de pormenorização, Power BI só se aplica filtros para os campos para os quais encontrar cadeia exacta corresponde ao nome de campo e o nome da tabela. Power BI não se aplica adesivos filtros de relatório de destino. No entanto, é, aplicável seu indicador pessoais predefinido se existir. Por exemplo, se seu indicador pessoal padrão inclui um filtro de nível de relatório para *país = EUA*, o Power BI aplica em primeiro lugar, esse filtro antes de aplicar o contexto de filtro de elemento visual de origem. 

Para a análise do relatório entre, o Power BI passa o contexto de filtro para todas as páginas padrão no relatório de destino. Power BI não passa o contexto de filtro para as páginas de descrição, porque as páginas de descrição são filtradas com base no elemento visual de origem que invoca a dica de ferramenta.

Se quiser retornar para o relatório de origem após a ação de pormenorização de relatório em vários, utilize o browser **volta** botão. 

## <a name="next-steps"></a>Próximos passos

Poderá também estar interessado nos seguintes artigos:

* [Utilizar a segmentação de dados no Power BI Desktop](visuals/power-bi-visualization-slicers.md)
* [Utilizar a pormenorização no Power BI Desktop](desktop-drillthrough.md)

