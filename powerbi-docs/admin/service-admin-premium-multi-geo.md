---
title: Suporte da Multi-Geo para o Power BI Premium
description: Saiba como pode implementar conteúdo em centros de dados em regiões diferentes da região base do inquilino do Power BI.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 01/20/2021
LocalizationGroup: Premium
ms.openlocfilehash: f68c01e503400b83fe3e0488fdc49e15f55d7067
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/22/2021
ms.locfileid: "98687057"
---
# <a name="configure-multi-geo-support-for-power-bi-premium"></a>Configurar o suporte da Multi-Geo para o Power BI Premium

A Multi-Geo é uma funcionalidade do Power BI Premium que ajuda os clientes multinacionais a cumprir os requisitos regionais, específicos da indústria ou da residência dos dados organizacionais. Como cliente do Power BI Premium, pode implementar conteúdo em centros de dados em regiões diferentes da região base do inquilino do Power BI. Uma área geográfica (geografia) pode conter mais do que uma região. Por exemplo, os Estados Unidos são uma área geográfica e E.U.A. Centro-Oeste e E.U.A. Centro-Sul são regiões nos Estados Unidos. Pode optar por implantar conteúdo em qualquer uma das seguintes geografias (geos) definidas no [mapa de geografia azul.](https://azure.microsoft.com/global-infrastructure/geographies/)

Nuvens soberanas suportam multi-geo em regiões dentro dessa nuvem.

> [!NOTE]
> Atualmente, a China North não suporta multi-geo para capacidades premium gen2.

A Multi-Geo também está agora disponível no Power BI Embedded. Leia mais em [Suporte da Multi-Geo no Power BI Embedded](../developer/embedded/embedded-multi-geo.md).

> [!NOTE]
> O Power BI Premium lançou recentemente uma nova versão do Premium, denominada **Premium Gen2**, que está atualmente em pré-visualização. O Premium Gen2 irá simplificar a gestão de capacidades Premium e reduzirá a sobrecarga de gestão. Para obter mais informações, veja [Power BI Premium Generation 2 (pré-visualização)](service-premium-what-is.md#power-bi-premium-generation-2-preview).

## <a name="enable-and-configure"></a>Ativar e configurar

Para obter as novas capacidades, ative a Multi-Geo ao selecionar uma região diferente da região predefinida na lista pendente.  Cada capacidade disponível mostra a região onde está atualmente localizada, por exemplo, **E.U.A. Centro-Oeste**.

![Tamanho da capacidade: selecione uma região. Power BI Multi-Geo](media/service-admin-premium-multi-geo/power-bi-multi-geo-capacity-size.png)

Depois de criar a capacidade, esta permanecerá nessa região e os conteúdos das áreas de trabalho criadas serão armazenados nessa região. Pode migrar as áreas de trabalho de uma região para outra através da lista pendente no ecrã de definições da área de trabalho.

![Editar área de trabalho: escolher uma capacidade disponível. Power BI Multi-Geo](media/service-admin-premium-multi-geo/power-bi-multi-geo-edit-workspace.png)

Verá esta mensagem para confirmar a alteração.

![Confirmação da alteração da área de trabalho atribuída](media/service-admin-premium-multi-geo/power-bi-multi-geo-change-assigned-workspace-capacity.png)

Não precisa de repor as credenciais do gateway durante a migração neste momento.  Depois de serem armazenadas na região da capacidade Premium, terá de repô-las após a migração.

Durante a migração, algumas operações podem falhar, como a publicação de novos conjuntos de dados ou a atualização agendada de dados.  

Os seguintes itens são armazenados na região Premium quando a Multi-Geo está ativada:

- Modelos (ficheiros .ABF) dos conjuntos de dados de importação e de Consulta Direta
- Cache de consulta
- Imagens R

Estes itens permanecem na região base do inquilino:

- Conjuntos de dados push
- Livros do Excel
- Metadados de relatórios/dashboards: por exemplo, nomes de mosaicos, consultas de mosaicos
- Barramentos de serviços para consultas de gateway ou tarefas de atualização agendadas
- Permissões
- Credenciais dos conjuntos de dados



## <a name="view-capacity-regions"></a>Ver as regiões das capacidades

No Portal de Administração, pode ver todas as capacidades do seu inquilino do Power BI e as regiões onde atualmente se encontram.

![Ver as capacidades Premium](media/service-admin-premium-multi-geo/power-bi-multi-geo-premium-capacities.png) 

## <a name="change-the-region-for-existing-content"></a>Alterar a região do conteúdo existente

Se precisar de alterar a região do conteúdo existente, tem duas opções.

- Criar uma segunda capacidade e mover as áreas de trabalho. Os utilizadores gratuitos não sofrerão qualquer período de indisponibilidade, desde que o inquilino tenha núcleos virtuais de reserva.
- Se não for possível criar uma segunda capacidade, poderá mover temporariamente o conteúdo para a capacidade partilhada a partir da capacidade Premium. Não precisa núcleos virtuais extras, mas os utilizadores gratuitos sofrerão alguns períodos de indisponibilidade.

## <a name="move-content-out-of-multi-geo"></a>Mover o conteúdo para fora da Multi-Geo  

Pode retirar as áreas de trabalho da capacidade Multi-Geo de uma das seguintes formas:

- Eliminar a capacidade atual onde está localizada a área de trabalho.  Essa ação move a área de trabalho de novo para a capacidade partilhada na região base.
- Migrar as áreas de trabalho individuais de novo para a capacidade Premium localizada no inquilino principal.

Os conjuntos de dados de formato de grande armazenamento não devem ser movidos da região onde foram criados. Os relatórios baseados em conjuntos de dados de grande formato não conseguirão carregar o conjunto de dados e devolverão o erro *Não foi possível carregar o modelo*. Mova os conjuntos de dados de formato de grande armazenamento para a sua região original para que fiquem disponíveis novamente.

## <a name="limitations-and-considerations"></a>Limitações e considerações

- Confirme que qualquer movimentação que efetuar entre regiões está conforme todos os requisitos de conformidade empresariais e governamentais antes de iniciar a transferência de dados.
- Uma consulta em cache armazenada numa região remota permanece inativa nessa região. No entanto, os outros dados em trânsito podem ir e voltar entre várias localizações geográficas.
- Ao mover dados de uma região para outra num ambiente Multi-Geo, os dados de origem pode permanecer na região da qual foram movidos até um máximo de 30 dias. Durante esse período, os utilizadores finais não terão acesso aos dados. São removidos desta região e destruídos durante esse período de 30 dias.
- O texto de consulta e o tráfego de resultados da consulta dos modelos de dados importados não transitam pela região base. Os metadados do relatório ainda provêm da região remota e certos estados de encaminhamento de DNS podem retirar o tráfego da região. 
- De momento, a funcionalidade de [fluxos de trabalho](../transform-model/dataflows/dataflows-introduction-self-service.md) não é suportada na Multi-Geo.
- Mover conjuntos de dados de formato de grande armazenamento da região onde foram criados fará com que os relatórios não consigam carregar o conjunto de dados. Mova os conjuntos de dados de grande armazenamento para a sua região original para que fiquem disponíveis. 

## <a name="next-steps"></a>Próximos passos

- [O que é o Power BI Premium?](service-premium-what-is.md)
- [Multi-Geo para as capacidades do Power BI Embedded](../developer/embedded/embedded-multi-geo.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

O Power BI introduziu o Power BI Premium Gen2 como uma oferta de pré-visualização, que melhora a experiência do Power BI Premium nos seguintes aspetos:
* Desempenho
* Licenciamento por utilizador
* Maior dimensionamento
* Métricas melhoradas
* Dimensionamento automático
* Sobrecarga de gestão reduzida

Para obter mais informações sobre o Power BI Premium Gen2, veja [Power BI Premium Generation 2 (pré-visualização)](service-premium-what-is.md#power-bi-premium-generation-2-preview).
