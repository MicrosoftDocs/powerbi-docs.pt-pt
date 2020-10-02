---
title: Configurar aplicações móveis do Power BI com o Microsoft Intune
description: Como configurar as aplicações do Power BI Mobile com o Microsoft Intune. Isto inclui como adicionar e implementar a aplicação. E como criar a política de aplicação móvel para controlo de segurança.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 09/25/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 214ef5072808decc4c153a28cf231e070c20508d
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/29/2020
ms.locfileid: "91524725"
---
# <a name="configure-mobile-apps-with-microsoft-intune"></a>Configurar aplicações móveis do Power BI com o Microsoft Intune

O Microsoft Intune permite às organizações gerir dispositivos e aplicações. As aplicações móveis do Power BI para iOS e Android podem ser integradas com o Intune. Esta integração permite-lhe gerir a aplicação nos seus dispositivos e controlar a segurança. Através de políticas de configuração, pode controlar itens como pedir um PIN de acesso, como os dados são processados pela aplicação e até mesmo encriptar dados de aplicação quando esta não estiver a ser utilizada.

A aplicação móvel Microsoft Power BI permite-lhe obter acesso a informações empresariais importantes. Pode ver e interagir com dashboards e relatórios de todos os dispositivos geridos e dados empresariais de aplicações da sua organização. Para obter mais informações sobre as aplicações do Intune, veja [Aplicações protegidas do Microsoft Intune](/intune/apps/apps-supported-intune-apps).

## <a name="general-mobile-device-management-configuration"></a>Configuração geral da gestão de dispositivos móveis

Este artigo pressupõe que o Intune está configurado corretamente e tem dispositivos registados no Intune. Este artigo não serve como guia de configuração completo para o Microsoft Intune. Para obter mais informações sobre o Intune, veja [O que é o Intune?](/intune/introduction-intune/)

O Microsoft Intune pode coexistir com a Gestão de Dispositivos Móveis (MDM) no Microsoft 365. Se estiver a utilizar o MDM, o dispositivo será apresentado como inscrito no mesmo, mas estará disponível para gestão no Intune.

Antes de os utilizadores finais poderem utilizar a aplicação Power BI nos respetivos dispositivos, um administrador do Intune tem de adicionar a aplicação ao Intune e atribuí-la a utilizadores finais.

> [!NOTE]
> Depois de configurar o Intune, a atualização de dados em segundo plano é desativada para a aplicação móvel do Power BI no dispositivo iOS ou Android. O Power BI atualiza os dados do serviço Power BI na Web quando entra na aplicação.

## <a name="step-1-add-the-power-bi-app-to-intune"></a>Passo 1: adicionar a aplicação Power BI ao Intune

Para adicionar a aplicação Power BI ao Intune, siga os passos indicados nos seguintes tópicos:
- [Adicionar aplicações da loja iOS ao Microsoft Intune](/intune/apps/store-apps-ios)
- [Adicionar aplicações da loja Android ao Microsoft Intune](/intune/apps/store-apps-android)

## <a name="step-2-assign-the-app-to-your-end-users"></a>Passo 2: atribuir a aplicação aos utilizadores finais

Depois de adicionar a aplicação Power BI ao Microsoft Intune, pode atribuir a aplicação a utilizadores e dispositivos. É importante denotar que pode atribuir uma aplicação a um dispositivo, quer o mesmo seja ou não gerido pelo Intune.

Para atribuir a aplicação Power BI a utilizadores e dispositivos, siga os passos indicados em [Atribuir aplicações a grupos com o Microsoft Intune](/intune/apps/apps-deploy).

## <a name="step-3-create-and-assign-app-protection-policies"></a>Passo 3: criar e atribuir políticas de proteção de aplicações

As políticas de proteção de aplicações (APP) são regras que garantem a segurança e o armazenamento de dados organizacionais numa aplicação gerida. Uma política pode ser uma regra que é aplicada quando o utilizador tenta aceder ou mover dados "empresariais" ou um conjunto de ações que são proibidas ou monitorizadas quando um utilizador utiliza a aplicação. Uma aplicação gerida é uma aplicação que tem políticas de proteção de aplicações aplicadas à mesma e pode ser gerida pelo Intune.

As políticas de proteção de aplicações de Gestão de Aplicações Móveis (MAM) permitem-lhe gerir e proteger os dados da sua organização numa aplicação. Com a MAM sem inscrição (MAM-WE), pode gerir uma aplicação relacionada com o trabalho ou com a escola que contenha dados confidenciais na maioria dos dispositivos, incluindo os dispositivos pessoais, em cenários BYOD (Bring Your Own Device). Para obter mais informações, veja [Descrição geral das políticas de proteção de aplicações](/intune/apps/app-protection-policy).

Para criar e atribuir uma política de proteção de aplicações à aplicação Power BI, siga os passos indicados em [Como criar e atribuir políticas de proteção de aplicações](/intune/apps/app-protection-policies).

## <a name="step-4-use-the-application-on-a-device"></a>Step 4: utilizar a aplicação num dispositivo

As aplicações geridas são as aplicações que o suporte da empresa pode configurar para ajudar a proteger os dados da empresa a que pode aceder nessa aplicação. Ao aceder a dados empresariais numa aplicação gerida num dispositivo, poderá reparar que a aplicação funciona de forma ligeiramente diferente do esperado. Por exemplo, poderá não conseguir copiar e colar dados protegidos da empresa ou poderá não conseguir guardar os dados em determinadas localizações.

Para compreender como os utilizadores finais podem utilizar a aplicação Power BI no respetivo dispositivo, reveja os passos indicados nos seguintes artigos:
- [Utilizar aplicações geridas no seu dispositivo iOS](https://docs.microsoft.com/intune-user-help/use-managed-apps-on-your-device-ios#how-do-i-get-managed-apps)
- [Utilizar aplicações geridas no seu dispositivo Android](https://docs.microsoft.com/intune-user-help/use-managed-apps-on-your-device-android)

## <a name="next-steps"></a>Passos seguintes

[Como criar e atribuir políticas de proteção de aplicações](/intune/app-protection-policies) 

[Power BI apps for mobile devices (Aplicações do Power BI para dispositivos móveis)](../consumer/mobile/mobile-apps-for-mobile-devices.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)  
