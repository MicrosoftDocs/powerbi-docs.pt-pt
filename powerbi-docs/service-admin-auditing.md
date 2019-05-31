---
title: Utilizar a auditoria na sua organização
description: Saiba como pode utilizar o auditoria com o Power BI para monitorizar e investigar as ações executadas. Pode utilizar o Centro de Segurança e Conformidade ou utilizar o PowerShell
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/23/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 559ff45974274420e2545228720000359d5fe971
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906829"
---
# <a name="use-auditing-within-your-organization"></a>Utilizar a auditoria na sua organização

Saber quem está a realizar ações no qual item do Power BI inquilino pode ser fundamental para ajudar sua organização a satisfazer os requisitos, como a conformidade regulamentar e gerenciamento de registros. Utilize o Power BI a auditoria para auditar as ações efetuadas pelos utilizadores, como "Ver relatório" e "Vista de Dashboard". Não é possível utilizar a auditoria para auditar as permissões.

Vai trabalhar com a auditoria no Centro de Conformidade e Segurança do Office 365 ou utilizar o PowerShell. A auditoria depende da funcionalidade no Exchange Online, que é aprovisionada automaticamente para suportar o Power BI.

Pode filtrar os dados de auditoria por intervalo de datas, utilizador, dashboard, relatório, conjunto de dados e tipo de atividade. Também pode transferir as atividades num arquivo csv (valores separados por vírgulas) para análise offline.

## <a name="requirements"></a>Requirements

Tem de cumprir estes requisitos para aceder aos registos de auditoria:

* Tem de ser um administrador global ou atribuída a função de registos de auditoria ou registos de auditoria de apenas de visualização no Exchange Online para aceder ao registo de auditoria. Por predefinição, os grupos de funções de gerenciamento de conformidade e gestão da organização vêm com estas funções atribuídas a **permissões** página no Centro de administração do Exchange.

    Para fornecer contas de não-administrador com acesso ao registo de auditoria, tem de adicionar o utilizador como membro de um desses grupos de função. Se quiser fazê-lo outra forma, pode criar um grupo de função personalizada no Centro de administração do Exchange, atribua a função de registos de auditoria ou registos de auditoria de apenas de visualização a este grupo e, em seguida, adicione a conta não administrativa para o novo grupo de função. Para obter mais informações, veja [Manage role groups in Exchange Online](/Exchange/permissions-exo/role-groups) (Gerir grupos de funções no Exchange Online).

    Se não conseguir aceder ao centro de administração do Exchange a partir do centro de administração do Microsoft 365, aceda a https://outlook.office365.com/ecp e inicie sessão com as suas credenciais.

* Se tem acesso ao registo de auditoria, mas não um administrador global ou administrador de serviço do Power BI, não terá acesso ao portal de administração do Power BI. Neste caso, tem de utilizar uma ligação direta para o [Centro de Conformidade e Segurança do Office 365](https://sip.protection.office.com/#/unifiedauditlog).

## <a name="access-your-audit-logs"></a>Aceder aos seus registos de auditoria

Para aceder aos registos, certifique-se de ativar o registo no Power BI. Para obter mais informações, veja [Registos de auditoria](service-admin-portal.md#audit-logs) na documentação do portal de administração. Pode haver até um atraso de 48 horas entre a hora de que ativar a auditoria e quando, pode ver os dados de auditoria. Se não vir logo os seus dados, consulte os registos de auditoria mais tarde. Pode existir um intervalo de tempo semelhante entre obter a permissão para ver os registos de auditoria e ter acesso aos mesmos.

Os registos de auditoria do Power BI estão disponíveis diretamente através do [Centro de Conformidade e Segurança do Office 365](https://sip.protection.office.com/#/unifiedauditlog). Também existe uma ligação do portal de administração do Power BI:

1. No Power BI, selecione o **ícone de engrenagem** no canto superior direito, em seguida, selecione **portal de administração**.

   ![Captura de ecrã do menu de lista pendente de engrenagem com a opção do portal de administração chamado.](media/service-admin-auditing/powerbi-admin.png)

1. Selecione **Registos de auditoria**.

1. Selecione **Aceder ao Centro de Administração do Office 365**.

   ![Captura de ecrã do portal de administração com a auditoria e registos de opção viagem para as opções de centro de administração do Microsoft Office 365 descritas.](media/service-admin-auditing/audit-log-o365-admin-center.png)

## <a name="search-only-power-bi-activities"></a>Procurar apenas atividades do Power BI

Restrinja os resultados só para atividades do Power BI. Para tal, siga estes passos. Para obter uma lista de atividades, veja a [lista de atividades auditadas pelo Power BI](#activities-audited-by-power-bi) mais adiante neste artigo.

1. Sobre o **pesquisa de registos de auditoria** página, em **pesquisa**, selecione na lista pendente para **atividades**.

2. Selecione **Atividades do Power BI**.

   ![Pesquisa de registos de captura de ecrã de auditoria com atividades do Power BI destacados.](media/service-admin-auditing/audit-log-search-filter-by-powerbi.png)

3. Selecione em qualquer lugar fora da caixa de seleção para fechá-lo.

Suas pesquisas retornará apenas atividades do Power BI.

## <a name="search-the-audit-logs-by-date"></a>Procurar os registos de auditoria por data

Pode procurar os registos por intervalo de datas com o campo **Data de início** e **Data de fim**. A seleção predefinida é nos últimos sete dias. A exibição apresenta a data e hora no formato de hora Universal Coordenada (UTC). O intervalo de data máximo que pode especificar é 90 dias. 

Receberá um erro se o intervalo de datas selecionadas for superior a 90 dias. Se estiver a utilizar o intervalo de datas máximo de 90 dias, selecione a hora atual para a **Data de início**. Caso contrário, vai receber uma mensagem de erro a informar que a data de início é anterior à data de fim. Se tiver ativado a auditoria para os últimos 90 dias, não poderá iniciar o intervalo de datas antes da data de auditoria ser ativada.

![Pesquisa de registos de captura de ecrã de auditoria com opções de data de início e data de fim destacados.](media/service-admin-auditing/search-audit-log-by-date.png)

## <a name="search-the-audit-logs-by-users"></a>Procurar os registos de auditoria por utilizador

Pode procurar entradas de registo de auditoria para atividades feitas por utilizadores específicos. Introduza um ou mais nomes de utilizador no **utilizadores** campo. O nome de utilizador é semelhante a um endereço de e-mail. Trata-se a conta que os utilizadores iniciam sessão no Power BI. Deixe esta caixa em branco para apresentar as entradas de todos os utilizadores (e as contas de serviço) na sua organização.

![Procurar por utilizadores](media/service-admin-auditing/search-audit-log-by-user.png)

## <a name="view-search-results"></a>Ver resultados da pesquisa

Depois de selecionar **pesquisa**, carregar os resultados da pesquisa. Após alguns instantes, serão apresentados em **resultados**. Quando a pesquisa estiver concluída, a exibição mostra o número de resultados encontrado. **Pesquisa de registos de auditoria** apresenta um máximo de 1000 eventos. Se mais de 1000 eventos cumprirem os critérios de pesquisa, a aplicação mostra os eventos 1000 mais recentes.

### <a name="view-the-main-results"></a>Ver os resultados principais

O **resultados** área tem as seguintes informações para cada evento devolvido pela pesquisa. Selecione um cabeçalho de coluna em **Resultados** para ordenar os resultados.

| **Coluna** | **Definição** |
| --- | --- |
| Data |A data e a hora (no formato UTC) em que ocorreu o evento. |
| Endereço IP |O endereço IP do dispositivo utilizado para a atividade com sessão iniciada. A aplicação apresenta o endereço IP no formato de endereço de um IPv4 ou IPv6. |
| Utilizador |O utilizador (ou a conta de serviço) que efetuou a ação que, por sua vez, acionou o evento. |
| Atividade |A atividade efetuada pelo utilizador. Este valor corresponde às atividades que selecionou na lista pendente **Atividades**. Para um evento do registo de auditoria de administrador do Exchange, o valor nesta coluna é um cmdlet do Exchange. |
| Item |O objeto criado ou modificado por causa da atividade correspondente. Por exemplo, o ficheiro visualizado ou modificado ou a conta de utilizador atualizada. Nem todas as atividades têm um valor nesta coluna. |
| Detalhe |Detalhe adicional sobre uma atividade. Novamente, nem todas as atividades têm um valor. |

### <a name="view-the-details-for-an-event"></a>Ver os detalhes de um evento

Para ver mais detalhes sobre um evento, selecione o registo de eventos na lista de resultados da pesquisa. R **detalhes** é apresentada a página que tem as propriedades detalhadas do registo de eventos. O **detalhes** página apresenta propriedades dependendo do serviço do Office 365 em que o evento ocorre.

Para apresentar estes detalhes, selecione **Mais informações**. Todas as entradas do Power BI têm um valor de 20 para a propriedade RecordType. Para obter informações acerca de outras propriedades, veja [Propriedades detalhadas no registo de auditoria](/office365/securitycompliance/detailed-properties-in-the-office-365-audit-log/).

   ![Captura de ecrã da caixa de diálogo de detalhes de auditoria com a opção de informações mais destacado.](media/service-admin-auditing/audit-details.png)

## <a name="export-search-results"></a>Exportar resultados da pesquisa

Para exportar o registo de auditoria do Power BI para um ficheiro CSV, siga estes passos.

1. Selecione **Exportar resultados**.

1. Selecione **Guardar resultados carregados** ou **Transferir todos os resultados**.

    ![Captura de ecrã da exportação resulta opção.](media/service-admin-auditing/export-auditing-results.png)

## <a name="use-powershell-to-search-audit-logs"></a>Utilize o PowerShell para pesquisar registos de auditoria

Também pode utilizar o PowerShell para aceder aos registos de auditoria com base no início de sessão. O exemplo seguinte mostra como ligar ao PowerShell do Exchange Online e utilizar, depois, o comando [Search-UnifiedAuditLog](/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog?view=exchange-ps/) para obter entradas do registo de auditoria do Power BI. Para executar o script, um administrador tem de atribuir as permissões adequadas, conforme descrito no [requisitos](#requirements) secção.

```powershell
Set-ExecutionPolicy RemoteSigned

$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2018 -EndDate 9/15/2018 -RecordType PowerBI -ResultSize 1000 | Format-Table | More
```

Para obter mais informações sobre a ligação ao Exchange Online, consulte [Ligar ao PowerShell do Exchange Online](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell/). Para obter outro exemplo de utilização do PowerShell com registos de auditoria, veja [Using Power BI audit log and PowerShell to assign Power BI Pro licenses](https://powerbi.microsoft.com/blog/using-power-bi-audit-log-and-powershell-to-assign-power-bi-pro-licenses/) (Utilizar o registo de auditoria do Power BI e o PowerShell para atribuir licenças do Power BI Pro).

## <a name="activities-audited-by-power-bi"></a>Atividades auditadas pelo Power BI

As seguintes atividades são auditadas pelo Power BI:

| Nome amigável                                     | Nome da operação                              | Notas                                  |
|---------------------------------------------------|---------------------------------------------|------------------------------------------|
| Origem de dados adicionada ao gateway do Power BI             | AddDatasourceToGateway                      |                                          |
| Acesso à pasta do Power BI adicionado                      | AddFolderAccess                             | Não é atualmente utilizado                       |
| Membros do grupo do Power BI adicionados                      | AddGroupMembers                             |                                          |
| Conta de armazenamento do fluxo de dados anexada ao inquilino pelo administrador | AdminAttachedDataflowStorageAccountToTenant | Não é atualmente utilizado                       |
| Conjunto de dados analisado do Power BI                         | AnalyzedByExternalApplication               |                                          |
| Relatório do Power BI analisado                          | AnalyzeInExcel                              |                                          |
| Conjunto de dados do Power BI vinculado ao gateway                | BindToGateway                               |                                          |
| Estado de capacidade alterado                            | ChangeCapacityState                         |                                          |
| Atribuição de utilizador da capacidade alterada                  | UpdateCapacityUsersAssignment               |                                          |
| Ligações de dados do Power BI alteradas              | SetAllConnections                           |                                          |
| Administradores do gateway do Power BI alterados                   | ChangeGatewayAdministrators                 |                                          |
| Utilizadores da origem de dados do gateway do Power BI alterados        | ChangeGatewayDatasourceUsers                |                                          |
| Pacote de conteúdos organizacional do Power BI criado      | CreateOrgApp                                |                                          |
| Aplicação do Power BI criada                              | CreateApp                                   |                                          |
| Dashboard do Power BI criado                        | CreateDashboard                             |                                          |
| Fluxo de dados do Power BI criado                         | CreateDataflow                              |                                          |
| Conjunto de dados do Power BI criado                          | CreateDataset                               |                                          |
| Subscrição de e-mail do Power BI criada               | CreateEmailSubscription                     |                                          |
| Pasta do Power BI criada                           | CreateFolder                                |                                          |
| Gateway do Power BI criado                          | CreateGateway                               |                                          |
| Grupo do Power BI criado                            | CreateGroup                                 |                                          |
| Relatório do Power BI criado                           | CreateReport                                |                                          |
| Fluxo de dados migrado para a conta de armazenamento externa     | DataflowMigratedToExternalStorageAccount    | Não é atualmente utilizado                       |
| Permissões do fluxo de dados adicionadas                        | DataflowPermissionsAdded                    | Não é atualmente utilizado                       |
| Permissões do fluxo de dados removidas                      | DataflowPermissionsRemoved                  | Não é atualmente utilizado                       |
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
| Origens de dados do conjunto de dados do Power BI detetadas          | GetDatasources                              |                                          |
| Relatório do Power BI transferido                        | DownloadReport                              |                                          |
| Permissão de certificação do Power BI editada          | EditCertificationPermission                 | Não é atualmente utilizado                       |
| Dashboard do Power BI editado                         | EditDashboard                               | Não é atualmente utilizado                       |
| Conjunto de dados do Power BI editado                           | EditDataset                                 |                                          |
| Propriedades do conjunto de dados do Power BI editadas                | EditDatasetProperties                       | Não é atualmente utilizado                       |
| Relatório do Power BI editado                            | EditReport                                  |                                          |
| Fluxo de dados do Power BI exportado                        | ExportDataflow                              |                                          |
| Dados visuais do relatório do Power BI exportados              | ExportReport                                |                                          |
| Dados do mosaico do Power BI exportados                       | ExportTile                                  |                                          |
| Falha ao adicionar permissões de fluxo de dados                | FailedToAddDataflowPermissions              | Não é atualmente utilizado                       |
| Falha ao remover permissões de fluxo de dados             | FailedToRemoveDataflowPermissions           | Não é atualmente utilizado                       |
| Token de SAS de fluxo de dados do Power BI gerado             | GenerateDataflowSasToken                    |                                          |
| Token de Incorporação do Power BI gerado                    | GenerateEmbedToken                          |                                          |
| Ficheiro importado para o Power BI                         | Importar                                      |                                          |
| Aplicação do Power BI instalada                            | InstallApp                                  |                                          |
| Área de trabalho migrada para uma capacidade                  | MigrateWorkspaceIntoCapacity                |                                          |
| Comentário do Power BI publicado                           | PostComment                                 |                                          |
| Dashboard do Power BI impresso                        | PrintDashboard                              |                                          |
| Página de relatório do Power BI impressa                      | PrintReport                                 |                                          |
| Relatório do Power BI publicado na Web                  | PublishToWebReport                          |                                          |
| Segredo do fluxo de dados do Power BI recebido do Key Vault  | ReceiveDataflowSecretFromKeyVault           | Não é atualmente utilizado                       |
| Origem de dados removida do gateway do Power BI         | RemoveDatasourceFromGateway                 |                                          |
| Membros do grupo do Power BI removidos                    | DeleteGroupMembers                          |                                          |
| Área de trabalho removida de uma capacidade                 | RemoveWorkspacesFromCapacity                |                                          |
| Nome de dashboard do Power BI mudado                        | RenameDashboard                             |                                          |
| Atualização do fluxo de dados do Power BI pedida               | RequestDataflowRefresh                      | Não é atualmente utilizado                       |
| Atualização do conjunto de dados do Power BI pedida                | RefreshDataset                              |                                          |
| Áreas de trabalho do Power BI obtidas                     | GetWorkspaces                               |                                          |
| Configurar atualização agendada no fluxo de dados do Power BI        | SetScheduledRefreshOnDataflow               |                                          |
| Atualização agendada do conjunto de dados do Power BI configurada         | SetScheduledRefresh                         |                                          |
| Dashboard do Power BI partilhado                         | ShareDashboard                              |                                          |
| Relatório do Power BI partilhado                            | ShareReport                                 |                                          |
| Avaliação expandida do Power BI iniciada                   | OptInForExtendedProTrial                    | Não é atualmente utilizado                       |
| Versão de avaliação do Power BI iniciada                            | OptInForProTrial                            |                                          |
| Controlou uma origem de dados do Power BI                   | TakeOverDatasource                          |                                          |
| Controlou um conjunto de dados do Power BI                        | TakeOverDataset                             |                                          |
| Aplicação do Power BI não publicada                          | UnpublishApp                                |                                          |
| Atualizar definições de governação do recurso da capacidade      | UpdateCapacityResourceGovernanceSettings    | Não está atualmente no centro de administração do Microsoft 365 |
| Administrador de capacidade atualizado                            | UpdateCapacityAdmins                        |                                          |
| Nome a apresentar da capacidade atualizado                     | UpdateCapacityDisplayName                   |                                          |
| Definições do Power BI da organização atualizadas          | UpdatedAdminFeatureSwitch                   |                                          |
| Aplicação do Power BI atualizada                              | UpdateApp                                   |                                          |
| Fluxo de dados do Power BI atualizado                         | UpdateDataflow                              |                                          |
| Origens de dados do conjunto de dados do Power BI atualizadas             | UpdateDatasources                           |                                          |
| Parâmetros do conjunto de dados do Power BI atualizados               | UpdateDatasetParameters                     |                                          |
| Subscrição de e-mail do Power BI atualizada               | UpdateEmailSubscription                     |                                          |
| Pasta do Power BI atualizada                           | UpdateFolder                                |                                          |
| Acesso à pasta do Power BI atualizado                    | UpdateFolderAccess                          |                                          |
| Credenciais da origem de dados do gateway do Power BI atualizadas  | UpdateDatasourceCredentials                 |                                          |
| Dashboard do Power BI visualizado                         | ViewDashboard                               |                                          |
| Fluxo de dados do Power BI visualizado                          | ViewDataflow                                |                                          |
| Relatório do Power BI visualizado                            | ViewReport                                  |                                          |
| Mosaico do Power BI visualizado                              | ViewTile                                    |                                          |
| Métricas de utilização do Power BI visualizadas                     | ViewUsageMetrics                            |                                          |
|                                                   |                                             |                                          |

## <a name="next-steps"></a>Próximos passos

[O que é a administração do Power BI?](service-admin-administering-power-bi-in-your-organization.md)  

[Portal de Administração do Power BI](service-admin-portal.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
