---
title: Descrição geral dos pipelines de implementação
description: Saiba o que são os pipelines de implementação no Power BI
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 09/09/2020
ms.openlocfilehash: 3994a5cdad4d80c87d4153ffe57af685d7a21d36
ms.sourcegitcommit: 92b033ee7a6e36808371b247b7b41536cee6c2f6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/10/2020
ms.locfileid: "90008589"
---
# <a name="introduction-to-deployment-pipelines-preview"></a>Introdução aos pipelines de implementação (pré-visualização)

No mundo de hoje, a análise é uma parte vital da tomada de decisão em quase todas as organizações. A utilização crescente do Power BI como ferramenta de análise requer a utilização de mais dados, que seja apelativo e fácil de utilizar. Acima de tudo, o Power BI precisa de estar sempre disponível e ser fiável. Para satisfazer estes requisitos, os criadores do BI devem colaborar de forma eficaz.

A ferramenta de pipelines de implementação permite aos criadores do BI gerir o ciclo de vida dos conteúdos organizacionais. A ferramenta é eficiente e reutilizável para os criadores numa empresa com capacidade Premium. A ferramenta permite aos criadores desenvolver e testar conteúdos do Power BI, antes de os conteúdos serem consumidos pelos utilizadores. Os tipos de conteúdo incluem relatórios, dashboards e conjuntos de dados.

A ferramenta foi concebida como um pipeline com três fases:

* **<a name="development"></a>Desenvolvimento**
    
    Esta fase serve para conceber, criar e carregar novos conteúdos com outros criadores. Esta é a primeira fase nos pipelines de implementação.

* **<a name="test"></a>Teste**

    Está pronto para entrar na fase de teste, após ter feito todas as alterações aos seus conteúdos. Basta carregar os conteúdos modificados para que possam ser movidos para esta fase de teste. Eis três exemplos daquilo que pode ser feito no ambiente de teste:

    * Partilhar conteúdo com técnicos de teste e revisores

    * Carregar e executar testes com volumes de dados de maiores dimensões

    * Testar a aplicação para ver qual o aspeto para os utilizadores finais

* **<a name="production"></a>Produção**

    Após testar o conteúdo, utilize a fase de produção para partilhar a versão final do conteúdo com os utilizadores empresariais em toda a organização.

![Uma captura de ecrã de um pipeline de implementação em funcionamento com as três fases, desenvolvimento, teste e produção, povoadas.](media/deployment-pipelines-overview/deployment-pipelines.png)

## <a name="next-steps"></a>Próximos passos

>[!div class="nextstepaction"]
>[Começar a utilizar os pipelines de implementação](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[Compreender o processo dos pipelines de implementação](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[Resolução de problemas dos pipelines de implementação](deployment-pipelines-troubleshooting.md)

>[!div class="nextstepaction"]
>[Melhores práticas dos pipelines de implementação](deployment-pipelines-best-practices.md)
