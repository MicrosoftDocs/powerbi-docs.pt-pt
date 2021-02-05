---
title: Base de Dados SQL do Azure com DirectQuery
description: Base de Dados SQL do Azure com DirectQuery
author: davidiseminger
ms.author: davidi
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.reviewer: ''
ms.custom: ''
ms.date: 04/28/2020
LocalizationGroup: Data from databases
ms.openlocfilehash: f23a7029f365f35d8f8f9324ff45716f45ba778d
ms.sourcegitcommit: afdc9d41da6a4fced63030648d3f976425131732
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/05/2021
ms.locfileid: "99570066"
---
# <a name="azure-sql-database-with-directquery"></a>Base de Dados SQL do Azure com DirectQuery

Obtenha informações sobre como pode ligar diretamente à Base de Dados SQL do Azure e criar relatórios que utilizam dados dinâmicos. Pode manter os seus dados na origem e não no Power BI.

Com o DirectQuery, as consultas são enviadas de volta para a Base de Dados SQL do Azure à medida que explora os dados na vista de relatório. Esta experiência é sugerida para utilizadores familiarizados com as bases de dados e as entidades às quais se ligam.

> [!Important]
> Esta descrição pressupõe que a base de dados SQL do Azure não está numa VNET ou tem um ponto final de ligação privada ativado.

**Notas:**

* Especifique o nome de servidor completamente qualificado ao ligar (veja abaixo para obter mais detalhes).
* Verifique se as regras de firewall da base de dados estão configuradas como "[Permitir acesso aos serviços do Azure](/azure/sql-database/sql-database-networkaccess-overview#allow-azure-services)".
* Cada ação, como selecionar uma coluna ou adicionar um filtro, enviará uma consulta de volta à base de dados.
* Os mosaicos são atualizados todas as horas (a atualização não tem de ser agendada). Quando ligar, poderá ajustar a frequência da atualização nas Definições avançadas.
* As alterações de esquema não são selecionadas automaticamente.

Estas restrições e notas podem mudar à medida que continuamos a melhorar as experiências. Os passos para ligar são detalhados abaixo.

> [!Important]
> Temos melhorado a nossa conectividade com a Base de Dados SQL do Azure.  Para obter a melhor experiência para se ligar à origem de dados da Base de Dados SQL do Azure, utilize o Power BI Desktop.  Assim que criar o seu modelo e relatório, pode publicá-lo no serviço Power BI.  O conector direto da Base de Dados SQL do Azure no serviço Power BI foi preterido.

## <a name="power-bi-desktop-and-directquery"></a>Power BI Desktop e DirectQuery

Para ligar à Base de Dados SQL do Azure com o DirectQuery, tem de utilizar o Power BI Desktop. Esta abordagem fornece mais flexibilidade e funcionalidades. Os relatórios criados com o Power BI Desktop podem ser publicados no serviço Power BI. Pode obter mais informações sobre como ligar à [Base de Dados SQL do Azure com o DirectQuery](desktop-use-directquery.md) no Power BI Desktop.

## <a name="find-parameter-values"></a>Localizar valores de parâmetros

Pode encontrar o nome de servidor completamente qualificado e o nome da base de dados no portal do Azure.

![Nova atualização do portal do Azure](media/service-azure-sql-database-with-direct-connect/azureportnew_update.png)

![Atualização do portal do Azure](media/service-azure-sql-database-with-direct-connect/azureportal_update.png)

[!INCLUDE [direct-query-sso](../includes/direct-query-sso.md)]

## <a name="next-steps"></a>Próximos passos

* [Utilização do DirectQuery no Power BI Desktop](desktop-use-directquery.md)  
* [O que é o Power BI?](../fundamentals/power-bi-overview.md)  
* [Obter dados para o Power BI](service-get-data.md)  

Mais perguntas? [Pergunte à comunidade do Power BI](https://community.powerbi.com/)