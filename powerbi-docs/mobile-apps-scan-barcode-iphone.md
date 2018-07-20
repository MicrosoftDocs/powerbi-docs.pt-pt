---
title: Ler um código de barras com um iPhone a partir da aplicação móvel do Power BI
description: Leia códigos de barras físicos para aceder diretamente a informações filtradas do Power BI na aplicação móvel do Power BI.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 10/13/2017
ms.author: maggies
ms.openlocfilehash: e5a61f1649e32def68afd01130c3c903c9f90a3c
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34294048"
---
# <a name="scan-a-barcode-with-your-iphone-from-the-power-bi-mobile-app"></a>Ler um código de barras com o iPhone a partir da aplicação móvel do Power BI
Leia códigos de barras físicos para aceder diretamente a informações filtradas do Power BI na aplicação móvel do Power BI.

![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-scanner.png)

Suponhamos que um colega [marcou um campo de código de barras num relatório do Power BI Desktop](desktop-mobile-barcodes.md) e partilhou o relatório consigo. 

Quando ler um código de barras de produto com o leitor na aplicação do Power BI no iPhone, irá ver o relatório (ou a lista de relatórios) com esse código de barras. Pode abrir esse relatório no iPhone, filtrado com base nesse código de barras.

## <a name="scan-a-barcode-with-the-power-bi-scanner"></a>Ler um código de barras com o leitor do Power BI
1. Na aplicação móvel do Power BI, abra o menu de navegação principal ![](media/mobile-apps-scan-barcode-iphone/pbi_iph_navmenu.png) na parte superior esquerda. 
2. Desloque-se para baixo e selecione **Leitor** e leia-o. 
   
    ![](media/mobile-apps-scan-barcode-iphone/power-bi-scanner.png)
3. Se a câmara não estiver ativada, tem de aprovar a utilização da câmara pela aplicação do Power BI. Esta aprovação só é feita uma vez. 
4. Aponte o leitor para um código de barras num produto. 
   
    Irá ver uma lista de relatórios associados a esse código de barras.
5. Toque no nome do relatório para o abrir no iPhone, filtrado automaticamente com base nesse código de barras.

## <a name="filter-by-other-barcodes-while-in-a-report"></a>Filtrar por outros códigos de barras num relatório
Ao ver um relatório filtrado por um código de barras no iPhone, poderá filtrar esse mesmo relatório por um código de barras diferente.

* Se o código de barras tiver um filtro ![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png), o filtro estará ativo e o relatório estará já filtrado por um código de barras. 
* Se o ícone não tiver um filtro ![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-unfiltered-icon.png), o filtro não estará ativo e o relatório não estará filtrado por um código de barras. 

Seja qual for o caso, toque no ícone para abrir um pequeno menu com um leitor a pairar.

* Coloque o foco do leitor no novo item para alterar o filtro do relatório para um valor de código de barras diferente. 
* Selecione **Limpar filtro de código de barras** para voltar ao relatório não filtrado.
* Selecione **Filtrar por códigos de barras recentes** para mudar o filtro de relatório para um dos códigos de barras que leu na sessão atual.

## <a name="issues-with-scanning-a-barcode"></a>Problemas ao ler um código de barras
Eis algumas das mensagens que poderá ver quando ler um código de barras num produto.

### <a name="couldnt-filter-report"></a>"Não foi possível filtrar o relatório..."
O relatório que decidiu filtrar baseia-se num modelo de dados que não inclui este valor de código de barras. Por exemplo, o produto "água mineral" não está incluído no relatório.  

### <a name="allsome-of-the-visuals-in-the-report-dont-contain-any-value"></a>Os visuais no relatório, ou alguns deles, não contêm valores
O valor do código de barras que leu existe no modelo mas os visuais no relatório, ou alguns deles, não contêm este valor e, consequentemente, a filtragem devolve um estado vazio. Tente ver outras páginas de relatório ou editar os seus relatórios no Power BI Desktop para conter este valor 

### <a name="looks-like-you-dont-have-any-reports-that-can-be-filtered-by-barcodes"></a>"Parece que não tem relatórios que possam ser filtrados por códigos de barras."
Isto significa que não tem relatórios compatíveis com códigos de barras. O leitor de código de barras só pode filtrar relatórios que tenham uma coluna marcada como **Código de barras**.  

Certifique-se de que o utilizador, ou o proprietário do relatório, marcou uma coluna como **Código de barras** no Power BI Desktop. Saiba mais sobre [marcar um campo de código de barras no Power BI Desktop](desktop-mobile-barcodes.md)

### <a name="couldnt-filter-report---looks-like-this-barcode-doesnt-exist-in-the-report-data"></a>"Não foi possível filtrar o relatório. Parece que este código de barras não existe nos dados de relatório".
O relatório que decidiu filtrar baseia-se num modelo de dados que não inclui este valor de código de barras. Por exemplo, o produto "água mineral" não está incluído no relatório. Pode ler um produto diferente, selecionar outro relatório (se houver mais do que um relatório disponível) ou ver o relatório sem filtragem. 

## <a name="next-steps"></a>Próximos passos
* [Marcar um campo de código de barras no Power BI Desktop](desktop-mobile-barcodes.md)
* [Mosaicos de dashboards no Power BI](service-dashboard-tiles.md)
* [Dashboards no Power BI](service-dashboards.md)

