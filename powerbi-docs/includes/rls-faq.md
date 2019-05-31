---
ms.openlocfilehash: b05b5b0b5212f39b9b47cb63e2fc8522fff2f8e3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61194074"
---
## <a name="faq"></a>PERGUNTAS FREQUENTES
**Pergunta:** E se eu tiver criado anteriormente funções e regras para um conjunto de dados no serviço Power BI? Estes continuarão a funcionar se não fizer nada?  
**Resposta:** Não. Os elementos visuais não ficarão compostos corretamente. Terá de voltar a criar as funções e regras no Power BI Desktop e, em seguida, publicá-las no serviço Power BI.

**Pergunta:** Posso criar estas funções para origens de dados do Analysis Services?  
**Resposta:** Se tiver importado os dados para o Power BI Desktop, pode fazê-lo. Se estiver a utilizar uma ligação em direto, não poderá configurar a RLS no serviço Power BI. Isto é definido no modelo do Analysis Services no local.

**Pergunta:** Posso utilizar a RLS para limitar as colunas ou medidas acessíveis pelos meus utilizadores?  
**Resposta:** Não. Se um utilizador tiver acesso a uma linha de dados específica, pode ver todas as colunas de dados dessa linha.

**Pergunta:** A RLS permite-me ocultar dados detalhados, mas dar acesso a dados resumidos nos elementos visuais?  
**Resposta:** Não. Pode proteger linhas individuais de dados, mas os utilizadores poderão sempre ver os detalhes ou os dados resumidos.

