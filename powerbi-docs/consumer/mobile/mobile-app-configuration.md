---
title: Definições de configuração da aplicação Power BI para iOS
description: Como personalizar o comportamento do Power BI para iOS com a ferramenta MDM
author: paulinbar
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/07/2019
ms.author: mshenhav
ms.openlocfilehash: bc9c6dd8cd892ab0304cc5a99a3bb780486f32f0
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/16/2019
ms.locfileid: "70160166"
---
# <a name="remotely-configure-power-bi-ios-app-using-mobile-device-management-mdm-tool"></a>Configurar remotamente a aplicação Power BI para iOS com a ferramenta de gestão de dispositivos móveis (MDM)

A aplicação Power BI Mobile para iOS suporta as definições da aplicação que permitem que os administradores do Office 365 e da gestão de dispositivos móveis (MDM), como o Intune, personalizem o comportamento da aplicação.

A aplicação Power BI Mobile para iOS suporta os seguintes cenários de configuração:

- Configuração do Servidor de Relatórios
- Definições de proteção de dados

## <a name="report-server-configuration"></a>Configuração do servidor de relatórios

A aplicação Power BI para iOS permite que os administradores emitam remotamente a configuração do Servidor de Relatórios com os dispositivos inscritos.

| Chave | Tipo | Descrição |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | Cadeia | URL do Servidor de Relatórios.<br><br>Deve começar por http/https.|
| com.microsoft.powerbi.mobile.ServerUsername | Cadeia | [opcional]<br><br>O nome de utilizador a utilizar para ligar o servidor.<br><br>Se não existir, a aplicação pedirá ao utilizador para escrever o nome de utilizador para a ligação.|
| com.microsoft.powerbi.mobile.ServerDisplayName | Cadeia | [opcional]<br><br>O valor predefinido é "Servidor de relatórios"<br><br>Um nome amigável utilizado na aplicação para representar o servidor. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Booleano | [opcional]<br><br>O valor predefinido é Verdadeiro. Quando definido como Verdadeiro, substitui todas as definições do Servidor de Relatórios já existente no dispositivo móvel. Os servidores existentes que já estiverem configurados serão eliminados. Quando a substituição está definida como Verdadeiro, isto impede também que o utilizador remova essa configuração.<br><br>Se estiver definido como Falso, adicionará os valores emitidos, mantendo as definições existentes. Se o mesmo URL do servidor já estiver configurado na aplicação móvel, esta manterá essa configuração tal como está. A aplicação não pedirá ao utilizador para voltar a autenticar para o mesmo servidor. |

## <a name="data-protection-setting"></a>Definição de proteção de dados

A aplicação Power BI para iOS permite que os administradores personalizem a configuração predefinida para as definições de privacidade e segurança. Pode forçar os utilizadores a fornecer o Face ID, o Touch ID ou um código de acesso para acederem à aplicação Power BI.

| Chave | Tipo | Descrição |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Booleano | O valor predefinido é Falso. <br><br>Podem ser necessários dados biométricos, tais como o TouchID e o FaceID, para que os utilizadores acedam à aplicação no respetivo dispositivo. Nesse caso, são utilizados dados biométricos além da autenticação.<br><br>Se forem utilizadas políticas de proteção de aplicações, a Microsoft recomenda a desativação desta definição para evitar pedidos de acesso duplo. |

## <a name="deploying-app-configuration-settings"></a>Implementar definições de configuração da aplicação

Os seguintes passos permitem-lhe criar uma política de configuração da aplicação. Depois de criar a política de configuração, pode atribuir as respetivas definições a grupos de utilizadores.

1. Ligue a sua ferramenta MDM.

2. Crie e dê um nome a uma nova política de configuração da aplicação.

3. Escolha os utilizadores pelos quais pretende distribuir esta política de configuração da aplicação.

4. Crie pares chave-valor para a definição que pretende emitir para os seus utilizadores.

O portal do Intune permite que os administradores implementem facilmente estas definições na aplicação Power BI para iOS através de políticas de configuração da aplicação.
No entanto, é suportado qualquer fornecedor de MDM. Se não utilizar o Intune, terá de consultar a documentação relativa à MDM para saber como implementar estas definições.

## <a name="next-steps"></a>Próximos passos

* Transfira a [aplicação móvel do Power BI para iPhone](http://go.microsoft.com/fwlink/?LinkId=522062)
* Siga [@MSPowerBI no Twitter](https://twitter.com/MSPowerBI)
* Participe na conversa na [Comunidade do Power BI](http://community.powerbi.com/)
