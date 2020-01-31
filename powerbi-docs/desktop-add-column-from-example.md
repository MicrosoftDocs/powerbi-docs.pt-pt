---
title: Adicionar uma coluna a partir de um exemplo no Power BI Desktop
description: Crie uma nova coluna rapidamente no Power BI Desktop utilizando as colunas existentes como exemplos.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: b10bbaa4158e6c5392cb6ed937c54bdbb5d555d2
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/23/2020
ms.locfileid: "76538576"
---
# <a name="add-a-column-from-examples-in-power-bi-desktop"></a>Adicionar uma coluna a partir dos exemplos no Power BI Desktop
Com a opção *adicionar colunas a partir dos exemplos* no Editor do Power Query, pode adicionar novas colunas ao seu modelo de dados ao fornecer simplesmente um ou mais valores de exemplo para as novas colunas. Pode criar os exemplos da nova coluna a partir de uma seleção ou dar contributos com base em todas as colunas existentes na tabela.

![](media/desktop-add-column-from-example/add-column-from-example_01.png)

A utilização da opção *adicionar coluna a partir de exemplo* permite-lhe criar novas colunas de forma rápida e fácil e é excelente nas seguintes situações:

- Sabe quais os dados que pretende incluir na sua nova coluna, mas não tem a certeza qual é a transformação ou coleção de transformações que irá obter.
- Já sabe quais são as transformações de que precisa mas não tem a certeza do que deve selecionar na IU para concretizá-las.
- Sabe tudo sobre as transformações que precisa com uma expressão de *Coluna Personalizada* na linguagem *M*, mas uma ou mais dessas expressões não estão disponíveis na IU.

Adicionar uma coluna a partir de um exemplo é fácil e simples. As próximas secções mostram como é fácil.

## <a name="add-a-new-column-from-examples"></a>Adicionar uma nova coluna a partir dos exemplos

Para obter dados de exemplo a partir da Wikipédia, selecione **Obter Dados** > **Web** a partir do separador **Home Page** do friso do Power BI Desktop. 

![Obter Dados da Web](media/desktop-add-column-from-example/add-column-from-example_02.png)

Cole o seguinte URL na caixa de diálogo que aparece e selecione **OK**: 

*https:\//wikipedia.org/wiki/List_of_states_and_territories_of_the_United_States*

Na caixa de diálogo **Navegador**, selecione a tabela **States of the United States of America** (Estados dos Estados Unidos da América) e, em seguida, selecione **Transformar Dados**. A tabela é aberta no Editor do Power Query.

Em alternativa, para abrir dados já carregados a partir do Power BI Desktop, selecione **Editar Consultas** a partir do separador **Home Page** do friso. Os dados são abertos no Editor do Power Query. 

![Selecione Editar Consultas a partir do Power BI Desktop](media/desktop-add-column-from-example/add-column-from-example_05.png)

Quando os dados de exemplo forem abertos no Editor do Power Query, selecione o separador **Adicionar Coluna** no friso e, em seguida, selecione **Coluna a partir dos Exemplos**. Selecione o ícone **Coluna a partir dos Exemplos** para criar a coluna a partir de todas as colunas existentes ou selecione a seta pendente para escolher entre **De Todas as Colunas** ou **Da Seleção**. Para estas instruções, utilize a opção **De Todas as Colunas**.

![Selecione Adicionar Coluna a Partir dos Exemplos](media/desktop-add-column-from-example/add-column-from-example_03.png)

## <a name="add-column-from-examples-pane"></a>Painel Adicionar Coluna a Partir dos Exemplos
Quando selecionar **Adicionar Coluna** > **a partir dos Exemplos**, o painel **Adicionar Coluna a partir dos Exemplos** é aberto na parte superior da tabela. A nova **Coluna 1** aparece à direita das colunas existentes (poderá ter de se deslocar para ver todas). Quando introduz os seus valores de exemplo nas células em branco da **Coluna 1**, o Power BI cria regras e transformações que correspondam aos seus exemplos e utiliza-as para preencher o resto da coluna.

Observe que a opção **Coluna a partir dos Exemplos** também aparece como um **Passo Aplicado** no painel **Definições da Consulta**. Como sempre, o Editor do Power Query regista os passos de transformação e aplica-os na consulta, por ordem.

![Painel Adicionar Coluna a Partir dos Exemplos](media/desktop-add-column-from-example/add-column-from-example_04.png)

À medida que escrever o exemplo na nova coluna, o Power BI mostra-lhe uma pré-visualização de qual o aspeto que a coluna irá ter, com base nas transformações que cria. Por exemplo, se escrever *Alabama* na primeira linha, corresponde ao valor **Alabama** na primeira coluna da tabela. Assim que premir Enter, o Power BI preenche o resto da nova coluna com base no valor da primeira coluna e dá o nome **Name & postal abbreviation[12] - Copy** (Nome e abreviatura postal[12] - Cópia) à coluna.

Agora, aceda à linha **Massachusetts[E]** da nova coluna e elimine a parte **[E]** da cadeia. O Power BI deteta a alteração e utiliza o exemplo para criar uma transformação. O Power BI descreve as transformações no painel **Adicionar Coluna a Partir dos Exemplos** e muda o nome da coluna para **Texto Antes do Delimitador.** 

![Coluna transformada a partir dos exemplos](media/desktop-add-column-from-example/add-column-from-example_06.png)

À medida que apresenta exemplos, o Editor do Power Query adiciona às transformações. Quando estiver satisfeito, selecione **OK** para consolidar as alterações. 

Pode dar o nome que quiser à nova coluna ao fazer duplo clique no cabeçalho da coluna ou ao fazer duplo clique na mesma coluna e selecionar **Mudar o nome**. 

Veja este vídeo para ver a opção **Adicionar Coluna a partir dos Exemplos** em ação, utilizando a origem de dados de exemplo: 

[Power BI Desktop: Add Column From Examples](https://www.youtube.com/watch?v=-ykbVW9wQfw) (Power BI Desktop: Adicionar Coluna a Partir dos Exemplos). 

## <a name="list-of-supported-transformations"></a>Lista de transformações suportadas
Muitas mas nem todas as transformações estão disponíveis ao utilizar a opção **Adicionar Coluna a Partir Dos Exemplos**. A seguinte lista apresenta as transformações suportadas:

**Geral**

- Coluna Condicional

**Referência**
  
- Referência a uma coluna específica, incluindo transformações de corte, limpeza e capitalização

**Transformações de texto**

- Combinar (suporta a combinação de cadeias de literais e valores da coluna completa)
- Substituir
- Comprimento
- Extrair   
  - Primeiros Carateres
  - Últimos Carateres
  - Intervalo
  - Texto antes do Delimitador
  - Texto após o Delimitador
  - Texto entre os Delimitadores
  - Comprimento
  - Remover Carateres
  - Manter Carateres

> [!NOTE]
> Todas as transformações de *Texto* têm em consideração o potencial de corte, limpeza ou aplicar uma transformação de capitalização no valor da coluna.

**Transformações de data**

- Dia
- Dia da Semana
- Nome do Dia da Semana
- Dia do Ano
- Mês
- Nome do Mês
- Trimestre do Ano
- Semana do Mês
- Semana do Ano
- Ano
- Idade
- Início do Ano
- Fim do Ano
- Início do Mês
- Fim do Mês
- Início do Trimestre
- Dias no Mês
- Fim do Trimestre
- Início da Semana
- Fim da Semana
- Dia do Mês
- Início do Dia
- Fim do Dia

**Transformações de hora**

- Hour
- Minuto
- Second  
- Para Hora Local

> [!NOTE]
> Todas as transformações de *Data* e *Hora* têm em consideração a potencial necessidade de converter o valor da coluna para *Data*, *Hora* ou *DateTime*.

**Transformações de número** 

- Valor Absoluto
- Arco cosseno
- Arco seno
- Arco tangente
- Converter para Número
- Cosseno
- Cubo
- Dividir
- Expoente
- Fatorial
- Divisão de Número Inteiro
- É Igual
- É Ímpar
- Ln
- Logaritmo de Base 10
- Módulo
- Multiplicar
- Arredondar por Defeito
- Arredondar por Excesso
- Assinar
- Sin
- Raiz Quadrada
- Quadrado
- Subtrair
- Som
- Tangente
- Decomposição/Intervalos

