---
title: Utilizar a pormenorização entre relatórios no Power BI Desktop
description: Saiba como pormenorizar de um relatório para outro no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/18/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 7189ef77446446b56b1dcb55b43b022d0fc5c057
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/03/2019
ms.locfileid: "73868767"
---
# <a name="use-cross-report-drillthrough-in-power-bi-desktop"></a>Utilizar a pormenorização entre relatórios no Power BI Desktop

Com a funcionalidade de pormenorização entre relatórios no Power BI Desktop, pode saltar contextualmente de um relatório para outro, o que funcionará se os relatórios estiverem dentro da mesma área de trabalho ou aplicação no serviço Power BI. Utilize a pormenorização entre relatórios para ligar dois ou mais relatórios que têm conteúdo relacionado e para transmitir o contexto de filtro junto com a ligação de um relatório para outro. Neste artigo, vai aprender a configurar uma pormenorização entre relatórios para os relatórios do Power BI e o que os utilizadores sentirão por si mesmos quando utilizarem a pormenorização entre relatórios.

![Captura de ecrã da opção de pormenorização do Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

É importante compreender as definições a seguir, antes de começarmos a configurar e a utilizar a pormenorização de relatórios cruzados:

* **Elemento visual de origem:** o elemento visual que invoca a ação de pormenorização ao utilizar o menu de contexto do elemento visual.
* **Relatório de origem:** o relatório que contém o elemento visual de origem para pormenorização entre relatórios.
* **Página de destino:** a página à qual chega o utilizador depois de iniciar uma ação de pormenorização.
* **Relatório de destino:** o relatório que contém a página de destino para a pormenorização entre relatórios.


> [!NOTE]
> Com a funcionalidade de pormenorização entre relatórios no Power BI Desktop, pode saltar contextualmente de um relatório para outro, o que funcionará se os relatórios estiverem dentro da mesma área de trabalho ou aplicação no serviço Power BI. Tal não é aplicável quando acede individualmente a relatórios partilhados em *A Minha Área de Trabalho* ([Relatórios partilhados comigo](service-share-dashboards.md#share-a-dashboard-or-report)); em vez disso, tem de aceder ao relatório na área de trabalho a partir da qual este foi partilhado originalmente.


## <a name="enable-cross-report-drillthrough"></a>Ativar a pormenorização entre relatórios

Para permitir que um relatório seja o destino de uma pormenorização entre relatórios, tem de ativar a funcionalidade para esse relatório na janela **Opções**. Aceda a **Ficheiro** > **Opções e definições** > **Opções** e, em seguida, vá para **Definições de relatório** junto à parte inferior da página à esquerda.

Marque a caixa de seleção **Permitir que elementos visuais neste relatório utilizem destinos de pormenorização de outros relatórios**, conforme mostrado na imagem a seguir.

![Captura de ecrã da janela Opções, com as Definições de relatório realçadas](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

A pormenorização entre relatórios está agora ativada.

## <a name="set-up-cross-report-drillthrough"></a>Configurar a pormenorização entre relatórios

A configuração da pormenorização entre relatórios é semelhante à configuração de pormenorização dentro de um relatório. A pormenorização é ativada na página de destino, ao permitir que os outros elementos visuais sejam direcionados para a página ativada para pormenorização. Para obter os passos para criar a pormenorização para um único relatório, veja [Utilizar a pormenorização no Power BI Desktop](desktop-drillthrough.md).

Para iniciar o processo de configuração, precisa de executar alguns passos iniciais:

* Configure uma página de destino da pormenorização, que pode ser acedida a partir de outros relatórios na área de trabalho ou aplicação.
* Permita que um relatório veja as páginas de pormenorização fora do próprio relatório.

Localize as opções de pormenorização na secção **Campos** do painel **Visualizações**, conforme mostrado na imagem a seguir.

![Captura de ecrã do painel Visualizações, com as opções Pormenorização realçadas](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

O primeiro passo na ativação da pormenorização de uma página consiste em validar os modelos de dados para os relatórios de origem e de destino. Confirme que: 

* Os campos que quer transmitir existem em ambos os modelos de dados.
* Os nomes dos campos e os nomes das tabelas a que pertencem são idênticos (as cadeias de caracteres também devem corresponder, pois diferenciam maiúsculas de minúsculas).

Por exemplo, se quiser transmitir um filtro no campo *País* na tabela *Geografia*, ambos os modelos deverão ter uma tabela *Geografia* e um campo *País* dentro desta tabela. Caso contrário, terá de atualizar o nome do campo ou o nome da tabela no modelo subjacente. A simples atualização do nome apresentado dos campos não funcionará corretamente para a pormenorização entre relatórios. (Repare que os esquemas de cada relatório não precisam de ser exatamente iguais.)

Para começar a configuração, precisará de preparar a página de destino. No Power BI Desktop, aceda à página e verifique se a alternância de pormenorização de **Relatório cruzado** está definida como **Ativada**. 

![Captura de ecrã da alternância de relatório cruzado definida como ativada](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Em seguida, arraste os campos que quer utilizar como o destino da pormenorização para a tela. Selecione se quer que o campo seja utilizado como uma categoria ou resumido como uma medida. Neste ponto, pode selecionar se quer desativar a alternância **Manter todos os filtros** para o elemento visual. Se não quiser transmitir outros filtros aplicados do elemento visual de origem para o elemento visual de destino na pormenorização, selecione **Desativado**.

> [!NOTE]
> Se estiver a utilizar apenas para pormenorização entre relatórios, deverá eliminar o botão **Voltar** que é adicionado automaticamente. O botão **Voltar** funciona apenas para a navegação dentro de um único relatório. 

Após o elemento visual ter sido configurado, confirme que guarda o relatório se estiver no serviço Power BI ou guarda e publica o relatório se estiver a utilizar o Power BI Desktop.

A secção anterior descreveu como ativar a pormenorização de relatórios cruzados para o Power BI Desktop (na janela **Opções**). Se estiver a utilizar o serviço Power BI para criar um destino de pormenorização dos relatórios cruzados, para ativar a pormenorização de relatórios cruzados, terá de: 

1. Selecionar a área de trabalho onde reside o relatório de destino e o relatório de origem.
2. Selecione **Relatórios**.
3. Selecione o ícone **Definições** do relatório de origem.
4. Verifique se a alternância de pormenorização de relatórios cruzados está **Ativada**.
5. Guarde o relatório.

Já está! O relatório está pronto para a experiência de pormenorização de relatórios cruzados. 

Na próxima secção, vamos ver a experiência a partir da perspectiva do utilizador.

## <a name="cross-report-drillthrough-experience"></a>Experiência de pormenorização de relatórios cruzados

Ao configurar a experiência de pormenorização de relatórios cruzados para um relatório, pode pôr a funcionalidade em utilização.

Selecione o relatório de origem no serviço Power BI e, em seguida, selecione um elemento visual que utiliza o campo ou os campos da forma especificada quando configurou a página de destino. Em seguida, clique com o botão direito do rato num ponto de dados para abrir o menu de contexto do elemento visual e selecione **Pormenorização**.

![Captura de ecrã do relatório de origem no serviço Power BI, com a Pormenorização realçada](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Em seguida, verá os resultados na página de pormenorização de relatórios cruzados de destino, assim como os que configurou quando criou o destino. Os resultados são filtrados de acordo com as definições de pormenorização.

> [!IMPORTANT]
> O Power BI coloca em cache os destinos da pormenorização dos relatórios cruzados. Se fizer alterações, confirme que atualiza o browser caso não veja os destinos de pormenorização conforme o esperado. 

Os destinos dos relatórios cruzados são formatados do seguinte modo: 

`Target Page Name [Target Report Name]`

Depois de selecionar a página de destino para a qual quer pormenorizar, o Power BI vai para essa página. Transmite junto com o contexto de filtro com base nas definições da página de destino. 

O contexto de filtro do elemento visual de origem pode incluir o seguinte: 

* Filtros de nível de relatório, página e elemento visual que afetam o elemento visual de origem. 
* Filtro cruzado e realce cruzado que afetam o elemento visual de origem. 
* Segmentações de dados na página e segmentações de dados síncronas.
* Parâmetros de URL.

Quando chega ao relatório de destino para a pormenorização, o Power BI aplica apenas filtros para os campos para os quais encontra as correspondências exatas das cadeias de caracteres do nome de campo e do nome de tabela. O Power BI não aplica filtros fixos do relatório de destino. No entanto, aplica o marcador pessoal padrão, caso exista. Por exemplo, se o marcador pessoal predefinido incluir um filtro ao nível do relatório para *País = EUA*, o Power BI aplicará primeiro este filtro antes de aplicar o contexto do filtro do elemento visual de origem. 

Para a pormenorização de relatórios cruzados, o Power BI transmite o contexto do filtro a todas as páginas predefinidas no relatório de destino. O Power BI não transmite o contexto do filtro das páginas de descrição, pois as páginas de descrição são filtradas com base no elemento visual de origem que invoca a descrição.

Se quiser regressar ao relatório de origem após a ação de pormenorização dos relatórios cruzados, utilize o botão **Voltar** do browser. 

## <a name="next-steps"></a>Próximos passos

Poderá também estar interessado nos seguintes artigos:

* [Utilizar a segmentação de dados no Power BI Desktop](visuals/power-bi-visualization-slicers.md)
* [Utilizar a pormenorização no Power BI Desktop](desktop-drillthrough.md)

