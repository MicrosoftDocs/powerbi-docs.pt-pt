---
title: Incorporar conteúdos na aplicação de análise incorporada do Power BI para permitir melhores informações de BI incorporadas para a sua organização
description: Saiba como integrar o Power BI na sua aplicação com o software de análise incorporada, ferramentas de análise incorporada ou ferramentas de business intelligence incorporada. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.custom: seodec18
ms.date: 12/17/2020
ms.openlocfilehash: fbae63597ecf4ff36783ad83785f87c242359f90
ms.sourcegitcommit: 2e81649476d5cb97701f779267be59e393460097
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2021
ms.locfileid: "99494996"
---
# <a name="tutorial-embed-power-bi-content-using-a-sample-embed-for-your-organization-application"></a>Tutorial: Incorporar o conteúdo do Power BI utilizando uma amostra *incorporada para a sua aplicação de organização*

A análise incorporada ao Power BI permite incorporar o conteúdo do Power BI, como relatórios, dashboards e azulejos, na sua aplicação.

Neste tutorial, irá aprender a:

>[!div class="checklist"]
>* Configurar o seu ambiente incorporado.
>* Configure uma *aplicação de* amostra incorporada para a sua organização (também conhecida como *utilizador de dados).*

Para utilizar a sua aplicação, os seus utilizadores terão de iniciar sôms no Power BI.

Normalmente, a solução Incorporar para a sua organização é utilizada por grandes empresas e organizações e é destinada a utilizadores internos.

## <a name="code-sample-specifications"></a>Especificações das amostras de código

Este tutorial inclui instruções para configurar um *incorporado para a sua* aplicação de amostra de organização num dos seguintes quadros:

* .NET Framework
* .NET Core
* Reagir TipoScript

>[!NOTE]
>As amostras *.NET Core* e *.NET Framework* permitirão ao utilizador final visualizar qualquer painel de instrumentos, relatório ou azulejos de Power BI a que tenham acesso no serviço Power BI. A amostra *React TypeScript* permite incorporar apenas um relatório ao qual o seu utilizador final já tem acesso no serviço Power BI.

As amostras de código suportam os seguintes browsers:

* Microsoft Edge
* Google Chrome
* Mozilla Firefox

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar este tutorial, verifique que tem as dependências do Power BI e de código listadas abaixo:

* **Dependências do Power BI**

    * O seu próprio [inquilino do Azure Active Directory](create-an-azure-active-directory-tenant.md).

    * Uma das seguintes licenças:

        * [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md)

        * [Premium por Utilizador (PPU)](../../admin/service-premium-per-user-faq.md)

    >[!NOTE]
    >Para [passar à produção,](move-to-production.md) precisará de uma das seguintes configurações:
    >* Todos os utilizadores com licenças Pro.
    >* Todos os utilizadores com licenças PPU.
    >* Uma [capacidade.](embedded-capacity.md) Esta configuração permite que todos os utilizadores tenham licenças gratuitas.

* **Dependências de código**

    # <a name="net-core"></a>[.NET Core](#tab/net-core)

    * [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) (ou superior)
    
    * Um ambiente de desenvolvimento integrado (IDE). Recomendamos a utilização de um dos seguintes:

        * [Visual Studio](https://visualstudio.microsoft.com/)

        * [Visual Studio Code](https://code.visualstudio.com/)

    # <a name="net-framework"></a>[.NET Framework](#tab/net-framework)

    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * [Visual Studio](https://visualstudio.microsoft.com/)

    # <a name="react-typescript"></a>[Reagir TipoScript](#tab/react)

    * Um editor de texto

    * Terminal da linha de comando (ou PowerShell)

---

## <a name="method"></a>Método

Para criar um incorporado para a sua aplicação de amostra de *organização,* siga estes passos:

1. [Registe uma aplicação do Azure AD](#step-1---register-an-azure-ad-application).

2. [Crie uma área de trabalho do Power BI](#step-2---create-a-power-bi-workspace).

3. [Crie e publique um relatório do Power BI](#step-3---create-and-publish-a-power-bi-report).

4. [Obtenha os valores de parâmetros de incorporação](#step-4---get-the-embedding-parameter-values).

5. [Incorpore os conteúdos](#step-5---embed-your-content).

## <a name="step-1---register-an-azure-ad-application"></a>Passo 1 - Registar uma aplicação AD Azure

Registar a sua aplicação com a Azure AD permite-lhe estabelecer uma identidade para a sua aplicação.

[!INCLUDE[Register Azure AD app](../../includes/embed-tutorial-register-app.md)]

## <a name="step-2---create-a-power-bi-workspace"></a>Passo 2 - Criar um espaço de trabalho Power BI

[!INCLUDE[Create a Power BI workspace](../../includes/embed-tutorial-create-workspace.md)]

## <a name="step-3---create-and-publish-a-power-bi-report"></a>Passo 3 - Criar e publicar um relatório Power BI

[!INCLUDE[Create a Power BI report](../../includes/embed-tutorial-create-report.md)]

## <a name="step-4---get-the-embedding-parameter-values"></a>Passo 4 - Obtenha os valores dos parâmetros incorporados

Para incorporar o seu conteúdo, terá de obter alguns valores de parâmetro. Os valores dos parâmetros de que necessitará dependem do idioma da aplicação da amostra que pretende utilizar. O quadro abaixo lista quais os valores dos parâmetros necessários para cada amostra.

|Parâmetro  |.NET Core  |.NET Framework  |Reagir TipoScript |
|---------|---------|---------|---------|
|[ID de Cliente](#client-id) |![Aplica-se a:](../../media/yes.png) |![Aplica-se a:](../../media/yes.png)         |![Aplica-se a:](../../media/yes.png) |
|[Segredo do cliente](#workspace-id) |![Aplica-se a:](../../media/yes.png) |![Aplica-se a:](../../media/yes.png) |![Não se aplica a:](../../media/no.png) |
|[ID da Área de Trabalho]() |![Não se aplica a:](../../media/no.png) |![Não se aplica a:](../../media/no.png) |![Aplica-se a:](../../media/yes.png) |
|[ID do Relatório]() |![Não se aplica a:](../../media/no.png) |![Não se aplica a:](../../media/no.png) |![Aplica-se a:](../../media/yes.png) |

### <a name="client-id"></a>ID de Cliente

>[!TIP]
>**Aplica-se a:** ![ Aplica-se ](../../media/yes.png) a. . Net Core ![ aplica-se a ](../../media/yes.png) . . Net Framework ![ aplica-se a. ](../../media/yes.png) Reagir TipoScript

[!INCLUDE[Get the client ID](../../includes/embed-tutorial-client-id.md)]

### <a name="client-secret"></a>Segredo do cliente

>[!TIP]
>**Aplica-se a:** ![ Aplica-se ](../../media/yes.png) a. . Net Core ![ aplica-se a ](../../media/yes.png) . . Net Framework ![ não se aplica a. ](../../media/no.png) Reagir TipoScript

[!INCLUDE[Get the client secret](../../includes/embed-tutorial-client-secret.md)]

### <a name="workspace-id"></a>ID da área de trabalho

>[!TIP]
>**Aplica-se a:** ![ Não se aplica ](../../media/no.png) a. . Net Core ![ não se aplica ](../../media/no.png) a. . Net Framework ![ aplica-se a. ](../../media/yes.png) Reagir TipoScript

[!INCLUDE[Get the workspace ID](../../includes/embed-tutorial-workspace-id.md)]

### <a name="report-id"></a>ID do Relatório

>[!TIP]
>**Aplica-se a:** ![ Não se aplica ](../../media/no.png) a. . Net Core ![ não se aplica ](../../media/no.png) a. . Net Framework ![ aplica-se a. ](../../media/yes.png) ReactTypeScript

[!INCLUDE[Get the report ID](../../includes/embed-tutorial-report-id.md)]

## <a name="step-5---embed-your-content"></a>Passo 5 – Incorporar os conteúdos

A aplicação de amostra incorporada Power BI permite-lhe criar um *incorporado para a aplicação* Power BI da sua organização.

Siga estes passos para modificar o incorporado para a sua aplicação de amostra de *organização,* para incorporar o seu relatório Power BI.

[!INCLUDE[Embedding steps](../../includes/embed-tutorial-embedding-steps.md)]

4. Consoante a linguagem que pretende que a aplicação utilize, abra uma das seguintes pastas:

    * .NET Core
    * .NET Framework
    * Reagir-TS

    >[!NOTE]
    >O *incorporado para as* aplicações de amostra da sua organização apenas suporta os quadros listados acima. As aplicações *de* amostra Java , *Node JS* e *Python,* apenas suportam o incorporado para a solução *[dos seus clientes.](embed-sample-for-customers.md)*

# <a name="net-core"></a>[.NET Core](#tab/net-core)

### <a name="configure-your-azure-ad-app"></a>Configure a sua app AD Azure

[!INCLUDE[Configure the Azure AD authentication options](../../includes/embed-tutorial-org-azure-ad-app.md)]

5. Nas *configurações da Plataforma,* abra a sua plataforma *Web* e na secção **URIs de redirecionamento,** adicione `https://localhost:5000/signin-oidc` .

    > [!NOTE]
    >Se não tiver uma plataforma **Web,** **selecione Adicione uma plataforma** e na janela das plataformas *Configure,* selecione **Web**.

6. Guarde as alterações.

:::image type="content" source="media/embed-sample-for-your-organization/azure-ad-net-configurations.png" alt-text="Screenshot mostrando as configurações de autenticação da aplicação AZure AD, incluindo o redirecionamento web U R I para a amostra de aplicação .NET core.":::

### <a name="configure-the-sample-embedding-app"></a>Configure a app de incorporação da amostra

1. Abra o **Incorporado para a pasta da organização.**

2. Abra o *incorporado para a sua aplicação* de amostra de organização usando um destes métodos:

    * Se estiver a utilizar o [Visual Studio,](https://visualstudio.microsoft.com/)abra o ficheiro **UserOwnsData.sln.**

    * Se estiver a utilizar o [Código do Estúdio Visual,](https://code.visualstudio.com/)abra a pasta **UserOwnsData.**

3. Abra **appsettings.js** e preencha os seguintes valores de parâmetro:

    * `ClientId` - Use o [ID](#client-id) GUID do cliente

    * `ClientSecret` - Use o segredo do [cliente](#client-secret)

### <a name="run-the-sample-app"></a>Execute a aplicação de exemplo

1. Execute o projeto ao selecionar a opção adequada:

    * Se estiver a utilizar o **Visual Studio**, selecione **IIS Express (play)** (IIS Express [reproduzir]).

    * Se estiver a utilizar o **Visual Studio Code**, selecione **Run > Start Debugging** (Executar > Iniciar Depuração).

[!INCLUDE[The embedded application sample app interface](../../includes/embed-tutorial-org-sample-app.md)]

# <a name="net-framework"></a>[.NET Framework](#tab/net-framework)

### <a name="configure-your-azure-ad-app"></a>Configure a sua app AD Azure

[!INCLUDE[Configure the Azure AD authentication options](../../includes/embed-tutorial-org-azure-ad-app.md)]

5. Nas *configurações da Plataforma,* configure o seguinte:

    1. Na sua plataforma *Web,* na secção **Redirecionar URIs,** adicione `https://localhost:44300/` .

        > [!NOTE]
        >Se não tiver uma plataforma **Web,** **selecione Adicione uma plataforma** e na janela das plataformas *Configure,* selecione **Web**.
    
    2. Em *bolsas implícitas e fluxos híbridos,* permita a opção **ID tokens.**
    
6. Guarde as alterações.

:::image type="content" source="media/embed-sample-for-your-organization/azure-ad-framework-configurations.png" alt-text="Screenshot mostrando as configurações de autenticação da aplicação AZure AD, incluindo o redirecionamento web U R I e a opção de token de acesso selecionado para a amostra de aplicação quadro .NET.":::

### <a name="configure-the-sample-embedding-app"></a>Configure a app de incorporação da amostra

1. Abra o **Incorporado para a pasta da organização.**

2. Utilizando [o Visual Studio,](https://visualstudio.microsoft.com/)abra o ficheiro **UserOwnsData.sln.**

3. Abra **Web.config** e preencha os seguintes valores de parâmetro:

    * `clientId` - Use o [ID](#client-id) GUID do cliente

    * `clientSecret` - Use o segredo do [cliente](#client-secret)

### <a name="run-the-sample-app"></a>Execute a aplicação de exemplo

1. Execute o projeto ao selecionar **IIS Express (play)** (IIS Express [reproduzir]).

[!INCLUDE[The embedded application sample app interface](../../includes/embed-tutorial-org-sample-app.md)]

# <a name="react-typescript"></a>[Reagir TipoScript](#tab/react)

### <a name="configure-your-azure-ad-app"></a>Configure a sua app AD Azure

[!INCLUDE[Configure the Azure AD authentication options](../../includes/embed-tutorial-org-azure-ad-app.md)]

5. Nas *configurações da Plataforma,* configure a sua plataforma **Web** da seguinte forma:

    1. Em **Redirecionar URIs** adicionar `https://localhost:3000` e selecionar **Configurar**.

        > [!NOTE]
        >Se não tiver uma plataforma **Web,** **selecione Adicione uma plataforma** e na janela das plataformas *Configure,* selecione **Web**.

    2. Nos *fluxos implícitos de concessão e híbridos,* permitir ambas as opções:
        * **Tokens de acesso**
        * **Tokens de ID**
    
6. Guarde as alterações.

:::image type="content" source="media/embed-sample-for-your-organization/azure-ad-react-configurations.png" alt-text="Screenshot mostrando as configurações de autenticação da aplicação AD Azure, incluindo o reorientador web U R I definido para local 3000.":::

### <a name="configure-the-sample-embedding-app"></a>Configure a app de incorporação da amostra

1. Abra o **Incorporado para a pasta**  >  **UserOwnsData**  >  **src da** sua organização.

2. Utilizando um editor de texto, abra o ficheiro **Config.ts** e preencha os seguintes valores de parâmetro:

    * `clientId` - Use o [ID](#client-id) GUID do cliente

    * `workspaceId` - Use o [ID do espaço de trabalho](#client-secret)

    * `reportId`- Use a [ID](#report-id) do relatório

3. Guarde o ficheiro.

### <a name="run-the-sample-app"></a>Execute a aplicação de exemplo

1. Abra um terminal e navegue para **incorporar para a sua organização**  >  **UserOwnsData**.

2. Instale as dependências necessárias executando o seguinte comando:

   `npm install`

3. Execute a aplicação executando o seguinte comando:

   `npm run start`

    >[!NOTE]
    >Durante o seu primeiro súlsem, será solicitado para permitir permissões AD AZure para a aplicação.

---

## <a name="developing-your-application"></a>Desenvolver a sua aplicação

Após configurar e executar a aplicação de amostra *Embed for your customers* (Incorporar para os seus clientes), pode começar a desenvolver a sua própria aplicação.

[!INCLUDE[Move to production](../../includes/embed-tutorial-production.md)]

## <a name="next-steps"></a>Passos seguintes

> [!div class="nextstepaction"]
>[Mover para produção](move-to-production.md)

>[!div class="nextstepaction"]
>[Incorporar para os seus clientes](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Incorporar relatórios paginados para os seus clientes](embed-paginated-reports-customers.md)

> [!div class="nextstepaction"]
>[Embed paginated reports for your organization (Incorporar relatórios paginados para a sua organização)](embed-paginated-reports-organization.md)

>[!div class="nextstepaction"]
>[Pergunte à Comunidade do Power BI](https://community.powerbi.com/)