---
title: 'Relatórios paginados no Power BI: PERGUNTAS FREQUENTES'
description: Este artigo responde às perguntas mais frequentes sobre os relatórios paginados. Estes relatórios são uma saída de imagem perfeita, altamente formatada e otimizada para impressão ou geração de PDFs.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 12/03/2019
ms.openlocfilehash: c1f8a274a17d85cf8f86d2e33ff63f3e9b686742
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/06/2020
ms.locfileid: "74831216"
---
# <a name="paginated-reports-in-power-bi-faq"></a>Relatórios paginados no Power BI: PERGUNTAS FREQUENTES 

Este artigo responde às perguntas mais frequentes sobre os relatórios paginados. Estes relatórios são uma saída de imagem perfeita, altamente formatada e otimizada para impressão ou geração de PDFs. Os relatórios são designados “paginados” porque são formatados para se ajustarem a várias páginas. Os relatórios paginados baseiam-se na tecnologia de relatório RDL do SQL Server Reporting Services. 

Este artigo responde a perguntas muito comuns que as pessoas têm sobre os relatórios paginados no Power BI Premium e sobre o Report Builder, a ferramenta autónoma para a criação de relatórios paginados. Precisa de uma licença do Power BI Pro para publicar um relatório no serviço. Pode publicar e partilhar relatórios paginados em A Minha Área de Trabalho ou em áreas de trabalho, desde que a área de trabalho esteja numa capacidade do Power BI Premium. 

## <a name="administration"></a>Administração

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>Preciso de que tamanho de capacidade Premium para os relatórios paginados?

A carga de trabalho dos relatórios paginados está disponível nas SKUs P1 – P3.  Poderá também utilizar os SKUs A4 – A6 para cenários incorporados ou de teste/desenvolvimento.

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>Qual é o limiar máximo de memória que posso definir para os relatórios paginados na minha capacidade?

Pode utilizar até 100% da memória nesta carga de trabalho.

### <a name="how-does-user-access-work-for-paginated-reports"></a>Como funciona o acesso de utilizador para os relatórios paginados?

O acesso de utilizador para os relatórios paginados é o mesmo que o acesso de utilizador para todos os outros conteúdos no serviço Power BI 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>Como ativar/desativar a minha carga de trabalho dos relatórios paginados?

O administrador de capacidade pode ativar ou desativar a carga de trabalho dos relatórios paginados na página do portal do administrador de capacidade.  Por predefinição, a carga de trabalho estará disponível para qualquer nova capacidade que criar.  

### <a name="how-can-i-monitor-usage-of-paginated-reports-in-my-tenant"></a>Como posso monitorizar a utilização dos relatórios paginados no meu inquilino?

Os registos de auditoria do Office 365 detalham a utilização deste tipo de relatório nos eventos seguintes: 

- Visualizar Relatório do Power BI
- Eliminar relatório do Power BI
- Criar relatório do Power BI
- Relatório do Power BI transferido

O campo ReportType tem o valor “PaginatedReport” para identificar os relatórios paginados por oposição aos relatórios do Power BI.

Além disso, os registos de auditoria fornecem os seguintes eventos para os relatórios paginados:

- Conjunto de dados do Power BI vinculado ao gateway
- Detetar origem de dados do Power BI
- TakeOverDatasource

### <a name="can-i-monitor-this-workload-through-the-premium-capacity-monitoring-app"></a>Posso monitorizar esta carga de trabalho através da Aplicação de Monitorização da Capacidade Premium?

Sim, a monitorização está disponível como um novo separador com os mesmos detalhes relevantes dos seus conjuntos de dados do Power BI.

### <a name="do-i-need-a-pro-license-to-create-and-publish-paginated-reports"></a>Preciso de uma licença Pro para criar e publicar relatórios paginados?

Pode carregar relatórios paginados para A Minha Área de Trabalho sem uma licença Pro, desde que pertença a uma Capacidade Premium.  Noutras áreas de trabalho, tem de ter uma licença Pro para criar e publicar conteúdo nas mesmas. Incentivamo-lo a transferir e a utilizar o Report Builder do Power BI mesmo sem a licença Pro, mas não pode publicar os relatórios paginados que criar sem esta ferramenta. 

### <a name="what-if-i-have-a-paginated-report-in-a-workspace-and-the-paginated-report-workload-is-turned-off"></a>E se eu tiver um relatório paginado numa área de trabalho e a carga de trabalho do relatório paginado estiver desativada?

Recebe uma mensagem de erro e não poderá visualizar o relatório até que a carga de trabalho seja novamente ativada. Pode ainda eliminar o relatório da área de trabalho.

### <a name="what-is-the-default-memory-for-each-of-the-premium-skus-supported-for-paginated-reports"></a>Qual é a memória predefinida para cada um dos SKUs Premium suportados para os relatórios paginados?

Memória predefinida em cada SKU Premium para os relatórios paginados:

- **P1/A4**: 20% predefinido; 10% mínimo
- **P2/A5**: 20% predefinido; 5% mínimo
- **P3/A6**: 20% predefinido; 2,5% mínimo

## <a name="general"></a>Geral

### <a name="when-should-i-use-a-paginated-report-vs-a-power-bi-report"></a>Quando devo utilizar um relatório paginado em vez de um relatório do Power BI?

Os relatórios paginados são melhores para os cenários que exigem uma saída de imagem perfeita, altamente formatada e otimizada para impressão ou geração de PDFs.  Uma demonstração de resultados é um bom exemplo do tipo de relatório que provavelmente desejaria criar como relatório paginado.  

Os relatórios do Power BI estão otimizados para a exploração e a interatividade.  Os relatórios do Power BI constituiriam uma melhor solução no caso dos relatórios de vendas em que os diferentes vendedores pretendem segmentar os dados no mesmo relatório pela sua região/indústria/cliente específicos e ver como os números se alteram.

### <a name="the-documentation-says-power-bi-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>A documentação indica que o Report Builder do Power BI é a ferramenta de criação preferencial. Posso criar relatórios paginados no SQL Server Data Tools para o Power BI?

Sim, mas o serviço Power BI permite-lhe apenas carregar um único item de cada vez, assim, muitos dos cenários que os autores utilizam com o SQL Server Data Tools (SSDT) não são ainda suportados. Veja a [lista completa de funcionalidades não suportadas](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi), disponível mais adiante nestas perguntas frequentes.  

### <a name="what-versions-of-report-builder-do-you-support"></a>Quais são as versões do Report Builder suportadas?

Lançámos recentemente o Report Builder do Power BI como a principal ferramenta de criação dos relatórios paginados no serviço Power BI. Instale o [Report Builder do Power BI a partir do Centro de Transferências da Microsoft](https://go.microsoft.com/fwlink/?linkid=2086513).

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>Como faço para mover os relatórios existentes, que guardei no SQL Server Reporting Services, para o Power BI?

Terá de transferir os relatórios do servidor e, em seguida, carregá-los no Power BI através do portal.  Não existe nenhuma ferramenta de migração disponível neste momento, mas estamos a considerar criar uma depois de termos concluído a pré-visualização pública e obtido o nível certo de paridade de funcionalidades entre os produtos.

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>Posso abrir relatórios e publicar diretamente no serviço?

Yes. Adicionámos recentemente suporte para abrir relatórios e publicá-los diretamente no serviço a partir do Report Builder do Power BI.

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>Quais as funcionalidades dos relatórios paginados no SSRS que não são ainda suportadas no Power BI?

Atualmente, os relatórios paginados não suportam os seguintes itens:

- Origens de dados partilhadas
- Conjuntos de dados partilhados
- Sub-relatórios
- Pormenorização e click-through para outros relatórios
- Relatórios ligados
- Camadas de mapa Bing
- Tipos de letra personalizados

Receberá uma mensagem de erro se tentar carregar um ficheiro que tem uma funcionalidade não suportada no serviço Power BI, além da alternância/ordenação.

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>Quais as origens de dados que são suportadas atualmente para os relatórios paginados?

Veja o artigo [Origens de dados suportadas para relatórios paginados do Power BI](paginated-reports-data-sources.md) para obter uma lista de origens de dados. 

### <a name="what-authentication-methods-do-you-support"></a>Quais os métodos de autenticação suportados?

Suportamos o SSO para o Azure Analysis Services, a Base de Dados SQL do Azure e origens de dados do Power BI.  Também suportamos o OAuth para a Base de Dados SQL do Azure e o Azure Analysis Services.  Noutras origens de dados, tem de armazenar um nome de utilizador e uma palavra-passe com a origem de dados no portal ou no gateway.  

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>Posso utilizar um conjunto de dados do Power BI como uma origem de dados para o meu relatório paginado?

Sim, suportamos os conjuntos de dados do Power BI como origens de dados para os relatórios paginados.

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>Posso utilizar os procedimentos armazenados através do Gateway?

Pode utilizar um procedimento armazenado através do Gateway, mas poderá deparar-se com problemas em determinados cenários, caso o procedimento armazenado tenha parâmetros.

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>Que formatos de exportação estão disponíveis para o meu relatório no serviço Power BI?

Pode exportar para o Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, .CSV, XML e MHTML.

### <a name="can-i-print-paginated-reports"></a>Posso imprimir relatórios paginados?

Sim, a impressão está disponível para os relatórios paginados, incluindo uma experiência de pré-visualização nova e melhorada. 

### <a name="are-e-mail-subscriptions-available-for-paginated-reports"></a>As subscrições por e-mail estão disponíveis para os relatórios paginados?

Sim, as subscrições por e-mail são totalmente suportadas para relatórios paginados e incluem o suporte para seis formatos de ficheiro e valores de parâmetros diferentes.

### <a name="can-i-run-custom-code-in-my-report"></a>Posso executar código personalizado no meu relatório?

Sim, suportamos a capacidade de executar código nos seus relatórios, tal como no SSRS.

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>Posso utilizar o Power BI incorporado para incorporar os meus relatórios paginados numa aplicação que estou a alojar?

A incorporação SaaS, incluindo o suporte para a Incorporação Segura, já está disponível.  O suporte para a incorporação PaaS está previsto para ainda este ano.

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>Posso pormenorizar de um relatório do Power BI para um relatório paginado?

Sim, esta ação pode ser conseguida utilizando parâmetros de URL com os seus relatórios paginados.

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>Posso partilhar o meu conteúdo de relatório paginado através de uma aplicação do Power BI?

Sim, os relatórios paginados são suportados para serem implantados com aplicações das áreas de trabalho v1 e v2. 

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-to-report-tiles-to-dashboards-work-with-paginated-reports"></a>As outras funcionalidades específicas do relatório do Power BI, como afixar mosaicos de relatório em dashboards, funcionarão com os relatórios paginados?

Planeamos que os relatórios suportem os mesmos cenários principais no serviço tanto quanto possível.  O ideal é que, embora a ferramenta de criação dos relatórios seja diferente, da perspetiva do consumidor seja apenas outro relatório na lista no portal. Eles não se importam como foram criados, desde que façam o que é preciso.  Um bom exemplo desta funcionalidade de paridade é o suporte planeado dos comentários. Embora a própria funcionalidade possa funcionar de forma ligeiramente diferente em cada tipo de relatório, poderá utilizar os comentários em ambos.

### <a name="is-a-migration-tool-planned-so-ssrs-customers-can-move-their-existing-reports-and-assets-to-power-bi"></a>Está planeada uma ferramenta de migração para que os clientes do SSRS possam mover os relatórios existentes e os recursos para o Power BI?

Um projeto no GitHub suporta agora a migração de conteúdos do SQL Server Reporting Services para o Power BI.  Veja os detalhes e transfira a ferramenta aqui: [https://github.com/microsoft/RdlMigration](https://github.com/microsoft/RdlMigration).

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>Existe um controlo de visualizador de relatório para relatórios paginados no serviço Power BI?

Não, atualmente, não está disponível um controlo de visualizador de relatório.

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>Pode-se procurar os relatórios paginados na nova experiência Raiz no serviço Power BI?

Sim, atualmente não pode procurar os relatórios paginados na Home Page.  Mas poderá vê-los noutras partes da nova experiência da Home Page.

## <a name="next-steps"></a>Próximos passos

- [Instalar o Report Builder do Power BI a partir do Centro de Transferências da Microsoft](https://go.microsoft.com/fwlink/?linkid=2086513)
- [Tutorial: Criar um relatório paginado](paginated-reports-quickstart-aw.md)
