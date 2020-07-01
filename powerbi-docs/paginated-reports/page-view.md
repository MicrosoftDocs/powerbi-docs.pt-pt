---
title: Definir vistas de relatórios para relatórios paginados – Power BI
description: Neste artigo, ficará a conhecer as diferentes vistas de relatório disponíveis para relatórios paginados no serviço Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: ''
ms.topic: how-to
ms.date: 05/14/2020
ms.openlocfilehash: 5ed7f3a05be1e600fc67e5162b496309ce315f94
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85230953"
---
# <a name="set-report-views-for-paginated-reports-in-the-power-bi-service"></a>Definir vistas de relatórios para relatórios paginados no serviço Power BI

Quando compõe um relatório paginado no serviço Power BI, a vista predefinida é interativa e baseada em HTML. Outra vista de relatório para formatos de página fixa, como o PDF, é a nova opção Vista de Página.

**Vista interativa predefinida**

![Vista Predefinida](media/page-view/power-bi-paginated-default-view.png)

**Vista de Página**

![Vista de Página](media/page-view/power-bi-paginated-page-view.png)

Na Vista de Página, o relatório composto tem um aspeto diferente em comparação com a vista predefinida. Algumas propriedades e conceitos nos relatórios paginados aplicam-se apenas a páginas fixas. A vista é semelhante a quando o relatório é impresso ou exportado. Ainda pode alterar alguns elementos, como valores de parâmetros, mas não tem outras funcionalidades interativas, como a ordenação de colunas e os botões de alternar.

A opção Vista de Página suporta todas as funcionalidades que o Visualizador de PDF do browser suporta, como Ampliar, Reduzir e Ajustar à página.

## <a name="switch-to-page-view"></a>Mudar para a Vista de Página

Quando abre um relatório paginado, este é composto numa vista interativa por predefinição. Se o relatório tiver parâmetros, selecione os parâmetros e, em seguida, veja o relatório.

1. Na barra de ferramentas, selecione **Ver** > **Vista de Página**.

    ![Mudar para a Vista de Página](media/page-view/power-bi-paginated-page-view-dropdown.png)

2. Pode alterar as definições da vista de página ao selecionar **Definições de Página** no menu **Ver** na barra de ferramentas. 

    ![Selecionar Definições de Página](media/page-view/power-bi-paginated-page-settings-dropdown.png)
    
    A caixa de diálogo **Definições de Página** tem opções para definir o **Tamanho da Página** e a **Orientação** da Vista de Página. Após aplicar as definições de página, serão aplicadas as mesmas opções quando imprimir a página mais tarde.
   
    ![Caixa de diálogo Definições de Página](media/page-view/power-bi-paginated-page-settings-dialog.png)

3. Para mudar novamente para a vista interativa, selecione **Predefinição** na caixa pendente **Ver**.

## <a name="browser-support"></a>Browser support (Suporte do browser)

A Vista de Página é suportada nos browsers Google Chrome e Microsoft Edge. Certifique-se de que a visualização de PDFs está ativada no browser. É a predefinição nestes browsers.

A Vista de Página não é suportada no Internet Explorer e no Safari, por isso a opção está desativada. Também não é suportada nos browsers em dispositivos móveis ou nas aplicações móveis nativas do Power BI.  


## <a name="next-steps"></a>Próximos passos

- [Ver um relatório paginado no serviço Power BI](../consumer/paginated-reports-view-power-bi-service.md)
- [O que são relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)
