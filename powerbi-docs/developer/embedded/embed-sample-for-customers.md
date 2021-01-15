---
title: Incorporar conteúdos na aplicação de análise incorporada do Power BI para permitir melhores informações de BI incorporadas para os seus clientes
description: Saiba como incorporar um relatório, dashboard ou mosaico numa amostra de análise do Power BI Embedded. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 12/22/2020
ms.openlocfilehash: de954c5950f550c3ed2f3c340714851f5233d3e8
ms.sourcegitcommit: a5e98bc86915f7bea6a0ab5df282683840e63d2c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/07/2021
ms.locfileid: "97969771"
---
# <a name="tutorial-embed-power-bi-content-using-a-sample-embed-for-your-customers-application"></a>Tutorial: Incorporar conteúdos do Power BI através de uma aplicação de amostra *Embed for your customers* (Incorporar para os seus clientes)

**A análise incorporada** e o **Power BI Embedded** (a oferta do Azure) permitem-lhe incorporar conteúdos do Power BI, como relatórios, dashboards e mosaicos, na sua aplicação.

Neste tutorial, irá aprender a:
>[!div class="checklist"]
>* Configurar o seu ambiente incorporado.
>* Configurar uma aplicação de amostra *Embed for your customers* (Incorporar para os seus clientes) – também conhecida como *App Owns Data* (A Aplicação Detém os Dados).

Os utilizadores não irão precisar de iniciar sessão no Power BI ou de ter uma licença do Power BI para utilizarem a sua aplicação.

Recomendamos que utilize o método *Incorporar para os seus clientes* para incorporar os seus conteúdos do Power BI se for um fabricante independente de software (ISV) ou um programador e quiser criar aplicações para terceiros.

## <a name="code-sample-specifications"></a>Especificações das amostras de código

Este tutorial inclui instruções para configurar uma aplicação de amostra *Embed for your customers* (Incorporar para os seus clientes) numa das seguintes linguagens:

* .NET Framework
* .NET Core
* Java
* Node JS
* Python

As amostras de código suportam os seguintes browsers:

* Google Chrome

* Microsoft Edge

* Mozilla Firefox

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar este tutorial, verifique que tem as dependências do Power BI e de código listadas abaixo:

* **Dependências do Power BI**

    * O seu próprio [inquilino do Azure Active Directory](create-an-azure-active-directory-tenant.md).

    * Para autenticar a sua aplicação no Power BI, precisará de ter um dos seguintes:

        * [Principal de serviço](embed-service-principal.md)– um [objeto principal de serviço](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) do Azure Active Directory (Azure AD) que permita que o Azure AD autentique a aplicação.

        * Licença do [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md) – é o seu **utilizador principal** e a sua aplicação irá utilizá-la para autenticar no Power BI.

        * Uma licença [Premium Por Utilizador (PPU)](../../admin/service-premium-per-user-faq.md) – é o seu **utilizador principal** e a sua aplicação irá utilizá-la para autenticar no Power BI.

    >[!NOTE]
    >Para [passar para a fase de produção](move-to-production.md) precisa de uma [capacidade](embedded-capacity.md).

* **Dependências de código**

    # <a name="net-framework"></a>[.NET Framework](#tab/net-framework)
    
    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * [Visual Studio](https://visualstudio.microsoft.com/)
    
    
    # <a name="net-core"></a>[.NET Core](#tab/net-core)
    
    * [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) (ou superior)
    
    * Um ambiente de desenvolvimento integrado (IDE). Recomendamos a utilização de um dos seguintes:
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)

    # <a name="java"></a>[Java](#tab/java)
    
    * [JDK (ou JRE)](https://www.oracle.com/java/technologies/)
    
    * [IDE do Eclipse](https://www.eclipse.org/downloads/packages/) – verifique que tem o *Eclipse for Java EE Developers* (edição empresarial)
    
    * [Distribuições Binárias do Apache Tomcat](https://tomcat.apache.org/)
    
    # <a name="node-js"></a>[Node JS](#tab/node-js)
    
    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * Um ambiente de desenvolvimento integrado (IDE). Recomendamos a utilização de um dos seguintes:
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)
    
    # <a name="python"></a>[Python](#tab/python)
    
    * [Python 3](https://www.python.org/downloads/) (ou superior)
    
        >[!NOTE]
        >* Se estiver a instalar o *Python* pela primeira vez, selecione a opção **Add Python to PATH** (Adicionar o Python ao PATH) para adicionar a instalação à variável `PATH`.
        >* Se já tiver o *Python* instalado, verifique que a variável `PATH` inclui o caminho da instalação. Para obter mais informações, consulte a documentação do Python [Excursus: Definir variáveis de ambiente ](https://docs.python.org/3/using/windows.html#excursus-setting-environment-variables) (esta ligação é referente ao Python 3).
    
    * Um ambiente de desenvolvimento integrado (IDE). Recomendamos a utilização de um dos seguintes:
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)
    
    ---

## <a name="method"></a>Método

Para criar uma aplicação de amostra *Embed for your customers* (Incorporar para os seus clientes), siga estes passos:

1. [Selecione o seu método de autenticação](#step-1---select-your-authentication-method).

2. [Registe uma aplicação do Azure AD](#step-2---register-an-azure-ad-application).

3. [Crie uma área de trabalho do Power BI](#step-3---create-a-power-bi-workspace).

4. [Crie e publique um relatório do Power BI](#step-4---create-and-publish-a-power-bi-report).

5. [Obtenha os valores de parâmetros de incorporação](#step-5---get-the-embedding-parameter-values).

6. [Conceda acesso de API ao principal de serviço](#step-6---service-principal-api-access)
 
7. [Permita o acesso à área de trabalho](#step-7---enable-workspace-access).

8. [Incorpore os conteúdos](#step-8---embed-your-content).

## <a name="step-1---select-your-authentication-method"></a>Passo 1 – Selecione o seu método de autenticação

A sua solução incorporada varia consoante o método de autenticação que selecionar. Assim, é importante compreender as diferenças entre os métodos de autenticação e decidir quais se adequam melhor à sua solução.

A tabela abaixo descreve algumas das principais diferenças entre os métodos de autenticação [principal de serviço](embed-service-principal.md) e **utilizador principal**.

|Consideração  |Service principal (Principal de serviço)  |Master user (Utilizador principal)  |
|---------|---------|---------|
|Mecanismo     |O [objeto principal de serviço](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) da sua aplicação do Azure AD permite ao Azure AD autenticar a sua aplicação de solução incorporada no Power BI.        |A sua aplicação do Azure AD utiliza as credenciais (nome de utilizador e palavra-passe) de um utilizador do Power BI para autenticar no Power BI.         |
|Segurança     |O *principal de serviço* é o método de autorização recomendado do Azure AD. Se estiver a utilizar um principal de serviço*, pode autenticar com um *segredo da aplicação* ou um *certificado*.</br></br>Este tutorial só abrange a utilização do *principal de serviço* com um *segredo da aplicação*. Para incorporar com um *principal de serviço* e um *certificado*, consulte o artigo [principal de serviço com um certificado](embed-service-principal-certificate.md).         |Este método de autenticação não é considerado tão seguro como utilizar um *principal de serviço*. Isto deve-se ao facto de ter de permanecer vigilante relativamente às credenciais do *utilizador principal* (nome de utilizador e palavra-passe). Por exemplo, não as pode expor na sua aplicação incorporada e deve alterar a palavra-passe com frequência.         |
|Permissões delegadas do Azure AD |Não necessárias. |O seu *utilizador principal* ou um administrador tem de dar o consentimento para a sua aplicação aceder às [permissões](/azure/active-directory/develop/v2-permissions-and-consent) da API REST do Power BI (também denominadas âmbitos). Por exemplo, *Report.ReadWrite.All*. |
|Acesso ao serviço Power BI |Não pode aceder ao serviço Power BI com um *principal de serviço*.|Pode aceder ao serviço Power BI com as suas credenciais de *utilizador principal*.|
|Licença     |Não é necessária uma licença Pro. Pode utilizar conteúdos de qualquer área de trabalho da qual seja membro ou administrador.         |É necessária uma licença do [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md).         |

## <a name="step-2---register-an-azure-ad-application"></a>Passo 2 – Registe uma aplicação do Azure AD

Registar a sua aplicação no Azure AD permite-lhe:
> [!div class="checklist"]
>* Estabelecer uma identidade para a sua aplicação
>* Permitir que a sua aplicação aceda às [APIs REST do Power BI](/rest/api/power-bi/)
>* Se estiver a utilizar um *utilizador principal* – especificar as [permissões REST do Power BI](/azure/active-directory/develop/v2-permissions-and-consent) da sua aplicação

Para registar a sua aplicação no Azure AD, siga as instruções em [Registar a sua aplicação](register-app.md).

>[!NOTE]
>Antes de registar a sua aplicação, terá de decidir que método de autenticação utilizar: *principal de serviço* ou *utilizador principal*.

## <a name="step-3---create-a-power-bi-workspace"></a>Passo 3 – Crie uma área de trabalho do Power BI

O Power BI guarda os seus relatórios, dashboards e mosaicos numa área de trabalho. Para incorporar estes itens, terá de os criar e carregar para uma área de trabalho.

>[!TIP]
>Se já tiver uma área de trabalho, pode ignorar este passo.

Para criar uma área de trabalho, faça o seguinte:

1. Inicie sessão no Power BI.

2. Selecione **Áreas de Trabalho**.

3. Selecione **Criar uma área de trabalho**.

4. Dê um nome à sua área de trabalho e selecione **Guardar**.

## <a name="step-4---create-and-publish-a-power-bi-report"></a>Passo 4 – Crie e publique um relatório do Power BI

O seu próximo passo é criar um relatório e carregá-lo para a sua área de trabalho. Pode [criar o seu próprio relatório](/power-bi/fundamentals/desktop-getting-started#build-reports) através do Power BI Desktop e [publicá-lo](/powerbi-docs/fundamentals/desktop-getting-started#share-your-work) na sua área de trabalho. Em alternativa, pode carregar um relatório de amostra para a sua área de trabalho.

>[!Tip]
>Se já tiver uma área de trabalho com um relatório, pode ignorar este passo.

Para transferir um relatório de amostra e publicá-lo na sua área de trabalho, siga estes passos:

1. Abra a pasta [Power BI Desktop samples](https://github.com/Microsoft/PowerBI-Desktop-Samples) (Amostras para o Power BI Desktop) no GitHub.

2. Selecione **Code** (Código) e, em seguida, selecione **Download zip** (Transferir pasta zip).

    :::image type="content" source="media/embed-sample-for-customers/download-sample-report.png" alt-text="Captura de ecrã a mostrar a opção de transferência de pasta ZIP no GitHub com as amostras para o Power BI Desktop":::

3. Extraia o ZIP transferido e navegue para a pasta **Samples Reports** (Relatórios de Amostra).

4. Selecione um relatório para incorporar e [publique-o](/powerbi-docs/fundamentals/desktop-getting-started#share-your-work) na sua área de trabalho.

## <a name="step-5---get-the-embedding-parameter-values"></a>Passo 5 – Obtenha os valores de parâmetros de incorporação

Para incorporar os conteúdos, terá de obter determinados valores de parâmetro. A tabela abaixo mostra os valores obrigatórios e indica se são aplicáveis ao método de autenticação *principal de serviço* ou ao *utilizador principal* ou a ambos.

Antes de incorporar os conteúdos, certifique-se de que tem todos os valores listados abaixo. Alguns dos valores serão diferentes consoante o método de autenticação que estiver a utilizar.

|Parâmetro   |Service principal (Principal de serviço)   |Master user (Utilizador principal)  |
|-------------------|---|---|
|[ID de Cliente](#client-id) |![Aplica-se a:](../../media/yes.png) |![Aplica-se a:](../../media/yes.png) |
|[ID da Área de Trabalho](#workspace-id)     |![Aplica-se a:](../../media/yes.png) |![Aplica-se a:](../../media/yes.png) |
|[ID do Relatório](#report-id)           |![Aplica-se a:](../../media/yes.png) |![Aplica-se a:](../../media/yes.png) |
|[Segredo do cliente](#client-secret) |![Aplica-se a:](../../media/yes.png) |![Não se aplica a:](../../media/no.png) |
|[ID do inquilino](#tenant-id)                 |![Aplica-se a:](../../media/yes.png) |![Não se aplica a:](../../media/no.png) |
|[Nome de utilizador do Power BI](#power-bi-username-and-password)   |![Não se aplica a:](../../media/no.png) |![Aplica-se a:](../../media/yes.png) |
|[Palavra-passe do Power BI](#power-bi-username-and-password)   |![Não se aplica a:](../../media/no.png) |![Aplica-se a:](../../media/yes.png) |

### <a name="client-id"></a>ID de Cliente

>[!TIP]
>**Aplica-se a:** ![Aplica-se a: ](../../media/yes.png)Principal de serviço![Aplica-se a: ](../../media/yes.png)Utilizador principal

Para obter o GUID do ID do cliente (também denominado *ID da aplicação*), siga estes passos:

1. Inicie sessão no [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Procure **Registos de aplicações** e selecione a ligação **Registos de aplicações**.

3. Selecione a aplicação do Azure AD que está a utilizar para incorporar os seus conteúdos do Power BI.

4. Na secção **Descrição Geral**, copie o GUID **ID de aplicação (cliente)** .

### <a name="workspace-id"></a>ID da área de trabalho

>[!TIP]
>**Aplica-se a:** ![Aplica-se a: ](../../media/yes.png)Principal de serviço![Aplica-se a: ](../../media/yes.png)Utilizador principal

Para obter o GUID do ID da área de trabalho, siga estes passos:

1. Inicie sessão no serviço Power BI.

2. Abra o relatório que quer incorporar.

3. Copie o GUID do URL. O GUID é o número entre **/groups/** e **/reports/** .

    :::image type="content" source="media/embed-sample-for-customers/workspace-id.png" alt-text="Captura de ecrã a mostrar o GUID do ID da área de trabalho no URL do serviço Power BI":::

### <a name="report-id"></a>ID do Relatório

>[!TIP]
>**Aplica-se a:** ![Aplica-se a: ](../../media/yes.png)Principal de serviço![Aplica-se a: ](../../media/yes.png)Utilizador principal

1. Inicie sessão no serviço Power BI.

2. Abra o relatório que quer incorporar.

3. Copie o GUID do URL. O GUID é o número entre **/reports/** e **/ReportSection**.

    :::image type="content" source="media/embed-sample-for-customers/report-id.png" alt-text="Captura de ecrã a mostrar o GUID do ID do relatório no URL do serviço Power BI":::

### <a name="client-secret"></a>Segredo do cliente

>[!TIP]
>**Aplica-se a:** ![Aplica-se a: ](../../media/yes.png)Principal de serviço ![Não se aplica a: ](../../media/no.png)Utilizador principal

Para obter o segredo do cliente, siga estes passos:

1. Inicie sessão no [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Procure **Registos de aplicações** e selecione a ligação **Registos de aplicações**.

3. Selecione a aplicação do Azure AD que está a utilizar para incorporar os seus conteúdos do Power BI.

4. Em **Gerir**, selecione **Certificados e segredos**.

5. Em **Segredos do cliente**, selecione **Novo segredo do cliente**.

6. Na janela de pop-up **Adicionar um segredo de cliente**, forneça uma descrição para o seu segredo da aplicação, selecione quando o segredo da aplicação expira e selecione **Adicionar**.

7. Na secção **Segredos do cliente**, copie a cadeia na coluna **Valor** do segredo da aplicação criado recentemente. O valor do segredo do cliente é o seu *ID do cliente*.

### <a name="tenant-id"></a>ID do inquilino

>[!TIP]
>**Aplica-se a:** ![Aplica-se a: ](../../media/yes.png)Principal de serviço ![Não se aplica a: ](../../media/no.png)Utilizador principal

Para obter o GUID do ID do inquilino, siga estes passos:

1. Inicie sessão no [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Procure **Registos de aplicações** e selecione a ligação **Registos de aplicações**.

3. Selecione a aplicação do Azure AD que está a utilizar para incorporar os seus conteúdos do Power BI.

4. Na secção **Descrição geral**, copie o GUID do **ID do diretório (inquilino)** .

### <a name="power-bi-username-and-password"></a>Nome de utilizador e palavra-passe do Power BI

>[!TIP]
>**Aplica-se a:** ![Não se aplica a: ](../../media/no.png)Principal de serviço ![Aplica-se a: ](../../media/yes.png)Utilizador principal

Obtenha o *nome de utilizador* e *palavra-passe* do utilizador do Power BI que está a utilizar como **utilizador principal**. Este é o mesmo utilizador que utilizou para criar uma área de trabalho e carregar um relatório para a mesma, no serviço Power BI.

## <a name="step-6---service-principal-api-access"></a>Passo 6 – Conceda acesso de API ao principal de serviço

>[!TIP]
>**Aplica-se a:** ![Aplica-se a: ](../../media/yes.png)Principal de serviço ![Não se aplica a: ](../../media/no.png)Utilizador principal
>
>Este passo só é relevante se estiver a utilizar o método de autenticação *principal de serviço*. Se estiver a utilizar um *utilizador principal*, ignore este passo e continue com o [Passo 7 – Permita o acesso à área de trabalho](#step-7---enable-workspace-access).

Para que uma aplicação do AAD possa aceder aos conteúdos e APIs do Power BI, o administrador do Power BI tem de permitir o acesso do principal de serviço no portal de administração do Power BI. Se não for o administrador do seu inquilino, peça ao mesmo para ativar as *Definições de inquilino* para si.
        
1. No *serviço Power BI*, selecione **Definições** > **Definições** > **Portal de administração**.
        
    :::image type="content" source="media/embed-sample-for-customers/admin-settings.png" alt-text="Captura de ecrã a mostrar a opção de menu Definições de administrador no menu Definições do serviço Power BI":::
        
2. Selecione **Definições de inquilino** e desloque para baixo até à secção **Definições de programador**.
        
3. Expanda **Permitir que os principais de serviço utilizem as APIs do Power BI** para ativar esta opção.
        
    :::image type="content" source="media/embed-sample-for-customers/developer-settings.png" alt-text="Captura de ecrã a mostrar como ativar a opção Definições de programador na opção do menu Definições de inquilino no serviço Power BI":::
        
>[!NOTE]
>Ao utilizar um *principal de serviço*, é recomendado limitar o respetivo acesso às definições de inquilino através de um *grupo de segurança*. Para saber mais sobre esta funcionalidade, veja estas secções no artigo sobre [principais de serviço](embed-service-principal.md):
> * [Criar um grupo de segurança do Azure AD](embed-service-principal.md#step-2---create-an-azure-ad-security-group)
>* [Ativar as definições de administração do serviço Power BI](embed-service-principal.md#step-3---enable-the-power-bi-service-admin-settings)

## <a name="step-7---enable-workspace-access"></a>Passo 7 – Permita o acesso à área de trabalho

Para permitir que a aplicação do Azure AD aceda a artefactos como relatórios, dashboards e conjuntos de dados no serviço Power BI, adicione o *principal de serviço* ou *utilizador principal* como *membro* ou *administrador* à área de trabalho.

1. Inicie sessão no serviço Power BI.

2. Navegue para a área de trabalho à qual quer permitir o acesso e, no menu **Mais**, selecione **Acesso à área de trabalho**.

    :::image type="content" source="media/embed-service-principal/workspace-access.png" alt-text="Captura de ecrã a mostrar o botão de acesso da área de trabalho no menu mais de uma área de trabalho do Power BI.":::

3. No painel **Acesso**, consoante o método de autenticação que estiver a utilizar, copie o *principal de serviço* ou *utilizador principal* para a caixa de texto **Introduzir endereço de e-mail**.

    >[!NOTE]
    >Se for um *principal de serviço*, o nome é o que deu à sua aplicação do Azure AD.

5. Selecione **Adicionar**.

## <a name="step-8---embed-your-content"></a>Passo 8 – Incorpore os conteúdos

A aplicação de amostra do Power BI Embedded permite-lhe criar uma aplicação do Power BI *Embed for your customers* (Incorporar para os seus clientes).

Siga estes passos para modificar a aplicação de amostra *Embed for your customers* (Incorporar para os seus clientes), para incorporar o seu relatório do Power BI.  

1. Abra a pasta [Power BI developer samples](https://github.com/microsoft/PowerBI-Developer-Samples) (Amostras para programadores do Power BI).

2. Selecione **Code** (Código) e, em seguida, selecione **Download zip** (Transferir pasta zip).

    :::image type="content" source="media/embed-sample-for-customers/developer-samples.png" alt-text="Captura de ecrã a mostrar a opção de transferência de pasta ZIP no GitHub com as amostras para programadores do Power BI":::

3. Extraia o ZIP transferido e navegue até à pasta **PowerBI-Developer-Samples-master**.

4. Consoante a linguagem que pretende que a aplicação utilize, abra uma das seguintes pastas:

* .NET Core
* .NET Framework
* Java
* Node JS
* Python
    >[!NOTE]
    >A aplicação de amostra *Embed for your customers* (Incorporar para os seus clientes) só suporta as linguagens listadas acima. A aplicação de amostra *React TS* só suporta a solução *[incorporar para a sua organização](embed-sample-for-your-organization.md)* .

5. Abra a pasta **Embed for your customers** (Incorporar para os seus clientes).

# <a name="net-core"></a>[.NET Core](#tab/net-core)

6. Abra a *aplicação de amostra Embed for your customers* (Incorporar para os seus clientes) através de um destes métodos:

    * Se estiver a utilizar o [Visual Studio](https://visualstudio.microsoft.com/), abra o ficheiro **AppOwnsData.sln**.

    * Se estiver a utilizar o [Visual Studio Code](https://code.visualstudio.com/), abra a pasta **App Owns Data** (A Aplicação Detém os Dados).

7. Abra **appsettings.json**.

8. Consoante o seu método de autenticação, preencha os seguintes valores de parâmetro:

    |Parâmetro            |Service principal (Principal de serviço)  |Master user (Utilizador principal)  |
    |---------------------|---------|---------|
    |`AuthenticationMode` |ServicePrincipal         |MasterUser         |
    |`ClientId`           |O seu [ID de cliente](#client-id) da aplicação do Azure AD         |O seu [ID de cliente](#client-id) da aplicação do Azure AD         |
    |`TenantId`           |O seu [ID de inquilino](#tenant-id) do Azure AD         |N/D         |
    |`PbiUsername`        |N/D         |O seu nome de utilizador de *utilizador principal*. Veja [Nome de utilizador e palavra-passe do Power BI](#power-bi-username-and-password)         |
    |`PbiPassword`        |N/D         |A sua palavra-passe de *utilizador principal*. Veja [Nome de utilizador e palavra-passe do Power BI](#power-bi-username-and-password)         |
    |`ClientSecret`       |O seu [segredo de cliente](#client-secret) do Azure AD         |N/D         |
    |`WorkspaceId`        |O ID da área de trabalho com o seu relatório incorporado. Veja [ID da Área de Trabalho](#workspace-id)          |O ID da área de trabalho com o seu relatório incorporado. Veja [ID da Área de Trabalho](#workspace-id)         |
    |`ReportId`           |O ID do relatório que está a incorporar. Veja [ID do Relatório](#report-id)            |O ID do relatório que está a incorporar. Veja [ID do Relatório](#report-id)         |

9. Execute o projeto ao selecionar a opção adequada:

    * Se estiver a utilizar o **Visual Studio**, selecione **IIS Express (play)** (IIS Express [reproduzir]).

    * Se estiver a utilizar o **Visual Studio Code**, selecione **Run > Start Debugging** (Executar > Iniciar Depuração).

# <a name="net-framework"></a>[.NET Framework](#tab/net-framework)

6. No [Visual Studio](https://visualstudio.microsoft.com/), abra o ficheiro **AppOwnsData.sln**.

7. Abra **Web.config**.

8. Consoante o seu método de autenticação, preencha os seguintes valores de parâmetro:

    |Parâmetro            |Service principal (Principal de serviço)  |Master user (Utilizador principal)  |
    |---------------------|---------|---------|
    |`authenticationType` |ServicePrincipal         |MasterUser         |
    |`applicationId`           |O seu [ID de cliente](#client-id) da aplicação do Azure AD         |O seu [ID de cliente](#client-id) da aplicação do Azure AD         |
    |`workspaceId`        |O ID da área de trabalho com o seu relatório incorporado. Veja [ID da Área de Trabalho](#workspace-id)          |O ID da área de trabalho com o seu relatório incorporado. Veja [ID da Área de Trabalho](#workspace-id)         |
    |`reportId`           |O ID do relatório que está a incorporar. Veja [ID do Relatório](#report-id)            |O ID do relatório que está a incorporar. Veja [ID do Relatório](#report-id)         |
    |`pbiUsername`        |N/D         |O seu nome de utilizador de *utilizador principal*. Veja [Nome de utilizador e palavra-passe do Power BI](#power-bi-username-and-password)         |
    |`pbiPassword`        |N/D         |A sua palavra-passe de *utilizador principal*. Veja [Nome de utilizador e palavra-passe do Power BI](#power-bi-username-and-password)         |
    |`applicationSecret`       |O seu [segredo de cliente](#client-secret) do Azure AD         |N/D         |
    |`tenant`           |O seu [ID de inquilino](#tenant-id) do Azure AD         |N/D         |

9. Execute o projeto ao selecionar **IIS Express (play)** (IIS Express [reproduzir]).

>[!NOTE]
>Se não vir um relatório incorporado ao executar a aplicação de amostra, atualize os pacotes do Power BI ao seguir estes passos:
>1. Clique com o botão direito do rato no nome do projeto (AppOwnsData) e selecione **Manage NuGet packages** (Gerir pacotes NuGet).
>2. Procure a opção **Power BI JavaScript** (JavaScript do Power BI) e reinstale o pacote.
>
>Para obter mais informações, veja [Como reinstalar e atualizar pacotes](/nuget/consume-packages/reinstalling-and-updating-packages).

# <a name="java"></a>[Java](#tab/java)

6. Abra o **Eclipse** e siga as instruções descritas abaixo.

    >[!NOTE]
    >As instruções para Java para a *aplicação de amostra Embed for your customers* (Incorporar para os seus clientes), são referentes ao [Eclipse IDE for Java EE Developers](https://www.eclipse.org/downloads/packages/) (edição empresarial). Se estiver a utilizar outra aplicação, terá de a configurar autonomamente.

7. Adicione o servidor do Tomcat ao Eclipse:

    a. Selecione **Window** (Janela)  > **Show View** (Mostrar Vista)  > **Servers** (Servidores).

    b. No separador Servers (Servidores), selecione **No servers are available. Click this link to create new server** (Não existem servidores disponíveis. Clique nesta ligação para criar um novo servidor).

    c. Na janela **Define a New Server** (Definir um Novo Servidor), expanda **Apache** e selecione o servidor do Tomcat que está a executar na máquina. Por exemplo, *Tomcat v9.0 Server*.

    d. Selecione **Seguinte**.

    e. Na janela **Tomcat Server** (Servidor do Tomcat), selecione **Browse** (Procurar) e navegue para a pasta que contém o servidor do Tomcat.

    f. Na janela **Tomcat Server** (Servidor do Tomcat), selecione **Installed JREs** (JREs Instalados).

    exemplo, Na janela **Installed JREs** (JREs Instalados), selecione o *jre* disponível e selecione **Apply and Close** (Aplicar e Fechar).

    h. Na janela **Tomcat Server** (Servidor do Tomcat), selecione **Finish** (Concluir). Agora verá o servidor do Tomcat no separador *Servers* (Servidores).

8. Abra o projeto no Eclipse:

    >[!IMPORTANT]
    >O Eclipse poderá deparar-se com problemas se o nome do caminho for demasiado longo. Para evitar este problema, verifique que a pasta da aplicação de amostra não se encontra numa localização demasiado profunda na estrutura de pastas da máquina.

    a. Selecione **File** (Ficheiro) e, em seguida, selecione **Open Projects from File System** (Abrir Projetos a Partir do Sistema de Ficheiros).

    b. Na janela **Import Projects from File System or Archive** (Importar Projetos a Partir do Sistema de Ficheiros ou Arquivo), selecione **Directory** (Diretório) e abra a pasta **AppOwnsData**.

    c. Selecione **Concluir**.

9. Adicione o servidor do Tomcat ao projeto:

    a. No painel **Package Explorer** (Explorador de Pacotes), clique com o botão direito do rato em **AppOwnsData** e selecione **Properties** (Propriedades).

    b. Na janela **Properties for AppOwnsData**(Propriedades de AppOwnsData), selecione **Targeted Runtimes** (Tempos de Execução Direcionados) e selecione **Apache Tomcat**. Esta seleção irá incluir a versão do *Apache Tomcat* que está a utilizar, por exemplo, *Apache Tomcat v9.0*.

    c. Selecione **Apply and Close**  (Aplicar e Fechar).

10. Preencha os parâmetros necessários

    a. No **Package explorer** (Explorador de Pacotes), expanda o projeto **AppOwnsData**.

    b. Expanda **Java Resources** (Recursos Java).

    c. Expanda **src**.

    d. Expanda **com.embedsample.appoensdata.config**.

    e. Abra **Config.java**.

    f. Consoante o seu método de autenticação, preencha os seguintes valores de parâmetro:

    |Parâmetro            |Service principal (Principal de serviço)  |Master user (Utilizador principal)  |
    |---------------------|---------|---------|
    |`authenticationType` |ServicePrincipal         |MasterUser         |
    |`workspaceId`        |O ID da área de trabalho com o seu relatório incorporado. Veja [ID da Área de Trabalho](#workspace-id)          |O ID da área de trabalho com o seu relatório incorporado. Veja [ID da Área de Trabalho](#workspace-id)         |
    |`reportId`           |O ID do relatório que está a incorporar. Veja [ID do Relatório](#report-id)            |O ID do relatório que está a incorporar. Veja [ID do Relatório](#report-id)         | 
    |`clientId`           |O seu [ID de cliente](#client-id) da aplicação do Azure AD         |O seu [ID de cliente](#client-id) da aplicação do Azure AD         |
    |`pbiUsername`        |N/D         |O seu nome de utilizador de *utilizador principal*. Veja [Nome de utilizador e palavra-passe do Power BI](#power-bi-username-and-password)         |
    |`pbiPassword`        |N/D         |A sua palavra-passe de *utilizador principal*. Veja [Nome de utilizador e palavra-passe do Power BI](#power-bi-username-and-password)         |
    |`tenantId`           |O seu [ID de inquilino](#tenant-id) do Azure AD         |N/D         |
    |`appSecret`       |O seu [segredo de cliente](#client-secret) do Azure AD         |N/D         |

11. Executar o projeto

    a. No **Package Explorer** (Explorador de Pacotes), clique com o botão direito do rato em **AppOwnsData**.

    b. Selecione **Run As** (Executar Como)   > **Run on Server** (Executar no Servidor).

    c. Na janela **Run on Server** (Executar no Servidor), selecione **Choose an existing server** (Selecionar um servidor existente) e selecione o servidor *Tomcat*.

    d. Selecione **Concluir**.

# <a name="node-js"></a>[Node JS](#tab/node-js)

6. Abra a pasta **App Owns Data** (A Aplicação Detém os Dados) com o seu IDE preferencial. Recomendamos a utilização de um dos seguintes:

    * [Visual Studio](https://visualstudio.microsoft.com/)

    * [Visual Studio Code](https://code.visualstudio.com/)

7. Abra um terminal e instale as dependências obrigatórias ao executar: `npm install`.

8. Expanda a pasta **Config** (Configuração) e abra **config.json**.

9. Consoante o seu método de autenticação, preencha os seguintes valores de parâmetro:

    |Parâmetro            |Service principal (Principal de serviço)  |Master user (Utilizador principal)  |
    |---------------------|---------|---------|
    |`authenticationMode` |ServicePrincipal         |MasterUser         |
    |`clientId`           |O seu [ID de cliente](#client-id) da aplicação do Azure AD         |O seu [ID de cliente](#client-id) da aplicação do Azure AD         |
    |`workspaceId`        |O ID da área de trabalho com o seu relatório incorporado. Veja [ID da Área de Trabalho](#workspace-id)          |O ID da área de trabalho com o seu relatório incorporado. Veja [ID da Área de Trabalho](#workspace-id)         |
    |`reportId`           |O ID do relatório que está a incorporar. Veja [ID do Relatório](#report-id)            |O ID do relatório que está a incorporar. Veja [ID do Relatório](#report-id)         |
    |`pbiUsername`        |N/D         |O seu nome de utilizador de *utilizador principal*. Veja [Nome de utilizador e palavra-passe do Power BI](#power-bi-username-and-password)         |
    |`pbiPassword`        |N/D         |A sua palavra-passe de *utilizador principal*. Veja [Nome de utilizador e palavra-passe do Power BI](#power-bi-username-and-password)         |
    |`clientSecret`       |O seu [segredo de cliente](#client-secret) do Azure AD         |N/D         |
    |`tenantId`           |O seu [ID de inquilino](#tenant-id) do Azure AD         |N/D         |

10. Execute o projeto ao fazer o seguinte:

    a. No terminal do IDE, execute `npm start`.

    b. Abra um novo separador no browser e navegue para `http://localhost:5300`.

# <a name="python"></a>[Python](#tab/python)

6. Abra o **PowerShell** ou a **Linha de Comandos**.

7. Confirme que está na pasta **Python** > **Embed for your customers** (Incorporar para os seus clientes) e que o ficheiro **requirements.txt** está na pasta e execute `pip3 install -r requirements.txt`.

8. Abra a pasta **App Owns Data** (A Aplicação Detém os Dados) com o seu IDE preferencial. Recomendamos a utilização de um dos seguintes:

    * [Visual Studio](https://visualstudio.microsoft.com/)

    * [Visual Studio Code](https://code.visualstudio.com/)

9. Abra **config.py**.

10. Consoante o seu método de autenticação, preencha os seguintes valores de parâmetro:

    |Parâmetro            |Service principal (Principal de serviço)  |Master user (Utilizador principal)  |
    |---------------------|---------|---------|
    |`AUTHENTICATION_MODE` |ServicePrincipal         |MasterUser         |
    |`WORKSPACE_ID`        |O ID da área de trabalho com o seu relatório incorporado. Veja [ID da Área de Trabalho](#workspace-id)          |O ID da área de trabalho com o seu relatório incorporado. Veja [ID da Área de Trabalho](#workspace-id)         |
    |`REPORT_ID`           |O ID do relatório que está a incorporar. Veja [ID do Relatório](#report-id)            |O ID do relatório que está a incorporar. Veja [ID do Relatório](#report-id)         |
    |`TENANT_ID`           |O seu [ID de inquilino](#tenant-id) do Azure AD         |N/D         |
    |`CLIENT_ID`           |O seu [ID de cliente](#client-id) da aplicação do Azure AD         |O seu [ID de cliente](#client-id) da aplicação do Azure AD         |
    |`CLIENT_SECRET`       |O seu [segredo de cliente](#client-secret) do Azure AD         |N/D         |
    |`POWER_BI_USER`        |N/D         |O seu nome de utilizador de *utilizador principal*. Veja [Nome de utilizador e palavra-passe do Power BI](#power-bi-username-and-password)         |
    |`POWER_BI_PASS`        |N/D         |A sua palavra-passe de *utilizador principal*. Veja [Nome de utilizador e palavra-passe do Power BI](#power-bi-username-and-password)         |

11. Guarde o ficheiro.

12. Execute o projeto ao fazer o seguinte:

    a. No **PowerShell** ou na **Linha de Comandos**, navegue até à pasta **Python** > **Embed for your customers** (Incorporar para os seus clientes)  > **AppOwnsData** e execute `flask run`.

    b. Abra um novo separador no browser e navegue para `http://localhost:5300`.

---

## <a name="developing-your-application"></a>Desenvolver a sua aplicação

Após configurar e executar a aplicação de amostra *Embed for your customers* (Incorporar para os seus clientes), pode começar a desenvolver a sua própria aplicação.

Quando estiver pronto, veja os requisitos para [passar para a fase de produção](move-to-production.md). Também precisará de uma [capacidade](embedded-capacity.md), pelo que deve ver o artigo sobre [planeamento de capacidades](embedded-capacity-planning.md) para compreender que SKU melhor se adequa às suas necessidades.


## <a name="next-steps"></a>Passos seguintes

> [!div class="nextstepaction"]
>[Mover para produção](move-to-production.md)

>[!div class="nextstepaction"]
>[Incorporar para a sua organização](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
>[Incorporar relatórios paginados para os seus clientes](embed-paginated-reports-customers.md)

> [!div class="nextstepaction"]
>[Embed paginated reports for your organization (Incorporar relatórios paginados para a sua organização)](embed-paginated-reports-organization.md)

>[!div class="nextstepaction"]
>[Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
