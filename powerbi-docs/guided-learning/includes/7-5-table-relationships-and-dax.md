---
ms.openlocfilehash: 679c3e8c3d94c93899e9dcfae1e57f4b678fb218
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "73800062"
---
O Power BI permite-lhe criar relações entre várias tabelas, incluindo tabelas provenientes de origens de dados completamente diferentes. Pode ver essas relações para qualquer modelo de dados na vista **Relações** do Power BI Desktop.

![](media/7-5-table-relationships-and-dax/dax-relationships_1.png)

## <a name="dax-relational-functions"></a>Funções relacionais da DAX
A DAX tem **funções relacionais** que lhe permitem interagir com as tabelas que têm relações estabelecidas.

Pode devolver o valor de uma coluna ou pode devolver todas as linhas numa relação através das funções da DAX.

Por exemplo, a função **RELATED** segue relações e devolve o valor de uma coluna, enquanto **RELATEDTABLE** segue relações e devolve uma tabela completa que é filtrada para incluir apenas linhas relacionadas.

![](media/7-5-table-relationships-and-dax/dax-relationships_2.png)

A função **RELATED** funciona em relações *muitos-para-um*, enquanto a função **RELATEDTABLE** destina-se a relações *um-para-muitos*.

Pode utilizar funções relacionais para criar expressões que incluem valores em várias tabelas. A DAX irá devolver um resultado com estas funções, independentemente do comprimento da cadeia da relação.

> Conteúdo de vídeo cortesia de [Alberto Ferrari, SQLBI](https://www.sqlbi.com/learning-dax)
> 
> 

