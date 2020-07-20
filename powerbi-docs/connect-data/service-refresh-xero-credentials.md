---
title: Como atualizar as suas credenciais do pacote de conteúdos do Xero
description: Se utilizar o pacote de conteúdos do Xero Power BI, pode ter ocorrido um problema na atualização diária do pacote de conteúdos devido a um incidente recente do serviço Power BI.
author: SarinaJoan
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 08/10/2017
ms.author: sarinas
LocalizationGroup: Troubleshooting
ms.openlocfilehash: a1697bfce1db1ca92d50bfb83210d21b2820fdae
ms.sourcegitcommit: e8ed3d120699911b0f2e508dc20bd6a9b5f00580
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/11/2020
ms.locfileid: "86263692"
---
# <a name="how-to-refresh-your-xero-content-pack-credentials-if-refresh-failed"></a>Como atualizar as suas credenciais do pacote de conteúdos Xero se a atualização falhar
Se utilizar o pacote de conteúdos do Xero Power BI, podem ter ocorrido alguns problemas na atualização diária do pacote de conteúdos devido a um incidente recente do serviço Power BI.

Pode ver se o pacote de conteúdos é atualizado com êxito ao verificar o último estado de atualização do conjunto de dados do Xero, conforme mostrado na captura de ecrã abaixo.

![Captura de ecrã a mostrar a caixa de diálogo Xero, com o estado de atualização do seu conjunto de dados Xero.](media/service-refresh-xero-credentials/powerbi-xero-refresh-failed.png)

Se vir que a atualização falhou, conforme mostrado acima, siga estes passos para renovar as credenciais do pacote de conteúdos.

1. Clique em **Mais opções** (...) junto ao conjunto de dados do Xero e clique em **Agendar atualização**. Esta ação abre a página de definições do pacote de conteúdos do Xero.
   
    ![Captura de ecrã a mostrar a caixa de diálogo Xero, com a seleção de Agendar Atualização.](media/service-refresh-xero-credentials/powerbi-xero-schedule-refresh.png)
2. Na página **Definições do Xero**, selecione **Credenciais da origem de dados** > **Editar credenciais**.
   
    ![Captura de ecrã a mostrar a caixa de diálogo Definições Xero com as definições do Xero com Editar credenciais selecionado.](media/service-refresh-xero-credentials/powerbi-xero-settings-page.png)
3. Introduza o nome da organização > **Seguinte**.
   
    ![Captura de ecrã a mostrar a caixa de diálogo Configurar Xero com o nome da Organização.](media/service-refresh-xero-credentials/powerbi-xero-configure.png)
4. Inicie sessão com a sua conta do Xero.
   
    ![Captura de ecrã a mostrar a caixa de diálogo para iniciar sessão no Xero, a demonstrar como iniciar sessão na sua conta Xero.](media/service-refresh-xero-credentials/powerbi-xero-welcome.png)
5. Agora que as suas credenciais estão atualizadas, vamos assegurar que o agendamento da atualização está definido para ser executado diariamente. Verifique ao clicar em **Mais opções** (...) junto ao conjunto de dados do Xero e clique novamente em **Agendar atualização**.
   
    ![Captura de ecrã a mostrar a caixa de diálogo Agendar Atualização, com a frequência de atualizações e o fuso horário.](media/service-refresh-xero-credentials/powerbi-xero-refresh-schedule.png)
6. Também pode optar por atualizar o conjunto de dados de imediato. Clique em **Mais opções** (...) junto ao conjunto de dados do Xero e clique em **Atualizar agora**.
   
    ![Captura de ecrã a mostrar a caixa de diálogo Xero, com a seleção de Atualizar Agora.](media/service-refresh-xero-credentials/powerbi-xero-refresh-now.png)

Se ainda estiver a ter problemas de atualização, não hesite em contactar-nos em [https://support.powerbi.com](https://support.powerbi.com) 

Para obter mais informações sobre o pacote de conteúdos do Xero do Power BI, aceda à [página de ajuda do pacote de conteúdos do Xero](service-connect-to-xero.md).

### <a name="next-steps"></a>Próximos passos
* Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)

