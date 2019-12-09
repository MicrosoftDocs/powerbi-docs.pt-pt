---
title: FAQ sobre elevada disponibilidade, ativação pós-falha e recuperação após desastre do Power BI
description: Compreenda de que forma o serviço Power BI oferece elevada disponibilidade, continuidade de negócio e recuperação após desastre aos seus utilizadores.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 24867d231cca0135c09119f4b885b393cb2b8dd8
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/02/2019
ms.locfileid: "74699067"
---
# <a name="power-bi-high-availability-failover-and-disaster-recovery-faq"></a>FAQ sobre elevada disponibilidade, ativação pós-falha e recuperação após desastre do Power BI

Este artigo explica de que forma o serviço Power BI oferece elevada disponibilidade, continuidade de negócio e recuperação após desastre aos seus utilizadores. Após a leitura deste artigo, deverá compreender melhor de que forma é alcançada a elevada disponibilidade, as circunstâncias em que o Power BI realiza uma ativação pós-falha e o que deve esperar do serviço após uma falha.

## <a name="what-does-high-availability-mean-for-power-bi"></a>Qual é o significado da "elevada disponibilidade" no Power BI?

O Power BI é um software como um serviço (SaaS) totalmente gerido.  Foi concebido e é operado pela Microsoft para ser resiliente a falhas de infraestrutura, para que os utilizadores possam sempre ter acesso aos seus relatórios.  O serviço é suportado por um [SLA de 99,9%](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37).

## <a name="what-is-a-power-bi-failover"></a>O que é uma ativação pós-falha do Power BI?

O Power BI mantém múltiplas instâncias de cada componente nos datacenters do Azure (também denominados regiões) para garantir a continuidade de negócio. Se houver uma indisponibilidade ou um problema que cause a inacessibilidade ou inoperabilidade do Power BI numa região, o Power BI efetua a ativação pós-falha de todos os seus componentes nessa região para uma instância de cópia de segurança. A ativação pós-falha restaura a disponibilidade e operabilidade da instância do serviço Power BI numa nova região (normalmente, na mesma localização geográfica, conforme indicado no [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location)).

Uma instância do serviço Power BI ativada após a falha suporta apenas _operações de leitura_, o que significa que as seguintes operações não são suportadas durante a ativação pós-falha: atualizações, operações de publicação de relatórios, modificações de dashboards ou relatórios e outras operações que exigem alterações a metadados do Power BI (por exemplo, a inserção de um comentário num relatório).  As operações de leitura, como a apresentação de dashboards e de relatórios (que não são baseadas no DirectQuery ou no Live Connect para origens de dados no local), continuam a funcionar normalmente.

## <a name="how-are-backup-instances-kept-in-sync-with-my-data"></a>Como é mantida a sincronização das instâncias de cópia de segurança com os meus dados?

Todos os componentes do serviço Power BI sincronizam regularmente as respetivas instâncias de cópia de segurança. O nosso objetivo é alcançar uma sincronização para um ponto anterior no tempo de 15 minutos para qualquer conteúdo carregado ou alterado no Power BI. O Power BI utiliza [replicação georredundante do armazenamento do Azure](/azure/storage/common/storage-redundancy-grs) e [replicação georredundante do Azure SQL](/azure/sql-database/sql-database-active-geo-replication) para garantir que as instâncias de cópia de segurança existem noutras regiões e podem ser utilizadas no caso de ocorrer uma ativação pós-falha.

## <a name="where-are-the-failover-clusters-located"></a>Onde se encontram os clusters de ativação pós-falha?

As instâncias de cópia de segurança residem na mesma área geográfica que selecionou quando inscreveu a sua organização no Power BI, exceto nas áreas indicadas no [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location). Uma área geográfica pode conter várias regiões e a Microsoft pode replicar dados para qualquer região de uma determinada área geográfica, para resiliência de dados. A Microsoft não irá replicar ou mover dados de clientes para fora da área geográfica. Para obter um mapeamento das áreas geográficas oferecidas pelo Power BI e das regiões dentro delas, veja o [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location).

## <a name="how-does-microsoft-decide-to-failover"></a>Como é que a Microsoft determinam quando realizar uma ativação pós-falha?

Há dois sistemas diferentes que indicam quando poderá ser necessária uma ativação pós-falha:

- As nossas investigações de monitorização externas e internas indicam uma falta de disponibilidade ou a incapacidade de operar adequadamente. Estas indicações podem ser baseadas em falhas detetadas em componentes do Power BI ou num ou mais dos serviços dos quais o Power BI depende numa região.
- A equipa de operações centrais do Microsoft Azure informa-nos de uma falha crítica numa região.

Em ambos os casos, são os membros da equipa executiva do Power BI que decidem realizar a ativação pós-falha. A decisão em si não é automatizada. Assim que a decisão é tomada, o processo de ativação pós-falha é iniciado automaticamente.

## <a name="how-do-i-know-power-bi-is-now-in-failover-mode"></a>Como é que sei se o Power BI está em modo de ativação pós-falha?

É publicada uma notificação na página de suporte do Power BI ([https://powerbi.microsoft.com/support/](https://powerbi.microsoft.com/support/)). A notificação inclui as principais operações que não estão disponíveis durante a ativação pós-falha, incluindo publicações, atualizações, criação de dashboards, duplicação de dashboards e alterações de permissões.

## <a name="how-long-does-it-take-power-bi-to-fail-over"></a>Quanto tempo demora a ativação pós-falha do Power BI?

Quando a decisão de efetuar uma ativação pós-falha é tomada, a disponibilidade de uma instância de ativação pós-falha pode demorar até 60 minutos.

## <a name="when-does-my-power-bi-instance-return-to-the-original-region"></a>Quando é que a minha instância do Power BI regressa à região original?

As instâncias do serviço Power BI irão regressar à sua região original quando o problema que tiver causado a ativação pós-falha for resolvido. Veja a página de suporte do Power BI: Quando o problema for resolvido, a equipa do Power BI irá remover a notificação que descreve a ativação pós-falha. Nesse momento, as operações devem ficar normalizadas.

## <a name="am-i-responsible-for-the-availability-of-my-power-bi-solution"></a>Sou responsável pela disponibilidade da minha solução do Power BI?

Se a solução do Power BI utilizada na sua organização incluir um dos seguintes elementos, terá de tomar algumas medidas para garantir que mantém a elevada disponibilidade da mesma:

- Se a sua organização utilizar o Power BI Premium, terá de garantir que a capacidade Premium tem a dimensão necessária para cumprir os requisitos de carga da sua implementação.  O [Power BI Premium Planning and Deployment whitepaper](https://aka.ms/Premium-Capacity-Planning-Deployment) (Documento Técnico de Planeamento e Implementação do Power BI Premium) e a [aplicação Power BI Premium Capacity Metrics](service-admin-premium-monitor-capacity.md) podem ajudá-lo a planear e cumprir estes requisitos. Adicionamos regularmente novas funcionalidades à aplicação de métricas e ao portal de administração no Power BI para ajudar.
- Se a sua organização aceder a origens de dados no local através do gateway de dados no local, terá de configurar o gateway [da forma descrita neste artigo](/data-integration/gateway/service-gateway-high-availability-clusters) para suportar a elevada disponibilidade. Siga esta documentação de orientação quer esteja a atualizar relatórios em modo de importação ou a aceder a dados ou modelos de dados através do DirectQuery ou Live Connect.

## <a name="will-gateways-function-when-in-failover-mode"></a>Os gateways funcionam no modo de ativação pós-falha?

Não. Os dados necessários de origens de dados no local (quaisquer relatórios e dashboards baseados no DirectQuery e no Live Connect) não funcionam durante uma ativação pós-falha. No entanto, a configuração do gateway não é alterada: quando a instância do Power BI regressa ao seu estado original, os gateways retomam as suas funções normais.
