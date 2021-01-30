---
title: Desativar a atualização em segundo plano do Power Query
description: Orientações sobre quando desativar a atualização em segundo plano do Power Query.
author: peter-myers
ms.author: kfollis
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 09/26/2019
ms.openlocfilehash: e620841089cd7a039fc157fe8b3f8f0857773cb8
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2021
ms.locfileid: "99087459"
---
# <a name="disable-power-query-background-refresh"></a>Desativar a atualização em segundo plano do Power Query

Este artigo destina-se aos Modeladores de dados de importação que trabalham com o Power BI Desktop.

Por predefinição, quando o Power Query importa dados, também coloca em cache até 1000 linhas de dados de pré-visualização para cada consulta. Os dados de pré-visualização ajudam a apresentar uma pré-visualização rápida dos dados de origem e dos resultados de transformação para cada passo das suas consultas. São armazenados separadamente no disco e não dentro do ficheiro do Power BI Desktop.

No entanto, quando o seu ficheiro do Power BI Desktop contém várias consultas, a recuperação e armazenamento de dados de pré-visualização pode aumentar o tempo necessário para concluir uma atualização.

## <a name="recommendation"></a>Recomendação

Obterá uma atualização mais rápida ao definir o ficheiro do Power BI Desktop para atualizar a cache de pré-visualização _em segundo plano_. No Power BI Desktop, pode ativar esta definição ao selecionar _Ficheiro > Opções e definições > Opções_ e, em seguida, a página _Carregar Dados_. Em seguida, pode ativar a opção **Permitir a transferência da pré-visualização dos dados em segundo plano**. Tenha em atenção que esta opção só pode ser definida para o ficheiro atual.

![Captura de ecrã a mostrar o Power B I Desktop com as opções de dados em segundo plano.](media/power-query-background-refresh/power-query-options-background-data.png)

Ativar a atualização em segundo plano pode fazer com que os dados de pré-visualização fiquem desatualizados. Se isso ocorrer, o Editor do Power Query irá notificá-lo com o seguinte aviso:

![Captura de ecrã a mostrar o Power B I Desktop com o aviso do Editor do Power Query sobre dados de pré-visualização antigos.](media/power-query-background-refresh/power-query-preview-data-old.png)

Pode sempre atualizar a cache de pré-visualização. Pode atualizá-la para uma única consulta ou para todas as consultas com o comando **Atualizar Pré-visualização**. Pode encontrá-lo no friso **Home Page** da janela do Editor do Power Query.

![Captura de ecrã a mostrar o Power B I Desktop com os comandos do Editor do Power Query para atualizar os dados de pré-visualização.](media/power-query-background-refresh/power-query-refresh-preview-data.png)

## <a name="next-steps"></a>Próximos passos

Para obter mais informações relacionadas com este artigo, consulte os seguintes recursos:

- [Documentação do Power Query](/power-query/)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
