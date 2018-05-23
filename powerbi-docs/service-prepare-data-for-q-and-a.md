---
title: Como fazer com que os seus dados do Excel funcionem bem com as Perguntas e Respostas no Power BI
description: Como fazer com que os seus dados funcionem bem com as Perguntas e Respostas no Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 03/01/2018
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: a6216169eb50ca535b73b07f5553c9b3d5e17470
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-make-your-excel-data-work-well-with-qa-in-power-bi"></a>Como fazer com que os seus dados do Excel funcionem bem com as Perguntas e Respostas no Power BI
Se é alguém que cria modelos de dados ou livros do Excel que serão utilizados com o Power BI, continue a ler...

No Power BI, as Perguntas e Respostas podem pesquisar dados estruturados e escolher a visualização certa para a pergunta, o que as torna uma ferramenta muito apelativa.   

As Perguntas e Respostas podem funcionar em qualquer ficheiro Excel carregado que contenha tabelas, intervalos ou que contenha um modelo PowerPivot, mas quantas mais otimizações e limpezas de dados efetuar, mais robusto é o desempenho das Perguntas e Respostas.  Se pretender partilhar relatórios e dashboards com base no seu conjunto de dados, deverá querer que os seus colegas façam perguntas facilmente e recebam respostas de qualidade.

### <a name="how-qa-works-with-excel"></a>Como funcionam as Perguntas e Respostas com o Excel
As Perguntas e Respostas têm um conjunto de capacidades de compreensão da linguagem natural essencial que funciona nos seus dados. Dispõem da pesquisa de palavra-chave dependente do contexto para a sua tabela, coluna e nomes de campos calculados do Excel. Também dispõem de conhecimento interno sobre como filtrar, ordenar, agregar, agrupar e exibir dados. 

Por exemplo, numa tabela do Excel com o nome "Vendas", com as colunas "Produto", "Mês", "Unidades vendidas", "Vendas brutas" e "Lucro", pode fazer perguntas sobre qualquer uma dessas entidades.  Pode pedir para mostrar as vendas, o lucro total por mês, ordenar os produtos por unidades vendidas e muitas outras opções. Leia mais sobre os [tipos de perguntas que pode realizar](power-bi-q-and-a.md) e os [tipos de visualização que pode especificar numa consulta de Perguntas e Respostas](power-bi-visualization-types-for-reports-and-q-and-a.md).

### <a name="prepare-an-excel-dataset-for-qa"></a>Preparar um conjunto de dados do Excel para as Perguntas e Respostas
As Perguntas e Respostas baseiam-se nos nomes das tabelas, colunas e campos calculados para responder a perguntas específicas de dados, o que significa que o nome que dá às entidades no livro é importante!

Eis algumas sugestões para aproveitar ao máximo das Perguntas e Respostas no seu livro.

* Certifique-se de que os dados estão numa tabela do Excel. [Como criar uma tabela do Excel](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-e81aa349-b006-4f8a-9806-5af9df0ac664?ui=en-US&rs=en-US&ad=US).
* Certifique-se de que os nomes das tabelas, colunas e campos calculados fazem sentido num discurso natural.
  
  Por exemplo, se tiver uma tabela com dados de vendas, dê o nome "Vendas" à tabela. Nomes de colunas como "Ano", "Produto", "Representante de vendas" e "Valor" funcionam bem com as Perguntas e Respostas.

* Se o livro tiver um modelo de dados do PowerPivot, pode efetuar ainda mais otimizações. Leia mais sobre [Desmistificando as perguntas e respostas do Power BI, parte 2](http://blogs.msdn.com/b/powerbi/archive/2014/02/27/demystifying-power-bi-q-amp-a-part-2.aspx) da nossa equipa interna de especialistas em linguagem natural.

* Abra o conjunto de dados no Power BI Desktop e crie novas colunas, crie medidas calculadas, concatene campos para criar valores exclusivos, classifique dados por tipo (por exemplo, datas, cadeias, geografia, imagens, URLs) e muito mais.

## <a name="next-steps"></a>Próximos passos
Voltar a [Perguntas e Respostas do Power BI](power-bi-q-and-a.md)  
[Preparar conjuntos de dados no local para as Perguntas e Respostas](service-q-and-a-direct-query.md)   
[Início Rápido das Perguntas e Respostas](power-bi-visualization-introduction-to-q-and-a.md)  
[Obter dados (para o Power BI)](service-get-data.md)  

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

