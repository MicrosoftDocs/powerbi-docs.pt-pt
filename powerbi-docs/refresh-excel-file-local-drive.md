---
title: "Atualizar um conjunto de dados criado com base numa pasta de trabalho do Excel – local"
description: Atualizar um conjunto de dados criado com base numa pasta do Excel numa unidade local
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: fc061d2f8c85a53028e6de82e4a1e21057be6c75
ms.sourcegitcommit: b3ee37e1587f1269ee7dd9daf1685a06dea3b50c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/23/2017
---
# <a name="refresh-a-dataset-created-from-an-excel-workbook-on-a-local-drive"></a>Atualizar um conjunto de dados criado com base numa pasta do Excel numa unidade local
## <a name="whats-supported"></a>O que é suportado?
No Power BI, há suporte para os recursos Atualizar Agora e Agendar Atualização para os conjuntos de dados criados por meio de pastas de trabalho do Excel importadas de uma unidade local em que o Power Query (Obter e Transformar dados no Excel 2016) ou o Power Pivot é usado para se conectar a qualquer uma das seguintes origens de dados e carregar dados no modelo de dados do Excel:  

### <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal
* Todas as origens de dados online mostradas no Power Query.
* Todas as origens de dados locais mostradas no Power Query, exceto o ficheiro do Hadoop (HDFS) e o Microsoft Exchange.
* Todas as origens de dados online mostradas no Power Pivot.\*
* Todas as origens de dados locais mostradas no Power Pivot, exceto o ficheiro do Hadoop (HDFS) e o Microsoft Exchange.

<!-- Refresh Data sources-->
[!INCLUDE [refresh-datasources](./includes/refresh-datasources.md)]

> **Observações:**  
> 
> * Um gateway deve ser instalado e estar em execução para que o Power BI se ligue a origens de dados locais e atualize o conjunto de dados.
> * Ao utilizar o Excel 2013, certifique-se de que atualizou o Power Query para a versão mais recente.
> * Não há suporte para a atualização para pastas de trabalho do Excel importadas de uma unidade local em que os dados existem somente em planilhas ou tabelas vinculadas. Há suporte para a atualização para dados de folha de cálculo se eles forem armazenados e importados do OneDrive. Para saber mais, veja [Atualizar um conjunto de dados criado com base numa pasta de trabalho do Excel no OneDrive ou SharePoint Online](refresh-excel-file-onedrive.md).
> * Quando atualiza um conjunto de dados criado através de uma pasta de trabalho do Excel importada de uma unidade local, apenas os dados consultados das origens de dados são atualizados. Se alterar a estrutura do modelo de dados no Excel ou no Power Pivot, por exemplo, criar uma nova medida ou alterar o nome de uma coluna, essas alterações não serão copiadas no conjunto de dados. Se fizer essas alterações, precisa de carregar ou publicar novamente a pasta de trabalho. Se pretende fazer alterações regulares na estrutura da pasta de trabalho e quiser que elas sejam refletidas no conjunto de dados no Power BI sem a necessidade de carregar novamente, considere colocar a sua pasta de trabalho no OneDrive. O Power BI atualiza automaticamente a estrutura e os dados de planilha das pastas de trabalho armazenadas e importadas do OneDrive.
> 
> 

## <a name="how-do-i-make-sure-data-is-loaded-to-the-excel-data-model"></a>Como ter certeza de que os dados são carregados no modelo de dados do Excel?
Quando utiliza o Power Query (Obter e transformar dados no Excel 2016) para se conectar a uma origem de dados, tem várias opções de onde carregar os dados. Para se certificar de que carrega os dados no modelo de dados, deve selecionar a opção **Adicionar esses dados ao Modelo de Dados** na caixa de diálogo **Carregar Para**.

> [!NOTE]
> As imagens aqui mostram o Excel 2016.
> 
> 

Em **Navegador**, clique em **Carregar para...**  
    ![](media/refresh-excel-file-local-drive/refresh_loadtodm_1.png)

Ou então, se clicar em **Editar** no Navegador, abre o Editor de Consultas. Lá, é possível clicar em **Fechar e Carregar para...**  
    ![](media/refresh-excel-file-local-drive/refresh_loadtodm_2.png)

Em seguida, em **Carregar para**, certifique-se de que selecionou **Adicionar esses dados ao Modelo de Dados**.  
    ![](media/refresh-excel-file-local-drive/refresh_loadtodm_3.png)

### <a name="what-if-i-use-get-external-data-in-power-pivot"></a>E se eu utilizar a funcionalidade Obter Dados Externos no Power Pivot?
Sem problemas. Sempre que utilizar o Power Pivot para se conectar e consultar dados de uma origem de dados local ou online, os dados serão carregados automaticamente no modelo de dados.

## <a name="how-do-i-schedule-refresh"></a>Como faço para agendar uma atualização?
Quando configurar um agendamento de atualização, o Power BI liga-se diretamente às origens de dados usando as informações de conexão e as credenciais no conjunto de dados para consultar os dados atualizados e, em seguida, carrega os dados atualizados no conjunto de dados. Todas as visualizações em relatórios e em dashboards baseadas nesse conjunto de dados no serviço Power BI também são atualizadas.

Para obter detalhes sobre como configurar a atualização de agendamento, veja [Configurar uma atualização agendada](refresh-scheduled-refresh.md).

## <a name="when-things-go-wrong"></a>Quando há algum problema
Quando as coisas dão errado, normalmente, isso se deve ao fato de o Power BI não conseguir entrar em origens de dados. Outra razão é que se o conjunto de dados se conecta a uma origem de dados local, o gateway fica offline. Verifique se o Power BI pode entrar em origens de dados. Se uma palavra-passe que utiliza para entrar numa origem de dados for alterada ou o Power BI for desconectado de uma origem de dados, certifique-se de que tenta entrar novamente nas suas origens de dados novamente nas Credenciais da Origem de Dados.

Lembre-se de deixar a opção **Enviar e-mail de notificação de falha de atualização para mim marcada**. Vai querer saber imediatamente de uma falha numa atualização agendada.

>[!IMPORTANT]
>Não é suportada a atualização de feeds OData ligados e consultados do Power Pivot. Ao utilizar um feed OData como uma origem de dados, use o Power Query.

## <a name="troubleshooting"></a>Resolução de problemas
Por vezes, atualizar os dados pode não correr como esperado. Normalmente, este problema está ligado a um gateway. Veja os artigos de resolução de problemas de gateways para ferramentas e problemas conhecidos.

[Resolução de problemas do gateway de dados no local](service-gateway-onprem-tshoot.md)

[Resolver problemas do Power BI Gateway - Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)

## <a name="next-steps"></a>Próximos passos
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

