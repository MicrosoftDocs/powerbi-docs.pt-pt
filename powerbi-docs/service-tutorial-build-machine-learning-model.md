---
title: 'Tutorial: Criar um modelo de Machine Learning no Power BI (pré-visualização)'
description: Neste tutorial, vai criar um modelo de Machine Learning no Power BI.
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
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61407198"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>Tutorial: Criar um modelo de Machine Learning no Power BI (pré-visualização)

Este artigo de tutorial, vai utilizar **automatizada Machine Learning** para criar e aplicar um modelo de predição binários no Power BI. O tutorial inclui orientações para a criação de um fluxo de dados do Power BI e, usar as entidades definidas no fluxo de dados para preparar e validar um modelo de machine learning diretamente no Power BI. Em seguida, usamos esse modelo para a classificação para gerar as previsões de indisponibilidade.

Em primeiro lugar, criará um binário predição modelo machine learning, para prever a intenção de compra de compradores online com base num conjunto de seus atributos de sessão online. Um conjunto de dados do parâmetro de comparação machine learning é utilizado para este exercício. Assim que é preparado um modelo, o Power BI irá gerar automaticamente um relatório de validação que explica os resultados de modelo. Em seguida, pode rever o relatório de validação e aplicar o modelo aos seus dados para a classificação.

Neste tutorial consiste nos passos seguintes:

> [!div class="checklist"]
> * Criar um fluxo de dados com os dados de entrada
> * Criar e formar um modelo de machine learning
> * Reveja o relatório de validação de modelo
> * Aplicar o modelo para uma entidade de fluxo de dados
> * A saída com a pontuação do modelo a utilizar no relatório do Power BI

## <a name="create-a-dataflow-with-the-input-data"></a>Criar um fluxo de dados com os dados de entrada

A primeira parte deste tutorial é criar um fluxo de dados com dados de entrada. Esse processo consiste em algumas etapas, conforme mostrado nas seções a seguir, começando com a obtenção de dados.

### <a name="get-data"></a>Obter dados

A primeira etapa na criação de um fluxo de dados é fazer com as origens de dados prontas. No nosso caso, podemos usar um conjunto de dados de aprendizagem automática de um conjunto de sessões online, alguns dos quais culminated numa compra. O conjunto de dados contém um conjunto de atributos sobre estas sessões, o que vamos utilizar para o nosso modelo de formação.

Pode transferir o conjunto de dados a partir do site da UC Irvine.  Além disso, temos disponível, para efeitos deste tutorial, da seguinte ligação: [online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv).

### <a name="create-the-entities"></a>Criar as entidades

Para criar as entidades no seu fluxo de dados, inicie sessão no serviço Power BI e navegue para uma área de trabalho na sua capacidade dedicada que tenha a pré-visualização de IA ativada.

Se ainda não tiver uma área de trabalho, pode criar uma selecionando **áreas de trabalho** no menu de navegação esquerdo no serviço Power BI e selecione **criar área de trabalho de aplicação** na parte inferior do painel que é apresentada. Esta ação abre um painel à direita para introduzir os detalhes da área de trabalho. Introduza um nome de área de trabalho e selecione **avançadas**. Confirme que a área de trabalho usa capacidade dedicada que utilize o botão de opção e que é atribuído a uma instância de capacidade dedicada que tem a pré-visualização de IA ativada. Em seguida, selecione **Guardar**.

![Criar uma área de trabalho](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

Depois da área de trabalho é criada, pode selecionar **ignorar** no canto inferior direito do ecrã de boas-vindos, conforme mostrado na imagem seguinte.

![Ignore se tiver uma área de trabalho](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

Selecione o **fluxos de dados (pré-visualização)** separador. Selecione o **Create** botão na parte superior direita da área de trabalho e, em seguida, selecione **fluxo de dados**.

![Criar o fluxo de dados](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

Selecione **Adicionar novas entidades**. Isso inicia um **Power Query** editor no browser.

![Adicionar nova entidade](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

Selecione **o ficheiro de texto/CSV** como uma origem de dados, mostrado na imagem seguinte.

![Ficheiro de texto/CSF selecionado](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

Na **ligar a uma origem de dados** que apresentada a seguir, cole a seguinte hiperligação para o *online_shoppers_intention.csv* para o **caminho de ficheiro ou URL** caixa e, em seguida, selecione  **Próxima**.

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![Caminho do ficheiro](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

O Editor do Power Query mostra uma pré-visualização dos dados de ficheiro. CSV. Selecione **transformar tabela** na faixa de opções de comando e, em seguida, selecione **utilizar primeira linha como cabeçalhos** no menu que aparece. Esta ação adiciona os _promovidos a cabeçalhos_ passo de consulta para o **passos aplicados** secção à direita do ecrã. Pode renomear a consulta para um nome ao alterar o valor no **nome** caixa encontrados no painel da direita. Por exemplo, pode alterar o nome da consulta para _visitante Online_.

![Alterar para um nome amigável](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

Alguns dos tipos de dados de atributo este conjunto de dados são _numérico_ ou _booleano_, embora estes podem ser interpretadas como seqüências de caracteres **Power Query**. Selecione o ícone de tipo de atributo na parte superior de cada cabeçalho de coluna para alterar as colunas listadas abaixo para os seguintes tipos:

* **Número decimal:** Administrative_Duration; Informational_Duration; ProductRelated_Duration; BounceRates; ExitRates; PageValues; SpecialDay
* **Verdadeiro/falso:** Fim de semana; Receita

![Alterar o tipo de dados](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

O **predição binário** modelo irá preparar necessita de um campo booleano como uma etiqueta de identificação os resultados dos últimos observações. Este conjunto de dados, o _receita_ atributo indica a compra e este atributo já está disponível como um booleano. Portanto, não precisamos adicionar uma coluna calculada para a etiqueta. Em outros conjuntos de dados, poderá ter de transformar os atributos de etiqueta existente numa coluna booleana.

Selecione o **feito** botão para fechar o Editor do Power Query. Isto mostra a lista de entidades com o _visitantes Online_ dados que adicionamos. Selecione **salvar** no canto superior direito, forneça um nome para o fluxo de dados e, em seguida, selecione **guardar** na caixa de diálogo, conforme mostrado na imagem seguinte.

![Guardar o fluxo de dados](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>Atualizar o fluxo de dados

A guardar os resultados de fluxo de dados numa notificação que está a ser apresentada, informando que o fluxo de dados foi guardado. Selecione **atualizar agora** para ingerir os dados da origem para o fluxo de dados.

![Atualizar agora](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

Selecione **Fechar** no canto superior direito e aguarde pela conclusão da atualização do fluxo de dados.

Também pode atualizar o seu fluxo de dados utilizando o **ações** comandos. O fluxo de dados mostra o carimbo de hora em que a atualização foi concluída.

![Timestamp de atualização](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>Criar e formar um modelo de machine learning

Selecione o fluxo de dados após a atualização foi concluída. Para adicionar um modelo de aprendizagem automática, selecione o **modelo de ML aplicar** botão no **ações** lista para a entidade base, que contém as informações de dados e a etiqueta de treinamento e, em seguida, selecione **adicionar um modelo de aprendizagem automática**.

![Adicione um modelo de machine learning](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

A primeira etapa para a criação de nosso modelo de aprendizagem automática é identificar os dados históricos, incluindo o campo de etiqueta que pretende prever. O modelo será criado pelo learning a partir destes dados.

No caso do conjunto de dados que estamos a utilizar, esse é o **receita** campo. Selecione **receita** como o valor de "campo de resultado de histórico" e selecione **próxima**.

![Selecione os dados históricos](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

Em seguida, podemos tem de selecionar o tipo de modelo para criar de machine learning. Power BI analisa os valores no campo de resultado históricos que identificou e sugere os tipos de modelos de aprendizagem automática que podem ser criados para prever esse campo.

Neste caso, uma vez que estamos estiver prever se um utilizador irá efetuar uma compra ou não um resultado binário, selecione **predição binário** para o tipo de modelo e, em seguida, selecionar seguinte.

![Predição binária selecionada](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

Em seguida, o Power BI faz uma verificação preliminar dos dados e sugere as entradas que poderia usar o modelo. Tem a opção de personalizar os campos de entrada para o modelo. No nosso conjunto de dados estruturado, para selecionar todos os campos, selecione a caixa de verificação junto ao nome da entidade. Selecione **seguinte** para aceitar as entradas.

![Selecione a caixa de verificação seguinte](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

No passo final, devemos fornecer um nome para o nosso modelo, bem como as etiquetas amigáveis para os resultados a utilizar no relatório gerado automaticamente que resume os resultados da validação do modelo. Em seguida, temos o modelo de nomear _predição de intenção de compra_e as etiquetas de verdadeiras ou falsos, como _Compra_ e _não Compra_. Em seguida, selecione **Guardar**.

![Guarde o modelo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

Nosso modelo de machine learning está agora pronto para treinamento. Selecione **atualizar agora** para começar a dar formação sobre o modelo.

![Atualizar agora](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

O processo de treinamento será iniciado por amostragem e normalizar os dados históricos e dividir o conjunto de dados em duas novas entidades *dados de treinamento de predição de intenção de compra* e *testes de predição de intenção de compra Dados*.

Dependendo do tamanho do conjunto de dados, o processo de treinamento pode demorar entre alguns minutos para algumas horas. Neste ponto, pode ver o modelo do **de Machine learning modelos** separador do fluxo de dados. O _pronto_ estado indica que o modelo tem foi colocado em fila para treinamento ou que está abaixo do treinamento.

![Pronto para formação](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

Embora o modelo é treinamento, não será possível ver ou editar o fluxo de dados. Pode confirmar que o modelo está a ser treinado e validados através do Estado do fluxo de dados. Esta opção aparece como uma atualização de dados em curso no **fluxos de dados** separador da área de trabalho.

![No processo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

Depois de concluída a preparação de modelos, o fluxo de dados apresenta uma hora de atualização atualizado. Pode confirmar que é preparado o modelo, ao navegar para o **de Machine learning modelos** separador no fluxo de dados. O modelo que criar deve mostrar o estado como **Trained** e o **última treinado** tempo agora deve ser atualizado.

![Última com base em com](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>Reveja o relatório de validação de modelo

Para consultar o relatório de validação de modelo, na **modelos de Machine learning, s** opte pelo **Ver relatório de desempenho e aplicar modelo** botão no **ações** coluna para o modelo . Este relatório descreve como é provável que executar o seu modelo de aprendizagem automática.

Na **desempenho do modelo** página do relatório, selecione **influenciadores chave** para ver os principais indicadores para o seu modelo. Pode selecionar um dos indicadores para ver como a distribuição de resultado associados a essa previsão.

![Desempenho do modelo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

Pode utilizar o **limiar de probabilidade** segmentação de dados na página de desempenho de modelos para examinar a influência sobre a precisão e lembre-se para o modelo.

![Probability threshold](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

As outras páginas do relatório descrevem as métricas de desempenho estatística para o modelo.

O relatório também inclui uma página de detalhes de treinamento que descreve as iterações diferentes que foram executados, como os recursos foram extraídos das entradas e hiperparâmetros do modelo final utilizado.

## <a name="apply-the-model-to-a-dataflow-entity"></a>Aplicar o modelo para uma entidade de fluxo de dados

Selecione o **aplicar modelo** botão na parte superior do relatório para invocar esse modelo quando o fluxo de dados é atualizado. Na **aplicar** caixa de diálogo, pode especificar a entidade de destino que tenha os dados de origem para o qual o modelo deve ser aplicado.

![Aplicar o modelo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

Quando lhe for pedido, terá **atualizar** o fluxo de dados para pré-visualizar os resultados do seu modelo.

Aplicar o modelo irá criar uma nova entidade com o sufixo **enriquecida < nome_modelo >** anexado à entidade à qual se inscreveu o modelo. No nosso caso, aplicar o modelo para o **OnlineShoppers** irá criar a entidade **OnlineShoppers enriquecida predição de intenção de compra**, que inclui a saída prevista do modelo.

Aplicar um modelo de predição binário adiciona três colunas com resultado previsto, probabilidade e os influenciadores principais de específicas do registo para a predição, cada um prefixo com o nome da coluna especificado.

![Três colunas de resultado](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

Devido a um problema conhecido, as colunas de saída com a pontuação na entidade plena só estão acessíveis a partir do Power BI Desktop. Para pré-visualizar isso com o serviço, tem de utilizar uma entidade preview especial.

Depois de concluída a atualização de fluxo de dados, pode selecionar o **OnlineShoppers enriquecida pré-visualização de predição de intenção de compra** entidade para ver os resultados.

![Ver os resultados](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>A saída com a pontuação do modelo a utilizar no relatório do Power BI

Para utilizar a saída com a pontuação do seu modelo de machine learning, pode ligar ao seu fluxo de dados da área de trabalho do Power BI, com o conector de fluxos de dados. O **OnlineShoppers enriquecida predição de intenção de compra** entidade pode agora ser utilizada para incorporar as previsões do modelo nos relatórios do Power BI.

## <a name="next-steps"></a>Próximos passos

Neste tutorial, criou e aplicadas um modelo de predição binários no Power BI utiliza estes passos:

* Criar um fluxo de dados com os dados de entrada
* Criar e formar um modelo de machine learning
* Reveja o relatório de validação de modelo
* Aplicar o modelo para uma entidade de fluxo de dados
* A saída com a pontuação do modelo a utilizar no relatório do Power BI

Para obter mais informações sobre a automatização de Machine Learning no Power BI, consulte [automatizada Machine Learning no Power BI (pré-visualização)](service-machine-learning-automated.md).
