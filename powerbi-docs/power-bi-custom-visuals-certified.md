---
title: Visualizações personalizadas certificadas no Power BI
description: Requisitos e processo de submissão de um visual personalizado para certificação. E uma lista de visuais personalizados já certificados.
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 02/13/2018
ms.author: mihart
ms.openlocfilehash: efddb15572705d6d1c7cb215250360e94a8546cb
ms.sourcegitcommit: 127df71c357127cca1b3caf5684489b19ff61493
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37600364"
---
# <a name="getting-a-custom-visual-certified"></a>Obter um visual personalizado *certificado*
## <a name="what-is-meant-by-certified"></a>O que se entende por *certificado*?
Um *visual personalizado certificado* é um que cumpre um conjunto de requisitos de código e passou testes rigorosos de segurança.  Após um visual personalizado ser certificado, este pode ser [exportado para o PowerPoint](service-publish-to-powerpoint.md), e será apresentado nos e-mails recebidos quando um utilizador [subscrever as páginas de relatórios](service-report-subscribe.md). Também pode ser utilizado como um [visual personalizado padrão](power-bi-custom-visuals.md), adicionado aos relatórios do serviço Power BI e do Power BI Desktop, visualizado no Power BI Mobile e incorporado.

É um programador Web e está interessado em criar as suas próprias visualizações e adicioná-las ao [Microsoft AppSource](https://appsource.microsoft.com)? Consulte [Introdução às Ferramentas de Programador](service-custom-visuals-getting-started-with-developer-tools.md) para saber como.


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
| [Gráfico Aster](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380759) | |
| [Calendário Beyondsoft](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381096) | |
| [Gráfico de Laço da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380838) | [Vídeo](https://youtu.be/So5xKMSpVJI) |
| [Gráfico de Caixa e Bigodes](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380831) | |
| [Gráfico de Caixa de Bigodes da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381351) | [Vídeo](https://youtu.be/JoHaFLfhXdo) |
| [Gráfico de Tijolos da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380836) | [Vídeo](https://youtu.be/hA3DOsvn2xY) |
| [Gráfico de Bolhas da Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381340) | |
| [Gráfico de Marcas](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380755) | [Vídeo](https://youtu.be/AOlsFYkfkcw) |
| [Gráfico de Marcas da OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380953) | [Vídeo](https://youtu.be/mtvUNl9bMjA) |
| [Calendário da Tallan](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381146) | |
| [Gráfico de velas da OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380952) | [Vídeo](https://youtu.be/nT_18gyRxPo) |
| [Cartão com Estados da OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380967) | |
| [Segmentação de Teclas](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380756) | |
| [Cordas](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380761) | [Vídeo](https://youtu.be/AQvd2FhRyCI) |
| [Medidor Circular da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380837) | [Vídeo](https://youtu.be/9NHXALkBXuY) |
| [Mapa de Cluster](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380806) | |
| [Medidor Cilíndrico da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380874) | [Vídeo](https://youtu.be/DgdoWi7Gcxo) |
| [Medidor de Marcação](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381184) | |
| [Desenho com Pontos](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380760) | |
| [Gráfico de Pontos da OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380949) | [Vídeo](https://youtu.be/By16pX9KT40) |
| [Cartograma de Desagregação](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381045) | |
| [Coropleto de Desagregação](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381044) | |
| [Gráfico de colunas de desagregação](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380857) | [Vídeo](https://youtu.be/lBy2gQQ5YsQ) |
| [Gráfico de colunas de desagregação para dados baseados no tempo](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380881) | [Vídeo](https://youtu.be/T_mRou18vx0) |
| [Gráfico de anel de desagregação](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380858) | [Vídeo](https://youtu.be/AUVFrSHmPeo) |
| [Dual KPI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380774) | |
| [Dynamic Tooltip by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380983) (Descrição Dinâmica da MAQ Software) | [Vídeo](https://youtu.be/Z-tl97BpEr0) |
| [Gráfico de Dispersão Avançada](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380762) | [Vídeo](https://youtu.be/xCfM0cjM4do) |
| [Enlighten Aquarium](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381112) | |
| [Otimizar Segmentação de Dados](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380960) | |
| [Gráfico de Pilhas Aleatórias da Enlighten](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380849) | |
| [Gráfico de Bolachas da Enlighten](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380850) | |
| [Gráfico Direcionado para Força](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380764) | [Vídeo](https://youtu.be/YsTa7uyJ4sg) |
| [Funil com Origem da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381334) | [Vídeo](https://youtu.be/R_EcimsLI8U) |
| [Gantt](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380765) | [Vídeo](https://youtu.be/qJ7s_KrGiUU) |
| [Gráfico de Gantt da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381364) | [Vídeo](https://youtu.be/vJLV9JRCpI8) |
| [Barras de Dados de Globo](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381344) | |
| [Grelha da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380825) | [Vídeo](https://youtu.be/VOPoDJgZfOY) |
| [Gráfico de Hierarquias da Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381333) | [Vídeo](https://youtu.be/0ZGzJaq_KT4) |
| [Gráfico de Histograma](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380776) | |
| [Histograma com pontos da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381032) | [Vídeo](https://youtu.be/-ILF--wExrw) |
| [Funil Horizontal da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380846) | [Vídeo](https://youtu.be/SudZei68PPo) |
| [Imagem da CloudScope](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381297) | |
| [Grelha Grande](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381355) | |
| [Designer de Infográficos](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380898) | |
| [Gráfico de KPI da Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381432) | |
| [Coluna de KPI da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380996) | [Vídeo](https://youtu.be/rU0xoOlIq1U) |
| [Grelha de KPI da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380947) | [Vídeo](https://youtu.be/dM4PvZh71V0) |
| [Indicador KPI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380832) | |
| [Ticker de KPI da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380946) | [Vídeo](https://youtu.be/cudG4gsZ2V8) |
| [Medidor Linear da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380821) | [Vídeo](https://youtu.be/7_jFaM30dkc) |
| [Gráfico de Linhas e Pontos](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380766) | |
| [Gráfico Mekko](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380785) | [Vídeo](https://youtu.be/90FLCKpgicA) |
| [Descrição geral da CloudScope](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381477) | |
| [Play Axis (Segmentação de Dados Dinâmica)](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380981) | |
| [Power KPI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381083) | [Vídeo](https://youtu.be/IvfIP3E6-1Q) |
| [Matriz do Power KPI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381299) | [Vídeo](https://youtu.be/1enze8pcGzY) |
| [Gráfico de Pontos Temporais](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381006) | [Vídeo](https://youtu.be/DQWdcQtjDVw) |
| [Gráfico de Quadrante da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381011) | [Vídeo](https://youtu.be/ppBnyhqWNC0) |
| [Gráfico de Radar](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380771) | |
| [Gráfico de Anel da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380824) | [Vídeo](https://youtu.be/pDToHDFHnq8) |
| [Gráfico Rotativo da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381007) | [Vídeo](https://youtu.be/d5xBCMmb3hU) |
| [Gráfico Sankey](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380777) | [Vídeo](https://youtu.be/WWP9wVUHGaA) |
| [Deslocador](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381018) | |
| [Smart Filter da OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380859) | [Vídeo](https://youtu.be/gcJsDDRQq28) |
| [Sparkline da OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380910) | [Vídeo](https://youtu.be/0m3Vnvso9tY) |
| [Gráfico de Fluxo](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380772) | |
| [Sunburst](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380767) | |
| [Painel Sinóptico da OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380873) | |
| [Mapa de Calor de Tabela](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380818) | |
| [Tacómetro](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380937) | [Vídeo](https://youtu.be/C3OXdETbS9o) |
| [Filtro de Texto](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381309) | |
| [Encapsulador de Texto da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380826) | |
| [Termómetro da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380847) | [Vídeo](https://youtu.be/SPX9mgrAdBc) |
| [Time Brush Slicer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380798) | |
| [Segmentação de Linha Cronológica](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380786) | [Vídeo](https://youtu.be/ozMtZ4_NZ10) |
| [Linha Cronológica da CloudScope](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381427) | [Vídeo](https://youtu.be/szNi9YgXFJc) |
| [Gráfico de tornado](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380768) | [Vídeo](https://www.youtube.com/watch?v=AQvd2FhRyCI) |
| [Gráfico de Transações da MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380823) | [Vídeo](https://youtu.be/xhTR6y6J9Ko) |
| [Desvio Fundamental](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381140) | [Vídeo](https://youtu.be/pDYF8iZxERs) |
| [Gráfico de Cascata Fundamental](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380956) | [Vídeo](https://youtu.be/0BZsVCQdEkc) |
| [Lista de Utilizadores da CloudScope](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381426) | |
| [Gráfico de Bolachas](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381049) | [Vídeo](https://youtu.be/1vRqYUsm3Vk) |
| [Nuvem de Palavras](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380752) | [Vídeo](https://youtu.be/AblTenl9fqo) |

## <a name="next-steps"></a>Próximos passos
[Introdução às ferramentas de programador de visuais personalizados (Pré-visualização)](service-custom-visuals-getting-started-with-developer-tools.md)      
[Lista de reprodução visual personalizada da Microsoft no YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
[Visualizações no Power BI](power-bi-report-visualizations.md)  
[Visualizações Personalizadas no Power BI](power-bi-custom-visuals.md)  
[Publicar visuais personalizados no Microsoft AppSource](developer/office-store.md)  
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

