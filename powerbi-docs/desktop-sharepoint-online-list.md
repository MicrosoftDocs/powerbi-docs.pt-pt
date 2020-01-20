---
title: Criar um relatório numa Lista do SharePoint
description: Este tutorial mostra como pode transformar os dados da sua Lista do SharePoint num relatório do Power BI.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/10/2020
ms.author: davidi
LocalizationGroup: Visualizations
ms.openlocfilehash: 4fd350ae5d4a916e6753f7cd66e1fca52137efd5
ms.sourcegitcommit: 052df769e6ace7b9848493cde9f618d6a2ae7df9
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/14/2020
ms.locfileid: "75925639"
---
# <a name="create-a-report-on-a-sharepoint-list"></a>Criar um relatório numa Lista do SharePoint

Várias equipas e organizações utilizam as Listas do SharePoint Online para armazenar dados, pois são fáceis de configurar e de serem atualizadas pelos utilizadores.  Por vezes, um gráfico é uma forma muito mais fácil de os utilizadores compreenderem os dados rapidamente ao invés de observar a lista em si. Neste tutorial, vamos mostrar como pode transformar os dados da sua Lista do SharePoint num relatório do Power BI.

Veja este tutorial em vídeo de cinco minutos ou desloque-se para baixo para obter instruções passo a passo.

<iframe width="400" height="450" src="https://www.youtube.com/embed/OZO3x2NF8Ak" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-connect-to-your-sharepoint-list"></a>Parte 1: estabelecer ligação à sua Lista do SharePoint

1. Se ainda não o tiver, pode transferir e instalar o [Power BI Desktop](https://powerbi.microsoft.com/desktop/).
2. Abra o Power BI Desktop e, no separador Base do friso, selecione **Obter Dados** > **Mais**.
3. Selecione **Serviços Online** e, em seguida, selecione **Lista do SharePoint Online**.  

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-getdata.png" alt="get data" width="350"/>

4. Selecione **Ligar**.
4. Localize o endereço (também denominado URL) do site do SharePoint Online que contém a sua lista.  Normalmente, numa página no SharePoint Online, pode obter o endereço do site ao selecionar **Home page** no painel de navegação ou no ícone do site na parte superior e, em seguida, copiar o endereço na barra de endereço do seu browser.

   Veja um vídeo deste passo:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=48&end=90" frameborder="0" allowfullscreen></iframe>

5. No Power BI Desktop, cole o endereço no campo **URL do Site** na caixa de diálogo aberta.

6. É possível que veja um ecrã de acesso ao SharePoint semelhante ao da seguinte imagem.  Se não o vir, avance para o passo 10.  Se o vir, selecione **Conta Microsoft** no lado esquerdo da página.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-auth1.png" alt="choose Microsoft account" width="500"/>

7. Selecione **Iniciar Sessão** e introduza o nome de utilizador e a palavra-passe que utiliza para iniciar sessão no Microsoft Office 365.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-auth2.png" alt="sign in" width="500"/>

8. Quando tiver iniciado sessão, selecione **Ligar**.

9. No lado esquerdo do Navegador, selecione a caixa de verificação junto à lista do SharePoint à qual pretende ligar.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-select-list.png" alt="get data" width="450"/>

10. Selecione **Carregar**.  O Power BI carrega os dados da sua lista para um novo relatório.

## <a name="part-2-create-a-report"></a>Parte 2: Criar um relatório

1. No lado esquerdo, selecione o ícone **Dados** para verificar se os dados da lista do SharePoint foram carregados.

2. Certifique-se de que as colunas de lista com números mostram o ícone de Soma (ou Sigma) no **painel Campos** à direita.  Se alguma não o mostrar, selecione o cabeçalho da coluna na vista de tabela, selecione o separador **Modeling** e, em seguida, altere o **Tipo de dados** para **Número Decimal** ou **Número Inteiro**, consoante os dados.  Se lhe for pedido que confirme a sua alteração, selecione **Sim**.  Se o seu número tiver um formato especial, tal como uma moeda, também pode optar pelo mesmo ao definir o **Formato**.

   Veja um vídeo deste passo:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=147&end=204" frameborder="0" allowfullscreen></iframe>

3. No lado esquerdo, selecione o ícone **Relatório**.
4. Selecione as colunas que pretende visualizar ao selecionar a caixa de verificação junto às mesmas no painel **Campos** do lado direito.

   Veja um vídeo deste passo:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=215&end=252" frameborder="0" allowfullscreen></iframe>

5. Altere o tipo de elemento visual, se necessário.
6. Pode criar múltiplas visualizações no mesmo relatório ao desselecionar o elemento visual existente e, em seguida, selecionar as caixas de verificação de outras colunas no painel **Campos**.
7. Selecione **Guardar** para guardar o seu relatório.
