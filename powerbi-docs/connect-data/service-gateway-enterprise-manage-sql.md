---
title: Gerir a origem de dados – SQL
description: Como gerir o gateway de dados no local e as origens de dados que pertencem a esse gateway.
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: 851b7645a9e0b5aa09ba9fff4f71abeb79b67dfc
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85237008"
---
# <a name="manage-your-data-source---sql-server"></a>Gerir a origem de dados – SQL Server

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

Depois de [instalar o gateway de dados no local](/data-integration/gateway/service-gateway-install), pode [adicionar origens de dados](service-gateway-data-sources.md#add-a-data-source) que podem ser utilizadas com o gateway. Este artigo aborda como trabalhar com gateways e origens de dados do SQL Server que são utilizados para uma atualização agendada ou para o DirectQuery.

## <a name="add-a-data-source"></a>Adicionar uma origem de dados

Para obter mais informações sobre como adicionar uma origem de dados, veja [Adicionar uma origem de dados](service-gateway-data-sources.md#add-a-data-source). Em **Tipo de Origem de Dados**, selecione **SQL Server**.

![Selecionar a origem de dados do SQL Server](media/service-gateway-enterprise-manage-sql/datasourcesettings2.png)

> [!NOTE]
> Quando utiliza o DirectQuery, o gateway suporta apenas o **SQL Server 2012 SP1** e versões posteriores.

Em seguida, preencha as informações sobre a origem de dados, que incluem o **Servidor** e a **Base de Dados**. 

Em **Método de Autenticação**, selecione **Windows** ou **Básico**. Selecione **Básico** se quiser utilizar a autenticação do SQL em vez da autenticação do Windows. Em seguida, introduza as credenciais que serão utilizadas para esta origem de dados.

> [!NOTE]
> Todas as consultas à origem de dados serão executadas através destas credenciais, exceto se o SSO (início de sessão único) do Kerberos estiver configurado e ativado para a origem de dados. Com o SSO, os conjuntos de dados de importação utilizam as credenciais armazenadas, mas os conjuntos de dados do DirectQuery utilizam o utilizador atual do Power BI para executar as consultas através de SSO. Para saber mais sobre a forma como as credenciais são armazenadas, veja [Armazenar credenciais encriptadas na cloud](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud). Em alternativa, veja o artigo que descreve como [utilizar o Kerberos para SSO (início de sessão único) a partir do Power BI para origens de dados no local](service-gateway-sso-kerberos.md).

![Preenchimento das definições de origem de dados](media/service-gateway-enterprise-manage-sql/datasourcesettings3.png)

Depois de preencher todos os campos, selecione **Adicionar.** Agora pode utilizar esta origem de dados para a atualização agendada ou para o DirectQuery num SQL Server local. Verá *Ligação Estabelecida com Êxito* se tiver êxito.

![Apresentar o estado da ligação](media/service-gateway-enterprise-manage-sql/datasourcesettings4.png)

### <a name="advanced-settings"></a>Definições avançadas

Opcionalmente, pode configurar o nível de privacidade da sua origem de dados. Esta definição controla a forma como os dados podem ser combinados. É utilizada apenas para a atualização agendada. A definição do nível de privacidade não se aplica ao DirectQuery. Para saber mais sobre os níveis de privacidade da sua origem de dados, veja [Níveis de privacidade (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Definir o nível de privacidade](media/service-gateway-enterprise-manage-sql/datasourcesettings9.png)

## <a name="use-the-data-source"></a>Utilizar a origem de dados

Depois de criar a origem de dados, esta fica disponível para utilização com as ligações do DirectQuery ou através da atualização agendada.

> [!NOTE]
> Os nomes do servidor e da base de dados têm de corresponder entre o Power BI Desktop e a origem de dados no gateway de dados no local.

A ligação entre o conjunto de dados e a origem de dados no gateway baseia-se no nome do servidor e no nome da base de dados. Estes nomes têm de corresponder. Por exemplo, se fornecer um endereço IP ao nome do servidor, no Power BI Desktop, terá de utilizar o endereço IP para a origem de dados na configuração do gateway. Se utilizar *SERVIDOR\INSTÂNCIA* no Power BI Desktop, terá de o utilizar na origem de dados configurada para o gateway.

Este requisito aplica-se ao DirectQuery e à atualização agendada.

### <a name="use-the-data-source-with-directquery-connections"></a>Utilizar a origem de dados com ligações do DirectQuery

Certifique-se de que os nomes do servidor e da base de dados no Power BI Desktop e na origem de dados configurada para o gateway correspondem. Também terá de se certificar de que o utilizador está listado no separador **Utilizadores** da origem de dados para publicar conjuntos de dados do DirectQuery. Para o DirectQuery, a seleção ocorre no Power BI Desktop quando importa dados pela primeira vez. Para obter mais informações sobre como utilizar o DirectQuery, veja [Utilizar o DirectQuery no Power BI Desktop](desktop-use-directquery.md).

Depois de publicar, a partir do Power BI Desktop ou de **Obter Dados**, os seus relatórios devem começar a funcionar. Poderá demorar vários minutos, depois de criar a origem de dados no gateway, para a ligação ser utilizável.

### <a name="use-the-data-source-with-scheduled-refresh"></a>Utilizar a origem de dados com a atualização agendada

Se estiver listado no separador **Utilizadores** da origem de dados configurada no gateway e o nome do servidor e da base de dados corresponderem, verá o gateway como uma opção a utilizar com a atualização agendada.

![Apresentar os utilizadores](media/service-gateway-enterprise-manage-sql/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>Próximas etapas

* [Ligar a dados no local no SQL Server](service-gateway-sql-tutorial.md)
* [Resolução de problemas do gateway de dados no local](/data-integration/gateway/service-gateway-tshoot)
* [Resolver problemas de gateways – Power BI](service-gateway-onprem-tshoot.md)
* [Utilizar o Kerberos para SSO (início de sessão único) a partir do Power BI para origens de dados no local](service-gateway-sso-kerberos.md)

Mais perguntas? Experimente perguntar à [Comunidade do Power BI](https://community.powerbi.com/).
