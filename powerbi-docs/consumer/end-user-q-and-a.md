---
title: Perguntas e Respostas para os consumidores do Power BI
description: Tópico de descrição geral de documentação para perguntas e respostas sobre linguagem natural em consultas do Power BI.
author: mihart
ms.reviewer: mohammad ali
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 7739967443a8c6dc75cdaa3fbd0e472dcc090b9a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "79488551"
---
# <a name="qa-for-power-bi-consumers"></a>Perguntas e Respostas para os consumidores do Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

## <a name="what-is-qa"></a>O que são as Perguntas e Respostas?
Às vezes, a maneira mais rápida de obter uma resposta dos seus dados é fazer uma pergunta em linguagem natural. Por exemplo, "qual foi o total de vendas no ano passado".

Utilize as Perguntas e Respostas para explorar os seus dados com recursos intuitivos em linguagem natural e receba as respostas na forma de quadros e gráficos. As Perguntas e Respostas são diferentes de um motor de busca -- as Perguntas e Respostas fornecem apenas resultados relativos aos dados no Power BI.

## <a name="which-visualization-does-qa-use"></a>Que visualização o P e R utiliza?
O P e R escolhe a melhor visualização com base nos dados que são apresentados. Por vezes, os dados no conjunto de dados subjacente são definidos como um determinado tipo ou categoria, o que ajuda as Perguntas e Respostas a saber como apresentá-los. Por exemplo, se os dados são definidos como um tipo de data, é mais provável que sejam apresentados como um gráfico de linhas. Os dados que são categorizados como uma cidade são mais prováveis de serem apresentados como um mapa.

Nas Perguntas e Respostas também pode especificar qual o elemento visual que quer utilizar ao adicioná-lo à sua pergunta. Mas tenha em mente que nem sempre será possível apresentar os dados no tipo de elemento visual que pediu. As Perguntas e Respostas irão apresentar uma lista dos tipos de elementos visuais viáveis.

## <a name="where-can-i-use-qa"></a>Onde posso utilizar as Perguntas e Respostas?
Poderá encontrar as Perguntas e Respostas nos dashboards no serviço Power BI e na parte inferior do dashboard no Power BI para dispositivos móveis. A menos que o designer lhe tenha dado permissões de edição, poderá utilizar as Perguntas e Respostas para explorar dados, mas não conseguirá guardar quaisquer visualizações criadas com as Perguntas e Respostas.

![caixa de perguntas](media/end-user-q-and-a/powerbi-qna.png)

Encontrará também Perguntas e Respostas sobre relatórios, se o *designer* de relatórios tiver adicionado um [elemento visual de Perguntas e Respostas](../visuals/power-bi-visualization-q-and-a.md).   

![Q&A visual (Elemento visual Perguntas e Respostas)](media/end-user-q-and-a/power-bi-q-and-a-default.png)

## <a name="qa-on-dashboards"></a>Perguntas e Respostas em dashboards

As **Perguntas e Respostas do Power BI** estão disponíveis mediante uma licença Pro ou Premium.  As [Perguntas e Respostas nas aplicações para dispositivos móveis do Power B](mobile/mobile-apps-ios-qna.md) e as [Perguntas e Respostas com o Power BI Embedded](../developer/embedded/qanda.md) são abordadas em artigos separados. Neste momento, as **Perguntas e Respostas do Power BI** apresentam apenas as respostas às consultas de linguagem natural realizadas em inglês, embora exista uma pré-visualização em espanhol que pode ser ativada pelo administrador do Power BI.


![mapa de árvore criado com as perguntas e respostas](media/end-user-q-and-a/power-bi-treemap.png)

A pergunta é apenas o início.  Divirta-se viajando pelos seus dados, refinando ou ampliando a sua pergunta, revelando informações novas e fiáveis, concentrando-se em detalhes e diminuindo o zoom para uma visão mais ampla. Vai ficar encantado com as informações obtidas e as descobertas.

A experiência é verdadeiramente interativa... e rápida! Com tecnologia de armazenamento dentro da memória, a resposta é praticamente instantânea.


## <a name="use-qa-on-a-dashboard-in-the-power-bi-service"></a>Utilizar as Perguntas e Respostas num dashboard no serviço Power BI
No serviço Power BI (app.powerbi.com), um dashboard contém mosaicos afixados a partir de um ou mais conjuntos de dados e, por isso, pode fazer perguntas sobre quaisquer dados contidos em qualquer um desses conjuntos de dados. Para ver os relatórios e os conjuntos de dados que foram utilizados na criação do dashboard, selecione **Ver relacionados** na lista pendente **Mais opções**.

![vista relacionada da barra de menus](media/end-user-q-and-a/power-bi-q-and-a-view-related.png)

## <a name="how-do-i-start"></a>Como posso começar?
Em primeiro lugar, familiarize-se com os conteúdos. Observe os elementos visuais no dashboard e no relatório. Obtenha uma ideia do tipo e do intervalo de dados que tem disponíveis. 

Por exemplo:

* Se os valores e as etiquetas do eixo dos elementos visuais incluírem “vendas”, “conta”, “mês” e “oportunidades”, poderá fazer perguntas como: "Que *conta* tem a *oportunidade* mais alta" ou "mostrar *vendas* por mês como um gráfico de barras."

* Se tiver dados de desempenho do site no Google Analytics, pode perguntar às Perguntas e Respostas sobre o tempo gasto numa página Web, o número de visitas à página exclusiva e taxas de envolvimento do utilizador. Ou, se estiver a consultar dados demográficos, poderá fazer perguntas sobre a faixa etária e o rendimento familiar por localização.

Assim que estiver familiarizado com os dados, regresse ao dashboard e coloque o cursor na caixa de perguntas. Esta ação irá abrir o ecrã Perguntas e Respostas.

![Ecrã Perguntas e Respostas](media/end-user-q-and-a/power-bi-suggested.png) 

Mesmo antes de começar a escrever, as Perguntas e Respostas apresentam um ecrã novo com sugestões para o ajudar a formular a sua pergunta. Verá as expressões e as perguntas que contêm os nomes das tabelas nos conjuntos de dados subjacentes e poderá até ver as perguntas *em destaque* criadas pelo próprio proprietário do conjunto de dados.

Pode selecionar qualquer uma destas para as adicionar à caixa de perguntas e, em seguida, reformulá-las para conseguir encontrar uma resposta específica. 

![Ecrã Perguntas e Respostas](media/end-user-q-and-a/power-bi-result.png) 

Para o ajudar a fazer perguntas, o Power BI tem outras funcionalidades, tais como os avisos, o preenchimento automático e as ajudas visuais. O Power BI ajuda-o com as Perguntas e Respostas nos dashboards, as Perguntas e Respostas nos relatórios e o elemento visual das Perguntas e Respostas. Iremos abordar estas funcionalidades em maior detalhe abaixo, na secção [Criar um elemento visual das Perguntas e Respostas ao introduzir uma consulta em linguagem natural](#create-a-qa-visual-by-typing-a-natural-language-query)

<!-- ![video](../visuals/media/end-user-q-and-a/qna4.gif) -->


## <a name="the-qa-visual-in-power-bi-reports"></a>O elemento visual das Perguntas e Respostas em relatórios do Power BI

O elemento visual das Perguntas e Respostas permite colocar perguntas em linguagem natural e obter respostas sob a forma de um elemento visual. O comportamento do elemento visual das Perguntas e Respostas é idêntico ao de qualquer outro elemento visual num relatório, na medida em que pode ter filtragem cruzada/destaque cruzado e também suporta marcadores e comentários. 

Pode identificar um elemento visual das Perguntas e Respostas pela sua caixa de perguntas na parte superior. É aqui que vai inserir ou introduzir perguntas em linguagem natural. O elemento visual das Perguntas e Respostas pode ser utilizado repetidamente para colocar perguntas sobre os seus dados. Quando sai do relatório, o elemento visual das Perguntas e Respostas é reposto para a predefinição. 

![Captura de ecrã do elemento visual das Perguntas e Respostas predefinido](media/end-user-q-and-a/power-bi-q-and-a-default.png)


## <a name="use-qa"></a>Utilizar as Perguntas e Respostas 
Para utilizar as Perguntas e Respostas num dashboard ou utilizar o elemento visual das Perguntas e Respostas num relatório, selecione uma das perguntas sugeridas ou escreva a sua própria pergunta em linguagem natural. 

### <a name="create-a-qa-visual-by-using-a-suggested-question"></a>Criar um elemento visual das Perguntas e Respostas através de uma pergunta sugerida

Aqui, selecionámos os **principais estados geográficos por unidades totais**. O Power BI faz o seu melhor para selecionar o tipo de elemento visual a utilizar. Neste caso, é um mapa.

![Mapa de elemento visual das Perguntas e Respostas](media/end-user-q-and-a/power-bi-q-and-a-suggested.png)

No entanto, pode indicar ao Power BI qual o tipo de elemento visual a utilizar ao adicioná-lo à sua consulta em linguagem natural. Tenha em conta que nem todos os tipos de elementos visuais funcionarão ou farão sentido com os seus dados. Por exemplo, estes dados não produziriam um gráfico de dispersão coerente. Mas funciona como um mapa de manchas.

![Elemento visual das Perguntas e Respostas como mapa de manchas](media/end-user-q-and-a/power-bi-filled-map.png)

### <a name="create-a-qa-visual-by-typing-a-natural-language-query"></a>Criar um elemento visual das Perguntas e Respostas ao introduzir uma consulta em linguagem natural


Se não souber que tipo de perguntas colocar ou qual a terminologia a utilizar, expanda **Mostrar todas as sugestões** ou procure outros elementos visuais no relatório. Assim, ficará familiarizado com os termos e conteúdos do conjunto de dados.

1. Escreva a sua pergunta no campo Perguntas e Respostas em linguagem natural. À medida que escreve a sua pergunta, o Power BI ajuda-o no preenchimento automático, ajudas visuais e feedback.

    **Preenchimento Automático** – ao escrever a sua pergunta, a funcionalidade Perguntas e Respostas do Power BI apresenta sugestões relevantes e contextuais para o ajudar a ser produtivo rapidamente com uma linguagem natural. Ao escrever, obtém feedback e resultados imediatos. A experiência é semelhante a escrever num motor de busca.

    Neste exemplo, a sugestão que pretendemos é a última. 

    ![As Perguntas e Respostas com uma palavra sublinhada a azul](media/end-user-q-and-a/power-bi-autocomplete.png)

    **Sublinhados a vermelho/azul** – a funcionalidade Perguntas e Respostas do Power BI apresenta as palavras com sublinhados para ajudar a ver que palavras o Power BI reconheceu ou não reconheceu. Um sublinhado azul sólido indica que o Power BI reconheceu a palavra. O exemplo abaixo mostra que a funcionalidade Perguntas e Respostas reconheceu a palavra **store** (loja).

    ![As Perguntas e Respostas com sugestões da lista pendente para concluir a pergunta](media/end-user-q-and-a/power-bi-blue.png)

    Selecione uma palavra sublinhada a azul para apresentar uma lista pendente de perguntas sugeridas. 

    ![Lista pendente com sugestões Também pode experimentar](media/end-user-q-and-a/power-bi-try.png)


    Muitas vezes, ao escrever uma palavra na funcionalidade Perguntas e Respostas, a mesma é marcada com um sublinhado a vermelho. Um sublinhado a vermelho pode indicar um de dois possíveis problemas. O primeiro tipo de problema é categorizado como confiança baixa. Se escrever uma palavra vaga ou ambígua, o campo será sublinhado a vermelho. Um exemplo poderá ser a palavra "Location" (Localização). Múltiplos campos podem conter a palavra "Location" (Localização), pelo que o sistema utiliza um sublinhado a vermelho para pedir que escolha o campo pretendido. Neste exemplo, o Power BI pede-lhe para selecionar o campo que pretende utilizar para "VanArsdel".
    
    ![Termo sublinhado a vermelho na caixa de perguntas das Perguntas e Respostas](media/end-user-q-and-a/power-bi-q-and-a-red.png)
    
    Outro exemplo de baixa confiança poderá ser se escrever a palavra "area" (área), mas a coluna correspondente for "district" (distrito). A funcionalidade Perguntas e Respostas do Power BI reconhece palavras que significam a mesma coisa, graças à integração com o Bing e o Office. A funcionalidade Perguntas e Respostas sublinha a palavra a vermelho para que saiba que não é uma correspondência direta

    ![A funcionalidade Perguntas e Respostas reescreve a pergunta com um sinónimo](media/end-user-q-and-a/power-bi-red.png)

    O segundo tipo de problema é quando a funcionalidade Perguntas e Respostas não reconhece a palavra. Um exemplo poderá ser utilizar a palavra "geography" (geografia), embora a mesma não exista nos dados. A palavra existe no dicionário, mas a funcionalidade Perguntas e Respostas marca este termo com um sublinhado a vermelho. A funcionalidade Perguntas e Respostas do Power BI não consegue criar uma visualização e sugere que pergunte ao designer do relatório para adicionar o termo.

    ![A funcionalidade Perguntas e Respostas a sugerir que peça ao designer para adicionar a palavra geografia](media/end-user-q-and-a/power-bi-geography.png)

    **Sugestões** – à medida que escreve a pergunta, o Power BI informa-o se não entender a mesma e tenta ajudar. No exemplo a seguir, o Power BI pergunta-lhe "Quis dizer..." e sugere outra forma de frasear a sua pergunta com terminologia do seu conjunto de dados. 

    ![Elemento visual das Perguntas e Respostas a apresentar correções sugeridas](media/end-user-q-and-a/power-bi-q-and-a-did-you-mean.png)

    Depois de selecionar a correção do Power BI, os resultados são apresentados como um gráfico de linhas. 

    ![Os resultados do elemento visual das Perguntas e Respostas apresentados como um gráfico de linhas](media/end-user-q-and-a/power-bi-q-and-a-line.png)


    Porém, pode alterar o gráfico de linhas para outro tipo de elemento visual.  

    ![Elemento visual das Perguntas e Respostas com "as a column chart" adicionado à pergunta](media/end-user-q-and-a/power-bi-q-and-a-specify-type.png)



## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas

**Pergunta**: Não vejo as Perguntas e Respostas neste dashboard.    
**Resposta 1**: Se não vir uma caixa de perguntas, verifique primeiro as suas definições. Para fazê-lo, selecione o ícone de engrenagem no canto superior direito da barra de ferramentas do Power BI.   
![ícone de engrenagem](media/end-user-q-and-a/power-bi-settings.png)

Em seguida, selecione **Definições** > **Dashboards**. Certifique-se de que existe uma marca de verificação junto a **Mostrar a caixa de pesquisa Perguntas e Respostas neste dashboard**.    
![Definições de Perguntas e Respostas do dashboard](media/end-user-q-and-a/power-bi-turn-on.png)  


**Resposta 2**: Por vezes, não terá acesso às definições. Se o *designer* do dashboard ou o administrador tiver desativado as Perguntas e Respostas, pergunte-lhe se é possível ativá-las novamente.   

**Pergunta**: Não estou a obter os resultados que pretendo ver ao escrever uma pergunta.    
**Resposta**: Selecione a opção para entrar em contacto com o proprietário do relatório ou do dashboard. Pode fazê-lo diretamente na página das Perguntas e Respostas do dashboard ou no elemento visual de Perguntas e Respostas. Em alternativa, pode procurar o proprietário no cabeçalho do Power BI.  Existem várias formas de o designer conseguir melhorar os resultados das Perguntas e Respostas. Por exemplo, o designer pode mudar o nome das colunas no conjunto de dados de maneira a utilizar termos que sejam fáceis de compreender (`CustomerFirstName` em vez de `CustFN`). Uma vez que o designer conhece muito bem o conjunto de dados, o próprio também poderá elaborar perguntas úteis e adicioná-las às perguntas sugeridas das Perguntas e Respostas.

![Apresentar informações de contacto](media/end-user-q-and-a/power-bi-q-and-a-contact.png)

## <a name="privacy"></a>Privacidade

A Microsoft pode utilizar as suas perguntas para melhorar o Power BI. Veja a [Declaração de Privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839) para obter mais informações.

## <a name="next-steps"></a>Próximos passos
Para saber como um elemento visual das Perguntas e Respostas é criado e gerido por um *designer* de relatórios, veja [Tipo de elemento visual das Perguntas e Respostas](../visuals/power-bi-visualization-q-and-a.md).
