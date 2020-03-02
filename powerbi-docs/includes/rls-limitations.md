---
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 01/31/2020
ms.author: davidi
ms.openlocfilehash: b67025de5e2a70876a31fd42e22c9572403288fa
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464425"
---
## <a name="limitations"></a>Limitações

As limitações atuais da segurança ao nível de linha nos modelos da cloud são as seguintes:

* Se tiver definido anteriormente funções e regras no serviço Power BI, tem de as recriar no Power BI Desktop.

* Pode definir a RLS apenas nos conjuntos de dados criados com o Power BI Desktop. Se quiser ativar a RLS para os conjuntos de dados criados com o Excel, primeiro tem de converter os seus ficheiros em ficheiros do Power BI Desktop (PBIX). [Saiba mais](../desktop-import-excel-workbooks.md).

* Só são suportadas ligações de Importação e DirectQuery. As ligações em direto para o Analysis Services são processadas no modelo no local.

## <a name="known-issues"></a>Problemas conhecidos

Existe um problema conhecido em que é apresentada uma mensagem de erro ao tentar publicar um relatório do Power BI Desktop publicado anteriormente. O cenário é o seguinte:

1. A Teresa tem um conjunto de dados que foi publicado no serviço Power BI e configurou a RLS.

1. A Teresa atualiza o relatório no Power BI Desktop e volta a publicar o conjunto de dados.

1. A Teresa vê um erro.

**Solução:** publicar novamente o ficheiro do Power BI Desktop a partir do serviço Power BI até que o problema seja resolvido. Pode fazê-lo ao selecionar **Obter Dados** > **Ficheiros**.
