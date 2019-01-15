---
title: Utilizar temas de dashboard no serviço Power BI
description: Saiba como utilizar uma paleta de cores personalizadas e aplicá-la a um dashboard completo no serviço Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/22/2018
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 8e444c78c1f6f9f3f0be1375f96f7381489cc069
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54282906"
---
# <a name="use-dashboard-themes-in-power-bi-service"></a>Utilizar Temas de Dashboard no serviço Power BI
Com **Temas de Dashboard**, pode aplicar um tema de cores a todo o dashboard, como cores empresariais, cores sazonais ou qualquer outro tema de cores que pretenda aplicar. Quando aplica um **Tema do Dashboard**, todos os elementos visuais no dashboard utilizam as cores do tema selecionado (aplicam-se algumas exceções, descritas mais à frente neste artigo).

![dashboard de exemplo com tema](media/service-dashboard-themes/power-bi-full-dashboard-theme.png)

Alterar as cores dos elementos visuais do relatório no dashboard não afetará os elementos visuais no relatório. Além disso, ao afixar mosaicos de um relatório que já tem um [tema de relatório aplicado](desktop-report-themes.md), terá a opção de manter o tema atual ou utilizar o tema do dashboard.


## <a name="prerequisites"></a>Pré-requisitos
* Para acompanhar, abra o [dashboard de exemplo de Vendas e Marketing](sample-datasets.md).


## <a name="how-dashboard-themes-work"></a>Como funcionam os Temas de Dashboard
Para começar, abra um dashboard que tenha criado (ou no qual tenha permissão de edição) e que pretenda personalizar. Selecione as reticências (...) e selecione **Tema do dashboard**. 

![opção do tema do dashboard](media/service-dashboard-themes/power-bi-dashboard-theme.png)

No painel do dashboard apresentado, selecione um dos temas pré-criados.  No exemplo abaixo, selecionámos **Escuro**.

![Opção Claro selecionada](media/service-dashboard-themes/power-bi-theme-menu.png)

![Opção Escuro aplicada](media/service-dashboard-themes/power-bi-theme-dark.png)

## <a name="create-a-custom-theme"></a>Criar um tema personalizado

O tema predefinido para os dashboards do Power BI é **Claro**. Se quiser personalizar as cores ou criar o seu próprio tema, selecione **Personalizar** no menu pendente. 

![Selecione Personalizar no menu pendente](media/service-dashboard-themes/power-bi-theme-custom.png)

Utilize as opções de personalização para criar o seu próprio tema do dashboard. Se adicionar uma imagem de fundo, recomendamos que a sua imagem tenha uma resolução mínima de 1920x1080. Para utilizar uma imagem como fundo, carregue a imagem para um site público, copie o URL e cole-o no campo **URL da imagem**. 

### <a name="using-json-themes"></a>Utilizar temas JSON
Outra forma de criar um tema personalizado é carregar um ficheiro JSON que tenha definições para todas as cores que pretende utilizar no seu dashboard. No Power BI Desktop, os criadores de relatórios utilizam ficheiros JSON para [criar temas para relatórios](desktop-report-themes.md). Estes ficheiros JSON podem ser carregados para dashboards ou pode encontrar e carregar ficheiros JSON a partir da [página da galeria de temas](https://community.powerbi.com/t5/Themes-Gallery/bd-p/ThemesGallery) na Comunidade do Power BI 

![Site da galeria de temas](media/service-dashboard-themes/power-bi-theme-gallery.png)

Também pode guardar o seu tema personalizado como um ficheiro JSON e, em seguida, partilhá-lo com outros criadores de dashboards. 

### <a name="use-a-theme-from-the-theme-gallery"></a>Utilizar um tema da Galeria de Temas

Tal como as opções personalizadas e incorporadas, quando o tema é carregado, as cores são automaticamente aplicadas em todos os mosaicos no dashboard. 

1. Paire o cursor sobre um tema e selecione **View report (Ver relatório)**.

    ![View report](media/service-dashboard-themes/power-bi-choose-theme.png)

2. Desloque-se para baixo e procure a ligação para o ficheiro JSON.  Selecione o ícone de transferência e guarde o ficheiro.

    ![JSON Spring Day](media/service-dashboard-themes/power-bi-theme-json.png)

3. No serviço Power BI, na janela Personalizar tema do dashboard, selecione **Carregar tema JSON**.

    ![Carregar JSON](media/service-dashboard-themes/power-bi-upload-theme.png)

4. Navegue até à localização onde guardou o ficheiro do tema JSON e selecione **Abrir**.

5. Na página Tema do dashboard, selecione **Guardar**. O novo tema é aplicado ao seu dashboard.

    ![novo tema aplicado](media/service-dashboard-themes/power-bi-json.png)

## <a name="considerations-and-limitations"></a>Considerações e limitações

* Se o relatório estiver a utilizar um tema diferente do tema do dashboard, pode controlar se o elemento visual mantém o tema atual ou utiliza o tema do dashboard para obter consistência em elementos visuais de várias origens. Quando afixar um mosaico a um dashboard, para manter o tema do relatório, selecione **Manter o tema atual**. O elemento visual no dashboard irá manter o tema do relatório, incluindo as definições de transparência. 

    Só verá as opções de **Personalização de Mosaicos** se tiver criado o relatório no Power BI Desktop, [adicionado um tema de relatório](desktop-report-themes.md) e, em seguida, publicado o relatório no serviço Power BI. 

    ![Opção Manter o tema atual selecionada](media/service-dashboard-themes/power-bi-keep-current.png)

    Experimente afixar novamente o mosaico e selecionar **Utilizar tema do dashboard**.

    ![Utilizar tema de destino](media/service-dashboard-themes/power-bi-use-destination.png)

* Os temas de dashboard não podem ser aplicados a páginas de relatórios dinâmicos afixados, mosaicos de iFrame, mosaicos de SSRS, mosaicos de livros ou imagens.
* Os temas de dashboard podem ser vistos em dispositivos móveis, mas só pode criar um tema de dashboard no serviço Power BI. 
* Os temas de dashboard personalizados só funcionam com mosaicos afixados a partir de relatórios. 

