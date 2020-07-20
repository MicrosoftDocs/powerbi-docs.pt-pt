---
title: Obter dados de ficheiros CSV (Valores Separados por Vírgula)
description: Saiba como obter dados de ficheiros CSV no Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 20c289648dc6e9b9784335c0d92f6725328dfffc
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2020
ms.locfileid: "86216330"
---
# <a name="get-data-from-comma-separated-value-csv-files"></a>Obter dados de ficheiros CSV (Valores Separados por Vírgula)
![Ícone de CSV](media/service-comma-separated-value-files/csv_icon.png)

Os ficheiros de valores separados por vírgula, geralmente conhecidos como .CSV, são ficheiros de texto simples com linhas de dados em que cada valor é separado por uma vírgula. Esses tipos de ficheiros podem conter grandes quantidades de dados num tamanho do ficheiro relativamente pequeno, tornando-os uma origem de dados ideal para o Power BI. É possível transferir um ficheiro .CSV de exemplo [aqui](https://go.microsoft.com/fwlink/?LinkID=619356).

Caso tenha um .CSV, é altura de o inserir no seu site do Power BI como um conjunto de dados, no qual será possível começar a explorar os seus dados, criar alguns dashboards e partilhar suas ideias com outras pessoas.

>[!TIP]
>Muitas organizações produzem um .CSV com dados atualizados diariamente. Para garantir que o conjunto de dados no Power BI permanece em sincronização com o ficheiro atualizado, certifique-se de que o ficheiro é guardado no OneDrive com o mesmo nome.

## <a name="where-your-file-is-saved-makes-a-difference"></a>O local em que o ficheiro é salvo faz a diferença
**Local** - Caso o ficheiro .CSV seja salvo numa unidade local no computador ou em outro local em sua organização, por meio do Power BI, é possível *importar* o ficheiro para o Power BI. Na verdade, o ficheiro permanecerá na unidade local; portanto, o ficheiro completo não é, de fato, importado para o Power BI. O que realmente ocorre é que um novo conjunto de dados é criado no Power BI e os dados do ficheiro .CSV são carregados nesse conjunto de dados.

**OneDrive - Business** – caso tenha o OneDrive para Empresas e entre com a mesma conta usada para o início de sessão no Power BI, essa é, sem dúvida, a forma mais eficiente de manter o ficheiro .CSV, bem como o seu conjunto de dados, os seus relatórios e dashboards no Power BI em sincronia. Visto que tanto o Power BI quanto o OneDrive ficam na nuvem, o Power BI se *conecta* ao seu ficheiro no OneDrive em intervalos aproximados de sessenta minutos. Caso sejam encontradas alterações, o conjunto de dados, os relatórios e os dashboards serão atualizados automaticamente no Power BI.

**OneDrive - Pessoal** – Caso os ficheiros sejam guardados na sua própria conta do OneDrive, vai aproveitar vários dos mesmos benefícios que teria com o OneDrive para Empresas. A maior diferença é que, na primeira ligação ao ficheiro (usando Obter Dados > Ficheiros > OneDrive – Personal), é necessário entrar no OneDrive com a sua conta da Microsoft, que normalmente é diferente daquela usada para iniciar a sessão no Power BI. Ao entrar no OneDrive com sua conta da Microsoft, certifique-se de selecionar a opção Mantenha-me conectado. Dessa forma, o Power BI poderá se conectar ao seu ficheiro em intervalos aproximados de sessenta minutos e garantir que o conjunto de dados no Power BI está em sincronia.

**SharePoint – Sites de Equipa** – Guardar os seus ficheiros do Power BI Desktop no SharePoint – Sites de Equipa é muito semelhante a guardá-los no OneDrive para Empresas. A maior diferença neste caso é como liga ao ficheiro do Power BI. Pode especificar um URL ou ligar à pasta raiz.

## <a name="import-or-connect-to-a-csv-file"></a>Importar ou conectar-se a um ficheiro .CSV
>[!IMPORTANT]
>O tamanho máximo do ficheiro que pode ser importado no Power BI é de 1 gigabyte.

1. No Power BI, no painel do navegador, clique em **Obter Dados**.
   
   ![Captura de ecrã a mostrar a opção Obter Dados no Power B I Desktop, com o botão no painel do navegador.](media/service-comma-separated-value-files/csv_get_data_button.png)
2. Em **Ficheiros**, clique em **Obter**.
   
   ![Captura de ecrã a mostrar a caixa de diálogo Ficheiro com o botão Obter.](media/service-comma-separated-value-files/csv_files_get.png)
3. Encontre o ficheiro.
   
   ![Captura de ecrã a mostrar quatro mosaicos para encontrar o seu ficheiro, com uma seleção de Ficheiro Local, OneDrive Empresas, OneDrive Pessoal e SharePoint.](media/service-comma-separated-value-files/csv_find_your_file.png)

## <a name="next-steps"></a>Próximos passos
**Explore os dados** – depois de obter dados do seu ficheiro no Power BI, é altura de explorá-los. Basta clicar com o botão direito do mouse no novo conjunto de dados e clicar em **Explorar**.

**Agendar atualização** – Caso o ficheiro seja salvo numa unidade local, é possível configurar a atualização agendada para que o conjunto de dados e os relatórios no Power BI permaneçam atualizados. Para saber mais, veja [Atualização de dados no Power BI](refresh-data.md). Se o ficheiro for salvo no OneDrive, o Power BI será sincronizado de forma automática com ele a cada hora, aproximadamente.

