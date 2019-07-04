---
title: 'Exemplo de Recursos Humanos: veja uma apresentação'
description: 'Exemplo de Recursos Humanos do Power BI: veja uma apresentação'
author: maggiesMSFT
manager: kfile
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/20/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 762a28d2340a691316b1aaf26b7ce62d45cc7496
ms.sourcegitcommit: 8dee40f07d284ec84a8afa0100359f146e1dd88b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67418748"
---
# <a name="human-resources-sample-for-power-bi-take-a-tour"></a>Exemplo de Recursos Humanos do Power BI: veja uma apresentação

O pacote de conteúdos de exemplo de Recursos Humanos contém um dashboard, um relatório e um conjunto de dados para um departamento de recursos humanos. Neste exemplo, o departamento de recursos humanos tem o mesmo modelo de relatório em diferentes empresas, mesmo quando existem diferenças no setor ou na dimensão. Este exemplo aborda novas contratações, funcionários ativos e funcionários que saíram. Tenta identificar as tendências na estratégia de contratação. Os nossos principais objetivos devem compreender:

* Quem contratamos
* Preconceitos na nossa estratégia de contratação
* Tendências nas separações voluntárias

![Dashboard do exemplo de Recursos Humanos](media/sample-human-resources/hr1.png)

Este exemplo faz parte de uma série que mostra como pode utilizar o Power BI com dados, relatórios e dashboards orientados para negócios. Foi criado com dados reais da [obviEnce](http://www.obvience.com/), que foram mantidos anónimos. Os dados estão disponíveis em vários formatos: pacote/aplicação de conteúdos, ficheiro .pbix do Power BI Desktop ou livro do Excel. Veja [Exemplos do Power BI](sample-datasets.md). 

Este tutorial utiliza o serviço Power BI e o pacote de conteúdos de exemplo de Recursos Humanos. Uma vez que as experiências do relatório são muito semelhantes, também pode acompanhar com o Power BI Desktop e o ficheiro .pbix de exemplo. 

## <a name="prerequisites"></a>Pré-requisitos

Para poder utilizar o exemplo, primeiro tem de transferi-lo como um [pacote de conteúdos](#get-the-content-pack-for-this-sample), um [ficheiro .pbix](#get-the-pbix-file-for-this-sample) ou um [livro do Excel](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Obter o pacote de conteúdos para este exemplo

1. Abra o serviço Power BI (app.powerbi.com), inicie sessão e abra a área de trabalho onde quer guardar o exemplo.

2. No canto inferior esquerdo, selecione **Obter Dados**.
   
   ![Selecionar Obter Dados](media/sample-datasets/power-bi-get-data.png)
3. Na página **Obter Dados** apresentada, selecione **Exemplos**.
   
4. Selecione **Exemplo de Recursos Humanos** e, em seguida, escolha **Ligar**.  
   
   ![Ligar ao exemplo](media/sample-human-resources/pbi_hr_sample_connect.png)

5. O Power BI importa o pacote de conteúdos e adiciona um novo dashboard, um relatório e um conjunto de dados à área de trabalho atual.
   
   ![Entrada do Exemplo de Recursos Humanos](media/sample-human-resources/hr-sample-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Obter o ficheiro .pbix para este exemplo

Em alternativa, pode transferir o exemplo de Recursos Humanos como um [ficheiro .pbix](http://download.microsoft.com/download/6/9/5/69503155-05A5-483E-829A-F7B5F3DD5D27/Human%20Resources%20Sample%20PBIX.pbix), concebido para utilização com o Power BI Desktop.

### <a name="get-the-excel-workbook-for-this-sample"></a>Obter o livro do Excel para este exemplo

Se quiser ver a origem de dados deste exemplo, também está disponível como um [livro do Excel](http://go.microsoft.com/fwlink/?LinkId=529780). O livro contém as folhas do Power View que pode ver e modificar. Para ver os dados não processados, ative os suplementos de Análise de Dados e, em seguida, selecione **Power Pivot > Gerir**. Para ativar os suplementos Power View e Power Pivot, veja [Observe os exemplos de Excel a partir do interior do próprio Excel](sample-datasets.md#optional-take-a-look-at-the-excel-samples-from-inside-excel-itself) para obter detalhes.

## <a name="new-hires"></a>Novas contratações
Primeiro, vamos explorar as novas contratações.

1. Na área de trabalho, selecione o separador **Dashboards** e abra o dashboard **Exemplo de Recursos Humanos**.
2. No dashboard, selecione o mosaico **Número de Novas Contratações, Novas Contratações no Mesmo Período do Ano Passado, Alteração da % Anual de Funcionários Ativos Por Mês**.  

   ![Mosaico Número de Novas Contratações](media/sample-human-resources/hr2.png)  

   O relatório Exemplo de Recursos Humanos é aberto na página **Novas Contratações**.  

   ![Página Novas Contratações](media/sample-human-resources/hr3.png)

3. Veja estes itens de interesse:

    * O gráfico de combinação **Número de Novas Contratações, Novas Contratações no Mesmo Período do Ano Passado, Alteração da % Anual de Funcionários Ativos por Mês** mostra que contratámos mais pessoas mensalmente neste ano em comparação com o ano passado. Um número significativamente superior de pessoas em alguns meses.
    * No gráfico de combinação **Número de Novas Contratações e Número de Funcionários Ativos por Região e Etnia**, observe que estamos a contratar menos pessoas na região **Leste**.
    * O gráfico de cascata **Var. de YoY de Novas Contratações por Grupo Etário** mostra que estamos a contratar principalmente pessoas mais jovens. Esta tendência pode dever-se, sobretudo, ao facto de os trabalhos serem em part-time.
    * O gráfico circular **Número de Novas Contratações por Género** mostra uma divisão aproximadamente uniforme.

    Pode encontrar mais informações? Por exemplo, uma região onde a divisão de género não é uniforme. 

4. Selecione diferentes faixas etárias e géneros nos gráficos para explorar as relações entre idade, género, região e grupo étnico.

5. Selecione **Exemplo de Recursos Humanos** na barra de navegação superior para regressar ao dashboard.

   ![Voltar ao dashboard](media/sample-human-resources/power-bi-breadcrumbs.png)

## <a name="compare-currently-active-and-former-employees"></a>Comparar os funcionários atualmente ativos e os funcionários antigos
Vamos explorar os dados de funcionários atualmente ativos e de funcionários que já não trabalham na empresa.

1. No dashboard, selecione o mosaico **Número de Funcionários Ativos por Grupo Etário**.

   ![Mosaico Número de Funcionários Ativos por Grupo Etário](media/sample-human-resources/pbi_hr_sample_activepie.png)

   O relatório de Exemplo de Recursos Humanos é aberto na página **Funcionários ativos vs. Separações**.  

   ![Página Funcionários Ativos vs. Separações](media/sample-human-resources/hr5.png)

 2. Veja estes itens de interesse:

    * Os dois gráficos de combinação no lado esquerdo mostram as alterações, ano após ano, dos funcionários ativos e das separações de funcionários. Temos mais funcionários ativos este ano devido à contratação rápida, mas também mais separações do que no ano passado.
    * Em agosto, tivemos mais separações em comparação com outros meses. Selecione as diferentes faixas etárias, géneros ou regiões para ver se consegue encontrar quaisquer exceções.
    * Ao examinar os gráficos circulares, observamos uma divisão bastante uniforme dos nossos funcionários ativos por género e grupo etário. Selecione diferentes grupos etários para ver como a divisão de géneros difere por idade. Temos uma divisão uniforme por género em cada faixa etária?

## <a name="reasons-for-separation"></a>Motivos de separação
Veja novamente o relatório no modo de Vista de Edição. Pode alterar os gráficos circulares para mostrar dados de separações de funcionários em vez de dados de funcionários ativos.

1. Selecione **Editar relatório** no canto superior esquerdo.

2. Selecione o gráfico circular **Número de Funcionários Ativos por Grupo Etário**.

3. Em **Campos**, selecione **Funcionários** para expandir a tabela **Funcionários**. Desmarque **Número de Funcionários Ativos** para remover esse campo.

4. Selecione **Número de Separações** na tabela **Funcionários** para adicionar à caixa **Valores** no painel **Campo**.

5. Na tela do relatório, selecione a barra **Voluntário** no gráfico de barras **Número de Separações por Motivo de Separação**. 

   Esta barra realça os funcionários que deixaram a empresa voluntariamente nos outros elementos visuais no relatório.

6. Selecione o grupo 50+ do gráfico circular **Número de Separações por Grupo Etário**.

7. Examine o gráfico de linhas no canto inferior direito. Este gráfico é filtrado para mostrar separações voluntárias.  

   ![Separações de funcionários com mais de 50 anos](media/sample-human-resources/pbi_hr_sample_sepsover50.png)

   Observe a tendência no grupo etário com + de 50 anos. No final do ano, mais funcionários com mais de 50 anos deixaram a empresa voluntariamente. Esta tendência é uma área a investigar melhor com mais dados.

8. Também pode seguir os mesmos passos para o gráfico circular **Número de Funcionários Ativos por Género** ao alterá-lo para Separações em vez de Funcionários Ativos. Examine os dados de separação voluntária por género para ver se encontra quaisquer outras informações.

9. Selecione **Exemplo de Recursos Humanos** na barra de navegação superior para regressar ao dashboard. Pode optar por guardar as alterações realizadas no relatório.

## <a name="bad-hires"></a>Contratações incorretas
A última área a explorar são as más contratações. As más contratações são definidas como funcionários que não duraram mais de 60 dias. Estamos a contratar rapidamente, mas estamos a contratar bons candidatos?

1. Selecione o mosaico do dashboard **Contratações Incorretas como % de Funcionários Ativos por Grupo Etário**. O relatório abre o separador três, **Contratações Incorretas**.

   ![Mosaico Contratações Incorretas como % de Funcionários Ativos por Grupo Etário](media/sample-human-resources/hr7.png)  
2. Selecione **Noroeste** na segmentação de dados **Região** à esquerda e selecione **Masculino** no gráfico de anel **Número de Contratações Incorretas por Género**. Examine outros gráficos na página **Contratações Incorretas**. Note que existem mais contratações incorretas de homens do que mulheres, assim como muitas contratações incorretas do Grupo A.

   ![Contratações incorretas no Noroeste](media/sample-human-resources/pbi_hr_sample_badhirespage.png)  

3. Se observar o gráfico de anel **Número de Contratações Incorretas por Género** e selecionar regiões diferentes na segmentação de dados **Região**, vai reparar que a região Leste é a única região com mais contratações incorretas de mulheres do que de homens.  

4. Selecione o nome do dashboard na barra de navegação superior para voltar ao dashboard.

## <a name="ask-a-question-in-the-dashboard-qa-box"></a>Faça uma pergunta na caixa de Perguntas e Respostas do dashboard
Na [caixa Perguntas e Respostas](power-bi-tutorial-q-and-a.md) no dashboard, pode fazer uma pergunta sobre os seus dados com uma linguagem natural. O P e R reconhece as palavras que escreve e descobre onde, no seu conjunto de dados, a resposta será encontrada.

1. Selecione a caixa de Perguntas e Respostas. Observe que, mesmo antes de começar a escrever, as Perguntas e Respostas apresentam sugestões para o ajudar a formular a sua pergunta.

   ![Sugestões da caixa Perguntas e Respostas](media/sample-human-resources/pbi_hr_sample_qabox.png)

2. Pode escolher uma das sugestões ou escrever: *mostrar grupo etário, género e contratações incorretas no mesmo período do ano passado com a região leste*.  

   ![Respostas da caixa Perguntas e Respostas](media/sample-human-resources/pbi_hr_sample_qa_answer.png)

   Veja que a maioria das más contratações de mulheres estão abaixo de 30 anos.

## <a name="next-steps-connect-to-your-data"></a>Próximos passos: Ligar aos seus dados
Aqui pode explorar à vontade, pois pode optar por não guardar as alterações. No entanto, se as guardar, pode sempre aceder a **Obter Dados** para obter uma nova cópia deste exemplo.

Esperamos que este tour tenha mostrado como os dashboards, o P e R e os relatórios do Power BI podem apresentar informações sobre os dados de recursos humanos. Agora, é a sua vez: ligue-se aos seus próprios dados. Com o Power BI, pode ligar-se a uma grande variedade de origens de dados. Para saber mais, veja [Introdução ao serviço Power BI](service-get-started.md).
