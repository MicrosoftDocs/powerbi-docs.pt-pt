---
title: Encontrar utilizadores do Power BI que iniciaram sessão
description: Se for um administrador inquilino e quiser ver quem iniciou sessão no Power BI, pode utilizar os relatórios de acesso e utilização do Azure Active Directory para obter visibilidade.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 32ca01d06f4fc8c3f90f73bf8137349eed0220a6
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/02/2019
ms.locfileid: "74698837"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Encontrar utilizadores do Power BI que iniciaram sessão

Se for administrador de inquilinos e quiser ver quem iniciou sessão no Power BI, utilize os [relatórios de acesso e utilização do Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins) para obter visibilidade.

> [!NOTE]
> O relatório de **Inícios de sessão** fornece informações úteis, mas não identifica o tipo de licença que cada utilizador tem. Utilize o centro de administração do Microsoft 365 para ver as licenças.

## <a name="requirements"></a>Requirements

Qualquer utilizador (incluindo não administradores) pode ver um relatório dos seus inícios de sessão, mas tem de cumprir os requisitos seguintes para ver um relatório de todos os utilizadores.

* O seu inquilino tem de ter uma licença do Azure Active Directory Premium associada.

* Deve estar numa das seguintes funções: Administrador Global, Administrador de Segurança ou Leitor de Segurança.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Utilizar o portal do Azure para ver inícios de sessão

Para ver a atividade de início de sessão, siga estes passos.

1. No **portal do Azure**, selecione **Azure Active Directory**.

1. Em **Monitorização**, selecione **Inícios de sessão**.
   
    ![Captura de ecrã a mostrar a IU do Azure com as opções Azure Active Directory e Inícios de sessão realçadas.](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Filtre a aplicação por **Microsoft Power BI** ou **Power BI Gateway** e selecione **Aplicar**.

    O **Microsoft Power BI** filtra a atividade de início de sessão relacionada com o serviço, enquanto o **Power BI Gateway** filtra a atividade de início de sessão específica do gateway de dados no local.
   
    ![Captura de ecrã a mostrar o filtro Inícios de sessão com o campo Aplicações realçado.](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>Exportar os dados

Pode [transferir um relatório de início de sessão](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report) num de dois formatos: um ficheiro .CSV ou um ficheiro .JSON.

![Captura de ecrã a mostrar o botão Transferir.](media/service-admin-access-usage/download-sign-in-data-csv.png)

Na parte superior do relatório **Inícios de sessão**, selecione **Transferir** e, em seguida, selecione uma das seguintes opções:

* **CSV** para transferir um ficheiro .CSV com os dados atualmente filtrados.

* **JSON** para transferir um ficheiro .JSON com os dados atualmente filtrados.

## <a name="data-retention"></a>Retenção de dados

Os dados relacionados com os inícios de sessão estão disponíveis durante um máximo de 30 dias. Para obter mais informações, veja [Políticas de retenção de relatórios do Azure Active Directory](/azure/active-directory/reports-monitoring/reference-reports-data-retention).

## <a name="next-steps"></a>Próximos passos

[Utilizar a auditoria na sua organização](service-admin-auditing.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)