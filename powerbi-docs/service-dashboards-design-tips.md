---
title: Sugestões para criar um dashboard excelente no Power BI
description: Sugestões para criar um dashboard excelente no Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/22/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 082d0ba1e638e8eaf6ae16fa8d5ed63c128c8ad5
ms.sourcegitcommit: a1b7ca499f4ca7e90421511e9dfa61a33333de35
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/10/2018
ms.locfileid: "51507859"
---
# <a name="tips-for-designing-a-great-power-bi-dashboard"></a>Sugestões para criar um dashboard excelente no Power BI
Agora que já criou um dashboard e adicionou alguns mosaicos, pense em como tornar o dashboard não apenas bonito, mas também funcional. Em geral, significa destacar as informações mais importantes e torná-las claras e organizadas.

Eis algumas sugestões.

> [!TIP]
> Muitos dos princípios de estrutura dos relatórios aplicam-se também aos dashboards.  Leia o nosso documento prático [Princípios de boa estrutura para relatórios e visualizações](visuals/power-bi-visualization-best-practices.md).
>
>

## <a name="watch-the-dashboard-makeover-webinarhttpsinfomicrosoftcomco-powerbi-wbnr-fy16-05may-12-dashboard-makeover-registrationhtml"></a>Veja o [webinar Makeover de Dashboard](https://info.microsoft.com/CO-PowerBI-WBNR-FY16-05May-12-Dashboard-Makeover-Registration.html)
Consulte o Gestor de Programas Principal da Microsoft e especialista de dashboards do Power BI, Marc Reguera [realizar makeovers de dashboard](https://info.microsoft.com/CO-PowerBI-WBNR-FY16-05May-12-Dashboard-Makeover-Registration.html).

## <a name="consider-your-audience"></a>Considerar o público-alvo
Quais são as principais métricas que ajudarão a tomar decisões? Como será utilizado o dashboard? Que suposições aprendidas ou culturais podem afetar as opções de design? De que informações o público-alvo precisa para ser bem-sucedido?

Não se esqueça de que um dashboard é uma descrição geral, um local para monitorizar o estado atual dos dados. O dashboard é baseado em conjuntos de dados e relatórios subjacentes, e pode conter muitos detalhes. Os leitores podem explorar os relatórios a partir do seu dashboard. Assim, não coloque detalhes no dashboard, a menos que seja o que os leitores precisam de monitorizar.

Onde será apresentado o dashboard? Se for apresentado num monitor grande, pode colocar mais conteúdo. Se os leitores o visualizarem em tablets, menos mosaicos serão mais legíveis.

## <a name="tell-a-story-and-keep-it-to-one-screen"></a>Contar uma história e mantê-la no ecrã
Uma vez que os dashboards devem mostrar informações importantes rapidamente, é melhor ter todos os mosaicos num único ecrã. Pode evitar barras de deslocamento no seu dashboard?

O dashboard está muito confuso?  Remova todas as informações que não são essenciais que podem ser facilmente lidas e interpretadas.

## <a name="make-use-of-full-screen-mode"></a>Utilizar o modo de ecrã inteiro
Mostre o seu dashboard em [ecrã inteiro](consumer/end-user-focus.md) sem distrações.

## <a name="make-the-most-important-information-biggest"></a>Adicionar as informações mais importantes
Se o texto e as visualizações no dashboard forem do mesmo tamanho, os leitores terão dificuldade em se concentrar no que é mais importante. Por exemplo, as visualizações de cartão são uma boa forma de apresentar um número importante em destaque:  
![Visualização de cartão](media/service-dashboards-design-tips/pbi_card.png)

Mas não se esqueça de fornecer contexto.  

Saiba mais sobre [criar um mosaico apenas com um número](visuals/power-bi-visualization-card.md).

## <a name="put-the-most-important-information-in-the-upper-corner"></a>Colocar as informações mais importantes no canto superior
A maioria das pessoas leem de cima para baixo, pelo que deve colocar o nível mais alto de detalhes na parte superior e mostrar mais detalhes à medida que se move na direção que o público-alvo utiliza para ler (da esquerda para a direita, da direita para a esquerda).

## <a name="use-the-right-visualization-for-the-data-and-format-it-for-easy-reading"></a>Utilizar a visualização correta para os dados e formatá-la para leitura facilitada
Evite várias visualizações.  As visualizações devem ter uma visão geral e serem fáceis de "ler" e interpretar.  Para alguns dados e visualizações, uma visualização gráfica simples é suficiente. No entanto, outros dados podem exigir uma visualização mais complexa. Certifique-se de que utiliza títulos, etiquetas e outras personalizações para ajudar o leitor.  

* [Escolha visualizações de dados apropriadas](https://www.youtube.com/watch?v=-tdkUYrzrio). Tenha cuidado ao utilizar gráficos que distorçam a realidade, ou seja, gráficos em 3D. Não se esqueça de que é difícil para o cérebro humano interpretar formas circulares. Gráficos circulares, gráficos em anel, medidores e outros tipos de gráficos circulares podem parecer muito bonitos, mas não são uma prática recomendada de visualização de dados.
* Seja consistente com escalas de gráfico de eixos, ordenação da dimensão do gráfico e também com as cores utilizadas para os valores de dimensão nos gráficos.
* Certifique-se de que codifica corretamente os dados quantitativos. Não exceda três ou quatro dígitos quando apresentar números. Apresente medidas com um ou dois números à esquerda da vírgula decimal e escala de milhares ou milhões, ou seja 3,4 milhões e não 3.400.000.
* Não misture os níveis de precisão e tempo. Certifique-se de que os períodos de tempo são bem compreendidos.  Não é necessário um gráfico com o mês passado ao lado de gráficos filtrados de um determinado mês do ano.
* Não misture medidas grandes e pequenas na mesma escala, como um gráfico de linhas ou de barras.  Por exemplo, uma medida pode estar em milhões e outras medidas em milhares.  Com uma escala grande, seria difícil ver as diferenças da medida que está em milhares.  Se precisar de combinar, escolha uma visualização que permita a utilização de um segundo eixo.
* Não sobrecarregue os gráficos com etiquetas de dados desnecessárias. Os valores em gráficos de barras são normalmente bem compreendidos sem apresentar o número real.
* Preste atenção a como [os gráficos são ordenados](consumer/end-user-change-sort.md).  Se quiser chamar a atenção para o número mais alto ou mais baixo, ordene pela medida.  Se quiser que as pessoas localizem rapidamente uma categoria específica de entre muitas outras categorias, ordene pelo eixo.  
* Os gráficos circulares são recomendados se tiverem menos de oito categorias. Uma vez que não pode comparar valores lado a lado, é mais difícil comparar valores num gráfico circular do que em gráficos de barras e colunas. Os gráficos circulares pode ser bons para ver relações de parte a um todo em vez de comparar as partes. Os gráficos de medidor são ótimos para apresentar o estado atual no contexto de um objetivo.

Para obter instruções específicas de visualização, consulte [Tipos de visualização no Power BI](visuals/power-bi-visualization-types-for-reports-and-q-and-a.md).  

## <a name="learning-more-about-best-practice-dashboard-design"></a>Saber Mais sobre a Melhor Prática para Criação de Dashboards
Para dominar a arte da excelente criação de dashboards, considere aprender os Princípios básicos de Gestalt de percepção visual e como comunicar claramente as informações acionáveis no contexto. Felizmente, existe um número infinito de recursos já amplamente disponíveis e espalhados nos nossos blogues. Alguns dos nossos livros favoritos incluem:

* *Information Dashboard Design* de Stephen Few  
* *Show Me the Numbers* de Stephen Few  
* *Now You See It* de Stephen Few  
* *Envisioning Information* de Edward Tufte  
* *Advanced Presentations* by Design de Andrew Abela   

## <a name="next-steps"></a>Próximos passos
[Criar um dashboard a partir de um relatório](service-dashboard-create.md)  
[Power BI - Conceitos Básicos](consumer/end-user-basic-concepts.md)  
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)
