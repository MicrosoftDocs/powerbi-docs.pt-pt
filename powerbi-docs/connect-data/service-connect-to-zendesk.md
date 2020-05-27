---
title: Ligue-se ao Zendesk com Power BI
description: Zendesk para o Power BI
author: paulinbar
ms.reviewer: sarinas
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/04/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 17d65296246100180f722dfccacb31ee9ebeade7
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83327168"
---
# <a name="connect-to-zendesk-with-power-bi"></a>Ligue-se ao Zendesk com Power BI

Este artigo vai orientá-lo durante a extração de dados da conta do Zendesk através de uma aplicação de modelo do Power BI. A aplicação Zendesk oferece um dashboard e um conjunto de relatórios do Power BI que proporcionam informações sobre os volumes de pedidos e o desempenho do agente. Os dados são atualizados automaticamente uma vez por dia. 

Após ter instalado a aplicação de modelo, poderá personalizar o dashboard e criar relatórios para realçar informações importantes. Em seguida, pode distribuir a área de trabalho como uma aplicação pelos colegas na sua organização.

Ligue-se à [aplicação de modelo Zendesk](https://app.powerbi.com/getdata/services/zendesk) ou leia mais sobre a [Integração do Zendesk](https://powerbi.microsoft.com/integrations/zendesk) com o Power BI.

Após ter instalado a aplicação de modelo, pode alterar o dashboard e o relatório. Em seguida, pode distribuir a área de trabalho como uma aplicação pelos colegas na sua organização.

>[!NOTE]
>Precisa de uma Conta de administrador do Zendesk para se ligar. Mais detalhes sobre os [requisitos](#system-requirements) abaixo.

## <a name="how-to-connect"></a>Como se ligar

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. Selecione **Zendesk** \> **Obter agora**.
4. Em **Instalar esta aplicação do Power BI?** , selecione **Instalar**.
4. No painel **Aplicações**, selecione o mosaico **Zendesk**.

    ![Mosaico de aplicação Zendesk do Power BI](media/service-connect-to-zendesk/power-bi-zendesk-tile.png)

6. Em **Comece já com a sua nova aplicação** , selecione **Ligar**.

    ![Comece já com a sua nova aplicação](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. Forneça o URL associado à sua conta. O URL tem o formato **https://company.zendesk.com** . Veja detalhes sobre [como encontrar estes parâmetros](#finding-parameters) abaixo.
   
   ![Ligar ao Zendesk](media/service-connect-to-zendesk/pbi_zendeskconnect.png)

5. Quando solicitado, insira as suas credenciais do Zendesk.  Selecione **oAuth 2** como o Mecanismo de Autenticação e clique em **Entrar**. Siga o fluxo de autenticação do Zendesk. (Se já tiver iniciado sessão no Zendesk no browser, poderão não lhe ser pedidas as credenciais).
   
   > [!NOTE]
   > Esta aplicação de modelo requer a ligação com uma Conta de administrador do Zendesk. 
   > 
   
   ![Iniciar sessão com oAuth2](media/service-connect-to-zendesk/pbi_zendesksignin.png)
6. Clique em **Permitir** para permitir que o Power BI aceda aos seus dados do Zendesk.
   
   ![Clicar em Permitir](media/service-connect-to-zendesk/zendesk2.jpg)
7. Clique em **Conectar** para iniciar o processo de importação. 
8. Depois de o Power BI importar os dados, verá a lista de conteúdos da aplicação Zendesk: um novo dashboard, relatório e conjunto de dados.
9. Selecione o dashboard para iniciar o processo de exploração.

    ![Dashboard Zendesk](media/service-connect-to-zendesk/power-bi-zendesk-dashboard.png)
   
## <a name="modify-and-distribute-your-app"></a>Modificar e distribuir a sua aplicação

Acabou de instalar a aplicação de modelo Zendesk, o que significa que também criou uma área de trabalho Zendesk. Na área de trabalho, pode alterar o relatório e o dashboard e, em seguida, distribuí-la como uma *aplicação* pelos colegas na sua organização. 

1. Para ver todos os conteúdos da nova área de trabalho Zendesk, no painel de navegação, selecione **Áreas de trabalho** > **Zendesk**. 

    ![Área de trabalho Zendesk no painel de navegação](media/service-connect-to-zendesk/power-bi-zendesk-workspace-left-nav.png)

    Esta vista é a lista de conteúdos da área de trabalho. No canto superior direito, verá a opção **Atualizar aplicação**. Quanto estiver a postos para distribuir a sua aplicação pelos seus colegas, deve começar por aí. 

    ![Lista de conteúdos do Zendesk](media/service-connect-to-zendesk/power-bi-zendesk-content-list.png)

2. Selecione **Relatórios** e **Conjuntos de dados** para ver os restantes elementos na área de trabalho.

    Leia mais sobre como [distribuir aplicações](../collaborate-share/service-create-distribute-apps.md) pelos seus colegas.

## <a name="system-requirements"></a>Requisitos de sistema
É necessária uma Conta de administrador do Zendesk para aceder à aplicação de modelo Zendesk. Se for um agente ou um utilizador final e estiver interessado em ver os dados do Zendesk, adicione uma sugestão e examine o conector Zendesk no [Power BI Desktop](desktop-connect-to-data.md).

## <a name="finding-parameters"></a>Parâmetros de localização
O URL do Zendesk vai ser igual ao URL que utiliza para se ligar à sua conta do Zendesk. Se não se lembrar do URL do Zendesk, utilize a [ajuda de início de sessão](https://www.zendesk.com/login/) do Zendesk.

## <a name="troubleshooting"></a>Resolução de problemas
Se estiver com problemas de ligação, verifique o URL do Zendesk e confirme que está a utilizar uma conta de administrador do Zendesk.

## <a name="next-steps"></a>Próximos passos

* [Create the new workspaces in Power BI](../collaborate-share/service-create-the-new-workspaces.md) (Criar as novas áreas de trabalho no Power BI)
* [Instalar e utilizar aplicações no Power BI](../consumer/end-user-apps.md)
* [Ligar a aplicações do Power BI para serviços externos](service-connect-to-services.md)
* Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)