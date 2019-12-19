---
title: Comprar e atribuir licenças Power BI Pro
description: Saiba como comprar e atribuir licenças de utilizador do Power BI Pro, para que os utilizadores possam aceder aos conteúdos e colaborar com colegas no serviço Power BI.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: quickstart
ms.date: 10/29/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 55cdfad221aef276c790e98de83dd844bc13aafe
ms.sourcegitcommit: 320d83ab392ded71bfda42c5491acab3d9d357b0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/10/2019
ms.locfileid: "74958725"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Comprar e atribuir licenças de utilizador do Power BI Pro

O Power BI Pro é uma licença de utilizador individual que permite aos utilizadores ler e interagir com relatórios e dashboards que outros utilizadores publicaram no serviço Power BI e partilhar conteúdos e colaborar com outros utilizadores do Power BI Pro. Apenas os utilizadores com uma licença de utilizador do Power BI Pro podem publicar ou partilhar conteúdos com outros utilizadores ou consumir conteúdos criados por outros utilizadores, a menos que esses conteúdos estejam alojados numa capacidade Premium do Power BI. Para obter mais informações, veja a secção _Comparação das funcionalidades do Power BI_ na página [Preços do Power BI](https://powerbi.microsoft.com/pricing/).

## <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Comprar e atribuir licenças de utilizador do Power BI Pro

Este artigo explica como comprar licenças de utilizador do Power BI Pro no centro de administração do Microsoft 365 e, em seguida, explica duas opções que os administradores têm para atribuir essas licenças a utilizadores individuais: no centro de administração do Microsoft 365 e no portal do Azure (escolha uma opção).

### <a name="prerequisites"></a>Pré-requisitos

Para comprar e atribuir licenças no centro de administração do Microsoft 365, tem de ser membro da função de **[Administrador global ou Administrador de faturação](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)** no Microsoft 365.

Para atribuir licenças no portal do Azure, tem de ser um proprietário da subscrição do Azure que o Power BI utiliza para pesquisas do Azure Active Directory.

### <a name="purchase-licenses-in-microsoft-365"></a>Comprar licenças no Microsoft 365

Siga estes passos para comprar licenças do Power BI Pro no centro de administração do Microsoft 365:

1. Abra o [centro de administração do Microsoft 365](https://portal.office.com/adminportal/home#/homepage).

2. No painel de navegação, selecione **Faturação** > **Subscrições**.

    ![Painel de navegação](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-01.png)

3. No canto superior direito da página **Subscrições**, selecione **Adicionar subscrições**.

    ![Subscrição](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-02.png)

4. Localize a oferta de subscrição pretendida:

    Em **Enterprise Suite**, selecione **Office 365 Enterprise E5**.

    ![Subscrição do Office E5](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-03.png)

    Em **Outros Planos**, selecione **Power BI Pro**.

    ![Subscrição do Power BI](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-04.png)

5. Paire o rato sobre as reticências (**. . .**) na subscrição pretendida e selecione **Comprar agora**.

    ![Comprar Agora](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-05.png)

6. Selecione **Pagar mensalmente** ou **Pagar o ano completo** consoante a sua preferência de faturação.

7. Em **Quantos utilizadores pretende?**, introduza o número pretendido de licenças e, em seguida, selecione **Finalizar a compra agora** e conclua a transação.

8. Verifique se a subscrição obtida se encontra agora listada na página **Subscrições**.

   ![Subscrição adquirida](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-06.png)

9. Para adicionar mais licenças após a compra inicial, selecione **Power BI Pro** da página **Subscrições** e, em seguida, selecione **Adicionar/Remover licenças**.

### <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Atribuir licenças no centro de administração do Microsoft 365

Siga estes passos para atribuir licenças do Power BI Pro a contas de utilizador individuais:

1. Abra o [centro de administração do Microsoft 365](https://portal.office.com/adminportal/home#/homepage).

2. No painel de navegação, expanda **Utilizadores** e, em seguida, selecione **Utilizadores ativos**.

    ![Utilizadores ativos](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-05.png)

3. Selecione um utilizador e, em seguida, em **Licenças de produtos**, selecione **Editar**.

    ![Editar licenças de produtos](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-06.png)

4. Em **Power BI Pro**, altere a definição para **Ativado** e selecione **Guardar**.

    ![Licenças de produtos ativadas](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-07.png)

5. Para a conta selecionada, verifique em **Estado** se a licença do Power BI Pro foi atribuída com êxito.

    ![Verifique o estado da licença](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-08.png)

### <a name="assign-licenses-in-the-azure-portal"></a>Atribuir licenças no portal do Azure

Siga estes passos para atribuir licenças do Power BI Pro a contas de utilizador individuais:

1. Abra o [portal do Azure](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0).

2. No painel de navegação, selecione **Azure Active Directory**.

    ![Azure Active Directory](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-01.png)

3. Em **Azure Active Directory**, selecione **Licenças**.

    ![Licenças](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-02.png)

4. Em **Licenças**, clique em **Todos os produtos** e, em seguida, selecione **Power BI Pro** para apresentar a lista de utilizadores com licenças.

    ![Licenças – todos os produtos](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-03.png)

5. Selecione **Atribuir** para adicionar uma licença do Power BI Pro a uma conta de utilizador.

    ![Atribuir licença](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-04.png)

## <a name="next-steps"></a>Próximos passos

Agora que já atribuiu licenças, saiba mais sobre o Power BI Pro.

[Licenciamento do Power BI na sua organização](service-admin-licensing-organization.md)

[Encontrar utilizadores do Power BI que iniciaram sessão](service-admin-access-usage.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
