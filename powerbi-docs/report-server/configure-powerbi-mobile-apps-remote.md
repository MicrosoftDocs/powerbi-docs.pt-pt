---
title: Configurar o acesso da aplicação móvel iOS a um servidor de relatórios remotamente
description: Saiba como configurar as aplicações móveis para iOS remotamente para o seu servidor de relatórios.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 11/15/2018
ms.author: maggies
ms.openlocfilehash: 740c012d83f9ca70f6e909b8cf62714f67c123d4
ms.sourcegitcommit: 6c6aa214dc36c26a01b29e823598d217a3e2b8a1
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/17/2018
ms.locfileid: "53451381"
---
# <a name="configure-power-bi-ios-mobile-app-access-to-a-report-server-remotely"></a>Configurar o acesso da aplicação móvel do Power BI para iOS a um servidor de relatórios remotamente

Neste artigo, saiba como utilizar a ferramenta MDM da sua organização para configurar o acesso da aplicação móvel do Power BI para iOS a um servidor de relatórios. Para configurar esta opção, os administradores de TI criam uma política de configuração da aplicação com as informações necessárias para serem enviadas para a aplicação. 

 Com a ligação do servidor de relatórios já configurada, os utilizadores da aplicação móvel Power BI para iOS podem ligar-se ao servidor de relatórios da respetiva organização mais facilmente. 

## <a name="create-the-app-configuration-policy-in-mdm-tool"></a>Criar a política de configuração da aplicação na ferramenta MDM 

Enquanto administrador, eis os passos que tem de seguir no Microsoft Intune para criar a política de configuração da aplicação. Os passos e a experiência de criação da política de configuração da aplicação podem ser diferentes noutras ferramentas MDM. 

1. Ligue a sua ferramenta MDM. 
2. Crie e dê um nome a uma nova política de configuração da aplicação. 
3. Escolha os utilizadores pelos quais pretende distribuir esta política de configuração da aplicação. 
4. Crie pares chave-valor. 

A seguinte tabela enuncia os pares.

|Chave  |Tipo  |Descrição  |
|---------|---------|---------|
| com.microsoft.powerbi.mobile.ServerURL | Cadeia | URL do Servidor de Relatórios </br> Deve começar por http/https |
| com.microsoft.powerbi.mobile.ServerUsername | Cadeia | [opcional] </br> O nome de utilizador a utilizar para ligar o servidor. </br> Se não existir, a aplicação pedirá ao utilizador para escrever o nome de utilizador para a ligação.| 
| com.microsoft.powerbi.mobile.ServerDisplayName | Cadeia | [opcional] </br> O valor predefinido é "Servidor de relatórios" </br> Um nome amigável utilizado na aplicação para representar o servidor | 
| com.microsoft.powerbi.mobile.OverrideServerDetails | Booleano | O valor predefinido é Verdadeiro </br>Quando definido como "True", substitui todas as definições do Servidor de Relatórios já existente no dispositivo móvel. Os servidores existentes que já estiverem configurados serão eliminados. </br> Quando a substituição está definida como Verdadeiro, isto impede também que o utilizador remova essa configuração. </br> Se estiver definido como "Falso", adicionará os valores emitidos, mantendo as definições existentes. </br> Se o mesmo URL do servidor já estiver configurado na aplicação móvel, esta manterá essa configuração tal como está. A aplicação não pedirá ao utilizador para voltar a autenticar para o mesmo servidor. |

Eis um exemplo de definição da política de configuração com o Intune.

![Definições de configuração do Intune](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configuration-settings.png)

## <a name="end-users-connecting-to-a-report-server"></a>Ligação dos utilizadores finais a um servidor de relatórios

 Imaginemos que publica a política de configuração da aplicação para uma lista de distribuição. Quando os utilizadores e dispositivos nessa lista de distribuição iniciarem a aplicação móvel para iOS, terão a seguinte experiência. 

1. Veem uma mensagem a informar que a aplicação móvel está configurada com um servidor de relatórios e tocam em **Iniciar sessão**.

    ![Iniciar sessão no servidor de relatórios](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-sign-in.png)

2.  Na página **Ligar ao servidor**, os detalhes do servidor de relatórios já estão preenchidos. Tocam em **Ligar**.

    ![Detalhes do servidor de relatórios preenchidos](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configure-connect-server.png)

3. Escrevem uma palavra-passe para autenticar e, em seguida, tocam em **Iniciar sessão**. 

    ![Detalhes do servidor de relatórios preenchidos](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-address.png)

Agora, podem ver e interagir com KPIs e relatórios do Power BI armazenados no servidor de relatórios.

## <a name="next-steps"></a>Próximos passos
[Descrição geral para administradores](admin-handbook-overview.md)  
[Instalar o Power BI Report Server](install-report-server.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

