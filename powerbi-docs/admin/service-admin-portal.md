---
title: Portal de administração do Power BI
description: O portal de administração permite-lhe configurar definições ao nível da organização para o Power BI. Pode ver métricas de utilização, áreas de trabalho, elementos visuais da organização e conteúdo em destaque, configurar definições de inquilino e trabalhar com a capacidade.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 01/25/2021
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 8305d4662da9f4f7b8a5cce2b3badf5e70e88bc5
ms.sourcegitcommit: 5c5a27aa7ba21612df4c4096e635dfe4b9aaebcf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/27/2021
ms.locfileid: "98861313"
---
# <a name="administering-power-bi-in-the-admin-portal"></a>Administrar o Power BI no portal de administração

O portal de administração permite-lhe gerir as definições do Power BI para a sua organização. O portal inclui itens, como métricas de utilização, acesso ao centro de administração do Microsoft 365 e definições que regem o Power BI para todos os utilizadores.

O portal de administração completo está acessível para administradores globais e utilizadores com a função Administrador de serviço do Power BI. Se não estiver numa destas funções, verá apenas as **Definições de capacidade** no portal. Para obter mais informações sobre a função de administrador do serviço Power BI, veja [Noções básicas sobre a função de administrador do Power BI](service-admin-role.md).

## <a name="how-to-get-to-the-admin-portal"></a>Como aceder ao portal de administração

Tem de ser um administrador global ou um administrador de serviço do Power BI para aceder ao portal de administração do Power BI. Para obter mais informações sobre a função de administrador do serviço Power BI, veja [Noções básicas sobre a função de administrador do Power BI](service-admin-role.md). Para aceder ao portal de administração do Power BI, siga estes passos:

1. Inicie sessão no [Power BI](https://app.powerbi.com) com as credenciais da sua conta de administrador.

1. No cabeçalho da página, selecione **Definições** > **Portal de administração**.

   :::image type="content" source="media/service-admin-portal/settings-portal.png" alt-text="Menu de definições com o portal de administração selecionado.":::

O Portal de administração tem várias secções. O resto deste artigo disponibiliza informações sobre cada um dessas secções.

   :::image type="content" source="media/service-admin-portal/portal-menu.png" alt-text="Menu do portal de administração.":::

* [Métricas de utilização](#usage-metrics)
* [Utilizadores](#users)
* [Premium por utilizador (pré-visualização)](#premium-per-user-preview)
* [Registos de auditoria](#audit-logs)
* [Definições de inquilino](#tenant-settings)
* [Definições de capacidade](#capacity-settings)
* [Códigos de incorporação](#embed-codes)
* [Elementos visuais da organização](organizational-visuals.md#organizational-visuals)
* [Ligações do Azure (pré-visualização)](#azure-connections-preview)
* [Áreas de trabalho](#workspaces)
* [Imagem corporativa personalizada](#custom-branding)
* [Métricas de proteção](#protection-metrics)
* [Conteúdo em destaque](#featured-content)

## <a name="usage-metrics"></a>Métricas de utilização

As **Métricas de utilização** permitem-lhe monitorizar a utilização do Power BI da sua organização. Também mostram quais os utilizadores e os grupos da sua organização mais ativos no Power BI.

> [!NOTE]
> Quando aceder ao dashboard pela primeira vez ou depois de voltar após um período longo em que não visualizou o dashboard, provavelmente verá um ecrã de carregamento enquanto carregamos o dashboard.

Após o carregamento do dashboard, verá duas secções de mosaicos. A primeira secção inclui os dados de utilização dos utilizadores individuais e a segunda secção tem informações semelhantes dos grupos.

Segue-se uma análise detalhada do que pode ver em cada mosaico:

* Contagem distinta de todos os dashboards, relatórios e conjuntos de dados na área de trabalho do utilizador.
  
    ![Contagem distinta de dashboards, relatórios e conjuntos de dados](media/service-admin-portal/powerbi-admin-usage-metrics-number-tiles.png)


* O dashboard mais consumido pelo número de utilizadores que podem aceder ao mesmo. Por exemplo: Tem um dashboard que partilhou com três utilizadores. Também adicionou o dashboard a um pacote de conteúdos ao qual dois utilizadores diferentes se ligaram. A contagem do dashboard seria 6 (1 + 3 + 2).
  
    ![Dashboards mais consumidos](media/service-admin-portal/powerbi-admin-usage-metrics-top-dashboards.png)

* Os utilizadores de conteúdo mais populares ligados ao mesmo. O conteúdo será qualquer item a que os utilizadores possam aceder através do processo Obter Dados, como pacotes de conteúdos SaaS, pacotes de conteúdos Organizacionais, ficheiros ou bases de dados.

  
    ![Pacotes mais consumidos](media/service-admin-portal/powerbi-admin-usage-metrics-top-connections.png)

* Uma vista dos principais utilizadores com base no número de dashboards que têm, tanto os dashboards que criaram como os dashboards partilhados com eles.
  
    ![Principais utilizadores – dashboards](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-dashboards.png)

* Uma vista dos principais utilizadores com base no número de relatórios que têm.
  
    ![Principais utilizadores – relatórios](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-reports.png)

A segunda secção apresenta o mesmo tipo de informação, mas com base em grupos. Esta secção permite-lhe ver quais os grupos mais ativos na sua organização e o tipo de conteúdo que estão a consumir.

Com estes dados, pode obter informações reais sobre como as pessoas estão a utilizar o Power BI na sua organização.

## <a name="control-usage-metrics"></a>Controlar métricas de utilização

Os relatórios de métrica de utilização são uma funcionalidade que o administrador do Power BI ou global pode ativar ou desativar. Os administradores têm controlo granular sobre quais utilizadores têm acesso às métricas de utilização. As métricas estão **Ativadas** por predefinição para todos os utilizadores na organização.

Os administradores também podem determinar se os criadores de conteúdo podem ver dados por utilizador nas métricas de utilização. 

Veja [Monitorizar as métricas de utilização para dashboards e relatórios do Power BI](../collaborate-share/service-usage-metrics.md) para obter detalhes sobre os relatórios.

### <a name="usage-metrics-for-content-creators"></a>Métricas de utilização para criadores de conteúdo

1. No Portal de administração, selecione **Definições de inquilino** > **Definições de auditoria e utilização** > **Métricas de utilização para criadores de conteúdo**.

    ![Definições de inquilino no portal de administração para métricas de utilização](media/service-admin-portal/power-bi-admin-usage-metrics.png)

1. Ative (ou desative) as métricas de utilização > **Aplicar**.

    ![Métrica de utilização ativada](../collaborate-share/media/service-usage-metrics/power-bi-tenant-settings-updated.png)

### <a name="per-user-data-in-usage-metrics-for-content-creators"></a>Dados por utilizador em métricas de utilização para criadores de conteúdo

Por predefinição, os dados por utilizador estão ativados para métricas de utilização e as informações da conta estão incluídas no relatório de métricas. Se não quiser incluir informações da conta para alguns ou para todos os utilizadores, desative a funcionalidade para grupos de segurança específicos ou para toda a organização. As informações da conta são apresentadas no relatório como *Sem nome*.

![Dados de utilização por utilizador](media/service-admin-portal/power-bi-admin-per-user-usage-data.png)

### <a name="delete-all-existing-usage-metrics-content"></a>Eliminar todo o conteúdo das métricas de utilização existente

Ao desativar as métricas de utilização para toda a respetiva organização, os administradores também podem escolher uma ou ambas as opções para:

- **Eliminar todo o conteúdo das métricas de utilização existente** para eliminar todos os relatórios e mosaicos de dashboard existentes que foram criados com os conjuntos de dados e relatórios de métricas de utilização. Esta opção remove todo o acesso a dados da métrica de utilização por parte de todos os utilizadores na organização que possam estar a utilizá-lo.
- **Eliminar todos os dados existentes por utilizador no conteúdo das métricas de utilização atual** para remover todo o acesso aos dados por parte de todos os utilizadores na organização que possam estar a utilizá-los.

Tenha cuidado, uma vez que eliminar o conteúdo das métricas de utilização por utilizador existente é irreversível.

## <a name="users"></a>Utilizadores

Os utilizadores, grupos e administradores do Power BI são geridos no centro de administração do Microsoft 365. O separador **Utilizadores** disponibiliza uma ligação para o centro de administração.

![Aceda ao centro de administração do Microsoft 365](media/service-admin-portal/powerbi-admin-manage-users.png)

## <a name="premium-per-user-preview"></a>Premium por utilizador (pré-visualização)

O Premium por utilizador é uma nova forma de licenciar funcionalidades Premium por utilizador. Esta funcionalidade encontra-se em pré-visualização. Depois de ser atribuída uma licença Premium por utilizador a, pelo menos, um utilizador, as funcionalidades associadas poderão ser ativadas em qualquer área de trabalho. Os administradores poderão gerir as definições de atualização automática e da carga de trabalho do conjunto de dados que são apresentadas aos utilizadores e os valores predefinidos. Por exemplo, o acesso ao Ponto Final XMLA pode ser desativado, definido como só de leitura ou definido como leitura/escrita.

   :::image type="content" source="media/service-admin-portal/premium-per-user-options.png" alt-text="Definições Premium por utilizador":::.

Consulte [FAQ do Power BI Premium Por Utilizador (pré-visualização)](service-premium-per-user-faq.md) para saber mais sobre este modelo de licenciamento.

## <a name="audit-logs"></a>Registos de auditoria

Os registos de auditoria do Power BI são geridos no centro de Segurança e Conformidade do Office 365. O separador **Registos de auditoria** proporciona uma ligação para o centro de Segurança e Conformidade. Para saber mais, veja [Controlar as atividades dos utilizadores no Power BI](service-admin-auditing.md).

Para utilizar os registos de auditoria, verifique se a definição [**Criar registos de auditoria para auditoria de atividade interna e de conformidade**](#create-audit-logs-for-internal-activity-auditing-and-compliance) está ativada.

## <a name="tenant-settings"></a>Definições do inquilino

As **Definições de inquilino** permitem um controlo refinado sobre as funcionalidades que são disponibilizadas à sua organização. Se tiver problemas com dados confidenciais, algumas das nossas funcionalidades poderão não ser adequadas para a sua organização ou poderá querer apenas uma determinada funcionalidade disponível para um grupo específico.

> [!NOTE]
> As definições de inquilino que controlam a disponibilidade das funcionalidades na interface do utilizador do Power BI podem ajudar a estabelecer políticas de governação, mas não são uma medida de segurança. Por exemplo, a definição **Exportar dados** não restringe as permissões de um utilizador do Power BI num conjunto de dados. Os utilizadores do Power BI com acesso de leitura a um conjunto de dados têm permissão para consultar este conjunto de dados e poderão conseguir fazer persistir os resultados sem utilizar a funcionalidade **Exportar dados** na interface do utilizador do Power BI.

As seguintes secções explicam as definições no separador **Definições de inquilino**.

> [!NOTE]
> Pode demorar até 15 minutos para a alteração à definição ter efeito para todos os utilizadores na sua organização.

Várias das definições podem ter um de três estados:

* **Desativado para toda a organização**: Ninguém na sua organização pode utilizar esta funcionalidade.

    ![Definição Desativado para todos](media/service-admin-portal/powerbi-admin-tenant-settings-disabled.png)

* **Ativado para toda a organização**: Todas as pessoas na sua organização podem utilizar esta funcionalidade.

    ![Definição Ativado para todos](media/service-admin-portal/powerbi-admin-tenant-settings-enabled.png)

* **Ativado para um subconjunto da organização**: grupos de segurança específicos na sua organização têm permissão para utilizar esta funcionalidade.

    Também pode ativar uma funcionalidade para toda a organização, **Exceto grupos de segurança específicos**.

    ![Definição Ativado para um subconjunto](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except.png)

    Pode também combinar definições para ativar a funcionalidade apenas para um grupo específico de utilizadores ou desativá-la para um grupo de utilizadores. Utilizar esta abordagem assegura que determinados utilizadores não tenham acesso à funcionalidade mesmo que estejam no grupo permitido. Aplica-se a definição mais restritiva para um utilizador.

    ![Definição Ativado com exceções](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except2.png)

As próximas secções fornecem uma descrição geral dos diferentes tipos de definições de inquilino.

## <a name="help-and-support-settings"></a>Definições de ajuda e suporte

### <a name="publish-get-help-information"></a>Publicar informações para "Obter Ajuda"

![Publicar informações para obter ajuda](media/service-admin-portal/powerbi-admin-tenant-settings-gethelp.png)

Os administradores podem especificar URLs internos para substituir o destino de ligações no menu de ajuda do Power BI e para atualizações de licença. Se forem definidos URLs personalizados, os utilizadores da organização acedem a recursos de ajuda e suporte internos em vez de acederem aos destinos predefinidos. Os seguintes destinos de recursos podem ser personalizados:

* **Learn**. Por predefinição, esta ligação do menu de ajuda tem como destino uma [lista de todos os nossos módulos e percursos de aprendizagem do Power BI](/learn/browse/?products=power-bi). Para direcionar esta ligação para os recursos de preparação internos, defina um URL personalizado para a **Documentação de preparação**.

* **Comunidade**. Para direcionar os utilizadores para um fórum interno a partir do menu de ajuda em vez da [Comunidade do Power BI](https://community.powerbi.com/), defina um URL personalizado para um **Fórum de debate**.

* **Atualizações de licenciamento**. Os utilizadores com uma licença do Power BI (gratuito) podem ter a oportunidade de atualizar a respetiva conta para o Power BI Pro ao utilizar o serviço. Se especificar um URL interno para **Pedidos de licenciamento**, redireciona os utilizadores para um fluxo de pedido e compra interno e impede que estes façam uma compra de gestão personalizada. Se quiser impedir os utilizadores de comprarem licenças, mas não de iniciarem uma avaliação do Power BI Pro, veja [Permitir que os utilizadores experimentem o Power BI Pro](#allow-users-to-try-power-bi-paid-features) para separar as experiências de compra e avaliação.

* **Obter ajuda**. Para direcionar os utilizadores para o suporte técnico interno a partir do menu de ajuda em vez do [Suporte do Power BI](https://powerbi.microsoft.com/support/), defina um URL personalizado para o **Suporte Técnico**.

### <a name="receive-email-notifications-for-service-outages-or-incidents"></a>Receber notificações por e-mail sobre incidentes ou indisponibilidades do serviço

Os grupos de segurança com capacidade de correio receberão notificações de e-mail se este inquilino for afetado por um incidente ou uma indisponibilidade do serviço. Saiba mais sobre as [Notificações de interrupção do serviço](service-interruption-notifications.md).

### <a name="allow-users-to-try-power-bi-paid-features"></a>Permitir que os utilizadores experimentem funcionalidades pagas do Power BI

![IU da definição Permitir que os utilizadores experimentem o Power BI Pro](media/service-admin-portal/allow-pro-trial.png)

A definição para **Permitir que os utilizadores experimentem funcionalidades pagas do Power BI** está ativada por predefinição. Esta definição aumenta o controlo sobre como os utilizadores adquirem as licenças do Power BI Pro. Nos cenários em que bloqueou a compra de gestão personalizada, esta definição permite que os utilizadores iniciem uma avaliação do Power BI Pro. A experiência do utilizador final depende da forma como combina as definições das licenças. A tabela abaixo mostra como diferentes combinações de definições afetam a experiência de atualização do Power BI (gratuito) para o Power BI Pro:

| Definição Compra de gestão personalizada | Definição Permitir que os utilizadores experimentem o Power BI Pro | Experiência do utilizador final |
| ------ | ------ | ----- |
| Ativado | Desativado | O utilizador pode comprar uma licença do Pro, mas não pode iniciar uma avaliação |
| Ativado | Ativado | O utilizador pode iniciar uma avaliação gratuita do Pro e atualizar para uma licença paga |
| Desativado | Desativado | O utilizador vê uma mensagem para contactar o administrador de TI para pedir uma licença |
| Desativado | Ativado | O utilizador pode iniciar uma avaliação do Pro, mas tem de contactar o administrador de TI para obter uma licença paga |

> [!NOTE]
> Pode adicionar um URL interno para pedidos de licenciamento nas [Definições de ajuda e suporte](#help-and-support-settings). Se definir o URL, este substituirá a experiência de compra de gestão personalizada predefinida. Não redirecionará a inscrição para uma licença de avaliação do Power BI Pro. Os utilizadores que podem comprar uma licença nos cenários descritos na tabela acima são redirecionados para o URL interno.

Para saber mais, veja [Ativar ou desativar a compra e inscrição de gestão personalizada](service-admin-disable-self-service.md)

### <a name="show-a-custom-message-before-publishing-reports"></a>Apresentar uma mensagem personalizada antes de publicar relatórios  

Os administradores podem indicar uma mensagem personalizada para ser apresentada antes de um utilizador publicar um relatório do Power BI Desktop. Depois de ativar a definição, tem de indicar uma **Mensagem personalizada**. A Mensagem personalizada pode ser texto simples ou seguir a sintaxe de Markdown, como mostra a seguinte mensagem de exemplo:

```markdown
#### Important Disclaimer 

Before publishing the report to a workspace, be sure to validate that the appropriate users or groups have access to the destination workspace. If some users or groups should *not* have access to the content and underlying artifacts, remove or modify their access to the workspace, or publish the report to a different workspace. [Learn more](https://docs.microsoft.com/power-bi/collaborate-share/service-create-the-new-workspaces#give-access-to-your-workspace). 
```

A área de texto da **Mensagem personalizada** suporta o deslocamento, pelo que pode fornecer uma mensagem com até 5000 carateres.

:::image type="content" source="media/service-admin-portal/admin-show-custom-message.png" alt-text="Captura de ecrã a mostrar a caixa de mensagem personalizada.":::

Quando os utilizadores publicarem relatórios em áreas de trabalho no Power BI, verão a mensagem que escreveu.

:::image type="content" source="media/service-admin-portal/admin-user-show-custom-message.png" alt-text="A caixa de diálogo que os utilizadores veem quando publicam relatórios numa área de trabalho.":::

Como ocorre noutras definições de inquilino, pode selecionar a quem se aplica a **Mensagem personalizada**:

- **Toda a organização**.
- **Grupos de segurança específicos**.
- Ou **Exceto grupos de segurança específicos**.

## <a name="workspace-settings"></a>Definições de área de trabalho

Em **Definições de inquilino**, o portal de administração possui três secções para controlar áreas de trabalho:

- [Criar as novas experiências de área de trabalho](#create-the-new-workspaces).
- [Utilizar conjuntos de dados em áreas de trabalho](#use-datasets-across-workspaces).
- [Impedir a criação de áreas de trabalho clássicas](#block-classic-workspace-creation).

### <a name="create-the-new-workspaces"></a>Criar as novas áreas de trabalho

As áreas de trabalho são locais onde os utilizadores colaboram em dashboards, relatórios e outros conteúdos. Os administradores utilizam a definição **Criar áreas de trabalho (nova experiência de área de trabalho)** para indicar quais são os utilizadores na organização que podem criar áreas de trabalho. Os administradores podem permitir que todos os utilizadores ou nenhum utilizador numa organização crie novas áreas de trabalho de experiências de área de trabalho. Também podem limitar a criação a membros de grupos de segurança específicos. Saiba mais sobre as [áreas de trabalho](../collaborate-share/service-new-workspaces.md).

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

Para obter mais informações, veja [Introdução aos conjuntos de dados em áreas de trabalho](../connect-data/service-datasets-across-workspaces.md).

### <a name="block-classic-workspace-creation"></a>Impedir a criação de áreas de trabalho clássicas

Os administradores podem controlar se a organização pode criar áreas de trabalho clássicas. Quando esta definição está ativada, os utilizadores que criam uma área de trabalho só podem criar áreas de trabalho da nova experiência. 

![Impedir a criação de áreas de trabalho clássicas](media/service-admin-portal/power-bi-admin-block-classic-workspaces.png)

Quando estiver ativada, os Grupos do Office 365 criados recentemente não serão apresentados na lista de áreas de trabalho do Power BI. As áreas de trabalho clássicas existentes continuarão a ser apresentadas na lista. Quando a definição estiver desativada, todos os Grupos do Office 365 dos quais o utilizador é membro aparecerão na lista de áreas de trabalho. Leia mais sobre as [áreas de trabalho da nova experiência](../collaborate-share/service-new-workspaces.md).

## <a name="export-and-sharing-settings"></a>Definições de exportação e partilha

### <a name="allow-azure-active-directory-guest-users-to-access-power-bi"></a>Permitir que os utilizadores convidados do Azure Active Directory acedam ao Power BI

Ao ativar esta definição, permite que os utilizadores do Azure AD B2B (Azure Active Directory Business-to-Business) acedam ao Power BI. Se desativar esta definição, os utilizadores convidados verão um erro ao tentar aceder ao Power BI. Se desativar esta definição para toda a organização, também impedirá que os utilizadores convidem pessoas para a sua organização. Utilize a opção de grupos de segurança específicos para controlar que utilizadores convidados podem aceder ao Power BI.

![Permitir que os utilizadores convidados do Azure Active Directory acedam ao Power BI](media/service-admin-portal/powerbi-admin-allow-aad-b2b-guests.png)

### <a name="invite-external-users-to-your-organization"></a>Convidar utilizadores externos para a sua organização 

A definição **Convidar utilizadores externos para a sua organização** ajuda as organizações a decidir se os novos utilizadores externos podem ser convidados para a organização através das experiências de partilha e permissões do Power BI. Se a definição estiver desativada, um utilizador externo que ainda não seja um utilizador convidado na organização não poderá ser adicionado à organização através do Power BI.

![Convidar utilizadores externos para a sua organização](media/service-admin-portal/powerbi-admin-allow-invite-aad-b2b-guests.png)

> [!IMPORTANT]
> Esta definição chamava-se anteriormente "Partilhar conteúdos com utilizadores externos". O novo nome reflete com mais precisão o que a definição faz.

Para convidar utilizadores externos para a sua organização, um utilizador também precisa da função Emitente de Convites do Azure Active Directory. Esta definição só controla a capacidade de convidar através do Power BI. 

### <a name="allow-external-guest-users-to-edit-and-manage-content-in-the-organization"></a>Permitir aos utilizadores externos convidados editarem e gerirem conteúdo na organização

Os utilizadores convidados do Azure AD B2B podem editar e gerir o conteúdo na organização. [Saiba mais](service-admin-azure-ad-b2b.md)

A seguinte imagem mostra a opção Permitir aos utilizadores externos convidados editarem e gerirem conteúdo na organização.

![Permitir aos utilizadores externos convidados editarem e gerirem conteúdo na organização](media/service-admin-portal/powerbi-admin-tenant-settings-b2b-guest-edit-manage.png)

No portal de administração, também controla quais os utilizadores que têm permissão para convidar utilizadores externos para a organização. Veja [Partilhar conteúdo com utilizadores externos](#export-and-sharing-settings) neste artigo para obter mais detalhes.

### <a name="publish-to-web"></a>Publicar na Web

Enquanto administrador do Power BI, a definição **Publicar na Web** dá-lhe opções que permite aos utilizadores criar códigos de incorporação para publicar relatórios na Web. Esta funcionalidade permite-lhe disponibilizar o relatório e os dados que contém a qualquer pessoa na Web. Saiba mais sobre como [publicar na Web](../collaborate-share/service-publish-to-web.md).

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
|**Incorporar códigos** no portal de administração|O estado tem um dos seguintes valores:<br>* Ativo<br>* Não suportado<br>* Bloqueado|O estado apresenta **Desativado**|O estado tem um dos seguintes valores:<br>* Ativo<br>* Não suportado<br>* Bloqueado<br><br>Se um utilizador não tiver autorizações com base na definição do inquilino, o estado é apresentado como **Em violação**.|
|Relatórios publicados existentes|Todos ativados|Todos desativados|Os relatórios continuam a ser compostos para todos.|

### <a name="copy-and-paste-visuals"></a>Copiar e colar elementos visuais

Os utilizadores da organização podem copiar elementos visuais a partir de um mosaico ou elemento visual de relatório e colá-los como imagens estáticas em aplicações externas.

![Captura de ecrã a mostrar o botão para ativar Copiar e colar elementos visuais.](media/service-admin-portal/powerbi-admin-portal-copy-paste-visuals-setting.png)

### <a name="export-to-excel"></a>Exportar para o Excel

Os utilizadores da organização podem exportar os dados de uma visualização para um ficheiro do Excel.

![Captura de ecrã a mostrar a definição Exportar para Excel](media/service-admin-portal/powerbi-admin-portal-export-to-excel-setting.png)

### <a name="export-to-csv"></a>Exportar para .csv

Os utilizadores na organização podem exportar dados de um mosaico, de uma visualização ou de um relatório paginado para um ficheiro .csv.

![Captura de ecrã a mostrar a definição Exportar para .csv](media/service-admin-portal/powerbi-admin-portal-export-to-csv-setting.png)

### <a name="download-reports"></a>Transferir relatórios

Os utilizadores na organização podem transferir ficheiros .pbix e relatórios paginados.

![Captura de ecrã a mostrar a definição Transferir relatórios.](media/service-admin-portal/powerbi-admin-portal-download-reports-setting.png)

### <a name="allow-live-connections"></a>Permitir ligações dinâmicas

Os utilizadores na organização podem utilizar o Live Connect do serviço Power BI, A permissão de ligações dinâmicas também permite que os utilizadores tirem partido da funcionalidade Analisar no Excel.

![Captura de ecrã a mostrar a definição Permitir ligações dinâmicas.](media/service-admin-portal/powerbi-admin-portal-allow-live-connections-setting.png)

### <a name="export-reports-as-powerpoint-presentations-or-pdf-documents"></a>Exportar relatórios como apresentações do PowerPoint ou documentos PDF

Os utilizadores na organização podem exportar relatórios como ficheiros do PowerPoint ou documentos PDF.

![Captura de ecrã a mostrar Exportar relatórios como PowerPoint ou documentos PDF.](media/service-admin-portal/powerbi-admin-portal-export-pptx-pdf-setting.png)

### <a name="export-reports-as-mhtml-documents"></a>Exportar relatórios como documentos MHTML

Os utilizadores na organização podem exportar Relatórios paginados como documentos MHTML.

![Captura de ecrã a mostrar a definição Exportar para MHTML.](media/service-admin-portal/powerbi-admin-portal-export-mhtml-setting.png)

### <a name="export-reports-as-word-documents"></a>Exportar relatórios como documentos Word

Os utilizadores na organização podem exportar Relatórios paginados como documentos Word.

![Captura de ecrã a mostrar a definição Exportar para Word.](media/service-admin-portal/powerbi-admin-portal-export-word-setting.png)

### <a name="export-reports-as-xml-documents"></a>Exportar relatórios como documentos XML

Os utilizadores na organização podem exportar Relatórios paginados como documentos XML.

![Captura de ecrã a mostrar a definição Exportar para XML.](media/service-admin-portal/powerbi-admin-portal-export-xml-setting.png)

### <a name="export-reports-as-image-files-preview"></a>Exportar relatórios como ficheiros de imagem (pré-visualização)

Os utilizadores na organização podem utilizar a API Exportar relatório para ficheiro para exportar os relatórios como ficheiros de imagem.

![Captura de ecrã a mostrar a definição Exportar como imagem.](media/service-admin-portal/powerbi-admin-portal-export-as-image-setting.png)

### <a name="print-dashboards-and-reports"></a>Imprimir dashboards e relatórios


![Captura de ecrã a mostrar a definição Imprimir dashboards e relatórios.](media/service-admin-portal/powerbi-admin-portal-print-dashboards-reports-setting.png)

### <a name="certification"></a>Certificação
Permite aos utilizadores desta organização certificarem conjuntos de dados, fluxos de dados, relatórios e aplicações. Para obter mais detalhes, veja [Ativar a certificação de conteúdo](service-admin-setup-certification.md).

### <a name="email-subscriptions"></a>Subscrições de E-mail
Os utilizadores na organização podem criar subscrições por e-mail. Saiba mais sobre as [subscrições](../collaborate-share/service-report-subscribe.md).

![Ativar as subscrições por e-mail](media/service-admin-portal/power-bi-manage-email-subscriptions.png)

### <a name="featured-content"></a>Conteúdo em destaque

Permita que alguns ou todos os autores de relatórios na sua organização destaquem os respetivos conteúdos na secção Em destaque da Base do Power BI. Os novos utilizadores verão o conteúdo em destaque na parte superior da respetiva Base do Power BI. O conteúdo em destaque move-se na Base à medida que os utilizadores adicionam conteúdos **Favoritos**, **Frequentes** e **Recentes**. 

Recomendamos que comece com um pequeno conjunto de promotores. Permitir que toda a organização destaque conteúdos na Base pode dificultar a monitorização de todos os conteúdos promovidos. 

Após permitir conteúdo em destaque, também pode geri-lo no Portal de administração. Veja [Gerir conteúdo em destaque](#manage-featured-content)neste artigo para ler sobre como controlar conteúdo em destaque no seu domínio.

### <a name="allow-connections-to-featured-tables"></a>Permitir ligações a tabelas em destaque

Esta definição permite aos administradores do Power BI controlarem quem na organização pode utilizar as tabelas em destaque na Galeria de Tipos de Dados do Excel. 

![Captura de ecrã a mostrar a definição Permitir ligações a tabelas em destaque.](media/service-admin-portal/powerbi-admin-portal-allow-connections-featured-tables-setting.png)

>[!NOTE]
>Se a definição [Permitir ligações dinâmicas](#allow-live-connections) estiver definida como Desativada, as ligações a tabelas em destaque também estarão desativadas.

Leia mais sobre as [tabelas em destaque do Power BI no Excel](../collaborate-share/service-excel-featured-tables.md).

### <a name="share-to-teams"></a>Partilhar no Teams

Esta definição permite que as organizações ocultem os botões **Partilhar no Teams** no serviço Power BI. Quando estiverem desativados, os utilizadores não verão os botões **Partilhar no Teams** na barra de ação ou menus de contexto quando virem relatórios e dashboards no serviço Power BI.

![Captura de ecrã a mostrar a definição do inquilino Partilhar no Teams no portal de administração do Power BI.](media/service-admin-portal/service-teams-share-to-teams-tenant-setting.png)

Leia mais sobre [partilhar conteúdos do Power BI no Teams](../collaborate-share/service-share-report-teams.md).

## <a name="content-pack-and-app-settings"></a>Definições da aplicação e do pacote de conteúdos

### <a name="publish-content-packs-and-apps-to-the-entire-organization"></a>Publicar pacotes de conteúdo e aplicações em toda a organização

Os administradores podem utilizar esta definição para decidir que utilizadores podem publicar pacotes de conteúdo e aplicações em toda a organização, ao invés de grupos específicos. Saiba mais sobre como [publicar aplicações](../collaborate-share/service-create-distribute-apps.md).

A imagem seguinte mostra a opção **A minha organização inteira** durante a criação de um pacote de conteúdos.

![Publicar o pacote de conteúdos para a organização](media/service-admin-portal/powerbi-admin-publish-entire-org.png)

### <a name="create-template-apps-and-organizational-content-packs"></a>Criar pacotes de conteúdos organizacionais e aplicações de modelo

Os utilizadores na organização podem criar pacotes de conteúdos organizacionais e aplicações de modelo que utilizam conjuntos de dados incorporados numa origem de dados no Power BI Desktop. Saiba mais sobre as [aplicações de modelo](../connect-data/service-template-apps-create.md).

### <a name="push-apps-to-end-users"></a>Aplicações push para utilizadores finais

Os criadores dos relatórios podem partilhar as aplicações diretamente com os utilizadores finais sem necessitar da instalação do [AppSource](https://appsource.microsoft.com). Saiba mais sobre como [instalar aplicações automaticamente para os utilizadores finais](../collaborate-share/service-create-distribute-apps.md#automatically-install-apps-for-end-users).

## <a name="integration-settings"></a>Definições de integração

### <a name="allow-xmla-endpoints-and-analyze-in-excel-with-on-premises-datasets"></a>Permitir pontos finais XMLA e Analisar no Excel com conjuntos de dados no local

Os utilizadores na organização podem utilizar o Excel para ver e interagir com conjuntos de dados no local do Power BI. Além disso, também permite ligações aos pontos finais XMLA. [Saiba mais](../collaborate-share/service-analyze-in-excel.md)

### <a name="use-arcgis-maps-for-power-bi"></a>Utilizar o ArcGIS Maps for Power BI

Os utilizadores na organização podem utilizar a visualização dos ArcGIS Maps for Power BI fornecida pela Esri. [Saiba mais](../visuals/power-bi-visualizations-arcgis.md)

### <a name="use-global-search-for-power-bi-preview"></a>Utilizar a pesquisa global para o Power BI (Pré-visualização)

Os utilizadores na organização podem utilizar as funcionalidades de pesquisa externa que dependem do Azure Search.

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

### <a name="web-content-on-dashboard-tiles"></a>Conteúdos Web em mosaicos do dashboard

Os utilizadores na organização podem adicionar e ver mosaicos de conteúdos Web em dashboards do Power BI. [Saiba mais](../create-reports/service-dashboard-add-widget.md)

> [!NOTE]
> Isto pode expor a sua organização a riscos de segurança provocados por conteúdos Web maliciosos.

## <a name="developer-settings"></a>Definições de programador

### <a name="embed-content-in-apps"></a>Incorporar conteúdo em aplicações

Os utilizadores na organização podem incorporar dashboards e relatórios do Power BI em aplicações Software como Serviço (SaaS). Desativar esta definição impede os utilizadores de usarem as APIs REST para incorporar conteúdo do Power BI na respetiva aplicação. [Saiba mais](../developer/embedded/embedding.md)

### <a name="allow-service-principals-to-use-power-bi-apis"></a>Permitir que os principais de serviço utilizem as APIs do Power BI

As aplicações Web registadas no Azure Active Directory (Azure AD) utilizarão um principal de serviço atribuído para aceder às APIs do Power BI que não tenham um utilizador com sessão iniciada. Para que uma aplicação possa utilizar a autenticação do principal de serviço, o respetivo principal de serviço tem de ser incluído num grupo de segurança permitido. [Saiba mais](../developer/embedded/embed-service-principal.md)

> [!NOTE]
> Os principais de serviço herdam as permissões de todas as definições do inquilino do Power BI do respetivo grupo de segurança. Para restringir as permissões, crie um grupo de segurança dedicado para os principais de serviço e adicione-o à lista "Exceto grupos de segurança específicos" para as definições do Power BI relevantes ativadas.

## <a name="dataflow-settings"></a>Definições do fluxo de dados

### <a name="create-and-use-dataflows"></a>Create and use dataflows (Criar e utilizar fluxos de dados)

Os utilizadores na organização podem criar e utilizar fluxos de dados. Para obter uma descrição geral dos fluxos de dados, veja [Preparação personalizada de dados no Power BI](../transform-model/dataflows/dataflows-introduction-self-service.md). Para ativar os fluxos de dados numa capacidade Premium, veja [Configurar cargas de trabalho](service-admin-premium-workloads.md).

> [!NOTE]
> Esta definição aplica-se a toda a organização e não pode estar limitada a grupos específicos.

## <a name="template-apps-settings"></a>Definições das aplicações de modelo

Três definições controlam a capacidade das aplicações de modelo de publicar ou instalar aplicações de modelo.

![Definições das aplicações de modelo no portal de administração do Power BI](media/service-admin-portal/power-bi-admin-portal-template-apps.png)

### <a name="publish-template-apps"></a>Publicar Aplicações de Modelo

Os utilizadores na organização podem criar áreas de trabalho de aplicações de modelo. Controle quais os utilizadores que podem publicar aplicações de modelo ou distribuí-las aos clientes fora da sua organização através do [AppSource](https://appsource.microsoft.com) ou de outro método de distribuição.

![Definição Publicar aplicações de modelo ativada para toda a organização](media/service-admin-portal/power-bi-admin-portal-template-app-settings.png)

### <a name="install-template-apps-listed-on-appsource"></a>Instalar aplicações de modelo listadas no AppSource

Os utilizadores na organização podem transferir e instalar aplicações de modelo **apenas** a partir do [AppSource](https://appsource.microsoft.com). Controle quais os utilizadores ou grupos de segurança específicos que podem instalar aplicações de modelo a partir do AppSource.

![Definição Instalar aplicações de modelo](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-appsource.png)

### <a name="install-template-apps-not-listed-on-appsource"></a>Instalar aplicações de modelo não listadas no AppSource

Controle quais os utilizadores na organização que podem transferir e instalar aplicações de modelo **não listadas no [AppSource](https://appsource.microsoft.com)** .

![Definição Instalar aplicações de modelo não listadas no AppSource](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-nonappsource.png)

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

## <a name="organizational-visuals"></a>Elementos visuais da organização

Todas as definições de administrador de elementos visuais do Power BI, incluindo as definições de inquilino dos elementos visuais do Power BI, são descritas em [Gerir as definições de administrador de elementos visuais do Power BI](organizational-visuals.md).

## <a name="azure-connections-preview"></a>Ligações do Azure (pré-visualização)

### <a name="tenant-level-storage-preview"></a>Armazenamento ao nível do inquilino (pré-visualização)

Por predefinição, os dados utilizados com o Power BI são armazenados no armazenamento interno fornecido pelo Power BI. Com a integração dos fluxos de dados e do Azure Data Lake Storage Gen2 (ADLS Gen2), pode armazenar os seus fluxos de dados na conta do Azure Data Lake Storage Gen2 da sua organização. Para obter mais informações, veja [Fluxos de dados e integração do Azure Data Lake (Pré-visualização)](../transform-model/dataflows/dataflows-azure-data-lake-storage-integration.md).

### <a name="workspace-level-storage-permissions-preview"></a>Permissões de armazenamento ao nível da área de trabalho (pré-visualização)

Por predefinição, os administradores de áreas de trabalho não podem ligar a sua própria conta de armazenamento. Com esta funcionalidade de pré-visualização, pode ativar uma definição que permite que os administradores de áreas de trabalho liguem a sua própria conta de armazenamento.

## <a name="workspaces"></a>Áreas de trabalho

Enquanto administrador, pode ver as áreas de trabalho existentes no seu inquilino no separador **Áreas de trabalho**. Neste separador, pode realizar estas ações:

- Atualizar a lista de áreas de trabalho e os respetivos detalhes.
- Exportar os dados sobre as áreas de trabalho para um ficheiro .csv. 
- Ver detalhes acerca de uma área de trabalho, incluindo o respetivo ID, utilizadores e respetivas funções, dashboards, relatórios e conjuntos de dados.
- Editar a lista de pessoas que têm acesso. Tal significa que pode eliminar a área de trabalho. Pode adicionar-se a si próprio a uma área de trabalho como administrador e, em seguida, abrir e eliminar a área de trabalho.
- Editar os campos Nome e Descrição.
- Atualizar as áreas de trabalho clássicas para a nova experiência de áreas de trabalho

![Lista de áreas de trabalho](media/service-admin-portal/workspaces-list.png)

Os administradores também podem controlar a capacidade dos utilizadores de criar áreas de trabalho na nova experiência e áreas de trabalho clássicas. Veja a secção [Definições da área de trabalho](#workspace-settings) neste artigo para obter mais detalhes.

As colunas da tabela no separador **Áreas de trabalho** correspondem às propriedades devolvidas pela [API Rest do administrador do Power BI](/rest/api/power-bi/admin) das áreas de trabalho. As áreas de trabalho pessoais são do tipo **GrupoPessoal**, as áreas de trabalho clássicas são do tipo **Grupo** e as novas experiências de área de trabalho são do tipo **Área de Trabalho**. Para obter mais informações, veja [Organizar o trabalho nas novas áreas de trabalho](../collaborate-share/service-new-workspaces.md).

No separador **Áreas de trabalho**, vê o *estado* de cada área de trabalho. A tabela abaixo fornece mais detalhes sobre o significado desses estados.

|Estado  |Descrição  |
|---------|---------|
| **Ativo** | Uma área de trabalho normal. Não indica nada sobre a utilização ou os respetivos conteúdos; apenas indica que a própria área de trabalho é "normal". |
| **Isolado** | Uma área de trabalho sem utilizador administrador. |
| **Eliminado** | Uma área de trabalho eliminada. Mantemos, durante 90 dias, metadados suficientes para restaurar a área de trabalho, se desejado. |
| **A remover** | Uma área de trabalho prestes a ser eliminada, mas que ainda não foi. Os utilizadores podem eliminar as suas próprias áreas de trabalho, colocando-as em A remover e, por fim, em Eliminado. |

Os administradores também podem gerir e recuperar áreas de trabalho, através do portal de administração ou dos cmdlets do PowerShell. 

![Lista de áreas de trabalho](media/service-admin-portal/workspaces-list.png)

Os administradores podem atualizar as áreas de trabalho clássicas para a nova experiência de áreas de trabalho. Os administradores podem selecionar uma ou mais áreas de trabalho com o tipo **Grupo** para atualizar. As atualizações são colocadas em fila e executadas de forma assíncrona. Poderá demorar desde alguns minutos a alguns dias a concluir todas as atualizações **Pendentes**, uma vez que a taxa geral de atualizações iniciadas por administradores está limitada, para que o serviço continue a funcionar sem problemas. A coluna **Estado da atualização de área de trabalho** ajuda os administradores a monitorizar o progresso das atualizações iniciadas por administradores. Os administradores podem cancelar as atualizações iniciadas por administradores quanto estas estiverem **Pendentes**. Para atualizar uma área de trabalho de imediato, contacte o Administrador da Área de trabalho e peça-lhe que inicie a atualização através do painel de definições da área de trabalho. [Saiba mais sobre a atualização da área de trabalho antes de dar início à sua atualização da área de trabalho iniciada por administradores.](../collaborate-share/service-upgrade-workspaces.md)

A tabela abaixo fornece mais detalhes sobre o estado da atualização.

|Estado  |Descrição  |
|---------|---------|
| **(Em branco)** | A área de trabalho não está a ser atualizada por um administrador do Power BI. |
| **Pendente** | A área de trabalho está na fila para ser atualizada. A atualização pode ser cancelada. |
| **Em Curso** | A área de trabalho está a ser atualizada ativamente. A atualização não pode ser cancelada. |
| **Concluído** | A área de trabalho foi atualizada nos últimos 30 dias por um administrador do Power BI. Um administrador da área de trabalho pode voltar à opção clássica se quiser fazê-lo durante o período 30 dias após a área de trabalho ter sido atualizada. |


## <a name="custom-branding"></a>Imagem corporativa personalizada

Como administrador, pode personalizar o aspeto do Power BI para toda a sua organização. Atualmente, existem três opções principais:

![Opções de imagem corporativa personalizada](media/service-admin-portal/power-bi-custom-branding.png)

* **Carregar Logótipo**: Para obter melhores resultados, carregue um logótipo que seja guardado como. png, 10 KB ou menor e, pelo menos, 200 x 30 píxeis.

* **Carregar imagem de capa**: Para obter melhores resultados, carregue uma imagem de capa que seja guardada como .jpg ou .png, 1 MB ou menor e, pelo menos, 1920 x 160 píxeis.

* **Selecionar cor do tema**: Pode selecionar o seu tema com base num número hexadecimal, RGB, valor ou na paleta fornecida.


Para obter mais informações, veja [Custom branding for your organization](https://aka.ms/orgBranding) (Imagem corporativa personalizada para a sua organização).

## <a name="protection-metrics"></a>Métricas de proteção

Depois de ativar a proteção das informações para o Power BI, as métricas de proteção de dados são apresentadas no portal de administração. O relatório mostra como as etiquetas de confidencialidade ajudam a proteger o seu conteúdo.

## <a name="manage-featured-content"></a>Gerir conteúdo em destaque

Enquanto administrador do Power BI, pode gerir todos os relatórios, dashboards e aplicações que tenham sido promovidos na secção Em destaque na Base do Power BI na sua organização.

- No portal de Administração, selecione **Conteúdo em destaque**.

Aqui pode ver uma descrição geral de quem destacou o conteúdo, quando o mesmo foi destacado e todos os respetivos metadados relevantes. Se algo parecer suspeito ou caso queira limpar a secção Em destaque, pode eliminar conteúdo promovido conforme necessário.

Veja [Conteúdo em destaque](#featured-content) neste artigo para obter informações sobre a ativação de conteúdo em destaque.

## <a name="next-steps"></a>Próximos passos

[Administrar o Power BI na sua Organização](service-admin-administering-power-bi-in-your-organization.md)  
[Compreender a função de administrador do Power BI](service-admin-role.md)  
[Fazer a auditoria do Power BI na sua organização](service-admin-auditing.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
