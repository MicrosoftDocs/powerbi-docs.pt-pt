---
title: "Início rápido: Criar um relatório paginado para o Power BI Report Server"
description: "Saiba como criar um relatório paginado para o Power BI Report Server em poucos passos simples."
services: powerbi
documentationcenter: 
author: maggiesMSFT
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
ms.date: 10/12/2017
ms.author: maggies
ms.openlocfilehash: 1e77a1ef92826010d6bc2fa28749a2ee17bbe723
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="quickstart-create-a-paginated-report-for-power-bi-report-server"></a>Início rápido: Criar um relatório paginado para o Power BI Report Server
Como o nome indica, os relatórios paginados podem ocupar muitas páginas. Estão dispostos num formato fixo e oferecem uma personalização precisa. Os relatórios paginados são ficheiros .rdl.

Pode armazenar e gerir relatórios paginados no portal Web do Power BI Report Server, tal como pode fazê-lo no portal Web do SQL Server Reporting Services (SSRS). Pode criar e editá-los no Report Builder ou Report Designer no SQL Server Data Tools (SSDT) e, em seguida, publicá-los através do portal Web. Depois, os leitores de relatórios na sua organização podem visualizá-los num browser ou numa aplicação móvel do Power BI, no respetivo dispositivo móvel.

![Relatório paginado do Power BI Report Server](media/quickstart-create-paginated-report/reportserver-paginated-report.png)

Se já criou relatórios paginados no Report Builder ou no Report Designer, está pronto para criar relatórios paginados para o Power BI Report Server. Se não o fez, eis alguns passos rápidos para começar.

## <a name="step-1-install-and-start-report-builder"></a>Passo 1: Instalar e iniciar o Report Builder
Pode já ter instalado o Report Builder para criar relatórios para um servidor SSRS. Pode utilizar a mesma versão ou o Report Builder para criar relatórios para o Power BI Report Server. Se ainda não o instalou, o processo é simples.

1. No portal Web do Power BI Report Server, selecione **Novo** > **Relatório Paginado**.
   
    ![Menu Novo Relatório Paginado](media/quickstart-create-paginated-report/reportserver-new-paginated-report-menu.png)
   
    Se não ainda não tiver o Report Builder instalado, será agora orientado pelo processo de instalação.
2. Após ser instalado, o Report Builder é aberto no ecrã **Novo Relatório ou Conjunto de Dados**.
   
    ![Ecrã Novo Relatório ou Conjunto de Dados](media/quickstart-create-paginated-report/reportserver-paginated-new-report-screen.png)
3. Selecione o assistente correspondente ao tipo de relatório que pretende criar:
   
   * Tabela ou matriz
   * Gráfico
   * Mapa
   * Vazio
4. Comecemos pelo assistente de Gráfico.
   
    O assistente de Gráfico orienta-o pelos passos de criação de um gráfico básico num relatório. A partir daí, pode personalizar o seu relatório praticamente sem limites.

## <a name="step-2-go-through-the-chart-wizard"></a>Passo 2: Percorrer o assistente de Gráfico
O assistente de Gráfico orienta-o nos passos básicos de criação de uma visualização num relatório.

Os relatórios paginados podem ligar a diversas origens de dados, desde o Microsoft SQL Server e a Base de Dados SQL do Microsoft Azure ao Oracle, Hyperion e muitos mais. Saiba mais sobre [origens de dados suportadas por relatórios paginados](connect-data-sources.md).

Na primeira página do assistente de Gráfico, **Selecione um conjunto de dados**, pode criar um conjunto de dados ou selecionar um conjunto de dados partilhado num servidor. Os *Conjuntos de dados* devolvem dados de relatórios de uma consulta numa origem de dados externa.

1. Selecione **Procurar** > selecionar um conjunto de dados partilhado num servidor > **Abrir** > **Seguinte**.
   
    ![Assistente de Gráfico: Selecionar um conjunto de dados](media/quickstart-create-paginated-report/reportserver-paginated-choose-dataset.png)
   
     Precisa de criar um conjunto de dados? Consulte [Criar um conjunto de dados partilhado ou incorporado](https://docs.microsoft.com/sql/reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs).
2. Selecione um tipo de gráfico (neste caso, um gráfico de barras).
   
    ![Assistente de Gráfico: tipo de gráfico](media/quickstart-create-paginated-report/reportserver-paginated-choose-chart-type.png)
3. Disponha os campos ao arrastá-los para as caixas **Categorias**, **Séries** e **Valores**.
   
    ![Assistente de Gráfico: dispor campos](media/quickstart-create-paginated-report/reportserver-paginated-arrange-fields.png)
4. Selecione **Seguinte** > **Concluir**.

## <a name="step-3-design-your-report"></a>Passo 3: Estruturar o seu relatório
Agora, está na vista de Estrutura do Relatório. Repare que os dados são apenas marcadores de posição, não os seus dados.

![Vista de Estrutura do Relatório](media/quickstart-create-paginated-report/reportserver-paginated-preview-report.png)

* Para ver os seus dados, selecione **Executar**.
  
     ![Executar relatório](media/quickstart-create-paginated-report/reportserver-paginated-run-report.png)
* Para regressar à vista de Estrutura, selecione **Estrutura**.

Pode modificar o gráfico que acabou de criar, alterando o esquema, os valores, a legenda... na verdade, quase tudo.

Pode também adicionar muitas outras visualizações: medidores, tabelas, matrizes, tabelas, mapas e muito mais. Pode adicionar cabeçalhos e rodapés a múltiplas páginas. Consulte os [tutoriais do Report Builder](https://docs.microsoft.com/sql/reporting-services/report-builder-tutorials) para experimentar.

![Vista de Estrutura do Report Builder](media/quickstart-create-paginated-report/reportserver-paginated-finished-design-report.png)

## <a name="step-4-save-your-report-to-the-report-server"></a>Passo 4: Guardar o seu relatório no servidor de relatório
Quando o seu relatório estiver pronto, guarde-o no Power BI Report Server.

1. No menu **Ficheiro**, selecione **Guardar como** e guarde-o no servidor de relatório. 
2. Agora, pode vê-lo no browser.
   
    ![Relatório paginado no browser](media/quickstart-create-paginated-report/reportserver-paginated-report.png)

## <a name="next-steps"></a>Próximas etapas
Existem muitos recursos excelentes para estruturar relatórios no Report Builder e no Report Designer no SQL Server Data Tools. Os tutoriais do Report Builder são um bom local para começar.

* [Tutoriais do Report Builder](https://docs.microsoft.com/sql/reporting-services/report-builder-tutorials)
* [Manual de utilizador do Power BI Report Server](user-handbook-overview.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
