---
title: Introdução ao Power BI com aplicações de terceiros
description: Introdução ao Power BI com aplicações de terceiros
author: maggiesMSFT
ms.author: maggies
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.reviewer: ''
ms.cunstom: ''
ms.date: 01/12/2021
LocalizationGroup: Get started
ms.openlocfilehash: b22ecdd806371455149f277b9114b1eaf315ce6d
ms.sourcegitcommit: ab28cf07b483cb4b01a42fa879b788932bba919d
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/15/2021
ms.locfileid: "98227060"
---
# <a name="get-started-with-third-party-apps"></a>Introdução com aplicações de terceiros

Com o Power BI, pode utilizar uma aplicação criada por uma empresa ou indivíduo diferente da Microsoft. Por exemplo, pode utilizar uma aplicação de terceiros que integre mosaicos do Power BI numa aplicação Web interna personalizada. Quando utiliza uma aplicação de terceiros, ser-lhe-á pedido que conceda a essa aplicação determinadas permissões para a conta e os recursos do Power BI. É importante que conceda apenas permissões às aplicações que conhece e confia. As permissões para uma aplicação podem ser revogadas em qualquer momento. Consulte [Revogar permissões de aplicações de terceiros](#revoke).

Aqui estão os tipos de acesso que uma aplicação pode pedir.

## <a name="power-bi-app-permissions"></a>Permissões de Aplicação do Power BI

* **Ver todos os dashboards**
  
  * Esta permissão permite a uma aplicação ver todos os dashboards a que tem acesso. Isto inclui dashboards dos quais é proprietário, que tenha obtido a partir de aplicações, que tenham sido partilhados consigo e que estejam em grupos a que pertence. A aplicação não pode efetuar quaisquer alterações ao dashboard. Entre outras coisas, esta permissão pode ser utilizada por uma aplicação para incorporar o conteúdo do dashboard nas suas experiências.

* **Ver todos os relatórios**
  
  * Esta permissão permite a uma aplicação ver todos os relatórios a que tem acesso. Isto inclui relatórios dos quais é proprietário, que tenha obtido a partir de aplicações e que estejam em grupos a que pertence. Parte da visualização do relatório significa que a aplicação também pode ver os respetivos dados. A aplicação não pode fazer modificações aos relatórios em si. Entre outras coisas, esta permissão pode ser utilizada por uma aplicação para incorporar o conteúdo do relatório nas suas experiências.

* **Ver todos os conjuntos de Dados**
  
  * Esta permissão permite a uma aplicação listar todos os conjuntos de dados aos quais tem acesso. Isto inclui conjuntos de dados dos quais é proprietário, que tenha obtido a partir de aplicações e que estejam em grupos a que pertence. Uma aplicação pode ver os nomes de todos os seus conjuntos de dados, bem como a estrutura, incluindo nomes de tabela e coluna. Esta permissão concede direitos para ler os dados num conjunto de dados. A permissão não concede à aplicação direitos para adicionar ou fazer alterações a um conjunto de dados.
* **Ler e escrever todos os conjuntos de dados**
  
  * Esta permissão permite a uma aplicação listar todos os conjuntos de dados aos quais tem acesso. Isto inclui conjuntos de dados dos quais é proprietário, que tenha obtido a partir de aplicações e que estejam em grupos a que pertence. Uma aplicação pode ver os nomes de todos os seus conjuntos de dados, bem como a estrutura, incluindo nomes de tabela e coluna. Esta permissão concede direitos para ler e escrever os dados num conjunto de dados. A aplicação também pode criar novos conjuntos de dados ou efetuar alterações aos já existentes. Isto é normalmente utilizado por uma aplicação para enviar dados diretamente para o Power BI.

* **Ver grupos do utilizador**
  
  * Esta permissão permite à aplicação listar todos os grupos dos quais é membro. Pode utilizar esta permissão, juntamente com algumas das outras permissões listados, para ver ou atualizar conteúdos de um grupo específico. A aplicação não pode fazer modificações ao grupo em si.

<a name="revoke"/>

## <a name="revoke-third-party-app-permissions"></a>Revogar permissões de aplicações de terceiros

Pode revogar as permissões de uma aplicação de terceiros ao aceder ao site As Minhas Aplicações do Office 365.

No site **As minhas aplicações do Office 365**, eis como revogar permissões de terceiros:

1. Aceda ao [site As minhas aplicações do Office 365](https://portal.office.com/myapps).

2. Na página **As minhas aplicações**, localize a aplicação de terceiros.

3. Coloque o cursor sobre o mosaico da aplicação, clique no botão **(…)**  e em **Remover**.

   ![A captura de ecrã mostra a opção Remover para revogar permissões de terceiros.](media/service-power-bi-get-started-third-party-apps/remove.png)