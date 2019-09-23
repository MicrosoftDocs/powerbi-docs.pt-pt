---
title: Melhores práticas dos fluxos de dados do Power BI
description: Melhores práticas dos fluxos de dados do Power BI
author: mohaali
manager: mohaali
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/10/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: c5aeb74277379b46398dc709f5deda1d10dc0926
ms.sourcegitcommit: 7eb74b060de080152c190ac7eb6b64767f8d6626
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70919612"
---
# <a name="dataflows-best-practice"></a>Melhores práticas dos fluxos de dados

Este artigo disponibiliza as melhores práticas para criar fluxos de dados no Power BI. Pode utilizar estas orientações para criar fluxos de dados e aplicar estas práticas aos seus próprios fluxos de dados.

> [!NOTE]
> As recomendações feitas neste artigo são orientações. Para cada prática recomendada neste artigo, pode haver motivos legítimos para se desviar destas orientações. 
> 
> 

### <a name="split-ingestion-and-transformation-to-use-the-enhanced-compute-engine"></a>Dividir a ingestão e a transformação para utilizar o mecanismo de computação melhorado

Ao criar fluxos de dados, pode ter a tentação de criar um único fluxo de dados com todas as entidades, transformações, associações e melhorias num único lugar. Para conjuntos de dados menores, um único fluxo de dados pode ser eficiente. Mas quando se lida com volumes de dados maiores, a execução de associações ou de determinadas transformações pode, às vezes, enfrentar limitações ou limites de memória. Para resolver estes problemas, foi lançado um mecanismo avançado para os utilizadores do Power BI Premium que fazem o dimensionamento para volumes de dados muito maiores. O mecanismo de computação melhorado funciona apenas em relação a entidades ligadas ou calculadas, por isso, criar um fluxo de dados distinto para ingestão e um fluxo de dados ligado para executar todas as fusões e transformações complexas pode beneficiar com o mecanismo avançado.

A divisão dos fluxos de dados também é benéfica para diagnosticar e depurar problemas de atualização, especialmente quando se trabalha com origens que têm limitações.

### <a name="perform-actions-that-can-use-the-enhanced-compute-engine"></a>Executar ações que podem utilizar o mecanismo de computação melhorado

Certifique-se de utilizar o mecanismo de computação melhorado, ao garantir que executa associações e filtra as transformações primeiro numa entidade calculada antes de executar outros tipos de transformações.

### <a name="split-dataflows-when-connecting-to-sharepoint"></a>Dividir os fluxos de dados ao ligar ao SharePoint

Ao trabalhar com o SharePoint e ao ligar-se a vários ficheiros, pode notar falhas esporádicas. O SharePoint limita os pedidos para garantir que permanece fiável e reativo. Como consequência, ao ligar-se a ficheiros do Excel a partir do SharePoint, pode estar inclinado a transferir todos os ficheiros num único fluxo de dados. Se estiver a transferir muitos ficheiros, mais de 20, crie dois fluxos de dados ou mais para dividir a carga de atualização e superar a limitação do SharePoint.

### <a name="avoid-scheduling-refresh-for-linked-entities-inside-the-same-workspace"></a>Evite a atualização de agendamento de entidades ligadas dentro da mesma área de trabalho

Se for bloqueado regularmente nos seus fluxos de dados que contêm entidades ligadas, este bloqueio poderá ser resultante do fluxo de dados dependente correspondente dentro da mesma área de trabalho, o qual é bloqueado durante a atualização do fluxo de dados. Este bloqueio fornece precisão transacional e garante que os dois fluxos de dados são atualizados com êxito, mas pode impedir que faça a sua edição. 

Se configurar um agendamento distinto para o fluxo de dados ligado, os fluxos de dados podem ser atualizados desnecessariamente e impedirão que edite o fluxo de dados. Existem duas recomendações para evitar este problema: 

* Evitar definir uma agenda de atualização para um fluxo de dados ligado na mesma área de fluxo de dados de origem
* Se quiser configurar uma agenda de atualização separadamente e quiser evitar o comportamento de bloqueio, separe o fluxo de dados numa área de trabalho distinta.

### <a name="create-a-separate-workspace-for-ingestion-transformation"></a>Criar uma área de trabalho separada para ingestão, transformação

Para fornecer acesso aos dados do fluxo de dados subjacente para muitos utilizadores, sem permitir acesso aos dados brutos do sistema de origem subjacente, crie uma área de trabalho separada que tenha todos os dados de que precisa para partilhar e atribua permissões. No momento, não são suportadas as permissões de fluxo de dados individuais.

### <a name="ensure-capacity-is-in-the-same-region"></a>Verificar se a capacidade está na mesma região

No momento, os fluxos de dados não são suportados nas regiões de múltiplas localizações geográficas. A capacidade Premium tem de estar na mesma região que o seu inquilino do Power BI.

### <a name="separate-on-premises-sources-from-cloud-sources"></a>Separar origens no local de origens na cloud

Além das melhores práticas descritas anteriormente, pode criar um fluxo de dados separado para cada tipo de origem, como, por exemplo, no local, cloud, SQL Server, Apache Spark, Dynamics e assim por diante. Recomenda-se vivamente que divida o fluxo de dados por tipo de origem de dados. Esta separação por tipo de origem ajuda na rápida resolução dos problemas e evita os limites internos ao atualizar os fluxos de dados.

### <a name="separate-dataflows-into-a-separate-capacity"></a>Fluxos de dados separados numa capacidade separada

Se estiver a enfrentar limitações ou estiver a ver falhas regulares nos fluxos de dados devido a limites de memória na capacidade, considere separar os fluxos de dados ou aumentar verticalmente a capacidade Premium para memória adicional.

## <a name="next-steps"></a>Próximos Passos

Este artigo forneceu informações sobre as melhores práticas dos fluxos de dados. Para obter mais informações sobre os fluxos de dados, os artigos seguintes podem ser úteis:

* [Preparação personalizada de dados com fluxos de dados](service-dataflows-overview.md)
* [Criar e utilizar fluxos de dados no Power BI](service-dataflows-create-use.md)
* [Utilizar entidades calculadas no Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Utilizar fluxos de dados com origens de dados no local](service-dataflows-on-premises-gateways.md)

Para obter informações sobre o desenvolvimento do CDM e os recursos de tutoriais, veja o seguinte:
* [Common Data Service – descrição geral](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [Pastas de CDM](https://go.microsoft.com/fwlink/?linkid=2045304)
* [Definição do ficheiro de modelo do CDM](https://go.microsoft.com/fwlink/?linkid=2045521)


Para obter mais informações sobre o Power Query e a atualização agendada, pode ler estes artigos:
* [Descrição geral das consultas no Power BI Desktop](desktop-query-overview.md)
* [Configurar a atualização agendada](refresh-scheduled-refresh.md)
