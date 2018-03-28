---
title: Atribuir licenças do Power BI Pro
description: Atribuir licenças do Power BI Pro
services: powerbi
documentationcenter: ''
author: markingmyname
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/22/2018
ms.author: maghan
LocalizationGroup: Administration
ms.openlocfilehash: 010f99922e2e9d43bbb192fe53eabb17a6af43f3
ms.sourcegitcommit: 1fe3ababba34c4e7aea08adb347ec5430e0b38e4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2018
---
# <a name="assigning-power-bi-pro-licenses"></a>Atribuir licenças do Power BI Pro

Os administradores podem escolher a partir de vários portais de gestão e cmdlets do PowerShell para atribuírem licenças do Power BI Pro a utilizadores. A gestão de licenças do Power BI é apoiada pelo Azure Active Directory (Azure AD).

* Os proprietários de subscrições do Azure podem utilizar o painel Azure Active Directory no [Portal do Azure](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0). 

* Os administradores globais e os administradores de contas de utilizador podem utilizar o [Centro de Administração do Office 365](https://portal.office.com/AdminPortal/Home#/homepage).

## <a name="managing-power-bi-pro-licenses-in-the-azure-portal"></a>Gerir licenças do Power BI Pro no Portal do Azure

O Power BI utiliza o Azure AD como um serviço fundamental. O Azure AD armazena contas e grupos de utilizador, assim como outras definições, tais como informações sobre os produtos adquiridos.

### <a name="assigning-licenses-to-individual-user-accounts"></a>Atribuir licenças a contas de utilizador individuais

Se for o proprietário de uma subscrição do Azure, siga estes passos para atribuir licenças do Power BI Pro a contas de utilizador individuais:

1. Navegue até ao [Portal do Azure](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0). 

2. Na barra de navegação esquerda, clique em Azure Active Directory.

    ![image](media/service-assigning-power-bi-pro-licenses/service-assigning-power-bi-pro-licenses-01.png)

3. No painel Azure Active Directory, clique em Licenças.

    ![image](media/service-assigning-power-bi-pro-licenses/service-assigning-power-bi-pro-licenses-02.png)

4. No painel Licenças, clique em Todos os produtos e, em seguida, clique em Power BI Pro para apresentar a lista de utilizadores com licenças.

    ![image](media/service-assigning-power-bi-pro-licenses/service-assigning-power-bi-pro-licenses-03.png)

5. Clique em Atribuir para adicionar uma licença do Power BI Pro a uma conta de utilizador adicional.

    ![image](media/service-assigning-power-bi-pro-licenses/service-assigning-power-bi-pro-licenses-04.png)

> [!NOTE]
> Embora possa gerir a maioria dos aspetos de licenciamento, não é possível comprar licenças do Power BI Pro no Portal do Azure. Utilize o Centro de Administração do Office 365 para comprar uma subscrição do Power BI Pro. Para obter mais informações, veja [Purchasing Power BI Pro (Comprar o Power BI Pro)](https://docs.microsoft.com/en-us/power-bi/service-admin-purchasing-power-bi-pro).
>

## <a name="managing-power-bi-pro-licenses-in-the-office-365-admin-center"></a>Gerir licenças do Power BI Pro no Centro de Administração do Office 365

Se for um administrador global, então o Centro de Administração do Office 365 é o local onde irá comprar uma subscrição do Power BI Pro e gerir as licenças associadas para a sua organização.

Se for um administrador do Office 365, siga estes passos para atribuir licenças do Power BI Pro a contas de utilizador individuais:

1. Navegue até ao centro de administração do Office 365.

2. No painel de navegação à esquerda, expanda Utilizadores e, em seguida, clique em Utilizadores ativos.

    ![image](media/service-assigning-power-bi-pro-licenses/service-assigning-power-bi-pro-licenses-05.png)

3. Selecione um ou múltiplos utilizadores e, em seguida, clique em Editar relativo a Licenças de produtos.

    ![image](media/service-assigning-power-bi-pro-licenses/service-assigning-power-bi-pro-licenses-06.png)

4. Em Power BI Pro, altere a definição para Ativado e clique em Guardar.

    ![image](media/service-assigning-power-bi-pro-licenses/service-assigning-power-bi-pro-licenses-07.png)

5. Para as contas selecionadas, verifique em Estado se a licença do Power BI Pro foi atribuída com êxito.

    ![image](media/service-assigning-power-bi-pro-licenses/service-assigning-power-bi-pro-licenses-08.png)

> [!NOTE]
> Se a sua subscrição ficar sem licenças, adicione mais ao expandir Faturação no painel de navegação à esquerda e, em seguida, clique em Subscrições. Na página Subscrições, selecione a subscrição do Power BI Pro e, em seguida, clique em Adicionar/Remover licenças.
>

## <a name="next-steps"></a>Próximos passos
[Power BI Pro in your organization](service-admin-power-bi-pro-in-your-organization.md) (Power BI Pro na sua organização)
</br>
[Ativação da Versão de Avaliação Pro alargada](service-extended-pro-trial.md)
</br>
[Contrato de serviço do Power BI para utilizadores individuais](https://powerbi.microsoft.com/terms-of-service/)
</br>
[Anúncio do Power BI Premium](https://aka.ms/pbipremium-announcement)
</br>
[Encontrar utilizadores do Power BI que iniciaram sessão](service-admin-access-usage.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)