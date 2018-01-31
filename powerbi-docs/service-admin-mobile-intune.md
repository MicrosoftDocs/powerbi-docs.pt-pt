---
title: "Configurar aplicações móveis do Power BI com o Microsoft Intune"
description: "Como configurar as aplicações do Power BI Mobile com o Microsoft Intune. Isto inclui como adicionar e implementar a aplicação. E como criar a política de aplicação móvel para controlo de segurança."
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
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 06/28/2017
ms.author: maghan
ms.openlocfilehash: 97f28a845be24baa7633f0cf4fcac29d4d1e74e9
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2018
---
# <a name="configure-mobile-apps-with-microsoft-intune"></a>Configurar aplicações móveis do Power BI com o Microsoft Intune
O Microsoft Intune permite às organizações gerir dispositivos e aplicações. As aplicações móveis do Power BI, para iOS e Android, integram-se no Intune para lhe permitir gerir a aplicação nos seus dispositivos e controlar a segurança. Através de políticas de configuração, pode controlar itens como requerer um PIN de acesso, controlar como os dados são processados pela aplicação e até mesmo encriptar dados de aplicação quando esta não estiver a ser utilizada.

<iframe width="560" height="315" src="https://www.youtube.com/embed/9HF-qsdQvHw?list=PLv2BtOtLblH1nPVPU2etFzTNmpz49dwXm" frameborder="0" allowfullscreen></iframe>

## <a name="general-mobile-device-management-configuration"></a>Configuração geral da gestão de dispositivos móveis
Este artigo não serve como guia de configuração completo para o Microsoft Intune. Se estiver a fazer a integração com o Intune apenas agora, existem alguns itens que tem de configurar. [Saiba mais](https://technet.microsoft.com/library/jj676587.aspx)

O Microsoft Intune pode coexistir com a Gestão de Dispositivos Móveis (MDM) no Office 365. [Saiba mais](https://blogs.technet.microsoft.com/configmgrdogs/2016/01/04/microsoft-intune-co-existence-with-mdm-for-office-365/)

Este artigo pressupõe que o Intune está configurado corretamente e tem dispositivos registados no Intune. Se estiver a coexistir com o MDM, o dispositivo será mostrado como registado no MDM, mas estará disponível para gestão no Intune.

> [!NOTE]
> Após a organização ter configurado o MAM do Microsoft Intune, caso utilize a aplicação móvel do Power BI num dispositivo iOS ou Android, a atualização de dados em segundo plano é desativada. Da próxima vez que entrar na aplicação, o Power BI atualiza os dados do serviço Power BI na Web.
> 
> 

## <a name="step-1-get-the-url-for-the-application"></a>Passo 1: obter o URL da aplicação
Antes de criar a aplicação no Intune, tem de obter os URLs para as aplicações. Para iOS, serão obtidos pelo iTunes. Para Android, pode obtê-los na página de aplicações móveis do Power BI.

Guarde o URL, uma vez que vai precisar deste durante a criação da aplicação.

### <a name="ios"></a>iOS
Para obter o URL da aplicação para iOS, tem de obtê-la no iTunes.

1. Abra o iTunes.
2. Procure *Power BI*.
3. Deverá ver **Microsoft Power BI** apresentado em **Aplicações para iPhone** e **Aplicações para iPad**. Pode utilizar qualquer opção, visto que obterá o mesmo URL.
4. Selecione o menu pendente **Obter** e **Copiar Ligação**.
   
    ![](media/service-admin-mobile-intune/itunes-url.png)

Deve ser semelhante ao seguinte.

    https://itunes.apple.com/us/app/microsoft-power-bi/id929738808?mt=8

### <a name="android"></a>Android
Pode obter o URL para o Google Play na [página de aplicações móveis do Power BI](https://powerbi.microsoft.com/mobile/). Clicar no ícone **transferir do Google Play** direcioná-lo-á para a página da aplicação. Pode copiar o URL da barra de endereços do browser. Deve ser semelhante ao seguinte.

    https://play.google.com/store/apps/details?id=com.microsoft.powerbim

## <a name="step-2-create-a-mobile-application-management-policy"></a>Passo 2: criar uma política de gestão de aplicações móveis
A política de gestão de aplicações móveis permite-lhe impor itens, como um PIN de acesso. Pode criar um no portal do Intune. 

Pode criar a aplicação ou a política primeiro. Não importa a ordem com que são adicionados. Têm apenas de existir para o passo de implementação.

1. Selecione **Política** > **Políticas de Configuração**.
   
    ![](media/service-admin-mobile-intune/intune-policy.png)
2. Selecione **Adicionar...**.
3. Em **Software**, pode selecionar a Gestão de Aplicações Móveis para Android ou iOS. Para começar rapidamente, pode selecionar **Criar uma política com as definições recomendadas** ou criar uma política personalizada.
4. Edite a política para configurar as restrições que quer na aplicação.

## <a name="step-3-create-the-application"></a>Passo 3: criar a aplicação
A aplicação é uma referência, ou pacote, guardada no Intune para implementação. Temos de criar uma aplicação e fazer referência ao URL da aplicação que obtivemos do Google Play ou iTunes.

Pode criar a aplicação ou a política primeiro. Não importa a ordem com que são adicionados. Têm apenas de existir para o passo de implementação.

1. Aceda ao portal do Intune e selecione **Aplicações** no menu à esquerda.
2. Selecione **Adicionar Aplicação**. Isto inicializará a aplicação **Adicionar Software**.

### <a name="ios"></a>iOS
1. Selecione **Aplicação iOS gerida a partir da App Store** no menu pendente.
2. Introduza o URL da aplicação obtido no [Passo 1](#step-1-get-the-url-for-the-application) e selecione **Seguinte**.
   
    ![](media/service-admin-mobile-intune/intune-add-software-ios1.png)
3. Forneça um **Editor**, um **Nome** e uma **Descrição**. Como alternativa, pode fornecer um **Ícone**. A **Categoria** refere-se à aplicação do Portal da Empresa. Quando terminar, selecione **Seguinte**.
4. Pode decidir se quer publicar a aplicação como **Qualquer** (predefinição), **iPad** ou **iPhone**. Por predefinição, será mostrado **Qualquer** e funcionará para ambos os tipos de dispositivo. A aplicação Power BI utiliza o mesmo URL para iPhone e iPad. Selecione **Seguinte**.
5. Selecione **Carregar**.

> [!NOTE]
> A aplicação pode não ser apresentada na lista de aplicações até que atualize a página. Pode clicar em **Descrição geral** e voltar para **Aplicações** para recarregar a página.
> 
> 

![](media/service-admin-mobile-intune/intune-add-software-ios2.png)

### <a name="android"></a>Android
1. Selecione **Ligação Externa** no menu pendente.
2. Introduza o URL da aplicação obtido no [Passo 1](#step-1-get-the-url-for-the-application) e selecione **Seguinte**.
   
    ![](media/service-admin-mobile-intune/intune-add-software-android1.png)
3. Forneça um **Editor**, um **Nome** e uma **Descrição**. Como alternativa, pode fornecer um **Ícone**. A **Categoria** refere-se à aplicação do Portal da Empresa. Quando terminar, selecione **Seguinte**.
4. Selecione **Carregar**.

> [!NOTE]
> A aplicação pode não ser apresentada na lista de aplicações até que atualize a página. Pode clicar em **Descrição geral** e voltar para **Aplicações** para recarregar a página.
> 
> 

![](media/service-admin-mobile-intune/intune-add-software-android2.png)

## <a name="step-4-deploy-the-application"></a>Passo 4: implementar a aplicação
Depois de ter adicionado a aplicação, tem de implementá-la para que fique disponível para os utilizadores finais. Este é o passo em que associará a política criada com a aplicação.

### <a name="ios"></a>iOS
1. No ecrã de aplicações, selecione a aplicação que criou. Selecione a ligação **Gerir Implementação…**.
   
    ![](media/service-admin-mobile-intune/intune-deploy-ios1.png)
2. No ecrã **Selecionar Grupos**, pode escolher os grupos nos quais quer implementar a aplicação. Selecione **Seguinte**.
3. No ecrã **Ação de Implementação**, pode escolher como quer implementar a aplicação. Ao selecionar **Instalação Disponível** ou **Instalação Obrigatória**, a aplicação será disponibilizada no Portal da Empresa para que os utilizadores a instalem a pedido. Quando terminar a sua seleção, selecione **Seguinte**.
   
    ![](media/service-admin-mobile-intune/intune-deploy-ios2.png)
4. No ecrã **Gestão de Aplicações Móveis**, pode selecionar a política de Gestão de Aplicações Móveis criada no [Passo 2](#step-2-create-a-mobile-application-management-policy). A predefinição será a política que criou, se for a única política iOS disponível. Selecione **Seguinte**.
   
    ![](media/service-admin-mobile-intune/intune-deploy-ios3.png)
5. No ecrã **Perfil de VPN**, pode selecionar uma política, se tiver uma para a sua organização. A predefinição é **Nenhum**. Selecione **Seguinte**.
6. No ecrã **Configuração de Aplicação Móvel**, pode selecionar uma **Política de Configuração da Aplicação**, se tiver criado uma. A predefinição é **Nenhum**. Isto não é necessário. Selecione **Concluir**.

Depois de implementar a aplicação, deverá ser mostrado **Sim** para implementado, na página de aplicações.

### <a name="android"></a>Android
1. No ecrã de aplicações, selecione a aplicação que criou. Selecione a ligação **Gerir Implementação…**.
   
    ![](media/service-admin-mobile-intune/intune-deploy-android1.png)
2. No ecrã **Selecionar Grupos**, pode escolher os grupos nos quais quer implementar a aplicação. Selecione **Seguinte**.
3. No ecrã **Ação de Implementação**, pode escolher como quer implementar a aplicação. Ao selecionar **Instalação Disponível** ou **Instalação Obrigatória**, a aplicação será disponibilizada no Portal da Empresa para que os utilizadores a instalem a pedido. Quando terminar a sua seleção, selecione **Seguinte**.
   
    ![](media/service-admin-mobile-intune/intune-deploy-android2.png)
4. No ecrã **Gestão de Aplicações Móveis**, pode selecionar a política de Gestão de Aplicações Móveis criada no [Passo 2](#step-2-create-a-mobile-application-management-policy). A predefinição será a política que criou, se for a única política Android disponível. Selecione **Concluir**.
   
    ![](media/service-admin-mobile-intune/intune-deploy-android3.png)

Depois de implementar a aplicação, deverá ser mostrado **Sim** para implementado, na página de aplicações.

## <a name="step-5-install-the-application-on-a-device"></a>Passo 5: instalar a aplicação num dispositivo
Instalará a aplicação através do Portal da Empresa. Se ainda não instalou o Portal da Empresa, pode obtê-lo na loja de aplicações nas plataformas iOS ou Android. Iniciará sessão no Portal da Empresa com o início de sessão empresarial.

1. Abra a aplicação Portal da Empresa.
2. Se não vir a aplicação Power BI listada como uma aplicação em destaque, selecione **Aplicações da Empresa**.
   
    ![](media/service-admin-mobile-intune/intune-companyportal1.png)
3. Selecione a aplicação Power BI que implementou.
   
    ![](media/service-admin-mobile-intune/intune-companyportal2.png)
4. Selecione **Instalar**.
   
    ![](media/service-admin-mobile-intune/intune-companyportal3.png)
5. Se estiver no iOS, a aplicação será enviada por push para si. Selecione **Instalar** na caixa de diálogo de envio por push.
   
    ![](media/service-admin-mobile-intune/intune-companyportal5.png)

Após a instalação, verá **Gerido pela sua empresa**. Se tiver ativado o acesso através de um PIN, na política, verá o seguinte.

![](media/service-admin-mobile-intune/intune-powerbi-pin.png)

## <a name="next-steps"></a>Próximos passos
[Configurar e implementar políticas de gestão de aplicações móveis na consola do Microsoft Intune](https://technet.microsoft.com/library/dn878026.aspx)  
[Power BI apps for mobile devices (Aplicações do Power BI para dispositivos móveis)](mobile-apps-for-mobile-devices.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

