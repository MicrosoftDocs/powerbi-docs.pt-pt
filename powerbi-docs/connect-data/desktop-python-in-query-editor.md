---
title: Utilizar o Python no Editor de Consultas do Power BI
description: Utilizar o Python no Editor de Consultas do Power BI Desktop para análise avançada
author: otarb
ms.author: otarb
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 06/18/2018
LocalizationGroup: Connect to data
ms.openlocfilehash: fac0b396abd6cde87e7e3b738e53480ce34eba88
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96405175"
---
# <a name="use-python-in-query-editor"></a>Utilizar o Python no Editor de Consultas
Pode utilizar o **Python**, uma linguagem de programação amplamente utilizada por estatísticos, cientistas de dados e analistas de dados no **Editor de Consultas** do Power BI Desktop. Esta integração do Python no **Editor de Consultas** permite-lhe efetuar a limpeza dos dados e fazer a formatação e análise de dados avançadas em conjuntos de dados, incluindo a conclusão de dados em falta, predições e clustering, apenas para mencionar alguns exemplos. O **Python** é uma linguagem avançada e pode ser utilizada no **Editor de Consultas** para preparar o seu modelo de dados e criar relatórios.

## <a name="installing-python"></a>Instalar o Python
Para utilizar o **Python** no **Editor de Consultas** do Power BI Desktop, tem de instalar o **Python** no seu computador local. Pode transferir e instalar o **Python** gratuitamente a partir de vários locais, incluindo a partir da [página de transferência do Python Oficial](https://www.python.org/) e a partir do [Anaconda](https://anaconda.org/anaconda/python/).

## <a name="using-python-in-query-editor"></a>Utilizar o Python no Editor de Consultas
Para mostrar como utilizar o **Python** no **Editor de Consultas**, veja este exemplo de um conjunto de dados da bolsa de valores, com base num ficheiro .CSV que pode [transferir a partir daqui](https://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/EuStockMarkets_NA.csv) e acompanhar. Os passos para este exemplo são os seguintes:

1. Primeiro, carregue os dados para o **Power BI Desktop**. Neste exemplo, carregue o ficheiro *EuStockMarkets_NA.csv* e selecione **Obter Dados > CSV** a partir do friso **Base** no **Power BI Desktop**.
   
   ![Captura de ecrã a mostrar o friso Obter Dados no Power BI Desktop, com a seleção de CSV.](media/desktop-python-in-query-editor/python-in-query-editor-1.png)
2. Selecione o ficheiro e a opção **Abrir**. O CSV é apresentado na caixa de diálogo **Ficheiro CSV**.
   
   ![Captura de ecrã a mostrar a caixa de diálogo do ficheiro CSV, com o CSV selecionado.](media/desktop-python-in-query-editor/python-in-query-editor-2.png)
3. Após o carregamento dos dados, estes são apresentados no painel **Campos** no Power BI Desktop.
   
   ![Captura de ecrã a mostrar o painel Campos, com os dados carregados.](media/desktop-python-in-query-editor/python-in-query-editor-3.png)
4. Abra o **Editor de Consultas** ao selecionar **Editar Consultas** no separador **Base** no **Power BI Desktop**.
   
   ![Captura de ecrã a mostrar o Editor de Consultas no Power BI Desktop, com a seleção de Editar Consultas.](media/desktop-python-in-query-editor/python-in-query-editor-4.png)
5. No separador **Transformar**, selecione **Executar Script do Python** e é apresentado o editor **Executar Script do Python** (mostrado no passo seguinte). Tenha em atenção que as linhas 15 e 20 têm dados em falta, tal como outras linhas que não consegue ver na imagem seguinte. Os passos abaixo mostram como o Python pode (e irá) preencher as linhas por si.
   
   ![Captura de ecrã a mostrar o separador Transformar com linhas de dados.](media/desktop-python-in-query-editor/python-in-query-editor-5.png)
6. Neste exemplo, introduza o seguinte código de script:
   
    ```python
       import pandas as pd
       completedData = dataset.fillna(method='backfill', inplace=False)
       dataset["completedValues"] =  completedData["SMI missing values"]
   ```

   > [!NOTE]
   > Terá de ter a biblioteca *pandas* instalada no seu ambiente de Python para o código de script anterior funcionar corretamente. Para instalar a biblioteca pandas, execute o seguinte comando na instalação do Python: |      > pip install pandas
   > 
   > 
   
   Quando colocado na caixa de diálogo **Executar Script do Python**, o código assemelha-se ao seguinte:
   
   ![Captura de ecrã a mostrar a caixa de diálogo Executar Script do Python com o código do script.](media/desktop-python-in-query-editor/python-in-query-editor-5b.png)
7. Após selecionar **OK**, o **Editor de Consultas** apresenta um aviso sobre a privacidade dos dados.
   
   ![Captura de ecrã a mostrar o painel Editor de Consultas com o aviso sobre a privacidade dos dados.](media/desktop-python-in-query-editor/python-in-query-editor-6.png)
8. Para os scripts de Python funcionarem corretamente no serviço Power BI, todas as origens de dados têm de estar definidas como *públicas*. Para obter mais informações sobre as definições de privacidade e as respetivas implicações, veja [Níveis de Privacidade](../admin/desktop-privacy-levels.md).
   
   ![Captura de ecrã a mostrar a caixa de diálogo de níveis de Privacidade, com a opção Público definida.](media/desktop-python-in-query-editor/python-in-query-editor-7.png)
   
   Repare na nova coluna no painel **Campos** com o nome *completedValues*. Tenha em atenção que existem alguns elementos de dados em falta, tal como nas linhas 15 e 18. Veja como o Python processa isto na secção seguinte.
   

Com apenas cinco linhas de script do Python, o **Editor de Consultas** preencheu os valores em falta com um modelo preditivo.

## <a name="creating-visuals-from-python-script-data"></a>Criar elementos visuais a partir de dados de scripts de Python
Agora, podemos criar um elemento visual para ver como o código de script de Python utilizou a biblioteca *pandas* para preencher os valores em falta, conforme mostrado na seguinte imagem:

![Captura de ecrã a mostrar o elemento visual, com os dados originais e valores em falta preenchidos da biblioteca pandas.](media/desktop-python-in-query-editor/python-in-query-editor-8.png)

Depois de esse elemento visual estar preenchido, assim como todos os outros elementos visuais que possa querer criar através do **Power BI Desktop**, pode guardar o ficheiro do **Power BI Desktop** (guardado como um ficheiro .pbix) e utilizar o modelo de dados, incluindo os scripts de Python que fazem parte do mesmo, no serviço Power BI.

> [!NOTE]
> Quer ver um ficheiro .pbix preenchido com estes passos? Está com sorte; pode transferir o ficheiro do **Power BI Desktop** preenchido utilizado nestes exemplos [aqui](https://download.microsoft.com/download/A/B/C/ABCF5589-B88F-49D4-ADEB-4A623589FC09/Complete%20Values%20with%20Python%20in%20PQ.pbix).

Depois de carregar o ficheiro .pbix para o serviço Power BI, são necessários mais alguns passos para ativar a atualização dos dados e dos elementos visuais no serviço (os dados precisam de aceder ao Python para os elementos visuais serem atualizados). Os passos adicionais são os seguintes:

* **Ativar a atualização agendada do conjunto de dados** – para ativar a atualização agendada do livro que contém o conjunto de dados com scripts de Python, veja [Configurar a atualização agendada](refresh-scheduled-refresh.md), que também inclui informações sobre o **Gateway Pessoal**.
* **Instalar o Gateway pessoal** – precisa de um **Gateway Pessoal** instalado no computador onde está localizado o ficheiro e onde está instalado o Python; o serviço Power BI tem de aceder a esse livro e compor novamente todos os elementos visuais atualizados. Pode obter mais informações sobre como [instalar e configurar o Gateway Pessoal](service-gateway-personal-mode.md).

## <a name="limitations"></a>Limitações
Existem algumas limitações a consultas que incluem scripts de Python criados no **Editor de Consultas**:

* Todas as definições da origem de dados do Python têm de ser *públicas* e todos os outros passos numa consulta criada no **Editor de Consultas** também têm de ser públicos. Para aceder às definições da origem de dados, no **Power BI Desktop** selecione **Ficheiro > Opções e definições > Definições da origem de dados**.
  
  ![Captura de ecrã a mostrar o menu Ficheiro no Power BI Desktop, com a seleção de definições de Origem de dados.](media/desktop-python-in-query-editor/python-in-query-editor-9.png)
  
  Na caixa de diálogo **Definições da Origem de Dados**, selecione as origens de dados e, em seguida, selecione **Editar Permissões...** e certifique-se de que o **Nível de Privacidade** está definido como *Público*.
  
  ![Captura de ecrã a mostrar a caixa de diálogo Origem de dados, com o Nível de Privacidade definido para Público.](media/desktop-python-in-query-editor/python-in-query-editor-10.png)    
* Para ativar a atualização agendada dos elementos visuais do Python ou do conjunto de dados, tem de ativar a **Atualização agendada** e ter um **Gateway Pessoal** instalado no computador que aloja o livro e a instalação do Python. Para obter mais informações sobre ambos, consulte a secção anterior neste artigo, que fornece ligações para saber mais sobre cada um deles.
* As tabelas aninhadas (tabela de tabelas) não são atualmente suportadas 

Pode fazer todo o tipo de coisas com o Python e com consultas personalizadas, por isso explore e formate os seus dados exatamente como pretende.
