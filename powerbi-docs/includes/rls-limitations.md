---
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 09/13/2019
ms.author: davidi
ms.openlocfilehash: 6d1a239954a64da1c92cc68b56912e6f4ab67228
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/04/2020
ms.locfileid: "74882812"
---
## <a name="limitations"></a>Limitações

Segue-se uma lista das limitações atuais da segurança ao nível de linha nos modelos da cloud.

* Se tiver definido anteriormente funções e regras no serviço Power BI, tem de as recriar no Power BI Desktop.

* Pode definir a RLS apenas nos conjuntos de dados criados com o Power BI Desktop. Se quiser ativar a RLS para os conjuntos de dados criados com o Excel, primeiro tem de converter os seus ficheiros em ficheiros do Power BI Desktop (PBIX). [Saiba mais](../desktop-import-excel-workbooks.md)

* Só são suportadas ligações de Importação e DirectQuery. As ligações em direto para o Analysis Services são processadas no modelo no local.

## <a name="known-issues"></a>Problemas conhecidos

Existe um problema conhecido em que é apresentada uma mensagem de erro ao tentar publicar um relatório do Power BI Desktop publicado anteriormente. Segue-se o cenário.

1. A Teresa tem um conjunto de dados que foi publicado no serviço Power BI e configurou a RLS.

1. A Teresa atualiza o relatório no Power BI Desktop e volta a publicar o conjunto de dados.

1. A Teresa vê um erro.

**Solução:** publicar novamente o ficheiro do Power BI Desktop a partir do serviço Power BI até que o problema seja resolvido. Pode fazê-lo ao selecionar **Obter Dados** > **Ficheiros**.
