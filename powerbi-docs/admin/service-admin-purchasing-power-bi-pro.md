---
title: Comprar e atribuir licenças Power BI Pro
description: Saiba como comprar e atribuir licenças de utilizador do Power BI Pro aos utilizadores, para que possam aceder aos conteúdos e colaborar com outros no serviço Power BI.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 04/08/2020
ms.author: kfollis
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 899055ea26d1f36592c426ba402aa363b65bfa15
ms.sourcegitcommit: 0d0ab427bb71b37c9e5170c515a8f274e1f20c17
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2020
ms.locfileid: "87878347"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Comprar e atribuir licenças de utilizador do Power BI Pro

>[!IMPORTANT]
>Este artigo destina-se aos administradores. É um utilizador pronto para atualizar para uma licença do Power BI Pro? Aceda diretamente a [Introdução ao Power BI Pro](https://go.microsoft.com/fwlink/?LinkId=2106428&clcid=0x409&cmpid=pbidocs-purchasing-power-bi-pro) para configurar a sua conta.

O Power BI Pro é uma licença de utilizador individual que permite que os utilizadores leiam e interajam com relatórios e dashboards que outras pessoas publicaram no serviço Power BI. Os utilizadores com este tipo de licença podem partilhar conteúdos e colaborar com outros utilizadores do Power BI Pro. Apenas os utilizadores do Power BI Pro podem publicar ou partilhar conteúdos com outros utilizadores ou consumir conteúdos criados por outros, a menos que uma capacidade do Power BI Premium hospede esse conteúdo. Para obter mais informações sobre os tipos de licenças e subscrições disponíveis, veja [Licenciamento do Power BI na sua organização](service-admin-licensing-organization.md).

## <a name="purchase-power-bi-pro-user-licenses"></a>Comprar licenças de utilizador do Power BI Pro

Este artigo explica como comprar licenças de utilizador do Power BI Pro no centro de administração do Microsoft 365. Após comprar as licenças, pode atribuí-las aos utilizadores no centro de administração do Microsoft 365 ou no portal do Azure.

> [!NOTE]
> A partir de 14 de janeiro de 2020, as capacidades de gestão de licenças, subscrição e aquisição self-service para os produtos do Power Platform (Power BI, Power Apps e Power Automate) estão disponíveis para clientes da cloud comercial. Para obter mais informações, veja [Self-service purchase FAQ](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/self-service-purchase-faq) (FAQ da compra personalizada). Para ativar ou desativar as capacidades da compra personalizada, veja [Enable or disable self-service sign-up and purchasing](/power-bi/admin/service-admin-disable-self-service) (Ativar ou desativar a compra e a inscrição personalizadas).

### <a name="prerequisites"></a>Pré-requisitos

Para comprar e atribuir licenças no centro de administração do Microsoft 365, tem de ser membro da função de [administrador global ou Administrador de faturação](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d) no Microsoft 365.

Para atribuir licenças no portal do Azure, tem de ser um proprietário da subscrição do Azure que o Power BI utiliza para pesquisas do Azure Active Directory.

### <a name="purchase-licenses-in-microsoft-365"></a>Comprar licenças no Microsoft 365

> [!NOTE]
> Se adquirir normalmente licenças mediante um contrato de licenciamento em volume, como um Contrato Enterprise, e quiser receber uma fatura em vez de comprar com um cartão de crédito ou uma conta bancária, terá de submeter a encomenda de forma diferente. Contacte o seu Revendedor Microsoft ou aceda ao Volume Licensing Service Center para adicionar ou remover licenças. Para obter mais informações, veja [Manage subscription licenses](https://docs.microsoft.com/microsoft-365/commerce/licenses/buy-licenses?view=o365-worldwide) (Gerir licenças de subscrição).

Siga estes passos para comprar licenças do Power BI Pro no centro de administração do Microsoft 365:

1. Inicie sessão no [centro de administração do Microsoft 365](https://admin.microsoft.com).

2. No menu de navegação, selecione **Faturação** > **Comprar serviços**.

3. Procure ou percorra para encontrar a subscrição que quer comprar. Encontrará o **Power BI** em **Outras categorias que possam interessar-lhe** perto da parte inferior da página. Selecione a ligação para visualizar as subscrições do Power BI disponíveis para a sua organização.

4. Selecione **Power BI Pro**.

5. Na página **Serviços de compra**, selecione **Comprar**.

6. Selecione **Pagar mensalmente** ou **Pagar o ano completo** de acordo com a forma que quer pagar.

7. Em **Quantos utilizadores quer?** , introduza o número de licenças que quer comprar e, em seguida, selecione **Finalizar compra agora** e conclua a transação.

8. Para verificar a sua compra, vá para **Faturação** > **Produtos e serviços** e procure **Power BI Pro**.

9. Para adicionar mais licenças posteriormente, localize **Power BI Pro** na página **Produtos e serviços** e, em seguida, selecione **Adicionar/Remover licenças**.


## <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Atribuir licenças no centro de administração do Microsoft 365

Para obter informações sobre a atribuição de licenças no centro de administração do Microsoft 365, veja [Atribuir licenças a utilizadores](/office365/admin/manage/assign-licenses-to-users).

Para utilizadores convidados, veja [Atribuir licenças a utilizadores na página Licenças](/office365/admin/manage/assign-licenses-to-users#assign-licenses-to-users-on-the-licenses-page). Antes de atribuir licenças do Power BI Pro a utilizadores convidados, contacte o seu representante da conta Microsoft para confirmar que está em conformidade com os termos do seu contrato com a Microsoft.

## <a name="assign-licenses-in-the-azure-portal"></a>Atribuir licenças no portal do Azure

Siga estes passos para atribuir licenças do Power BI Pro a contas de utilizador individuais:

1. Inicie sessão no [portal do Azure](https://portal.azure.com/).

2. Procure e selecione **Azure Active Directory**.

3. Em **Gerir** no menu de recursos **Azure Ative Directory**, selecione **Licenças**.

4. Selecione **Todos os produtos** no menu de recursos **Licenças – Descrição geral** e, em seguida, selecione **Power BI Pro** para apresentar a lista de utilizadores licenciados.

5. Na barra de comandos, selecione **+Atribuir**. Na página **Atribuir licença**, escolha primeiro um utilizador e, em seguida, selecione **Opções de atribuição** para ativar uma licença do Power BI Pro para a conta de utilizador selecionada.

## <a name="next-steps"></a>Próximos passos

- [Licenciamento do Power BI na sua organização](service-admin-licensing-organization.md)

 - [Encontrar utilizadores do Power BI que iniciaram sessão](service-admin-access-usage.md)

 - [Aderir ao Power BI como um indivíduo](../fundamentals/service-self-service-signup-for-power-bi.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
