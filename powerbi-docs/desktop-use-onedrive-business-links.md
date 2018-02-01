---
title: "Utilizar ligações do OneDrive for Business no Power BI Desktop"
description: "Utilizar ligações do OneDrive for Business no Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/05/2017
ms.author: davidi
ms.openlocfilehash: 2c249cac17e8fe6da35634c78837e3ca16e70a5c
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2017
---
# <a name="use-onedrive-for-business-links-in-power-bi-desktop"></a>Utilizar ligações do OneDrive for Business no Power BI Desktop
Muitas pessoas têm livros do Excel armazenados na sua unidade do OneDrive para Empresas que seriam adequados para utilização com o Power BI Desktop. No **Power BI Desktop**, pode utilizar ligações online para ficheiros do **Excel** armazenados no **OneDrive para Empresas**, para criar relatórios e visuais. Pode utilizar uma conta de grupo do **OneDrive para Empresas** ou a sua conta individual do **OneDrive para Empresas**.

Obter uma ligação online do **OneDrive para Empresas** requer passos específicos. As seguintes secções explicam esses passos, que lhe permitem partilhar a ligação para o ficheiro em grupos, em diferentes computadores e com os seus colegas.

## <a name="get-a-link-from-excel-starting-in-the-browser"></a>Obter uma ligação do Excel, a começar no browser
1. Navegue para a sua localização do OneDrive para Empresas através de um browser. Clique com o botão direito do rato no ficheiro que pretende utilizar e selecione **Abrir no Excel**.
   
   > [!NOTE]
> A sua interface de browser pode não ter um aspeto exatamente igual à imagem seguinte. Existem diversas formas de selecionar **Abrir no Excel** para ficheiros na sua interface de browser do **OneDrive para Empresas**. Pode utilizar qualquer opção que lhe permita abrir o ficheiro no Excel.
   > 
   > 
   
   ![](media/desktop-use-onedrive-business-links/odb-links_02.png)
2. No **Excel**, selecione **Ficheiro > Informações** e selecione a ligação acima do botão **Proteger Livro**. Selecione **Copiar ligação para a área de transferência** (a sua versão poderá dizer **Copiar caminho para a área de transferência**).
   
   ![](media/desktop-use-onedrive-business-links/odb-links_03.png)

## <a name="use-the-link-in-power-bi-desktop"></a>Utilizar a ligação no Power BI Desktop
No Power BI Desktop, pode utilizar a ligação que copiou para a área de transferência. Siga estes passos:

1. No Power BI Desktop, selecione **Obter Dados > Web**.
   
   ![](media/desktop-use-onedrive-business-links/odb-links_04.png)
2. Cole a ligação na caixa de diálogo **Da Web** (**não** selecione OK por enquanto).
   
    ![](media/desktop-use-onedrive-business-links/odb-links_05.png)
3. Repare na cadeia *?web=1* no final da ligação. Tem de *remover essa parte da cadeia do URL Web* **antes** de selecionar **OK**, para que o **Power BI Desktop** possa navegar devidamente para o seu ficheiro.
4. Se o **Power BI Desktop** lhe pedir credenciais, selecione **Windows** (para sites do SharePoint no local) ou **Conta Profissional** (para sites do Office 365 ou OneDrive para Empresas).
   
   ![](media/desktop-use-onedrive-business-links/odb-links_06.png)

Aparece uma janela do **Navegador**, que lhe permite selecionar da lista de tabelas, folhas e intervalos encontrados no livro do Excel. A partir daí, pode utilizar o ficheiro do OneDrive para Empresas como qualquer outro ficheiro do Excel, bem como criar relatórios e utilizá-lo em conjuntos de dados como faria com qualquer outra origem de dados.

> [!NOTE]
> Para utilizar o ficheiro do **OneDrive para Empresas** como uma origem de dados no serviço Power BI, com a **Atualização de Serviço** ativada para esse ficheiro, certifique-se de que seleciona **OAuth2** como **Método de autenticação** ao configurar as suas definições de atualização. Caso contrário, pode deparar-se com um erro (por exemplo, *Não foi possível atualizar as credenciais de origens de dados*) ao tentar ligar-se ou atualizar. Selecionar **OAuth2** como método de autenticação soluciona esse erro de credenciais.
> 
> 
