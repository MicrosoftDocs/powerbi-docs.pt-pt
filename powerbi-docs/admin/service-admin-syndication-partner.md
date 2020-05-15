---
title: Unable to add Power BI to O365 partner (Não é possível adicionar o Power BI ao parceiro do Office 365)
description: Não é possível adicionar o Power BI a um parceiro de distribuição do Office 365. O modelo de distribuição é um modelo de compra utilizado pelo Office 365.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 5907f23bb5bf1bcdc5a4ca3412e5331a09d145c9
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83344946"
---
# <a name="unable-to-add-power-bi-to-office-365-partner-subscription"></a>Não é possível adicionar o Power BI a uma subscrição de parceiro do Office 365

O Office 365 permite que as empresas o revendam acompanhado e integrado com as suas próprias soluções, fornecendo aos clientes finais um único ponto de contacto para compra, faturação e suporte.

Se estiver interessado em adquirir o Power BI, juntamente com a sua subscrição do Office 365, recomendamos que contacte o seu parceiro. Se o seu parceiro não oferecer atualmente o Power BI, poderá optar por opções diferentes.

## <a name="work-with-your-partner-to-purchase-power-bi"></a>Trabalhar com o seu parceiro para comprar o Power BI

Se quiser comprar uma subscrição do Power BI Pro ou do Power BI Premium, trabalhe com o seu parceiro para considerar as opções que estão disponíveis:

* O seu parceiro concorda em adicionar o Power BI ao respetivo portefólio para que possa fazer compras através dele.

* O seu parceiro consegue fazer a sua transição para um modelo a partir do qual pode comprar o Power BI diretamente à Microsoft ou a outro parceiro que ofereça o Power BI.

## <a name="purchase-from-microsoft-or-another-channel"></a>Comprar na Microsoft ou através de outro canal

Consoante a relação com o parceiro, pode comprar o Power BI diretamente na Microsoft ou através de outro parceiro. Pode verificar se pode adicionar subscrições do Power BI no centro de administração do Microsoft 365 (requer a associação na função de Administrador Global ou Administrador de Faturação).

1. Aceda ao [centro de administração do Microsoft 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. No menu esquerdo, abra **Faturação**:

    * Se vir **Subscrições**, poderá adquirir o serviço diretamente na Microsoft ou poderá entrar em contacto com outro parceiro que ofereça o Power BI.

        ![Faturação – com subscrições](media/service-admin-syndication-partner/billingsub.png)

    * Se não vir **Subscrições**, não poderá comprar diretamente na Microsoft ou através de outro parceiro.

Se o seu parceiro não oferecer o Power BI nem conseguir comprar diretamente na Microsoft ou através de outro parceiro, considere inscrever-se numa avaliação gratuita.

## <a name="sign-up-for-a-free-trial"></a>Inscrever-se numa avaliação gratuita

Pode inscrever-se numa avaliação gratuita do Power BI. Se não comprar o Power BI Pro no final do período de avaliação, continuará a ter uma licença gratuita que disponibiliza muitas das funcionalidades do Power BI. Para obter mais informações, veja [Inscrever-se no Power BI como um indivíduo](../fundamentals/service-self-service-signup-for-power-bi.md).

### <a name="enable-ad-hoc-subscriptions"></a>Ativar as subscrições ad-hoc

Por predefinição, as inscrições individuais (também conhecidas como subscrições ad-hoc) estão desativadas. Neste caso, pode ver a seguinte mensagem quando tentar inscrever-se: *O departamento de TI desativou a inscrição no Microsoft Power BI*.

![Imagem Lamentamos](media/service-admin-syndication-partner/sorry.png)

Para ativar as subscrições ad-hoc, contacte o seu parceiro e peça-lhe que as ative. Se for um administrador do inquilino e souber utilizar os comandos do Azure Active Directory PowerShell, poderá ativar as subscrições ad-hoc. [Azure Active Directory PowerShell for Graph](/powershell/azure/active-directory/install-adv2/) (Azure Active Directory PowerShell para Graph)

1. Inicie sessão no Azure Active Directory com as suas credenciais do Office 365. A primeira linha do script abaixo pede-lhe as suas credenciais. Na segunda linha, é ligado ao Azure Active Directory.

    ```powershell
    $msolcred = get-credential
    connect-msolservice -credential $msolcred
    ```

    ![Introduzir as credenciais](media/service-admin-syndication-partner/aad-signin.png)

1. Depois de iniciar sessão, execute o seguinte comando para marcar a definição atual para `AllowAdHocSubscriptions`.

    ```powershell
    Get-MsolCompanyInformation
    ```

1. Execute o seguinte comando para ativar as inscrições gratuitas.

    ```powershell
    Set-MsolCompanySettings -AllowAdHocSubscriptions $true
    ```

## <a name="next-steps"></a>Próximas etapas

[Licenciamento do Power BI na sua organização](service-admin-licensing-organization.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)