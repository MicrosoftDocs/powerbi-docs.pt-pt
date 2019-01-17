---
title: Power BI REST API limitations (Limitações da API REST do Power BI)
description: A API REST do Power BI tem as seguintes limitações
author: markingmyname
manager: kfile
ms.author: maghan
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: df17563d384359fe33123ed87743754bb33bf04d
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54277990"
---
# <a name="power-bi-rest-api-limitations"></a>Power BI REST API limitations (Limitações da API REST do Power BI)  
  
**Para Linhas POST**  
  
* Máx. de 75 colunas
* Máx. de 75 tabelas
* Máx. de 10 000 linhas por pedido de linhas POST único  
* 1 000 000 linhas adicionadas por hora, por conjunto de dados  
* Máx. de 5 pedidos de linhas POST pendentes por conjunto de dados  
* 120 pedidos de linhas POST por minuto, por conjunto de dados
* Se a tabela tiver 250 000 linhas ou mais, 120 pedidos de linhas POST por hora, por conjunto de dados    
* Máx. de 200 000 linhas armazenadas por tabela no conjunto de dados FIFO  
* Máx. de 5 000 000 linhas armazenadas por tabela no conjunto de dados “nenhuma política de retenção”  
* 4000 carateres por valor para a coluna da cadeia na operação de linhas POST
  
## <a name="see-also"></a>Veja também

[Limites e restrições do serviço Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-service-limits-restrictions)   
[Visão geral da API REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/)