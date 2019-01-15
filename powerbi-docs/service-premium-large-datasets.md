---
title: Suporte do Power BI Premium para conjuntos de dados grandes
description: O Power BI Premium suporta agora conjuntos de dados de até 10 GB.
author: jocaplan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/18/2018
ms.author: jocaplan
LocalizationGroup: Premium
ms.openlocfilehash: 3aa8ef5ea7a51da226d48869bdf255900dee8d6d
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54284202"
---
# <a name="power-bi-premium-support-for-large-datasets"></a>Suporte do Power BI Premium para conjuntos de dados grandes

O Power BI Premium suporta carregamentos de ficheiros do Power BI Desktop (.pbix) com até 10 GB. Após ser carregado, pode atualizar um conjunto de dados para um tamanho de até 12 GB. Para utilizar um conjunto de dados grande, publique-o numa área de trabalho com capacidade Premium.
 
## <a name="best-practices"></a>Melhores práticas

Esta secção descreve as melhores práticas para trabalhar com conjuntos de dados grandes.

Os **modelos grandes podem exigir bastantes recursos** à sua capacidade. Recomendamos, no mínimo, um SKU P1 para os modelos superiores a 1 GB. Embora a publicação de modelos grandes em áreas de trabalho suportadas por SKUs A até ao A3 possa funcionar, não poderá atualizá-los.

A seguinte tabela descreve os SKUs recomendados para vários tamanhos de ficheiro .pbix:

   |SKU  |Tamanho do ficheiro .pbix   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3, P4 e P5    | até 10 GB   |

O SKU A4 do Power BI Embedded é igual ao SKU P1, A5 = P2 e A6 = P3. Tenha em atenção que a publicação de modelos grandes em SKUs A e EM poderá devolver erros que não são específicos ao erro de limitação do tamanho dos modelos na capacidade partilhada. É provável que os erros de atualização de modelos grandes em SKUs A e EM indiquem limites de tempo excedidos como a causa. Estamos a trabalhar para melhorar as mensagens de erro nestes cenários.

**Os seus ficheiros .pbix representam dados num estado altamente comprimido**. Provavelmente, os dados serão expandidos várias vezes quando forem carregados na memória. A partir daí, poderão ser expandidos mais algumas vezes durante a atualização de dados.

**A atualização agendada de conjuntos de dados grandes pode demorar muito tempo** e exigir bastantes recursos. Por esse motivo, não agende demasiadas atualizações sobrepostas. Tenha em atenção que o tempo limite das tarefas de atualização agendadas foi duplicado para quatro horas para todos os conjuntos de dados nesta capacidade. Recomendamos a [atualização incremental](service-premium-incremental-refresh.md) devido a ser mais rápida e fiável e ao facto de consumir menos recursos.

**A carga de relatórios inicial de conjuntos de dados pode ser muito demorada**, se a última utilização do conjunto de dados tiver sido feita há algum tempo, pois o modelo é carregado na memória da sua capacidade Premium. Uma barra de carregamento para relatórios de carregamento mais demorado apresenta o progresso do carregamento.

**Se remover a área de trabalho da capacidade Premium**, o modelo e os dashboards e relatórios associados não funcionarão.

**Embora a memória por consulta e as restrições de tempo sejam muito superiores na capacidade Premium**, é altamente recomendada a utilização de filtros e segmentações de dados para limitar os elementos visuais para apresentar apenas o que é necessário.

**Próximos passos**

[O que é o Power BI Premium?](service-premium.md)
[Notas de versão do Power BI Premium](service-premium-release-notes.md)
[Microsoft Power BI Premium whitepaper](https://aka.ms/pbipremiumwhitepaper)
 (Documento técnico do Microsoft Power BI Premium) [Documento técnico Planning a Power BI Enterprise Deployment](https://aka.ms/pbienterprisedeploy) (Planear uma Implementação Empresarial do Power BI)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
