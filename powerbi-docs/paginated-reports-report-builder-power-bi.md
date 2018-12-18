---
title: O que são relatórios paginados no Power BI Premium? (Pré-visualização)
description: Os relatórios paginados, que são há muito o formato de relatório padrão no SQL Server Reporting Services, estão agora disponíveis no serviço Power BI. Estes relatórios podem ser impressos ou partilhados. Pode controlar o esquema do relatório com exatidão. Os relatórios paginados apresentam todos os dados numa tabela, por exemplo, mesmo que a tabela se estenda por várias páginas.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: report-builder
ms.topic: overview
ms.date: 12/05/2018
ms.author: maggies
ms.openlocfilehash: d79299f469062ec74c49ff4b7e9edda26c3409a3
ms.sourcegitcommit: 72c9d9ec26e17e94fccb9c5a24301028cebcdeb5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53026133"
---
# <a name="what-are-paginated-reports-in-power-bi-premium-preview"></a>O que são relatórios paginados no Power BI Premium? (Pré-visualização)
Os relatórios paginados, que são há muito o formato de relatório padrão no SQL Server Reporting Services, estão agora disponíveis no serviço Power BI. Estes relatórios podem ser impressos ou partilhados. Os relatórios são designados "paginados" porque são formatados para se ajustarem a uma página. Os relatórios paginados apresentam todos os dados numa tabela, mesmo que a tabela ocupe múltiplas páginas. Às vezes são chamados “imagem perfeita”, uma vez que pode controlar o esquema de página do relatório com exatidão. Os relatórios paginados baseiam-se na tecnologia de relatório RDL do SQL Server Reporting Services. O Report Builder é a ferramenta autónoma para a criação de relatórios paginados. 

Os relatórios paginados podem ter muitas páginas. Por exemplo, este relatório tem 563 páginas. Cada página está disposta com exatidão, com uma página por fatura e cabeçalhos e rodapés repetidos.

![Relatório paginado no serviço Power BI](media/paginated-reports-report-builder-power-bi/power-bi-paginated-wwi-report-page.png)

Pode visualizar o relatório no Report Builder e, em seguida, publicá-lo no serviço Power BI, http://app.powerbi.com. Precisa de uma licença do Power BI Pro para publicar um relatório no serviço. Pode publicar e partilhar relatórios paginados em A Minha Área de Trabalho ou nas áreas de trabalho da aplicação, desde que a área de trabalho esteja numa capacidade do Power BI Premium. Além disso, um administrador do Power BI tem de ativar os relatórios paginados no portal de administração do Power BI. Saiba mais sobre a [configuração de cargas de trabalho](service-admin-premium-manage.md#configure-workloads). 

## <a name="create-reports-in-report-builder"></a>Criar relatórios no Report Builder

Os relatórios paginados têm a sua própria ferramenta de criação, o Report Builder. É a mesma ferramenta e versão utilizada para criar relatórios paginados para o Power BI Report Server ou para o SQL Server Reporting Services (SSRS). Na verdade, os relatórios paginados que criar para o SSRS 2016 e 2017 ou para o Power BI Report Server no local, são compatíveis com o serviço Power BI. O serviço Power BI mantém a retrocompatibilidade, pelo que pode mudar os relatórios para a versão mais recente e pode atualizar os relatórios paginados de qualquer versão anterior. Nem todas as funcionalidades de relatórios estão disponíveis no lançamento. Veja a secção [Limitações e considerações](#limitations-and-considerations) neste artigo para obter detalhes.
     
## <a name="report-from-a-variety-of-data-sources"></a>Relatório de diversas origens de dados

Um único relatório paginado pode ter uma série de origens de dados diferentes, não tem um modelo de dados subjacente, ao contrário dos relatórios do Power BI. Para a versão inicial dos relatórios paginados no serviço Power BI, irá criar origens de dados e conjuntos de dados incorporados no relatório propriamente dito. Por agora, não pode utilizar conjuntos de dados partilhados ou origens de dados partilhadas. Vai criar os relatórios no Report Builder no computador local. Se um relatório ligar a dados no local, depois de carregar o relatório no serviço Power BI, terá de criar um gateway e redirecionar a ligação de dados. Veja a seguir as origens de dados a que pode ligar para a versão inicial:

- Base de Dados SQL do Azure e Azure SQL Data Warehouse
- SQL Server através de um gateway
- SQL Server Analysis Services através de um gateway
 
Estarão disponíveis mais origens de dados durante o período de pré-visualização.

## <a name="design-your-report"></a>Criar o relatório  

### <a name="create-paginated-reports-with-matrix-chart-and-free-form-layouts"></a>Criar relatórios paginados com matriz, gráfico e esquemas de forma livre

Os relatórios de tabela funcionam bem para dados baseados em colunas. Os relatórios de matriz, como relatórios de referência cruzada ou de Tabela Dinâmica, são ideais para dados resumidos. Os relatórios de gráfico apresentam dados num formato gráfico e os relatórios de *lista* de forma livre podem apresentar quase todos os dados, como faturas. 
  
Pode começar com um dos assistentes do Report Builder. Os Assistentes de tabelas, de matrizes e de gráficos vão guiá-lo durante a criação da ligação à origem de dados incorporada e ao conjunto de dados incorporado. Em seguida, vai arrastar e largar os campos para criar uma consulta de conjunto de dados, selecionar um esquema e estilo e personalizar o relatório.  
  
Com o Assistente de mapas, vai criar relatórios que apresentam dados agregados sobre um fundo geográfico ou geométrico. Os dados dos mapas podem ser dados geográficos de uma consulta Transact-SQL ou um ficheiro de formas do Environmental Systems Research Institute, Inc. (ESRI). Também pode adicionar um fundo do mosaico de mapa do Microsoft Bing.  

### <a name="add-more-to-your-report"></a>Adicionar mais elementos ao relatório

Modifique os dados ao filtrar, agrupar e classificar os dados ou ao adicionar fórmulas ou expressões. Adicione gráficos, medidores, gráficos sparkline e indicadores para resumir os dados num formato visual.  Utilize parâmetros e filtros para filtrar dados para vistas personalizadas. Incorpore ou referencie imagens e outros recursos, incluindo conteúdo externo.  

Tudo num relatório paginado, desde o próprio relatório a cada caixa de texto, imagem, tabela e gráfico, tem um conjunto de propriedades que pode definir para que o relatório tenha exatamente o aspeto que pretende.

## <a name="creating-a-report-definition"></a>Criar uma definição do relatório

Quando cria um relatório paginado, está, na realidade, a criar uma *definição do relatório*, ou seja, não contém os dados, especifica onde obter os dados, quais os dados a obter e como apresentar os dados. Quando executar o relatório, o processador do relatório utiliza a definição do relatório que especificou, obtém os dados e combina-os com o esquema de relatório para gerar o relatório. Carregue a definição do relatório no serviço Power BI, http://app.powerbi.com, ou em A Minha Área de Trabalho ou numa área de trabalho partilhada com os seus colegas. Se a origem de dados do relatório for no local, depois de carregar o relatório, deverá redirecionar a ligação da origem de dados para passar por um gateway. 

## <a name="view-your-paginated-report"></a>Visualizar o relatório paginado
Pode ver o relatório paginado no serviço Power BI num browser e também nas aplicações móveis do Power BI. No serviço Power BI, pode exportar o relatório para uma série de formatos, tais como HTML, MHTML, PDF, XML, CSV, TIFF, Word e Excel. Também pode partilhá-lo com outras pessoas.  
  
## <a name="limitations-and-considerations"></a>Limitações e considerações

Apresentamos a seguir mais algumas funcionalidades que não são suportadas na versão inicial:

- Afixar páginas de relatórios ou elementos visuais em dashboards do Power BI. Pode ainda afixar visualizações a um dashboard do Power BI a partir de um relatório paginado no local num servidor de relatórios do Power BI Report Server ou do Reporting Services. Veja [Afixar itens do Reporting Services nos dashboards do Power BI](https://docs.microsoft.com/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards) para obter mais informações.
- Funcionalidades interativas como mapas de documentos e os botões mostrar/ocultar.
- Sub-relatórios e relatórios de pormenorização.
- Subscrições.
- Origens de dados partilhadas e conjuntos de dados partilhados.
- Conjuntos de dados do Power BI.
- Elementos visuais de relatórios do Power BI.
- Relatórios paginados nas aplicações. Pode partilhar um relatório paginado de uma área de trabalho de aplicação, mas não pode inclui-lo quando publicar a aplicação a partir dessa área de trabalho.
 
## <a name="next-steps"></a>Próximos passos

- [Instalar o Report Builder a partir do Centro de Transferências da Microsoft](http://go.microsoft.com/fwlink/?LinkID=734968)
- [Tutorial: Criar um relatório paginado](paginated-reports-quickstart-aw.md)
- [Introduzir dados diretamente num relatório paginado](paginated-reports-enter-data.md)

  

