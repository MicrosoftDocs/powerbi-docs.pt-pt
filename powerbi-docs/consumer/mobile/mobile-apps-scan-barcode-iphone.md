---
title: Scan código de barras da aplicação móvel Power BI
description: Leia códigos de barras físicos para aceder diretamente a informações filtradas do Power BI na aplicação móvel do Power BI.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 12/02/2019
ms.openlocfilehash: 3d35df1c38a0a62325f88fa19ee7267a3b209647
ms.sourcegitcommit: f7330dabb9cd8bce90bb2efec3e3273a11578f10
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2021
ms.locfileid: "99494529"
---
# <a name="scan-barcodes-from-the-mobile-app-to-get-filtered-data"></a>Scaneie códigos de barras da aplicação móvel para obter dados filtrados 
Digitalize códigos de barras no mundo real para obter diretamente informações de BI filtradas na aplicação móvel Power BI.

Aplica-se a:

| ![iPhone](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![iPads](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![Telemóvel Android](././media/mobile-apps-qr-code/android-logo-40-px.png) | ![Tablet Android](././media/mobile-apps-qr-code/android-logo-40-px.png) |
|:--- |:--- |:--- |:--- |
|iPhones |iPads |Telemóveis Android |Tablets Android |

Digamos que a sua organização tem relatórios que têm dados que foram [marcados como dados de código de barras no Power BI Desktop](../../transform-model/desktop-mobile-barcodes.md). Quando digitalizar um código de barras do produto com o scanner na aplicação Power BI no seu dispositivo, receberá uma lista dos relatórios que têm dados de código de barras. Pode abrir o relatório que procura, filtrado automaticamente para a informação de que precisa.

![Captura de ecrã a mostrar a leitura de um código de barras de um produto, com o leitor sobre o código de barras de uma bebida colorida.](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-scanner.png)

Aqui estão exemplos de dois cenários onde a digitalização de códigos de barras é útil:
* Imagine que está a verificar o inventário num grande supermercado e enquanto está nos corredores precisa de obter informações sobre determinados produtos, como quantos a loja tem em stock, quais os departamentos em que os itens estão abastecidos, etc. Basta abrir o scanner Power BI no seu dispositivo móvel e digitalizar o código de barras de um item. Receberá uma lista de relatórios que têm dados de código de barras. Escolha o relatório relevante e o relatório abre, filtrado para os dados relevantes.
* Digamos que as máquinas no chão da fábrica são identificadas com códigos de barras, e a telemetria dessas máquinas está a ser processada e enviada para o Power BI. Quando os engenheiros estão no estado da máquina de verificação do chão, podem facilmente digitalizar o código de barras de uma máquina e chegar a um relatório do KPI sobre o seu desempenho e estado.

## <a name="scan-a-barcode-with-the-power-bi-scanner"></a>Ler um código de barras com o leitor do Power BI
1. Na barra de navegação, toque em **Mais opções** (...) e, em seguida, toque em **Leitor**.

    ![Captura de ecrã a mostrar Mais opções no painel de navegação e a seleção do leitor.](media/mobile-apps-scan-barcode-iphone/power-bi-scanner.png)

1. Se a câmara não estiver ativada, tem de aprovar a utilização da câmara pela aplicação do Power BI. Esta aprovação só é feita uma vez. 
1. Aponte o scanner para um código de barras no item que lhe interessa. Você verá uma lista de relatórios que têm campos de código de barras.
1. Encontre o relatório que procura e toque para o abrir no seu dispositivo, filtrado automaticamente de acordo com o código de barras que digitalizou. Se o relatório não contiver o código de barras, receberá a mensagem "Não foi conseguindo filtrar o relatório". Nesse caso, pode voltar à lista e tentar outro relatório.
    
>[!NOTE]
>Se houver apenas um relatório com um campo de código de barras, não obterá uma lista de relatórios, mas o relatório abrir-se-á diretamente, filtrado de acordo com o código de barras que digitalizou. Se o relatório não contiver o código de barras que digitalizou, também receberá a mensagem "Não foi conseguindo filtrar o relatório".

## <a name="filter-by-other-barcodes-while-in-a-report"></a>Filtrar por outros códigos de barras num relatório
Ao ver um relatório filtrado por um código de barras no seu dispositivo, poderá filtrar esse mesmo relatório por um código de barras diferente.

Na barra de ação do relatório, toque **em Mais opções (...)** e encontre o ícone de código de barras.

* Se o ícone de código de barras estiver preenchido, ![Ícone filtrado](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png), o filtro estará ativo e o relatório estará já filtrado por um código de barras. 
* Se o ícone estiver claro ![Ícone não filtrado](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-unfiltered-icon.png), o filtro não estará ativo e o relatório não estará filtrado por um código de barras. 

Seja qual for o caso, toque no ícone para abrir um pequeno menu com um leitor a pairar.

* Coloque o foco do leitor no novo item para alterar o filtro do relatório para um valor de código de barras diferente. 
* Selecione **Limpar filtro de código de barras** para voltar ao relatório não filtrado.
* Selecione **Filtrar por códigos de barras recentes** para mudar o filtro de relatório para um dos códigos de barras que leu na sessão atual.

## <a name="clear-a-barcode-filter"></a>Limpar um filtro de código de barras
Para limpar a filtragem do código de barras enquanto está num relatório filtrado:
1. Na barra de ação do relatório, toque **em Mais opções (...)** e encontre o ícone filtrado do scanner de código de barras preenchido que indique que um filtro está ativo e toque nele para abrir o ![ ](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png) scanner.
1. Selecione **Limpar filtro de código de barras** para voltar ao relatório não filtrado.

## <a name="limitations"></a>Limitações

* O painel de filtros não indica a filtragem do código de barras. Para saber se um relatório é atualmente filtrado por um código de barras, veja o ícone no item do menu do Scanner de Código de Barras:

    ![Ícone filtrado](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png) indica que o relatório é atualmente filtrado por um código de barras.
    
    ![Ícone não filtrado](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-unfiltered-icon.png) indica que o relatório não é atualmente filtrado por um código de barras. 
* As aplicações móveis suportam a filtragem de Código de Barras apenas para relatórios que tenham apenas uma coluna de código de barras em todas as tabelas de dados do relatório. Se pesquisar um código de barras para um relatório que tenha mais de uma coluna de código de barras, não se faz filtragem.

## <a name="issues-with-scanning-a-barcode"></a>Problemas ao ler um código de barras
Aqui estão algumas emissões que poderá encontrar quando digitalizar um código de barras num item.

* Obtém-se uma mensagem Não pode filtrar o relatório - Parece que **este código de barras não existe nos dados do relatório**: Isto significa que o valor do código de barras que digitalizou não aparece no modelo de dados do relatório que escolheu filtrar. Este pode ser o caso, por exemplo, se o produto cujo código de barras digitalizou não estiver incluído no relatório. Pode ler um produto diferente, selecionar outro relatório (se houver mais do que um relatório disponível) ou ver o relatório sem filtragem.

* Recebes uma mensagem **Parece que não tens quaisquer relatórios que possam ser filtrados por códigos de barras**: Isto significa que não tens nenhum relatório habilitado para códigos de barras. O leitor de código de barras só pode filtrar relatórios que tenham uma coluna marcada como **Código de barras**. Certifique-se de que o utilizador, ou o proprietário do relatório, marcou uma coluna como **Código de barras** no Power BI Desktop. Saiba mais sobre [marcar um campo de código de barras no Power BI Desktop](../../transform-model/desktop-mobile-barcodes.md)

* A filtragem devolve um estado vazio. Isto pode significar que o valor de código de barras que digitalizou existe no seu modelo, mas todos ou alguns dos visuais do seu relatório não contêm este valor. Neste caso, tente olhar para outras páginas de relatório ou edite os seus relatórios no Power BI Desktop para conter este valor 

## <a name="next-steps"></a>Próximos passos
* [Marcar um campo de código de barras no Power BI Desktop](../../transform-model/desktop-mobile-barcodes.md)
* [Mosaicos de dashboards no Power BI](../end-user-tiles.md)
* [Dashboards no Power BI](../end-user-dashboards.md)