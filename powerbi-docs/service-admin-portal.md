---
title: "Portal de administração do Power BI"
description: "O portal de administração permite a gestão de inquilinos do Power BI na sua organização. Inclui itens, como métricas de utilização, acesso ao centro de administração do Office 365 e definições."
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
ms.date: 01/02/2018
ms.author: maghan
ms.openlocfilehash: 36f2b591f53e7d9e930048cdedde114348466147
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2018
---
# <a name="power-bi-admin-portal"></a>Portal de administração do Power BI

O portal de administração permite a gestão de inquilinos do Power BI na sua organização. Inclui itens, como métricas de utilização, acesso ao centro de administração do Office 365 e definições.

A gestão de inquilinos do Power BI para a sua empresa é efetuada através do portal de administração do Power BI. O portal de administração está acessível a todos os utilizadores que sejam Administradores Globais no Office 365 ou a quem tenha sido atribuída a função de administrador do serviço Power BI. Para obter mais informações sobre a função de administrador do serviço Power BI, veja [Noções básicas sobre a função de administrador do Power BI](service-admin-role.md).

Todos os utilizadores verão o **Portal de administração** por baixo do ícone de engrenagem. Se não forem um administrador, apenas verão a secção **Definições Premium** e as capacidades para as quais têm direitos de gestão.

## <a name="how-to-get-to-the-admin-portal"></a>Como aceder ao portal de administração

A conta tem de estar marcada como **Administrador Global**, no Office 365 ou no Azure Active Directory, ou ter sido atribuída a função de administrador do serviço Power BI, para obter acesso ao portal de administração do Power BI. Para obter mais informações sobre a função de administrador do serviço Power BI, veja [Noções básicas sobre a função de administrador do Power BI](service-admin-role.md). Para aceder ao portal de administração do Power BI, efetue o seguinte procedimento.

1. Selecione a engrenagem de definições na parte superior direita do serviço Power BI.
2. Selecione **Portal de Administração**.

![](media/service-admin-portal/powerbi-admin-settings.png)

No portal, existem cinco separadores. Estão descritos abaixo.

* [Métricas de utilização](#usage-metrics)
* [Utilizadores](#users)
* [Registos de auditoria](#audit-logs)
* [Definições de inquilino](#tenant-settings)
* [Definições Premium](#premium-settings)
* [Códigos de incorporação](#embed-codes)

![](media/service-admin-portal/powerbi-admin-landing-page.png)

## <a name="usage-metrics"></a>Métricas de utilização
O primeiro separador no portal de administração é **Métricas de utilização**. O relatório de métricas de utilização permite monitorizar a utilização no Power BI relativamente à sua organização. Permite também ver quais os utilizadores e os grupos mais ativos no Power BI para a sua organização.

> [!NOTE]
> Quando aceder ao dashboard pela primeira vez ou depois de voltar após um período longo em que não visualizou o dashboard, provavelmente verá um ecrã de carregamento enquanto carregamos o dashboard.

Após o carregamento do dashboard, verá duas secções de mosaicos. A primeira secção inclui os dados de utilização para utilizadores individuais e a segunda secção tem informações semelhantes para grupos na sua organização.

Segue-se uma análise detalhada do que verá em cada mosaico:

* Contagem distinta de todos os dashboards, relatórios e conjuntos de dados na área de trabalho do utilizador
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-number-tiles.png)

* O dashboard mais consumido pelo número de utilizadores que podem aceder ao mesmo. Por exemplo, se tiver um dashboard partilhado com 3 utilizadores e também o tiver adicionado a um pacote de conteúdos com dois utilizadores diferentes ligados, a contagem será 6 (1 + 3 + 2)
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-top-dashboards.png)

* Os utilizadores de conteúdo mais populares ligados ao mesmo. Isto será qualquer item a que os utilizadores possam aceder através do processo Obter Dados, como pacotes de conteúdos SaaS, pacotes de conteúdos Organizacionais, ficheiros ou bases de dados.
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-top-connections.png)

* Uma vista dos principais utilizadores com base no número de dashboards que têm, tanto os dashboards que criaram como os dashboards partilhados com eles.
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-dashboards.png)

* Uma vista dos principais utilizadores com base no número de relatórios que têm.
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-reports.png)

A segunda secção apresenta o mesmo tipo de informação, mas com base em grupos. Isto permitirá ver quais os grupos mais ativos na sua organização e o tipo de informação que estão a utilizar.

Com esta informação, conseguirá obter dados reais relativamente à forma como as pessoas estão a utilizar o Power BI na sua organização e reconhecer os utilizadores e grupos que são muito ativos na sua organização.

## <a name="users"></a>Utilizadores

O segundo separador no portal de administração é **Gerir Utilizadores**. A gestão de utilizadores, para o Power BI, é efetuada no centro de administração do Office 365, pelo que esta secção permite aceder rapidamente à área para gerir utilizadores, administradores e grupos no Office 365.

![](media/service-admin-portal/powerbi-admin-manage-users.png)

Ao clicar em **Ir para o Centro de Administração do O365**, acede diretamente à página de destino do centro de administração do Office 365 para gerir os utilizadores do seu inquilino.

![](media/service-admin-portal/powerbi-admin-o365-admin-center.png)

## <a name="audit-logs"></a>Registos de auditoria

O terceiro separador no portal de administração é **Registos de auditoria**. Os registos estão localizados no Centro de Conformidade e Segurança do Office 365. Esta secção permite aceder rapidamente a essa área no Office 365. 

Para obter mais informações sobre registos de auditoria, veja [Auditoria do Power BI na sua organização](service-admin-auditing.md)

## <a name="tenant-settings"></a>Definições de inquilino

O quarto separador no portal de administração é **Definições de inquilino**. As definições de inquilino dão-lhe mais controlo sobre as funcionalidades disponibilizadas para a sua organização. Se tiver problemas com dados confidenciais, algumas das nossas funcionalidades podem não ser adequadas para a sua organização ou pode querer apenas uma determinada funcionalidade disponível para um grupo específico. Se for este o caso, pode desativar a definição no inquilino.

![](media/service-admin-portal/powerbi-admin-tenant-settings.png)

> [!NOTE]
> Pode demorar até 10 minutos para a definição ter efeito para todos os utilizadores no inquilino.

As definições podem ter três estados com base nas definições que especificou.

### <a name="disabled-for-the-entire-organization"></a>Desativada para toda a organização

Pode desativar uma funcionalidade para que os utilizadores não a possam utilizar.

![](media/service-admin-portal/powerbi-admin-tenant-settings-disabled.png)

### <a name="enabled-for-the-entire-organization"></a>Ativada para toda a organização

Pode ativar uma funcionalidade para toda a organização, o que permitirá que todos os utilizadores tenham acesso à mesma.

![](media/service-admin-portal/powerbi-admin-tenant-settings-enabled.png)

### <a name="enabled-for-a-subset-of-the-organization"></a>Ativada para um subconjunto da organização

Também pode ativar uma funcionalidade para uma parte da sua organização. Isto pode acontecer de formas diferentes. Pode ativá-la para toda a organização, exceto para um grupo específico de utilizadores.

![](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except.png)

Pode também ativar a funcionalidade apenas para um grupo específico de utilizadores ou desativá-la para um grupo de utilizadores. Isto assegura que determinados utilizadores não tenham acesso à funcionalidade mesmo que estejam no grupo permitido.

![](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except2.png)

## <a name="export-and-sharing-settings"></a>Definições de exportação e partilha

### <a name="share-content-to-external-users"></a>Partilhar conteúdo com utilizadores externos

Os utilizadores na organização podem partilhar dashboards com utilizadores fora da organização.

![](media/service-admin-portal/powerbi-admin-sharing-external.png)

### <a name="publish-to-web"></a>Publicar na Web

Os utilizadores na organização podem publicar os relatórios na Web. [Saiba mais](service-publish-to-web.md)

![](media/service-admin-portal/powerbi-admin-publish-to-web.png)

Os utilizadores verão opções diferentes na IU consoante a definição da funcionalidade Publicar na Web.

|Destaque |Ativada para toda a organização |Desativada para toda a organização |Grupos de segurança específicos   |
|---------|---------|---------|---------|
|**Publicar na Web**, no menu **Ficheiro** do relatório.|Ativada para todos|Não visível para todos|Visível apenas para utilizadores ou grupos autorizados.|
|**Gerir códigos de incorporação**, em **Definições**|Ativada para todos|Ativada para todos|Ativada para todos<br><br>* A opção **Eliminar** está ativada apenas para utilizadores e grupos autorizados.<br>* A opção **Obter códigos** está ativada para todos.|
|**Incorporar códigos** no portal de administração|O estado será um dos seguintes:<br>* Ativo<br>* Não suportado<br>* Bloqueado|O estado apresentado será **Desativado**|O estado será um dos seguintes:<br>* Ativo<br>* Não suportado<br>* Bloqueado<br><br>Se um utilizador não estiver autorizado com base na definição do inquilino, o estado apresentado será **Em violação**.|
|Relatórios publicados existentes|Todos ativados|Todos desativados|Os relatórios continuam a ser compostos para todos.|

### <a name="export-data"></a>Exportar dados

Os utilizadores na organização podem exportar dados de um mosaico ou visualização. [Saiba mais](power-bi-visualization-export-data.md)

![](media/service-admin-portal/powerbi-admin-export-data.png)

> [!NOTE]
> Desativar a opção **Exportar Dados** também impede os utilizadores de usarem a funcionalidade **Analisar no Excel**, bem como a ligação em direto do serviço Power BI.

### <a name="export-reports-as-powerpoint-presentations"></a>Exportar relatórios como apresentações do PowerPoint

Os utilizadores na organização podem exportar relatórios do Power BI como ficheiros do PowerPoint. [Saiba mais](service-publish-to-powerpoint.md)

![](media/service-admin-portal/powerbi-admin-powerpoint.png)

### <a name="print-dashboards-and-reports"></a>Imprimir dashboards e relatórios

Os utilizadores na organização podem imprimir dashboards e relatórios. [Saiba mais](service-print.md)

![](media/service-admin-portal/powerbi-admin-print-dashboard.png)

![](media/service-admin-portal/powerbi-admin-print-report.png)

## <a name="content-pack-settings"></a>Definições do pacote de conteúdos

### <a name="publish-content-packs-to-the-entire-organization"></a>Publicar pacotes de conteúdos para toda a organização

Os utilizadores na organização podem publicar pacotes de conteúdo para toda a organização.

![](media/service-admin-portal/powerbi-admin-publish-entire-org.png)

### <a name="create-template-organizational-content-packs"></a>Criar pacotes de conteúdos organizacionais modelo

Os utilizadores na organização podem criar pacotes de conteúdos modelo que utilizam conjuntos de dados incorporados numa origem de dados no Power BI Desktop.

## <a name="integration-settings"></a>Definições de integração

### <a name="ask-questions-about-data-using-cortana"></a>Fazer perguntas sobre dados através do Cortana
Os utilizadores na organização podem fazer perguntas sobre os respetivos dados através do Cortana.

> [!NOTE]
> Esta definição aplica-se a toda a organização e não pode estar limitada a grupos específicos.

### <a name="use-analyze-in-excel-with-on-premises-datasets"></a>Utilizar a funcionalidade Analisar no Excel com conjuntos de dados no local
Os utilizadores na organização podem utilizar o Excel para ver e interagir com conjuntos de dados no local do Power BI. [Saiba mais](service-analyze-in-excel.md)

> [!NOTE]
> Desativar a opção **Exportar Dados** também impede os utilizadores de usarem a funcionalidade **Analisar no Excel**.

### <a name="user-arcgis-maps-for-power-bi-preview"></a>Utilizar o ArcGIS Maps para Power BI (Pré-visualização)

Os utilizadores na organização podem utilizar a visualização ArcGIS Maps para Power BI (Pré-visualização) fornecida pela Esri. [Saiba mais](power-bi-visualization-arcgis.md)


## <a name="custom-visuals-settings"></a>Definições de elementos visuais personalizados
### <a name="enable-custom-visuals-for-the-entire-organization"></a>Ativar os elementos visuais personalizados para toda a organização
Os utilizadores na organização podem interagir e partilhar elementos visuais personalizados. [Saiba mais](power-bi-custom-visuals.md)

![Definições de elementos visuais personalizados](media/service-admin-portal/powerbi-admin-custom-visuals.png)

> [!NOTE]
> Esta definição aplica-se a toda a organização e não pode estar limitada a grupos específicos.

## <a name="r-visuals-settings"></a>Definições de elementos visuais R

### <a name="interact-with-an-dshare-r-visuals"></a>Interagir com elementos visuais R dshare

Os utilizadores na organização podem interagir e partilhar elementos visuais criados com scripts R. [Saiba mais](service-r-visuals.md)

> [!NOTE]
> Esta definição aplica-se a toda a organização e não pode estar limitada a grupos específicos.

## <a name="audit-settings"></a>Definições de auditoria

### <a name="create-audit-logs-for-internal-activity-auditing-and-compliance"></a>Criar registos de auditoria para auditoria e conformidade da atividade interna

Os utilizadores na organização podem utilizar a auditoria para monitorizar as ações executadas no Power BI por outros utilizadores na organização. [Saiba mais](service-admin-auditing.md)

Esta definição tem de estar ativada para as entradas de registo de auditoria serem registadas.

> [!NOTE]
> Esta definição aplica-se a toda a organização e não pode estar limitada a grupos específicos.

## <a name="dashboard-settings"></a>Definições do dashboard

### <a name="data-classification-for-dashboards"></a>Classificação de dados para dashboards

Os utilizadores na organização podem identificar os dashboards com classificações que indicam os respetivos níveis de segurança. [Saiba mais](service-data-classification.md)

> [!NOTE]
> Esta definição aplica-se a toda a organização e não pode estar limitada a grupos específicos.

## <a name="developer-settings"></a>Definições do programador

### <a name="embed-content-in-apps"></a>Incorporar conteúdo em aplicações

Os utilizadores na organização podem incorporar dashboards e relatórios do Power BI em aplicações Software como Serviço (SaaS). Desativar esta definição impedirá os utilizadores de usarem as APIs REST para incorporar conteúdo do Power BI na respetiva aplicação.

## <a name="premium-settings"></a>Definições Premium

O separador Definições Premium permite gerir qualquer capacidade do Power BI Premium comprada para a sua organização. Todos os utilizadores na sua organização verão o separador Definições Premium, mas apenas verão o conteúdo no mesmo se estiverem atribuídos como **Administrador de capacidade** ou um utilizador com permissões de atribuição. Se um utilizador não tiver nenhuma permissão, verá a mensagem seguinte.

![](media/service-admin-portal/premium-settings-no-access.png "Sem acesso às definições Premium")

Para obter mais informações sobre como gerir as definições Premium, veja [Gerir o Power BI Premium](service-admin-premium-manage.md).

## <a name="embed-codes"></a>Códigos de incorporação

![Códigos de incorporação no portal de administração do Power BI](media/service-admin-portal/embed-codes.png)

Enquanto administrador, pode ver os códigos de incorporação gerados para o seu inquilino. Pode ver o relatório e eliminar o código de incorporação para o revogar.

## <a name="next-steps"></a>Próximos passos

[Compreender a função de administrador do Power BI](service-admin-role.md)  
[Auditoria do Power BI na sua organização](service-admin-auditing.md)  
[Gerir o Power BI Premium](service-admin-premium-manage.md)  
[Administrar o Power BI na sua organização](service-admin-administering-power-bi-in-your-organization.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)