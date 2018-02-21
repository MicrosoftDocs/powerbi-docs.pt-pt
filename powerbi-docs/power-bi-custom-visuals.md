---
title: "Visualizações personalizadas no Power BI"
description: "Visualizações personalizadas no Power BI"
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 02/06/2018
ms.author: maghan
ms.openlocfilehash: 72c4c0e3a177f83582677113b1c349a6ae295428
ms.sourcegitcommit: ad9bd4e52471b1179f46f847960d5ed79c0c0761
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/11/2018
---
# <a name="custom-visuals-in-power-bi"></a>Elementos visuais personalizados no Power BI
Ao criar ou editar um relatório no Power BI, existem vários tipos diferentes de visuais disponíveis para utilizar. Estes visuais são apresentados no painel **Visualizações**. Quando transfere o Power BI Desktop ou abre o serviço Power BI (app.powerbi.com), este conjunto de visuais vem "pré-embalado".

![](media/power-bi-custom-visuals/power-bi-visualizations.png)

No entanto, não está limitado a este conjunto de visuais. Selecionar as reticências abre outra fonte de visuais de relatórios: *visuais personalizados*.

Os elementos visuais personalizados são criados pelos programadores, através do SDK dos elementos visuais personalizados, para permitir que os utilizadores empresariais vejam os seus dados de uma forma que melhor se adequa à empresa. Os autores do relatório podem, em seguida, importar os ficheiros dos elementos visuais personalizados para os relatórios e utilizá-los como quaisquer outros elementos visuais do Power BI. Os elementos visuais personalizados são cidadãos de 1.ª classe no Power BI e podem ser filtrados, realçados, editados, partilhados, etc.

Os elementos visuais personalizados podem ter o formato de três canais de implementação:
* Ficheiros de elementos visuais personalizados
* Elementos visuais da organização
* Elementos visuais do Marketplace

## <a name="custom-visual-files"></a>Ficheiros de elementos visuais personalizados

Os elementos visuais personalizados são pacotes que incluem código para compor os dados que são lhes enviados. Qualquer pessoa pode criar um elemento visual personalizado e criar um pacote do mesmo como um ficheiro .pbiviz único, que pode ser importado para um relatório do Power BI.

> [!WARNING]
> Um elemento visual personalizado pode conter código com riscos de privacidade ou de segurança. Garanta que confia no autor e na origem do elemento visual personalizado antes de o importar para o relatório.
> 
> 

## <a name="organization-visuals-preview"></a>Elementos visuais da organização (Pré-visualização)

Os administradores do Power BI podem implementar elementos visuais personalizados na organização para que os autores de relatório possam facilmente detetar e utilizar os elementos visuais personalizados que o administrador aprovou para utilização na organização. Deste modo, proporciona ao administrador o controlo para escolher os elementos visuais personalizados específicos a implementar na organização, bem como uma forma fácil de gerir (ou seja, atualizar a versão, desativar/ativar) esses elementos visuais. Para o autor do relatório, é uma forma fácil para detetar os elementos visuais que são exclusivos à organização, bem como um suporte totalmente integrado para atualizar esses elementos visuais.

Para obter mais informações sobre esses elementos visuais personalizados de organização, [leia mais sobre os elementos visuais organizacionais](power-bi-custom-visuals-organization.md).

## <a name="marketplace-visuals"></a>Elementos visuais do Marketplace

Os membros da comunidade, bem como a Microsoft, contribuíram com os seus elementos visuais personalizados para o benefício do público e publicaram-nos no marketplace [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals). Estes visuais podem ser transferidos e adicionados a relatórios do Power BI. Todos estes elementos visuais personalizados foram testados e aprovados pela Microsoft ao nível da funcionalidade e da qualidade.

O que é o AppSource? Em termos simples, é o local onde se encontram as aplicações, os suplementos e as extensões para o seu software da Microsoft. O [AppSource](https://appsource.microsoft.com/en-us/) liga milhões de utilizadores de produtos como o Office 365, Azure, Dynamics 365, Cortana e Power BI a soluções que os ajudam a trabalhar com mais eficácia, mais informações e melhores visuais.

### <a name="certified-visuals"></a>Elementos visuais certificados

Os elementos visuais certificados do Power BI são elementos visuais do marketplace que passaram testes rigorosos adicionais ao nível da qualidade e são suportados em cenários adicionais, tais como [subscrições de e-mails](https://docs.microsoft.com/en-us/power-bi/service-report-subscribe) e [exportar para o PowerPoint](https://docs.microsoft.com/en-us/power-bi/service-publish-to-powerpoint).
Para ver a lista de visuais personalizados certificados ou para submeter o seu, consulte [Visuais personalizados certificados](https://docs.microsoft.com/en-us/power-bi/power-bi-custom-visuals-certified).

É um programador Web e está interessado em criar as suas próprias visualizações e adicioná-las ao AppSource? Consulte [Introdução às Ferramentas de Programação](https://docs.microsoft.com/en-us/power-bi/service-custom-visuals-getting-started-with-developer-tools) e saiba como [publicar visuais personalizados no AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals).

### <a name="import-a-custom-visuals-from-a-file"></a>Importar elementos visuais personalizados de um ficheiro

1. Selecione as reticências na parte inferior do painel Visualizações.

    ![](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. No menu pendente, selecione **Importar do ficheiro**.

    ![](media/power-bi-custom-visuals/power-bi-custom-visual-import-from-file.png)

3. No menu Abrir ficheiro, selecione o ficheiro .pbiviz que quer importar e, em seguida, selecione Abrir. O ícone do visual personalizado é adicionado à parte inferior do seu painel Visualizações e fica agora disponível para utilizar no seu relatório.

    ![](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="import-organization-visuals"></a>Importar elementos visuais da organização

1. Selecione as reticências na parte inferior do painel Visualizações.

    ![](media/power-bi-custom-visuals/power-bi-visual-org-01.png)

2. No menu pendente, selecione Importar do marketplace.

    ![](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Selecione **A MINHA ORGANIZAÇÃO** no menu do separador superior.

    ![](media/power-bi-custom-visuals/power-bi-visual-org-03.png)

4. Percorra a lista para encontrar o visual a importar.
    
    ![](media/power-bi-custom-visuals/power-bi-visual-org-04.png)

5. Importe o visual personalizado ao selecionar **Adicionar**. O ícone do visual personalizado é adicionado à parte inferior do seu painel Visualizações e fica agora disponível para utilizar no seu relatório.

    ![](media/power-bi-custom-visuals/power-bi-visual-org-05.png)
 
## <a name="download-or-import-custom-visuals-from-microsoft-appsource"></a>Transferir ou importar visuais personalizados do Microsoft AppSource
Tem duas opções para transferir e importar visuais personalizados: do Power BI e do site do AppSource.

### <a name="import-custom-visuals-from-within-power-bi"></a>Importar visuais personalizados do Power BI

1. Selecione as reticências na parte inferior do painel Visualizações.

    ![](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. No menu pendente, selecione **Importar do marketplace**.

    ![](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Percorra a lista para encontrar o visual a importar.

    ![](media/power-bi-custom-visuals/power-bi-import-visual.png)

4. Para saber mais sobre um dos visuais, realce-o e selecione-o.

    ![](media/power-bi-custom-visuals/power-bi-select.png)

5. Na página de detalhes, pode ver capturas de ecrã, vídeos, descrições detalhadas e muito mais.

    ![](media/power-bi-custom-visuals/power-bi-synoptic.png)

6. Desloque-se até à parte inferior para ver críticas.

    ![](media/power-bi-custom-visuals/power-bi-reviews.png)

7. Importe o elemento visual personalizado ao selecionar Adicionar. O ícone do visual personalizado é adicionado à parte inferior do seu painel Visualizações e fica agora disponível para utilizar no seu relatório.

    ![](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="download-and-import-custom-visuals-from-microsoft-appsource"></a>Transferir e importar visuais personalizados do Microsoft AppSource

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

7. Importe o ficheiro .pbiviz para o relatório (Veja a secção [Importar um elemento visual personalizado de um ficheiro](#import-a-custom-visuals-from-a-file) acima)

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas

- Um elemento visual personalizado é adicionado a um relatório específico, quando importado. Se pretender utilizar o elemento visual noutro relatório, terá de importá-lo também para esse relatório. Quando um relatório com um visual personalizado é guardado através da opção **Guardar Como**, uma cópia do visual personalizado será guardada com o novo relatório.

- Se não vir um painel **Visualizações**, significa que não tem permissões de edição para o relatório.  Só pode adicionar visuais personalizados a relatórios que pode editar, não a relatórios que foram partilhados consigo.

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)