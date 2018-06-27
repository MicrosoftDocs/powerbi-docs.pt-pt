---
title: Resolução de problemas de aplicações incorporadas
description: Este artigo aborda alguns problemas comuns que poderá encontrar ao incorporar conteúdos do Power BI.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 04/23/2018
ms.author: maghan
ms.openlocfilehash: ad23161985cc2721562cfdfd9128e326db887ece
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/26/2018
ms.locfileid: "34813164"
---
# <a name="troubleshooting-your-embedded-application"></a>Resolução de problemas de aplicações incorporadas

Este artigo aborda alguns problemas comuns que poderá encontrar ao incorporar conteúdos do Power BI.

## <a name="tools-for-troubleshooting"></a>Ferramentas para resolução de problemas

### <a name="fiddler-trace"></a>Rastreio do Fiddler

[Fiddler](http://www.telerik.com/fiddler) é uma ferramenta gratuita da Telerik que monitoriza o tráfego HTTP.  Pode ver a comunicação com as APIs do Power BI do computador cliente. Isto pode mostrar erros e outras informações relacionadas.

![Rastreio do Fiddler](../includes/media/gateway-onprem-tshoot-tools-include/fiddler.png)

### <a name="f12-in-browser-for-front-end-debugging"></a>F12 no Browser para depuração em front-end

A tecla F12 abre a janela de programador no seu browser. Isto permite-lhe ver o tráfego de rede e outras informações.

![Depuração de Browser através de F12](media/embedded-troubleshoot/browser-f12.png)

### <a name="extracting-error-details-from-power-bi-response"></a>Extrair os detalhes do erro da resposta do Power BI

Este fragmento de código mostra como extrair os detalhes do erro de exceção de HTTP:

```
public static string GetExceptionText(this HttpOperationException exc)
{
    var errorText = string.Format("Request: {0}\r\nStatus: {1} ({2})\r\nResponse: {3}",
    exc.Request.Content, exc.Response.StatusCode, (int)exc.Response.StatusCode, exc.Response.Content);
    if (exc.Response.Headers.ContainsKey("RequestId"))
    {
        var requestId = exc.Response.Headers["RequestId"].FirstOrDefault();
        errorText += string.Format("\r\nRequestId: {0}", requestId);
    }

    return errorText;
}
```
Recomendamos que registe os ids do pedido (e os detalhes do erro na resolução de problemas).
Indique o id do pedido quando falar com o suporte da Microsoft.

## <a name="app-registration"></a>Registo de aplicações

**Falha de registo de aplicações**

As mensagens de erro no portal do Azure ou na página de registo da aplicação Power BI irão mencionar privilégios insuficientes. Para registar uma aplicação, tem de ser um administrador no inquilino do Azure AD ou os registos de aplicações têm de estar ativados para os utilizadores que não são utilizadores.

**O Serviço Power BI não aparece no portal do Azure ao registar uma nova Aplicação**

Pelo menos um utilizador tem de estar inscrito no Power BI. Se não vir o **Serviço Power BI** listado na lista de APIs, nenhum utilizador estará inscrito no Power BI.

## <a name="rest-api"></a>API REST

**O pedido de API devolve um erro 401**

Poderá ser necessária uma captura de fiddler para se investigar mais aprofundadamente. O âmbito de permissão necessário poderá estar em falta para a aplicação registada no Azure AD. Certifique-se de que o âmbito necessário está presente no registo de aplicações para o Azure AD no portal do Azure.

**O pedido de API devolve o erro 403**

Poderá ser necessária uma captura de fiddler para se investigar mais aprofundadamente. Poderá haver vários motivos para um erro 403.

* O utilizador excedeu a quantidade de tokens de incorporação que podem ser gerados numa capacidade partilhada. Precisa de comprar as capacidades do Azure para gerar tokens de incorporação e atribuir a área de trabalho a essa capacidade. Veja [Create Power BI Embedded capacity in the Azure portal](https://docs.microsoft.com/azure/power-bi-embedded/create-capacity) (Criar capacidade do Power BI Embedded no portal do Azure).
* O token de autenticação do Azure AD expirou.
* O utilizador autenticado não é um membro do grupo (área de trabalho de aplicação).
* O utilizador autenticado não é um administrador do grupo (área de trabalho de aplicação).
* O cabeçalho de autorização poderá não estar corretamente listado. Certifique-se de que não existem gralhas.

O back-end da aplicação poderá ter de atualizar o token de autenticação antes de chamar o GenerateToken.

```
    GET https://wabi-us-north-central-redirect.analysis.windows.net/metadata/cluster HTTP/1.1
    Host: wabi-us-north-central-redirect.analysis.windows.net
    ...
    Authorization: Bearer eyJ0eXAiOi...
    ...
 
    HTTP/1.1 403 Forbidden
    ...
     
    {"error":{"code":"TokenExpired","message":"Access token has expired, resubmit with a new access token"}}
```

**A geração de token falha ao fornecer identidade eficaz**

O GenerateToken pode falhar, com identidade eficaz fornecida, por vários motivos diferentes.

* O conjunto de dados não suporta a identidade em vigor
* O nome de utilizador não foi fornecido
* A função não foi fornecida
* O DatasetId não foi fornecido
* O utilizador não tem as permissões corretas

Para verificar qual é o motivo, experimente o seguinte.

* Execute a operação [obter conjunto de dados](https://docs.microsoft.com/rest/api/power-bi/datasets). A propriedade IsEffectiveIdentityRequired é verdadeira?
* O nome de utilizador é obrigatório para qualquer EffectiveIdentity.
* Se IsEffectiveIdentityRolesRequired for verdadeiro, é necessária uma Função.
* DatasetId é obrigatório para qualquer EffectiveIdentity.
* No Analysis Services, o utilizador principal tem de ser um administrador de gateway.

## <a name="data-sources"></a>Origens de dados

**O ISV pretende ter credenciais diferentes para a mesma origem de dados**

Uma origem de dados pode ter um único conjunto de credenciais para um utilizador principal. Se precisar de utilizar credenciais diferentes, crie utilizadores principais adicionais. Depois, atribua as diferentes credenciais em cada contexto do utilizador principal e incorpore através do token do Azure AD do utilizador.

## <a name="content-rendering"></a>Composição de conteúdos

**A composição ou o consumo de conteúdos incorporados falha ou o tempo expira**

Certifique-se de que o token de incorporação não expirou. Certifique-se de que está a verificar a expiração do token de incorporação e a atualizá-lo. Para obter mais informações, consulte [Refresh token using JavaScript SDK (Atualizar o token através do JavaScript SDK - em inglês)](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Refresh-token-using-JavaScript-SDK-example).

**O relatório ou o dashboard não carrega**

Se o utilizador não conseguir ver o relatório ou dashboard, certifique-se de que o relatório ou dashboard é devidamente carregado em powerbi.com. O relatório ou dashboard não funciona na sua aplicação se não for carregado em powerbi.com.

**O relatório ou dashboard tem um desempenho lento**

Abra o ficheiro no Power BI Desktop ou no powerbi.com e certifique-se de que o desempenho é aceitável para excluir problemas na sua aplicação ou nas APIs de incorporação.

## <a name="onboarding-experience-tool-for-embedding"></a>Ferramenta de experiência de inclusão para incorporar

Pode utilizar a [Ferramenta de experiência de inclusão](https://aka.ms/embedsetup) para transferir rapidamente uma aplicação de exemplo. Em seguida, pode comparar a sua aplicação com a de exemplo.

### <a name="prerequisites"></a>Pré-requisitos

Verifique se tem todos os pré-requisitos adequados antes de utilizar a Ferramenta de experiência de inclusão. Precisa de uma conta do **Power BI Pro** e de uma subscrição do **Microsoft Azure**.

* Se não estiver inscrito no **Power BI Pro**, [inscreva-se para uma avaliação gratuita](https://powerbi.microsoft.com/en-us/pricing/) antes de começar.
* Se não tiver uma subscrição do Azure, crie uma [conta gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) antes de começar.
* Tem de ter a sua própria configuração de [inquilino do Azure Active Directory](create-an-azure-active-directory-tenant.md).
* Precisa do [Visual Studio](https://www.visualstudio.com/) instalado (versão 2013 ou posterior).

### <a name="common-issues"></a>Problemas Comuns

Eis alguns problemas comuns com que se poderá deparar quando realizar testes com a Ferramenta de experiência de inclusão:

#### <a name="using-the-embed-for-your-customers-sample-application"></a>Utilização da aplicação de exemplo Incorporar para os seus clientes

Se estiver a trabalhar com a experiência **Incorporar para os seus clientes**, guarde e deszipe o ficheiro *PowerBI-Developer-Samples.zip*. Em seguida, abra a pasta *PowerBI-Developer-Samples-master\App Owns Data* e execute o ficheiro *PowerBIEmbedded_AppOwnsData.sln*.

Quando seleciona **Conceder permissões** (o passo Conceder permissões), obtém o seguinte erro:

    AADSTS70001: Application with identifier <client ID> was not found in the directory <directory ID>

A solução passa por fechar o pop-up, aguardar alguns segundos e tentar novamente. Poderá ter de repetir esta ação algumas vezes. O intervalo de tempo origina o problema desde a conclusão do processo de registo da aplicação até ao momento em que está disponível para APIs externas.

A seguinte mensagem de erro é apresentada quando a aplicação de exemplo é executada:

    Password is empty. Please fill password of Power BI username in web.config.

Este erro ocorre porque o único valor que não está a ser injetado na aplicação de exemplo é a sua palavra-passe de utilizador. Abra o ficheiro Web.config na solução e preencha o campo pbiPassword com a sua palavra-passe de utilizador.

#### <a name="using-the-embed-for-your-organization-sample-application"></a>Utilização da aplicação de exemplo Incorporar para a sua organização

Se estiver a trabalhar com a experiência **Incorporar para a sua organização**, guarde e deszipe o ficheiro *PowerBI-Developer-Samples.zip*. Em seguida, abra a pasta *PowerBI-Developer-Samples-master\User Owns Data\integrate-report-web-ap* e execute o ficheiro *pbi-saas-embed-report.sln*.

Quando executa a aplicação de exemplo **Incorporar para a sua organização**, obtém o seguinte erro:

    AADSTS50011: The reply URL specified in the request does not match the reply URLs configured for the application: <client ID>

Isto acontece porque o URL de redirecionamento especificado para a aplicação de servidor Web é diferente do URL do exemplo. Se quiser registar a aplicação de exemplo, utilize *http://localhost:13526/* como o URL de redirecionamento.

Se quiser editar a aplicação registada, saiba como editar a [aplicação registada no AAD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications#updating-an-application) para que a aplicação possa dar acesso às APIs Web.

Se quiser editar o seu perfil ou os seus dados de utilizador do Power BI, saiba como editar os seus [dados do Power BI](https://docs.microsoft.com/en-us/power-bi/service-basic-concepts).

Para obter mais informações, veja [Perguntas frequentes sobre o Power BI Embedded](embedded-faq.md).

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)