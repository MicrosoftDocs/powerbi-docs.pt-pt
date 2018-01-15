## <a name="faq"></a>PERGUNTAS FREQUENTES
**Pergunta:** e se eu tiver criado anteriormente funções/regras para um conjunto de dados no serviço Power BI? Estes continuarão a funcionar se não fizer nada?  
**Resposta:** não. Os elementos visuais não ficarão compostos corretamente. Terá de voltar a criar as funções/regras no Power BI Desktop e, em seguida, publicá-las no serviço Power BI.

**Pergunta:** posso cria estas funções para origens de dados do Analysis Services?  
**Resposta:** pode, se tiver importado os dados para o Power BI Desktop. Se estiver a utilizar uma ligação em direto, não poderá configurar a RLS no serviço Power BI. Isto é definido no modelo do Analysis Services no local.

**Pergunta:** posso utilizar a RLS para limitar as colunas ou medidas acessíveis pelos meus utilizadores?  
**Resposta:** não. Se um utilizador tiver acesso a uma linha de dados específica, pode ver todas as colunas de dados dessa linha.

**Pergunta:** a RLS permite-me ocultar dados detalhados enquanto concedo acesso a dados resumidos nos elementos visuais?  
**Resposta:** não. Protege linhas individuais de dados, mas os utilizadores podem sempre ver os detalhes ou dados resumidos.

