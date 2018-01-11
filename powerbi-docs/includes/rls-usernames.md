## <a name="using-the-username-or-userprincipalname-dax-function"></a>Utilizar as funções DAX username() ou userprincipalname()
Pode tirar partido das funções DAX *username()* ou *userprincipalname()* dentro do conjunto de dados. Pode utilizá-las nas expressões no Power BI Desktop. Quando publicar o seu modelo, este será utilizado no âmbito do serviço Power BI.

No Power BI Desktop, *username()* irá devolver um utilizador no formato de *DOMÍNIO\Utilizador* e *userprincipalname()* irá devolver um utilizador no formato de  *user@contoso.com*.

No âmbito do serviço Power BI, *username()* e *userprincipalname()* irão devolver o Nome Principal de Utilizador (UPN) do utilizador. Isto parece ser semelhante a um endereço de e-mail.

