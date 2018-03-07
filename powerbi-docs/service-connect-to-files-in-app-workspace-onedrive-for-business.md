---
title: "Ligar a ficheiros no OneDrive para uma área de trabalho de aplicação do Power BI"
description: "Saiba como armazenar e ligar aos seus ficheiros do Excel, CSV e Power BI Desktop no OneDrive para a sua área de trabalho de aplicação do Power BI."
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: ajayan
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/12/2017
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 8a078475bc01dec37d49f654d1fa90162a9d8366
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="connect-to-files-stored-in-onedrive-for-your-power-bi-app-workspace"></a>Ligar a ficheiros armazenados no OneDrive para a sua área de trabalho de aplicação do Power BI
Depois de [criar uma área de trabalho de aplicação no Power BI](service-create-distribute-apps.md), pode armazenar os seus ficheiros do Excel, CSV e Power BI Desktop no OneDrive para Empresas para a sua área de trabalho de aplicação do Power BI. Pode continuar a atualizar os ficheiros que armazena no OneDrive e essas atualizações são automaticamente refletidas nos relatórios e dashboards do Power BI com base nos ficheiros. 

A adição de ficheiros à área de trabalho de aplicação é um processo de dois passos: 

1. Primeiro, [carregue os ficheiros para o OneDrive para Empresas](service-connect-to-files-in-app-workspace-onedrive-for-business.md#1-upload-files-to-the-onedrive-for-business-for-your-app-workspace) para a sua área de trabalho da aplicação.
2. Em seguida, [ligue a esses ficheiros a partir do Power BI](service-connect-to-files-in-app-workspace-onedrive-for-business.md#2-import-excel-files-as-datasets-or-as-excel-online-workbooks).

> [!NOTE]
> As áreas de trabalho de aplicação estão disponíveis apenas no [Power BI Pro](service-free-vs-pro.md).
> 
> 

## <a name="1-upload-files-to-the-onedrive-for-business-for-your-app-workspace"></a>1 Carregar ficheiros para o OneDrive para Empresas para a sua área de trabalho de aplicação
1. No serviço Power BI, selecione a seta junto a Áreas de trabalho > selecione as reticências (**…**) junto ao nome da sua área de trabalho. 
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-ellipsis.png)
2. Selecione **Ficheiros** para abrir o OneDrive para Empresas para a sua área de trabalho de aplicação no Office 365.
   
   > [!NOTE]
   > Se não vir **Ficheiros** no menu da área de trabalho de aplicação, selecione **Membros** para abrir o OneDrive para Empresas para a sua área de trabalho de aplicação. Aí, selecione **Ficheiros**. O Office 365 configura uma localização de armazenamento do OneDrive para os ficheiros de área de trabalho de grupo da sua aplicação. Este processo pode demorar algum tempo. 
   > 
   > 
3. Aqui, pode carregar os seus ficheiros para o OneDrive para Empresas para a sua área de trabalho da aplicação. Selecione **Carregar**e navegue até aos ficheiros.
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grpfilesonedrive.png)

## <a name="2-import-excel-files-as-datasets-or-as-excel-online-workbooks"></a>2 Importar ficheiros do Excel como conjuntos de dados ou como livros do Excel Online
Agora que os seus ficheiros estão no OneDrive para Empresas para a sua área de trabalho da aplicação, tem uma opção. Pode: 

* [Importar os dados do livro do Excel como um conjunto de dados](service-get-data-from-files.md) e utilizar os dados para criar relatórios e dashboards que pode ver num browser e em dispositivos móveis.
* Ou [ligar a um livro do Excel inteiro no Power BI](service-excel-workbook-files.md) e apresentá-lo exatamente como aparece no Excel Online.

### <a name="import-or-connect-to-the-files-in-your-app-workspace"></a>Importar ou ligar a ficheiros na sua área de trabalho de aplicação
1. No Power BI, mude para a área de trabalho de aplicação, de modo a que o nome da área de trabalho apareça no canto superior esquerdo. 
2. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo. 
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-get-data-button.png)
3. Na caixa **Ficheiros** , selecione **Obter**.
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_getfiles.png)
4. Selecione **OneDrive** - *O Nome da sua Área de Trabalho de Aplicação*.
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grp_one_drive_shrpt.png)
5. Selecione o ficheiro desejado > **Ligar**.
   
    Esse é o momento de decidir se deseja [importar os dados do livro do Excel](service-get-data-from-files.md) ou [ligar-se a livros completas do Excel](service-excel-workbook-files.md).
6. Selecione **Importar** ou **Ligar**.
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_importexceldataorwholecrop.png)
7. Se selecionar **Importar**, o livro aparece no separador **Conjuntos de dados**. 
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-import.png)
   
    Se selecionar **Ligar**, o livro está no separador **Livros**.
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-connect.png)

## <a name="next-steps"></a>Próximos passos
* [Criar aplicações e áreas de trabalho de aplicação no Power BI](service-create-distribute-apps.md)
* [Importar dados de livros do Excel](service-get-data-from-files.md)
* [Ligar a livros inteiros do Excel](service-excel-workbook-files.md)
* Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)
* Comentários? Visite [Ideias para o Power BI](https://ideas.powerbi.com/forums/265200-power-bi)

