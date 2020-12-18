---
title: 'Tutorial: Consumir um modelo do Azure Machine Learning no Power BI'
titleSuffix: Azure Machine Learning
description: Saiba como consumir modelos do Azure Machine Learning no Power BI.
services: machine-learning
ms.service: machine-learning
ms.subservice: core
ms.topic: tutorial
ms.author: samkemp
author: samuel100
ms.reviewer: sdgilley, maggies
ms.date: 12/10/2020
ms.openlocfilehash: 6c68fff575e4da0c9126904df2de5292747c209c
ms.sourcegitcommit: 46cf62d9bb33ac7b7eae7910fbba6756f626c65f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97491788"
---
# <a name="tutorial-consume-azure-machine-learning-models-in-power-bi"></a>Tutorial: Consumir modelos do Azure Machine Learning no Power BI

Este tutorial explica como pode criar um relatório do Power BI com base num modelo de machine learning. No final deste tutorial, será capaz de:

> [!div class="checklist"]
> * Classificar modelos de machine learning (implementados com o Azure Machine Learning) no Power BI.
> * Ligar a um modelo do Azure Machine Learning no Editor do Power Query.
> * Criar um relatório com uma visualização baseada nesse modelo.
> * Publicar o relatório no serviço Power BI.
> * Configurar uma atualização agendada para o relatório.

## <a name="prerequisites"></a>Pré-requisitos

Antes de iniciar este tutorial, tem de:

- Preparar e implementar um modelo de machine learning no Azure Machine Learning. Utilizar um dos seguintes tutoriais do Azure Machine Learning: 

    - [Opção A: Código](/azure/machine-learning/tutorial-power-bi-custom-model)
    - [Opção B: Estruturador](/azure/machine-learning/tutorial-power-bi-designer-model)
    - [Opção C: ML Automatizado](/azure/machine-learning/tutorial-power-bi-automated-model)

- Inscrever-se numa [avaliação gratuita do Power BI](https://app.powerbi.com/signupredirect?pbi_source=web).
- [Instale o Power BI Desktop](https://powerbi.microsoft.com/desktop/) num computador local.

## <a name="create-the-data-model"></a>Criar o modelo de dados

Abra o Power BI Desktop e selecione **Obter Dados**. Na caixa de diálogo **Obter Dados**, procure **Web**. Selecione a origem **Web** > **Ligar**.

:::image type="content" source="media/service-aml-integrate/pbi-get-data.png" alt-text="Captura de ecrã a mostrar dados da Web.":::

Na caixa de diálogo **Da Web**, copie e cole o seguinte URL na caixa:

```txt 
https://www4.stat.ncsu.edu/~boos/var.select/diabetes.tab.txt
```

:::image type="content" source="media/service-aml-integrate/pbi-data.png" alt-text="Captura de ecrã a mostrar o URL da Web.":::

Selecione **OK**.

Selecione **Transformar dados** para abrir a janela **Editor do Power Query**.

No friso Base do Editor do Power Query, selecione o botão **Azure Machine Learning**.

:::image type="content" source="media/service-aml-integrate/aml-button.png" alt-text="Captura de ecrã a mostrar o Editor do Power Query.":::

Depois de iniciar sessão na conta do Azure com o início de sessão único, verá uma lista dos serviços disponíveis. Selecione o serviço **my-sklearn-service** que criou no tutorial Preparar e implementar um modelo de machine learning. 

O Power Query povoa as colunas automaticamente. Deve lembrar-se de que no nosso esquema do serviço, tínhamos um decorador Python que especificava as entradas. Selecione **OK**.

:::image type="content" source="media/service-aml-integrate/aml-pbi-run.png" alt-text="Captura de ecrã a mostrar os Modelos do Azure Machine Learning.":::

A seleção de **OK** chama o serviço Azure Machine Learning. Aciona um aviso sobre a privacidade dos dados e do ponto final.

:::image type="content" source="media/service-aml-integrate/data_privacy_warning.png" alt-text="Captura de ecrã a mostrar um aviso de privacidade.":::

Selecione **Continuar**. No ecrã seguinte, selecione **Ignorar as verificações de Níveis de Privacidade neste ficheiro** > **Guardar**.

Após a classificação dos dados, o Power Query cria uma coluna adicional denominada **zureML.my-diabetes-model**.

:::image type="content" source="media/service-aml-integrate/scored-data.png" alt-text="Captura de ecrã a mostrar a coluna classificada adicionada.":::

Os dados são devolvidos pelo serviço na forma de uma **lista**. 

> [!NOTE]
> Se tiver implementado um modelo de estruturador, verá um **registo**.

Para obter as predições, no friso **Transformar**, selecione o botão **Expandir coluna** > **Expandir para Novas Linhas**.

Após a expansão, verá as predições na coluna AzureML.my-diabetes-model.

:::image type="content" source="media/service-aml-integrate/after-expand.png" alt-text="Captura de ecrã a mostrar a expansão.":::

Siga os passos seguintes para concluir a limpeza do modelo de dados.

1. Mude o nome da coluna **AzureML.my-diabetes-model** para **previsto**.
1. Mude o nome da coluna **Y** para **real**.
1. Altere o tipo da coluna **real**: selecione a coluna e, no friso **Transformar**, selecione **Tipo de Dados** > **Número Decimal**.
1. Altere o tipo da coluna **previsto**: selecione essa coluna e, no friso **Transformar**, selecione **Tipo de Dados** > **Número Decimal**.
1. No friso **Base**, selecione **Fechar e Aplicar**.

## <a name="create-a-report-with-visualizations"></a>Criar um relatório com visualizações

Pode agora criar algumas visualizações para mostrar os dados.

1. No painel **Visualizações**, selecione um **Gráfico de linhas**. 
1. Com o elemento visual do gráfico de linhas selecionado:
1. Arraste o campo **IDADE** para o **Eixo**.
1. Arraste o campo **real** para **Valores**.
1. Arraste o campo **previsto** para **Valores**.

Redimensione o gráfico de linhas para preencher a página. O relatório tem agora um único gráfico de linhas com duas linhas, uma para os valores previstos e outra para os valores reais, distribuídos por idade.

:::image type="content" source="media/service-aml-integrate/report-viz.png" alt-text="Captura de ecrã a mostrar a visualização do relatório.":::

## <a name="publish-the-report"></a>Publicar o relatório

Pode adicionar mais visualizações, se desejar. Por questões de brevidade, vamos publicar o relatório neste tutorial.

1. Guarde o relatório.
1. Selecione **Ficheiro** > **Publicar** > **Publicar no Power BI**.
1. Inicie sessão no serviço Power BI.
1. Selecione **A Minha Área de Trabalho**.
1. Quando o relatório for publicado com êxito, selecione a ligação **Abrir <O_MEU_FICHEIRO_PBIX.pbix> no Power BI**. O relatório é aberto no Power BI no browser escolhido.

     :::image type="content" source="media/service-aml-integrate/publish-success.png" alt-text="Captura de ecrã a mostrar a publicação realizada com êxito.":::

## <a name="enable-datasets-to-refresh"></a>Permitir a atualização dos conjuntos de dados

Num cenário em que a origem de dados é atualizada com os novos dados a classificar, tem de atualizar as credenciais para que os dados possam ser classificados. 

Em A Minha Área de Trabalho do serviço Power BI, na barra de cabeçalho preta, selecione **Mais opções (...)**  > **Definições** > **Definições**.

:::image type="content" source="media/service-aml-integrate/settings-pbi.png" alt-text="Captura de ecrã a mostrar as definições.":::

Selecione **Conjuntos de dados**, expanda **Credenciais da origem de dados** e selecione **Editar Credenciais**.

:::image type="content" source="media/service-aml-integrate/data-refresh.png" alt-text="Captura de ecrã a mostrar a atualização das credenciais.":::

Siga as instruções para **azureMLFunctions** e **Web**. Selecione um nível de privacidade. Pode agora definir a **Atualização agendada** dos dados. Selecione uma **Frequência de atualização** e o **Fuso horário**. Também pode selecionar um endereço de e-mail para o qual o Power BI possa enviar as notificações de falha das atualizações.

:::image type="content" source="media/service-aml-integrate/schedule-refresh.png" alt-text="Captura de ecrã a mostrar o conjunto de dados e a atualização da classificação.":::

Selecione **Aplicar**.

>[!NOTE]
> Quando os dados são atualizados, também são enviados para o ponto final do Azure Machine Learning para classificação.

## <a name="clean-up-resources"></a>Limpar os recursos

>[!IMPORTANT]
>Pode utilizar os recursos que criou como pré-requisitos para outros tutoriais do Azure Machine Learning e artigos de procedimentos.

Se não planear utilizar os recursos que criou, elimine-os para não incorrer em custos.

1. No portal do Azure, selecione **Grupos de recursos** na extremidade esquerda.
 
1. Na lista, selecione o grupo de recursos que criou.

1. Selecione **Eliminar grupo de recursos**.

   ![Captura de ecrã a mostrar as seleções para eliminar um grupo de recursos no portal do Azure.](./media/service-aml-integrate/delete-resources.png)

1. Introduza o nome do grupo de recursos. Em seguida, selecione **Eliminar**.
1. Em A Minha Área de Trabalho no serviço Power BI, elimine o relatório e o conjunto de dados relacionado. Não precisa de eliminar o Power BI Desktop nem o relatório no computador. O Power BI Desktop é gratuito.

## <a name="next-steps"></a>Passos seguintes

Nesta série de tutoriais, aprendeu a configurar um agendamento no Power BI para que os novos dados possam ser classificados pelo ponto final de classificação no Azure Machine Learning.
