---
title: Introdução ao Power BI com aplicações de terceiros
description: Introdução ao Power BI com aplicações de terceiros
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.cunstom: ''
ms.date: 08/10/2017
LocalizationGroup: Get started
ms.openlocfilehash: 11afe27ffbca295eec67fd07731cc646bcca56dc
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769696"
---
# <a name="get-started-with-third-party-apps"></a>Introdução com aplicações de terceiros

Com o Power BI, pode utilizar uma aplicação criada por uma empresa ou indivíduo diferente da Microsoft. Por exemplo, poderá utilizar uma aplicação de terceiros que se integra mosaicos do Power BI numa aplicação web personalizados internos. Quando utiliza uma aplicação de terceiros, será solicitado a conceder essa aplicação determinadas permissões para a sua conta do Power BI e recursos. É importante que conceda apenas permissões às aplicações que conhece e confia. As permissões para uma aplicação podem ser revogadas em qualquer momento. Consulte [Revogar permissões de aplicações de terceiros](#revoke).

Aqui estão os tipos de acesso que uma aplicação pode pedir.

## <a name="power-bi-app-permissions"></a>Permissões de Aplicação do Power BI

* **Ver todos os dashboards**
  
  * Esta permissão permite a uma aplicação ver todos os dashboards a que tem acesso. Isto inclui dashboards de que é proprietário, que obteve a partir de pacotes de conteúdos, que foram partilhados consigo e que estão em grupos a que pertenceu. A aplicação não pode efetuar quaisquer alterações ao dashboard. Entre outras coisas, esta permissão pode ser utilizada por uma aplicação para incorporar o conteúdo do dashboard nas suas experiências.

* **Ver todos os relatórios**
  
  * Esta permissão permite a uma aplicação ver todos os relatórios a que tem acesso. Isto inclui dashboards de que é proprietário, que obteve a partir de pacotes de conteúdos e que estão em grupos a que pertenceu. Parte da visualização do relatório significa que a aplicação também pode ver os respetivos dados. A aplicação não pode fazer modificações aos relatórios em si. Entre outras coisas, esta permissão pode ser utilizada por uma aplicação para incorporar o conteúdo do relatório nas suas experiências.

* **Ver todos os conjuntos de Dados**
  
  * Esta permissão permite a uma aplicação listar todos os conjuntos de dados aos quais tem acesso. Isto inclui conjuntos de dados de que é proprietário, que obteve a partir de pacotes de conteúdos e que estão em grupos a que pertenceu. Uma aplicação pode ver os nomes de todos os seus conjuntos de dados, bem como a estrutura, incluindo nomes de tabela e coluna. Esta permissão concede direitos para ler os dados num conjunto de dados. A permissão não concede à aplicação direitos para adicionar ou fazer alterações a um conjunto de dados.
* **Ler e escrever todos os conjuntos de dados**
  
  * Esta permissão permite a uma aplicação listar todos os conjuntos de dados aos quais tem acesso. Isto inclui conjuntos de dados de que é proprietário, que obteve a partir de pacotes de conteúdos e que estão em grupos a que pertenceu. Uma aplicação pode ver os nomes de todos os seus conjuntos de dados, bem como a estrutura, incluindo nomes de tabela e coluna. Esta permissão concede direitos para ler e escrever os dados num conjunto de dados. A aplicação também pode criar novos conjuntos de dados ou efetuar alterações aos já existentes. Isto é normalmente utilizado por uma aplicação para enviar dados diretamente para o Power BI.

* **Ver grupos do utilizador**
  
  * Esta permissão permite à aplicação listar todos os grupos dos quais é membro. Pode utilizar esta permissão, juntamente com algumas das outras permissões listados, para ver ou atualizar conteúdos de um grupo específico. A aplicação não pode fazer modificações ao grupo em si.

<a name="revoke"/>

## <a name="revoke-third-party-app-permissions"></a>Revogar permissões de aplicações de terceiros

Revogar as permissões para uma aplicação de terceiros ao aceder ao site as minhas aplicações do Office 365.

Sobre o **Office 365 minhas aplicações** do site, eis como revogar permissões de terceiros:

1. Aceda ao [site As minhas aplicações do Office 365](https://portal.office.com/myapps).

2. Sobre o **as minhas aplicações** página, localize a aplicação de terceiros.

3. Coloque o cursor sobre o mosaico da aplicação, clique no botão **(…)**  e em **Remover**.

   ![Remover](media/service-power-bi-get-started-third-party-apps/remove.png)