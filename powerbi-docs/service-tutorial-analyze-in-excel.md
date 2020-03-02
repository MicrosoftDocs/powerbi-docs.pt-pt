---
title: 'Tutorial: Utilizar a opção Analisar no Excel do Power BI, a começar no Excel'
description: Neste tutorial, começa no Excel e liga-se à página Conjuntos de dados do Power BI para importar conjuntos de dados para o Excel.
author: tejaskulkarni
ms.reviewer: davidiseminger
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 02/13/2020
ms.author: tekulkar
LocalizationGroup: Connect to services
ms.openlocfilehash: d3795c34e477c593af4afefbe5cc01040026bfa4
ms.sourcegitcommit: d6a48e6f6e3449820b5ca03638b11c55f4e9319c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/18/2020
ms.locfileid: "77426547"
---
# <a name="tutorial-use-power-bi-analyze-in-excel-starting-in-excel"></a>Tutorial: Utilizar a opção Analisar no Excel do Power BI, a começar no Excel

A sua organização utiliza o Power BI para partilhar o acesso aos dados. Inicia a funcionalidade Analisar no Excel do Power BI no Excel, para criar tabelas dinâmicas e gráficos dinâmicos no Excel. Estes podem trazer contexto adicional à sua análise ou reduzir o tempo para localizar e importar conjuntos de dados relevantes.

Para começar com um conjunto de dados do Power BI, no Excel, selecione "Analisar no Excel". Verá orientações para criar uma tabela dinâmica que utiliza os dados.  

Poderá encontrar conjuntos de dados adicionais partilhados pela sua organização ao regressar à página Conjuntos de dados.

Se tiver algum tipo de problema em qualquer passo, selecione **Não** no passo apropriado no fluxo abaixo e forneça comentários no formulário associado.  

Neste tutorial, vai aprender a:

> [!div class="checklist"]
> * Transferir um ficheiro ODC da página Conjuntos de dados do Power BI.
> * Ativar o acesso para os conjuntos de dados a partir do Excel.
> * Começar a utilizar o conjunto de dados para criar Tabelas Dinâmicas, gráficos e folhas de cálculo

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este tutorial, precisa de:

* Uma conta do Power BI. Se não estiver inscrito no Power BI, [inscreva-se para uma avaliação gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) antes de começar.

* Confirmar que está confortável com todos os passos listados no tutorial [Introdução ao serviço Power BI](https://docs.microsoft.com/power-bi/service-get-started).

* Um conjunto de dados do Power BI Premium e de uma licença do Power BI Pro. Para obter mais informações, veja [O que é o Power BI Premium?](https://docs.microsoft.com/power-bi/service-premium-what-is).

* Pode encontrar uma lista completa dos pré-requisitos no documento abrangente [Analisar no Excel](https://docs.microsoft.com/power-bi/service-analyze-in-excel#requirements).

* Uma [Subscrição do Microsoft Office E5](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software?activetab=pivot%3aoverviewtab) ativa

## <a name="get-started"></a>Introdução

No Excel, selecione a opção para criar Tabelas Dinâmicas com os dados partilhados do Power BI e navegue para a página Conjuntos de dados do Power BI.

![Página Conjuntos de Dados](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-01.png)

Ao utilizar o fluxo de trabalho Analisar no Excel, verá várias instruções que o vão guiar; indique se concluiu cada passo para progredir. Se tiver algum problema em qualquer passo, selecione **Não** e forneça os seus comentários no formulário correspondente.

![Instruções do Fluxo de Trabalho](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-02.png)

## <a name="download-and-open-the-odc-file"></a>Transferir e abrir o ficheiro ODC

Escolha o conjunto de dados na lista correspondente e na área de trabalho associada e, em seguida, clique em Analisar no Excel. O Power BI cria um ficheiro ODC e transfere-o do browser para o computador.

![Selecionar conjunto de dados](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-03.png)

Ao abrir o ficheiro no Excel, é apresentada uma lista vazia de Tabelas Dinâmicas e Campos com as tabelas, os campos e as medidas do conjunto de dados do Power BI. Pode criar Tabelas Dinâmicas, gráficos e analisar esse conjunto de dados tal como faria com um conjunto de dados local no Excel.

## <a name="enable-data-connections"></a>Ativar ligações de dados

Para analisar os dados do Power BI no Excel, pode ser-lhe pedido para confiar na ligação. Os administradores podem desativar a utilização da funcionalidade Analisar no Excel com conjuntos de dados no local alojados em Bases de Dados dos Analysis Services no Portal de Administração do Power BI.

![Ativar a Ligação](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-04.png)

## <a name="install-updates-and-authenticate"></a>Instalar atualizações e autenticar

Na primeira vez que abrir um novo ficheiro ODC, também lhe pode ser pedido que se autentique com a sua conta do Power BI.  Se tiver problemas, veja o documento abrangente [Analisar no Excel](https://docs.microsoft.com/power-bi/service-analyze-in-excel#sign-in-to-power-bi ) para obter mais informações ou clique em Não durante o fluxo de trabalho.

![Ativar a Ligação](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-05.png)

## <a name="analyze-away"></a>Analisar

À semelhança de outros livros locais, Analisar no Excel permite-lhe criar Tabelas Dinâmicas, gráficos, adicionar dados e criar diferentes folhas de cálculo com vistas para os dados. Analisar no Excel expõe todos os dados ao nível de detalhe a todos os utilizadores que tenham permissão para aceder ao conjunto de dados. Pode guardar este livro, mas não o pode publicar ou importar de volta para o Power BI nem o pode partilhar com outros utilizadores na organização. Para obter mais informações e outros casos práticos, veja [Analisar no Excel](https://docs.microsoft.com/power-bi/service-analyze-in-excel#analyze-away).

## <a name="clean-up-resources"></a>Limpar recursos

As interações com a página Conjuntos de Dados e Serviço do Power BI devem estar limitadas à transferência do ficheiro ODC e aos cliques no fluxo de trabalho. Se tiver algum tipo de problema com algum destes passos, indique **Não** no passo adequado e forneça comentários no formulário associado. O formulário contém uma ligação para obter mais informações sobre o problema. Visite novamente a página Conjuntos de dados para voltar a tentar o processo ou selecione outro conjunto de dados.

## <a name="next-steps"></a>Próximos passos

Poderá também estar interessado nos seguintes artigos:

* [Utilizar a pormenorização de relatório cruzado no Power BI Desktop](https://docs.microsoft.com/power-bi/desktop-cross-report-drill-through)

* [Utilizar a segmentação de dados no Power BI Desktop](https://docs.microsoft.com/power-bi/visuals/power-bi-visualization-slicers)
