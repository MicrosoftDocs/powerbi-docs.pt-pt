---
title: Portal de administração do Power BI
description: O portal de administração permite a gestão de inquilinos do Power BI na sua organização. Inclui itens, como métricas de utilização, acesso ao centro de administração do Office 365 e definições.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/24/2019
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: d592cca246b7d8bf348a9cdd889b6d8ba0e248c1
ms.sourcegitcommit: ac63b08a4085de35e1968fa90f2f49ea001b50c5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/18/2019
ms.locfileid: "57980387"
---
# <a name="administering-power-bi-in-the-admin-portal"></a>Administrar o Power BI no portal de administração

O portal de administração permite-lhe gerir o *inquilino* do Power BI da sua organização. O portal inclui itens, como métricas de utilização, acesso ao centro de administração do Office 365 e definições.

O portal de administração completo está acessível a todos os utilizadores que sejam Administradores Globais no Office 365 ou a quem tenha sido atribuída a função de administrador do serviço Power BI. Se não estiver numa destas funções, verá apenas as **Definições de capacidade** no portal. Para obter mais informações sobre a função de administrador do serviço Power BI, veja [Noções básicas sobre a função de administrador do Power BI](service-admin-role.md).

## <a name="how-to-get-to-the-admin-portal"></a>Como aceder ao portal de administração

A conta tem de estar marcada como **Administrador Global**, no Office 365 ou no Azure Active Directory, ou ter sido atribuída a função de administrador do serviço Power BI, para obter acesso ao portal de administração do Power BI. Para obter mais informações sobre a função de administrador do serviço Power BI, veja [Noções básicas sobre a função de administrador do Power BI](service-admin-role.md). Para aceder ao portal de administração do Power BI, efetue o seguinte procedimento.

1. Selecione a engrenagem de definições na parte superior direita do serviço Power BI.

1. Selecione **Portal de administração**.

    ![Definições do portal de administração](media/service-admin-portal/powerbi-admin-settings.png)

Existem sete separadores no portal. O resto deste artigo disponibiliza informações sobre cada um destes separadores.

![Navegação no portal de administração](media/service-admin-portal/powerbi-admin-landing-page.png)

* [Métricas de utilização](#usage-metrics)
* [Utilizadores](#users)
* [Registos de auditoria](#audit-logs)
* [Definições de inquilino](#tenant-settings)
* [Definições de capacidade](#capacity-settings)
* [Códigos de incorporação](#embed-codes)
* [Elementos visuais da organização](#organizational-visuals)

## <a name="usage-metrics"></a>Métricas de utilização

As **Métricas de utilização** permitem-lhe monitorizar a utilização do Power BI da sua organização. Permite também ver quais os utilizadores e os grupos mais ativos no Power BI para a sua organização.

> [!NOTE]
> Quando aceder ao dashboard pela primeira vez ou depois de voltar após um período longo em que não visualizou o dashboard, provavelmente verá um ecrã de carregamento enquanto carregamos o dashboard.

Após o carregamento do dashboard, verá duas secções de mosaicos. A primeira secção inclui os dados de utilização dos utilizadores individuais e a segunda secção tem informações semelhantes dos grupos na sua organização.

Veja a seguir uma análise detalhada do que pode ver em cada mosaico:

* Contagem distinta de todos os dashboards, relatórios e conjuntos de dados na área de trabalho do utilizador
  
    ![Contagem distinta de dashboards, relatórios e conjuntos de dados](media/service-admin-portal/powerbi-admin-usage-metrics-number-tiles.png)

* O dashboard mais consumido pelo número de utilizadores que podem aceder ao mesmo. Por exemplo, se tiver um dashboard partilhado com três utilizadores e também o tiver adicionado a um pacote de conteúdos com dois utilizadores diferentes ligados, a contagem será 6 (1 + 3 + 2)
  
    ![Dashboards mais consumidos](media/service-admin-portal/powerbi-admin-usage-metrics-top-dashboards.png)

* Os utilizadores de conteúdo mais populares ligados ao mesmo. Isto será qualquer item a que os utilizadores possam aceder através do processo Obter Dados, como pacotes de conteúdos SaaS, pacotes de conteúdos Organizacionais, ficheiros ou bases de dados.
  
    ![Pacotes mais consumidos](media/service-admin-portal/powerbi-admin-usage-metrics-top-connections.png)

* Uma vista dos principais utilizadores com base no número de dashboards que têm, tanto os dashboards que criaram como os dashboards partilhados com eles.
  
    ![Principais utilizadores – dashboards](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-dashboards.png)

* Uma vista dos principais utilizadores com base no número de relatórios que têm.
  
    ![Principais utilizadores – relatórios](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-reports.png)

A segunda secção apresenta o mesmo tipo de informação, mas com base em grupos. Tal permite-lhe ver quais os grupos mais ativos na sua organização e o tipo de conteúdo que estão a consumir.

Com estas informações, pode obter informações reais relativamente à forma como as pessoas estão a utilizar o Power BI na sua organização e reconhecer os utilizadores e grupos que são muito ativos na sua organização.

## <a name="users"></a>Utilizadores

Os utilizadores, grupos e administradores do Power BI são geridos no centro de administração do Office 365. O separador **Utilizadores** disponibiliza uma ligação para o centro de administração do seu inquilino.

![Ir para Centro de Administração do O365](media/service-admin-portal/powerbi-admin-manage-users.png)

## <a name="audit-logs"></a>Registos de auditoria

Os registos de auditoria do Power BI são geridos no centro de Segurança e Conformidade do Office 365. O separador **Registos de auditoria** proporciona uma ligação para o centro de Segurança e Conformidade do seu inquilino. [Saiba mais](service-admin-auditing.md)

Para utilizar os registos de auditoria, verifique se a definição [**Criar registos de auditoria para auditoria de atividade interna e de conformidade**](#create-audit-logs-for-internal-activity-auditing-and-compliance) está ativada.

## <a name="tenant-settings"></a>Definições de inquilino

O separador **Definições de inquilino** permite um controlo refinado sobre as funcionalidades que são disponibilizadas à sua organização. Se tiver problemas com dados confidenciais, algumas das nossas funcionalidades poderão não ser adequadas para a sua organização ou poderá querer apenas uma determinada funcionalidade disponível para um grupo específico.

A imagem seguinte mostra as duas primeiras secções do separador **Definições de inquilino**.

![Definições de inquilino](media/service-admin-portal/powerbi-admin-tenant-settings.png)

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

## <a name="workspace-settings"></a>Definições de área de trabalho

### <a name="create-workspaces-preview"></a>Criar áreas de trabalho (pré-visualização)

Os utilizadores na organização podem criar áreas de trabalho de aplicações para colaborar em dashboards, relatórios e noutros conteúdos. [Saiba mais](service-create-the-new-workspaces.md)

## <a name="export-and-sharing-settings"></a>Definições de exportação e partilha

### <a name="share-content-to-external-users"></a>Partilhar conteúdo com utilizadores externos

Os utilizadores na organização podem partilhar dashboards com utilizadores fora da organização. [Saiba mais](service-share-dashboards.md#share-a-dashboard-or-report-with-people-outside-your-organization)

![Definição Utilizadores externos](media/service-admin-portal/powerbi-admin-sharing-external-02.png)

A imagem seguinte mostra a mensagem que aparece quando partilha com um utilizador externo.

![Partilhar com um utilizador externo](media/service-admin-portal/powerbi-admin-sharing-external.png)

### <a name="publish-to-web"></a>Publicar na Web

Os utilizadores na organização podem publicar os relatórios na Web. [Saiba mais](service-publish-to-web.md)

A imagem seguinte mostra o menu **Ficheiro** de um relatório quando a definição **Publicar na Web** está ativada.

![Definição Publicar na Web](media/service-admin-portal/powerbi-admin-publish-to-web.png)

Os utilizadores veem opções diferentes na IU consoante a definição **Publicar na Web**.

|Destaque |Ativada para toda a organização |Desativada para toda a organização |Grupos de segurança específicos   |
|---------|---------|---------|---------|
|**Publicar na Web**, no menu **Ficheiro** do relatório.|Ativada para todos|Não visível para todos|Visível apenas para utilizadores ou grupos autorizados.|
|**Gerir códigos de incorporação**, em **Definições**|Ativada para todos|Ativada para todos|Ativada para todos<br><br>* A opção **Eliminar** está ativada apenas para utilizadores e grupos autorizados.<br>* A opção **Obter códigos** está ativada para todos.|
|**Incorporar códigos** no portal de administração|O estado é um dos seguintes:<br>* Ativo<br>* Não suportado<br>* Bloqueado|O estado apresenta **Desativado**|O estado é um dos seguintes:<br>* Ativo<br>* Não suportado<br>* Bloqueado<br><br>Se um utilizador não tiver autorizações com base na definição do inquilino, o estado apresentado será **Em violação**.|
|Relatórios publicados existentes|Todos ativados|Todos desativados|Os relatórios continuam a ser compostos para todos.|

### <a name="export-data"></a>Exportar dados

Os utilizadores na organização podem exportar dados de um mosaico ou visualização. [Saiba mais](visuals/power-bi-visualization-export-data.md)

A imagem seguinte mostra a opção para exportar os dados de um mosaico.

![Exportar dados de um mosaico](media/service-admin-portal/powerbi-admin-export-data.png)

> [!NOTE]
> Desativar a opção **Exportar Dados** também impede os utilizadores de usarem a funcionalidade **Analisar no Excel**, bem como a ligação em direto do serviço Power BI.

### <a name="export-reports-as-powerpoint-presentations-or-pdf-documents"></a>Exportar relatórios como apresentações do PowerPoint ou documentos PDF

Os utilizadores na organização podem exportar relatórios do Power BI como ficheiros do PowerPoint ou documentos PDF. [Saiba mais](consumer/end-user-powerpoint.md)

A seguinte imagem mostra o menu **Ficheiro** de um relatório quando a definição **Exportar relatórios como apresentações do PowerPoint ou documentos PDF** está ativada.

![Exportar relatórios como apresentações do PowerPoint](media/service-admin-portal/powerbi-admin-powerpoint.png)

### <a name="print-dashboards-and-reports"></a>Imprimir dashboards e relatórios

Os utilizadores na organização podem imprimir dashboards e relatórios. [Saiba mais](consumer/end-user-print.md)

A imagem seguinte mostra a opção para imprimir um dashboard.

![Imprimir dashboard](media/service-admin-portal/powerbi-admin-print-dashboard.png)

A imagem seguinte mostra o menu **Ficheiro** de um relatório quando a definição **Imprimir dashboards e relatórios** está ativada.

![Imprimir relatório](media/service-admin-portal/powerbi-admin-print-report.png)

### <a name="allow-external-guest-users-to-edit-and-manage-content-in-the-organization"></a>Permitir aos utilizadores externos convidados editarem e gerirem conteúdo na organização
Os utilizadores convidados do Azure B2B podem editar e gerir o conteúdo na organização. [Saiba mais](service-admin-azure-ad-b2b.md)

A seguinte imagem mostra a opção Permitir aos utilizadores externos convidados editarem e gerirem conteúdo na organização.

![Permitir aos utilizadores externos convidados editarem e gerirem conteúdo na organização](media/service-admin-portal/powerbi-admin-tenant-settings-b2b-guest-edit-manage.png)

## <a name="content-pack-and-app-settings"></a>Definições da aplicação e do pacote de conteúdos

### <a name="publish-content-packs-and-apps-to-the-entire-organization"></a>Publicar pacotes de conteúdo e aplicações em toda a organização

Os utilizadores na organização podem publicar pacotes de conteúdos e aplicações para toda a organização, ao invés de apenas grupos específicos. [Saiba mais](service-organizational-content-pack-manage-update-delete.md)

A imagem seguinte mostra a opção **A minha organização inteira** durante a criação de um pacote de conteúdos.

![Publicar o pacote de conteúdos para a organização](media/service-admin-portal/powerbi-admin-publish-entire-org.png)

### <a name="create-template-apps"></a>Create template apps (Criar aplicações de modelo)

Os utilizadores na organização podem criar aplicações de modelo que utilizam conjuntos de dados incorporados no Power BI Desktop. Saiba mais sobre as [aplicações de modelo](template-content-pack-authoring.md)

### <a name="push-apps-to-end-users"></a>Aplicações push para utilizadores finais

Os utilizadores podem partilhar aplicações diretamente com os utilizadores finais sem necessitar da instalação do AppSource. [Saiba mais](service-create-distribute-apps.md)

## <a name="integration-settings"></a>Definições de integração

### <a name="ask-questions-about-data-using-cortana"></a>Fazer perguntas sobre dados através do Cortana

Os utilizadores na organização podem fazer perguntas sobre os respetivos dados através do Cortana. [Saiba mais](service-cortana-enable.md)

> [!NOTE]
> Esta definição aplica-se a toda a organização e não pode estar limitada a grupos específicos.

### <a name="use-analyze-in-excel-with-on-premises-datasets"></a>Utilizar a funcionalidade Analisar no Excel com conjuntos de dados no local

Os utilizadores na organização podem utilizar o Excel para ver e interagir com conjuntos de dados no local do Power BI. [Saiba mais](service-analyze-in-excel.md)

> [!NOTE]
> Desativar a opção **Exportar Dados** também impede os utilizadores de usarem a funcionalidade **Analisar no Excel**.

### <a name="use-arcgis-maps-for-power-bi"></a>Utilizar o ArcGIS Maps for Power BI

Os utilizadores na organização podem utilizar a visualização dos ArcGIS Maps for Power BI fornecida pela Esri. [Saiba mais](visuals/power-bi-visualization-arcgis.md)

### <a name="use-global-search-for-power-bi-preview"></a>Utilizar a pesquisa global para o Power BI (Pré-visualização)

Os utilizadores na organização podem utilizar as funcionalidades de pesquisa externa que dependem do Azure Search. Por exemplo, os utilizadores podem utilizar a Cortana para obterem informações-chave diretamente dos dashboards e relatórios do Power BI. [Saiba mais](service-cortana-intro.md)

## <a name="custom-visuals-settings"></a>Definições de elementos visuais personalizados

### <a name="add-and-use-custom-visuals"></a>Adicionar e utilizar elementos visuais personalizados

Os utilizadores na organização podem interagir e partilhar elementos visuais personalizados. [Saiba mais](power-bi-custom-visuals.md)

> [!NOTE]
> Esta definição pode ser aplicada a toda a organização ou pode ser limitada a grupos específicos.


O Power BI Desktop (a partir do lançamento de março de 2019) suporta a utilização da **Política de Grupo** para desativar a utilização de elementos visuais personalizados nos computadores implementados numa organização.

<table>
<tr><th>Attribute</th><th>Valor</th>
</tr>
<td>chave</td>
    <td>Software\Policies\Microsoft\Power BI Desktop\</td>
<tr>
<td>valueName</td>
<td>EnableCustomVisuals</td>
</tr>
</table>

Um valor de 1 (decimal) ativa a utilização de elementos visuais personalizados no Power BI (esta é a predefinição).

Um valor de 0 (decimal) desativa a utilização de elementos visuais personalizados no Power BI.

### <a name="allow-only-certified-visuals"></a>Permitir apenas elementos visuais certificados

Os utilizadores na organização que receberam permissões para adicionar e utilizar elementos visuais personalizados, representado pela definição "Adicionar e utilizar elementos visuais personalizados", só poderão utilizar [elementos visuais personalizados certificados](https://go.microsoft.com/fwlink/?linkid=2002010) (os elementos visuais não certificados serão bloqueados e apresentarão uma mensagem de erro quando utilizados). 


O Power BI Desktop (a partir do lançamento de março de 2019) suporta a utilização da **Política de Grupo** para desativar a utilização de elementos visuais personalizados não certificados nos computadores implementados numa organização.

<table>
<tr><th>Attribute</th><th>Valor</th>
</tr>
<td>chave</td>
    <td>Software\Policies\Microsoft\Power BI Desktop\</td>
<tr>
<td>valueName</td>
<td>EnableUncertifiedVisuals</td>
</tr>
</table>

Um valor de 1 (decimal) ativa a utilização de elementos visuais personalizados não certificados no Power BI (esta é a predefinição).

Um valor de 0 (decimal) desativa a utilização de elementos visuais personalizados não certificados no Power BI (esta opção só ativa a utilização de [elementos visuais personalizados certificados](https://go.microsoft.com/fwlink/?linkid=2002010)).

## <a name="r-visuals-settings"></a>Definições de elementos visuais R

### <a name="interact-with-and-share-r-visuals"></a>Interagir e partilhar visuais R

Os utilizadores na organização podem interagir e partilhar elementos visuais criados com scripts R. [Saiba mais](visuals/service-r-visuals.md)

> [!NOTE]
> Esta definição aplica-se a toda a organização e não pode estar limitada a grupos específicos.

## <a name="audit-and-usage-settings"></a>Definições de utilização e auditoria

### <a name="create-audit-logs-for-internal-activity-auditing-and-compliance"></a>Criar registos de auditoria para auditoria de atividade interna e de conformidade

Os utilizadores na organização podem utilizar a auditoria para monitorizar as ações executadas no Power BI por outros utilizadores na organização. [Saiba mais](service-admin-auditing.md)

Esta definição tem de estar ativada para as entradas de registo de auditoria serem registadas. Pode existir um intervalo de 48 horas entre a ativação da auditoria e a capacidade de ver os dados da mesma. Se não vir logo os seus dados, consulte os registos de auditoria mais tarde. Pode existir um intervalo de tempo semelhante entre obter a permissão para ver os registos de auditoria e ter acesso aos mesmos.

> [!NOTE]
> Esta definição aplica-se a toda a organização e não pode estar limitada a grupos específicos.

### <a name="usage-metrics-for-content-creators"></a>Métricas de utilização para criadores de conteúdo

Os utilizadores na organização podem ver as métricas de utilização dos dashboards e os relatórios que criam. [Saiba mais](service-usage-metrics.md)

### <a name="per-user-data-in-usage-metrics-for-content-creators"></a>Dados por utilizador em métricas de utilização para criadores de conteúdo

As métricas de utilização para os criadores de conteúdo irão expor nomes a apresentar e endereços de e-mail de utilizadores que estão a aceder ao conteúdo. [Saiba mais](service-usage-metrics.md)

Por predefinição, os dados por utilizador estão ativados para métricas de utilização e as informações da conta do criador de conteúdo estão incluídas no relatório de métricas. Se não quiser incluir estas informações para alguns ou para todos os utilizadores, desative a funcionalidade para grupos de segurança específicos ou para toda a organização. As informações da conta serão apresentadas no relatório como *Sem nome*.

## <a name="dashboard-settings"></a>Definições do dashboard

### <a name="data-classification-for-dashboards"></a>Classificação de dados para dashboards

Os utilizadores na organização podem identificar os dashboards com classificações que indicam os seus níveis de segurança. [Saiba mais](service-data-classification.md)

> [!NOTE]
> Esta definição aplica-se a toda a organização e não pode estar limitada a grupos específicos.

## <a name="developer-settings"></a>Definições de programador

### <a name="embed-content-in-apps"></a>Incorporar conteúdo em aplicações

Os utilizadores na organização podem incorporar dashboards e relatórios do Power BI em aplicações Software como Serviço (SaaS). Desativar esta definição impede os utilizadores de usarem as APIs REST para incorporar conteúdo do Power BI na respetiva aplicação. [Saiba mais](developer/embedding.md)

## <a name="dataflow-settings-preview"></a>Definições de fluxos de dados (pré-visualização)

### <a name="create-and-use-dataflows-preview"></a>Criar e utilizar fluxos de dados (pré-visualização)

Os utilizadores na organização podem criar e utilizar fluxos de dados. Para obter uma descrição geral dos fluxos de dados, veja [Preparação personalizada de dados no Power BI (Pré-visualização)](service-dataflows-overview.md). Para ativar os fluxos de dados numa capacidade Premium, veja [Configurar cargas de trabalho](service-admin-premium-workloads.md).

> [!NOTE]
> Esta definição aplica-se a toda a organização e não pode estar limitada a grupos específicos.

## <a name="template-apps-settings-preview"></a>Definições de aplicações de modelo (pré-visualização)

Existem duas definições que controlam aplicações de modelo. 

![Definições de aplicações de modelo no portal de administração do Power BI](media/service-admin-portal/power-bi-admin-portal-template-apps.png)

A primeira definição, **Criar aplicações de modelo**, controla as pessoas na sua organização que podem criar aplicações de modelo. Em seguida, os criadores de aplicações de modelo podem distribuí-las para os clientes fora da sua organização através do AppSource ou de outro método de distribuição.

![Portal de administração do Power BI. Definição Criar aplicações de modelo](media/service-admin-portal/power-bi-admin-portal-template-app-settings.png)

A segunda definição, **Instalar aplicações de modelo**, permite-lhe controlar as pessoas na sua organização que podem transferir e instalar aplicações de modelo a partir do AppSource ou de outra origem

## <a name="capacity-settings"></a>Definições de capacidade

### <a name="power-bi-premium"></a>Power BI Premium

O separador **Power BI Premium** permite-lhe gerir todas as capacidades do Power BI Premium (SKU EM ou P) compradas para a sua organização. Todos os utilizadores na organização podem ver o separador **Power BI Premium**, mas apenas verão os conteúdos no mesmo se estiverem atribuídos como *Administrador de capacidade* ou como um utilizador com permissões de atribuição. Se um utilizador não tiver nenhuma permissão, será apresentada a mensagem seguinte.

![Sem acesso às definições Premium](media/service-admin-portal/premium-settings-no-access.png)

### <a name="power-bi-embedded"></a>Power BI Embedded

O separador **Power BI Embedded** permite-lhe ver as capacidades do Power BI Embedded (SKU A) que comprou para o seu cliente. Uma vez que apenas pode comprar SKUs A no Azure, vai [gerir as capacidades incorporadas no Azure](developer/azure-pbie-create-capacity.md) no **Portal do Azure**.

Para obter mais informações sobre como gerir as definições do Power BI Embedded (SKU A), veja [O que é o Power BI Embedded?](developer/azure-pbie-what-is-power-bi-embedded.md)

## <a name="embed-codes"></a>Códigos de incorporação

Enquanto administrador, pode ver os códigos de incorporação gerados para o seu inquilino. Também pode revogar ou eliminar códigos. [Saiba mais](service-publish-to-web.md)

![Códigos de incorporação no portal de administração do Power BI](media/service-admin-portal/embed-codes.png)

## <a name="organizational-visuals"></a>Elementos visuais da organização

O separador **Elementos visuais da organização** permite-lhe implementar e gerir os elementos visuais personalizados na sua organização. Com os elementos visuais organizacionais, pode facilmente implementar elementos visuais proprietários na sua organização, os quais os autores dos relatórios podem posteriormente detetar e importar para os seus relatórios do Power BI Desktop. [Saiba mais](power-bi-custom-visuals-organization.md)

> [!WARNING]
> Um elemento visual personalizado pode conter código com riscos de privacidade ou de segurança. Garanta que confia no autor e na origem do elemento visual personalizado antes de implementar no repositório da organização.

A página seguinte mostra todos os elementos visuais personalizados que estão atualmente implementados no repositório da organização.

![Elemento visual de administração da organização](media/service-admin-portal/power-bi-custom-visuals-organizational-admin-01.png)

### <a name="add-a-new-custom-visual"></a>Adicionar um novo elemento visual personalizado

Para adicionar um novo elemento visual personalizado à lista, siga estes passos. 

1. No painel direito, selecione **Adicionar um elemento visual personalizado**.

    ![Formulário dos elementos visuais personalizados](media/service-admin-portal/power-bi-custom-visuals-organizational-admin-02.png)

1. Preencha o formulário **Adicionar elemento visual personalizado**:

    * **Escolher um ficheiro .pbiviz** (obrigatório): selecione um ficheiro de elemento visual personalizado para carregar. Apenas são suportados os elementos visuais personalizados com a versão da API (leia aqui o que significa).

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

Para obter mais informações, visite [Perguntas frequentes sobre os elementos visuais personalizados organizacionais](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-faq#organizational-custom-visuals)

## <a name="dataflow-storage-preview"></a>Armazenamento do fluxo de dados (pré-visualização)

Por predefinição, os dados utilizados com o Power BI são armazenados no armazenamento interno fornecido pelo Power BI. Com a integração dos fluxos de dados e do Azure Data Lake Storage Gen2 (ADLS Gen2), pode armazenar os seus fluxos de dados na conta do Azure Data Lake Storage Gen2 da sua organização. Para obter mais informações, veja [Fluxos de dados e integração do Azure Data Lake (Pré-visualização)](service-dataflows-azure-data-lake-integration.md).

## <a name="workspaces-preview"></a>Áreas de trabalho (pré-visualização)

Enquanto administrador, pode ver as áreas de trabalho existentes no seu inquilino. Pode ordenar e filtrar a lista de áreas de trabalho e ver os detalhes de cada área de trabalho. Tenha em atenção que as colunas da tabela correspondem às propriedades devolvidas pela [API Rest do administrador do Power BI](/rest/api/power-bi/admin) para áreas de trabalho. As áreas de trabalho pessoais são do tipo **PersonalGroup**, as áreas de trabalho de legado são do tipo **Group** e as áreas de trabalho modernas são do tipo **Workspace**. Para obter mais informações, veja [Criar as novas áreas de trabalho (pré-visualização) no Power BI](service-create-the-new-workspaces.md).

![Lista de áreas de trabalho](media/service-admin-portal/workspaces-list.png)

## <a name="next-steps"></a>Próximos passos

[Administrar o Power BI na sua Organização](service-admin-administering-power-bi-in-your-organization.md)  [Compreender a função de administrador do Power BI](service-admin-role.md)  
[Fazer a auditoria do Power BI na sua organização](service-admin-auditing.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
