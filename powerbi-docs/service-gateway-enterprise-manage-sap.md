---
title: Faça a gestão da sua origem de dados SAP HANA
description: Como gerir o Gateway de dados no local e as origens de dados que pertencem a esse gateway. Este artigo é específico para SAP HANA.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 01/24/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: e4fabd59396872be9ffa77d8957b06ffcf7eb45f
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54276635"
---
# <a name="manage-your-sap-hana-data-source"></a>Faça a gestão da sua origem de dados SAP HANA
Depois de instalar o Gateway de dados no local, terá de adicionar as origens de dados que podem ser utilizadas com o gateway. Este artigo abordará como trabalhar com gateways e origens de dados. Pode uilizar a origem de dados do SAP HANA para a atualização agendada ou para o DirectQuery.

## <a name="download-and-install-the-gateway"></a>Transferir e instalar o gateway
Pode transferir o gateway a partir do serviço Power BI. Selecione **Transferências** > **Gateway de Dados** ou aceda à [página de transferência do gateway](https://go.microsoft.com/fwlink/?LinkId=698861).

![](media/service-gateway-enterprise-manage-sap/powerbi-download-data-gateway.png)

## <a name="add-a-gateway"></a>Adicionar um gateway
Para adicionar um gateway, basta [transferir](https://go.microsoft.com/fwlink/?LinkId=698861) e instalar o gateway num servidor no ambiente. Depois de instalar o gateway, este será mostrado na lista de gateways em **Gerir gateways**.

> [!NOTE]
> **Gerir gateways** não será apresentado até ser o administrador de, pelo menos, um gateway. Isto pode acontecer ao ser adicionado como um administrador ou ao instalar e configurar um gateway.
> 
> 

## <a name="remove-a-gateway"></a>Remover um gateway
A remoção de um gateway também elimina as origens de dados contidas no mesmo.  Isto também interromperá todos os dashboards e relatórios que dependem dessas origens de dados.

1. Selecione o ícone de engrenagem ![](media/service-gateway-enterprise-manage-sap/pbi_gearicon.png) no canto superior direito > **Gerir gateways**.
2. Gateway > **Remover**
   
   ![](media/service-gateway-enterprise-manage-sap/datasourcesettings7.png)

## <a name="add-a-data-source"></a>Adicionar uma origem de dados
Pode adicionar uma origem de dados ao selecionar um gateway e clicar em **Adicionar origem de dados** ou ir para Gateway > **Adicionar origem de dados**.

![](media/service-gateway-enterprise-manage-sap/datasourcesettings1.png)

Pode então selecionar o **Tipo de Origem de Dados** na lista.

![](media/service-gateway-enterprise-manage-sap/datasourcesettings2-sap.png)

Em seguida, é necessário preencher as informações sobre a origem de dados, que incluem o **Servidor**, **Nome de utilizador** e **Palavra-passe**.

> [!NOTE]
> Todas as consultas à origem de dados serão executadas com estas credenciais. Para obter mais informações, veja o artigo principal sobre o Gateway de dados no local para saber mais sobre como as [credenciais](service-gateway-onprem.md#credentials) são armazenadas.
> 
> 

![](media/service-gateway-enterprise-manage-sap/datasourcesettings3-sap.png)

Pode clicar em **Adicionar** depois preencher tudo.  Pode agora utilizar esta origem de dados para a atualização agendada ou para o DirectQuery num servidor SAP HANA no local. Verá *Ligação efetuada* se tiver êxito.

![](media/service-gateway-enterprise-manage-sap/datasourcesettings4.png)

### <a name="advanced-settings"></a>Definições avançadas
Pode configurar o nível de privacidade para a sua origem de dados. Controla a forma como os dados podem ser combinados. É utilizado apenas para a atualização agendada. Não se aplica ao DirectQuery. [Saiba mais](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)

![](media/service-gateway-enterprise-manage-sap/datasourcesettings9.png)

## <a name="remove-a-data-source"></a>Remover uma origem de dados
A remoção de uma origem de dados interromperá todos os dashboards ou relatórios que dependem da origem de dados em questão.  

Para remover uma Origem de Dados, vá para Origem de Dados > **Remover**.

![](media/service-gateway-enterprise-manage-sap/datasourcesettings6.png)

## <a name="manage-administrators"></a>Gerir administradores
No separador Administradores no gateway, pode adicionar e remover os utilizadores (ou grupos de segurança) que podem administrar o gateway.

![](media/service-gateway-enterprise-manage-sap/datasourcesettings8.png)

## <a name="manage-users"></a>Gerir utilizadores
No separador Utilizadores, da origem de dados, pode adicionar e remover os utilizadores ou grupos de segurança que podem utilizar esta origem de dados.

> [!NOTE]
> A lista de utilizadores controla apenas quem tem permissão para publicar relatórios. Os proprietários de relatório podem criar dashboards ou pacotes de conteúdos e partilhá-los com outros utilizadores.
> 
> 

![](media/service-gateway-enterprise-manage-sap/datasourcesettings5.png)

## <a name="using-the-data-source"></a>Utilizar a origem de dados
Depois de criar a origem de dados, esta ficará disponível para utilização com qualquer uma das ligações do DirectQuery ou através da atualização agendada.

> [!NOTE]
> Os nomes do servidor e da base de dados têm de corresponder entre o Power BI Desktop e a origem de dados do Gateway de dados no local!
> 
> 

A ligação entre o conjunto de dados e a origem de dados no gateway é baseada no nome do servidor e no nome da base de dados. Estes têm de corresponder. Por exemplo, se fornecer um Endereço IP ao nome do servidor, no Power BI Desktop, terá de utilizar o Endereço IP para a origem de dados na configuração do gateway. Se utilizar *SERVIDOR\INSTÂNCIA*, no Power BI Desktop, terá de utilizar o mesmo na origem de dados configurada para o gateway.

Este é o caso do DirectQuery e da atualização agendada.

### <a name="using-the-data-source-with-directquery-connections"></a>Utilizar a origem de dados com ligações do DirectQuery
Terá de se certificar de que os nomes do servidor e da base de dados correspondem entre o Power BI Desktop e a origem de dados configurada para o gateway. Também terá de se certificar de que o utilizador está listado no separador **Utilizadores** da origem de dados para poder publicar conjuntos de dados do DirectQuery. Para o DirectQuery, a seleção ocorre no Power BI Desktop quando importa dados pela primeira vez. [Saiba mais](desktop-use-directquery.md)

Depois de publicar, a partir do Power BI Desktop ou de **Obter Dados**, os seus relatórios devem começar a funcionar. Poderá demorar vários minutos, depois de criar a origem de dados dentro do gateway, para a ligação ser utilizável.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Utilizar a origem de dados com a atualização agendada
Se estiver listado no separador **Utilizadores** da origem de dados configurada no gateway, e o nome do servidor e da base de dados corresponderem, irá ver o gateway como uma opção a utilizar com a atualização agendada.

![](media/service-gateway-enterprise-manage-sap/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>Próximos passos
[Gateway de dados no local](service-gateway-onprem.md)  
[Gateway de dados no local - detalhado](service-gateway-onprem-indepth.md)  
[Resolução de problemas do Gateway de dados no local](service-gateway-onprem-tshoot.md)  
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

