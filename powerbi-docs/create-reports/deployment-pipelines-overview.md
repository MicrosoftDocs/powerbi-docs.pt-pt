---
title: Descrição geral dos pipelines de implementação
description: Saiba o que são os pipelines de implementação no Power BI
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: be945d1d9612804a90c14c47d2c468f5ed5a843f
ms.sourcegitcommit: 008467dc9d4f88f91728c59caeb68b7db94f267c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/07/2020
ms.locfileid: "82885036"
---
# <a name="introduction-to-deployment-pipelines-preview"></a>Introdução aos pipelines de implementação (pré-visualização)

No mundo de hoje, a análise é uma parte vital da tomada de decisão em quase todas as organizações. A utilização crescente do Power BI como ferramenta de análise requer a utilização de mais dados, que seja apelativo e fácil de utilizar. Acima de tudo, o Power BI precisa de estar sempre disponível e ser fiável. Para satisfazer estes requisitos, os criadores do BI devem colaborar de forma eficaz.

Os pipelines de implementação são uma ferramenta eficiente e reutilizável que permite aos criadores do BI numa empresa com capacidade Premium gerirem o ciclo de vida dos conteúdos organizacionais. Gestão essa que permite desenvolver e testar conteúdos do Power BI, como relatórios, dashboards e conjuntos de dados, antes de serem consumidos pelos utilizadores finais.

A ferramenta foi concebida como um pipeline com três fases:

* **<a name="development"></a>Desenvolvimento**
    
    Esta fase serve para conceber, criar e carregar novos conteúdos com outros criadores. Esta é a primeira fase nos pipelines de implementação.

* **<a name="test"></a>Teste**

    Depois de carregar o conteúdo e de todas as alterações serem feitas na fase de desenvolvimento, o conteúdo pode ser movido para esta fase para testes. Veja a seguir três exemplos do que pode ser feito no ambiente de teste:

    * Partilhar conteúdo com técnicos de teste e revisores

    * Carregar e executar testes com volumes de dados de maiores dimensões

    * Testar a aplicação para ver qual o aspeto para os utilizadores finais

* **<a name="production"></a>Produção**

    Após testar o conteúdo, utilize a fase de produção para partilhar a versão final do conteúdo com os utilizadores empresariais em toda a organização.

![pipelines de implementação](media/deployment-pipelines-overview/deployment-pipelines.png)

## <a name="next-steps"></a>Próximos passos

>[!div class="nextstepaction"]
>[Começar a utilizar os pipelines de implementação](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[Compreender o processo dos pipelines de implementação](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[Resolução de problemas dos pipelines de implementação](deployment-pipelines-troubleshooting.md)

>[!div class="nextstepaction"]
>[Melhores práticas dos pipelines de implementação](deployment-pipelines-best-practices.md)