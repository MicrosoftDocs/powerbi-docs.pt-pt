---
title: Introdução aos dashboards para designers do Power BI
description: Os dashboards são uma funcionalidade chave do serviço Power BI. São uma página única, frequentemente denominada tela, que utiliza visualizações para contar uma história.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 01/08/2021
LocalizationGroup: Dashboards
ms.openlocfilehash: 2d5eb4047b467544110a5802fa1d41b7ed65bb6a
ms.sourcegitcommit: f791eef8e885f18c48997c9af63ab56211f1ceb8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/09/2021
ms.locfileid: "98053357"
---
# <a name="introduction-to-dashboards-for-power-bi-designers"></a>Introdução aos dashboards para designers do Power BI

Um *dashboard* do Power BI é uma página única, frequentemente denominada tela, que utiliza visualizações para contar uma história. Como está limitado a uma página, um dashboard bem concebido contém apenas os elementos mais importantes da história. Os leitores podem ver relatórios relacionados para obter detalhes.

![Dashboard](media/service-dashboards/power-bi-dashboard2.png)

Os dashboards são uma funcionalidade apenas do serviço Power BI. Não estão disponíveis no Power BI Desktop. Embora não possa criar dashboards em dispositivos móveis, pode [ver e partilhá-los](../consumer/mobile/mobile-apps-view-dashboard.md).

## <a name="dashboard-basics"></a>Conceitos básicos dos dashboard 

As visualizações que vê no dashboard são denominadas *mosaicos*. Pode *afixar* os mosaicos num dashboard a partir de relatórios. Se for um novo utilizador do Power BI, pode obter uma boa base de aprendizagem ao ler os [Conceitos básicos para os designers do serviço Power BI](../fundamentals/service-basic-concepts.md).

As visualizações num dashboard são provenientes de relatórios e cada relatório baseia-se num conjunto de dados. Uma forma de pensar num dashboard é pensar numa entrada para os relatórios e conjuntos de dados subjacentes. Selecionar uma visualização leva-o ao relatório (e ao conjunto de dados) em que se baseia.

![Diagrama a mostrar as relações entre dashboards, relatórios, conjuntos de dados](media/service-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>Vantagens dos dashboards
Os dashboards são uma forma fantástica de monitorizar a sua empresa e ver rapidamente todas as métricas mais importantes. As visualizações num dashboard podem ser provenientes de um ou vários conjuntos de dados subjacentes, ou de um ou vários relatórios subjacentes. Um dashboard combina dados no local e na cloud ao fornecer uma vista consolidada, independentemente de onde os dados residem.

Um dashboard não é apenas uma imagem bonita. É também altamente interativa e os mosaicos são atualizados à medida que os dados subjacentes são alterados.

## <a name="who-can-create-a-dashboard"></a>Como posso criar um dashboard?
A capacidade de criar um dashboard é considerada uma funcionalidade de *criador* e exige permissões de edição no relatório. As permissões de edição estão disponíveis para os criadores de relatórios e para os colegas aos quais o criador concede acesso. Por exemplo, se o David criar um relatório na área de trabalho ABC e o adicionar como um membro dessa área de trabalho, ambos terão permissões de edição. Por outro lado, se um relatório tiver sido partilhado consigo diretamente ou como parte de uma [aplicação do Power BI](../collaborate-share/service-create-distribute-apps.md), estará a *consumir* o relatório. Poderá não conseguir afixar mosaicos a um dashboard. 

> [!IMPORTANT]
> Necessita de uma licença do [Power BI Pro](../fundamentals/service-features-license-type.md) para criar dashboards nas áreas de trabalho. Pode criar dashboards na sua própria A Minha Área de Trabalho sem uma licença Power BI Pro.


## <a name="dashboards-versus-reports"></a>Dashboards versus relatórios
Os [Relatórios](../consumer/end-user-reports.md) e os dashboards parecem semelhantes porque ambos são telas preenchidas com visualizações. No entanto, há grandes diferenças, tal como pode ver na tabela abaixo.

| **Capacidade** | **Dashboards** | **Relatórios** |
| --- | --- | --- |
| Páginas |Uma página |Uma ou mais páginas |
| Origens de dados |Um ou mais relatórios e um ou mais conjuntos de dados por dashboard |Um único conjunto de dados por relatório |
| Disponível no Power BI Desktop |Não | Yes. Podem criar e ver relatórios no Power BI Desktop |
| Subscrever |Yes. Pode subscrever um dashboard |Yes. Pode subscrever uma página de relatório |
| Filtragem |Não. Não pode filtrar nem segmentar um dashboard. *Pode* filtrar um [mosaico de dashboard no modo de detalhe](../consumer/end-user-focus.md#working-in-focus-mode), mas não pode guardar o filtro. |Yes. Várias formas diferentes de filtrar, realçar e segmentar |
| Destaques |Yes. Pode definir um dashboard como o seu dashboard *em destaque* |Não |
| Favorito | Yes. Pode definir múltiplos dashboards como *favoritos* | Yes. Pode definir múltiplos relatórios como *favoritos* |
| Definir alertas |Yes. Disponível para mosaicos de dashboards em determinadas circunstâncias |Não |
| Consultas de linguagem natural (Perguntas e Respostas) |Sim | Sim, desde que tenha permissões de edição para o relatório e o conjunto de dados subjacente |
| Pode ver as tabelas e os campos de conjuntos de dados subjacentes |Não. Pode exportar dados, mas não pode ver tabelas e campos no próprio dashboard |Sim |


## <a name="next-steps"></a>Próximos passos
* Conheça melhor os dashboards ao ver uma apresentação de um dos nossos [dashboards de exemplo](sample-tutorial-connect-to-the-samples.md).
* Saiba mais sobre os [mosaicos de dashboards](service-dashboard-tiles.md).
* Quer controlar um mosaico do dashboard individual e receber um e-mail quando atingir um determinado limiar? [Criar um alerta num mosaico](service-set-data-alerts.md).
* Saiba como utilizar as [Perguntas e Respostas do Power BI](power-bi-tutorial-q-and-a.md) para fazer uma pergunta sobre os dados e receber uma resposta na forma de uma visualização.
