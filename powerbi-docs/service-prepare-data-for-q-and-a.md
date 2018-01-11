---
title: "Faça com que os seus dados funcionem bem com as Perguntas e Respostas no Power BI"
description: "Faça com que os seus dados funcionem bem com as Perguntas e Respostas no Power BI"
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 09/26/2017
ms.author: mihart
ms.openlocfilehash: 499c3beca9046af9336de6dfec96994004050986
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="make-your-data-work-well-with-qa-in-power-bi"></a>Faça com que os seus dados funcionem bem com as Perguntas e Respostas no Power BI
Se é alguém que cria modelos de dados ou livros do Excel que serão utilizados com o Power BI, continue a ler...

No Power BI, as Perguntas e Respostas podem pesquisar dados estruturados e escolher a visualização certa para a pergunta, o que as torna uma ferramenta muito apelativa.   

As Perguntas e Respostas podem funcionar em qualquer ficheiro Excel carregado que contenha tabelas, intervalos ou que contenha um modelo PowerPivot, mas quantas mais otimizações e limpezas de dados efetuar, mais robusto é o desempenho das Perguntas e Respostas. 

## <a name="how-qa-works"></a>Como funcionam as Perguntas e Respostas
As Perguntas e Respostas têm um conjunto de capacidades de compreensão da linguagem natural essencial que funciona nos seus dados. Dispõem da pesquisa de palavra-chave dependente do contexto para a sua tabela, coluna e nomes de campos calculados do Excel. Dispõem ainda de conhecimento interno sobre como filtrar, ordenar, agregar, agrupar e exibir dados. 

Por exemplo, numa tabela do Excel com o nome "Vendas", com as colunas "Produto", "Mês", "Unidades vendidas", "Vendas brutas" e "Lucro", pode fazer perguntas sobre qualquer uma dessas entidades.  Pode pedir para mostrar as vendas, o lucro total por mês, ordenar os produtos por unidades vendidas e muitas outras opções. Leia mais sobre os [tipos de perguntas que pode realizar](http://blogs.msdn.com/b/powerbi/archive/2014/02/27/demystifying-power-bi-q-amp-a-part-1.aspx) e [fazer perguntas utilizando um modelo](service-q-and-a.md) e [tipos de visualização que pode especificar numa consulta de perguntas e respostas](power-bi-visualization-types-for-reports-and-q-and-a.md).

## <a name="prepare-a-workbook-for-qa"></a>Preparar um livro para Perguntas e Respostas
As Perguntas e Respostas baseiam-se nos nomes das tabelas, colunas e campos calculados para responder a perguntas específicas de dados, o que significa que o nome que dá às entidades no livro é importante!

Eis algumas sugestões para aproveitar ao máximo das Perguntas e Respostas no seu livro.

* Certifique-se de que os dados estão numa tabela do Excel. [Como criar uma tabela do Excel](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-e81aa349-b006-4f8a-9806-5af9df0ac664?ui=en-US&rs=en-US&ad=US).
* Certifique-se de que os nomes das tabelas, colunas e campos calculados fazem sentido em português.
  
  Por exemplo, se tiver uma tabela com dados de vendas, dê o nome "Vendas" à tabela. Nomes de colunas como "Ano", "Produto", "Representante de vendas" e "Valor" funcionam bem com as Perguntas e Respostas.

> [!NOTE]
> Se o livro tiver um modelo de dados do PowerPivot, pode efetuar ainda mais otimizações. Leia mais sobre [Desmistificando as perguntas e respostas do Power BI, parte 2](http://blogs.msdn.com/b/powerbi/archive/2014/02/27/demystifying-power-bi-q-amp-a-part-2.aspx) da nossa equipa interna de especialistas em linguagem natural.
> 
> 

## <a name="next-steps"></a>Próximos passos
[Perguntas e Respostas no Power BI](service-q-and-a.md)  
[Tutorial: introdução às perguntas e respostas do Power BI](power-bi-visualization-introduction-to-q-and-a.md)  
[Obter dados (para o Power BI)](service-get-data.md)  
[Power BI - Conceitos Básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

