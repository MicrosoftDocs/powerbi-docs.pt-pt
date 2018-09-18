---
title: Incorporar um relatório através de um iFrame
description: Incorporar um relatório do Power BI Report Server num iFrame no SharePoint Server
author: markingmyname
ms.author: maghan
ms.date: 05/04/2018
ms.topic: quickstart
ms.service: powerbi
ms.component: powerbi-report-server
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 802107ce9c12075ffc51461375ca3e9a313f2be1
ms.sourcegitcommit: 9c3a9ec14c111d766ef5703366c316e72f6e588f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45558430"
---
# <a name="quickstart-embed-a-power-bi-report-server-report-using-an-iframe-in-sharepoint-server"></a>Início Rápido: incorporar um relatório do Power BI Report Server com um iFrame no SharePoint Server

Neste manual de início rápido vai aprender a incorporar um relatório do Power BI Report Server com um iFrame numa página do SharePoint. Se estiver a trabalhar com o SharePoint Online, o Power BI Report Server tem de estar acessível publicamente. No SharePoint Online, a Peça Web do Power BI que funciona com o serviço Power BI não funciona com o Power BI Report Server. 

![Exemplo de iFrame](media/quickstart-embed/quickstart_embed_01.png)
## <a name="prerequisites"></a>Pré-requisitos
* Tem de ter o [Power BI Report Server](https://powerbi.microsoft.com/en-us/report-server/) instalado e configurado.
* Terá de ter o [Power BI Desktop otimizado para o Power BI Report Server](install-powerbi-desktop.md) instalado.
* Terá de ter um ambiente do [SharePoint](https://docs.microsoft.com/sharepoint/install/install) instalado e configurado.

## <a name="creating-the-power-bi-report-server-report-url"></a>Criar o URL do relatório do Power BI Report Server

1. Transferir o exemplo a partir do GitHub – [Demonstração no Blogue](https://github.com/Microsoft/powerbi-desktop-samples).

    ![transferir ficheiro PBIX de exemplo](media/quickstart-embed/quickstart_embed_14.png)

2. Abra o ficheiro PBIX de exemplo a partir do GitHub no **Power BI Desktop otimizado para o Power BI Report Server**.

    ![Ferramenta PBI RS Desktop](media/quickstart-embed/quickstart_embed_02.png)

3. Guarde o relatório no **Power BI Report Server**. 

    ![PBI RS Guardar](media/quickstart-embed/quickstart_embed_03.png)

4. Ver o relatório no **Portal Web**.

    ![Portal Web](media/quickstart-embed/quickstart_embed_04.png)

### <a name="capturing-the-url-parameter"></a>Capturar o parâmetro de URL

Após ter o seu URL, pode criar um iFrame numa página do SharePoint para alojar o relatório. Para qualquer URL de relatório do Power BI Report Server, pode adicionar um parâmetro de cadeia de consulta de `?rs:embed=true` para incorporar o relatório num iFrame. 

   Por exemplo:
    ``` 
    http://myserver/reports/powerbi/Sales?rs:embed=true
    ```
## <a name="embedding-a-power-bi-report-server-report-in-a-sharepoint-iframe"></a>Incorporar um relatório do Power BI Report Server num iFrame do SharePoint

1. Navegue para uma página de **Conteúdo do Site** do SharePoint.

    ![Página de Conteúdo do Site](media/quickstart-embed/quickstart_embed_05.png)

2. Escolha a página onde pretende adicionar o relatório.

    ![Aplicação de Página de Conteúdo do Site](media/quickstart-embed/quickstart_embed_06.png)

3. Selecione a roda dentada no canto superior direito e selecione **Editar Página**.

    ![Opção Editar Página](media/quickstart-embed/quickstart_embed_07.png)

4. Selecione **Adicionar Peça Web**.

    ![Adicionar Peça Web](media/quickstart-embed/quickstart_embed_08.png)

5. Em **Categorias** selecione **Suportes de Dados e Conteúdo**, em **Peças**, selecione **Editor de Conteúdo** e, em seguida, selecione **Adicionar**.

    ![Selecionar Peça Web do Editor de Conteúdo](media/quickstart-embed/quickstart_embed_09.png) ![Selecione Adicionar](media/quickstart-embed/quickstart_embed_091.png)

6. Selecione **Clique aqui para adicionar novo conteúdo**.

    ![Adicionar novo conteúdo](media/quickstart-embed/quickstart_embed_10.png)

7. No friso, selecione o separador **Formatar Texto** e, em seguida, selecione **Editar Origem**.

     ![Editar Origem](media/quickstart-embed/quickstart_embed_11.png)

8. Na janela Editar Origem, cole o código de iFrame e selecione OK.

    ![Código de iFrame](media/quickstart-embed/quickstart_embed_12.png)

     Por exemplo:
     ```
     <iframe width="800" height="600" src="http://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
     ```

9. No friso, selecione o separador **Página** e selecione **Parar Edição**.

    ![Parar Edição](media/quickstart-embed/quickstart_embed_13.png)

10. Agora deverá ver o relatório na página.

    ![Exemplo de iFrame](media/quickstart-embed/quickstart_embed_01.png)

## <a name="next-steps"></a>Próximos passos

[Início rápido: Criar um relatório do Power BI para o Power BI Report Server](quickstart-create-powerbi-report.md)  
[Início rápido: Criar um relatório paginado para o Power BI Report Server](quickstart-create-paginated-report.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/) 