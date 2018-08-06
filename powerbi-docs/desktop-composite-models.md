---
title: Utilizar Modelos compostos no Power BI Desktop (Pré-visualização)
description: Criar modelos de dados com várias ligações de dados e relações muitos para muitos no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/31/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: ddfe0c7ad116a74fa6887491ee41e544096de0f9
ms.sourcegitcommit: 06f59902105c93700e71e913dff8453e221e4f82
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/01/2018
ms.locfileid: "39388853"
---
# <a name="composite-models-in-power-bi-desktop-preview"></a>Modelos compostos no Power BI Desktop (Pré-visualização)

Anteriormente no **Power BI Desktop** quando utilizava um DirectQuery num relatório, nenhuma outra ligação de dados, DirectQuery ou Importação, era permitida nesse relatório. Com os **modelos compostos**, essa restrição deixa de existir e um relatório pode incluir de forma perfeita ligações de dados de mais do que um DirectQuery ou importar a ligação de dados, em qualquer combinação que escolha.

![modelos compostos no Power BI Desktop](media/desktop-composite-models/composite-models_01.png)

A capacidade **modelos compostos** no **Power BI Desktop** consiste em três funcionalidades relacionadas:

* **Modelos compostos** – permite que um relatório tenha várias ligações de dados, incluindo ligações DirectQuery ou de importação, em qualquer combinação.
* **Relações muitos para muitos** – com os **modelos compostos**, pode estabelecer **relações muitos para muitos** entre tabelas, ao remover requisitos de valores exclusivos nas tabelas e ao remover soluções alternativas anteriores, como a introdução de novas tabelas apenas para estabelecer relações. 
* **Modo de armazenamento** – agora pode especificar que elementos visuais necessitam de uma consulta às origens de dados de back-end e aqueles que não o exigem serão importados mesmo se se basearem no DirectQuery, o que melhora o desempenho e reduz a carga de back-end. Anteriormente, mesmo os elementos visuais simples como as consultas iniciadas pelas segmentações eram enviadas para as origens de back-end. 

Os três recursos relacionados dos **modelos compostos** desta coleção são descritos em artigos separados:

* Os **modelos compostos** são descritos em detalhe neste artigo.
* As **relações muitos para muitos** são descritas no seu próprio artigo: [Relações muitos para muitos no Power BI Desktop (Pré-visualização)](desktop-many-to-many-relationships.md).
* O **modo de armazenamento** é descrito no seu próprio artigo: [Modo de armazenamento no Power BI Desktop (Pré-visualização)](desktop-storage-mode.md).

## <a name="enabling-the-composite-models-preview-feature"></a>Ativar a funcionalidade de pré-visualização dos modelos compostos

A funcionalidade **modelos compostos** está em Pré-visualização e tem ser ativada no **Power BI Desktop**. Para ativar os **modelos compostos**, selecione **Ficheiro > Opções e Definições > Opções > Funcionalidades de Pré-visualização** e, em seguida, selecione a caixa de verificação **modelos compostos**. 

![ativar as funcionalidades de pré-visualização](media/desktop-composite-models/composite-models_02.png)

Terá de reiniciar o **Power BI Desktop** para que a funcionalidade seja ativada.

![reinício necessário para que as alterações entrem em vigor](media/desktop-composite-models/composite-models_03.png)


## <a name="using-composite-models"></a>Utilizar modelos compostos

Com os **modelos compostos**, pode ligar-se a todos os diversos tipos de origens de dados quando utiliza o **Power BI Desktop** ou o **serviço Power BI** e pode efetuar essas ligações de dados de formas diferentes. Pode importar dados para o Power BI, que é a forma mais comum de obtê-los ou pode ligar-se diretamente aos dados no repositório de origem original através do DirectQuery. Para saber mais sobre os detalhes do DirectQuery, veja o artigo [Utilizar o DirectQuery no Power BI](desktop-directquery-about.md).

Ao utilizar o DirectQuery, com os **modelos compostos**, é possível criar um modelo do Power BI (por exemplo, um único ficheiro. pbix do Power BI Desktop) que faz o seguinte:

* combina dados a partir de uma ou mais origens do DirectQuery e/ou
* combina dados de origens do DirectQuery e importa dados

Por exemplo, com os **modelos compostos**, é possível criar um modelo que combine dados das vendas de um armazém de dados empresarial, com dados dos objetivos de vendas que estejam numa base de dados SQL Server departamental, juntamente com alguns dados importados de uma folha de cálculo. Um modelo que combina dados de mais de uma origem do DirectQuery ou combina o DirectQuery com dados importados é designado por *modelo composto*.

> [!NOTE]
> Embora os modelos compostos estejam em pré-visualização, não é possível publicar modelos compostos no serviço Power BI. 

Pode criar relações entre as tabelas como sempre fez, até mesmo quando essas tabelas são provenientes de diferentes origens, com a seguinte restrição: todas as relações que tenham origens diferentes têm de ser definidas como tendo uma cardinalidade de **Muitos para Muitos** , independentemente da sua cardinalidade real. O comportamento de tais relações é então o mesmo que o comportamento normal para as relações **Muitos para Muitos**, conforme descrito em [Relações muitos para muitos no Power BI Desktop (Pré-visualização)](desktop-many-to-many-relationships.md). Observe que dentro do contexto dos modelos compostos, todas as tabelas importadas são, efetivamente, o única origem, independentemente da origem de dados real subjacente, da qual são, de facto, importadas.   

## <a name="example-of-using-composite-models"></a>Exemplo de utilização de modelos compostos

Como exemplo de um **modelo composto**, considere um relatório que se ligou a um armazém de dados da empresa (no SQL Server) com o DirectQuery, em que o armazém de dados contém dados de *Vendas por País*, do *Trimestre* e de *Bicicleta (Produto)*, conforme mostrado na imagem seguinte.

![vista de relações dos modelos compostos](media/desktop-composite-models/composite-models_04.png)

Neste momento, pode criar elementos visuais simples com os campos desta origem. Por exemplo, o elemento visual seguinte mostra a quantidade total de vendas por *Nome do Produto*, num trimestre selecionado. 

![elemento visual com base nos dados](media/desktop-composite-models/composite-models_05.png)

Mas, e se tivesse algumas informações sobre o Gestor de Produtos que foi atribuído a cada produto, juntamente com a prioridade de marketing, onde são mantidos esses dados numa folha de cálculo do Excel? Talvez queira ver o *Montante de Vendas* por *Gestor de Produtos*, mas adicionar estes dados locais ao armazém de dados da empresa seria provavelmente impraticável ou levar meses na melhor das hipóteses. Embora seja possível importar esses dados de vendas do armazém de dados (em vez de utilizar o DirectQuery) e, em seguida, combiná-los com os dados importados da folha de cálculo, essa abordagem não é razoável tendo em conta os motivos que levam a utilizar o DirectQuery em primeiro lugar – por exemplo, uma combinação das regras de segurança impostas na origem subjacente, a necessidade de ser capaz de ver os dados mais recentes e a enorme escala dos dados. 

É aqui que entram os **modelos compostos**. Os modelos compostos dão-lhe a opção de ligar ao armazém de dados através do DirectQuery e utilizar também GetData para origens adicionais. Neste caso, estabelecemos a ligação do DirectQuery para o armazém de dados da empresa e, em seguida, utilizamos GetData e escolhemos o Excel, navegamos para a folha de cálculo que contém os nossos dados locais e importamos a folha de cálculo que contém os *Nomes dos Produtos*, o *Gestor de Vendas* atribuído e a *Prioridade*.  

![Janela Navegador](media/desktop-composite-models/composite-models_06.png)

Agora, na lista **Campos**, vemos a tabela original *Bicicleta* (do SQL Server) e uma nova tabela *Gestores de Produtos* (com os dados importados do Excel). 

![vista Campos das tabelas](media/desktop-composite-models/composite-models_07.png)

Da mesma forma, ao observar a **Vista de Relações** no **Power BI Desktop**, agora, vemos uma tabela adicional chamada *Gestores de Produtos*. 

![vista de relações das tabelas](media/desktop-composite-models/composite-models_08.png)

Agora, precisamos de relacionar estas tabelas com as outras tabelas no modelo, o que fazemos como fizemos sempre, através da criação de uma relação entre a tabela *Bicicleta* (no SQL Server) e a tabela *Gestores de Produtos* (que é importada), como entre *Bicicleta[Nome do Produto]* e *Gestores de Produtos[Nome do Produto]*. Conforme discutido anteriormente neste artigo, todas as relações com as várias origens têm de ter cardinalidade **muitos para muitos** e, assim, essa é a cardinalidade predefinida que está selecionada. 

![caixa de diálogo Criar relação](media/desktop-composite-models/composite-models_09.png)

Depois de criar esta relação, a mesma é apresentada na **Vista de Relações** no **Power BI Desktop**, conforme esperado.

![nova vista de relações](media/desktop-composite-models/composite-models_10.png)

Com essas relações das tabelas estabelecidas, agora podemos criar elementos visuais com qualquer um dos campos na lista **Campos**, de forma totalmente integrada ao misturar dados de várias origens. Por exemplo, o elemento visual abaixo mostra o *Montante de Vendas* total de cada *Gestor de Produtos*. 

![elemento visual com painel Campos mostrado](media/desktop-composite-models/composite-models_11.png)

Este exemplo mostra um caso comum de uma tabela de *dimensão* (como *Produto* ou *Cliente*) que está a ser expandida com alguns dados adicionais importados de outro local, também é possível ter tabelas a utilizar o DirectQuery para fazer ligação a origens diferentes. Para expandirmos o nosso exemplo, imagine que *Objetivos de Vendas* por *País* e *Período* são armazenados numa base de dados departamental em separado. Pode usar **GetData** para se ligar aos dados, como faria normalmente, conforme mostrado na imagem seguinte. 

![caixa de diálogo Navegador](media/desktop-composite-models/composite-models_12.png)

Em seguida, à semelhança do fizemos anteriormente neste exemplo, podemos criar relações entre a nova tabela e as outras tabelas no modelo e criar elementos visuais que combinem os dados. Vamos examinar novamente a **Vista de Relações**, em que estabelecemos novas relações no nosso cenário de exemplo expandido.

![vista de relações com muitas tabelas](media/desktop-composite-models/composite-models_13.png)

Conforme mostrado na imagem seguinte, que se baseia nos dados novos e nas relações que acabamos de criar, o elemento visual no canto inferior esquerdo mostra o *Montante de Vendas* versus *Objetivo*, com o cálculo da variação que mostra a diferença, em que *Montante de Vendas* e *Objetivo* proveem de duas bases de dados diferentes do SQL Server. 

![elemento visual a mostrar mais dados](media/desktop-composite-models/composite-models_14.png)

## <a name="setting-storage-mode"></a>Definir o modo de armazenamento

Cada tabela num **modelo composto** tem um **modo de armazenamento** que indica se a tabela se baseia no DirectQuery ou na importação. O **modo de armazenamento** pode ser visualizado e modificado no painel **Propriedade**. Para aceder ao painel, selecione **Propriedades** na lista **Campos** do menu de contexto com o botão direito do rato. A imagem seguinte mostra o **modo de armazenamento** (abreviado para **Armazenamento...**  na imagem, devido à largura do painel).

![Definição do modo de armazenamento](media/desktop-composite-models/composite-models_15.png)

O **modo de armazenamento** também pode ser visto na descrição de cada tabela.

![descrição com o modo de armazenamento](media/desktop-composite-models/composite-models_16.png)

Para qualquer ficheiro do **Power BI Desktop** (um ficheiro .pbix) que contém algumas tabelas do DirectQuery e algumas tabelas de importação, a barra de estado apresenta um **modo de armazenamento** **Misto**. Pode clicar nesse termo na barra de estado e mudar facilmente todas as tabelas a importar.

Os detalhes sobre o **modo de armazenamento** são descritos pormenorizadamente no artigo [Modo de armazenamento no Power BI Desktop (Pré-visualização)](desktop-storage-mode.md).  

## <a name="calculated-tables"></a>Tabelas calculadas

As tabelas calculadas podem ser adicionadas a um modelo que utiliza o DirectQuery e o DAX que define a tabela calculada pode fazer referência às tabelas importadas, às tabelas DirectQuery ou a uma combinação de ambas. 

As tabelas calculadas são sempre importadas e os dados dessas tabelas são atualizados quando a tabela é atualizada. Assim, se uma tabela calculada referenciar uma tabela DirectQuery, os elementos visuais que referenciam a tabela DirectQuery mostrarão sempre os valores mais recentes na origem subjacente, mas os elementos visuais que referenciam a tabela calculada mostrarão os valores no momento em que a tabela calculada tiver sido atualizada pela última vez.

## <a name="security-implications"></a>Implicações de Segurança 

Os modelos compostos têm algumas implicações de segurança. Uma consulta enviada para uma origem de dados pode incluir valores de dados que foram obtidos de outra fonte diferente. Para o exemplo descrito anteriormente neste artigo, o elemento visual que mostra o *Montante de Vendas* por *Gestor de Produtos* resultará numa consulta SQL ser enviada para a base de dados relacional **Vendas**, sendo que essa consulta SQL pode conter os nomes dos *Gestores de Produtos* e os *Produtos* associados. 

![script a mostrar as implicações de segurança](media/desktop-composite-models/composite-models_17.png)

Por este motivo, as informações armazenadas na folha de cálculo estão agora a ser incluídas numa consulta enviada à base de dados relacional. Se estas informações forem confidenciais, deverão ser consideradas as implicações de segurança. Em particular, deve considerar as seguintes implicações:

* Qualquer administrador da base de dados que possa ver os rastreios ou os registos de auditoria será capaz de ver estas informações, mesmo que não tenha permissões para ver os dados na origem original (neste caso, permissões para o ficheiro do Excel).

* Devem considerar-se as definições de encriptação para cada origem, para evitar informações obtidas de uma origem com uma ligação encriptada e depois incluí-las inadvertidamente numa consulta enviada para outra origem com uma ligação não encriptada. 

O **Power BI Desktop** mostra uma mensagem de aviso quando se está a criar um modelo composto, para permitir a confirmação de que quaisquer implicações de segurança foram consideradas.  

Por motivos semelhantes, tem de haver um certo cuidado ao abrir um ficheiro do **Power BI Desktop** enviado de uma origem não fidedigna. Se esse ficheiro contiver modelos compostos, significa que as informações obtidas de uma origem (com as credenciais do utilizador que abre o ficheiro) serão enviadas para outra origem de dados como parte da consulta (sendo que, possivelmente, poderão ser vistas pelo autor mal-intencionado do ficheiro do Power BI Desktop). Portanto, ao abrir um ficheiro do Power BI Desktop pela primeira vez, se o mesmo contiver várias fontes, será apresentado um aviso. Este aviso é parecido com o aviso apresentado quando abre um ficheiro que contém consultas SQL nativas.  

## <a name="performance-implications"></a>Implicações de Desempenho  

Quando utilizar o DirectQuery, deve sempre considerar o desempenho, principalmente para garantir que a origem de back-end tem recursos suficientes para proporcionar uma boa experiência aos utilizadores. Uma boa experiência significa que os elementos visuais devem ser atualizados no espaço de cinco segundos ou menos. Também deve seguir o conselho de desempenho apresentado no artigo [Utilizar o DirectQuery no Power BI](desktop-directquery-about.md). A utilização de modelos compostos traz considerações de desempenho adicionais, uma vez que um único elemento visual pode resultar no envio de consultas a várias origens e, muitas vezes, passar os resultados de uma consulta para uma segunda origem. Esta situação pode resultar nas seguintes formas de execução possíveis:

* **Uma consulta SQL que inclui um grande número de valores literais** – por exemplo, um elemento visual que pede o *Montante de Vendas* total (da base de dados SQL) a um conjunto de *Gestores de Produtos* selecionado (da tabela relacionada que foi importada de uma folha de cálculo) precisaria primeiro de encontrar quais os *Produtos* geridos por esses Gestores de Produtos, antes de enviar uma consulta SQL que incluísse todos os IDs de produto numa cláusula *WHERE*.

* **Uma consulta SQL que consulta num nível inferior de granularidade, com os dados a serem agregados localmente** – usando o mesmo exemplo apresentado no item de marca anterior nesta lista, como o número de *Produtos* que corresponde ao filtro em *Gestor de Produtos* se torna muito grande, a certo ponto, torna-se ineficaz ou é pouco exequível incluí-los a todos numa cláusula *WHERE*. Em vez disso, é necessário consultar a origem relacional no nível mais baixo de *Produto* e, em seguida, agregar localmente os resultados. Se a cardinalidade de *Produtos* exceder o limite de um milhão, a consulta falhará.

* **Várias consultas SQL, uma por grupo e por valor** – quando a agregação utiliza **Contagem Distinta**, agrupada por algumas colunas de outra origem, se a origem externa não suportar a passagem eficiente de muitos valores literais que definem o agrupamento, será necessário enviar uma consulta SQL por grupo e por valor. Por exemplo, um elemento visual a solicitar uma contagem distinta do *Número de Conta de Cliente* (da tabela do SQL Server) por *Gestor de Produtos* (da tabela relacionada importada de uma folha de cálculo) teria de passar os detalhes da tabela *Gestor de Produtos* na consulta enviada para o SQL Server. Noutras origens, por exemplo, Redshift, isso não é viável e haveria antes uma consulta SQL enviada por *Gestor de Vendas* (até um limite prático, altura em que a consulta falha). 

Cada um desses casos tem as próprias implicações no desempenho, com os detalhes exatos a serem diferentes para cada origem de dados. Uma boa regra prática é que, enquanto a cardinalidade das colunas utilizadas na relação de associação de duas origens continua a ser baixa (alguns milhares), o desempenho não deve ser afetado significativamente. À medida que aumenta esta cardinalidade, tem de ter-se mais em consideração o impacto sobre o desempenho resultante. 

Além disso, a utilização de relações **muitos para muitos** significa que consultas separadas têm de ser enviadas para a origem subjacente para cada nível de total/subtotal, em vez de agregar os valores detalhados localmente. Como tal, um elemento visual de tabela simples com totais enviaria duas consultas SQL, em vez de uma. 

## <a name="limitations-and-considerations"></a>Limitações e considerações

Existem algumas limitações nesta versão dos **modelos compostos**.

As seguintes origens multidimensionais não podem ser utilizadas com **modelos compostos**:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Conjuntos de dados do Power BI

Ao ligar-se a essas origens multidimensionais através do DirectQuery, também não poderá ligar-se à outra origem do DirectQuery nem combinar com dados importados.

As limitações existentes da utilização do DirectQuery ainda se aplicam ao utilizar os **modelos compostos**. Muitas destas limitações são agora por tabela, de acordo com o **modo de armazenamento** da tabela. Por exemplo, uma coluna calculada numa tabela importada pode referir-se a outras tabelas, mas uma coluna calculada numa tabela DirectQuery está restrita a referir-se apenas às colunas na mesma tabela. As outras limitações aplicar-se-ão ao modelo como um todo se qualquer uma das tabelas no modelo for DirectQuery. Por exemplo, as funcionalidades **QuickInsights** e **Perguntas e Respostas** não estarão disponíveis nos modelos se qualquer uma das tabelas dentro dos mesmos tiverem um **modo de armazenamento** do DirectQuery. 

## <a name="next-steps"></a>Próximos passos

Os artigos seguintes descrevem de forma mais detalhada os modelos compostos e o DirectQuery.

* [Relações muitos para muitos no Power BI Desktop (Pré-visualização)](desktop-many-to-many-relationships.md)
* [Modo de armazenamento no Power BI Desktop (Pré-visualização)](desktop-storage-mode.md)

Artigos do DirectQuery:

* [Utilizar o DirectQuery no Power BI](desktop-directquery-about.md)
* [Origens de dados suportadas pelo DirectQuery no Power BI](desktop-directquery-data-sources.md)

