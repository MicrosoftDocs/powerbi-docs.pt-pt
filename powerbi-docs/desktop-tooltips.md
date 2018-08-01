---
title: Utilizar páginas de descrições de relatórios no Power BI
description: As páginas de descrição no Power BI Desktop permitem-lhe criar descrições que surgem ao pairar o cursor para os elementos visuais nos seus relatórios
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 07/24/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: b2437074fb6beff4b1be62287d547111488862e3
ms.sourcegitcommit: 6faeb642721ee5abb41c04a8b729880c01c4d40e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2018
ms.locfileid: "39210336"
---
# <a name="create-tooltips-based-on-report-pages-in-power-bi-desktop-preview"></a>Criar descrições com base em páginas de relatórios no Power BI Desktop (pré-visualização)
Pode criar **descrições de relatórios** visualmente avançadas que surgem ao pairar o cursor sobre elementos visuais, com base nas páginas de relatórios que criar no **Power BI Desktop**. Ao criar uma página de relatório que serve como descrição, as suas descrições personalizadas podem incluir elementos visuais, imagens e qualquer outra coleção de itens que criar na página do relatório. 

![Descrições de relatórios para o Power BI Desktop](media/desktop-tooltips/desktop-tooltips_00a.png)

Pode criar as páginas de descrição que pretender. Cada página de descrição pode ser associada a um ou mais campos do relatório de forma a que, quando pairar o cursor sobre um elemento visual que inclua o campo selecionado, a descrição criada na página de descrição seja apresentada, filtrada com base no ponto de dados sobre o qual está a pairar o cursor do rato. 

Existem inúmeras coisas interessantes que pode fazer com as descrições de relatórios. Veja como pode criar descrições e o que tem de fazer para as configurar.

### <a name="enable-the-tooltips-preview"></a>Ativar a pré-visualização de descrições 
Uma vez que as descrições de relatórios se encontram atualmente no modo de pré-visualização, terá de ativar as descrições de relatórios antes de as poder criar. Para ativar a funcionalidade de pré-visualização das descrições de relatórios, selecione **Ficheiro > Opções e Definições > Opções > Funcionalidades de Pré-visualização** no Power BI Desktop e, em seguida, selecione a caixa de verificação junto a **Descrições da página de relatório**. 

![Ativar a funcionalidade de pré-visualização de descrições de relatórios](media/desktop-tooltips/desktop-tooltips_01.png)

Terá de reiniciar o **Power BI Desktop** após efetuar a seleção para ativar a versão de pré-visualização das descrições de relatórios.

## <a name="create-a-report-tooltip-page"></a>Criar uma página de descrições de relatórios
Para começar, crie uma nova página de relatório ao clicar no botão **+**, que se encontra na parte inferior da tela do **Power BI Desktop**, na área de separadores de página. O botão encontra-se junto à última página no relatório. 

![Criar uma nova página de relatório para a descrição](media/desktop-tooltips/desktop-tooltips_02.png)

Pode criar uma descrição com o tamanho que quiser. No entanto, tenha em atenção que as descrições pairam sobre a tela do relatório, pelo que as deve manter razoavelmente pequenas. No painel **Formato** no cartão **Tamanho da Página**, poderá ver um novo modelo de tamanho de página denominado *Descrição*. Este modelo fornece um tamanho de tela da página de relatório pronto a utilizar para a sua descrição.

![Selecionar Descrição em Tamanho da Página para obter uma descrição pronta a utilizar](media/desktop-tooltips/desktop-tooltips_03.png)

Por predefinição, o **Power BI Desktop** ajusta a tela do seu relatório ao espaço disponível na página. Muitas vezes essa é uma boa opção, mas não no caso das descrições. Para compreender melhor e ver o aspeto da sua descrição quando tiver terminado, pode alterar a **Vista de Página** para o tamanho real. 

Para tal, selecione o separador **Ver** no friso. A partir daí, selecione **Vista de Página > Tamanho Real**, conforme apresentado na imagem seguinte.

![Mostrar a página do relatório em tamanho real para facilitar a criação de descrições](media/desktop-tooltips/desktop-tooltips_04.png)

Também pode atribuir um nome à página do relatório para tornar o seu propósito mais claro. Selecione o cartão **Informações da Página** no painel **Formato** e, em seguida, escreva o nome no campo **Nome** que lhe for apresentado. Na imagem seguinte, o nome do relatório da descrição é *Descrição 1*, mas pode mudá-lo para um nome mais sugestivo.

![Atribuir um nome à página de relatório da descrição](media/desktop-tooltips/desktop-tooltips_05.png)

A partir daí, pode criar os elementos visuais que pretende que sejam apresentados na sua descrição. Na imagem seguinte, existem dois cartões e um gráfico de barras agrupadas na página de descrição, juntamente com uma cor de fundo da própria página e fundos para cada um dos elementos visuais, de modo a dar o aspeto que pretende.

![Descrições de relatórios para o Power BI Desktop](media/desktop-tooltips/desktop-tooltips_06.png)

Existem mais passos que tem de concluir antes de a descrição da página de relatório estar pronta a funcionar como uma descrição. Tem de configurar a página de descrição de diversas formas, conforme descrito na secção seguinte. 

## <a name="configure-your-tooltip-report-page"></a>Configurar a página de relatório da descrição

Assim que tiver criado a página de relatório da descrição, terá de configurar a página de modo a que o **Power BI Desktop** possa registá-la como uma descrição e de garantir que esta é apresentada nos elementos visuais corretos.

Para começar, tem de definir o controlo de deslize **Descrição** para a posição **Ativado**, no cartão **Informações da Página**, para tornar a página numa descrição. 

![Definir o controlo de deslize Descrição para a posição Ativado para indicar que a página é uma descrição](media/desktop-tooltips/desktop-tooltips_07.png)

Assim que definir o controlo de deslize para Ativado, especifique os campos onde pretende que a descrição do relatório seja apresentada. A descrição será apresentada para os elementos visuais no relatório que incluírem o campo especificado. Pode especificar os campos aplicáveis ao arrastá-los para o registo **Campos de descrição**, que se encontra na secção **Campos** do painel **Visualizações**. Na imagem seguinte, o campo *MontanteDeVendas* foi arrastado para o registo **Campos de descrição**.

![Adicione campos para determinar o local onde a descrição será apresentada](media/desktop-tooltips/desktop-tooltips_08.png)
 
Pode adicionar campos numéricos e de categorias no registo **Campos de descrição**, incluindo medidas.

Assim que terminar, a página de relatório da descrição que criar será utilizada como uma descrição em elementos visuais no relatório que utilizar qualquer um dos campos que colocou no registo **Campos de descrição**, ao substituir a descrição predefinida do Power BI.

## <a name="manually-setting-a-report-tooltip"></a>Definir manualmente uma descrição de relatório

Para além de criar uma descrição que é apresentada automaticamente ao pairar o cursor sobre um elemento visual que contém o campo especificado, pode definir uma descrição manualmente. 

Qualquer elemento visual que suportar descrições de relatório passará a incluir um cartão **Descrição** no respetivo painel **Formatação**. 

Para definir manualmente uma descrição, selecione o elemento visual para o qual pretende especificar a descrição manual e, em seguida, no painel **Visualizações**, selecione a secção **Formato** e expanda o cartão **Descrição**.

![Cartão Descrição de um elemento visual individual](media/desktop-tooltips/desktop-tooltips_09.png)

Em seguida, no menu pendente **Página**, selecione a página de descrição que pretende utilizar para o elemento visual selecionado. Tenha em atenção que apenas as páginas de relatório especificadas como páginas de **Descrição** são apresentadas na caixa de diálogo.

![Selecionar uma página de descrição para a descrição manual](media/desktop-tooltips/desktop-tooltips_10.png)

Pode utilizar a definição manual de descrições de várias formas. Pode definir uma página em branco para uma descrição e, deste modo, substituir a descrição do Power BI predefinida. A definição manual também se aplica quando não pretende utilizar a descrição selecionada automaticamente pelo Power BI. Por exemplo, se tiver um elemento visual que inclui dois campos e existir uma descrição associada a ambos, o Power BI só seleciona uma para apresentação. Se quiser que isso não aconteça, poderá selecionar manualmente a descrição que deve ser apresentada.

## <a name="reverting-to-default-tooltips"></a>Reverter para as descrições predefinidas

Se criar uma descrição manual para um elemento visual, mas decidir que pretende a descrição predefinida fornecida pelo Power BI, poderá sempre regressar a essa descrição predefinida. Para tal, quando um elemento visual estiver selecionado e o cartão **Descrição** estiver expandido, selecione *Automático* no menu pendente **Página** para regressar à predefinição.

![Regressar à descrição predefinida de um elemento visual](media/desktop-tooltips/desktop-tooltips_11.png)

## <a name="custom-report-tooltips-and-line-charts"></a>Descrições de relatórios e gráficos de linhas personalizados

Existem algumas considerações a ter em conta quando as suas descrições de relatórios interagem com elementos visuais de gráficos de linhas e com elementos visuais realçados de forma cruzada.

### <a name="report-tooltips-and-line-charts"></a>Descrições de relatórios e gráficos de linhas

Quando uma descrição de relatório é apresentada para um gráfico de linhas, só é apresentada uma única descrição para todas as linhas no gráfico. Este comportamento é semelhante ao da descrição predefinida para gráficos de linhas, que também apresenta apenas uma única descrição. 

Isto acontece porque o campo na legenda não passa por um filtro na descrição. Na imagem seguinte, a descrição apresentada mostra todas as unidades vendidas nesse dia nas três categorias expostas na descrição do relatório (neste exemplo, Deluxe, Económica e Normal). 

![Os gráficos de linhas apenas mostram dados de descrição agregados](media/desktop-tooltips/desktop-tooltips_12.png)

### <a name="report-tooltips-and-cross-highlighting"></a>Descrições de relatórios e realce de forma cruzada

Quando um elemento visual é realçado de forma cruzada num relatório, as descrições de relatórios mostram sempre os dados realçados de forma cruzada, mesmo que paire o cursor sobre a secção desvanecida do ponto de dados. Na imagem seguinte, o cursor do rato está a pairar sobre a secção desvanecida do gráfico de barras (a secção que não está realçada), mas a descrição do relatório continua a mostrar os dados da parte realçada nesse ponto de dados (os dados realçados).

![As descrições de relatórios mostram os dados realçados ao realçar elementos de forma cruzada](media/desktop-tooltips/desktop-tooltips_13.png)



## <a name="limitations-and-considerations"></a>Limitações e considerações
Nesta versão de pré-visualização das **descrições** de relatórios, existem algumas limitações e considerações a ter em conta.

* A partir da versão de julho de 2018 do **Power BI Desktop**, os elementos visuais Tabela e Matriz têm suporte para descrições. 
* As descrições de relatórios não são suportadas ao visualizar relatórios em aplicações para dispositivos móveis ou ambientes incorporados, incluindo a funcionalidade Publicar na Web. 
* As descrições de relatórios não são suportadas para elementos visuais personalizados. 
* Atualmente, os clusters não são suportados como campos que podem ser apresentados em descrições de relatórios. 
* Ao selecionar um campo a apresentar em descrições de relatórios, se utilizar um campo em vez de uma categoria, os elementos visuais que contêm esse campo só mostrarão a descrição especificada quando o resumo do campo selecionado corresponder. 


## <a name="next-steps"></a>Próximos passos
Para obter mais informações sobre funcionalidades semelhantes ou como interagir com descrições de relatórios, veja os artigos seguintes:

* [Utilizar a pormenorização no Power BI Desktop](desktop-drillthrough.md)
* [Apresentar um mosaico do dashboard ou um elemento visual do relatório no modo de detalhe](service-focus-mode.md)

