---
title: "Obter dados de ficheiros CSV (Valores Separados por Vírgula)"
description: Saiba como obter dados de ficheiros CSV no Power BI
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: complete
qualitydate: 03/30/2016
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: 5e6d981978fbf7690b797e5f07c1266e4a7c6b99
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2017
---
# <a name="get-data-from-comma-separated-value-csv-files"></a>Obter dados de ficheiros CSV (Valores Separados por Vírgula)
![](media/service-comma-separated-value-files/csv_icon.png)

Os ficheiros de valores separados por vírgula, geralmente conhecidos como .CSV, são ficheiros de texto simples com linhas de dados em que cada valor é separado por uma vírgula. Esses tipos de ficheiros podem conter grandes quantidades de dados num tamanho do ficheiro relativamente pequeno, tornando-os uma origem de dados ideal para o Power BI. É possível transferir um ficheiro .CSV de exemplo [aqui](http://go.microsoft.com/fwlink/?LinkID=619356).

Caso tenha um .CSV, é altura de o inserir no seu site do Power BI como um conjunto de dados, no qual será possível começar a explorar os seus dados, criar alguns dashboards e partilhar suas ideias com outras pessoas.

>[!TIP]
>Muitas organizações produzem um .CSV com dados atualizados diariamente. Para garantir que o conjunto de dados no Power BI permanece em sincronização com o ficheiro atualizado, certifique-se de que o ficheiro é guardado no OneDrive com o mesmo nome.

## <a name="where-your-file-is-saved-makes-a-difference"></a>O local em que o ficheiro é salvo faz a diferença
**Local** - Caso o ficheiro .CSV seja salvo numa unidade local no computador ou em outro local em sua organização, por meio do Power BI, é possível *importar* o ficheiro para o Power BI. Na verdade, o ficheiro permanecerá na unidade local; portanto, o ficheiro completo não é, de fato, importado para o Power BI. O que realmente ocorre é que um novo conjunto de dados é criado no Power BI e os dados do ficheiro .CSV são carregados nesse conjunto de dados.

**OneDrive - Business** – caso tenha o OneDrive para Empresas e entre com a mesma conta usada para o início de sessão no Power BI, essa é, sem dúvida, a forma mais eficiente de manter o ficheiro .CSV, bem como o seu conjunto de dados, os seus relatórios e dashboards no Power BI em sincronia. Visto que tanto o Power BI quanto o OneDrive ficam na nuvem, o Power BI se *conecta* ao seu ficheiro no OneDrive em intervalos aproximados de sessenta minutos. Caso sejam encontradas alterações, o conjunto de dados, os relatórios e os dashboards são atualizados automaticamente no Power BI.

**OneDrive - Personal** – Caso os ficheiros sejam guardados na sua própria conta do OneDrive, vai aproveitar vários dos mesmos benefícios que teria com o OneDrive for Business. A maior diferença é que, na primeira ligação ao ficheiro (usando Obter Dados > Ficheiros > OneDrive – Personal), é necessário entrar no OneDrive com a sua conta da Microsoft, que normalmente é diferente daquela usada para iniciar a sessão no Power BI. Ao entrar no OneDrive com sua conta da Microsoft, certifique-se de selecionar a opção Mantenha-me conectado. Dessa forma, o Power BI poderá se conectar ao seu ficheiro em intervalos aproximados de sessenta minutos e garantir que o conjunto de dados no Power BI está em sincronia.

**SharePoint – Sites de Equipe** – Salvar seus ficheiros do Power BI Desktop no SharePoint – Sites de Equipe é muito semelhante a salvá-los no OneDrive for Business. A maior diferença nesse caso é como se liga ao ficheiro do Power BI. É possível especificar um URL ou ligar-se à pasta raiz.

## <a name="import-or-connect-to-a-csv-file"></a>Importar ou conectar-se a um ficheiro .CSV
>[!IMPORTANT]
>O tamanho máximo do ficheiro que pode ser importado no Power BI é de 1 gigabyte.

1. No Power BI, no painel do navegador, clique em **Obter Dados**.
   
   ![](media/service-comma-separated-value-files/csv_get_data_button.png)
2. Em **Ficheiros**, clique em **Obter**.
   
   ![](media/service-comma-separated-value-files/csv_files_get.png)
3. Encontre o ficheiro.
   
   ![](media/service-comma-separated-value-files/csv_find_your_file.png)

## <a name="next-steps"></a>Próximos passos
**Explore os dados** – depois de obter dados do seu ficheiro no Power BI, é altura de explorá-los. Basta clicar com o botão direito do mouse no novo conjunto de dados e clicar em **Explorar**.

**Agendar atualização** – Caso o ficheiro seja salvo numa unidade local, é possível configurar a atualização agendada para que o conjunto de dados e os relatórios no Power BI permaneçam atualizados. Para saber mais, veja [Atualização de dados no Power BI](refresh-data.md). Se o ficheiro for salvo no OneDrive, o Power BI será sincronizado de forma automática com ele a cada hora, aproximadamente.

