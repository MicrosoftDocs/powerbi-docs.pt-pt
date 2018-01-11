---
title: Base de Dados SQL do Azure com DirectQuery
description: Base de Dados SQL do Azure com DirectQuery
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/10/2017
ms.author: asaxton
ms.openlocfilehash: 83613f0ed915a03b65b90d4bf61e37568b922182
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="azure-sql-database-with-directquery"></a>Base de Dados SQL do Azure com DirectQuery
Obtenha informações sobre como pode ligar diretamente à Base de Dados SQL do Azure e criar relatórios que utilizam dados dinâmicos. Pode manter os seus dados na origem e não no Power BI.

Com o DirectQuery, as consultas são enviadas de volta para a Base de Dados SQL do Azure à medida que explora os dados na vista de relatório. Esta experiência é sugerida para utilizadores familiarizados com as bases de dados e as entidades às quais se ligam.

**Notas:**

* Especifique o nome de servidor completamente qualificado ao ligar (veja abaixo para obter mais detalhes)
* Certifique-se de que as regras de firewall da base de dados estão configuradas para “[Permitir acesso aos serviços do Azure](https://msdn.microsoft.com/library/azure/ee621782.aspx)”.
* Cada ação, como selecionar uma coluna ou adicionar um filtro, enviará uma consulta de volta à base de dados
* Os mosaicos são atualizados aproximadamente a cada 15 minutos (a atualização não tem de ser agendada). Isto pode ser ajustado nas Definições avançadas quando ligar.
* As Perguntas e Respostas não estão disponíveis para conjuntos de dados do DirectQuery
* As alterações de esquema não são aplicadas automaticamente

Estas restrições e notas podem mudar à medida que continuamos a melhorar as experiências. Os passos para ligar são detalhados abaixo. 

## <a name="power-bi-desktop-and-directquery"></a>Power BI Desktop e DirectQuery
Para ligar à Base de Dados SQL do Azure com o DirectQuery, terá de utilizar o Power BI Desktop. Esta abordagem fornece mais flexibilidade e capacidades. Os relatórios criados com o Power BI Desktop podem ser publicados no serviço Power BI. Pode obter mais informações sobre como ligar à [Base de Dados SQL do Azure com o DirectQuery](desktop-use-directquery.md) no Power BI Desktop. 

## <a name="connecting-through-power-bi"></a>Ligar através do Power BI
Já não pode ligar à Base de Dados SQL do Azure SQL diretamente a partir do serviço Power BI. Quando seleciona o [conector da Base de Dados SQL do Azure](https://app.powerbi.com/getdata/bigdata/azure-sql-database-with-live-connect), é-lhe pedido que efetue a ligação no Power BI Desktop. Em seguida, pode publicar os seus relatórios do Power BI Desktop no serviço Power BI. 

![](media/service-azure-sql-database-with-direct-connect/azure-sql-database-in-power-bi.png)

### <a name="finding-parameter-values"></a>Localizar Valores de Parâmetros
O nome de servidor completamente qualificado e o nome da base de dados podem ser encontrados no Portal do Azure.

![](media/service-azure-sql-database-with-direct-connect/azureportnew_update.png)

![](media/service-azure-sql-database-with-direct-connect/azureportal_update.png)

## <a name="next-steps"></a>Próximos passos
[Utilização do DirectQuery no Power BI Desktop](desktop-use-directquery.md)  
[Introdução ao Power BI](service-get-started.md)  
[Obter dados para o Power BI](service-get-data.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

