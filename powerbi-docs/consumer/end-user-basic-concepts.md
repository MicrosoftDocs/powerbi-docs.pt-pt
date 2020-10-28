---
title: O serviço Power BI – conceitos básicos para utilizadores empresariais
description: As áreas de trabalho, dashboards, relatórios, conjuntos de dados, livros e aplicações do serviço Power BI.
author: mihart
ms.reviewer: mihart
featuredvideoid: B2vd4MQrz4M
ms.service: powerbi
ms.custom: seodec18
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/08/2020
ms.author: mihart
LocalizationGroup: Get started
ms.openlocfilehash: 5c534436b93205d40251c26830be4d6acdfa034d
ms.sourcegitcommit: 6b436f6ed872cbc040ed6e2d3ac089c08fc78daf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928380"
---
# <a name="basic-concepts-for-the-power-bi-service-consumers"></a>Conceitos básicos para os consumidores do serviço Power BI

[!INCLUDE[consumer-appliesto-ynnm](../includes/consumer-appliesto-ynnm.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Este artigo pressupõe que já leu a [Descrição geral do Power BI](../fundamentals/power-bi-overview.md) e que se identificou como um [utilizador empresarial do Power BI](end-user-consumer.md). Os *utilizadores empresariais* recebem conteúdos do Power BI, como dashboards, relatórios e aplicações dos colegas. Os *utilizadores empresariais* trabalham com o serviço Power BI (app.powerbi.com), que é a versão baseada em site do Power BI.

A receção de conteúdo de outras pessoas implica um dos seguintes requisitos:
- Uma licença de utilizador do Power BI Pro
- Que a sua organização tenha uma subscrição do Power BI Premium e que o conteúdo seja partilhado consigo a partir de uma capacidade Power  BI Premium. [Procure os seus tipos de licença e subscrição](end-user-license.md).

Vai, sem dúvida, ouvir o termo “Power BI Desktop” ou apenas “Desktop”. É a ferramenta autónoma utilizada pelos *criadores* que criam e partilham dashboards e relatórios consigo. É importante saber que existem outras ferramentas do Power BI. Desde que seja um utilizador empresarial**, vai trabalhar apenas com o serviço Power BI. Este artigo aplica-se apenas ao serviço Power BI.

## <a name="terminology-and-concepts"></a>Terminologia e conceitos

Este artigo não é um tutorial prático nem uma apresentação visual do Power BI. Trata-se de um artigo de descrição geral para lhe dar a conhecer os conceitos e a terminologia do Power BI. Vai apresentar-lhe os conceitos e explicar-lhe como funcionam. Para uma apresentação do serviço Power BI e da navegação, aceda a [Início Rápido – Introdução ao serviço Power BI](end-user-experience.md).

## <a name="open-the-power-bi-service-for-the-first-time"></a>Abrir o serviço Power BI pela primeira vez

A maioria dos *utilizadores empresariais* do Power BI obtém o serviço Power BI porque 1) a empresa compra licenças e 2) um administrador atribui essas licenças aos colaboradores.

Para começar, abra um browser e escreva **app.powerbi.com** . Na primeira vez que abrir o serviço Power BI, verá algo como o seguinte:

![Uma captura de ecrã do Ecrã de boas-vindas do serviço Power BI.](media/end-user-basic-concepts/power-bi-home-open.png)

À medida que utilizar o serviço Power BI, poderá personalizar o que lhe será apresentado sempre que abrir o site. Por exemplo, algumas pessoas preferem que seja apresentada a **Home Page** do Power BI, enquanto outras pessoas preferem ver um dashboard favorito. Não se preocupe, estes dois artigos vão ensiná-lo a personalizar a sua experiência.

- [Apresentação da Home Page do Power BI e da Pesquisa Global](https://powerbi.microsoft.com/blog/introducing-power-bi-home-and-global-search)

- [Dashboards em destaque no serviço Power BI](end-user-featured.md)

![Uma captura de ecrã que mostra a vista da Home page e a vista do dashboard.](media/end-user-basic-concepts/power-bi-dash-home.png)

Antes de avançar mais, vamos falar sobre os elementos base que constituem o serviço Power BI.

_______________________________________________________

## <a name="power-bi-content"></a>Conteúdos do Power BI

### <a name="introduction-to-building-blocks"></a>Introdução aos elementos base

Para um *utilizador empresarial* do Power BI, os cinco blocos modulares são: **_visualizações_** , **_dashboards_** , **_relatórios_** , **_aplicações_** e **_conjuntos de dados_** . Por vezes, estes elementos são denominados *conteúdos* **_do Power BI_** . Os *conteúdos* existem em **_áreas de trabalho_** . Um fluxo de trabalho típico envolve todos os blocos modulares: Um *criador* do Power BI (a amarelo no diagrama abaixo) recolhe dados de *conjuntos de dados* , incorpora-os no Power BI para análise, cria *relatórios* com *visualizações* que destacam informações e factos interessantes, afixa as visualizações dos relatórios num *dashboard* e partilha os relatórios e dashboards com *clientes empresariais* , como é o seu caso (a preto no diagrama abaixo). O *designer* partilha-os na forma de dashboards, relatórios ou aplicações.

![Um gráfico de fluxo de trabalho do Power BI básico.](media/end-user-basic-concepts/power-bi-workflow.png)

Fundamentalmente:

- ![Uma captura de ecrã do ícone de visualização.](media/end-user-basic-concepts/visual.png) uma **_visualização_** (ou *elemento visual* ), é um tipo de gráfico criado pelos *criadores* do Power BI. Os elementos visuais apresentam os dados a partir de *relatórios* e de *conjuntos de dados* . Geralmente, os *criadores* criam os elementos visuais no Power BI Desktop.

    Para obter mais informações, veja [Interagir com elementos visuais em relatórios, dashboards e aplicações](end-user-visualizations.md).

- ![Uma captura de ecrã do ícone da base de dados.](media/end-user-basic-concepts/power-bi-dataset-icon.png) Um *conjunto de dados* é um contentor de dados. Por exemplo, pode ser um ficheiro do Excel da Organização Mundial de Saúde. Também pode ser uma base de dados dos clientes de uma empresa ou um ficheiro do Salesforce. Os conjuntos de dados são geridos por *designers* .

- ![Uma captura de ecrã do ícone de dashboard.](media/end-user-basic-concepts/dashboard.png) Um *ícone de dashboard* é um único ecrã com gráficos, texto e elementos visuais interativos. Um dashboard recolhe as suas métricas mais importantes, num único ecrã, para contar uma história ou responder a uma pergunta. Os conteúdos do dashboard são provenientes de um ou mais relatórios ou conjuntos de dados.

    Para obter mais informações, veja [Dashboards para os utilizadores empresariais do serviço Power BI](end-user-dashboards.md).

- ![Uma captura de ecrã do ícone de relatório.](media/end-user-basic-concepts/report.png) Um *relatório* é composto por uma ou mais páginas de gráficos, texto e elementos visuais interativos que, em conjunto, constituem um só relatório. O Power BI baseia um relatório num único conjunto de dados. Muitas vezes, o *designer* organiza páginas dos relatórios para abordar uma área de interesse central ou responder a uma única pergunta.

    Para obter mais informações, veja [Relatórios no Power BI](end-user-reports.md).

- ![Uma captura de ecrã do ícone de aplicação.](media/end-user-basic-concepts/app.png) Uma *aplicação* é uma forma de os *criadores* agruparem e partilharem dashboards e relatórios relacionados em conjunto. Os *utilizadores empresariais* recebem algumas aplicações automaticamente, mas podem procurar outras aplicações criadas por colegas ou pela comunidade. Por exemplo, as aplicações prontas a utilizar estão disponíveis para os serviços externos que já pode utilizar, como o Google Analytics e o Microsoft Dynamics CRM.

Ou seja, se for um novo utilizador e iniciar sessão no serviço Power BI pela primeira vez, provavelmente não verá desde logo quaisquer dashboards, aplicações ou relatórios.

_______________________________________________________

## <a name="datasets"></a>Conjuntos de dados

Um *conjunto de dados* é uma coleção de dados importada ou à qual os *criadores* se ligam e depois utilizam para criar relatórios e dashboards. Como *utilizador empresarial* , não vai interagir diretamente com conjuntos de dados, mas pode ser útil compreender o papel dos mesmos no panorama geral.  

Cada conjunto de dados representa uma única origem de dados. Por exemplo, a origem pode ser um livro do Excel no OneDrive, um conjunto de dados tabular no local do SQL Server Analysis Services ou um conjunto de dados do Salesforce. O Power BI suporta várias origens de dados diferentes.

Quando um designer partilha uma aplicação consigo, pode procurar quais conjuntos de dados estão a ser usados, ao abrir **Conteúdo relacionado** .  Não vai poder adicionar ou alterar nada no conjunto de dados. No entanto, se o designer lhe conceder permissões, pode transferir o relatório, procurar [informações nos dados](end-user-insights.md) ou até [criar o seu próprio relatório](../create-reports/service-report-create-new.md) com base no conjunto de dados.  

![Captura de ecrã da interface de utilizador do Power BI e a seta a apontar para a secção Conjuntos de dados na tela.](media/end-user-basic-concepts/power-bi-datasets.png)

Um conjunto de dados...

- Pode ser utilizado várias vezes por um criador de relatórios para criar dashboards e relatórios

- Pode servir para criar vários relatórios diferentes

- Os elementos visuais desse conjunto de dados podem ser apresentados em vários dashboards diferentes

  ![Um gráfico que mostra um conjunto de dados com relações muitos para um](media/end-user-basic-concepts/drawing2.png)

Vamos avançar para o elemento seguinte: as visualizações

_______________________________________________________

## <a name="visualizations"></a>Visualizações

As visualizações (também conhecidas como elementos visuais) apresentam informações que o Power BI descobre nos dados. As visualizações facilitam a interpretação das informações, pois o cérebro consegue compreender mais rápido uma imagem do que uma folha de cálculo com números.

Eis algumas das visualizações que poderá encontrar no Power BI: cascata, friso, mapa de árvore, circular, funil, cartão, dispersão e medidor.

   ![Uma captura de ecrã de oito elementos visuais de exemplo.](media/end-user-basic-concepts/power-bi-visuals.png)

Veja a [lista completa de visualizações incluídas no Power BI](end-user-visual-type.md).

A comunidade disponibiliza visualizações especiais, que são denominadas *elementos visuais personalizados* . Se receber um relatório com um elemento visual que não reconhece, é provável que se trate de um elemento visual personalizado. Se precisar de ajuda para interpretar o elemento visual personalizado, procure o nome do *criador* do relatório ou dashboard e contacte-o. As informações de contacto estão disponíveis ao selecionar o título na barra de menus superior.

Uma visualização num relatório…

- Pode aparecer várias vezes no mesmo relatório

- Pode aparecer em vários dashboards diferentes

_______________________________________________________

## <a name="reports"></a>Relatórios

Um relatório do Power BI é composto por uma ou mais páginas de visualizações, gráficos e texto. Todas as visualizações num relatório vêm de um único conjunto de dados. Os *designers* criam relatórios e partilham-nos com outras pessoas, de forma individual ou como parte de uma aplicação.  Normalmente, os *utilizadores empresariais* [interagem com relatórios na *Vista de leitura*](end-user-reading-view.md).

![Captura de ecrã de um relatório com separadores.](media/end-user-basic-concepts/power-bi-report.png)

Um relatório…

- Pode ser associado a vários dashboards (os mosaicos afixados desse relatório único podem aparecer em vários dashboards).

- Pode ser criado através dos dados de um único conjunto de dados.  

- Pode fazer parte de múltiplas aplicações.

  ![Um gráfico que mostra as relações de um relatório.](media/end-user-basic-concepts/drawing5.png)

_______________________________________________________

## <a name="dashboards"></a>Dashboards

Um dashboard representa uma vista gráfica personalizada de um subconjunto de um ou vários conjuntos de dados subjacentes. Os *designers* criam dashboards e partilham-nos com os *utilizadores empresariais* , de forma individual ou como parte de uma aplicação. Um dashboard é uma única tela que contém *mosaicos* , gráficos e texto.

  ![Captura de ecrã de um dashboard de exemplo](media/end-user-basic-concepts/power-bi-dashboard.png)

Um mosaico é uma representação de um elemento visual que um *criador* *afixa* (por exemplo, de um relatório para um dashboard). Cada mosaico afixado apresenta uma [visualização](end-user-visualizations.md) que o estruturador criou a partir de um conjunto de dados e afixou a esse dashboard. Um mosaico também pode conter uma página de relatório inteira, bem como um vídeo ou dados de transmissão em direto. Os *designers* podem adicionar mosaicos a dashboards de muitas formas, pelo que não é possível abordá-las todas neste artigo geral. Para saber mais, consulte [Mosaicos de dashboard no Power BI](end-user-tiles.md).

Os *utilizadores empresariais* não podem editar dashboards. No entanto, podem adicionar comentários, ver dados relacionados, definir o dashboard como favorito, subscrevê-lo e mais.

Quais são as finalidades dos dashboards?  Eis algumas delas:

- para ver rapidamente todas as informações necessárias para tomar decisões

- para monitorizar as informações mais importantes sobre o seu negócio

- para garantir que todos os colegas estão em sintonia e conseguem ver e utilizar as mesmas informações

- para monitorizar a solidez de uma empresa, produto, unidade de negócio, campanha de marketing, etc.

- para criar uma vista personalizada de um dashboard maior – todas as métricas importantes para si

**UM** dashboard...

- pode exibir visualizações de vários conjuntos de dados diferentes

- pode exibir visualizações de vários relatórios diferentes

- pode mostrar visualizações afixadas de outras ferramentas (por exemplo, Excel)

  ![Um gráfico de relações de um dashboard.](media/end-user-basic-concepts/drawing1.png)

_______________________________________________________

## <a name="apps"></a>Aplicações

Estas coleções de dashboards e relatórios organizam e agrupam os conteúdos num único pacote. Os *designers* do Power BI criam-nos em áreas de trabalho e partilham aplicações com utilizadores individuais, grupos, organizações inteiras ou com o público. Como *utilizador empresarial* , pode ter a certeza de que os seus colegas estão a trabalhar consigo nas mesmas informações: uma única versão fidedigna das informações.

Às vezes, a própria área de trabalho da aplicação é partilhado e pode haver muita gente a colaborar e a atualizar a área de trabalho e a aplicação. A extensão de o que pode fazer com uma aplicação será determinada pelas permissões e pelo acesso que recebeu.

![Captura de ecrã do ecrã Permissões de aplicações.](media/end-user-basic-concepts/power-bi-app-permissions.png)

> [!NOTE]
> A utilização de aplicações exige uma licença do Power BI Pro ou que a área de trabalho da aplicação seja armazenada na capacidade Premium. [Saiba mais sobre as licenças](end-user-license.md).



É fácil encontrar e instalar aplicações no [serviço Power BI](https://powerbi.com) e no dispositivo móvel. Depois de instalar uma aplicação, não precisa de memorizar os nomes de vários dashboards e relatórios diferentes. Estes estão todos juntos numa aplicação, no browser ou no dispositivo móvel.

Esta aplicação tem dois dashboards e dois relatórios que constituem uma única aplicação. Se selecionar a seta à direita do nome de um relatório, verá uma lista de páginas que compõem esse relatório.

![Captura de ecrã de conteúdo relacionado para a aplicação selecionada.](media/end-user-basic-concepts/power-bi-app-display.png)

Sempre que a aplicação for atualizada, verá automaticamente as alterações. Além disso, o autor controla o agendamento para a frequência com que o Power BI atualiza os dados. Não precisa de se preocupar com a atualização dos dados.

Pode obter aplicações de várias formas diferentes:

- O estruturador de aplicações pode instalar a aplicação automaticamente na sua conta do Power BI.

- O estruturador de aplicações pode enviar-lhe uma ligação direta para uma aplicação.

- Pode pesquisar de dentro do serviço Power BI aplicações disponíveis para si a partir da sua organização ou da comunidade. Também pode visitar o [Microsoft AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi), onde verá todas as aplicações que pode utilizar.

No Power BI no seu dispositivo móvel, só pode instalar aplicações a partir de uma ligação direta e não a partir do AppSource. Se o criador da aplicação instalar a aplicação automaticamente, irá vê-la na sua lista de aplicações.

Quando a aplicação estiver instalada, selecione-a na sua lista Aplicações e, em seguida, selecione o dashboard ou o relatório que pretende abrir e explorar primeiro.

![Captura de ecrã da opção Aplicações selecionada no painel esquerdo do Power BI.](media/end-user-basic-concepts/power-bi-apps-card.png)

Esperamos que este artigo tenha sido útil para compreender os blocos modulares que constituem o serviço Power BI para utilizadores empresariais.

## <a name="next-steps"></a>Passos seguintes

- Rever e marcar o [Glossário](end-user-glossary.md)

- Ver [uma apresentação do serviço Power BI](end-user-experience.md)

- Ler a [descrição geral do Power BI destinada a utilizadores empresariais](end-user-consumer.md)

- Ver um vídeo em que o Will explica os conceitos básicos e faz uma apresentação do serviço Power BI.

    <iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>
