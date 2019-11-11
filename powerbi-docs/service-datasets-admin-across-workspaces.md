---
title: Controlar a utilização de conjuntos de dados em áreas de trabalho (Pré-visualização) – Power BI
description: Aprenda a restringir o fluxo de informações no inquilino do Power BI.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d1ad29bebc148d9f30e8d22240dd149787251a0a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73872591"
---
# <a name="control-the-use-of-datasets-across-workspaces-preview"></a>Controlar a utilização de conjuntos de dados em áreas de trabalho (Pré-visualização)

A utilização de conjuntos de dados em áreas de trabalho é uma excelente forma de fomentar a cultura e a democratização de dados numa organização. Ainda assim, se for um administrador do Power BI, poderá querer restringir o fluxo de informações no seu inquilino do Power BI. Com a definição de inquilinos **Utilizar conjuntos de dados em áreas de trabalho**, poderá restringir total ou parcialmente a reutilização de conjuntos de dados por grupos de segurança.

![Definições de área de trabalho de um administrador do Power BI](media/service-datasets-admin-across-workspaces/power-bi-admin-workspace-settings.png)

Se desativar esta definição, serão estes os efeitos nos criadores de relatórios:

- O botão para copiar relatórios em áreas de trabalho não estará disponível. 
- Num relatório baseado num conjunto de dados partilhado, o botão **Editar relatório** não estará disponível.
- No serviço Power BI, a experiência de deteção só apresentará conjuntos de dados na área de trabalho atual.
- No Power BI Desktop, a experiência de deteção só apresentará conjuntos de dados de áreas de trabalho das quais é membro.
- No Power BI Desktop, se os utilizadores abrirem um ficheiro .pbix com uma ligação em direto a um conjunto de dados fora de quaisquer áreas de trabalho das quais sejam membros, verão uma mensagem de erro a pedir-lhe para ligarem a um conjunto de dados diferente.

## <a name="provide-a-link-for-the-certification-process"></a>Fornecer uma ligação para o processo de certificação

Enquanto administrador de inquilinos, pode fornecer um URL para a ligação **Saiba mais** na página de definições **Recomendação**.  Esta ligação pode direcionar os utilizadores para documentação acerca do seu processo de certificação. Se não fornecer um destino para a ligação **Saiba mais**, esta irá direcionar os utilizadores, por predefinição, para o artigo de [certificação de conjuntos de dados](service-datasets-certify.md).

![Ligação Saiba mais da certificação de conjuntos de dados](media/service-datasets-certify-promote/power-bi-dataset-learn-more-certification.png)

## <a name="next-steps"></a>Próximos passos

- [Use datasets across workspaces (Preview)](service-datasets-across-workspaces.md) (Utilizar conjuntos de dados em várias áreas de trabalho [Pré-visualização])
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
