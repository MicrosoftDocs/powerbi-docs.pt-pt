---
title: O que é o Power BI Desktop?
description: Saiba o que é o Power BI Desktop e como começar a utilizá-lo
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: overview
ms.date: 09/19/2019
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: 01e5effcf5f72dd110005815e2ba86c9a6731a70
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73865138"
---
# <a name="what-is-power-bi-desktop"></a>O que é o Power BI Desktop?

O **Power BI Desktop** é uma aplicação gratuita que pode instalar no seu computador local e que lhe permite ligar-se a dados, transformá-los e visualizá-los. Com o **Power BI Desktop**, pode ligar-se a várias origens de dados diferentes e combiná-las (frequentemente denominado modelação) num modelo de dados que lhe permite compilar elementos visuais e coleções de elementos visuais que pode partilhar como relatórios com outras pessoas dentro da sua organização. A maioria dos utilizadores que trabalha em projetos de Business Intelligence utiliza o **Power BI Desktop** para criar relatórios e, em seguida, utiliza o **serviço Power BI** partilhar os seus relatórios com outras pessoas.

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

Eis as utilizações as mais comuns para o **Power BI Desktop**:

* Ligar-se a dados
* Transformar e limpar esses dados, para criar um modelo de dados
* Criar elementos visuais, tais como gráficos ou tabelas, que fornecem representações visuais dos dados
* Criar relatórios que são coleções de elementos visuais, numa ou mais páginas de relatório
* Partilhar relatórios com outros utilizadores com o **serviço Power BI**

As pessoas mais frequentemente responsáveis por essas tarefas são bastantes vezes consideradas *analistas de dados* (por vezes apenas denominadas *analistas*) ou profissionais de Business Intelligence (frequentemente denominadas *criadores de relatórios*). No entanto, muitas pessoas que não se consideram um analista ou um criador de relatórios utilizam o **Power BI Desktop** para criar relatórios convincentes ou para obter dados de várias origens e criar modelos de dados, que podem partilhar com os seus colegas e organizações.

Existem três vistas no Power BI Desktop, mostradas ao longo do lado esquerdo da tela. As vistas, mostradas pela ordem em que aparecem, são as seguintes:
* **Vista de Relatório** – aqui é onde cria relatórios e elementos visuais e onde a maior parte do tempo de criação é passado.
* **Vista de Dados** – aqui pode ver as tabelas, as medidas e outros dados usados no modelo de dados associado ao relatório e transformar os dados para melhor utilização no modelo do relatório.
* **Vista de Modelo** – nesta vista, vê e gere as relações entre tabelas no seu modelo de dados.

A imagem seguinte mostra as três Vistas, conforme apresentadas ao longo do lado esquerdo da tela:

![vistas diferentes](media/desktop-what-is-desktop/what-is-desktop-07.png)


Com o **Power BI Desktop**, pode criar relatórios visualmente avançados e complexos com dados de várias origens, todos num relatório que pode partilhar com outras pessoas na sua organização. 

## <a name="connect-to-data"></a>Ligar-se a dados
Para começar a utilizar o **Power BI Desktop**, o primeiro passo é ligar-se aos dados. Existem bastantes origens de dados diferentes às quais se pode ligar a partir do **Power BI Desktop**. Para se ligar aos dados, basta selecionar o friso **Base** e, em seguida, **Obter Dados > Mais**. A imagem seguinte mostra a janela **Obter Dados** apresentada, que mostra as várias categorias às quais o Power BI Desktop se pode ligar.

![Obter Dados no Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_02.png)

Quando seleciona um tipo de dados, são-lhe pedidas informações, tais como o URL e as credenciais, que são precisos para o Power BI Desktop se ligar à origem de dados em seu nome.

![Ligar a uma base de dados SQL Server no Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_03.png)

Depois de se ligar a uma ou mais origens de dados, sugerimos que transforme os dados de modo a ser-lhe mais útil.

## <a name="transform-and-clean-data-create-a-model"></a>Transformar e limpar dados, criar um modelo

No Power BI Desktop, pode limpar e transformar os dados com o **Editor de Consultas** incorporado. Com o Editor de Consultas, pode efetuar alterações aos seus dados, tais como alterar um tipo de dados, remover colunas ou combinar dados de várias origens. É um pouco como a escultura – pode começar com um bloco grande de barro (ou dados) e, em seguida, ir retirando pedaços ou adicionar outros conforme seja preciso, até que a forma dos dados seja aquela que quer. 

![Editor de Consultas no Power BI Desktop](media/desktop-getting-started/designer_gsg_editquery.png)

Cada passo que realizar na transformação dos dados (como mudar o nome de uma tabela, transformar um tipo de dados ou eliminar colunas) é registado pelo **Editor de Consultas**. Sempre que esta consulta ligar à origem de dados, esses passos serão executados, para que os dados sejam sempre formatados da forma que especificou.

A imagem seguinte mostra o painel **Definições da Consulta** relativamente a uma consulta que tenha sido formatada e transformada num modelo.

 ![](media/desktop-getting-started/shapecombine_querysettingsfinished.png)

Assim que os dados estiverem consoante as suas preferências, pode criar elementos visuais. 

## <a name="create-visuals"></a>Criar elementos visuais 

Depois de ter um modelo de dados, pode arrastar *campos* para a tela de relatórios para criar *elementos visuais*. Um *elemento visual* é uma representação gráfica dos dados no seu modelo. O visual seguinte mostra um gráfico de colunas simples. 

![Um elemento visual no Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_04.png)

Existem vários tipos de elementos visuais à sua escolha no Power BI Desktop. Para criar ou alterar um visual, basta selecionar o ícone visual do painel **Visualizações**. Se tiver um elemento visual selecionado na tela de relatórios, o elemento visual selecionado muda para o tipo que selecionou. Se não estiver selecionado nenhum elemento visual, é criado um visual novo com base na sua seleção.

![O painel Visualizações no Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_05.png)

## <a name="create-reports"></a>Create reports (Criar relatórios)

Mais frequentemente, é provável que queira criar uma coleção de elementos visuais que mostram vários aspetos dos dados que utilizou para criar o seu modelo no Power BI Desktop. Uma coleção de elementos visuais, num ficheiro do Power BI Desktop, denomina-se *relatório*. Um relatório pode ter uma ou mais páginas, tal como um ficheiro do Excel pode ter uma ou mais folhas de cálculo. Na imagem seguinte, apresentamos a primeira página de um relatório do Power BI Desktop, com o nome de Descrição geral (pode ver o separador perto da parte inferior da imagem). Neste relatório, existem dez páginas.

![Relatório do Power BI Desktop com dez páginas](media/desktop-what-is-desktop/what-is-desktop_01.png)

## <a name="share-reports"></a>Relatórios de partilha

Depois de um relatório estar pronto para ser partilhado com outras pessoas, pode **Publicar** o relatório no **serviço Power BI**e disponibilizá-lo a qualquer pessoa na sua organização que tenha uma licença do Power BI. Para publicar um relatório do Power BI Desktop, selecione o botão **Publicar** no friso **Base** no Power BI Desktop.

![Publicar um relatório a partir do Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_06.png)

Depois de selecionar **Publicar**, o Power BI Desktop liga-o ao **serviço Power BI** com a sua conta do Power BI e, em seguida, pede-lhe para selecionar em que parte do serviço Power BI pretende partilhar o relatório, como a sua área de trabalho, uma área de trabalho de equipa ou outra localização no serviço Power BI. Precisa de ter uma licença do Power BI para partilhar relatórios no serviço Power BI.


## <a name="next-steps"></a>Próximos passos

Para começar a utilizar o **Power BI Desktop**, primeiro precisa de transferir e instalar a aplicação. Existem duas formas de obter o **Power BI Desktop**:

* [Transferir o Power BI Desktop a partir da Web](desktop-get-the-desktop.md)
* [Obter o Power BI Desktop a partir da Loja Windows](https://aka.ms/pbidesktopstore)
