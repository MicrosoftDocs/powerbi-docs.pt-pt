---
title: Títulos com base em expressão no Power BI Desktop
description: Criar títulos dinâmicos no Power BI Desktop que mudam com base nas expressões programáticas, usando a formatação condicional programática
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: reference
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b90ef66d2c118a70f1b18ed4fe302ce1db23e45c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769755"
---
# <a name="expression-based-titles-in-power-bi-desktop"></a>Títulos com base em expressão no Power BI Desktop

Pode criar dinâmico, personalizado títulos os elementos visuais do Power BI. Criando expressões DAX (Data Analysis) com base nos campos, as variáveis ou outros elementos de programação, os títulos dos elementos visuais podem ajustar automaticamente conforme necessário. Estas alterações são baseadas em filtros, as seleções, ou outras interações do usuário e configurações.

![Opção de formatação condicional de captura de ecrã do Power BI Desktop](media/desktop-conditional-formatting-visual-titles/expression-based-title-01.png)

Criar títulos dinâmicos, por vezes denominado *títulos com base em expressão*, é muito simples. 

## <a name="create-a-field-for-your-title"></a>Criar um campo para o título

A primeira etapa na criação de um título com base em expressão é criar um campo no seu modelo a utilizar para o título. 

Existem todos os tipos de formas criativas de ter o título da visual refletem o que deseja que ele faça ou o que deseja express. Vamos dar uma olhada em alguns exemplos.

Pode criar uma expressão que as alterações com base no contexto de filtro que recebe do elemento visual para o nome da marca do produto. A imagem seguinte mostra a fórmula DAX para este campo.

![Fórmula de captura de ecrã da DAX](media/desktop-conditional-formatting-visual-titles/expression-based-title-02.png)

Outro exemplo está a utilizar um título dinâmico que as alterações com base no idioma ou cultura do usuário. Pode criar títulos de idioma específico numa medida DAX, utilizando o `USERCULTURE()` função. Esta função devolve o código de cultura para o utilizador, com base no respetivo sistema operativo ou as definições do browser. Pode utilizar a seguinte instrução de comutador DAX para selecionar o valor correto de traduzido. 

```
SWITCH (
  USERCULTURE(),
  "de-DE", “Umsatz nach Produkt”,
  "fr-FR", “Ventes par produit”,
  “Sales by product”
)
```

Ou pode recuperar a cadeia de caracteres de uma tabela de pesquisa que contém todas as traduções. Essa tabela é colocar no seu modelo. 

Estes são apenas alguns exemplos que pode utilizar para criar títulos dinâmicos, com base em expressão, os elementos visuais no Power BI Desktop. O que pode fazer com os títulos de estão limitadas apenas pela sua imaginação e seu modelo.


## <a name="select-your-field-for-your-title"></a>Selecione o campo para o título

Depois de criar a expressão DAX para o campo que criar no seu modelo, precisa para aplicá-la ao título do seu elemento visual.

Selecione o campo e aplicá-lo, vá para o **visualizações** painel. Na **formato** área, selecione **Title** para mostrar as opções de título para o elemento visual. 

Quando com o botão direito **texto do título**, é apresentado um menu de contexto que permite-lhe selecionar ***fx * a formatação condicional**. Quando seleciona esse item de menu, um **texto do título** é apresentada a caixa de diálogo. 

![Caixa de diálogo de texto de captura de ecrã do título](media/desktop-conditional-formatting-visual-titles/expression-based-title-02b.png)

Essa janela, pode selecionar o campo que criou a utilizar para o título.

## <a name="limitations-and-considerations"></a>Limitações e considerações

Existem algumas limitações para a implementação atual de títulos com base em expressão para elementos visuais:

* Formatação com base em expressão não é atualmente suportado em elementos visuais de Python, os elementos visuais R ou o elemento visual de influenciadores chave.
* O campo que criar para o título tem de ser um tipo de dados de cadeia de caracteres. Medidas que retornam números ou data/hora (ou qualquer outro tipo de dados) não são atualmente suportadas.

## <a name="next-steps"></a>Próximos passos

Este artigo descreveu como criar expressões DAX que transformar os títulos dos seus elementos visuais em campos dinâmicos que podem alterar como os utilizadores interagem com os seus relatórios. Pode encontrar os seguintes artigos úteis também.

* [Utilizar a análise do relatório no Power BI Desktop](desktop-cross-report-drill-through.md)
* [Utilizar a pormenorização no Power BI Desktop](desktop-drillthrough.md)