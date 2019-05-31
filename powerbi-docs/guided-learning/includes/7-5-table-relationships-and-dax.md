---
ms.openlocfilehash: cd6ea6fd52f929e2cd254214cf0e8c96e858f6c2
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61273634"
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

> Conteúdo de vídeo cortesia de [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax)
> 
> 

