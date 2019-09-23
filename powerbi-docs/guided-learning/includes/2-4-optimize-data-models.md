---
ms.openlocfilehash: b42efb2c9237baf85a71be12cfaf61da189601d4
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61257063"
---
Muitas vezes, os dados importados contêm campos de que, na verdade, não precisa para as tarefas de criação de relatórios e visualização, porque se trata de informações adicionais ou porque os dados já estão disponíveis noutra coluna. O Power BI Desktop possui ferramentas para otimizar os seus dados e torná-los mais utilizáveis para criar relatórios e elementos visuais, bem como para visualizar os seus relatórios partilhados.

## <a name="hiding-fields"></a>Ocultar campos
Para ocultar uma coluna no painel **Campos** do Power BI Desktop, clique com o botão direito do rato na mesma e selecione **Ocultar**. Tenha em atenção que as colunas ocultas não são eliminadas. Caso tenha utilizado esse campo em visualizações existentes, os dados ainda estão nesse elemento visual e também ainda pode utilizar esses dados noutras visualizações. O campo oculto apenas não é apresentado no painel **Campos**.

![](media/2-4-optimize-data-models/2-4_1.png)

Se visualizar tabelas na vista de **Relações**, os campos ocultos são apresentados desativados. Mais uma vez, os respetivos dados continuam disponíveis e ainda fazem parte do modelo, estão apenas ocultos na visualização. Pode sempre mostrar qualquer campo que tenha sido oculto, clicando com o botão direito do rato no campo e selecionando **Mostrar**.

## <a name="sorting-visualization-data-by-another-field"></a>Ordenar dados de visualização por outro campo
A ferramenta **Ordenar por Coluna**, disponível no separador **Modelação**, é muito útil para garantir que os seus dados são apresentados pela ordem que pretendia.

![](media/2-4-optimize-data-models/2-4_2.png)

Um exemplo comum: os dados que incluem o nome de um mês são ordenados alfabeticamente por predefinição. Assim, por exemplo, "Agosto" aparece antes de "Fevereiro".

![](media/2-4-optimize-data-models/2-4_3.png)

Neste caso, para resolver o problema, selecione o campo na lista de Campos, selecione **Ordenar por Coluna** no separador **Modelação** e, em seguida, escolha um campo pelo qual ordenar. Neste caso, a opção de ordenação da categoria "MonthNo" ordena os meses da forma pretendida.

![](media/2-4-optimize-data-models/2-4_4.png)

Outra forma de otimizar as suas informações para que sejam tratadas corretamente consiste em definir o tipo de dados para um campo. Para alterar um tipo de dados da tela do relatório, selecione a coluna no painel **Campos** e, em seguida, utilize o menu pendente **Formatar** para selecionar uma das opções de formatação. Todos os elementos visuais que tenha criado que apresentem esse campo são atualizados automaticamente.

