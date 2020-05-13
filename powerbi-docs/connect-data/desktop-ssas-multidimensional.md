---
title: Dados multidimensionais do Analysis Services no Power BI Desktop
description: Dados multidimensionais do SQL Server Analysis Services (SSAS) no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: eac1134ff12025d05cd59e86b7538cde58e3a2ee
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83287700"
---
# <a name="connect-to-ssas-multidimensional-models-in-power-bi-desktop"></a>Ligar a modelos multidimensionais do SSAS no Power BI Desktop

Com o Power BI Desktop, pode aceder a *modelos multidimensionais do SSAS*, normalmente denominados *SSAS MD*.

Para ligar a uma base de dados SSAS MD, selecione **Obter Dados**, selecione **Base de dados** > **Base de dados do SQL Server Analysis Services** e, em seguida, selecione **Ligar**:

![Base de dados do SQL Server Analysis Services (SSAS), caixa de diálogo Obter Dados, Power BI Desktop](media/desktop-ssas-multidimensional/ssas-multidimensional-2.png)

O serviço Power BI e o Power BI Desktop suportam os modelos multidimensionais do SASS no modo de ligação em direto. Pode publicar e carregar relatórios que utilizam **modelos multidimensionais do SSAS** no modo Em direto no serviço Power BI.

## <a name="capabilities-and-features-of-ssas-md"></a>Funcionalidades e capacidades do SSAS MD

As secções a seguir descrevem as funcionalidades e capacidades das ligações do Power BI e SSAS MD.

### <a name="tabular-metadata-of-multidimensional-models"></a>Metadados tabulares de modelos multidimensionais

A tabela a seguir mostra a correspondência entre objetos multidimensionais e os metadados tabulares que são devolvidos ao Power BI Desktop. O Power BI consulta o modelo para encontrar metadados tabulares. Com base nos metadados devolvidos, o Power BI Desktop executa consultas DAX adequadas no SSAS quando cria uma visualização (como uma tabela, matriz, gráfico ou segmentação de dados).

| Objeto multidimensional de BISM | Metadados tabulares |
| --- | --- |
| Cubo |Modelo |
| Dimensão do cubo |Tabela |
| Atributos de dimensão (chaves), nome |Colunas |
| Grupo de medidas |Tabela |
| Medida |Medida |
| Medidas sem grupo de medidas associado |Na tabela chamada *Medidas* |
| Grupo de medidas -> Relação da dimensão do cubo |Relação |
| Perspetiva |Perspetiva |
| KPI |KPI |
| Hierarquias utilizador/principal-subordinado |Hierarquias |

### <a name="measures-measure-groups-and-kpis"></a>Medidas, grupos de medidas e KPIs

Os grupos de medidas num cubo multidimensional estão expostos como tabelas com o símbolo sigma (∑) ao lado, no painel **Campos**. As medidas calculadas sem um grupo de medidas associadas são agrupadas numa tabela especial, denominada *Medidas*, nos metadados da tabela.

Para ajudar a simplificar modelos complexos num modelo multidimensional, pode definir um conjunto de medidas ou KPIs num cubo a ser localizado dentro de uma *pasta de apresentação*. O Power BI reconhece as pastas de apresentação nos metadados tabulares e mostra as medidas e KPIs dentro das pastas de apresentação. Os KPIs em bases de dados multidimensionais suportam *Valor*, *Objetivo*, *Gráfico de Estado* e *Gráfico de Tendência*.

### <a name="dimension-attribute-type"></a>Tipo de atributo de dimensão

Os modelos multidimensionais também suportam a associação de atributos de dimensão com tipos de atributo de dimensão específicos. Por exemplo, uma dimensão **Geografia**, onde os atributos de dimensão *Cidade*, *Estado-Distrito*, *País* e *Código Postal* têm tipos geográficos adequados associados são expostos nos metadados da tabela. O Power BI reconhece os metadados, permitindo a criação de visualizações de mapa. Irá reconhecer estas associações pelo ícone de *mapa* junto ao elemento no painel de **Campo** no Power BI.

O Power BI também pode compor imagens quando fornece um campo que contém os URLs (Uniform Resource Locators) das imagens. Pode especificar estes campos como tipos *ImageURL* no SQL Server Data Tools (ou no Power BI). As informações de tipo são depois fornecidas ao Power BI nos metadados tabulares. O Power BI pode recuperar essas imagens através do URL e apresentá-las em elementos visuais.

### <a name="parent-child-hierarchies"></a>Hierarquias principal-subordinado

Os modelos multidimensionais suportam hierarquias principal-subordinado, que são apresentadas como uma *hierarquia* nos metadados da tabela. Cada nível da hierarquia principal-subordinado é exposto como uma coluna oculta nos metadados tabulares. O atributo chave da dimensão principal-subordinado não é exposto nos metadados tabulares.

### <a name="dimension-calculated-members"></a>Membros calculados da dimensão

Os modelos multidimensionais suportam a criação de vários tipos de *membros calculados*. Os dois tipos mais comuns de membros calculados são:

* Membros calculados em hierarquias de atributos que não são colaterais de *Todos*
* Membros calculados em hierarquias de utilizador

O modelo multidimensional expõe *membros calculados em hierarquias de atributo* como valores de uma coluna. Tem algumas opções e restrições adicionais se expuser este tipo de membro calculado:

* Um atributo de dimensão pode ter um *UnknownMember* opcional.

* Um atributo com membros calculados não pode ser o atributo chave da dimensão, a menos que seja o único atributo da dimensão.

* Um atributo com membros calculados não pode ser um atributo principal-subordinado.

Os membros calculados de hierarquias de utilizador não são expostos no Power BI. Em alternativa, pode ligar a um cubo que contenha membros calculados em hierarquias de utilizadores. No entanto, não poderá ver os membros calculados se estes não cumprirem as restrições que mencionámos na lista anterior.

### <a name="security"></a>Segurança

Os modelos multidimensionais suportam a segurança ao nível da dimensão e da célula por meio de *funções*. Ao ligar-se a um cubo com o Power BI, é autenticado e avaliado quanto às permissões apropriadas. Se um utilizador tiver a *segurança de dimensão* aplicada, os respetivos membros da dimensão não são vistos pelo utilizador no Power BI. No entanto, quando um utilizador tem uma permissão de *segurança da célula* definida, em que determinadas células são restritas, esse utilizador não pode ligar ao cubo com o Power BI.

## <a name="considerations-and-limitations"></a>Considerações e limitações

Existem algumas limitações na utilização do SSAS MD:

* Apenas as edições Enterprise e BI do SQL Server 2014 suportam ligações em direto. Para a edição padrão do SQL Server, é necessário o SQL Server 2016 ou posterior para ligações em direto.

* As *Ações* e os *conjuntos com nome* não são expostos ao Power BI. Para criar elementos visuais e relatórios, pode continuar a ligar a cubos que também contêm ações ou conjuntos com nome.

* Quando o Power BI apresenta os metadados de um modelo SSAS, por vezes não é possível obter dados do modelo. Este cenário pode ocorrer se tiver instalado a versão de 32 bits do fornecedor MSOLAP, mas não a versão de 64 bits. Instalar a versão de 64 bits poderá resolver o problema.

* Não pode criar medidas ao *nível de relatório* ao criar um relatório ligado em tempo real a um modelo SSAS multidimensional. As únicas medidas disponíveis são as definidas no modelo MD.

## <a name="supported-features-of-ssas-md-in-power-bi-desktop"></a>Funcionalidades com Suporte do SSAS MD no Power BI Desktop

O consumo dos seguintes elementos é suportado nesta versão do SSAS MD. Para obter mais informações sobre estas funcionalidades, veja [Compreender a vista avançada para modelos multidimensionais](/sql/analysis-services/multidimensional-models/understanding-power-view-for-multidimensional-models?view=sql-server-2014).

* Membros predefinidos
* Atributos de dimensão
* Tipos de atributo de dimensão
* Membros calculados da dimensão, que:
  * Tem de ser um membro real único quando a dimensão tiver mais do que um atributo.
  * Não pode ser o atributo principal da dimensão, a menos que seja o único atributo.
  * Não pode ser um atributo principal-subordinado.
* Segurança da dimensão
* Mostrar pastas
* Hierarquias
* ImageUrls
* KPIs
* Tendências de KPI
* Medidas (com ou sem grupos de medidas)
* Medidas como variantes

## <a name="troubleshooting"></a>Resolução de problemas

A lista seguinte descreve todos os problemas conhecidos ao ligar-se ao SQL Server Analysis Services (SSAS).

* **Erro: Não foi possível carregar o esquema do modelo**. Normalmente, este erro ocorre quando o utilizador que se liga ao Analysis Services não tem acesso à base de dados/cubo.
