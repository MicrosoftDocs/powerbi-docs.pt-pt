---
title: O que é Power BI?
description: 'Descrição geral do Power BI e como os diferentes elementos encaixam: Power BI Desktop, serviço Power BI, Power BI Mobile, Report Server e Power BI Embedded.'
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: overview
ms.date: 09/04/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 17c352a28561278ae282d76f725322ad800fb76d
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73064451"
---
# <a name="what-is-power-bi"></a>O que é Power BI?
O **Power BI** é uma coleção de serviços de software, aplicações e conectores que funcionam em conjunto para transformar as origens de dados não relacionadas em informações coerentes, visualmente envolventes e interativas. Os dados podem ser uma folha de cálculo do Excel ou uma coleção de armazéns de dados híbridos no local e com base na cloud. O Power BI permite-lhe ligar-se facilmente às suas origens de dados, visualizar e descobrir o que é importante, bem como partilhar os seus conteúdos com qualquer pessoa.

## <a name="the-parts-of-power-bi"></a>As partes do Power BI
O Power BI consiste: 
- Numa aplicação para computadores com Windows, chamada **Power BI Desktop**.
- Num serviço SaaS (*Software como Serviço*) online chamado **serviço Power BI**. 
- Nas **aplicações móveis** do Power BI para dispositivos Windows, iOS e Android.

![Power BI Desktop, serviço, móvel](media/power-bi-overview/power-bi-overview-blocks.png)

Estes três elementos(&mdash;o Power BI Desktop, o serviço Power BI e as aplicações móveis do Power BI&mdash;) foram concebidos para permitir que crie, partilhe e consuma informações empresariais de forma a satisfazer ao máximo as suas necessidades pessoais ou profissionais.

Um quarto elemento, o **Power BI Report Server**, permite-lhe publicar relatórios do Power BI num servidor de relatórios no local, depois de os criar no Power BI Desktop. Saiba mais sobre o [Power BI Report Server](#on-premises-reporting-with-power-bi-report-server).

## <a name="how-power-bi-matches-your-role"></a>Como o Power BI corresponde à sua função
O modo de utilização do Power BI poderá depender da sua função num projeto ou numa equipa. É possível que cada pessoa utilize o Power BI de forma diferente, consoante a respetiva função numa empresa.

Por exemplo, pode utilizar o **serviço Power BI** principalmente para ver relatórios e dashboards. Um dos seus colegas que cria relatórios empresariais com muitos cálculos matemáticos poderá fazer um uso extensivo do **Power BI Desktop** para criar relatórios e depois publicá-los no serviço Power BI, onde os vê. Outro dos seus colegas, do departamento de vendas, poderá utilizar a **aplicação Power BI para telemóvel** principalmente para monitorizar o progresso das quotas de vendas e explorar detalhes de novas oportunidades potenciais de vendas.

Caso seja programador, pode utilizar APIs do Power BI para emitir dados via push a conjuntos de dados ou incorporar dashboards e relatórios nas suas próprias aplicações personalizadas. Tem uma ideia para um novo elemento visual? Crie-o e partilhe-o com outras pessoas.  

Também pode utilizar cada elemento do Power BI em alturas diferentes, consoante o seu objetivo ou a sua função num determinado projeto.

A forma como utiliza o Power BI pode basear-se na funcionalidade ou no serviço do Power BI que é a melhor ferramenta para a sua situação. Por exemplo, pode utilizar o Power BI Desktop para criar relatórios para a sua equipa sobre estatísticas de envolvimento dos clientes e ver o progresso de fabrico e inventário num dashboard em tempo real no serviço Power BI. Cada parte do Power BI está disponível para si e é por isso que é tão flexível e convincente.

Explore os documentos que dizem respeito à sua função:
- Power BI Desktop para [*designers*](../desktop-what-is-desktop.md)
- Power BI para [*consumidores*](../consumer/end-user-consumer.md)
- Power BI para [*programadores*](../developer/what-can-you-do.md)
- Power BI para [*administradores*](../service-admin-administering-power-bi-in-your-organization.md)

## <a name="the-flow-of-work-in-power-bi"></a>O fluxo de trabalho no Power BI
Um fluxo de trabalho comum no Power BI começa pela ligação a origens de dados e pela criação de um relatório no Power BI Desktop. Em seguida, publica esse relatório a partir do Power BI Desktop no serviço Power BI e partilha-o para que os utilizadores finais no serviço Power BI e na aplicação móvel do Power BI possam ver e interagir com o relatório.
Este fluxo de trabalho é comum e mostra como os três elementos principais do Power BI se complementam entre si.

Eis uma [comparação detalhada do Power BI Desktop e do serviço Power BI](../designer/service-service-vs-desktop.md).

## <a name="on-premises-reporting-with-power-bi-report-server"></a>Relatórios no local com o Power BI Report Server

E se não estiver preparado para passar para a cloud e precisar de manter os seus relatórios atrás de uma firewall da empresa?  Continue a ler.

Pode criar, implementar e gerir relatórios paginados e móveis do Power BI no local com um conjunto de ferramentas e serviços prontos a utilizar fornecidos pelo Power BI Report Server.

![diagrama de relatórios no local](media/power-bi-overview/power-bi-report-server2.png)

O Power BI Report Server é uma solução que o utilizador implementa por trás da firewall e que, em seguida, fornece os seus relatórios aos utilizadores corretos de várias formas, sejam elas através da visualização num browser, num dispositivo móvel ou como uma mensagem de e-mail. E, porque o Power BI Report Server é compatível com o Power BI na cloud, pode passar para a cloud quando estiver preparado. 

Saiba mais sobre o [Power BI Report Server](../report-server/get-started.md).

## <a name="next-steps"></a>Próximos passos
- [Início Rápido: Saiba como utilizar o serviço Power BI](../service-the-new-power-bi-experience.md)   
- [Tutorial: Introdução ao serviço Power BI](../service-get-started.md)
- [Início Rápido: Ligar a Dados no Power BI Desktop](../desktop-quickstart-connect-to-data.md)
