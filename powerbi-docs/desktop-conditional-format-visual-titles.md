---
title: Títulos baseados em expressões no Power BI Desktop
description: Crie títulos dinâmicos no Power BI Desktop que mudam em função de expressões programáticas com recurso à formatação programática condicional
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: reference
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1b4e134ef6f8da43a1856c8a5458c8c09b2c42b5
ms.sourcegitcommit: f05ba39a0e46cb9cb43454772fbc5397089d58b4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/26/2019
ms.locfileid: "68522187"
---
# <a name="expression-based-titles-in-power-bi-desktop"></a>Títulos baseados em expressões no Power BI Desktop

Pode criar títulos dinâmicos e personalizados para os seus elementos visuais do Power BI. Ao criar DAX (Data Analysis Expressions) com base em campos, variáveis ou outros elementos programáticos, os títulos dos seus elementos visuais podem ajustar-se automaticamente conforme necessário. Estas alterações baseiam-se em filtros, seleções ou outras interações e configurações de utilizador.

![Captura de ecrã a mostrar a opção de formatação condicional do Power BI Desktop](media/desktop-conditional-formatting-visual-titles/expression-based-title-01.png)

A criação de títulos dinâmicos, por vezes chamados *títulos baseados em expressões*, é simples. 

## <a name="create-a-field-for-your-title"></a>Criar um campo para o seu título

O primeiro passo da criação de um título baseado em expressões consiste na criação de um campo no seu modelo a utilizar para o título. 

Há diversas formas criativas de fazer com que o título do seu elemento visual reflita o que pretende dizer ou expressar. Vamos ver alguns exemplos.

Pode criar uma expressão que muda em função do contexto do filtro que o elemento visual recebe para o nome da marca do produto. A seguinte imagem mostra a fórmula DAX desse campo.

![Captura de ecrã a mostrar a fórmula DAX](media/desktop-conditional-formatting-visual-titles/expression-based-title-02.png)

Outro exemplo consiste na utilização de um título dinâmico que muda em função do idioma ou da cultura do utilizador. Pode criar títulos específicos de idioma numa medida DAX com recurso à função `USERCULTURE()`. Esta função devolve o código da cultura do utilizador com base no sistema operativo ou nas definições do browser do mesmo. Pode utilizar a seguinte instrução switch DAX para selecionar o valor traduzido correto. 

```
SWITCH (
  USERCULTURE(),
  "de-DE", “Umsatz nach Produkt”,
  "fr-FR", “Ventes par produit”,
  “Sales by product”
)
```

Em alternativa, pode obter a cadeia de carateres de uma tabela de referência que contenha todas as traduções. Para tal, tem de colocar essa tabela no seu modelo. 

Estes são apenas alguns exemplos que pode utilizar para criar títulos baseados em expressões dinâmicos para os seus elementos visuais no Power BI Desktop. O que pode fazer com os títulos é limitado apenas pela sua imaginação e pelo seu modelo.


## <a name="select-your-field-for-your-title"></a>Selecionar o campo para o seu título

Depois de criar a expressão DAX para o campo que criar no seu modelo, precisará de a aplicar ao título do seu elemento visual.

Para selecionar e aplicar o campo, aceda ao painel **Visualizações**. Na área **Formatação**, selecione **Título** para mostrar as opções de título para o elemento visual. 

Quando clicar com o botão direito do rato em **Texto do título**, será apresentado um menu de contexto que lhe permite selecionar a ***fx* formatação condicional**. Quando selecionar esse item de menu, aparece uma caixa de diálogo **Texto do título**. 

![Captura de ecrã a mostrar a caixa de diálogo do texto do título](media/desktop-conditional-formatting-visual-titles/expression-based-title-02b.png)

Nessa janela, pode selecionar o campo que criou para o utilizar no seu título.

## <a name="limitations-and-considerations"></a>Limitações e considerações

De momento, a implementação de títulos baseados em expressões para elementos visuais tem algumas limitações:

* De momento, a formatação baseada em expressões não é suportada em elementos visuais de Python, em elementos visuais de R ou no elemento visual de influenciadores principais.
* O tipo de dados do campo que criar para o título tem de ser uma cadeia de carateres. Atualmente, não são suportadas medidas que devolvem números ou data/hora (ou qualquer outro tipo de dados).
* Os títulos baseados em expressões não são transferidos quando afixa um elemento visual a um dashboard.

## <a name="next-steps"></a>Próximos passos

Este artigo descreveu como criar expressões DAX que transformam os títulos dos seus elementos visuais em campos dinâmicos que podem mudar à medida que os utilizadores interagem com os seus relatórios. Também poderá achar os seguintes artigos úteis.

* [Formatação condicional em tabelas](desktop-conditional-table-formatting.md)
* [Utilizar a pormenorização de relatório cruzado no Power BI Desktop](desktop-cross-report-drill-through.md)
* [Utilizar a pormenorização no Power BI Desktop](desktop-drillthrough.md)
