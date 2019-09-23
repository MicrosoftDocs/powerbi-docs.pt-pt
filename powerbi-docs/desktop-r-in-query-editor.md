---
title: Utilizar o R no Editor do Power Query
description: Utilizar o R no Editor de Consultas do Power BI Desktop para análise avançada
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/06/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b64b4b736291ce1c3bde02010b7e583a0c3dc406
ms.sourcegitcommit: 226b47f64e6749061cd54bf8d4436f7deaed7691
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2019
ms.locfileid: "70841503"
---
# <a name="use-r-in-query-editor"></a>Utilizar o R no Editor de Consultas

O [**R**](https://mran.microsoft.com/documents/what-is-r) é uma linguagem de programação avançada que muitos estatísticos, cientistas de dados e analistas de dados utilizam. Pode utilizar o **R** no **Editor de Consultas** do Power BI Desktop para:

* Preparar modelos de dados

* Create reports (Criar relatórios)

* Efetuar limpeza de dados, formatação de dados avançada e análise de conjuntos de dados, que incluem a conclusão de dados em falta, predições, clustering e mais.  

## <a name="install-r"></a>Instalar o R

Pode transferir o **R** gratuitamente a partir da [página de transferência do Revolution Open](https://mran.revolutionanalytics.com/download/) e do [Repositório CRAN](https://cran.r-project.org/bin/windows/base/).

### <a name="install-mice"></a>Instalar a biblioteca mice

Precisa de ter a biblioteca [**mice** ](https://www.rdocumentation.org/packages/mice/versions/3.5.0/topics/mice)instalada no seu ambiente de R. Sem a biblioteca **mice**, o código de script de exemplo não irá funcionar corretamente. O pacote de **mice** implementa um método para lidar com os dados em falta.

Para instalar a biblioteca **mice**:

1. Inicie o programa R.exe (por exemplo, C:\Program Files\Microsoft\R Open\R-3.5.3\bin\R.exe)  

2. Execute o comando de instalação:

   ``` 
   >  install.packages('mice') 
   ```

## <a name="use-r-in-query-editor"></a>Utilizar o R no Editor de Consultas

Para demonstrar a utilização de **R** no **Editor de Consultas**, iremos utilizar um conjunto de dados da bolsa de valores contido num ficheiro .csv e trabalhar no mesmo através dos seguintes passos:

1. [Transfira o ficheiro **EuStockMarkets_NA.csv**](http://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/EuStockMarkets_NA.csv). Lembre-se de onde o guardou.

1. Carregue o ficheiro para o **Power BI Desktop**: no friso **Base**, selecione **Obter Dados > Texto/CSV**.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_1.png)

1. Selecione o ficheiro e, em seguida, selecione **Abrir**. Os dados CSV são apresentados na caixa de diálogo **Ficheiro de Texto/CSV**.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_2.png)

1. Após o carregamento dos dados, estes são apresentados no painel **Campos**.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_3.png)

1. Para abrir o **Editor de Consultas**, no friso **Base** selecione **Editar Consultas**.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_4.png)

1. No friso **Transformar**, selecione **Executar Script de R**. É apresentado o editor **Executar Script do R**.  

   As linhas 15 e 20 têm dados em falta, bem como outras linhas que não são visíveis na imagem. Os passos abaixo mostram como o R completa essas linhas automaticamente.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_5d.png)

1. Neste exemplo, introduza o seguinte código de script. Certifique-se de que substitui "&lt;O Caminho do Ficheiro&gt;" pelo caminho para **EuStockMarkets_NA.csv** no seu sistema de ficheiros local, por exemplo, C:/Users/Guilherme Sarmento/Documents/Microsoft/EuStockMarkets_NA.csv

    ```r
       dataset <- read.csv(file="<Your File Path>/EuStockMarkets_NA.csv", header=TRUE, sep=",")
       library(mice)
       tempData <- mice(dataset,m=1,maxit=50,meth='pmm',seed=100)
       completedData <- complete(tempData,1)
       output <- dataset
       output$completedValues <- completedData$"SMI missing values"
    ```

    > [!NOTE]
    > Poderá ter de substituir uma variável chamada *saída* para criar corretamente o novo conjunto de dados com os filtros aplicados.

7. Após selecionar **OK**, o **Editor de Consultas** apresenta um aviso sobre a privacidade dos dados.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_6.png)
8. Para os scripts R funcionarem corretamente no serviço Power BI, precisa de definir todas as origens de dados como **públicas**. Para obter mais informações sobre as definições de privacidade e as respetivas implicações, veja [Níveis de Privacidade](desktop-privacy-levels.md).

   ![](media/desktop-r-in-query-editor/r-in-query-editor_7.png)

   Após selecionar **Guardar**, o script é executado. Repare na nova coluna no painel **Campos** com o nome **completedValues**. Tenha em atenção que existem alguns elementos de dados em falta, tal como nas linhas 15 e 18. Veja como o R processa isto na secção seguinte.

   Com apenas cinco linhas de script R, o **Editor de Consultas** preencheu os valores em falta com um modelo preditivo.

## <a name="create-visuals-from-r-script-data"></a>Criar elementos visuais a partir de dados de scripts R

Agora, podemos criar um elemento visual para ver como o código de script R utilizou a biblioteca **mice** para preencher os valores em falta, conforme mostrado na imagem seguinte:

![](media/desktop-r-in-query-editor/r-in-query-editor_8a.png)

Pode guardar todos os elementos visuais concluídos num ficheiro .pbix do **Power BI Desktop** e utilizar o modelo de dados e os respetivos scripts R no serviço Power BI.

> [!NOTE]
> Pode [transferir um ficheiro .pbix](http://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/Complete%20Values%20with%20R%20in%20PQ.pbix) quando tiver concluído todos estes passos.

Após carregar o ficheiro .pbix para o serviço Power BI, precisa de seguir passos adicionais para ativar a atualização de dados de serviço e a apresentação de elementos visuais atualizados:  

* **Ativar a atualização agendada do conjunto de dados** – para ativar a atualização agendada do livro que contém o conjunto de dados com scripts R, veja [Configurar a atualização agendada](refresh-scheduled-refresh.md), que também inclui informações sobre o **Gateway Pessoal**.

* **Instalar o Gateway Pessoal** – precisa de ter um **Gateway Pessoal** instalado numa máquina onde estejam localizados o ficheiro e o **R**. O serviço Power BI acede a esse livro e recompõe os elementos visuais atualizados. Para obter mais informações, veja como [instalar e configurar o Gateway Pessoal](service-gateway-personal-mode.md).

## <a name="limitations"></a>Limitações

Existem algumas limitações a consultas que incluem scripts R criados no **Editor de Consultas**:

* Todas as definições de origens de dados R têm de estar definidas como **Públicas**. Todos os outros passos numa consulta do **Editor de Consultas** também têm de estar públicos. Para aceder às definições da origem de dados, no **Power BI Desktop** selecione **Ficheiro > Opções e definições > Definições da origem de dados**.

  ![](media/desktop-r-in-query-editor/r-in-query-editor_9.png)

  Na caixa de diálogo **Definições da Origem de Dados**, selecione as origens de dados e, em seguida, selecione **Editar Permissões...** .  Defina o **Nível de Privacidade** como **Público**.

  ![](media/desktop-r-in-query-editor/r-in-query-editor_10.png)    
* Para ativar a atualização agendada dos elementos visuais de R ou do conjunto de dados, tem de ativar a **Atualização agendada** e ter um **Gateway Pessoal** instalado no computador que contém o livro e o **R**. Para obter mais informações sobre ambos, consulte a secção anterior neste artigo, que fornece ligações para saber mais sobre cada um deles.

Existem todos os tipos de coisas que pode fazer com o R e consultas personalizadas, por isso, explore e formate os dados apenas da forma como quer que apareçam.

## <a name="next-steps"></a>Próximos Passos

* [Introdução ao R](https://mran.microsoft.com/documents/what-is-r) 

* [Executar scripts R no Power BI Desktop](desktop-r-scripts.md) 

* [Utilizar um IDE R externo com o Power BI](desktop-r-ide.md) 

* [Pacotes R no serviço Power BI](service-r-packages-support.md)
