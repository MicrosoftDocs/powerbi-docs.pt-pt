---
title: Alterar o tamanho de uma página de relatório
description: Alterar as definições de visualização de uma página num relatório do Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 01/24/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: c2b9a106c4007af868cf69902ce511da8e03e75f
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="change-the-size-of-a-report-page"></a>Alterar o tamanho de uma página de relatório
No [artigo e vídeo anterior](power-bi-report-display-settings.md), aprendeu duas maneiras diferentes de controlar a apresentação de página nos relatórios do Power BI: **Ver** e **Tamanho da Página**. A Vista de Página e o Tamanho da Página estão disponíveis no serviço Power BI e no Power BI Desktop, e têm um aspeto e funcionalidade quase idênticos. Porém, para este tutorial vamos utilizar o serviço Power BI.

### <a name="prerequisites"></a>Pré-requisitos
- Serviço Power BI   
- [Relatório de Exemplo de Análise de Revenda](sample-retail-analysis.md)

## <a name="first-lets-change-the-page-view-setting"></a>Primeiro, vamos alterar a definição de Visualização da página

1. Abra o relatório na Vista de Leitura ou na Vista de Edição e selecione o separador de relatório **New Stores** (Lojas novas). Por predefinição, esta página do relatório é apresentada com a definição **Ajustar à Página**.  Neste caso, Ajustar à Página apresenta a página de relatório sem barras de deslocamento vertical, mas alguns dos detalhes e títulos são pequenos demais para leitura.

   ![](media/power-bi-change-report-display-settings/pbi_fit_to_page.png)
2. Certifique-se de que nenhuma visualização seja selecionada na tela. Selecione **Vista** e reveja as opções de apresentação.

    * Verá isto na vista de Leitura.

     ![](media/power-bi-change-report-display-settings/power-bi-page-view-menu-new.png)
    * Verá isto na vista de Edição.

    ![](media/power-bi-change-report-display-settings/power-bi-view-editing-view.png)

1. Vejamos qual o aspeto da página ao utilizar a definição **Tamanho real**.

   ![](media/power-bi-change-report-display-settings/power-bi-actal-size2.png)

   Agora, o dashboard tem barras de deslocamento duplas, o que não é muito bom.
2. Alterne para **Ajustar à Largura**.

   ![](media/power-bi-change-report-display-settings/pbi_fit_to_width.png)

   Muito melhor. Agora temos barras de deslocamento vertical, mas é mais fácil ler os detalhes.

## <a name="change-the-default-view-for-a-report-page"></a>Alterar a vista predefinida de uma página de relatório
Se for *criador* do relatório, pode alterar a vista predefinida para as páginas do relatório. Ao partilhar o relatório com outras pessoas, as páginas do relatório irão abrir com a vista que tiver definido. Os *consumidores* do relatório poderão alterar a vista, mas não conseguirão guardar as alterações depois de saírem do relatório.

1. Na página **New stores** (Lojas novas) do relatório, regresse à vista **Tamanho real**.

   ![](media/power-bi-change-report-display-settings/power-bi-actual-size.png)

2. Na página do relatório **District Monthly Sales** (Vendas mensais de distrito), defina Vista como **Ajustar à largura**.

3. Na página do relatório **Descrição geral**, deixe a predefinição de Vista.

4. Agora, guarde o relatório, selecionando **Ficheiro > Guardar**. Da próxima vez que abrir este relatório, as páginas serão apresentadas com as novas definições de Vista. Vamos ver como fica.

   ![](media/power-bi-change-report-display-settings/power-bi-save.png)
3. Selecione o nome da área de trabalho atual na barra de navegação superior para regressar a essa área de trabalho.  

   ![](media/power-bi-change-report-display-settings/power-bi-my-workspace.png)
4. Selecione o separador **Relatórios** e escolha o mesmo relatório (Exemplo de Análise de Revenda).

    ![](media/power-bi-change-report-display-settings/power-bi-new-report2.png)
5. Abra cada uma das páginas do relatório para ver as novas definições.

   ![](media/power-bi-change-report-display-settings/power-bi-page-view.gif)

## <a name="now-lets-explore-the-page-size-setting"></a>Agora, vamos explorar a definição *tamanho da página*
As definições de tamanho de página só estão disponíveis na [Vista de edição](service-interact-with-a-report-in-editing-view.md), pelo que tem de ter permissões de edição (*criador*) para o relatório para alterar as definições de tamanho de página. Se já se ligou a algum dos nossos [exemplos](sample-datasets.md), terá permissões de *criador* nesses relatórios.

1. Abra a página "District monthly sales" (Vendas mensais de distrito) do [Exemplo de Análise de Revenda](sample-retail-analysis.md) na Vista de Edição.
2. Certifique-se de que nenhuma visualização seja selecionada na tela.  No painel **Visualizações**, selecione o ícone do rolo de pintura ![](media/power-bi-change-report-display-settings/power-bi-paintroller.png).
3. Selecione **Tamanho da página** &gt; **Tipo** para ver as opções de tamanho da página.

   ![](media/power-bi-change-report-display-settings/power-bi-page-size-menu-new.png)
4. Selecione **Letra**.  Na tela, apenas o conteúdo que se encaixa em 816 x 1056 pixels (tamanho de Carta) permanecerá na parte branca da tela.

   ![](media/power-bi-change-report-display-settings/power-bi-letter-new.png)
5. Selecione **Tamanho da página** proporção **16:9**.

   ![](media/power-bi-change-report-display-settings/power-bi-16-to-9-new.png)

   A página de relatório é apresentada com uma proporção de 16 de largura por 9 de altura. Para ver o tamanho de pixel real que está a ser utilizado, observe os campos de largura e altura acinzentados (1280x720). Há muito espaço vazio à volta da tela de relatório, uma vez que **Vista** foi predefinido como "Ajustar à Largura".
7. Continue a explorar as opções de **Tamanho da Página**.

## <a name="use-page-view-and-page-size-together"></a>Utilizar a Vista de página e o Tamanho da Página em conjunto
Utilize a Vista de página e o Tamanho da Página em conjunto para criar um relatório que tenha o seu melhor aspeto quando partilhado com colegas ou incorporado noutra aplicação.

Neste exercício, vai criar uma página de relatório que será apresentada numa aplicação com espaço para 500 píxeis de largura e 750 píxeis de altura.

Lembre-se de que, no passo anterior, vimos que a nossa página de relatório tem atualmente 1280 de largura e 720 de altura. Sabemos portanto que precisamos de fazer bastante redimensionamento e reorganização para que todos os visuais fiquem ajustados.

1. Redimensione e mova os visuais para que consigam caber em menos de metade da área da tela.

    ![](media/power-bi-change-report-display-settings/power-bi-custom-view.gif)
2. Selecione **Tamanho da Página** &gt; **Personalizado**.
3. Defina a Largura como 500 e a Altura como 750.

    ![](media/power-bi-change-report-display-settings/power-bi-custom-new.png)
4. Otimize a página do relatório para que tenha o melhor aspeto possível. Alterne entre **Ver > Tamanho real** e **Ver > Ajustar à página** para fazer ajustes.

    ![](media/power-bi-change-report-display-settings/power-bi-final-new.png)

## <a name="next-steps"></a>Próximos passos
[Criar relatórios para a Cortana](service-cortana-answer-cards.md)

Voltar a [Configurações de apresentação de página num relatório do Power BI](power-bi-report-display-settings.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)
