---
title: Elementos visuais personalizados no Power BI
description: Visualizações personalizadas no Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 12/18/2018
LocalizationGroup: Visualizations
ms.openlocfilehash: 0d634d7fc7753f7aaaf7d7118cfad1ab90b6e82a
ms.sourcegitcommit: c09241803664643e1b2ba0c150e525e1262ca466
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54072250"
---
# <a name="custom-visuals-in-power-bi"></a>Elementos visuais personalizados no Power BI

Ao criar ou editar um relatório no Power BI, existem vários tipos diferentes de visuais disponíveis para utilizar. Estes visuais são apresentados no painel **Visualizações**. Quando transfere o [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/) ou abre o [serviço Power BI](https://app.powerbi.com), este conjunto de elementos visuais vem "pré-embalado".

![visualizações](media/power-bi-custom-visuals/power-bi-visualizations.png)

No entanto, não está limitado a este conjunto de elementos visuais. Selecionar as reticências abre outra fonte de elementos visuais de relatórios, os *visuais personalizados*.

Os elementos visuais personalizados são criados pelos programadores, através do SDK dos elementos visuais personalizados, para permitir que os utilizadores empresariais vejam os seus dados de uma forma que melhor se adequa à empresa. Os autores do relatório podem, em seguida, importar os ficheiros dos elementos visuais personalizados para os relatórios e utilizá-los como quaisquer outros elementos visuais do Power BI. Os elementos visuais personalizados são cidadãos de primeira classe no Power BI e podem ser filtrados, realçados, editados, partilhados, etc.

Os elementos visuais personalizados podem ter o formato de três canais de implementação:

* Ficheiros de elementos visuais personalizados
* Elementos visuais da organização
* Elementos visuais do Marketplace

## <a name="custom-visual-files"></a>Ficheiros de elementos visuais personalizados

Os elementos visuais personalizados são pacotes que incluem código para compor os dados que são lhes enviados. Qualquer pessoa pode criar um elemento visual personalizado e criar um pacote do mesmo como um ficheiro `.pbiviz` único, que pode ser importado para um relatório do Power BI.

> [!WARNING]
> Um elemento visual personalizado pode conter código com riscos de privacidade ou de segurança. Garanta que confia no autor e na origem do elemento visual personalizado antes de o importar para o relatório.

## <a name="organizational-visuals"></a>Elementos visuais da organização

Os administradores do Power BI podem implementar elementos visuais personalizados na organização para que os autores de relatório possam facilmente detetar e utilizar os elementos visuais personalizados que o administrador aprovou para utilização na organização. Assim, o administrador tem controlo para selecionar os elementos visuais personalizados específicos a implementar na organização, bem como uma forma fácil de gerir (por exemplo, atualizar a versão, desativar/ativar) os mesmos. Para o autor do relatório, é uma forma fácil para detetar os elementos visuais que são exclusivos à organização, bem como um suporte totalmente integrado para atualizar esses elementos visuais.

Para obter mais informações sobre esses elementos visuais personalizados de organizações, [leia mais sobre os elementos visuais organizacionais](power-bi-custom-visuals-organization.md).

## <a name="marketplace-visuals"></a>Elementos visuais do Marketplace

Os membros da comunidade, bem como a Microsoft, contribuíram com os seus elementos visuais personalizados para o benefício do público e publicaram-nos no marketplace [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals). Estes visuais podem ser transferidos e adicionados a relatórios do Power BI. Todos estes elementos visuais personalizados foram testados e aprovados pela Microsoft ao nível da funcionalidade e da qualidade.

O que é o [AppSource](developer/office-store.md)? É o local onde se encontram as aplicações, os suplementos e as extensões para o seu software da Microsoft. O [AppSource](https://appsource.microsoft.com/en-us/) liga milhões de utilizadores de produtos como o Office 365, Azure, Dynamics 365, Cortana e Power BI a soluções que os ajudam a trabalhar com mais eficácia, mais informações e melhores visuais.

### <a name="certified-visuals"></a>Elementos visuais certificados

Os elementos visuais certificados do Power BI são elementos visuais do marketplace que passaram testes rigorosos adicionais ao nível da qualidade e são suportados em cenários adicionais, tais como [subscrições de e-mails](https://docs.microsoft.com/power-bi/service-report-subscribe) e [exportar para o PowerPoint](https://docs.microsoft.com/power-bi/service-publish-to-powerpoint).
Para ver a lista de visuais personalizados certificados ou para submeter o seu, consulte [Visuais personalizados certificados](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified).

É um programador Web e está interessado em criar as suas próprias visualizações e adicioná-las ao AppSource? Veja [Desenvolver um elemento visual personalizado do Power BI](developer/custom-visual-develop-tutorial.md) e saiba como [publicar elementos visuais personalizados no AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals).

### <a name="import-a-custom-visual-from-a-file"></a>Importar um elemento visual personalizado de um ficheiro

1. Selecione as reticências na parte inferior do painel Visualizações.

    ![visualizações2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. No menu pendente, selecione **Importar do ficheiro**.

    ![importar do ficheiro](media/power-bi-custom-visuals/power-bi-custom-visual-import-from-file.png)

3. No menu Abrir ficheiro, selecione o ficheiro `.pbiviz` que pretende importar e, em seguida, selecione Abrir. O ícone do visual personalizado é adicionado à parte inferior do seu painel Visualizações e fica agora disponível para utilizar no seu relatório.

    ![elemento visual certificado importado](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="import-organizational-visuals"></a>Importar elementos visuais da organização

1. Selecione as reticências na parte inferior do painel Visualizações.

    ![organização de elementos visuais 1](media/power-bi-custom-visuals/power-bi-visual-org-01.png)

2. No menu pendente, selecione Importar do marketplace.

    ![organização de elementos visuais 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Selecione **A MINHA ORGANIZAÇÃO** no menu do separador superior.

    ![organização de elementos visuais 3](media/power-bi-custom-visuals/power-bi-visual-org-03.png)

4. Percorra a lista para encontrar o visual a importar.

    ![organização de elementos visuais 4](media/power-bi-custom-visuals/power-bi-visual-org-04.png)

5. Importe o visual personalizado ao selecionar **Adicionar**. O ícone do visual personalizado é adicionado à parte inferior do seu painel Visualizações e fica agora disponível para utilizar no seu relatório.

    ![organização de elementos visuais 5](media/power-bi-custom-visuals/power-bi-visual-org-05.png)

## <a name="download-or-import-custom-visuals-from-microsoft-appsource"></a>Transferir ou importar visuais personalizados do Microsoft AppSource

Tem duas opções para transferir e importar visuais personalizados: do Power BI e do site do AppSource.

### <a name="import-custom-visuals-from-within-power-bi"></a>Importar visuais personalizados do Power BI

1. Selecione as reticências na parte inferior do painel Visualizações.

    ![visualizações 2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. No menu pendente, selecione **Importar do marketplace**.

    ![organização de elementos visuais 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Percorra a lista para encontrar o visual a importar.

    ![importar elemento visual](media/power-bi-custom-visuals/power-bi-import-visual.png)

4. Para saber mais sobre um dos visuais, realce-o e selecione-o.

    ![Selecionar](media/power-bi-custom-visuals/power-bi-select.png)

5. Na página de detalhes, pode ver capturas de ecrã, vídeos, descrições detalhadas e muito mais.

    ![Sinóptico](media/power-bi-custom-visuals/power-bi-synoptic.png)

6. Desloque-se até à parte inferior para ver críticas.

    ![Revisões](media/power-bi-custom-visuals/power-bi-reviews.png)

7. Importe o elemento visual personalizado ao selecionar Adicionar. O ícone do visual personalizado é adicionado à parte inferior do seu painel Visualizações e fica agora disponível para utilizar no seu relatório.

    ![elemento visual importado](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="download-and-import-custom-visuals-from-microsoft-appsource"></a>Transferir e importar visuais personalizados do Microsoft AppSource

1. Comece no [Microsoft AppSource](https://appsource.microsoft.com) e selecione o separador de **Aplicações**.

    ![AppSource](media/power-bi-custom-visuals/power-bi-appsource-apps.png)

2. Aceda à [Página de resultados de aplicações](https://appsource.microsoft.com/en-us/marketplace/apps), onde pode ver as principais aplicações em cada categoria, incluindo *Aplicações do Power BI*. Como estamos à procura de visuais personalizados, vamos filtrar os resultados ao selecionar **Visuais do Power BI** na lista de navegação à esquerda.

    ![elementos visuais do AppSource](media/power-bi-custom-visuals/power-bi-appsource-visuals.png)

3. O AppSource mostra um mosaico para cada visual personalizado.  Cada mosaico tem um instantâneo do visual personalizado e indica uma breve descrição e uma ligação de transferência. Para ver mais detalhes, selecione o mosaico.

    ![Selecionar Elemento Visual Personalizado](media/power-bi-custom-visuals/powerbi-custom-select-visual.png)

4. Na página de detalhes, pode ver capturas de ecrã, vídeos, descrições detalhadas e muito mais. Transfira o elemento visual personalizado ao selecionar **Obter agora** e aceitar os Termos de Utilização.

    ![Obter no AppSource](media/power-bi-custom-visuals/power-bi-appsource-get.png)

5. Selecione a ligação para transferir o visual personalizado.

    ![Transferir](media/power-bi-custom-visuals/powerbi-custom-download.png)

    A página de transferência também inclui instruções para importar o elemento visual personalizado para o Power BI Desktop e para o serviço Power BI.

    Pode também transferir um relatório de exemplo que inclui o elemento visual personalizado e demonstra as capacidades do mesmo.

    ![Experimentar Relatório de Exemplo](media/power-bi-custom-visuals/powerbi-custom-try-sample.png)

6. Guarde o ficheiro ".pbiviz" e, em seguida, abra o Power BI.

7. Importe o ficheiro ".pbiviz" para o relatório (Veja a secção [Importar um elemento visual personalizado de um ficheiro](#import-a-custom-visuals-from-a-file) acima)

## <a name="considerations-and-limitations"></a>Considerações e limitações

* Um elemento visual personalizado é adicionado a um relatório específico, quando importado. Se pretender utilizar o elemento visual noutro relatório, terá de importá-lo também para esse relatório. Quando um relatório com um visual personalizado é guardado através da opção **Guardar Como**, uma cópia do visual personalizado será guardada com o novo relatório.

* Se não vir um painel **Visualizações**, significa que não tem permissões de edição para o relatório.  Só pode adicionar visuais personalizados a relatórios que pode editar, não a relatórios que foram partilhados consigo.

## <a name="troubleshoot"></a>Resolução de Problemas

Para obter mais informações sobre resoluções de problemas, aceda a [Troubleshooting your Power BI custom visuals](power-bi-custom-visuals-troubleshoot.md) (Resolver problemas com os elementos visuais personalizados do Power BI).

## <a name="faq"></a>PERGUNTAS FREQUENTES

Para obter mais informações e respostas a perguntas, aceda às [Perguntas frequentes sobre os elementos visuais personalizados do Power BI](power-bi-custom-visuals-faq.md#organizational-custom-visuals).

## <a name="next-steps"></a>Próximos passos

* [Visualizações no Power BI](visuals/power-bi-report-visualizations.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/).
