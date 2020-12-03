---
title: Orientação para a utilização de imagens para relatórios paginados
description: Orientações para utilizar imagens nos relatórios paginados do Power BI.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 02/16/2020
ms.openlocfilehash: ccb61899337e5585d03d9297fbe8f8a5decc612e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418400"
---
# <a name="image-use-guidance-for-paginated-reports"></a>Orientação para a utilização de imagens para relatórios paginados

O presente artigo destina-se a si, na qualidade de autor de relatório que cria [relatórios paginados](../paginated-reports/paginated-reports-report-builder-power-bi.md) do Power BI. Apresenta sugestões quando trabalhar com imagens. Normalmente, as imagens nos esquemas de relatório podem apresentar um gráfico, como um logótipo de empresa ou imagens.

As imagens podem ser armazenadas em três locais diferentes:

- No relatório (incorporado)
- Num servidor Web
- Numa base de dados, que podem ser obtidas por um conjunto de dados

Em seguida, podem ser utilizadas em vários cenários nos esquemas de relatório:

- Logótipo de posicionamento livre ou imagem
- Imagens associadas às linhas de dados
- Fundo de determinados itens de relatório:
  - Corpo do relatório
  - Caixa de texto
  - Retângulo
  - Região de dados Tablix (tabela, matriz ou lista)

## <a name="suggestions"></a>Sugestões

Considere as seguintes sugestões para obter esquemas de relatório profissionais, facilidade de manutenção e desempenho de relatório otimizado:

- **Utilize o tamanho mais pequeno possível**: recomendamos que prepare imagens pequenas, mas ainda assim nítidas. O mais importante é o equilíbrio entre a qualidade e o tamanho. Considere utilizar um editor gráfico (como o MS Paint) para reduzir o tamanho do ficheiro de imagem.
- **Evite imagens incorporadas**: primeiro, as imagens incorporadas podem aumentar o tamanho do ficheiro de relatório, o que pode contribuir para uma composição mais lenta do relatório. segundo, as imagens incorporadas podem tornar-se rapidamente um pesadelo em termos de manutenção se precisar de atualizar muitas imagens de relatório (como pode ser o caso se alterar o logótipo da sua empresa).
- **Utilize o armazenamento no servidor Web**: armazenar imagens num servidor Web é uma boa opção, especialmente para o logótipo da empresa, que pode ser proveniente do site da empresa. No entanto, tenha cuidado se os utilizadores tiverem de aceder a relatórios fora da sua rede. Neste caso, certifique-se de que as imagens estão disponíveis através da Internet.

    Quando as imagens estão relacionadas com os seus dados (como as imagens dos vendedores), atribua um nome aos ficheiros de imagem para que uma expressão de relatório possa produzir dinamicamente o caminho do URL da imagem. Por exemplo, pode atribuir nomes às imagens dos vendedores através do número de colaborador de cada vendedor. Desde que o conjunto de dados do relatório obtenha o número de colaborador, pode escrever uma expressão para produzir o caminho completo do URL da imagem.
- **Utilize o armazenamento da base de dados**: quando uma base de dados relacional armazena dados de imagens, faz sentido obter os dados de imagens diretamente das tabelas da base de dados, sobretudo quando as imagens não são muito grandes.
- **Imagens de fundo adequadas**: se decidir utilizar imagens de fundo, tenha cuidado para não distrair o utilizador dos dados do relatório. 

    Além disso, certifique-se de que utiliza _imagens com marca d'água_. Geralmente, as imagens com marca d'água têm um fundo transparente (ou têm a mesma cor de fundo utilizada pelo relatório). Também utilizam cores suaves. Exemplos comuns de imagens com marca d'água incluem o logótipo da empresa ou etiquetas de confidencialidade, como "Rascunho" ou "Confidencial".

## <a name="next-steps"></a>Próximos passos

Para obter mais informações relacionadas com este artigo, consulte os seguintes recursos:

- [O que são relatórios paginados no Power BI Premium?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)
