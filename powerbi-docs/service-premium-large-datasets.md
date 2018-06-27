---
title: Suporte do Power BI Premium para conjuntos de dados grandes
description: O Power BI Premium suporta agora conjuntos de dados de até 10 GB.
author: jocaplan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 02/27/2018
ms.author: jocaplan
LocalizationGroup: Premium
ms.openlocfilehash: fa05fd6808ebe78d5d17e2ad3d93fbcf22f7d3c9
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/26/2018
ms.locfileid: "34298602"
---
# <a name="power-bi-premium-support-for-large-datasets"></a>Suporte do Power BI Premium para conjuntos de dados grandes

O Power BI Premium suporta carregamentos de ficheiros do Power BI Desktop (.pbix) com até 10 GB. Após ser carregado, pode atualizar um conjunto de dados para um tamanho de até 12 GB. Para utilizar um conjunto de dados grande, publique-o numa área de trabalho com capacidade Premium.
 
## <a name="best-practices"></a>Melhores práticas

Esta secção descreve as melhores práticas para trabalhar com conjuntos de dados grandes.

**Os modelos grandes podem exigir bastantes recursos** à sua capacidade. Recomendamos, no mínimo, um SKU P1 para os modelos superiores a 1 GB. A seguinte tabela descreve os SKUs recomendados para vários tamanhos de ficheiro .pbix:


   |SKU  |Tamanho do ficheiro .pbix   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3    | até 10 GB   |



**Os seus ficheiros .pbix representam dados num estado altamente comprimido**. Provavelmente, os dados serão expandidos várias vezes quando forem carregados na memória. A partir daí, poderão ser expandidos mais algumas vezes durante a atualização de dados.

**A atualização agendada de conjuntos de dados grandes pode demorar muito tempo** e exigir bastantes recursos. Por esse motivo, não agende demasiadas atualizações sobrepostas. Tenha em atenção que o tempo limite das tarefas de atualização agendadas foi duplicado para quatro horas para todos os conjuntos de dados nesta capacidade.

**A carga de relatórios inicial de conjuntos de dados pode ser muito demorada**, se a última utilização do conjunto de dados tiver sido feita há algum tempo, pois o modelo é carregado na memória da sua capacidade Premium. Uma barra de carregamento para relatórios de carregamento mais demorado apresenta o progresso do carregamento.

**Se remover a área de trabalho da capacidade Premium**, o modelo e os dashboards e relatórios associados não funcionarão.

**Apesar de a memória por consulta e as restrições de tempo serem muito superiores na capacidade Premium**, é altamente recomendada a utilização de filtros e segmentações de dados para limitar os elementos visuais para apresentar apenas o que é necessário.

## <a name="next-steps"></a>Próximos passos
[Power BI Premium – o que é?](service-premium.md)  
[Notas de versão do Power BI Premium](service-premium-release-notes.md)  
[Documento técnico do Microsoft Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  
[Documento técnico sobre Planear uma Implementação Empresarial do Power BI](https://aka.ms/pbienterprisedeploy)  
[Ativação da Versão de Avaliação Pro Expandida](service-extended-pro-trial.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
