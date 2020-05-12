---
title: Ensinar Perguntas e Respostas para compreender as perguntas e os termos nas Perguntas e Respostas do Power BI
description: Como utilizar as Perguntas e Respostas do Power BI para explorar os seus dados
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/21/2020
ms.author: maggies
LocalizationGroup: Ask questions of your datadefintion
ms.openlocfilehash: e5b870201943b93bfdaec2881005785c2f3c470b
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/06/2020
ms.locfileid: "82865824"
---
# <a name="teach-qa-to-understand-questions-and-terms-in-power-bi-qa"></a>Ensinar Perguntas e Respostas para compreender as perguntas e os termos nas Perguntas e Respostas do Power BI

Na secção **Ensinar Perguntas e Respostas** da configuração das Perguntas e Respostas, irá preparar Perguntas e Respostas para compreender as perguntas e os termos de linguagem natural que não são reconhecidos. Para começar, submeta uma pergunta que contenha uma ou mais palavras que as Perguntas e Respostas não reconhecem. Em seguida, as Perguntas e Respostas pedem-lhe para definir esse termo. Introduza um filtro ou um nome de campo que corresponda ao significado dessa palavra. Depois, as Perguntas e Respostas reinterpretam a pergunta original. Se estiver satisfeito com os resultados, guarde-os.

> [!NOTE]
> A funcionalidade Ensinar Perguntas e Respostas apenas suporta o modo de importação. Também ainda não suporta a ligação a uma origem de dados no local ou do Azure Analysis Services. Esta limitação deverá ser removida nas versões subsequentes do Power BI.

## <a name="start-to-teach-qa"></a>Começar a ensinar Perguntas e Respostas

1. No Power BI Desktop, no friso **Modelação**, selecione **Configuração das Perguntas e Respostas** > **Ensinar Perguntas e Respostas**.

    ![Sinónimo de Ensinar Perguntas e Respostas a vermelho](media/q-and-a-tooling-teach-q-and-a/qna-tooling-teach-synonym-red.png)

2. Escreva uma frase com um termo que as Perguntas e Respostas não reconhecem e selecione **Submeter**.

3. Selecione a palavra sublinhada a vermelho. 

    As Perguntas e Respostas fornecem sugestões e pedem-lhe para indicar a definição correta do termo. 
    
3. Em **Definir os termos que as Perguntas e Respostas não compreenderam**, forneça uma definição.

    ![Pré-visualização de sinónimos de Ensinar Perguntas e Respostas](media/q-and-a-tooling-teach-q-and-a/qna-tooling-teach-fixpreview.png)

4. Selecione **Guardar** para pré-visualizar o elemento visual atualizado.

5. Introduza a pergunta seguinte ou selecione o **X** para fechar.

Os consumidores do seu relatório só verão esta alteração quando publicar o relatório novamente no serviço.

## <a name="define-nouns-and-adjectives"></a>Definir substantivos e adjetivos

Pode ensinar dois tipos de termos às Perguntas e Respostas:

- Substantivos
- Adjetivos

### <a name="define-a-noun-synonym"></a>Definir um sinónimo de substantivo

Quando trabalha com dados, geralmente tem nomes de campos que podem ser referidos com nomes alternativos. Um exemplo poderia ser "Vendas". Várias palavras ou frases podem referir-se a vendas, como "receita". Se uma coluna for denominada "Vendas" e os consumidores do relatório escreverem "receita", as Perguntas e Respostas podem não escolher a coluna correta para responder à pergunta adequadamente. Nesse caso, quer informar as Perguntas e Respostas que "Vendas" e "Receita" se referem à mesma coisa.

As Perguntas e Respostas detetam automaticamente quando uma palavra não reconhecida é um substantivo através do conhecimento do Microsoft Office. Se as Perguntas e Respostas detetarem um substantivo, ser-lhe-á pedido da seguinte forma:

- <your term> **refere-se a** 

Preenche a caixa com o termo dos seus dados.

![Pedido de sinónimo de Ensinar Perguntas e Respostas](media/q-and-a-tooling-teach-q-and-a/qna-tooling-synonym-prompt.png)

Se fornecer algo diferente de um campo do modelo de dados, poderá obter resultados indesejáveis.

### <a name="define-an-adjective-filter-condition"></a>Definir uma condição de filtro de adjetivo

Por vezes, poderá querer definir termos que atuem como uma condição nos dados subjacentes. Um exemplo poderia ser "Publicadores Fantásticos". "Fantástico" pode ser uma condição que seleciona apenas publicadores que publicaram um determinado número de produtos. As Perguntas e Respostas tentam detetar os adjetivos e mostram um pedido diferente:

- <field name> **que tem**  

Preenche a caixa com a condição.

![Pedido de sinónimo de Ensinar Perguntas e Respostas](media/q-and-a-tooling-teach-q-and-a/qna-tooling-adjectives.png)

Algumas condições de exemplo que pode definir são:

- País, que é EUA
- País, que não é EUA
- Produtos > 100
- Produtos é maior do que 100
- Produtos = 100
- Produtos é 100
- Produtos < 100
- Produtos é menos do que 100

Nestes exemplos, "Produtos" pode ser um nome de coluna ou uma medida. 

Também pode especificar uma agregação na própria expressão de Perguntas e Respostas. Por exemplo, se "produtos populares" forem produtos com pelo menos 100 unidades vendidas, pode definir produtos com "soma de unidades vendidas > 100" como populares.  

:::image type="content" source="media/q-and-a-tooling-teach-q-and-a/power-bi-qna-popular-products.png" alt-text="Definir "produtos populares"":::

Só pode definir uma condição nas ferramentas. Para definir condições mais complexas, utilize o DAX para criar uma coluna ou medida calculada e, em seguida, a secção de ferramentas para criar uma única condição para essa coluna ou medida.

## <a name="manage-terms"></a>Gerir termos

Depois de fornecer as definições, pode ver todas as correções feitas e editá-las ou eliminá-las. 

1. Em **Configuração das Perguntas e Respostas**, vá para a secção **Gerir termos**.

2. Elimine os termos que já não quer. Atualmente, não pode editar os termos. Para redefinir um termo, elimine-o e defina-o.

    ![Gerir termos das Perguntas e Respostas](media/q-and-a-tooling-teach-q-and-a/qna-manage-terms.png)

## <a name="next-steps"></a>Próximos passos

Existem diversas melhores práticas para melhorar o motor de linguagem natural. Para obter mais informações, veja [Melhores práticas das Perguntas e Respostas](q-and-a-best-practices.md).
