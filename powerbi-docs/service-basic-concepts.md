---
title: "Power BI - conceitos básicos"
description: "Power BI - conceitos básicos"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: B2vd4MQrz4M
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/31/2017
ms.author: mihart
ms.openlocfilehash: f20ea18fb46928bf7533caacf55a0cdb3d761571
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="power-bi---basic-concepts-for-power-bi-service"></a>Power BI - conceitos básicos para o serviço Power BI
<!-- Shared newnav Include -->
[!INCLUDE [newnavbydefault](./includes/newnavbydefault.md)]

Este artigo pressupõe que já se [inscreveu no Power BI](service-self-service-signup-for-power-bi.md) e [adicionou dados](service-get-data.md).

Quando abrir o serviço Power BI, irá ver um ***dashboard*** apresentado. Os dashboards são um elemento que distingue o serviço Power BI do Power BI Desktop.

![](media/service-basic-concepts/completenewer.png)

As principais funcionalidades da IU do serviço Power BI são as seguintes:

1. barra de navegação
2. dashboard com mosaicos
3. caixa de perguntas das Perguntas e Respostas
4. botões de ajuda e comentários
5. título do dashboard
6. Iniciador da aplicações do Office 365
7. Botões da página inicial do Power BI
8. Ações adicionais do dashboard

Aprofundaremos estes itens mais tarde, mas primeiro vamos examinar alguns conceitos do Power BI.

Pode também ver este vídeo antes de ler o resto do artigo.  No vídeo, o Will revê os conceitos básicos e faz uma apresentação do serviço Power BI.

<iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>


## <a name="power-bi-concepts"></a>Conceitos do Power BI
Os 3 principais blocos modulares do Power BI são: ***dashboards***, ***relatórios*** e ***conjuntos de dados***. Não pode ter dashboards ou relatórios sem dados (aliás, pode ter dashboards vazios e relatórios vazios, mas não são muito úteis até que tenham dados), por isso vamos começar pelos **conjuntos de dados**.

## <a name="datasets"></a>Conjuntos de dados
Um *conjunto de dados* é uma coleção de dados que *importa* ou à qual se *liga*. O Power BI permite ligar-se e importar todos os tipos de conjuntos de dados e reuni-los num único lugar.  

Na barra de navegação, os conjuntos de dados aos quais se ligou ou que importou são apresentados sob o cabeçalho **Conjuntos de dados**. Cada conjunto de dados listado representa uma origem de dados única, por exemplo, um livro do Excel no OneDrive, um conjunto de dados tabular SSAS local ou um conjunto de dados do Salesforce. São suportadas muitas origens de dados diferentes e estamos sempre a adicionar novas. [Consulte a lista de tipos de conjuntos de dados que podem ser utilizados com o Power BI](service-get-data.md).

**UM** conjunto de dados...

* pode ser usado repetidas vezes, indefinidamente.
* pode ser usado em vários relatórios diferentes.
* Visualizações desse conjunto de dados único podem ser exibidas em vários dashboards diferentes.
  
  ![](media/service-basic-concepts/drawing2.png)

Para se [ligar ou importar um conjunto de dados](service-get-data.md), selecione **Obter Dados** (na parte inferior da barra de navegação) ou selecione o ícone de adição junto do cabeçalho **Conjuntos de Dados**. Siga as instruções para se ligar ou importar a origem específica e adicionar o conjunto de dados à sua área de trabalho. Os novos conjuntos de dados aparecem listados no painel de navegação à esquerda e marcados com um asterisco amarelo. O trabalho que realiza no Power BI não altera o conjunto de dados subjacente.

Se fizer [parte de uma ***área de trabalho de aplicação***](service-collaborate-power-bi-workspace.md), os conjuntos de dados adicionados por um membro da área de trabalho serão disponibilizados para os restantes membros da área de trabalho.

Os conjuntos de dados podem ser atualizados, renomeados, explorados, utilizados para criar relatórios e removidos. Para explorar um conjunto de dados, selecione-o. O que está realmente a fazer é abrir o conjunto de dados no editor de relatórios, onde pode de facto começar a explorar os dados e a criar visualizações. Vamos então passar para o próximo tópico – relatórios.

### <a name="dig-deeper"></a>Aprofunde:
* [Power BI Premium – o que é?](service-premium.md)
* [Obter dados para o Power BI](service-get-data.md)
* [Conjuntos de dados de exemplo e pacotes de conteúdo para o Power BI](sample-datasets.md)

## <a name="reports"></a>Relatórios
Um relatório do Power BI é uma ou mais páginas de visualizações (gráficos como gráficos de linhas, gráficos circulares, treemaps, entre outros). As visualizações chamam-se também ***visuais***. Todas as visualizações num relatório vêm de um único conjunto de dados. Os relatórios podem ser criados do zero com o Power BI, podem ser importados com dashboards que os seus colegas partilham consigo ou podem ser criados quando se liga a conjuntos de dados do Excel, Power BI Desktop, bases de dados, aplicações SaaS e [pacotes de conteúdos](service-organizational-content-pack-introduction.md).  Por exemplo, quando se liga a um livro do Excel que contém folhas do Power View, o Power BI cria um relatório baseado nessas folhas. E quando se liga a uma aplicação SaaS, o Power BI importa um relatório previamente criado.

Há dois modos de ver e interagir com relatórios: [Vista de Leitura](service-report-open-in-reading-view.md) e [Vista de Edição](service-interact-with-a-report-in-editing-view.md).  Apenas a pessoa que criou o relatório, os coproprietários e as pessoas com permissão concedida têm acesso a todas as capacidades de exploração, estruturação, criação e partilha da ***Vista de Edição*** desse relatório. As pessoas com quem partilharem o relatório podem explorar e interagir com o relatório ao utilizar a ***Vista de Leitura***.   

No painel de navegação, os seus relatórios são listados no cabeçalho **Relatórios**. Cada relatório listado representa uma ou mais páginas de visualizações, com base num dos conjuntos de dados subjacentes. Para abrir um relatório, basta selecioná-lo. Por predefinição, o relatório é aberto primeiro na Vista de Leitura.  Basta selecionar **Editar relatório** para abrir o mesmo na Vista de Edição (se tiver as permissões necessárias).  Se um dashboard partilhado tiver relatórios, NÃO verá o relatório listado na barra de navegação. Em vez disso, abra relatórios partilhados diretamente a partir do dashboard partilhado selecionando um mosaico de dashboard (mais informações sobre os mosaicos serão fornecidas posteriormente).

**UM** relatório...

* pode ser associado a vários dashboards (os mosaicos afixados desse relatório único podem aparecer em vários dashboards).
* pode ser criado utilizando dados de um conjunto de dados. (a pequena exceção é que o Power BI Desktop pode combinar mais de um conjunto de dados num único relatório que pode, por sua vez, ser importado para o Power BI)
  
  ![](media/service-basic-concepts/drawing3new.png)

## <a name="dashboards"></a>Dashboards
Um *dashboard* é algo que cria ou algo que um colega cria e partilha consigo. Trata-se de uma única tela, que contém zero ou mais mosaicos e widgets. Cada mosaico mostra uma única [visualização](power-bi-report-visualizations.md) que foi criada a partir de um conjunto de dados e afixada ao dashboard. Há várias formas de adicionar mosaicos ao seu dashboard; demasiadas para serem abordadas neste tópico de descrição geral. Para saber mais, consulte [Mosaicos de dashboard no Power BI](service-dashboard-tiles.md). 

Na barra de navegação, os "seus" dashboards são listados sob o cabeçalho **Dashboards**. "Seus" significa que tem acesso a eles, não necessariamente que os criou. Cada dashboard representa uma vista personalizada de algum subconjunto dos conjuntos de dados subjacentes.  Se for o proprietário do dashboard, também terá acesso aos conjuntos de dados subjacentes e estes aparecerão na barra de navegação, em **Conjuntos de dados**.  Se o dashboard foi partilhado consigo, tem um ícone de partilha ![](media/service-basic-concepts/sharing-icon.png) junto ao mesmo e, dependendo de como foi partilhado, pode ou não ver os conjuntos de dados subjacentes listados na sua barra de navegação.

> [!NOTE]
> A afixação e os mosaicos são abordados mais detalhadamente sob o cabeçalho "Dashboard com mosaicos".
> 
> 

**UM** dashboard...

* pode exibir visualizações de vários conjuntos de dados diferentes
* pode exibir visualizações de vários relatórios diferentes
* pode mostrar visualizações afixadas de outras ferramentas (por exemplo, Excel)
  
  ![](media/service-basic-concepts/drawing1.png)

### <a name="dig-deeper"></a>Aprofunde:
**Um dashboard pode ser [criado de raiz](service-dashboard-create.md)**. Crie um dashboard novo em branco e, em seguida, obtenha dados. 

**O utilizador, ou um colega seu, pode criar um dashboard e [partilhá-lo](service-share-dashboards.md)**. Quando aceitar o convite, o dashboard partilhado, bem como qualquer relatório e conjunto de dados associado, será adicionado à sua barra de navegação. O Power BI Pro é necessário tanto para partilhar um dashboard como para visualizar um dashboard partilhado.

**Às vezes, os dashboards são importados com o conjunto de dados ou são criados quando o utilizador se liga ao conjunto de dados**. Por exemplo, o assistente **Obter Dados** para Salesforce pergunta-lhe se pretende que um dashboard e/ou relatório seja criado a partir do conjunto de dados. 

**Por que é que as pessoas criam dashboards?**  Eis apenas alguns dos motivos:

* para ver rapidamente todas as informações necessárias para tomar decisões
* para monitorizar as informações mais importantes sobre os seus negócios
* para garantir que todos os colegas estão em sintonia, visualizando e usando a mesma informação
* para monitorizar a solidez de uma empresa, produto, unidade de negócio, campanha de marketing, etc.
* para criar uma vista personalizada de um dashboard maior – todas as métricas que são importantes para mim

## <a name="my-workspace"></a>A minha área de trabalho
Voltámos ao dashboard e área de trabalho do Power BI. Vamos ver mais atentamente os elementos que constituem a pasta de destino do serviço Power BI.

![](media/service-basic-concepts/completenewer.png)

### <a name="1-navigation-bar-navbar"></a>1. **Barra de navegação**
Use a barra de navegação para mover-se entre os blocos modulares do Power BI: dashboards, relatórios e conjuntos de dados.  

  ![](media/service-basic-concepts/navpane-new.png)

* Selecione **Obter Dados** para [adicionar conjuntos de dados, relatórios e dashboards ao Power BI](service-get-data.md).
* Expanda e recolha a barra de navegação com este ícone ![](media/service-basic-concepts/expand-icon.png).
* Utilize **Procurar** para encontrar itens específicos na barra de navegação.
* Selecione um ícone de adição ![](media/service-basic-concepts/pbi_nancy_plus.png) para criar um novo dashboard ou obter um novo conjunto de dados.
* Os **Dashboards, Relatórios** e **Conjuntos de dados** estão disponíveis para utilização.  Os dashboards partilhados são só de leitura e exibem o ícone de partilhado ![](media/service-basic-concepts/sharing-icon.png).
* Os nomes de dashboards, relatórios e conjuntos de dados correspondem normalmente ao nome do ficheiro de conjunto de dados subjacente, mas pode [alterar o nome](service-rename.md) dos mesmos.
* Clique com o botão direito do rato num dashboard, relatório ou conjunto de dados para exibir o menu sensível ao contexto. 
  
  ![](media/service-basic-concepts/menu.png)

Clique uma vez em

* um título para recolhê-lo ou expandi-lo
* um dashboard para exibi-lo
* um relatório para abri-lo na Vista de Leitura
* um conjunto de dados para explorá-lo

### <a name="2-dashboard-with-tiles"></a>2. **Dashboard com mosaicos**
Os dashboards são compostos por [mosaicos](service-dashboard-tiles.md).  Os mosaicos são criados na Vista Edição do relatório, Perguntas e Respostas, outros dashboards e podem ser afixados do Excel, SSRS, entre outros. Um tipo especial de mosaico, intitulado [widget](service-dashboard-add-widget.md), é adicionado diretamente ao dashboard. Os mosaicos que aparecem num dashboard foram especificamente inseridos no sítio pelo criador/proprietário de um relatório.  O ato de adicionar um mosaico a um dashboard denomina-se *afixar*.

![](media/service-basic-concepts/canvas.png)

Para obter mais informações, consulte **Dashboards** (acima).

### <a name="3-qa-question-box"></a>3. **Caixa de perguntas das Perguntas e Respostas**
Uma maneira de explorar seus dados é fazer uma pergunta e deixar que as Perguntas e Respostas do Power BI lhe forneçam uma resposta, na forma de uma visualização. As Perguntas e Respostas não podem ser utilizadas para adicionar conteúdo a um relatório – apenas para adicionar conteúdo a dashboards, na forma de mosaicos.

As Perguntas e Respostas procuram uma resposta no conjunto(s) de dados ligado ao dashboard.  Um conjunto de dados ligado é aquele que tem pelo menos um mosaico afixado a esse dashboard.

![](media/service-basic-concepts/qna.png)

Assim que começa a escrever a sua pergunta, as Perguntas e Respostas levam-no até a página de Perguntas e Respostas. À medida que digita, as Perguntas e Respostas ajudam-no a fazer a pergunta certa e a encontrar a melhor resposta com reformulações frásicas, preenchimento automático, sugestões e muito mais. Quando encontrar uma visualização (resposta) de que gosta, afixe-a no seu dashboard. Para obter mais informações, consulte [Perguntas e Respostas no Power BI](service-q-and-a.md).

### <a name="4-full-screen-notifications-settings-downloads-help-and-feedback"></a>4. **Ecrã inteiro, Notificações, Definições, Transferências, Ajuda e comentários**
Os ícones no canto superior direito são os seus recursos para definições, notificações, transferências, obter ajuda e fornecer comentários à equipa do Power BI. Selecione a seta dupla para abrir o dashboard no modo de **Ecrã inteiro**.  

![](media/service-basic-concepts/help-new.png)

### <a name="5-dashboard-title-aka-what-dashboard-is-active"></a>5. **Título do dashboard** (Também conhecido como "Que dashboard está ativo?")
Nem sempre é fácil descobrir que dashboard está ativo.  O título do dashboard aparece na página de exibição do dashboard, na página de Perguntas e Respostas, na Vista de Edição de relatório, na Vista de Leitura de relatório e quando abre um conjunto de dados.   

![](media/service-basic-concepts/dash-title-new.png)

### <a name="6-office-365-app-launcher"></a>6. **Iniciador de aplicações do Office 365**
O iniciador de aplicações foi criado para ajudá-lo com as suas aplicações do Office 365.

![](media/service-basic-concepts/basicconcepts2-newer.png)

### <a name="7-power-bi-home"></a>7. **Página inicial do Power BI**
Selecionar esta opção leva-o de novo para o dashboard visualizado mais recentemente.

   ![](media/service-basic-concepts/version-new.png)

### <a name="8-options"></a>8. **Opções**
Esta secção da área de trabalho contém ícones para interagir com o dashboard.  Além de **Adicionar mosaico**, **Favorito** e **Partilhar**, selecionar as reticências mostra opções para duplicar, imprimir e atualizar o dashboard e muito mais.

   ![](media/service-basic-concepts/options.png)

## <a name="next-steps"></a>Passos seguintes
[Introdução ao Power BI](service-get-started.md)  
[Vídeos do Power BI](videos.md)  
[Power BI Premium – o que é?](service-premium.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

