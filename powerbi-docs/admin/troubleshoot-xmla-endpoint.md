---
title: Resolver problemas de conectividade de pontos finais XMLA no Power BI
description: Descreve como resolver problemas de conectividade através do ponto final XMLA no Power BI Premium.
author: Minewiskan
ms.author: kfollis
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: troubleshooting
ms.date: 01/13/2021
ms.custom: seodec18, css_fy20Q4
LocalizationGroup: Premium
ms.openlocfilehash: 0753a9c3d5b832275f65ac11b87f90c38606f289
ms.sourcegitcommit: ab28cf07b483cb4b01a42fa879b788932bba919d
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226991"
---
# <a name="troubleshoot-xmla-endpoint-connectivity"></a>Troubleshoot XMLA endpoint connectivity (Resolver problemas de conectividade de pontos finais XMLA)

Os pontos finais XMLA no Power BI Premium dependem do protocolo de comunicação do Analysis Services nativo para obter acesso aos conjuntos de dados do Power BI. Por este motivo, a resolução de problemas do ponto final XMLA é praticamente idêntica à resolução de problemas numa ligação normal do Analysis Services. No entanto, existem algumas diferenças relacionadas com dependências específicas do Power BI.

## <a name="before-you-begin"></a>Before you begin

Antes resolver problemas num cenário de ponto final XMLA, confirme que analisa os conceitos básicos abordados em [Conectividade de conjuntos de dados com o ponto final XMLA](service-premium-connect-tools.md). Os casos de utilização mais comuns de pontos finais XMLA são abrangidos nesse documento. Outros guias de resolução de problemas do Power BI, como [Resolver problemas de gateways – Power BI](../connect-data/service-gateway-onprem-tshoot.md) e [Resolver problemas da função Analisar no Excel](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md), também podem ser úteis.

## <a name="enabling-the-xmla-endpoint"></a>Ativar o ponto final XMLA

Pode ativar o ponto final XMLA nas capacidades Power BI Premium e Power BI Embedded. Em capacidades mais pequenas, como uma capacidade A1 com apenas 2,5 GB de memória, poderá encontrar um erro nas definições da Capacidade ao tentar definir o ponto final XMLA para **Ler/Escrever** se, em seguida, selecionar **Aplicar**. O erro indica “Ocorreu um problema com as definições da carga de trabalho. Tente novamente dentro de momentos”.

Pode experimentar o seguinte:

- Limitar o consumo de memória de outros serviços na capacidade, como Fluxos de dados, para 40% ou menos, ou desativar completamente um serviço desnecessário.  
- Atualizar a capacidade para um SKU maior. Por exemplo, atualizar de uma capacidade A1 para uma A3 resolve este problema de configuração sem ser necessário desativar os Fluxos de dados.

Nota: também deve ativar a [definição Exportar dados](service-premium-connect-tools.md#security) ao nível do inquilino no Portal de Administração do Power BI. Esta definição também é necessária para a função Analisar no Excel.

## <a name="establishing-a-client-connection"></a>Estabelecer uma ligação com o cliente

Após ativar o ponto final XMLA, é uma boa ideia testar a conectividade com uma área de trabalho na capacidade. Para saber mais, veja [Ligar a uma área de trabalho Premium](service-premium-connect-tools.md#connecting-to-a-premium-workspace). Leia também a secção [Requisitos da ligação](service-premium-connect-tools.md#connection-requirements) para obter informações e sugestões úteis sobre as limitações atuais da conectividade XMLA.

### <a name="connecting-with-a-service-principal"></a>Ligar-se com um principal de serviço

Se tiver ativado as definições do inquilino para permitir que os principais de serviço utilizem APIs do Power BI, conforme descrito em [Ativar os principais de serviço](service-premium-service-principal.md#enable-service-principals), poderá ligar-se a um ponto final XMLA com um principal de serviço. Tenha em atenção que o principal de serviço requer o mesmo nível de permissões de acesso ao nível da área de trabalho ou do que o conjunto de dados que os utilizadores regulares.

Para utilizar um principal de serviço, confirme que especifica as informações de identidade da aplicação na cadeia de ligação como:

- `User ID=<app:appid@tenantid>`
- `Password=<application secret>`

Por exemplo:

`Data Source=powerbi://api.powerbi.com/v1.0/myorg/Contoso;Initial Catalog=PowerBI_Dataset;User ID=app:91ab91bb-6b32-4f6d-8bbc-97a0f9f8906b@19373176-316e-4dc7-834c-328902628ad4;Password=6drX...;`

Se receber o seguinte erro:

“Não é possível ligar ao conjunto de dados devido a informações incompletas na conta. Para os principais de serviço, confirme que especifica o ID do inquilino e o ID da aplicação no formato:\<appId>@\<tenantId>, em seguida, tenta novamente.”

Confirme que especifica o ID do inquilino e o ID da aplicação no formato correto.

Também pode especificar o ID da aplicação sem o ID do inquilino. No entanto, neste caso, tem de substituir o alias `myorg` no URL da origem de dados pelo ID do inquilino real. O Power BI pode então localizar o principal de serviço no inquilino correto. Mas, como melhor prática, utilize o alias `myorg` e especifique o ID do inquilino juntamente com o ID da aplicação no parâmetro ID do Utilizador.

### <a name="connecting-with-azure-active-directory-b2b"></a>Ligar-se com o Azure Active Directory B2B

Com suporte para o Azure Ative Directory (AAD) empresa-empresa (B2B) no Power BI, pode conceder aos utilizadores convidados externos acesso aos conjuntos de dados através do ponto final XMLA. Confirme que a definição [Partilhar conteúdo com utilizadores externos](service-admin-portal.md#export-and-sharing-settings) está ativada no Portal de administração do Power BI. Para saber mais, veja [Distribuir conteúdos do Power BI para utilizadores convidados externos com o AAD B2B](service-admin-azure-ad-b2b.md).

## <a name="deploying-a-dataset"></a>Implementar um conjunto de dados

Pode implementar um projeto de modelo tabular no Visual Studio (SSDT) numa área de trabalho do Power BI Premium de forma idêntica à do Azure Analysis Services. No entanto, ao implementar numa área de trabalho do Power BI Premium, existem algumas considerações adicionais. Confirme que lê a secção [Implementar projetos de modelo do Visual Studio (SSDT)](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt) no artigo Conectividade do conjunto de dados com o ponto final XMLA.

### <a name="deploying-a-new-model"></a>Implementar um novo modelo

Na configuração padrão, o Visual Studio tenta processar o modelo como parte da operação de implementação para carregar dados no conjunto de dados a partir das origens de dados. Conforme descrito em [Implementar projetos de modelo do Visual Studio (SSDT)](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt), esta operação pode falhar devido às credenciais da origem de dados não poderem ser especificadas como parte da operação de implementação. Em vez disso, se as credenciais da origem de dados ainda não estiverem definidas para nenhum dos conjuntos de dados existentes, deverá especificar as credenciais da origem de dados nas definições do conjunto de dados com a interface de utilizador do Power BI (**Conjuntos de dados** > **Definições** > **Credenciais da origem de dados** > **Editar credenciais**). Após ter definido as credenciais da origem de dados, o Power BI poderá aplicar automaticamente as credenciais a esta origem de dados para qualquer novo conjunto de dados, após a implementação de metadados ter sido bem-sucedida e o conjunto de dados ter sido criado.

Se o Power BI não conseguir vincular o novo conjunto de dados às credenciais da origem de dados, receberá um erro a indicar “Não é possível processar a base de dados. Motivo: Falha ao guardar as modificações no servidor.” com o código de erro “DMTS_DatasourceHasNoCredentialError”, conforme apresentado abaixo:

:::image type="content" source="media/troubleshoot-xmla-endpoint/deploy-refresh-error.png" alt-text="Erro na implementação do modelo":::

Para evitar a falha no processamento, defina **Opções de Implementação** > **Opções de Processamento** como **Não Processar**, conforme apresentado na imagem seguinte. O Visual Studio implementa apenas os metadados. Em seguida, pode configurar as credenciais da origem de dados e clicar em **Atualizar agora** para o conjunto de dados na interface de utilizador do Power BI. Para obter informações sobre a resolução de problemas de processamento, veja a secção [Atualizar um conjunto de dados](#refreshing-a-dataset) mais à frente neste artigo.

:::image type="content" source="media/troubleshoot-xmla-endpoint/do-not-process.png" alt-text="Opção Não processar":::

### <a name="new-project-from-an-existing-dataset"></a>Novo projeto a partir de um conjunto de dados existente

A criação de um novo projeto tabular no Visual Studio através da importação de metadados de um conjunto de dados existente na área de trabalho do Power BI Premium não é suportada. No entanto, pode ligar-se ao conjunto de dados com o SQL Server Management Studio, criar o script de metadados e reutilizá-lo noutros projetos tabulares.

## <a name="migrating-a-dataset-to-power-bi"></a>Migrar um conjunto de dados para o Power BI

É recomendado especificar um nível de compatibilidade de 1500 (ou superior) para os modelos tabulares. Este nível de compatibilidade suporta a maioria das capacidades e tipos de origens de dados. Os níveis de compatibilidade posteriores são retrocompatíveis com os níveis anteriores.

### <a name="supported-data-providers"></a>Fornecedores de dados suportados

No nível de compatibilidade 1500, o Power BI suporta os seguintes tipos de origens de dados:

- Origens de dados do fornecedor (legadas com uma cadeia de ligação nos metadados do modelo).
- Origens de dados estruturadas (introduzidas no nível de compatibilidade 1400).
- Declarações M inline de origens de dados (como declaradas pelo Power BI Desktop).

Recomenda-se a utilização de origens de dados estruturadas, que o Visual Studio cria por predefinição ao analisar o fluxo de dados de Importação. No entanto, se estiver a planear migrar um modelo existente para o Power BI que utiliza uma origem de dados do fornecedor, confirme que a origem de dados do fornecedor depende de um fornecedor de dados suportado. Especificamente, o Controlador OLE DB da Microsoft para SQL Server e todos os controladores ODBC de terceiros. No Controlador OLE DB para SQL Server, deve mudar a definição da origem de dados para o Fornecedor de Dados .NET Framework para SQL Server. Nos controladores ODBC de terceiros que possam estar indisponíveis no serviço Power BI, deve mudar para uma definição de origem de dados estruturada.

Recomenda-se também que substitua o controlador OLE DB da Microsoft para SQL Server (SQLNCLI11) desatualizado nas definições da origem de dados do SQL Server com o Fornecedor de Dados .NET Framework para SQL Server.

A tabela seguinte apresenta um exemplo de uma cadeia de ligação do Fornecedor de Dados .NET Framework para SQL Server a substituir uma cadeia de ligação correspondente do Controlador OLE DB para SQL Server.

|Controlador OLE DB para SQL Server  |Fornecedor de Dados .NET Framework para SQL Server   |
|---------|---------|
|`Provider=SQLNCLI11;Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW;Trusted_Connection=yes;`    |   `Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW2016;Integrated Security=SSPI;Encrypt=true;TrustServerCertificate=false`       |

### <a name="cross-referencing-partition-sources"></a>Cruzamento de referências de origens de partição

Assim como existem vários tipos de origens de dados, também existem vários tipos de origem de partição que um modelo tabular pode incluir para importar dados para uma tabela. Especificamente, uma partição pode utilizar uma origem de partição de consulta ou uma origem de partição M. Estes tipos de origem de partição, por sua vez, podem referenciar origens de dados do fornecedor ou origens de dados estruturadas. Apesar de os modelos tabulares no Azure Analysis Services suportarem as referências cruzadas a estes vários tipos de origens de dados e de partição, o Power BI impõe uma relação mais estrita. As origens de partição de consulta devem referenciar as origens de dados do fornecedor e as origens da partição M devem referenciar as origens de dados estruturadas. Outras combinações não são suportadas no Power BI. Se quiser migrar um conjunto de dados de referência cruzada, a seguinte tabela descreve as configurações suportadas:  

|Origem de dados   |Origem da partição   |Comentários   |Suportado no Power BI Premium com o ponto final XMLA   |
|---------|---------|---------|---------|
|Origem de dados do fornecedor      |   Origem da partição de consulta      |   O motor AS utiliza a pilha de conectividade com base em cartucho para aceder à origem de dados.       |     Sim     |
|Origem de dados do fornecedor      |   Origem da partição M       |   O motor AS converte a origem de dados do fornecedor numa origem de dados estruturada genérica e, em seguida, utiliza o motor de Aplicação Híbrida para importar os dados.       |    Não     |
|Origem de dados estruturada      |     Origem da partição de consulta     |    O motor AS molda a consulta nativa na origem da partição numa expressão M e, em seguida, utiliza o motor de Aplicação Híbrida para importar os dados.      |    Não     |
|Origem de dados estruturada      |    Origem da partição M      |     O motor AS utiliza o motor de Aplicação Híbrida para importar os dados.     |   Sim      |

## <a name="refreshing-a-dataset"></a>Atualizar um conjunto de dados

Os pontos finais XMLA permitem-lhe executar operações de atualização em modelos tabulares e, também, em conjuntos de dados criados no Power BI Desktop. Para suportar este último, confirme que especifica a definição Formato de armazenamento melhorado. Esta definição será obrigatória se quiser realizar operações de processamento ou outras operações de leitura/escrita com o ponto final XMLA. Pode encontrar a definição no Power BI Desktop em funcionalidades de Pré-visualização. Após definir, publique novamente a solução PBIX na área de trabalho do Power BI Premium.  

O Power BI apresentará o erro seguinte se realizar uma atualização através do ponto final XMLA num modelo sem metadados melhorados: “A operação só é suportada no modelo com a propriedade “DefaultPowerBIDataSourceVersion” definida como “PowerBI_V3” no Power BI Premium.”

### <a name="data-sources-and-impersonation"></a>Origem de dados e representação

As definições de representação que pode definir para as origens de dados do fornecedor não são relevantes para o Power BI. O Power BI utiliza um mecanismo diferente com base nas definições do conjunto de dados para gerir credenciais da origem de dados. Por este motivo, confirme que seleciona **Conta de Serviço** se estiver a criar uma Origem de Dados do Fornecedor.

:::image type="content" source="media/troubleshoot-xmla-endpoint/impersonate-services-account.png" alt-text="Representar conta de serviço":::

### <a name="fine-grained-processing"></a>Processamento detalhado

Ao acionar uma atualização agendada ou um pedido de atualização no Power BI, normalmente todo o conjunto de dados é atualizado. Em muitos casos, é mais eficiente para realizar atualizações de forma mais seletiva. Pode executar tarefas de processamento detalhadas no SQL Server Management Studio (SSMS), conforme apresentado abaixo, ou com ferramentas ou scripts de terceiros.

:::image type="content" source="media/troubleshoot-xmla-endpoint/process-tables.png" alt-text="Tabelas de processos no SSMS":::

### <a name="overrides-in-refresh-tmsl-command"></a>Substituições no comando TMSL Atualizar

As substituições no [comando Atualizar (TMSL)](/analysis-services/tmsl/refresh-command-tmsl) permitem aos utilizadores escolher uma definição diferente de consulta de partição ou definição da origem de dados para a operação de atualização. Neste momento, **as substituições não são suportadas** no Power BI Premium. É devolvido o seguinte erro: "O enlace fora de linha não é permitido no Power BI Premium. Para obter mais informações, veja 'Suporte de leitura/escrita XMLA' na documentação do produto".

## <a name="errors-in-ssms---premium-gen-2"></a>Erros no SSMS – Premium Gen 2

### <a name="query-execution"></a>Execução da consulta

Quando ligado a uma área de trabalho numa capacidade [Premium Gen2](service-premium-what-is.md#power-bi-premium-generation-2-preview), o SQL Server Management Studio pode apresentar o seguinte erro:

```
Executing the query ...
Error -1052311437:
```

Isto ocorre porque as bibliotecas de cliente instaladas com o SSMS v18.7.1 não suportam o rastreio de sessão. Esta situação foi resolvida no SSMS 18.8 e superior. [Transferir o SSMS mais recente](/sql/ssms/download-sql-server-management-studio-ssms).

### <a name="refresh-operations"></a>Operações de atualização

Quando utiliza o SSMS v18.7.1 ou uma versão inferior para executar uma operação de atualização de execução prolongada (superior a 1 minuto) numa capacidade Premium Gen2, mesmo se a operação de atualização for bem-sucedida, o SSMS poderá apresentar um erro como o seguinte:

```
Executing the query ...
Error -1052311437:
The remote server returned an error: (400) Bad Request.

Technical Details:
RootActivityId: 3716c0f7-3d01-4595-8061-e6b2bd9f3428
Date (UTC): 11/13/2020 7:57:16 PM
Run complete
```

Isto ocorre devido a um problema conhecido nas bibliotecas de cliente em que o estado do pedido de atualização é rastreado incorretamente. Esta situação foi resolvida no SSMS 18.8 e superior. [Transferir o SSMS mais recente](/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="editing-role-memberships-in-ssms"></a>Editar associações de funções no SSMS

Quando utiliza o SQL Server Management Studio (SSMS) v18.8 para editar uma associação de função num conjunto de dados, o SSMS poderá apresentar o seguinte erro:

```
Failed to save modifications to the server. 
Error returned: ‘Metadata change of current operation cannot be resolved, please check the command or try again later.’ 
```

Isso ocorre devido a um problema conhecido na API REST dos serviços aplicacionais. Esta situação será resolvida numa versão futura do SSMS. Entretanto, para contornar esse erro, em **Propriedades da Função**, clique em **Script** e, em seguida, introduza e execute o seguinte comando TMSL:

```json
{ 
  "createOrReplace": { 
    "object": { 
      "database": "AdventureWorks", 
      "role": "Role" 
    }, 
    "role": { 
      "name": "Role", 
      "modelPermission": "read", 
      "members": [ 
        { 
          "memberName": "xxxx", 
          "identityProvider": "AzureAD" 
        }, 
        { 
          "memberName": “xxxx” 
          "identityProvider": "AzureAD" 
        } 
      ] 
    } 
  } 
} 
```

## <a name="publish-error---live-connected-dataset"></a>Erro de Publicação – Conjunto de dados ligado em direto

Ao voltar a publicar um conjunto de dados ligado em direto com o Analysis Services Connector, o seguinte erro poderá ser apresentado:

:::image type="content" source="media/troubleshoot-xmla-endpoint/couldnt-publish-to-power-bi.png" alt-text="Erro Não foi possível publicar no Power BI.":::

Conforme indicado na mensagem de erro, elimine ou mude o nome do conjunto de dados existente para resolver este problema. Além disso, certifique-se de que volta a publicar todas as aplicações que dependem do relatório. Se for necessário, os utilizadores a jusante também devem ser informados para atualizar quaisquer marcadores com o novo endereço de relatório de modo a garantir que acedem ao relatório mais recente.  

## <a name="workspaceserver-alias"></a>Alias do servidor/área de trabalho

Ao contrário do Azure Analysis Services, os [aliases](/azure/analysis-services/analysis-services-server-alias) do nome de servidor **não são suportados** para áreas de trabalho do Power BI Premium. 

## <a name="dataset-refresh-through-the-xmla-endpoint"></a>Atualização do conjunto de dados através do ponto final XMLA

A data e hora da última atualização é apresentada em vários locais no Power BI, como as colunas Atualizado em relatórios e listas, os detalhes do conjunto de dados, as definições do conjunto de dados e o histórico de atualizações do conjunto de dados. Atualmente, as datas e horas de atualização apresentadas no Power BI **não** incluem operações de atualização efetuadas através do ponto final XMLA com recurso ao TMSL/TOM, SSMS ou ferramentas de terceiros.

## <a name="see-also"></a>Veja também

[Conectividade dos conjuntos de dados com o ponto final XMLA](service-premium-connect-tools.md)  
[Automatizar as tarefas de conjuntos de dados e áreas de trabalho Premium com principais de serviço](service-premium-service-principal.md)  
[Resolução de Problemas de Análise no Excel](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md)  
[Implementação da solução de modelo tabular](/analysis-services/deployment/tabular-model-solution-deployment?view=power-bi-premium-current&preserve-view=true)
