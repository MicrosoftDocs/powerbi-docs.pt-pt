---
title: Início Rápido Ligar a dados no Power BI Desktop
description: Como ligar às origens de dados disponíveis no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: quickstart
ms.date: 01/10/2020
ms.author: davidi
LocalizationGroup: quickstart
ms.openlocfilehash: 5aed52ec232d3e603d69bfe93640187401279ff6
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "75885225"
---
# <a name="quickstart-connect-to-data-in-power-bi-desktop"></a>Início Rápido: ligar a dados no Power BI Desktop

Neste manual de início rápido, liga-se a dados com o Power BI Desktop, que é o primeiro passo na criação de modelos de dados e na criação de relatórios.

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

Se não estiver inscrito no Power BI, [inscreva-se para uma avaliação gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) antes de começar.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir os passos neste artigo, precisa dos seguintes recursos:

* Transferir e instalar o Power BI Desktop, uma aplicação gratuita que é executada no seu computador local. Pode [transferir o Power BI Desktop](https://powerbi.microsoft.com/desktop) diretamente ou pode obtê-lo a partir da [Microsoft Store](https://aka.ms/pbidesktopstore).
* [Transfira este livro do Excel de exemplo](https://go.microsoft.com/fwlink/?LinkID=521962)e crie uma pasta denominada *C:\PBID-qs*, onde pode armazenar o ficheiro do Excel. Os passos posteriores neste manual de início rápido partem do princípio que esta é a localização do ficheiro para o livro do Excel transferido.
* Há muitos conectores de dados para o Power BI Desktop que requerem o Internet Explorer 10 (ou mais recente) para autenticação.

## <a name="launch-power-bi-desktop"></a>Iniciar o Power BI Desktop

Depois de instalar o Power BI Desktop, inicie a aplicação para que seja executada no computador local. É apresentado um tutorial do Power BI. Siga o tutorial ou feche a caixa de diálogo para começar com uma tela em branco. A tela serve para criar elementos visuais e relatórios a partir dos seus dados.

![Power BI Desktop com tela em branco](media/desktop-quickstart-connect-to-data/qs-connect-data_01.png)

## <a name="connect-to-data"></a>Ligar a dados

O Power BI Desktop permite ligar-se a vários tipos diferentes de dados. Estas origens incluem origens de dados básicas, como um ficheiro do Microsoft Excel. Pode ligar-se a serviços online que contêm todos os tipos de dados, como Salesforce, Microsoft Dynamics, Azure Blob Storage e muitos mais.

Para se ligar a dados, no friso **Base**, selecione **Obter Dados**.

![Obter Dados no friso Home Page](media/desktop-quickstart-connect-to-data/qs-connect-data_02.png)

A janela **Obter Dados** é apresentada. Pode optar entre as várias origens de dados diferentes às quais o Power BI Desktop pode ligar-se. Neste início rápido, utilize o livro do Excel que transferiu nos [Pré-requisitos](#prerequisites).

![Obter Dados de todas as origens](media/desktop-quickstart-connect-to-data/qs-connect-data_03.png)

Uma vez que esta origem de dados é um ficheiro do Excel, selecione **Excel** na janela **Obter Dados** e, em seguida, selecione o botão **Ligar**.

O Power BI pede-lhe que forneça a localização do ficheiro do Excel para estabelecer ligação. O ficheiro transferido denomina-se *Financial Sample* (Exemplo Financeiro). Selecione esse ficheiro e, em seguida, selecione **Abrir**.

![Obter Dados no Financial Sample (Exemplo Financeiro)](media/desktop-quickstart-connect-to-data/qs-connect-data_04.png)

O Power BI Desktop carrega o livro, lê o conteúdo e mostra-lhe os dados disponíveis no ficheiro com a janela **Navegador**. Nessa janela, pode escolher os dados que pretende carregar para o Power BI Desktop. Selecione as tabelas ao assinalar as caixas de verificação ao lado de cada tabela que pretende importar. Importe as duas tabelas disponíveis.

![Selecionar dados na janela Navegador](media/desktop-quickstart-connect-to-data/qs-connect-data_05.png)

Assim que tiver selecionado as opções, selecione **Carregar** para importar os dados para o Power BI Desktop.

## <a name="view-data-in-the-fields-pane"></a>Ver dados no painel Campos

Assim que tiver carregado as tabelas, o painel **Campos** mostra-lhe os dados. Pode expandir cada tabela ao selecionar a seta junto ao nome. Na imagem seguinte, a tabela *finanças* é expandida e mostra cada um dos campos.

![Obter Dados](media/desktop-quickstart-connect-to-data/qs-connect-data_06.png)

E já está! Ligou-se aos dados no Power BI Desktop, carregou esses dados e, agora, pode ver todos os campos disponíveis nessas tabelas.

## <a name="next-steps"></a>Próximas etapas

Existem vários tipos de tarefas que pode fazer com o Power BI Desktop logo que tenha ligado os dados. Pode criar elementos visuais e relatórios. Observe o recurso seguinte para seguir no caminho certo:

* [Introdução ao Power BI Desktop](desktop-getting-started.md)
