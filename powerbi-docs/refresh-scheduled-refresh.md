---
title: Configurar a atualização agendada
description: Isto inclui os passos para selecionar um gateway e configurar a atualização agendada.
author: mgblythe
manager: kfile
ms.reviewer: kayu''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/06/2019
ms.author: mblythe
LocalizationGroup: Data refresh
ms.openlocfilehash: 9f1289b5fce74c60e5b3802054cef008dd33ada2
ms.sourcegitcommit: 2aa83bd53faad6fb02eb059188ae623e26503b2a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/29/2019
ms.locfileid: "73021561"
---
# <a name="configure-scheduled-refresh"></a>Configurar a atualização agendada

>[!NOTE]
>Após dois meses de inatividade, a atualização agendada no conjunto de dados é colocada em pausa. Para obter mais informações, veja [*Atualização agendada*](#scheduled-refresh) mais à frente neste artigo.
>
>

Se o seu conjunto de dados suportar atualizações agendadas através das opções **Atualizar Agora** e **Agendar Atualização**, existem alguns requisitos e definições importantes para que a atualização seja bem-sucedida. Tratam-se de **Ligação do gateway**, **Credenciais da origem de dados** e **Atualização agendada**. Vejamos cada um com atenção.

Este artigo descreve as opções disponíveis para o [Gateway de dados no local (modo pessoal)](service-gateway-personal-mode.md) e o[Gateway de dados no local](service-gateway-onprem.md).

Para aceder ao ecrã **Atualização agendada**, pode fazer o seguinte:

1. Selecione **Mais opções** (...) junto a um conjunto de dados listado em **Conjuntos de Dados**.
2. Selecione **Agendar Atualização**.

    ![Agendar Atualização](media/refresh-scheduled-refresh/dataset-menu.png)

## <a name="gateway-connection"></a>Ligação do gateway
Aqui verá diferentes opções, dependendo de se tem um gateway pessoal ou empresarial, online e disponível.

Se nenhum gateway estiver disponível, a opção **Ligação do gateway** estará desativada. Também verá uma mensagem a indicar como instalar o gateway pessoal.

![Gateway não configurado](media/refresh-scheduled-refresh/gateway-not-configured.png)

Se tiver um gateway pessoal configurado, este estará disponível para seleção, caso esteja online. Será apresentado offline caso não esteja disponível.

![Ligação do gateway](media/refresh-scheduled-refresh/gateway-connection.png)

Também poderá selecionar o gateway empresarial, se houver um disponível. Só verá um gateway empresarial disponível se a sua conta estiver listada no separador **Utilizadores** da origem de dados configurada para determinado gateway.

## <a name="data-source-credentials"></a>Credenciais de origem de dados
### <a name="power-bi-gateway---personal"></a>Gateway do Power BI - Pessoal
Se estiver a utilizar o gateway pessoal para atualizar os dados, terá de fornecer as credenciais para ligar-se à origem de dados de back-end. Se estiver ligado a um pacote de conteúdos de um serviço online, as credenciais introduzidas para ligar-se serão transferidas para a atualização agendada.

![Credenciais de origem de dados](media/refresh-scheduled-refresh/data-source-credentials-pgw.png)

Só terá de iniciar sessão numa origem de dados na primeira vez que utilizar a atualização nesse conjunto de dados. Uma vez introduzidas, essas credenciais são mantidas com o conjunto de dados.

> [!NOTE]
> Para alguns métodos de autenticação, se a palavra-passe utilizada para iniciar sessão numa origem de dados expirar ou for alterada, também terá de alterá-la para a origem de dados em **Credenciais de origem de dados**.
>
>

Quando ocorre algum erro, o problema geralmente tem algo a ver com o gateway estar offline porque não foi possível iniciar sessão no Windows e iniciar o serviço ou o Power BI não conseguiu ligar-se às origens de dados para consultar dados atualizados. Se a atualização falhar, verifique as configurações do conjunto de dados. Se o serviço de gateway estiver offline, verá o erro em **Estado**. Se o Power BI não conseguir iniciar sessão nas origens de dados, será apresentado um erro em Credenciais da Origem de Dados.

### <a name="on-premises-data-gateway"></a>Gateway de dados no local
Se estiver a utilizar o Gateway de dados no local para atualizar os dados, não será necessário fornecer credenciais, uma vez que são definidas para a origem de dados pelo administrador do gateway.

![Comando Agendar Atualização](media/refresh-scheduled-refresh/data-source-credentials-egw.png)

> [!NOTE]
> Ao ligar ao SharePoint no local para a atualização de dados, o Power BI suporta apenas os mecanismos de autenticação *Anónimo*, *Básico* e *Windows (NTLM/Kerberos)*. O Power BI não suporta *ADFS* nem nenhum mecanismo *Autenticação Baseada em Formulários* de atualização de dados de origens de dados do SharePoint no local.
>
>

## <a name="scheduled-refresh"></a>Atualização agendada
A secção **Atualização agendada** é o local onde define a frequência e os intervalos de tempo para atualizar o conjunto de dados. Algumas origens de dados não precisam que um gateway seja configurável para a atualização, mas outras origens de dados precisam de um gateway.

Defina o controlo de deslize **Manter os dados atualizados** para **Ativado** para configurar as definições.

> [!NOTE]
> Os serviço Power BI inicia a atualização dos dados dentro de **15 minutos** após a hora de atualização agendada.
>
>

![Caixa de diálogo Atualização agendada](media/refresh-scheduled-refresh/scheduled-refresh.png)

> [!NOTE]
> Após dois meses de inatividade, a atualização agendada no conjunto de dados é colocada em pausa. Um conjunto de dados é considerado inativo quando nenhum utilizador tiver visitado qualquer dashboard ou relatório incorporado no conjunto de dados. Nessa altura, é enviado um e-mail ao proprietário do conjunto de dados a indicar que a atualização agendada está em pausa e o agendamento de atualização do conjunto de dados é apresentado como **desativado**. Para retomar a atualização agendada, basta visitar novamente qualquer dashboard ou relatório incorporado no conjunto de dados.
>
>

## <a name="whats-supported"></a>O que é suportado?
Alguns conjuntos de dados são suportados em gateways diferentes para a atualização agendada. Aqui está uma referência para entender o que está disponível.

### <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal
**Power BI Desktop**

* Todas as origens de dados online apresentadas no Editor de Consultas e em **Obter Dados** no Power BI Desktop.
* Todas as origens de dados locais apresentadas no Editor de Consultas e em **Obter Dados** no Power BI Desktop, exceto o ficheiro do Hadoop (HDFS) e o Microsoft Exchange.

**Excel**

> [!NOTE]
> No Excel 2016 e posterior, o Power Query é agora listado na secção **Dados** do friso, em **Obter e Transformar Dados**.
>
>

* Todas as origens de dados online mostradas no Power Query.
* Todas as origens de dados locais apresentadas no Power Query, exceto o ficheiro do Hadoop (HDFS) e o Microsoft Exchange.
* Todas as origens de dados online apresentadas no Power Pivot.
* Todas as origens de dados locais apresentadas no Power Pivot, exceto o ficheiro do Hadoop (HDFS) e o Microsoft Exchange.

<!-- Refresh Data sources-->
[!INCLUDE [refresh-datasources](./includes/refresh-datasources.md)]

## <a name="troubleshooting"></a>Resolução de problemas
Por vezes, atualizar os dados pode não correr como esperado. Normalmente, este problema está ligado a um gateway. Veja os artigos de resolução de problemas de gateways para ferramentas e problemas conhecidos.

- [Resolução de problemas do Gateway de dados no local](service-gateway-onprem-tshoot.md)
- [Resolver problemas do Power BI Gateway - Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)

## <a name="next-steps"></a>Próximos passos
- [Atualização de dados no Power BI](refresh-data.md)  
- [Power BI Gateway - Personal](service-gateway-personal-mode.md)  
- [Gateway de dados no local (modo pessoal)](service-gateway-onprem.md)  
- [Resolução de problemas do Gateway de dados no local](service-gateway-onprem-tshoot.md)  
- [Resolver problemas do Power BI Gateway - Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

