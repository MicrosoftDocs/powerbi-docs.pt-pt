---
title: Solucionando problemas do Power BI Gateway - Personal
description: Solucionando problemas do Power BI Gateway - Personal
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 5/06/2019
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 7827ce359022eccfb75798b08da164b7504c84df
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271836"
---
# <a name="troubleshooting-power-bi-gateway---personal"></a>Solucionando problemas do Power BI Gateway - Personal

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

As secções que se seguem mostram alguns problemas comuns que poderá ter ao utilizar o Power BI Gateway – Personal.

## <a name="update-to-the-latest-version"></a>Atualize para a versão mais recente

A versão atual do gateway para utilização pessoal é o **Gateway de dados no local (pessoal)** . Atualize a instalação para utilizar essa versão.

Muitos problemas podem surgir quando a versão do gateway está desatualizada.  É uma boa prática geral ter a certeza de que está a utilizar a versão mais recente. Se não tiver atualizado o gateway durante um mês ou mais, pondere instalar a versão mais recente do gateway. Em seguida, verifique se consegue reproduzir o problema.

## <a name="installation"></a>Instalação
**O gateway pessoal é de 64 bits** – se o seu computador for de 32 bits, não conseguirá instalar o gateway pessoal. A versão do seu sistema operacional tem de ser a de 64 bits. Instale uma versão de 64 bits do Windows ou instale o gateway pessoal num computador de 64 bits.

**Falha na instalação do gateway pessoal como serviço, mesmo que seja um administrador local do computador** – a instalação poderá falhar se o utilizador estiver no grupo do Administrador local do computador, mas a política de grupo não permitir que esse nome de utilizador inicie sessão como serviço. Nesse momento, certifique-se de que a política de grupo permite que um utilizador inicie sessão como serviço. Estamos a trabalhar para encontrar uma correção para este problema. [Saiba mais](https://technet.microsoft.com/library/cc739424.aspx)

**Tempo limite da operação excedido** – esta mensagem é comum caso o computador (computador físico ou VM) no qual o gateway pessoal está a ser instalado tenha um processador de núcleo único. Feche todos os aplicações, desligue todos os processos não essenciais e tente instalar novamente.

**O Gateway de Gestão de Dados ou o Analysis Services Connector não pode ser instalado no mesmo computador que o gateway pessoal** – se já tiver um Analysis Services Connector ou Gateway de Gestão de Dados instalado, deverá desinstalar primeiro o Connector ou o gateway. Em seguida, tente instalar o gateway pessoal.

> [!NOTE]
> Se tiver algum problema durante a instalação, os registos de configuração podem fornecer informações para o ajudar a resolver o problema. Para obter mais informações, veja os [Registos de Configuração](#SetupLogs).
> 
> 

 **Configuração do proxy** Pode encontrar problemas ao configurar o gateway pessoal se o seu ambiente tiver de utilizar um proxy. Para obter mais informações sobre como configurar as informações de proxy, veja [Configurar definições de proxy para o gateway de dados no local](/data-integration/gateway/service-gateway-proxy).

## <a name="schedule-refresh"></a>Agendar atualização
**Erro: As credenciais armazenadas na cloud estão ausentes.**

Poderá receber este erro nas Definições para \<conjunto de dados\> se tiver uma atualização agendada e tiver desinstalado e reinstalado o gateway pessoal. Ao desinstalar um gateway pessoal, as credenciais de origem de dados de um conjunto de dados que foram configuradas para atualização serão removidas do serviço Power BI.

**Solução:** No Power BI, aceda às configurações de atualização de um conjunto de dados. Em Gerir Origens de Dados, para qualquer origem de dados com um erro, selecione **Editar credenciais** e volte a iniciar sessão na origem de dados.

**Erro: As credenciais fornecidas para o conjunto de dados são inválidas. Atualize as credenciais através de uma atualização ou no diálogo Configurações de Origens de Dados para continuar.**

**Solução**: Se receber uma mensagem de credenciais, isso pode significar:

* Certifique-se de que os nomes de utilizador e as palavras-passe utilizadas para iniciar sessão nas origens de dados estão atualizados. No Power BI, vá a configurações de atualização do conjunto de dados. Em Gerir Origens de Dados, selecione **Editar credenciais** para atualizar as credenciais da origem de dados.
* Os mashups entre uma origem na cloud e uma origem no local, numa única consulta, não conseguem ser atualizados no gateway pessoal se uma das origens estiver a utilizar o OAuth para autenticação. Um exemplo deste problema é um mashup entre o CRM Online e um SQL Server local. O mashup falha porque o CRM Online exige o OAuth.
  
  Este é um erro conhecido que está a ser analisado. Para resolver o problema, separe a consulta da origem na cloud da consulta da origem no local. Em seguida, utilize uma consulta de intercalação ou acréscimo para as combinar.

**Erro: Origem de dados não suportada.**

**Solução:** Se receber uma mensagem a informar que não existe suporte para a origem de dados nas definições Agendar Atualização, pode significar que: 

* Atualmente, não há suporte para a atualização da origem de dados no Power BI. 
* O livro do Excel não contém um modelo de dados; só contém dados da folha do cálculo. O Power BI atualmente apenas suporta à atualização se o livro do Excel carregado contiver um modelo de dados. Quando importa dados utilizando o Power Query no Excel, lembre-se de escolher a opção Carregar dados para o modelo de dados. Esta opção garante que os dados são importados para um modelo de dados. 

**Erro: [não é possível combinar dados] &lt;parte da consulta&gt;/&lt;…&gt;/&lt;…&gt; está a aceder a origens de dados com níveis de privacidade que não podem ser utilizados em conjunto. Recompile esta combinação de dados.**

**Solução**: Este erro ocorre devido a restrições associadas aos níveis de privacidade e aos tipos de origens de dados que está a utilizar.

**Erro: Erro de origem de dados: Não conseguimos converter o valor “\[Table\]” para o tipo Tabela.**

**Solução**: Este erro ocorre devido a restrições associadas aos níveis de privacidade e aos tipos de origens de dados que está a utilizar.

**Erro: Não existe espaço suficiente para esta linha.**

Este erro ocorre se tiver uma única linha com um tamanho superior a 4 MB. Localize a linha que pertence à sua origem de dados e tente filtrá-la ou reduzir o tamanho dessa linha.

## <a name="data-sources"></a>Origens de dados
**Fornecedor de dados em falta** – a versão do gateway pessoal é apenas de 64 bits. Este exige a instalação de uma versão de 64 bits dos fornecedores de dados no mesmo computador em que o gateway pessoal está instalado. Por exemplo, se a origem de dados no conjunto de dados for o Microsoft Access, será necessário instalar o fornecedor ACE de 64 bits no mesmo computador em que o gateway pessoal está instalado.  

>[!NOTE]
>Se tiver a versão de 32 bits do Excel, não pode instalar uma versão de 64 bits do fornecedor ACE no mesmo computador.

**A autenticação do Windows não é suportado para a base de dados do Access** – Neste momento, o Power BI apenas suporta a autenticação anónima para a base de dados do Access. Estamos a trabalhar para ativar a autenticação do Windows para a base de dados do Access.

**Erro de início de sessão ao introduzir as credenciais de uma origem de dados** – se receber um erro como este ao introduzir as credenciais do Windows de uma origem de dados, isto significa que talvez ainda esteja a utilizar uma versão mais antiga do gateway pessoal. [Instale a versão mais recente do Power BI Gateway - Personal](https://powerbi.microsoft.com/gateway/).

  ![](media/service-admin-troubleshooting-power-bi-personal-gateway/pbi_pg_credentialserror.jpg.png)

**Erro: Erro de início de sessão ao selecionar a autenticação do Windows para uma origem de dados com ACE OLEDB**. Se receber o erro seguinte ao introduzir as credenciais de uma origem de dados com o fornecedor ACE OLEDB:

![](media/service-admin-troubleshooting-power-bi-personal-gateway/aceoledberror.png)

O Power BI atualmente não suporta autenticação do Windows para uma origem de dados com recurso ao fornecedor ACE OLEDB.

**Solução:** Para solucionar este erro, pode selecionar a  **autenticação Anónima**. Para o fornecedor ACE OLEDB herdado, as credenciais Anónimas são iguais às credenciais do Windows.

## <a name="tile-refresh"></a>Atualização de mosaico
Se estiver a receber um erro com a atualização de mosaicos do dashboard, consulte o seguinte artigo.

[Resolução de problemas de erros de mosaico](refresh-troubleshooting-tile-errors.md)

## <a name="tools-for-troubleshooting"></a>Ferramentas para solução de problemas
### <a name="refresh-history"></a>Histórico de Atualizações
O **Histórico de Atualizações** ajuda-o a ver os erros que ocorreram, além de fornecer dados úteis se precisar de criar um pedido de suporte. Pode ver as atualizações agendadas ou pedidas. Eis como pode aceder ao **Histórico de Atualizações**.

1. No painel de navegação do Power BI, em **Conjuntos de Dados** , selecione um conjunto de dados &gt; Abrir Menu &gt; **Agendar Atualização**.
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh.png)
1. Em **Definições para...** , selecione **Histórico de Atualizações**.  
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh-2.png)
   
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/refresh-history.png)

### <a name="event-logs"></a>Registos de eventos
Existem vários registos de eventos que podem fornecer informações. Os dois primeiros, **Gateway de Gestão de Dados** e **PowerBIGateway**, estão presentes se for administrador no computador.  Se não for administrador e estiver a utilizar o Gateway Pessoal, verá as entradas de registo dentro do registo da **Aplicação**.

O **Data Management Gateway** e os registos do **PowerBIGateway** estão presentes nos **registos de aplicações e serviços**.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/event-logs.png)

### <a name="fiddler-trace"></a>Rastreio do Fiddler
O [Fiddler](http://www.telerik.com/fiddler) é uma ferramenta gratuita da Telerik que monitoriza o tráfego HTTP. Pode ver as comunicações com o serviço Power BI a partir do computador cliente. Estas comunicações podem mostrar erros e outras informações relacionadas.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/fiddler.png)

<a name="SetupLogs"></a>

### <a name="setup-logs"></a>Registos de configuração
Em caso de falha na instalação do **Gateway Pessoal**, verá uma ligação para apresentar o registo de configuração. O registo de configuração pode mostrar detalhes sobre a falha. Estes registos são Registos de Instalação do Windows, também conhecidos como Registos do MSI. Estes podem ser bastante complexos e de difícil leitura. Normalmente, o erro resultante é mostrado na parte inferior, mas não é comum determinar a causa do erro. Este pode ser um resultado de erros num registo diferente ou de um erro apresentado acima no registo.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-log.png)

Em alternativa, pode aceder à **pasta Temp** (%temp%) e procurar os ficheiros começados por **Power\_BI\_** .

> [!NOTE]
> Ir para %temp% poderá levá-lo a uma subpasta de temp. Os ficheiros **Power\_BI\_** estão na raiz do diretório temp.  Talvez seja necessário subir um nível ou dois.
> 
> 

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-logs2.png)

## <a name="next-steps"></a>Próximos passos
[Configurar definições de proxy para o gateway de dados no local](/data-integration/gateway/service-gateway-proxy)  
[Atualização de Dados](refresh-data.md)  
[Power BI Gateway - Personal](service-gateway-personal-mode.md)  
[Resolução de problemas de erros de mosaico](refresh-troubleshooting-tile-errors.md)  
[Resolução de problemas do Gateway de dados no local](service-gateway-onprem-tshoot.md)  
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

