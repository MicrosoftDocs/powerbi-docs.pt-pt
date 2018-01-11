---
title: "Atualizar um conjunto de dados criado a partir de um livro do Excel – cloud"
description: Atualizar um conjunto de dados criado a partir de um livro do Excel no OneDrive ou SharePoint Online
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
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: 33b6cec4222947695fc3c5b822ff97bf1ef45670
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2017
---
# <a name="refresh-a-dataset-created-from-an-excel-workbook-on-onedrive-or-sharepoint-online"></a>Atualizar um conjunto de dados criado a partir de um livro do Excel no OneDrive ou SharePoint Online
Pode importar livros do Excel que estão armazenados na máquina local ou no armazenamento na cloud, como o OneDrive para Empresas ou o SharePoint Online. Abordaremos as vantagens de utilizar o armazenamento na cloud para os ficheiros do excel. Para obter mais informações sobre como importar os ficheiros do Excel para o Power BI, veja [Obter dados de ficheiros de livro do Excel](service-excel-workbook-files.md).

## <a name="what-are-the-advantages"></a>Quais são as vantagens?
Importar ficheiros do OneDrive ou SharePoint Online é uma ótima maneira de garantir que o trabalho que está a fazer no Excel permanece sincronizado com o serviço Power BI. Todos os dados que carregou no modelo do ficheiro são importados para o conjunto de dados e todos os relatórios que criou no ficheiro são carregados nos Relatórios do Power BI. Caso faça alterações no ficheiro do OneDrive ou SharePoint Online, como adicionar novas medidas, alterar nomes de coluna ou editar visualizações, depois de guardá-las, essas alterações também serão atualizadas no Power BI, normalmente, em menos de uma hora.

Quando importa um livro do Excel do OneDrive pessoal, todos os dados no livro, como tabelas em folhas de cálculo e/ou dados que são carregados no modelo de dados do Excel, bem como a estrutura do modelo de dados, são importados para um novo conjunto de dados no Power BI. Quaisquer visualizações do Power View são recriadas em Relatórios. O Power BI liga-se automaticamente ao livro no OneDrive ou SharePoint Online em intervalos aproximados de sessenta minutos para verificar se há atualizações. Se o livro tiver sido alterado, o Power BI atualizará o conjunto de dados e os relatórios no serviço Power BI.

Pode atualizar o conjunto de dados no serviço Power BI. Quando atualiza manualmente ou agenda a atualização no conjunto de dados, o Power BI liga-se diretamente às origens de dados externas para consultar os dados atualizados e carrega-os no conjunto de dados. A atualização de um conjunto de dados no Power BI não atualiza os dados no livro no OneDrive ou SharePoint Online. 

## <a name="whats-supported"></a>O que é suportado?
No Power BI, há suporte para os recursos Atualizar Agora e Agendamento da Atualização relativamente aos conjuntos de dados criados a partir de ficheiros do Power BI Desktop importados de uma unidade local em que Obter Dados/Editor de Consultas é usado para se ligar a qualquer uma das seguintes origens de dados e carregar dados a partir delas:  

### <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal
* Todas as origens de dados online mostradas no Editor de Consultas e em Obter Dados no Power BI Desktop.
* Todas as origens de dados locais mostradas no Editor de Consultas e em Obter Dados no Power BI Desktop, exceto o ficheiro Hadoop (HDFS) e o Microsoft Exchange.

<!-- Refresh Data sources-->
[!INCLUDE [refresh-datasources](./includes/refresh-datasources.md)]

> [!NOTE]
> Um gateway tem de estar instalado e em execução para que o Power BI se ligue a origens de dados locais e atualize o conjunto de dados.
> 
> 

## <a name="onedrive-or-onedrive-for-business-whats-the-difference"></a>OneDrive ou OneDrive para Empresas. Qual é a diferença?
Se tiver um OneDrive Pessoal e um OneDrive para Empresas, é recomendável manter no OneDrive para Empresas todos os ficheiros que deseja importar para o Power BI. A razão é esta: provavelmente usa duas contas diferentes para entrar neles.

A ligação ao OneDrive para Empresas no Power BI é normalmente contínua, porque a conta que usa para entrar no Power BI é geralmente a conta usada para entrar no OneDrive para Empresas. Mas com o OneDrive pessoal, provavelmente, entrará com outra [conta Microsoft](http://www.microsoft.com/account/default.aspx).

Ao entrar com a sua conta Microsoft, certifique-se de que seleciona Manter a sessão iniciada. O Power BI pode então sincronizar as atualizações feitas no ficheiro do Power BI Desktop com conjuntos de dados no Power BI  
    ![](media/refresh-excel-file-onedrive/refresh_signin_keepmesignedin.png)

Se fizer alterações no ficheiro no OneDrive que não podem ser sincronizadas com o conjunto de dados ou relatórios no Power BI por as suas credenciais de conta Microsoft terem sido alteradas, terá de se ligar e importar o ficheiro novamente do OneDrive pessoal.

## <a name="options-for-connecting-to-excel-file"></a>Opções de ligação ao ficheiro do Excel
Quando se liga a um livro do Excel no OneDrive para Empresas ou SharePoint Online, terá duas opções sobre como inserir o conteúdo do seu livro no Power BI.

[**Importar dados do Excel no Power BI**](service-excel-workbook-files.md#import-or-connect-to-an-excel-workbook-from-power-bi) – Ao importar um livro do Excel através do OneDrive para Empresas ou SharePoint Online, este funcionará da forma descrita acima.

[**Ligar, gerir e visualizar o Excel no Power BI**](service-excel-workbook-files.md#one-excel-workbook--two-ways-to-use-it) – Ao usar esta opção, cria uma ligação direta do Power BI ao seu livro no OneDrive para Empresas ou SharePoint Online.

Quando se liga a um livro do Excel dessa forma, não é criado um conjunto de dados no Power BI. No entanto, o livro irá aparecer no serviço Power BI em Relatórios com um ícone do Excel junto ao nome. Ao contrário do Excel Online, quando se liga ao livro do Power BI, caso existam neste ligações a origens de dados externas que carregam dados no modelo de dados do Excel, é possível configurar um agendamento de atualização.

Quando configura um agendamento de atualização dessa forma, a única diferença é que os dados atualizados são inseridos no modelo de dados do livro no OneDrive ou SharePoint Online, em vez de um conjunto de dados no Power BI.

## <a name="how-do-i-make-sure-data-is-loaded-to-the-excel-data-model"></a>Como me certifico de que os dados são carregados no modelo de dados do Excel?
Quando usa o Power Query (Obter e Transformar dados no Excel 2016) para se ligar a uma origem de dados, tem várias opções de onde carregar os dados. Para se certificar de que carrega os dados no modelo de dados, tem de selecionar a opção **Adicionar estes dados ao Modelo de Dados** na caixa de diálogo **Carregar para**.

> [!NOTE]
> As presentes imagens mostram o Excel 2016.
> 
> 

Em **Navegador**, clique em **Carregar para...**  
    ![](media/refresh-excel-file-onedrive/refresh_loadtodm_1.png)

Ou então, se clicar em **Editar** no Navegador, abrirá o Editor de Consultas. Aí é possível clicar em **Fechar e Carregar para...**  
    ![](media/refresh-excel-file-onedrive/refresh_loadtodm_2.png)

Em seguida, em **Carregar para**, certifique-se de que selecionou **Adicionar estes dados ao Modelo de Dados**.  
    ![](media/refresh-excel-file-onedrive/refresh_loadtodm_3.png)

### <a name="what-if-i-use-get-external-data-in-power-pivot"></a>E se eu usar o recurso Obter Dados Externos no Power Pivot?
Sem problemas. Sempre que usa o Power Pivot para se ligar e consultar dados de uma origem de dados local ou online, os dados são carregados automaticamente no modelo de dados.

## <a name="how-do-i-schedule-refresh"></a>Como faço para agendar uma atualização?
Quando configura um agendamento de atualização, o Power BI liga-se diretamente às origens de dados com informações de ligação e credenciais no conjunto de dados para consultar os dados atualizados e, em seguida, carrega os dados atualizados no conjunto de dados. Todas as visualizações em relatórios e em dashboards baseadas nesse conjunto de dados no serviço Power BI também são atualizadas.

Para detalhes sobre como configurar a atualização agendada, consulte [Configurar a atualização agendada](refresh-scheduled-refresh.md).

## <a name="when-things-go-wrong"></a>Quando algo corre mal
Quando as coisas correm mal, normalmente, deve-se ao facto de o Power BI não conseguir entrar nas origens de dados. Outra razão é o conjunto de dados ligar-se a uma origem de dados local e o gateway estar offline. Certifique-se de que o Power BI pode entrar nas origens de dados. Se uma palavra-passe que utiliza para entrar numa origem de dados for alterada ou o Power BI for desligado de uma origem de dados, certifique-se de que se inscreve novamente nas suas origens de dados nas Credenciais da Origem de Dados.

Lembre-se de deixar marcada a opção **Enviar-me e-mail de notificação de falha de atualização**. Irá querer saber de imediato sobre uma falha de uma atualização agendada.

## <a name="important-notes"></a>Notas importantes
\*Não há suporte para a atualização de feeds OData ligados ao Power Pivot e consultados por meio do mesmo. Ao utilizar um feed OData como uma origem de dados, utilize o Power Query.

## <a name="troubleshooting"></a>Resolução de problemas
Por vezes, atualizar os dados pode não correr como esperado. Normalmente, este problema está ligado a um gateway. Veja os artigos de resolução de problemas de gateways para ferramentas e problemas conhecidos.

[Resolução de problemas do gateway de dados no local](service-gateway-onprem-tshoot.md)

[Resolver problemas do Power BI Gateway - Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

