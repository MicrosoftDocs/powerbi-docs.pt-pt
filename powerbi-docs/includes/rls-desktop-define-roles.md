## <a name="define-roles-and-rules-in-power-bi-desktop"></a>Definir funções e regras no Power BI Desktop
Pode definir funções e regras no Power BI Desktop. Quando publicar no Power BI, este também publicará as definições de funções.

Siga estes passos para definir funções de segurança.

1. Importar dados para o seu relatório do Power BI Desktop ou configurar uma ligação do DirectQuery.
   
   > [!NOTE]
   > Não pode definir funções no Power BI Desktop para ligações em direto do Analysis Services. Terá de o fazer no modelo do Analysis Services.
   > 
   > 
1. Selecione o separador **Modelação**.
2. Selecione **Gerir funções**.
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security.png)
4. Selecione **Criar**.
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-create-role.png)
5. Indique um nome para a função. 
6. Selecione a tabela à qual pretende aplicar uma regra DAX.
7. Introduza as expressões DAX. Esta expressão deverá devolver um valor de verdadeiro ou falso. Por exemplo: [ID de Entidade] = “Valor”.
   
   > [!NOTE]
   > Pode utilizar *username()* nesta expressão. Tenha em conta que *username()* tem o formato *DOMAIN\username* no Power BI Desktop. No serviço Power BI e no Power BI Report Server, estará no formato do Nome Principal de Utilizador (UPN). Em alternativa, pode utilizar *userprincipalname()*, que irá sempre devolver o utilizador no formato do respetivo nome principal de utilizador, *username@contoso.com*.
   > 
   > 
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-create-rule.png)
8. Após criar a expressão DAX, pode selecionar a caixa de verificação acima da caixa de expressão para validar a expressão.
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-validate-dax.png)
9. Selecione **Guardar**.

Não pode atribuir utilizadores a uma função no Power BI Desktop. Pode atribuí-los no serviço Power BI. Pode ativar a segurança dinâmica no Power BI Desktop ao utilizar as funções DAX *username()* ou *userprincipalname()* e ter as devidas relações configuradas. 

