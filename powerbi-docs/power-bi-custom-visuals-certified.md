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
ms.date: 01/12/2018
ms.author: mihart
ms.openlocfilehash: 955435ee526c6acae8f478539641529515e2e0a8
ms.sourcegitcommit: 259d7689bcb1683d4d63a245a9b02becea072139
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="getting-a-custom-visual-certified"></a>Obter um visual personalizado *certificado*
## <a name="what-is-meant-by-certified"></a>O que se entende por *certificado*?
Um *visual personalizado certificado* é um que cumpre um conjunto de requisitos de código e passou testes rigorosos de segurança.  Após um visual personalizado ser certificado, este pode ser [exportado para o PowerPoint](service-publish-to-powerpoint.md), e será apresentado nos e-mails recebidos quando um utilizador [subscrever as páginas de relatórios](service-report-subscribe.md). Também pode ser utilizado como um [visual personalizado padrão](power-bi-custom-visuals.md), adicionado aos relatórios do serviço Power BI e do Power BI Desktop, visualizado no Power BI Mobile e incorporado.

É um programador Web e está interessado em criar as suas próprias visualizações e adicioná-las ao [Microsoft AppSource](https://appsource.microsoft.com)? Veja [Introdução ás Ferramentas de Programador](service-custom-visuals-getting-started-with-developer-tools.md) para saber como.


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
| [Regras de associação](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380815) | |
| [Gráfico Aster](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759?src=office&tab=Overview) | |
| [BciCalendar (Calendário Beyondsoft)](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381096?src=office&tab=Overview)  | |
| [Gráfico de laço da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838?src=office&tab=Overview) |[Vídeo](https://youtu.be/So5xKMSpVJI) |
| [Caixa e Bigodes](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831?src=office&tab=Overview) | |
| [Gráfico de tijolos da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380836) | |
| [Gráfico de bolhas da Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381340?src=office) | |
| [Gráfico de Marcas](https://store.office.com/app.aspx?assetid=WA104380755) |[Vídeo1](https://youtu.be/AOlsFYkfkcw)   [Vídeo2](https://youtu.be/AQvd2FhRyCI) |
| [Gráfico de Marcas da OKViz](https://store.office.com/bullet-chart-by-okviz-WA104380953.aspx) |[Vídeo](https://youtu.be/mtvUNl9bMjA) |
| [Calendário da Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146?src=office&tab=Overview) | |
| [Gráfico de velas da OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380952) | |
| [Segmentação de teclas](https://store.office.com/chiclet-slicer-WA104380756.aspx) |[Vídeo](https://youtu.be/iYOkJ1APueY) |
| [Gráfico de cordas](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761?src=office&tab=Overview) |[Vídeo](https://youtu.be/AQvd2FhRyCI) |
| [Medidor circular da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837?tab=Overview) | |
| [Medidor cilíndrico](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874) | |
| [Medidor de marcação](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184) |[Vídeo](https://youtu.be/AOlsFYkfkcw) |
| [Gráfico de anel da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824?tab=Overview) |[Vídeo](https://youtu.be/pDToHDFHnq8) |
| [Gráfico de Pontos da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381101) | |
| [Gráfico de Pontos da OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104381101?src=office&tab=Overview) |[Vídeo](https://youtu.be/4lskRgcpFJY) |
| [Gráfico de Pontos da Microsoft](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380760?src=office) | |
| [Gráfico de anel de desagregação da ZoomCharts](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858) | |
| [Cartograma de Desagregação](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381045?src=office) | |
| [Coropleto de Desagregação](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381044?src=office) | |
| [Gráfico de colunas de desagregação da ZoomCharts](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380881?src=office) | |
| [Gráfico de colunas de desagregação para dados baseados no tempo da ZoomCharts](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380881) | |
| [Gráfico de anel de desagregação da ZoomCharts](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380858) | |
| [Dual KPI](https://store.office.com/dual-kpi-WA104380774.aspx) |[Vídeo](https://youtu.be/821o0-eVBXo?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x) |
| [Gráfico de dispersão avançada](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380762) | |
| [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112?src=office&tab=Overview) | |
| [Gráfico de Bolhas Empilhadas da Enlighten](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380868) | |
| [Gráfico de Pilhas Aleatórias da Enlighten](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380849) | |
| [Gráfico de Bolachas da Enlighten](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380850) | |
| [Bandeiras do Mundo da Enlighten](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380923) | |
| [Flywheel]() | |
| [Previsões TBATS](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381326?src=office) | |
| [Gantt](https://store.office.com/gantt-WA104380765.aspx) |[Vídeo](https://youtu.be/qJ7s_KrGiUU) |
| [Gráfico de hierarquias da Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381333?src=office) | |
| [Histograma](https://store.office.com/histogram-chart-WA104380776.aspx) | |
| [Funil Horizontal](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846) |[Vídeo](https://youtu.be/SudZei68PPo) |
| [Linha Cronológica com Imagens](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381254) | |
| [Designer de Infográficos](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380898?src=office) | |
| [Indicador KPI](https://store.office.com/kpi-indicator-WA104380832.aspx) | |
| [Ticker de KPI da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380946) | |
| [Gráfico de Linhas e Pontos](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380766?src=office) | |
| [Medidor linear da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821?src=office&tab=Overview) |[Vídeo](https://youtu.be/AOlsFYkfkcw) |
| [Gráfico Mekko](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785?src=office&tab=Overview)  | [Vídeo](https://youtu.be/90FLCKpgicA)|
| [Play Axis (Segmentação de Dados Dinâmica)](https://store.office.com/play-axis-dynamic-slicer-WA104380981.aspx) | |
| [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083) |[Vídeo](https://youtu.be/IvfIP3E6-1Q) |
| [Gráfico de Pontos Temporais](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381006) | |
| [Gráfico de radar](https://store.office.com/radar-chart-WA104380771.aspx) | |
| [Gráfico de anel da MAQSoftware](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380824?src=office&tab=Overview) | [Vídeo](https://youtu.be/pDToHDFHnq8)|
| [Gráfico rotativo da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381007?src=office) |  |
| [Gráfico Sankey](https://store.office.com/app.aspx?assetid=WA104380777.aspx) |[Vídeo](https://youtu.be/WWP9wVUHGaA) |
| [Deslocador](https://store.office.com/scroller-WA104381018.aspx) |[Vídeo](https://youtu.be/uhRFQF2cGSY) |
| [Smart Filter da SQLBI](https://store.office.com/smart-filter-by-okviz-WA104380859.aspx) |[Vídeo](https://youtu.be/gcJsDDRQq28) |
| [Sparkline da OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910?src=office&tab=Overview) |[Vídeo](https://youtu.be/0m3Vnvso9tY) |
| [Sunburst](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767?src=office&tab=Overview) | |
| [Mapa de Calor de Tabela](https://store.office.com/table-heatmap-WA104380818.aspx) | |
| [Tacómetro](https://store.office.com/tachometer-WA104380937.aspx?) |[Vídeo](https://www.youtube.com/watch?v=C3OXdETbS9o) |
| [Encapsulador de texto](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826) | |
| [Termómetro](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847?src=office&tab=Overview) | [Vídeo](https://youtu.be/SPX9mgrAdBc)|
| [Decomposição de série temporal](https://appsource.microsoft.com/product/power-bi-visuals/WA104380897) | |
| [Segmentação de linha cronológica](https://store.office.com/timeline-slicer-WA104380786.aspx) |[Vídeo](https://youtu.be/ozMtZ4_NZ10) |
| [Gráfico de tornado](https://store.office.com/tornado-chart-WA104380768.aspx) |[Vídeo](https://youtu.be/AQvd2FhRyCI) |
| [Gráfico de Desvio Fundamental da Klaus Birringer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381140?src=office) | |
| [Gráfico de Cascata Fundamental gratuito](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380956) | |
| [Diagrama Venn da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381231) | |
| [VitaraCharts da MicroChart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381165) | |
| [Gráfico de bolacha](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049?src=office&tab=Overview) |[Vídeo](https://youtu.be/1vRqYUsm3Vk) |
| [Nuvem de Palavras](https://store.office.com/word-cloud-WA104380752.aspx?) |[Vídeo](https://www.youtube.com/watch?v=AblTenl9fqo) |

## <a name="next-steps"></a>Passos seguintes
[Introdução às ferramentas de programador de visuais personalizados (Pré-visualização)](service-custom-visuals-getting-started-with-developer-tools.md)      
[Lista de reprodução visual personalizada da Microsoft no YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
[Visualizações no Power BI](power-bi-report-visualizations.md)  
[Visualizações Personalizadas no Power BI](power-bi-custom-visuals.md)  
[Publicar visuais personalizados no Microsoft AppSource](developer/office-store.md)  
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

