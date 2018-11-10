---
title: Dashboards no serviço Power BI
description: Os dashboards são uma funcionalidade chave do serviço Power BI.
author: maggieMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/18/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: b7f94d47452fb9d1ea24c950dba2988c6c80c053
ms.sourcegitcommit: 2c4a075fe16ccac8e25f7ca0b40d404eacb49f6d
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/20/2018
ms.locfileid: "49473734"
---
# <a name="dashboards-in-the-power-bi-service"></a>Dashboards no serviço Power BI

Um ***dashboard*** do Power BI é uma única página, frequentemente denominada tela, que utiliza visualizações para contar uma história. Como está limitada a uma página, um dashboard bem concebido contém apenas os elementos mais importantes da história.

![dashboard](media/service-dashboards/power-bi-dashboard2.png)

Os dashboards são uma funcionalidade do serviço Power BI e não estão disponíveis no Power BI Desktop. Os dashboards não podem ser criados em dispositivos móveis, mas podem ser [visualizados e partilhados](mobile-apps-view-dashboard.md).

## <a name="dashboard-creators-and-dashboard-consumers"></a>Criadores e consumidores de dashboards
Consoante o seu cargo, pode ser uma pessoa que cria dashboards para sua utilização ou para partilhar com colegas. Pode encontrar informações em **Dashboards para criadores**. Recebe dashboards de outras pessoas? Quer saber como compreender e interagir com o dashboard. Este artigo é para si!


### <a name="if-you-will-be-receiving-and-consuming-dashboards"></a>Se for receber e consumir dashboards

As visualizações que vê no dashboard são denominadas *mosaicos* e são *afixadas* ao dashboard a partir de relatórios pelos *criadores* de dashboards. Se for um novo utilizador do Power BI, pode obter uma boa base de aprendizagem ao ler os [conceitos básicos do Power BI](service-basic-concepts.md).

> [!IMPORTANT]
> Para ver um dashboard partilhado, é necessário o [Power BI Pro](service-free-vs-pro.md).

As visualizações num dashboard são provenientes de relatórios e cada relatório baseia-se num conjunto de dados. Na verdade, uma forma de pensar num dashboard é como uma entrada para os relatórios e conjuntos de dados subjacentes. Selecionar uma visualização leva-o ao relatório (e ao conjunto de dados) que utilizou para a criar.

![diagrama a mostrar as relações entre dashboards, relatórios, conjuntos de dados](media/service-dashboards/power-bi-diagram.png)



## <a name="advantages-of-dashboards"></a>Vantagens dos dashboards
Os dashboards são uma forma fantástica de monitorizar a sua empresa, procurar respostas e ver rapidamente todas as métricas mais importantes. As visualizações num dashboard podem ser provenientes de um ou vários conjuntos de dados subjacentes ou de um ou vários relatórios subjacentes. Um dashboard combina dados no local e na cloud ao fornecer uma vista consolidada, independentemente de onde os dados residem.

Um dashboard não é apenas uma imagem apelativa. É também altamente interativa e os mosaicos são atualizados à medida que os dados subjacentes são alterados.

## <a name="dashboards-versus-reports"></a>Dashboards versus relatórios
Os [relatórios](service-reports.md) costumam ser confundidos com os dashboards, pois também são telas preenchidas com visualizações. No entanto, existem algumas diferenças significativas para os consumidores do Power BI.

| **Capacidade** | **Dashboards** | **Relatórios** |
| --- | --- | --- |
| Páginas |Uma página |Uma ou mais páginas |
| Origens de dados |Um ou mais relatórios e um ou mais conjuntos de dados por dashboard |Um único conjunto de dados por relatório |
| Disponível no Power BI Desktop |Não |Sim, os ***criadores*** podem criar e ver relatórios no Power BI Desktop |
| Subscrever |Pode subscrever um dashboard |Pode subscrever páginas de relatório |
| Filtragem |Não pode filtrar nem segmentar |Várias formas diferentes de filtrar, realçar e segmentar |
| Destaques |Pode definir um dashboard como o seu dashboard "em destaque" |Não pode criar um relatório em destaque |
| Favorito | Pode definir dashboards como *favoritos* | Pode definir relatórios como *favoritos*
| Definir alertas |Disponível para mosaicos de dashboards em determinadas circunstâncias |Não disponível nos relatórios |
| Consultas de linguagem natural |Disponível no dashboard |Não disponível nos relatórios |
| Pode ver as tabelas e os campos de conjuntos de dados subjacentes |Não. Pode exportar dados mas não pode ver tabelas e campos no próprio dashboard. |Sim. Pode ver tabelas, campos e valores de conjuntos de dados. |
| Personalização |Não |Na Vista de leitura, pode publicar, incorporar, filtrar, exportar, transferir como .pbix, ver conteúdos relacionados, gerar códigos QR, analisar no Excel e mais.  |

## <a name="next-steps"></a>Próximos passos
* Conheça melhor os dashboards ao ver uma apresentação de um dos nossos [dashboards de exemplo](sample-tutorial-connect-to-the-samples.md).
* Saiba mais sobre [mosaicos do dashboard](service-dashboard-tiles.md) e o que acontece quando seleciona um.
* Quer controlar um mosaico do dashboard individual e receber um e-mail quando atingir um determinado limiar? [Crie alertas nos mosaicos](service-set-data-alerts.md).
* Divirta-se a fazer perguntas ao dashboard. Saiba como utilizar as [Perguntas e Respostas do Power BI](power-bi-tutorial-q-and-a.md) para fazer uma pergunta sobre os dados e receber uma resposta na forma de uma visualização.
