---
title: Machine Learning automatizada no Power BI (Pré-visualização)
description: Saiba como utilizar automatizada Machine Learning (AutoML) no Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/02/2019
ms.author: davidi
LocalizationGroup: conceptual
ms.openlocfilehash: 894e92687a6283ce71b253bd4dc635aca0c4673f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61236829"
---
# <a name="automated-machine-learning-in-power-bi-preview"></a>Machine Learning automatizada no Power BI (Pré-visualização)

Automatizada aprendizagem automática (AutoML) para fluxos de dados permite que os analistas de negócios preparar, validar e invocar os modelos de Machine Learning diretamente no Power BI. Ele inclui uma experiência simple para criar um novo modelo de ML em que os analistas podem utilizar os seus fluxos de dados para especificar os dados de entrada para o modelo de formação. O serviço extrai os recursos mais relevantes, seleciona automaticamente um algoritmo apropriado e adaptável e valida o modelo de ML. Depois de um modelo é preparado, o Power BI gera automaticamente um relatório que inclui os resultados de validação que explica o desempenho e resultados para os analistas. O modelo, em seguida, pode ser invocado em quaisquer dados novos ou atualizados no fluxo de dados.

![Ecrã do Machine learning](media/service-machine-learning-automated/automated-machine-learning-power-bi-01.png)

Aprendizagem automatizada está disponível para fluxos de dados que estão alojados no Power BI Premium e Embedded capacidades apenas. Nesta pré-visualização, AutoML permite-lhe preparar modelos de aprendizagem automática para modelos de predição binário, classificação e regressão.

## <a name="working-with-automl"></a>Trabalhar com AutoML

[Power BI fluxos de dados](service-dataflows-overview.md) oferecem a preparação de dados personalizada para grandes volumes de dados. AutoML permite-lhe tirar partido do seu esforço de preparação de dados para a criação de modelos de aprendizagem automática, diretamente a partir do Power BI.

AutoML no Power BI permite que os analistas de dados usar fluxos de dados para criar modelos de machine learning com uma experiência simplificada, com apenas as competências do Power BI. A maioria da ciência de dados por trás da criação de modelos de ML é automatizado pelo Power BI, com guardrails para garantir que o modelo produzido tem boa qualidade e visibilidade para lhe fornecer com total conhecimento sobre o processo usado para criar o seu modelo de ML.

AutoML suporta a criação de **predição binário**, **classificação**, e **regressão** modelos para fluxos de dados. Estes são tipos de modelos de supervisionadas do machine learning, que significa que aprenderam com os resultados conhecidos das observações anteriores para prever os resultados das outras observações. O conjunto de dados de entrada para um modelo de AutoML de formação é um conjunto de registos que estão **rotulado** com os resultados conhecidos.

AutoML no Power BI integra-se [automatizada ML](https://docs.microsoft.com/azure/machine-learning/service/concept-automated-ml) partir do [serviço Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml) para criar os seus modelos de ML. No entanto, não precisa de uma subscrição do Azure para utilizar AutoML no Power BI. O processo de treinamento e os modelos de ML de alojamento é gerido completamente pelo serviço Power BI.

Depois de um modelo de ML é preparado, AutoML gera automaticamente um relatório do Power BI que explica o provável desempenho do seu modelo de ML. AutoML enfatiza explainability, por destacar os influenciadores principais entre suas entradas que influenciam as previsões devolvidas pelo seu modelo. O relatório também inclui as principais métricas para o modelo, dependendo do tipo de modelo de ML.

Outras páginas do relatório gerado mostram o resumo de estatístico do modelo e os detalhes de treinamento. O resumo de estatístico é de interesse para os usuários que gostariam de ver as medidas de ciência de dados padrão de desempenho para o modelo. Os detalhes de treinamento resumem todas as iterações que foram executadas para criar o seu modelo, com os parâmetros de modelagem associados. Ele também descreve como cada entrada foi utilizada para criar o modelo de ML.

Em seguida, pode aplicar o modelo de ML aos seus dados para a classificação. Quando o fluxo de dados é atualizado, as previsões do seu modelo de ML são automaticamente aplicadas aos seus dados. O Power BI também inclui uma explicação individualizada para cada classificação de predição específico que produz o modelo de ML.

## <a name="creating-a-machine-learning-model"></a>Criar um modelo de machine learning

Esta secção descreve como criar um modelo de aprendizagem AutoML. 

### <a name="data-prep-for-creating-an-ml-model"></a>Preparação de dados para criar um modelo de ML

Para criar um modelo de aprendizagem automática no Power BI, tem primeiro de criar um fluxo de dados para os dados com as informações de histórico de resultado, o que são utilizadas para dar formação sobre o modelo de ML. Para obter detalhes sobre como configurar o seu fluxo de dados, consulte [de preparação de dados de Self-serviços no Power BI](service-dataflows-overview.md).

Na versão atual, o Power BI utiliza os dados a partir de uma única entidade para preparar o modelo de ML. Portanto, se os dados históricos consiste em várias entidades, tem manualmente de associar os dados para uma entidade de fluxo de dados única. Também deve adicionar colunas calculadas para quaisquer métricas de negócio que podem ser indicadores fortes para o resultado que está a tentar prever.

AutoML tem requisitos de dados específicos para um modelo de machine learning de formação. Estes requisitos são descritos nas secções abaixo, com base nos tipos de respetivo modelo.

### <a name="configuring-the-ml-model-inputs"></a>Configurar as entradas de modelo de ML

Para criar um modelo de AutoML, selecione o ícone de ML no **ações** coluna da entidade de fluxo de dados com os dados históricos e selecione **adicionar um modelo de aprendizagem automática**.

![Adicionar um modelo de Machine learning](media/service-machine-learning-automated/automated-machine-learning-power-bi-02.png)

É iniciada uma experiência simplificada, que consiste de um assistente que orienta-o ao longo do processo de criação do modelo de ML. O assistente inclui os seguintes passos simples.

1. Selecione a entidade com os dados históricos de resultado e o campo para o qual deseja uma predição
2. Escolher um tipo de modelo com base no tipo de predição que gostariam de ver
3. Selecione as entradas que pretende que o modelo utilize como sinais preditivas
4. Nomeie o seu modelo e guardar a configuração

O campo de resultado históricos identifica o atributo de etiqueta para preparar o modelo de ML, mostrado na imagem seguinte.

![Selecionar dados históricos de resultado](media/service-machine-learning-automated/automated-machine-learning-power-bi-03.png)

Quando especificar o campo de resultado históricos, AutoML analisa os dados de etiqueta para identificar os tipos de modelos de ML que podem ser treinados para que os dados e sugere o tipo de modelo de ML mais provável que pode ser treinado. 

> [!NOTE]
> Alguns tipos de modelo, poderão não ser suportados para os dados que selecionou.

AutoML também analisa todos os campos da entidade selecionada para sugerir as entradas que podem ser utilizadas para preparar o modelo de ML. Este processo é aproximado e baseia-se na análise estatística, pelo que deve rever as entradas utilizadas. Quaisquer entradas que dependem do campo de resultado históricos (ou o campo de etiqueta) não devem ser usadas para preparar o modelo de ML, uma vez que elas afetam o desempenho dele.

![Personalizar campos de entrada](media/service-machine-learning-automated/automated-machine-learning-power-bi-04.png)

No passo final, pode nomear o modelo e salvar suas configurações.

Nesta fase, são-lhe pedido para atualizar o fluxo de dados, que inicia o processo de treinamento para o modelo de ML.

### <a name="ml-model-training"></a>Preparação de modelos de ML

Treinamento de modelos de AutoML é uma parte da atualização de fluxo de dados. AutoML primeiro prepara os dados de treinamento.

AutoML divide os dados históricos de que fornecer um treinamento e teste de conjuntos de dados. O conjunto de dados de teste é um conjunto de exclusão que serve para validar o desempenho do modelo depois de treinamento. Estes são realizados como **preparação e teste** entidades no fluxo de dados. AutoML usa a validação cruzada para a validação de modelo.

Em seguida, cada campo de entrada é analisado e imputation é aplicada, que substitui os valores em falta com valores serão substituídos. Algumas estratégias de imputation diferentes são usadas pelo AutoML. Em seguida, qualquer amostragem necessária e a normalização são aplicadas aos seus dados.

AutoML aplica-se várias transformações são cada campo de entrada selecionado com base no respetivo tipo de dados e as respetivas propriedades estatísticas. AutoML usa essas transformações para extrair recursos para utilização no seu modelo de ML de treinamento.

O processo de treinamento para modelos de AutoML consiste em até 50 iterações com algoritmos de modelagem de diferentes e definições de hiper-parâmetros para localizar o modelo com o melhor desempenho. O desempenho de cada um desses modelos é avaliado pela validação com o conjunto de dados de teste de exclusão. Durante este passo de treinamento, AutoML cria vários pipelines de formação e validação dessas iterações. O processo de avaliar o desempenho dos modelos de pode demorar tempo, em qualquer lugar de alguns minutos a algumas horas, dependendo do tamanho do seu conjunto de dados e os recursos de capacidade dedicada disponíveis.

Em alguns casos, o modelo final gerado utilizar ensemble de aprendizado, onde os vários modelos são utilizados para proporcionar melhor desempenho de previsão.

### <a name="automl-model-explainability"></a>AutoML explainability de modelo

Depois do modelo foi treinado, AutoML analisa a relação entre os recursos de entrada e saída de modelo. Ele avalia a magnitude e a direção de alteração para o resultado de modelo para o conjunto de dados de teste de exclusão para cada funcionalidade de entrada. Isso é conhecido como o *importância da funcionalidade*.

![Importância de funcionalidade](media/service-machine-learning-automated/automated-machine-learning-power-bi-05.png)

### <a name="automl-model-report"></a>Relatório de modelo AutoML

AutoML gera um relatório do Power BI que resume o desempenho do modelo durante a validação, juntamente com a importância de recurso global. O relatório resume os resultados de aplicar o modelo de ML para os dados de teste de exclusão e comparar as previsões com os valores de resultado conhecidos.

Pode rever o relatório de modelo para compreender o desempenho dele. Também pode validar que os influenciadores principais do modelo de se alinhar com as informações de negócio sobre os resultados conhecidos.

Os gráficos e as medidas usadas para descrever o desempenho do modelo no relatório dependem do tipo de modelo. Estes gráficos de desempenho e as medidas são descritas nas seções a seguir.

Páginas adicionais do relatório podem descrever medidas estatísticas sobre o modelo de uma perspectiva de ciência de dados. Por exemplo, o **predição binário** relatório inclui um gráfico de ganho e a curva ROC para o modelo.

Os relatórios também incluem uma **detalhes de treinamento** página inclui uma descrição de como o modelo foi treinado e inclui um gráfico que descreve o desempenho do modelo ao longo de cada uma das iterações é executada.

![Detalhes de treino](media/service-machine-learning-automated/automated-machine-learning-power-bi-06.png)

Outra seção nesta página descreve como o método imputation utilizado para preencher valores em falta para os campos de entrada, bem como a forma como cada campo de entrada foi transformado para extrair as funcionalidades utilizadas no modelo. Ele também inclui os parâmetros utilizados pelo modelo final.

![Obter mais informações para o modelo](media/service-machine-learning-automated/automated-machine-learning-power-bi-07.png)

Se o modelo produzido utiliza a aprendizagem de ensemble, em seguida, o **detalhes de treinamento** página também inclui uma seção que descreva o peso de cada modelo que constituem o ensemble, bem como seus parâmetros.

![Ponderação no ensemble](media/service-machine-learning-automated/automated-machine-learning-power-bi-08.png)

## <a name="applying-the-automl-model"></a>Aplicar o modelo de AutoML

Se estiver satisfeito com o desempenho do modelo de ML criado, pode aplicá-la aos dados novos ou atualizados quando o fluxo de dados é atualizado. Pode fazê-lo a partir do relatório de modelo, selecionando o **aplicar** botão no canto superior direito.

Para aplicar o modelo de ML, tem de especificar o nome da entidade a que devem ser aplicada e um prefixo para as colunas que serão adicionados a esta entidade para a saída do modelo. O prefixo de padrão para os nomes das colunas é o nome de modelo. O *aplicar* função pode incluir parâmetros adicionais específicos para o tipo de modelo.

Aplicar o modelo de ML cria uma nova entidade de fluxo de dados com o sufixo **enriquecida < nome_modelo >** . Por exemplo, se aplicar a _PurchaseIntent_ modelos para o _OnlineShoppers_ entidade, o resultado irá gerar o **OnlineShoppers enriquecida PurchaseIntent**.

Atualmente, não pode servir-se a entidade de saída para pré-visualizar os resultados de modelo de ML no editor do Power Query. As colunas de saída sempre mostram nulo como resultado. Para ver os resultados, o segundo resultado de entidade com o sufixo **enriquecida < nome_modelo > pré-visualização** é criado quando o modelo é aplicado.

Tem de atualizar o fluxo de dados, pré-visualizar os resultados no Editor de consultas.

![Editor de consultas](media/service-machine-learning-automated/automated-machine-learning-power-bi-09.png)

Quando aplica o modelo, AutoML sempre mantém sua previsões atualizado quando o fluxo de dados é atualizado.

AutoML também inclui uma explicação individualizada para cada linha que ele pontua na entidade de saída.

Para utilizar as informações e as previsões do modelo de ML no relatório do Power BI, pode ligar para a entidade de saída do Power BI Desktop usando o **fluxos de dados** conector.

## <a name="binary-prediction-models"></a>Modelos de predição de binários

Modelos de previsão binários, conhecidos mais formalmente como **modelos de classificação binária**, são utilizados para classificar um conjunto de dados em dois grupos. Eles são usados para prever eventos que podem ter um resultado de binário, como se irá converter uma oportunidade de vendas, se as alterações a uma conta, se uma nota fiscal será paga em tempo; Se uma transação é fraudulentas e assim por diante.

Uma vez que o resultado é binário, o Power BI espera a etiqueta de um modelo de predição de binário ser um valor booleano, com resultados conhecidos que está a ser o nome **true** ou **falso**. Por exemplo, num modelo de conversão de oportunidade de vendas, oportunidades de venda que tenham sido ganhou estão identificados como verdadeiras, aqueles que tenham sido perdidos estão identificados como falsas e oportunidades de venda abertas estão identificados como nulo.

O resultado de um modelo de previsão de binários é uma pontuação de probabilidade, que identifica a probabilidade de que o resultado correspondente ao valor de etiqueta a ser verdadeiro irá ser alcançado.

### <a name="training-a-binary-prediction-model"></a>Preparar um modelo de previsão de binários

Para criar um modelo de predição binário, a entidade de entrada que contém os seus dados de preparação tem de ter um campo booleano como o campo de resultado de histórico para identificar os últimos resultados conhecidos.

Pré-requisitos:

* Um campo Booleano tem de ser utilizado como o campo de resultado históricos
* É necessário para cada classe de resultados um mínimo de 50 linhas de dados históricos

Em geral, se os últimos resultados são identificados por campos de um tipo de dados diferentes, pode adicionar uma coluna calculada para transformar isso num valor booleano com o Power Query.

O processo de criação de um modelo de predição binário segue os mesmos passos como outros modelos de AutoML, descritos na secção **configurar as entradas de modelo de ML** acima.

### <a name="binary-prediction-model-report"></a>Relatório de modelo de predição binário

O modelo de predição binário produz, como resultado, uma probabilidade de que um registo irá atingir o resultado definido pelo valor da etiqueta Boolean como verdadeiro. O relatório inclui uma segmentação de dados para o limiar de probabilidade, o que influencia a forma como as pontuações acima e abaixo do limiar de probabilidade são interpretadas.

O relatório descreve o desempenho do modelo em termos de *positivos verdadeiros*, *falsos positivos*, *negativos True* e *falsos negativos*. VERDADEIRO valores positivos e negativos VERDADEIRO são os resultados previstos corretamente para as duas classes nos dados de resultado. Falsos positivos são os resultados que tinham a etiqueta booleana real do valor False, mas foram previstos como True. Por outro lado, falsos negativos são os resultados em que o valor de etiqueta booleano real era True, mas foram previstos como falso.

Medidas, como a precisão e lembre-se, descrevem o efeito do limiar de probabilidade sobre os resultados previstos. Pode utilizar a segmentação de dados do limiar de probabilidade para selecionar um limiar que ofereça um bom equilíbrio entre a precisão e lembre-se.

![Pré-visualização de precisão](media/service-machine-learning-automated/automated-machine-learning-power-bi-10.png)

O **relatório de precisão** página do relatório de modelo inclui o *quadro de ganhos cumulativos* gráfico e o ROC curva para o modelo. Estes são medidas estatísticas de desempenho do modelo. Os relatórios incluem descrições dos gráficos mostrados.

![Tela de relatório de precisão](media/service-machine-learning-automated/automated-machine-learning-power-bi-11.png)

### <a name="applying-a-binary-prediction-model"></a>Aplicar um modelo de predição de binários

Para aplicar um modelo de predição binário, tem de especificar a entidade com os dados aos quais pretende aplicar as previsões do modelo de ML. Outros parâmetros incluem o prefixo de nome de coluna de saída e o limiar de probabilidade para classificar o resultado previsto.

![Entradas de predição](media/service-machine-learning-automated/automated-machine-learning-power-bi-12.png)

Quando é aplicado um modelo de predição binário, ele adiciona três colunas de saída para a entidade de saída plena. Estes são os **PredictionScore**, **PredictionOutcome** e **PredictionExplanation**. Os nomes das colunas na entidade têm o prefixo especificado quando o modelo é aplicado.

O **PredictionOutcome** coluna contém a etiqueta de resultado prevista. Registos com a exceder o limiar de probabilidades são prever a probabilidade de alcançar o resultado e aqueles abaixo estão previstos como improvável que atinja o resultado.

O **PredictionExplanation** coluna contém uma explicação com a influência específica que os recursos de entrada tinham no **PredictionScore**. Esta é uma coleção de formatação JSON de pesos das funcionalidades de entrada para a predição.

## <a name="classification-models"></a>Modelos de classificação

Modelos de classificação são utilizados para classificar um conjunto de dados em múltiplos grupos ou classes.  Eles são usados para prever eventos que podem ter um de vários resultados possíveis, por exemplo, se um cliente é provável que tenha um muito alta, alta, média ou baixa de tempo de vida de valor; Se o risco para a predefinição é alto, moderado, baixo ou muito baixa; e assim por diante.

O resultado de um modelo de classificação é uma pontuação de probabilidade, que identifica a probabilidade de que um registo irá obter os critérios para uma determinada classe.

### <a name="training-a-classification-model"></a>Preparar um modelo de classificação

A entidade de entrada que contém os dados de treinamento para um modelo de classificação tem de ter uma cadeia ou um campo numérico, como o campo de resultado históricos, que identifica os últimos resultados conhecidos.

Pré-requisitos:

* É necessário para cada classe de resultados um mínimo de 50 linhas de dados históricos

O processo de criação de um modelo de classificação segue os mesmos passos como outros modelos de AutoML, descritos na secção **configurar as entradas de modelo de ML** acima.

### <a name="classification-model-report"></a>Relatório de modelo de classificação

A classificação de relatório do modelo é produzido ao aplicar o modelo de ML para a exclusão de teste de dados e comparando a classe prevista para um registo com a classe conhecida real.

O relatório de modelo inclui um gráfico que inclui a divisão dos registos corretamente e incorretamente classificadas para cada classe conhecido.

![Relatório de modelo](media/service-machine-learning-automated/automated-machine-learning-power-bi-13.png)

Um detalhamento de classe específicas ainda mais permite uma análise de como as previsões de uma classe conhecida são distribuídas. Isto inclui as outras classes em que registros de conhecidos classe têm probabilidades de ser classificado erroneamente.

![Relatório de análise](media/service-machine-learning-automated/automated-machine-learning-power-bi-14.png)

A explicação de modelo no relatório também inclui os principais indicadores para cada classe.

O relatório de modelo de classificação também inclui uma página de detalhes de treinamento semelhante para as páginas para outros tipos de modelo, conforme descrito na secção **relatório de modelo AutoML** no início deste artigo.

### <a name="applying-a-classification-model"></a>Aplicar um modelo de classificação

Para aplicar um modelo de ML de classificação, tem de especificar a entidade com os dados de entrada e o prefixo de nome de coluna de saída.

Quando é aplicado um modelo de classificação, ele adiciona que três colunas para a entidade de saída plena de saída. Estes são os **PredictionScore**, **PredictionClass** e **PredictionExplanation**. Os nomes das colunas na entidade têm o prefixo especificado quando o modelo é aplicado.

O **PredictionClass** coluna contém a classe provavelmente prevista para o registo. O **PredictionScore** coluna contém a lista das pontuações de probabilidade para o registo para cada classe possíveis.

O **PredictionExplanation** coluna contém uma explicação com a influência específica que os recursos de entrada tinham no **PredictionScore**. Esta é uma coleção de formatação JSON de pesos das funcionalidades de entrada para a predição.

## <a name="regression-models"></a>Modelos de regressão

Modelos de regressão são utilizados para prever um valor, como a receita probabilidade de ser alcançado com uma quantidade de vendas, o valor de duração de uma conta, a quantidade de uma nota fiscal da receber que é provável que a serem pagas, a data em que uma nota fiscal poderá ser pago , e assim por diante.

O resultado de um modelo de regressão é o valor previsto.

### <a name="training-a-regression-model"></a>Preparar um modelo de regressão

A entidade de entrada que contém os dados de treinamento para um modelo de regressão tem de ter um campo numérico como o campo de resultado históricos, que identifica os últimos valores de resultado conhecidos.

Pré-requisitos:

* É necessário para um modelo de regressão um mínimo de 100 linhas de dados históricos

O processo de criação de um modelo de regressão segue os mesmos passos como outros modelos de AutoML, descritos na secção **configurar as entradas de modelo de ML** acima.

### <a name="regression-model-report"></a>Relatório de modelo de regressão

Como os outros AutoML modelo relatórios, o relatório de regressão baseia-se nos resultados de aplicar o modelo para os dados de teste de exclusão.

O relatório de modelo inclui um gráfico que compara os valores previstos para o valor real. Neste gráfico, a distância da diagonal indica o erro na predição.

O gráfico de erro residuais mostra a distribuição da percentagem de erros média para valores diferentes no conjunto de dados de teste de exclusão. O eixo horizontal representa a média do valor real para o grupo, com o tamanho da bolha que mostra a frequência ou a contagem de valores nesse intervalo. O eixo vertical é o erro residual médio.

![Gráfico de erro residuais](media/service-machine-learning-automated/automated-machine-learning-power-bi-15.png)

O relatório de modelo de regressão também inclui uma página de detalhes de treinamento como os relatórios para outros tipos de modelo, conforme descrito na secção **relatório de modelo AutoML** acima.

### <a name="applying-a-regression-model"></a>Aplicar um modelo de regressão

Para aplicar um modelo de regressão ML, tem de especificar a entidade com os dados de entrada e o prefixo de nome de coluna de saída.

![Aplicar uma regressão](media/service-machine-learning-automated/automated-machine-learning-power-bi-16.png)

Quando é aplicado um modelo de regressão, ele adiciona duas colunas de saída para a entidade de saída plena. Estes são os **PredictionValue**, e **PredictionExplanation**. Os nomes das colunas na entidade têm o prefixo especificado quando o modelo é aplicado.

O **PredictionValue** coluna contém o valor previsto para o registo com base nos campos de entrada. O **PredictionExplanation** coluna contém uma explicação com a influência específica que os recursos de entrada tinham no **PredictionValue**. Esta é uma coleção de formatação JSON de pesos dos recursos de entrada.

## <a name="next-steps"></a>Próximos passos

Este artigo fornecida uma visão geral do Machine Learning automatizada para fluxos de dados no serviço Power BI. Os seguintes artigos também podem ser úteis.

* [Tutorial: Criar um modelo de Machine Learning no Power BI (pré-visualização)](service-tutorial-build-machine-learning-model.md)
* [Tutorial: Utilizar os Serviços Cognitivos no Power BI](service-tutorial-use-cognitive-services.md)
* [Tutorial: Invocar um modelo do Machine Learning Studio no Power BI (Pré-visualização)](service-tutorial-invoke-machine-learning-model.md)
* [Serviços Cognitivos no Power BI (Pré-visualização)](service-cognitive-services.md)
* [Integração do Azure Machine Learning no Power BI (Pré-visualização)](service-machine-learning-integration.md)

Para obter mais informações sobre fluxos de dados, leia estes artigos:
* [Criar e utilizar fluxos de dados no Power BI](service-dataflows-create-use.md)
* [Usando entidades calculadas no Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Utilizar fluxos de dados com origens de dados no local](service-dataflows-on-premises-gateways.md)
* [Recursos para desenvolvedores de fluxos de dados do Power BI](service-dataflows-developer-resources.md)
* [Fluxos de dados e integração do Azure Data Lake (Pré-visualização)](service-dataflows-azure-data-lake-integration.md)


