---
title: Melhores práticas para o desempenho do Power BI
description: Este artigo fornece orientação para construir relatórios rápidos e fiáveis no Power BI
author: MarkMcGeeAtAquent
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/18/2018
ms.author: v-mamcge
LocalizationGroup: Reports
ms.openlocfilehash: 78dcd0ac0735bfbb3c22678d6bda1397120360cd
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/26/2018
ms.locfileid: "34310550"
---
# <a name="power-bi-performance-best-practices"></a>Melhores Práticas para o Desempenho do Power BI 
Este artigo oferece orientação para construir relatórios rápidos e fiáveis no Power BI.  

## <a name="use-filters-to-limit-report-visuals-to-display-only-whats-needed"></a>Utilizar filtros para que os elementos visuais de relatório apresentem apenas o necessário 

Quanto maior for o volume de dados que um elemento visual tem de apresentar, mais lento será a carregar. Embora este princípio pareça óbvio, pode ser fácil esquecê-lo. Por exemplo, digamos que tem um conjunto de dados grande. Além disso, quer criar um relatório com uma tabela de uma tabela. Os utilizadores finais utilizarão as segmentações na página para aceder às linhas que pretendem. Normalmente, só estão interessados em algumas dezenas de linhas.

Um erro comum é deixar a vista predefinida da tabela não filtrada, ou seja, com mais de um milhão de linhas visíveis. Os dados destas linhas têm de ser carregados para a memória e descomprimidos a cada atualização. Isto criava enormes cargas de memória. A solução: reduzir o número máximo de itens que uma tabela apresenta através do filtro "Top N". O número máximo de itens por ser muito superior ao número que será necessário aos utilizadores, por exemplo 10 000. Como resultado, a experiência do utilizador final manteve-se igual, enquanto a utilização da memória baixou consideravelmente e o desempenho melhorou. 
 
Aconselhamos uma abordagem semelhante à apresentada para todos os elementos visuais nos seus relatórios. Faça a pergunta: "Será que são precisos todos os dados neste elemento visual? Será que existe uma forma de filtrar o volume de dados apresentados que tenha um impacto mínimo na experiência do utilizador final?" Tenha em atenção que as tabelas, em particular, podem utilizar muita memória. 
 
## <a name="limit-visuals-on-report-pages"></a>Limitar os elementos visuais nas páginas de relatórios 
O princípio apresentado acima aplica-se também ao número de elementos visuais num determinado relatório. Recomendamos que limite o número de elementos visuais num determinado relatório de forma a ter apenas os necessários. As páginas de exploração são úteis para fornecer detalhes adicionais sem acrescentar mais elementos visuais ao relatório.  
 
## <a name="optimize-your-model"></a>Otimizar o seu modelo 
Algumas das melhores práticas: 
 
- Se possível, deve remover as tabelas e colunas que não são utilizadas. 
- Evite contagens distintas em campos com cardinalidade elevada, ou seja, milhões de valores distintos.  
- Tome medidas para evitar campos com precisão desnecessária e uma alta cardinalidade. Por exemplo, pode dividir valores datetime altamente exclusivos em colunas separadas (por exemplo, mês, ano, dia, etc.). Em alternativa, sempre que possível, pode arredondar em campos de alta precisão para diminuir a cardinalidade (por exemplo, 13,29889 -> 13,3). 
- Sempre que possível, utilize números inteiros em vez de cadeias. 
- Tenha em atenção que as funções DAX, como a RANKX, têm de testar cada linha de uma tabela. No pior dos cenários, devido ao aumento linear do tamanho da tabela, estas funções podem aumentar exponencialmente o tempo de carregamento e os requisitos de memória. 
- Ao ligar a origens de dados através do DirectQuery, pondere voltar a indexar colunas que estão normalmente filtradas ou segmentadas. Isto melhorará bastante a reatividade do relatório.  
 

Para obter mais orientação sobre como otimizar as origens de dados para o DirectQuery, veja [DirectQuery in SQL Server 2016 Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2017/04/06/directquery-in-sql-server-2016-analysis-services-whitepaper/) (Serviços de Análise do DirectQuery no SQL Server 2016). 
 
## <a name="directquery-and-live-connection-understand-underlying-data-source-performance"></a>DirectQuery e Ligação em Direto: compreender o desempenho das origens de dados subjacentes 

No caso do DirectQuery ou da ligação em direto, quando os utilizadores acedem a um relatório do Power BI, o programa envia consultas em tempo real para a origem de dados subjacente. O relatório é composto após a origem de dados devolver os dados da consulta. Como resultado, o desempenho do seu relatório nestes casos depende, em grande parte, do desempenho da origem de dados subjacente. 
 
Nestes casos, é importante compreender o desempenho da sua origem de dados subjacente. Diferentes origens de dados terão diferentes ferramentas para compreender o desempenho das consultas. Por exemplo, o SQL Server e o Azure SQL fornecem o Arquivo de Consultas, que captura um histórico das consultas e as respetivas estatísticas de tempo de execução. 
 
Regra geral, ao implementar relatórios do Power BI através do DirectQuery e da ligação em direto, experimente executar algumas das ações que os utilizadores finais realizarão no Power BI Desktop. Se o relatório demorar muito a carregar no Power BI Desktop, certamente será lento a carregar no serviço dos seus utilizadores finais. 
 
## <a name="directquery-best-practices"></a>Melhores práticas do DirectQuery 
A seguinte secção descreve as melhores práticas gerais para se ligar através do DirectQuery.
  
### <a name="db-design-guidance"></a>Orientação sobre estrutura de base dados 
- Sempre que possível, envie as colunas e medidas calculadas para a origem através de push. Quanto mais perto estiverem da origem, maior a probabilidade de um bom desempenho. 
- Otimize! Compreenda os planos de execução para as suas consultas, adicione índices para colunas filtradas frequentemente, entre outros. 

### <a name="modelling-guidance"></a>Orientação sobre modelação 
- Comece no Power BI Desktop. 
- Evite consultas complexas no Editor de Consultas. 
- Não utilize filtragem por data relativa no Editor de Consultas.  
- Inicialmente, mantenha as medidas simples. Adicione complexidade progressivamente. 
- Evite relações em colunas calculadas e colunas de identificador exclusivo. 
- Experimente ativar a funcionalidade "Assumir Integridade Referencial" para as relações. Em muitos casos, poderá aumentar significativamente o desempenho das consultas.  

### <a name="general"></a>Geral 
- Aplique filtros primeiro. 
- Pondere desativar a interação entre elementos visuais. Isto reduzirá a carga da consulta quando os utilizadores realçarem de forma cruzada. 
- Limite o número de elementos visuais e os dados por elemento visual, como descrito acima. 
- A ativação da segurança ao nível da linha pode resultar em alterações substanciais no desempenho. Certifique-se de que testa as diferentes funções de segurança ao nível da linha que serão assumidas pelos seus utilizadores. 
- Tenha em atenção que existem limites de tempo ao nível das consultas impostos pelo serviço, de forma a garantir que as consultas de execução longa não monopolizam os recursos do sistema. As consultas que demorarem mais do que 225 segundos excederão o limite de tempo e resultarão num erro ao nível do elemento visual. 

## <a name="understanding-dashboards-and-query-caches"></a>Compreender dashboards e caches de consultas 
Os elementos visuais afixados a dashboards são processados pela cache de consulta quando o dashboard é carregado. Por outro lado, ao aceder a um relatório, as consultas na origem de dados são feitas no momento, seja no serviço Power BI (no caso de importações) ou na origem de dados que especificar (no caso do DirectQuery ou da ligação em direto).  
 
> [!NOTE]
> Quando afixa relatórios dinâmicos a um dashboard, os mesmos não são processados a partir da cache de consulta. Em vez disso, funcionam como relatórios e realizam consultas imediatas aos núcleos back-end. 
 

Como o nome indica, obter os dados da cache de consulta fornece um desempenho melhor e mais consistente do que a obtenção da origem de dados. Uma forma de tirar partido desta funcionalidade é definir os dashboards como a página de destino principal dos seus utilizadores. Afixe aos dashboards os elementos visuais utilizados e pedidos frequentemente. Desta forma, os dashboards tornam-se uma valiosa "primeira linha de defesa" que fornece consistência no desempenho com uma carga menor na capacidade. Ainda assim, os utilizadores podem clicar no relatório para examinar os detalhes.  
 

Tenha em atenção que, para o DirectQuery e a ligação em tempo real, esta cache de consulta é atualizada periodicamente através de consultas à origem de dados. Por predefinição, a consulta é feita a cada hora, embora possa ser configurada nas definições do conjunto de dados. Cada atualização da cache enviará consultas para a origem de dados subjacente para atualizar a cache. O número de consultas geradas depende do número de elementos visuais afixados aos dashboards que dependem da respetiva origem de dados. Tenha em atenção que, se a segurança ao nível da linha estiver ativada, as consultas são geradas para cada contexto de segurança diferente. Por exemplo, se tiver duas funções diferentes para os seus utilizadores, com duas vistas diferentes dos dados, serão gerados dois conjuntos de consultas durante a atualização da cache de consulta. 
 
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

   TCP    [::1]:55786            [::1]:55830            ESTABLISHED 

   [msmdsrv.exe] 

   Procure a porta utilizada pelo msmdsrv.exe e anote-a para utilização futura. Neste caso, deverá utilizar a porta 55786. 
3.  **Ligar o SQL Server Profiler ao Power BI Desktop** 

   - Inicie o SQL Server Profiler a partir do menu **Iniciar** 
   - **File** (Ficheiro) > **New Trace** (Novo Rastreio) 
   - Server Type (Tipo de Servidor): Analysis Services 
   - Server name (Nome do servidor): localhost:[número da porta indicado cima] 
   - No ecrã seguinte, selecione **Run** (Executar) 
   - Agora, o SQL Profiler está ativo e criará ativamente os perfis das consultas que o Power BI Desktop enviar. 
   - Ao serem executadas as consultas, poderá ver as respetivas durações e tempo de CPU. Com estas informações, pode determinar quais as consultas que provocam estrangulamentos.  

Através do SQL Profiler, pode identificar as consultas que ocupam mais tempo de CPU, sendo essas provavelmente as causas dos estrangulamentos de desempenho. Os elementos visuais que executam as referidas consultas devem tornar-se os pontos principais a resolver para uma otimização contínua. 

## <a name="gateway-best-practices"></a>Melhores práticas de gateway 

O Gateway de dados no local é uma excelente ferramenta para ligar o serviço Power BI aos seus dados no local. Por outro lado, se não for bem planeado, pode originar um estrangulamento no desempenho dos relatórios. Isto aplica-se especialmente aos conjuntos de dados do DirectQuery/ligação em direto, onde todas as consultas e respostas das consultas passam pelo gateway. Seguem-se algumas das melhores práticas para garantir gateways com desempenho elevado: 
 
- **Utilize o modo Enterprise** em vez do modo pessoal. 
- **Especificações de hardware recomendadas para o gateway**: 8 núcleos de CPU, 16 GB de RAM. 
- **Configure a monitorização**: configure a monitorização do desempenho no computador do gateway para que o mesmo compreenda que o gateway está a ficar sobrecarregado e a provocar um estrangulamento. Para obter mais informações, veja [Resolução de problemas do Gateway de dados no local](service-gateway-onprem-tshoot.md).
- **Aumente verticalmente ou horizontalmente**: se o gateway estiver a sofrer um estrangulamento, pondere aumentar verticalmente (isto é, mover o gateway para um computador com mais CPU e RAM) ou aumentar horizontalmente (por exemplo, dividir os conjuntos de dados por diferentes gateways). 
- **Importação separada vs. DirectQuery**: se ampliar horizontalmente, pondere separar os gateways responsáveis pela importação dos responsáveis pelo DirectQuery. 
 
## <a name="network-latency"></a>Latência de rede 
A latência de rede pode ter um impacto no desempenho do relatório ao aumentar o tempo necessário para os pedidos chegarem ao serviço Power BI e para as respostas serem devolvidas. Os inquilinos no Power BI estão atribuídos a uma região específica. Pode ver a região "base" do seu inquilino ao aceder a powerbi.cim, selecionar **?** no canto superior direito e, em seguida, clicar em **About Power BI** (Acerca do Power BI). Quando os utilizadores de um inquilino acedem ao serviço Power BI, os respetivos pedidos são encaminhados para esta região. Quando os pedidos chegarem ao serviço Power BI, o mesmo poderá enviar pedidos adicionais (por exemplo, para a origem de dados subjacente ou o gateway) que também estão sujeitos à latência de rede. 

As ferramentas como o [Azure Speed Test](http://azurespeedtest.azurewebsites.net/) (Teste de Velocidade do Azure) podem fornecer um indicativo da latência de rede entre o cliente e a região do Azure. No geral, para minimizar o impacto da latência de rede, tente manter as origens de dados, os gateways e o seu cluster do Power BI o mais próximo possível. Se a latência de rede for um problema, pode experimentar colocar os gateways e origens de dados mais perto do seu cluster do Power BI ao colocá-los em máquinas virtuais. 

Para melhorar a latência de rede, pondere utilizar o [Azure ExpressRoute](https://azure.microsoft.com/services/expressroute/), que consegue criar ligações de rede mais rápidas e de confiança entre os seus clientes e os datacenters do Azure. 

## <a name="next-steps"></a>Próximos passos
- [Planear uma Implementação do Power BI Enterprise](https://aka.ms/pbienterprisedeploy) com um guia completo sobre implementações do Power BI em larga escala 
- [DirectQuery no SQL Server 2016 Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2017/04/06/directquery-in-sql-server-2016-analysis-services-whitepaper/) 
- [[YouTube] Building Fast and Reliable Reports in Power BI](https://www.youtube.com/watch?v=GhiJABR7XX0) (Criar Relatórios Rápidos e de Confiança no Power BI) 
- [[YouTube] Power BI Enterprise Deployments](https://www.youtube.com/watch?v=K-zEWICvICM) (Implementações do Power BI Enterprise)  
 
 
