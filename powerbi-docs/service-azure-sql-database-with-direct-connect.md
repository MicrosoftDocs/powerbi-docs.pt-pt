---
title: Base de Dados SQL do Azure com DirectQuery
description: Base de Dados SQL do Azure com DirectQuery
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 06/20/2018
LocalizationGroup: Data from databases
ms.openlocfilehash: 5365c076b75d0989df8db15c1dc16f4e11bc3f09
ms.sourcegitcommit: c539726c9c180e899a8a34443e3fda2b9848beb2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/31/2019
ms.locfileid: "66448363"
---
# <a name="azure-sql-database-with-directquery"></a>Base de Dados SQL do Azure com DirectQuery

Obtenha informações sobre como pode ligar diretamente à Base de Dados SQL do Azure e criar relatórios que utilizam dados dinâmicos. Pode manter os seus dados na origem e não no Power BI.

Com o DirectQuery, as consultas são enviadas de volta para a Base de Dados SQL do Azure à medida que explora os dados na vista de relatório. Esta experiência é sugerida para utilizadores familiarizados com as bases de dados e as entidades às quais se ligam.

**Notas:**

* Especifique o nome de servidor completamente qualificado ao ligar (veja abaixo para obter mais detalhes)
* Verifique se as regras de firewall da base de dados estão configuradas como “[Permitir acesso aos serviços do Azure](https://msdn.microsoft.com/library/azure/ee621782.aspx)”
* Cada ação, como selecionar uma coluna ou adicionar um filtro, enviará uma consulta de volta à base de dados
* Os mosaicos são atualizados todas as horas (a atualização não tem de ser agendada). Isto pode ser ajustado nas Definições avançadas quando ligar.
* As Perguntas e Respostas não estão disponíveis para conjuntos de dados do DirectQuery
* As alterações de esquema não são aplicadas automaticamente

Estas restrições e notas podem mudar à medida que continuamos a melhorar as experiências. Os passos para ligar são detalhados abaixo.

> [!Important]
> Temos melhorado a nossa conectividade com a Base de Dados SQL do Azure.  Para obter a melhor experiência para se ligar à origem de dados da Base de Dados SQL do Azure, utilize o Power BI Desktop.  Assim que criar o seu modelo e relatório, pode publicá-lo no serviço Power BI.  O conector direto da Base de Dados SQL do Azure no serviço Power BI foi preterido.

## <a name="power-bi-desktop-and-directquery"></a>Power BI Desktop e DirectQuery

Para ligar à Base de Dados SQL do Azure com o DirectQuery, terá de utilizar o Power BI Desktop. Esta abordagem fornece mais flexibilidade e funcionalidades. Os relatórios criados com o Power BI Desktop podem ser publicados no serviço Power BI. Pode obter mais informações sobre como ligar à [Base de Dados SQL do Azure com o DirectQuery](desktop-use-directquery.md) no Power BI Desktop.

## <a name="finding-parameter-values"></a>Localizar Valores de Parâmetro

O nome de servidor completamente qualificado e o nome da base de dados podem ser encontrados no portal do Azure.

![Nova atualização do portal do Azure](media/service-azure-sql-database-with-direct-connect/azureportnew_update.png)

![Atualização do portal do Azure](media/service-azure-sql-database-with-direct-connect/azureportal_update.png)

[!INCLUDE [direct-query-sso](includes/direct-query-sso.md)]

## <a name="next-steps"></a>Próximos passos

* [Utilização do DirectQuery no Power BI Desktop](desktop-use-directquery.md)  
* [O que é o Power BI?](power-bi-overview.md)  
* [Obter Dados para o Power BI](service-get-data.md)  

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)
