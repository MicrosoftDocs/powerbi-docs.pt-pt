---
ms.openlocfilehash: 3966521d158c244487638be4117f98ea570e1f28
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "73800063"
---
Bem-vindo à secção da **Aprendizagem Orientada** do Power BI que visa apresentar o **DAX**.

**DAX** significa **Data Analysis Expressions** e é a linguagem de fórmulas utilizada em todo o Power BI (também é utilizada pelo Power BI nos bastidores). O DAX também se encontra noutras ofertas da Microsoft, como o Power Pivot e o SSAS Tabular, mas estes tópicos de Aprendizagem Orientada centram-se na forma como o DAX é utilizado (e pode ser utilizado por si ) no Power BI.

## <a name="dax-and-this-guided-learning-video-series"></a>DAX e a série de vídeos desta Aprendizagem Orientada
O objetivo desta secção da **Aprendizagem Orientada** é ensinar-lhe as noções básicas e os princípios do DAX – como pensar no DAX, como funciona e as funcionalidades mais úteis, tal como explicadas (e aprendidas com muita experiências) por uma especialista de renome no DAX, [ Alberto Ferrari](https://www.sqlbi.com/learning-dax).

![Retrato de Alberto Ferrari](media/7-1-intro-to-dax/intro_dax_6_alberto_ferrari.png)

Os vídeos nesta secção da **Aprendizagem Orientada** sobre o **DAX** ensinam-lhe as noções básicas do DAX na perspetiva de como funciona a linguagem de fórmulas DAX. Isto é útil para criar fórmulas DAX a partir do zero, mas também é muito útil para compreender como o Power BI cria essas fórmulas DAX à medida que o utilizador cria consultas no **Editor de Consultas**.

## <a name="in-this-video---introduction-to-dax"></a>Neste vídeo - introdução ao DAX
Os conceitos do DAX são simples e objetivos, mas o DAX é poderoso. O DAX utiliza alguns padrões e conceitos de programação únicos que podem dificultar a plena utilização e compreensão dos mesmos. As formas tradicionais de aprender linguagens podem não ser a melhor abordagem ao DAX, pelo que o objetivo deste vídeo é ensinar conceitos e teoria que o irão ajudar mais tarde na sua utilização do Power BI.

O DAX é uma *linguagem funcional*, que significa que o código executado completo está contido dentro de uma função.

No DAX, as funções podem conter outras funções aninhadas, instruções condicionais e referências de valor. A execução no DAX começa na função ou parâmetro mais interno e funciona para fora. No Power BI, as fórmulas DAX são escritas numa única linha, pelo que é importante para a legibilidade formatar corretamente as suas funções.

O DAX foi concebido para funcionar com tabelas, pelo que tem apenas dois tipos de dados principais: **Numérico** e **Outro**. **Numérico** pode incluir *números inteiros*, *decimais* e *moeda*. **Outro** pode incluir *cadeias* e *objetos binários*. Isto significa que se criar a função DAX para funcionar num tipo de número, pode ter a garantia de que irá funcionar em quaisquer outros dados Numéricos.

O DAX utiliza a sobrecarga de operadores, o que significa que pode misturar tipos de dados nos seus cálculos e os resultados irão mudar com base no tipo de dados utilizados nas entradas. A conversão acontece automaticamente, o que significa que não tem de conhecer os tipos de dados das colunas com que está a trabalhar no Power BI, mas também significa que, por vezes, a conversão pode ocorrer de formas inesperadas. Recomenda-se que compreenda os dados que está a utilizar para garantir que os operadores se comportam como previsto.

Há um tipo de dados em particular com o qual irá, provavelmente, trabalhar com frequência no Power BI: **DateTime**. **DateTime** é armazenado como um valor de vírgula flutuante com partes de número inteiro e decimal. DateTime pode ser utilizado com precisão para cálculos de qualquer período de tempo após 1 de março de 1900.

> Conteúdo de vídeo cortesia de [Alberto Ferrari, SQLBI](https://www.sqlbi.com/learning-dax/?utm_source=powerbi&utm_medium=marketing&utm_campaign=after-summit)
> 
> 

