---
title: "Alterar o tamanho de uma página de relatório (Tutorial)"
description: "Tutorial: alterar as configurações de apresentação de uma página num relatório do Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: modifying
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/25/2017
ms.author: mihart
ms.openlocfilehash: a5cc05e26012f88e889612788d4479a370063d4f
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="change-the-size-of-a-report-page-tutorial"></a>Alterar o tamanho de uma página de relatório (Tutorial)
No [artigo e vídeo anterior](power-bi-report-display-settings.md), aprendeu duas maneiras diferentes de controlar a apresentação de página nos relatórios do Power BI: **Ver** e **Tamanho da Página**. Agora vamos tentar sozinhos.

## <a name="first-lets-change-the-page-view-setting"></a>Primeiro, vamos alterar a definição de Visualização da página
1. Abra um relatório na Vista de Leitura ou na Vista de Edição. Este exemplo usa a página “Novas Lojas” do [exemplo de Análise de Revenda](sample-retail-analysis.md).  A página é apresentada segundo a definição **Ajustar à Página**.  Neste caso, Ajustar à Página apresenta a página de relatório sem barras de deslocamento vertical, mas alguns dos detalhes e títulos são pequenos demais para leitura.
   
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
Todos os relatórios do Power BI têm a vista **Ajustar à página** predefinida. E se pretender que esta página de relatório seja sempre aberta na vista de **Tamanho real**?

1. Na página **New stores** (Lojas novas) do relatório, regresse à vista **Tamanho real**.
   
   ![](media/power-bi-change-report-display-settings/power-bi-actual-size.png)
2. Guarde o relatório com um nome diferente ao selecionar **Ficheiro > Guardar como**. Tem agora 2 cópias deste relatório: no relatório original, **New stores** (Lojas novas) continuará a abrir na vista predefinida mas, no novo relatório, será aberto na vista de **Tamanho real**. Vamos ver como fica.
   
   ![](media/power-bi-change-report-display-settings/power-bi-save-as.png)
3. Selecione o nome da área de trabalho atual na barra de navegação superior para regressar a essa área de trabalho.  
   
   ![](media/power-bi-change-report-display-settings/power-bi-my-workspace.png)
4. Selecione o separador **Relatórios** e selecione o relatório novo que acabou de criar (terá um asterisco amarelo).
   
    ![](media/power-bi-change-report-display-settings/power-bi-new-report2.png)
5. O relatório é aberto na vista de **Tamanho real**!
   
   ![](media/power-bi-change-report-display-settings/power-bi-actal-size2.png)

## <a name="now-lets-explore-the-page-size-setting"></a>Agora, vamos explorar a definição *tamanho da página*
As definições de tamanho da página apenas estão disponíveis na [Vista de edição](service-interact-with-a-report-in-editing-view.md). Para abrir um relatório na Vista de edição, tem de ter permissões de proprietário do relatório. Se já se ligou a algum dos nossos [exemplos](sample-datasets.md), terá permissões de proprietário nesses relatórios.

1. Abra a página "District monthly sales" (Vendas mensais de distrito) do [Exemplo de Análise de Revenda](sample-retail-analysis.md) na Vista de Edição.
2. Certifique-se de que nenhuma visualização seja selecionada na tela.  No painel **Visualizações**, selecione o ícone do rolo de pintura ![](media/power-bi-change-report-display-settings/power-bi-paintroller.png).
3. Selecione **Tamanho da página** &gt; **Tipo** para ver as opções de tamanho da página.
   
   ![](media/power-bi-change-report-display-settings/power-bi-page-size-menu-new.png)
4. Selecione **Letra**.  Na tela, apenas o conteúdo que se encaixa em 816 x 1056 pixels (tamanho de Carta) permanecerá na parte branca da tela.
   
   ![](media/power-bi-change-report-display-settings/power-bi-letter-new.png)
5. Se alterarmos **Vista** para "Ajustar à Largura", a nossa tela apresenta apenas a página de conteúdo que ajusta no tamanho da letra.
   
   ![](media/power-bi-change-report-display-settings/power-bi-fit-to-width-new.png)
6. Selecione **Tamanho da página** proporção **16:9**.
   
   ![](media/power-bi-change-report-display-settings/power-bi-16-to-9-new.png)
   
   A página de relatório é apresentada com uma proporção de 16 de largura por 9 de altura. Para ver o tamanho de pixel real que está a ser utilizado, observe os campos de largura e altura acinzentados (1280x720). Há muito espaço vazio à volta da tela de relatório, uma vez que **Vista** foi predefinido como "Ajustar à Largura".
7. Continue a explorar as opções de **Tamanho da Página**.

## <a name="using-page-view-and-page-size-together"></a>Usar a Vista de página e o Tamanho de Página juntos
Use a Vista de página e o Tamanho da Página em conjunto para criar um relatório que tenha o seu melhor aspeto quando incorporado noutra aplicação.

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

Leia mais sobre os [relatórios no Power BI ](service-reports.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

