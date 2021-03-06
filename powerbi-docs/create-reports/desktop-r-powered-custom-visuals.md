---
title: Utilizar elementos visuais baseados em R no Power BI
description: Utilizar elementos visuais baseados em R no Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 07/27/2018
LocalizationGroup: Create reports
ms.openlocfilehash: e2a610e12da1a91db6e22ab493ed39410ec1c091
ms.sourcegitcommit: a5e98bc86915f7bea6a0ab5df282683840e63d2c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/07/2021
ms.locfileid: "97969748"
---
# <a name="use-r-powered-power-bi-visuals-in-power-bi"></a>Utilizar elementos visuais baseados em R no Power BI

No **Power BI Desktop** e no **serviço Power BI**, pode utilizar elementos visuais baseados em R, sem qualquer conhecimento do mesmo e sem qualquer script R. Isto permite-lhe tirar partido do poder analítico e visual dos elementos visuais e dos scripts baseados em R, sem aprender a utilizar o R ou fazer qualquer programação.

Para utilizar elementos visuais baseados em R, primeiro selecione e transfira o elemento visual personalizado baseado em R que gostaria de utilizar a partir da galeria do [**AppSource**](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals&page=1) de **elementos visuais do Power BI** para o Power BI.

![R visual 1a](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_1a.png)

As secções seguintes descrevem como selecionar, carregar e utilizar elementos visuais baseados em R no **Power BI Desktop**.

## <a name="use-r-power-bi-visuals"></a>Utilizar elementos visuais do Power BI baseados em R

Para utilizar elementos visuais baseados em R, transfira cada elemento visual da biblioteca de **elementos visuais do Power BI** e, em seguida, utilize o elemento visual como qualquer outro tipo de elemento visual no **Power BI Desktop**. Existem duas formas de obter elementos visuais do Power BI: pode transferi-los do site do **AppSource** online ou procurar e obtê-los no **Power BI Desktop**. 

### <a name="get-power-bi-visuals-from-appsource"></a>Obter elementos visuais do Power BI a partir do AppSource

Seguem-se os passos para procurar e selecionar elementos visuais no site do **AppSource** online:

1. Navegue para a biblioteca Elementos Visuais do Power BI, em [https://appsource.microsoft.com](https://appsource.microsoft.com/). Selecione a caixa de verificação *Aplicações do Power BI* em *Refinar por produto* e, em seguida, selecione a ligação **Ver todos**.

   ![R visual 2a](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_2a.png)

2. Na página da biblioteca [Elementos visuais do Power BI](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals&page=1), selecione **Elementos visuais do Power BI** na lista de Suplementos do painel esquerdo.

   ![R visual 2b](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_2b.png)

3. Selecione o **elemento visual** que gostaria de utilizar na galeria e será encaminhado para uma página que descreve o elemento visual. Selecione o botão **Obter agora** para transferir.

   > [!NOTE]
    > Para criar no **Power BI Desktop**, precisa de ter o R instalado no seu computador local. Mas, quando os utilizadores quiserem ver um elemento visual baseado em R no **serviço Power BI**, não precisam de ter o R instalado localmente.

   ![R visual 3a](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_3a.png)

   Não precisa de instalar o R para utilizar elementos visuais do Power BI baseados em R no **serviço Power BI**. No entanto, se quiser utilizar elementos visuais do Power BI baseados em R no **Power BI Desktop**, *tem* de instalar o R no computador local. Pode transferir o R a partir das seguintes localizações:

   * [CRAN](https://cran.r-project.org/)
   * [MRO](https://mran.microsoft.com/)

4. Assim que o elemento visual é transferido (tal como é transferido qualquer ficheiro a partir do browser), aceda a **Power BI Desktop** e clique em **Mais opções** (...) no painel **Visualizações** e selecione **Importar do ficheiro**.

   ![R visual 4a](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_4a.png)
5. É avisado da importação de elementos visuais personalizados, conforme mostrado na imagem seguinte:

   ![R visual 5](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_5.png)
6. Navegue para onde foi guardado o ficheiro do elemento visual e, em seguida, selecione-o. As visualizações personalizadas do **Power BI Desktop** têm a extensão .pbiviz.

   ![R visual 6](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_6.png)
7. Quando regressar ao Power BI Desktop, pode ver o novo tipo de elemento visual no painel **Visualizações**.

   ![R visual 7](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_7.png)
8. Quando importar o novo elemento visual (ou abrir um relatório que contém um elemento visual personalizado baseado em R), o **Power BI Desktop** instala os pacotes R necessários.

   ![R visual 8](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_8.png)

9. A partir daí, pode adicionar dados ao elemento visual, tal como faria com qualquer outro elemento visual do **Power BI Desktop**. Quando terminar, pode ver o elemento visual terminado na tela. No elemento visual seguinte, o elemento visual personalizado baseado em R de **Previsão** foi utilizado com projeções de taxa de nascimento das Nações Unidas (NU) (o elemento visual à esquerda).

    ![R visual 10](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_10.png)

    À semelhança de qualquer outro elemento visual do **Power BI Desktop**, pode publicar este relatório com os elementos visuais personalizados baseados em R no **serviço Power BI** e partilhá-lo com outras pessoas.

    Verifique a biblioteca com frequência, uma vez que os elementos visuais novos são adicionados a toda a hora.

### <a name="get-power-bi-visuals-from-within-power-bi-desktop"></a>Obter elementos visuais do Power BI a partir do **Power BI Desktop**

1. Também pode obter elementos visuais do Power BI a partir do **Power BI Desktop**. No **Power BI Desktop**, clique nas reticências (...), no painel **Visualizações**, e selecione **Importar do mercado**.

   ![R visual 4a](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_4a.png)

2. Quando o fizer, a caixa de diálogo **Elementos Visuais do Power BI** é apresentada, onde pode percorrer uma lista dos elementos visuais do Power BI disponíveis e selecionar o que quiser. Pode pesquisar por nome, selecionar uma categoria ou apenas percorrer os elementos visuais disponíveis. Quando estiver pronto, basta selecionar **Adicionar** para adicionar o elemento visual personalizado ao **Power BI Desktop**.

   ![R visual 12](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_12.png)

## <a name="contribute-r-powered-power-bi-visuals"></a>Contribuir com elementos visuais do Power BI baseados em R

Se criar os seus elementos visuais em R para utilização nos seus relatórios, pode partilhá-los com o mundo ao contribuir com os mesmos para a **galeria de elementos visuais do Power BI**. As contribuições são realizadas através do GitHub e o processo é destacado na seguinte localização:

* [Contribuir para a galeria de elementos visuais do Power BI baseados em R](https://github.com/PowerBi-Projects/PowerBI-visuals#building-r-powered-custom-visual-corrplot)

## <a name="troubleshoot-r-powered-power-bi-visuals"></a>Resolver problemas associados aos elementos visuais do Power BI baseados em R

Os elementos visuais do Power BI baseados em R têm determinadas dependências que devem ser cumpridas para os elementos visuais funcionarem corretamente. Quando os elementos visuais do Power BI baseados em R não são executados ou carregados corretamente, o problema é, normalmente, um dos seguintes:

* O motor do R está em falta
* Erros no script R no qual se baseia o elemento visual
* Os pacotes de R estão em falta ou desatualizados

A secção seguinte descreve os passos de resolução de problemas que pode tomar para ajudar a resolver problemas de endereço que podem ocorrer.

### <a name="missing-or-outdated-r-packages"></a>Pacotes de R em falta ou desatualizados

Quando tentar instalar um elemento visual personalizado baseado em R, pode encontrar erros quando existirem pacotes de R em falta ou desatualizados; isto devido a um dos seguintes motivos:

* A instalação do R não é compatível com o pacote R
* A firewall, o software antivírus ou as definições de proxy estão a impedir o R de se ligar à Internet
* A ligação à Internet está lenta ou existe um problema de ligação à Internet

A equipa do Power BI está a trabalhar ativamente para mitigar estes problemas antes de chegarem até si e o próximo Power BI Desktop irá incorporar atualizações para resolver estes problemas. Até lá, pode seguir um ou mais dos seguintes passos para mitigar os problemas:

1. Remova o elemento visual personalizado e, em seguida, instale-o novamente. Esta ação inicia uma reinstalação dos pacotes de R.
2. Se a instalação do R não estiver atualizada, atualize-a e, em seguida, remova e reinstale o elemento visual personalizado, conforme descrito no passo anterior.

   As versões suportadas do R estão listadas na descrição de cada elemento visual personalizado com tecnologia de R, conforme mostrado na imagem seguinte.

     ![R visual 11](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_11.png)
    > [!NOTE]
    > Pode manter a instalação do R original e associar apenas o Power BI Desktop à versão atual instalada. Vá para **Ficheiro > Opções e definições > Opções > Scripting do R**.

3. Instale os pacotes do R manualmente com qualquer consola do R. Os passos para esta abordagem são os seguintes:

   a. Transfira o script de instalação do elemento visual baseado em R e guarde esse ficheiro numa unidade local.

   b. Na consola do R, execute o seguinte:

      ```console
      source("C:/Users/david/Downloads/ScriptInstallPackagesForForecastWithWorkarounds.R")
      ```

   As localizações de instalação predefinida típica são as seguintes:

   ```console
       c:\Program Files\R\R-3.3.x\bin\x64\Rterm.exe (for CRAN-R)
       c:\Program Files\R\R-3.3.x\bin\x64\Rgui.exe (for CRAN-R)
       c:\Program Files\R\R-3.3.x\bin\R.exe (for CRAN-R)
       c:\Program Files\Microsoft\MRO-3.3.x\bin\R.exe (for MRO)
       c:\Program Files\Microsoft\MRO-3.3.x\bin\x64\Rgui.exe (for MRO)
       c:\Program Files\RStudio\bin\rstudio.exe (for RStudio)
   ```

4. Se os passos anteriores não funcionarem, experimente o seguinte:

   a. Utilize o **R Studio** e siga o passo descrito em 3.b. acima (executar a linha de script a partir da consola do R).

   b. Se o passo anterior não funcionar, altere **Ferramentas > Opções Globais > Pacotes** no **R Studio** e ative a caixa de verificação para **Utilizar a biblioteca/proxy do Internet Explorer para HTTP** e, em seguida, repita o passo 3.b. dos passos acima.

## <a name="next-steps"></a>Próximas etapas

Veja as seguintes informações adicionais sobre o R no Power BI.

* [Galeria de elementos visuais do Power BI](https://app.powerbi.com/visuals/)
* [Executar Scripts R no Power BI Desktop](../connect-data/desktop-r-scripts.md)
* [Criar elementos visuais do R no Power BI Desktop](desktop-r-visuals.md)
* [Utilizar um IDE do R externo com o Power BI](../connect-data/desktop-r-ide.md)
