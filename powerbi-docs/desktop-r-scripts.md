---
title: Executar scripts R no Power BI Desktop
description: Executar scripts R no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/27/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 6796de2b32061629e8f4fbcbc9b3311b5a95042d
ms.sourcegitcommit: f01a88e583889bd77b712f11da4a379c88a22b76
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/27/2018
ms.locfileid: "39327298"
---
# <a name="run-r-scripts-in-power-bi-desktop"></a>Executar scripts R no Power BI Desktop
É possível executar scripts do R diretamente no **Power BI Desktop** e importar os conjuntos de dados resultantes para um modelo de dados do Power BI Desktop.

## <a name="install-r"></a>Instalar o R
Para executar scripts R no Power BI Desktop, tem de instalar o **R** no seu computador local. Pode transferir e instalar o **R** gratuitamente a partir de vários locais, incluindo a [página de transferência do Revolution Open](https://mran.revolutionanalytics.com/download/) e o [Repositório CRAN](https://cran.r-project.org/bin/windows/base/). A versão atual de scripting R no Power BI Desktop suporta carateres Unicode, bem como espaços (carateres vazios) no caminho de instalação.

## <a name="run-r-scripts"></a>Executar scripts R
Com apenas alguns passos no Power BI Desktop, pode executar scripts R e criar um modelo de dados, através do qual pode criar relatórios e partilhá-los no serviço Power BI. O scripting R no Power BI Desktop suporta agora formatos numéricos com decimais (.) e vírgulas (,).

### <a name="prepare-an-r-script"></a>Preparar um script R
Para executar um script R no Power BI Desktop, crie o script no seu ambiente de desenvolvimento local do R e certifique-se de que é executado com êxito.

Para executar o script no Power BI Desktop, verifique se é executado com êxito numa área de trabalho nova e não modificada. Isto significa que todos os pacotes e dependências têm de ser explicitamente carregados e executados. Pode utilizar *source()* para executar scripts dependentes.

Quando preparar e executar um script R no Power BI Desktop, existem algumas limitações:

* Apenas os pacotes de dados são importados, pelo que deve certificar-se de que os dados que quer importar para o Power BI estão representados num pacote de dados
* As colunas escritas como Complexas e Vetoriais não são importadas e são substituídas por valores de erro na tabela criada
* Os valores que são N/D são convertidos em valores NULL no Power BI Desktop
* Qualquer script R executado durante mais de 30 minutos expira
* As chamadas interativas no script R, como aguardar a entrada do utilizador, interrompem a execução do script
* Quando definir o diretório de trabalho no script R, é *necessário* definir um caminho completo para o diretório de trabalho, em vez de um caminho relativo

### <a name="run-your-r-script-and-import-data"></a>Executar o script R e importar dados
1. No Power BI Desktop, o conector de dados de Script R pode ser encontrado em **Obter Dados**. Para executar o Script R, selecione **Obter Dados &gt; Mais...** e, em seguida, selecione **Outro &gt; Script do R**, conforme mostrado na seguinte imagem:
   
   ![](media/desktop-r-scripts/r-scripts-1.png)
2. Se o R estiver instalado no computador local, será selecionada a versão mais recente instalada como o motor do R. Basta copiar o script para a janela do script e selecionar **OK**.
   
   ![](media/desktop-r-scripts/r-scripts-2.png)
3. Se o R não estiver instalado, não for identificado ou se houver várias instalações no computador local, expanda **Definições de Instalação do R** para apresentar as opções de instalação ou selecionar em que instalação quer executar o script R.
   
   ![](media/desktop-r-scripts/r-scripts-3.png)
   
   Se o R estiver instalado e não for identificado, pode fornecer explicitamente a sua localização na caixa de texto fornecida ao expandir as **Definições de Instalação do R**. Na imagem acima, o caminho *C:\Program Files\R\R-3.2.0* é explicitamente fornecido na caixa de texto.
   
   As definições de instalação do R estão localizadas centralmente na secção Scripting R da caixa de diálogo Opções. Para especificar as configurações de instalação do R, selecione **Ficheiro > Opções e definições** e, em seguida **Opções > Scripting R**. Se houver várias instalações do R disponíveis, será apresentado um menu pendente que permite selecionar que instalação será usada.
   
   ![](media/desktop-r-scripts/r-scripts-4.png)
4. Selecione **OK** para executar o Script R. Quando o script é executado com êxito, pode escolher os pacotes de dados resultantes a adicionar ao modelo do Power BI.

### <a name="refresh"></a>Atualizar
Pode atualizar um script R no Power BI Desktop. Quando atualiza um script R, o Power BI Desktop executa-o novamente no respetivo ambiente.

## <a name="next-steps"></a>Passos seguintes
Veja as seguintes informações adicionais sobre o R no Power BI.

* [Criar visuais R no Power BI Desktop](desktop-r-visuals.md)
* [Utilizar um IDE R externo com o Power BI](desktop-r-ide.md)

