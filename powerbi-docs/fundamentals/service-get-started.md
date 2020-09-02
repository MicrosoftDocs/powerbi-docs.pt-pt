---
title: 'Tutorial: Introdução ao serviço de criação no Power BI'
description: Introdução ao serviço Power BI online (app.powerbi.com)
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: tutorial
ms.date: 07/08/2020
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: d40bda8ef6469e5dc826d36db3cc21cfe72f0da6
ms.sourcegitcommit: 70a892df1a0c196db58bf9165b3aa31b26bbe149
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/29/2020
ms.locfileid: "89092389"
---
# <a name="tutorial-get-started-creating-in-the-power-bi-service"></a>Tutorial: Introdução ao serviço de criação no Power BI
Este tutorial é uma introdução a algumas das funcionalidades do *serviço Power BI*. Aqui, irá aprender a ligar-se aos dados, a criar um relatório e um dashboard, e a fazer perguntas sobre os seus dados. As várias funcionalidades do serviço Power BI permitem-lhe fazer muito mais. Este tutorial é só o começo. Para saber como o serviço Power BI se encaixa nas restantes ofertas do Power BI, recomendamos que leia [O que é o Power BI?](power-bi-overview.md).

É um *leitor* de relatórios em vez de um criador? A [Introdução ao serviço Power BI](../consumer/end-user-experience.md) é um bom ponto de partida para si.

:::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="Captura de ecrã a mostrar o dashboard Exemplo Financeiro":::.

Neste tutorial, irá concluir os seguintes passos:

> [!div class="checklist"]
> * Iniciar sessão na sua conta do Power BI online ou inscrever-se, se ainda não tiver uma conta.
> * Abrir o serviço Power BI.
> * Obter alguns dados e abri-los na vista de relatório.
> * Utilizar esses dados para criar visualizações e guardá-las como um relatório.
> * Criar um dashboard ao afixar mosaicos do relatório.
> * Adicionar outra visualização ao dashboard com a ferramenta de linguagem natural Perguntas e Respostas.
> * Redimensionar, reorganizar e editar detalhes para os mosaicos no dashboard.
> * Limpar recursos ao eliminar conjuntos de dados, relatórios e dashboards.

## <a name="sign-up-for-the-power-bi-service"></a>Inscreva-se no serviço do Power BI
Para criar conteúdos no Power BI, é necessária uma licença do Power BI Pro. Se não tiver uma conta no Power BI, [inscreva-se numa avaliação gratuita do Power BI Pro](https://app.powerbi.com/signupredirect?pbi_source=web) antes de começar.

## <a name="step-1-get-data"></a>Passo 1: Obter dados

Geralmente, quando quer criar um relatório do Power BI, começa no Power BI Desktop. O Power BI Desktop dá-lhe mais poder. Pode transformar, formatar e modelar dados, antes de começar a conceber um relatório. Desta vez, contudo, vamos começar a criar do zero um relatório no serviço Power BI.

Neste tutorial, obtemos dados a partir de um ficheiro simples do Microsoft Excel. Quer acompanhar? [Transfira o ficheiro de Exemplo Financeiro](https://go.microsoft.com/fwlink/?LinkID=521962).

1. Para começar, abra o serviço Power BI (app.powerbi.com) no seu browser. 

    Não tem uma conta? Não se preocupe. Pode [inscrever-se numa avaliação gratuita do Power BI Pro](https://app.powerbi.com/signupredirect?pbi_source=web)

1. Na barra de navegação, selecione **A minha área de trabalho**.

1. Em **A minha área de trabalho**, selecione **Novo** > **Carregar um ficheiro**.

    É aberta a página **Obter Dados**.   

3. Na secção **Criar novo conteúdo**, certifique-se de que a opção **Ficheiros** está selecionada e, em seguida, selecione o localização onde quer guardar o ficheiro Excel.
   
    :::image type="content" source="media/service-get-started/power-bi-service-get-data-local-file.png" alt-text="Captura de ecrã a mostrar Criar novo conteúdo > Ficheiros.":::

5. Procure o ficheiro no computador e selecione **Abrir**.

5. Neste tutorial, vamos selecionar **Importar** para adicionar o ficheiro do Excel como um conjunto de dados que podemos utilizar para criar relatórios e dashboards. Se selecionar **Carregar**, todo o livro do Excel será carregado para o Power BI, onde poderá abrir e editar o mesmo no Excel Online.
   
   :::image type="content" source="media/service-get-started/power-bi-import.png" alt-text="Captura de ecrã a mostrar a seleção de Importar.":::
6. Quando o seu conjunto de dados estiver pronto, selecione **Mais opções (...)** junto ao conjunto de dados de Exemplo Financeiro e, em seguida, selecione **Criar relatório**.
1. abra o editor de relatórios. 

    :::image type="content" source="media/service-get-started/power-bi-service-datasets.png" alt-text="Captura de ecrã a mostrar Todo o conteúdo > Criar relatório.":::

    A tela do relatório está em branco. No lado direito, podemos ver os painéis **Filtros**, **Visualizações** e **Campos**.

    :::image type="content" source="media/service-get-started/power-bi-service-blank-report.png" alt-text="Captura de ecrã a mostrar a tela de relatórios em branco.":::

    > [!TIP]
    > Selecione o botão de navegação global no canto superior esquerdo para fechar o painel de navegação. Desta forma, a sua tela tem mais espaço.
    >
    >:::image type="content" source="media/service-get-started/power-bi-global-nav-button.png" alt-text="Botão de navegação global.":::
    >

7. Encontra-se atualmente na Vista de Edição. Veja a opção **Vista de Leitura** na barra de menus. 

    :::image type="content" source="media/service-get-started/power-bi-service-reading-view.png" alt-text="Captura de ecrã a mostrar a opção Vista de Leitura.":::

    Enquanto estiver na Vista de Edição, pode modificar os relatórios, uma vez que é o *proprietário* e *criador* do relatório. Quando partilha o seu relatório com colegas, muitas vezes só conseguem interagir com o relatório na Vista de Leitura. São *consumidores* dos relatórios em **A minha área de trabalho**. 

## <a name="step-2-create-a-chart-in-a-report"></a>Passo 2: Criar um gráfico num relatório
Agora que já está ligado aos dados, pode começar a explorar. Quando encontrar alguma coisa interessante, pode guardá-la na tela de relatórios. Em seguida, pode afixá-la num dashboard para monitorizá-la e ver como se altera ao longo do tempo. Comecemos pelo mais importante.
    
1. No editor de relatórios, comece pelo painel **Campos**, no lado direito da página, para criar uma visualização. Selecione o campo **Gross Sales** e, em seguida, o campo **Date**.
   
   :::image type="content" source="media/service-get-started/power-bi-service-fields-pane-selected.png" alt-text="Captura de ecrã a mostrar a lista Campos.":::

    O Power BI analisa os dados e cria uma visualização do gráfico de colunas. 

    > [!NOTE]
    > Se selecionar primeiro o campo **Date** em vez de **Gross Sales**, verá uma tabela. Não se preocupe! Vamos alterar a visualização no próximo passo.

    Alguns campos têm símbolos de sigma ao lado dos mesmos, porque o Power BI detetou que contêm valores numéricos.

    :::image type="content" source="media/service-get-started/power-bi-sigma-fields.png" alt-text="Campos com símbolos de sigma.":::

2. Vamos mudar para uma forma diferente de apresentar estes dados. Os gráficos de linhas são bons elementos visuais para apresentar os valores ao longo do tempo. No painel **Visualizações**, selecione o ícone do **Gráfico de linhas**.
   
   :::image type="content" source="media/service-get-started/power-bi-service-select-line-chart.png" alt-text="Captura de ecrã a mostrar o editor de Relatórios, com o gráfico de linhas selecionado.":::

3. Este gráfico parece ser interessante, por isso, vamos *afixá-lo* a um dashboard. Passe o cursor sobre a visualização e selecione o ícone de afixar.
   
   :::image type="content" source="media/service-get-started/power-bi-service-pin-visual.png" alt-text="Captura de ecrã a mostrar o ícone Afixar.":::

4. Como este relatório é novo, será pedido que o guarde antes de poder afixar uma visualização num dashboard. Dê um nome ao seu relatório (por exemplo, *relatório de Exemplo Financeiro*) e, em seguida, selecione **Guardar**. 

    Está agora a ver o relatório na Vista de Leitura. 

6. Selecione o ícone **Afixar** novamente.
 
5. Selecione **Novo dashboard** e dê-lhe, por exemplo, o nome *dashboard de Exemplo Financeiro*. 
   
   :::image type="content" source="media/service-get-started/power-bi-pin.png" alt-text="Captura de ecrã a mostrar a opção Dar um nome ao dashboard.":::
  
    Uma mensagem de êxito (perto do canto superior direito) informa que a visualização foi adicionada como um mosaico ao dashboard.
   
    :::image type="content" source="media/service-get-started/power-bi-pin-success.png" alt-text="Captura de ecrã a mostrar a caixa de diálogo Afixar no dashboard.":::

    Agora que já afixou esta visualização, encontra-se armazenada no seu dashboard. Os dados ficam atualizados de forma a que possa controlar os valores mais recentes numa visão geral. Contudo, se alterar o tipo de visualização no relatório, a visualização no dashboard não se altera.

7. Selecione **Aceder ao dashboard** para ver o novo dashboard com o gráfico de linhas afixado como um mosaico. 
   
   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tile.png" alt-text="Captura de ecrã a mostrar o dashboard, com uma visualização afixada.":::
   
8. Selecione um novo mosaico no seu dashboard. O Power BI regressa ao relatório na Vista de leitura.

1. Para mudar novamente para a Vista de edição, selecione **Mais opções** (...) na barra de menus > **Editar**.

    :::image type="content" source="media/service-get-started/power-bi-service-edit-report.png" alt-text="Captura de ecrã a mostrar a seleção Editar para editar o relatório.":::

    Quando voltar à Vista de edição, pode continuar a explorar e a afixar mosaicos.

## <a name="step-3-explore-with-qa"></a>Passo 3: Explorar através da caixa Perguntas e Respostas

Para explorar os dados rapidamente, experimente fazer uma pergunta na caixa de Perguntas e Respostas. As Perguntas e Respostas permitem-lhe fazer consultas com uma linguagem natural sobre os seus dados. Nos dashboards, a caixa Perguntas e Respostas está na parte superior (**Fazer uma pergunta sobre os dados**) abaixo da barra de menus. Num relatório, está na barra de menus superior (**Fazer uma pergunta**).

1. Para voltar ao dashboard, selecione **A minha área de trabalho** na barra de cabeçalho preta do **Power BI**.

    :::image type="content" source="media/service-get-started/power-bi-service-go-my-workspace.png" alt-text="Captura de ecrã a mostrar a opção Voltar à página A minha área de trabalho.":::

1. Na página **A minha área de trabalho**, selecione o seu dashboard.

    :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tab.png" alt-text="Captura de ecrã a mostrar a seleção do seu dashboard.":::

1. Selecione **Fazer uma pergunta sobre os dados**. A caixa Perguntas e Respostas oferece automaticamente várias sugestões. 

    :::image type="content" source="media/service-get-started/power-bi-service-new-qanda.png" alt-text="Captura de ecrã a mostrar a tela Perguntas e Respostas.":::

    > [!NOTE]
    > Se não vir as sugestões, ative a **Nova experiência de Perguntas e Respostas**.

    :::image type="content" source="media/service-get-started/power-bi-new-qna-experience.png" alt-text="Captura de ecrã a mostrar a ativação da nova experiência das Perguntas e Respostas.":::

1. Algumas sugestões devolvem um único valor. Por exemplo, selecione **qual é a média de cog**.

    A caixa Perguntas e Respostas procura uma resposta e apresenta-a sob a forma de uma visualização de *cartão*.

3. Selecione **Afixar elemento visual** e afixe esta visualização ao dashboard de Exemplo Financeiro.

    :::image type="content" source="media/service-get-started/power-bi-qna-pin-tile.png" alt-text="Captura de ecrã a mostrar como afixar o elemento visual.":::

1. Regresse às Perguntas e Respostas e selecione **Mostrar todas as sugestões**.
1. Selecione **total profit por country**. 

    :::image type="content" source="media/service-get-started/power-bi-qna-total-profit-country.png" alt-text="Captura de ecrã a mostrar o lucro total (total profit) por país (country).":::

1. Afixe também o mapa ao dashboard de Exemplo Financeiro.

1. No dashboard, selecione o mapa que acabou de afixar. Vê como abriu as Perguntas e Respostas novamente? 
1. Coloque o cursor depois de *por country* na caixa Perguntas e Respostas e escreva *em barras*. O Power BI cria um gráfico de barras com os resultados.

    :::image type="content" source="media/service-get-started/power-bi-qna-profit-country-bar.png" alt-text="Captura de ecrã a mostrar a visualização do gráfico de barras.":::

1. Afixe também o gráfico de barras ao dashboard de Exemplo Financeiro.

4. Selecione **Sair das Perguntas e Respostas** e regresse ao seu dashboard, onde verá os novos mosaicos que criou. 

   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-qna.png" alt-text="Captura de ecrã a mostrar um dashboard, com os elementos visuais das Perguntas e Respostas afixados.":::

   Veja que, apesar de ter alterado o mapa para um gráfico de barras nas Perguntas e Respostas, o mosaico manteve-se um mapa, porque era um mapa quando o afixou. 

## <a name="step-4-reposition-tiles"></a>Step 4: Reposicionar os mosaicos

Podemos reorganizar os mosaicos para garantir uma melhor utilização do espaço do dashboard.

1. Arraste o canto inferior direito do mosaico do gráfico de linhas *Vendas Brutas* para cima, até que fique à mesma altura do mosaico Vendas, e depois solte-o.

    :::image type="content" source="media/service-get-started/power-bi-service-resize-tile.png" alt-text="Captura de ecrã a mostrar como redimensionar o mosaico.":::

    Agora, os dois mosaicos têm a mesma altura.

1. Selecione **Mais opções (...)** para o mosaico Média de COGS > **Editar detalhes**. 

    :::image type="content" source="media/service-get-started/power-bi-tile-edit-details.png" alt-text="Captura de ecrã a mostrar o menu Mais opções de um mosaico.":::

1. Na caixa **Título**, escreva *Custo Médio de Bens Vendidos* > **Aplicar**.

    :::image type="content" source="media/service-get-started/power-bi-tile-details-dialog.png" alt-text="Captura de ecrã da caixa de diálogo Editar detalhes.":::

1. Reorganize os outros elementos visuais de forma a encaixarem.

    Assim está melhor.

    :::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="Captura de ecrã a mostrar o dashboard reorganizado.":::


## <a name="clean-up-resources"></a>Limpar recursos
Agora que concluiu o tutorial, pode eliminar o conjunto de dados, o relatório e o dashboard. 

1. Selecione **A minha área de trabalho** na barra de cabeçalho preta do **Power BI**.
2. Selecione **Mais opções (...)** junto ao conjunto de dados de Exemplo Financeiro > **Eliminar**.

    :::image type="content" source="media/service-get-started/power-bi-service-delete-dataset.png" alt-text="Captura de ecrã a mostrar o conjunto de dados a ser eliminado.":::

    Verá um aviso a indicar que **Todos os mosaicos de dashboard e relatórios que contêm dados deste conjunto de dados também serão eliminados**.

4. Selecione **Eliminar**.

## <a name="next-steps"></a>Próximos passos

Explore as coleções de conteúdos do Microsoft Learn para o Power BI:

- [Learn Power BI](https://docs.microsoft.com/learn/powerplatform/power-bi?WT.mc_id=powerbi_landingpage-docs-link) (Aprender a utilizar o Power BI)
- [Become a Power BI data analyst](https://docs.microsoft.com/users/microsoftpowerplatform-5978/collections/djwu3eywpk4nm) (Tornar-se um analista de dados do Power BI)
