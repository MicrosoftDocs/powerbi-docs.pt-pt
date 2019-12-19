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
ms.date: 12/02/2019
ms.openlocfilehash: 0a39496ade27cd45fae116eea92ef4b472e04582
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/11/2019
ms.locfileid: "74999750"
---
# <a name="get-a-power-bi-visual-certified"></a>Certificar um elemento visual do Power BI

Os elementos visuais do Power BI certificados são os elementos visuais do *Marketplace* que cumprem determinados requisitos *de código especificados* que foram testados e aprovados pela *equipa do Microsoft Power BI*. Os testes são concebidos para verificar que o elemento visual não acede a recursos ou serviços externos.

Os elementos visuais do Power BI certificados e os [elementos visuais do Power BI padrão](power-bi-custom-visuals.md) são utilizados da mesma forma. Podem ser adicionados ao [Power BI Desktop](../desktop-what-is-desktop.md) e ao [serviço Power BI](../power-bi-service-overview.md), e visualizados com o [Power BI Mobile](../consumer/mobile/mobile-apps-for-mobile-devices.md) e o [Power BI Embedded](embedding.md).

O processo de certificação é um processo opcional. Cabe aos programadores decidir se querem que os elementos visuais do Power BI no marketplace sejam certificados. Quando um elemento visual do Power BI é certificado, oferece mais funcionalidades. Por exemplo, pode [exportar para o PowerPoint](../consumer/end-user-powerpoint.md) ou apresentar o elemento visual em e-mails recebidos quando um utilizador [subscreve as páginas de relatório](../consumer/end-user-subscribe.md).

Os elementos visuais do Power BI não certificados não são necessariamente inseguros. Alguns elementos visuais não estão certificados porque não cumprem um ou mais [requisitos de certificação](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Um exemplo disto é a ligação a um serviço externo, como elementos visuais de mapa, ou elementos visuais que utilizam bibliotecas comerciais.

Se for um programador Web interessado em criar os seus próprios elementos visuais Power BI e adicioná-los ao  [Microsoft AppSource](https://appsource.microsoft.com), comece pelo tutorial  [Desenvolver um elemento visual do Power BI](visuals/custom-visual-develop-tutorial.md).

> [!NOTE]
> A **Microsoft** *não* é responsável pela criação de elementos visuais do Power BI de terceiros. Para verificar a funcionalidade dos elementos visuais de terceiros, aconselhamos os clientes a contactarem o autor do elemento visual diretamente.

> [!IMPORTANT]
> A Microsoft pode remover um elemento visual do Power BI da [lista de certificados](#list-of-power-bi-visuals-that-have-been-certified) a seu critério exclusivo.

## <a name="certification-requirements"></a>Requisitos de certificação

Para obter o [certificado](#get-a-power-bi-visual-certified) de elemento visual do Power BI, confirme que o elemento visual do Power BI está em conformidade com os requisitos listados nesta secção. 

> [!TIP]
> Recomendamos que utilize o EsLint com o conjunto predefinido de regras de segurança para pré-validar o código antes da submissão.

* Aprovado pelo Centro de Parceiros ou Dashboard de Vendedor da Microsoft. O elemento visual do Power BI deve estar no nosso [marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals).
* O elemento visual do Power BI é escrito com a *API v2.5* ou superior.
* O repositório de código está disponível para análise pela equipa do Power BI. Por exemplo, um formato legível do código fonte (JavaScript ou TypeScript) está disponível através do GitHub.

    >[!NOTE]
    > Não tem de partilhar o seu código em público no GitHub.

* Requisitos do repositório de código:
  * Deve incluir estes ficheiros:
    * .gitignore
    * capabilities.json
    * pbiviz.json
    * package.json
    * package-lock.json
    * tsconfig.json
  * Não deve incluir a pasta *node_modules* (adicione *node_modules* ao ficheiro .gitingore).
  * O comando *npm install* não deve devolver erros.
  * O comando *npm audit* não deve devolver avisos com nível alto ou moderado.
  * O comando *pbiviz package* não deve devolver erros.
  * Deve incluir o [TSlint da Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) sem configurações substituídas. Este comando não deve devolver erros lint.
   * O pacote compilado do elemento visual do Power BI deve corresponder ao pacote enviado (o hash md5 de ambos os ficheiros deve ser igual).
* Requisitos do código fonte:
   * O elemento visual do Power BI deve suportar a [API de Eventos de Composição](https://microsoft.github.io/PowerBI-visuals/docs/how-to-guide/rendering-events/).
   * Confirme que nenhum código arbitrário/dinâmico é executado (incorreto: eval(), não seguro usar setTimeout(), requestAnimationFrame(), setInterval(alguma função com entrada do utilizador), execução da entrada/dados do utilizador).
   * Verifique se o DOM é manipulado com segurança (incorreto: innerHTML, D3.html(<some user/data input>), use a limpeza para entrada/dados do utilizador antes de adicioná-lo ao DOM.
   * Verifique se não existem erros ou exceções de JavaScript na consola do browser para quaisquer dados de entrada. Os utilizadores poderão utilizar o elemento visual do Power BI com um intervalo diferente de dados inesperados, pelo que o elemento visual não deve falhar. Pode utilizar este [relatório de exemplo](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) como um conjunto de dados de teste.

* Se alguma propriedade no ficheiro *capabilities.json* for alterada, confirme que não interrompem os relatórios do utilizador existentes.

* Confirme que o elemento visual do Power BI está em conformidade com as [diretrizes dos elementos visuais do Power BI](./guidelines-powerbi-visuals.md).
    
* O código só pode utilizar componentes OSS que possam ser revistos publicamente, como bibliotecas TypeScript ou JavaScript públicas. O código fonte tem de estar disponível para análise e não apresentar vulnerabilidades conhecidas. Não é possível verificar um elemento visual personalizado com um componente comercial.

* O elemento visual do Power BI não deve aceder a serviços ou recursos externos. Por exemplo, nenhum pedido HTTP/S ou WebSocket pode sair do Power BI para quaisquer serviços. 

## <a name="submitting-a-power-bi-visual-for-certification"></a>Enviar um elemento visual do Power BI para certificação

Pode pedir que o elemento visual do Power BI seja certificado pela equipa do Power BI através do Centro de Parceiros.

>[!TIP]
>O processo de certificação do Power BI pode demorar algum tempo. Se estiver a criar um novo elemento visual do Power BI, recomendamos que o publique através do Centro de Parceiros antes de pedir a certificação do Power BI. Esse procedimento garante que a publicação do elemento visual não sofre atrasos.

Para pedir a certificação do Power BI:

1. Inicie sessão no Centro de Parceiros.
2. Na **página Descrição geral**, escolha o elemento visual do Power BI e vá para a página de configuração do **Produto**.
3. Marque a caixa de verificação **Pedir certificação do Power BI**.
4. Na página **Rever e publicar**, na caixa de texto **Notas da certificação**, forneça uma ligação para o código fonte e as credenciais de acesso necessárias.

>[!NOTE]
> Se se encontrar a meio do processo de submissão de um elemento visual do Power BI e tiver de utilizar o [Dashboard de Vendedor](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) (a antiga ferramenta de gestão), veja as instruções do [Processo de submissão de certificação do Dashboard de Vendedor](seller-dashboard.md#seller-dashboard-certification-submission-process).

## <a name="list-of-power-bi-visuals-that-have-been-certified"></a>Lista de elementos visuais do Power BI que foram certificados

| Ligação | Vídeo |
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

* [Developing a Power BI custom visual](../developer/custom-visual-develop-tutorial.md) (Desenvolver um elemento visual personalizado do Power BI)
* [Lista de reprodução visual personalizada da Microsoft no YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Visualizações no Power BI](../visuals/power-bi-report-visualizations.md)  
* [Visualizações Personalizadas no Power BI](power-bi-custom-visuals.md)  
* [Publicar elementos visuais do Power BI no Microsoft AppSource](../developer/office-store.md)  

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
