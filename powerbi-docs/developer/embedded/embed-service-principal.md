---
title: Incorporar conteúdos do Power BI com o principal de serviço e um segredo da aplicação
description: Saiba como autenticar-se para obter análises incorporadas com um principal de serviço da aplicação do Azure Active Directory e um segredo da aplicação.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.custom: ''
ms.date: 10/15/2020
ms.openlocfilehash: 6f6a13f239d1bcfa7731361f4efcd129da7e2031
ms.sourcegitcommit: 1428acb6334649fc2d3d8ae4c42cfbc17e8f7476
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "92197748"
---
# <a name="embed-power-bi-content-with-service-principal-and-an-application-secret"></a>Incorporar conteúdos do Power BI com o principal de serviço e um segredo da aplicação

[!INCLUDE[service principal overview](../../includes/service-principal-overview.md)]

Este artigo descreve a autenticação do principal de serviço com o *ID da Aplicação* e o *Segredo da aplicação* .

>[!NOTE]
>Recomendamos que proteja os seus serviços de back-end com certificados, em vez de chaves secretas.
>* [Saiba mais sobre como obter tokens de acesso do Azure AD com chaves secretas ou certificados](/azure/architecture/multitenant-identity/client-assertion).
>* [Incorporar conteúdos do Power BI com o principal de serviço e um certificado](embed-service-principal-certificate.md).

## <a name="method"></a>Método

Para utilizar o principal de serviço e um ID da aplicação com a análise incorporada, siga estes passos:

1. Crie uma [aplicação do Azure Active Directory](/azure/active-directory/manage-apps/what-is-application-management).

    1. Crie o segredo da aplicação do AAD.
    
    2. Obtenha o *ID da Aplicação* e o *Segredo da aplicação* .

    >[!NOTE]
    >Estes passos são descritos no **passo 1** . Para obter mais informações sobre a criação de uma aplicação do AAD, veja o artigo [Criar uma aplicação do Azure Active Directory](/azure/active-directory/develop/howto-create-service-principal-portal).

2. Crie um grupo de segurança do AAD.

3. Ative as definições de administração do serviço Power BI.

4. Adicione o principal de serviço à área de trabalho.

5. Incorpore os conteúdos.

> [!IMPORTANT]
> Assim que ativar o principal de serviço a ser utilizado com o Power BI, as permissões do AD da aplicação deixarão de estar em vigor. Em seguida, as permissões da aplicação serão geridas através do portal de administração do Power BI.

## <a name="step-1---create-an-azure-ad-app"></a>Passo 1 – Criar uma aplicação do Azure Active Directory

Crie uma aplicação do AAD através de um destes métodos:

* Crie a aplicação no portal do [Microsoft Azure](https://portal.azure.com/#allservices)

* Crie a aplicação com o [PowerShell](/powershell/azure/create-azure-service-principal-azureps).

### <a name="creating-an-azure-ad-app-in-the-microsoft-azure-portal"></a>Criar uma aplicação do AAD no portal do Microsoft Azure

[!INCLUDE[service create app](../../includes/service-principal-create-app.md)]

7. Clique no separador **Certificados e segredos** .

     ![Uma captura de ecrã a mostrar o painel certificados e segredos de uma aplicação no portal do Azure.](media/embed-service-principal/certificates-and-secrets.png)


8. Clique em **Novo segredo do cliente**

    ![Uma captura de ecrã que mostra o botão novo segredo de cliente no painel certificados e segredos.](media/embed-service-principal/new-client-secret.png)

9. Na janela *Adicionar um segredo do cliente* , introduza uma descrição, especifique quando quer que o segredo do cliente expire e clique em **Adicionar** .

10. Copie e guarde o valor do *Segredo do cliente* .

    ![Uma captura de ecrã que mostra um valor secreto desfocado no painel de certificados e segredos.](media/embed-service-principal/client-secret-value.png)

    >[!NOTE]
    >Quando fechar esta janela, o valor do segredo do cliente será ocultado e não poderá vê-lo nem copiá-lo novamente.

### <a name="creating-an-azure-ad-app-using-powershell"></a>Criar uma aplicação do Azure Active Directory com o PowerShell

Esta secção inclui um script de exemplo para criar uma nova aplicação do AAD com o [PowerShell](/powershell/azure/create-azure-service-principal-azureps).

```powershell
# The app ID - $app.appid
# The service principal object ID - $sp.objectId
# The app key - $key.value

# Sign in as a user that's allowed to create an app
Connect-AzureAD

# Create a new Azure AD web application
$app = New-AzureADApplication -DisplayName "testApp1" -Homepage "https://localhost:44322" -ReplyUrls "https://localhost:44322"

# Creates a service principal
$sp = New-AzureADServicePrincipal -AppId $app.AppId

# Get the service principal key
$key = New-AzureADServicePrincipalPasswordCredential -ObjectId $sp.ObjectId
```
[!INCLUDE[service create steps two, three and four](../../includes/service-principal-create-steps.md)]

## <a name="step-5---embed-your-content"></a>Passo 5 – Incorporar os conteúdos

Pode incorporar os conteúdos numa aplicação de exemplo ou na sua própria aplicação.

* [Incorporar conteúdos com a aplicação de exemplo](embed-sample-for-customers.md#embed-content-using-the-sample-application)
* [Incorporar conteúdos na sua aplicação](embed-sample-for-customers.md#embed-content-within-your-application)

Uma vez incorporados os conteúdos, está pronto para [avançar para a produção](embed-sample-for-customers.md#move-to-production).

[!INCLUDE[service principal limitations](../../includes/service-principal-limitations.md)]

## <a name="next-steps"></a>Próximos passos

>[!div class="nextstepaction"]
>[Registar uma aplicação](register-app.md)

> [!div class="nextstepaction"]
>[Power BI Embedded para clientes](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Objetos do principal de serviço e aplicação no Azure Active Directory](/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[Segurança ao nível da linha com o gateway de dados no local com o principal de serviço](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)

>[!div class="nextstepaction"]
>[Incorporar conteúdos do Power BI com o principal de serviço e um certificado](embed-service-principal-certificate.md)