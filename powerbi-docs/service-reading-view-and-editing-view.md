---
title: "Vista de leitura e Vista de edição de relatórios no serviço Power BI"
description: "Descrição geral detalhada das diferenças entre a Vista de leitura e a Vista de edição nos relatórios do serviço Power BI"
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 01/08/2018
ms.author: mihart
ms.openlocfilehash: 6948f0e333ba1136f6fda8fa0f62b146cefdd710
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/19/2018
---
# <a name="reading-view-and-editing-view-in-power-bi-service-reports"></a>Vista de Leitura e Vista de Edição nos relatórios do serviço Power BI
No serviço Power BI (mas não no Power BI Desktop), existem dois modos de visualizar e interagir com os relatórios: Vista de leitura e Vista de edição. A Vista de leitura está disponível para todos os utilizadores e foi especialmente concebida para *consumidores* de dados, enquanto a Vista de edição só está disponível para *criadores* e proprietários de relatórios. 

![](media/service-reading-view-and-editing-view/power-bi-creators-consumers.png)

## <a name="report-reading-view"></a>Vista de leitura dos relatórios

 A Vista de leitura serve para explorar e interagir com o relatório. É uma forma segura e divertida de reproduzir e ficar a conhecer os seus dados. A Vista de leitura foi concebida para os *consumidores* de relatórios; aqueles que abrem relatórios de aplicações ou que têm relatórios [partilhados com as mesmas](service-share-dashboards.md). A Vista de leitura assegura que cada consumidor de um relatório específico está a ver o mesmo relatório, as mesmas visualizações, com os mesmos filtros aplicados.  Os consumidores podem interagir com os relatórios, mas não podem guardar as alterações.

>**NOTA**: em determinadas circunstâncias, os consumidores dos relatórios poderão ver dados diferentes devido à segurança ao nível da linha e às permissões dos dados. 

## <a name="report-editing-view"></a>Vista de edição dos relatórios

A Vista de edição só está disponível para a pessoa que criou o relatório ou para o [coproprietário de um relatório como um membro ou administrador de uma área de trabalho da aplicação](service-create-distribute-apps.md).

A Vista de edição foi concebida para os *criadores* dos relatórios. É nesta vista que os criadores importam e se ligam aos conjuntos de dados, exploram os dados e criam relatórios e dashboards. Na Vista de edição, os *criadores* podem aprofundar ainda mais os dados ao adicionar e remover campos, ao alterar o tipo de visualização, ao criar novas visualizações e ao adicionar e eliminar visualizações e páginas do relatório. Em seguida, podem partilhar com os colegas os relatórios criados.

## <a name="reading-view-versus-editing-view"></a>Vista de leitura versus Vista de edição
Este gráfico não lista todas as capacidades de relatório do serviço Power BI! Lista apenas as tarefas de relatório que não estão disponíveis nas **duas** vistas. 


|Tarefa  | Vista de leitura  | Vista de edição |
|-------------------------|-------|-------|
|**Relatórios, como um todo**  |
||||
| [Criar ou editar um relatório](service-report-create-new.md) | Não  | Sim |
| [Partilhar um relatório](service-share-reports.md)| Sim | Sim e também pode gerir as permissões, incluindo conceder a outros permissões de *proprietário*. |
| [Criar filtros persistentes (permanentes) pormenorizados de nível visual, nível de página e nível de relatório no painel Filtros](power-bi-report-add-filter.md) | Não  | Sim |
| [Utilizar o painel Filtros do relatório](power-bi-how-to-report-filter.md) | Sim, pode utilizar os filtros existentes, mas as alterações não são guardadas com o relatório. | Sim |
| [Utilizar o painel Análise do relatório](service-analytics-pane.md) | Não | Sim |
| [Opções **Vista** do relatório](power-bi-report-display-settings.md) | Sim, com algumas exceções. | Sim, todas, incluindo as linhas de grelha, o ajuste e o bloqueio. |
| [Criar um agendamento de atualização](refresh-data.md) | Não  | Sim |
| [Subscrever um relatório](service-report-subscribe.md) | Sim | Não |
| [Perguntas e respostas – fazer perguntas nos relatórios](power-bi-q-and-a.md) | Não  | Sim |
| [Ver métricas de utilização ](service-usage-metrics.md) | Sim, na tela do relatório. | Sim, na lista de relatórios (vista de conteúdo) |
| [Ver relacionados](service-related-content.md) | Sim, na tela do relatório. | Sim, na lista de relatórios (vista de conteúdo) |
| [Guardar um relatório](service-report-save.md) | Sim, mas apenas através da opção **Guardar como**. | Sim |
| [Eliminar um relatório](service-delete.md) | Não  | Sim |
|**Páginas do relatório** |
||||
| [Adicionar ou mudar o nome de uma página do relatório](power-bi-report-add-page.md)  | Não  | Sim  |
| [Duplicar uma página do relatório](power-bi-report-copy-paste-page.md) | Não  | Sim |
| [Eliminar página do relatório](service-delete.md) | não | sim |
|**Trabalhar com visualizações de relatórios**|
||||
| [Adicionar visualizações a um relatório](power-bi-report-add-visualizations-i.md) | Não  | Sim |
| [Adicionar caixas de texto e formas a um relatório](power-bi-reports-add-text-and-shapes.md) | Não  | Sim |
| [Utilizar o painel Formatação do relatório](service-the-report-editor-take-a-tour.md) | Não | Sim |
| [Definir interações visuais](service-reports-visual-interactions.md) | Não  | Sim |
| [Ver os dados utilizados para criar a visualização](service-reports-show-data.md) | Não  | Sim |
| [Configurar a desagregação](power-bi-visualization-drill-down.md) | Não  | Sim |
| [Alterar a visualização que está a ser utilizada](power-bi-report-change-visualization-type.md) | Não | Sim|
| [Eliminar a visualização, a caixa de texto ou a forma](service-delete.md)| Não | Sim |


## <a name="navigating-between-editing-view-and-reading-view"></a>Navegar entre a Vista de edição e a Vista de leitura
Nota: só o criador e o(s) proprietário(s) do relatório poderão abri-lo na Vista de edição.

1. Por predefinição, o relatório geralmente é aberto na Vista de leitura. Sabe que está na Vista de leitura se vir uma opção para **Editar relatório**. Se **Editar relatório** aparecer a cinzento, significa que não dispõe de permissões para abrir o relatório na Vista de edição.

   ![](media/service-reading-view-and-editing-view/power-bi-edit-report-grey.png)

2. Se **Editar relatório** não aparecer a cinzento, selecione a opção para abrir o relatório na Vista de edição. 
   
   ![](media/service-reading-view-and-editing-view/power-bi-edit-report.png)
   
   O relatório está agora na Vista de edição e utiliza as mesmas [configurações de apresentação](power-bi-report-display-settings.md) utilizadas pela última vez na Vista de leitura.

2. Para voltar à Vista de leitura, selecione **Vista de Leitura** na barra de navegação superior.
   
    ![](media/service-reading-view-and-editing-view/power-bi-reading-view.png)



### <a name="next-steps"></a>Próximos passos
Há muitas maneiras de interagir com o relatório na Vista de leitura, através da divisão e da repartição de dados para descobrir ideias e obter respostas a perguntas.  O próximo tópico, [Interagir com um relatório na Vista de leitura](service-interact-with-a-report-in-editing-view.md), descreve algumas em detalhe.    
Voltar a [relatórios no Power BI](service-reports.md)    
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/) 

