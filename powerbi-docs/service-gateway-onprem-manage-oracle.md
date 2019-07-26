---
title: Gerir a origem de dados – Oracle
description: Como gerir o gateway de dados no local e as origens de dados que pertencem a esse gateway.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: af3ebd421a82448ce8a3f13661801ffc1d0051e0
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271498"
---
# <a name="manage-your-data-source---oracle"></a>Gerir a origem de dados – Oracle

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Depois de [instalar o gateway de dados no local](/data-integration/gateway/service-gateway-install), terá de [adicionar origens de dados](service-gateway-data-sources.md#add-a-data-source) que podem ser utilizadas com o gateway. Este artigo aborda como trabalhar com gateways e Origens de dados do Oracle para uma atualização agendada ou para o DirectQuery.

## <a name="installing-the-oracle-client"></a>Instalar o cliente Oracle

Para o gateway conseguir ligar ao seu servidor Oracle, o Oracle Data Provider para .NET (ODP.NET) tem de estar instalado e configurado. Este processo faz parte do Oracle Data Access Components (ODAC).

Para as versões de **32 bits** do Power BI Desktop, utilize a seguinte ligação para transferir e instalar o cliente Oracle de **32 bits**:

* [Oracle Data Access Components (ODAC) de 32 bits com o Oracle Developer Tools for Visual Studio (12.1.0.2.4)](http://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)

Para as versões de **64 bits** do Power BI Desktop ou para o gateway de dados no local, utilize a seguinte ligação para transferir e instalar o cliente Oracle de **64 bits**:

* [ODAC 12.2c Release 1 (12.2.0.1.0) de 64 bits para o Windows x64](http://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)

Após a instalação, terá de configurar o ficheiro tnsnames.ora com as informações adequadas para a base de dados. O Power BI Desktop e o gateway sairão do net_service_name definido no ficheiro tnsnames.ora. Se não estiver configurado, não conseguirá estabelecer ligação. O caminho predefinido para tnsnames.ora é `[Oracle Home Directory]\Network\Admin\tnsnames.ora`. Para obter mais informações sobre como configurar ficheiros tnsnames.ora, veja [Oracle: Local Naming Parameters (tnsnames.ora)](https://docs.oracle.com/cd/B28359_01/network.111/b28317/tnsnames.htm) (Parâmetros de Nomenclatura Locais (tnsnames.ora)).

### <a name="example-tnsnamesora-file-entry"></a>Entrada do ficheiro tnsnames.ora de exemplo

O formato básico de uma entrada no ficheiro tnsname.ora é o seguinte.

```
net_service_name=
 (DESCRIPTION=
   (ADDRESS=(protocol_address_information))
   (CONNECT_DATA=
     (SERVICE_NAME=service_name)))
```

Segue-se um exemplo do servidor e das informações da porta preenchidas.

```
CONTOSO =
  (DESCRIPTION =
    (ADDRESS = (PROTOCOL = TCP)(HOST = oracleserver.contoso.com)(PORT = 1521))
    (CONNECT_DATA =
      (SERVER = DEDICATED)
      (SERVICE_NAME = CONTOSO)
    )
  )
```

## <a name="add-a-data-source"></a>Adicionar uma origem de dados

Para obter informações sobre como adicionar uma origem de dados, veja [Adicionar uma origem de dados](service-gateway-data-sources.md#add-a-data-source). Selecione Oracle como o **Tipo de Origem de Dados**.

![Adicionar a origem de dados Oracle](media/service-gateway-onprem-manage-oracle/data-source-oracle.png)

Após selecionar o tipo de origem de dados Oracle, irá preencher as informações **Servidor**, **Base de dados** referentes à origem de dados.  

Também é necessário selecionar um **Método de Autenticação**.  Pode ser **Windows** ou **Básico**.  É recomendado selecionar **Básico** se quiser utilizar uma conta criada no Oracle em vez da Autenticação do Windows. Em seguida, insira as credenciais que serão utilizadas para esta origem de dados.

> [!NOTE]
> Todas as consultas à origem de dados serão executadas com estas credenciais. Para saber mais sobre a forma como as credenciais são armazenadas, veja [Armazenar credenciais encriptadas na cloud](service-gateway-data-sources.md#storing-encrypted-credentials-in-the-cloud).

![Preenchimento das definições de origem de dados](media/service-gateway-onprem-manage-oracle/data-source-oracle2.png)

Selecione **Adicionar** depois de preencher tudo. Agora, pode utilizar esta origem de dados para atualização agendada, ou DirectQuery, num servidor Oracle que esteja no local. Verá *Ligação Estabelecida com Êxito* se tiver êxito.

![Apresentar o estado da ligação](media/service-gateway-onprem-manage-oracle/datasourcesettings4.png)

### <a name="advanced-settings"></a>Definições avançadas

Opcionalmente, pode configurar o nível de privacidade da sua origem de dados. Isto controla a forma como os dados podem ser combinados. É utilizado apenas para atualização agendada. Não se aplica ao DirectQuery. Para saber mais sobre os níveis de privacidade da sua origem de dados, veja [Níveis de privacidade (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Definir o nível de privacidade](media/service-gateway-onprem-manage-oracle/datasourcesettings9.png)

## <a name="using-the-data-source"></a>Utilizar a origem de dados

Depois de criar a origem de dados, esta ficará disponível para utilização com qualquer uma das ligações do DirectQuery ou através da atualização agendada.

> [!WARNING]
> Os nomes do servidor e da base de dados têm de corresponder entre o Power BI Desktop e a origem de dados do gateway de dados no local.

A ligação entre o conjunto de dados e a origem de dados no gateway é baseada no nome do servidor e no nome da base de dados. Estes têm de corresponder. Por exemplo, se fornecer um Endereço IP ao nome do servidor, no Power BI Desktop, terá de utilizar o Endereço IP para a origem de dados na configuração do gateway. Este nome também tem de corresponder ao alias definido no ficheiro tnsnames.ora. Para obter mais informações sobre o ficheiro tnsnames.ora, veja [Instalar o Cliente Oracle](#installing-the-oracle-client).

Este é o caso do DirectQuery e da atualização agendada.

### <a name="using-the-data-source-with-directquery-connections"></a>Utilizar a origem de dados com ligações do DirectQuery

Terá de se certificar de que os nomes do servidor e da base de dados no Power BI Desktop e na origem de dados configurada para o gateway correspondem. Também terá de se certificar de que o utilizador está listado no separador **Utilizadores** da origem de dados para poder publicar conjuntos de dados do DirectQuery. Para o DirectQuery, a seleção ocorre no Power BI Desktop quando importa dados pela primeira vez. Para obter mais informações sobre como utilizar o DirectQuery, veja [Utilizar o DirectQuery no Power BI Desktop](desktop-use-directquery.md).

Depois de publicar, a partir do Power BI Desktop ou de **Obter Dados**, os seus relatórios devem começar a funcionar. Poderá demorar vários minutos, depois de criar a origem de dados dentro do gateway, para a ligação ser utilizável.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Utilizar a origem de dados com a atualização agendada

Se estiver listado no separador **Utilizadores** da origem de dados configurada no gateway e o nome do servidor e da base de dados corresponderem, irá ver o gateway como uma opção a utilizar com a atualização agendada.

![Apresentar os utilizadores](media/service-gateway-onprem-manage-oracle/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="troubleshooting"></a>Resolução de problemas

Pode encontrar vários erros do Oracle quando a sintaxe de nomenclatura estiver incorreta ou não estiver configurada corretamente.

* ORA-12154: TNS: não foi possível resolver o identificador de ligação especificado  
* ORA-12514: TNS: o serviço de escuta não conhece atualmente o serviço pedido no descritor de ligação  
* ORA-12541: TNS: nenhum serviço de escuta  
* ORA-12170: TNS: tempo limite da ligação excedido  
* ORA-12504: TNS: o serviço de escuta não foi atribuído a SERVICE_NAME em CONNECT_DATA  

Estes erros podem ocorrer se o cliente Oracle não estiver instalado ou se não estiver configurado corretamente. Se estiver instalado, certifique-se de que o ficheiro tnsnames.ora está configurado corretamente e está a utilizar o net_service_name adequado. Também terá de certificar-se de que o net_service_name é o mesmo entre o computador que está a utilizar o Power BI Desktop e o computador que está a executar o gateway. Para obter mais informações, consulte [Instalar o Cliente Oracle](#installing-the-oracle-client).

> [!NOTE]
> Pode também estar a ocorrer um problema de compatibilidade entre a versão do servidor Oracle e a versão do cliente Oracle. Normalmente, estes têm de corresponder.

Para obter informações adicionais de resolução de problemas relacionadas com o gateway, veja [Resolução de problemas do gateway de dados no local](/data-integration/gateway/service-gateway-tshoot).

## <a name="next-steps"></a>Próximos passos

* [Resolver problemas de gateways – Power BI](service-gateway-onprem-tshoot.md)
* [Power BI Premium](service-premium.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

