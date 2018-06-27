---
title: Editar o esquema linguístico e adicionar expressões nas Perguntas e Respostas
description: Como utilizar o Power BI Desktop para editar o esquema linguístico utilizado pelas Perguntas e Respostas do Power BI.
author: willthom
manager: kfile
ms.reviewer: mihart
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/22/2018
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: c504280257a959ccd7a46e61b9d377c22b76c14d
ms.sourcegitcommit: 2b9ef93bbff5c741ba55ea0502f642632683d593
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/24/2018
ms.locfileid: "34471899"
---
# <a name="language-modeling-and-the-linguistic-schema"></a>Modelação de linguagem e esquema linguístico 
Utilizar linguagem natural e expressões comuns para fazer perguntas sobre os seus dados é algo extremamente útil. Torna-se ainda mais eficaz quando os seus dados respondem a essas perguntas e é isso que as Perguntas e Respostas no Power BI lhe permitem fazer. Quando coloca uma questão nas Perguntas e Respostas do Power BI, estas fazem todos os possíveis para responder corretamente. 

No entanto, para conseguir interações ainda melhores das Perguntas e Respostas, existem formas de melhorar as respostas: uma forma é editar o esquema linguístico. 

Tudo começa com os dados da sua empresa.  Quanto melhor for o modelo de dados, mais fácil será para os utilizadores obter respostas de qualidade. Uma forma de melhorar o modelo é adicionar um esquema linguístico que defina e categorize a terminologia e as relações entre os nomes de tabelas e colunas no conjunto de dados. O Power BI Desktop é onde gere os seus esquemas linguísticos. 

## <a name="what-is-a-linguistic-schema"></a>O que é um esquema linguístico
Um esquema linguístico descreve os termos e as expressões que as Perguntas e Respostas devem compreender para objetos num conjunto de dados, incluindo partes do discurso, sinónimos e expressões relacionados com esse conjunto de dados. Quando importa ou liga a um conjunto de dados, o Power BI cria um esquema linguístico com base na estrutura do conjunto de dados. Quando coloca uma questão nas Perguntas e Respostas, são procuradas correspondências e relações nos dados para descobrir a intenção da sua pergunta. Por exemplo, são procurados substantivos, verbos, adjetivos, expressões e outros elementos. São também procuradas relações, como as colunas que são objetos de um verbo. 

Provavelmente já conhece as partes do discurso (caso contrário, consulte abaixo), mas as expressões podem ser um novo termo para si.  Uma expressão é a forma como fala sobre as relações entre as coisas. Por exemplo, para descrever a relação entre clientes e produtos, pode dizer "os clientes compram produtos". Para descrever a relação entre clientes e idades, pode dizer "as idades indicam há quanto tempo são clientes". Para descrever a relação entre clientes e números de telefone, pode simplesmente dizer "os clientes têm números de telefone".

Estas expressões têm várias formas e tamanhos. Algumas correspondem diretamente a relações no modelo de dados. Algumas estabelecem relações entre as colunas e as respetivas tabelas. Outras estão relacionadas com múltiplas tabelas e colunas em relações complexas. Em todos os casos, descrevem como as coisas estão relacionadas com termos de uso corrente.

Os esquemas linguísticos são guardados num formato YAML. Este formato está relacionado com o formato JSON muito popular, mas fornece uma sintaxe mais flexível e fácil de ler. Os esquemas linguísticos podem ser editados, exportados e importados para o Power BI Desktop.

## <a name="prerequisites"></a>Pré-requisitos
- Se ainda não tiver lido o artigo sobre como [melhorar o seu modelo de dados para as Perguntas e Respostas](desktop-qna-in-reports.md), poderá ser útil lê-lo primeiro. Inclui várias sugestões para estruturar e melhorar o seu modelo de dados e uma secção importante sobre como adicionar sinónimos.  

- Existem dois lados nas Perguntas e Respostas.  O primeiro é a preparação ou "modelação".  O segundo é colocar questões e explorar os dados, ou "consumir". Em algumas empresas, os colaboradores conhecidos como Modeladores de Dados ou Administradores de TI podem ser aqueles que montam os conjuntos de dados, criam os modelos de dados e publicam os conjuntos de dados no Power BI.  Enquanto um segundo conjunto de colaboradores poderá ser constituído por aqueles que "consomem" os dados online.  Noutras empresas, estas funções podem estar combinadas. 

    Este tópico destina-se aos modeladores de dados. As pessoas que utilizam um conjunto de dados e o otimizam para fornecer os melhores resultados de Perguntas e Respostas possíveis. 

- [Ficheiros .yaml e .pbix de exemplo](https://go.microsoft.com/fwlink/?linkid=871858)    
- Como editor de ficheiros YAML, recomendamos o [Visual Studio Code](https://code.visualstudio.com/)



### <a name="set-up-an-editor-for-yaml-files"></a>Configurar um editor de ficheiros YAML
Recomendamos que utilize o Visual Studio Code para editar os ficheiros YAML de esquema linguístico. O Visual Studio Code inclui suporte integrado para ficheiros YAML e pode ser expandido para validar especificamente o formato do esquema linguístico do Power BI.
1. Instale o [Visual Studio Code](https://code.visualstudio.com/).    

2. Selecione o esquema linguístico de exemplo que guardou anteriormente: [ficheiro YAML](https://go.microsoft.com/fwlink/?linkid=871858) (SummerOlympics.lsdl.yaml).    
4. Selecione **Visual Studio Code** e **Utilizar sempre esta aplicação para abrir ficheiros .yaml**.

    ![Como pretende abrir este ficheiro](media/power-bi-q-and-a-linguistic-schema/power-bi-visual-code.png)

4. No Visual Studio Code, instale a extensão YAML Support by Red Hat.    
    a. Selecione o separador **Extensões** (o último à esquerda) ou Ctrl+Shift+X.    
    ![ícone de extensões](media/power-bi-q-and-a-linguistic-schema/power-bi-extensions.png)    
    b. Procure "yaml" e selecione **YAML Support by Red Hat** na lista.    
    c. Selecione **Instalar > Recarregar**.


## <a name="working-with-linguistic-schemas"></a>Trabalhar com esquemas linguísticos
Os esquemas linguísticos podem ser editados, importados e exportados na vista [Relações](desktop-relationship-view.md) no Power BI Desktop. Uma forma de editar um esquema linguístico é [adicionar sinónimos ao painel **Sinónimos**](desktop-qna-in-reports.md). Isto não envolve abrir o ficheiro YAML.

![Painel Sinónimos](media/power-bi-q-and-a-linguistic-schema/power-bi-synonyms-pane.png)


 A outra forma de editar um esquema linguístico é exportar e editar diretamente o ficheiro YAML.  Ao editar um ficheiro YAML de esquema linguístico, irá etiquetar as colunas na tabela como diferentes elementos gramaticais e definir as palavras que um colega poderá utilizar para formular uma pergunta. Por exemplo, indica as colunas que são o sujeito e o objeto do verbo, e adiciona palavras alternativas que os seus colegas poderão utilizar para fazer referência a tabelas, colunas e medidas no seu modelo. 

![ficheiro yaml de esquema linguístico de exemplo](media/power-bi-q-and-a-linguistic-schema/power-bi-linguistic-schema.png)

Antes de poder editar um esquema linguístico, tem de o abrir (exportar) a partir do Power BI Desktop. Quando guardar o ficheiro YAML na mesma localização, isto é considerado importação.  No entanto, também pode importar outros ficheiros YAML.  Por exemplo, se tiver um conjunto de dados semelhante e já tiver tido muito trabalho a adicionar partes do discurso, identificar relações, criar expressões e criar sinónimos. 

As Perguntas e Respostas utilizam todas estas informações juntamente com as melhorias feitas para fornecer melhores respostas, preenchimento automático e resumo das perguntas.



## <a name="edit-a-linguistic-schema"></a>Editar um esquema linguístico
Quando exporta primeiro o esquema linguístico a partir do Power BI Desktop, a maior parte ou todos os conteúdos no ficheiro são gerados automaticamente pelo motor das Perguntas e Respostas. Estas entidades, palavras (sinónimos), relações e expressões geradas são designadas com uma etiqueta **Estado: Gerado** e estão incluídas no ficheiro principalmente para fins informativos, mas podem ser um ponto de partida útil para as suas próprias alterações. 

> [!NOTE]
> O ficheiro YAML de exemplo incluído neste tutorial não contém as etiquetas **Estado: Gerado** ou **Estado: Eliminado**, uma vez que foi preparado especialmente para este tutorial. Para ver estas etiquetas, abra um ficheiro .pbix não editado na vista Relações e exporte o esquema linguístico.

![YAML que mostra Estado: Gerado](media/power-bi-q-and-a-linguistic-schema/power-bi-generated-state.png)


Quando importar o ficheiro de esquema linguístico de volta para o Power BI Desktop, o que estiver marcado como **Estado: Gerado** será na verdade ignorado (e mais tarde regenerado), por isso, se quiser fazer uma alteração aos conteúdos gerados, certifique-se de que remove também a etiqueta **Estado: Gerado** correspondente. Da mesma forma, se quiser remover conteúdos gerados, terá de alterar a etiqueta **Estado: Gerado** para **Estado: Eliminado** para que não seja gerada novamente quando importar o ficheiro de esquema linguístico.

1. Abra o conjunto de dados na vista *Relações* do Power BI Desktop. 
2. Selecione o separador **Modelação** e **Exportar esquema linguístico**.
3. Selecione o Visual Code (ou outro editor).
4. Faça as edições e guarde o ficheiro YAML.
5. No Power BI Desktop, selecione a **vista Relações > separador Modelação > Esquema Linguístico > Importar esquema linguístico**.
6. Navegue para a localização onde guardou o ficheiro YAML editado e selecione-o. Uma mensagem de êxito indica que o ficheiro YAML de esquema linguístico foi importado com êxito.

    ![Mensagem de êxito](media/power-bi-q-and-a-linguistic-schema/power-bi-success.png)

### <a name="add-phrasings-to-the-linguistic-schema"></a>Adicionar expressões ao esquema linguístico
Uma expressão é a forma como fala sobre as relações entre as coisas. Por exemplo, para descrever a relação entre clientes e produtos, pode dizer "os clientes compram produtos". Para descrever a relação entre clientes e idades, pode dizer "as idades indicam há quanto tempo são clientes". Para descrever a relação entre atletas e medalhas, pode simplesmente dizer "os atletas ganham medalhas".

Estas expressões têm várias formas e tamanhos. Algumas correspondem diretamente a relações no modelo semântico. Algumas estabelecem relações entre as colunas e as respetivas tabelas. Outras estão relacionadas com múltiplas tabelas e colunas em relações complexas. Em todos os casos, descrevem como as coisas estão relacionadas com termos de uso corrente.

## <a name="where-do-phrasings-come-from"></a>Qual a origem das expressões?
Muitas expressões simples são adicionadas automaticamente ao esquema linguístico, com base na estrutura do modelo e em alguns palpites baseados nos nomes de coluna. Por exemplo:
- A maioria das colunas é associada à respetiva tabela através de uma expressão simples, como "produtos com descrições".
- As relações do modelo resultam em expressões predefinidas para ambas as direções da relação, como "encomendas com produtos" e "produtos com encomendas".
- Algumas relações do modelo podem, com base nos respetivos nomes de coluna, obter uma expressão predefinida mais complexa, como "as encomendas são enviadas para cidades".

No entanto, existem inúmeras formas de os utilizadores falarem sobre temas que as Perguntas e Respostas não podem adivinhar. Nesse caso, pode adicionar as suas próprias expressões manualmente.


## <a name="why-should-i-add-phrasings"></a>Por que motivo devo adicionar expressões?
O primeiro motivo para adicionar uma expressão é definir um novo termo. Por exemplo, se quiser perguntar "listar os clientes mais antigos", tem primeiro de ensinar às Perguntas e Respostas o que significa "antigo". Deverá fazê-lo ao adicionar uma expressão como "as idades indicam há quanto tempo são clientes".

O segundo motivo para adicionar uma expressão é resolver a ambiguidade. Uma pesquisa por palavra-chave básica só resulta quando as palavras têm mais do que um significado. Por exemplo, "voos para Chicago" significa algo bastante diferente de "voos de Chicago", mas as Perguntas e Respostas não sabem a qual se refere, exceto se adicionar as expressões "voos de cidades de partida" e "voos para cidades de chegada". Da mesma forma, a distinção entre "carros que o João vendeu à Mariana" e "carros que o João comprou à Mariana" só será compreendida depois de adicionar as expressões "os clientes compram carros de colaboradores" e "os colaboradores vendem carros a clientes".

O último motivo para adicionar uma expressão é melhorar as reformulações. Em vez de as Perguntas e Respostas devolverem "Mostrar os clientes e os seus produtos", seria mais claro indicar "Mostrar os clientes e os produtos que compraram" ou "Mostrar os clientes e os produtos que reviram", consoante a interpretação da pergunta. A adição de expressões personalizadas permite que as reformulações sejam mais explícitas e inequívocas.


## <a name="what-kinds-of-phrasings-are-there"></a>Que tipos de expressões existem?
Para compreender os diferentes tipos de expressões, primeiro terá de se lembrar de alguns termos gramaticais muito básicos:
- Um *substantivo* é uma pessoa, local ou coisa. 
    - Exemplos: carro, adolescente, Mateus, condensador de fluxos
- Um *verbo* é uma ação ou o estado de ser. 
    - Exemplos: chocar, explodir, devorar, ejetar
- Um *adjetivo* é uma palavra descritiva que modifica um substantivo. 
    - Exemplos: poderoso, mágico, dourado, roubado
- Uma *preposição* é uma palavra utilizada antes de um substantivo para o relacionar com um substantivo, verbo ou adjetivo anterior 
    - Exemplos: de, para, próximo, do
-  Um *atributo* é uma qualidade ou funcionalidade de algo.
-  Um *nome* é uma palavra ou conjunto de palavras pelas quais uma pessoa, animal, local ou coisa é conhecida ou referida.   


## <a name="attribute-phrasings"></a>Expressões de atributo
As expressões de atributo são a base das Perguntas e Respostas, utilizadas quando uma coisa está a agir como atributo de outra coisa. São simples, diretas e fazem a maior parte do trabalho pesado quando ainda não foi definida uma expressão mais subtil e detalhada. As expressões de atributo são descritas através do verbo básico "ter" ("os produtos têm categorias" e "os países anfitriões têm cidades anfitriãs") e também permitem automaticamente fazer perguntas com as preposições "de" e "para" ("categorias de produtos", "encomendas para produtos") e possessivos ("as encomendas do João"). As expressões de atributo são utilizadas em perguntas como, por exemplo:
- Que clientes têm encomendas?
- Listar as cidades anfitriãs por país por ordem ascendente
- Mostrar as encomendas que têm chai
- Listar os clientes com encomendas
- Qual é a categoria de cada produto?
- Contar as encomendas de Samuel Costa    

A vasta maioria das expressões de atributo necessárias no seu modelo será gerada automaticamente, com base nas relações de contenção e modelo de tabela/coluna, pelo que normalmente não tem de as criar.
Segue-se um exemplo do aspeto de uma expressão de atributo dentro do esquema linguístico:

```json
product_has_category:
  Binding: {Table: Products}
  Phrasings:
  - Attribute: {Subject: product, Object: product.category}
```
 
## <a name="name-phrasings"></a>Expressões de Nome
As expressões de nome são úteis se o modelo de dados tiver uma tabela com objetos nomeados, como nomes de atletas e de clientes. Por exemplo, uma expressão "os nomes de produtos são nomes de produtos" é essencial para poder utilizar nomes de produtos em perguntas. Embora uma expressão de nome também permita "com o nome" como verbo (por exemplo, "Listar clientes com o nome Guilherme Sarmento"), é mais importante quando utilizada em conjunto com outras expressões, para permitir que um valor de nome seja utilizado para fazer referência a uma linha de tabela específica. Por exemplo, em "Clientes que compraram chai", as Perguntas e Respostas podem dizer que o valor "chai" faz referência a toda a linha da tabela de produtos, em vez de somente um valor na coluna de nomes de produto. As expressões de nome são utilizadas em perguntas como:    
- Colaboradores com o nome Samuel Costa
- Pessoas com o nome Tiago Ribeiro
- Desporto de Fernand De Montigny
- Número de atletas com o nome Mariana
- O que comprou Samuel Costa?

Partindo do princípio que utilizou uma convenção de nomenclatura pertinente para colunas de nomes no seu modelo (por exemplo, "Name" ou "ProductName" em vez de "PrdNm"), a maioria das expressões de nome necessárias no seu modelo será gerada automaticamente, pelo que normalmente não tem de as criar.

Segue-se um exemplo do aspeto de uma expressão de nome dentro do esquema linguístico:

```json
employee_has_name:
  Binding: {Table: Employees}
  Phrasings:
  - Name:
      Subject: employee
      Name: employee.name
```

 
## <a name="adjective-phrasings"></a>Expressões de adjetivo
As expressões de adjetivo definem novos adjetivos utilizados para descrever coisas no seu modelo. Por exemplo, a expressão "clientes satisfeitos são clientes em que a classificação > 6" é necessária para fazer perguntas como "listar clientes satisfeitos em Des Moines". Existem várias formas de expressões de adjetivo, para utilização em diversas situações.

As *expressões de adjetivo simples* definem um novo adjetivo com base numa condição, como "produtos descontinuados são produtos em que o estado = D". As expressões de adjetivo simples são utilizadas em perguntas como:
- Que produtos foram descontinuados?
- Listar os produtos descontinuados
- Listar os medalhistas de ouro
- Produtos que estão pendentes

Segue-se um exemplo do aspeto de uma expressão de adjetivo simples dentro do esquema linguístico: product_is_discontinued:

```json
Binding: {Table: Products}
  Conditions:
  - Target: product.discontinued
    Operator: Equals
    Value: true
  Phrasings:
  - Adjective:
      Subject: product
      Adjectives: [discontinued]
```

As *expressões de adjetivo de medição* definem um novo adjetivo com base num valor numérico que indica a extensão a que o adjetivo se aplica, como "os comprimentos indicam o comprimento dos rios" e "as pequenas regiões têm áreas terrestres pequenas". As expressões de adjetivo de medição são utilizadas em perguntas como:
- Listar os rios longos
- Quais os rios mais longos?
- Listar as regiões mais pequenas que ganharam o ouro em basquetebol
- Qual é o comprimento do Rio Grande?

Segue-se um exemplo do aspeto de uma expressão de adjetivo de medição dentro do esquema linguístico: river_has_length:

 ```json
Binding: {Table: Rivers}
  Phrasings:
  - Adjective:
      Subject: river
      Adjectives: [long]
      Antonyms: [short]
      Measurement: river.length
```

As *expressões de adjetivo dinâmicas* definem um conjunto de novos adjetivos com base nos valores numa coluna no modelo, como "as cores descrevem os produtos" e "os eventos têm géneros". As expressões de adjetivo dinâmicas são utilizadas em perguntas como:
- Listar os produtos vermelhos
- Que produtos são verdes?
- Mostrar eventos de skate para mulheres
- Número de problemas ativos

Segue-se um exemplo do aspeto de uma expressão de adjetivo dinâmica dentro do esquema linguístico: product_has_color:
```json
Binding: {Table: Products}
  Phrasings:
  - DynamicAdjective:
      Subject: product
      Adjective: product.color
```

 
## <a name="noun-phrasings"></a>Expressões de substantivo
As expressões de substantivo definem novos substantivos que descrevem subconjuntos de coisas no seu modelo. Incluem muitas vezes algum tipo de medição ou condição específica do modelo. Por exemplo, para o nosso modelo de Jogos Olímpicos, podemos adicionar expressões que distinguem os campeões dos medalhistas, os desportos com bola dos desportos aquáticos, as equipas dos individuais, categorias de idade de atletas (juvenis, adultos, séniores), etc. Para a nossa base de dados de filmes, podemos adicionar expressões de substantivo para "os falhanços são filmes em que o lucro líquido < 0" para podermos fazer perguntas como "número de falhanços por ano". Existem duas formas de expressões de substantivo, para utilização em diversas situações.

As *expressões de substantivo simples* definem um novo substantivo com base numa condição, como "os contratantes são colaboradores em que o tempo inteiro = false" e "o campeão é um atleta em que o número de medalhas > 5". As expressões de substantivo simples são utilizadas em perguntas como:

- Que colaboradores são contratantes?
- Número de contratantes em Portland
- Quantos campeões em 2016

Segue-se um exemplo do aspeto de uma expressão de substantivo simples dentro do esquema linguístico: employee_is_contractor:

```json
Binding: {Table: Employees}
  Conditions:
  - Target: employee.full_time
    Operator: Equals
    Value: false
  Phrasings:
  - Noun:
      Subject: employee
      Nouns: [contractor]
```

As *expressões de substantivo dinâmicas* definem um conjunto de novos substantivos com base nos valores numa coluna no modelo, como "os trabalhos definem os subconjuntos de colaboradores". As expressões de substantivo dinâmicas são utilizadas em perguntas como:

- Listar os caixas em Chicago
- Que colaboradores são baristas?
- Listar os árbitros em 1992

Segue-se um exemplo do aspeto de uma expressão de substantivo dinâmica dentro do esquema linguístico: employee_has_job:

 ```json
Binding: {Table: Employees}
  Phrasings:
  - DynamicNoun:
      Subject: employee
      Noun: employee.job
```

## <a name="preposition-phrasings"></a>Expressões de preposição
As expressões de preposição são utilizadas para descrever como as coisas no seu modelo estão relacionadas através de preposições. Por exemplo, uma expressão "as cidades estão em países" melhora a compreensão de perguntas como "número de cidades em Washington". Algumas expressões de preposição são criadas automaticamente quando uma coluna é reconhecida como uma entidade geográfica. As expressões de preposição são utilizadas em perguntas como:

- Número de clientes em Nova Iorque
- Listar os livros sobre linguística
- Em que cidade está John Galt?
- Quantos livros existem de Stephen Pinker?
 
Segue-se um exemplo do aspeto de uma expressão de preposição dentro do esquema linguístico: customers_are_in_cities:

 ```json
Binding: {Table: Customers}
  Phrasings:
  - Preposition:
      Subject: customer
      Prepositions: [in]
      Object: customer.city
```

 
## <a name="verb-phrasings"></a>Expressões de Verbo
As expressões de verbo são utilizadas para descrever como as relações entre os itens no seu modelo são feitas através de verbos. Por exemplo, uma expressão "os clientes compram produtos" melhora a compreensão de perguntas como "quem comprou queijo?" e "o que comprou o João?". As expressões de verbo são as mais flexíveis de todos os tipos de expressões, muitas vezes relacionadas com mais de duas coisas, como em "os colaboradores vendem produtos a clientes". As expressões de verbo são utilizadas em perguntas como, por exemplo:

- Quem vendeu o quê a quem?
- Que colaborador vendeu chai ao João?
- A Mariana vendeu chai a quantos clientes?
- Listar os produtos que a Mariana vendeu ao João.
- Que produtos descontinuados foram vendidos aos clientes de Chicago pelos colaboradores de Boston?

As expressões de verbo também podem conter expressões preposicionais, adicionadas à respetiva flexibilidade, como "os atletas ganham medalhas em competições" ou "os clientes recebem reembolsos de produtos". As expressões de verbo com expressões preposicionais são utilizadas em perguntas como:

- Quantos atletas ganharam uma medalha de ouro no Campeonato Visa?
- A que clientes foi atribuído um reembolso referente a queijo?
- Em que competição Danell Leyva ganhou uma medalha de bronze?

Algumas expressões de verbo são criadas automaticamente quando uma coluna é reconhecida como tendo um verbo e uma preposição.

Segue-se um exemplo do aspeto de uma expressão de verbo dentro do esquema linguístico: customers_buy_products_from_salespeople:

```json
Binding: {Table: Orders}
  Phrasings:
  - Verb:
      Subject: customer
      Verbs: [buy, purchase]
      Object: product
      PrepositionalPhrases:
      - Prepositions: [from]
        Object: salesperson
```

## <a name="relationships-with-multiple-phrasings"></a>Relações com múltiplas expressões
Muitas vezes, uma só relação pode ser descrita de diversas formas. Neste caso, uma só relação pode ter mais do que uma expressão. É bastante comum uma relação entre uma entidade de tabela e uma entidade de coluna ter uma expressão de atributo e outra expressão. Por exemplo, na relação entre cliente e nome do cliente, é aconselhável ter uma expressão de atributo (por exemplo, "os clientes têm nomes") e uma expressão de nome (por exemplo, "os nomes de cliente são os nomes dos clientes"), pelo que pode fazer os dois tipos de perguntas.

Segue-se um exemplo do aspeto de uma relação com duas expressões dentro do esquema linguístico: customer_has_name:

  ```json
Binding: {Table: Customers}
  Phrasings:
    - Attribute: {Subject: customer, Object: customer.name}
    - Name:
        Subject: customer
        Object: customer.name
```

Outro exemplo seria adicionar a expressão alternativa "os colaboradores vendem produtos a clientes" à relação "os clientes compram produtos a colaboradores". Tenha em atenção que não tem de adicionar variações como "os colaboradores vendem produtos **a clientes**" ou "os produtos são vendidos a clientes **por colaboradores**", uma vez que as variações "por" e "a" do sujeito e do objeto indireto são inferidas automaticamente pelas Perguntas e Respostas.

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
Se fizer uma alteração a um ficheiro .lsdl.yaml que não esteja em conformidade com o formato de esquema linguístico, verá agora traços de validação como este para indicar problemas: 

    ![yaml file showing errors](media/power-bi-q-and-a-linguistic-schema/power-bi-yaml-errors.png)


Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)
