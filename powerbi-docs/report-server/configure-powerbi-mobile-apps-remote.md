---
title: Configurar o acesso da aplicação móvel para um Servidor de Relatórios remotamente
description: Saiba como configurar as aplicações móveis remotamente para o servidor de relatórios.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 11/07/2019
ms.openlocfilehash: c83ce0735e31e65a813723ce411281821680628d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418101"
---
# <a name="configure-power-bi-mobile-app-access-to-report-server-remotely"></a>Configurar o acesso da aplicação móvel do Power BI para um Servidor de Relatórios remotamente

Aplica-se a:

| ![iPhone](./media/configure-powerbi-mobile-apps-remote/ios-logo-40-px.png) | ![Telemóvel Android](./media/configure-powerbi-mobile-apps-remote/android-logo-40-px.png) |
|:--- |:--- |
| iOS |Android |

Neste artigo, saiba como utilizar a ferramenta MDM da sua organização para configurar o acesso da aplicação móvel do Power BI para um Servidor de Relatórios. Para configurar esta opção, os administradores de TI criam uma política de configuração da aplicação com as informações necessárias para serem enviadas para a aplicação. 

 Com a ligação do Servidor de Relatórios já configurada, os utilizadores da aplicação móvel do Power BI podem ligar-se ao Servidor de Relatórios da organização mais facilmente. 

## <a name="create-the-app-configuration-policy-in-mdm-tool"></a>Criar a política de configuração da aplicação na ferramenta MDM 

Enquanto administrador, eis os passos que tem de seguir no Microsoft Intune para criar a política de configuração da aplicação. Os passos e a experiência de criação da política de configuração da aplicação podem ser diferentes noutras ferramentas MDM. 

1. Ligue a sua ferramenta MDM. 
2. Crie e dê um nome a uma nova política de configuração da aplicação. 
3. Escolha os utilizadores pelos quais pretende distribuir esta política de configuração da aplicação. 
4. Crie pares chave-valor. 

A seguinte tabela enuncia os pares.

|Chave  |Tipo  |Descrição  |
|---------|---------|---------|
| com.microsoft.powerbi.mobile.ServerURL | Cadeia | URL do Servidor de Relatórios <br> Deve começar por http/https |
| com.microsoft.powerbi.mobile.ServerUsername | Cadeia | [opcional] <br> O nome de utilizador a utilizar para ligar o servidor. <br> Se não existir, a aplicação pedirá ao utilizador para escrever o nome de utilizador para a ligação.| 
| com.microsoft.powerbi.mobile.ServerDisplayName | Cadeia | [opcional] <br> O valor predefinido é "Servidor de relatórios" <br> Um nome amigável utilizado na aplicação para representar o servidor | 
| com.microsoft.powerbi.mobile.OverrideServerDetails | Booleano | O valor predefinido é Verdadeiro <br>Quando definido como "True", substitui todas as definições do Servidor de Relatórios já existente no dispositivo móvel. Os servidores existentes que já estiverem configurados serão eliminados. <br> Quando a substituição está definida como Verdadeiro, isto impede também que o utilizador remova essa configuração. <br> Se estiver definido como "Falso", adicionará os valores emitidos, mantendo as definições existentes. <br> Se o mesmo URL do servidor já estiver configurado na aplicação móvel, esta manterá essa configuração tal como está. A aplicação não pedirá ao utilizador para voltar a autenticar para o mesmo servidor. |

Eis um exemplo de definição da política de configuração com o Intune.

![Definições de configuração do Intune](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configuration-settings.png)

## <a name="end-users-connecting-to-report-server"></a>Ligação dos utilizadores finais a um Servidor de Relatórios

 Imaginemos que publica a política de configuração da aplicação para uma lista de distribuição. Quando os utilizadores e os dispositivos nessa lista de distribuição iniciarem a aplicação móvel, terão a seguinte experiência. 

1. Verão uma mensagem a informar que a aplicação móvel está configurada com um Servidor de Relatórios e deverão tocar em **Iniciar sessão**.

    ![Iniciar sessão no servidor de relatórios](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-sign-in.png)

2.  Na página **Ligar ao servidor**, os detalhes do servidor de relatórios já estão preenchidos. Tocam em **Ligar**.

    ![Detalhes do servidor de relatórios preenchidos](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configure-connect-server.png)

3. Escrevem uma palavra-passe para autenticar e, em seguida, tocam em **Iniciar sessão**. 

    ![Captura de ecrã a mostrar a introdução da palavra-passe com o botão Iniciar sessão.](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-address.png)

Agora, podem ver e interagir com os KPIs e os relatórios do Power BI armazenados no Servidor de Relatórios.

## <a name="next-steps"></a>Próximas etapas

- [Ativar o acesso remoto ao Power BI Mobile com o Proxy de Aplicações do Azure Active Directory](/azure/active-directory/manage-apps/application-proxy-integrate-with-power-bi)
- [Descrição geral para administradores](admin-handbook-overview.md)  
- [Instalar o Power BI Report Server](install-report-server.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)