---
ms.openlocfilehash: cd0696b44e285119193059304c89cfa04c755771
ms.sourcegitcommit: bbd9b38f30a4ca5cb8072496c9cacb635b03aa88
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71409379"
---
## <a name="faq"></a>PERGUNTAS FREQUENTES
**Pergunta:** E se eu tiver criado anteriormente funções e regras para um conjunto de dados no serviço Power BI? Estes continuarão a funcionar se não fizer nada?  
**Resposta:** Não, os elementos visuais não serão compostos corretamente. Terá de voltar a criar as funções e regras no Power BI Desktop e, em seguida, publicá-las no serviço Power BI.

**Pergunta:** Posso criar estas funções para origens de dados do Analysis Services?  
**Resposta:** Se tiver importado os dados para o Power BI Desktop, pode fazê-lo. Se estiver a utilizar uma ligação em direto, não poderá configurar a RLS no serviço Power BI. Isto é definido no modelo do Analysis Services no local.

**Pergunta:** Posso utilizar a RLS para limitar as colunas ou medidas acessíveis pelos meus utilizadores?  
**Resposta:** Não, se um utilizador tiver acesso a uma linha de dados específica, pode ver todas as colunas de dados dessa linha.

**Pergunta:** A RLS permite-me ocultar dados detalhados, mas dar acesso a dados resumidos nos elementos visuais?  
**Resposta:** Não. Pode proteger linhas individuais de dados, mas os utilizadores poderão sempre ver os detalhes ou os dados resumidos.

**Pergunta:** A minha origem de dados já tem funções de segurança definidas (por exemplo, funções do SQL Server ou de SAP BW). Qual é a relação entre estas e a RLS?  
**Resposta:** A resposta depende do facto de estar a importar dados ou a utilizar o DirectQuery. Se estiver a importar dados para o seu conjunto de dados do Power BI, não serão utilizadas as funções de segurança na sua origem de dados. Neste caso, deve definir a RLS para impor regras de segurança aos utilizadores que se ligam ao Power BI. Se estiver a utilizar o DirectQuery, serão utilizadas as funções de segurança na sua origem de dados. Quando um utilizador abre um relatório, o Power BI envia uma consulta para a origem de dados subjacente, que aplica regras de segurança aos dados com base nas credenciais do utilizador.
