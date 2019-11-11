---
title: Segurança dinâmica ao nível da linha com o modelo de tabela dos serviços de Análise do Power BI
description: Segurança dinâmica ao nível da linha com o modelo em tabela do Analysis Services
author: selvarms
ms.reviewer: davidi
editor: davidi
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 05/28/2019
ms.author: selvar
LocalizationGroup: Connect to data
ms.openlocfilehash: 09726bccdd5a0b9a88d4a2df4d5be3b902a64b8c
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73876104"
---
# <a name="dynamic-row-level-security-with-analysis-services-tabular-model"></a>Segurança dinâmica ao nível da linha com o modelo em tabela do Analysis Services

Com um conjunto de dados de exemplo para executar os passos abaixo, este tutorial mostra-lhe como implementar [**segurança ao nível da linha**](service-admin-rls.md) num **Modelo de Tabela do Analysis Services** e utilizá-lo num relatório do Power BI. 

* Criar uma nova tabela de segurança na base de dados [**AdventureworksDW2012**](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)
* Criar o modelo de tabela com os factos e as dimensões de tabela necessários
* Definir funções e permissões de utilizadores
* Implementar o modelo numa instância **em tabela do Analysis Services**
* Criar um relatório do Power BI Desktop que apresenta dados personalizados ao utilizador que acede ao relatório
* Implementar o relatório no **serviço Power BI**
* Criar um novo dashboard com base no relatório
* Partilhar o dashboard com os colegas 

Este tutorial necessita da base de dados [**AdventureworksDW2012**](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).

## <a name="task-1-create-the-user-security-table-and-define-data-relationship"></a>Tarefa 1: Criar a tabela de segurança de utilizador e definir a relação de dados

Pode encontrar muitos artigos que descrevem como definir a segurança dinâmica ao nível da linha com o **modelo de tabela do SQL Server Analysis Services (SSAS)** . No nosso exemplo, utilizamos o artigo [Implement Dynamic Security by Using Row Filters](https://docs.microsoft.com/analysis-services/tutorial-tabular-1200/supplemental-lesson-implement-dynamic-security-by-using-row-filters) (Implementar Segurança Dinâmica com Filtros de Linha). 

Os passos aqui descritos necessitam da utilização da base de dados relacional **AdventureworksDW2012**.

1. Em **AdventureworksDW2012**, crie a tabela **DimUserSecurity** conforme ilustrado abaixo. Pode utilizar o [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) para criar a tabela.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable.png)

2. Quando criar e guardar a tabela, pode estabelecer a relação entre a coluna **SalesTerritoryID** da tabela **DimUserSecurity** e a coluna **SalesTerritoryKey** da tabela **DimSalesTerritory**, conforme mostrado abaixo. 

   No **SSMS**, clique com o botão direito na tabela **DimUserSecurity** e selecione **Design** (Estrutura). Em seguida, selecione **Table Designer -> Relationships...** (Estruturador de Tabelas > Relações...). Quando tiver terminado, guarde a tabela.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_keys.png)

3. Adicionar utilizadores à tabela: clique com o botão direito na tabela **DimUserSecurity** e selecione **Edit Top 200 Rows** (Editar as 200 Linhas Superiores). Depois de adicionar utilizadores, a tabela **DimUserSecurity** deverá ser semelhante à seguinte, mas com os seus utilizadores:
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_users.png)
   
   Verá estes utilizadores em tarefas futuras.

4. Em seguida, efetue uma *associação interna* com a tabela **DimSalesTerritory**, que mostra os detalhes de região associados ao utilizador. O código SQL aqui faz a *associação interna*, e a imagem mostra como a tabela é depois apresentada.
   
       select b.SalesTerritoryCountry, b.SalesTerritoryRegion, a.EmployeeID, a.FirstName, a.LastName, a.UserName from [dbo].[DimUserSecurity] as a join  [dbo].[DimSalesTerritory] as b on a.[SalesTerritoryID] = b.[SalesTerritoryKey]
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_join_users.png)

   A imagem mostra quem é responsável por cada região de vendas, graças à relação criada no **Passo 2**. Por exemplo, pode ver que **Jon Doe** é responsável pela região **Australia**. 

## <a name="task-2-create-the-tabular-model-with-facts-and-dimension-tables"></a>Tarefa 2: Criar o modelo de tabela com os factos e as tabelas de dimensão

1. Assim que o armazém de dados relacional estiver implementado, precisa de definir o modelo de tabela. Pode criar o modelo com o [**SQL Server Data Tools (SSDT)** ](https://docs.microsoft.com/sql/ssdt/sql-server-data-tools). Para obter mais informações, veja [Create a New Tabular Model Project](https://msdn.microsoft.com/library/hh231689.aspx) (Criar um Novo Projeto de Modelo de Tabela).

2. Importe todas as tabelas necessárias para o modelo, conforme mostrado abaixo.
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/ssdt_model.png)

3. Assim que tiver importado as tabelas necessárias, tem de definir uma função chamada **SalesTerritoryUsers** com permissão de **Leitura**. Selecione o menu **Model** (Modelo) no SQL Server Data Tools e, em seguida, selecione **Roles** (Funções). Na caixa de diálogo **Role Manager** (Gestor de Funções), selecione **New** (Novo).

4. No separador **Members** (Membros) do **Role Manager** (Gestor de Funções), adicione os utilizadores que definiu na tabela **DimUserSecurity** na **Tarefa 1 - passo 3**.
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager.png)

5. Em seguida, adicione as funções adequadas para as tabelas **DimSalesTerritory** e **DimUserSecurity**, conforme mostrado por baixo do separador **Filtros de Linha**.
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager_complete.png)

6. Neste passo, utilize a função **LOOKUPVALUE** para devolver os valores de uma coluna na qual o nome de utilizador do Windows corresponde ao que a função **USERNAME** devolve. Em seguida, pode restringir as consultas aos casos em que os valores devolvidos por **LOOKUPVALUE** correspondem aos na mesma tabela ou numa tabela relacionada. Na coluna **Filtro DAX**, escreva a seguinte fórmula:
   
       =DimSalesTerritory[SalesTerritoryKey]=LOOKUPVALUE(DimUserSecurity[SalesTerritoryID], DimUserSecurity[UserName], USERNAME(), DimUserSecurity[SalesTerritoryID], DimSalesTerritory[SalesTerritoryKey])

    Nesta fórmula, a função **LOOKUPVALUE** devolve todos os valores para a coluna **DimUserSecurity[SalesTerritoryID]** , em que **DimUserSecurity[UserName]** é o igual ao nome do utilizador atual com sessão iniciada no Windows, e **DimUserSecurity[SalesTerritoryID]** é igual a **DimSalesTerritory[SalesTerritoryKey]** .
   
    > [!IMPORTANT]
    > Ao utilizar segurança ao nível da linha, a função DAX [USERELATIONSHIP](https://msdn.microsoft.com/query-bi/dax/userelationship-function-dax) não é suportada.

   O conjunto de Vendas devolvido pelo **LOOKUPVALUE** de SalesTerritoryKey é então utilizado para restringir as linhas apresentadas em **DimSalesTerritory**. Apenas as tabelas em que o valor **SalesTerritoryKey** está nos IDs que a função **LOOKUPVALUE** devolve são apresentadas.

7. Para a tabela **DimUserSecurity**, na coluna **DAX Filter** (Filtro DAX), adicione a seguinte fórmula:
   
       =FALSE()

    Esta fórmula especifica que todas as colunas resolvem para `false`; o que significa que as colunas da tabela **DimUserSecurity** não podem ser consultadas.

8. Agora, é necessário processar e implementar o modelo. Para obter mais informações, veja o artigo [Deploy](https://msdn.microsoft.com/library/hh231693.aspx) (Implementar).

## <a name="task-3-add-data-sources-within-your-on-premises-data-gateway"></a>Tarefa 3: Adicionar Origens de Dados no Gateway de dados no local

Depois de o seu modelo de tabela estar implementado e pronto para utilizar, tem de adicionar uma ligação de origem de dados ao servidor da tabela no local do Analysis Services.

1. Para permitir que o **serviço Power BI** aceda ao seu serviço de análise no local, tem de ter um **[Gateway de dados no local](service-gateway-onprem.md)** instalado e configurado no seu ambiente.

2. Depois de o gateway estar configurado corretamente, tem de criar uma ligação à origem de dados para a sua instância de tabela do **Analysis Services**. Para mais informações, veja [Gerir a sua origem de dados – Analysis Services](service-gateway-enterprise-manage-ssas.md).
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_gateway.png)

  Com o passo anterior concluído, o gateway está configurado e pronto para interagir com a sua origem de dados do **Analysis Services** no local.

## <a name="task-4-create-report-based-on-analysis-services-tabular-model-using-power-bi-desktop"></a>Tarefa 4: Criar o relatório baseado no modelo de tabela de serviços de análise, com o Power BI Desktop

1. Inicie o **Power BI Desktop** e selecione **Obter Dados > Base de Dados**.

2. Na lista de origens de dados, selecione **Base de Dados do SQL Server Analysis Services** e selecione **Ligar**.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata.png)

3. Preencha os detalhes de instância de tabela do **Analysis Services** e selecione **Ligar em Direto**. Em seguida, selecione **OK**. No **Power BI**, a segurança dinâmica funciona apenas com a **Ligação em direto**.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)

4. Pode ver que o modelo implementado está na instância do **Analysis Services**. Selecione o modelo e selecione **OK**.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)

   O **Power BI Desktop** apresenta agora todos os campos disponíveis, à direita da tela do painel **Campos**.

5. No painel **Campos** à direita, selecione a medida **SalesAmount** da tabela **FactInternetSales** e a dimensão **SalesTerritoryRegion** da tabela **SalesTerritory**.

6. Para manter este relatório simples, de momento, não iremos adicionar mais colunas. Para obter uma representação mais significativa dos dados, altere a visualização para **Gráfico em anel**.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart.png)

7. Assim que o relatório estiver pronto, pode publicá-lo diretamente no portal do Power BI. No friso **Base** do **Power BI Desktop**, selecione **Publicar**.

## <a name="task-5-create-and-share-a-dashboard"></a>Tarefa 5: Criar e partilhar um dashboard

1. Criou o relatório e publicou-o no serviço **Power BI**. Agora, pode utilizar o exemplo criado nos passos anteriores para demonstrar o cenário de segurança do modelo.
   
   Na função **Gestor de Vendas**, o Sumit pode ver os dados de todas as regiões de vendas diferentes. O Sumit cria este relatório (o relatório criado nos passos das tarefas anteriores) e publica-o no serviço Power BI.
   
   Assim que publica o relatório, o próximo passo consiste em criar um dashboard no serviço Power BI chamado **TabularDynamicSec** com base nesse relatório. Na seguinte imagem, repare que o Sumit consegue ver os dados correspondentes a toda a região de vendas.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart_1.png)

2. Agora, partilha o dashboard com o seu colega, Jon Doe, que é responsável pelas vendas na região da Australia.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/user_jon_doe.png)
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_dashboard.png)

3. Quando o Jon Doe iniciar sessão no serviço **Power BI** e vir o dashboard partilhado que o Sumit criou, deverá ver **apenas** as vendas da sua região. 
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/dashboard_jon_doe.png)

    Parabéns! O **serviço Power BI** mostra a segurança ao nível da linha dinâmica definida no modelo de tabela local do **Analysis Services**. O Power BI utiliza a propriedade **EffectiveUserName** para enviar a credencial do utilizador atual do Power BI à origem de dados no local para executar as consultas.

## <a name="task-6-understand-what-happens-behind-the-scenes"></a>Tarefa 6: Compreender o que acontece em segundo plano

Esta tarefa pressupõe que está familiarizado com o [SQL Profiler](https://docs.microsoft.com/sql/tools/sql-server-profiler/sql-server-profiler), uma vez que é necessário capturar um rastreio de gerador de perfis do SQL Server na sua instância de tabela do SSAS no local.

1. A sessão é inicializada assim que o utilizador (Jon Doe) acede ao dashboard do serviço Power BI. Pode ver que a função **salesterritoryusers** tem efeito imediato com o nome de utilizador efetivo como **<EffectiveUserName>jondoe@moonneo.com</EffectiveUserName>**
   
       <PropertyList><Catalog>DefinedSalesTabular</Catalog><Timeout>600</Timeout><Content>SchemaData</Content><Format>Tabular</Format><AxisFormat>TupleFormat</AxisFormat><BeginRange>-1</BeginRange><EndRange>-1</EndRange><ShowHiddenCubes>false</ShowHiddenCubes><VisualMode>0</VisualMode><DbpropMsmdFlattened2>true</DbpropMsmdFlattened2><SspropInitAppName>PowerBI</SspropInitAppName><SecuredCellValue>0</SecuredCellValue><ImpactAnalysis>false</ImpactAnalysis><SQLQueryMode>Calculated</SQLQueryMode><ClientProcessID>6408</ClientProcessID><Cube>Model</Cube><ReturnCellProperties>true</ReturnCellProperties><CommitTimeout>0</CommitTimeout><ForceCommitTimeout>0</ForceCommitTimeout><ExecutionMode>Execute</ExecutionMode><RealTimeOlap>false</RealTimeOlap><MdxMissingMemberMode>Default</MdxMissingMemberMode><DisablePrefetchFacts>false</DisablePrefetchFacts><UpdateIsolationLevel>2</UpdateIsolationLevel><DbpropMsmdOptimizeResponse>0</DbpropMsmdOptimizeResponse><ResponseEncoding>Default</ResponseEncoding><DirectQueryMode>Default</DirectQueryMode><DbpropMsmdActivityID>4ea2a372-dd2f-4edd-a8ca-1b909b4165b5</DbpropMsmdActivityID><DbpropMsmdRequestID>2313cf77-b881-015d-e6da-eda9846d42db</DbpropMsmdRequestID><LocaleIdentifier>1033</LocaleIdentifier><EffectiveUserName>jondoe@moonneo.com</EffectiveUserName></PropertyList>

2. Com base no pedido do nome de utilizador efetivo, o Analysis Services converte o pedido para a credencial moonneo/jondoe atual, depois de consultar o Active Directory local. Quando o **Analysis Services** obtiver a credencial, o **Analysis Services** devolve os dados que o utilizador tem permissão para ver e aceder.

3. Se ocorrer mais atividade no dashboard, por exemplo, se Jon Doe passar do dashboard para o relatório subjacente, com o SQL Profiler irá ver uma consulta específica, que regressa ao modelo em tabela do Analysis Services com uma consulta DAX.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/profiler1.png)

4. Também pode ver abaixo a consulta DAX que está a ser executada para preencher os dados do relatório.
   
   ```
   EVALUATE
     ROW(
       "SumEmployeeKey", CALCULATE(SUM(Employee[EmployeeKey]))
     )
   
   <PropertyList xmlns="urn:schemas-microsoft-com:xml-analysis">``
             <Catalog>DefinedSalesTabular</Catalog>
             <Cube>Model</Cube>
             <SspropInitAppName>PowerBI</SspropInitAppName>
             <EffectiveUserName>jondoe@moonneo.com</EffectiveUserName>
             <LocaleIdentifier>1033</LocaleIdentifier>
             <ClientProcessID>6408</ClientProcessID>
             <Format>Tabular</Format>
             <Content>SchemaData</Content>
             <Timeout>600</Timeout>
             <DbpropMsmdRequestID>8510d758-f07b-a025-8fb3-a0540189ff79</DbpropMsmdRequestID>
             <DbPropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbPropMsmdActivityID>
             <ReturnCellProperties>true</ReturnCellProperties>
             <DbpropMsmdFlattened2>true</DbpropMsmdFlattened2>
             <DbpropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbpropMsmdActivityID>
           </PropertyList>
   ```

## <a name="considerations"></a>Considerações

* A segurança ao nível da linha no local com o Power BI só está disponível com uma Ligação em Direto.

* Quaisquer alterações nos dados após o processamento do modelo ficariam imediatamente disponíveis para os utilizadores que acedessem ao relatório através da **Ligação em Direto** do serviço Power BI.

