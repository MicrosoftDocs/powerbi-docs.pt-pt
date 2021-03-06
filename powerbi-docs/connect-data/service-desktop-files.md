---
title: Obter dados de ficheiros do Power BI Desktop
description: Aprenda a obter dados e relatórios do Power BI Desktop para o Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/26/2020
LocalizationGroup: Data from files
ms.openlocfilehash: e89f45d302216af8193029cb613b4e7a54365b8d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410396"
---
# <a name="get-data-from-power-bi-desktop-files"></a>Obter dados de ficheiros do Power BI Desktop
![Ícone de ficheiro do Power BI Desktop](media/service-desktop-files/pbid_file_icon.png)

O **Power BI Desktop** torna a business intelligence e relatórios mais fáceis. Quer esteja a ligar a várias origens de dados, a consultar e transformar dados, a modelar os seus dados e a criar relatórios poderosos e dinâmicos, o **Power BI Desktop** torna as tarefas de business intelligente intuitivas e rápidas. Se não estiver familiarizado com o **Power BI Desktop**, consulte [Introdução ao Power BI Desktop](../fundamentals/desktop-getting-started.md).

Assim que tiver dados no **Power BI Desktop** e criar alguns relatórios, está na altura de obter o seu ficheiro guardado no **serviço do Power BI**.

## <a name="where-your-file-is-saved-makes-a-difference"></a>O local em que o ficheiro é guardado faz a diferença
**Local** – Se guardar o ficheiro numa uma unidade local no computador ou noutro local na sua organização, através do Power BI Desktop, pode *importar* o ficheiro ou *publicá-lo* a partir do Power BI para obter os dados e relatórios para o Power BI. Na verdade, o ficheiro permanecerá na unidade local, pelo que, o ficheiro não é completamente movido para o Power BI. O que realmente acontece é que é criado um novo conjunto de dados no Power BI e os dados e o modelo de dados do ficheiro do Power BI Desktop são carregados para o conjunto de dados. Se o ficheiro tiver relatórios, estes serão apresentados no site do Power BI em Relatórios.

**OneDrive - Empresas** – Caso tenha o OneDrive para Empresas e inicie sessão com a mesma conta utilizada para o início de sessão no Power BI, esta será, sem dúvida, a forma mais eficaz de manter o seu trabalho no Power BI Desktop em sincronização com o conjunto de dados, os relatórios e os dashboards no Power BI. Como o Power BI e o OneDrive estão na cloud, o Power BI *liga* ao ficheiro no OneDrive em intervalos aproximados de uma hora. Caso sejam encontradas alterações, o conjunto de dados, os relatórios e os dashboards serão atualizados automaticamente no Power BI.

**OneDrive - Pessoal** – Caso os ficheiros sejam guardados na sua própria conta do OneDrive, vai aproveitar vários dos mesmos benefícios que teria com o OneDrive para Empresas. A maior diferença é que, na primeira ligação ao ficheiro (ao utilizar Obter Dados > Ficheiros > OneDrive – Pessoal), tem de iniciar sessão no OneDrive com a sua conta Microsoft, a qual é normalmente diferente da utilizada para iniciar sessão no Power BI. Ao iniciar sessão no OneDrive com a sua conta Microsoft, certifique-se de que seleciona a opção Manter sessão iniciada. Dessa forma, o Power BI poderá ligar ao ficheiro em intervalos aproximados de uma hora e garantir que o conjunto de dados no Power BI está sincronizado.

**SharePoint – Sites de Equipa** – Guardar os seus ficheiros do Power BI Desktop no SharePoint – Sites de Equipa é muito semelhante a guardá-los no OneDrive para Empresas. A maior diferença neste caso é como liga ao ficheiro do Power BI. Pode especificar um URL ou ligar à pasta raiz. Também pode <a href="https://support.microsoft.com/office/sync-sharepoint-and-teams-files-with-the-onedrive-sync-app-6de9ede8-5b6e-4503-80b2-6190f3354a88">configurar uma pasta Síncrona</a> que aponta para a pasta do SharePoint. Os ficheiros nessa pasta serão sincronizados com a cópia principal no SharePoint.

## <a name="import-or-connect-to-a-power-bi-desktop-file-from-power-bi"></a>Importar ou ligar a um ficheiro do Power BI Desktop através do Power BI
>[!IMPORTANT]
>O tamanho máximo do ficheiro que pode ser importado no Power BI é de 1 gigabyte.

1. No Power BI, no painel do navegador, clique em **Obter Dados**.
   
   ![Captura de ecrã a mostrar a opção Obter Dados, com o botão no painel de navegação.](media/service-desktop-files/pbid_get_data_button.png)
2. Em **Ficheiros**, clique em **Obter**.
   
   ![Captura de ecrã a mostrar a caixa de diálogo Ficheiros, com o botão Obter.](media/service-desktop-files/pbid_files_get.png)
3. Encontre o ficheiro. Os ficheiros do Power BI Desktop têm a extensão .PBIX.
   
   ![Captura de ecrã a mostrar quatro mosaicos para encontrar o seu ficheiro, com os mosaicos Ficheiro Local, OneDrive Empresas, OneDrive Pessoal e SharePoint.](media/service-desktop-files/pbid_find_your_file.png)

## <a name="publish-a-file-from-power-bi-desktop-to-your-power-bi-site"></a>Publicar um ficheiro do Power BI Desktop para o site do Power BI
Utilizar a funcionalidade Publicar a partir do Power BI Desktop é semelhante a utilizar Obter Dados no Power BI, em termos de importar inicialmente os dados do ficheiro a partir de uma unidade local ou ligar ao mesmo no OneDrive. No entanto, existem diferenças: se fizer o carregamento a partir de uma unidade local, deverá atualizar esses dados frequentemente para garantir que as cópias online e locais dos dados estão atualizadas entre si. 

Segue-se o procedimento mais rápido, mas pode ver [Publicar através do Power BI Desktop](../create-reports/desktop-upload-desktop-files.md) para saber mais.

1. No Power BI Desktop, clique em **Ficheiro** > **Publicar** > **Publicar no Power BI** ou clique em **Publicar** no friso.
   
   ![Captura de ecrã a mostrar a opção Publicar no friso, que apresenta como Publicar a partir do Power B I Desktop.](media/service-desktop-files/pbid_publish.png)
2. Inicie sessão no Power BI. Apenas tem de fazer isto da primeira vez.
   
   Quando terminar, receberá uma ligação para abrir o relatório no site do Power BI.
   
   ![Captura de ecrã a mostrar a caixa de diálogo de confirmação Iniciar sessão, a indicar que iniciou sessão com êxito através de uma ligação para abrir o seu relatório.](media/service-desktop-files/pbid_publishing.png)

## <a name="next-steps"></a>Próximos passos
**Explorar os dados** – Depois de obter dados e relatórios do ficheiro no Power BI, chegou a hora de explorá-los. Se o ficheiro já contiver relatórios, estes aparecerão no painel do navegador em **Relatórios**. Se o ficheiro tinha apenas dados, pode criar novos relatórios; basta clicar com o botão direito do rato no novo conjunto de dados e clicar em **Explorar**.

**Atualizar origens de dados externas** – Se o ficheiro do Power BI Desktop ligar a origens de dados externas, pode configurar a atualização agendada para garantir que o conjunto de dados está sempre atualizado. Na maioria dos casos, é muito fácil configurar a atualização agendada, mas não vamos entrar em detalhes porque está fora do âmbito deste artigo. Veja [Atualização de dados no Power BI](refresh-data.md) para saber mais.
