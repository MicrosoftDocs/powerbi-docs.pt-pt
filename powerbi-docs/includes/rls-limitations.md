## <a name="limitations"></a>Limitações
Segue-se uma lista das limitações atuais da segurança ao nível de linha nos modelos da cloud.

* Se anteriormente tinha funções e regras definidas no serviço Power BI, terá de recriá-las no Power BI Desktop.
* Pode definir a RLS apenas nos conjuntos de dados criados com o cliente do Power BI Desktop. Se desejar ativar a RLS para conjuntos de dados criados com o Excel, será necessário converter os ficheiros em ficheiros PBIX primeiro. [Saiba mais](../desktop-import-excel-workbooks.md)
* Só são suportadas ligações ETL e DirectQuery. As ligações em direto para o Analysis Services são processadas no modelo no local.
* De momento, as Perguntas e Respostas e o Cortana não são suportados com a RLS. Não verá a caixa de entrada de Perguntas e Respostas para os dashboards, se todos os modelos tiverem a RLS configurada. Isto está planeado, mas não está disponível uma data futura.
* Para qualquer modelo, o número máximo de principais do Azure AD (ou seja, utilizadores individuais ou grupos de segurança) que podem ser atribuídos a funções de segurança é 1000. Para atribuir grandes números de utilizadores a funções, atribua grupos de segurança, em vez de utilizadores individuais.

## <a name="known-issues"></a>Problemas conhecidos
Existe um problema conhecido em que será apresentada uma mensagem de erro ao tentar publicar a partir do Power BI Desktop, se os conteúdos tiverem sido publicados anteriormente. Segue-se o cenário.

1. A Anna tem um conjunto de dados que foi publicado no serviço Power BI e configurou a RLS.
2. A Anna atualiza o relatório no Power BI Desktop e volta a publicar o conjunto de dados.
3. A Teresa vê um erro.

**Solução:** publicar novamente o ficheiro do Power BI Desktop a partir do serviço Power BI, até que o problema seja resolvido. Pode fazê-lo ao selecionar **Obter Dados** > **Ficheiros**. 

