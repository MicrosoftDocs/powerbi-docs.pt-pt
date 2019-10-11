---
title: Compreender como os elementos visuais interagem num relatório
description: Documentação para os utilizadores finais do Power BI que explica como os elementos visuais interagem numa página de relatório.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 3a73656d8de462dfc7d1d9e7ac742d588cc8c810
ms.sourcegitcommit: b7a9862b6da940ddebe61bc945a353f91cd0e4bd
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71943897"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Forma como os elementos visuais efetuam a filtragem cruzada entre si num relatório do Power BI
Um dos recursos incríveis do Power BI é a forma como estão interligados todos os elementos visuais numa página de relatório. Se selecionar um ponto de dados num dos elementos visuais, serão alterados todos os outros elementos visuais na página que contêm esses dados, com base nessa seleção. 

![vídeo de interação dos elementos visuais](media/end-user-interactions/interactions.gif)

## <a name="how-visuals-interact-with-each-other"></a>Como os elementos visuais interagem entre si

Por predefinição, selecionar um ponto de dados num elemento visual numa página de relatório irá efetuar a filtragem cruzada ou o realce cruzado dos restantes elementos visuais na página. O modo exato como interagem os elementos visuais numa página é definido pelo *designer* do relatório. Os *designers* têm opções para ativar e desativar interações visuais e para alterar o comportamento de filtragem cruzada, realce cruzado e [exploração](end-user-drill.md) predefinidos. 

Caso ainda não se tenha deparado com hierarquias ou com a exploração, pode saber tudo sobre as mesmas ao ler este artigo sobre a [desagregação no Power BI](end-user-drill.md). 

A filtragem cruzada e o realce cruzado podem ser úteis para identificar como um valor dos seus dados contribui para outro valor. Por exemplo, selecionar o segmento Moderation (Moderação) no gráfico em anel realça a contribuição desse segmento para cada coluna no gráfico "Total units by Month" (Total de Unidades por Mês) e filtra o gráfico de linhas.

![Imagem de interação dos elementos visuais](media/end-user-interactions/power-bi-interactions.png)

Consulte [Sobre filtragem e realce](end-user-report-filter.md). 


  
> [!NOTE]
> Os termos *filtro cruzado* e *realce cruzado* são utilizados para distinguir o comportamento descrito aqui sobre o que acontece quando utiliza o painel **Filtros** para filtrar e realçar elementos visuais.  

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
- Se o seu relatório tiver um elemento visual que suporte a [exploração](end-user-drill.md) por predefinição, a exploração de um elemento visual não tem impacto nos restantes elementos visuais na página de relatório.     
- Se utilizar o elemento visual A para interagir com o elemento visual B, os filtros ao nível do elemento visual A serão aplicados ao elemento visual B.

## <a name="next-steps"></a>Próximos passos
[Como utilizar filtros de relatório](../power-bi-how-to-report-filter.md)
