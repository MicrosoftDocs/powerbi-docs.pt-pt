---
title: Separar relatórios de modelos no Power BI Desktop
description: Orientação para separar relatórios de modelos no Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/11/2020
ms.author: v-pemyer
ms.openlocfilehash: dad451da460abed65a69990394522f268d7f21cd
ms.sourcegitcommit: 5ece366fceee9832724dae40eacf8755e1d85b04
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2020
ms.locfileid: "81525277"
---
# <a name="separate-reports-from-models-in-power-bi-desktop"></a>Separar relatórios de modelos no Power BI Desktop

Ao criar uma nova solução do Power BI Desktop, uma das primeiras tarefas que deve realizar é “obter dados”. A obtenção de dados pode resultar em dois resultados completamente diferentes. Pode:

- Criar uma [Ligação em Direto](../desktop-report-lifecycle-datasets.md) para um modelo já publicado, que pode ser um conjunto de dados do Power BI ou um modelo do Analysis Services alojado remotamente.
- Inicie o desenvolvimento de um novo modelo, que pode ser um modelo de Importação, DirectQuery ou Composto.

Este artigo aborda o segundo cenário. Proporciona orientações sobre se um relatório e um modelo devem ser combinados num único ficheiro do Power BI Desktop.

## <a name="single-file-solution"></a>Solução de ficheiro único

Uma _solução de ficheiro único_ funciona bem quando existe só um relatório único baseado no modelo. Neste caso, é provável que tanto o modelo como o relatório sejam resultado dos esforços da mesma pessoa. Definida como uma solução _BI Pessoal_, embora o relatório possa ser partilhado com outros utilizadores. Estas soluções podem representar relatórios no âmbito da função ou avaliações únicas de um desafio empresarial – normalmente, descritos como relatórios _ad hoc_.

:::image type="content" source="media/report-separate-from-model/single-file-solution.png" alt-text="Um ficheiro único contém um modelo e relatório, desenvolvido pela mesma pessoa." border="true":::

## <a name="separate-report-files"></a>Ficheiros de relatório separado

Faz sentido separar o desenvolvimento do modelo e do relatório em ficheiros separados do Power BI Desktop quando:

- Os modeladores dos dados e os autores dos relatórios são pessoas diferentes.
- Está subentendido que um modelo será a origem de vários relatórios, agora ou no futuro.

:::image type="content" source="media/report-separate-from-model/separate-report-files.png" alt-text="Existem três ficheiros PBIX. O primeiro contém apenas um modelo. Os outros dois contêm apenas relatórios, e estão diretamente ligados ao modelo alojado no serviço Power BI. Os relatórios são desenvolvidos por pessoas diferentes." border="true":::

Os modeladores dos dados ainda podem utilizar a experiência de criação de relatórios do Power BI Desktop para testar e validar os designs dos modelos. No entanto, logo após a publicação do ficheiro no serviço Power BI, devem remover o relatório da área de trabalho. E, devem lembrar-se de remover o relatório de cada vez que publicam novamente e substituem o conjunto de dados.

### <a name="preserve-the-model-interface"></a>Preservar a interface do modelo

Por vezes, as alterações ao modelo são inevitáveis. Os modeladores dos dados devem ter cuidado, para não criarem alterações interruptivas na interface do modelo. Se o fizerem, será possível que os elementos visuais relacionados ou os mosaicos do dashboard sofram alterações interruptivas. Os elementos visuais interrompidos surgem como erros e podem resultar em frustração para os consumidores e autores de relatórios. E pior, podem reduzir a confiança nos dados.

Assim, deve gerir as alterações ao modelo com cuidado. Se possível, evite as seguintes alterações:

- Mudar o nome de tabelas, colunas, hierarquias, níveis de hierarquia ou medidas.
- Modificar os tipos de dados de colunas.
- Modificar as expressões de medida para que devolvam um tipo de dados diferente.
- Mover medidas para uma tabela principal diferente, porque mover uma medida pode criar uma interrupção nas medidas no âmbito do relatório que qualificam completamente as medidas com o nome da tabela principal. Não recomendamos que escreva as expressões DAX com nomes de medidas completamente qualificados. Para obter mais informações, veja [DAX: Referências de colunas e de medidas](dax-column-measure-references.md).

A adição de novas tabelas, colunas, hierarquias, níveis de hierarquia ou medidas é segura, com uma exceção: É possível que um novo nome de medida possa entrar em conflito com um nome de medida no âmbito do relatório. Para evitar o conflito de nomes, recomendamos que os autores dos relatórios adotem uma convenção de nomenclatura ao definir medidas nos relatórios. Podem prefixar os nomes de medidas no âmbito do relatório com um caráter de sublinhado ou outro(s) caráter(es).

Se tiver de realizar alterações interruptivas aos modelos, recomendamos que:

- [Veja os conteúdos relacionados com o conjunto de dados](../consumer/end-user-related.md#view-related-content-for-a-dataset) no serviço Power BI.
- Explore a vista [Linhagem de dados](../collaborate-share/service-data-lineage.md) no serviço Power BI.

Ambas as opções permitem identificar rapidamente os relatórios e dashboards relacionados. A vista Linhagem de dados é provavelmente a melhor escolha, dado que é fácil ver a pessoa de contacto de cada artefacto relacionado. De facto, trata-se de uma hiperligação que abre uma mensagem de e-mail dirigida ao contacto.

Recomendamos que contacte o proprietário de cada artefacto relacionado para os informar de quaisquer alterações interruptivas planeadas. Desta forma, podem estar preparados e prontos para corrigir e publicar novamente os relatórios, o que ajuda a minimizar o tempo de inatividade e a frustração.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações relacionadas com este artigo, consulte os seguintes recursos:

- [Ligar a conjuntos de dados no serviço Power BI a partir do Power BI Desktop](../desktop-report-lifecycle-datasets.md)
- [Ver conteúdos relacionados no serviço Power BI](../consumer/end-user-related.md)
- [Linhagem de dados](../collaborate-share/service-data-lineage.md)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)
