---
title: Encontrar utilizadores do Power BI que iniciaram sessão
description: Se for um administrador de inquilino e quiser ver quem iniciou sessão no Power BI, pode utilizar os relatórios de acesso e utilização do Azure Active Directory para ganhar visibilidade.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/23/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: e513607dd89aee15f10145cf62bd461621cc12c0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906681"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Encontrar utilizadores do Power BI que iniciaram sessão

Se for um administrador de inquilino e quiser ver quem iniciou sessão no Power BI, utilize o [relatórios de acesso e utilização do Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins) ganhar visibilidade.

<iframe width="640" height="360" src="https://www.youtube.com/embed/1AVgh9w9VM8?showinfo=0" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> O **inícios de sessão** relatório fornece informações úteis, mas ele não identifica o tipo de licença, cada utilizador tem. Utilize o centro de administração do Microsoft 365 para ver as licenças.

## <a name="requirements"></a>Requirements

Qualquer utilizador (incluindo não administradores) pode ver um relatório dos seus inícios de sessão, mas tem de cumprir os requisitos seguintes para ver um relatório de todos os utilizadores.

* O inquilino tem de ter uma licença do Azure Active Directory Premium associada a ele.

* Deve estar numa das seguintes funções: Administrador Global, Administrador de Segurança ou Leitor de Segurança.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Utilizar o portal do Azure para ver inícios de sessão

Para ver a atividade de início de sessão, siga estes passos.

1. No **portal do Azure**, selecione **Azure Active Directory**.

1. Em **Monitorização**, selecione **Inícios de sessão**.
   
    ![Captura de ecrã da interface do Usuário do Azure com as opções do Azure Active Directory e inícios de sessão realçadas.](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Filtre a aplicação por **Microsoft Power BI** ou **Power BI Gateway** e selecione **Aplicar**.

    **Microsoft Power BI** filtros para a atividade de início de sessão relacionada com o serviço, enquanto **Power BI Gateway** filtros para início de sessão atividade específica para o gateway de dados no local.
   
    ![Captura de ecrã do filtro de inícios de sessão com o campo de aplicativos realçado.](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>Exportar os dados

Pode [transferir um relatório de início de sessão](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report) em qualquer um dos dois formatos: um ficheiro CSV ou um ficheiro JSON.

![Captura de ecrã do botão de transferência.](media/service-admin-access-usage/download-sign-in-data-csv.png)

Na parte superior a **inícios de sessão** relatório, selecione **transferir** e, em seguida, selecione uma das seguintes opções:

* **CSV** para transferir um ficheiro CSV para os dados atualmente filtrados.

* **JSON** para transferir um ficheiro JSON para os dados atualmente filtrados.

## <a name="data-retention"></a>Retenção de dados

Os dados relacionados com os inícios de sessão estão disponíveis durante um máximo de 30 dias. Para mais informações, veja [políticas de retenção de relatórios do Azure Active Directory](/azure/active-directory/reports-monitoring/reference-reports-data-retention).

## <a name="next-steps"></a>Próximos passos

[Utilizar a auditoria na sua organização](service-admin-auditing.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)