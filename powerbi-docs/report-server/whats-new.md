---
title: Novidades no Power BI Report Server
description: "Saiba mais sobre as novidades no Power BI Report Server. Esta secção abrange áreas de funcionalidades importantes e é atualizada à medida que são lançados novos itens."
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.date: 10/31/2017
ms.author: maghan
ms.openlocfilehash: 433581f77cfeaa002cffeecd927ba8751fc46617
ms.sourcegitcommit: eec6b47970bf69ed30638d1a20051f961ba792f2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/06/2018
---
# <a name="whats-new-in-power-bi-report-server"></a>Novidades no Power BI Report Server
Saiba mais sobre as novidades no Power BI Report Server. Esta secção abrange áreas de funcionalidades importantes e é atualizada à medida que são lançados novos itens.

Para transferir o Power BI Report Server e o Power BI Desktop otimizado para o Power BI Report Server, aceda a [Relatórios no local com o Power BI Report Server](https://powerbi.microsoft.com/report-server/).

![sugestão](media/whats-new/fyi-tip.png "sugestão") Para obter as atuais notas de versão, consulte [Power BI Report Server - Notas de versão](release-notes.md).

Para informações sobre “Novidades” relacionadas, consulte:

* [Novidades no serviço Power BI](../service-whats-new.md)
* [Novidades no Power BI Desktop](../desktop-latest-update.md)
* [Novidades em aplicativos móveis para o Power BI](../mobile-whats-new-in-the-mobile-apps.md)
* [Blogue da equipa do Power BI](https://powerbi.microsoft.com/blog/)

## <a name="october-2017-release"></a>Versão de outubro de 2017
### <a name="power-bi-report-data-sources"></a>Origens de dados de relatórios do Power BI
Os relatórios do Power BI no Power BI Report Server podem ligar-se a diversas origens de dados. Pode importar dados e agendar atualizações de dados ou consultá-los diretamente através do DirectQuery ou de uma ligação em direto ao SQL Server Analysis Services. Consulte a lista de origens de dados que suportam atualizações agendadas e as que suportam o DirectQuery em "Origens de dados de relatórios do Power BI no Power BI Report Server".

### <a name="scheduled-data-refresh-for-imported-data"></a>Atualização de dados agendada para dados importados
No Power BI Report Server, pode configurar atualizações de dados agendadas para manter os dados atualizados em relatórios do Power BI com um modelo incorporado em vez de uma ligação em direto ou do DirectQuery. Importe os dados com um modelo incorporado, para que seja desassociado da origem de dados original. Este precisa de ser atualizado para manter os dados em dia, o que se consegue através da atualização agendada. Obtenha mais informações sobre a "atualização agendada para relatórios do Power BI no Power BI Report Server".

### <a name="editing-power-bi-reports-from-the-server"></a>Editar relatórios do Power BI a partir do servidor
Pode abrir e editar ficheiros de relatório do Power BI (.pbix) a partir do servidor, mas pode recuperar o ficheiro original que carregou.  Isto significa que, **se os dados tiverem sido atualizados pelo servidor, os dados não serão atualizados quando abrir o ficheiro pela primeira vez**. Precisa de atualizá-lo localmente, de forma manual, para ver a alteração.

### <a name="large-file-uploaddownload"></a>Carregar/transferir ficheiros grandes
Pode carregar ficheiros com um tamanho máximo de 2 GB mas, por predefinição, este limite é de 1 GB nas definições do Report Server no SQL Server Management Studio (SSMS).  Estes ficheiros são armazenados na base de dados, tal como são no caso do SharePoint, e não é necessária uma configuração especial para o catálogo do SQL Server.  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>Aceder a conjuntos de dados partilhados como feeds do OData
Pode aceder a conjuntos de dados partilhados a partir do Power BI Desktop com um feed do OData. Para obter mais informações, consulte [Aceder a conjuntos de dados partilhados como feeds do OData no Power BI Report Server](access-dataset-odata.md).

### <a name="scale-out"></a>Aumentar
Esta versão suporta o aumento. Utilize um balanceador de carga e defina a afinidade de servidor para uma experiência otimizada. Note que o cenário ainda não está otimizado para aumento, pelo que irá ver modelos potencialmente replicados em múltiplos nós. O cenário funciona sem o Balanceador de Carga em Rede e sessões fixas. No entanto, não só irá ver uma utilização aumentada de memória nos nós à medida que o modelo é carregado N vezes, mas também haverá um abrandamento de desempenho entre ligações, pois o modelo é transmitido à medida que atinge um novo nó entre pedidos.  

### <a name="administrator-settings"></a>Definições de administrador
Os administradores podem definir as seguintes propriedades nas Propriedades Avançadas do SSMS para o farm do servidor:

* EnableCustomVisuals: True/False
* EnablePowerBIReportEmbeddedModels: True/False
* EnablePowerBIReportExportData: True/False
* MaxFileSizeMb: Agora, a predefinição é 1000
* ModelCleanupCycleMinutes: Frequência com que verifica modelos para expulsar da memória
* ModelExpirationMinutes: Quantidade de tempo até o modelo expirar e ser expulso, com base na última vez em que foi utilizado
* ScheduleRefreshTimeoutMinutes: Quanto tempo a atualização de dados pode demorar para um modelo. Por predefinição, são duas horas.  Não existe um limite superior fixo.

**Ficheiro de configuração rsreportserver.config**

```
<Configuration>
  <Service>
    <PollingInterval>10</PollingInterval>
    <IsDataModelRefreshService>false</IsDataModelRefreshService>
    <MaxQueueThreads>0</MaxQueueThreads>
  </Service>
</Configuration>
```

### <a name="developer-api"></a>API para Programadores
A API para programadores (API REST) apresentada para o SSRS 2017 foi alargada para dar ao Power BI Report Server compatibilidade com ficheiros Excel e ficheiros .pbix. Um potencial caso de utilização é transferir ficheiros programaticamente do servidor, atualizá-los e, em seguida, voltar a publicá-los. Esta é a única forma de atualizar livros do Excel para modelos do PowerPivot, por exemplo.

Note que existe uma nova API separada para ficheiros grandes, que será atualizada na versão Power BI Report Server do Swagger. 

### <a name="sql-server-analysis-services-ssas-and-the-power-bi-report-server-memory-footprint"></a>SQL Server Analysis Services (SSAS) e o tamanho de memória do Power BI Report Server
Agora, o Power BI Report Server aloja o SQL Server Analysis Services (SSAS) internamente. Não é uma situação específica de uma atualização agendada. Alojar o SSAS pode expandir bastante o tamanho de memória do servidor de relatório. O ficheiro de configuração AS.ini está disponível nos nós de servidor, pelo que, se estiver familiarizado com o SSAS, poderá querer atualizar as definições, incluindo o limite máximo de memória e a colocação em cache do disco, etc. Consulte [Server properties in Analysis Services (Propriedades de servidor no Analysis Services - em inglês)](https://docs.microsoft.com/sql/analysis-services/server-properties/server-properties-in-analysis-services) para obter detalhes.

### <a name="viewing-and-interacting-with-excel-workbooks"></a>Ver e interagir com livros do Excel
O Excel e o Power BI contêm um portefólio de ferramentas sem igual na indústria. Em conjunto, permitem que os analistas empresariais consigam mais facilmente recolher, moldar, analisar e explorar visualmente os dados. Além de ver relatórios do Power BI no portal Web, os utilizadores empresariais podem agora fazer o mesmo com livros do Excel no Power BI Report Server, dando-lhes um único local para publicarem e verem conteúdos self-service do Microsoft BI.

Publicámos uma [explicação passo a passo sobre como adicionar o Office Online Server (OOS) ao seu ambiente de pré-visualização do Power BI Report Server](excel-oos.md). Os clientes com uma conta de Licenciamento de Volume podem transferir o OOS do Centro de Serviço de Licenciamento de Volume gratuitamente, e terão funcionalidade só de visualização. Após a configuração, os utilizadores podem ver e interagir com os livros do Excel que:

* Não têm dependências de origens de dados externas
* Têm uma ligação em direto a uma origem de dados do SQL Server Analysis Services
* Têm um modelo de dados PowerPivot

### <a name="support-for-new-table-and-matrix-visuals"></a>Suporte para novos visuais de tabelas e matrizes
Agora, o Power BI Report Server suporta os novos visuais de tabelas e matrizes do Power BI. Para criar relatórios com estes visuais, precisará de uma versão do Power BI Desktop atualizada para a versão de outubro de 2017. Não pode ser instalada paralelamente com a versão do Power BI Desktop (junho de 2017). Para obter a versão mais recente do Power BI Desktop, na [página de transferência do Power BI Report Server](https://powerbi.microsoft.com/report-server/), selecione **Opções de transferência avançadas**.

## <a name="june-2017"></a>Junho de 2017
* O Power BI Report Server está agora normalmente disponível (GA).

## <a name="may-2017"></a>Maio de 2017
* Pré-visualização do Power BI Report Server disponibilizada
* Capacidade de publicar relatórios do Power BI no local
  * Suporte para visuais personalizados
  * Suporte apenas para ligações em direto ao Analysis Services, com mais origens de dados brevemente disponíveis.
  * Aplicação móvel Power BI Mobile atualizada para mostrar relatórios do Power BI armazenados no Power BI Report Server
* Colaboração melhorada em relatórios com comentários

## <a name="next-steps"></a>Passos seguintes
[Notas de versão do Power BI Report Server](release-notes.md)  
[Manual do utilizador](user-handbook-overview.md)  
[Manual do administrador](admin-handbook-overview.md)  
[Início rápido: instalar o Power BI Report Server](quickstart-install-report-server.md)  
[Instalar o Report Builder](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Transferir o SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

