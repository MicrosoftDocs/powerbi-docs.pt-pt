---
title: Power BI REST API limitations (Limitações da API REST do Power BI)
description: A API REST do Power BI tem as seguintes limitações
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 6699167cecebea5085eff4621c077096fd4c6c2e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61385149"
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