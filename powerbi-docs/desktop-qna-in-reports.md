---
title: Utilizar as Perguntas e Respostas no Power BI Desktop
description: Agora pode utilizar consultas de linguagem natural no Power BI Desktop com as Perguntas e Respostas
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/12/2017
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: d6075832d77f6bea7d7d8588719c4a002cdbf298
ms.sourcegitcommit: 93e7362fc47319959b6992dfd037effdf831d010
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/21/2018
---
# <a name="use-qa-in-power-bi-desktop-for-natural-language-queries"></a>Utilizar as Perguntas e Respostas no Power BI Desktop para consultas de linguagem natural
Utilizar linguagem natural e expressões comuns para fazer perguntas sobre os seus dados é algo extremamente útil. Torna-se ainda mais eficaz quando os seus dados respondem a essas perguntas e é isso que as Perguntas e Respostas no **Power BI Desktop** lhe permitem fazer.

Para que a funcionalidade Perguntas e Respostas interprete com êxito a abrangente quantidade de perguntas às quais consegue responder, esta tem de fazer suposições sobre o modelo. Se a estrutura do seu modelo não corresponder a uma ou mais destas suposições, terá de ajustar o seu modelo. Esses ajustes às Perguntas e Respostas são as mesmas otimizações recomendadas para qualquer modelo no Power BI, independentemente se utiliza as Perguntas e Respostas. 

Nas secções seguintes, descrevemos como ajustar o seu modelo para que funcione bem com as Perguntas e Respostas no Power BI.

## <a name="add-missing-relationships"></a>Adicionar relações em falta

Se o seu modelo tiver relações entre tabelas em falta, os relatórios do Power BI e as Perguntas e Respostas não conseguirão interpretar a forma como devem associar essas tabelas se fizer perguntas sobre as mesmas. As relações são o alicerce de um bom modelo. Por exemplo, não pode pedir as "vendas totais dos clientes do Porto" se a relação entre as tabelas *encomendas* e *clientes* estiver em falta. As seguintes imagens mostram-lhe exemplos de um modelo que precisa de ser modificado e um modelo que está pronto para as Perguntas e Respostas.

**Precisa de ser modificado**

![relações que precisam de ser modificadas para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_01.png)

**Está pronto para as Perguntas e Respostas**

![relações que estão prontas para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_02.png)


## <a name="rename-tables-and-columns"></a>Mudar o nome de tabelas e colunas

A escolha das tabelas e colunas é muito importante para as Perguntas e Respostas. Por exemplo, se tivesse uma tabela com o nome *ResumoDeClientes* com uma lista dos seus clientes, teria de fazer perguntas como "Lista dos resumos de clientes em Lisboa" em vez de "Lista dos clientes em Lisboa". 

Embora consigam fazer deteção de plurais e quebras de palavras básicas, as Perguntas e Respostas presumem que os nomes da sua tabela e coluna refletem os conteúdos de forma precisa.

Considere outro exemplo. Imagine que tem uma tabela com o nome *ContagemDeFuncionários*, que contém o nome próprio, o apelido e os números dos funcionários, e que tem outra tabela com o nome *Funcionários*, que contém os números dos funcionários, os números das tarefas e as datas de início. As pessoas que conhecem o modelo podem compreendê-lo, mas se outra pessoa pedir a "contagem dos funcionários" irá receber a contagem das linhas da tabela "Funcionários" e provavelmente não era isso que tinha em mente, uma vez que é uma contagem de todas as tarefas que os funcionários já fizeram. Seria melhor mudar o nome dessas tabelas para refletirem corretamente os conteúdos.

**Precisa de ser modificado**

![nomes de tabelas que precisam de ser modificados para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_03.png)

**Está pronto para as Perguntas e Respostas**

![nomes de tabelas que estão prontos para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_04.png)

## <a name="fix-incorrect-data-types"></a>Corrigir tipos de dados incorretos

Os dados importados podem ter tipos de dados incorretos. Nomeadamente, as colunas *data* e *número* que são importadas como *cadeias* não serão interpretadas pelas Perguntas e Respostas como datas e números. Deve garantir que seleciona o tipo de dados correto no seu modelo do Power BI.

![selecionar o tipo de dados correto para garantir que está disponível para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_05.png)

## <a name="mark-year-and-identifier-columns-as-dont-summarize"></a>Marcar as colunas de ano e identificador como Não Resumir

O Power BI agrega agressivamente as colunas numéricas por predefinição, por isso perguntas como "vendas totais por ano" podem resultar num total geral de vendas juntamente como um total geral de anos. Se tiver colunas específicas em que não pretende que o Power BI apresente este comportamento, defina a propriedade **Resumir Por** na coluna para **Não Resumir**. Tenha cuidado com as colunas **ano**, **mês**, **dia** e **ID**, pois costumam causar problemas mais frequentemente. Para outras colunas que não são sensíveis a somas, como *idade*, também pode ser benéfico definir a opção **Resumir Por** para **Não Resumir** ou para **Média**. Encontrará esta definição no separador **Modelação**.

![Não Resumir colunas como ano, mês, data para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_06.png)

## <a name="choose-a-data-category-for-each-date-and-geography-column"></a>Selecionar uma Categoria de Dados para cada coluna de data e geografia

A **Categoria de Dados** fornece conhecimento semântico adicional sobre os conteúdos de uma coluna, para além do tipo de dados. Por exemplo, uma coluna de número inteiro poderá ser marcada como um Código Postal, uma coluna de cadeia poderá ser marcada como uma Cidade, País, Região e por aí adiante. Estas informações são utilizadas pelas Perguntas e Respostas de duas formas importantes: para seleção da visualização e para tendências da linguagem.

Em primeiro lugar, as Perguntas e Respostas utilizam as informações em **Categorias de Dados** para ajudar a tomar decisões sobre o tipo de apresentação visual a utilizar. Por exemplo, reconhece que colunas com **Categorias de Dados** de data ou hora são normalmente uma boa opção para o eixo horizontal de um gráfico de linhas ou o eixo de reprodução de um gráfico de bolhas. Presume que os resultados que contêm colunas com **Categorias de Dados** geográficos podem ter um bom aspeto num mapa.

Em segundo lugar, as Perguntas e Respostas fazem suposições fundamentadas sobre como os utilizadores irão falar sobre as colunas de geografia e data, para ajudar a compreender determinados tipos de perguntas. Por exemplo, a palavra "quando" em "Quando é que o Guilherme Sarmento foi contratado?" irá mapear a uma coluna de data e é mais provável que a palavra "Aveiro" em "Contagem de clientes em Aveiro" seja referente a uma cidade e não a um nome próprio.


![Escolher Categorias de Dados corretamente para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_07.png)

## <a name="choose-a-sort-by-column-for-relevant-columns"></a>Escolher uma opção Ordenar Por Coluna para colunas relevantes

A propriedade **Escolher Por Coluna** permite que uma coluna seja ordenada automaticamente de acordo com uma coluna diferente. Por exemplo, quando pede para "ordenar clientes pelo tamanho da t-shirt", provavelmente quer que a coluna Tamanho da T-shirt seja ordenada pelo tamanho subjacente (XS, S, M, L, XL) e não alfabeticamente (L, M, S, XL, XS).

![Escolher uma opção Ordenar Por Coluna adequada para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_08.png)

## <a name="normalize-your-model"></a>Normalizar o seu modelo

Tenha em atenção que não estamos a dizer que precisa de reformatar o seu modelo inteiro. No entanto, existem determinadas estruturas que são demasiado difíceis e as Perguntas e Respostas não irão processá-las corretamente. Se fizer uma normalização básica da estrutura do seu modelo, a usabilidade dos relatórios do Power BI aumentará significativamente, bem como a precisão dos resultados das Perguntas e Respostas.

A regra geral que deve seguir é esta: cada "conteúdo" exclusivo sobre o qual o utilizador fala deve ser representado exatamente por um objeto de modelo (tabela ou coluna). Se os seus utilizadores falarem sobre clientes, deverá existir um objeto *cliente*. Se os seus utilizadores falarem sobre vendas, deverá existir um objeto *vendas*. Parece simples, não é? Pode ser simples dependendo da formatação dos dados que tem. Existem funcionalidades avançadas de formatação de dados disponíveis no **Editor de Consultas** se for necessário, no entanto, as transformações mais simples podem ocorrer ao utilizar cálculos no modelo do Power BI.

As secções seguintes contêm algumas transformações comuns que poderá ter de realizar.

### <a name="create-new-tables-for-multi-column-entities"></a>Criar novas tabelas para entidades de múltiplas colunas

Se tiver múltiplas colunas que atuam como uma única unidade distinta numa tabela maior, essas colunas devem ser divididas numa tabela própria. Por exemplo, se tiver uma coluna Nome do Contacto, Cargo do Contacto e Telefone do Contacto na tabela *Empresas*, uma estrutura melhor incluiria ter uma tabela *Contactos* separada para conter o Nome, Cargo e Telefone e uma ligação para a tabela *Empresas*. Isto torna muito mais fácil fazer perguntas sobre os contactos, independentemente das perguntas sobre as empresas a que os contactos pertencem, e melhora a flexibilidade da apresentação.

**Precisa de ser modificado**

![utilizar múltiplas tabelas para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_09.png)

**Está pronto para as Perguntas e Respostas**

![utilizar múltiplas tabelas para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_10.png)

### <a name="pivot-to-eliminate-property-bags"></a>Dinamizar para eliminar matrizes de propriedades

Se tiver matrizes de propriedades no seu modelo, estas devem ser reestruturadas para ter uma única coluna por propriedade. As matrizes de propriedades, embora sejam convenientes para gerir grandes quantidades de propriedades, têm várias limitações inerentes que os relatórios do Power BI e as Perguntas e Respostas não conseguem ultrapassar.

Por exemplo, considere uma tabela *DadosDemográficosDosClientes* com as colunas IDDoCliente, Propriedade e Valor, em que cada linha representa uma propriedade diferente do cliente (por exemplo, idade, estado civil, cidade, etc). Ao sobrecarregar o significado da coluna Valor com base nos conteúdos da coluna Propriedade, torna-se impossível para as Perguntas e Respostas interpretarem a maioria das consultas que fazem referência à mesma. Uma pergunta tão simples como "mostrar a idade de cada cliente" poderá funcionar, uma vez que pode ser interpretada como "mostrar os clientes e os dados demográficos dos clientes em que a propriedade é idade". No entanto, a estrutura do modelo não suporta perguntas ligeiramente mais complexas, como "idade média dos clientes em Lisboa". Embora os utilizadores que criam diretamente relatórios do Power BI possam por vezes encontrar formas mais inteligentes de obter os dados que procuram, as Perguntas e Respostas só funcionam quando cada coluna tem apenas um único significado.

**Precisa de ser modificado**

![não utilize matrizes de propriedades em modelos para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_11.png)

**Está pronto para as Perguntas e Respostas**

![utilize múltiplas tabelas para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_12.png)

### <a name="union-to-eliminate-partitioning"></a>União para eliminar a criação de partições

Se tiver criado partições dos seus dados em múltiplas tabelas ou tiver valores articulados em múltiplas colunas, será difícil ou mesmo impossível para os seus utilizadores realizarem algumas operações comuns. Em primeiro lugar, considere a criação de partições de uma tabela típica: uma tabela *Vendas2000-2010* e uma tabela *Vendas2011-2020*. Se todos os seus relatórios importantes estiverem restritos a uma década específica, provavelmente deverá mantê-los desta forma para os relatórios do Power BI. No entanto, a flexibilidade das Perguntas e Respostas levará os seus utilizadores a esperar respostas a perguntas como "vendas totais por ano". Para isto funcionar, terá de unir os dados numa única tabela de modelo do Power BI.

Da mesma forma, considere uma coluna de valor articulado típica: uma tabela *ApresentaçãoDoLivro* que contém as colunas Autor, Livro, Cidade1, Cidade2 e Cidade3. Com uma estrutura como esta, mesmo as perguntas simples como "contagem de livros por cidade" não podem ser interpretadas corretamente. Para isto funcionar, deve criar uma tabela *CidadesDaApresentaçãoDoLivro* separada, que faz a união dos valores de cidade numa única coluna.

**Precisa de ser modificado**

![não utilize matrizes de propriedades em modelos para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_13.png)

**Está pronto para as Perguntas e Respostas**

![utilize múltiplas tabelas para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_14.png)

### <a name="split-formatted-columns"></a>Dividir colunas formatadas

Se a origem a partir da qual está a importar os seus dados contiver colunas formatadas, os relatórios do Power BI (e Perguntas e Respostas) não irão aceder à coluna para analisar os conteúdos. Por isso, se tiver, por exemplo, uma coluna **Endereço Completo** que contém o endereço, cidade e país, também deve dividi-la nas colunas Endereço, Cidade e País para que os seus utilizadores possam consultá-las individualmente.

**Precisa de ser modificado**

![não utilize colunas únicas para múltiplos elementos de dados para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_15.png)

**Está pronto para as Perguntas e Respostas**

![utilize múltiplas tabelas para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_16.png)

Da mesma forma, se tiver colunas de nome completo para uma pessoa, é recomendável adicionar as colunas **Nome Próprio** e **Apelido**, no caso de alguém querer fazer perguntas com nomes parciais. 


### <a name="create-new-tables-for-multi-value-columns"></a>Criar novas tabelas para colunas de múltiplos valores

Além disso, se a origem a partir da qual está a importar os seus dados contiver colunas de múltiplos valores, os relatórios do Power BI (e as Perguntas e Respostas) não irão aceder à coluna para analisar os conteúdos. Por isso, se tiver, por exemplo, uma coluna Compositor que contém os nomes de múltiplos compositores de uma canção, deve dividi-la em múltiplas linhas numa tabela *Compositores* separada.

**Precisa de ser modificado**

![não utilize colunas de múltiplos valores para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_17.png)

**Está pronto para as Perguntas e Respostas**

![utilize múltiplas tabelas para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_18.png)

### <a name="denormalize-to-eliminate-inactive-relationships"></a>Desnormalizar para eliminar relações inativas

A única exceção à regra "a normalização é melhor" ocorre quando existe mais do que um caminho para ir de uma tabela para outra. Por exemplo, se tiver uma tabela *Voos* com as colunas IDDaCidadeDeOrigem e IDDaCidadeDeDestino, em que cada uma está relacionada com a tabela *Cidades*, uma dessas relações terá de ser marcada como inativa. Como as Perguntas e Respostas só podem utilizar relações ativas, não poderá fazer perguntas sobre a origem ou o destino, dependendo do que escolher. Se desnormalizar as colunas de nome de cidade para a tabela *Voos*, poderá fazer perguntas como: "lista de voos de amanhã com a cidade de origem Lisboa e a cidade de destino Porto".

**Precisa de ser modificado**

![apenas um caminho para cada tabela para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_19.png)

**Está pronto para as Perguntas e Respostas**

![utilize múltiplas tabelas para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_20.png)

### <a name="add-synonyms-to-tables-and-columns"></a>Adicionar sinónimos a tabelas e colunas

Este passo aplica-se especificamente às Perguntas e Respostas (e não aos relatórios do Power BI em geral). Muitas vezes, os utilizadores têm uma variedade de termos que utilizam para fazer referência aos mesmos conteúdos, tal como vendas totais, vendas líquidas, vendas líquidas totais. O modelo do Power BI permite que estes sinónimos sejam adicionados a tabelas e colunas no modelo. 

Este pode ser um passo muito importante. Mesmo tendo nomes de coluna e tabela simples, os utilizadores das Perguntas e Respostas fazem perguntas com o vocabulário de que se lembram e não ao escolher a partir de uma lista de colunas predefinida. Quantos mais sinónimos pertinentes adicionar, melhor será a experiência dos seus utilizadores com o seu relatório. Para adicionar Sinónimos, na vista **Relações**, selecione o botão Sinónimos no friso, conforme apresentado na seguinte imagem.

![Adicionar sinónimos para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_21.png)

O campo **Sinónimos** é apresentado no lado direito do **Power BI Desktop**, onde pode adicionar os seus sinónimos, conforme apresentado na seguinte imagem.

![Adicionar sinónimos para as Perguntas e Respostas](media/desktop-qna-in-reports/desktop-qna_22.png)

 Tenha cuidado ao adicionar sinónimos, uma vez que adicionar o mesmo sinónimo a mais do que uma coluna ou tabela irá introduzir ambiguidade. As Perguntas e Respostas utilizam o contexto sempre que possível para optar entre sinónimos ambíguos, mas nem todas as perguntas têm contexto suficiente. Por exemplo, quando o seu utilizador pede a "contagem de clientes", se tiver três coisas com o sinónimo "cliente" no seu modelo, poderá não obter a resposta que procura. Nestes casos, certifique-se de que o sinónimo principal é exclusivo, uma vez que é utilizado na reformulação. Pode alertar o utilizador acerca da ambiguidade (por exemplo, com a reformulação "mostrar o número de registos de cliente arquivados"), para sugerir que pode perguntar de forma diferente.


## <a name="next-steps"></a>Próximos passos
Para obter mais informações sobre funcionalidades no Power BI Desktop, veja os seguintes artigos:

* [Utilizar a pormenorização no Power BI Desktop](desktop-drillthrough.md)
* [Apresentar um mosaico do dashboard ou um elemento visual do relatório no modo de detalhe](service-focus-mode.md)

