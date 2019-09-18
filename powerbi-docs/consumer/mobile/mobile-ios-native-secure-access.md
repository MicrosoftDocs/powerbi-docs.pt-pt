---
title: Proteger os dados do Power BI com o método de identificação nativo do dispositivo
description: Saiba como configurar a sua aplicação para iOS para que exija um método de identificação adicional antes de poder aceder aos seus dados do Power BI
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/07/2019
ms.author: mshenhav
ms.openlocfilehash: b7418c9579a439a18a30a967947c15d58693fd44
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/16/2019
ms.locfileid: "66816829"
---
# <a name="protect-power-bi-app-with-face-id-touch-id-or-passcode"></a>Proteger a aplicação Power BI com o Face ID, Touch ID ou um código de acesso 

Em muitos casos, os dados geridos no Power BI são confidenciais, têm de ser protegidos e só podem ser acedidos por utilizadores autorizados. 

A aplicação Power BI para iOS permite-lhe proteger os seus dados ao configurar métodos de identificação adicionais. Terá de fornecer o Face ID, o Touch ID ou um código de acesso sempre que iniciar a aplicação ou quando mudar a aplicação de segundo para primeiro plano.

| ![iPhone](./media/tutorial-mobile-apps-ios-qna/iphone-logo-50-px.png) | ![iPad](./media/tutorial-mobile-apps-ios-qna/ipad-logo-50-px.png) |
|:--- |:--- |
| iPhones |iPads |

## <a name="turn-on-face-id-touch-id-or-passcode-in-app-setting"></a>Ativar o Face ID, Touch ID ou código de acesso nas definições da aplicação

Para utilizar métodos de identificação adicionais no Power BI, aceda às definições da aplicação em **Privacidade e Segurança**. Verá a opção para ativar o Face ID, Touch ID ou código de acesso, com base nas capacidades do seu dispositivo.

![Página de definições da aplicação Power BI para iOS](./media/mobile-ios-native-secure-access/mobile-ios-native-secured-setting.png)

Quando esta opção estiver configurada, sempre que iniciar o Power BI ou mudar a aplicação de segundo para primeiro plano, ser-lhe-á pedido para fornecer a sua identificação antes que possa aceder à aplicação. 

A decisão de pedir o Face ID, Touch ID ou código de acesso é tomada pelo sistema iOS, com base nas capacidades do dispositivo. Se o seu dispositivo suportar o Face ID, terá de utilizar o Face ID. Se suportar o Touch ID, terá de utilizar o Touch ID. Se nenhuma destas funcionalidades for suportada, terá de fornecer um código de acesso.

![Face ID do iOS no Power BI](./media/mobile-ios-native-secure-access/mobile-ios-native-secured-faceid.png)

## <a name="use-mdm-to-enforce-face-id-touch-id-or-passcode"></a>Utilize a MDM para impor a utilização do Face ID, Touch ID ou código de acesso

Algumas organizações têm políticas de segurança e requisitos de conformidade que impõem métodos de identificação adicionais antes que possa aceder a dados confidenciais da empresa. 

A aplicação Power BI para iOS permite que os administradores controlem essa definição ao emitir as definições de configuração da aplicação via push a partir do Microsoft Intune e de outras soluções de gestão de dados globais (MDM). Os administradores podem utilizar a política de proteção de aplicações para ativar esta definição para todos ou para um grupo de utilizadores.

|Chave  |Tipo  |Descrição  |
|---------|---------|---------|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Booleano | O valor predefinido é Falso. <br>Quando o valor estiver definido como Verdadeiro, a aplicação irá forçar os utilizadores a identificarem-se com o Face ID, Touch ID ou código de acesso antes de poderem ver dados do Power BI na aplicação. Os utilizadores que não tenham o Face ID, Touch ID ou um código de acesso configurado no respetivo dispositivo, terão de configurar um destes métodos antes que possam aceder ao Power BI.  |

## <a name="next-steps"></a>Próximos passos

[Use MDM to remotely configure Power BI iOS app](mobile-app-configuration.md) (Utilizar a MDM para configurar a aplicação Power BI para iOS remotamente)
