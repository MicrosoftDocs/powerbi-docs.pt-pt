---
title: SQL Server Analysis Services live data in Power BI (Dados dinâmicos do SQL Server Analysis Services no Power BI)
description: Dados dinâmicos do SQL Server Analysis Services no Power BI. Isto é feito através de uma origem de dados configurada para um gateway empresarial.
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
author: Minewiskan
ms.author: owend
ms.reviewer: ''
ms.custom: ''
ms.date: 08/10/2017
LocalizationGroup: Data from databases
ms.openlocfilehash: c88c0d56d24f12edf30c2c79ddebb13fa941695a
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85238199"
---
# <a name="sql-server-analysis-services-live-data-in-power-bi"></a>SQL Server Analysis Services live data in Power BI (Dados dinâmicos do SQL Server Analysis Services no Power BI)

No Power BI, existem duas formas de ligar a um servidor do SQL Server Analysis Services. Em **Obter dados**, pode lugar a um servidor do SQL Server Analysis Services ou a um [ficheiro do Power BI Desktop](service-desktop-files.md) ou [livro do Excel](service-excel-workbook-files.md), já ligado a um servidor do Analysis Services. Como melhor prática, a Microsoft recomenda vivamente que utilize o Power BI Desktop devido à riqueza do conjunto de ferramentas e à capacidade para manter uma cópia de segurança do ficheiro do Power BI Desktop localmente.

>[!IMPORTANT]
> * Para ligar em direto a um servidor do Analysis Services, é necessário um administrador instalar e configurar um Gateway de dados no local. Para obter mais informações, veja [Gateway de dados no local](service-gateway-onprem.md).
> * Quando utilizar o gateway, os seus dados permanecem no local.  Os relatórios criados com base nesses dados são guardados no serviço Power BI. 
> * A [consulta de linguagem natural com Perguntas e Respostas](../create-reports/service-q-and-a-direct-query.md) está em pré-visualização para ligações em direto do Analysis Services.

## <a name="to-connect-to-a-model-from-get-data"></a>Para ligar a um modelo a partir de Obter dados

1. Em **A Minha Área de Trabalho**, selecione **Obter dados**. Também pode mudar para uma área de trabalho de grupo, se estiver disponível.

   ![Botão Ligar-se para obter dados](media/sql-server-analysis-services-tabular-data/connecttoas_getdatabutton.png)

2. Selecione **Bases de Dados e Mais**.

   ![Ligar-se para obter dados 1](media/sql-server-analysis-services-tabular-data/connecttoas_getdata_1.png)

3. Selecione **SQL Server Analysis Services** > **Ligar**.

   ![Ligar-se para obter dados 2](media/sql-server-analysis-services-tabular-data/connecttoas_getdata_2.png)

4. Selecione um servidor. Se não vir nenhum servidor listado aqui, significa que não está configurado um gateway e uma origem de dados ou a conta não está listada no separador **Utilizadores** da origem de dados, no gateway. Contacte o seu administrador.

5. Selecione o modelo ao qual quer ligar. Pode ser Tabular ou Multidimensional.

Depois de ligar ao modelo, este será apresentado no site do Power BI em **A Minha Área de Trabalho/Conjuntos de Dados**. Se mudou para uma área de trabalho de grupo, o conjunto de dados será apresentado no grupo.

![Ligar-se a conjunto de dados](media/sql-server-analysis-services-tabular-data/connecttoas_dataset_5.png)

## <a name="dashboard-tiles"></a>Mosaicos de dashboard

Se afixar elementos visuais de um relatório no dashboard, os mosaicos afixados serão atualizados automaticamente a cada 10 minutos. Se os dados no servidor do Analysis Services no local forem atualizados, os mosaicos serão atualizados automaticamente após 10 minutos.

## <a name="common-issues"></a>Problemas Comuns

* Erro "Não é possível carregar o esquema do modelo" – Este erro ocorre quando o utilizador que está a ligar ao SSAS não tem acesso à base de dados, ao cubo e ao modelo SSAS.

## <a name="next-steps"></a>Próximas etapas

* [Gateway de dados no local](service-gateway-onprem.md)  
* [Gerir origens de dados do Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [Resolução de problemas do Gateway de dados no local](service-gateway-onprem-tshoot.md)  

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)