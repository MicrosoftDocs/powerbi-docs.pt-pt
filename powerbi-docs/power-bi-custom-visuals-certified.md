---
title: Elementos visuais do Power BI certificados
description: Requisitos e processo de submissão de um visual personalizado para certificação. E uma lista de elementos visuais do Power BI já certificados.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 05/9/2019
ms.openlocfilehash: 8b119f0f3b0dfb67dc2f9cb1dfd6f19d72593d66
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874566"
---
# <a name="get-a-power-bi-visual-certified"></a>Certificar um elemento visual do Power BI

## <a name="what-are-_certified_-power-bi-visuals"></a>O que são elementos visuais do Power BI **_certificados_** ?

Os elementos visuais do Power BI certificados são os elementos visuais do **Marketplace** que cumprem determinados requisitos **de código especificados** que foram testados e aprovados pela **equipa do Microsoft Power BI**. Quando um elemento visual personalizado é certificado, oferece mais funcionalidades. Alguns exemplos são as possibilidades de [exportar para o PowerPoint](consumer/end-user-powerpoint.md) e de apresentar o elemento visual em e-mails recebidos quando um utilizador [subscreve as páginas de relatório](consumer/end-user-subscribe.md).

Os **elementos visuais do Power BI certificados** são utilizados como os [elementos visuais do Power BI padrão](power-bi-custom-visuals.md). Os elementos visuais do Power BI certificados podem ser adicionados ao **serviço Power BI** e a um **relatório do Power BI Desktop**, e visualizados com o **Power BI Mobile** e o **Power BI Embedded**.

Os testes realizados são concebidos para verificar que o elemento visual não acede a serviços ou recursos externos. A **Microsoft** *não* é responsável pela criação dos elementos visuais do Power BI de terceiros e recomenda aos clientes que entrem diretamente em contacto com o autor para verificar a funcionalidade desses elementos visuais.

O processo de certificação é opcional e cabe aos programadores decidir se querem a certificação do seu elemento visual no marketplace.  

Os **elementos visuais do Power BI não certificados** não são necessariamente inseguros. Alguns elementos visuais não estão certificados porque não cumprem um ou mais [requisitos de certificação](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Um exemplo disto é a ligação a um serviço externo, como elementos visuais de mapa, ou elementos visuais que utilizam bibliotecas comerciais.

É um programador Web e está interessado em criar as suas próprias visualizações e adicioná-las ao  **[Microsoft AppSource](https://appsource.microsoft.com)** ? Veja  **[Develop a Power BI custom visual](developer/visuals/custom-visual-develop-tutorial.md)** (Desenvolver um elemento visual personalizado do Power BI) para saber como o pode fazer.

## <a name="removal-of-power-bi-certified-power-bi-visuals"></a>Remoção dos elementos visuais do Power BI Certificados

A Microsoft pode remover um elemento visual da [lista de certificados](#list-of-power-bi-visuals-that-have-been-certified) a seu critério exclusivo.

## <a name="getting-a-custom-visualcertified"></a>Certificar um elemento visual personalizado

### <a name="certification-requirements"></a>Requisitos de certificação

Para [certificar](#get-a-power-bi-visual-certified) o seu elemento visual personalizado, certifique-se de que este cumpre os requisitos apresentados abaixo:  

* Aprovação pelo Microsoft AppSource. O seu elemento visual personalizado deve estar no nosso [marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals).
* O elemento visual personalizado é escrito com a **API com versão 2.5** ou superior.
* O repositório de código está disponível para análise pela equipa do Power BI (por exemplo, código-fonte, como JavaScript ou TypeScript, num formato legível por humanos disponível através do GitHub).

    >[!Note]
    > Não tem de partilhar o seu código em público no GitHub.
* Requisitos do repositório de código:
   * Deve incluir o conjunto mínimo necessário de ficheiros:
      * .gitignore
      * capabilities.json
      * pbiviz.json
      * package.json
      * package-lock.json
      * tsconfig.json
   * Não deve incluir a pasta node_modules (adicionar node_modules ao ficheiro .gitingore)
   * O comando **npm install** não deve devolver nenhum erro.
   * O comando **npm audit** não deve devolver nenhum aviso com nível alto ou moderado.
   * O comando **pbiviz package** não deve devolver nenhum erro.
   * Deve incluir [TSlint da Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) sem nenhuma configuração substituída, e este comando não deve devolver erros de lint.
   * O pacote compilado do Visual Personalizado deve corresponder ao pacote enviado (o hash md5 de ambos os ficheiros deve ser igual).
* Requisitos do código fonte:
   * O elemento visual deve suportar a [API de Eventos de Composição](https://microsoft.github.io/PowerBI-visuals/docs/how-to-guide/rendering-events/).
   * Confirme que nenhum código arbitrário/dinâmico é executado (incorreto: eval(), não seguro usar setTimeout(), requestAnimationFrame(), setInterval(alguma função com entrada do utilizador), execução da entrada/dados do utilizador).
   * Verifique se o DOM é manipulado com segurança (incorreto: innerHTML, D3.html(<some user/data input>), use a limpeza para entrada/dados do utilizador antes de adicioná-lo ao DOM.
   * Verifique se não existem erros/exceções de JavaScript no consola do browser para quaisquer dados de entrada. Os utilizadores podem usar seu elemento visual com um intervalo diferente de dados inesperados, pelo que o elemento visual não deve falhar. Pode utilizar [este relatório de amostra](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) como um conjunto de dados de teste.

* Se alguma propriedade em capabilities.json for alterada, confirme que não interrompem os relatórios do utilizador existentes.

* Verifique se o elemento visual está em conformidade com as [diretrizes para elementos visuais do Power BI](./developer/guidelines-powerbi-visuals.md#guidelines-for-power-bi-visuals-with-additional-purchases). **Não são permitidas marcas d'água**.

* O elemento visual utiliza apenas componentes OSS que podem ser analisados pelo público (TypeScript ou bibliotecas JS públicos. O código-fonte está disponível para análise e não apresenta vulnerabilidades conhecidas). Não é possível verificar um elemento visual personalizado com um componente comercial.

* O elemento visual não tem acesso a serviços ou recursos externos, o que implica, entre outras coisas, que nenhum pedido HTTP/S ou WebSocket seja feito pelo Power BI a quaisquer serviços. 

> [!TIP]
> Recomendamos que utilize o EsLint com o conjunto predefinido de regras de segurança, para pré-validar o seu código antes da submissão.

## <a name="process-for-submitting-a-custom-visual-for-certification"></a>Processo de submissão de um elemento visual personalizado para certificação

Para enviar um visual personalizado para certificação:

1. Envie um e-mail para a equipa de suporte para elementos visuais do Power BI (pbicvsupport@microsoft.com). No e-mail, inclua as seguintes informações:
    * Título: Pedido de Certificação de Elemento Visual
    * Forneça uma ligação para o repositório do GitHub em que está alojado o código-fonte legível por humanos
    * [Cumprir os requisitos](#certification-requirements)
    * Passar na análise de código

2. A equipa de elementos visuais do Power BI da Microsoft irá enviar-lhe uma notificação a informar que o seu elemento visual personalizado foi certificado e adicionado à [lista de elementos visuais certificados](#list-of-power-bi-visuals-that-have-been-certified) ou que foi rejeitado. No segundo caso, será enviado um relatório dos problemas a corrigir. O programador é responsável por manter a comunicação aberta com a Microsoft e atualizar os seus elementos visuais certificados consoante necessário.

## <a name="list-of-power-bi-visuals-that-have-been-certified"></a>Lista de elementos visuais do Power BI que foram certificados

| Ligação para o AppSource | Ligação para o vídeo |
| --- | --- |
| [3AG Systems – Gráfico de Barras com Desvio Relativo](https://appsource.microsoft.com/en/product/power-bi-visuals/WA104381912) | |
| [3AG Systems – Gráfico de Colunas com Desvio Relativo](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803) | |
| [Advanced Donut Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941) | |
| [Advanced Network Visualization](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942) | |
| [Advanced TimeSeries Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943) | |
| [Advanced Combo Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104381944) | |
| [Gráfico Aster](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759) | |
| [Calendário Beyondsoft](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096) | |
| [Gráfico de Laço da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838) | [Vídeo](https://youtu.be/So5xKMSpVJI) |
| [Gráfico de Caixa e Bigodes](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831) | |
| [Gráfico de Caixa de Bigodes da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351) | [Vídeo](https://youtu.be/JoHaFLfhXdo) |
| [Gráfico de Tijolos da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836) | [Vídeo](https://youtu.be/hA3DOsvn2xY) |
| [Gráfico de Bolhas da Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340) | |
| [Gráfico de Marcas](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755) | [Vídeo](https://youtu.be/AOlsFYkfkcw) |
| [Gráfico de Marcas da OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953) | [Vídeo](https://youtu.be/mtvUNl9bMjA) |
| [Calendário da Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146) | |
| [Gráfico de velas da OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952) | [Vídeo](https://youtu.be/nT_18gyRxPo) |
| [Cartão com Estados da OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967) | |
| [Segmentação de Teclas](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756) | |
| [Cordas](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761) | [Vídeo](https://youtu.be/AQvd2FhRyCI) |
| [Medidor Circular da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837) | [Vídeo](https://youtu.be/9NHXALkBXuY) |
| [Mapa de Cluster](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806) | |
| [Medidor Cilíndrico da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874) | [Vídeo](https://youtu.be/DgdoWi7Gcxo) |
| [Medidor de Marcação](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184) | |
| [Desenho com Pontos](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760) | |
| [Gráfico de Pontos da OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949) | [Vídeo](https://youtu.be/By16pX9KT40) |
| [Cartograma de Desagregação](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045) | |
| [Coropleto de Desagregação](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044) | |
| [Gráfico de colunas de desagregação](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857) | [Vídeo](https://youtu.be/lBy2gQQ5YsQ) |
| [Gráfico de colunas de desagregação para dados baseados no tempo](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881) | [Vídeo](https://youtu.be/T_mRou18vx0) |
| [Gráfico de anel de desagregação](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858) | [Vídeo](https://youtu.be/AUVFrSHmPeo) |
| [Dual KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774) | |
| [Dynamic Tooltip by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983) (Descrição Dinâmica da MAQ Software) | [Vídeo](https://youtu.be/Z-tl97BpEr0) |
| [Gráfico de Dispersão Avançada](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762) | [Vídeo](https://youtu.be/xCfM0cjM4do) |
| [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112) | |
| [Otimizar Segmentação de Dados](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960) | |
| [Gráfico de Pilhas Aleatórias da Enlighten](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849) | |
| [Gráfico de Bolachas da Enlighten](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850) | |
| [Filtrar por Lista da DevScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413) | [Vídeo](https://youtu.be/RetEWGwBu0I) |
| [Gráfico Direcionado para Força](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764) | [Vídeo](https://youtu.be/YsTa7uyJ4sg) |
| [Funil com Origem da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334) | [Vídeo](https://youtu.be/R_EcimsLI8U) |
| [Gantt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765) | [Vídeo](https://youtu.be/qJ7s_KrGiUU) |
| [Gráfico de Gantt da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364) | [Vídeo](https://youtu.be/vJLV9JRCpI8) |
| [Barras de Dados de Globo](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344) | |
| [Grelha da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825) | [Vídeo](https://youtu.be/VOPoDJgZfOY) |
| [Gráfico de Hierarquias da Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333) | [Vídeo](https://youtu.be/0ZGzJaq_KT4) |
| [Gráfico de Histograma](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776) | |
| [Histograma com pontos da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032) | [Vídeo](https://youtu.be/-ILF--wExrw) |
| [Funil Horizontal da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846) | [Vídeo](https://youtu.be/SudZei68PPo) |
| [Imagem da CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297) | |
| [Grelha Grande](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355) | |
| [Designer de Infográficos](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898) | |
| [Gráfico de KPI da Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432) | |
| [Coluna de KPI da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996) | [Vídeo](https://youtu.be/rU0xoOlIq1U) |
| [Grelha de KPI da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947) | [Vídeo](https://youtu.be/dM4PvZh71V0) |
| [Indicador KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832) | |
| [Ticker de KPI da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946) | [Vídeo](https://youtu.be/cudG4gsZ2V8) |
| [Medidor Linear da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821) | [Vídeo](https://youtu.be/7_jFaM30dkc) |
| [Gráfico de Linhas e Pontos](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766) | |
| [Gráfico Mekko](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785) | [Vídeo](https://youtu.be/90FLCKpgicA) |
| [Multi KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763) | |
| [Descrição geral da CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477) | |
| [Play Axis (Segmentação de Dados Dinâmica)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981) | |
| [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083) | [Vídeo](https://youtu.be/IvfIP3E6-1Q) |
| [Matriz do Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299) | [Vídeo](https://youtu.be/1enze8pcGzY) |
| [Gráfico de Pontos Temporais](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006) | [Vídeo](https://youtu.be/DQWdcQtjDVw) |
| [Gráfico de Quadrante da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011) | [Vídeo](https://youtu.be/ppBnyhqWNC0) |
| [Gráfico de Radar](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771) | |
| [Gráfico de Anel da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824) | [Vídeo](https://youtu.be/pDToHDFHnq8) |
| [Gráfico Rotativo da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007) | [Vídeo](https://youtu.be/d5xBCMmb3hU) |
| [Gráfico Sankey](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777) | [Vídeo](https://youtu.be/WWP9wVUHGaA) |
| [Gráfico de Dispersão da Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703) | |
| [Deslocador](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018) | |
| [Smart Filter da OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859) | [Vídeo](https://youtu.be/gcJsDDRQq28) |
| [Sparkline da OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910) | [Vídeo](https://youtu.be/0m3Vnvso9tY) |
| [Gráfico de Fluxo](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772) | |
| [Sunburst](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767) | |
| [Painel Sinóptico da OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873) | |
| [Mapa de Calor de Tabela](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818) | |
| [Tacómetro](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937) | [Vídeo](https://youtu.be/C3OXdETbS9o) |
| [Filtro de Texto](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309) | |
| [Encapsulador de Texto da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826) | |
| [Termómetro da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847) | [Vídeo](https://youtu.be/SPX9mgrAdBc) |
| [Time Brush Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798) | |
| [Segmentação de Linha Cronológica](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786) | [Vídeo](https://youtu.be/ozMtZ4_NZ10) |
| [Linha Cronológica da CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427) | [Vídeo](https://youtu.be/szNi9YgXFJc) |
| [Gráfico de tornado](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768) | [Vídeo](https://www.youtube.com/watch?v=AQvd2FhRyCI) |
| [Gráfico de Transações da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823) | [Vídeo](https://youtu.be/xhTR6y6J9Ko) |
| [Desvio Fundamental](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140) | [Vídeo](https://youtu.be/pDYF8iZxERs) |
| [Gráfico de Cascata Fundamental](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956) | [Vídeo](https://youtu.be/0BZsVCQdEkc) |
| [Lista de Utilizadores da CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426) | |
| [Gráfico de Bolachas](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049) | [Vídeo](https://youtu.be/1vRqYUsm3Vk) |
| [Nuvem de Palavras](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752) | [Vídeo](https://youtu.be/AblTenl9fqo) |

## <a name="faq"></a>PERGUNTAS FREQUENTES

Para obter mais informações acerca dos elementos visuais, aceda às [Perguntas frequentes sobre os elementos visuais certificados](power-bi-custom-visuals-faq.md#certified-power-bi-visuals).

## <a name="next-steps"></a>Próximos passos

* [Developing a Power BI custom visual](developer/visuals/custom-visual-develop-tutorial.md) (Desenvolver um elemento visual personalizado do Power BI)
* [Lista de reprodução visual personalizada da Microsoft no YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Visualizações no Power BI](visuals/power-bi-report-visualizations.md)  
* [Visualizações Personalizadas no Power BI](power-bi-custom-visuals.md)  
* [Publicar elementos visuais do Power BI no Microsoft AppSource](developer/office-store.md)  

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
