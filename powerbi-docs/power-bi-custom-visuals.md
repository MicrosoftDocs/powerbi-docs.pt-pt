---
title: "Visualizações personalizadas no Power BI"
description: "Visualizações personalizadas no Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/20/2017
ms.author: mihart
ms.openlocfilehash: c50b984cd8babc845dbe0223613e463a7a8ee76d
ms.sourcegitcommit: 12236d08c27c7ee3fabb7ef9d767e9dee693f8aa
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/21/2017
---
# <a name="custom-visuals-in-power-bi"></a>Elementos visuais personalizados no Power BI
Ao criar ou editar um relatório no Power BI, existem vários tipos diferentes de visuais disponíveis para utilizar. Estes visuais são apresentados no painel **Visualizações**. Quando transfere o Power BI Desktop ou abre o serviço Power BI (app.powerbi.com), este conjunto de visuais vem "pré-embalado". 

![](media/power-bi-custom-visuals/power-bi-visualizations.png)

No entanto, não está limitado a este conjunto de visuais. Selecionar as reticências abre outra fonte de visuais de relatórios: *visuais personalizados*.

Os visuais personalizados são criados pelos membros da comunidade e pela Microsoft e estão alojados no [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals). Estes visuais podem ser transferidos e adicionados a relatórios do Power BI. Todos estes visuais personalizados foram aprovados pela Microsoft e têm um comportamento semelhante às visualizações pré-embaladas incluídas no Power BI: podem ser filtrados, realçados, editados, partilhados, etc. 

O que é a AppSource? Em termos simples, é o local onde se encontram as aplicações, os suplementos e as extensões para o seu software da Microsoft. O [AppSource](https://appsource.microsoft.com) liga milhões de utilizadores de produtos como o Office 365, Azure, Dynamics 365, Cortana e Power BI a soluções que os ajudam a trabalhar com mais eficácia, mais informações e melhores visuais.

## <a name="two-types-of-custom-visuals"></a>Dois tipos de visuais personalizados

Os visuais personalizados do Power BI que estão disponíveis no AppSource enquadram-se em duas categorias: **aprovados** e **certificados**. Os visuais *aprovados para o AppSource* podem ser executados em browsers, relatórios e dashboards.  Os visuais *certificados para o Power BI* passaram testes rigorosos e são suportados em cenários adicionais, como [subscrições de e-mails](service-report-subscribe.md) e [exportar para PowerPoint](service-publish-to-powerpoint.md).

Para ver a lista de visuais personalizados certificados ou para submeter o seu, consulte [Visuais personalizados certificados](power-bi-custom-visuals-certified.md).

É um programador Web e está interessado em criar as suas próprias visualizações e adicioná-las ao AppSource?  Consulte [Introdução às Ferramentas de Programação](service-custom-visuals-getting-started-with-developer-tools.md) e saiba como [publicar visuais personalizados no AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals).

## <a name="download-or-import-custom-visuals-from-microsoft-appsource"></a>Transferir ou importar visuais personalizados do Microsoft AppSource
Tem duas opções para transferir e importar visuais personalizados: do Power BI e do site do AppSource. 

###    <a name="import-custom-visuals-from-within-power-bi"></a>Importar visuais personalizados do Power BI
1. Selecione as reticências na parte inferior do painel Visualizações. 

    ![](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. No menu pendente, selecione **Importar da loja**.

    ![](media/power-bi-custom-visuals/power-bi-custom-visual-import.png)

3. Percorra a lista para encontrar o visual a importar. 

    ![](media/power-bi-custom-visuals/power-bi-import-visual.png)

4.  Para saber mais sobre um dos visuais, realce-o e selecione-o.

    ![](media/power-bi-custom-visuals/power-bi-select.png)

5.  Na página de detalhes, pode ver capturas de ecrã, vídeos, descrições detalhadas e muito mais. 

    ![](media/power-bi-custom-visuals/power-bi-synoptic.png)

6. Desloque-se até à parte inferior para ver críticas.

    ![](media/power-bi-custom-visuals/power-bi-reviews.png)

7.    Importe o visual personalizado ao selecionar **Adicionar**. O ícone do visual personalizado é adicionado à parte inferior do seu painel Visualizações e fica agora disponível para utilizar no seu relatório.

       ![](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)


###    <a name="download-and-import-custom-visuals-from-microsoft-appsource"></a>Transferir e importar visuais personalizados do Microsoft AppSource

1. Comece no [Microsoft AppSource](https://appsource.microsoft.com) e selecione o separador de **Aplicações**. 

    ![](media/power-bi-custom-visuals/power-bi-appsource-apps.png)

2. Esta ação redireciona-o para a [Página de resultados de aplicações](https://appsource.microsoft.com/en-us/marketplace/apps), onde pode ver as principais aplicações em cada categoria, incluindo *Aplicações do Power BI*. Como estamos à procura de visuais personalizados, vamos filtrar os resultados ao selecionar **Visuais do Power BI** na lista de navegação à esquerda.

    ![](media/power-bi-custom-visuals/power-bi-appsource-visuals.png)

3. O AppSource mostra um mosaico para cada visual personalizado.  Cada mosaico tem um instantâneo do visual personalizado e indica uma breve descrição e uma ligação de transferência. Para ver mais detalhes, selecione o mosaico. 

    ![](media/power-bi-custom-visuals/powerbi-custom-select-visual.png)

4. Na página de detalhes, pode ver capturas de ecrã, vídeos, descrições detalhadas e muito mais. Transfira o visual personalizado ao selecionar **Obter agora** e aceitar os Termos de utilização. 

    ![](media/power-bi-custom-visuals/power-bi-appsource-get.png)

5. Selecione a ligação para transferir o visual personalizado.

    ![](media/power-bi-custom-visuals/powerbi-custom-download.png)

    A página de transferência também inclui instruções para importar o visual personalizado para o Power BI Desktop e para o serviço Power BI.

    Pode também transferir um relatório de exemplo que inclui o visual personalizado e demonstra as capacidades do mesmo.

    ![](media/power-bi-custom-visuals/powerbi-custom-try-sample.png)

6. Guarde o ficheiro .pbiviz e, em seguida, abra o Power BI.    
7. Abra o relatório onde pretende adicionar o visual personalizado e, na parte inferior do painel **Visualizações**, selecione as reticências > **Importar de ficheiro**.  

      ![](media/power-bi-custom-visuals/power-bi-custom-visual-import-from-file.png)

8. Selecione o ficheiro de visual personalizado para adicionar o ícone desse visual personalizado à parte inferior do seu painel **Visualizações**. Agora, o visual personalizado está disponível para utilização no seu relatório.

    ![](media/power-bi-custom-visuals/power-bi-chord.png)
    
##    <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas


- Um elemento visual personalizado é adicionado a um relatório específico, quando importado. Se pretender utilizar o elemento visual noutro relatório, terá de importá-lo também para esse relatório. Quando um relatório com um visual personalizado é guardado através da opção **Guardar Como**, uma cópia do visual personalizado será guardada com o novo relatório.

- Se não vir um painel **Visualizações**, significa que não tem permissões de edição para o relatório.  Só pode adicionar visuais personalizados a relatórios que pode editar, não a relatórios que foram partilhados consigo.


Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

