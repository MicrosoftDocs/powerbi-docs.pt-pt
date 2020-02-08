---
title: Elementos visuais do Power BI certificados
description: Requisitos e processo de submissão de um elemento visual personalizado para certificação e uma lista de elementos visuais do Power BI certificados.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 01/12/2019
ms.openlocfilehash: 4ffab3913560498dd57103f0a25c39f7a03a42ec
ms.sourcegitcommit: 75300b3f53f438ed7d3bd4edc93b9eb5925bf3af
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/05/2020
ms.locfileid: "77026675"
---
# <a name="get-a-power-bi-visual-certified"></a>Certificar um elemento visual do Power BI

Os elementos visuais do Power BI certificados são os elementos visuais do [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals) que cumprem os [requisitos de código](#certification-requirements) da equipa do Microsoft Power BI. Estes elementos visuais são testados para verificar que não acedem a recursos ou serviços externos e que seguem as diretrizes e os padrões de codificação seguros.

Quando um elemento visual do Power BI é certificado, oferece mais funcionalidades. Por exemplo, pode [exportar para o PowerPoint](../consumer/end-user-powerpoint.md) ou apresentar o elemento visual em e-mails recebidos quando um utilizador [subscreve as páginas de relatório](../consumer/end-user-subscribe.md).

O processo de certificação é opcional. Os elementos visuais do Power BI que não estão certificados não são necessariamente elementos visuais do Power BI não seguros. Alguns elementos visuais do Power BI não estão certificados porque não cumprem um ou mais [requisitos de certificação](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Por exemplo, um elemento visual do Power BI de mapa que liga a um serviço externo ou um elemento visual do Power BI que utiliza bibliotecas comerciais.

> [!NOTE]
> A Microsoft não é responsável pela criação de elementos visuais do Power BI de terceiros. Para verificar a funcionalidade dos elementos visuais de terceiros, contacte o autor do elemento visual diretamente.

## <a name="certification-requirements"></a>Requisitos de certificação

Para obter o [certificado](#get-a-power-bi-visual-certified) de elemento visual do Power BI, o elemento visual do Power BI deve estar em conformidade com os requisitos listados nesta secção. 

### <a name="general-requirements"></a>Requisitos gerais

O elemento visual do Power BI deve ser aprovado pelo Dashboard do Vendedor ou Centro de Parceiros. É recomendado que o elemento visual do Power BI já esteja no [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals). Para saber como publicar um elemento visual do Power BI no AppSource, veja [Publicar elementos visuais do Power BI no Centro de Parceiros](office-store.md).

Antes de submeter o elemento visual do Power BI para certificação, confirme que este está em conformidade com as [diretrizes dos elementos visuais do Power BI](./guidelines-powerbi-visuals.md).

Ao submeter o elemento visual do Power BI, confirme que o pacote compilado corresponde exatamente ao pacote submetido.

### <a name="code-repository-requirements"></a>Requisitos do repositório de código

Embora não seja necessário partilhar publicamente o código no GitHub, o repositório de código deve estar disponível para análise pela equipa do Power BI. A melhor maneira de o fazer, é fornecer o código fonte (JavaScript ou TypeScript) no GitHub.

O repositório deve conter o código para apenas um elemento visual do Power BI. Não pode conter código para vários elementos visuais do Power BI ou código não relacionado.

O repositório tem de conter um ramo denominado **certificação** (obrigatoriamente em minúsculas). O código fonte neste ramo deve corresponder ao pacote submetido. Este código só pode ser atualizado durante o próximo processo de submissão, caso esteja a submeter novamente o elemento visual do Power BI.

Se o elemento visual do Power BI utilizar pacotes npm privados ou submódulos git, deve fornecer acesso aos repositórios adicionais que contêm este código.

### <a name="file-requirements"></a>Requisitos de ficheiros

Utilize a versão mais recente da API para escrever o elemento visual do Power BI.

O repositório deve incluir os seguintes ficheiros:
* **.gitignore** – adicione `node_modules` a este ficheiro. Este código não pode incluir a pasta *node_modules*.
* **capabilities.json** – se estiver a submeter uma versão mais recente do elemento visual do Power BI com alterações às propriedades neste ficheiro, confirme que estas não danificam os relatórios dos utilizadores existentes.
* **pbiviz.json**
* **package.json**
* **package-lock.json**
* **tsconfig.json**

### <a name="command-requirements"></a>Requisitos de comandos

Confirme que os seguintes comandos não devolvem erros.

* `npm install`
* `pbiviz package`
* `npm audit` – não deve devolver nenhum aviso com nível alto ou moderado.
* [TSlint da Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) sem configurações substituídas. Este comando não deve devolver erros lint.

### <a name="compiling-requirements"></a>Requisitos de compilação

Utilize a versão mais recente do [powerbi-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools) para escrever o elemento visual do Power BI.

Deve compilar o elemento visual do Power BI com `pbiviz package`. Se estiver a utilizar os scripts criados por si, indique um comando de construção personalizado `npm run package`.



### <a name="source-code-requirements"></a>Requisitos do código fonte

Confirme que seguiu a lista de políticas de [certificação adicional dos elementos visuais do Power BI](https://docs.microsoft.com/legal/marketplace/certification-policies#1200-power-bi-visuals-additional-certification). Se a submissão não seguir estas diretrizes, o e-mail de rejeição do Centro de Parceiros incluirá os números das políticas listados nesta ligação.

Siga os requisitos de código listados abaixo para confirmar que o código está em conformidade com as políticas de certificação do Power BI.  

**Obrigatório**
* Utilize apenas componentes OSS que possam ser revistos publicamente, como bibliotecas TypeScript ou JavaScript públicas.
* O código deve suportar a [API de Eventos de Composição](./visuals/event-service.md).
* Confirme que o DOM é manipulado em segurança. Utilize a limpeza para a entrada de utilizador ou dados de utilizador, antes de os adicionar ao DOM.
* Utilize este [relatório de exemplo](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) como um conjunto de dados de teste.

**Não permitido**
* Aceder a recursos ou serviços externos. Por exemplo, nenhum pedido HTTP/S ou WebSocket pode sair do Power BI para quaisquer serviços.
* Com `innerHTML`ou `D3.html(user data or user input)`.
* Os erros ou as exceções de JavaScript na consola do browser para quaisquer dados de entrada.
* Código dinâmico ou arbitrário, como `eval()`, utilização não segura de `settimeout()`, `requestAnimationFrame()`, `setinterval(user input function)` e dados de entrada ou dados de utilizador.
* Projetos ou ficheiros de JavaScript em miniatura.

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

## <a name="certified-power-bi-visuals"></a>Elementos visuais do Power BI certificados

Os elementos visuais do Power BI certificados estão listados abaixo. Clique na ligação para abrir o elemento visual do Power BI no AppSource. Se estiver disponível um vídeo, pode clicar na ligação do mesmo para o ver.

* [3AG Systems - Bar Chart With Absolute Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381802)
*  [3AG Systems – Gráfico de Barras com Desvio Relativo](https://appsource.microsoft.com/product/power-bi-visuals/WA104381912)
*  [3AG Systems – Gráfico de Colunas com Desvio Relativo](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803)
*  [3AG Systems - Column Chart with Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381724)
* [Advanced Donut Visual (Full Edition)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941)
*  [Advanced Donut Visual (Light Edition)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858)
*  [Advanced Graph Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104382086)
*  [Advanced Network Visualization](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942)
*  [Advanced TimeSeries Visual (Full Edition)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943)
*  [Gráfico Aster](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759)
*  [Calendário Beyondsoft](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096)
*  [Gráfico de Laço da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838)
*  [Gráfico de Caixa e Bigodes](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831)
* [Gráfico de Caixa de Bigodes da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351)
*  [Gráfico de Tijolos da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836)
*  [Gráfico de Bolhas da Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340)
*  [Bullet Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755), **[ligação de vídeo](https://youtu.be/AOlsFYkfkcw)**
* [Gráfico de Marcas](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755)
*  [Bullet Chart by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953), **[ligação de vídeo](https://youtu.be/mtvUNl9bMjA)**
* [Calendar by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381844)
*  [Calendário da Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146)
*  [Candlestick by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952), **[ligação de vídeo](https://youtu.be/nT_18gyRxPo)**
*  [Cartão com Estados da OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967)
*  [Segmentação de Teclas](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756)
*  [Chord](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761), **[ligação de vídeo](https://youtu.be/AQvd2FhRyCI)**
*  [Medidor Circular da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837)
*  [Mapa de Cluster](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806)
* [Custom Calendar by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381179)
* [Medidor Cilíndrico da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874)
*  [Dial Gauge](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184)
[Gráfico de Pontos](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760)
*  [Dot Plot by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949), **[ligação de vídeo](https://youtu.be/By16pX9KT40)**
*  [Cartograma de Desagregação](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045)
*  [Coropleto de Desagregação](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044)
*  [Drill-down column chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857), **[ligação de vídeo](https://youtu.be/lBy2gQQ5YsQ)**
*  [Drill-down column chart for time based data](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881), **[ligação de vídeo](https://youtu.be/T_mRou18vx0)**
*  [Drill-down donut chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858), **[ligação de vídeo](https://youtu.be/AUVFrSHmPeo)**
*  [Dual KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774)
*  [Dynamic Tooltip by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983) (Descrição Dinâmica da MAQ Software)
*  [Enhanced Scatter](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762), **[ligação de vídeo](https://youtu.be/xCfM0cjM4do)**
*  [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112)
*  [Otimizar Segmentação de Dados](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960)
*  [Gráfico de Pilhas Aleatórias da Enlighten](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849)
*  [Gráfico de Bolachas da Enlighten](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850)
*  [Filter by List by Devscope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413), **[ligação de vídeo](https://youtu.be/RetEWGwBu0I)**
*  [Force-Directed Graph](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764), **[ligação de vídeo](https://youtu.be/YsTa7uyJ4sg)**
*  [Funil com Origem da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334)
*  [Gantt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765), **[ligação de vídeo](https://youtu.be/qJ7s_KrGiUU)**
* [Gráfico de Gantt da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364)
*  [Barras de Dados de Globo](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344)
*  [Grelha da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825)
*  [Hierarchy Chart by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333), **[ligação de vídeo](https://youtu.be/0ZGzJaq_KT4)**
*  [Gráfico de Histograma](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776)
*  [Histograma com pontos da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032)
* [Horizontal bar chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381230)
*  [Funil Horizontal da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846)
*  [Imagem da CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297)
*  [Grelha Grande](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355)
*  [Designer de Infográficos](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898)
*  [Gráfico de KPI da Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432)
*  [Coluna de KPI da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996)
*  [Grelha de KPI da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947)
*  [Indicador KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832)
*  [Ticker de KPI da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946)
* [Medidor Linear da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821)
*  [Gráfico de Linhas e Pontos](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766)
*  [Mekko Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785), **[ligação de vídeo](https://youtu.be/90FLCKpgicA)**
*  [Multi KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763)
*  [Descrição geral da CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477)
*  [Play Axis (Segmentação de Dados Dinâmica)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981)
*  [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083), [ligação de vídeo](https://youtu.be/IvfIP3E6-1Q)
*  [Power KPI Matrix](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299), **[ligação de vídeo](https://youtu.be/1enze8pcGzY)**
*  [Pulse Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006), **[ligação de vídeo](https://youtu.be/DQWdcQtjDVw)**
*  [Gráfico de Quadrante da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011)
*  [Gráfico de Radar](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771)
*  [Gráfico de Anel da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824)
*  [Gráfico Rotativo da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007)
*  [Sankey Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777), **[ligação de vídeo](https://youtu.be/WWP9wVUHGaA)**
*  [Gráfico de Dispersão da Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703)
*  [Deslocador](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018)
*  [Smart Filter by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859), **[ligação de vídeo](https://youtu.be/gcJsDDRQq28)**
*  [Sparkline by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910), **[ligação de vídeo](https://youtu.be/0m3Vnvso9tY)**
*  [Gráfico de Fluxo](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772)
*  [Sunburst](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767)
*  [Painel Sinóptico da OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873)
*  [Mapa de Calor de Tabela](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818)
*  [Tachometer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937), **[ligação de vídeo](https://youtu.be/C3OXdETbS9o)**
*  [Filtro de Texto](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309)
*  [Encapsulador de Texto da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826)
*  [Termómetro da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847)
*  [Time Brush Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798)
*  [Timeline Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786), **[ligação de vídeo](https://youtu.be/ozMtZ4_NZ10)**
*  [Timeline by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427), [ligação de vídeo](https://youtu.be/szNi9YgXFJc)
*  [Tornado chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768), **[ligação de vídeo](https://www.youtube.com/watch?v=AQvd2FhRyCI)**
*  [Gráfico de Transações da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823)
* [Ultimate KPI Card](https://appsource.microsoft.com/product/power-bi-visuals/WA104381977)
*  [Ultimate Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140), **[ligação de vídeo](https://youtu.be/pDYF8iZxERs)**
*  [Ultimate Waterfall](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956), **[ligação de vídeo](https://youtu.be/0BZsVCQdEkc)**
*  [Lista de Utilizadores da CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426)
*  [Diagrama Venn da MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381231)
*  [Violin Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104381947)
*  [Visio Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104381132)
*  [Waffle Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049), **[ligação de vídeo](https://youtu.be/1vRqYUsm3Vk)**
*  [Word Cloud](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752), **[ligação de vídeo](https://youtu.be/AblTenl9fqo)**

## <a name="faq"></a>PERGUNTAS FREQUENTES

Para obter mais informações acerca dos elementos visuais, aceda às [Perguntas frequentes sobre os elementos visuais certificados](power-bi-custom-visuals-faq.md#certified-power-bi-visuals).

## <a name="next-steps"></a>Próximos passos

* [Developing a Power BI custom visual](../developer/custom-visual-develop-tutorial.md) (Desenvolver um elemento visual personalizado do Power BI)
* [Lista de reprodução visual personalizada da Microsoft no YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Visualizações no Power BI](../visuals/power-bi-report-visualizations.md)  
* [Visualizações Personalizadas no Power BI](power-bi-custom-visuals.md)  
* [Publicar elementos visuais do Power BI no Microsoft AppSource](../developer/office-store.md) 
* Se for um programador Web interessado em criar os seus próprios elementos visuais Power BI e adicioná-los ao  [Microsoft AppSource](https://appsource.microsoft.com), comece pelo tutorial  [Desenvolver um elemento visual do Power BI](visuals/custom-visual-develop-tutorial.md). 

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
