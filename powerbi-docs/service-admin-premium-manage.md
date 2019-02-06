---
title: Gerir as capacidades no Power BI Premium e no Power BI Embedded
description: Saiba como pode gerir o Power BI Premium e permitir a toda a sua organização o acesso a conteúdos.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/20/2018
LocalizationGroup: Premium
ms.openlocfilehash: 7b7940daa977c05080e5415ae5337a718ada4323
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762611"
---
# <a name="manage-capacities-within-power-bi-premium-and-power-bi-embedded"></a>Gerir as capacidades no Power BI Premium e no Power BI Embedded

Saiba como pode gerir as capacidades do Power BI Premium e do Power BI Embedded que disponibilizam recursos dedicados para os seus conteúdos.

![Ecrã de definições de capacidade do Power BI](media/service-admin-premium-manage/premium-capacity-management.png)

## <a name="what-is-capacity"></a>O que é a capacidade?

A *capacidade* é a parte principal das ofertas do Power BI Premium e do Power BI Embedded. É o conjunto de recursos reservados para utilização exclusiva pela sua organização. Ter capacidade dedicada permite-lhe publicar dashboards, relatórios e conjuntos de dados para os utilizadores em toda a organização sem ter de comprar licenças individuais para os mesmos. Esta ação proporciona também um desempenho fiável e consistente dos conteúdos alojados na capacidade. Para obter mais informações, consulte [O que é o Power BI Premium?](service-premium.md).

### <a name="capacity-admins"></a>Administradores de capacidade

Quando lhe é atribuída a função de *administrador de capacidade*, tem controlo total sobre a capacidade e as respetivas funcionalidades administrativas. A partir do portal de administração do Power BI, pode adicionar mais administrações de capacidade ou conceder aos utilizadores permissões de atribuição de capacidade. Pode atribuir áreas de trabalho em massa a uma capacidade e visualizar a métrica de utilização uma capacidade.

> [!NOTE]
> Para a capacidade do Power BI Embedded, os administradores de capacidade são definidos no portal do Microsoft Azure.

Cada capacidade tem os seus próprios administradores. Atribuir um administrador de capacidade a uma capacidade não lhe concede acesso a todas as capacidades da sua organização. Por predefinição, os administradores de capacidade não têm acesso a todas as áreas de administração do Power BI, como as métricas de utilização, os registos de auditoria ou as definições de inquilino. Os administradores de capacidade também não dispõem de permissões para configurar novas capacidades ou alterar o SKU das capacidades existentes. Apenas os Administradores Globais do Office 365 ou os administradores do serviço Power BI têm acesso a essas opções.

Todos os Administradores Globais do Office 365 e os administradores do serviço Power BI são automaticamente administradores de capacidade das capacidades do Power BI Premium e do Power BI Embedded.

## <a name="purchase-capacity"></a>Capacidade de compra

Para tirar partido da capacidade dedicada, tem de comprar o Power BI Premium no Centro de administração do Office 365 ou de criar um recurso do Power BI Embedded no portal do Microsoft Azure. Para obter mais informações, veja os seguintes artigos:

* **Power BI Premium:** [Como comprar o Power BI Premium](service-admin-premium-purchase.md)

* **Power BI Embedded:** [Criar capacidade do Power BI Embedded no portal do Azure](https://docs.microsoft.com/azure/power-bi-embedded/create-capacity)

Ao comprar SKUs do Power BI Premium ou do Power BI Embedded, o seu inquilino recebe o número correspondente de núcleos virtuais para utilização em capacidades de execução. Por exemplo, a compra de uma Power BI Premium P3 SKU fornece ao inquilino 32 núcleos virtuais. Para obter mais informações sobre SKUs, veja [Nós de capacidade Premium](service-premium.md#premium-capacity-nodes).

## <a name="what-premium-looks-like-for-users"></a>O que o Premium parece para os utilizadores

Na maioria das vezes, os utilizadores não precisam de saber que estão numa capacidade Premium. Os respetivos dashboards e relatórios são suficientes. Como uma sugestão visual, existe um ícone de losango junto às áreas de trabalho que estejam numa capacidade Premium.

![É apresentado um diamante, que indica que a área de trabalho é apoiada pela capacidade Premium](media/service-admin-premium-manage/premium-workspace.png)

## <a name="configure-workloads"></a>Configurar cargas de trabalho

Por predefinição, as capacidades do Power BI Premium e do Power BI Embedded suportam apenas a carga de trabalho associada à execução de consultas do Power BI na cloud. Agora, oferecemos suporte de pré-visualização para duas cargas de trabalho adicionais: **Relatórios paginados** e **Fluxos de dados**. Para obter mais informações, veja [Cargas de trabalho na capacidade Premium](service-premium.md#workloads-in-premium-capacity).

Para permitir cargas de trabalho no portal de administração do Power BI, siga estes passos.

1. Em **Definições de capacidade**, selecione uma capacidade.

1. Em **MAIS OPÇÕES**, expanda **Cargas de trabalho**.

1. Ative uma ou mais cargas de trabalho e defina um valor para **Memória Máx**.

    ![Configurar cargas de trabalho no portal de administração](media/service-admin-premium-manage/admin-portal-workloads.png)

1. Selecione **Aplicar**.

## <a name="monitor-capacity-usage"></a>Monitorizar a utilização de capacidade

O Power BI fornece uma aplicação para monitorizar a utilização das capacidades. Para obter mais informações, veja [Monitorizar as capacidades do Power BI Premium na sua organização](service-admin-premium-monitor-capacity.md).

## <a name="manage-capacity"></a>Gerir capacidade

Depois de comprar nós de capacidade no Office 365, tem de configurar a capacidade no portal de administração do Power BI. Pode gerir as capacidades do Power BI Premium na secção **Definições de capacidade** do portal.

![Definições de capacidade no portal de administração](media/service-admin-premium-manage/admin-portal-premium.png)

Selecione o nome de uma capacidade para gerir a mesma. Isto permite-lhe aceder ao ecrã de gestão de capacidade.

![Selecione o nome da capacidade para aceder ao ecrã de atribuição de capacidade](media/service-admin-premium-manage/capacity-assignment.png)

Se não tiverem sido atribuídas áreas de trabalho à capacidade, verá uma mensagem sobre como [atribuir uma área de trabalho à capacidade](#assign-a-workspace-to-a-capacity).

### <a name="setting-up-a-new-capacity-power-bi-premium"></a>Configurar uma nova capacidade (Power BI Premium)

O portal de administração mostra o número de *núcleos virtuais* que utilizou e que ainda tem disponíveis. O número total de núcleos virtuais baseia-se nos SKUs Premium que comprou. Por exemplo, a compra de um SKU P3 e de um SKU P2 resultará em 48 núcleos disponíveis – 32 do P3 e 16 do P2.

![Núcleos virtuais utilizados e disponíveis para o Power BI Premium](media/service-admin-premium-manage/admin-portal-v-cores.png)

Se tiver núcleos virtuais disponíveis, configure a sua nova capacidade ao seguir estes passos.

1. Selecione **Configurar nova capacidade**.

1. Atribua um nome à sua capacidade.

1. Defina a que administrador pretende atribuir esta capacidade.

1. Selecione o tamanho da capacidade. As opções disponíveis dependem do número de núcleos virtuais disponíveis. Não pode selecionar uma opção que seja superior à que está disponível.

    ![Tamanhos de capacidade de Premium disponíveis](media/service-admin-premium-manage/premium-capacity-size.png)

1. Selecione **Configurar**.

    ![Configurar uma nova capacidade](media/service-admin-premium-manage/set-up-capacity.png)

Os administradores de capacidade, bem como os administradores do Power BI e os Administradores Globais do Office 365, irão ver a capacidade listada no portal de administração.

### <a name="capacity-settings"></a>Definições de capacidade

1. No ecrã de gestão de capacidade do Power BI Premium, em **Ações**, selecione o **ícone de engrenagem** para rever e atualizar definições. 

    ![Ações de capacidade na área de gestão de capacidade](media/service-admin-premium-manage/capacity-actions.png)

1. Pode ver quem são os administradores de serviço, o SKU/tamanho da capacidade e a região onde esta se encontra.

    ![Definições de capacidade](media/service-admin-premium-manage/capacity-settings.png)

1. Também pode eliminar ou mudar o nome de uma capacidade.

    ![Eliminar e aplicar botões a definições de capacidade no Power BI Premium](media/service-admin-premium-manage/capacity-settings-delete.png)

> [!NOTE]
> As definições de capacidade do Power BI Embedded são geridas no portal do Microsoft Azure.

### <a name="change-capacity-size"></a>Alterar o tamanho da capacidade

Os administradores do Power BI e os Administradores Globais do Office 365 podem alterar a capacidade do Power BI Premium. Os administradores de capacidade que não sejam administradores do Power BI ou Administradores Globais do Office 365 não têm esta opção.

1. Selecione **Alterar o tamanho da capacidade**.

    ![Alterar o tamanho de capacidade do Power BI Premium](media/service-admin-premium-manage/change-capacity-size.png)

1. No ecrã **Alterar o tamanho da capacidade**, aumente ou diminua o tamanho da capacidade conforme adequado.

    ![Alterar o menu pendente do tamanho da capacidade do Power BI Premium](media/service-admin-premium-manage/change-capacity-size2.png)

    Os administradores são livres de criar, redimensionar e eliminar nós, desde que tenham o número previsto de núcleos virtuais.

    Os SKUs P não podem ser mudados para uma versão anterior, como os SKUs EM. Pode pairar o rato sobre qualquer opção desativada para ver uma explicação.

### <a name="manage-user-permissions"></a>Gerir permissões de utilizador

Pode atribuir administradores de capacidade adicionais e utilizadores com permissões de *atribuição de capacidade*. Se forem administradores dessa área de trabalho, os utilizadores com permissões de atribuição podem atribuir uma área de trabalho de aplicação a uma capacidade. Podem também atribuir a respetiva *A minha área de trabalho* à capacidade. Os utilizadores com permissões de atribuição não têm acesso ao portal de administração.

> [!NOTE]
> Para a capacidade do Power BI Embedded, os administradores de capacidade são definidos no portal do Microsoft Azure.

Em **Permissões de utilizador**, expanda a secção **Utilizadores com permissões de atribuição** e, em seguida, adicione utilizadores ou grupos conforme adequado.

![Permissões de utilizador da capacidade](media/service-admin-premium-manage/capacity-user-permissions2.png)

## <a name="assign-a-workspace-to-a-capacity"></a>Atribuir uma área de trabalho a uma capacidade

Existem duas formas de atribuir uma área de trabalho a uma capacidade: no portal de administração e a partir de uma área de trabalho de aplicação.

### <a name="assign-from-the-admin-portal"></a>Atribuir a partir do portal de administração

Os administradores de capacidade, em conjunto com os administradores do Power BI e os Administradores Globais do Office 365, podem atribuir áreas de trabalho em massa na secção de gestão de capacidade premium do portal de administração. Ao gerir uma capacidade, verá a secção **Áreas de trabalho**, que lhe permite atribuir áreas de trabalho.

![Área de atribuição de área de trabalho de gestão de capacidade](media/service-admin-premium-manage/capacity-manage-workspaces.png)

1. Selecione **Atribuir áreas de trabalho**. Esta opção esta disponível em múltiplos locais.

1. Selecione uma opção em **Aplicar a**.

    ![Atribuir áreas de trabalho](media/service-admin-premium-manage/assign-workspaces.png)

   | Seleção | Descrição |
   | --- | --- |
   | **Áreas de trabalho por utilizadores** | Quando atribui áreas de trabalho por utilizador ou grupo, todas as áreas de trabalho pertencentes a esses utilizadores são atribuídas à capacidade de Premium, incluindo a área de trabalho pessoal do utilizador. Os utilizadores referidos obtêm automaticamente permissões de atribuição de áreas de trabalho.<br>Isto inclui áreas de trabalho já atribuídas a uma capacidade diferente. |
   | **Áreas de trabalho específicas** | Introduza o nome de uma área de trabalho específica a atribuir à capacidade selecionada. |
   | **Todas as áreas de trabalho da empresa** | A atribuição das áreas de trabalho de toda a organização à capacidade Premium atribui todas as áreas de trabalho de aplicação e As Minhas Áreas de Trabalho, na sua organização, a esta capacidade Premium. Além disso, todos os utilizadores atuais e futuros terão permissão para atribuir de novo áreas de trabalho individuais a esta capacidade. |
   | | |

1. Selecione **Aplicar**.

### <a name="assign-from-app-workspace-settings"></a>Atribuir a partir das definições da área de trabalho de aplicação

Também pode atribuir uma área de trabalho de aplicação a uma capacidade Premium a partir das definições dessa área de trabalho. Para mover uma área de trabalho para uma capacidade, tem de ter permissões de administração para essa área de trabalho, bem como permissões de atribuição de capacidade para essa capacidade. Tenha em atenção que os administradores de área de trabalho podem sempre remover uma área de trabalho da capacidade Premium.

1. Edite uma área de trabalho de aplicação ao selecionar as reticências **(. . .)** e, em seguida, **Editar área de trabalho**.

    ![Editar a área de trabalho a partir do menu de contexto de reticências](media/service-admin-premium-manage/edit-app-workspace.png)

1. Em **Editar área de trabalho**, expanda a secção **Avançado**.

1. Selecione a capacidade à qual pretende atribuir esta área de trabalho de aplicação.

    ![Menu pendente de seleção de capacidade](media/service-admin-premium-manage/app-workspace-advanced.png)

1. Selecione **Guardar**.

Depois de guardar, a área de trabalho e todos os respetivos conteúdos são movidos para a capacidade Premium sem qualquer interrupção da experiência para os utilizadores finais.

## <a name="power-bi-report-server-product-key"></a>Chave de produto do Power BI Report Server

No separador **Definições de capacidade** do portal do administração do Power BI, terá acesso à sua chave de produto do Power BI Report Server. Esta opção estará apenas disponível para administradores globais ou utilizadores com a função de administrador de serviço Power BI atribuída e se tiver adquirido uma SKI Power BI Premium.

![Chave do Power BI Report Server nas definições de capacidade](media/service-admin-premium-manage/pbirs-product-key.png)

Ao selecionar **Chave do Power BI Report Server**, será apresentada uma caixa de diálogo com a sua chave de produto. Pode copiá-la e utilizá-la na instalação.

![Chave de produto do Power BI Report Server](media/service-admin-premium-manage/pbirs-product-key-dialog.png)

Para obter mais informações, consulte [Instalar o Power BI Report Server](report-server/install-report-server.md).

## <a name="next-steps"></a>Próximos passos

Partilhe aplicações publicadas com utilizadores. Para obter mais informações, veja [Create and distribute an app in Power BI](service-create-distribute-apps.md) (Criar e distribuir uma aplicação no Power BI).

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
