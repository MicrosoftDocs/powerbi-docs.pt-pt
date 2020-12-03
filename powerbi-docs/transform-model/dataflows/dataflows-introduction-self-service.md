---
title: Introdução aos fluxos de dados e à preparação personalizada de dados
description: Descrição geral dos fluxos de dados do Power BI e quando devem ser utilizados
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-dataflows
ms.topic: how-to
ms.date: 10/01/2020
LocalizationGroup: Data from files
ms.openlocfilehash: 5dde70b9834d990987e42c6aa945940a7f110949
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416077"
---
# <a name="introduction-to-dataflows-and-self-service-data-prep"></a>Introdução aos fluxos de dados e à preparação personalizada de dados

À medida que o volume de dados continua a crescer, o mesmo acontece com o desafio de preparação desses dados em informações acionáveis e bem formadas. Queremos dados que estejam prontos para análises, para preencher elementos visuais, relatórios e dashboards, para que possamos transformar rapidamente os nossos volumes de dados em informações acionáveis. Com a preparação personalizada de dados para grandes volumes de dados no Power BI, pode ir dos dados às informações do Power BI com apenas alguns cliques.

![fluxo de dados](media/dataflows-introduction-self-service-flow.png)

## <a name="when-to-use-dataflows"></a>Quando utilizar os fluxos de dados

Os fluxos de dados foram concebidos para suportar os seguintes cenários:

* Crie lógica de transformação reutilizável que pode ser partilhada por muitos conjuntos de dados e relatórios no Power BI. Os fluxos de dados promovem a reutilização dos elementos de dados subjacentes, eliminando a necessidade de criar ligações separadas com as suas origens de dados no local ou na cloud.

* Exponha os dados no seu próprio armazenamento do Azure Data Lake Gen2, permitindo-lhe ligar outros serviços do Azure aos dados não processados subjacentes.

* Crie uma única versão dos dados ao forçar os analistas a ligar aos fluxos de dados, em vez de ligar aos sistemas subjacentes, dando-lhe assim controlo sobre os dados que são acedidos e como os dados são expostos aos criadores de relatórios. Também pode mapear os dados às definições padrão do setor, o que lhe permite criar vistas bem organizadas que podem funcionar com outros serviços e produtos no Power Platform.

* Se quiser trabalhar com grandes volumes de dados e realizar ETL em escala, os fluxos de dados do Power BI Premium dimensionam de forma mais eficiente e proporcionam-lhe maior flexibilidade. Os fluxos de dados suportam um grande número de origens no local e na cloud. 

* Impeça que os analistas tenham acesso direto à origem de dados subjacente. Uma vez que os criadores de relatórios podem criá-los com base em fluxos de dados, poderá ser-lhe mais conveniente conceder o acesso às origens de dados subjacentes apenas a algumas pessoas e depois dar aos analistas acesso aos fluxos de dados a partir dos quais podem criar os relatórios. Esta abordagem reduz a carga dos sistemas subjacentes e proporciona aos administradores um maior controlo sobre quando os sistemas são carregados por atualizações.

Depois de criar um fluxo de dados, pode utilizar o Power BI Desktop e o serviço Power BI para criar conjuntos de dados, relatórios, dashboards e aplicações que tiram partido do Common Data Model para impulsionar as informações aprofundadas nas suas atividades empresariais. O agendamento de atualização dos fluxos de dados é gerido diretamente a partir da área de trabalho em que o fluxo de dados foi criado, da mesma forma que os conjuntos de dados.

## <a name="next-steps"></a>Passos seguintes
Este artigo forneceu uma descrição geral da preparação personalizada para macrodados no Power BI e as várias formas de utilização. 

Os seguintes artigos fornecem mais informações sobre os fluxos de dados e o Power BI:

* [Criar um fluxo de dados](dataflows-create.md)
* [Configurar e consumir um fluxo de dados](dataflows-configure-consume.md)
* [Configurar o armazenamento do fluxo de dados para utilizar o Azure Data Lake Gen2](dataflows-azure-data-lake-storage-integration.md)
* [Funcionalidades Premium do fluxo de dados](dataflows-premium-features.md)
* [IA com fluxos de dados](dataflows-machine-learning-integration.md)
* [Limitações e considerações dos fluxo de dados](dataflows-features-limitations.md)
* [Melhores práticas dos fluxos de dados](dataflows-best-practices.md)


Para obter mais informações sobre o Common Data Service, pode ler o seguinte artigo de descrição geral:
* [Common Data Model – descrição geral](/powerapps/common-data-model/overview)