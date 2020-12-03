---
title: Incorporar um relatório do Power BI Report Server com um iFrame no SharePoint Server
description: Este artigo demonstra como incorporar um relatório do Power BI Report Server com um iFrame no SharePoint Server
author: maggiesMSFT
ms.author: maggies
ms.date: 07/28/2020
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.openlocfilehash: 698f12f4bf5266373be8393d2add45d70979ab41
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418446"
---
# <a name="embed-a-power-bi-report-server-report-using-an-iframe-in-sharepoint-server"></a>Incorporar um relatório do Power BI Report Server com um iFrame no SharePoint Server

Neste artigo, irá aprender a incorporar um relatório do Power BI Report Server com um iFrame numa página do SharePoint. Se estiver a trabalhar com o SharePoint Online, o Power BI Report Server tem de estar acessível publicamente. No SharePoint Online, a peça Web do Power BI que funciona com o serviço Power BI não funciona com o Power BI Report Server.  

![Exemplo de iFrame](media/quickstart-embed/quickstart_embed_01.png)

## <a name="prerequisites"></a>Pré-requisitos
* [Power BI Report Server](https://powerbi.microsoft.com/report-server/) instalado e configurado.
* [Power BI Desktop otimizado para o Power BI Report Server](install-powerbi-desktop.md) instalado.
* Um [ambiente do SharePoint 2013, 2016 ou 2019](/sharepoint/install/install) instalado e configurado.
* O Internet Explorer 11 só será suportado se o modo de documento estiver definido como modo IE11 (Edge) ou quando estiver a utilizar o SharePoint Online. Pode utilizar outros browsers suportados com o SharePoint no local e o SharePoint Online.

## <a name="create-the-power-bi-report-url"></a>Criar URL de relatório do Power BI

1. Transfira o exemplo a partir do GitHub: [Demonstração no Blogue](https://github.com/Microsoft/powerbi-desktop-samples). Selecione **Clonar ou transferir** e, em seguida, selecione **Transferir ZIP**.

    ![Transferir ficheiro PBIX de exemplo](media/quickstart-embed/quickstart_embed_14.png)

2. Deszipe o ficheiro e abra o ficheiro .pbix de exemplo no Power BI Desktop otimizado para o Power BI Report Server.

    ![Ferramenta PBI RS Desktop](media/quickstart-embed/quickstart_embed_02.png)

3. Guarde o relatório no **Power BI Report Server**. 

    ![PBI RS Guardar](media/quickstart-embed/quickstart_embed_03.png)

4. Veja o relatório no portal Web do Power BI Report Server.

    ![Portal Web](media/quickstart-embed/quickstart_embed_04.png)

### <a name="capture-the-url-parameter"></a>Capturar o parâmetro de URL

Quando tiver o seu URL, pode criar um iFrame numa página do SharePoint para alojar o relatório. Para qualquer URL de relatório do Power BI Report Server, adicione o seguinte parâmetro de cadeia de consulta para incorporar o seu relatório num iFrame do SharePoint: `?rs:embed=true`.

   Por exemplo:
    ``` 
    https://myserver/reports/powerbi/Sales?rs:embed=true
    ```
## <a name="embed-the-report-in-a-sharepoint-iframe"></a>Incorporar o relatório num iFrame do SharePoint

1. Navegue para uma página de **Conteúdo do Site** do SharePoint.

    ![Página de Conteúdo do Site](media/quickstart-embed/quickstart_embed_05.png)

2. Escolha a página onde pretende adicionar o relatório.

    ![Aplicação de página de Conteúdo do Site](media/quickstart-embed/quickstart_embed_06.png)

3. Selecione o ícone de roda dentada no canto superior direito e, em seguida, selecione **Editar página**.

    ![Opção Editar página](media/quickstart-embed/quickstart_embed_07.png)

4. Selecione **Adicionar uma Peça Web**.

5. Em **Categorias**, selecione **Multimédia e Conteúdo**. Em **Peças**, selecione **Editor de Conteúdo** e, em seguida, selecione **Adicionar**.

    ![Selecionar Peça Web do Editor de Conteúdo](media/quickstart-embed/quickstart_embed_09.png)

6. Selecione **Clique aqui para adicionar novo conteúdo**.

7. No menu superior, selecione **Formatar Texto** e, em seguida, selecione **Editar Origem**.

     ![Editar Origem](media/quickstart-embed/quickstart_embed_11.png)

8. Na janela **Editar Origem**, cole o código de iFrame em **Origem HTML** e, em seguida, selecione **OK**.

    ![Código de iFrame](media/quickstart-embed/quickstart_embed_12.png)

     Por exemplo:
     ```html
     <iframe width="800" height="600" src="https://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
     ```

9. No menu superior, selecione **Página** e, em seguida, selecione **Parar Edição**.

    ![Parar Edição](media/quickstart-embed/quickstart_embed_13.png)

    O relatório aparece na página.

    ![Exemplo de iFrame](media/quickstart-embed/quickstart_embed_01.png)

## <a name="next-steps"></a>Próximos passos

- [Criar um relatório do Power BI para o Power BI Report Server](quickstart-create-powerbi-report.md).  
- [Criar um relatório paginado para o Power BI Report Server](quickstart-create-paginated-report.md).  

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/).