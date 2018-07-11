---
title: Gerir a origem de dados – Atualização Importada/Agendada
description: Como gerir o Gateway de dados no local e as origens de dados que pertencem a esse gateway. Este artigo é específico para origens de dados que podem ser utilizadas com a atualização importada/agendada.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 17c608b017123b5ae7111ef6d97703cdbc30940d
ms.sourcegitcommit: 001ea0ef95fdd4382602bfdae74c686de7dc3bd8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38937333"
---
# <a name="manage-your-data-source---importscheduled-refresh"></a>Gerir a origem de dados – Atualização Importada/Agendada
Depois de instalar o Gateway de dados no local, terá de adicionar as origens de dados que podem ser utilizadas com o gateway. Este artigo analisará como trabalhar com gateways e origens de dados utilizadas para atualização agendada em vez do DirectQuery ou de ligações dinâmicas.

## <a name="download-and-install-the-gateway"></a>Transferir e instalar o gateway
Pode transferir o gateway a partir do serviço Power BI. Selecione **Transferências** > **Gateway de Dados** ou aceda à [página de transferência do gateway](https://go.microsoft.com/fwlink/?LinkId=698861).

![](media/service-gateway-enterprise-manage-scheduled-refresh/powerbi-download-data-gateway.png)

## <a name="add-a-gateway"></a>Adicionar um gateway
Para adicionar um gateway, basta [transferir](https://go.microsoft.com/fwlink/?LinkId=698863) e instalar o gateway empresarial num servidor do ambiente. Depois de instalar o gateway, este será apresentado na lista de gateways em **Gerir gateways**.

> [!NOTE]
> **Gerir gateways** não será apresentado até ser o administrador de, pelo menos, um gateway. Isto pode acontecer ao ser adicionado como um administrador ou ao instalar e configurar um gateway.
> 
> 

## <a name="remove-a-gateway"></a>Remover um gateway
A remoção de um gateway também elimina as origens de dados contidas no mesmo.  Isto também interromperá todos os dashboards e relatórios que dependem dessas origens de dados.

1. Selecione o ícone de engrenagem ![](media/service-gateway-enterprise-manage-scheduled-refresh/pbi_gearicon.png) no canto superior direito > **Gerir gateways**.
2. Gateway > **Remover**
   
   ![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings7.png)

## <a name="add-a-data-source"></a>Adicionar uma origem de dados
Pode adicionar uma origem de dados ao selecionar um gateway e clicar em **Adicionar origem de dados** ou ir para Gateway > **Adicionar origem de dados**.

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings1.png)

Pode selecionar o **Tipo de Origem de Dados** na lista. Todas as origens de dados relacionadas podem ser utilizadas para atualização agendada com o gateway empresarial. O Analysis Services, o SQL Server e o SAP HANA podem ser utilizados para atualização agendada ou DirectQuery/ligações dinâmicas.

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings2.png)

Em seguida, é necessário preencher as informações sobre a origem de dados, que inclui as informações de origem e as credenciais utilizadas para aceder à origem de dados.

> [!NOTE]
> Todas as consultas à origem de dados serão executadas com estas credenciais. Para obter mais informações, veja o artigo principal sobre o Gateway de dados no local para saber mais sobre como as [credenciais](service-gateway-onprem.md#credentials) são armazenadas.
> 
> 

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings3-oracle.png)

Pode clicar em **Adicionar** depois preencher tudo.  Pode agora utilizar esta origem de dados para atualização agendada com os seus dados no local. Verá *Ligação Com Êxito* se tiver êxito.

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings4.png)

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

### <a name="advanced-settings"></a>Definições avançadas
Pode configurar o nível de privacidade para a sua origem de dados. Controla a forma como os dados podem ser combinados. É utilizado apenas para atualização agendada. [Saiba mais](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings9.png)

## <a name="remove-a-data-source"></a>Remover uma origem de dados
A remoção de uma origem de dados interromperá todos os dashboards ou relatórios que dependem da origem de dados em questão.  

Para remover uma Origem de Dados, vá para Origem de Dados > **Remover**.

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings6.png)

## <a name="manage-administrators"></a>Gerir administradores
No separador Administradores, do gateway, pode adicionar e remover os utilizadores que podem administrar o gateway. Neste momento, apenas pode adicionar utilizadores. Não é possível adicionar grupos de segurança.

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings8.png)

## <a name="manage-users"></a>Gerir utilizadores
No separador Utilizadores, da origem de dados, pode adicionar e remover os utilizadores ou grupos de segurança que podem utilizar esta origem de dados.

> [!NOTE]
> A lista de utilizadores controla apenas quem tem permissão para publicar relatórios. Os proprietários do relatório podem criar dashboards ou pacotes de conteúdos e partilhá-los com outros utilizadores.
> 
> 

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings5.png)

## <a name="using-the-data-source-for-scheduled-refresh"></a>Utilizar a origem de dados para a atualização agendada
Depois de criar a origem de dados, esta ficará disponível para utilização com qualquer uma das ligações do DirectQuery ou através da atualização agendada.

> [!NOTE]
> Os nomes do servidor e da base de dados têm de corresponder entre o Power BI Desktop e a origem de dados do Gateway de dados no local!
> 
> 

A ligação entre o conjunto de dados e a origem de dados no gateway é baseada no nome do servidor e no nome da base de dados. Estes têm de corresponder. Por exemplo, se fornecer um Endereço IP ao nome do servidor, no Power BI Desktop, terá de utilizar o Endereço IP para a origem de dados na configuração do gateway. Se utilizar *SERVIDOR\INSTÂNCIA*, no Power BI Desktop, terá de utilizar o mesmo na origem de dados configurada para o gateway.

Se estiver listado no separador **Utilizadores** da origem de dados configurada no gateway, e o nome do servidor e da base de dados corresponderem, irá ver o gateway como uma opção a utilizar com a atualização agendada.

![](media/service-gateway-enterprise-manage-scheduled-refresh/powerbi-gateway-enterprise-schedule-refresh.png)

> [!WARNING]
> Se o conjunto de dados contém várias origens de dados, cada origem de dados tem de ser adicionada ao gateway. Se uma ou mais origens de dados não são adicionadas no gateway, não verá o gateway como disponível para a atualização agendada.
> 
> 

## <a name="limitations"></a>Limitações
* O OAuth não é um esquema de autenticação suportado com o Gateway de dados no local. Não é possível adicionar origens de dados que necessitam o OAuth. Se o conjunto de dados tem uma origem de dados que requere OAuth, não poderá utilizar o gateway para a atualização agendada.

## <a name="next-steps"></a>Próximos passos
[Gateway de dados no local](service-gateway-onprem.md)  
[Gateway de dados no local - detalhado](service-gateway-onprem-indepth.md)  
[Resolução de problemas do Gateway de dados no local](service-gateway-onprem-tshoot.md)  
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

