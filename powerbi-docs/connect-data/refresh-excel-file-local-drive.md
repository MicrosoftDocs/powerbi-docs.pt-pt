---
title: Atualizar um conjunto de dados criado com base numa pasta de trabalho do Excel – local
description: Atualizar um conjunto de dados criado com base numa pasta do Excel numa unidade local
author: davidiseminger
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Data refresh
ms.openlocfilehash: ef9c39f6c00738718d88dd485430b150ad95ec50
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2020
ms.locfileid: "86216347"
---
# <a name="refresh-a-dataset-created-from-an-excel-workbook-on-a-local-drive"></a>Atualizar um conjunto de dados criado com base numa pasta do Excel numa unidade local
## <a name="whats-supported"></a>O que tem suporte?
No Power BI, há suporte para os recursos Atualizar Agora e Agendar Atualização para os conjuntos de dados criados por meio de pastas de trabalho do Excel importadas de uma unidade local em que o Power Query (Obter e Transformar dados no Excel 2016) ou o Power Pivot é usado para se conectar a qualquer uma das seguintes origens de dados e carregar dados no modelo de dados do Excel:  

### <a name="power-bi-gateway---personal"></a>Gateway do Power BI - Pessoal
* Todas as origens de dados online mostradas no Power Query.
* Todas as origens de dados locais apresentadas no Power Query, exceto o ficheiro do Hadoop (HDFS) e o Microsoft Exchange.
* Todas as origens de dados online mostradas no Power Pivot.\*
* Todas as origens de dados locais mostradas no Power Pivot, exceto o ficheiro do Hadoop (HDFS) e o Microsoft Exchange.

<!-- Refresh Data sources-->
[!INCLUDE [refresh-datasources](../includes/refresh-datasources.md)]

> **Observações:**  
> 
> * Um gateway deve ser instalado e estar em execução para que o Power BI se ligue a origens de dados locais e atualize o conjunto de dados.
> * Ao utilizar o Excel 2013, certifique-se de que atualizou o Power Query para a versão mais recente.
> * Não há suporte para a atualização para pastas de trabalho do Excel importadas de uma unidade local em que os dados existem somente em planilhas ou tabelas vinculadas. Há suporte para a atualização para dados de folha de cálculo se eles forem armazenados e importados do OneDrive. Para saber mais, veja [Atualizar um conjunto de dados criado com base numa pasta de trabalho do Excel no OneDrive ou SharePoint Online](refresh-excel-file-onedrive.md).
> * Quando atualiza um conjunto de dados criado através de uma pasta de trabalho do Excel importada de uma unidade local, apenas os dados consultados das origens de dados são atualizados. Se alterar a estrutura do modelo de dados no Excel ou no Power Pivot, por exemplo, criar uma nova medida ou alterar o nome de uma coluna, essas alterações não serão copiadas no conjunto de dados. Se fizer essas alterações, precisa de carregar ou publicar novamente a pasta de trabalho. Se pretende fazer alterações regulares na estrutura da pasta de trabalho e quiser que elas sejam refletidas no conjunto de dados no Power BI sem a necessidade de carregar novamente, considere colocar a sua pasta de trabalho no OneDrive. O Power BI atualiza automaticamente a estrutura e os dados de planilha das pastas de trabalho armazenadas e importadas do OneDrive.
> 
> 

## <a name="how-do-i-make-sure-data-is-loaded-to-the-excel-data-model"></a>Como ter certeza de que os dados são carregados no modelo de dados do Excel?
Quando usa o Power Query (Obter e Transformar dados no Excel 2016) para se ligar a uma origem de dados, tem várias opções de onde carregar os dados. Para se certificar de que carrega os dados no modelo de dados, tem de selecionar a opção **Adicionar estes dados ao Modelo de Dados** na caixa de diálogo **Carregar para**.

> [!NOTE]
> As presentes imagens mostram o Excel 2016.
> 
> 

Em **Navegador**, clique em **Carregar para...**  
    ![Captura de ecrã a mostrar a opção Carregar para no Navegador, com a seleção de Carregar para.](media/refresh-excel-file-local-drive/refresh_loadtodm_1.png)

Ou então, se clicar em **Editar** no Navegador, abrirá o Editor de Consultas. Aí é possível clicar em **Fechar e Carregar para...**  
    ![Captura de ecrã a mostrar o separador Home Page no Navegador, com as seleções Fechar e Carregar para.](media/refresh-excel-file-local-drive/refresh_loadtodm_2.png)

Em seguida, em **Carregar para**, certifique-se de que selecionou **Adicionar estes dados ao Modelo de Dados**.  
    ![Captura de ecrã a mostrar a caixa de diálogo Carregar para, com a caixa de verificação Adicionar estes dados ao Modelo de Dados selecionada.](media/refresh-excel-file-local-drive/refresh_loadtodm_3.png)

### <a name="what-if-i-use-get-external-data-in-power-pivot"></a>E se eu usar o recurso Obter Dados Externos no Power Pivot?
Não há problema. Sempre que usa o Power Pivot para se ligar e consultar dados de uma origem de dados local ou online, os dados são carregados automaticamente no modelo de dados.

## <a name="how-do-i-schedule-refresh"></a>Como faço para agendar uma atualização?
Quando configurar um agendamento de atualização, o Power BI ligará diretamente às origens de dados através das informações de ligação e das credenciais no conjunto de dados para consultar os dados atualizados e, em seguida, carregará os dados atualizados para o conjunto de dados. Todas as visualizações em relatórios e em dashboards baseadas nesse conjunto de dados no serviço do Power BI também são atualizadas.

Para obter detalhes sobre como configurar a atualização de agendamento, veja [Configurar uma atualização agendada](refresh-scheduled-refresh.md).

## <a name="when-things-go-wrong"></a>Quando acontece algo de errado
Quando ocorre algo errado, normalmente isso deve-se ao facto de o Power BI não conseguir iniciar sessão nas origens de dados ou se o conjunto de dados ligar a uma origem de dados no local, o gateway ficar offline. Certifique-se de que o Power BI consegue iniciar sessão nas origens de dados. Se uma palavra-passe que utiliza para iniciar sessão numa origem de dados for alterada ou a sessão do Power BI for terminada numa origem de dados, certifique-se de que tenta iniciar sessão novamente nas origens de dados em Credenciais da Origem de Dados.

Lembre-se de deixar marcada a opção **Enviar-me e-mail de notificação de falha de atualização**. Vai querer saber imediatamente de uma falha numa atualização agendada.

>[!IMPORTANT]
>Não é suportada a atualização de feeds OData ligados e consultados do Power Pivot. Ao utilizar um feed OData como uma origem de dados, use o Power Query.

## <a name="troubleshooting"></a>Resolução de problemas
Por vezes, atualizar os dados pode não correr como esperado. Normalmente, este problema está ligado a um gateway. Veja os artigos de resolução de problemas de gateways para ferramentas e problemas conhecidos.

[Resolução de problemas do Gateway de dados no local](service-gateway-onprem-tshoot.md)

[Resolver problemas do Power BI Gateway - Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)

## <a name="next-steps"></a>Próximos passos
Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
