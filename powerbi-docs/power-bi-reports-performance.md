---
title: Melhores práticas para o desempenho do Power BI
description: Este artigo fornece orientação para construir relatórios rápidos e fiáveis no Power BI
author: Bhavik-MSFT
ms.author: bhmerc
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/30/2018
LocalizationGroup: Reports
ms.openlocfilehash: 736c1ee1b1998ec7f991167352313a05061b3f3c
ms.sourcegitcommit: 226b47f64e6749061cd54bf8d4436f7deaed7691
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2019
ms.locfileid: "70841496"
---
# <a name="power-bi-performance-best-practices"></a>Melhores práticas para o desempenho do Power BI

Este artigo oferece orientação para construir relatórios rápidos e fiáveis no Power BI.  

## <a name="choose-an-appropriate-storage-mode-import-directquery"></a>Escolha um modo de armazenamento apropriado: Import, DirectQuery

Na maioria dos casos, o modo de importação é a melhor opção, pois oferece a maior velocidade ao aproveitar os dados em cache na memória armazenados localmente que são compactados com o armazenamento em colunas. O modo de importação também permite utilizar a funcionalidade DAX completa. Considere o DirectQuery (e os Modelos compostos) quando o volume de dados de origem for demasiado grande para se ajustar à capacidade do Power BI. O DirectQuery também é útil quando precisa de obter na origem os dados mais recentes de cada vez que carrega um relatório. Se não tiver estes requisitos e os utilizadores precisarem de ver apenas os dados que são atualizados algumas vezes por dia ou menos (por exemplo, de um armazém de dados empresarial), recomenda-se vivamente a Importação. No modo DirectQuery, os utilizadores podem tentar atualizar o relatório sem perceberem que estão a obter exatamente os mesmos dados da origem.      

## <a name="use-filters-to-limit-report-visuals-to-display-only-whats-needed"></a>Utilizar filtros para que os elementos visuais de relatório apresentem apenas o necessário 

Quanto maior for o volume de dados que um elemento visual tem de apresentar, mais lento será o carregamento. Embora este princípio pareça óbvio, pode ser fácil esquecê-lo. Por exemplo, digamos que tem um conjunto de dados grande. Além do conjunto de dados, pode criar um relatório com uma tabela. Os utilizadores finais podem utilizar as segmentações na página para aceder às linhas que pretendem. Normalmente, só estão interessados em algumas dezenas de linhas.

Um erro comum é deixar a vista predefinida da tabela não filtrada, ou seja, com mais de 100 milhões de linhas. Os dados destas linhas são carregados para a memória e descomprimidos a cada atualização. Esse processamento cria enormes carregamentos de memória. A solução é utilizar o filtro "Top N" para reduzir o número máximo de itens apresentados na tabela. Pode definir um número máximo de itens muito superior ao que os utilizadores necessitam, por exemplo 10 000. Como resultado, a experiência do utilizador final não é alterada, mas a utilização da memória baixa consideravelmente e o desempenho melhora.

Aconselhamos uma abordagem semelhante à apresentada acima para todos os elementos visuais nos seus relatórios. Faça a pergunta: "Será que são precisos todos os dados neste elemento visual? Existe alguma forma de filtrar o volume de dados apresentados no elemento visual de modo a que tenha um impacto mínimo na experiência do utilizador final?" As tabelas, em particular, podem utilizar muita memória.

## <a name="limit-visuals-on-report-pages"></a>Limitar os elementos visuais nas páginas de relatórios

O princípio apresentado acima aplica-se também ao número de elementos visuais num determinado relatório. Recomendamos que limite o número de elementos visuais num determinado relatório de forma a ter apenas os necessários. As páginas de exploração são úteis para fornecer detalhes adicionais sem acrescentar mais elementos visuais ao relatório.  

## <a name="optimize-your-model"></a>Otimizar o seu modelo

Algumas das melhores práticas:

- Se for possível, remova as tabelas e colunas que não são utilizadas. 
- Evite contagens distintas em campos com cardinalidade elevada, ou seja, milhões de valores distintos.  
- Tome medidas para evitar campos com precisão desnecessária e uma alta cardinalidade. Por exemplo, pode dividir valores datetime altamente exclusivos em colunas separadas (como mês, ano, dia, entre outros). Em alternativa, sempre que possível, deve arredondar os valores em campos de alta precisão para diminuir a cardinalidade (por exemplo, 13,29889 -> 13,3).
- Sempre que possível, utilize números inteiros em vez de cadeias.
- Tenha em atenção que as funções DAX, como a RANKX, têm de testar cada linha de uma tabela. No pior dos cenários, devido ao aumento linear do tamanho das tabelas, estas funções podem aumentar exponencialmente o tempo de execução e os requisitos de memória.
- Ao ligar-se a origens de dados através do DirectQuery, pondere voltar a indexar as colunas que são normalmente filtradas ou segmentadas. A indexação melhora consideravelmente a resposta do relatório.  

Para obter mais informações sobre a otimização de dados do DirectQuery, veja [DirectQuery in SQL Server 2016 Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2017/04/06/directquery-in-sql-server-2016-analysis-services-whitepaper/) (Serviços de Análise do DirectQuery no SQL Server 2016).

## <a name="directquery-and-live-connection-understand-underlying-data-source-performance"></a>DirectQuery e Ligação em Direto: compreender o desempenho das origens de dados subjacentes

No caso do DirectQuery ou da ligação em direto, quando os utilizadores acedem a um relatório do Power BI, o programa envia consultas em tempo real para a origem de dados subjacente. O relatório é composto após a origem de dados devolver os dados da consulta. Como resultado, o desempenho do seu relatório depende, em grande parte, do desempenho da origem de dados subjacente.

Nestes casos, é importante compreender o desempenho da sua origem de dados subjacente. Diferentes origens de dados têm diferentes ferramentas de compreensão do desempenho das consultas. Por exemplo, o SQL Server e o Azure SQL fornecem o Arquivo de Consultas, que captura um histórico das consultas e as respetivas estatísticas de tempo de execução.

Ao implementar relatórios do Power BI através do DirectQuery e da ligação em direto, experimente executar algumas das ações que os utilizadores finais realizarão no Power BI Desktop. Se o relatório demorar muito a carregar no Power BI Desktop, é provável que seja lento a carregar no serviço dos seus utilizadores finais. 

## <a name="directquery-best-practices"></a>Melhores práticas do DirectQuery

A seguinte secção descreve as melhores práticas gerais para se ligar através do DirectQuery.

### <a name="db-design-guidance"></a>Orientação sobre estrutura de base dados

- Sempre que possível, envie as colunas e medidas calculadas para a origem através de push. Quanto maior for a proximidade à origem, maior será a probabilidade de obter um bom desempenho.
- Otimize! Compreenda os planos de execução das suas consultas, adicione índices para colunas filtradas frequentemente, entre outros.

### <a name="modeling-guidance"></a>Orientação sobre modelação

- Comece no Power BI Desktop.
- Evite consultas complexas no Editor de Consultas.
- Não utilize a filtragem por data relativa no Editor de Consultas.  
- Inicialmente, mantenha as medidas simples. Adicione complexidade progressivamente.
- Evite relações em colunas calculadas e colunas de identificador exclusivo.
- Experimente ativar a funcionalidade "Assumir Integridade Referencial" para as relações. Em muitos casos, esta definição aumenta significativamente o desempenho das consultas.  

### <a name="general"></a>Geral

- Aplique filtros primeiro.
- Pondere desativar a interação entre elementos visuais. Isto reduzirá o carregamento da consulta quando os utilizadores utilizarem o realce cruzado.
- Limite o número de elementos visuais e os dados por elemento visual, como descrito acima.
- A ativação da segurança ao nível da linha pode resultar em alterações consideráveis no desempenho. Certifique-se de que testa as diferentes funções de segurança ao nível da linha que serão assumidas pelos seus utilizadores.
- Existem tempos limite ao nível das consultas impostos pelo serviço, de forma a garantir que as consultas de execução longa não monopolizam os recursos do sistema. As consultas que demorarem mais do que 225 segundos excederão o limite de tempo e resultarão num erro ao nível do elemento visual.

## <a name="understand-dashboards-and-query-caches"></a>Compreender dashboards e caches de consultas

Os elementos visuais afixados a dashboards são processados pela cache de consulta quando o dashboard é carregado. Por outro lado, ao aceder a um relatório, as consultas na origem de dados são feitas no momento, seja no serviço Power BI (no caso de importações) ou na origem de dados que especificar (no caso do DirectQuery ou da ligação em direto).  

> [!NOTE]
> Quando afixa relatórios de mosaico a um dashboard, os mesmos não são processados a partir da cache de consulta. Em vez disso, funcionam como relatórios e realizam consultas imediatas aos núcleos back-end.

Como o nome indica, obter os dados da cache de consulta fornece um desempenho melhor e mais consistente do que a obtenção da origem de dados. Uma forma de tirar partido desta funcionalidade é definir os dashboards como a página de destino principal dos seus utilizadores. Afixe os elementos visuais mais utilizados e pedidos aos dashboards. Desta forma, os dashboards tornam-se uma valiosa "primeira linha de defesa", que fornece consistência no desempenho com uma carga menor na capacidade. Ainda assim, os utilizadores podem clicar no relatório para examinar os detalhes.  
 

No caso do DirectQuery e da ligação em direto, a cache de consulta é atualizada periodicamente através de consultas à origem de dados. Por predefinição, a consulta é feita a cada hora, embora possa ser configurada nas definições do conjunto de dados. Cada atualização da cache enviará consultas para a origem de dados subjacente para atualizar a cache. O número de consultas geradas depende do número de elementos visuais afixados aos dashboards que dependem da respetiva origem de dados. Tenha em atenção que, se a segurança ao nível da linha estiver ativada, as consultas são geradas para cada contexto de segurança diferente. Por exemplo, se tiver duas funções diferentes para categorizar os seus utilizadores e os mesmos tiverem duas vistas diferentes dos dados, o Power BI irá gerar dois conjuntos de consultas durante a atualização de cache da consulta. 

## <a name="understand-custom-visual-performance"></a>Compreender o desempenho de um elemento visual personalizado 

Certifique se de que testa os seus elementos visuais personalizados com cuidado para garantir um desempenho elevado. Os elementos visuais personalizados mal otimizados podem afetar negativamente o desempenho de todo o relatório. 

## <a name="deep-dive-into-query-performance-with-sql-profiler-and-power-bi-desktop"></a>Aprofundamento sobre o desempenho das consultas com o SQL Profiler e o Power BI Desktop

Para um aprofundamento sobre quais os elementos visuais que ocupam mais tempo e recursos, pode ligar o SQL Profiler ao Power BI Desktop para ter uma visão completa do desempenho da consulta.

> [!NOTE]
> O Power BI Desktop suporta a ligação a uma porta de diagnóstico. A porta de diagnóstico permite que outras ferramentas se liguem e executem rastreios para fins de diagnóstico. *Fazer alterações ao modelo não é suportado! As alterações ao modelo podem provocar danos e perda de dados.*

As instruções são as seguintes:
  
1. **Instale o SQL Server Profiler e execute o Power BI Desktop**

   O SQL Server Profiler está disponível como parte do SQL Server Management Studio.

2. **Determinar a porta utilizada pelo Power BI Desktop**

   Execute a linha de comandos ou o PowerShell com privilégios de administrador e utilize o comando netstat para localizar a porta que o Power BI Desktop está a utilizar para a análise:

   `> netstat -b -n`

   O resultado deverá ser uma lista de aplicações e as respetivas portas abertas. Por exemplo:  

   `TCP    [::1]:55786            [::1]:55830            ESTABLISHED`

   [msmdsrv.exe]

   Procure a porta utilizada pelo msmdsrv.exe e anote-a para utilização futura. Neste caso, utiliza a porta 55786.
3. **Ligar o SQL Server Profiler ao Power BI Desktop**

   - Inicie o SQL Server Profiler a partir do menu **Iniciar**
   - **File** (Ficheiro) > **New Trace** (Novo Rastreio)
   - Tipo de Servidor: Analysis Services
   - Server name (Nome do servidor): localhost:[número da porta indicado cima]
   - No ecrã seguinte, selecione **Run** (Executar)
   - Agora, o SQL Profiler está ativo e criará ativamente os perfis das consultas que o Power BI Desktop enviar. 
   - Ao serem executadas as consultas, poderá ver as respetivas durações e tempo de CPU. Com estas informações, pode determinar quais as consultas que provocam estrangulamentos.  

Através do SQL Profiler, pode identificar as consultas que ocupam mais tempo de CPU. É provável que os estrangulamentos de desempenho sejam causados por essas consultas. Os elementos visuais que executam essas consultas devem ser alvo de otimizações contínuas.

## <a name="gateway-best-practices"></a>Melhores práticas de gateway

O Gateway de dados no local é uma excelente ferramenta para ligar o serviço Power BI aos seus dados no local. Por outro lado, se não for bem planeado, pode originar um estrangulamento no desempenho dos relatórios. Isto aplica-se especialmente aos conjuntos de dados do DirectQuery/ligação em direto, onde todas as consultas e respostas das consultas passam pelo gateway. Seguem-se algumas das melhores práticas para garantir gateways com desempenho elevado: 

- **Utilize o modo Enterprise** em vez do modo pessoal.
- **Especificações de hardware recomendadas para o gateway**: 8 núcleos de CPU, 16 GB de RAM.
- **Configurar a monitorização**: configure a monitorização do desempenho no computador do gateway para verificar se o gateway está a ficar sobrecarregado e a provocar um estrangulamento. Para obter mais informações, veja [Resolução de problemas do Gateway de dados no local](service-gateway-onprem-tshoot.md).
- **Aumentar verticalmente ou horizontalmente**: se o gateway estiver a provocar um estrangulamento, pondere aumentar verticalmente (isto é, mover o gateway para um computador com mais CPU e RAM) ou horizontalmente (por exemplo, dividir os conjuntos de dados por diferentes gateways). 
- **Importação separada vs. DirectQuery**: se aumentar horizontalmente, pondere separar os gateways responsáveis pela importação dos gateways responsáveis pelo DirectQuery.

## <a name="network-latency"></a>Latência de rede

A latência de rede pode ter um impacto no desempenho do relatório ao aumentar o tempo necessário para os pedidos chegarem ao serviço Power BI e para as respostas serem devolvidas. Os inquilinos no Power BI estão atribuídos a uma região específica. Pode ver a região "base" do seu inquilino ao aceder a powerbi.cim, selecionar **?** no canto superior direito e, em seguida, selecionar **Sobre o Power BI**. Quando os utilizadores de um inquilino acedem ao serviço Power BI, os respetivos pedidos são sempre encaminhados para esta região. Quando os pedidos chegarem ao serviço Power BI, o mesmo poderá enviar pedidos adicionais (por exemplo, para a origem de dados subjacente ou o gateway) que também estão sujeitos à latência de rede.

As ferramentas como o [Azure Speed Test](http://azurespeedtest.azurewebsites.net/) podem fornecer um indicador da latência de rede entre o cliente e a região do Azure. No geral, para minimizar o impacto da latência de rede, tente manter as origens de dados, os gateways e o seu cluster do Power BI o mais próximo possível. Se a latência de rede for um problema, experimente colocar os gateways e as origens de dados mais perto do seu cluster do Power BI ao colocá-los em máquinas virtuais.

Para melhorar a latência de rede, pondere utilizar o [Azure ExpressRoute](https://azure.microsoft.com/services/expressroute/), que consegue criar ligações de rede mais rápidas e fiáveis entre os seus clientes e os datacenters do Azure.

## <a name="next-steps"></a>Próximos passos

- [Planear uma Implementação do Power BI Enterprise](https://aka.ms/pbienterprisedeploy) com um guia completo sobre implementações do Power BI em larga escala
- [DirectQuery no SQL Server 2016 Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2017/04/06/directquery-in-sql-server-2016-analysis-services-whitepaper/)
- [[YouTube] Building Fast and Reliable Reports in Power BI](https://www.youtube.com/watch?v=GhiJABR7XX0) (Criar Relatórios Rápidos e de Confiança no Power BI)
- [[YouTube] Power BI Enterprise Deployments](https://www.youtube.com/watch?v=K-zEWICvICM) (Implementações do Power BI Enterprise)
