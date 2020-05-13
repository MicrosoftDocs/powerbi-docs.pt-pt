---
title: Criar análises e visualizações avançadas com scripts R
description: Utilizar scripts R no Power BI Desktop para criar análises e visualizações avançadas
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/14/2019
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: a7de3dfbbd378ea96f56c1d6d37d273434f5c2f9
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83349822"
---
# <a name="create-and-use-r-visuals-in-power-bi"></a>Criar e utilizar elementos visuais R no Power BI Desktop

[!INCLUDE[consumer-appliesto-nnyn](../includes/consumer-appliesto-nnyn.md)]

Atualmente, os elementos visuais R só podem ser criados no **Power BI Desktop** e publicados no serviço Power BI. Para obter mais informações sobre a criação de elementos visuais R, veja [Criar elementos visuais do Power BI com o R](../create-reports/desktop-r-visuals.md).

## <a name="viewing-r-visuals-in-the-power-bi-service"></a>Ver elementos visuais R no serviço Power BI
O serviço Power BI suporta a visualização e interação com elementos visuais criados com scripts R. Os elementos visuais criados com scripts R, geralmente denominados *elementos visuais R*, podem apresentar formação e análise de dados avançadas, como previsão, ao utilizar o poder avançado de análise e visualização da linguagem R.

> [!NOTE]
> A [linguagem de programação R](https://www.r-project.org/) é uma das linguagens mais utilizadas por estatísticos, cientistas de dados e analistas de negócio. A linguagem R tem uma comunidade de código aberto que disponibiliza mais de 7000 pacotes de suplementos, bem como os muito utilizados Grupos de Utilizadores de R. A versão da linguagem R implementada no serviço Power BI é a *Microsoft R 3.4.4.* .
> 
> 

A imagem seguinte mostra um dashboard do Power BI com uma coleção de elementos visuais R utilizados para análise avançada.

![Captura de ecrã a mostrar a tela de relatório do serviço Power BI](media/service-r-visuals/power-bi-r-visuals.png)

Os elementos visuais R são criados num [relatório do Power BI Desktop](../fundamentals/desktop-get-the-desktop.md), tal como o relatório mostrado na imagem seguinte.

![Relatório de Ambiente de trabalho com dois elementos visuais](media/service-r-visuals/power-bi-r-visual-desktop.png)

Assim que o relatório for criado no **Power BI Desktop**, pode publicar o relatório que contém um ou mais elementos visuais R no serviço Power BI. 

 Tenha em atenção que o serviço não suporta todos os pacotes R. Obtenha a lista de pacotes atualmente suportados no serviço Power BI no final deste artigo.

Pode transferir este [ficheiro de exemplo do Power BI Desktop](https://download.microsoft.com/download/D/9/A/D9A65269-D1FC-49F8-8EC3-1217E3A4390F/RVisual_correlation_plot_sample%20SL.pbix) (ficheiro .pbix) que contém alguns elementos visuais R para ver como tudo funciona e experimentar.

Os elementos visuais R criados no **Power BI Desktop** e publicados no serviço Power BI, na maior parte dos casos, comportam-se como qualquer outro elemento visual no serviço Power BI; pode interagir, filtrar, dividir por setores e afixar a um dashboard ou partilhá-los com outras pessoas. Para obter mais informações sobre como partilhar dashboards e elementos visuais, veja [Partilhar um dashboard com colegas e outras pessoas](../collaborate-share/service-share-dashboards.md). Uma diferença dos outros elementos visuais é que os elementos visuais R não podem mostrar sugestões nem ser utilizados para filtrar outros elementos visuais.

Como pode ver na imagem seguinte, os elementos visuais R no serviço Power BI, em dashboards ou relatórios, na sua maioria, são apresentados e comportam-se como qualquer outro elemento visual e os utilizadores não precisam de considerar o script R subjacente que criou o elemento visual.

![captura de ecrã da página de relatório no serviço Power BI](media/service-r-visuals/power-bi-r-visual.png)

## <a name="r-scripts-security"></a>Segurança dos scripts R
Os elementos visuais R são criados a partir de scripts R, os quais podem conter potencialmente código com riscos de segurança ou privacidade.

Estes riscos existem principalmente na fase de criação, quando o autor do script executa o script no seu próprio computador.

O serviço Power BI aplica uma tecnologia de *sandbox* para proteger os utilizadores e o serviço de riscos de segurança.

Esta abordagem de *sandbox* impõe algumas restrições aos scripts R em execução no serviço Power BI, tais como aceder à Internet ou a outros recursos que não têm de criar o elemento visual R.

## <a name="r-scripts-error-experience"></a>Experiência de erro de scripts R
Quando um script R encontra um erro, o elemento visual R não é desenhado e é apresentada uma mensagem de erro. Para obter detalhes sobre o erro, selecione **Ver detalhes** no erro do elemento visual R na tela, conforme mostrado na imagem seguinte.

![mensagem de erro](media/service-r-visuals/r-visuals-service-4.png)

Como outro exemplo, a imagem seguinte mostra a mensagem de erro apresentada quando um script R não foi executado corretamente devido a um pacote R em falta no Azure.

![Captura de ecrã a mostrar um erro de runtime](media/service-r-visuals/r-visuals-service-5.png)

## <a name="licensing"></a>Licenciamento
Os elementos visuais R requerem uma licença do [Power BI Pro](../fundamentals/service-self-service-signup-for-power-bi.md) para composição em relatórios, atualização, filtro e filtro cruzado. Para obter mais informações sobre as licenças do Power BI Pro e como diferem das licenças gratuitas, veja [Conteúdo do Power BI Pro - o que é isto?](../admin/service-admin-purchasing-power-bi-pro.md)

Os utilizadores gratuitos do Power BI só podem consumir mosaicos partilhados com os próprios nas áreas de trabalho Premium. Para obter mais informações, veja [Comprar o Power BI Pro](../admin/service-admin-purchasing-power-bi-pro.md).

A tabela seguinte descreve as capacidades dos elementos visuais R com base no licenciamento.


|  |Criar elementos visuais R no Power BI Desktop  | Criar relatórios de serviço do PBI com visuais R |Ver visuais R em relatórios  | Ver mosaicos R em dashboards |
|---------|---------|---------|---------|--------|
|**Convidado** (Power BI Embedded)     |  Suportado|  Não suportado      | Suportado apenas na capacidade Premium/Azure  | Suportado apenas na capacidade Premium/Azure |
|**Inquilino não gerido** (domínio não verificado) | Suportado | Não suportado |  Não suportado |Suportado (cenário B2B) |
|**Inquilino gerido** com uma licença gratuita    |  Suportado       |  Não suportado       |    Suportado apenas na capacidade Premium    | Suportado |
**Inquilino gerido** com uma licença Pro     |   Suportado      | Suportado      | Suportado    |Suportado|



## <a name="known-limitations"></a>Limitações Conhecidas
Os elementos visuais R no serviço Power BI têm algumas limitações:

* O suporte para os elementos visuais R está limitado aos pacotes identificados em [Saiba quais os pacotes R suportados](../connect-data/service-r-packages-support.md). Atualmente, não existe suporte de pacotes personalizados.
* Limitações de tamanho de dados – os dados utilizados pelo elemento visual R para desenhar têm um limite de 150 000 linhas. Se forem selecionadas mais de 150 000 linhas, apenas as primeiras 150 000 linhas serão utilizadas e será apresentada uma mensagem na imagem. Além disso, os dados de entrada têm um limite de 250 MB.
* Resolução – todos os elementos visuais R são apresentados a 72 DPI.
* Dispositivo de desenho – só é suportado o desenho para o dispositivo predefinido. 
* Limite de tempo de cálculo – se um cálculo do elemento visual R exceder 60 segundos, o script atinge o tempo limite, resultando num erro.
* Os elementos visuais R são atualizados após atualizações de dados, filtragem e realce. No entanto, a imagem propriamente dita não é interativa e não suporta sugestões.
* Os elementos visuais R respondem ao realce de outros elementos visuais, mas não pode clicar em elementos no elemento visual R para fazer filtragem cruzada de outros elementos.
* Os elementos visuais R não são atualmente suportados para o tipo de dados *Tempo*. Em vez disso, utilize Data/Hora.
* Os elementos visuais R não são apresentados quando utilizar **Publicar na Web**.
* Os elementos visuais R não suportam a mudança de nome de colunas de entrada. As colunas serão referidas pelo seu nome original durante a execução do script.
* Atualmente, os elementos visuais R não são impressos a partir do dashboard e de relatórios
* Atualmente, os elementos visuais R não são suportados no modo DirectQuery do Analysis Services
* Os elementos visuais R têm a capacidade de converter etiquetas de texto em elementos gráficos. Para o fazer no serviço Power BI, é necessário o seguinte passo adicional:
  
  * Adicione a seguinte linha ao início do script R:
    
        powerbi_rEnableShowText =  1
* Os tipos de letra chinês, japonês e coreano requerem todos os passos adicionais seguintes para funcionar corretamente no serviço Power BI:
  
  * Primeiro, instale o pacote R *showtext* e todas as respetivas dependências. Pode fazê-lo ao executar o seguinte script:
    
        *install.packages("showtext")*
  * Em seguida, adicione a seguinte linha ao início do script R:
    
        powerbi_rEnableShowTextForCJKLanguages =  1

## <a name="overview-of-r-packages"></a>Descrição geral de pacotes R
Os pacotes R são coleções de funções R, dados e código compilado combinadas num formato bem definido. Quando a linguagem R estiver instalada, esta inclui um conjunto de pacotes padrão e estão disponíveis outros pacotes para transferência e instalação. Depois de instalados, os pacotes R têm de ser carregados para a sessão para serem utilizados. A origem principal dos pacotes R gratuitos é a CRAN, [Comprehensive R Archive Network](https://cran.r-project.org/web/packages/available_packages_by_name.html).

O **Power BI Desktop** pode utilizar qualquer tipo de pacote R sem limitação. Pode instalar pacotes R para utilização no **Power BI Desktop** (através do [RStudio IDE](https://www.rstudio.com/), por exemplo).

Os elementos visuais R no **serviço Power BI** são suportados pelos pacotes encontrados na secção **Pacotes Suportados** encontrada [neste artigo](../connect-data/service-r-packages-support.md). Se não encontrar um pacote que lhe interesse na lista de pacotes suportados, pode solicitar o suporte do pacote. Veja [Pacotes R no serviço Power BI](../connect-data/service-r-packages-support.md) para obter informações sobre como solicitar o suporte.

### <a name="requirements-and-limitations-of-r-packages"></a>Requisitos e Limitações de pacotes R
Existem alguns requisitos e limitações para pacotes R:

* O serviço Power BI suporta, na maioria das vezes, pacotes R com licenças de software gratuitas e open source, como GPL-2, GPL-3, MIT+, entre outros.
* O serviço Power BI suporta pacotes publicados na CRAN. O serviço não suporta pacotes R privados ou personalizados. Recomendamos aos utilizadores que disponibilizem os respetivos pacotes privadas na CRAN antes de solicitarem que o pacote esteja disponível no serviço Power BI.
* No **Power BI Desktop**, existem duas variações para pacotes R:
  
  * Para elementos visuais R, pode instalar qualquer pacote, incluindo pacotes R personalizados
  * Para elementos visuais R personalizados, apenas os pacotes CRAN públicos são suportados para instalação automática dos pacotes
* Por motivos de segurança e privacidade, atualmente não suportamos pacotes R que forneçam consultas de cliente-servidor através da Web (por exemplo, RgoogleMaps) no serviço. O funcionamento em rede é bloqueado para essas tentativas. Veja [Pacotes R no serviço Power BI](../connect-data/service-r-packages-support.md) para obter uma lista dos pacotes R suportados e não suportados.
* O processo de aprovação para incluir um novo pacote R tem uma árvore de dependências; algumas dependências que têm de ser instaladas no serviço não podem ser suportadas.

### <a name="supported-packages"></a>Pacotes Suportados:
Para obter uma longa lista de pacotes R suportados (e a pequena lista de pacotes não suportados), veja o seguinte artigo:

* [Pacotes R no serviço Power BI](../connect-data/service-r-packages-support.md)
