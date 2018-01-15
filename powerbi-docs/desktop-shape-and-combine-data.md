---
title: Formatar e combinar dados no Power BI Desktop
description: Formatar e combinar dados no Power BI Desktop
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: bb4f910f0ac6240ed2dab987a7076b3f996b86fe
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2017
---
# <a name="shape-and-combine-data-in-power-bi-desktop"></a>Formatar e combinar dados no Power BI Desktop
Com o **Power BI Desktop**, pode ligar a muitos tipos diferentes de origens de dados e, em seguida, formatar os dados de acordo com as suas necessidades. *Formatar* dados significa transforma os dados – como mudar o nome de colunas ou tabelas, converter o texto em números, remover linhas, definir a primeira linha como cabeçalhos, etc. *Combinar* dados significa ligar a duas ou mais origens de dados, formatá-las conforme necessário e consolidá-las numa consulta útil.

Este documento demonstra como formatar uma consulta com o Power BI Desktop, realçando algumas das tarefas mais comuns. A consulta utilizada aqui é descrita de forma mais pormenorizada, incluindo como criar a consulta do zero, em [Introdução ao Power BI Desktop](desktop-getting-started.md).

É útil saber que o **Editor de Consultas** no Power BI Desktop utiliza amplamente menus de contexto, bem como o friso. A maioria das opções que pode selecionar no friso **Transformar** também estão disponíveis ao clicar com o botão direito do rato num item (tal como uma coluna) e ao escolher no menu apresentado.

## <a name="shape-data"></a>Formatar dados
Ao formatar dados no Editor de Consultas, está a fornecer instruções passo-a-passo (que o Editor de Consultas executa) para ajustar os dados à medida que são carregados e apresentados pelo Editor de Consultas. A origem de dados original não é afetada; apenas é ajustada ou *formatada*esta vista específica dos dados.

Os passos que especificar (como mudar o nome de uma tabela, transformar um tipo de dados ou eliminar colunas) são registados pelo Editor de Consultas. Sempre que esta consulta ligar à origem de dados, esses passos serão executados, para que os dados sejam sempre formatados da forma que especificar. Este processo ocorre sempre que utiliza a funcionalidade Editor de Consultas no Power BI Desktop, ou para qualquer pessoa que utilize a sua consulta partilhada, como no serviço **Power BI**. Esses passos são capturados, sequencialmente, no painel **Definições da Consulta**, em **Passos Aplicados**.

A imagem seguinte mostra o painel **Configurações da Consulta** para uma consulta que foi formatada – abordaremos cada um desses passos nos próximos parágrafos.

![](media/desktop-shape-and-combine-data/shapecombine_querysettingsfinished.png)

Com os dados de reforma de [Introdução ao Power BI Desktop](https://powerbi.uservoice.com/knowledgebase/articles/471664), que encontramos ao ligar a uma origem de dados da Web, vamos formatar esses dados de acordo com as nossas necessidades.

Para começar, as pontuações de uma coluna não foram transformadas automaticamente de texto em números quando o Editor de Consultas carregou a tabela, mas precisamos dessas pontuações como números. Sem problemas – basta clicar com o botão direito do rato no cabeçalho da coluna e selecionar**Alterar Tipo \> Número Inteiro** para alterá-los. Para escolher mais de uma coluna, selecione primeiro uma coluna e, em seguida, mantenha premida a tecla **SHIFT**, selecione colunas adjacentes adicionais e clique com o botão direito do rato num cabeçalho de coluna para alterar todas as colunas selecionadas. Também pode utilizar a tecla **CTRL** para escolher colunas não adjacentes.

![](media/desktop-shape-and-combine-data/shapecombine_changetype.png)

Também pode *transformar* essas colunas de texto em cabeçalho a partir do friso **Transformar**. Este é o friso **Transformar**, com uma seta a apontar para o botão **Tipo de Dados**, que permite transformar o tipo de dados atual noutro tipo de dados.

![](media/desktop-shape-and-combine-data/queryoverview_transformribbonarrow.png)

Note que, em **Definições da Consulta**, os **Passos Aplicados** refletem os passos de formatação aplicados aos dados. Se quiser remover qualquer passos do processo de formatação, basta selecionar o **X** à esquerda do passo. Na imagem seguinte, **Passos Aplicados** reflete os passos executados até agora: ligar ao site (**Origem**), selecionar a tabela (**Navegação**) e, ao carregar a tabela, o Editor de Consulta alterou automaticamente as colunas com números em formato de texto, de *Texto* para *Número Inteiro* (**Tipo Alterado**). Uma coluna de classificações não foi alterada automaticamente para um tipo de número, e descobriremos o motivo nos próximos parágrafos.

![](media/desktop-shape-and-combine-data/shapecombine_appliedstepsearly.png)

Antes de podermos trabalhar com esta consulta, temos de fazer algumas alterações para colocar os dados nela contidos onde queremos:

* *Remover a primeira coluna* – não precisamos dela, inclui apenas linhas redundantes que indicam “Verifique qual é a classificação do seu estado em relação à reforma”, o que é um artefacto por esta origem de dados ser uma tabela baseada na Web
* *Corrigir alguns Erros* – uma das colunas, **Qualidade dos cuidados de saúde**, contém alguns empates nas classificações dos estados, o que foi observado no site pela apresentação do texto *(empate)* a seguir aos respetivos números. Isso funciona bem no site, mas requer que transformemos manualmente a coluna de texto em dados. É fácil corrigir este problema com o Power BI Desktop, e fazê-lo demonstra uma funcionalidade interessante de **Passos Aplicados** na Consulta
* *Alterar o Nome da Tabela* – o nome **Tabela 0** não é um descritor útil, mas é fácil alterá-lo

Para remover a primeira coluna, basta selecionar a coluna e escolher o separador **Base** no friso e, em seguida, **Remover Colunas**, como mostra a figura seguinte.

![](media/desktop-shape-and-combine-data/shapecombine_removecolumnsretirement.png)

Em seguida, precisamos de processar a coluna de texto e transformá-la em números. No início, parece simples podermos alterar apenas o tipo da coluna **Qualidade dos cuidados de saúde** de texto para número (como *Número Inteiro* ou *Número Decimal*). Mas quando alteramos o tipo de **Texto** para **Número Inteiro** e analisamos os valores nessa coluna, descobrimos que o Editor de Consultas reporta alguns erros.

![](media/desktop-shape-and-combine-data/shapecombine_error.png)

Existem algumas formas de obter mais informações sobre cada erro. Pode selecionar a célula (sem clicar na palavra **Erro**) ou clicar diretamente na palavra **Erro**. Se selecionar a célula *sem* clicar diretamente na palavra **Erro**, o Editor de Consultas apresenta as informações de erro na parte inferior da janela.

![](media/desktop-shape-and-combine-data/shapecombine_errorinfo.png)

Se clicar na palavra *Erro* diretamente, a Consulta cria um **Passo Aplicado** no painel **Definições da Consulta** e apresenta informações sobre o erro.

![](media/desktop-shape-and-combine-data/shapecombine_errorselect.png)

Para voltar ao Editor de Consultas, tem de remover esse passo, selecionando o **X** ao lado dele.

Quando selecionamos o **Passo Aplicado** mais recente, podemos ver o erro que acabamos de descrever, como mostra a imagem seguinte.

![](media/desktop-shape-and-combine-data/shapecombine_querystep1.png)

Como o Editor de Consultas regista os passos sequencialmente, podemos selecionar o passo antes de alterar o tipo, em **Passos Aplicados**, e ver qual é o valor da célula antes da transformação, como mostra a imagem seguinte.

![](media/desktop-shape-and-combine-data/shapecombine_querystep2.png)

Muito bem, agora podemos corrigir esses valores e, *em seguida*, alterar o tipo. Como o Editor de Consultas regista os passos sequencialmente, embora independentemente uns dos outros, pode mover cada **Passo Aplicado** para cima ou para baixo na sequência. Basta clicar com o botão direito do rato em qualquer passo para que o Editor de Consultas mostre um menu que permite executar as seguintes operações: **Mudar o nome**, **Eliminar**, **Eliminar** **Até ao Fim** (remover o passo atual, bem como todos os passos subsequentes), **Mover para Cima** ou **Mover para Baixo**.

![](media/desktop-shape-and-combine-data/shapecombine_querystepreorder.png)

Além disso, pode selecionar um **Passo Aplicado** em qualquer lugar na lista e continuar a formatar os dados nesse ponto na sequência. O Editor de Consultas inserirá automaticamente um novo passos diretamente a seguir ao **Passo Aplicado** selecionado. Vamos experimentar.

Primeiro, selecionamos o **Passo Aplicado** antes de alterar o tipo da coluna **Qualidade dos cuidados de saúde**. Em seguida, substituímos os valores pelo texto "(empate)" na célula para que apenas o número permaneça. Clique com o botão direito do rato na célula que contém “35 (empate)” e selecione *Substituir Valores...* no menu apresentado. Observe qual é o **Passo Aplicado** que está selecionado (o passo anterior à alteração do tipo).

![](media/desktop-shape-and-combine-data/shapecombine_replacevalues.png)

Uma vez que estamos a inserir um passo, o Editor de Consultas avisa-nos sobre o perigo de fazer isso: os passos subsequentes poderiam causar uma fragmentação da consulta. Temos de ser cuidadosos e ponderados! Como isto é um tutorial e estamos a destacar uma funcionalidade realmente interessante do Editor de Consultas para demonstrar como pode criar, eliminar, inserir e reorganizar os passos, vamos avançar e selecionar **Inserir**.

![](media/desktop-shape-and-combine-data/shapecombine_insertstep.png)

Há três empates, portanto, substituímos os valores de cada um deles. Quando cria um novo Passo Aplicado, o Editor de Consultas atribui um nome ao mesmo com base na ação - neste caso, o **Valor Substituído**. Quando tem mais de um passo com o mesmo nome na sua consulta, o Editor de Consultas adiciona um número (em sequência) a cada **Passo Aplicado** subsequente, para diferenciá-los.

O ecrã seguinte mostra os três passos de **Valor Substituído** nas **Definições da Consulta**, mas também mostra algo ainda mais interessante: como removermos cada instância do texto "(empate)" da coluna **Qualidade dos cuidados de saúde**, o passo **Tipo Alterado** é agora concluído *sem erros*.

![](media/desktop-shape-and-combine-data/shapecombine_replacedvaluesok.png)

> [!NOTE]
> Também pode **Remover Erros** (com o friso ou com o menu de contexto), que remove todas as linhas que contêm erros. Neste caso, teria removido todos os estados que tinham "*(empate)*" dos nossos dados e não queríamos que o fizesse – gostamos de todos os estados e queremos mantê-los na tabela.

Foi um pouco complexo, é certo, mas mesmo assim foi um bom exemplo de quão poderoso e versátil o Editor de Consultas pode ser.

Por fim, pretendemos alterar o nome dessa tabela para algo descritivo. Ao criar relatórios, é especialmente útil ter nomes de tabela descritivos, principalmente quando ligamos a várias origens de dados, e todos eles estão listados no painel **Campos** da vista **Relatório**.

É fácil alterar o nome da tabela: no painel **Definições da Consulta**, em **Propriedades**, basta escrever o novo nome da tabela, como mostra a imagem seguinte, e premir **Enter**. Vamos chamar esta tabela *RetirementStats*.

![](media/desktop-shape-and-combine-data/shapecombine_renametable.png)

Muito bem, a formatação desses dados foi realizada na medida necessária. Em seguida, vamos ligar a outra origem de dados e combinar dados.

## <a name="combine-data"></a>Combinar dados
Esses dados sobre vários estados são interessantes e serão úteis para a criação de esforços de análise e consultas adicionais. Mas há um problema: a maioria dos dados utilizam uma abreviatura de duas letras para códigos de estado, em vez de utilizarem o nome completo do estado. Precisamos de alguma forma de associar os nomes de estado às respetivas abreviaturas.

Estamos com sorte: há outra origem de dados pública que faz exatamente isso, mas também precisa de formatação considerável antes de a podermos ligar à nossa tabela de reforma. Eis o recurso Web para abreviaturas de estado:

<http://en.wikipedia.org/wiki/List_of_U.S._state_abbreviations>

No friso **Base** no Editor de Consultas, selecionamos **Nova Origem \> Web** e escrevemos o endereço, selecionamos OK e o Navegador mostra o que encontrou nessa página da Web.

 ![](media/desktop-shape-and-combine-data/designer_gsg_usstateabbreviationsnavigator.png)

Selecionamos **Table[edit]** porque inclui os dados que queremos, mas será necessária bastante formatação para restringir os dados da tabela ao que pretendemos.

> [!TIP]
> Existe uma forma mais rápida ou mais fácil de executar os passos abaixo? Sim, podíamos criar uma *relação* entre as duas tabelas e formatar os dados com base nessa relação. Ainda é bom aprender os passos seguintes para trabalhar com tabelas, basta saber que as relações podem ajudá-lo a utilizar rapidamente os dados de várias tabelas.
> 
> 

Para formatar estes dados, vamos executar os seguintes passos:

* Remova as duas primeiras linhas – são o resultado do modo como a tabela da página Web foi criada e não precisamos delas. No friso **Base**, selecione **Reduzir Linhas \> Remover Linhas \> Remover Linhas Principais**.

![](media/desktop-shape-and-combine-data/shapecombine_removetoprows.png)

A janela **Remover Linhas Principais** é apresentada, permitindo-lhe especificar o número de linhas que pretende remover.

* Remova as últimas 26 linhas – são todas referentes a territórios, que não precisamos de incluir. No friso **Base**, selecione **Reduzir Linhas \> Remover Linhas \> Remover Linhas Inferiores**.

![](media/desktop-shape-and-combine-data/shapecombine_removebottomrows.png)

* Como a tabela RetirementStats não tem informações de Washington D.C., temos de filtrá-la da nossa lista. Selecione a seta para baixo ao lado da coluna Estado da Região e desmarque a caixa de verificação ao lado de **Distrito federal**.

![](media/desktop-shape-and-combine-data/shapecombine_filterdc.png)

* Remova algumas colunas desnecessárias – precisamos apenas do mapeamento do estado para a sua abreviação oficial de duas letras, para que possamos remover as seguintes colunas: **Column2**, **Column3** e, em seguida, **Column5** até **Column10**. Primeiro, selecione Column2, mantenha premida a tecla **CTRL** e selecione as outras colunas que pretende remover (desta forma, pode selecionar várias colunas não contíguas). No separador Base do friso, selecione **Remover Colunas \> Remover Colunas**.

![](media/desktop-shape-and-combine-data/shapecombine_removecolumns.png)

* Utilize a primeira linha como cabeçalhos – já que removemos as três primeiras linhas, a primeira linha atual é a que queremos para o cabeçalho. Pode selecionar **Utilizar Primeira Linha como Cabeçalhos** no separador **Base** ou no separador **Transformar** no friso.

![](media/desktop-shape-and-combine-data/shapecombine_usefirstrowasheaders.png)

>[!NOTE]
>Este é um bom momento para salientar que a *sequência* de passos aplicados no Editor de Consultas é importante e pode afetar a forma como os dados são formatados. Também é importante considerar como um passo pode afetar outro passo subsequente; se remover um passo dos Passos Aplicados, os passos subsequentes podem não se comportar como pretendido originalmente, devido ao impacto da sequência de passos da consulta.

>[!NOTE]
>Quando redimensiona a janela do Editor de Consultas para diminuir a largura, alguns itens do friso são condensados para aproveitar ao máximo o espaço visível. Ao aumentar a largura da janela do Editor de Consultas, os itens do friso são expandidos para tirar o máximo partido da área aumentada do friso.

* Mudar o nome das colunas e da própria tabela – como sempre, existem algumas formas de mudar o nome de uma coluna; em primeiro lugar, selecione a coluna, selecione **Mudar o Nome** no separador **Transformar** no friso ou clique com o botão direito do rato e selecione **Mudar o nome…** no menu que aparece. A imagem seguinte tem setas que apontam para ambas as opções; só precisa de escolher uma.

![](media/desktop-shape-and-combine-data/shapecombine_rename.png)

Vamos mudar o nomes das mesmas para *Nome do Estado* e *Código do Estado*. Para mudar o nome da tabela, basta escrever o nome na caixa **Nome** do painel **Definições da Consulta**. Vamos chamar esta tabela *StateCodes*.

Agora que já formatámos a tabela StateCodes como pretendemos, vamos combinar estas duas tabelas, ou consultas, numa só; como as tabelas que temos agora são o resultado das consultas que aplicámos aos dados, geralmente são designadas por *consultas*.

Existem duas formas principais de combinar consultas – *unindo* e *acrescentando*.

Quando tem uma ou mais colunas que pretende adicionar a outra consulta, **une** as consultas. Quando tem linhas de dados adicionais que pretende adicionar a uma consulta existente, **acrescenta** a consulta.

Neste caso, pretendemos intercalar consultas. Para começar, no painel esquerdo do Editor de Consultas, selecione a consulta *à qual* pretendemos unir a outra consulta, que neste caso é *RetirementStats*. Em seguida, selecione **Combinar \> Intercalar Consultas** no separador **Base** do friso.

![](media/desktop-shape-and-combine-data/shapecombine_mergequeries.png)

Poderá ser-lhe solicitado que defina os níveis de privacidade, para garantir que os dados são combinados sem a inclusão ou transferência de dados que não quer que sejam transferidos.

![](media/desktop-shape-and-combine-data/shapecombine_mergequeriesb.png)

Em seguida, a janela **Unir** é apresentada, a pedir-nos que selecionemos a tabela que pretendemos unir à tabela selecionada e, em seguida, as colunas correspondentes a utilizar para a união. Selecione State na tabela *RetirementStats* (consulta) e selecione a consulta *StateCodes* (neste caso é fácil, já que só há mais uma consulta – quando ligar a várias origens de dados, existirão muitas consultas por onde escolher). Quando selecionamos as colunas correspondentes corretas – **State** em *RetirementStats* e **State Name** em *StateCodes* – a janela **Unir** é semelhante à seguinte e o botão **OK** está ativado.

![](media/desktop-shape-and-combine-data/shapecombine_merge.png)

Uma **NewColumn** é criada no fim da consulta, que consiste no conteúdo da tabela (consulta) que foi unida à consulta existente. Todas as colunas da consulta unida são condensadas na **NewColumn**, mas pode optar por **Expandir** a tabela e incluir as colunas que quiser.

![](media/desktop-shape-and-combine-data/shapecombine_mergenewcolumn.png)

Para Expandir a tabela unida e selecionar as colunas a incluir, selecione o ícone de expansão (![Expandir](media/desktop-shape-and-combine-data/icon.png)). A janela **Expandir** é apresentada.

![](media/desktop-shape-and-combine-data/shapecombine_mergeexpand.png)

Neste caso, como só queremos a coluna **State Code**, selecionamos apenas essa coluna e, em seguida, selecionamos **OK**. Desmarcamos a caixa de verificação Utilizar o nome de coluna original como prefixo porque não precisamos nem queremos essa opção; se deixarmos essa opção selecionada, a coluna unida chamar-se-á **NewColumn.State Code** (o nome da coluna original ou **NewColumn**, seguido de um ponto e do nome da coluna que está a ser introduzida na consulta).

>[!NOTE]
>Quer fazer experiências com a forma de introduzir essa tabela **NewColumn**? Pode experimentar um pouco e, se não gostar dos resultados, basta eliminar esse passo da lista **Passos Aplicados** no painel **Definições da Consulta**; a consulta volta ao estado anterior à aplicação desse passo **Expandir**. Pode refazer estas ações livremente, quantas vezes desejar, até que o processo de expansão tenha o aspeto pretendido.

Agora temos uma única consulta (tabela) que combinou duas origens de dados, cada uma das quais foi desenvolvida para corresponder às nossas necessidades. Esta consulta pode servir como base para muitas ligações de dados adicionais interessantes – como estatísticas de custo de alojamento, dados demográficos ou oportunidades de trabalho em qualquer estado.

Para aplicar as alterações e fechar o Editor de Consultas, selecione Fechar e Aplicar no separador do friso **Base**. O conjunto de dados transformado é apresentado no Power BI Desktop, pronto para ser utilizado para a criação de relatórios.

![](media/desktop-shape-and-combine-data/shapecombine_closeandapply.png)

## <a name="next-steps"></a>Passos seguintes
Há inúmeras coisas que pode fazer com o Power BI Desktop. Para obter mais informações sobre as respetivas capacidades, consulte as seguintes fontes:

* [Introdução ao Power BI Desktop](desktop-getting-started.md)
* [Descrição Geral das Consultas no Power BI Desktop](desktop-query-overview.md)
* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Ligar a Dados no Power BI Desktop](desktop-connect-to-data.md)
* [Tarefas Comuns de Consulta no Power BI Desktop](desktop-common-query-tasks.md)   

