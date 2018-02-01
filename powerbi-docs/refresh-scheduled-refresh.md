---
title: "Configurar a atualização agendada"
description: "Isto inclui os passos para selecionar um gateway e configurar a atualização agendada."
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: 2e0b13b950aed0fbecbc183140f6ec4fc9c44978
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2017
---
# <a name="configuring-scheduled-refresh"></a>Configurar a atualização agendada

>[!NOTE]
>Após dois meses de inatividade, a atualização agendada no conjunto de dados é colocada em pausa. Veja a secção [*Agendar atualização*](#schedule-refresh) mais à frente neste artigo para obter mais informações.
> 
> 

Se o conjunto de dados dá suporte à atualização agendada, utilizando Atualizar Agora e Agendar Atualização, há alguns requisitos e configurações importantes que precisa de saber para que a atualização tenha êxito. Estes são **Ligação do gateway**, **Credenciais da Origem de Dados** e **Agendar Atualização**. Vejamos cada um com atenção.

Isto descreverá as opções disponíveis para o [Power BI Gateway – Personal](personal-gateway.md) e o [gateway de dados no local](service-gateway-onprem.md).

Para aceder ao ecrã da atualização agendada, pode efetuar o seguinte.

1. Selecione as **reticências (...)** junto a um conjunto de dados listado em **Conjuntos de Dados**.
2. Selecione **Agendar Atualização**.
   
    ![](media/refresh-scheduled-refresh/dataset-menu.png)

## <a name="gateway-connection"></a>Ligação do gateway
Aqui verá diferentes opções, dependendo de se tem um gateway pessoal ou empresarial, online e disponível.

Se nenhum gateway estiver disponível, verá as **configurações do Gateway** desativadas. Também verá uma mensagem a indicar como instalar o gateway pessoal.

![](media/refresh-scheduled-refresh/gateway-not-configured.png)

Se tiver um gateway pessoal configurado, este estará disponível para seleção, caso esteja online. Será apresentado offline caso não esteja disponível.

![](media/refresh-scheduled-refresh/gateway-connection.png)

Também poderá selecionar o gateway empresarial, se houver um disponível. Só verá um gateway empresarial disponível se a conta estiver listada no separador Utilizadores da origem de dados configurada para determinado gateway.

## <a name="data-source-credentials"></a>Credenciais da origem de dados
### <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal
Se estiver a utilizar o gateway pessoal para atualizar os dados, será necessário fornecer as credenciais utilizadas para ligar-se à origem de dados de back-end. Se estiver ligado a um pacote de conteúdo a partir de um serviço online, as credenciais introduzidas para ligar-se serão transferidas para a atualização agendada.

![](media/refresh-scheduled-refresh/data-source-credentials-pgw.png)

Só é necessário iniciar sessão nas origens de dados a primeira vez que utilizar a atualização desse conjunto de dados. Uma vez introduzidas, essas credenciais são mantidas com o conjunto de dados.

> [!NOTE]
> Para alguns métodos de autenticação, se a palavra-passe utilizada para iniciar sessão numa origem de dados expirar ou for alterada, também terá de alterá-la na origem de dados em Credenciais da Origem de Dados.
> 
> 

Quando ocorre algum erro, o problema geralmente tem algo a ver com o gateway estar offline porque não foi possível iniciar sessão no Windows e iniciar o serviço ou o Power BI não conseguiu ligar-se às origens de dados para consultar dados atualizados. Se a atualização falhar, verifique as configurações do conjunto de dados. Se o serviço de gateway estiver offline, verá o erro no Estado do Gateway. Se o Power BI não conseguir iniciar sessão nas origens de dados, será apresentado um erro em Credenciais da Origem de Dados.

### <a name="on-premises-data-gateway"></a>Gateway de dados local
Se estiver a utilizar o gateway de dados no local para atualizar os dados, não será necessário fornecer credenciais, uma vez que são definidas para a origem de dados pelo administrador do gateway.

![](media/refresh-scheduled-refresh/data-source-credentials-egw.png)

> [!NOTE]
> Ao ligar ao SharePoint no local para a atualização de dados, o Power BI suporta apenas os mecanismos de autenticação *Anónimo*, *Básico* e *Windows (NTLM/Kerberos)*. O Power BI não suporta *ADFS* nem nenhum mecanismo *Autenticação Baseada em Formulários* de atualização de dados de origens de dados do SharePoint no local.
> 
> 

## <a name="schedule-refresh"></a>Agendar atualização
A secção sobre a atualização agendada é o local no qual define a frequência e o intervalo de tempo para atualizar o conjunto de dados. Algumas origens de dados não exigem a presença de um gateway para que estejam disponíveis para configuração. Outras exigirão um gateway.

Tem de definir o controlo de deslize **Manter os dados atualizados** como **Sim** para configurar as definições.

> [!NOTE]
> Os serviço Power BI inicia a atualização dos dados dentro de **15 minutos** após a hora de atualização agendada.
> 
> 

![](media/refresh-scheduled-refresh/scheduled-refresh.png)

> [!NOTE]
> Após dois meses de inatividade, a atualização agendada no conjunto de dados é colocada em pausa. Um conjunto de dados é considerado inativo quando nenhum utilizador tiver visitado qualquer dashboard ou relatório incorporado no conjunto de dados. Nessa altura, é enviado um e-mail ao proprietário do conjunto de dados a indicar que a atualização agendada está em pausa e o agendamento de atualização do conjunto de dados é apresentado como **desativado**. Para retomar a atualização agendada, basta visitar novamente qualquer dashboard ou relatório incorporado no conjunto de dados.
> 
> 

## <a name="whats-supported"></a>O que é suportado?
Alguns conjuntos de dados são suportados em gateways diferentes para a atualização agendada. Aqui está uma referência para entender o que está disponível.

### <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal
**Power BI Desktop**

* Todas as origens de dados online mostradas no Editor de Consultas e em Obter Dados no Power BI Desktop.
* Todas as origens de dados locais mostradas no Editor de Consultas e em Obter Dados no Power BI Desktop, exceto o ficheiro do Hadoop (HDFS) e o Microsoft Exchange.

**Excel**

> [!NOTE]
> No Excel 2016 e posterior, o Power Query é agora listado na secção Dados do friso, em Obter e Transformar dados.
> 
> 

* Todas as origens de dados online apresentadas no Power Query.
* Todas as origens de dados locais apresentadas no Power Query, exceto o ficheiro do Hadoop (HDFS) e o Microsoft Exchange.
* Todas as origens de dados online mostradas no Power Pivot.\*
* Todas as origens de dados locais apresentadas no Power Pivot, exceto o ficheiro do Hadoop (HDFS) e o Microsoft Exchange.

<!-- Refresh Data sources-->
[!INCLUDE [refresh-datasources](./includes/refresh-datasources.md)]

## <a name="troubleshooting"></a>Resolução de problemas
Por vezes, atualizar os dados pode não correr como esperado. Normalmente, este problema está ligado a um gateway. Veja os artigos de resolução de problemas de gateways para ferramentas e problemas conhecidos.

[Resolução de problemas do gateway de dados no local](service-gateway-onprem-tshoot.md)

[Resolver problemas do Power BI Gateway - Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)

## <a name="next-steps"></a>Próximos passos
[Atualização de dados no Power BI](refresh-data.md)  
[Power BI Gateway - Personal](personal-gateway.md)  
[Gateway de dados no local](service-gateway-onprem.md)  
[Resolução de problemas do gateway de dados no local](service-gateway-onprem-tshoot.md)  
[Resolver problemas do Power BI Gateway - Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
