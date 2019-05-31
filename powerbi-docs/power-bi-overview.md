---
title: O que é Power BI?
description: Descrição geral do Power BI e como as diferentes partes se encaixam - Power BI Desktop, o Power BI service, Power BI mobile, servidor de relatórios e Power BI embedded.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: overview
ms.date: 05/29/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 7236caba1c7a8eb07e93c6f2af7068141b8ac3a7
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66413033"
---
# <a name="what-is-power-bi"></a>O que é Power BI?
O **Power BI** é uma coleção de serviços de software, aplicações e conectores que funcionam em conjunto para transformar as origens de dados não relacionadas em informações coerentes, visualmente envolventes e interativas. Os dados podem ser uma folha de cálculo do Excel ou uma coleção de armazéns de dados híbridos no local e com base na cloud. Power BI permite-lhe facilmente ligar às suas origens de dados, visualizar e descobrir o que é importante e partilhá-lo com qualquer pessoa ou todos os utilizadores que pretende.

![diagrama que mostra as origens de entrada do Power BI](media/power-bi-overview/power-bi-input-new.png)

O Power BI pode ser simples e rápido, capaz de criar informações rápidas a partir de uma planilha do Excel ou uma base de dados local. Mas o Power BI também é robusto e de nível empresarial pronto para modelação extensa e análise em tempo real, bem como desenvolvimento personalizado. Ele pode ser a sua ferramenta de visualização e o pessoal de relatórios e também servir como o motor de decisão e análise para projetos de grupo, divisões ou empresas inteiras.

## <a name="the-parts-of-power-bi"></a>As partes do Power BI
Power BI é composto por: 
- Um aplicativo de desktop do Windows chamado **Power BI Desktop**
- Um SaaS online (*Software como um serviço*) serviço chamado o **serviço Power BI** 
- Power BI **aplicações móveis** para dispositivos Android, iOS e Windows

![Power BI Desktop, serviço, móvel](media/power-bi-overview/power-bi-blocks.png)

Estes três elementos&mdash;Power BI Desktop, o serviço e as aplicações móveis&mdash;foram concebidos para permitir que as pessoas, criar, partilhar e consumir informações de negócio da forma que serve-los, ou a sua função, de forma mais eficaz.

Um quarto elemento, o **Power BI Report Server**, permite-lhe publicar relatórios do Power BI num servidor de relatórios no local, depois de os criar no Power BI Desktop. Saiba mais sobre o [Power BI Report Server](#on-premises-reporting-with-power-bi-report-server).

## <a name="how-power-bi-matches-your-role"></a>Como o Power BI corresponde à sua função
O modo de utilização do Power BI poderá depender da sua função num projeto ou numa equipa. Outras pessoas, noutras funções, podem utilizar o Power BI forma diferente.

Por exemplo, pode utilizar principalmente o **serviço Power BI**. Mas um dos seus colegas que cria relatórios empresariais com muitos cálculos matemáticos poderá fazer um uso extensivo do **Power BI Desktop** para criar relatórios, publicar, em seguida, esses relatórios no serviço Power BI, onde poderá vê-los. Outro colega de trabalho, nas vendas, poderá utilizar principalmente a seus **aplicação de telemóvel do Power BI** para monitorizar o progresso em suas cotas de vendas e para explorar novos detalhes de oportunidades potenciais de vendas.

Caso seja programador, pode utilizar APIs do Power BI para emitir dados via push a conjuntos de dados ou incorporar dashboards e relatórios nas suas próprias aplicações personalizadas. Tem uma ideia para um novo elemento visual? Crie-o e partilhe-o com outras pessoas.  

Também poderá utilizar cada elemento do Power BI em alturas diferentes, consoante o que está tentando alcançar ou a sua função para um determinado projeto.

A forma como utiliza o Power BI pode basear-se na funcionalidade ou no serviço do Power BI que é a melhor ferramenta para a sua situação. Por exemplo, pode utilizar o Power BI Desktop para criar relatórios para a sua própria equipa sobre estatísticas de envolvimento do cliente e pode ver o inventário e o progresso em tempo real num dashboard no serviço Power BI de produção. Cada parte do Power BI está disponível para si e é por isso que é tão flexível e convincente.

Explore os documentos que dizem respeito à sua função:
- Power BI para [***designers***](desktop-what-is-desktop.md)
- Power BI para [***consumidores***](consumer/end-user-consumer.md)
- Power BI para [***programadores***](developer/what-can-you-do.md)
- Power BI para [***administradores***](service-admin-administering-power-bi-in-your-organization.md)

## <a name="the-flow-of-work-in-power-bi"></a>O fluxo de trabalho no Power BI
Um fluxo de trabalho no Power BI comum começa ao ligar a origens de dados e criação de um relatório no Power BI Desktop. Em seguida, publicar esses relatórios do Power BI Desktop no serviço Power BI e partilhá-lo para que os utilizadores finais no serviço Power BI e dispositivos móveis, pode ver e interagir com o relatório.
Este fluxo de trabalho é comum e mostra como os três elementos principais do Power BI se complementam entre si.

Eis uma [comparação detalhada do Power BI Desktop e do serviço Power BI](service-service-vs-desktop.md).

E se não estiver preparado para passar para a cloud e quiser manter os seus relatórios atrás de uma firewall de empresa?  Continue a ler.

## <a name="on-premises-reporting-with-power-bi-report-server"></a>Relatórios no local com o Power BI Report Server
Criar, implementar e gerir relatórios móveis e paginados do Power BI no local com o intervalo de prontos a utilizar ferramentas e serviços que fornece o Power BI Report Server.

![diagrama de relatórios no local](media/power-bi-overview/power-bi-report-server2.png)

O Power BI Report Server é uma solução que o utilizador implementa por trás da firewall e que, em seguida, fornece os seus relatórios aos utilizadores corretos de várias formas, sejam elas através da visualização num browser, num dispositivo móvel ou como uma mensagem de e-mail. E, porque o Power BI Report Server é compatível com o Power BI na cloud, pode passar para a cloud quando estiver preparado. 

Saiba mais sobre o [Power BI Report Server](report-server/get-started.md).

## <a name="next-steps"></a>Próximos passos
- [Início Rápido: Dê os primeiros no serviço Power BI](service-the-new-power-bi-experience.md)   
- [Tutorial: Introdução ao serviço Power BI](service-get-started.md)
- [Início Rápido: Ligar a Dados no Power BI Desktop](desktop-quickstart-connect-to-data.md)
