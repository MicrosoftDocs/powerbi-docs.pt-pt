---
title: "Visualizações personalizadas certificadas no Power BI"
description: "Requisitos e processo de submissão de um visual personalizado para certificação. E uma lista de visuais personalizados já certificados."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/20/2017
ms.author: mihart
ms.openlocfilehash: 3d51475b300fadc55f33960b03c3adc0031a39b8
ms.sourcegitcommit: 12236d08c27c7ee3fabb7ef9d767e9dee693f8aa
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/21/2017
---
# <a name="getting-a-custom-visual-certified"></a>Obter um visual personalizado *certificado*
## <a name="what-is-meant-by-certified"></a>O que se entende por *certificado*?
Um *visual personalizado certificado* é um que cumpre um conjunto de requisitos de código e passou testes rigorosos de segurança.  Após um visual personalizado ser certificado, este pode ser [exportado para o PowerPoint](service-publish-to-powerpoint.md), e será apresentado nos e-mails recebidos quando um utilizador [subscrever as páginas de relatórios](service-report-subscribe.md).

É um programador Web e está interessado em criar as suas próprias visualizações e adicioná-las ao [Microsoft AppSource](https://appsource.microsoft.com)? Consulte [Introdução ás Ferramentas de Programador](service-custom-visuals-getting-started-with-developer-tools.md) para saber como.


## <a name="certification-requirements"></a>Requisitos de certificação
* Aprovado pelo Microsoft AppSource    
* O visual personalizado foi criado para a API com versão 1.2 ou superior    
* Repositório de código disponível para revisão (por exemplo, Visual Code que nos é disponibilizado através do GitHub)    
* Utiliza apenas componentes OSS que podem ser revistos publicamente    
* Não acede a serviços ou recursos externos    

> **Sugestão**: recomendamos que utilize o EsLint com o conjunto predefinido de regras de segurança, para pré-validar o seu código antes da submissão.
> 
> 

## <a name="process-for-submitting-a-custom-visual-for-certification"></a>Processo de submissão de um visual personalizado para Certificação
Para enviar um visual personalizado para certificação:

1. Envie um e-mail para o Suporte dos Elementos Visuais Personalizados do Power BI (pbicvsupport@microsoft.com). No e-mail, inclua as seguintes informações:    
   
   * Título: Pedido de Certificação Visual    
   * Forneça uma ligação para o repositório do GitHub onde se situa o código-fonte do visual    
   * Cumprir os requisitos (ver acima)    
   * Passar a revisão de código e segurança    
2. A equipa de Elementos Visuais Personalizados na Microsoft irá notificá-lo de que o seu visual personalizado foi certificado e adicionado à lista de Certificados (abaixo) ou rejeitado, com um relatório dos problemas a corrigir. É da responsabilidade do programador manter uma linha aberta de comunicação com a Microsoft e atualizar os visuais Certificados conforme necessário.

## <a name="removal-of-power-bi-certified-custom-visuals"></a>Remoção dos visuais personalizados Certificados do Power BI
A Microsoft pode remover um visual da lista de Certificados a seu critério exclusivo.  

## <a name="list-of-custom-visuals-that-have-been-certified"></a>Lista de visuais personalizados que foram certificados
| Ligação para o AppSource | Ligação para o vídeo |
| --- | --- |
| [Gráfico Aster](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759?src=office&tab=Overview) | |
| [Gráfico de laço da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838?src=office&tab=Overview) |[Vídeo](https://youtu.be/So5xKMSpVJI) |
| [BciCalendar (Calendário Beyondsoft)](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381096?src=office&tab=Overview)  | |
| [Caixa e Bigodes](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831?src=office&tab=Overview) | |
| [Gráfico de Marcas](https://store.office.com/app.aspx?assetid=WA104380755) |[Vídeo1](https://youtu.be/AOlsFYkfkcw)   [Vídeo2](https://youtu.be/AQvd2FhRyCI) |
| [Gráfico de Marcas da OKViz](https://store.office.com/bullet-chart-by-okviz-WA104380953.aspx) |[Vídeo](https://youtu.be/mtvUNl9bMjA) |
| [Calendário da Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146?src=office&tab=Overview) | |
| [Segmentação de teclas](https://store.office.com/chiclet-slicer-WA104380756.aspx) |[Vídeo](https://youtu.be/iYOkJ1APueY) |
| [Gráfico de Cordas](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761?src=office&tab=Overview) |[Vídeo](https://youtu.be/AQvd2FhRyCI) |
| [Medidor circular da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837?tab=Overview) | |
| [Medidor cilíndrico](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874) | |
| [Medidor de marcação](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184) |[Vídeo](https://youtu.be/AOlsFYkfkcw) |
| [Gráfico de anel da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824?tab=Overview) |[Vídeo](https://youtu.be/pDToHDFHnq8) |
| [Gráfico de Pontos da OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104381101?src=office&tab=Overview) |[Vídeo](https://youtu.be/4lskRgcpFJY) |
| [Gráfico de anel de desagregação da ZoomCharts](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858) | |
| [Dual KPI](https://store.office.com/dual-kpi-WA104380774.aspx) |[Vídeo](https://youtu.be/821o0-eVBXo?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x) |
| [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112?src=office&tab=Overview) | |
| Enlighten World Flags - disponível em breve | |
| Enlighten Stack Shuffle - disponível em breve | |
| [Gantt](https://store.office.com/gantt-WA104380765.aspx) |[Vídeo](https://youtu.be/qJ7s_KrGiUU) |
| [Histograma](https://store.office.com/histogram-chart-WA104380776.aspx) | |
| [Funil Horizontal](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846) |[Vídeo](https://youtu.be/SudZei68PPo) |
| [Indicador KPI](https://store.office.com/kpi-indicator-WA104380832.aspx) | |
| [Medidor linear da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821?src=office&tab=Overview) |[Vídeo](https://youtu.be/AOlsFYkfkcw) |
| [Gráfico Mekko](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785?src=office&tab=Overview)  | [Vídeo](https://youtu.be/90FLCKpgicA)|
| [Play Axis (Segmentação de Dados Dinâmica)](https://store.office.com/play-axis-dynamic-slicer-WA104380981.aspx) | |
| [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083) |[Vídeo](https://youtu.be/IvfIP3E6-1Q) |
| [Gráfico de radar](https://store.office.com/radar-chart-WA104380771.aspx) | |
| [Gráfico de anel da MAQSoftware](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380824?src=office&tab=Overview) | [Vídeo](https://youtu.be/pDToHDFHnq8)|
| [Gráfico Sankey](https://store.office.com/app.aspx?assetid=WA104380777.aspx) |[Vídeo](https://youtu.be/WWP9wVUHGaA) |
| [Deslocador](https://store.office.com/scroller-WA104381018.aspx) |[Vídeo](https://youtu.be/uhRFQF2cGSY) |
| [Smart Filter da SQLBI](https://store.office.com/smart-filter-by-okviz-WA104380859.aspx) |[Vídeo](https://youtu.be/gcJsDDRQq28) |
| [Sparkline da OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910?src=office&tab=Overview) |[Vídeo](https://youtu.be/0m3Vnvso9tY) |
| [Sunburst](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767?src=office&tab=Overview) | |
| [Tacómetro](https://store.office.com/tachometer-WA104380937.aspx?) |[Vídeo](https://www.youtube.com/watch?v=C3OXdETbS9o) |
| [Termómetro](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847?src=office&tab=Overview) | [Vídeo](https://youtu.be/SPX9mgrAdBc)|
| [Decomposição de série temporal](https://appsource.microsoft.com/product/power-bi-visuals/WA104380897) | |
| [Mapa de Calor de Tabela](https://store.office.com/table-heatmap-WA104380818.aspx) | |
| [Encapsulador de texto](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826) | |
| [Segmentação de linha cronológica](https://store.office.com/timeline-slicer-WA104380786.aspx) |[Vídeo](https://youtu.be/ozMtZ4_NZ10) |
| [Gráfico de tornado](https://store.office.com/tornado-chart-WA104380768.aspx) |[Vídeo](https://youtu.be/AQvd2FhRyCI) |
| [Gráfico de bolacha](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049?src=office&tab=Overview) |[Vídeo](https://youtu.be/1vRqYUsm3Vk) |
| [Nuvem de Palavras](https://store.office.com/word-cloud-WA104380752.aspx?) |[Vídeo](https://www.youtube.com/watch?v=AblTenl9fqo) |

## <a name="next-steps"></a>Próximos passos
[Introdução às ferramentas de programador de visuais personalizados (Pré-visualização)](service-custom-visuals-getting-started-with-developer-tools.md)      
[Lista de reprodução visual personalizada da Microsoft no YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
[Visualizações no Power BI](power-bi-report-visualizations.md)  
[Visualizações Personalizadas no Power BI](power-bi-custom-visuals.md)  
[Publicar visuais personalizados no Microsoft AppSource](developer/office-store.md)  
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

