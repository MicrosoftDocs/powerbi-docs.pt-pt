---
title: Incorporar conteúdo do Power BI numa aplicação para os seus clientes
description: Saiba como integrar ou incorporar um relatório, dashboard ou mosaico numa aplicação Web com as APIs do Power BI para os seus clientes.
services: powerbi
author: markingmyname
ms.author: maghan
ms.date: 05/07/2018
ms.topic: tutorial
ms.service: powerbi
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 2d4fdee8d3e4cca60294acd0a9167da1f048afa5
ms.sourcegitcommit: 9fa954608e78dcdb8d8a503c3c9b01c43ca728ab
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/11/2018
ms.locfileid: "34051939"
---
# <a name="tutorial-embed-a-power-bi-report-dashboard-or-tile-into-an-application-for-your-customers"></a>Tutorial: incorporar um relatório, dashboard ou mosaico do Power BI numa aplicação para os seus clientes
Com o **Power BI Embedded no Azure**, pode incorporar relatórios, dashboards ou mosaicos numa aplicação, para que os seus clientes possam partilhar dados. Geralmente, trata-se de um cenário de **programador ISV** com uma estrutura **os dados pertencem à aplicação**. **Os dados pertencem à aplicação** significa incorporar conteúdo do Power BI para os seus clientes. Por exemplo, o utilizador do conteúdo do Power BI pode visualizar relatórios, dashboards ou mosaicos sem ter de iniciar sessão no **Power BI**. Este tutorial demonstra como integrar ou incorporar um relatório numa aplicação com o .NET SDK do **Power BI** em conjunto com a API de JavaScript do **Power BI** quando utilizar o **Power BI Embedded no Azure** para os seus clientes com a estrutura **os dados pertencem à aplicação**.

Neste tutorial, vai aprender a:
>[!div class="checklist"]
>* Registe uma aplicação no Azure.
>* Incorpore um relatório, dashboard ou mosaico numa aplicação com o Power BI Embedded no Azure.

## <a name="prerequisites"></a>Pré-requisitos
Para começar, precisa de uma conta do **Power BI Pro** e uma conta do **Microsoft Azure**.

* Se não estiver inscrito no **Power BI Pro**, [inscreva-se para uma avaliação gratuita](https://powerbi.microsoft.com/en-us/pricing/) antes de começar.
* Se não tiver uma subscrição do Azure, crie uma [conta gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) antes de começar.
* Tem de ter a sua própria configuração de [inquilino do Azure Active Directory](create-an-azure-active-directory-tenant.md).
* Precisa do [Visual Studio](https://www.visualstudio.com/) instalado (versão 2013 ou posterior).

## <a name="setup-your-embedded-analytics-development-environment"></a>Configurar o ambiente de desenvolvimento de análise incorporado

Antes de começar a incorporar relatórios, dashboards ou mosaicos na sua aplicação, deve certificar-se de que o ambiente está configurado para permitir a incorporação. Como parte da configuração, terá de fazer o seguinte.

### <a name="register-an-application-in-azure-active-directory-azure-ad"></a>Registar uma aplicação no Azure Active Directory (Azure AD)

Pode registar a aplicação com o Azure Active Directory para permitir que a aplicação aceda às APIs REST do Power BI. Este procedimento permite-lhe estabelecer uma identidade para a sua aplicação e especificar permissões para recursos REST do Power BI.

1. Aceite os [Termos da API do Microsoft Power BI](https://powerbi.microsoft.com/api-terms).

2. Inicie sessão no [portal do Azure](https://portal.azure.com).
 
    ![Portal do Azure Principal](media/embed-sample-for-customers/embed-sample-for-customers-002.png)

3. No painel de navegação esquerdo, escolha **Todos os Serviços**, selecione **Registos de Aplicação** e, em seguida, selecione **Novo registo de aplicação**.
   
    ![Pesquisa de registo de aplicações](media/embed-sample-for-customers/embed-sample-for-customers-003.png)</br>
    ![Registo de nova aplicação](media/embed-sample-for-customers/embed-sample-for-customers-004.png)

4. Siga as instruções e crie uma nova aplicação. Para estruturas “os dados pertencem à aplicação”, tem de utilizar **Nativo** para o tipo de aplicação. Também precisa de um **URI de Redirecionamento**, que o **Azure AD** utiliza para devolver respostas de token. Introduza um valor específico na aplicação (por exemplo: http://localhost:13526/redirect).

    ![Criar Aplicação](media/embed-sample-for-customers/embed-sample-for-customers-005.png)

### <a name="apply-permissions-to-your-application-within-azure-active-directory"></a>Aplicar permissões à sua aplicação no Azure Active Directory

Terá de ativar permissões adicionais para a sua aplicação, além do que foi fornecido na página de registo de aplicações. Precisa de ter sessão iniciada com a conta *mestre* utilizada para incorporar, que tem de ser uma conta de administrador global.

### <a name="use-the-azure-active-directory-portal"></a>Utilizar o portal do Azure Active Directory

1. Navegue até aos [Registos de aplicação](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ApplicationsListBlade) no portal do Azure e selecione a aplicação que estiver a utilizar para incorporar.
   
    ![Escolher Aplicação](media/embed-sample-for-customers/embed-sample-for-customers-006.png)

2. Selecione **Definições** e, em **Acesso à API**, selecione **Permissões obrigatórias**.
   
    ![Permissões Obrigatórias](media/embed-sample-for-customers/embed-sample-for-customers-008.png)

3. Selecione **Windows Azure Active Directory** e, em seguida, certifique-se de que seleciona **Aceder ao diretório como o utilizador com sessão iniciada**. Selecione **Guardar**.
   
    ![Permissões do Microsoft Azure AD](media/embed-sample-for-customers/embed-sample-for-customers-011.png)

4. Selecione **Adicionar**.

    ![Adicionar Permissões](media/embed-sample-for-customers/embed-sample-for-customers-012.png)

5. Selecione **Selecionar uma API**.

    ![Adicionar Acesso à API](media/embed-sample-for-customers/embed-sample-for-customers-013.png)

6. Selecione **Serviço Power BI** e, em seguida, selecione **Selecionar**.

    ![Selecionar Serviços PBI](media/embed-sample-for-customers/embed-sample-for-customers-014.png)

7. Selecione todas as permissões em **Permissões Delegadas**. Terá de as selecionar uma a uma para guardar as seleções. Selecione **Guardar** quando terminar.
   
    ![Selecionar permissões delegadas](media/embed-sample-for-customers/embed-sample-for-customers-015.png)

8. Em **Permissões precisas**, selecione **Conceder Permissões**.
   
    A ação **Conceder Permissões** é precisa para a *conta mestra*, para evitar que lhe seja pedido consentimento pelo Azure AD. Se a conta que executa esta ação for de um Administrador Global, este irá conceder permissões a todos os utilizadores na sua organização para esta aplicação. Se a conta que realiza esta ação é a *conta mestra* e não for de um Administrador Global, este irá conceder permissões apenas à *conta mestra* para esta aplicação.
   
    ![Conceder permissões na caixa de diálogo de permissões precisas](media/embed-sample-for-customers/embed-sample-for-customers-016.png)

### <a name="create-your-power-bi-embedded-dedicated-capacity-in-azure"></a>Criar a sua capacidade dedicada Power BI Embedded no Azure

1. Inicie sessão no [portal do Azure](https://portal.azure.com).

    ![Portal do Azure Principal](media/embed-sample-for-customers/embed-sample-for-customers-002.png)

2. No painel de navegação à esquerda, escolha **Todos os Serviços** e selecione **Power BI Embedded**.

    ![Pesquisa de PBIE](media/embed-sample-for-customers/embed-sample-for-customers-017.png)

3. Siga as instruções e preencha as informações adequadas que são precisas para criar uma nova capacidade dedicada do **Power BI Embedded** e, em seguida, selecione **Criar**. Quando escolher o **Escalão de Preço**, reveja a tabela abaixo para decidir qual o escalão que melhor se adapta às suas necessidades. Em seguida, selecione **Criar** e aguarde que o recurso esteja concluído.

    ![Configuração de PBIE](media/embed-sample-for-customers/embed-sample-for-customers-018.png)

| Nó de Capacidade | Total de núcleos<br/>*(Back-end + front-end)* | Núcleos de Back-end | Núcleos de Front-end | Limites do DirectQuery/ligação em direto | Composição máxima de páginas em hora de ponta |
| --- | --- | --- | --- | --- | --- |
| A1 |1 núcleo virtual |.5 núcleos, 3 GB de RAM |.5 núcleos | 5 por segundo |1-300 |
| A2 |2 núcleos virtuais |1 núcleo, 5 GB de RAM |1 núcleo | 10 por segundo |301-600 |
| A3 |4 núcleos virtuais |2 núcleos, 10 GB de RAM |2 núcleos | 15 por segundo |601-1200 |
| A4 |8 núcleos virtuais |4 núcleos, 25 GB de RAM |4 núcleos |30 por segundo |1,201-2,400 |
| A5 |16 núcleos virtuais |8 núcleos, 50 GB de RAM |8 núcleos |60 por segundo |2,401-4,800 |
| A6 |32 núcleos virtuais |16 núcleos, 100 GB de RAM |16 núcleos |120 por segundo |4801-9600 |

Agora pode visualizar a nova **capacidade dedicada do Power BI Embedded**.

   ![Capacidade dedicada do PBIE](media/embed-sample-for-customers/embed-sample-for-customers-019.png)

## <a name="setup-your-power-bi-environment"></a>Configurar o ambiente do Power BI

### <a name="create-an-app-workspace"></a>Criar uma área de trabalho de aplicação

Se estiver a incorporar relatórios, dashboards ou mosaicos para os seus clientes, tem de colocar o conteúdo dentro de uma área de trabalho de aplicação. A conta *mestre* tem de ser um administrador da área de trabalho de aplicação.

1. Comece por criar a área de trabalho. Selecione **áreas de trabalho** > **Criar área de trabalho de aplicação**. Este será o local onde deve colocar o conteúdo ao qual a sua aplicação precisa de aceder.

    ![Criar Área de Trabalho](media/embed-sample-for-customers/embed-sample-for-customers-020.png)

2. Atribua um nome à área de trabalho. Se o **ID da área de trabalho** correspondente não estiver disponível, edite-o para obter um ID exclusivo. Este será também o nome da aplicação.

    ![Atribuir nome a Área de Trabalho](media/embed-sample-for-customers/embed-sample-for-customers-021.png)

3. Tem algumas opções a definir. Se optar por **Pública**, qualquer pessoa na sua organização pode ver o que está na área de trabalho. **Privada**, por outro lado, significa que apenas os membros da área de trabalho podem ver o respetivo conteúdo.

    ![Privada/Pública](media/embed-sample-for-customers/embed-sample-for-customers-022.png)

    Não é possível alterar a definição de pública/privada depois de criar o grupo.

4. Também pode escolher se os membros podem **editar** ou têm acesso **só de visualização**.

    ![Adicionar Membros](media/embed-sample-for-customers/embed-sample-for-customers-023.png)

5. Adicione os endereços de e-mail das pessoas que pretende que tenham acesso à área de trabalho e selecione **Adicionar**. Não é possível adicionar aliases de grupo, apenas indivíduos.

6. Decida se cada pessoa é um membro ou um administrador. Os administradores podem editar a área de trabalho, incluindo adicionar outros membros. Os membros podem editar o conteúdo da área de trabalho, a menos que tenham acesso só de visualização. Tanto os administradores como os membros podem publicar a aplicação.

7. Expanda **Avançadas**, ative **Capacidade dedicada** e, em seguida, selecione a **capacidade dedicada do Power BI Embedded** que criou. Em seguida, selecione **Guardar**.

    ![Adicionar Membros](media/embed-sample-for-customers/embed-sample-for-customers-024.png)

Agora pode visualizar a nova área de trabalho. O Power BI cria a área de trabalho e abre-a. É apresentada na lista de áreas de trabalho das quais é membro. Visto que é um administrador, pode selecionar as reticências (…) para voltar atrás e fazer alterações, adicionar novos membros ou alterar as respetivas permissões.

   ![Nova área de Trabalho](media/embed-sample-for-customers/embed-sample-for-customers-025.png)

### <a name="create-and-publish-your-reports"></a>Criar e publicar os seus relatórios

Pode criar os seus relatórios e conjuntos de dados com o Power BI Desktop e, em seguida, publicar esses relatórios numa área de trabalho de aplicação. O utilizador final que publica os relatórios tem de ter uma licença do Power BI Pro para poder publicar numa área de trabalho da aplicação.

1. Transfira o exemplo de [Demonstração no Blogue](https://github.com/Microsoft/powerbi-desktop-samples) a partir do GitHub.

    ![exemplo de relatório](media/embed-sample-for-customers/embed-sample-for-customers-026-1.png)

2. Abrir relatório PBIX de exemplo no **Power BI Desktop**

   ![Relatório do PBI Desktop](media/embed-sample-for-customers/embed-sample-for-customers-027.png)

3. Publicar na **área de trabalho da aplicação**

   ![Relatório do PBI Desktop](media/embed-sample-for-customers/embed-sample-for-customers-028.png)

    Agora, pode ver o relatório no serviço Power BI online

   ![Relatório do PBI Desktop](media/embed-sample-for-customers/embed-sample-for-customers-029.png)

## <a name="embed-your-content"></a>Incorporar o seu conteúdo

1. Transfira o [exemplo de estrutura Os Dados Pertencem à Aplicação](https://github.com/Microsoft/PowerBI-Developer-Samples) a partir do GitHub para começar.

    ![Exemplo de aplicação Os Dados Pertencem à Aplicação](media/embed-sample-for-customers/embed-sample-for-customers-026.png)

2. Abra o ficheiro Web.config da aplicação de exemplo. Existem 5 campos que terá de preencher para executar a aplicação com êxito. O **clientID**, o **groupId**, o **reportId**, o **pbiUsername** e o **pbiPassword**.

      ![Ficheiro Web Config](media/embed-sample-for-customers/embed-sample-for-customers-030.png)

    * Preencha as informações de **clientId** com o **ID da Aplicação** do **Azure**. O **clientId** serve para a aplicação se identificar aos utilizadores aos quais está a pedir permissões. Para obter o **clientId**, siga estes passos:

        1. Inicie sessão no [portal do Azure](https://portal.azure.com).

        ![Portal do Azure Principal](media/embed-sample-for-customers/embed-sample-for-customers-002.png)

        2. No painel de navegação à esquerda, escolha **Todos os Serviços** e selecione **Registos de Aplicação**.

        ![Pesquisa de registo de aplicações](media/embed-sample-for-customers/embed-sample-for-customers-003.png)
        3. Selecione a aplicação em que pretende obter o **clientId**.

        ![Escolher Aplicação](media/embed-sample-for-customers/embed-sample-for-customers-006.png)

      4. Deverá ver um **ID da Aplicação** que está listado como um GUID. Utilize este **ID da Aplicação** como o **clientId** para a aplicação.

        ![clientId](media/embed-sample-for-customers/embed-sample-for-customers-007.png)     

    * Preencha as informações do **groupId** com o **GUID da área de trabalho de aplicação** do Power BI.

        ![groupId](media/embed-sample-for-customers/embed-sample-for-customers-031.png)

    * Preencha as informações do **reportId** com o **GUID de relatório** do Power BI.

        ![reportId](media/embed-sample-for-customers/embed-sample-for-customers-032.png)    

    * Preencha o **pbiUsername** com o utilizador principal da conta do Power BI.
    * Preencha o **pbiPassword** com a palavra-passe do utilizador principal da conta do Power BI.

3. Execute a aplicação!

    Comece por selecionar **Executar** no **Visual Studio**.

    ![Executar a aplicação](media/embed-sample-for-customers/embed-sample-for-customers-033.png)

    Em seguida, selecione **Incorporar Relatório**. Consoante o conteúdo que optar por efetuar os testes – relatórios, dasboards ou mosaicos – selecione essa opção na aplicação.

    ![Selecionar um conteúdo](media/embed-sample-for-customers/embed-sample-for-customers-034.png)
 
    Agora pode visualizar o relatório na aplicação de exemplo.

    ![Visualizar aplicação](media/embed-sample-for-customers/embed-sample-for-customers-035.png)

Para obter um exemplo completo de utilização da API de JavaScript, pode utilizar a [ferramenta Playground](https://microsoft.github.io/PowerBI-JavaScript/demo). Esta é uma forma rápida de fazer experiências com vários tipos de exemplos de Power BI Embedded. Também pode obter mais informações sobre a API de JavaScript ao visitar a página da [wiki do PowerBI-JavaScript](https://github.com/Microsoft/powerbi-javascript/wiki).

Se tiver mais dúvidas sobre o Power BI Embedded, visite a página de [FAQ](embedded-faq.md).  Se estiver a ter problemas com o Power BI Embedded na sua aplicação, visite a página de [resolução de problemas](embedded-troubleshoot.md).

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/) 