---
title: Encontrar utilizadores do Power BI que iniciaram sessão
description: Se for administrador inquilino e quiser ver quem iniciou sessão no Power BI, pode utilizar os relatórios de acesso e utilização do Azure Active Directory para obter visibilidade.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 12a15360efbff62c40f5bd1098886ee046661e4f
ms.sourcegitcommit: 5222bc6a8336acc77c8e22db57ea6a7bf7daea57
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59290748"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Encontrar utilizadores do Power BI que iniciaram sessão

Se for administrador de inquilinos e quiser ver quem iniciou sessão no Power BI, utilize os [relatórios de acesso e utilização do Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins) para obter visibilidade.

<iframe width="640" height="360" src="https://www.youtube.com/embed/1AVgh9w9VM8?showinfo=0" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> O relatório de atividade fornece informações úteis, mas não identifica o tipo de licença que cada utilizador tem. Utilize o centro de administração do Microsoft 365 para ver as licenças.

## <a name="requirements"></a>Requirements

Qualquer utilizador (incluindo não administradores) pode ver um relatório dos seus inícios de sessão, mas tem de cumprir os requisitos seguintes para ver um relatório de todos os utilizadores.

* O seu inquilino tem de ter uma licença do Azure AD Premium associada.

* Deve estar numa das seguintes funções: Administrador Global, Administrador de Segurança ou Leitor de Segurança.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Utilizar o portal do Azure para ver inícios de sessão

Para ver a atividade de início de sessão, siga estes passos.

1. No **portal do Azure**, selecione **Azure Active Directory**.

1. Em **Monitorização**, selecione **Inícios de sessão**.
   
    ![Inícios de sessão do Microsoft Azure AD](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Filtre a aplicação por **Microsoft Power BI** ou **Power BI Gateway** e selecione **Aplicar**.

    O **Microsoft Power BI** filtra a atividade de início de sessão relacionada com o serviço, enquanto o **Power BI Gateway** filtra a atividade de início de sessão específica do Gateway de dados no local.
   
    ![Filtrar inícios de sessão](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>Exportar os dados

Tem duas opções para exportar os dados de início de sessão: transferir um ficheiro csv ou utilizar o PowerShell. Na parte superior do relatório de início de sessão, selecione uma das seguintes opções:

* **Transferir** para transferir um ficheiro csv para os dados atualmente filtrados.

* **Script** para transferir um script do PowerShell para os dados atualmente filtrados. Pode atualizar o filtro no script, conforme necessário.

![Transferir o ficheiro csv ou o script](media/service-admin-access-usage/download-sign-in-data-csv.png)

## <a name="data-retention"></a>Retenção de dados

Os dados relacionados com os inícios de sessão estão disponíveis durante um máximo de 30 dias. Para obter mais informações, veja [Políticas de retenção de relatórios do Azure Active Directory](/azure/active-directory/reports-monitoring/reference-reports-data-retention).

## <a name="next-steps"></a>Próximos passos

[Utilizar a auditoria na sua organização](service-admin-auditing.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

