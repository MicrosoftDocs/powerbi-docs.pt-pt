## <a name="validating-the-role-within-power-bi-desktop"></a>Validar a função no Power BI Desktop
Depois de ter criado a função, pode testar os resultados da função no Power BI Desktop. Para tal, selecione **Ver Como Funções**.

![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

A caixa de diálogo **Ver como funções** permite-lhe alterar a vista do que está a ver para essa função ou utilizador específico. Verá as funções que criou.

![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

Selecione a função que criou e, em seguida, selecione **OK** para aplicar essa função ao que está a visualizar. Os relatórios vão apenas compor os dados relevantes para essa função.

Também pode selecionar Outro utilizador e fornecer um determinado utilizador. É melhor fornecer o Nome Principal de Utilizador (UPN), que é o que o serviço Power BI irá utilizar. Selecione **OK** e os relatórios serão compostos com base no que o utilizador pode ver. 

![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

> [!NOTE]
> No Power BI Desktop, isto apenas apresentará diferentes resultados se estiver a utilizar a segurança dinâmica com base nas expressões DAX.
> 
> 

