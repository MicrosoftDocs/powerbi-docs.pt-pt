---
title: Atualização automática de páginas no Power BI Desktop
description: Este artigo mostra como atualizar automaticamente páginas para origens do DirectQuery no Power BI Desktop.
author: davidiseminger
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 06/10/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 9a1e42b4901e8659bb5d999294f29a80a0389280
ms.sourcegitcommit: 10c5b6cd5e7070f96de8a9f1d9b95f3d242ac7f2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/21/2020
ms.locfileid: "86557239"
---
# <a name="automatic-page-refresh-in-power-bi-desktop"></a>Atualização automática de páginas no Power BI Desktop 

Quando monitoriza eventos críticos, é importante que os dados sejam atualizados assim que a origem de dados é atualizada. Por exemplo, na indústria transformadora, é essencial saber quando uma máquina tem problemas de funcionamento ou está perto de os ter.

A funcionalidade de atualização automática de páginas no Power BI permite que a página de relatório ativa consulte quanto à existência de novos dados, com uma cadência predefinida, nas [origens do DirectQuery](https://docs.microsoft.com/power-bi/desktop-directquery-about).

## <a name="using-automatic-page-refresh"></a>Utilizar a atualização automática de página

A atualização automática de página só está disponível para as origens de dados do DirectQuery.

Para utilizar a atualização automática de página, selecione a página de relatório para a qual deseja ativar a atualização. No painel **Visualizações**, selecione o botão **Formatação** (um rolo de tinta) e localize **Atualização de páginas** próximo da parte inferior do painel. 

![Localização da atualização de página](media/desktop-automatic-page-refresh/automatic-page-refresh-01.png)

A imagem seguinte mostra o cartão **Atualização de página**. Os elementos numerados estão descritos depois da imagem.

![Cartão de atualização de página](media/desktop-automatic-page-refresh/automatic-page-refresh-02.png)

1.    Ativa ou desativa a atualização de páginas
2.    Valor do número do intervalo de atualização de páginas
3.    Unidade do intervalo de atualização de páginas

Neste cartão, pode ativar a atualização de páginas e selecionar a duração da atualização. O valor predefinido é de 30 minutos (o intervalo mínimo de atualização é de um segundo). O relatório começará a ser atualizado com o intervalo definido. 

## <a name="determining-the-page-refresh-interval"></a>Determinar o intervalo de atualização de página

Quando a atualização automática de página está ativada, o Power BI Desktop está constantemente a enviar consultas para a origem de dados do DirectQuery. Depois do envio da consulta, ocorre um atraso até os dados serem devolvidos. Assim, para intervalos de atualização curtos, deve confirmar que as consultas devolveram com êxito os dados da consulta dentro do intervalo configurado. Se os dados não forem devolvidos dentro do intervalo, os elementos visuais serão atualizados com menos frequência do que o configurado.

Como melhor prática, o intervalo de atualização deve, pelo menos, corresponder à taxa de chegada esperada dos novos dados:

* Se chegarem novos dados à origem a cada 20 minutos, o intervalo de atualização não poderá ser inferior a 20 minutos. 

* Se chagarem novos dados a cada segundo, defina o intervalo para um segundo. 

Para intervalos de baixa atualização, como um segundo, tenha em consideração fatores como os seguintes:
- O tipo da origem de dados do DirectQuery
- A carga que as consultas criam no mesmo
- A distância dos visualizadores do relatório do datacenter da capacidade 

Pode estimar os tempos de devolução através do Analisador de Desempenho no Power BI Desktop. O Analisador de Desempenho permite-lhe verificar se cada consulta de elemento visual tem tempo suficiente para voltar com os resultados da origem. Também permite determinar onde o tempo é gasto. Com base nos resultados do Analisador de Desempenho, pode ajustar a origem de dados ou experimentar com outros elementos visuais e medidas no relatório.

Esta imagem mostra os resultados de um DirectQuery no Analisador de Desempenho:

![Resultados do Analisador de Desempenho](media/desktop-automatic-page-refresh/automatic-page-refresh-03.png)

Vamos considerar outras características desta origem de dados: 

-    Os dados chegam a uma taxa de 2 segundos. 
-    O Analisador de Desempenho mostra uma consulta máxima + tempo de apresentação de aproximadamente 4,9 segundos (4688 milissegundos). 
-    A origem de dados está configurada para lidar com aproximadamente 1000 consultas simultâneas por segundo. 
-    Espera que aproximadamente 10 utilizadores visualizem o relatório em simultâneo.

O que resulta na seguinte equação:

**5 elementos visuais x 10 utilizadores = aproximadamente 50 consultas**

O resultado deste cálculo mostra muito mais carga do que a origem de dados consegue suportar. Os dados chegam a uma taxa de dois segundos. Assim, esta deve ser a sua taxa de atualização. No entanto, dado que a conclusão da consulta demora cerca de cinco segundos, deve defini-la para mais de cinco segundos. 

Note também que este resultado pode diferir à medida que publica o relatório no serviço. Esta diferença ocorre porque o relatório utilizará a instância do Azure Analysis Services alojada na cloud. Pode querer ajustar as taxas de atualização em conformidade. 

Para ter em conta o tempo das consultas e de atualização, o Power BI só executará a próxima consulta de atualização quando todas as consultas de atualização restantes forem concluídas. Assim, mesmo que o intervalo de atualização seja menor do que o tempo que as consultas demoram a ser processadas, o Power BI só atualizará novamente quando as consultas restantes forem concluídas. 

Agora, vamos ver como pode, potencialmente, detetar e diagnosticar problemas de desempenho como um administrador de capacidade. Também pode ver a secção [Perguntas mais frequentes](#frequently-asked-questions) mais adiante neste artigo, para obter mais perguntas e respostas sobre desempenho e a resolução de problemas.

## <a name="automatic-page-refresh-in-the-power-bi-service"></a>Atualização automática de página no serviço Power BI

Também pode definir os intervalos de atualização automática de páginas para os relatórios que foram criados no Power BI Desktop e publicados no serviço Power BI. 

Para configurar a atualização automática de páginas para os relatórios no serviço Power BI, siga os passos semelhantes que utilizaria no Power BI Desktop. Quando está configurada no serviço Power BI, a atualização de página automática também suporta conteúdos do [Power BI Embedded](../developer/embedded/embedding.md). Esta imagem mostra a configuração da **Atualização de páginas** do serviço Power BI:

![Atualização automática de página no serviço Power BI](media/desktop-automatic-page-refresh/automatic-page-refresh-04.png)

Estas descrições correspondem aos elementos numerados: 

1.    Ativa ou desativa a atualização de páginas.
2.    Valor do número do intervalo de atualização de páginas. Tem de ser um número inteiro.
3.    Unidade do intervalo de atualização de páginas.

### <a name="page-refresh-intervals"></a>Intervalos da atualização de páginas

Os intervalos da atualização de páginas permitidos no serviço Power BI são afetados pelo tipo de área de trabalho do relatório. Esta situação aplica-se aos seguintes relatórios:

* Publicar um relatório numa área de trabalho que tem a atualização automática de páginas ativada
* Editar um intervalo de atualização de páginas que já se encontra numa área de trabalho
* Criar um relatório diretamente no serviço

O Power BI Desktop não tem restrições para intervalos de atualização. O intervalo de atualização pode ser tão frequente como a cada segundo. No entanto, quando os relatórios são publicados no serviço Power BI, aplicam-se determinadas restrições. Estas restrições estão descritas nas secções seguintes.

### <a name="restrictions-on-refresh-intervals"></a>Restrições dos intervalos de atualização

No serviço Power BI, aplicam-se restrições à atualização automática de páginas com base em fatores como a área de trabalho e se está a utilizar serviços Premium.

Para esclarecer como estas restrições funcionam, vamos começar com algum contexto sobre as capacidades e áreas de trabalho.

As *capacidades* são um conceito importante do Power BI. Representam um conjunto de recursos (armazenamento, processador e memória) utilizados para alojar e fornecer conteúdo do Power BI. As capacidades podem ser partilhadas ou dedicadas. Uma *capacidade partilhada* é partilhada com outros clientes da Microsoft. Uma *capacidade dedicada* está totalmente comprometida com um único cliente. Para obter uma introdução às capacidades dedicadas, veja [Gerir as capacidades Premium](../admin/service-premium-capacity-manage.md).

Na capacidade partilhada, as cargas de trabalho são executadas em recursos computacionais partilhados com outros clientes. Dado que a capacidade tem de partilhar recursos, são impostos limites para garantir *fair play*, como definir um tamanho máximo de modelo (1 GB) e uma frequência máxima de atualização diária (oito vezes por dia).

As *áreas de trabalho* do Power BI residem nas capacidades. Representam contentores de segurança, colaboração e implementação. Cada utilizador do Power BI tem uma área de trabalho pessoal conhecida como **A Minha Área de Trabalho**. Podem ser criadas áreas de trabalho adicionais para permitir a colaboração e implementação. São conhecidas como *áreas de trabalho*. Por predefinição, as áreas de trabalho, incluindo as áreas de trabalho pessoais, são criadas na capacidade partilhada.

Veja a seguir alguns detalhes dos dois cenários de área de trabalho:

**Áreas de trabalho partilhadas**. Para áreas de trabalho normais (áreas de trabalho que não fazem parte de uma capacidade Premium), a atualização automática de páginas tem um intervalo mínimo de 30 minutos (o intervalo mais baixo permitido).

**Áreas de trabalho Premium**. A disponibilidade da atualização automática de páginas nas áreas de trabalho Premium depende das definições de carga de trabalho que o administrador Premium configurou para a capacidade Premium do Power BI. Existem duas variáveis que podem afetar a capacidade para configurar a atualização automática de páginas:

 - **Funcionalidade ativada/desativada**. Se o administrador de capacidade tiver desativado a funcionalidade, não conseguirá configurar nenhum tipo de atualização de páginas no relatório publicado.

 - **Intervalo mínimo de atualização**. Ao ativar a funcionalidade, o administrador de capacidade tem de definir um intervalo mínimo de atualização. Se o intervalo for inferior ao mínimo, o serviço Power BI definirá o intervalo para respeitar o intervalo mínimo definido pelo administrador de capacidade. Essa substituição é designada como “Definição manual do administrador de capacidade” na tabela seguinte. 

Esta tabela descreve com mais detalhes onde esta funcionalidade está disponível e os limites para cada tipo de capacidade e [modo de armazenamento](../connect-data/service-dataset-modes-understand.md):

| Modo de armazenamento | Capacidade dedicada | Capacidade partilhada |
| --- | --- | --- |
| DirectQuery | **Suportado**: Sim <br>**Intervalo mínimo de atualização**: 1 segundo <br>**Definição manual do administrador de capacidade**: Sim | **Suportado**: Sim <br>**Intervalo mínimo de atualização**: 30 minutos <br>**Definição manual do administrador de capacidade**: Não |
| Importar | **Suportado**: Não <br>**Intervalo mínimo de atualização**: N/D <br>**Definição manual do administrador de capacidade**: N/D | **Suportado**: Não <br>**Intervalo mínimo de atualização**: N/D <br>**Definição manual do administrador de capacidade**: N/D |
| Modo misto (DirectQuery + outras origens de dados) | **Suportado**: Sim <br>**Intervalo mínimo de atualização**: 1 segundo <br>**Definição manual do administrador de capacidade**: Sim | **Suportado**: Sim <br>**Intervalo mínimo de atualização**: 30 minutos <br>**Definição manual do administrador de capacidade**: Não |
| Live Connect AS | **Suportado**: Não <br>**Intervalo mínimo de atualização**: N/D <br>**Definição manual do administrador de capacidade**: N/D | **Suportado**: Não <br>**Intervalo mínimo de atualização**: N/D <br>**Definição manual do administrador de capacidade**: N/D |
| Live Connect PBI | **Suportado**: Não <br>**Intervalo mínimo de atualização**: N/D <br>**Definição manual do administrador de capacidade**: N/D | **Suportado**: Não <br>**Intervalo mínimo de atualização**: N/D <br>**Definição manual do administrador de capacidade**: N/D |

> [!NOTE]
> Ao publicar o relatório com a atualização automática de páginas ativada no Power BI Desktop para o serviço, terá de introduzir as credenciais para a origem de dados do DirectQuery no menu de definições do conjunto de dados.

## <a name="considerations-and-limitations"></a>Considerações e limitações

Existem algumas coisas a ter em conta ao utilizar a atualização automática de páginas no Power BI Desktop ou no serviço Power BI:

* Os modos de armazenamento Push, LiveConnect e Importação não são suportados pela atualização automática de páginas.  
* São suportados os modelos compostos que têm, pelo menos, uma origem de dados do DirectQuery.
* O Power BI Desktop não tem restrições para intervalos de atualização. O intervalo de atualização pode ser tão frequente como a cada segundo. Quando os relatórios são publicados no serviço Power BI, aplicam-se determinadas restrições, conforme descrito [anteriormente](#restrictions-on-refresh-intervals) neste artigo.
* A incorporação do SharePoint Online não suporta a atualização automática de páginas.

### <a name="performance-diagnostics"></a>Diagnósticos de desempenho

A atualização automática de páginas é útil para cenários de monitorização e exploração de dados em rápida mudança. No entanto, por vezes pode colocar uma carga indevida sobre a capacidade ou a origem de dados.

Para evitar uma carga indevida sobre as origens de dados, o Power BI tem as seguintes proteções:

- Todas as consultas de atualização automática de páginas são executadas com uma prioridade mais baixa para garantir que as consultas interativas (como carregamento de páginas e filtragem cruzada de elementos visuais) tenham prioridade.
- Se uma consulta não tiver sido concluída antes do próximo ciclo de atualização, o Power BI não emitirá novas consultas de atualização até que a consulta anterior seja concluída. Por exemplo, se possuir um intervalo de atualização de um segundo e as consultas demorarem uma média de quatro segundos, o Power BI só emitirá efetivamente uma consulta a cada quatro segundos.

Existem duas áreas nas quais ainda pode encontrar estrangulamentos de desempenho:

1. **Capacidade**. A consulta atinge primeiro a capacidade Premium que vai criar e avaliar a consulta DAX gerada a partir das visualizações do relatório para a origem das consultas.
2. **Origem de dados do DirectQuery**. as consultas convertidas no passo anterior são, em seguida, executadas em relação à origem. A origem seria as instâncias do SQL Server, as origens do SAP Hana e assim por diante.

Com a [aplicação Poer BI Premium Capacity Metrics](../admin/service-admin-premium-monitor-capacity.md) disponível para os administradores, pode visualizar quanta da capacidade está a ser utilizada por consultas de baixa prioridade.

As consultas de baixa prioridade consistem em consultas de atualização automática de páginas e consultas de atualização de modelos. Atualmente, não existe forma de distinguir entre a carga de atualização automática de páginas e as consultas de atualização de modelos.

Se notar que a capacidade está sobrecarregada com consultas de baixa prioridade, existem algumas ações que poderá executar:

- Pedir um SKU premium maior.
- Contactar o proprietário do relatório para diminuir o intervalo de atualização.
- No portal de administrador de capacidade, pode:
   - Desativar a atualização automática de páginas para essa capacidade.
   - Aumentar o intervalo de atualização mínimo, o que vai afetar todos os relatórios dessa capacidade.


### <a name="frequently-asked-questions"></a>Perguntas frequentes

**Sou autor de relatórios. Defini o intervalo de atualização do relatório para um segundo no Power BI Desktop, mas após a publicação, o relatório não está a ser atualizado no serviço.**

* Confirme se a atualização automática de páginas está ativada para a página. Dado que esta definição é por página, tem de garantir que está ativada para cada página no relatório que quer que seja atualizado.
* Verifique se carregou para uma área de trabalho com uma capacidade Premium anexada. Se não o fez, o intervalo de atualização será bloqueado nos 30 minutos.
* Se o relatório se encontrar numa área de trabalho Premium, pergunte ao administrador se esta funcionalidade está ativada para a capacidade anexada. Confirme também se o intervalo mínimo de atualização para a capacidade é inferior ou igual ao intervalo do relatório.

**Sou administrador de capacidade. Alterei as definições do intervalo de atualização automática de páginas, mas as alterações não estão refletidas. Por outras palavras, os relatórios ainda estão a ser atualizados a uma taxa que não deveriam ou não estão a ser atualizados apesar de ter ativado a atualização automática de páginas.**

* As alterações à definição de atualização automática de páginas feitas na IU do administrador de capacidade demoram até 5 minutos a serem propagadas nos relatórios.
* Além de ativar a atualização automática de páginas para a capacidade, também tem de ativá-la para as páginas de um relatório em que queira ativá-la.

**O meu relatório está a funcionar no modo misto (modo misto significa que o relatório tem uma ligação do DirectQuery e uma origem de dados de Importação). Alguns elementos visuais não estão a ser atualizados.**

- Se os elementos visuais fizerem referência a tabelas de Importação, este comportamento será normal. A atualização automática de páginas não é suportada para Importação.
- Veja a primeira pergunta nesta secção.

**O meu relatório estava a atualizar sem problemas no serviço, mas subitamente parou.**

* Experimente atualizar a página para ver se o problema se resolveu sozinho.
* Verifique junto do administrador de capacidade. O administrador pode ter desativado a funcionalidade ou aumentado o intervalo mínimo de atualização (veja a segunda pergunta nesta secção).

**Sou autor de relatórios. Os meus elementos visuais não estão a ser atualizados na cadência que especifiquei. Estão a ser atualizados a uma taxa mais lenta.**

* Se as consultas estiverem a demorar demasiado a ser executadas, o intervalo de atualização será atrasado. A atualização automática de páginas espera que todas as consultas sejam concluídas antes de executar novas consultas.
* O administrador de capacidade pode ter definido um intervalo de atualização mínimo superior ao que tinha definido no relatório. Peça ao administrador de capacidade para reduzir o intervalo mínimo de atualização.

**As consultas de atualização automática de páginas são servidas a partir da cache?**

* Não. Todas as consultas de atualização automática de páginas ignoram os dados armazenados em cache.


## <a name="next-steps"></a>Próximos passos

Para obter mais informações, veja estes artigos:

* [Utilizar o DirectQuery no Power BI](../connect-data/desktop-directquery-about.md)
* [Utilizar modelos compostos no Power BI Desktop](../transform-model/desktop-composite-models.md)
* [Utilizar o Analisador de Desempenho para examinar o desempenho do elemento de relatório](desktop-performance-analyzer.md)
* [Implementar e gerir capacidades Premium do Power BI](../guidance/whitepaper-powerbi-premium-deployment.md)
* [Origens de dados no Power BI Desktop](../connect-data/desktop-data-sources.md)
* [Formatar e combinar dados no Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md)
* [Ligar a livros do Excel no Power BI Desktop](../connect-data/desktop-connect-excel.md)   
* [Introduzir dados diretamente no Power BI Desktop](../connect-data/desktop-enter-data-directly-into-desktop.md)   
