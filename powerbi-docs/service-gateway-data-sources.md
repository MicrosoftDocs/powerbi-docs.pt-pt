---
title: Gerir origens de dados
description: Saiba como gerir origens de dados no Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Gateways
ms.openlocfilehash: c46a5c419c242ae25ecca74428362ec27f234afd
ms.sourcegitcommit: 73228d0a9038b8369369c059ad06168d2c5ff062
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/02/2019
ms.locfileid: "68730206"
---
# <a name="manage-data-sources"></a>Gerir origens de dados

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

O Power BI suporta várias origens de dados no local, sendo que cada uma delas tem os seus próprios requisitos. Pode utilizar um gateway para uma única origem de dados ou para múltiplas origens de dados. Neste exemplo, mostramos-lhe como pode adicionar o SQL Server como uma origem de dados. Os passos são semelhantes para outras origens de dados.

A maioria das operações de gestão de origens de dados também pode ser executada com APIs. Para obter mais informações, veja [APIs REST (Gateways)](/rest/api/power-bi/gateways).

## <a name="add-a-data-source"></a>Adicionar uma origem de dados

1. No canto superior direito do serviço Power BI, selecione o ícone de engrenagem ![Ícone de engrenagem de Definições](media/service-gateway-data-sources/icon-gear.png) > **Gerir gateways**.

    ![Gerir gateways](media/service-gateway-data-sources/manage-gateways.png)

2. Selecione um gateway e, em seguida, **Adicionar origem de dados**. Em alternativa, aceda a **Gateways** > **Adicionar origem de dados**.

    ![Adicionar origem de dados](media/service-gateway-data-sources/add-data-source.png)

3. Selecione o **Tipo de Origem de Dados**.

    ![Selecionar SQL Server](media/service-gateway-data-sources/select-sql-server.png)

4. Introduza as informações da origem de dados. Neste exemplo, trata-se de **Servidor**, **Base de dados** e outras informações. 

    ![Definições da origem de dados](media/service-gateway-data-sources/data-source-settings.png)

5. Para o SQL Server, pode selecionar um **Método de Autenticação** do **Windows** ou **Básico** (Autenticação SQL). Se optar por **Básico**, introduza as credenciais da sua origem de dados.

6. Em **Advanced settings** (Definições avançadas), configure opcionalmente o [privacy level](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540) (nível de privacidade) da sua origem de dados (não se aplica ao [DirectQuery](desktop-directquery-about.md)).

    ![Definições avançadas](media/service-gateway-data-sources/advanced-settings.png)

7. Selecione **Adicionar**. Aparece a mensagem *Ligação Efetuada com Êxito* se o processo for bem-sucedido.

    ![Ligação estabelecida com êxito](media/service-gateway-data-sources/connection-successful.png)

Agora, pode utilizar esta origem de dados para incluir dados do SQL Server nos seus dashboards e relatórios do Power BI.

## <a name="remove-a-data-source"></a>Remover uma origem de dados

Pode remover uma origem de dados se já não a utilizar. A remoção de uma origem de dados interrompe todos os dashboards e relatórios que dependem da mesma.

Para remover uma origem de dados, aceda à origem de dados e, em seguida, selecione **Remover**.

![Remover uma origem de dados](media/service-gateway-data-sources/remove-data-source.png)

## <a name="use-the-data-source-for-scheduled-refresh-or-directquery"></a>Utilizar a origem de dados para a atualização agendada ou o DirectQuery

Depois de criar a origem de dados, esta está disponível para utilização com as ligações do DirectQuery ou através da atualização agendada.

> [!NOTE]
>Os nomes do servidor e da base de dados têm de corresponder entre o Power BI Desktop e a origem de dados no gateway de dados no local.

A ligação entre o conjunto de dados e a origem de dados no gateway é baseada no nome do servidor e no nome da base de dados. Estes nomes têm de corresponder. Por exemplo, se fornecer um endereço IP ao nome do servidor, no Power BI Desktop, terá de utilizar o endereço IP para a origem de dados na configuração do gateway. Se utilizar *SERVIDOR\INSTÂNCIA*, no Power BI Desktop, terá de utilizar o mesmo na origem de dados configurada para o gateway.

Se estiver listado no separador **Utilizadores** da origem de dados configurada no gateway e o nome do servidor e da base de dados corresponderem, verá o gateway como uma opção a utilizar com a atualização agendada.

![Ligação do gateway](media/service-gateway-data-sources/gateway-connection.png)

> [!WARNING]
> Se o conjunto de dados contiver múltiplas origens de dados, cada origem de dados terá de ser adicionada ao gateway. Se uma ou mais origens de dados não forem adicionadas ao gateway, não verá o gateway como disponível para a atualização agendada.

### <a name="limitations"></a>Limitações

O OAuth é um esquema de autenticação suportado apenas para conectores personalizados com o gateway de dados no local. Não é possível adicionar outras origens de dados que exigem o OAuth. Se o seu conjunto de dados tiver uma origem de dados que exige o OAuth e a mesma não for um conector personalizado, não poderá utilizar o gateway para a atualização agendada.

## <a name="manage-users"></a>Gerir utilizadores

Depois de adicionar uma origem de dados a um gateway, pode dar aos utilizadores e aos grupos de segurança com o e-mail ativado acesso a origens de dados específicas (não a todo o gateway). A lista de utilizadores da origem de dados controla apenas quem está autorizado a publicar relatórios que incluam dados da origem de dados. Os proprietários de relatórios podem criar dashboards, pacotes de conteúdos e aplicações e, em seguida, partilhar esses itens com outros utilizadores.

Também pode conceder aos utilizadores e grupos de segurança acesso administrativo ao gateway.

### <a name="add-users-to-a-data-source"></a>Adicionar utilizadores a uma origem de dados

1. No canto superior direito do serviço Power BI, selecione o ícone de engrenagem ![Ícone de engrenagem de Definições](media/service-gateway-data-sources/icon-gear.png) > **Gerir gateways**.

2. Selecione a origem de dados à qual quer adicionar utilizadores.

3. Selecione **Utilizadores**e introduza um utilizador da sua organização a quem pretenda conceder acesso à origem de dados selecionada. Por exemplo, no ecrã seguinte irá adicionar a Teresa e o André.

    ![Separador Utilizadores](media/service-gateway-data-sources/users-tab.png)

4. Selecione **Adicionar** e o nome do membro adicionado aparece na caixa.

    ![Adicionar utilizador](media/service-gateway-data-sources/add-user.png)

Lembre-se de que tem de adicionar utilizadores a cada uma das origens de dados às quais quer conceder acesso. Cada origem de dados tem uma lista de utilizadores separada. Adicione utilizadores a cada origem de dados separadamente.

### <a name="remove-users-from-a-data-source"></a>Remover utilizadores de uma origem de dados

No separador **Utilizadores** da origem de dados, pode remover utilizadores e grupos de segurança que utilizam esta origem de dados.

![Remover utilizador](media/service-gateway-data-sources/remove-user.png)

## <a name="store-encrypted-credentials-in-the-cloud"></a>Armazenar credenciais encriptadas na cloud

Ao adicionar uma origem de dados ao gateway, tem de fornecer credenciais para essa origem de dados. Todas as consultas à origem de dados serão executadas com estas credenciais. As credenciais são encriptadas com segurança. Estas utilizam encriptação simétrica, para que não possam ser desencriptadas na cloud antes de serem armazenadas na mesma. As credenciais são enviadas para o computador que executa o gateway no local, onde são desencriptadas quando as origens de dados são acedidas.

## <a name="list-of-available-data-source-types"></a>Relação dos tipos de origens de dados disponíveis

O gateway de dados no local suporta as seguintes origens de dados para o Power BI. Além das origens de no local, as origens protegidas por uma firewall, uma VPN ou uma rede virtual também poderão precisar de um gateway de dados.

| **Origem de dados** | **Em direto/DirectQuery** | **Atualização manual ou agendada (configurada pelo utilizador)** |
| --- | --- | --- |
| Amazon Redshift |Sim |Sim |
| Cubos AtScale |Sim |Sim |
| Azure Active Directory |Não |Sim |
| Azure Analysis Services |Sim |Sim |
| Armazenamento de Blobs do Azure |Não |Sim |
| Azure DevOps Server |Não |Sim |
| Armazenamento de Tabelas do Azure |Não |Sim |
| Conector BI |Sim |Sim |
| Denodo |Sim |Sim |
| Dremio |Sim |Sim |
| EmigoDataSourceConnector |Não |Sim |
| Essbase |Sim |Sim |
| Exasol |Sim |Sim |
| Ficheiro |Não |Sim |
| Pasta |Não |Sim |
| Paxata |Não |Sim |
| IBM DB2 |Sim |Sim |
| Base de Dados IBM Informix |Não |Sim |
| IBM Netezza |Sim |Sim |
| Impala |Sim |Sim |
| ODBC da Jethro |Sim |Sim |
| Kyligence Enterprise |Sim |Sim |
| ODBC da MarkLogic |Sim |Sim |
| Segurança do Microsoft Graph |Não |Sim |
| MySQL |Não |Sim |
| ODBC |Não |Sim |
| OData |Não |Sim |
| OLEDB |Não |Sim |
| Oracle |Sim |Sim |
| PostgreSQL |Não |Sim |
| QubolePresto |Sim |Sim |
| Conector Quick Base |Não |Sim |
| SAP Business Warehouse Message Server |Sim |Sim |
| SAP Business Warehouse Server |Sim |Sim |
| SAP HANA |Sim |Sim |
| SQL Server |Sim |Sim |
| SharePoint |Não |Sim |
| Snowflake |Sim |Sim |
| Spark |Sim |Sim |
| SurveyMonkey |Não |Sim |
| Sybase |Não |Sim |
| TeamDesk.Database |Não |Sim |
| Teradata |Sim |Sim |
| Vertica |Sim |Sim |
| Web |Não |Sim |
| Workforce Dimensions |Não |Sim |

## <a name="next-steps"></a>Próximos passos

* [Gerir a sua origem de dados – Analysis Services](service-gateway-enterprise-manage-ssas.md)
* [Gerir a sua origem de dados – SAP HANA](service-gateway-enterprise-manage-sap.md)
* [Gerir a sua origem de dados – SQL Server](service-gateway-enterprise-manage-sql.md)
* [Gerir a sua origem de dados – Oracle](service-gateway-onprem-manage-oracle.md)
* [Gerir a origem de dados – atualização importada/agendada](service-gateway-enterprise-manage-scheduled-refresh.md)
* [Diretrizes para implementar um gateway de dados](service-gateway-deployment-guidance.md)

Mais perguntas? Experimente perguntar à [Comunidade do Power BI](http://community.powerbi.com/).
