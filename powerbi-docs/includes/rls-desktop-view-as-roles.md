---
ms.openlocfilehash: eb7cba03daee47f6772fc46be50419731b41765e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61194137"
---
## <a name="validate-the-roles-within-power-bi-desktop"></a>Validar as funções no Power BI Desktop
Depois de criar as suas funções, teste os resultados das mesmas no Power BI Desktop.

1. Selecione **Ver Como Funções**. 

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

    Em **Ver como funções**, pode ver as funções que criou.

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

3. Selecione uma função que criou e selecione **OK** para a aplicar. O relatório compõe os dados relevantes para essa função. 

4. Também pode selecionar **Outro utilizador** e fornecer um determinado utilizador. Recomendamos que forneça o Nome Principal de Utilizador (UPN), uma vez que é utilizado pelo serviço Power BI e pelo Power BI Report Server.

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

1. Selecione **OK** e o relatório será composto com base no que esse utilizador pode ver. 

No Power BI Desktop, a opção **Outro utilizador** só apresentará resultados diferentes se estiver a utilizar a segurança dinâmica com base nas suas expressões DAX. 

