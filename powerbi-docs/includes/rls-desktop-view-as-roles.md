---
ms.openlocfilehash: 8dc488a47ac2b5b4e7980b7404b2722b1120b6ab
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464412"
---
## <a name="validate-the-roles-within-power-bi-desktop"></a>Validar as funções no Power BI Desktop
Depois de criar as suas funções, teste os resultados das mesmas no Power BI Desktop.

1. No separador **Modelação**, selecione **Ver como Funções**. 

    ![Selecionar Ver como Funções](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

    A janela **Ver como funções** é apresentada e pode ver as funções que criou.

    ![Janela Ver como funções](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

3. Selecione uma função que criou e, em seguida, selecione **OK** para a aplicar. 

   O relatório compõe os dados relevantes para essa função.

4. Também pode selecionar **Outro utilizador** e fornecer um determinado utilizador. 

    ![Selecionar Outro utilizador](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

   Recomendamos que forneça o Nome Principal de Utilizador (UPN), uma vez que é utilizado pelo serviço Power BI e pelo Power BI Report Server.

   No Power BI Desktop, a opção **Outro utilizador** só apresentará resultados diferentes se estiver a utilizar a segurança dinâmica com base nas suas expressões DAX. 

5. Selecione **OK**. 

   O relatório será composto com base no que esse utilizador pode ver.



