---
title: Power BI Gateway - Personal
description: Power BI Gateway - Personal
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: fc062387282bf01fd06a9e3d2420ac748c0bc592
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2017
---
# <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal
> [!NOTE]
> Há uma nova versão do gateway pessoal para Power BI, com o nome de **gateway de dados no local (modo pessoal)**. O artigo seguinte descreve a versão anterior do gateway pessoal, com o nome de **Power BI Gateway - Personal**, que será descontinuado e deixará de funcionar após 31 de julho de 2017. Para obter informações sobre a nova versão do gateway pessoal, incluindo como instalar a nova versão, consulte o artigo [**Gateway de dados no local (modo pessoal)**](service-gateway-personal-mode.md).
> 
> 

O **Power BI Gateway - Personal** atua como uma ponte, fornecendo uma transferência de dados rápida e segura entre o serviço Power BI e as origens de dados locais que suportam a [atualização](refresh-data.md). Este artigo destina-se a oferecer uma compreensão aprofundada de como o gateway funciona e se precisa de um. Também fizemos este [vídeo bastante útil](https://www.youtube.com/watch?v=de58vROLqZI) sobre o gateway pessoal. 

Ele é instalado e executado como um serviço no seu computador. Como serviço, ele é executado com uma conta do Windows especificada durante a configuração. Em alguns casos, o Gateway é executado como uma aplicação. Veremos mais detalhes posteriormente.

Quando o Power BI atualiza os dados de uma origem de dados local, o gateway garante que a sua conta do Power BI tem as permissões certas para se ligar e consultar os dados da origem.

A transferência de dados entre o Power BI e o gateway é protegida pelo [Azure Service Bus](http://azure.microsoft.com/documentation/services/service-bus/). O Service Bus cria um canal seguro entre o serviço Power BI e o seu computador. Como o gateway oferece esta ligação segura, geralmente, não é preciso abrir uma porta no firewall.

Antes de entrarmos em detalhes sobre o gateway, vamos ver alguns termos utilizados no Power BI:

Um *conjunto de dados* são dados carregados no serviço Power BI de uma origem de dados online ou local. Crie um conjunto de dados quando utilizar a funcionalidade Obter Dados para se ligar e carregar dados. Os conjuntos de dados aparecem no painel A Minha Área de Trabalho da Área de Trabalho do Power BI no seu navegador. Quando cria relatórios e afixa mosaicos aos seus dashboards, verá os dados dos seus conjuntos de dados.

Uma *origem de dados* é o local de onde são provenientes os dados carregados para um conjunto de dados. Pode ser qualquer coisa: uma base de dados, uma folha de cálculo do Excel, um serviço Web, etc. Com os livros do Excel, pode criar uma folha de cálculo simples com linhas de dados, o que é considerado uma origem de dados. Também pode utilizar o Power Query ou o Power Pivot no Excel para ligar e consultar dados de origens de dados online e locais, tudo no mesmo livro. Com o Power BI Desktop, pode utilizar a funcionalidade Obter Dados para ligar e consultar dados de origens de dados online e locais.

O gateway pessoal é instalado através do gateway de dados no local. Pode transferi-lo na [página do Power BI Gateway](https://powerbi.microsoft.com/gateway/).

## <a name="do-i-need-a-gateway"></a>Preciso de um gateway?
Antes de instalar um gateway, é importante saber se realmente precisa de um. Realmente depende das suas origens de dados:

### <a name="on-premises-data-sources"></a>Origens de dados locais
*É preciso* um gateway pessoal para atualizar os conjuntos de dados que obtêm dados de uma origem de dados local suportada na sua organização.

Com um gateway, as funcionalidades ATUALIZAR AGORA e AGENDAR ATUALIZAÇÃO são suportadas para conjuntos de dados carregados de:

* Livros do Microsoft Excel 2013 (ou posterior) em que o Power Query ou o Power Pivot serve para ligar e consultar dados de uma origem de dados online ou local com suporte. Todas as origens de dados locais mostradas em Obter Dados Externos no Power Query ou no Power Pivot suportam a atualização, exceto o ficheiro do Hadoop (HDFS) e o Microsoft Exchange.
* Ficheiros do Microsoft Power BI Desktop, nos quais a funcionalidade Obter Dados é utilizada para ligar e consultar dados de uma origem de dados local suportada. Todas as origens de dados locais mostradas em Obter Dados suportam a atualização, exceto o ficheiro do Hadoop (HDFS) e o Microsoft Exchange.

### <a name="online-data-sources"></a>Origens de dados online
Um gateway *só é necessário* se estiver a utilizar a função [**Web.Page**](https://msdn.microsoft.com/library/mt260924.aspx). Noutros casos, *não* é necessário um gateway para atualizar os conjuntos de dados que obtêm dados apenas de uma origem de dados online.

> [!NOTE]
> Se estiver a utilizar a função [**Web.Page**](https://msdn.microsoft.com/library/mt260924.aspx), só precisa de um gateway se tiver republicado o conjunto de dados ou o seu relatório após 18 de novembro de 2016.
> 
> 

As funcionalidades ATUALIZAR AGORA e AGENDAR ATUALIZAÇÃO são suportadas sem um gateway para conjuntos de dados carregados de:

* Pacotes de conteúdos de origens de dados online (pacotes de conteúdos\\serviços). Por predefinição, os conjuntos de dados de pacotes de conteúdos são atualizados automaticamente uma vez por dia, mas também pode atualizar manualmente ou configurar um agendamento de atualização.
* Os livros do Microsoft Excel 2013 (ou posterior) em que o Power Query ou o Power Pivot serve para ligar e consultar dados de uma origem de dados online.
* Os ficheiros do Microsoft Power BI Desktop, nos quais a funcionalidade Obter Dados é utilizada para ligar e consultar dados de uma origem de dados online.

**Pergunta:** E se o meu livro do Excel ou ficheiro do Power BI Desktop obtiver dados de origens de dados online e locais?

**Resposta:** *É* preciso um gateway. Irá precisar de instalar e configurar um gateway para atualizar os dados das origens de dados locais.

**Pergunta:** E se o meu livro do Excel tiver apenas linhas de dados em que escrevi?**

**Resposta:** *Não é* preciso um gateway. Irá precisar de instalar e configurar um gateway apenas se o seu livro utilizar o Power Query ou o Power Pivot para consultar e carregar dados no modelo de dados através de uma origem de dados local suportada

## <a name="setting-up-a-gateway-for-the-first-time"></a>Configurar um gateway pela primeira vez
Configurar um gateway pela primeira vez consiste num processo de três passos:

1. Transferir e instalar um gateway
2. Configurar o gateway
3. Iniciar sessão nas origens de dados do Power BI

Vamos examinar mais detalhadamente cada passo.

### <a name="download-and-install-a-gateway"></a>Transferir e instalar um gateway
> [!NOTE]
> Há uma nova versão do gateway pessoal para Power BI, com o nome de **gateway de dados no local (modo pessoal)**. Este artigo descreve a versão anterior do gateway pessoal, com o nome de **Power BI Gateway - Personal**, que será descontinuado e deixará de funcionar após 31 de julho de 2017. Para obter informações sobre a nova versão do gateway pessoal, incluindo como instalar a nova versão, consulte o artigo [**Gateway de dados no local (modo pessoal)**](service-gateway-personal-mode.md).
> 
> 

Será pedido que instale um gateway quando clicar pela primeira vez em ATUALIZAR AGORA ou AGENDAR ATUALIZAÇÃO para um conjunto de dados suportado. Em alternativa, para transferir o gateway, selecione **Gateway de Dados** no menu Transferências. Transfira o [gateway de dados no local](http://go.microsoft.com/fwlink/?LinkID=820925).

Deverá selecionar **Gateway Pessoal** em vez de **Gateway de dados no local** para ter um gateway próprio para si.

Não é difícil instalar um gateway. Irá selecionar um local para instalá-lo e deverá ler e aceitar o contrato de licença, assim como qualquer outra aplicação. No entanto, existem algumas coisas importantes que tem de saber. Em particular, o tipo de computador no qual o gateway é instalado e o tipo de conta em que tem sessão iniciada no Windows nesse computador.

> [!NOTE]
> O gateway precisa de ter acesso à origem de dados. Se o seu computador pessoal não se puder ligar à origem de dados, poderá considerar instalar um [gateway de dados no local](service-gateway-onprem.md) num computador que tenha acesso à origem de dados. Um exemplo seria o SQL Server instalado numa máquina virtual (VM) alojada no Azure. O seu computador pessoal poderá não ter acesso à VM. Pode instalar o gateway de dados no local na VM, e configurar uma origem de dados no serviço Power BI.
> 
> 

### <a name="computer-type"></a>Tipo de computador
O tipo de computador em que instala o gateway é importante.

> [!NOTE]
> O gateway pessoal é suportado apenas em sistemas operativos Windows de 64 bits.
> 
> 

Num computador portátil – para que uma atualização agendada ocorra, o gateway precisa de estar em execução. Os computadores portáteis estão geralmente desligados ou no estado de suspensão por um período mais longo do que são executados. Se instalar o gateway num computador portátil, certifique-se de que define os horários da atualização agendada nos quais será executado. Caso contrário, não haverá uma nova tentativa de atualização até à próxima hora da atualização agendada.

Num computador de secretária – não há muitos problemas aqui. Assegure-se de que o computador e o gateway estão em execução nos horários da atualização agendada. Muitos computadores de secretária entram no modo de suspensão e a atualização agendada não poderá ocorrer se eles estiverem suspensos.

Assim que instalar um gateway, não irá precisar de instalar outro. Um gateway funcionará para qualquer número de conjuntos de dados suportados. Também não precisa de instalar o gateway no mesmo computador em que carregou o livro e os ficheiros do Power BI Desktop. Veja um exemplo: digamos que tem um livro do Excel que se liga a uma origem de dados do SQL Server na sua organização. Utilizou a funcionalidade Obter Dados no Power BI para carregar o livro do computador portátil. Também tem um computador de secretária que mantém em execução permanente, e instalou e configurou um gateway nesse computador. No Power BI, iniciou sessão nas suas origens de dados e configurou um agendamento de atualização para o conjunto de dados.  Quando chega o horário da atualização agendada, o Power BI é ligado de forma segura ao gateway instalado no computador de secretária. Em seguida, é ligado com segurança às origens de dados para obter atualizações. Para a atualização, não há nenhuma comunicação com o livro original carregado do computador portátil.

> [!NOTE]
> Pode instalar os gateways pessoais e empresariais no mesmo computador.
> 
> 

### <a name="windows-account"></a>Conta do Windows
Ao instalar o gateway, irá iniciar sessão no computador com a sua conta do Windows. O tipo de permissões que a sua conta do Windows tem terá um efeito sobre como o gateway é instalado e como é executado no Windows.

Quando tiver sessão iniciada no Windows:

|  | Com permissões de administrador | Sem permissões de administrador |
| --- | --- | --- |
| **O Power BI Gateway - Personal é executado como** |Serviço |Aplicação |
| **Atualização Agendada** |Enquanto o computador e o serviço de gateway estiverem em execução, não precisa de ter sessão iniciada no horário agendado para atualização. |Deve ter sessão iniciada no computador no horário agendado para atualização. |
| **Alterar palavra-passe da conta do Windows** |Deve alterar a sua Palavra-passe no serviço do gateway. Se a palavra-passe da conta utilizada pelo gateway já não for válida, a atualização irá falhar. |O gateway sempre será executado com a conta e a palavra-passe em que tem sessão iniciada. Se não tiver sessão iniciada no Windows, o gateway não será executado e ocorrerá uma falha na atualização. |

### <a name="configure-the-gateway"></a>Configurar o gateway
Depois de concluir o Assistente de Instalação, ser-lhe-á pedido para iniciar o Assistente de Configuração. Não é difícil configurar um gateway. Irá precisar de iniciar sessão no Power BI do Assistente. É necessário para que o Assistente se ligue à sua conta do Power BI no serviço Power BI.

Se tiver sessão iniciada no Windows com uma conta com permissões de Administrador, ser-lhe-á pedido para inserir as suas credenciais de conta do Windows. Pode especificar uma conta diferente do Windows, mas lembre-se de que as permissões determinam como o gateway é executado. O serviço do gateway será executado com esta conta.

### <a name="sign-in-to-data-sources"></a>Iniciar sessão nas origens de dados
Depois de concluir o Assistente de Configuração e o gateway estiver em execução, irá precisar de especificar um tipo de Autenticação e iniciar sessão em cada uma das origens de dados do conjunto de dados. Irá concluir este passo no Power BI.

![](media/personal-gateway/pg_dataset_settings_signin.png)

Apenas precisa de especificar um tipo de autenticação e iniciar sessão numa origem de dados uma única vez. Inicie sessão na secção **Gerir Origens de Dados** no ecrã Definições de um conjunto de dados. Se tiver várias origens de dados, terá de iniciar sessão em cada uma delas. O gateway determina um tipo de Autenticação predefinido, dependendo da origem de dados. Na maioria dos casos, é a autenticação do Windows; no entanto, em alguns casos, a sua origem de dados pode exigir um tipo de autenticação diferente. Se não tiver certeza, verifique com o seu administrador da origem de dados.

## <a name="up-and-running"></a>Em execução!
Quando o gateway estiver em execução, pode clicar em AGENDAR ATUALIZAÇÃO para um conjunto de dados, em que verá a página Definições do conjunto de dados.

![](media/personal-gateway/pg_awintsales_settings.png)

Esta página mostra:

1. Atualizar estado - Mostra o êxito da atualização e a hora da próxima atualização agendada.
2. **Gateway** – Mostra se um gateway está instalado e online. Se um gateway estiver instalado, mas não estiver online, as definições Gerir Origens de Dados e Agendar Atualização são desativadas.
3. **Gerir Origens de Dados** - Mostra as origens de dados às quais o conjunto de dados se liga. Pode Iniciar sessão ou alterar o tipo de autenticação. Apenas irá precisar de Iniciar sessão em cada origem de dados uma só vez.
4. **Agendar Atualização** – Pode configurar as definições de um agendamento de atualização aqui. Se o gateway não estiver online, estas definições serão desativadas.
5. Notificações de falha de atualização – Esta opção, selecionada por predefinição, irá enviar um e-mail para si em caso de falha de uma atualização agendada.

## <a name="updating-your-windows-account-password"></a>Atualizar a palavra-passe da conta do Windows
Se tinha sessão iniciada no computador com uma conta do Windows com privilégios de administrador durante a instalação do gateway, ele seria executado como um serviço com a conta do Windows especificada no Assistente de Configuração. Normalmente, esta será a mesma conta do Windows que utiliza para iniciar sessão no seu computador. Quando alterar a palavra-passe da sua conta do Windows, também irá precisar de a alterar no gateway; caso contrário, o serviço poderá não ser executado e ocorrerá uma falha na atualização. Para alterar a sua palavra-passe da conta do Windows para o gateway, clique no ícone do gateway pessoal na Barra de Tarefas da Área de Trabalho do Windows ou em Aplicações.

![](media/personal-gateway/pg_programicon.png)

Aqui, pode atualizar a sua palavra-passe e verificar o estado de ligação do gateway.

![](media/personal-gateway/pg_credentials.png)

## <a name="ports"></a>Portas
O gateway comunica com as portas de saída TCP 443 (predefinição), 5671, 5672, 9350 a 9354.  O gateway não precisa de portas de entrada.

| Nomes de domínio | Portas de saída | Descrição |
| --- | --- | --- |
| *.powerbi.com |443 |HTTPS |
| *.analysis.windows.net |443 |HTTPS |
| *.login.windows.net |443 |HTTPS |
| *.servicebus.windows.net |5671-5672 |Advanced Message Queuing Protocol (AMQP) |
| *.servicebus.windows.net |443, 9350-9354 |Ouvintes no Reencaminhamento do Service Bus por TCP (precisa de 443 para aquisição do token de Controlo de Acesso) |
| *.frontend.clouddatahub.net |443 |HTTPS |
| *.core.windows.net |443 |HTTPS |
| login.microsoftonline.com |443 |HTTPS |
| login.windows.net |443 |HTTPS |

Se precisar de colocar endereços IP em vez de domínios na lista branca, pode transferir e utilizar a lista de intervalos de IP do Datacenter do Microsoft Azure. [Transferir](https://www.microsoft.com/download/details.aspx?id=41653)

## <a name="next-steps"></a>Próximos passos
[Gateway de dados local (modo pessoal) - A nova versão do gateway pessoal](service-gateway-personal-mode.md)
[Configurar definições de proxy para Gateways do Power BI](service-gateway-proxy.md)  
[Power BI Premium](service-premium.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

