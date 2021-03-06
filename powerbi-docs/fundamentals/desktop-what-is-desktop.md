---
title: O que é o Power BI Desktop?
description: Saiba mais sobre o Power BI Desktop e como começar a utilizá-lo.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-fundamentals
ms.topic: overview
ms.date: 07/23/2020
LocalizationGroup: Get started
ms.openlocfilehash: 07dba29c57b533537513d84361b4b7b2b61f9221
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088126"
---
# <a name="what-is-power-bi-desktop"></a>O que é o Power BI Desktop?

O *Power BI Desktop* é uma aplicação gratuita que instala no seu computador local e que lhe permite ligar-se a dados, transformá-los e visualizá-los. Com o Power BI Desktop, pode ligar-se a múltiplas origens de dados diferentes e combiná-las (frequentemente denominado *modelação*) num modelo de dados. Este modelo de dados permite que crie elementos visuais e coleções de elementos visuais que pode partilhar como relatórios, com outras pessoas da sua organização. A maioria dos utilizadores que trabalha em projetos de Business Intelligence utiliza o Power BI Desktop para criar relatórios e, em seguida, utiliza o *serviço Power BI* para partilhar os seus relatórios com outras pessoas.

![Captura de ecrã a mostrar o Power B I Desktop com dados de amostra.](media/desktop-what-is-desktop/what-is-desktop_01.png)

Eis as utilizações mais comuns para o Power BI Desktop:

* Ligar-se a dados
* Transformar e limpar esses dados, para criar um modelo de dados
* Criar elementos visuais, tais como gráficos ou tabelas, que fornecem representações visuais dos dados
* Criar relatórios que são coleções de elementos visuais, numa ou mais páginas de relatório
* Partilhar relatórios com outros utilizadores com o serviço Power BI

As pessoas mais frequentemente responsáveis por essas tarefas são bastantes vezes consideradas *analistas de dados* (por vezes denominadas *analistas*) ou profissionais de business intelligence (frequentemente denominadas *criadores de relatórios*). No entanto, muitas pessoas que não se consideram analistas ou criadoras de relatórios utilizam o Power BI Desktop para criar relatórios apelativos ou para obter dados de várias origens e criar modelos de dados, que podem partilhar com os seus colegas e organizações.


> [!IMPORTANT]
> O Power BI Desktop é atualizado e lançado mensalmente e incorpora feedback dos clientes e novas funcionalidades. Apenas é suportada a versão mais recente do Power BI Desktop. Aos clientes que contactarem o suporte do Power BI Desktop, será pedido que atualizem para a versão mais recente. Pode obter a versão mais recente do Power BI Desktop na [Windows Store](https://aka.ms/pbidesktopstore). Também pode obtê-la como um único ficheiro executável, com todos os idiomas suportados, que pode [transferir](https://www.microsoft.com/download/details.aspx?id=58494) e instalar no seu computador.


Existem três vistas disponíveis no Power BI Desktop, que seleciona no lado esquerdo da tela. As vistas, mostradas pela ordem em que aparecem, são as seguintes:
* **Relatório**: Nesta vista, cria relatórios e elementos visuais, que utiliza na maior parte do tempo de criação.
* **Dados**: Nesta vista, pode ver as tabelas, as medidas e outros dados usados no modelo de dados associado ao relatório e transformar os dados para melhor utilização no modelo do relatório.
* **Modelo**: Nesta vista, vê e gere as relações entre tabelas no seu modelo de dados.

A imagem seguinte mostra as três vistas, conforme apresentadas ao longo do lado esquerdo da tela:

![Captura de ecrã a mostrar o Power B I Desktop com o painel Três Vistas.](media/desktop-what-is-desktop/what-is-desktop-07.png)
 

## <a name="connect-to-data"></a>Ligar-se a dados
Para começar a utilizar o Power BI Desktop, o primeiro passo é ligar-se aos dados. Existem bastantes origens de dados diferentes às quais se pode ligar a partir do Power BI Desktop. 

Para se ligar aos dados:

1. No friso **Home page**, selecione **Obter Dados** > **Mais**. 

   A janela **Obter Dados** é apresentada e mostra as várias categorias às quais o Power BI Desktop se pode ligar.

   ![Captura de ecrã a mostrar o Power B I Desktop, com a caixa de diálogo Obter Dados.](media/desktop-what-is-desktop/what-is-desktop_02.png)

2. Quando seleciona um tipo de dados, são-lhe pedidas informações, tais como o URL e as credenciais, que são precisos para o Power BI Desktop se ligar à origem de dados em seu nome.

   ![Captura de ecrã a mostrar o Power B I Desktop, com a caixa de diálogo da Base de Dados do S Q L Server.](media/desktop-what-is-desktop/what-is-desktop_03.png)

3. Depois de se ligar a uma ou mais origens de dados, sugerimos que transforme os dados de modo a serem-lhe mais úteis.

## <a name="transform-and-clean-data-create-a-model"></a>Transformar e limpar dados, criar um modelo

No Power BI Desktop, pode limpar e transformar os dados com o [Editor do Power Query](../transform-model/desktop-query-overview.md) incorporado. Com o Editor do Power Query, pode efetuar alterações aos seus dados, tais como alterar um tipo de dados, remover colunas ou combinar dados de várias origens. É um pouco como a escultura: pode começar com um bloco grande de barro (ou dados) e, em seguida, ir retirando pedaços ou adicionar outros conforme seja preciso, até que a forma dos dados seja aquela que quer. 

Para iniciar o Editor do Power Query:

- Na fita **Home,** na secção **Consultas,** selecione **Transform data**.

   É apresentada a janela do **Editor do Power Query**.

   ![Captura de ecrã a mostrar o Power B I Desktop, com a janela do Editor do Power Query.](media/desktop-getting-started/designer_gsg_editquery.png)

Cada etapa executada na transformação de dados (como mudar o nome de uma tabela, transformar um tipo de dados ou eliminar uma coluna) é registada pelo Editor do Power Query. Sempre que esta consulta for ligada à origem de dados, os passos serão executados. Deste modo, os dados ficam sempre formatados da forma que o utilizador especificar.

A imagem seguinte mostra a janela do **Editor do Power Query** relativamente a uma consulta que tenha sido formatada e transformada num modelo.

 ![Captura de ecrã a mostrar o Power B I Desktop, com a janela do Editor do Power Query de uma consulta formatada.](media/desktop-getting-started/shapecombine_querysettingsfinished.png)

Assim que os dados estiverem consoante as suas preferências, pode criar elementos visuais. 

## <a name="create-visuals"></a>Criar elementos visuais 

Depois de ter um modelo de dados, pode arrastar *campos* para a tela de relatórios para criar *elementos visuais*. Um elemento visual é uma representação gráfica dos dados no seu modelo. Existem vários tipos de elementos visuais à sua escolha no Power BI Desktop. O visual seguinte mostra um gráfico de colunas simples. 

![Captura de ecrã a mostrar o Power B I Desktop com um gráfico de barras de amostra.](media/desktop-what-is-desktop/what-is-desktop_04.png)

Para criar ou alterar um elemento visual: 

- No painel **Visualizações**, selecione o ícone do elemento visual. 

   ![Captura de ecrã a mostrar o Power B I Desktop com o painel Visualizações.](media/desktop-what-is-desktop/what-is-desktop_05.png)

   Se já tiver um elemento visual selecionado na tela de relatórios, o elemento visual selecionado muda para o tipo que selecionou. 

   Se não estiver selecionado nenhum elemento visual na tela, é criado um elemento visual novo com base na sua seleção.


## <a name="create-reports"></a>Create reports (Criar relatórios)

Mais frequentemente, é provável que queira criar uma coleção de elementos visuais que mostram vários aspetos dos dados que utilizou para criar o seu modelo no Power BI Desktop. Uma coleção de elementos visuais, num ficheiro do Power BI Desktop, denomina-se *relatório*. Um relatório pode ter uma ou mais páginas, tal como um ficheiro do Excel pode ter uma ou mais folhas de cálculo.

Com o Power BI Desktop, pode criar relatórios visualmente avançados e complexos com dados de várias origens, todos num relatório que pode partilhar com outras pessoas na sua organização.

Na imagem seguinte, apresentamos a primeira página de um relatório do Power BI Desktop, com o nome de **Descrição geral**, como se pode ver no separador perto da parte inferior da imagem. 

![Captura de ecrã a mostrar o Power B I Desktop com o separador Descrição Geral.](media/desktop-what-is-desktop/what-is-desktop_01.png)

## <a name="share-reports"></a>Relatórios de partilha

Depois de um relatório estar pronto para ser partilhado com outras pessoas, pode *publicar* o relatório no serviço Power BI e disponibilizá-lo a qualquer pessoa na sua organização que tenha uma licença do Power BI. 

Para publicar um relatório do Power BI Desktop: 

1. Selecione **Publicar** no friso **Base**.

   ![Captura de ecrã a mostrar o Power B I Desktop com o botão Publicar.](media/desktop-what-is-desktop/what-is-desktop_06.png)

   O Power BI Desktop liga-o ao serviço Power BI com a sua conta do Power BI. 

2. O Power BI solicita que selecione onde no serviço Power BI gostaria de partilhar o relatório, tal como a sua área de trabalho, uma área de trabalho de equipa ou qualquer outro local no serviço Power BI. 

   Precisa de ter uma licença do Power BI para partilhar relatórios no serviço Power BI.


## <a name="next-steps"></a>Próximos passos

Para começar a utilizar o Power BI Desktop, primeiro precisa de transferir e instalar a aplicação. Existem duas formas de obter o Power BI Desktop:

* [Obter o Power BI Desktop a partir da Loja Windows](https://aka.ms/pbidesktopstore)
* [Transferir o Power BI Desktop a partir da Web](https://www.microsoft.com/download/details.aspx?id=58494)
