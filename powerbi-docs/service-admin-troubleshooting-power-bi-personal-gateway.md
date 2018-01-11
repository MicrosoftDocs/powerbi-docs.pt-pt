---
title: Solucionando problemas do Power BI Gateway - Personal
description: Solucionando problemas do Power BI Gateway - Personal
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: 7774153ff73fb67a434ac79016507a2e94cf40f1
ms.sourcegitcommit: 8f72ce6b35aa25979090a05e3827d4937dce6a0d
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/27/2017
---
# <a name="troubleshooting-power-bi-gateway---personal"></a>Solucionando problemas do Power BI Gateway - Personal
O exemplo a seguir mostra alguns problemas comuns que poderá ter ao usar o Power BI Gateway - Personal.

> [!NOTE]
> Caso encontre um problema que não esteja listado abaixo, pode pedir assistência no [site da comunidade](http://community.powerbi.com/) ou criar um [pedido de suporte](https://powerbi.microsoft.com/support/).
> 
> 

## <a name="update-to-the-latest-version"></a>Atualize para a versão mais recente
Muitos problemas podem surgir quando a versão de gateway está desatualizada.  É uma boa prática geral certificar-se de que se encontra na última versão.  Se não tiver atualizado o gateway durante um mês ou mais, considere a possibilidade de instalar a última versão do gateway e tentar reproduzir o problema.

## <a name="installation"></a>Instalação
**O gateway pessoal é de 64 bits** – Se o seu computador tiver 32 bits, não pode instalar o gateway pessoal. O sistema operativo tem de ser de 64 bits. Terá de instalar uma versão de 64 bits do Windows ou instalar o gateway pessoal num computador de 64 bits.

**Falha na instalação do gateway pessoal como serviço, mesmo que seja um administrador local do computador** – A instalação poderá falhar se o utilizador estiver no grupo do Administrador local do computador, mas a política de grupo não permitir que esse nome de utilizador inicie sessão como serviço.  Nesse momento, assegure que a política de grupo permita que um utilizador inicie sessão como um serviço. Estamos a trabalhar para encontrar uma correção para este problema. [Saiba mais](https://technet.microsoft.com/library/cc739424.aspx)

**Tempo limite da operação excedido** – Isto é comum caso o computador (computador físico ou VM) no qual o gateway pessoal está a ser instalado tenha um processador de núcleo único. Feche todos os aplicações, desligue todos os processos não essenciais e tente instalar novamente.

**O Data Management Gateway ou o Analysis Services Connector não pode ser instalado no mesmo computador que o gateway pessoal** – Se já tiver um Analysis Services Connector ou Gateway de Gestão de Dados instalado, deverá desinstalar primeiro o Connector ou o gateway e, em seguida, tentar instalar o gateway pessoal.

> [!NOTE]
> Se tiver algum problema durante a instalação, os registos de configuração poderão fornecer informações para ajudá-lo a resolver o problema. Veja [Registos de Instalação](#SetupLogs) para obter mais informações.
> 
> 

 **Configuração do proxy** Pode encontrar problemas na configuração do gateway pessoal se o seu ambiente tiver de utilizar um proxy. Para obter mais informações sobre como configurar as informações de proxy, veja [Configurar definições de proxy para os Gateways do Power BI](service-gateway-proxy.md)

## <a name="schedule-refresh"></a>Agendar atualização
**Erro: as credenciais armazenadas na cloud estão ausentes.**

Pode receber este erro nas Definições para \<conjunto de dados\> se tiver uma atualização agendada e tiver desinstalado e reinstalado o gateway pessoal. Ao desinstalar um gateway pessoal, as credenciais de origem de dados de um conjunto de dados que foram configuradas para atualização serão removidas do serviço Power BI.

**Solução:** no Power BI, vá para as configurações de atualização de um conjunto de dados. Em Gerir Origens de Dados, para qualquer origem de dados com um erro, clique em Editar credenciais e entre novamente na origem de dados.

**Erro: as credenciais fornecidas para o conjunto de dados são inválidas. Atualize as credenciais através de uma atualização ou no diálogo Configurações de Origens de Dados para continuar.**

**Solução**: se receber uma mensagem de credenciais, isso pode significar:

* Verifique se os nomes de utilizador e as palavras-passe usadas para iniciar sessão nas origens de dados estão atualizados. No Power BI, vá a configurações de atualização do conjunto de dados. Em Gerir Origens de Dados, clique em Editar credenciais para atualizar as credenciais da origem de dados.
* Os mashups entre uma origem de cloud e uma origem local, numa única consulta, não conseguirão ser atualizados no gateway pessoal se uma das origens estiver a utilizar o OAuth para autenticação. Um exemplo disso é um mashup entre o CRM Online e um SQL Server local. Isto irá falhar porque o CRM Online exige o OAuth.
  
  Este é um problema conhecido e está a ser analisado. Para resolver o problema, tenha uma consulta separada para a origem de cloud e a origem local e use uma consulta em série ou acréscimo para combiná-las.

**Erro: origem de dados não suportada.**

**Solução:** se receber uma mensagem a informar que não há suporte para a origem de dados nas configurações de Agendar Atualização, isto pode significar que: 

* Atualmente, não há suporte para a atualização da origem de dados no Power BI. 
* O livro do Excel não contém um modelo de dados, apenas os dados da folha do cálculo. O Power BI atualmente apenas suporta à atualização se o livro do Excel carregado contiver um modelo de dados. Quando importa dados utilizando o Power Query no Excel, lembre-se de escolher a opção Carregar dados para o modelo de dados. Isto garante que os dados sejam importados num modelo de dados. 

**Erro: [não é possível combinar dados] &lt;parte da consulta&gt;/&lt;…&gt;/&lt;…&gt; está a aceder a origens de dados com níveis e privacidade que não podem ser utilizados em conjunto. Reconstruia esta combinação de dados.**

**Solução**: este erro ocorre devido a restrições no nível de privacidade e aos tipos de origens de dados que estão a ser utilizados. [Saiba mais](refresh-enable-fast-combine.md)

**Erro: erro na origem de dados: não é possível converter o valor "\[Table\]" para o tipo Tabela.**

**Solução**: este erro ocorre devido a restrições no nível de privacidade e aos tipos de origens de dados que estão a ser utilizados. [Saiba mais](refresh-enable-fast-combine.md)

**Erro: não existe espaço suficiente para esta linha.**

Esta situação ocorrerá se tiver uma única linha com um tamanho superior a 4 MB. Terá de determinar qual linha pertence à sua origem de dados e tentar filtrá-la ou reduzir o tamanho dessa linha.

## <a name="data-sources"></a>Origens de dados
**Fornecedor de dados em falta** – O gateway pessoal BI tem apenas 64 bits. Este exige a instalação de uma versão de 64 bits dos fornecedores de dados no mesmo computador em que o gateway pessoal está instalado. Por exemplo, se a origem de dados no conjunto de dados for o Microsoft Access, será necessário instalar o fornecedor ACE de 64 bits no mesmo computador em que o gateway pessoal está instalado.  

>[!NOTE]
>Se tiver o Excel de 32 bits, não pode instalar um fornecedor ACE de 64 bits no mesmo computador.

**A autenticação do Windows não é suportado para a base de dados do Access** – Neste momento, o Power BI apenas suporta a autenticação anónima para a base de dados do Access. Estamos a trabalhar para ativar a autenticação do Windows para a base de dados do Access.

**Erro de ligação ao introduzir as credenciais de uma origem de dados** – Se receber um erro semelhante a este ao introduzir as credenciais do Windows de uma origem de dados, isto significa que talvez ainda esteja a utilizar uma versão mais antiga do gateway pessoal. [Instale a versão mais recente do Power BI Gateway - Personal](https://powerbi.microsoft.com/gateway/).

  ![](media/service-admin-troubleshooting-power-bi-personal-gateway/pbi_pg_credentialserror.jpg.png)

**Erro: erro de ligação ao selecionar a autenticação do Windows para uma origem de dados utilizando o ACE OLEDB** - se receber o erro seguinte ao introduzir as credenciais da origem de dados para uma origem de dados utilizando o fornecedor ACE OLEDB:

![](media/service-admin-troubleshooting-power-bi-personal-gateway/aceoledberror.png)

O Power BI atualmente não suporta autenticação do Windows para uma origem de dados utilizando o fornecedor ACE OLEDB.

**Solução:** Para solucionar este erro, pode selecionar a autenticação Anónima. Para o fornecedor ACE OLEDB herdado, as credenciais Anónimas são equivalentes às credenciais do Windows.

## <a name="tile-refresh"></a>Atualização de mosaico
Se estiver a receber um erro com a atualização de mosaicos do dashboard, veja o artigo seguinte.

[Resolução de problemas de erros de mosaico](refresh-troubleshooting-tile-errors.md)

## <a name="tools-for-troubleshooting"></a>Ferramentas para solução de problemas
### <a name="refresh-history"></a>Histórico de atualização
O **Histórico de Atualização** poderá ajudá-lo a ver que erros ocorreram, além de fornecer dados úteis se precisar de criar um pedido de suporte. Pode ver as atualizações agendadas ou pedidas. Aqui está como pode aceder ao **Histórico de Atualização**.

1. No painel de navegação do Power BI, em **Conjuntos de Dados** , selecione um conjunto de dados &gt; Abrir Menu &gt; **Agendar Atualização**.
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh.png)
2. Em **Definições para...** &gt; **Agendar Atualização**, selecione **Histórico de Atualizações**.  
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh-2.png)
   
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/refresh-history.png)

### <a name="event-logs"></a>Registos de eventos
Existem vários registos de eventos que podem fornecer informações. Os dois primeiros, **Data Management Gateway** e **PowerBIGateway**, estão presentes se for um administrador no computador.  Se não for um administrador e estiver a utilizar o Gateway pessoal, verá as entradas de registo dentro do registo da **Aplicação** .

O **Data Management Gateway** e os registos do **PowerBIGateway** estão presentes nos **registos de aplicações e serviços**.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/event-logs.png)

### <a name="fiddler-trace"></a>Rastreio do Fiddler
[Fiddler](http://www.telerik.com/fiddler) é uma ferramenta gratuita da Telerik que monitoriza o tráfego HTTP.  Pode ver as comunicações com o serviço Power BI do computador de cliente. Isto pode mostrar erros e outras informações relacionadas.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/fiddler.png)

<a name="SetupLogs"></a>

### <a name="setup-logs"></a>Registos de configuração
Em caso de falha na instalação do **Personal Gateway**, verá uma ligação para apresentar o registo de instalação. Isto poderia mostrar detalhes sobre a falha. Estes são os Registos de Instalação do Windows, também conhecidos como Registos do MSI. Estes podem ser bastante complexos e de difícil leitura. Normalmente, o erro resultante é mostrado na parte inferior, mas não é comum determinar a causa do erro. Este pode ser um resultado de erros num registo diferente ou de um erro apresentado acima no registo.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-log.png)

Como alternativa, pode aceder à **pasta Temp** (%temp%) e procurar os ficheiros começados por **Power\_BI\_**.

> [!NOTE]
> Ir para %temp% poderá levá-lo a uma subpasta de temp.  Os ficheiros **Power\_BI\_** estão na raiz do diretório temp.  Talvez seja necessário subir um nível ou dois.
> 
> 

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-logs2.png)

## <a name="next-steps"></a>Próximos passos
[Configurar definições de proxy para os Gateways do Power BI](service-gateway-proxy.md)  
[Atualização de Dados](refresh-data.md)  
[Power BI Gateway - Personal](personal-gateway.md)  
[Resolução de problemas de erros de mosaico](refresh-troubleshooting-tile-errors.md)  
[Resolução de problemas do gateway de dados no local](service-gateway-onprem-tshoot.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

