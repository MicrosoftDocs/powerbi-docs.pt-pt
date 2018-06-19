---
title: Intercalar ou anexar origens de dados na cloud e no local
description: Utilize o gateway de dados no local para intercalar ou anexar origens de dados no local e na cloud na mesma consulta.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 06/06/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 3550a3fc0cfc51b61e1d7e51a50c2a36325f2388
ms.sourcegitcommit: 49570ab8f5b5cd5bab4cd388f4281b1372bcb80b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2018
ms.locfileid: "35250655"
---
# <a name="merge-or-append-on-premises-and-cloud-data-sources"></a>Intercalar ou anexar origens de dados na cloud e no local

O gateway de dados no local permite-lhe intercalar ou anexar origens de dados no local e na cloud na mesma consulta. Isto é útil quando quer fazer o mashup de dados de múltiplas origens sem ter de utilizar consultas separadas.

## <a name="prerequisites"></a>Pré-requisitos

- Um [gateway instalado](service-gateway-install.md) num computador local.
- Um ficheiro do Power BI Desktop com consultas que combinem origens de dados no local e na cloud.

1. No canto superior direito do serviço Power BI, selecione o ícone de engrenagem ![Ícone de engrenagem de Definições](media/service-gateway-mashup-on-premises-cloud/icon-gear.png) > **Gerir gateways**.

    ![Gerir gateways](media/service-gateway-mashup-on-premises-cloud/manage-gateways.png)

2. Selecione o gateway que pretende configurar.

3. Em **Definições do Cluster de Gateway**, selecione **Permitir que as origens de dados na cloud do utilizador atualizem através deste cluster de gateway** > **Aplicar**.

    ![Atualizar através deste cluster de gateway](media/service-gateway-mashup-on-premises-cloud/refresh-gateway-cluster.png)

4. Neste cluster de gateway, adicione todas as [origens de dados no local](service-gateway-enterprise-manage-scheduled-refresh.md#add-a-data-source) utilizadas nas suas consultas. Não precisa de adicionar as origens de dados na cloud aqui.

4. Carregue o seu ficheiro do Power BI Desktop para o serviço Power BI com as consultas que combinam origens de dados no local e na cloud.

5. Na página **Definições do conjunto de dados** para o novo conjunto de dados:

    - Para a origem no local, selecione o gateway associado a esta origem de dados.

    - Em **Credenciais da origem de dados**, edite as credenciais de origem de dados na cloud, conforme necessário.

    ![Definições do conjunto de dados](media/service-gateway-mashup-on-premises-cloud/dataset-settings.png)

6. Com as credenciais da cloud definidas, pode atualizar o conjunto de dados através da opção **Atualizar agora** ou agendá-la para ser atualizada periodicamente.


## <a name="next-steps"></a>Próximos passos

Para saber mais sobre a atualização de dados para gateways, veja [Utilizar a origem de dados para a atualização agendada](service-gateway-enterprise-manage-scheduled-refresh.md#using-the-data-source-for-scheduled-refresh).