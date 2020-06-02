---
title: Use DirectQuery with dataflows in Power BI (preview) (Utilizar o DirectQuery com fluxos de dados no Power BI [pré-visualização])
description: Saiba como utilizar o DirectQuery com fluxos de dados no Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/21/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 469b8b13f77c56f9371ae8c1c81dcb94278c62e0
ms.sourcegitcommit: 5e5a7e15cdd55f71b0806016ff91256a398704c1
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/22/2020
ms.locfileid: "83794002"
---
# <a name="use-directquery-with-dataflows-in-power-bi-preview"></a>Use DirectQuery with dataflows in Power BI (preview) (Utilizar o DirectQuery com fluxos de dados no Power BI [pré-visualização])

Pode utilizar o DirectQuery para ligar diretamente a fluxos de dados e, assim, ligar diretamente ao seu fluxo de dados sem ter de importar os respetivos dados. 

Utilizar o DirectQuery com fluxos de dados permite as seguintes melhorias aos seus processos do Power BI e fluxos de dados:

* **Evitar as agendas de atualização em separado** – o DirectQuery liga diretamente a um fluxo de dados, não sendo necessário criar um conjunto de dados importado. Como tal, utilizar o DirectQuery com os seus fluxos de dados significa que já não precisa de separar as agendas de atualização para o fluxo de dados e o conjunto de dados para garantir que os seus dados estão sincronizados.

* **Filtrar dados** – o DirectQuery é útil para trabalhar numa vista filtrada dos dados dentro de um fluxo de dados. Se quiser filtrar os dados e trabalhar com um subconjunto de dados mais pequeno no seu fluxo de dados, pode utilizar o DirectQuery (e o motor de computação) para filtrar os dados do fluxo de dados e trabalhar com o subconjunto filtrado de que precisa.


## <a name="using-directquery-for-dataflows"></a>Utilizar o DirectQuery para fluxos de dados

A utilização do DirectQuery com fluxos de dados é uma funcionalidade de pré-visualização disponível a partir da versão de maio de 2020 do Power BI Desktop. 

Também existem pré-requisitos para utilizar o DirectQuery com fluxos de dados:

* O seu fluxo de dados tem de residir numa área de trabalho do Power BI Premium
* O **motor de computação** tem de estar ativado. Para obter mais informações sobre o motor de computação, veja [o motor de computação melhorado](service-dataflows-enhanced-compute-engine.md).

## <a name="enable-directquery-for-dataflows"></a>Ativar o DirectQuery para fluxos de dados

Para garantir que o seu fluxo de dados está disponível para acesso ao DirectQuery, o motor de computação avançado tem de estar no respetivo estado otimizado. Para ativar o DirectQuery para fluxos de dados, defina a nova opção **Definições do motor de computação avançado** para **Ativado**. A seguinte imagem mostra a definição devidamente selecionada.

![Ativar o motor de computação avançado para os fluxos de dados](media/service-dataflows-directquery/dataflows-directquery-01.png)

Após aplicar essa definição, atualize o fluxo de dados para que a otimização seja aplicada. 


## <a name="considerations-and-limitations"></a>Considerações e limitações

Existem algumas limitações conhecidas com o DirectQuery e os fluxos de dados, explicadas na lista seguinte.

* O DirectQuery para fluxos de dados não funciona com a funcionalidade de **pré-visualização de metadados melhorados** ativada. Esta exclusão deverá ser removida num lançamento mensal futuro do Power BI Desktop.

* Durante o período de pré-visualização desta funcionalidade, alguns clientes poderão ter problemas de desempenho ou com tempos limite ao utilizar o DirectQuery com fluxos de dados. Estes problemas estão a ser ativamente resolvidos durante este período de pré-visualização.

* Atualmente, os modelos compostos/mistos com origens de dados de importação e do DirectQuery não são suportados.

* Os fluxos de dados grandes podem deparar-se com problemas de limite de tempo durante as visualizações. Prevê-se que esta limitação seja removida no âmbito da disponibilidade geral da funcionalidade. Entretanto, os fluxos de dados grandes que se deparem com problemas de limite de tempo devem utilizar o Modo de importação.

* Nas definições da origem de dados, o conector de fluxos de dados mostrará credenciais inválidas se estiver a utilizar o DirectQuery. Esta situação não afeta o comportamento e o conjunto de dados irá funcionar corretamente. Este problema deixará de existir à medida que nos aproximarmos da disponibilidade geral.



## <a name="next-steps"></a>Passos seguintes

Os artigos seguintes são úteis para obter mais informações e cenários quando utilizar fluxos de dados:

* [Preparação personalizada de dados com fluxos de dados](service-dataflows-overview.md)
* [Utilizar entidades calculadas no Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Utilizar fluxos de dados com origens de dados no local](service-dataflows-on-premises-gateways.md)
* [Recursos para programadores para fluxos de dados do Power BI](service-dataflows-developer-resources.md)
* [Fluxos de dados e integração do Azure Data Lake (Pré-visualização)](service-dataflows-azure-data-lake-integration.md)

Para obter mais informações sobre o Common Data Service, pode ler o seguinte artigo de descrição geral:
* [Common Data Service – descrição geral](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [Saiba mais sobre o esquema do Common Data Service e as entidades no GitHub](https://github.com/Microsoft/CDM)

Artigos do Power BI Desktop relacionados:

* [Ligar a conjuntos de dados no serviço Power BI a partir do Power BI Desktop](../connect-data/desktop-report-lifecycle-datasets.md)
* [Descrição geral de consulta no Power BI Desktop](desktop-query-overview.md)

Artigos do Power BI Desktop relacionados:
* [Configurar a atualização agendada](../connect-data/refresh-scheduled-refresh.md)
