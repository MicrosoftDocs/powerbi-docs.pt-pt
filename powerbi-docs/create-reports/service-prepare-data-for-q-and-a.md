---
title: Faça com que os dados do Excel funcionem bem com as Perguntas e Respostas no Power BI
description: Como fazer com que os seus dados funcionem bem com as Perguntas e Respostas no Power BI
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 05/13/2019
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 41672fa809544198a053ae41f935e890d83cfa72
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96388109"
---
# <a name="make-excel-data-work-well-with-qa-in-power-bi"></a>Faça com que os dados do Excel funcionem bem com as Perguntas e Respostas no Power BI
Se é alguém que cria modelos de dados ou livros do Excel que serão utilizados com o Power BI, continue a ler...

No Power BI, as Perguntas e Respostas podem pesquisar dados estruturados e escolher a visualização certa para a pergunta, o que as torna uma ferramenta muito apelativa.   

As Perguntas e Respostas podem funcionar em qualquer ficheiro Excel carregado que contenha tabelas, intervalos ou que contenha um modelo PowerPivot, mas quantas mais otimizações e limpezas de dados efetuar, mais robusto é o desempenho das Perguntas e Respostas.  Se pretender partilhar relatórios e dashboards com base no seu conjunto de dados, deverá querer que os seus colegas façam perguntas facilmente e recebam respostas de qualidade.

## <a name="how-qa-works-with-excel"></a>Como funcionam as Perguntas e Respostas com o Excel
As Perguntas e Respostas têm um conjunto de capacidades de compreensão da linguagem natural essencial que funciona nos seus dados. Dispõem da pesquisa de palavra-chave dependente do contexto para a sua tabela, coluna e nomes de campos calculados do Excel. Também dispõem de conhecimento interno sobre como filtrar, ordenar, agregar, agrupar e exibir dados. 

Por exemplo, numa tabela do Excel com o nome "Vendas", com as colunas "Produto", "Mês", "Unidades vendidas", "Vendas brutas" e "Lucro", pode fazer perguntas sobre qualquer uma dessas entidades.  Pode pedir para mostrar as vendas, o lucro total por mês, ordenar os produtos por unidades vendidas e muitas outras opções. Leia mais sobre [utilizar as Perguntas e Respostas em dashboards e relatórios](power-bi-tutorial-q-and-a.md) e os [tipos de visualização que pode especificar numa consulta de Perguntas e Respostas](../visuals/power-bi-visualization-types-for-reports-and-q-and-a.md).

## <a name="prepare-an-excel-dataset-for-qa"></a>Preparar um conjunto de dados do Excel para as Perguntas e Respostas
As Perguntas e Respostas baseiam-se nos nomes das tabelas, colunas e campos calculados para responder a perguntas específicas de dados, o que significa que o nome que dá às entidades no livro é importante!

Eis algumas sugestões para aproveitar ao máximo das Perguntas e Respostas no seu livro.

* Certifique-se de que os dados estão numa tabela do Excel. [Como criar uma tabela do Excel](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-e81aa349-b006-4f8a-9806-5af9df0ac664).
* Certifique-se de que os nomes das tabelas, colunas e campos calculados fazem sentido num discurso natural.
  
  Por exemplo, se tiver uma tabela com dados de vendas, dê o nome "Vendas" à tabela. Nomes de colunas como "Ano", "Produto", "Representante de vendas" e "Valor" funcionam bem com as Perguntas e Respostas.

* Se o livro tiver um modelo de dados do PowerPivot, pode efetuar ainda mais otimizações. Leia mais sobre [Desmistificando as perguntas e respostas do Power BI, parte 2](https://powerbi.microsoft.com/blog/demystifying-power-bi-q-amp-a-part-2/) da nossa equipa interna de especialistas em linguagem natural.

* Abra o conjunto de dados no Power BI Desktop e crie novas colunas, crie medidas, concatene campos para criar valores exclusivos, classifique dados por tipo (por exemplo, datas, cadeias, geografia, imagens, URLs) e muito mais.

## <a name="next-steps"></a>Próximos passos

- [Perguntas e Respostas para consumidores](../consumer/end-user-q-and-a.md)  
- [Utilizar Perguntas e Respostas em dashboards e relatórios](power-bi-tutorial-q-and-a.md)
- [Preparar conjuntos de dados no local para as Perguntas e Respostas](service-q-and-a-direct-query.md)   
- [Obter dados (para o Power BI)](../connect-data/service-get-data.md)  

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
