---
title: 'Tutorial: Criar um modelo de Machine Learning no Power BI (Pré-visualização)'
description: Neste tutorial, vai criar um modelo de Machine Learning no Power BI.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 03/29/2019
ms.author: davidi
LocalizationGroup: Connect to services
ms.openlocfilehash: 611d6f6c923e6cb68af94840c4266a0b6dee7651
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61407198"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>Tutorial: Criar um modelo de Machine Learning no Power BI (Pré-visualização)

Neste artigo de tutorial, será utilizada o **Machine Learning Automatizado** para criar e aplicar um modelo de predição binária no Power BI. O tutorial inclui orientações para a criação de um fluxo de dados do Power BI e a utilização das entidades definidas no fluxo de dados para preparar e validar um modelo de machine learning diretamente no Power BI. Em seguida, vamos utilizar esse modelo para classificação para gerar predições.

Em primeiro lugar, deverá criar um modelo de machine learning de Predição Binária para prever a intenção de compra dos compradores online com base num conjunto dos atributos de sessão online desses compradores. Para este exercício, é utilizado um conjunto de dados de machine learning de referência. Após a preparação de um modelo, o Power BI gerará automaticamente um relatório de validação que explica os resultados do modelo. Em seguida, pode rever o relatório de validação e aplicar o modelo aos seus dados para classificação.

Este tutorial consiste nos seguintes passos:

> [!div class="checklist"]
> * Criar um fluxo de dados com os dados de entrada
> * Criar e preparar um modelo de machine learning
> * Rever o relatório de validação do modelo
> * Aplicar o modelo a uma entidade de fluxo de dados
> * Utilizar a saída classificada do modelo num relatório do Power BI

## <a name="create-a-dataflow-with-the-input-data"></a>Criar um fluxo de dados com os dados de entrada

A primeira parte deste tutorial consiste em criar um fluxo de dados com os dados de entrada. Esse processo implica alguns passos, conforme indicado nas secções a seguir, e começa com a obtenção de dados.

### <a name="get-data"></a>Obter dados

O primeiro passo na criação de um fluxo de dados é ter as origens de dados preparadas. No nosso caso, vamos utilizar um conjunto de dados de machine learning de um conjunto de sessões online, algumas das quais culminaram numa compra. O conjunto de dados contém um conjunto de atributos sobre essas sessões, que utilizaremos para a preparação do nosso modelo.

Pode transferir o conjunto de dados a partir do site da UC Irvine.  Além disso, temos o conjunto disponível, para efeitos deste tutorial, na seguinte ligação: [online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv).

### <a name="create-the-entities"></a>Criar as entidades

Para criar as entidades no seu fluxo de dados, inicie sessão no serviço Power BI e navegue para uma área de trabalho na sua capacidade dedicada que tenha a pré-visualização de IA ativada.

Se ainda não tiver uma área de trabalho, poderá criar uma ao selecionar **Áreas de Trabalho** no menu de navegação esquerdo do serviço Power BI e, em seguida, **Criar área de trabalho da aplicação** na parte inferior do painel apresentado. Esta ação abre um painel no lado direito para introduzir os detalhes da área de trabalho. Introduza um nome de área de trabalho e selecione **Avançado**. Confirme se a área de trabalho utiliza uma Capacidade Dedicada com o botão de opção e se está atribuída a uma instância de capacidade dedicada que tenha a pré-visualização de IA ativada. Em seguida, selecione **Guardar**.

![Criar uma área de trabalho](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

Após a criação da área de trabalho, pode selecionar **Ignorar** na parte inferior direita do ecrã Boas-vindas, conforme mostrado na imagem seguinte.

![Ignorar se tiver uma área de trabalho](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

Selecione o separador **Fluxos de dados (pré-visualização)** . Selecione o botão **Criar** na parte superior direita da área de trabalho e, em seguida, **Fluxo de dados**.

![Criar o fluxo de dados](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

Selecione **Adicionar novas entidades**. Esta ação inicia um editor do **Power Query** no browser.

![Adicionar nova entidade](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

Selecione **Ficheiro de Texto/CSV** como uma origem de dados, conforme mostrado na imagem seguinte.

![Ficheiro de texto/CSV selecionado](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

Em **Ligar a uma origem de dados** apresentado em seguida, cole a seguinte ligação para *online_shoppers_intention.csv* na caixa **URL ou caminho do ficheiro** e selecione **Seguinte**.

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![Caminho do ficheiro](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

O Editor do Power Query mostra uma pré-visualização dos dados do ficheiro CSV. Selecione **Transformar Tabela** no friso de comandos e, em seguida, **Utilizar primeira linha como cabeçalhos** no menu apresentado. Esta ação adiciona o passo de consulta _Cabeçalhos promovidos_ à secção **Passos aplicados** no lado direito do ecrã. Pode mudar o nome da consulta para um nome mais amigável ao alterar o valor na caixa **Nome** no painel direito. Por exemplo, pode alterar o nome da consulta para _Visitante Online_.

![Alterar para um nome amigável](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

Alguns dos tipos de dados de atributo neste conjunto de dados são _numéricos_ ou _Booleanos_, embora possam ser interpretados como cadeias de carateres pelo **Power Query**. Selecione o ícone de tipo de atributo na parte superior de cada cabeçalho de coluna para alterar as colunas listadas abaixo para os seguintes tipos:

* **Número decimal:** Administrative_Duration; Informational_Duration; ProductRelated_Duration; BounceRates; ExitRates; PageValues; SpecialDay
* **Verdadeiro/Falso:** Weekend; Revenue

![Alterar o tipo de dados](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

O modelo de **Predição Binária** que vamos preparar exige um campo Booleano como uma etiqueta que identifica os resultados das observações anteriores. Neste conjunto de dados, o atributo _Revenue_ indica uma compra e já está disponível como um Booleano. Deste modo, não é necessário adicionar uma coluna calculada para a etiqueta. Noutros conjuntos de dados, talvez seja necessário transformar os atributos de etiqueta existentes numa coluna Booleana.

Selecione o botão **Concluído** para fechar o Editor do Power Query. Esta ação apresenta a lista de entidades com os dados dos _Visitantes Online_ que adicionámos. Selecione **Guardar** no canto superior direito, forneça um nome para o fluxo de dados e, em seguida, selecione **Guardar** na caixa de diálogo, conforme mostrado na imagem seguinte.

![Guardar o fluxo de dados](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>Atualizar o fluxo de dados

Guardar os resultados de fluxo de dados resulta na apresentação de uma notificação que informa que o fluxo de dados foi guardado. Selecione **Atualizar agora** para ingerir os dados da origem para o fluxo de dados.

![Atualizar agora](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

Selecione **Fechar** no canto superior direito e aguarde pela conclusão da atualização do fluxo de dados.

Também pode atualizar o fluxo de dados com os comandos **Ações**. O fluxo de dados mostra o carimbo de data/hora quando a atualização estiver concluída.

![Carimbo de data/hora da atualização](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>Criar e preparar um modelo de machine learning

Selecione o fluxo de dados após a atualização estar concluída. Para adicionar um modelo de machine learning, selecione o botão **Aplicar modelo de ML** na lista de **Ações** para a entidade base com os dados de preparação e as informações de etiqueta e, em seguida, selecione **Adicionar um modelo de machine learning**.

![Adicione um modelo de machine learning](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

O primeiro passo para a criação do nosso modelo de machine learning é identificar os dados históricos, incluindo o campo de etiqueta que quer prever. O modelo será criado através da aprendizagem desses dados.

No caso do conjunto de dados que estamos a utilizar, este é o campo **Revenue**. Selecione **Revenue** como o valor do “campo Resultado histórico” e **Seguinte**.

![Selecionar os dados históricos](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

Em seguida, devemos selecionar o tipo de modelo de machine learning a criar. O Power BI analisa os valores no campo de resultado histórico que identificou e sugere os tipos de modelos de machine learning que podem ser criados para prever esse campo.

Neste caso, uma vez que estamos a prever um resultado binário sobre se um utilizador efetuará ou não uma compra, selecione **Predição Binária** para o tipo de modelo e Seguinte.

![Predição binária selecionada](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

Em seguida, o Power BI realiza uma análise preliminar dos dados e sugere as entradas que o modelo poderá utilizar. O utilizador tem a opção de personalizar os campos de entrada utilizados para o modelo. No nosso conjunto de dados organizado, para selecionar todos os campos, selecione a caixa de verificação junto ao nome da entidade. Selecione **Seguinte** para aceitar as entradas.

![Selecionar a caixa de verificação Seguinte](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

No passo final, devemos fornecer um nome para o nosso modelo, bem como as etiquetas amigáveis para os resultados a serem utilizados no relatório gerado automaticamente, que resumirá os resultados da validação do modelo. Em seguida, temos de atribuir o nome _Purchase Intent Prediction_ ao modelo e _Purchase_ e _No-Purchase_ às etiquetas de verdadeiro e falso. Em seguida, selecione **Guardar**.

![Guardar o modelo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

O nosso modelo de machine learning está agora pronto para a preparação. Selecione **Atualizar Agora** para começar a preparar o modelo.

![Atualizar agora](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

O processo de preparação começará com a amostragem e a normalização dos dados históricos e com a divisão do conjunto de dados em duas novas entidades: *Purchase Intent Prediction Training Data* e *Purchase Intent Prediction Testing Data*.

Dependendo do tamanho do conjunto de dados, o processo de preparação pode demorar de alguns minutos até algumas horas. Neste ponto, pode ver o modelo no separador **Modelos de machine learning** do fluxo de dados. O estado _Pronto_ indica que o modelo foi colocado em fila para a preparação ou está a ser preparado.

![Pronto para a preparação](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

Quando o modelo está a ser preparado, não poderá ver nem editar o fluxo de dados. Pode confirmar que o modelo está a ser preparado e validado através do estado do fluxo de dados. Tal é apresentado como uma atualização de dados em curso no separador **Fluxo de dados** da área de trabalho.

![Em processamento](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

Após a conclusão da preparação do modelo, o fluxo de dados apresenta um tempo de atualização atualizado. Pode confirmar que o modelo foi preparado ao aceder ao separador **Modelos de machine learning** no fluxo de dados. O modelo que criou deve apresentar o estado **Preparado** e a data/hora da **Última Preparação** deve estar agora atualizada.

![Última preparação em](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>Rever o relatório de validação do modelo

Para rever o relatório de validação do modelo, em **Modelos de machine learning**, selecione o botão **Ver relatório de desempenho e aplicar modelo** na coluna de **Ações** do modelo. Este relatório descreve o desempenho provável do modelo de machine learning.

Na página **Desempenho do Modelo** do relatório, selecione **Principais Influenciadores** para ver as principais previsões para o modelo. Pode selecionar uma das previsões para ver como a distribuição dos resultados está associada a essa previsão.

![Desempenho do modelo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

Pode utilizar a segmentação de dados **Limite de Probabilidade** na página Desempenho do Modelo para examinar a influência na Precisão e na Revocação do modelo.

![Probability threshold](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

As outras páginas do relatório descrevem as métricas estatísticas de desempenho do modelo.

O relatório também inclui uma página Detalhes da Preparação que descreve as diferentes iterações executadas, o modo de extração dos recursos das entradas e os hiperparâmetros utilizados para o modelo final.

## <a name="apply-the-model-to-a-dataflow-entity"></a>Aplicar o modelo a uma entidade de fluxo de dados

Selecione o botão **Aplicar modelo** na parte superior do relatório para invocar este modelo quando o fluxo de dados estiver atualizado. Na caixa de diálogo **Aplicar**, pode especificar a entidade de destino com os dados de origem aos quais o modelo deve ser aplicado.

![Aplicar o modelo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

Quando pedido, deve **Atualizar** o fluxo de dados para pré-visualizar os resultados do modelo.

A aplicação do modelo criará uma nova entidade, com o sufixo **enriched <nome_modelo>** anexado à entidade à qual aplicou o modelo. No nosso caso, a aplicação do modelo à entidade **OnlineShoppers** criará um **OnlineShoppers enriched Purchase Intent Prediction**, que inclui a saída prevista do modelo.

A aplicação de um modelo de Predição Binária adiciona três colunas com os resultados previstos, uma classificação de probabilidade e os principais influenciadores específicos do registo para a predição, cada um com um prefixo com o nome de coluna especificado.

![Três colunas de resultado](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

Devido a um problema conhecido, as colunas de saída classificadas na entidade melhorada são apenas acessíveis a partir do Power BI Desktop. Para pré-visualizar as colunas no serviço, deve utilizar uma entidade de pré-visualização especial.

Após a conclusão da atualização do fluxo de dados, pode selecionar a entidade **OnlineShoppers enriched Purchase Intent Prediction Preview** para ver os resultados.

![Ver os resultados](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>Utilizar a saída classificada do modelo num relatório do Power BI

Para utilizar a saída classificada do modelo de machine learning, pode ligar ao fluxo de dados a partir do Power BI Desktop através do conector de fluxos de dados. A entidade **OnlineShoppers enriched Purchase Intent Prediction Preview** pode agora ser utilizada para incorporar as predições do modelo nos relatórios do Power BI.

## <a name="next-steps"></a>Próximos passos

Neste tutorial, criou e aplicou um modelo de predição binária no Power BI com estes passos:

* Criar um fluxo de dados com os dados de entrada
* Criar e preparar um modelo de machine learning
* Rever o relatório de validação do modelo
* Aplicar o modelo a uma entidade de fluxo de dados
* Utilizar a saída classificada do modelo num relatório do Power BI

Para obter mais informações sobre a automatização do Machine Learning no Power BI, veja [Machine Learning Automatizado no Power BI (Pré-visualização)](service-machine-learning-automated.md).
