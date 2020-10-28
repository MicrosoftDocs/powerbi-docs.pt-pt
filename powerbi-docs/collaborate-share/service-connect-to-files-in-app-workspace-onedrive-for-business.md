---
title: Ligar a ficheiros no OneDrive para uma área de trabalho do Power BI
description: Saiba como armazenar e ligar aos seus ficheiros do Excel, CSV e Power BI Desktop no OneDrive para a sua área de trabalho do Power BI.
author: maggiesMSFT
ms.reviewer: lukasz
ms.service: powerbi
ms.topic: how-to
ms.date: 10/15/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 738ef62811ff510b20be60851cb6bd8225b1ad34
ms.sourcegitcommit: 59d07be9c3e4a2067f6d42c3002a194371bc4341
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2020
ms.locfileid: "92117009"
---
# <a name="connect-to-files-stored-in-onedrive-for-your-power-bi-workspace"></a>Ligar a ficheiros armazenados no OneDrive para a sua área de trabalho do Power BI
Ao [criar uma área de trabalho no Power BI](service-create-workspaces.md), também está a criar um grupo do Microsoft 365, com um OneDrive para Empresas associado. Este artigo explica como armazenar e atualizar os seus ficheiros do Excel, CSV e Power BI Desktop nesse OneDrive para Empresas. Essas atualizações são automaticamente refletidas nos relatórios e dashboards do Power BI com base nos ficheiros.

> [!NOTE]
> A nova experiência de área de trabalho muda a relação entre as áreas de trabalho do Power BI e os grupos do Microsoft 365. Não cria automaticamente um grupo do Microsoft 365 sempre que cria uma das novas áreas de trabalho. Leia mais sobre como [criar as novas áreas de trabalho](service-create-the-new-workspaces.md)

A adição de ficheiros à área de trabalho é um processo de dois passos: 

1. Primeiro, [carregue os ficheiros para o OneDrive para Empresas](#1-upload-files-to-the-onedrive-for-business-for-your-workspace) para a sua área de trabalho.
2. Em seguida, [ligue a esses ficheiros a partir do Power BI](#2-import-excel-files-as-datasets-or-as-excel-online-workbooks).

> [!NOTE]
> As áreas de trabalho estão disponíveis apenas com uma licença [Power BI Pro](../fundamentals/service-features-license-type.md).
> 

## <a name="1-upload-files-to-the-onedrive-for-business-for-your-workspace"></a>1 Carregar ficheiros para o OneDrive para Empresas para a sua área de trabalho
1. No serviço Power BI, selecione a seta junto a Áreas de trabalho > selecione as reticências ( **…** ) junto ao nome da sua área de trabalho. 
   
   ![Captura de ecrã a mostrar a área de trabalho do Power B I, com o nome da área de trabalho selecionada.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-ellipsis.png)
2. Selecione **Ficheiros** para abrir o OneDrive para Empresas para a sua área de trabalho no Microsoft 365.
   
   > [!NOTE]
   > Se não vir **Ficheiros** no menu da área de trabalho, selecione **Membros** para abrir o OneDrive para Empresas para a sua área de trabalho. Aí, selecione **Ficheiros** . O Microsoft 365 configura uma localização de armazenamento do OneDrive para os ficheiros de área de trabalho de grupo da sua aplicação. Este processo pode demorar algum tempo.
   > 
   > 
3. Aqui, pode carregar os seus ficheiros para o OneDrive para Empresas para a sua área de trabalho. Selecione **Carregar** e navegue até aos ficheiros.
   
   ![Captura de ecrã a mostrar o OneDrive para Empresas, a demonstrar como navegar para carregar um ficheiro.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grpfilesonedrive.png)

## <a name="2-import-excel-files-as-datasets-or-as-excel-online-workbooks"></a>2 Importar ficheiros do Excel como conjuntos de dados ou como livros do Excel Online
Agora que os seus ficheiros estão no OneDrive para Empresas para a sua área de trabalho, tem uma opção. Pode: 

* [Importe os dados do livro do Excel como um conjunto de dados](../connect-data/service-get-data-from-files.md). Em seguida, utilize os dados para criar relatórios e dashboards que pode ver num browser e em dispositivos móveis.
* Ou [ligar a um livro do Excel inteiro no Power BI](../connect-data/service-excel-workbook-files.md) e apresentá-lo exatamente como aparece no Excel Online.

### <a name="import-or-connect-to-the-files-in-your-workspace"></a>Importar ou ligar a ficheiros na sua área de trabalho
1. No Power BI, mude para a área de trabalho, de modo a que o nome da área de trabalho apareça no canto superior esquerdo. 
2. Selecione **Obter Dados** na parte inferior do painel de navegação. 
   
   ![Captura de ecrã a mostrar o botão Obter Dados no painel de navegação.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-get-data-button.png)
3. Na caixa **Ficheiros** , selecione **Obter** .
   
   ![Captura de ecrã a mostrar a caixa de diálogo Ficheiros com o botão Obter.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_getfiles.png)
4. Selecione **OneDrive** - *O Nome da sua Área de Trabalho* .
   
    ![Captura de ecrã a mostrar três mosaicos para selecionar a sua área de trabalho, com as opções Arquivo Local, OneDrive e SharePoint.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grp_one_drive_shrpt.png)
5. Selecione o ficheiro desejado > **Ligar** .
   
    Neste momento, deve decidir se deseja [importar os dados do livro do Excel](../connect-data/service-get-data-from-files.md) ou [ligar-se a livros completos do Excel](../connect-data/service-excel-workbook-files.md).
6. Selecione **Importar** ou **Ligar** .
   
    ![Captura de ecrã a mostrar a caixa de diálogo do OneDrive para Empresas, com a opção Importar do Excel ou Ligar ao Excel.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_importexceldataorwholecrop.png)
7. Se selecionar **Importar** , o livro aparece no separador **Conjuntos de dados** . 
   
    ![Captura de ecrã a mostrar as Áreas de trabalho no Power B I com o separador Conjuntos de dados.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-import.png)
   
    Se selecionar **Ligar** , o livro está no separador **Livros** .
   
    ![Captura de ecrã a mostrar as Áreas de trabalho no Power B I com o separador Livros.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-connect.png)

## <a name="next-steps"></a>Próximos passos
* [Criar aplicações e áreas de trabalho no Power BI](../collaborate-share/service-create-distribute-apps.md)
* [Importar dados de livros do Excel](../connect-data/service-get-data-from-files.md)
* [Connect to whole Excel workbooks](../connect-data/service-excel-workbook-files.md
* Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/)
* Comentários? Visite [Ideias para o Power BI](https://ideas.powerbi.com/forums/265200-power-bi)
