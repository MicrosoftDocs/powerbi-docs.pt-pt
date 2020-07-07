---
title: Criar as novas áreas de trabalho – Power BI
description: Saiba como criar as novas áreas de trabalho, coleções de dashboards, relatórios e relatórios paginados criados para fornecer métricas importantes à sua organização.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/26/2020
ms.author: maggies
ms.custom: contperfq4
LocalizationGroup: Share your work
ms.openlocfilehash: c3a625dcdd58f881c9314e821753f66098e073f5
ms.sourcegitcommit: caf60154a092f88617eb177bc34fb784f2365962
ms.contentlocale: pt-PT
ms.lasthandoff: 06/25/2020
ms.locfileid: "85354438"
---
# <a name="create-the-new-workspaces-in-power-bi"></a>Criar as novas áreas de trabalho no Power BI

Este artigo explica como criar uma das *novas áreas de trabalho* em vez de uma área de trabalho *clássica*. Ambos os tipos de áreas de trabalho são locais onde colabora com colegas. Pode criar coleções de dashboards, relatórios e relatórios paginados nas mesmas. Se quiser, também pode agrupar essa coleção numa *aplicação* e distribuí-la para um público mais vasto.

Veja o que distingue as novas áreas de trabalho das antigas. Nas novas áreas de trabalho, pode:

- Atribuir funções de área de trabalho a grupos de utilizadores e indivíduos.
- Criar uma área de trabalho no Power BI sem criar um grupo do Microsoft 365.
- Utilizar funções de áreas de trabalho mais avançadas para uma gestão de permissões mais flexível.

:::image type="content" source="media/service-create-the-new-workspaces/power-bi-workspace-sales-marketing.png" alt-text="Exemplo de área de trabalho de Vendas e Marketing":::

Para obter mais informações, veja o artigo [novas áreas de trabalho](service-new-workspaces.md).

Pronto para migrar a área de trabalho clássica? Veja [Atualizar as áreas de trabalho clássicas para as novas áreas de trabalho no Power BI](service-upgrade-workspaces.md) para obter detalhes.

> [!NOTE]
> Para impor a segurança a nível da linha (RLS) para os utilizadores do Power BI Pro que procuram conteúdos numa área de trabalho, atribua a Função Visualizador aos mesmos.

## <a name="create-one-of-the-new-workspaces"></a>Criar uma das novas áreas de trabalho

1. Comece por criar a área de trabalho. Selecione **Áreas de trabalho** > **Criar área de trabalho**.
   
     ![Criar área de trabalho](media/service-create-the-new-workspaces/power-bi-workspace-create.png)

2. Está automaticamente a criar uma área de trabalho atualizada, a não ser que opte por **Reverter para a clássica**.
   
     ![Nova experiência de área de trabalho](media/service-create-the-new-workspaces/power-bi-new-workspace.png)
     
     Se selecionar **Reverter para clássica**, [cria uma área de trabalho clássica](service-create-workspaces.md) baseada num grupo do Microsoft 365.

2. Atribua um nome exclusivo à área de trabalho. Se o nome não estiver disponível, edite-o para criar um nome exclusivo.
   
     A aplicação que criar a partir da área de trabalho terá o mesmo nome e ícone que a área de trabalho.
   
1. Aqui estão alguns itens opcionais que pode definir para a área de trabalho:

    Carregue uma **Imagem da área de trabalho**. Os ficheiros podem ser .png ou .jpg. O tamanho do ficheiro tem de ser inferior a 45 KB.
    
    [Adicione uma **Lista de contactos**](#create-a-contact-list). Por predefinição, os administradores da área de trabalho são os contactos. 
    
    [Especifique um **OneDrive da Área de Trabalho**](#set-a-workspace-onedrive) para utilizar a localização de armazenamento dos ficheiros de um grupo do Microsoft 365. 

    Para atribuir a área de trabalho a uma **Capacidade dedicada**, no separador**Premium**, selecione **Capacidade dedicada**.
     
    ![Capacidade dedicada](media/service-create-the-new-workspaces/power-bi-workspace-premium.png)

1. Selecione **Guardar**.

    O Power BI cria a área de trabalho e abre-a. Irá vê-la na lista de áreas de trabalho das quais é membro. 

## <a name="create-a-contact-list"></a>Criar uma lista de contactos

Pode especificar os utilizadores que receberão notificações sobre problemas que afetam a área de trabalho. Por predefinição, qualquer utilizador ou grupo especificado como administrador da área de trabalho é notificado, mas pode adicionar outras pessoas à *lista de contactos*. Os utilizadores ou grupos na lista de contactos estão listados na interface de utilizador (IU) para ajudar os utilizadores a obter ajuda relacionada com a área de trabalho.

1. Aceda à configuração da nova **Lista de contactos** de uma destas duas formas:

    No painel **Criar uma área de trabalho** quando a cria pela primeira vez.

    No painel de navegação, selecione a seta junto a **Áreas de trabalho**, selecione **Mais opções** (...) junto ao nome da área de trabalho > **Definições da área de trabalho**. O painel **Definições** é apresentado.

    ![Definições de área de trabalho](media/service-create-the-new-workspaces/power-bi-workspace-new-settings.png)

2. Em **Avançado** > **Lista de contactos**, aceite a predefinição, **Administradores da área de trabalho**, ou adicione a sua própria lista de **Utilizadores ou grupos específicos**. 

    ![Contactos da área de trabalho](media/service-create-the-new-workspaces/power-bi-workspace-contacts.png)

3. Selecione **Guardar**.

## <a name="set-a-workspace-onedrive"></a>Definir um OneDrive da área de trabalho

A funcionalidade OneDrive da Área de Trabalho permite-lhe configurar um grupo do Microsoft 365 cujo armazenamento de ficheiros da Biblioteca de Documentos do SharePoint está disponível para os utilizadores da área de trabalho. Crie primeiro o grupo fora do Power BI. 

O Power BI não sincroniza as permissões de utilizadores ou grupos que estão configurados para terem acesso à área de trabalho com a associação ao grupo do Microsoft 365. A melhor prática consiste em [conceder o acesso à área de trabalho](#give-access-to-your-workspace) ao mesmo grupo do Microsoft 365 cujo armazenamento de ficheiros configurar nesta definição do grupo do Microsoft 365. Em seguida, faça a gestão do acesso à área de trabalho ao gerir a associação do grupo do Microsoft 365. 

1. Aceda à nova definição da **Área de trabalho do OneDrive** de uma destas duas formas:

    No painel **Criar uma área de trabalho** quando a cria pela primeira vez.

    No painel de navegação, selecione a seta junto a **Áreas de trabalho**, selecione **Mais opções** (...) junto ao nome da área de trabalho > **Definições da área de trabalho**. O painel **Definições** é apresentado.

    ![Definições de área de trabalho](media/service-create-the-new-workspaces/power-bi-workspace-new-settings.png)

2. Em **Avançado** > **Área de trabalho do OneDrive**, introduza o nome do grupo do Microsoft 365 que criou anteriormente. Introduza apenas o nome, não o URL. O Power BI seleciona automaticamente o OneDrive para o grupo.

    ![Especificar a localização do OneDrive](media/service-create-the-new-workspaces/power-bi-new-workspace-onedrive.png)

3. Selecione **Guardar**.

### <a name="access-the-workspace-onedrive-location"></a>Aceder à localização da área de trabalho OneDrive

Uma vez configurada a localização do OneDrive, poderá aceder da mesma forma que acede a outras origens de dados no serviço Power BI.

1. No painel de navegação, selecione **Obter Dados** e, na caixa **Ficheiros**, selecione **Obter**.

    ![Obter dados, obter ficheiros](media/service-create-the-new-workspaces/power-bi-get-data-files.png)

1.  A entrada **OneDrive – Empresas** é o seu próprio OneDrive para Empresas. O segundo OneDrive é aquele que adicionou.

    ![Localização dos ficheiros da área de trabalho – obter dados](media/service-create-the-new-workspaces/power-bi-new-workspace-get-data-onedrive.png)

### <a name="connect-to-apps-in-new-workspaces"></a>Ligar a aplicações nas novas áreas de trabalho

As novas experiências de área de trabalho criam e consomem *aplicações* em vez de pacotes de conteúdos. As aplicações são coleções de dashboards, relatórios e conjuntos de dados que se ligam a serviços de terceiros e dados organizacionais. As aplicações facilitam a obtenção de dados de serviços como o Microsoft Dynamics CRM, o Salesforce e o Google Analytics.

Na nova experiência de áreas de trabalho, não pode criar ou consumir pacotes de conteúdos organizacionais. Peça às suas equipas internas que forneçam aplicações para os pacotes de conteúdos que está a utilizar atualmente. 

## <a name="give-access-to-your-workspace"></a>Conceder acesso à área de trabalho

Qualquer pessoa com função de administrador numa área de trabalho pode conceder acesso à mesma a outras pessoas.

1. Uma vez que desempenha a função de administrador, vê a opção **Acesso** na página da lista de conteúdo da área de trabalho.

    ![Lista de conteúdo da área de trabalho](media/service-create-the-new-workspaces/power-bi-workspace-access-icon.png)

1. Adicione grupos de segurança, listas de distribuição, grupos do Microsoft 365 ou utilizadores individuais a estas áreas de trabalho como administradores, membros, contribuidores ou visualizadores. Veja [Funções nas novas áreas de trabalho](service-new-workspaces.md#roles-in-the-new-workspaces) para obter uma explicação sobre as diferentes funções.

    ![Opção para adicionar membros, administradores e contribuidores às áreas de trabalho](media/service-create-the-new-workspaces/power-bi-workspace-add-members.png)

9. Selecione **Adicionar** > **Fechar**.


## <a name="distribute-an-app"></a>Distribuir uma aplicação

Se quiser distribuir conteúdos oficiais para um grande público na sua organização, poderá publicar uma *aplicação* a partir da sua área de trabalho.  Quando os conteúdos estiverem prontos, selecione os dashboards e os relatórios que pretende publicar e, em seguida, publique-os como uma aplicação. Pode criar uma aplicação a partir de cada área de trabalho.

Leia sobre como [publicar uma aplicação a partir das novas áreas de trabalho](service-create-distribute-apps.md).

## <a name="security-settings"></a>Definições de segurança

A definição **Permitir que os contribuidores atualizem a aplicação desta área de trabalho** permite que os Administradores da área de trabalho deleguem aos utilizadores na função Contribuidor a capacidade de atualizar a aplicação para a área de trabalho. Por predefinição, apenas os Administradores e Membros da área de trabalho podem publicar e atualizar a aplicação para a área de trabalho. 

Quando estiver ativada, os Contribuidores podem:
* Atualizar os metadados da aplicação, como nome, ícone, descrição, site de suporte e cor
* Adicionar ou remover itens incluídos na aplicação, como adicionar relatórios ou conjuntos de dados
* Alterar a navegação da aplicação ou o item predefinido em que a aplicação é aberta

No entanto, os Contribuidores não podem:
* Publicar a aplicação pela primeira vez
* Alterar quem tem permissão para a aplicação


## <a name="next-steps"></a>Próximos passos
* Leia mais no artigo [Organizar o trabalho na nova experiência de áreas de trabalho no Power BI](service-new-workspaces.md)
* [Criar as áreas de trabalho clássicas](service-create-workspaces.md)
* [Publicar uma aplicação a partir das novas áreas de trabalho no Power BI](service-create-distribute-apps.md)
* Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
