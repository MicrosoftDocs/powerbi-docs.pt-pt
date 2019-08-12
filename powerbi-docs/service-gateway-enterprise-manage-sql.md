---
title: Gerir a origem de dados – SQL
description: Como gerir o Gateway de dados no local e as origens de dados que pertencem a esse gateway.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 2c21792f97445b336709038f7ec2ec39d041312b
ms.sourcegitcommit: 73228d0a9038b8369369c059ad06168d2c5ff062
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/02/2019
ms.locfileid: "68730057"
---
# <a name="manage-your-data-source---sql-server"></a>Gerir a origem de dados – SQL Server

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Depois de [instalar o gateway de dados no local](/data-integration/gateway/service-gateway-install), poderá [adicionar origens de dados](service-gateway-data-sources.md#add-a-data-source) que podem ser utilizadas com o gateway. Este artigo aborda como trabalhar com gateways e origens de dados do SQL Server que são utilizados para uma atualização agendada ou para o DirectQuery.

## <a name="add-a-data-source"></a>Adicionar uma origem de dados

Para obter informações sobre como adicionar uma origem de dados, veja [Adicionar uma origem de dados](service-gateway-data-sources.md#add-a-data-source).

![Selecionar a origem de dados do SQL Server](media/service-gateway-enterprise-manage-sql/datasourcesettings2.png)

> [!NOTE]
> Quando utiliza o DirectQuery, o gateway suporta apenas o **SQL Server 2012 SP1** e versões posteriores.

Em seguida, é necessário preencher as informações sobre a origem de dados, que incluem o **Servidor** e a **Base de Dados**.  

Também é necessário selecionar um **Método de Autenticação**. Pode ser **Windows** ou **Básico**. Deverá selecionar **Básico** se for utilizar a Autenticação do SQL em vez da Autenticação do Windows. Em seguida, insira as credenciais que serão utilizadas para esta origem de dados.

> [!NOTE]
> Todas as consultas à origem de dados serão executada através destas credenciais, exceto se o Início de Sessão Único (SSO) Kerberos estiver configurado e ativado para a origem de dados. Com o SSO, os conjuntos de dados de importação utilizam as credenciais armazenadas, mas os conjuntos de dados do DirectQuery utilizam o utilizador atual do Power BI para executar as consultas através de SSO. Para saber mais sobre como as credenciais são armazenadas, veja [Storing encrypted credentials in the cloud](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud) (Armazenar credenciais encriptadas na cloud) ou o artigo que descreve como [Utilizar o Kerberos para SSO (início de sessão único) a partir do Power BI para origens de dados no local](service-gateway-sso-kerberos.md).

![Preenchimento das definições de origem de dados](media/service-gateway-enterprise-manage-sql/datasourcesettings3.png)

Selecione **Adicionar** depois de preencher tudo. Agora pode utilizar esta origem de dados para atualização agendada, ou para o DirectQuery, num SQL Server local. Verá *Ligação Efetuada com Êxito* se tiver êxito.

![Apresentar o estado da ligação](media/service-gateway-enterprise-manage-sql/datasourcesettings4.png)

### <a name="advanced-settings"></a>Definições avançadas

Opcionalmente, pode configurar o nível de privacidade da sua origem de dados. Isto controla a forma como os dados podem ser combinados. É utilizado apenas para atualização agendada. Não se aplica ao DirectQuery. Para saber mais sobre os níveis de privacidade da sua origem de dados, veja [Níveis de privacidade (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Definir o nível de privacidade](media/service-gateway-enterprise-manage-sql/datasourcesettings9.png)

## <a name="using-the-data-source"></a>Utilizar a origem de dados

Depois de criar a origem de dados, esta ficará disponível para utilização com qualquer uma das ligações do DirectQuery ou através da atualização agendada.

> [!NOTE]
> Os nomes do servidor e da base de dados têm de corresponder entre o Power BI Desktop e a origem de dados do gateway de dados no local.

A ligação entre o conjunto de dados e a origem de dados no gateway é baseada no nome do servidor e no nome da base de dados. Estes têm de corresponder. Por exemplo, se fornecer um Endereço IP ao nome do servidor, no **Power BI Desktop**, terá de utilizar o Endereço IP para a origem de dados na configuração do gateway. Se utilizar *SERVIDOR\INSTÂNCIA*, no Power BI Desktop, terá de utilizar o mesmo na origem de dados configurada para o gateway.

Este é o caso do DirectQuery e da atualização agendada.

### <a name="using-the-data-source-with-directquery-connections"></a>Utilizar a origem de dados com ligações do DirectQuery

Terá de se certificar de que os nomes do servidor e da base de dados correspondem entre o **Power BI Desktop** e a origem de dados configurada para o gateway. Também terá de se certificar de que o utilizador está listado no separador **Utilizadores** da origem de dados para poder publicar conjuntos de dados do DirectQuery. Para o DirectQuery, a seleção ocorre no Power BI Desktop quando importa dados pela primeira vez. Para obter mais informações sobre como utilizar o DirectQuery, veja [Utilizar o DirectQuery no Power BI Desktop](desktop-use-directquery.md).

Depois de publicar, a partir do Power BI Desktop ou de **Obter Dados**, os seus relatórios devem começar a funcionar. Poderá demorar vários minutos, depois de criar a origem de dados dentro do gateway, para a ligação ser utilizável.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Utilizar a origem de dados com a atualização agendada

Se estiver listado no separador **Utilizadores** da origem de dados configurada no gateway e o nome do servidor e da base de dados corresponderem, verá o gateway como uma opção a utilizar com a atualização agendada.

![Apresentar os utilizadores](media/service-gateway-enterprise-manage-sql/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>Próximos passos

* [Ligar a dados no local no SQL Server](service-gateway-sql-tutorial.md)
* [Resolução de problemas do gateway de dados no local](/data-integration/gateway/service-gateway-tshoot)
* [Resolver problemas de gateways – Power BI](service-gateway-onprem-tshoot.md)
* [Utilizar o Kerberos para SSO (início de sessão único) do Power BI para origens de dados no local](service-gateway-sso-kerberos.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

