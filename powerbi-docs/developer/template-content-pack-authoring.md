---
title: "Criar pacotes de conteúdos de modelo no Power BI"
description: "Criação do Pacote de Conteúdos de Modelo"
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/09/2017
ms.author: asaxton
ms.openlocfilehash: 332b8eb7087bbf70559a1e63b0736c9cb9289349
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="author-template-content-packs-in-power-bi"></a>Criar pacotes de conteúdos de modelo no Power BI
Criar um pacote de conteúdos de modelo que utiliza o Power BI Desktop e o PowerBI.com. Existem quatro componentes para o pacote de conteúdos:

* As consultas permitem-lhe [ligar](../desktop-connect-to-data.md) e [transformar](../desktop-query-overview.md) os dados, bem como definir [parâmetros](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/)  
* Modelo de dados para criar [relações](../desktop-create-and-manage-relationships.md), [medidas](../desktop-measures.md) e melhorias de perguntas e respostas  
* As [páginas](../desktop-report-view.md) do relatório incluem elementos visuais e filtros para apresentar informações sobre os seus dados  
* O [dashboard](../service-dashboards.md) e os [mosaicos](../service-dashboard-create.md) oferecem uma descrição geral das informações incluídas  

Poderá estar familiarizado com cada peça como as funcionalidades existentes do Power BI. Ao criar um pacote de conteúdos, existem mais pontos a considerar para cada aspeto, veja cada secção abaixo para obter mais detalhes.

<a name="queries"></a>

## <a name="queries"></a>Consultas
Para pacotes de conteúdos de modelo, são utilizadas consultas desenvolvidas no Power BI Desktop para ligar a sua origem de dados e importar dados. Estas consultas são precisas para devolver um esquema consistente e são suportadas para a atualização de Dados Agendados (a consulta direta não é suportada).

Os pacotes de conteúdo de modelo suportam apenas uma origem de dados por pacote de conteúdo, por isso defina as suas consultas cuidadosamente. Uma única origem de dados está definida. Pode realizar várias chamadas de API em diferentes consultas, se todas as chamadas forem para o mesmo ponto final de API e utilizarem a mesma autenticação. Os pacotes de conteúdos do Power BI não suportam várias origens que precisam de autenticações diferentes.

### <a name="connect-to-your-api"></a>Ligar à sua API
Para começar, terá de ligar à sua API do Power BI Desktop para começar a criar as suas consultas.

Pode utilizar os Conectores de Dados que estão imediatamente disponíveis no Power BI Desktop para ligar à sua API. Pode utilizar o Conector de Dados da Web (Obter Dados -> Web) para ligar à API Rest ou ao conector de OData (Obter Dados -> Feed do OData) para ligar ao feed do OData. Tenha em atenção que estes conectores irão funcionar imediatamente apenas se a sua API suportar a Autenticação Básica.

> [!NOTE]
> Se a sua API utiliza outros tipos de autenticação, como o OAuth 2.0 ou a Chave de API Web, então terá de desenvolver o seu próprio Conector de Dados para permitir que o Power BI Desktop se ligue com êxito e realize a autenticação à sua API. Para obter detalhes sobre como desenvolver o seu próprio Conector de Dados para o Pacote de Conteúdos, veja a documentação dos Conectores de Dados [aqui](https://aka.ms/DataConnectors). 
> 
> 

### <a name="consider-the-source"></a>Considere a origem
As consultas definem os dados que serão incluídos no modelo de dados. Dependendo do tamanho do seu sistema, estas consultas também devem incluir filtros para garantir que os seus clientes estão a lidar com um tamanho gerível que se adequa ao seu cenário de negócio.

Os pacotes de conteúdos do Power BI podem executar várias consultas em paralelo e para vários utilizadores em simultâneo.  Planeie a estratégia de limitação e de concorrência com antecedência e pergunte-nos como tornar o pacote de conteúdos tolerante a falhas.

### <a name="schema-enforcement"></a>Imposição de esquema
Certifique-se de que as suas consultas são resilientes a alterações no seu sistema, as alterações no esquema de atualização podem interromper o modelo. Se a origem puder devolver resultados do esquema nulo/em falta para algumas consultas, considere devolver uma tabela vazia ou gerar mensagens personalizadas de erro que façam sentido para o utilizador.

### <a name="parameters"></a>Parâmetros
Os [parâmetros](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/) no Power BI Desktop permitem que os utilizadores apresentem valores de entrada que personalizam os dados obtidos pelo utilizador. Considere os parâmetros de antemão para evitar voltar a trabalhar após investir tempo para criar consultas detalhadas ou relatórios.

> [!NOTE]
> Os pacotes de conteúdos de modelo atualmente suportam apenas parâmetros de texto. Podem ser utilizados outros tipos de parâmetros durante o desenvolvimento, mas durante a parte de [teste](template-content-pack-testing.md#templates), todos os valores fornecidos pelos utilizadores serão literais.
> 
> 

### <a name="additional-query-tips"></a>Sugestões de consulta adicionais
* Certifique-se de que todas as colunas são escritas adequadamente  
* As colunas têm nomes informativos (veja as perguntas e respostas)  
* Para a lógica partilhada, considere a utilização de funções ou consultas  
* Os níveis de privacidade não são atualmente suportados no serviço - se receber um aviso sobre os níveis de privacidade, poderá ter de escrever novamente a consulta para utilizar caminhos relativos  

## <a name="data-model"></a>Modelo de Dados
Um modelo de dados bem definido irá garantir que os seus clientes podem interagir facilmente e de forma intuitiva com o pacote de conteúdos. Crie o modelo de dados no Power BI Desktop.

> [!NOTE]
> Muitas das modelações básicas (ou seja, nomes das colunas) devem ser feitas nas [consultas](#queries).
> 
> 

### <a name="qa"></a>Perguntas e Respostas
A modelação também irá afetar a forma como as perguntas e respostas podem apresentar resultados para os seus clientes. Certifique-se de que adiciona sinónimos às colunas utilizadas habitualmente e que as colunas estão corretamente designadas nas [consultas](#queries).

### <a name="additional-data-model-tips"></a>Sugestões de modelos de dados adicionais
* Todas as colunas de valor têm a formatação aplicada
    >[!NOTE]
    >Os tipos devem ser aplicados na consulta.  
* Todas as medidas têm a formatação aplicada  
* O Resumo de Predefinição está definido. Especialmente "Não Resumir", quando aplicável (para valores exclusivos por exemplo)  
* A Categoria de Dados foi definida, quando aplicável  
* As relações são definidas, conforme preciso  

## <a name="reports"></a>Relatórios
As páginas de relatório oferecem informações adicionais sobre os dados incluídos no pacote de conteúdos. Utilize as páginas dos relatórios para responder às principais perguntas empresariais que o pacote de conteúdos está a tentar resolver. Criar o relatório com o Power BI Desktop.

> [!NOTE]
> Pode ser incluído apenas um relatório num pacote de conteúdos, tire partido das diferentes páginas para destacar secções específicas do seu cenário.
> 
> 

### <a name="additional-report-tips"></a>Sugestões de relatório adicionais
* Utilize mais de um elemento visual por página para filtragem cruzada  
* Alinhe os elementos visuais cuidadosamente (sem sobreposição)  
* A página está definida como "4:3" ou "16:9" modo de esquema  
* Todas as agregações apresentadas têm um sentido numérico (médias, valores únicos)  
* Repartir produz resultados razoáveis  
* O logótipo está presente, pelo menos, no relatório principal  
* Os elementos estão no esquema de cores do cliente na medida do possível  

<a name="dashboard"></a>

## <a name="dashboard"></a>Dashboard
O dashboard é o principal ponto de interação com o pacote de conteúdos para os seus clientes. Deve incluir uma descrição geral do conteúdo incluído, especialmente as métricas importantes para o seu cenário de negócio.

Para criar um dashboard para o pacote de conteúdos de modelo, basta carregar o PBIX através de Obter Dados > Ficheiros ou publicar diretamente do Power BI Desktop.

> [!NOTE]
> Os pacotes de conteúdos de modelo precisam atualmente de um único relatório e conjunto de dados por pacote de conteúdos. Não afixe conteúdo a partir de vários relatórios/conjuntos de dados no dashboard utilizado no pacote de conteúdos.
> 
> 

### <a name="additional-dashboard-tips"></a>Sugestões adicionais do dashboard
* Mantenha o mesmo tema ao afixar, de modo a que os mosaicos no dashboard sejam consistentes  
* Afixe um logótipo ao tema, para que consumidores saibam de onde é o pacote  
* O esquema sugerido para trabalhar com a maioria das resoluções de ecrã é de 5-6 mosaicos pequenos de largura  
* Todos os mosaicos do dashboard devem ter títulos/subtítulos adequados  
* Considere os agrupamentos no dashboard para diferentes cenários, verticalmente ou horizontalmente  

<a name="restrictions"></a>

## <a name="summary-of-restrictions"></a>Resumo de restrições
Conforme indicado nas secções acima, atualmente os pacotes de conteúdos de modelo têm um conjunto de restrições:  

| Suportado | *Não Suportado* |
| --- | --- |
| Conjuntos de dados incorporados no PBI Desktop |*Conjuntos de dados de outros pacotes de conteúdos ou entradas, como ficheiros do Excel* |
| Origem de dados suportada para atualização de Dados Agendada na cloud |*Não é suportada a consulta direta ou conectividade no local* |
| Consultas que devolvam erros ou esquemas consistentes quando apropriado |*Esquemas dinâmicos ou personalizados* |
| Uma origem de dados por conjunto de dados |*Várias origens de dados, como aplicações híbridas ou URLs que são detetados como múltiplas origens de dados* |
| Parâmetros de tipo de texto |*Outros tipos de parâmetro (como a data) ou a "lista permitida de valores"* |
| Um dashboard, relatório e conjunto de dados |*Vários dashboards, relatórios ou conjuntos de dados* |

## <a name="next-step"></a>Próxima etapa
[Submissão e Teste do Pacote de Conteúdos](template-content-pack-testing.md)

