---
title: "Utilizar a auditoria na sua organização"
description: "Saiba como pode utilizar o auditoria com o Power BI para monitorizar e investigar as ações executadas. Pode utilizar o Centro de segurança e conformidade ou utilizar o PowerShell."
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 12/12/2017
ms.author: maghan
ms.openlocfilehash: 4aca31605b0627929951c34dfb74aa736c89a04f
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2018
---
# <a name="using-auditing-within-your-organization"></a>Utilizar a auditoria na sua organização

<iframe width="560" height="315" src="https://www.youtube.com/embed/zj4kA39jV_4?showinfo=0" frameborder="0" allowfullscreen></iframe>

Saiba como pode utilizar o auditoria com o Power BI para monitorizar e investigar as ações executadas. Pode utilizar o Centro de Segurança e Conformidade ou utilizar o PowerShell

Saber quem está a realizar ações em que item no inquilino Power BI pode ser fundamental para ajudar a sua organização a satisfazer os requisitos, tais como a conformidade regulamentar e a gestão de registos.

Pode filtrar os dados de auditoria por intervalo de datas, utilizador, dashboard, tipo de relatório, conjunto de dados e tipo de atividade. Também pode transferir as atividades num ficheiro csv (valores separados por vírgulas) para análise offline.

> [!NOTE]
> A funcionalidade de auditoria no Power BI está no modo de pré-visualização e disponível em todas as regiões de dados.

## <a name="requirements"></a>Requisitos
Tem de cumprir estes requisitos para aceder aos registos de auditoria:

- Para aceder à secção de auditoria do Centro de Segurança e Conformidade do Office 365, tem de ter uma licença do Exchange Online (incluída nas subscrições do Office 365 Enterprise E3 e E5).
- Tem de ser um administrador global ou ter uma função de administrador do Exchange que oferece acesso ao registo de auditoria. 

  As funções de administrador do Exchange são controladas através do Centro de administração do Exchange. Para obter mais informações, consulte [Permissões no Exchange Online](https://technet.microsoft.com/library/jj200692(v=exchg.150).aspx).

- Se tiver acesso ao registo de auditoria, mas não for um administrador global ou um administrador de Serviço do Power BI, não terá acesso ao portal de Administrador do Power BI. Neste caso, tem de obter uma ligação direta para o Centro de Segurança e Conformidade do Office 365.

## <a name="enabling-auditing-functionality-in-the-power-bi-admin-portal"></a>Ativar a funcionalidade de auditoria no portal de administração do Power BI

Terá de ativar a auditoria para a sua organização para poder trabalhar com os relatórios. Pode fazê-lo através das definições de inquilino do portal de administração.

1. Selecione o **ícone de engrenagem** no canto superior direito.

2. Selecione **Portal de Administração**.
   
   ![](media/service-admin-auditing/powerbi-admin.png)

3. Selecione **Definições de inquilino**.
   
   ![](media/service-admin-auditing/powerbi-admin-tenant-settings.png)

4. Ative **Criar registos de auditoria para auditoria e conformidade da atividade interna**.

5. Selecione **Aplicar**.

O Power BI começa a registar diversas atividades que os utilizadores executam no Power BI. Os registos demoram até 48 horas a aparecer no Centro de Segurança e Conformidade do Office 365. Para obter mais informações sobre como as atividades são registadas, consulte [Lista de atividades auditadas pelo Power BI](#list-of-activities-audited-by-power-bi).

> [!NOTE]
> Para ativar a auditoria do Power BI no seu inquilino, deve ter, pelo menos, uma licença de caixa de correio do Exchange no seu inquilino.

## <a name="accessing-your-audit-logs"></a>Aceder aos seus registos de auditoria

Para auditar os registos do Power BI, tem visitar o Centro de Segurança e Conformidade do Office 365.

1. Selecione o **ícone de engrenagem** no canto superior direito.

2. Selecione **Portal de Administração**.
   
   ![](media/service-admin-auditing/powerbi-admin.png)

3. Selecione **Registos de auditoria**.
 
4. Selecione **Aceder ao Centro de Administração do Office 365**.
   
   ![](media/service-admin-auditing/audit-log-o365-admin-center.png)

Em alternativa, pode navegar para [Office 365 | Segurança e Conformidade](https://protection.office.com/#/unifiedauditlog).

> [!NOTE]
> Para fornecer contas de não-administrador com acesso ao registo de auditoria, terá de atribuir permissões no Centro de Administração do Exchange Online. Por exemplo, pode atribuir um utilizador a um grupo de funções existente, como Gestão da Organização, ou pode criar um novo grupo de funções com a função Registos de Auditoria. Para obter mais informações, consulte [Permissões no Exchange Online](https://technet.microsoft.com/library/jj200692\(v=exchg.150\).aspx).

## <a name="search-only-power-bi-activities"></a>Procurar apenas atividades do Power BI

Efetue o procedimento que se segue para saber restringir os resultados apenas para atividades do Power BI.

1. Na página **Pesquisa de registos de auditoria**, selecione o menu pendente em **Atividades** em **Procurar**.

2. Selecione **Atividades do PowerBI**.
   
   ![](media/service-admin-auditing/audit-log-search-filter-by-powerbi.png)

3. Selecione em qualquer lugar fora da caixa de seleção para fechá-lo.

As suas pesquisas serão agora filtradas apenas para as atividades do Power BI.

## <a name="search-the-audit-logs-by-date"></a>Procurar os registos de auditoria por data

Pode procurar os registos por intervalo de datas, utilizando o campo "Data de início" e "Data de fim". Os últimos sete dias são selecionados por predefinição. A data e hora são apresentados no formato Hora Universal Coordenada (UTC). O intervalo de data máximo que pode especificar é 90 dias. É apresentado um erro se o intervalo de datas selecionadas for superior a 90 dias.

> [!NOTE]
> Se estiver a utilizar o intervalo de datas máximo de 90 dias, selecione a hora atual para a data de início. Caso contrário, vai receber uma mensagem de erro a informar que a data de início é anterior à data de fim. Se ativou a auditoria para os últimos 90 dias, não é possível iniciar o intervalo de datas máximo antes da data de auditoria ser ativada.

![](media/service-admin-auditing/search-audit-log-by-date.png)

## <a name="search-the-audit-logs-by-users"></a>Procurar os registos de auditoria por utilizador

Pode procurar entradas de registo de auditoria relativas a atividades realizadas por utilizadores específicos. Para tal, introduza um ou mais nomes de utilizador no campo "Utilizadores".  Isto seria o nome de utilizador com que iniciam sessão no Power BI. Aspeto de um endereço de e-mail.
Deixe esta caixa em branco para apresentar as entradas de todos os utilizadores (e as contas de serviço) na sua organização.

![](media/service-admin-auditing/search-audit-log-by-user.png)

## <a name="viewing-search-results"></a>Ver os resultados da pesquisa

Depois de premir o botão de procura, os resultados da pesquisa são carregados e após alguns instantes são apresentados em Resultados. Quando a pesquisa estiver concluída, é apresentado o número de resultados encontrado. 

> [!NOTE]
> Será apresentado um máximo de 1000 eventos. Se mais de 1000 eventos cumprirem os critérios de pesquisa, são apresentados os 1000 eventos mais recentes.

Os resultados contêm as seguintes informações sobre cada evento devolvido pela pesquisa.

| **Coluna** | **Definição** |
| --- | --- |
| Data |A data e a hora (no formato UTC) em que ocorreu o evento. |
| Endereço IP |O endereço IP do dispositivo que foi utilizado quando a atividade foi registada. O endereço IP é apresentado no formato de endereço IPv4 ou IPv6. |
| Utilizador |O utilizador (ou a conta de serviço) que efetuou a ação que, por sua vez, acionou o evento. |
| Atividade |A atividade efetuada pelo utilizador. Este valor corresponde às atividades que selecionou na lista pendente Activitiesdrop. Para um evento do registo de auditoria de administrador do Exchange, o valor nesta coluna é um cmdlet do Exchange. |
| Item |O objeto criado ou modificado como resultado da atividade correspondente. Por exemplo, o ficheiro visualizado ou modificado ou a conta de utilizador que foi atualizada. Nem todas as atividades têm um valor nesta coluna. |
| Detalhe |Detalhe adicional sobre uma atividade. Nem todas as atividades terão um valor. |

> [!NOTE]
> Selecione um cabeçalho de coluna em Resultados para ordenar os resultados. Pode ordenar os resultados de A a Z ou de Z a A. Clique no cabeçalho Data para ordenar os resultados dos mais antigos para os mais recentes ou dos recentes para os mais antigos.

## <a name="view-the-details-for-an-event"></a>Ver os detalhes de um evento

Pode ver mais detalhes sobre um evento selecionando o registo de eventos na lista de resultados da pesquisa. É apresentada uma página de detalhes que contém as propriedades detalhadas do registo de eventos. As propriedades apresentadas dependem do serviço do Office 365 em que decorre o evento. Para apresentar detalhes adicionais, selecione **Obter mais informações**.

A tabela seguinte fornece detalhes sobre o que pode ver apresentado.

| **Parâmetro ou Evento** | **Descrição** | **Detalhes Adicionais** |
| --- | --- | --- |
| Relatório do Power BI transferido |Esta atividade é registada sempre que um relatório é transferido. |Nome do Relatório, Nome do Conjunto de Dados |
| Criar relatório |Esta atividade é registada sempre que é criado um novo relatório. |Nome do Relatório, Nome do Conjunto de Dados |
| Editar Relatório |Esta atividade é registada sempre que um relatório é editado. |Nome do Relatório, Nome do Conjunto de Dados |
| Criar conjunto de dados |Esta atividade é registada sempre que é criado um conjunto de dados. |Nome do Conjunto de Dados, DataConnectivityMode |
| Eliminar Conjunto de Dados |Esta atividade é registada sempre que um conjunto de dados é eliminado. |Nome do Conjunto de Dados, DataConnectivityMode |
| Criar a aplicação Power BI |Esta atividade é registada sempre que é criada uma aplicação Power BI. |Nome da aplicação, Permissões, Nome da Área de Trabalho |
| Instalar a aplicação Power BI |Esta atividade é registada sempre que uma aplicação Power BI é instalada. |Nome da aplicação |
| Atualizar a aplicação Power BI |Esta atividade é registada sempre que uma aplicação Power BI é atualizada. |Nome da aplicação, Permissões, Nome da Área de Trabalho |
| Avaliação expandida do Power BI iniciada |Esta atividade é registada sempre que um utilizador aceita a versão de avaliação profissional expandida, que funciona até 31 de maio de 2018. | |
| Conjunto de dados analisado do Power BI |Esta atividade é registada sempre que um conjunto de dados do Power BI é analisado no Excel. | |
| Gateway do Power BI criado |Esta atividade é registada sempre que é criado um novo gateway. |Nome do Gateway, Tipo de Gateway |
| Gateway do Power BI eliminado |Esta atividade é registada sempre que um gateway é eliminado. |Nome do Gateway, Tipo de Gateway |
| Origem de dados adicionada ao gateway do Power BI |Esta atividade é registada sempre que uma origem de dados é adicionada ao gateway. |Nome do Gateway, Tipo de Gateway, Nome da Origem de Dados, Tipo de Origem de Dados |
| Origem de dados removida do gateway do Power BI |Esta atividade é registada sempre que uma origem de dados é removida de um gateway. |Nome do Gateway, Tipo de Gateway, Nome da Origem de Dados, Tipo de Origem de Dados |
| Administradores do gateway do Power BI alterados |Esta atividade é registada sempre que os administradores de um gateway são alterados (adicionados/removidos). |Nome do Gateway, Utilizadores Adicionados, Utilizadores Removidos |
| Os utilizadores da origem de dados do gateway Power IB foram alterados |Esta atividade é registada sempre que os utilizadores de um gateway são alterados (adicionados/removidos). |Nome do Gateway, Utilizadores Adicionados, Utilizadores Removidos |
| SetScheduledRefresh |Esta atividade é registada sempre que uma nova atualização está agendada para um conjunto de dados. |Nome do Conjunto de Dados, Frequência de Atualização (em minutos) |

## <a name="using-powershell-to-search"></a>Utilizar o PowerShell para fazer pesquisas

Pode utilizar o PowerShell para aceder aos registos de auditoria com base no início de sessão. Isto é efetuado quando acede ao Exchange Online. Segue-se um exemplo de um comando para extrair entradas de registo de auditoria do Power BI.

> [!NOTE]
> Para utilizar o comando New-PSSession, a sua conta necessita de uma licença do Exchange Online atribuída a este e necessita de aceder ao registo de auditoria do seu inquilino.

```
Set-ExecutionPolicy RemoteSigned

$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2016 -EndDate 9/15/2016 -RecordType PowerBI -ResultSize 1000 | Format-Table | More
```

Para obter mais informações sobre a ligação ao Exchange Online, consulte [Ligar ao PowerShell do Exchange Online](https://technet.microsoft.com/library/jj984289\(v=exchg.160\).aspx).

Para obter mais informações sobre os parâmetros e a utilização do comando Search-UnifiedAuditLog, consulte [Search-UnifiedAuditLog](https://technet.microsoft.com/library/mt238501\(v=exchg.160\).aspx).

Para ver um exemplo de utilização do PowerShell para procurar o registo de auditoria e, em seguida, atribuir licenças do Power BI Pro, com base nas entradas, consulte [Utilizar o registo de auditoria do Power BI e o PowerShell para atribuir licenças do Power BI Pro](https://powerbi.microsoft.com/blog/using-power-bi-audit-log-and-powershell-to-assign-power-bi-pro-licenses/).

## <a name="export-the-power-bi-audit-log"></a>Exportar o registo de auditoria do Power BI

Pode exportar o registo de auditoria do Power BI para um ficheiro csv.

1. Selecione **Exportar resultados**.

2. Selecione **Guardar resultados carregados** ou **Transferir todos os resultados**.
   
   ![](media/service-admin-auditing/export-auditing-results.png)

## <a name="record-and-user-types"></a>Tipos de registo e de utilizador

As entradas de registo de auditoria terão um RecordType e UserType como parte dos detalhes da entrada. Todas as entradas do Power BI terão um RecordType de 20.

Para obter uma listagem completa, consulte [Propriedades detalhadas no registo de auditoria do Office 365](https://support.office.com/article/Detailed-properties-in-the-Office-365-audit-log-ce004100-9e7f-443e-942b-9b04098fcfc3)

## <a name="list-of-activities-audited-by-power-bi"></a>Lista de atividades auditadas pelo Power BI

| Atividade | Descrição | Detalhes adicionais |
| --- | --- | --- |
| CreateDashboard |Esta atividade é registada sempre que é criado um novo dashboard. |- Nome do Dashboard. |
| EditDashboard |Esta atividade é registada sempre que o nome de um dashboard é alterado. |- Nome do Dashboard. |
| DeleteDashboard |Esta atividade é registada sempre que um dashboard é eliminado. |- Nome do Dashboard. |
| PrintDashboard |Este evento é registado sempre que um dashboard é impresso. |- Nome do Dashboard.<br/>- Nome do conjunto de dados |
| ShareDashboard |Esta atividade é registada sempre que um dashboard é partilhado. |- Nome do Dashboard.<br/>- Endereço de e-mail do destinatário.<br/>- Nome do conjunto de dados.<br>- Partilhar de novo permissões. |
| ViewDashboard |Esta atividade é registada sempre que um dashboard é visualizado. |- Nome do Dashboard. |
| ExportTile |Este evento é registado sempre que os dados são exportados de um mosaico do dashboard. |- Nome do mosaico.<br/>- Nome do conjunto de dados. |
| DeleteReport |Esta atividade é registada sempre que um relatório é eliminado. |- Nome do relatório. |
| ExportReport |Este evento é registado sempre que os dados são exportados de um mosaico de relatório. |- Nome do relatório.<br/>- Nome do conjunto de dados. |
| PrintReport |Este evento é registado sempre que um relatório é impresso. |- Nome do relatório.<br/>- Nome do conjunto de dados. |
| PublishToWebReport |Este evento é registado sempre que um relatório é publicado na Web. |- Nome do relatório.<br/>- Nome do conjunto de dados. |
| ViewReport |Esta atividade é registada sempre que um relatório é visualizado. |- Nome do relatório. |
| ExploreDataset |Este evento é registado sempre que seleciona um conjunto de dados para explorá-lo. |- Nome do conjunto de dados |
| DeleteDataset |Este evento é registado sempre que um conjunto de dados é eliminado. |- Nome do conjunto de dados. |
| CreateOrgApp |Esta atividade é registada sempre que é criado um pacote de conteúdos organizacional. |- Nome do pacote de conteúdo organizacional.<br/>- Nomes do dashboard.<br/>- Nomes dos relatórios.<br/>- Nomes do conjunto de dados. |
| CreateGroup |Esta atividade é desencadeada sempre que é criado um grupo. |- Nome do grupo. |
| AddGroupMembers |Esta atividade é registada sempre que um membro é adicionado a uma área de trabalho de grupo do Power BI. |- Nome do grupo.<br/>- Endereços de e-mail. |
| UpdatedAdminFeatureSwitch |Este evento é registado sempre que um comutador da funcionalidade de administração é alterado. |- Nome do comutador.<br/>- Novo estado do comutador. |
| OptInForProTrial |Este evento é registado quando um utilizador optar por experimentar o Power BI Pro no serviço. |- Endereço de e-mail |

## <a name="next-steps"></a>Próximos passos

[Portal de Administração do Power BI](service-admin-portal.md)  
[Power BI Premium – o que é?](service-premium.md)  
[Comprar o Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[Permissões no Exchange Online](https://technet.microsoft.com/library/jj200692\(v=exchg.150\).aspx)  
[Ligar ao PowerShell do Exchange Online](https://technet.microsoft.com/library/jj984289\(v=exchg.160\).aspx)  
[Search-UnifiedAuditLog](https://technet.microsoft.com/library/mt238501\(v=exchg.160\).aspx)  
[Propriedades detalhadas no registo de auditoria do Office 365](https://support.office.com/article/Detailed-properties-in-the-Office-365-audit-log-ce004100-9e7f-443e-942b-9b04098fcfc3)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)