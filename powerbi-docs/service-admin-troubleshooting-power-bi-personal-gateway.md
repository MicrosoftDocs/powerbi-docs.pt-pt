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
ms.openlocfilehash: bc6eaccc2976266102dcca0d20df73df810fa5f3
ms.sourcegitcommit: bf535771c9ef495f9bb658569403fa5e3dd82e6a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65853517"
---
# <a name="troubleshooting-power-bi-gateway---personal"></a>Solucionando problemas do Power BI Gateway - Personal
As secções seguintes passam por alguns problemas comuns que pode encontrar ao utilizar o Power BI Gateway-Personal.

> [!NOTE]
> A versão atual do gateway para utilização pessoal é o **Gateway de dados no local (pessoal)**. Atualize a instalação para utilizar essa versão.
> 
> 

## <a name="update-to-the-latest-version"></a>Atualize para a versão mais recente
Muitos problemas podem surgir quando a versão do gateway está desatualizada.  É uma boa prática geral para se certificar de que está na versão mais recente. Se não tiver atualizado o gateway durante um mês ou mais, considere instalar a versão mais recente do gateway. Em seguida, veja se pode reproduzir o problema.

## <a name="installation"></a>Instalação
**Gateway pessoal é de 64 bits** -se a sua máquina é de 32 bits, não é possível instalar o gateway pessoal. O sistema operativo tem de ser a versão de 64 bits. Instalar uma versão de 64 bits do Windows ou instalar o gateway pessoal num computador de 64 bits.

**Falha na instalação como um serviço, mesmo que seja um administrador local para o computador do gateway pessoal** -instalação poderá falhar se o utilizador está no grupo de administradores local do computador, mas a diretiva de grupo não permite esse nome de utilizador iniciar sessão como um serviço. No momento, certifique-se de que a política de grupo permite que um utilizador inicie sessão como um serviço. Estamos a trabalhar para encontrar uma correção para este problema. [Saiba mais](https://technet.microsoft.com/library/cc739424.aspx)

**A operação excedeu** -esta mensagem é comum se o computador (computador físico ou VM) no qual está a instalar o gateway pessoal tem um processador de núcleo único. Feche todos os aplicações, desligue todos os processos não essenciais e tente instalar novamente.

**O Data Management Gateway ou o Analysis Services Connector não pode ser instalado no mesmo computador que o gateway pessoal** – se já tiver um Analysis Services Connector ou Gateway de gestão de dados instalado, primeiro tem de desinstalar o conector ou o gateway. Em seguida, tente instalar o gateway pessoal.

> [!NOTE]
> Se ocorrer um problema durante a instalação, os registos de configuração podem fornecer informações para ajudar a resolver o problema. Para obter mais informações, consulte [registos de configuração](#SetupLogs).
> 
> 

 **Configuração de proxy** poderá ver problemas com a configuração do gateway pessoal se o seu ambiente tiver de utilizar um proxy. Para obter mais informações sobre como configurar as informações de proxy, veja [Configurar definições de proxy para os Gateways do Power BI](service-gateway-proxy.md)

## <a name="schedule-refresh"></a>Agendar atualização
**Erro: As credenciais armazenadas na cloud estão ausentes.**

Poderá receber este erro nas definições para \<conjunto de dados\> se tiver uma atualização agendada e, em seguida, desinstalado e reinstalado o gateway pessoal. Quando desinstala um gateway pessoal, são removidas as credenciais da origem de dados para um conjunto de dados que tenha sido configurado para a atualização do serviço Power BI.

**Solução:** No Power BI, aceda às configurações de atualização de um conjunto de dados. Em Gerir origens de dados, para qualquer origem de dados com um erro, selecione **editar credenciais** e inicie sessão para a origem de dados novamente.

**Erro: As credenciais fornecidas para o conjunto de dados são inválidas. Atualize as credenciais através de uma atualização ou no diálogo Configurações de Origens de Dados para continuar.**

**Solução**: Se receber uma mensagem de credenciais, isso pode significar:

* Certifique-se de nomes de utilizador e palavras-passe para iniciar sessão nas origens de dados estão atualizadas. No Power BI, vá a configurações de atualização do conjunto de dados. Em Gerir origens de dados, selecione **editar credenciais** para atualizar as credenciais da origem de dados.
* Os Mashups entre uma origem de cloud e uma origem de locais, numa única consulta, não conseguir atualizar no gateway pessoal se uma das origens estiver a utilizar o OAuth para autenticação. Um exemplo deste problema é um mashup entre o CRM Online e um SQL Server local. O mashup não consegue porque o CRM Online exige o OAuth.
  
  Este erro é um problema conhecido e está a ser examinou. Para contornar o problema, tenha uma consulta separada para a origem de cloud e a origem no local. Em seguida, utilize uma intercalação ou acrescentar a consulta para combiná-los.

**Erro: Origem de dados não suportada.**

**Solução:** Se receber uma mensagem a informar que não existe suporte para a origem de dados nas definições Agendar Atualização, pode significar que: 

* A origem de dados não é atualmente suportada para a atualização no Power BI. 
* O livro do Excel não contém um modelo de dados, apenas os dados de folha de cálculo. O Power BI atualmente apenas suporta à atualização se o livro do Excel carregado contiver um modelo de dados. Quando importa dados utilizando o Power Query no Excel, lembre-se de escolher a opção Carregar dados para o modelo de dados. Essa opção assegura que dados são importados para um modelo de dados. 

**Erro: [Não é possível combinar dados] &lt;parte da consulta&gt;/&lt;... &gt; / &lt;... &gt; está a aceder a origens de dados com níveis de privacidade, que não podem ser utilizados em conjunto. Recompile esta combinação de dados.**

**Solução**: Este erro é devido as restrições no nível de privacidade e os tipos de origens de dados que estiver a utilizar.

**Erro: Erro de origem de dados: Não conseguimos converter o valor “\[Table\]” para o tipo Tabela.**

**Solução**: Este erro é devido as restrições no nível de privacidade e os tipos de origens de dados que estiver a utilizar.

**Erro: Não existe espaço suficiente para esta linha.**

Este erro ocorre se tiver uma única linha superior a 4 MB de tamanho. Localizar a linha da sua origem de dados e tente filtrá-la ou reduzir o tamanho dessa linha.

## <a name="data-sources"></a>Origens de dados
**Fornecedor de dados em falta** – o gateway pessoal é apenas a versão de 64 bits. Este exige a instalação de uma versão de 64 bits dos fornecedores de dados no mesmo computador em que o gateway pessoal está instalado. Por exemplo, se a origem de dados no conjunto de dados for o Microsoft Access, será necessário instalar o fornecedor ACE de 64 bits no mesmo computador em que o gateway pessoal está instalado.  

>[!NOTE]
>Se tiver a versão de 32 bits Excel, não é possível instalar um fornecedor ACE de versão de 64 bits no mesmo computador.

**A autenticação do Windows não é suportado para a base de dados do Access** – Neste momento, o Power BI apenas suporta a autenticação anónima para a base de dados do Access. Estamos a trabalhar na ativar a autenticação do Windows para a base de dados de acesso.

**Erro de ligação ao introduzir as credenciais para uma origem de dados** -se obtiver um erro como ao introduzir as credenciais do Windows para uma origem de dados, que talvez ainda esteja numa versão anterior do gateway pessoal. [Instale a versão mais recente do Power BI Gateway - Personal](https://powerbi.microsoft.com/gateway/).

  ![](media/service-admin-troubleshooting-power-bi-personal-gateway/pbi_pg_credentialserror.jpg.png)

**Erro: Erro de início de sessão ao selecionar a autenticação do Windows para uma origem de dados com ACE OLEDB**. Se receber o erro seguinte ao introduzir as credenciais de uma origem de dados com o fornecedor ACE OLEDB:

![](media/service-admin-troubleshooting-power-bi-personal-gateway/aceoledberror.png)

O Power BI atualmente não suporta a autenticação do Windows para uma origem de dados utilizando o fornecedor ACE OLEDB.

**Solução:** Para contornar este erro, pode selecionar **autenticação anónima**. Para o fornecedor ACE OLEDB herdado, as credenciais anónimas são iguais às credenciais do Windows.

## <a name="tile-refresh"></a>Atualização de mosaico
Se está a receber um erro com a atualização de mosaicos do dashboard, consulte o artigo seguinte.

[Resolução de problemas de erros de mosaico](refresh-troubleshooting-tile-errors.md)

## <a name="tools-for-troubleshooting"></a>Ferramentas para solução de problemas
### <a name="refresh-history"></a>Histórico de Atualizações
**Histórico de atualização** ajuda-o a ver os erros que ocorreram e fornece dados úteis se precisar de criar um pedido de suporte. Pode ver agendas e a pedido, é atualizado. Eis como obter para o **histórico de atualização**.

1. No painel de navegação do Power BI, em **Conjuntos de Dados** , selecione um conjunto de dados &gt; Abrir Menu &gt; **Agendar Atualização**.
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh.png)
1. No **definições para...** , selecione **histórico de atualização**.  
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh-2.png)
   
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/refresh-history.png)

### <a name="event-logs"></a>Registos de eventos
Vários registos de eventos pode fornecer informações. Os dois primeiros, **Data Management Gateway** e **PowerBIGateway**, estão presentes se for um administrador na máquina.  Se não for um administrador e estiver a utilizar o Gateway pessoal, verá as entradas de log dentro da **aplicativo** log.

O **Data Management Gateway** e os registos do **PowerBIGateway** estão presentes nos **registos de aplicações e serviços**.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/event-logs.png)

### <a name="fiddler-trace"></a>Rastreio do Fiddler
O [Fiddler](http://www.telerik.com/fiddler) é uma ferramenta gratuita da Telerik que monitoriza o tráfego HTTP. Pode ver a comunicação com o serviço Power BI do computador cliente. Esta comunicação pode mostrar erros e outras informações relacionadas.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/fiddler.png)

<a name="SetupLogs"></a>

### <a name="setup-logs"></a>Registos de configuração
Se o **Gateway pessoal**, falha na instalação, verá um link para mostrar o registo da configuração. O registo da configuração mostra os detalhes sobre a falha. Estes registos são registos de instalação do Windows, também conhecidos como registos do MSI. Estes podem ser bastante complexos e de difícil leitura. Normalmente, o erro resultante é na parte inferior, mas que determina a causa do erro não é trivial. Este pode ser um resultado de erros num registo diferente ou de um erro apresentado acima no registo.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-log.png)

Em alternativa, pode aceder à sua **pasta Temp** (% temp %) e procure ficheiros começados por **Power\_BI\_**.

> [!NOTE]
> Ir para %temp% poderá levá-lo a uma subpasta de temp. O **Power\_BI\_**  ficheiros estão na raiz do diretório temp.  Talvez seja necessário subir um nível ou dois.
> 
> 

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-logs2.png)

## <a name="next-steps"></a>Próximos passos
[Configurar definições de proxy para os Gateways do Power BI](service-gateway-proxy.md)  
[Atualização de Dados](refresh-data.md)  
[Power BI Gateway - Personal](service-gateway-personal-mode.md)  
[Resolução de problemas de erros de mosaico](refresh-troubleshooting-tile-errors.md)  
[Resolução de problemas do Gateway de dados no local](service-gateway-onprem-tshoot.md)  
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

