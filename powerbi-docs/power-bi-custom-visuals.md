---
title: Elementos visuais personalizados no Power BI
description: Visualizações personalizadas no Power BI
author: sranins
ms.author: rasala
manager: kfile
ms.reviewer: maghan
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: 3fd2f3e47c9b6dd2144ed5a66d45e65a00c5b92e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051247"
---
# <a name="custom-visuals-in-power-bi"></a>Elementos visuais personalizados no Power BI

Quando criar ou editar um relatório do Power BI, pode utilizar vários tipos de elementos visuais. Os ícones para estes elementos visuais são apresentados no **visualizações** painel. Estes elementos visuais são pré-embalado quando baixar [Power BI Desktop](https://powerbi.microsoft.com/desktop/) ou abrir o [serviço Power BI](https://app.powerbi.com).

![visualizações](media/power-bi-custom-visuals/power-bi-visualizations.png)

No entanto, não fica limitado a este conjunto de elementos visuais. Se selecionar as reticências (...) na parte inferior, outra origem de elementos visuais do relatório torna-se está disponível –*elementos visuais personalizados*.

Os programadores criar elementos visuais personalizados através dos SDK dos elementos visuais personalizados. Estes elementos visuais que os usuários vejam os seus dados de forma que melhor satisfaz os seus negócios. Os autores do relatório, em seguida, podem importar os ficheiros de visual personalizados para os relatórios e utilizá-los como faria com qualquer outros visuais do Power BI. Os elementos visuais personalizados são cidadãos de primeira classe no Power BI e podem ser filtrados, realçados, editados, partilhados e assim por diante.

Os elementos visuais personalizados são implementados de três formas:

* Ficheiros de elementos visuais personalizados
* Elementos visuais da organização
* Elementos visuais do Marketplace

## <a name="custom-visual-files"></a>Ficheiros de elementos visuais personalizados

Os elementos visuais personalizados são pacotes que incluem código para compor os dados lhes enviados. Qualquer pessoa pode criar um elemento visual personalizado e empacotá-lo como um único `.pbiviz` arquivo, que, em seguida, pode ser importado para um relatório do Power BI.

> [!WARNING]
> Um elemento visual personalizado pode conter código com riscos de privacidade ou segurança. Certifique-se de que confia no autor e na origem de visual personalizada antes de importá-lo ao seu relatório.

## <a name="organizational-visuals"></a>Elementos visuais da organização

Administradores do Power BI aprovar e implementar os elementos visuais personalizados na organização que os autores do relatório podem facilmente descobrir, atualizar e utilizar. Os administradores podem gerir facilmente (por exemplo, atualizar a versão, desativar/ativar) esses elementos visuais.

 [Saiba mais sobre os elementos visuais organizacionais](power-bi-custom-visuals-organization.md).

## <a name="marketplace-visuals"></a>Elementos visuais do Marketplace

Membros da Comunidade e a Microsoft tem contribuído seus elementos visuais personalizados para o benefício do público e publicaram-na [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) marketplace. Pode transferi-los elementos visuais adicioná-los aos seus relatórios do Power BI. A Microsoft testadas e aprovadas estes elementos visuais personalizados para a funcionalidade e qualidade.

O que é o [AppSource](developer/office-store.md)? É o local onde pode encontrar aplicações, suplementos e extensões para o seu software da Microsoft. [AppSource](https://appsource.microsoft.com/) liga milhões de utilizadores de produtos, como o Office 365, Azure, Dynamics 365, Cortana e Power BI, soluções que os ajudam a realizar o trabalho mais eficiente, inteligente e visuais que antes.

### <a name="certified-visuals"></a>Elementos visuais certificados

Os elementos visuais são elementos visuais do marketplace que passaram testes de qualidade rigorosa adicional e são suportados em cenários adicionais, tais como certificados do Power BI [subscrições de e-mails](https://docs.microsoft.com/power-bi/service-report-subscribe), e [exportar para PowerPoint](https://docs.microsoft.com/power-bi/service-publish-to-powerpoint).
Para ver a lista de visuais personalizados certificados ou para submeter o seu, consulte [Visuais personalizados certificados](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified).

É um programador Web e está interessado em criar as suas próprias visualizações e adicioná-las ao AppSource? Ver [desenvolver um visual personalizado do Power BI](developer/custom-visual-develop-tutorial.md) e saiba como [publicar elementos visuais personalizados no AppSource](https://docs.microsoft.com/power-bi/developer/office-store).

### <a name="import-a-custom-visual-from-a-file"></a>Importar um elemento visual personalizado de um ficheiro

1. Selecione as reticências na parte inferior a **visualizações** painel.

    ![visualizações2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. No menu pendente, selecione **Importar do ficheiro**.

    ![importar do ficheiro](media/power-bi-custom-visuals/power-bi-custom-visual-import-from-file.png)

3. No menu abrir o ficheiro, selecione o `.pbiviz` ficheiro que pretende importar e, em seguida, selecione **aberto**. Ícone do elemento visual personalizado é adicionado à parte inferior da sua **visualizações** painel e agora está disponível para utilização no seu relatório.

    ![elemento visual certificado importado](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="import-organizational-visuals"></a>Importar elementos visuais da organização

1. Selecione as reticências na parte inferior a **visualizações** painel.

    ![organização de elementos visuais 1](media/power-bi-custom-visuals/power-bi-visual-org-01.png)

2. No menu pendente, selecione **Importar do marketplace**.

    ![organização de elementos visuais 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Selecione **A MINHA ORGANIZAÇÃO** no menu do separador superior.

    ![organização de elementos visuais 3](media/power-bi-custom-visuals/power-bi-visual-org-03.png)

4. Percorra a lista para encontrar o visual a importar.

    ![organização de elementos visuais 4](media/power-bi-custom-visuals/power-bi-visual-org-04.png)

5. Selecione **adicionar** para importar o elemento visual personalizado. O ícone é adicionado à parte inferior da sua **visualizações** painel e agora está disponível para utilização no seu relatório.

    ![organização de elementos visuais 5](media/power-bi-custom-visuals/power-bi-visual-org-05.png)

## <a name="download-or-import-custom-visuals-from-microsoft-appsource"></a>Transferir ou importar visuais personalizados do Microsoft AppSource

Tem duas opções para transferir e importar visuais personalizados: do Power BI e do [Web site do AppSource](https://appsource.microsoft.com/).

### <a name="import-custom-visuals-from-within-power-bi"></a>Importar visuais personalizados do Power BI

1. Selecione as reticências na parte inferior a **visualizações** painel.

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

7. Selecione **adicionar** para importar o elemento visual personalizado. O ícone é adicionado à parte inferior da sua **visualizações** painel e agora está disponível para utilização no seu relatório.

    ![elemento visual importado](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="download-and-import-custom-visuals-from-microsoft-appsource"></a>Transferir e importar visuais personalizados do Microsoft AppSource

1. Comece no [Microsoft AppSource](https://appsource.microsoft.com) e selecione o separador de **Aplicações**.

    ![AppSource](media/power-bi-custom-visuals/power-bi-appsource-apps.png)

2. Aceda à [Página de resultados de aplicações](https://appsource.microsoft.com/marketplace/apps), onde pode ver as principais aplicações em cada categoria, incluindo *Aplicações do Power BI*. Estamos procurando os elementos visuais personalizados, vamos, então, selecione **visuais do Power BI** na lista de navegação à esquerda para limitar os resultados.

    ![elementos visuais do AppSource](media/power-bi-custom-visuals/power-bi-appsource-visuals.png)

3. O AppSource mostra um mosaico para cada visual personalizado.  Cada mosaico tem um instantâneo visual personalizado com uma breve descrição e uma ligação de transferência. Para ver mais detalhes, selecione o mosaico.

    ![Selecionar Elemento Visual Personalizado](media/power-bi-custom-visuals/powerbi-custom-select-visual.png)

4. Na página de detalhes, pode ver capturas de ecrã, vídeos, descrições detalhadas e muito mais. Selecione **obter agora** para transferir o elemento visual personalizado e, em seguida, aceitar os termos de utilização.

    ![Obter no AppSource](media/power-bi-custom-visuals/power-bi-appsource-get.png)

5. Selecione a ligação para transferir o visual personalizado.

    ![Transferir](media/power-bi-custom-visuals/powerbi-custom-download.png)

    A página de download também inclui instruções sobre como importar o elemento visual personalizado para o Power BI Desktop e o serviço Power BI.

    Pode também transferir um relatório de exemplo que inclui o elemento visual personalizado e demonstra as capacidades do mesmo.

    ![Experimentar Relatório de Exemplo](media/power-bi-custom-visuals/powerbi-custom-try-sample.png)

6. Guardar o `.pbiviz` de ficheiros e, em seguida, abra o Power BI.

7. Importar o `.pbiviz` ficheiro para o seu relatório. (Veja a secção [Importar um elemento visual personalizado de um ficheiro](#import-a-custom-visual-from-a-file) acima.)

## <a name="considerations-and-limitations"></a>Considerações e limitações

* Um elemento visual personalizado é adicionado a um relatório específico, quando importado. Se pretender utilizar o elemento visual noutro relatório, terá de importá-lo também para esse relatório. Quando um relatório com um visual personalizado é guardado através da opção **Guardar Como**, uma cópia do visual personalizado será guardada com o novo relatório.

* Se não vir um **visualizações** painel, o que significa que não tem permissões de edição do relatório.  Só pode adicionar visuais personalizados a relatórios que pode editar, não a relatórios que foram partilhados consigo.

## <a name="troubleshoot"></a>Resolução de Problemas

Para resolver problemas, consulte [resolução de problemas dos elementos de visuais personalizados do Power BI](power-bi-custom-visuals-troubleshoot.md).

## <a name="faq"></a>PERGUNTAS FREQUENTES

Para obter mais informações e respostas a perguntas, aceda às [Perguntas frequentes sobre os elementos visuais personalizados do Power BI](power-bi-custom-visuals-faq.md#organizational-custom-visuals).

## <a name="next-steps"></a>Próximos passos

* [Visualizações nos relatórios do Power BI](visuals/power-bi-report-visualizations.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/).
