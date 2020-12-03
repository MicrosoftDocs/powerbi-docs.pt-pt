---
title: Controlar as atividades dos utilizadores no Power BI
description: Saiba como pode utilizar registos de atividades e a auditoria com o Power BI para monitorizar e investigar as ações executadas.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 08/20/2020
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 3c1e2b4513b3ac920d447ef0b8195c76c1ec2a04
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413754"
---
# <a name="track-user-activities-in-power-bi"></a>Controlar as atividades dos utilizadores no Power BI

Saber quem está a realizar ações em que item no inquilino Power BI pode ser fundamental para ajudar a sua organização a satisfazer os requisitos, como a conformidade regulamentar e a gestão de registos. Com o Power BI, tem duas opções para controlar a atividade de utilizador: O [registo de atividade do Power BI](#use-the-activity-log) e o [registo de auditoria unificado](#use-the-audit-log). Estes registos contém uma cópia completa dos [dados de auditoria do Power BI](#operations-available-in-the-audit-and-activity-logs), mas há várias diferenças principais, tal como é resumido na seguinte tabela.

| **Registo de auditoria unificado** | **Registo de atividades do Power BI** |
| --- | --- |
| Inclui eventos do SharePoint Online, Exchange Online, Dynamics 365 e outros serviços além dos eventos de auditoria do Power BI. | Inclui apenas os eventos de auditoria do Power BI. |
| Apenas os utilizadores com a função Ver Apenas Registos de Auditoria ou permissões dos Registos de Auditoria têm acesso, como os administradores globais e os auditores. | Os administradores globais e os administradores do serviço Power BI têm acesso. |
| Os administradores globais e os auditores podem procurar no registo de auditoria unificado através do Centro de Segurança do Microsoft 365 e do Centro de Conformidade do Microsoft 365. | Ainda não existe uma interface de utilizador para pesquisar o registo de atividades. |
| Os administradores globais e os auditores podem transferir as entradas de registo de auditoria ao utilizar as APIs de Gestão e os cmdlets do Microsoft 365. | Os administradores globais e os administradores do serviço Power BI podem transferir as entradas de registo de atividades ao utilizar uma API REST do Power BI e o cmdlet de gestão. |
| Mantém os dados de auditoria por 90 dias | Mantém os dados de atividade por 30 dias (pré-visualização pública). |
| Retém dados de auditoria, mesmo que o inquilino seja transferido para outra região do Azure. | Não retém dados de auditoria quando o inquilino seja transferido para outra região do Azure. |


## <a name="use-the-activity-log"></a>Utilizar o registo de atividades

> [!NOTE]
> O registo de atividades não é suportado para o Microsoft Cloud Deutschland. Saiba mais sobre as limitações de serviço da cloud da Alemanha em [Perguntas Mais Frequentes sobre o Power BI para clientes da cloud da Alemanha](service-govde-faq.md).


Enquanto administrador do serviço Power BI, pode analisar a utilização de todos os recursos do Power BI ao nível do inquilino ao utilizar relatórios personalizados com base no registo de atividades do Power BI. Pode transferir as atividades ao utilizar a API REST ou o cmdlet do PowerShell. Também pode filtrar os dados de atividade por intervalo de datas, utilizador e tipo de atividade.

### <a name="activity-log-requirements"></a>Requisitos do registo de atividades

Tem de cumprir estes requisitos para aceder aos registos de atividades do Power BI:

- Tem de ser um administrador global ou um administrador do serviço Power BI.
- Instalou os [cmdlets de Gestão do Power BI](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt) localmente ou utiliza os cmdlets de Gestão do Power BI no Azure Cloud Shell.

### <a name="activityevents-rest-api"></a>API REST do ActivityEvents

Pode utilizar uma aplicação administrativa baseada nas APIs REST do Power BI para exportar eventos de atividade para um arquivo de blob ou base de dados SQL. Em seguida, pode criar um relatório de utilização personalizado sobre os dados exportados. Na chamada à REST API do **ActivityEvents**, tem de especificar uma data de início e data de fim e, opcionalmente, um filtro para selecionar atividades por tipo de atividade ou ID de utilizador. Como o registo de atividades pode conter uma grande quantidade de dados, a API **ActivityEvents** só suporta atualmente a transferência de até um dia de dados por pedido. Por outras palavras, a data de início e a data de fim têm de especificar o mesmo dia, como no seguinte exemplo. Certifique-se de que especifica os valores DataTime no formato UTC.

```
https://api.powerbi.com/v1.0/myorg/admin/activityevents?startDateTime='2019-08-31T00:00:00'&endDateTime='2019-08-31T23:59:59'
```

Se o número de entradas for grande, a API **ActivityEvents** devolve apenas cerca de 5000 a 10 000 entradas e um token de continuação. Chame a API **ActivityEvents** novamente com o token de continuação para obter o próximo lote de entradas e assim sucessivamente, até que tenha obtido todas as entradas e deixe de receber um token de continuação. O seguinte exemplo mostra como utilizar o token de continuação.

```
https://api.powerbi.com/v1.0/myorg/admin/activityevents?continuationToken='%2BRID%3ARthsAIwfWGcVAAAAAAAAAA%3D%3D%23RT%3A4%23TRC%3A20%23FPC%3AARUAAAAAAAAAFwAAAAAAAAA%3D'
```

Independentemente do número de entradas devolvidas, se os resultados incluírem um token de continuação, certifique-se de que chama a API novamente com esse token para obter os dados restantes, até que um token de continuação não volte a ser devolvido. É possível que uma chamada devolva até mesmo um token de continuação sem qualquer entrada de evento. O seguinte exemplo mostra como fazer um ciclo com um token de continuação devolvido na resposta:

```
while(response.ContinuationToken != null)
{
   // Store the activity event results in a list for example
    completeListOfActivityEvents.AddRange(response.ActivityEventEntities);

    // Make another call to the API with continuation token
    response = GetPowerBIActivityEvents(response.ContinuationToken)
}
completeListOfActivityEvents.AddRange(response.ActivityEventEntities);
```
> [!NOTE]
> Poderá demorar até 24 horas para que todos os eventos sejam apresentados, embora os dados completos sejam normalmente disponibilizados muito mais rapidamente.
>
>
Para saber mais sobre como utilizar a API REST do Power BI, incluindo exemplos de como obter eventos de atividade de auditoria, veja [Administrador – Obter Eventos de Atividade](/rest/api/power-bi/admin/getactivityevents) na documentação de referência da API REST do Power BI.

### <a name="get-powerbiactivityevent-cmdlet"></a>Cmdlet Get-PowerBIActivityEvent

Transfira eventos de atividade ao utilizar os cmdlets do Power BI Management para PowerShell. O cmdlet **Get-PowerBIActivityEvent** processa automaticamente o token de continuação. O cmdlet **Get-PowerBIActivityEvent** utiliza um parâmetro StartDateTime e um parâmetro EndDateTime com as mesmas restrições que a API REST **ActivityEvents**. Por outras palavras, a data de início e a data de fim têm de fazer referência ao mesmo valor de data, porque só é possível obter os dados de atividade para um dia de cada vez.

O seguinte script demonstra como transferir todas as atividades do Power BI. O comando converte os resultados do JSON em objetos .NET para obter acesso direto às propriedades individuais da atividade. Estes exemplos mostram os carimbos de data/hora possíveis menores e maiores para um dia, para garantir que não são perdidos eventos.

```powershell
Login-PowerBI

$activities = Get-PowerBIActivityEvent -StartDateTime '2019-08-31T00:00:00' -EndDateTime '2019-08-31T23:59:59' | ConvertFrom-Json

$activities.Count
$activities[0]

```

### <a name="filter-activity-data"></a>Filtrar dados de atividade

Pode filtrar eventos de atividade por tipo de atividade e ID de utilizador. O seguinte script demonstra como transferir apenas os dados de evento para a atividade **ViewDashboard**. Para obter informações adicionais sobre os parâmetros suportados, utilize o comando `Get-Help Get-PowerBIActivityEvent`.

```powershell
Login-PowerBI

$activities = Get-PowerBIActivityEvent -StartDateTime '2019-08-31T00:00:00' -EndDateTime '2019-08-31T23:59:59' -ActivityType 'ViewDashboard' | ConvertFrom-Json

$activities.Count
$activities[0]

```

> [!NOTE]
> Está disponível uma amostra do PowerShell para o ajudar a aprender a filtrar e obter eventos do registo de atividades do Power BI. Para obter mais informações, veja [Aceder ao registo de atividades do Power BI](../guidance/admin-activity-log.md).

## <a name="use-the-audit-log"></a>Utilizar o registo de auditoria

Se a sua tarefa for controlar as atividades de utilizador no Power BI e no Microsoft 365, pode trabalhar com a auditoria no Centro de Conformidade e Segurança do Office 365 ou utilizar o PowerShell. A auditoria depende da funcionalidade no Exchange Online, que é aprovisionada automaticamente para suportar o Power BI.

Pode filtrar os dados de auditoria por intervalo de datas, utilizador, dashboard, tipo de relatório, conjunto de dados e tipo de atividade. Também pode transferir as atividades num ficheiro csv (valores separados por vírgulas) para analisar offline.

### <a name="audit-log-requirements"></a>Requisitos do registo de auditoria

Tem de cumprir estes requisitos para aceder aos registos de auditoria:

- Para aceder ao registo de auditoria, tem de ser administrador global ou ter a função Registos de Auditoria ou Ver Apenas Registos de Auditoria no Exchange Online. Por predefinição, os grupos de funções de Gestão de Conformidade e Gestão da Organização têm estas funções atribuídas na página **Permissões** do centro de administração do Exchange. Para obter mais informações sobre as funções que podem ver registos de auditoria, veja [Requisitos para pesquisar o registo de auditoria](/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance?view=o365-worldwide#requirements-to-search-the-audit-log).

    Para dar acesso a contas de utilizadores não administradores ao registo de auditoria, adicione esses utilizadores como membros de um daqueles grupos de funções. Se quiser fazê-lo de outra forma, pode criar um grupo de funções personalizado no centro de administração do Exchange, atribuir a função Registos de Auditoria ou Ver Apenas Registos de Auditoria ao mesmo e, depois, adicionar a conta do utilizador não administrador ao grupo novo. Para obter mais informações, veja [Manage role groups in Exchange Online](/Exchange/permissions-exo/role-groups) (Gerir grupos de funções no Exchange Online).

    Se não conseguir aceder ao centro de administração do Exchange a partir do centro de administração do Microsoft 365, aceda a https://outlook.office365.com/ecp e inicie sessão com as suas credenciais.

- Se tiver acesso ao registo de auditoria, mas não for um administrador global ou um administrador de Serviço do Power BI, não poderá aceder ao portal de Administrador do Power BI. Neste caso, utilize uma ligação direta para o [Centro de Conformidade e Segurança do Office 365](https://sip.protection.office.com/#/unifiedauditlog).

### <a name="access-your-audit-logs"></a>Aceder aos seus registos de auditoria

Para aceder aos registos, confirme primeiro que ativa o registo no Power BI. Para obter mais informações, veja [Registos de auditoria](service-admin-portal.md#audit-logs) na documentação do portal de administração. Poderá existir um atraso de 48 horas entre a altura em que ativa a auditoria e o momento em que pode ver os dados de auditoria. Se não vir logo os seus dados, consulte os registos de auditoria mais tarde. Pode existir um intervalo de tempo semelhante entre obter a permissão para ver os registos de auditoria e ter acesso aos mesmos.

Os registos de auditoria do Power BI estão disponíveis diretamente através do [Centro de Conformidade e Segurança do Office 365](https://sip.protection.office.com/#/unifiedauditlog). Também existe uma ligação no portal de administração do Power BI:

1. No Power BI, selecione o **ícone de engrenagem** no canto superior direito e, em seguida, selecione **Portal de administração**.

   ![Captura de ecrã do menu pendente de engrenagem com a opção do Portal de administração em destaque.](media/service-admin-auditing/powerbi-admin.png)

1. Selecione **Registos de auditoria**.

1. Selecione **Aceder ao Centro de Administração do Microsoft 365**.

   ![Captura de ecrã do Portal de administração com as opções Registos de auditoria e Aceder ao Centro de Administração do Microsoft 365 realçadas.](media/service-admin-auditing/audit-log-o365-admin-center.png)

### <a name="search-only-power-bi-activities"></a>Procurar apenas atividades do Power BI

Restrinja os resultados só para atividades do Power BI. Para tal, siga estes passos. Para obter uma lista de atividades, veja a [lista de atividades auditadas pelo Power BI](#operations-available-in-the-audit-and-activity-logs) mais adiante neste artigo.

1. Na página **Pesquisa de registo de auditoria**, em **Pesquisa**, selecione a lista pendente de **Atividades**.

2. Selecione **Atividades do Power BI**.

   ![Captura de ecrã a mostrar a Pesquisa de registo de auditoria, com atividades do Power B I em destaque.](media/service-admin-auditing/audit-log-search-filter-by-powerbi.png)

3. Selecione em qualquer lugar fora da caixa de seleção para fechar.

As suas pesquisas apenas vão devolver atividades do Power BI.

### <a name="search-the-audit-logs-by-date"></a>Procurar os registos de auditoria por data

Pode procurar os registos por intervalo de datas com o campo **Data de início** e **Data de fim**. A seleção predefinida é os últimos sete dias. O ecrã apresenta a data e hora no formato Hora Universal Coordenada (UTC). O intervalo de data máximo que pode especificar é 90 dias. 

Receberá um erro se o intervalo de datas selecionadas for superior a 90 dias. Se estiver a utilizar o intervalo de datas máximo de 90 dias, selecione a hora atual para a **Data de início**. Caso contrário, vai receber uma mensagem de erro a informar que a data de início é anterior à data de fim. Se tiver ativado a auditoria para os últimos 90 dias, não poderá iniciar o intervalo de datas antes da data de auditoria ser ativada.

![Captura de ecrã a mostrar a Pesquisa de registo de auditoria, com as opções Data de Início e Data de Fim em destaque.](media/service-admin-auditing/search-audit-log-by-date.png)

### <a name="search-the-audit-logs-by-users"></a>Procurar os registos de auditoria por utilizador

Pode procurar entradas de registo de auditoria relativas a atividades efetuadas por utilizadores específicos. Introduza um ou mais nomes de utilizador no campo **Utilizadores**. O nome do utilizador tem o aspeto de um endereço de e-mail. É a conta com a qual os utilizadores iniciam sessão no Power BI. Deixe esta caixa em branco para apresentar as entradas de todos os utilizadores (e as contas de serviço) na sua organização.

![Captura de ecrã a mostrar a Pesquisa de registo de auditoria, com os Utilizadores em destaque.](media/service-admin-auditing/search-audit-log-by-user.png)

### <a name="view-search-results"></a>Ver resultados da pesquisa

Depois de selecionar **Pesquisar**, os resultados da pesquisa são carregados. Após alguns instantes, são apresentados em **Resultados**. Quando a pesquisa terminar, o ecrã apresenta o número de resultados encontrado. A **Pesquisa de registo de auditoria** apresenta um máximo de 1000 eventos. Se mais de 1000 eventos cumprirem os critérios de pesquisa, a aplicação apresenta os 1000 eventos mais recentes.

#### <a name="view-the-main-results"></a>Ver os resultados principais

A área **Resultados** tem as seguintes informações para cada evento devolvido pela pesquisa. Selecione um cabeçalho de coluna em **Resultados** para ordenar os resultados.

| **Coluna** | **Definição** |
| --- | --- |
| Data |A data e a hora (no formato UTC) em que ocorreu o evento. |
| Endereço IP |O endereço IP do dispositivo usado para a atividade registada. A aplicação apresenta o endereço IP no formato de endereço IPv4 ou IPv6. |
| Utilizador |O utilizador (ou a conta de serviço) que efetuou a ação que, por sua vez, acionou o evento. |
| Atividade |A atividade realizada pelo utilizador. Este valor corresponde às atividades que selecionou na lista pendente **Atividades**. Para um evento do registo de auditoria de administrador do Exchange, o valor nesta coluna é um cmdlet do Exchange. |
| Item |O objeto criado ou modificado devido à atividade correspondente. Por exemplo, o ficheiro visto ou modificado, ou a conta de utilizador atualizada. Nem todas as atividades têm um valor nesta coluna. |
| Detalhe |Os detalhes adicionais sobre uma atividade. Nem todas as atividades têm um valor. |

#### <a name="view-the-details-for-an-event"></a>Ver os detalhes de um evento

Para ver mais detalhes sobre um evento, selecione o registo de eventos na lista de resultados da pesquisa. Aparece uma página **Detalhes** que contém as propriedades detalhadas do registo de eventos. A página **Detalhes** apresenta propriedades consoante o serviço do Microsoft 365 em que decorre o evento.

Para apresentar estes detalhes, selecione **Mais informações**. Todas as entradas do Power BI têm um valor de 20 para a propriedade RecordType. Para obter informações acerca de outras propriedades, veja [Propriedades detalhadas no registo de auditoria](/office365/securitycompliance/detailed-properties-in-the-office-365-audit-log/).

   ![Captura de ecrã da caixa de diálogo de detalhes da auditoria com a opção Mais informações em destaque.](media/service-admin-auditing/audit-details.png)

### <a name="export-search-results"></a>Exportar resultados da pesquisa

Para exportar o registo de auditoria do Power BI para um ficheiro CSV, siga estes passos.

1. Selecione **Exportar resultados**.

1. Selecione **Guardar resultados carregados** ou **Transferir todos os resultados**.

    ![Captura de ecrã a mostrar a opção Exportar resultados, com a opção Transferir todos os resultados em destaque.](media/service-admin-auditing/export-auditing-results.png)

### <a name="use-powershell-to-search-audit-logs"></a>Utilize o PowerShell para pesquisar registos de auditoria

Também pode utilizar o PowerShell para aceder aos registos de auditoria com base no início de sessão. O exemplo seguinte mostra como ligar ao PowerShell do Exchange Online e utilizar, depois, o comando [Search-UnifiedAuditLog](/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog?view=exchange-ps/) para obter entradas do registo de auditoria do Power BI. Para executar o script, um administrador tem de lhe atribuir as permissões adequadas, conforme descrito na secção [Requisitos de registo de auditoria](#audit-log-requirements).

```powershell
Set-ExecutionPolicy RemoteSigned

$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2018 -EndDate 9/15/2018 -RecordType PowerBI -ResultSize 1000 | Format-Table | More
```

### <a name="use-powershell-to-export-audit-logs"></a>Utilizar o PowerShell para exportar registos de auditoria

Também pode utilizar o PowerShell para exportar os resultados da sua pesquisa de registos de auditoria. O exemplo seguinte mostra como enviar a partir do comando [Search-UnifiedAuditLog](/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog?view=exchange-ps/) e exportar os resultados através do cmdlet [Export-Csv](/powershell/module/microsoft.powershell.utility/export-csv). Para executar o script, um administrador tem de lhe atribuir as permissões adequadas, conforme descrito na secção [Requisitos de registo de auditoria](#audit-log-requirements).

```powershell
$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2019 -EndDate 9/15/2019 -RecordType PowerBI -ResultSize 5000 |
Export-Csv -Path "c:\temp\PowerBIAuditLog.csv" -NoTypeInformation

Remove-PSSession $Session
```

Para obter mais informações sobre a ligação ao Exchange Online, veja [Ligar ao PowerShell do Exchange Online](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell/). Para obter outro exemplo de utilização do PowerShell com registos de auditoria, veja [Using Power BI audit log and PowerShell to assign Power BI Pro licenses](https://powerbi.microsoft.com/blog/using-power-bi-audit-log-and-powershell-to-assign-power-bi-pro-licenses/) (Utilizar o registo de auditoria do Power BI e o PowerShell para atribuir licenças do Power BI Pro).

## <a name="operations-available-in-the-audit-and-activity-logs"></a>Operações disponíveis nos registos de auditoria e de atividades

As seguintes operações estão disponíveis tanto no registo de auditoria como no registo de atividades.

| Nome amigável                                     | Nome da operação                              | Notas                                  |
|---------------------------------------------------|---------------------------------------------|------------------------------------------|
| Tabelas em destaque do Power BI no Excel acedidas | AnalyzedByExternalApplication |    |
| Origem de dados adicionada ao gateway do Power BI             | AddDatasourceToGateway                      |                                          |
| Acesso à pasta do Power BI adicionado                      | AddFolderAccess                             | Não é atualmente utilizado                       |
| Membros do grupo do Power BI adicionados                      | AddGroupMembers                             |                                          |
| Conta de armazenamento do fluxo de dados anexada ao inquilino pelo administrador | AdminAttachedDataflowStorageAccountToTenant | Não é atualmente utilizado                       |
| Conjunto de dados analisado do Power BI                         | AnalyzedByExternalApplication               | Gerado quando os utilizadores interagem com o serviço                                         |
| Relatório do Power BI analisado                          | AnalyzeInExcel                              |                                          |
| Atribuída uma área de trabalho a um pipeline de implementação                          | AssignWorkspaceToPipeline                              |                                          |
| Conta de armazenamento do fluxo de dados anexada                 | AttachedDataflowStorageAccount              |                                          |
| Conjunto de dados do Power BI vinculado ao gateway                | BindToGateway                               |                                          |
| Atualização do fluxo de dados cancelada                        | CancelDataflowRefresh                       |                                          |
| Estado de capacidade alterado                            | ChangeCapacityState                         |                                          |
| Atribuição de utilizador da capacidade alterada                  | UpdateCapacityUsersAssignment               |                                          |
| Ligações de dados do Power BI alteradas              | SetAllConnections                           |                                          |
| Administradores do gateway do Power BI alterados                   | ChangeGatewayAdministrators                 |                                          |
| Utilizadores da origem de dados do gateway do Power BI alterados        | ChangeGatewayDatasourceUsers                |                                          |
| Elemento visual personalizado organizacional criado                          | InsertOrganizationalGalleryItem                                |                                          |
| Pacote de conteúdos organizacional do Power BI criado      | CreateOrgApp                                |                                          |
| Pipeline de implementação criado      | CreateAlmPipeline                                |                                          |
| Aplicação do Power BI criada                              | CreateApp                                   |                                          |
| Dashboard do Power BI criado                        | CreateDashboard                             |                                          |
| Fluxo de dados do Power BI criado                         | CreateDataflow                              |                                          |
| Conjunto de dados do Power BI criado                          | CreateDataset                               |                                          |
| Subscrição de e-mail do Power BI criada               | CreateEmailSubscription                     |                                          |
| Pasta do Power BI criada                           | CreateFolder                                |                                          |
| Gateway do Power BI criado                          | CreateGateway                               |                                          |
| Grupo do Power BI criado                            | CreateGroup                                 |                                          |
| Relatório do Power BI criado                           | CreateReport <sup>1</sup>                                |                                          |
| Criar a área de trabalho da aplicação de modelo do Power BI | CreateTemplateApp   |
| Criar o pedido de instalação da aplicação de modelo do Power BI | CreateTemplateAppInstallTicket |
| Criar o pacote de aplicações de modelo do Power BI | CreateTemplateAppPackage |
| O elemento visual personalizado pediu um token de acesso do Azure Active Directory                           | GenerateCustomVisualAADAccessToken                                |                                          |
| O elemento visual personalizado pediu um token de acesso do Office Web Apps                           | GenerateCustomVisualWACAccessToken                                |                                          |
| Fluxo de dados migrado para a conta de armazenamento externa     | DataflowMigratedToExternalStorageAccount    | Não é atualmente utilizado                       |
| Permissões do fluxo de dados adicionadas                        | DataflowPermissionsAdded                    | Não é atualmente utilizado                       |
| Permissões do fluxo de dados removidas                      | DataflowPermissionsRemoved                  | Não é atualmente utilizado                       |
| Elemento visual personalizado organizacional eliminado     | DeleteOrganizationalGalleryItem                                |                                          |
| Pipeline de implementação eliminado      | DeleteAlmPipeline                                |                                          |
| Pacote de conteúdos organizacional do Power BI criado      | DeleteOrgApp                                |                                          |
| Comentário do Power BI eliminado                          | DeleteComment                               |                                          |
| Dashboard do Power BI eliminado                        | DeleteDashboard                             | Não é atualmente utilizado                       |
| Fluxo de dados do Power BI eliminado                         | DeleteDataflow                              | Não é atualmente utilizado                       |
| Conjunto de dados do Power BI eliminado                          | DeleteDataset                               |                                          |
| Subscrição de e-mail do Power BI eliminada               | DeleteEmailSubscription                     |                                          |
| Pasta do Power BI eliminada                           | DeleteFolder                                |                                          |
| Acesso à pasta do Power BI eliminado                    | DeleteFolderAccess                          | Não é atualmente utilizado                       |
| Gateway do Power BI eliminado                          | DeleteGateway                               |                                          |
| Grupo do Power BI eliminado                            | DeleteGroup                                 |                                          |
| Relatório do Power BI eliminado                           | DeleteReport                                |                                          |
| Área de trabalho da aplicação de modelo do Power BI eliminada | DeleteTemplateApp |
| Pacote de aplicações de modelo do Power BI eliminado | DeleteTemplateAppPackage |
| Implementado numa fase de pipeline                           | DeployAlmPipeline                                |                                          |
| Origens de dados do conjunto de dados do Power BI detetadas          | GetDatasources                              |                                          |
| Relatório do Power BI transferido                        | DownloadReport                              |                                          |
| Propriedades do fluxo de dados editadas                        | EditDataflowProperties                      |                                          |
| Permissão de certificação do Power BI editada          | EditCertificationPermission                 | Não é atualmente utilizado                       |
| Dashboard do Power BI editado                         | EditDashboard                               | Não é atualmente utilizado                       |
| Conjunto de dados do Power BI editado                           | EditDataset                                 |                                          |
| Propriedades do conjunto de dados do Power BI editadas                | EditDatasetProperties                       | Não é atualmente utilizado                       |
| Relatório do Power BI editado                            | EditReport                                  |                                          |
| Fluxo de dados do Power BI exportado                        | ExportDataflow                              |                                          |
| Dados visuais do relatório do Power BI exportados              | ExportReport                                |                                          |
| Dados do mosaico do Power BI exportados                       | ExportTile                                  |                                          |
| Pacote da aplicações de modelo do Power BI extraído para a área de trabalho | ExtractTemplateAppPackage |
| Falha ao adicionar permissões de fluxo de dados                | FailedToAddDataflowPermissions              | Não é atualmente utilizado                       |
| Falha ao remover permissões de fluxo de dados             | FailedToRemoveDataflowPermissions           | Não é atualmente utilizado                       |
| Token de SAS de fluxo de dados do Power BI gerado             | GenerateDataflowSasToken                    |                                          |
| Token de Incorporação do Power BI gerado                    | GenerateEmbedToken                          |                                          |
| Gerar captura de ecrã                       | GenerateScreenshot |                     |
| Ficheiro importado para o Power BI                         | Importar                                      |                                          |
| Aplicação do Power BI instalada                            | InstallApp                                  |                                          |
| Aplicação de modelo do Power BI instalada | InstallTemplateApp |
| Área de trabalho migrada para uma capacidade                  | MigrateWorkspaceIntoCapacity                |                                          |
| Comentário do Power BI publicado                           | PostComment                                 |                                          |
| Dashboard do Power BI impresso                        | PrintDashboard                              |                                          |
| Página de relatório do Power BI impressa                      | PrintReport                                 |                                          |
| Pacote de aplicações de modelo do Power BI promovido | PromoteTemplateAppPackage |
| Relatório do Power BI publicado na Web                  | PublishToWebReport <sup>2</sup>                         |                                          |
| Tabelas em destaque publicadas ou atualizadas | UpdateFeaturedTables <sup>3</sup>   | |
| Segredo do fluxo de dados do Power BI recebido do Key Vault  | ReceiveDataflowSecretFromKeyVault           |                                          |
| Removida uma área de trabalho de um pipeline de implementação         | UnassignWorkspaceFromPipeline                 |                                          |
| Origem de dados removida do gateway do Power BI         | RemoveDatasourceFromGateway                 |                                          |
| Membros do grupo do Power BI removidos                    | DeleteGroupMembers                          |                                          |
| Área de trabalho removida de uma capacidade                 | RemoveWorkspacesFromCapacity                |                                          |
| Nome de dashboard do Power BI mudado                        | RenameDashboard                             |                                          |
| Atualização do fluxo de dados do Power BI pedida               | RequestDataflowRefresh                      | Não é atualmente utilizado                       |
| Atualização do conjunto de dados do Power BI pedida                | RefreshDataset                              |                                          |
| Áreas de trabalho do Power BI obtidas                     | GetWorkspaces                               |                                          |
| Etiqueta de Confidencialidade Aplicada                         | SensitivityLabelApplied                     |                                          |
| Etiqueta de Confidencialidade Alterada                         | SensitivityLabelChanged                     |                                          |
| Etiqueta de Confidencialidade Removida                         | SensitivityLabelRemoved                     |                                          |
| Definir o local de armazenamento do fluxo de dados para uma área de trabalho     | SetDataflowStorageLocationForWorkspace      |                                          |
| Configurar atualização agendada no fluxo de dados do Power BI        | SetScheduledRefreshOnDataflow               |                                          |
| Atualização agendada do conjunto de dados do Power BI configurada         | SetScheduledRefresh                         |                                          |
| Dashboard do Power BI partilhado                         | ShareDashboard                              |                                          |
| Relatório do Power BI partilhado                            | ShareReport                                 |                                          |
| Avaliação expandida do Power BI iniciada                   | OptInForExtendedProTrial                    | Não é atualmente utilizado                       |
| Versão de avaliação do Power BI iniciada                            | OptInForProTrial                            |                                          |
| Controlou uma origem de dados do Power BI                   | TakeOverDatasource                          |                                          |
| Controlou um conjunto de dados do Power BI                        | TakeOverDataset                             |                                          |
| Controlou um fluxo de dados do Power BI                     | TookOverDataflow                             |                                          |
| Aplicação do Power BI não publicada                          | UnpublishApp                                |                                          |
| Atualizar definições de governação do recurso da capacidade      | UpdateCapacityResourceGovernanceSettings    | Não está atualmente no centro de administração do Microsoft 365 |
| Elemento visual personalizado organizacional atualizado                     | UpdateOrganizationalGalleryItem                   |                                          |
| Administrador de capacidade atualizado                            | UpdateCapacityAdmins                        |                                          |
| Nome a apresentar da capacidade atualizado                     | UpdateCapacityDisplayName                   |                                          |
| Permissões de atribuição de armazenamento do fluxo de dados atualizadas   | UpdatedDataflowStorageAssignmentPermissions |                                          |
| Acesso ao pipeline de implementação atualizado   | UpdateAlmPipelineAccess |                                          |
| Parâmetros da aplicação de modelo do Power BI instalados e atualizados | UpdateInstalledTemplateAppParameters |
| Configuração do pipeline de implementação atualizada   | SetConfigurationAlmPipeline |                                          |
| Definições do Power BI da organização atualizadas          | UpdatedAdminFeatureSwitch                   |                                          |
| Aplicação do Power BI atualizada                              | UpdateApp                                   |                                          |
| Fluxo de dados do Power BI atualizado                         | UpdateDataflow                              |                                          |
| Origens de dados do conjunto de dados do Power BI atualizadas             | UpdateDatasources                           |                                          |
| Parâmetros do conjunto de dados do Power BI atualizados               | UpdateDatasetParameters                     |                                          |
| Subscrição de e-mail do Power BI atualizada               | UpdateEmailSubscription                     |                                          |
| Pasta do Power BI atualizada                           | UpdateFolder                                |                                          |
| Acesso à pasta do Power BI atualizado                    | UpdateFolderAccess                          |                                          |
| Credenciais da origem de dados do gateway do Power BI atualizadas  | UpdateDatasourceCredentials                 |                                          |
| Definições da aplicação de modelo do Power BI atualizadas | UpdateTemplateAppSettings |
| Permissões de acesso ao teste da aplicação de modelo do Power BI atualizadas | UpdateTemplateAppTestPackagePermissions |
| Dashboard do Power BI visualizado                         | ViewDashboard                               |                                          |
| Fluxo de dados do Power BI visualizado                          | ViewDataflow                                |                                          |
| Relatório do Power BI visualizado                            | ViewReport                                  |                                          |
| Mosaico do Power BI visualizado                              | ViewTile                                    |                                          |
| Métricas de utilização do Power BI visualizadas                     | ViewUsageMetrics                            |                                          |
|                                                   |                                             |                                          |

<sup>1</sup> A publicação do Power BI Desktop para o serviço é um evento CreateReport no serviço.

<sup>2</sup> PublishtoWebReport refere-se à funcionalidade [Publicar na Web](../collaborate-share/service-publish-to-web.md).

<sup>3</sup> UpdateFeaturedTables refere-se a [tabelas em destaque do Power BI no Excel](../collaborate-share/service-excel-featured-tables.md).

## <a name="next-steps"></a>Próximos passos

- [O que é a administração do Power BI?](service-admin-administering-power-bi-in-your-organization.md)
- [Portal de Administração do Power BI](service-admin-portal.md)
- [Access the Power BI activity log (Aceder ao registo de atividades do Power BI)](../guidance/admin-activity-log.md)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)