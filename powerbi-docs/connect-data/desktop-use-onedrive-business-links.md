---
title: Utilizar ligações do OneDrive for Business no Power BI Desktop
description: Utilizar ligações do OneDrive for Business no Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/27/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 70607632dd4e93d1b0d5e53f19ef697c6599128d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410856"
---
# <a name="use-onedrive-for-business-links-in-power-bi-desktop"></a>Utilizar ligações do OneDrive for Business no Power BI Desktop
Muitas pessoas têm livros do Excel armazenados no OneDrive para Empresas que seriam adequados para utilização com o Power BI Desktop. No Power BI Desktop, pode utilizar ligações online para ficheiros do Excel armazenados no OneDrive para Empresas para criar relatórios e elementos visuais. Pode utilizar uma conta de grupo do OneDrive para Empresas ou a sua conta individual do OneDrive para Empresas.

Obter uma ligação online do OneDrive para Empresas requer passos específicos. As seguintes secções explicam esses passos, que lhe permitem partilhar a ligação para o ficheiro em grupos, em diferentes computadores e com os seus colegas.

## <a name="get-a-link-from-excel"></a>Obter uma ligação do Excel
1. Navegue para a sua localização do OneDrive para Empresas através de um browser. Clique com o botão direito do rato no ficheiro que pretende utilizar e selecione **Abrir no Excel**.
   
   > [!NOTE]
   > A sua interface de browser pode não ter um aspeto exatamente igual à imagem seguinte. Existem diversas formas de selecionar **Abrir no Excel** para ficheiros na sua interface de browser do OneDrive para Empresas. Pode utilizar qualquer opção que lhe permita abrir o ficheiro no Excel.
   
   ![Captura de ecrã a mostrar o OneDrive no browser, com a opção Abrir no Excel.](media/desktop-use-onedrive-business-links/odb-links_02.png)

2. No Excel, selecione **Ficheiro** > **Informações** e, em seguida, selecione o botão **Copiar caminho**, conforme mostrado na imagem seguinte.
   
   ![Captura de ecrã a mostrar o menu Informações com a seleção do botão Copiar caminho.](media/desktop-use-onedrive-business-links/onedrive-copy-path.png)

## <a name="use-the-link-in-power-bi-desktop"></a>Utilizar a ligação no Power BI Desktop
No Power BI Desktop, pode utilizar a ligação que copiou para a área de transferência. Siga estes passos:

1. No Power BI Desktop, selecione **Obter Dados** > **Web**.
   
   ![Captura de ecrã a mostrar o friso Obter Dados no Power B I Desktop com a seleção Web.](media/desktop-use-onedrive-business-links/power-bi-web-link-onedrive.png)
2. Com a opção **Básico** selecionada, cole a ligação na caixa de diálogo **Da Web**.
3. Remova a cadeia *?web=1* no fim da ligação para que o Power BI Desktop consiga navegar até ao seu ficheiro e, em seguida, selecione **OK**.
   
    ![Captura de ecrã a mostrar a caixa de diálogo Da Web a demonstrar como remover uma cadeia do campo de U R L.](media/desktop-use-onedrive-business-links/power-bi-web-link-confirmation.png) 
4. Se o Power BI Desktop lhe pedir credenciais, selecione **Windows** (para sites do SharePoint no local) ou **Conta Organizacional** (para sites do Microsoft 365 ou OneDrive para Empresas).
   
   ![Captura de ecrã a mostrar o pedido de credenciais do Power B I Desktop, com a seleção de conta Windows ou Organizacional.](media/desktop-use-onedrive-business-links/odb-links_06.png)

   É apresentada uma caixa de diálogo do **Navegador**, que lhe permite selecionar da lista de tabelas, folhas e intervalos encontrados no livro do Excel. A partir daí, pode utilizar o ficheiro do OneDrive para Empresas da mesma forma que qualquer outro ficheiro Excel. Pode criar relatórios e utilizá-los em conjuntos de dados tal como faria com qualquer outra origem de dados.

> [!NOTE]
> Para utilizar um ficheiro do OneDrive para Empresas como uma origem de dados no serviço Power BI, com a **Atualização de Serviço** ativada para esse ficheiro, confirme que seleciona **OAuth2** como **Método de autenticação** ao configurar as definições de atualização. Caso contrário, pode ocorrer um erro (por exemplo, *Falha ao atualizar as credenciais da origem de dados*) ao tentar estabelecer ligação ou atualizar. Selecionar **OAuth2** como método de autenticação soluciona esse erro de credenciais.
>
