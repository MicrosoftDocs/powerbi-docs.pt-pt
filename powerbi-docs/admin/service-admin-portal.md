---
title: Portal de administração do Power BI
description: O portal de administração permite a gestão de inquilinos do Power BI na sua organização. Inclui itens, como métricas de utilização, acesso ao centro de administração do Microsoft 365 e definições.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 05/12/2020
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 90cd12bc7d8d7261e25edd32c5afa7cf144e8202
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/28/2020
ms.locfileid: "87252515"
---
# <a name="administering-power-bi-in-the-admin-portal"></a>Administrar o Power BI no portal de administração

O portal de administração permite-lhe gerir o *inquilino* do Power BI da sua organização. O portal inclui itens, como métricas de utilização, acesso ao centro de administração do Microsoft 365 e definições.

O portal de administração completo está acessível a todos os utilizadores que sejam administradores globais ou a quem tenha sido atribuída a função de administrador de serviço do Power BI. Se não estiver numa destas funções, verá apenas as **Definições de capacidade** no portal. Para obter mais informações sobre a função de administrador do serviço Power BI, veja [Noções básicas sobre a função de administrador do Power BI](service-admin-role.md).

## <a name="how-to-get-to-the-admin-portal"></a>Como aceder ao portal de administração

A conta tem de estar marcada como **Administrador Global**, no Microsoft 365 ou no Azure Active Directory (Azure AD), ou ter sido atribuída a função de administrador de serviço do Power BI, para obter acesso ao portal de administração do Power BI. Para obter mais informações sobre a função de administrador do serviço Power BI, veja [Noções básicas sobre a função de administrador do Power BI](service-admin-role.md). Para aceder ao portal de administração do Power BI, efetue o seguinte procedimento.

1. Selecione a engrenagem de definições na parte superior direita do serviço Power BI.

1. Selecione **Portal de administração**.

    ![Definições do portal de administração](media/service-admin-portal/powerbi-admin-settings.png)

Existem nove separadores no portal. O resto deste artigo disponibiliza informações sobre cada um destes separadores.

![Navegação no portal de administração](media/service-admin-portal/powerbi-admin-landing-page.png)

* [Métricas de utilização](#usage-metrics)
* [Utilizadores](#users)
* [Registos de auditoria](#audit-logs)
* [Definições de inquilino](#tenant-settings)
* [Definições de capacidade](#capacity-settings)
* [Códigos de incorporação](#embed-codes)
* [Elemento visuais da organização](#organizational-visuals)
* [Armazenamento do fluxo de dados (pré-visualização)](#dataflowStorage)
* [Áreas de trabalho](#workspaces)
* [Imagem corporativa personalizada](#custom-branding)

## <a name="usage-metrics"></a>Métricas de utilização

As **Métricas de utilização** permitem-lhe monitorizar a utilização do Power BI da sua organização. Permite também ver quais os utilizadores e os grupos mais ativos no Power BI para a sua organização. 

> [!NOTE]
> Quando aceder ao dashboard pela primeira vez ou depois de voltar após um período longo em que não visualizou o dashboard, provavelmente verá um ecrã de carregamento enquanto carregamos o dashboard.

Após o carregamento do dashboard, verá duas secções de mosaicos. A primeira secção inclui os dados de utilização dos utilizadores individuais e a segunda secção tem informações semelhantes dos grupos na sua organização.

Segue-se uma análise detalhada do que pode ver em cada mosaico:

* Contagem distinta de todos os dashboards, relatórios e conjuntos de dados na área de trabalho do utilizador.
  
    ![Contagem distinta de dashboards, relatórios e conjuntos de dados](media/service-admin-portal/powerbi-admin-usage-metrics-number-tiles.png)

* O dashboard mais consumido pelo número de utilizadores que podem aceder ao mesmo. Por exemplo, se tiver um dashboard partilhado com três utilizadores e também o tiver adicionado a um pacote de conteúdos com dois utilizadores diferentes ligados, a contagem será 6 (1 + 3 + 2).
  
    ![Dashboards mais consumidos](media/service-admin-portal/powerbi-admin-usage-metrics-top-dashboards.png)

* Os utilizadores de conteúdo mais populares ligados ao mesmo. Isto será qualquer item a que os utilizadores possam aceder através do processo Obter Dados, como pacotes de conteúdos SaaS, pacotes de conteúdos Organizacionais, ficheiros ou bases de dados.
  
    ![Pacotes mais consumidos](media/service-admin-portal/powerbi-admin-usage-metrics-top-connections.png)

* Uma vista dos principais utilizadores com base no número de dashboards que têm, tanto os dashboards que criaram como os dashboards partilhados com eles.
  
    ![Principais utilizadores – dashboards](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-dashboards.png)

* Uma vista dos principais utilizadores com base no número de relatórios que têm.
  
    ![Principais utilizadores – relatórios](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-reports.png)

A segunda secção apresenta o mesmo tipo de informação, mas com base em grupos. Tal permite-lhe ver quais os grupos mais ativos na sua organização e o tipo de conteúdo que estão a consumir.

Com estas informações, pode obter informações reais relativamente à forma como as pessoas estão a utilizar o Power BI na sua organização e reconhecer os utilizadores e grupos que são muito ativos na sua organização.

## <a name="control-usage-metrics"></a>Controlar métricas de utilização

Os relatórios de métrica de utilização são uma funcionalidade que o administrador do Power BI ou global pode ativar ou desativar. Os administradores têm controlo granular sobre quais utilizadores têm acesso às métricas de utilização. As métricas estão **Ativadas** por predefinição para todos os utilizadores na organização.

Os administradores também podem determinar se os criadores de conteúdo podem ver dados por utilizador nas métricas de utilização. 

Veja [Monitorizar as métricas de utilização para dashboards e relatórios do Power BI](../collaborate-share/service-usage-metrics.md) para obter detalhes sobre os relatórios.

### <a name="usage-metrics-for-content-creators"></a>Métricas de utilização para criadores de conteúdo

1. No portal de administração, selecione **Definições de inquilino** > **Métricas de utilização para criadores de conteúdo**.

    ![Definições de inquilino no portal de administração para métricas de utilização](media/service-admin-portal/power-bi-admin-usage-metrics.png)

1. Ative (ou desative) as métricas de utilização > **Aplicar**.

    ![Métrica de utilização ativada](../collaborate-share/media/service-usage-metrics/power-bi-tenant-settings-updated.png)


### <a name="per-user-data-in-usage-metrics"></a>Dados por utilizador nas métricas de utilização

Por predefinição, os dados por utilizador estão ativados para métricas de utilização e as informações da conta do consumidor de conteúdos estão incluídas no relatório de métricas. Se não quiser incluir estas informações para alguns ou para todos os utilizadores, desative a funcionalidade para grupos de segurança específicos ou para toda a organização. As informações da conta são apresentadas no relatório como *Sem nome*.

![Dados de utilização por utilizador](media/service-admin-portal/power-bi-admin-per-user-usage-data.png)

### <a name="delete-all-existing-usage-metrics-content"></a>Eliminar todo o conteúdo das métricas de utilização existente

Ao desativar as métricas de utilização para toda a respetiva organização, os administradores também podem escolher uma ou ambas as opções para:

- **Eliminar todo o conteúdo das métricas de utilização existente** para eliminar todos os relatórios e mosaicos de dashboard existentes que foram criados com os conjuntos de dados e relatórios de métricas de utilização. Esta opção remove todo o acesso a dados da métrica de utilização por parte de todos os utilizadores na organização que possam estar a utilizá-lo. 
- **Eliminar todos os dados por utilizador existentes no conteúdo de métricas de utilização atual**; esta opção remove todo o acesso a dados das métricas de utilização por parte de todos os utilizadores na organização que possam estar a utilizá-los. 

Tenha cuidado, uma vez que eliminar o conteúdo das métricas de utilização por utilizador existente é irreversível.

## <a name="users"></a>Utilizadores

Os utilizadores, grupos e administradores do Power BI são geridos no centro de administração do Microsoft 365. O separador **Utilizadores** disponibiliza uma ligação para o centro de administração do seu inquilino.

![Aceda ao centro de administração do Microsoft 365](media/service-admin-portal/powerbi-admin-manage-users.png)

## <a name="audit-logs"></a>Registos de auditoria

Os registos de auditoria do Power BI são geridos no centro de Segurança e Conformidade do Office 365. O separador **Registos de auditoria** proporciona uma ligação para o centro de Segurança e Conformidade do seu inquilino. [Saiba mais](service-admin-auditing.md)

Para utilizar os registos de auditoria, verifique se a definição [**Criar registos de auditoria para auditoria de atividade interna e de conformidade**](#create-audit-logs-for-internal-activity-auditing-and-compliance) está ativada.

## <a name="tenant-settings"></a>Definições do inquilino

O separador **Definições de inquilino** permite um controlo refinado sobre as funcionalidades que são disponibilizadas à sua organização. Se tiver problemas com dados confidenciais, algumas das nossas funcionalidades poderão não ser adequadas para a sua organização ou poderá querer apenas uma determinada funcionalidade disponível para um grupo específico.

> [!NOTE]
> As definições do inquilino que controlam a disponibilidade das funcionalidades na interface do utilizador do Power BI podem ajudar a estabelecer políticas de governação, mas não são uma medida de segurança. Por exemplo, a definição **Exportar dados** não restringe as permissões de um utilizador do Power BI num conjunto de dados. Os utilizadores do Power BI com acesso de leitura a um conjunto de dados têm permissão para consultar este conjunto de dados e poderão conseguir fazer persistir os resultados sem utilizar a funcionalidade **Exportar dados** na interface do utilizador do Power BI.

A seguinte imagem apresenta várias definições no separador **Definições de inquilino**.

![Definições do inquilino](media/service-admin-portal/powerbi-admin-tenant-settings.png)

> [!NOTE]
> Pode demorar até 10 minutos para a alteração à definição ter efeito para todos os utilizadores no inquilino.

As definições podem ter três estados:

* **Desativado para toda a organização**: Ninguém na sua organização pode utilizar esta funcionalidade.

    ![Definição Desativado para todos](media/service-admin-portal/powerbi-admin-tenant-settings-disabled.png)

* **Ativado para toda a organização**: Todas as pessoas na sua organização podem utilizar esta funcionalidade.

    ![Definição Ativado para todos](media/service-admin-portal/powerbi-admin-tenant-settings-enabled.png)

* **Ativado para um subconjunto da organização**: Um subconjunto específico de utilizadores ou grupos na sua organização pode utilizar esta funcionalidade.

    Pode ativar a funcionalidade para toda a organização, exceto para um grupo específico de utilizadores.

    ![Definição Ativado para um subconjunto](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except.png)

    Pode também ativar a funcionalidade apenas para um grupo específico de utilizadores ou desativá-la para um grupo de utilizadores. Utilizar esta abordagem assegura que determinados utilizadores não tenham acesso à funcionalidade mesmo que estejam no grupo permitido.

    ![Definição Ativado com exceções](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except2.png)

As próximas secções fornecem uma descrição geral dos diferentes tipos de definições de inquilino.

## <a name="help-and-support-settings"></a>Definições de ajuda e suporte

### <a name="publish-get-help-information"></a>Publicar informações para "Obter Ajuda"

Os utilizadores na organização podem aceder aos recursos de ajuda e suporte internos a partir do menu de ajuda do Power BI. Especificamente, estes parâmetros alteram o comportamento dos itens de menu de ajuda Saber mais, Comunidade e Obter ajuda.

Além disso, ao especificar um URL para pedidos de licenciamento, pode personalizar o URL de destino do botão **Atualizar conta**. Os utilizadores sem uma licença do Power BI Pro veem este botão na caixa de diálogo **Atualizar para o Power BI Pro**, bem como na página **Gerir armazenamento pessoal**. Além disso, o Power BI já não apresenta o botão **Experimentar o Pro gratuitamente** nesta caixa de diálogo ou página de armazenamento. Isto garante que o Power BI orienta os seus utilizadores de forma fiável pelos processos definidos na sua organização através da sua solução de gestão de licenças.

![Definição Ativado com exceções](media/service-admin-portal/powerbi-admin-tenant-settings-gethelp.png)

### <a name="receive-email-notifications-for-service-outages-or-incidents"></a>Receber notificações por e-mail sobre incidentes ou indisponibilidades do serviço

Os grupos de segurança com capacidade de correio receberão notificações de e-mail se este inquilino for afetado por um incidente ou uma indisponibilidade do serviço. Saiba mais sobre as [Notificações de interrupção do serviço](service-interruption-notifications.md).

## <a name="workspace-settings"></a>Definições de área de trabalho

Em **Definições do inquilino**, o portal de administração possui duas secções para controlar áreas de trabalho:

- Criar as novas experiências de área de trabalho.
- Utilizar conjuntos de dados em áreas de trabalho.
- Impedir a criação de áreas de trabalho clássicas.

### <a name="create-the-new-workspaces"></a>Criar as novas áreas de trabalho

As áreas de trabalho são locais onde os utilizadores podem colaborar em dashboards, relatórios e outros conteúdos. Os administradores utilizam a definição **Criar áreas de trabalho (nova experiência de área de trabalho)** para indicar quais são os utilizadores na organização que podem criar áreas de trabalho. Os administradores podem permitir que todos os utilizadores ou nenhum utilizador numa organização crie novas áreas de trabalho de experiências de área de trabalho. Também podem limitar a criação a membros de grupos de segurança específicos. Saiba mais sobre as [áreas de trabalho](../collaborate-share/service-new-workspaces.md).

:::image type="content" source="media/service-admin-portal/power-bi-admin-workspace-settings.png" alt-text="Criar as novas experiências de área de trabalho":::

No caso das áreas de trabalho clássicas com base em Grupos do Microsoft 365, a administração continua a ocorrer no portal de administração do Microsoft 365 e no Azure Active Directory.

> [!NOTE]
> Por predefinição, a definição **Criar áreas de trabalho (nova experiência de área de trabalho)** permite que apenas os utilizadores que podem criar Grupos do Microsoft 365 possam criar novas áreas de trabalho no Power BI. Confirme que define um valor no portal de administração do Power BI para garantir que os utilizadores apropriados os podem criar.

**Lista de áreas de trabalho**

O portal de administração tem outra secção de definições sobre as áreas de trabalho no seu inquilino. Nesta secção, pode ordenar e filtrar a lista de áreas de trabalho e ver os detalhes de cada área de trabalho. Veja a secção [Áreas de trabalho](#workspaces) neste artigo para obter mais detalhes.

**Publicar pacotes de conteúdo e aplicações**

No portal de administração, também controla quais os utilizadores que têm permissão para distribuir aplicações para a organização. Veja [Publicar pacotes de conteúdo e aplicações em toda a organização](#publish-content-packs-and-apps-to-the-entire-organization) neste artigo para obter detalhes.

### <a name="use-datasets-across-workspaces"></a>Utilizar conjuntos de dados em áreas de trabalho

Os administradores podem controlar quais os utilizadores na organização que podem utilizar conjuntos de dados em áreas de trabalho. Quando esta definição está ativada, os utilizadores ainda precisam da Permissão de compilação para um conjunto de dados específico.

:::image type="content" source="media/service-admin-portal/power-bi-admin-datasets-workspaces.png" alt-text="Utilizar conjuntos de dados em áreas de trabalho":::

Veja [Introdução aos conjuntos de dados em áreas de trabalho](../connect-data/service-datasets-across-workspaces.md) para obter mais informações.

### <a name="block-classic-workspace-creation"></a>Impedir a criação de áreas de trabalho clássicas

Os administradores podem controlar se a organização pode criar áreas de trabalho clássicas. Quando esta definição está ativada, os utilizadores que criam uma área de trabalho só podem criar áreas de trabalho da nova experiência. 

![Impedir a criação de áreas de trabalho clássicas](media/service-admin-portal/power-bi-admin-block-classic-workspaces.png)

Quando estiver ativada, os Grupos do Office 365 criados recentemente não serão apresentados na lista de áreas de trabalho do Power BI. As áreas de trabalho clássicas existentes continuarão a ser apresentadas na lista. Quando a definição estiver desativada, todos os Grupos do Office 365 dos quais o utilizador é membro aparecerão na lista de áreas de trabalho. Leia mais sobre as [áreas de trabalho da nova experiência](../collaborate-share/service-new-workspaces.md).

## <a name="export-and-sharing-settings"></a>Definições de exportação e partilha

### <a name="share-content-with-external-users"></a>Partilhar conteúdo com utilizadores externos

Os utilizadores na organização podem partilhar dashboards, relatórios e aplicações com utilizadores fora da organização. Saiba mais sobre a [partilha externa](../collaborate-share/service-share-dashboards.md#share-a-dashboard-or-report-outside-your-organization).

![Definição Utilizadores externos](media/service-admin-portal/powerbi-admin-sharing-external-02.png)

A imagem seguinte mostra a mensagem que aparece quando partilha com um utilizador externo.

![Partilhar com um utilizador externo](media/service-admin-portal/powerbi-admin-sharing-external.png)  

> [!IMPORTANT]
> Esta opção controla se os utilizadores no Power BI podem convidar utilizadores externos para se tornarem utilizadores convidados do Azure Active Directory B2B (Azure AD B2B) na sua organização através do Power BI. Quando ativada, os utilizadores com a função Emitente de Convites no Azure AD poderão adicionar endereços de e-mail externos quando partilharem relatórios, dashboards e aplicações do Power BI. O destinatário externo é convidado a aderir à sua organização como utilizador convidado do Azure AD B2B. O mais importante é que, quando desativar esta definição, os utilizadores externos que já sejam utilizadores convidados do Azure AD B2B na sua organização continuam a aparecer nas IUs do seletor de pessoas no Power BI e pode ser-lhes concedido acesso a itens, áreas de trabalho e aplicações.

### <a name="publish-to-web"></a>Publicar na Web

Como administrador de um inquilino do Power BI, a definição **Publicar na Web** permite-lhe escolher os utilizadores que podem criar códigos de incorporação para publicar relatórios na Web. Esta funcionalidade permite-lhe disponibilizar o relatório e os dados que contém a qualquer pessoa na Web. Saiba mais sobre como [publicar na Web](../collaborate-share/service-publish-to-web.md).

> [!NOTE]
> Apenas o administrador do Power BI pode permitir a criação de novos códigos de incorporação de publicação na Web. As organizações poderão já ter códigos de incorporação. Veja a secção [Códigos de incorporação](service-admin-portal.md#embed-codes) do portal de administração para consultar os relatórios atualmente publicados.

A imagem seguinte mostra o menu **Mais opções (...)** de um relatório quando a definição **Publicar na Web** está ativada.

![Publicar na Web no menu Mais opções](media/service-admin-portal/power-bi-more-options-publish-web.png)

A definição **Publicar na Web** no portal de administração permite escolher os utilizadores que podem criar códigos de incorporação.

![Definição Publicar na Web](media/service-admin-portal/powerbi-admin-publish-to-web-setting.png)

Os administradores podem definir **Publicar na Web** como **Ativada** e **Escolha como funcionam os códigos de incorporação** como **Permitir apenas códigos de incorporação existentes**. Nesse caso, os utilizadores podem criar códigos de incorporação, mas têm de contactar o administrador do Power BI para lhes permitir isso.

![Pedido para publicar na Web](../collaborate-share/media/service-publish-to-web/publish_to_web_admin_prompt.png)

Os utilizadores veem opções diferentes na IU consoante a definição **Publicar na Web**.

|Funcionalidade |Ativada para toda a organização |Desativada para toda a organização |Grupos de segurança específicos   |
|---------|---------|---------|---------|
|**Publicar na Web** no menu **Mais opções (...)** do relatório|Ativada para todos|Não visível para todos|Visível apenas para utilizadores ou grupos autorizados.|
|**Gerir códigos de incorporação**, em **Definições**|Ativada para todos|Ativada para todos|Ativada para todos<br><br>* A opção **Eliminar** está ativada apenas para utilizadores e grupos autorizados.<br>* A opção **Obter códigos** está ativada para todos.|
|**Incorporar códigos** no portal de administração|O estado é um dos seguintes:<br>* Ativo<br>* Não suportado<br>* Bloqueado|O estado apresenta **Desativado**|O estado é um dos seguintes:<br>* Ativo<br>* Não suportado<br>* Bloqueado<br><br>Se um utilizador não tiver autorizações com base na definição do inquilino, o estado é apresentado como **Em violação**.|
|Relatórios publicados existentes|Todos ativados|Todos desativados|Os relatórios continuam a ser compostos para todos.|

### <a name="export-data"></a>Exportar dados

Os utilizadores na organização podem exportar dados de um mosaico ou visualização. Isto controla a funcionalidade Analisar no Excel, a exportação para .csv, as transferências de conjuntos de dados (.pbix) e o Live Connect do Serviço Power BI. Saiba mais sobre como [exportar dados a partir de um mosaico ou elemento visual](../visuals/power-bi-visualization-export-data.md).

>[!NOTE]
> Antes da introdução da definição Exportar para o Excel, esta definição também controlava a exportação dos dados para ficheiros do Excel. Consulte a [nota em Exportar para o Excel](#export-to-excel) para obter detalhes.

![Definição Exportar dados](media/service-admin-portal/powerbi-admin-portal-export-data-setting.png)

A imagem seguinte mostra a opção para exportar os dados de um mosaico.

![Exportar dados de um mosaico](media/service-admin-portal/powerbi-admin-export-data.png)

> [!NOTE]
> Desativar a opção **Exportar Dados** também impede os utilizadores de usarem a funcionalidade [Analisar no Excel](../collaborate-share/service-analyze-in-excel.md), bem como a ligação em direto do serviço Power BI.

### <a name="export-to-excel"></a>Exportar para o Excel

Os utilizadores da organização podem exportar os dados de uma visualização para um ficheiro do Excel.

![Definição Exportar para o Excel](media/service-admin-portal/powerbi-admin-portal-export-to-excel-setting.png)

>[!IMPORTANT]
> Antes da introdução da definição Exportar para o Excel, a exportação para o Excel era controlada pela definição Exportar dados. Como tal, nos inquilinos que existiam antes da introdução da definição Exportar para o Excel, na primeira vez que os administradores de inquilinos observarem a definição Exportar para o Excel, verão que tem *Alterações não aplicadas*. Têm de aplicar estas alterações para que a nova definição entre em vigor. Caso contrário, a exportação para um ficheiro do Excel continuará a ser controlada pela definição Exportar dados.

### <a name="export-reports-as-powerpoint-presentations-or-pdf-documents"></a>Exportar relatórios como apresentações do PowerPoint ou documentos PDF

Os utilizadores na organização podem exportar relatórios do Power BI como ficheiros do PowerPoint ou documentos PDF. [Saiba mais](../consumer/end-user-powerpoint.md)

A seguinte imagem mostra o menu **Ficheiro** de um relatório quando a definição **Exportar relatórios como apresentações do PowerPoint ou documentos PDF** está ativada.

![Exportar relatórios como apresentações do PowerPoint](media/service-admin-portal/powerbi-admin-powerpoint.png)

### <a name="print-dashboards-and-reports"></a>Imprimir dashboards e relatórios

Os utilizadores na organização podem imprimir dashboards e relatórios. [Saiba mais](../consumer/end-user-print.md)

A imagem seguinte mostra a opção para imprimir um dashboard.

![Imprimir dashboard](media/service-admin-portal/powerbi-admin-print-dashboard.png)

A imagem seguinte mostra o menu **Ficheiro** de um relatório quando a definição **Imprimir dashboards e relatórios** está ativada.

![Imprimir relatório](media/service-admin-portal/powerbi-admin-print-report.png)

### <a name="allow-external-guest-users-to-edit-and-manage-content-in-the-organization"></a>Permitir aos utilizadores externos convidados editarem e gerirem conteúdo na organização

Os utilizadores convidados do Azure AD B2B podem editar e gerir o conteúdo na organização. [Saiba mais](service-admin-azure-ad-b2b.md)

A seguinte imagem mostra a opção Permitir aos utilizadores externos convidados editarem e gerirem conteúdo na organização.

![Permitir aos utilizadores externos convidados editarem e gerirem conteúdo na organização](media/service-admin-portal/powerbi-admin-tenant-settings-b2b-guest-edit-manage.png)

No portal de administração, também controla quais os utilizadores que têm permissão para convidar utilizadores externos para a organização. Veja [Partilhar conteúdo com utilizadores externos](#export-and-sharing-settings) neste artigo para obter mais detalhes.

### <a name="email-subscriptions"></a>Subscrições de E-mail
Os utilizadores na organização podem criar subscrições por e-mail. Saiba mais sobre as [subscrições](../collaborate-share/service-publish-to-web.md).

![Ativar as subscrições por e-mail](media/service-admin-portal/power-bi-manage-email-subscriptions.png)

### <a name="featured-content"></a>Conteúdo em destaque

Permita que alguns ou todos os autores de relatórios na sua organização destaquem os respetivos conteúdos na secção Em destaque da Base do Power BI. Os novos utilizadores verão o conteúdo em destaque na parte superior da respetiva Base do Power BI. O conteúdo em destaque move-se na Base à medida que os utilizadores adicionam conteúdos **Favoritos**, **Frequentes** e **Recentes**. 

Recomendamos que comece com um pequeno conjunto de promotores. Permitir que toda a organização destaque conteúdos na Base pode dificultar a monitorização de todos os conteúdos promovidos. 

Após permitir conteúdo em destaque, também pode geri-lo no Portal de administração. Veja [Gerir conteúdo em destaque](#manage-featured-content)neste artigo para ler sobre como controlar conteúdo em destaque no seu domínio.

## <a name="content-pack-and-app-settings"></a>Definições da aplicação e do pacote de conteúdos

### <a name="publish-content-packs-and-apps-to-the-entire-organization"></a>Publicar pacotes de conteúdo e aplicações em toda a organização

Os administradores podem utilizar esta definição para decidir que utilizadores podem publicar pacotes de conteúdo e aplicações em toda a organização, ao invés de apenas grupos específicos. Saiba mais sobre como [publicar aplicações](../collaborate-share/service-create-distribute-apps.md).

A imagem seguinte mostra a opção **A minha organização inteira** durante a criação de um pacote de conteúdos.

![Publicar o pacote de conteúdos para a organização](media/service-admin-portal/powerbi-admin-publish-entire-org.png)

### <a name="create-template-apps-and-organizational-content-packs"></a>Criar pacotes de conteúdos organizacionais e aplicações de modelo

Os utilizadores na organização podem criar pacotes de conteúdos organizacionais e aplicações de modelo que utilizam conjuntos de dados incorporados numa origem de dados no Power BI Desktop. Saiba mais sobre as [aplicações de modelo](../connect-data/service-template-apps-create.md).

### <a name="push-apps-to-end-users"></a>Aplicações push para utilizadores finais

Os criadores dos relatórios podem partilhar as aplicações diretamente com os utilizadores finais sem necessitar da instalação do [AppSource](https://appsource.microsoft.com). Saiba mais sobre como [instalar aplicações automaticamente para os utilizadores finais](../collaborate-share/service-create-distribute-apps.md#automatically-install-apps-for-end-users).

## <a name="integration-settings"></a>Definições de integração

### <a name="use-analyze-in-excel-with-on-premises-datasets"></a>Utilizar a funcionalidade Analisar no Excel com conjuntos de dados no local

Os utilizadores na organização podem utilizar o Excel para ver e interagir com conjuntos de dados no local do Power BI. [Saiba mais](../collaborate-share/service-analyze-in-excel.md)

> [!NOTE]
> Desativar a opção **Exportar Dados** também impede os utilizadores de usarem a funcionalidade **Analisar no Excel**.

### <a name="use-arcgis-maps-for-power-bi"></a>Utilizar o ArcGIS Maps for Power BI

Os utilizadores na organização podem utilizar a visualização dos ArcGIS Maps for Power BI fornecida pela Esri. [Saiba mais](../visuals/power-bi-visualization-arcgis.md)

### <a name="use-global-search-for-power-bi-preview"></a>Utilizar a pesquisa global para o Power BI (Pré-visualização)

Os utilizadores na organização podem utilizar as funcionalidades de pesquisa externa que dependem do Azure Search.

## <a name="featured-tables-settings"></a>Definições das tabelas em destaque

Em **Definições do inquilino**, a definição do inquilino **Permitir ligações a tabelas em destaque** permite que os administradores do Power BI controlem que pessoas na organização podem utilizar tabelas em destaque na Galeria de Tipos de Dados do Excel. 

:::image type="content" source="media/service-admin-portal/admin-allow-connections-featured-tables.png" alt-text="Todas as ligações a tabelas em destaque":::

As ligações a tabelas em destaque também estão desativadas se a definição do inquilino **Exportar dados** estiver definida como **Desativado**.

Leia mais sobre as [tabelas em destaque do Power BI no Excel](../collaborate-share/service-excel-featured-tables.md).

## <a name="share-to-teams-tenant-setting"></a>Definição do inquilino Partilhar no Teams

A definição **Partilhar no Teams** está na secção **Definições do inquilino** do portal de administração do Power BI. A definição permite que as organizações ocultem os botões **Partilhar no Teams** no serviço Power BI. Quando estiverem desativados, os utilizadores não verão os botões **Partilhar no Teams** na barra de ação ou menus de contexto quando virem relatórios e dashboards no serviço Power BI.

![Captura de ecrã a mostrar a definição do inquilino Partilhar no Teams no portal de administração do Power BI.](media/service-admin-portal/service-teams-share-to-teams-tenant-setting.png)

Leia mais sobre [partilhar conteúdos do Power BI no Teams](../collaborate-share/service-share-report-teams.md).


## <a name="power-bi-visuals-settings"></a>Definições de elementos visuais do Power BI

### <a name="add-and-use-power-bi-visuals"></a>Adicionar e utilizar elementos visuais do Power BI

Os utilizadores na organização podem partilhar e interagir com elementos visuais do Power BI. [Saiba mais](../developer/visuals/power-bi-custom-visuals.md)

> [!NOTE]
> Esta definição pode ser aplicada a toda a organização ou pode ser limitada a grupos específicos.

O Power BI Desktop (a partir do lançamento de março de 2019) suporta a utilização da **Política de Grupo** para desativar a utilização de elementos visuais do Power BI nos computadores implementados numa organização.

<table>
<tr><th>Atributo</th><th>Valor</th>
</tr>
<td>chave</td>
    <td>Software\Policies\Microsoft\Power BI Desktop\</td>
<tr>
<td>valueName</td>
<td>EnableCustomVisuals</td>
</tr>
</table>

Um valor de 1 (decimal) ativa a utilização de elementos visuais do Power BI no Power BI (esta é a predefinição).

Um valor de 0 (decimal) desativa a utilização de elementos visuais do Power BI no Power BI.

### <a name="allow-only-certified-visuals"></a>Permitir apenas elementos visuais certificados

Os utilizadores na organização que receberam permissões para adicionar e utilizar elementos visuais do Power BI, representado pela definição "Adicionar e utilizar elementos visuais do Power BI", só poderão utilizar [elementos visuais do Power BI certificados](https://go.microsoft.com/fwlink/?linkid=2002010) (os elementos visuais não certificados serão bloqueados e apresentarão uma mensagem de erro quando utilizados). 


O Power BI Desktop (a partir do lançamento de março de 2019) suporta a utilização da **Política de Grupo** para desativar a utilização de elementos visuais do Power BI não certificados nos computadores implementados numa organização.

<table>
<tr><th>Atributo</th><th>Valor</th>
</tr>
<td>chave</td>
    <td>Software\Policies\Microsoft\Power BI Desktop\</td>
<tr>
<td>valueName</td>
<td>EnableUncertifiedVisuals</td>
</tr>
</table>

Um valor de 1 (decimal) ativa a utilização de elementos visuais do Power BI não certificados no Power BI (esta é a predefinição).

Um valor de 0 (decimal) desativa a utilização de elementos visuais do Power BI não certificados no Power BI (esta opção só ativa a utilização de [elementos visuais do Power BI certificados](https://go.microsoft.com/fwlink/?linkid=2002010)).

## <a name="r-visuals-settings"></a>Definições de elementos visuais R

### <a name="interact-with-and-share-r-visuals"></a>Interagir e partilhar visuais R

Os utilizadores na organização podem interagir e partilhar elementos visuais criados com scripts R. [Saiba mais](../visuals/service-r-visuals.md)

> [!NOTE]
> Esta definição aplica-se a toda a organização e não pode estar limitada a grupos específicos.

## <a name="audit-and-usage-settings"></a>Definições de utilização e auditoria

### <a name="create-audit-logs-for-internal-activity-auditing-and-compliance"></a>Criar registos de auditoria para auditoria de atividade interna e de conformidade

Os utilizadores na organização podem utilizar a auditoria para monitorizar as ações executadas no Power BI por outros utilizadores na organização. [Saiba mais](service-admin-auditing.md)

Esta definição tem de estar ativada para as entradas de registo de auditoria serem registadas. Pode existir um intervalo de 48 horas entre a ativação da auditoria e a capacidade de ver os dados da mesma. Se não vir logo os seus dados, consulte os registos de auditoria mais tarde. Pode existir um intervalo de tempo semelhante entre obter a permissão para ver os registos de auditoria e ter acesso aos mesmos.

> [!NOTE]
> Esta definição aplica-se a toda a organização e não pode estar limitada a grupos específicos.

### <a name="usage-metrics-for-content-creators"></a>Métricas de utilização para criadores de conteúdo

Os utilizadores na organização podem ver as métricas de utilização dos dashboards e os relatórios que criam. [Saiba mais](../collaborate-share/service-usage-metrics.md)

### <a name="per-user-data-in-usage-metrics-for-content-creators"></a>Dados por utilizador em métricas de utilização para criadores de conteúdo

As métricas de utilização para os criadores de conteúdo irão expor nomes a apresentar e endereços de e-mail de utilizadores que estão a aceder ao conteúdo. [Saiba mais](../collaborate-share/service-usage-metrics.md)

Por predefinição, os dados por utilizador estão ativados para métricas de utilização e as informações da conta do criador de conteúdo estão incluídas no relatório de métricas. Se não pretender recolher estas informações para todos os utilizadores, poderá desativar a funcionalidade para grupos de segurança específicos ou para toda a organização. As informações da conta dos utilizadores excluídos serão apresentadas no relatório como *Sem nome*.

## <a name="dashboard-settings"></a>Definições de dashboard

### <a name="data-classification-for-dashboards"></a>Classificação de dados para dashboards

Os utilizadores na organização podem identificar os dashboards com classificações que indicam os seus níveis de segurança. [Saiba mais](../create-reports/service-data-classification.md)

> [!NOTE]
> Esta definição aplica-se a toda a organização e não pode estar limitada a grupos específicos.

## <a name="developer-settings"></a>Definições de programador

### <a name="embed-content-in-apps"></a>Incorporar conteúdo em aplicações

Os utilizadores na organização podem incorporar dashboards e relatórios do Power BI em aplicações Software como Serviço (SaaS). Desativar esta definição impede os utilizadores de usarem as APIs REST para incorporar conteúdo do Power BI na respetiva aplicação. [Saiba mais](../developer/embedded/embedding.md)

### <a name="allow-service-principals-to-use-power-bi-apis"></a>Permitir que os principais de serviço utilizem as APIs do Power BI

As aplicações Web registadas no Azure Active Directory (Azure AD) utilizarão um principal de serviço atribuído para aceder às APIs do Power BI que não tenham um utilizador com sessão iniciada. Para que uma aplicação possa utilizar a autenticação do principal de serviço, esta tem de ser incluída num grupo de segurança permitido. [Saiba mais](../developer/embedded/embed-service-principal.md)

> [!NOTE]
> Os principais de serviço herdam as permissões de todas as definições do inquilino do Power BI do respetivo grupo de segurança. Para restringir as permissões, crie um grupo de segurança dedicado para os principais de serviço e adicione-o à lista "Exceto grupos de segurança específicos" para as definições do Power BI relevantes ativadas.

## <a name="dataflow-settings"></a>Definições do fluxo de dados

### <a name="create-and-use-dataflows"></a>Create and use dataflows (Criar e utilizar fluxos de dados)

Os utilizadores na organização podem criar e utilizar fluxos de dados. Para obter uma descrição geral dos fluxos de dados, veja [Preparação personalizada de dados no Power BI](../transform-model/service-dataflows-overview.md). Para ativar os fluxos de dados numa capacidade Premium, veja [Configurar cargas de trabalho](service-admin-premium-workloads.md).

> [!NOTE]
> Esta definição aplica-se a toda a organização e não pode estar limitada a grupos específicos.

## <a name="template-apps-settings"></a>Definições das aplicações de modelo

Três definições controlam a capacidade das aplicações de modelo de publicar ou instalar aplicações de modelo.

![Definições de aplicações de modelo no portal de administração do Power BI](media/service-admin-portal/power-bi-admin-portal-template-apps.png)

### <a name="publish-template-apps"></a>Publicar Aplicações de Modelo

Os utilizadores na organização podem criar áreas de trabalho de aplicações de modelo. Controle quais os utilizadores que podem publicar aplicações de modelo ou distribuí-las aos clientes fora da sua organização através do [AppSource](https://appsource.microsoft.com) ou de outro método de distribuição.

![Portal de administração do Power BI. Definição Criar aplicações de modelo](media/service-admin-portal/power-bi-admin-portal-template-app-settings.png)

### <a name="install-template-apps-listed-on-appsource"></a>Instalar aplicações de modelo listadas no AppSource

Os utilizadores na organização podem transferir e instalar aplicações de modelo **apenas** a partir do [AppSource](https://appsource.microsoft.com). Controle quais os utilizadores ou grupos de segurança específicos que podem instalar aplicações de modelo a partir do AppSource.

![Portal de administração do Power BI, definição Instalar aplicações de modelo](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-appsource.png)

### <a name="install-template-apps-not-listed-on-appsource"></a>Instalar aplicações de modelo não listadas no AppSource

Controle quais os utilizadores na organização que podem transferir e instalar aplicações de modelo **não listadas no [AppSource](https://appsource.microsoft.com)** .

![Portal de administração do Power BI, definição Instalar aplicações de modelo](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-nonappsource.png)

## <a name="capacity-settings"></a>Definições de capacidade

### <a name="power-bi-premium"></a>Power BI Premium

O separador **Power BI Premium** permite-lhe gerir todas as capacidades do Power BI Premium (SKU EM ou P) compradas para a sua organização. Todos os utilizadores na organização podem ver o separador **Power BI Premium**, mas apenas verão os conteúdos no mesmo se estiverem atribuídos como *Administrador de capacidade* ou como um utilizador com permissões de atribuição. Se um utilizador não tiver nenhuma permissão, será apresentada a mensagem seguinte.

![Sem acesso às definições Premium](media/service-admin-portal/premium-settings-no-access.png)

### <a name="power-bi-embedded"></a>Power BI Embedded

O separador **Power BI Embedded** permite-lhe ver as capacidades do Power BI Embedded (SKU A) que comprou para o seu cliente. Uma vez que apenas pode comprar SKUs A no Azure, vai [gerir as capacidades incorporadas no Azure](../developer/embedded/azure-pbie-create-capacity.md) no **Portal do Azure**.

Para obter mais informações sobre como gerir as definições do Power BI Embedded (SKU A), veja [O que é o Power BI Embedded?](../developer/embedded/azure-pbie-what-is-power-bi-embedded.md)

## <a name="embed-codes"></a>Códigos de incorporação

Enquanto administrador, pode ver os códigos de incorporação gerados para o seu inquilino para partilhar relatórios publicamente. Também pode revogar ou eliminar códigos. [Saiba mais](../collaborate-share/service-publish-to-web.md)

![Códigos de incorporação no portal de administração do Power BI](media/service-admin-portal/embed-codes.png)

 ## <a name=""></a><a name="organizational-visuals">Elemento visuais da organização</a> 

O separador **Elementos visuais da organização** permite-lhe implementar e gerir os elementos visuais do Power BI na sua organização. Com os elementos visuais organizacionais, pode facilmente implementar elementos visuais proprietários na sua organização, os quais os autores dos relatórios podem posteriormente detetar e importar para os seus relatórios do Power BI Desktop. [Saiba mais](../developer/visuals/power-bi-custom-visuals-organization.md)

> [!WARNING]
> Um elemento visual personalizado pode conter código com riscos de privacidade ou de segurança. Garanta que confia no autor e na origem do elemento visual personalizado antes de implementar no repositório da organização.

A página seguinte mostra todos os elementos visuais do Power BI que estão atualmente implementados no repositório da organização.

![Elemento visual de administração da organização](media/service-admin-portal/power-bi-custom-visuals-organizational-admin-01.png)

### <a name="add-a-new-custom-visual"></a>Adicionar um novo elemento visual personalizado

Para adicionar um novo elemento visual personalizado à lista, siga estes passos. 

1. No painel direito, selecione **Adicionar um elemento visual personalizado**.

    ![Formulário sobre elementos visuais do Power BI](media/service-admin-portal/power-bi-custom-visuals-organizational-admin-02.png)

1. Preencha o formulário **Adicionar elemento visual personalizado**:

    * **Escolher um ficheiro .pbiviz** (obrigatório): selecione um ficheiro de elemento visual personalizado para carregar. Apenas são suportados os elementos visuais do Power BI com a versão da API (leia aqui o que significa).

    Antes de carregar um elemento visual personalizado, deverá verificar a segurança e privacidade desse elemento visual para garantir que este cumpre os padrões da sua organização.

    * **Atribuir um nome ao elemento visual personalizado** (obrigatório): atribua um título curto ao elemento visual para que os utilizadores do Power BI Desktop compreendam facilmente o que faz

    * **Ícone**: O ficheiro de ícones que é mostrado na IU do Power BI Desktop.

    * **Descrição**: uma breve descrição do elemento visual para proporcionar mais contexto e informação ao utilizador

1. Selecione **Adicionar** para iniciar o pedido de carregamento. Se tiver êxito, poderá ver o novo item na lista. Se falhar, receberá uma mensagem de erro apropriada

### <a name="delete-a-custom-visual-from-the-list"></a>Eliminar um elemento visual personalizado da lista

Selecione o ícone de caixote do lixo para eliminar permanentemente um elemento visual no repositório.

> [!IMPORTANT]
> A eliminação é irreversível. Depois de eliminado, o elemento visual deixa imediatamente de ser composto nos relatórios existentes. Mesmo que carregue o mesmo elemento visual novamente, este não substitui o anterior que foi eliminado. No entanto, os utilizadores podem importar novamente o novo elemento visual e substituir a instância presente nos seus relatórios.

### <a name="disable-a-custom-visual-in-the-list"></a>Desativar um elemento visual personalizado na lista

Para desativar o elemento visual na loja organizacional, selecione o ícone de engrenagem. Na secção **Acesso**, desative o elemento visual personalizado.

Depois de desativar o elemento visual, este não será composto nos relatórios existentes e será apresentada a mensagem de erro abaixo.

*Este elemento visual personalizado já não está disponível. Contacte o seu administrador para obter detalhes.*

No entanto, os elementos visuais que são marcadores continuam a funcionar.

Após qualquer atualização ou alteração de administrador, os utilizadores do Power BI Desktop devem reiniciar a aplicação ou atualizar o browser no serviço Power BI para ver as atualizações.

### <a name="update-a-visual"></a>Atualizar um elemento visual

Para atualizar o elemento visual na loja organizacional, selecione o ícone de engrenagem. Procure e carregue uma nova versão do elemento visual.

Confirme que o ID de Elemento Visual permanece inalterado. O novo ficheiro substituirá o ficheiro anterior em todos os relatórios da organização. Contudo, se houver a possibilidade de a nova versão do elemento visual interromper qualquer utilização ou estrutura de dados da versão anterior do elemento visual, não substitua a versão anterior. Em vez disso, deve criar uma nova lista para a nova versão do elemento visual. Por exemplo, adicione um novo número de versão (versão X.X) ao título do novo elemento visual listado. Desta forma, torna-se claro que é o mesmo elemento visual apenas com um número de versão atualizado, assim, os relatórios existentes não vão interromper a sua funcionalidade. Novamente, verifique se o ID de Elemento Visual permanece inalterado. Da próxima vez que os utilizadores entrarem no repositório da organização a partir do Power BI Desktop, poderão importar a nova versão, que pedirá a substituição da versão atual que têm no relatório.

Para obter mais informações, veja [Perguntas frequentes sobre os elementos visuais do Power BI organizacionais](../developer/visuals/power-bi-custom-visuals-faq.md#organizational-power-bi-visuals)

## <a name=""></a><a name="dataflowStorage">Armazenamento do fluxo de dados (pré-visualização)</a>

Por predefinição, os dados utilizados com o Power BI são armazenados no armazenamento interno fornecido pelo Power BI. Com a integração dos fluxos de dados e do Azure Data Lake Storage Gen2 (ADLS Gen2), pode armazenar os seus fluxos de dados na conta do Azure Data Lake Storage Gen2 da sua organização. Para obter mais informações, veja [Fluxos de dados e integração do Azure Data Lake (Pré-visualização)](../transform-model/service-dataflows-azure-data-lake-integration.md).

## <a name="workspaces"></a>Áreas de trabalho

Enquanto administrador, pode ver as áreas de trabalho existentes no seu inquilino. Pode ordenar e filtrar a lista de áreas de trabalho e ver os detalhes de cada área de trabalho. As colunas da tabela correspondem às propriedades devolvidas pela [API Rest do administrador do Power BI](/rest/api/power-bi/admin) das áreas de trabalho. As áreas de trabalho pessoais são do tipo **GrupoPessoal**, as áreas de trabalho clássicas são do tipo **Grupo** e as novas experiências de área de trabalho são do tipo **Área de Trabalho**. Para obter mais informações, veja [Organizar o trabalho nas novas áreas de trabalho](../collaborate-share/service-new-workspaces.md).

Os administradores também podem gerir e recuperar áreas de trabalho, através do portal de administração ou dos cmdlets do PowerShell. 

![Lista de áreas de trabalho](media/service-admin-portal/workspaces-list.png)

No separador **Áreas de trabalho**, vê o *estado* de cada área de trabalho. A tabela abaixo fornece mais detalhes sobre o significado desses estados.

|Estado  |Descrição  |
|---------|---------|
| Ativo | Uma área de trabalho normal. Não indica nada sobre a utilização ou os respetivos conteúdos; apenas indica que a própria área de trabalho é "normal". |
| Isolado | Uma área de trabalho sem utilizador administrador. |
| Eliminado | Uma área de trabalho eliminada. Mantemos, durante 90 dias, metadados suficientes para restaurar a área de trabalho, se desejado. |
| A remover | Uma área de trabalho prestes a ser eliminada, mas que ainda não foi. Os utilizadores podem eliminar as suas próprias áreas de trabalho, colocando-as em A remover e, por fim, em Eliminado. |

## <a name="custom-branding"></a>Imagem corporativa personalizada

Como administrador, pode personalizar o aspeto do Power BI para toda a sua organização. Atualmente, existem três opções principais:

![Opções de imagem corporativa personalizada](media/service-admin-portal/power-bi-custom-branding.png)

* **Carregar Logótipo**: Para obter melhores resultados, carregue um logótipo que seja guardado como. png, 10 KB ou menor e, pelo menos, 200 x 30 píxeis.

* **Carregar imagem de capa**: Para obter melhores resultados, carregue uma imagem de capa que seja guardada como .jpg ou .png, 1 MB ou menor e, pelo menos, 1920 x 160 píxeis.

* **Selecionar cor do tema**: Pode selecionar o seu tema com base num número hexadecimal, RGB, valor ou na paleta fornecida.


Para obter mais informações, veja [Custom branding for your organization](https://aka.ms/orgBranding) (Imagem corporativa personalizada para a sua organização).

![Lista de áreas de trabalho](media/service-admin-portal/workspaces-list.png)

## <a name="manage-featured-content"></a>Gerir conteúdo em destaque

Enquanto administrador do inquilino, pode gerir todos os relatórios, dashboards e aplicações que tenham sido promovidos na secção Em destaque na Base do Power BI na sua organização.

- No portal de Administração, selecione **Conteúdo em destaque**.

Aqui pode ver uma descrição geral de quem destacou o conteúdo, quando o mesmo foi destacado e todos os respetivos metadados relevantes. Se algo parecer suspeito ou caso queira limpar a secção Em destaque, pode eliminar conteúdo promovido conforme necessário.

Veja [Conteúdo em destaque](#featured-content) neste artigo para obter informações sobre a ativação de conteúdo em destaque.

## <a name="next-steps"></a>Próximos passos

[Administrar o Power BI na sua Organização](service-admin-administering-power-bi-in-your-organization.md)  
[Compreender a função de administrador do Power BI](service-admin-role.md)  
[Fazer a auditoria do Power BI na sua organização](service-admin-auditing.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
