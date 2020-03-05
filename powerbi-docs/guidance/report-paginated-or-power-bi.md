---
title: Quando utilizar os relatórios paginados no Power BI
description: Orientações para quando utilizar os relatórios paginados do Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/04/2020
ms.author: v-pemyer
ms.openlocfilehash: 3838c0b487be7faace2e58dd706aa7d172841215
ms.sourcegitcommit: b59ec11a4a0a3d5be2e4d91548d637d31b3491f8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78290504"
---
# <a name="when-to-use-paginated-reports-in-power-bi"></a>Quando utilizar os relatórios paginados no Power BI

O presente artigo destina-se a si, na qualidade de criador de relatórios para o Power BI. Fornece sugestões para ajudá-lo a escolher quando criar os [relatórios paginados do Power BI](../paginated-reports-report-builder-power-bi.md).

> [!NOTE]
> Para publicar os relatórios paginados do Power BI, é necessária uma subscrição do Power BI Premium. Os relatórios vão ser compostos somente quando estiverem numa área de trabalho numa capacidade dedicada que tenha [a carga de trabalho Relatórios Paginados ativada](../service-admin-premium-workloads.md#paginated-reports).

Os relatórios paginados do Power BI são otimizados para **impressão**ou **geração de PDFs**. Também lhe proporcionam a capacidade de produzir esquemas altamente formatados e com um aspeto perfeito. Portanto, os relatórios paginados são ideais para relatórios operacionais, como faturas de vendas.

Em contrapartida, os relatórios do Power BI estão otimizados para a **exploração e a interatividade**. Além disso, podem apresentar os seus dados através de uma gama abrangente de elementos visuais ultramodernos. Assim, os relatórios do Power BI são ideais para relatórios analíticos, pois permitem que os utilizadores dos seus relatórios explorem os dados e descubram relações e padrões.

Recomendamos que pondere utilizar um relatório paginado do Power BI quando:

- Sabe que o relatório tem de ser impresso ou emitido como um documento PDF.
- Os esquemas da grelha de dados podem expandir-se e exceder a capacidade. Num relatório do Power BI, considere que uma tabela ou matriz não pode ser redimensionada dinamicamente para apresentar todos os dados e, em vez disso, irá fornecer barras de deslocamento. No entanto, se for impresso, não será possível deslocar-se para revelar quaisquer dados que não estejam visíveis.
- As funcionalidades e capacidades paginadas do Power BI funcionam a seu favor. Muitos desses cenários de relatórios são descritos mais adiante neste artigo.

## <a name="legacy-reports"></a>Relatórios antigos

Quando já tiver os relatórios [Report Definition Language (RDL)](/sql/reporting-services/reports/report-definition-language-ssrs) do SQL Server Reporting Services (SSRS), pode optar por voltar a criá-los como [relatórios do Power BI](../consumer/end-user-reports.md) ou migrá-los como relatórios paginados para o Power BI. Para obter mais informações, veja [Migrar os relatórios do SQL Server Reporting Services para o Power BI](migrate-ssrs-reports-to-power-bi.md).

Uma vez publicados numa área de trabalho do Power BI, os relatórios paginados estão disponíveis lado a lado com os relatórios do Power BI. Posteriormente, estes podem ser facilmente distribuídos através das [aplicações do Power BI](../service-create-distribute-apps.md).

Poderá ponderar voltar a criar os relatórios SSRS, em vez de os migrar. Isto aplica-se sobretudo aos relatórios que se destinam a fornecer experiências analíticas. Nesses casos, os relatórios do Power BI vão provavelmente fornecer melhores experiências para os utilizadores de relatórios.

## <a name="paginated-report-scenarios"></a>Cenários de relatórios paginados

Quando é preferível criar um relatório paginado do Power BI, há muitos cenários apelativos. Muitos destes cenários são funcionalidades ou capacidades não suportadas pelos relatórios do Power BI.

- **Pronto para impressão**: os relatórios paginados são otimizados para impressão ou geração de PDFs. Quando necessário, as regiões de dados podem expandir e sobrecarregar para várias páginas de forma controlada. Os esquemas de relatório podem definir margens, cabeçalhos e rodapés de página.
- **Formatos de composição**: o Power BI pode compor relatórios paginados em formatos diferentes. Os formatos incluem Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, CSV, XML e MHTML (o formato MHTML é utilizado pelo serviço Power BI para compor relatórios). Os utilizadores de relatórios podem decidir exportar no formato que preferirem.
- **Esquema preciso**: pode criar esquemas com um aspeto perfeito e altamente formatados com o tamanho exato e a localização configurada em frações de polegadas ou centímetros.
- **Esquema dinâmico**: pode produzir esquemas altamente reativos ao definir muitas propriedades de relatório para utilizar expressões VB.NET. As expressões têm acesso a muitas bibliotecas do .NET Framework importantes.
- **Esquema de composição específica**: pode utilizar expressões para modificar o esquema de relatório com base no formato de composição aplicado. Por exemplo, pode criar o relatório para desativar a alternância de visibilidade (de modo a desagregar e a agregar) quando este é composto através de um formato não interativo, como PDF.
- **Consultas nativas**: não é preciso criar previamente um conjunto de dados do Power BI. É possível criar consultas nativas (ou utilizar procedimentos armazenados) para qualquer [origem de dados suportada](../paginated-reports-data-sources.md). As consultas podem incluir parametrização.
- **Designers de consultas gráficas**: o Power BI Report Builder inclui designers de consultas gráficas para ajudá-lo a escrever e a testar as consultas de conjuntos de dados.
- **Conjuntos de dados estáticos**: pode definir um conjunto de dados e introduzir dados diretamente na definição do relatório. Esta funcionalidade é, sobretudo, útil para suportar uma demonstração ou para fornecer uma prova de conceito (POC).
- **Integração de dados**: pode combinar dados de diferentes origens de dados ou com conjuntos de dados estáticos. Isto é conseguido através da criação de campos personalizados com expressões VB.NET.
- **Parametrização**: pode criar experiências de parametrização altamente personalizadas, incluindo parâmetros de dados e em cascata. Também é possível definir as predefinições dos parâmetros. Estas experiências podem ser criadas para ajudar os utilizadores do relatório a definir rapidamente filtros apropriados. Além disso, os parâmetros não precisam de filtrar os dados do relatório. Podem ser utilizados para suportar cenários "hipotéticos", ou estilo ou filtragem dinâmica.
- **Dados de imagens**: o seu relatório pode compor imagens quando estas estão armazenadas no formato binário numa origem de dados.
- **Código personalizado**: pode criar blocos de código das funções VB.NET no relatório e utilizá-las em qualquer expressão do relatório.
- **Sub-relatórios**: pode incorporar outros relatórios paginados do Power BI (da mesma área de trabalho) no seu relatório.
- **Grelhas de dados flexíveis**: tem controlo detalhado dos esquemas de grelha ao utilizar a região de dados tablix. Também suporta esquemas complexos, incluindo grupos adjacentes e aninhados. Pode ser configurado para repetir cabeçalhos ao ser impresso em várias páginas. Além disso, pode incorporar um sub-relatório ou outras visualizações, incluindo barras de dados, gráficos sparkline e indicadores.
- **Tipos de dados espaciais**: a região de dados do mapa pode visualizar os [tipos de dados espaciais do SQL Server](/sql/relational-databases/spatial/spatial-data-sql-server). Portanto, os tipos de dados GEOGRAPHY (Geografia) e GEOMETRY (Geometria) podem ser utilizados para visualizar pontos, linhas ou polígonos. Também é possível visualizar polígonos definidos em ficheiros de formas ESRI.
- **Medidores modernos**: os medidores radiais e lineares podem ser utilizados para apresentar os valores e o estado de KPI. Estes até podem ser incorporados em regiões de dados da grelha e repetir dentro dos grupos.
- **Composição de HTML**: pode apresentar texto com formatação avançada quando este estiver armazenado como HTML.
- **Impressão em série**: pode utilizar marcadores de posição de caixa de texto para inserir valores de dados no texto. Desta forma, pode produzir um relatório de impressão em série.
- **Funcionalidades de interatividade**: as funcionalidades interativas incluem a alternância de visibilidade (de modo a desagregar e a agregar), ligações, ordenação interativa e descrições. Também pode adicionar ligações que efetuem uma pormenorização para relatórios do Power BI ou outros relatórios paginados do Power BI. As ligações podem, inclusive, avançar para outra localização dentro do mesmo relatório.
- **Subscrições**: o Power BI pode apresentar relatórios paginados numa agenda como e-mails, com anexos de relatórios em qualquer formato suportado.
- **Esquemas por utilizador**: pode criar esquemas de relatórios reativos com base no utilizador autenticado que abrir o relatório. Pode fazer com que o relatório filtre dados de forma diferente, oculte regiões de dados ou visualizações, aplique formatos diferentes ou defina predefinições de parâmetros específicos do utilizador.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações relacionadas com este artigo, consulte os seguintes recursos:

- [O que são relatórios paginados no Power BI Premium?](../paginated-reports-report-builder-power-bi.md)
- [Migrar os relatórios do SQL Server Reporting Services para o Power BI](migrate-ssrs-reports-to-power-bi.md)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)
