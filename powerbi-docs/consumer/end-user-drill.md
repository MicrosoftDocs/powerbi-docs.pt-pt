---
title: Desagregação e agregação num elemento visual
description: Este artigo mostra como pode desagregar num elemento visual no serviço Microsoft Power BI.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 02/18/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 0ca9fed0d086ab602ac5e7c4ae558e85a619da88
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85235219"
---
# <a name="drill-mode-in-a-visual-in-power-bi"></a>Modo de exploração num elemento visual no Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Este artigo mostra como pode desagregar num elemento visual no serviço Microsoft Power BI. Com a desagregação e a agregação nos pontos de dados, pode explorar os detalhes mais aprofundados sobre os seus dados. 

## <a name="drill-requires-a-hierarchy"></a>A desagregação requer uma hierarquia

Quando um visual tem uma hierarquia, pode desagregar para revelar detalhes adicionais. Por exemplo, pode ter um elemento visual que observa a contagem de medalhas olímpicas por uma hierarquia constituída por desporto, disciplina e evento. Por predefinição, o elemento visual mostra a contagem de medalhas por desporto: ginástica, esqui, desportos aquáticos, etc. Porém, dado que tem uma hierarquia, selecionar um dos elementos visuais (como uma barra, linha ou bolha) apresentaria uma imagem cada vez mais detalhada. Selecionar o elemento **desportos aquáticos** iria apresentar dados sobre natação, mergulho e polo aquático.  Selecionar o elemento **mergulho** iria apresentar detalhes sobre eventos de mergulho sincronizado, plataforma e prancha.

As datas são um tipo único de hierarquia.  Os designers de relatórios costumam adicionar hierarquias de datas aos elementos visuais. Uma hierarquia de datas comum contém o ano, trimestre, mês e dia. 

## <a name="figure-out-which-visuals-can-be-drilled"></a>Descubra quais elementos visuais podem ser explorados
Não sabe que elementos visuais do Power BI contêm uma hierarquia? Paire o cursor sobre um elemento visual. Se for apresentada uma combinação dos seguintes controlos de exploração na parte superior, significa que o seu elemento visual contém uma hierarquia.

![Captura de ecrã a mostrar os ícones de exploração.](./media/end-user-drill/power-bi-drill-icons.png)  


## <a name="learn-how-to-drill-down-and-up"></a>Saiba como desagregar e agregar

Neste exemplo, utilizamos um gráfico treemap que contém uma hierarquia composta pelo território, cidade, código postal e nome da loja. O gráfico treemap, antes de ser explorado, apresenta o total de unidades vendidas este ano por território. 

![Captura de ecrã a mostrar o gráfico treemap e os respetivos filtros.](./media/end-user-drill/power-bi-treemaps.png)  


### <a name="two-ways-to-access-the-drill-features"></a>Duas formas de aceder às funcionalidades de exploração

Tem duas formas de aceder às funcionalidades para desagregar, agregar e expandir os elementos visuais que contêm hierarquias. Experimente-as e utilize a que mais lhe agradar.

- Primeira forma: paire o cursor sobre um elemento visual para ver e utilizar os ícones.  

    ![Captura de ecrã do exemplo de passagem do cursor.](./media/end-user-drill/power-bi-hover.png)

- Segunda forma: clique com o botão direito do rato num elemento visual para apresentar e utilizar o menu.

    ![Captura de ecrã do exemplo de clique no botão direito do rato.](./media/end-user-drill/power-bi-drill-menu.png)



## <a name="drill-pathways"></a>Caminhos de desagregação

### <a name="drill-down-all-fields-at-once"></a>Desagregar todos os campos de uma só vez
![Ícone de desagregação](./media/end-user-drill/power-bi-drill-icon3.png)

Existem várias formas de explorar um elemento visual. Selecionar o ícone de desagregação permite-lhe aceder ao nível seguinte da hierarquia. Se estiver a observar o nível **Territory** (Território) para Kentucky e Tennessee, pode desagregar para o nível da cidade em ambos os estados e, em seguida, para o nível do código postal para ambos os estados e, por último, para o nível do nome da loja para ambos os estados. Cada passo do caminho apresenta novas informações.

![Diagrama a mostrar o caminho da desagregação](./media/end-user-drill/power-bi-drill-path.png)

Selecione o ícone de desagregação ![Ícone de desagregação](./media/end-user-drill/power-bi-drill-icon5.png) até voltar a "Total units this year by territory" (Total de unidades este ano por território).

### <a name="expand-all-fields-at-once"></a>Expandir todos os campos em simultâneo
![Ícone de expansão](./media/end-user-drill/power-bi-drill-icon6.png)

**Expandir** adiciona outro nível de hierarquia à vista atual. Por isso, se estiver no nível **Território**, poderá expandir e adicionar detalhes da cidade, código postal e nome ao treemap. Cada passo no caminho apresenta as mesmas informações e adiciona um nível de informações novas.

![Diagrama a mostrar o caminho da expansão](./media/end-user-drill/power-bi-expand-path.png)

Também pode optar por desagregar ou expandir um campo de cada vez.


### <a name="drill-down-one-field-at-a-time"></a>Desagregar um campo de cada vez


1. Selecione o ícone de desagregação para a ativar ![Captura de ecrã do ícone de desagregação ativada.](./media/end-user-drill/power-bi-drill-icon2.png).

    Agora tem a opção de desagregar **um campo de cada vez** ao selecionar um elemento visual. Exemplos de elementos visuais são: barra, bolha e folha.

    ![Captura de ecrã do elemento visual com seta a apontar para o ícone de desagregação ativada.](media/end-user-drill/power-bi-drill-icon-selected.png)

    Se não ativar a desagregação, a seleção de um elemento visual (como uma barra, bolha ou folha) não procederá à desagregação. Em vez disso, será efetuada a filtragem cruzada dos outros gráficos na página do relatório.

1. Selecione a folha para **TN**. O gráfico treemap apresenta agora todas as cidades e territórios no Tennessee que têm uma loja.

    ![Captura de ecrã do treemap a mostrar apenas os dados de TN.](media/end-user-drill/power-bi-drill-down-one.png)

1. Neste momento, pode:

    1. Continuar a desagregação no Tennessee.

    1. Efetuar uma desagregação numa determinada cidade do Tennessee.

    1. Optar por expandir.

    Continuemos a desagregar um campo de cada vez.  Selecione **Knoxville, TN**. O treemap mostra agora o código postal da sua loja em Knoxville.

    ![Captura de ecrã do treemap a mostrar o código postal 37919.](media/end-user-drill/power-bi-drill-two.png)

    Repare que o título muda à medida que desagrega e regressa.

### <a name="expand-all-and-expand-one-field-at-a-time"></a>Expandir tudo e expandir um campo de cada vez

Um treemap a mostrar apenas um código postal não é algo informativo.  Por isso, vamos *expandir* para baixo um nível na hierarquia.  

1. Com o treemap ativo, selecione o ícone *Expandir para baixo*![Captura de ecrã do ícone Expandir para baixo.](./media/end-user-drill/power-bi-drill-icon6.png). O treemap mostra agora dois níveis da nossa hierarquia: código postal e nome da loja.

    ![Captura de ecrã do treemap a mostrar o código postal e o nome da loja](./media/end-user-drill/power-bi-expand-one.png)

1. Para ver os quatro níveis de dados da hierarquia do Tennessee, selecione a seta de agregação até chegar ao segundo nível do treemap, **Total de unidades deste ano por território e por cidade**.

    ![Captura de ecrã do treemap a mostrar todos os dados de TN.](media/end-user-drill/power-bi-expand-two.png)

1. Confirme que a desagregação ainda está ativada, ![Captura de ecrã do ícone da desagregação ativado.](./media/end-user-drill/power-bi-drill-icon2.png) e selecione o ícone *expandir para baixo*![Captura de ecrã do ícone Expandir para baixo.](./media/end-user-drill/power-bi-drill-icon6.png). O gráfico treemap mostra agora o mesmo número de folhas (caixas), mas cada folha tem detalhes adicionais. Em vez de apresentar apenas a cidade e o estado, agora também apresenta o código postal.

    ![Captura de ecrã do elemento visual a mostrar a cidade, o estado e o código postal.](./media/end-user-drill/power-bi-expand-three.png)

1. Selecione novamente o ícone *Expandir para baixo* para apresentar os quatro níveis de detalhe da hierarquia do Tennessee no treemap. Coloque o cursor sobre uma folha para ver ainda mais detalhes.

    ![Captura de ecrã do treemap a mostrar uma sugestão de ferramenta com dados específicos da folha.](./media/end-user-drill/power-bi-expand-all.png)

## <a name="show-the-data-as-you-drill"></a>Mostrar os dados à medida que explora
Utilize a opção **Mostrar dados** para ver o que acontece nos bastidores. Sempre que explorar ou expandir, a opção **Mostrar dados** irá apresentar os dados utilizados para criar o elemento visual. Isto pode ajudar a compreender como as hierarquias, a exploração e a expansão funcionam em conjunto para criar elementos visuais. 

No canto superior direito, selecione **Mais opções** (...) e, em seguida, selecione **Mostrar Dados**. 

![Captura de ecrã do menu de reticências.](./media/end-user-drill/power-bi-ellipses.png)

A tabela seguinte mostra os resultados da desagregação de todos os campos em simultâneo, de Territory (Território) a Store Name (Nome da Loja).  


![Captura de ecrã a mostrar os dados dos quatro níveis de desagregação.](./media/end-user-drill/power-bi-show-data.png)

Repare que os totais são iguais para **City** (Cidade), **PostalCode** (Código Postal) e **Name** (Nome). Isto não acontecerá sempre.  Porém, para estes dados só existe uma loja em cada código postal e em cada cidade.  



## <a name="considerations-and-limitations"></a>Considerações e limitações
- Por predefinição, a desagregação não filtrará outros elementos visuais num relatório. No entanto, o designer do relatório pode alterar este comportamento predefinido. À medida que explora, observe se os outros elementos visuais na página foram sujeitos à filtragem cruzada ou ao realce cruzado.

- Para ver um relatório que foi partilhado consigo necessita de uma licença Power BI Pro ou Premium. [Qual é a minha licença?](end-user-license.md)


## <a name="next-steps"></a>Próximas etapas

[Elementos visuais em relatórios do Power BI](../visuals/power-bi-report-visualizations.md)

[Relatórios do Power BI](end-user-reports.md)

[Power BI - conceitos básicos](end-user-basic-concepts.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
