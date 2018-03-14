---
title: "O que é um dashboard do Power BI?"
description: "Os dashboards são uma funcionalidade chave do serviço Power BI."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: monitoring
qualitydate: 04/05/2017
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/02/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 223df3a898c925d2a8ffc6d004a26c1a67807fc2
ms.sourcegitcommit: 5e1f7d2673efe25c47b9b9f315011055bfe92c8f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/09/2018
---
# <a name="dashboards-in-power-bi-service"></a>Dashboards no serviço Power BI

Um ***dashboard*** do Power BI é uma única página, frequentemente denominada tela, que utiliza visualizações para contar uma história. Como está limitada a uma página, um dashboard bem concebido contém apenas os elementos mais importantes da história.

![dashboard](media/service-dashboards/power-bi-dashboard2.png)

As visualizações que vê no dashboard são denominadas *mosaicos* e são *afixadas* ao dashboard a partir de relatórios. Se for um novo utilizador do Power BI, pode obter uma boa base de aprendizagem ao ler os [conceitos básicos do Power BI](service-basic-concepts.md).

> [!NOTE]
> Os dashboards são uma funcionalidade do serviço Power BI e não estão disponíveis no Power BI Desktop. Os dashboards não podem ser criados em dispositivos móveis, mas podem ser [visualizados e partilhados](mobile-apps-view-dashboard.md).
> 
> 

As visualizações num dashboard são provenientes de relatórios e cada relatório baseia-se num conjunto de dados. Na verdade, uma forma de pensar num dashboard é como uma entrada para os relatórios e conjuntos de dados subjacentes. Selecionar uma visualização leva-o ao relatório (e ao conjunto de dados) que utilizou para a criar.

![diagrama a mostrar as relações entre dashboards, relatórios, conjuntos de dados](media/service-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>Vantagens dos dashboards
Os dashboards são uma forma fantástica de monitorizar a sua empresa, procurar respostas e ver rapidamente todas as métricas mais importantes. As visualizações num dashboard podem ser provenientes de um ou vários conjuntos de dados subjacentes ou de um ou vários relatórios subjacentes. Um dashboard combina dados no local e na cloud ao fornecer uma vista consolidada, independentemente de onde os dados residem.

Um dashboard não é apenas uma imagem bonita; é altamente interativo e personalizável e os mosaicos são atualizados à medida que os dados subjacentes são alterados.

## <a name="dashboards-versus-reports"></a>Dashboards versus relatórios
Os [relatórios](service-reports.md) costumam ser confundidos com os dashboards, pois também são telas preenchidas com visualizações. No entanto, existem algumas diferenças importantes.

| **Capacidade** | **Dashboards** | **Relatórios** |
| --- | --- | --- |
| Páginas |Uma página |Uma ou mais páginas |
| Origens de dados |Um ou mais relatórios e um ou mais conjuntos de dados por dashboard |Um único conjunto de dados por relatório |
| Disponível no Power BI Desktop |Não |Sim, pode criar e ver relatórios no Desktop |
| Afixação |Pode afixar visualizações (mosaicos) existentes apenas do dashboard atual aos seus outros dashboards |Pode afixar visualizações (como mosaicos) aos seus dashboards. Pode afixar páginas de relatório inteiras aos seus dashboards. |
| Subscrição |Não pode subscrever um dashboard |Pode subscrever páginas de relatório |
| Filtragem |Não pode filtrar nem segmentar |Várias formas diferentes de filtrar, realçar e segmentar |
| Definir alertas |Pode criar alertas para que lhe seja enviado um e-mail quando são cumpridas determinadas condições |Não |
| Destaque |Pode definir um dashboard como o seu dashboard "em destaque" |Não pode criar um relatório em destaque |
| Consultas de linguagem natural |Disponível no dashboard |Não disponível nos relatórios |
| Pode alterar o tipo de visualização |Não. De facto, se um proprietário de relatório alterar o tipo de visualização no relatório, a visualização afixada no dashboard não é atualizada |Sim |
| Pode ver as tabelas e os campos de conjuntos de dados subjacentes |Não. Pode exportar dados mas não pode ver tabelas e campos no próprio dashboard. |Sim. Pode ver tabelas, campos e valores de conjuntos de dados. |
| Pode criar visualizações |Limitado a adicionar widgets ao dashboard através de "Adicionar mosaico" |Pode criar vários tipos diferentes de elementos visuais, adicionar elementos visuais personalizados, editar elementos visuais e muito mais com permissões de Edição |
| Personalização |Pode efetuar ações com visualizações (mosaicos) como mover e dispor, redimensionar, adicionar ligações, mudar o nome, eliminar e mostrar em ecrã inteiro. No entanto, os dados e as visualizações propriamente ditos são só de leitura. |Na Vista de leitura, pode publicar, incorporar, filtrar, exportar, transferir como .pbix, ver conteúdos relacionados, gerar códigos QR, analisar no Excel e muito mais.  Na Vista de edição, pode fazer tudo o que foi anteriormente mencionado e muito mais. |

## <a name="dashboard-creators-and-dashboard-consumers"></a>Criadores e consumidores de dashboards
Consoante o seu cargo, pode ser uma pessoa que cria dashboards para sua utilização ou para partilhar com colegas. Quer saber como criar e partilhar dashboards. Também pode ser uma pessoa que recebe dashboards de terceiros. Quer saber como compreender e interagir com o dashboard.

Eis alguns tópicos, por função, que o ajudarão a começar.

O Power BI Pro é necessário tanto para partilhar um dashboard como para visualizar um dashboard partilhado.

### <a name="if-you-will-be-creating-and-sharing-dashboards"></a>Se for criar e partilhar dashboards
* Utilize um dos nossos exemplos para [criar um dashboard a partir de um relatório](service-dashboard-create.md).
* Saiba mais sobre [mosaicos do dashboard](service-dashboard-tiles.md) e todas as diferentes formas de afixá-los a um dashboard.
* Ajude os consumidores do dashboard ao criar dashboards que [funcionam bem com consultas de linguagem natural de Perguntas e Respostas](service-prepare-data-for-q-and-a.md) e com [Informações rápidas](service-insights-optimize.md).
* Saiba todas as diferentes formas de [partilhar um dashboard com colegas](service-how-to-collaborate-distribute-dashboards-reports.md).

### <a name="if-you-will-be-receiving-and-consuming-dashboards"></a>Se for receber e consumir dashboards
* Conheça melhor os dashboards ao ver uma apresentação de um dos nossos [dashboards de exemplo](sample-tutorial-connect-to-the-samples.md).
* Saiba mais sobre [mosaicos do dashboard](service-dashboard-tiles.md) e o que acontece quando seleciona um.
* Não gosta do aspeto de um dashboard?  Pode [redimensionar, mover e mudar o nome dos mosaicos](service-dashboard-edit-tile.md).
* Quer controlar um mosaico do dashboard individual e receber um e-mail quando atingir um determinado limiar? [Crie alertas nos mosaicos](service-set-data-alerts.md).
* Divirta-se a fazer perguntas ao dashboard. Saiba como utilizar as [Perguntas e Respostas do Power BI](power-bi-tutorial-q-and-a.md) para fazer uma pergunta sobre os dados e receber uma resposta na forma de uma visualização.

> [!TIP]
> Se não encontrou aqui o que procurava, utilize o Índice à esquerda.
> 
> 

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)  
[Power BI - Conceitos Básicos](service-basic-concepts.md)  
[Power BI Premium – o que é?](service-premium.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

