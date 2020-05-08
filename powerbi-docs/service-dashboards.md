---
title: Introdução aos dashboards para designers do Power BI
description: Os dashboards são uma funcionalidade chave do serviço Power BI. São uma página única, frequentemente denominada tela, que utiliza visualizações para contar uma história.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: eb2c513e8ee8ad1c8ad93866f688e40f6c5af56d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "76160794"
---
# <a name="introduction-to-dashboards-for-power-bi-designers"></a>Introdução aos dashboards para designers do Power BI

Um *dashboard* do Power BI é uma página única, frequentemente denominada tela, que utiliza visualizações para contar uma história. Como está limitado a uma página, um dashboard bem concebido contém apenas os elementos mais importantes da história. Os leitores podem ver relatórios relacionados para obter detalhes.

![Dashboard](media/service-dashboards/power-bi-dashboard2.png)

Os dashboards são uma funcionalidade apenas do serviço Power BI. Não estão disponíveis no Power BI Desktop. Embora não possa criar dashboards em dispositivos móveis, pode [ver e partilhá-los](mobile-apps-view-dashboard.md).

## <a name="dashboard-basics"></a>Conceitos básicos dos dashboard 

As visualizações que vê no dashboard são denominadas *mosaicos*. Pode *afixar* os mosaicos num dashboard a partir de relatórios. Se for um novo utilizador do Power BI, pode obter uma boa base de aprendizagem ao ler os [Conceitos básicos para os designers do serviço Power BI](service-basic-concepts.md).

As visualizações num dashboard são provenientes de relatórios e cada relatório baseia-se num conjunto de dados. Uma forma de pensar num dashboard é pensar numa entrada para os relatórios e conjuntos de dados subjacentes. Selecionar uma visualização leva-o ao relatório (e ao conjunto de dados) em que se baseia.

![Diagrama a mostrar as relações entre dashboards, relatórios, conjuntos de dados](media/service-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>Vantagens dos dashboards
Os dashboards são uma forma fantástica de monitorizar a sua empresa e ver rapidamente todas as métricas mais importantes. As visualizações num dashboard podem ser provenientes de um ou vários conjuntos de dados subjacentes, ou de um ou vários relatórios subjacentes. Um dashboard combina dados no local e na cloud ao fornecer uma vista consolidada, independentemente de onde os dados residem.

Um dashboard não é apenas uma imagem bonita. É também altamente interativa e os mosaicos são atualizados à medida que os dados subjacentes são alterados.

## <a name="who-can-create-a-dashboard"></a>Como posso criar um dashboard?
A capacidade de criar um dashboard é considerada uma funcionalidade de *criador* e exige permissões de edição no relatório. As permissões de edição estão disponíveis para os criadores de relatórios e para os colegas aos quais o criador concede acesso. Por exemplo, se o David criar um relatório na área de trabalho ABC e o adicionar como um membro dessa área de trabalho, ambos terão permissões de edição. Por outro lado, se um relatório tiver sido partilhado consigo diretamente ou como parte de uma [aplicação do Power BI](service-create-distribute-apps.md), estará a *consumir* o relatório. Poderá não conseguir afixar mosaicos a um dashboard. 

> [!IMPORTANT]
> Necessita de uma licença do [Power BI Pro](service-free-vs-pro.md) para criar dashboards nas áreas de trabalho. Pode criar dashboards na sua própria A Minha Área de Trabalho sem uma licença Power BI Pro.


## <a name="dashboards-versus-reports"></a>Dashboards versus relatórios
Os [Relatórios](service-reports.md) e os dashboards parecem semelhantes porque ambos são telas preenchidas com visualizações. No entanto, há grandes diferenças, tal como pode ver na tabela abaixo.

| **Capacidade** | **Dashboards** | **Relatórios** |
| --- | --- | --- |
| Páginas |Uma página |Uma ou mais páginas |
| Data sources |Um ou mais relatórios e um ou mais conjuntos de dados por dashboard |Um único conjunto de dados por relatório |
| Disponível no Power BI Desktop |No | Sim. Podem criar e ver relatórios no Power BI Desktop |
| Subscrição |Sim. Pode subscrever um dashboard |Sim. Pode subscrever uma página de relatório |
| Filtragem |N.º Não pode filtrar nem segmentar |Sim. Várias formas diferentes de filtrar, realçar e segmentar |
| Destaques |Sim. Pode definir um dashboard como o seu dashboard *em destaque* |No |
| Favorito | Sim. Pode definir múltiplos dashboards como *favoritos* | Sim. Pode definir múltiplos relatórios como *favoritos*
| Definir alertas |Sim. Disponível para mosaicos de dashboards em determinadas circunstâncias |No |
| Consultas de linguagem natural (Perguntas e Respostas) |Yes | Sim, desde que tenha permissões de edição para o relatório e o conjunto de dados subjacente |
| Pode ver tabelas e campos de conjuntos de dados subjacentes |N.º Pode exportar dados, mas não pode ver tabelas e campos no próprio dashboard |Yes |


## <a name="next-steps"></a>Próximas etapas
* Conheça melhor os dashboards ao ver uma apresentação de um dos nossos [dashboards de exemplo](sample-tutorial-connect-to-the-samples.md).
* Saiba mais sobre os [mosaicos de dashboards](service-dashboard-tiles.md).
* Quer controlar um mosaico do dashboard individual e receber um e-mail quando atingir um determinado limiar? [Criar um alerta num mosaico](service-set-data-alerts.md).
* Saiba como utilizar as [Perguntas e Respostas do Power BI](power-bi-tutorial-q-and-a.md) para fazer uma pergunta sobre os dados e receber uma resposta na forma de uma visualização.
