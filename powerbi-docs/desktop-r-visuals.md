---
title: Criar elementos visuais do Power BI com o R
description: Criar elementos visuais do Power BI com o R
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 641a4f457782711902ee7e2414cb9afffb391afc
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34286342"
---
# <a name="create-power-bi-visuals-using-r"></a>Criar elementos visuais do Power BI com o R
Com o **Power BI Desktop**, pode utilizar o **R** para visualizar os dados.

## <a name="install-r"></a>Instalar o R
O **Power BI Desktop** não inclui, implementa nem instala o motor **R**. Para executar scripts R no **Power BI Desktop**, tem de instalar o **R** no computador local separadamente. É possível transferir e instalar o **R** gratuitamente a partir de várias localizações, incluindo a [página de transferência do Revolution Open](https://mran.revolutionanalytics.com/download/) e o [Repositório CRAN](https://cran.r-project.org/bin/windows/base/). A versão atual do script R no **Power BI Desktop** suporta carateres Unicode, bem como espaços (carateres vazios) no caminho de instalação.

## <a name="enable-r-visuals"></a>Ativar elementos visuais do R
Para ativar elementos visuais do R, selecione **Ficheiro > Opções e definições > Opções** e, na página **Opções** apresentada, verifique se a sua instalação local do R está especificada na secção **Script do R** da janela **Opções**, conforme mostrado na imagem seguinte. Na imagem seguinte, a instalação local do caminho de R é **C:\Programas\R\R-3.2.0** e esse caminho é explicitamente fornecido na caixa de texto. Certifique-se de que o caminho apresentado reflete a instalação local do R que pretende que o **Power BI Desktop** utilize.
   
   ![](media/desktop-r-visuals/r-visuals-2.png)

Depois de especificar a instalação do R, estará pronto para começar a criar elementos visuais do R.

## <a name="create-r-visuals-in-power-bi-desktop"></a>Criar elementos visuais do R no Power BI Desktop
1. Selecione o ícone **Elemento visual do R** no painel **Visualização**, conforme mostrado na imagem seguinte, para adicionar um elemento visual do R.
   
   ![](media/desktop-r-visuals/r-visuals-3.png)

   Quando adiciona um elemento visual do R a um relatório, o **Power BI Desktop** faz o seguinte:
   
   - Uma imagem do elemento visual do R é apresentada na tela do relatório.
   
   - O **editor de scripts R** é apresentado na parte inferior do painel central.
   
   ![](media/desktop-r-visuals/r-visuals-4.png)

2. Em seguida, adicione os campos que deseja consumir no seu script R à secção **Valores** em **Campos** , como faria com qualquer outro elemento visual do **Power BI Desktop**. 
    
    Apenas os campos que foram adicionados à área **Campos** estão disponíveis para o script R. Pode adicionar novos campos ou remover campos desnecessários da área **Campos** enquanto trabalha no script R no **Editor de scripts R do Power BI Desktop**. O **Power BI Desktop** deteta automaticamente os campos que adicionou ou removeu.
   
   > [!NOTE]
   > O tipo de agregação predefinido para elementos visuais do R é *não resumir*.
   > 
   > 
   
3. Agora, pode utilizar os dados selecionados para criar um desenho. 

    Ao selecionar campos, o **editor de scripts R** gera um código de enlace de script R com suporte, com base nas suas seleções na secção cinzenta na parte superior do painel do editor. Ao selecionar ou remover campos adicionais, o suporte de código no editor de scripts R é automaticamente gerado ou removido adequadamente.
   
   No exemplo mostrado na imagem seguinte, três campos foram selecionados: hp, engrenagem e drat. Como resultado dessas seleções, o editor de scripts R gerou o seguinte código de enlace:
   
   * Um pacote de dados chamado **dataset** foi criado
     * Esse pacote de dados é composto por diferentes campos selecionados pelo utilizador
   * A agregação padrão é *não resumir*
   * Semelhantes aos elementos visuais de tabela, os campos são agrupados e as linhas duplicadas aparecem apenas uma vez
   
   ![](media/desktop-r-visuals/r-visuals-5.png)
   
   > [!TIP]
   > Em certos casos, pode não querer o agrupamento automático ou pode querer que todas as linhas sejam apresentadas, incluindo duplicados. Nesse caso, pode adicionar um campo de índice ao conjunto de dados, que faz com que todas as linhas sejam consideradas exclusivas e, assim, impedir o agrupamento.
   > 
   > 
   
   O pacote de dados gerado é denominado **dataset** e pode aceder às colunas selecionadas pelos seus nomes. Por exemplo, aceda ao campo de engrenagem ao escrever *dataset$gear* no script R. Para campos com espaços ou carateres especiais, utilize plicas.

4. Com o pacote de dados gerado automaticamente pelos campos selecionados, está pronto para escrever um script R que resulta em desenhar no dispositivo padrão R. Quando o script estiver concluído, selecione **Executar** na barra de título **Editor de scripts R** (**Executar** está no lado direito da barra de título).
   
    Quando selecionar **Executar**, o **Power BI Desktop** identifica o desenho e apresenta-o na tela. Uma vez que o processo é executado na instalação local do R, confirme que os pacotes necessários estão instalados.
   
   O **Power BI Desktop** volta a desenhar o elemento visual quando qualquer um dos seguintes eventos ocorre:
   
   * Quando selecionar **Executar** na barra de título **Editor de scripts R**
   * Sempre que ocorre uma alteração de dados, devido à atualização, filtragem ou destaque de dados

    A imagem seguinte mostra um exemplo de código de desenho de correlação, e desenha as correlações entre atributos de tipos de carros diferentes.

    ![](media/desktop-r-visuals/r-visuals-6.png)

5. Para obter uma vista ampliada das visualizações, pode minimizar o **Editor de scripts R**. E, claro, como noutros elementos visuais no **Power BI Desktop**, pode efetuar a filtragem cruzada do desenho de correlação, ao selecionar apenas carros desportivos no elemento visual de anel (o elemento visual redondo à direita, na imagem de exemplo acima).

    ![](media/desktop-r-visuals/r-visuals-7.png)

6. Também pode modificar o script R para personalizar o elemento visual e aproveitar o poder do R, adicionando parâmetros ao comando de desenho.

    O comando original de desenho era o seguinte:

    corrplot(M, method = "color",  tl.cex=0.6, tl.srt = 45, tl.col = "black")

    Com poucas alterações no script R, o comando é agora o seguinte:

    corrplot(M, method = "circle", tl.cex=0.6, tl.srt = 45, tl.col = "black", type= "upper", order="hclust")

    Como resultado, o elemento visual do R agora desenha círculos, só considera na metade superior e reorganiza a matriz para atributos correlacionados de cluster, conforme mostrado na imagem seguinte.

    ![](media/desktop-r-visuals/r-visuals-8.png)

    Ao executar um script R que resulta num erro, o elemento visual do R não é desenhado, e uma mensagem de erro é apresentada na tela. Para obter detalhes sobre o erro, selecione **Ver detalhes** no erro de elemento visual do R na tela.

    ![](media/desktop-r-visuals/r-visuals-9.png)

    > **Segurança dos scripts R**: os elementos visuais do R são criados a partir de scripts R, os quais podem conter código com riscos de segurança ou privacidade. Ao tentar ver ou interagir com um elemento visual R pela primeira vez, é apresentada uma mensagem de aviso de segurança. Ative os elementos visuais do R apenas se confiar no autor e na origem, ou depois de analisar e compreender o script R.
    > 
    > 

## <a name="known-limitations"></a>Limitações conhecidas
Os elementos visuais do R no **Power BI Desktop** apresentam algumas limitações:

* Limitações de tamanho de dados – os dados utilizados pelo elemento visual do R para desenhar são limitados a 150.000 linhas. Se forem selecionadas mais de 150.000 linhas, apenas as primeiras 150.000 linhas serão utilizadas e uma mensagem será apresentada na imagem.
* Limite de tempo de cálculo: se um cálculo do elemento visual R exceder cinco minutos, a execução atingirá o tempo limite e resultará num erro.
* Relações – tal como com outros elementos visuais do Power BI Desktop, se os campos de dados de tabelas diferentes numa relação definida entre estes forem selecionados, ocorrerá um erro.
* Os elementos visuais do R são atualizados após atualizações, filtragem e destaque de dados. No entanto, a própria imagem não é interativa e não pode ser a origem da filtragem cruzada.
* Os elementos visuais do R respondem ao destaque de outros elementos visuais, mas não pode clicar em elementos em elementos no visual do R para efetuar a filtragem cruzada de outros elementos.
* Apenas os desenhos que são desenhados no dispositivo de visualização predefinida do R são apresentados corretamente na tela. Evite a utilização explícita de um dispositivo de visualização diferente do R.
* Nesta versão, as instalações do RRO não são automaticamente identificadas pela versão de 32 bits do Power BI Desktop; portanto, é necessário fornecer manualmente o caminho para o diretório de instalação do R em **Opções e definições > Opções > Scripting do R**.

## <a name="next-steps"></a>Passos seguintes
Veja as seguintes informações adicionais sobre a linguagem R no Power BI.

* [Executar Scripts R no Power BI Desktop](desktop-r-scripts.md)
* [Utilizar um IDE R externo com o Power BI](desktop-r-ide.md)

