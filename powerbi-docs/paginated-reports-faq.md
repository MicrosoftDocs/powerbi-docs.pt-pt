---
title: 'Relatórios paginados no Power BI: FAQ (Pré-Visualização)'
description: Este artigo responde às perguntas mais frequentes sobre os relatórios paginados. Estes relatórios são uma saída de imagem perfeita, altamente formatada e otimizada para impressão ou geração de PDFs.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: report-builder
ms.topic: overview
ms.date: 11/05/2018
ms.author: maggies
ms.openlocfilehash: d3fdf9b568aa13ba5a8437c684835e0fce803d19
ms.sourcegitcommit: bb4cf3469b44e451153c469725a9069dcd548809
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/20/2018
ms.locfileid: "53649451"
---
# <a name="paginated-reports-in-power-bi-faq-preview"></a>Relatórios paginados no Power BI: FAQ (Pré-Visualização)

Este artigo responde às perguntas mais frequentes sobre os relatórios paginados. Estes relatórios são uma saída de imagem perfeita, altamente formatada e otimizada para impressão ou geração de PDFs. Os relatórios são designados “paginados” porque são formatados para se ajustarem a várias páginas. Os relatórios paginados baseiam-se na tecnologia de relatório RDL do SQL Server Reporting Services. 

Este artigo responde a perguntas muito comuns que as pessoas têm sobre os relatórios paginados no Power BI Premium e sobre o Report Builder, a ferramenta autónoma para a criação de relatórios paginados. Precisa de uma licença do Power BI Pro para publicar um relatório no serviço. Pode publicar e partilhar relatórios paginados em A Minha Área de Trabalho ou nas áreas de trabalho da aplicação, desde que a área de trabalho esteja numa capacidade do Power BI Premium. 

## <a name="administration"></a>Administração

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>Preciso de que tamanho de capacidade Premium para os relatórios paginados?

A carga de trabalho dos relatórios paginados está disponível nos SKUs P1-P3 para pré-visualização pública.  Também pode utilizá-la para cenários de teste/desenvolvimento com os SKUs A4-A6.

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>Qual é o limiar máximo de memória que posso definir para os relatórios paginados na minha capacidade?

Atualmente, pode reservar apenas 50% da memória para esta carga de trabalho. 

### <a name="how-does-user-access-work-for-paginated-reports"></a>Como funciona o acesso de utilizador para os relatórios paginados?

O acesso de utilizador para os relatórios paginados é o mesmo que o acesso de utilizador para todos os outros conteúdos no serviço Power BI 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>Como ativar/desativar a minha carga de trabalho dos relatórios paginados?

O administrador de capacidade pode ativar ou desativar a carga de trabalho dos relatórios paginados na página do portal do administrador de capacidade.  

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

Sim. Não pode carregar relatórios para a área de trabalho sem uma licença Pro. Pode transferir e experimentar o Report Builder sem a licença Pro, mas não pode publicar os relatórios paginados que criar. 

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

### <a name="the-documentation-says-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>A documentação indica que Report Builder é a ferramenta de criação preferencial. Posso criar relatórios paginados no SQL Server Data Tools para o Power BI?

Sim, mas o serviço Power BI permite-lhe apenas carregar um único item de cada vez, assim, muitos dos cenários que os autores utilizam com o SQL Server Data Tools (SSDT) não são ainda suportados. Veja a [lista completa de funcionalidades não suportadas](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi), disponível mais adiante nestas perguntas frequentes.  

### <a name="what-versions-of-report-builder-do-you-support"></a>Quais são as versões do Report Builder suportadas?

Utilize a versão mais recente do SQL Server 2016 Report Builder para criar e publicar os relatórios no serviço Power BI. Instale o [Report Builder a partir do Centro de Transferências da Microsoft](https://www.microsoft.com/download/details.aspx?id=53613).

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>Como faço para mover os relatórios existentes, que guardei no SQL Server Reporting Services, para o Power BI?

Terá de transferir os relatórios do servidor e, em seguida, carregá-los no Power BI através do portal.  Não existe nenhuma ferramenta de migração disponível neste momento, mas estamos a considerar criar uma depois de termos concluído a pré-visualização pública e obtido o nível certo de paridade de funcionalidades entre os produtos.

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>Posso abrir relatórios e publicar diretamente no serviço?

Neste momento, não. Vamos adicionar suporte para abrir relatórios e publicá-los diretamente no serviço do Report Builder no futuro, tal como pode fazer com o Power BI Desktop.

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>Quais as funcionalidades dos relatórios paginados no SSRS que não são ainda suportadas no Power BI?

Atualmente, os relatórios paginados não suportam os seguintes itens:

- Origens de dados partilhadas
- Conjuntos de dados partilhados
- Sub-relatórios
- Ações por clique e de pormenorização
- Relatórios ligados
- Marcadores
- Camadas de mapa Bing
- Tipos de letra personalizados

Receberá uma mensagem de erro se tentar carregar um ficheiro que tem uma funcionalidade não suportada no serviço Power BI, além da alternância/ordenação.

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>Quais as origens de dados que são suportadas atualmente para os relatórios paginados?

Existe suporte para a Base de Dados SQL do Azure, para o SQL Server e para os modelos em tabela (DAX) e multidimensional (MDX) do SQL Server Analysis Services (SSAS) que utilizam o Gateway no local.

Ao aceder ao SSAS através do Gateway, o utilizador cujas credenciais estão armazenadas precisa de permissões elevadas no SSAS para trabalhar através do Gateway.

### <a name="what-authentication-methods-do-you-support"></a>Quais os métodos de autenticação suportados?

Atualmente, precisa de armazenar um nome de utilizador e uma palavra-passe com a origem de dados no portal ou no gateway.  Outros métodos de autenticação para dar suporte a aspetos como a segurança ao nível da linha estão previstos para uma data posterior na pré-visualização.

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>Posso utilizar um conjunto de dados do Power BI como uma origem de dados para o meu relatório paginado?

Ainda não, mas este suporte está planeado para breve.

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>Posso utilizar os procedimentos armazenados através do Gateway?

Pode utilizar um procedimento armazenado através do Gateway, mas poderá deparar-se com problemas em determinados cenários, caso o procedimento armazenado tenha parâmetros.

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>Que formatos de exportação estão disponíveis para o meu relatório no serviço Power BI?

Pode exportar para o Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, .CSV, XML e MHTML.

### <a name="can-i-print-paginated-reports"></a>Posso imprimir relatórios paginados?

Sim, a impressão está disponível para Relatórios Paginados, incluindo uma nova e melhorada experiência de pré-visualização. 

### <a name="are-e-mail-subscriptions-available-yet-for-paginated-reports"></a>As subscrições por e-mail já estão disponíveis para os relatórios paginados?

Não, as subscrições por e-mail estarão disponíveis brevemente.

### <a name="what-features-from-ssrs-will-you-be-supporting-in-the-power-bi-service"></a>Quais as funcionalidades do SSRS que terão suporte no serviço Power BI?

O nosso plano é fornecer a paridade de funcionalidades para a maioria dos cenários. No entanto, poderá não fazer sentido alterar determinadas funcionalidades do SSRS e do Power BI para se ajustar aos padrões do SSRS existentes.  Por exemplo, os vários modelos de permissão do Power BI não podem ser mapeados novamente ao SSRS.  Estaremos atentos ao feedback dos clientes e parceiros para tomar estes tipos de decisões.

### <a name="can-i-run-custom-code-in-my-report"></a>Posso executar código personalizado no meu relatório?

Sim, suportamos a capacidade de executar código nos seus relatórios, tal como no SSRS.

### <a name="does-this-mean-ssrs-is-going-away"></a>Este suporte significa que o SSRS está a acabar?

De modo algum.  Esta nova oferta disponibiliza aos clientes uma opção com base na cloud para os relatórios paginados.  

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>Posso utilizar o Power BI incorporado para incorporar os meus relatórios paginados numa aplicação que estou a alojar?

Planeamos suportar este cenário com as APIs existentes do Power BI, mas não temos ainda uma calendarização para quando este cenário estará disponível.

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>Posso pormenorizar de um relatório do Power BI para um relatório paginado?

Ainda não, mas planeamos suportar este cenário.

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>Posso partilhar o meu conteúdo de relatório paginado através de uma aplicação do Power BI?

Atualmente, pode partilhar relatórios paginados individuais com outros utilizadores através da ação de partilha no portal ou da barra de ferramentas. Não suportamos ainda a partilha numa aplicação, mas está prevista para breve. 

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-to-report-tiles-to-dashboards-work-with-paginated-reports"></a>As outras funcionalidades específicas do relatório do Power BI, como afixar mosaicos de relatório em dashboards, funcionarão com os relatórios paginados?

Planeamos que os relatórios suportem os mesmos cenários principais no serviço tanto quanto possível.  O ideal é que, embora a ferramenta de criação dos relatórios seja diferente, da perspetiva do consumidor seja apenas outro relatório na lista no portal. Eles não se importam como foram criados, desde que façam o que é preciso.  Um bom exemplo desta funcionalidade de paridade é o suporte planeado dos comentários. Embora a própria funcionalidade possa funcionar de forma ligeiramente diferente em cada tipo de relatório, poderá utilizar os comentários em ambos.

### <a name="are-you-planning-to-create-a-new-authoring-tool-for-paginated-reports-in-the-power-bi-service--we-cant-do-everything-we-need-to-with-report-builder-today"></a>Estão a planear criar uma nova ferramenta de criação para os relatórios paginados no serviço Power BI?  Não podemos fazer tudo o que precisamos com o Report Builder hoje.

Ainda estamos a considerar diferentes opções para obtermos a melhor versão da ferramenta de relatórios paginados no Power BI. 

### <a name="is-a-migration-tool-planned-so-ssrs-customers-can-move-their-existing-reports-and-assets-to-power-bi"></a>Está planeada uma ferramenta de migração para que os clientes do SSRS possam mover os relatórios existentes e os recursos para o Power BI?

Estamos a avaliar as opções para permitir que os conteúdos sejam movidos para o Power BI de forma automatizada, mas esta funcionalidade só estará disponível após a Disponibilidade Geral.

### <a name="will-i-ever-be-able-to-create-both-paginated-reports-and-power-bi-reports-in-a-single-authoring-tool"></a>Serei alguma vez capaz de criar relatórios paginados e relatórios do Power BI numa única ferramenta de criação?

Poderá vir a ser possível.  Atualmente, estamos a analisar as formas de permitir este cenário e a determinar se apenas distribuiremos as ferramentas de criação como um único conjunto do Power BI ou se teremos transferências/aplicações de imagens corporativas individuais.

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>Existe um controlo de visualizador de relatório para relatórios paginados no serviço Power BI?

Não, atualmente, não está disponível um controlo de visualizador de relatório.

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>Pode-se procurar os relatórios paginados na nova experiência Raiz no serviço Power BI?

Não, atualmente não pode procurar os relatórios paginados na Raiz.  No entanto, pode vê-los noutras partes da nova experiência Raiz.

## <a name="next-steps"></a>Próximos passos

- [Instalar o Report Builder a partir do Centro de Transferências da Microsoft](https://www.microsoft.com/download/details.aspx?id=53613)
- [Tutorial: Criar um relatório paginado](paginated-reports-quickstart-aw.md)
