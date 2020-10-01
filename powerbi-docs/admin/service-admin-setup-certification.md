---
title: Configurar a certificação de conjuntos de dados e de fluxos de dados (pré-visualização)
description: Saiba como configurar o processo de certificação de conjuntos de dados e de fluxos de dados na sua organização.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 05/15/2020
ms.author: painbar
LocalizationGroup: Share your work
ms.openlocfilehash: 11079e2ab1578cfe5db352e7e3286d491bdfca2c
ms.sourcegitcommit: 02b5d031d92ea5d7ffa70d5098ed15e4ef764f2a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/26/2020
ms.locfileid: "91374919"
---
# <a name="set-up-dataset-and-dataflow-certification-preview"></a>Configurar a certificação de conjuntos de dados e de fluxos de dados (pré-visualização)

A sua organização pode certificar conjuntos de dados e fluxos de dados que sejam as origens autoritativas de informações críticas.

Como administrador do Power BI, é responsável por configurar o processo de certificação para a sua organização. Isto significa:
* Ativar a certificação no seu inquilino.
* Definir uma lista de grupos e utilizadores autorizados a certificar conjuntos de dados e fluxos de dados.
* Para conjuntos de dados, fornecer o URL da política de certificação do conjunto de dados da organização, se existir.

A certificação de conjuntos de dados e de fluxos de dados faz parte do *endossamento* de conjuntos de dados e de fluxos de dados. Para obter mais informações, veja [endossamento do conjunto de dados](../connect-data/service-datasets-promote.md) e [endossamento do fluxo de dados](../transform-model/service-dataflows-promote-certify.md).


## <a name="set-up-certification"></a>Configurar a certificação

1. No portal de administração, aceda às Definições de inquilino.
1. Na secção Definições de exportação e partilha, expanda a secção Certificação.

   ![Set up dataset and dataflow certification (Configurar a certificação de conjuntos de dados e de fluxos de dados)](media/service-admin-setup-certification/service-admin-certification-setup-dialog.png)

1. Mova o botão para **Ligado**.
1. Para a certificação de conjuntos de dados, se a sua organização tiver uma política de certificação publicada, pode fornecer o URL aqui. Irá tornar-se a ligação **Saiba mais** na secção de certificação da [caixa de diálogo de definições do endossamento do fluxo de dados](../connect-data/service-datasets-promote.md#request-dataset-certification) 
1. Especifique os utilizadores ou grupos autorizados a certificar conjuntos de dados e fluxos de dados. Estas pessoas autorizadas poderão utilizar o botão Certificação na secção de certificação da caixa de diálogo de definições do endossamento do [conjunto de dados](../connect-data/service-datasets-promote.md#request-dataset-certification) ou [fluxo de dados](../transform-model/service-dataflows-promote-certify.md#certify-a-dataflow).
1. Clique em **Aplicar**.

## <a name="next-steps"></a>Próximos passos
* [Promote datasets](../connect-data/service-datasets-promote.md) (Promover conjuntos de dados)
* [Certify datasets](../connect-data/service-datasets-certify.md) (Certificar conjuntos de dados)
* [Promote dataflows](../transform-model/service-dataflows-promote-certify.md#promote-a-dataflow) (Promover fluxos de dados)
* [Certify dataflows](../transform-model/service-dataflows-promote-certify.md#certify-a-dataflow) (Certificar fluxos de dados)
* Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
