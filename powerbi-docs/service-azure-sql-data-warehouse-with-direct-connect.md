---
title: Azure SQL Data Warehouse com DirectQuery
description: Azure SQL Data Warehouse com DirectQuery
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/20/2018
ms.author: maghan
LocalizationGroup: Data from databases
ms.openlocfilehash: a09b9bed97f34b317fadc6b60216019a6c562d0f
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54295690"
---
# <a name="azure-sql-data-warehouse-with-directquery"></a>Azure SQL Data Warehouse com DirectQuery
O Azure SQL Data Warehouse com DirectQuery permite criar relatórios dinâmicos com base nos dados e nas métricas já existentes no Azure SQL Data Warehouse. Com o DirectQuery, as consultas são enviadas de volta para o Azure SQL Data Warehouse em tempo real à medida que explora os dados. As consultas em tempo real, combinadas com o dimensionamento do SQL Data Warehouse, permitem aos utilizadores criar, em minutos, relatórios dinâmicos referentes a terabytes de dados. Além disso, a introdução do botão **Abrir no Power BI** permite que os utilizadores liguem diretamente o Power BI ao SQL Data Warehouse sem precisar de especificar manualmente as informações.

Ao usar o conector do SQL Data Warehouse:

* Especifique o nome de servidor completamente qualificado quando ligar (veja abaixo para obter mais detalhes)
* Certifique-se de que as regras de firewall para o servidor estão configuradas para "Permitir acesso aos serviços do Azure"
* Cada ação, como selecionar uma coluna ou adicionar um filtro, consultará diretamente o armazém de dados
* Os mosaicos são definidos para serem atualizados aproximadamente a cada 15 minutos e a atualização não tem de ser agendada.  A atualização pode ser ajustada nas Definições avançadas quando se ligar.
* As Perguntas e Respostas não estão disponíveis para conjuntos de dados do DirectQuery
* As alterações de esquema não são selecionadas automaticamente

Estas restrições e notas podem mudar à medida que continuamos a melhorar as experiências. Os passos para ligar são detalhados abaixo.

## <a name="using-the-open-in-power-bi-button"></a>Através do botão "Abrir no Power BI"

> [!Important]
> Temos melhorado a nossa conectividade com o Azure SQL Data Warehouse.  Para obter a melhor experiência para se ligar à origem de dados do Azure SQL Data Warehouse, utilize o Power BI Desktop.  Assim que criar o seu modelo e relatório, pode publicá-lo no serviço Power BI.  O conector direto do Azure SQL Data Warehouse no serviço Power BI foi preterido.
>

A forma mais fácil de se mover entre o SQL Data Warehouse e o Power BI é com o botão **Abrir no Power BI** do portal do Azure. Este botão permite-lhe começar a criar novos dashboards no Power BI.

1. Para começar, navegue até à instância do SQL Data Warehouse no portal do Azure. Tenha em atenção que, de momento, o SQL Data Warehouse só está presente no portal de Pré-visualização do Azure.
2. Clique no botão **Abrir no Power BI**
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/openinpowerbi.png)
3. Se não conseguir iniciar sessão diretamente ou se não tiver uma conta do Power BI, terá de iniciar sessão.
4. Será direcionado para a página de ligação do SQL Data Warehouse, com as informações do SQL Data Warehouse pré-preenchidas. Introduza as credenciais e selecione Ligar para criar uma ligação.

## <a name="connecting-through-power-bi"></a>Ligar através do Power BI
O SQL Data Warehouse também está listado na página Obter Dados do Power BI. 

1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.  
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/getdatabutton.png)
2. Em **Bases de dados**, selecione **Obter**.
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/databases.png)
3. Selecione **SQL Data Warehouse** \> **Ligar**.
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/azuresqldatawarehouseconnect.png)
4. Introduza as informações necessárias para ligar. A secção **A localizar Parâmetros** a seguir mostra onde estes dados podem estar localizados no Portal do Azure.
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/servername.png)
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/servernamewithadvanced.png)
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/username.png)
   
   > [!NOTE]
   > O nome de utilizador é um utilizador que está definido na instância do Azure SQL Data Warehouse.
   > 
   > 
5. Analise o conjunto de dados ao selecionar o novo mosaico ou o conjunto de dados recém-criado, indicado pelo asterisco. Este conjunto de dados terá o mesmo nome da base de dados.
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/dataset2.png)
6. Pode explorar todas as tabelas e colunas. Selecionar uma coluna resultará no envio de uma consulta de volta para a origem, o que cria dinamicamente o elemento visual. Os filtros também serão convertidos em consultas de volta para o armazém de dados. Estes elementos visuais podem ser guardados num novo relatório e afixados ao dashboard.
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/explore3.png)

## <a name="finding-parameter-values"></a>Localizar Valores de Parâmetro
O nome de servidor completamente qualificado e o nome da base de dados podem ser encontrados no portal do Azure. Tenha em atenção que, de momento, o SQL Data Warehouse só está presente no portal de Pré-visualização do Azure.

![](media/service-azure-sql-data-warehouse-with-direct-connect/azureportal.png)

> [!NOTE]
> Se o seu inquilino do Power BI estiver na mesma região que o Azure SQL Data Warehouse, não existirão custos de saída. Pode saber onde o seu inquilino do Power BI se encontra com [estas instruções](https://docs.microsoft.com/power-bi/service-admin-where-is-my-tenant-located).
>

## <a name="next-steps"></a>Próximos passos
[O que é o Power BI?](power-bi-overview.md)  
[Obter Dados para o Power BI](service-get-data.md)  
[Azure SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-overview-what-is/)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)