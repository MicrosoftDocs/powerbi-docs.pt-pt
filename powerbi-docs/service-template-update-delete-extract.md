---
title: Update, delete, and extract a Power BI template app (Atualizar, eliminar e extrair uma aplicação de modelo do Power BI)
description: Como atualizar, eliminar e extrair uma aplicação de modelo.
author: teddybercovitz
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: tebercov
ms.openlocfilehash: 273734493c761739f9780e6a7fe6e781900723f9
ms.sourcegitcommit: 7d52401f50944feaaa112c84113ee47f606dbf68
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/13/2019
ms.locfileid: "67125884"
---
# <a name="update-delete-and-extract-template-app"></a>Atualizar, eliminar e extrair uma aplicação de modelo

Agora que a aplicação está em produção, pode recomeçar a fase de teste sem interromper a aplicação em produção.
## <a name="update-your-app"></a>Atualizar a sua aplicação


1. No painel **Gestão de Versões**, selecione **Criar aplicação**.
2. Repita o processo de criação de aplicações.
3. Após definir as categorias **Personalização**, **Conteúdo**, **Controlo** e **Acesso**, selecione novamente **Criar aplicação**.
4. Selecione **Fechar** e regresse ao painel **Gestão de Versões**.

   Verá que agora tem duas versões: A versão em produção e uma nova versão em modo de teste.

    ![Duas versões de uma aplicação de modelo](media/service-template-apps-update-extract-delete/power-bi-template-app-update.png)

5. Quando estiver pronto para promover a sua aplicação para pré-produção para que sejam feitos testes adicionais fora do seu inquilino, regresse ao painel Gestão de Versões e selecione **Promover aplicação** junto a **Teste**.
6. A ligação está agora ativada. Submeta-a novamente no Cloud Partner Portal (CPP). Para tal, execute os passos descritos em [Atualização da oferta da aplicação Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-update-existing-offer).
7. No CPP, tem de **publicar** novamente a oferta e validá-la.

>[!NOTE]
>Promova a aplicação para a fase de produção apenas depois de ser aprovada pelo Cloud Partner Portal e depois de a publicar.

## <a name="extract-workspace"></a>Extrair a área de trabalho
Com a capacidade de extração, agora é mais fácil do que nunca reverter para a versão anterior de uma aplicação de modelo. Os passos seguintes permitem extrair uma versão específica, a partir das várias fases da versão, para uma nova área de trabalho:

1. No painel de gestão de versões, prima mais **(...)** e, em seguida, **Extrair**.

    ![extrair versão da aplicação de modelo](media/service-template-apps-update-extract-delete/power-bi-template-app-extract.png) ![extrair versão da aplicação de modelo](media/service-template-apps-update-extract-delete/power-bi-template-app-extract-dialog.png)
2. Na caixa de diálogo, introduza o nome da área de trabalho extraída. Será adicionada uma nova área de trabalho.

A nova versão da área de trabalho é reposta e pode continuar a desenvolver e a distribuir a aplicação de modelo a partir da área de trabalho recentemente extraída.

## <a name="delete-template-app-version"></a>Eliminar a versão da aplicação de modelo
Uma área de trabalho da aplicação de modelo é a origem de dados de uma aplicação de modelo ativa. Para proteger os utilizadores da aplicação de modelo, não é possível eliminar uma área de trabalho sem primeiro remover todas as versões da aplicação criadas na área de trabalho.
Ao eliminar uma versão da aplicação, também elimina o URL da aplicação, que deixará de funcionar.

1. No painel de gestão de versões, prima para selecionar as reticências **(...)** e, em seguida, prima **Eliminar**.
 ![Eliminar versão da aplicação de modelo](media/service-template-apps-update-extract-delete/power-bi-template-app-delete.png)
 ![Eliminar versão de aplicação de modelo](media/service-template-apps-update-extract-delete/power-bi-template-app-delete-dialog.png)

>[!NOTE]
>Confirme que não elimina a versão da aplicação que está a ser utilizada pelos clientes ou pela **AppSource**. Caso contrário, a aplicação deixará de funcionar.

## <a name="next-steps"></a>Próximos passos

Veja como os seus clientes interagem com a sua aplicação de modelo em [Install, customize, and distribute template apps in your organization](service-template-apps-install-distribute.md) (Instalar, personalizar e distribuir aplicações de modelo na sua organização).

Veja a [Oferta da aplicação Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) para obter detalhes sobre como distribuir a sua aplicação.
