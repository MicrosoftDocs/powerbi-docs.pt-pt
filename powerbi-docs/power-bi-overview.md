---
title: O que é Power BI?
description: 'Descrição geral do Power BI e como as várias partes encaixam: Power BI Desktop, serviço Power BI, Power BI Mobile, Report Server, Power BI Embedded.'
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: overview
ms.date: 02/07/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: b1efe45d52b5a7a18a86407b41e8af287d3c8260
ms.sourcegitcommit: b717118c44499c8fd8f57534a275f2f78aacc0f1
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/09/2019
ms.locfileid: "55971654"
---
# <a name="what-is-power-bi"></a>O que é Power BI?
O **Power BI** é uma coleção de serviços de software, aplicações e conectores que funcionam em conjunto para transformar as origens de dados não relacionadas em informações coerentes, visualmente envolventes e interativas. Os dados podem ser uma folha de cálculo do Excel ou uma coleção de armazéns de dados híbridos no local e com base na cloud. O **Power BI** permite-lhe ligar facilmente às suas origens de dados, visualizar e descobrir o que é importante e partilhá-lo com qualquer pessoa ou com todas as pessoas que quiser.

![diagrama que mostra as origens de entrada do Power BI](media/power-bi-overview/power-bi-input-new.png)

O **Power BI** pode ser simples e rápido – com capacidade para criar informações rápidas a partir de uma folha de cálculo do Excel ou de uma base de dados local. No entanto, o **Power BI** também é robusto e de nível empresarial, está preparado para modelação extensa e análise em tempo real, bem como desenvolvimento personalizado. Por isso, pode ser a sua ferramenta pessoal de relatórios e visualização. Também pode servir como o motor de decisão e análise para projetos de grupo, divisões ou empresas inteiras.

## <a name="the-parts-of-power-bi"></a>As partes do Power BI
O Power BI é composto por uma aplicação de ambiente de trabalho do Windows chamada **Power BI Desktop**, um serviço SaaS online (*Software como um Serviço*) denominado o **serviço Power BI** e **aplicações móveis** do Power BI para dispositivos Windows, iOS e Android.

![Power BI Desktop, serviço, móvel](media/power-bi-overview/power-bi-blocks.png)

Estes três elementos: o **Power BI Desktop**, o **serviço** e as **aplicações móveis**, foram concebidos para permitir que as pessoas criem, partilhem e consumam informações de negócio da forma mais eficaz para elas ou para a respetiva função.

Um quarto elemento, o **Power BI Report Server**, permite-lhe publicar relatórios do Power BI num servidor de relatórios no local, depois de os criar no Power BI Desktop. Saiba mais sobre o [Power BI Report Server](#on-premises-reporting-with-power-bi-report-server).

## <a name="how-power-bi-matches-your-role"></a>Como o Power BI corresponde à sua função
O modo de utilização do Power BI poderá depender da sua função num projeto ou numa equipa. Outras pessoas, noutras funções, poderão utilizar o Power BI de forma diferente, o que é normal.

Por exemplo, pode utilizar principalmente o **serviço Power BI**. Mas um dos seus colegas que cria relatórios empresariais com muitos cálculos matemáticos poderá fazer um uso extensivo do **Power BI Desktop** para criar relatórios, publicar, em seguida, esses relatórios no serviço Power BI, onde poderá vê-los. Outra das suas colegas, no departamento de vendas, poderá utilizar principalmente a aplicação do Power BI para telemóvel para monitorizar o progresso nas suas quotas de vendas e para explorar detalhes de novas oportunidades potenciais de vendas.

Caso seja programador, pode utilizar APIs do Power BI para emitir dados via push a conjuntos de dados ou incorporar dashboards e relatórios nas suas próprias aplicações personalizadas. Tem uma ideia para um novo elemento visual? Crie-o e partilhe-o com outras pessoas.  

Também poderá utilizar cada elemento do **Power BI** em alturas diferentes, consoante o que estiver a tentar obter ou consoante a sua função num determinado projeto.

Talvez utilize o **Power BI Desktop** para criar relatórios para a sua própria equipa sobre estatísticas de envolvimento do cliente. Talvez também veja o progresso do inventário e do fabrico num dashboard em tempo real no serviço. A forma como utiliza o Power BI pode basear-se na funcionalidade ou no serviço do Power BI que é a melhor ferramenta para a sua situação. Cada parte do Power BI está disponível para si e é por isso que é tão flexível e convincente.

Explore os documentos que dizem respeito à sua função:
- Power BI para [***designers***](desktop-what-is-desktop.md)
- Power BI para [***consumidores***](consumer/end-user-consumer.md)
- Power BI para [***programadores***](developer/what-can-you-do.md)
- Power BI para [***administradores***](service-admin-administering-power-bi-in-your-organization.md)

## <a name="the-flow-of-work-in-power-bi"></a>O fluxo de trabalho no Power BI
Um fluxo de trabalho comum no Power BI começa pela ligação a origens de dados e pela criação de um relatório no **Power BI Desktop**. Em seguida, publica esse relatório a partir do **Power BI Desktop** no **serviço Power BI** e partilha-o para que os utilizadores finais no **serviço** e nos **dispositivos móveis** possam ver e interagir com o relatório.
Este fluxo de trabalho é comum e mostra como os três elementos principais do Power BI se complementam entre si.

Eis uma [comparação detalhada do Power BI Desktop e do serviço Power BI](service-service-vs-desktop.md).

E se não estiver preparado para passar para a cloud e quiser manter os seus relatórios atrás de uma firewall de empresa?  Continue a ler.

## <a name="on-premises-reporting-with-power-bi-report-server"></a>Relatórios no local com o Power BI Report Server
Crie, implemente e gira relatórios paginados, móveis e do Power BI no local com um conjunto de ferramentas e serviços prontos a utilizar, proporcionados pelo Power BI Report Server.

![diagrama de relatórios no local](media/power-bi-overview/power-bi-report-server2.png)

O Power BI Report Server é uma solução que o utilizador implementa por trás da firewall e que, em seguida, fornece os seus relatórios aos utilizadores corretos de várias formas, sejam elas através da visualização num browser, num dispositivo móvel ou como uma mensagem de e-mail. E, porque o Power BI Report Server é compatível com o Power BI na cloud, pode passar para a cloud quando estiver preparado. 

Saiba mais sobre o [Power BI Report Server](report-server/get-started.md).

## <a name="next-steps"></a>Próximos passos
[Sign in, get some data, and learn your way around Power BI service](service-the-new-power-bi-experience.md)  (Iniciar sessão, obter alguns dados e saber como utilizar o serviço Power BI)  
[Tutorial: Introdução ao serviço Power BI](service-get-started.md)
[Início Rápido: Ligar a Dados no Power BI Desktop](desktop-quickstart-connect-to-data.md)