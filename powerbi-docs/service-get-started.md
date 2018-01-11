---
title: "Introdução ao serviço do Power BI"
description: "Introdução ao serviço do Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: B2vd4MQrz4M
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/31/2017
ms.author: mihart
ms.openlocfilehash: 6714283ea4590ac9c2f3728121e05d03d4aa646e
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="get-started-with-power-bi-service"></a>Introdução ao serviço do Power BI
Este tutorial ajuda-o a começar a utilizar o ***serviço Power BI***. Para saber como o serviço Power BI se encaixa nas restantes ofertas do Power BI, recomendamos vivamente que comece por ler [O que é o Power BI?](guided-learning/gettingstarted.yml#step-1).

![](media/service-get-started/power-bi-components.png)

O serviço Power BI tem uma versão gratuita e uma versão Pro. Seja qual for a versão que utiliza, abra um browser e escreva www.powerbi.com para começar. Se já se tiver inscrito, selecione a ligação **Iniciar sessão** que irá ver no canto superior direito. Se ainda não se inscreveu no serviço Power BI, selecione a ligação **Inscreva-se gratuitamente**.

![](media/service-get-started/power-bi-sign-up.png)

Se estiver à procura de ajuda para o Power BI Desktop, consulte [Introdução ao Desktop](desktop-getting-started.md). Se procura ajuda no Power BI Mobile, consulte [Aplicações do Power BI para dispositivos móveis](mobile-apps-for-mobile-devices.md).

> [!TIP]
> Prefere um curso gratuito de formação autónoma? [Inscreva-se no nosso curso Analyzing and Visualizing Data (Analisar e Visualizar Dados) no EdX](http://aka.ms/edxpbi).

Consulte a nossa [lista de reprodução no YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP). Um bom vídeo de partida é a Introdução ao serviço Power BI:
> 
> <iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>
> 
> 
> 

O Microsoft Power BI ajuda-lhe a manter-se atualizado em relação às informações importantes para si.  Com o serviço Power BI, os ***dashboards*** ajudam-no a controlar com um clique o ritmo da sua empresa.  Os seus dashboards mostram ***mosaicos*** nos quais pode clicar para abrir ***relatórios*** para explorar mais detalhadamente.  Ligue-se a vários ***conjuntos de dados*** para juntar todos os seus dados relevantes num único local. Precisa de ajuda para compreender os blocos modulares que compõem o Power BI?  Veja [Power BI – Conceitos básicos](service-basic-concepts.md).

Se tem dados importantes em ficheiros do Excel ou CSV, é possível criar um dashboard do Power BI para manter-se informado em qualquer lugar e partilhar informações com outras pessoas.  Tem uma subscrição de uma aplicação SaaS como o Salesforce?  Comece por se [ligar ao Salesforce](service-connect-to-salesforce.md) para criar automaticamente um dashboard a partir desses dados ou [consulte todas as outras aplicações SaaS](service-get-data.md) às quais se pode ligar. Se fizer parte de uma organização, veja se há [aplicações](service-create-distribute-apps.md) já publicadas para si.

Leia sobre todas as outras formas de [obter dados para o Power BI](service-get-data.md).

## <a name="step-1-get-data"></a>Passo 1: obter dados
Veja um exemplo de como obter dados de um ficheiro CSV. Deseja acompanhar este tutorial? [Transfira este ficheiro CSV de exemplo](http://go.microsoft.com/fwlink/?LinkID=521962).

1. [Inicie sessão no Power BI](http://www.powerbi.com/). Não tem uma conta? Não se preocupe. Pode inscrever-se gratuitamente.
2. O Power BI é aberto no seu browser. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-get-started/getdata3.png)
3. Selecione **Ficheiros**. 
   
   ![](media/service-get-started/gs1.png)
4. Selecione **Ficheiro Local**, navegue para o ficheiro no seu computador e selecione **Abrir**.
   
   ![](media/service-get-started/gs2.png)
5. Neste tutorial, vamos selecionar **Importar** para adicionar o ficheiro Excel como um conjunto de dados que podemos utilizar para criar relatórios e dashboards.  
   
   > [!NOTE]
   > Se selecionar **Carregar**, todo o livro do Excel será carregado para o Power BI, onde poderá abrir e editar o mesmo no Excel online.
   > 
   > 
   
   ![](media/service-get-started/power-bi-import.png)
6. Quando o seu conjunto de dados, estiver pronto, selecione **Ver conjunto de dados** para o abrir no editor de relatórios. ![](media/service-get-started/power-bi-gs.png).
   
   > [!TIP]
   > Uma excelente forma de se familiarizar com o editor de relatórios é [fazer uma visita](service-the-report-editor-take-a-tour.md)
   > 
   > 

## <a name="step-2-start-exploring-your-dataset"></a>Passo 2: começar a explorar o conjunto de dados
Agora que se ligou aos dados, explore-os para encontrar novas percepções.  Quando encontrar algo que deseja monitorizar, pode criar um dashboards para manter-se atualizado em relação às alterações.

1. Selecione a imagem do conjunto de dados no dashboard para explorar os dados aos quais se ligou ou, no cabeçalho **Conjuntos de dados**, selecione o nome do conjunto de dados para o abrir. Esta ação abre o conjunto de dados como um relatório em branco.
   
   ![](media/service-get-started/power-bi-report-editor.png)
   
   > [!NOTE]
> Outra forma de explorar os seus dados são as **Informações Rápidas**.  Para mais informações, consulte [Introdução às Informações Rápidas](service-insights.md)
   > 
   > 
2. Na lista **Campos** no lado direito da página, selecione os campos para criar uma visualização.  Selecione a caixa de verificação de **Gross Sales** (Vendas Brutas) e  **Date** (Data).
   
   ![](media/service-get-started/fields.png)
3. O Power BI analisa os dados e cria um elemento visual.  Se tiver selecionado **Date** (Data) primeiro, verá uma tabela.  Se tiver selecionado **Gross Sales** (Vendas Brutas) primeiro, verá um gráfico. Mude para uma forma diferente de apresentação dos dados. Tente mudar para um gráfico de linhas selecionando a opção correspondente.
   
   ![](media/service-get-started/gettingstart5new.png)
4. Quando desejar ter uma determinada visualização no seu dashboard, passe o cursor sobre a visualização e selecione o ícone **Afixar**.  Quando afixar esta visualização, esta será armazenada no dashboard para que possa acompanhar rapidamente o valor mais recente.
   
   ![](media/service-get-started/pinnew.png)
5. Como este é um novo relatório, é necessário guarda-lo antes de poder afixar uma visualização deste no dashboard. Dê um nome ao seu relatório (como *Vendas ao Longo do Tempo*) e selecione **Guardar e Continuar**. 
   
   ![](media/service-get-started/pbi_getstartsaveb4pinnew.png)
   
   O novo relatório é apresentado no painel de navegação no cabeçalho **Relatórios**.
6. Afixe o mosaico num dashboard existente ou num novo dashboard. 
   
   ![](media/service-get-started/power-bi-pin.png)
   
   * **Dashboard existente**: selecione o nome do dashboard no menu pendente.
   * **Novo dashboard**: escreva o nome do novo dashboard.
7. Selecione **Afixar**.
   
   Uma mensagem de Êxito (perto do canto superior direito) informa que a visualização foi adicionada, como um mosaico, ao dashboard.
   
   ![](media/service-get-started/power-bi-pin-success.png)
8. Selecione **Ir para o dashboard** para ver o seu novo dashboard com o mosaico afixado. O gráfico de linhas está afixado, como mosaico, ao dashboard. Melhore ainda mais o aspeto do seu dashboard ao [mudar o nome, redimensionar, ligar e reposicionar mosaicos](service-dashboard-edit-tile.md).
   
   ![](media/service-get-started/power-bi-new-dashboard.png)
   
   Selecione o novo mosaico no seu dashboard para regressar ao relatório a qualquer altura.

## <a name="step-3-continue-exploring-with-qa-natural-language-querying"></a>Passo 3: continuar a explorar com as perguntas e respostas (consulta em linguagem natural)
1. Para explorar os dados rapidamente, tente fazer uma pergunta na caixa de perguntas e respostas. A caixa de perguntas das perguntas e respostas encontra-se na parte superior do dashboard. Por exemplo, experimente escrever "**what segment had the most revenue**" (que segmento teve mais receita).
   
   ![](media/service-get-started/powerbi-qna.png)
2. Clique no ícone de afixar ![](media/service-get-started/pbi_pinicon.png) para mostrar esta visualização no dashboard também.
3. Afixe a visualização no dashboard de Exemplo Financeiro.
   
    ![](media/service-get-started/power-bi-pin2.png)
4. Selecione a seta para trás para **Sair das Perguntas e Respostas** ![](media/service-get-started/pbi_qabackarrow.png) e regresse ao seu dashboard, onde verá o novo mosaico.

## <a name="next-steps"></a>Próximos passos
Pronto para experimentar mais?  Aqui estão alguns modos excelentes de explorar mais do Power BI.

* [Ligue-se a outro conjunto de dados](service-get-data.md).
* [Partilhe o seu dashboard](service-share-dashboards.md) com colegas.
* Consulte as [sugestões para estruturar dashboards](service-dashboards-design-tips.md).
* Ver os dashboards com uma [aplicação do Power BI num dispositivo móvel](mobile-apps-for-mobile-devices.md)

Ainda não está preparado para avançar diretamente? Comece por estes tópicos criados para ajudá-lo a familiarizar-se com o Power BI.

* [Saiba como os relatórios, conjuntos de dados, dashboards e mosaicos se conjugam](service-basic-concepts.md)
* [Vídeos do Power BI](videos.md)
* [Veja os exemplos que temos disponíveis para utilizar](sample-datasets.md)

### <a name="stay-in-touch-with-power-bi"></a>Mantenha-se em contacto com o Power BI
* Siga o [@MSPowerBI no Twitter](https://twitter.com/mspowerbi)
* Subscreva o nosso [canal de vídeos no YouTube](https://www.youtube.com/channel/UCy--PYvwBwAeuYaR8JLmrfg)
* Veja os nossos [Webinars de introdução ao Power BI](webinars.md) a pedido
* Não sabe onde ir para obter ajuda? Consulte a nossa página [10 sugestões para obter ajuda](service-tips-for-finding-help.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

