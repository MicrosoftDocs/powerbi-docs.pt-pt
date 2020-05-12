---
title: Introdução às ferramentas das Perguntas e Respostas para preparar as Perguntas e Respostas do Power BI (pré-visualização)
description: Introdução às ferramentas das Perguntas e Respostas do Power BI
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/17/2020
ms.author: maggies
ms.openlocfilehash: 6178c9f157578110a09abf3fcbebccba54339f13
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866080"
---
# <a name="intro-to-qa-tooling-to-train-power-bi-qa-preview"></a>Introdução às ferramentas das Perguntas e Respostas para preparar as Perguntas e Respostas do Power BI (pré-visualização)

Com as *ferramentas* das Perguntas e Respostas do Power BI, pode melhorar a experiência de linguagem natural dos seus utilizadores. Como designer ou administrador, interage com o motor de linguagem natural e faz melhorias em três áreas: 

- Rever perguntas que os utilizadores colocaram.
- Ensinar as Perguntas e Respostas a entender as perguntas.
- Gerir os termos que ensinou às Perguntas e Respostas.

Além destas capacidades dedicadas de ferramentas, o separador **Modelação** no Power BI Desktop oferece mais opções:  

- Sinónimos
- Etiquetas de linha
- Ocultar das Perguntas e Respostas
- Configuração do esquema linguístico (avançado)

## <a name="get-started-with-qa-tooling"></a>Introdução às ferramentas das Perguntas e Respostas

As ferramentas das Perguntas e Respostas só estão disponíveis no Power BI Desktop e, atualmente, apenas suportam o modo de importação.

1. Abra o Power BI Desktop e utilize as Perguntas e Respostas para criar um elemento visual. 
2. No canto do elemento visual, selecione o ícone de engrenagem. 

    ![Engrenagem do elemento visual das Perguntas e Respostas](media/q-and-a-tooling-intro/qna-visual-gear.png)

    É aberta a página de Introdução.  

    ![Introdução às Perguntas e Respostas](media/q-and-a-tooling-intro/qna-tooling-dialog.png)

### <a name="review-questions"></a>Rever as perguntas

Selecione **Rever perguntas** para ver uma lista de conjuntos de dados que estão a ser utilizados no serviço Power BI para o seu inquilino. A página **Rever perguntas** mostra também o proprietário do conjunto de dados, a área de trabalho e a data da última atualização. A partir daí, pode selecionar um conjunto de dados e ver que perguntas os utilizadores têm feito. Os dados também mostram palavras que não foram reconhecidas. Todos os dados mostrados aqui dizem respeito aos últimos 28 dias.

![Rever as perguntas das Perguntas e Respostas](media/q-and-a-tooling-intro/qna-tooling-review-questions.png)

### <a name="teach-qa"></a>Ensinar Perguntas e Respostas

A secção **Ensinar Perguntas e Respostas** permite-lhe preparar as Perguntas e Respostas para reconhecer palavras. Para começar, escreva uma pergunta que contenha uma ou mais palavras que as Perguntas e Respostas não reconhecem. As Perguntas e Respostas pedem-lhe a definição desse termo. Introduza um filtro ou um nome de campo que corresponda ao significado dessa palavra. Depois, as Perguntas e Respostas reinterpretam a pergunta original. Se estiver satisfeito com os resultados, pode guardar o texto introduzido. Para saber mais, veja [Ensinar Perguntas e Respostas](q-and-a-tooling-teach-q-and-a.md)

![Pré-visualização de sinónimos de Ensinar Perguntas e Respostas](media/q-and-a-tooling-intro/qna-tooling-teach-fixpreview.png)

### <a name="manage-terms"></a>Gerir termos

Tudo o que tiver guardado da secção Ensinar Perguntas e Respostas aparece aqui, pelo que pode rever ou eliminar os termos que definiu. Atualmente, não pode editar uma definição existente, por isso, para redefinir um termo, tem de o eliminar e voltar a criar.

![Gerir termos das Perguntas e Respostas](media/q-and-a-tooling-intro/qna-manage-terms.png)

### <a name="suggest-questions"></a>Sugerir perguntas

O elemento visual de Perguntas e Respostas sugere várias perguntas para começar, sem ser necessária configuração. Estas perguntas são geradas automaticamente com base no seu modelo de dados. Em **Sugerir perguntas**, pode substituir as perguntas geradas automaticamente pelas suas perguntas. 

Para começar, escreva a pergunta que pretende adicionar na caixa de texto. Na secção de pré-visualização, verá o resultado no elemento visual de Perguntas e Respostas. 

:::image type="content" source="media/q-and-a-tooling-intro/power-bi-qna-suggest-questions.png" alt-text="Sugerir perguntas para as Perguntas e Respostas":::
 
Selecione o botão **Adicionar** para adicionar esta pergunta a **As suas perguntas sugeridas**. Todas as perguntas adicionais serão adicionadas ao final desta lista. As perguntas serão apresentadas no elemento visual de Perguntas e Respostas pela mesma ordem que nesta lista. 

:::image type="content" source="media/q-and-a-tooling-intro/power-bi-qna-save-suggest-questions.png" alt-text="Guardar perguntas sugeridas":::
 
Certifique-se de que seleciona **Guardar** para mostrar a sua lista de perguntas sugeridas no elemento visual de Perguntas e Respostas. 


## <a name="other-qa-settings"></a>Outras definições das Perguntas e Respostas

### <a name="bulk-synonyms"></a>Sinónimos em massa

O separador **Modelação** do Power BI Desktop tem mais opções para melhorar a experiência das Perguntas e Respostas. 

1. No Power BI Desktop, selecione a Vista de modelação.

2. Selecione um campo ou uma tabela para mostrar o painel **Propriedades**.  Este painel é apresentado do lado direito da tela e lista diversas ações das Perguntas e Respostas. Uma das opções é **Sinónimos**. Na caixa **Sinónimos**, pode rapidamente definir alternativas da tabela ou do campo que selecionar. Pode também definir sinónimos na secção **Ensinar Perguntas e Respostas** da caixa de diálogo de Ferramentas, mas costuma ser mais rápido definir aqui sinónimos para muitos campos numa tabela.

    ![Sinónimos no painel Modelação das Perguntas e Respostas](media/q-and-a-tooling-intro/qna-modelling-pane-synonyms.png)

3. Para definir múltiplos sinónimos para um só campo, utilize vírgulas para indicar o sinónimo seguinte.

### <a name="hide-from-qa"></a>Ocultar das Perguntas e Respostas

Pode também ocultar campos e tabelas, para que não apareçam nos resultados das Perguntas e Respostas. 

1. No Power BI Desktop, selecione a Vista de modelação.

2. Selecione um campo ou uma tabela para mostrar o painel **Propriedades** e coloque **Está oculto** **Ativado**.

    As Perguntas e Respostas respeitam essa definição e garantem que esse campo não é reconhecido pelas Perguntas e Respostas. Por exemplo, talvez queira ocultar campos de ID e chaves de referência para evitar campos duplicados desnecessários que tenham o mesmo nome. Mesmo que oculte o campo, pode ainda utilizar o mesmo no Power BI Desktop em elementos visuais fora das Perguntas e Respostas.

### <a name="set-a-row-label"></a>Definir uma etiqueta de linha

Uma etiqueta de linha permite-lhe definir qual a coluna (ou o *campo*) que melhor identifica uma linha única numa tabela. Por exemplo, numa tabela chamada "Cliente", a etiqueta de linha costuma ser "Nome a Apresentar". Fornecer estes metadados adicionais permite às Perguntas e Respostas desenhar um elemento visual mais útil, quando os utilizadores escrevem "Mostrar-me as vendas por cliente". Em vez de tratar "cliente" como uma tabela, pode utilizar "Nome a Apresentar" e apresentar um gráfico de barras que mostra as vendas para cada cliente. Só pode definir a Vista de modelação da etiqueta de linha. 

1. No Power BI Desktop, selecione a Vista de modelação.

2. Selecione uma tabela para mostrar o painel **Propriedades**.

3. Na caixa **Etiqueta de linha**, selecione um campo.

## <a name="configure-the-linguistic-schema-advanced"></a>Configurar o esquema linguístico (avançado)

No Power BI, pode preparar totalmente e melhorar o motor de linguagem natural dentro das Perguntas e Respostas, incluindo mudar a pontuação e a ponderação dos resultados em linguagem natural subjacentes. Para saber como, veja [Editar o esquema linguístico e adicionar expressões nas Perguntas e Respostas](q-and-a-tooling-advanced.md).

## <a name="next-steps"></a>Próximos passos

Existem diversas melhores práticas para melhorar o motor de linguagem natural. Para obter mais informações, veja [Melhores práticas das Perguntas e Respostas](q-and-a-best-practices.md).
