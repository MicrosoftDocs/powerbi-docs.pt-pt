---
title: Adicionar um filtro de relatório
description: Como adicionar um filtro a um relatório no serviço Power BI para consumidores
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/19/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 31b3584b0cbd2481db64160bcf502caf46e7acc3
ms.sourcegitcommit: 2c4a075fe16ccac8e25f7ca0b40d404eacb49f6d
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/20/2018
ms.locfileid: "49473813"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Fazer uma visita do painel Filtros
Este artigo analisa o painel Filtros de relatórios no serviço Power BI.

Existem diversas formas de filtrar dados no Power BI e recomendamos que comece por ler [Sobre os filtros e o realce](../power-bi-reports-filters-and-highlighting.md).

![relatório no browser](media/end-user-report-filter/power-bi-browser.png)

## <a name="working-with-the-report-filters-pane"></a>Trabalhar com o painel Filtros
Quando um colega partilha um relatório consigo, verifique o painel **Filtros**. Por vezes, é encolhido ao longo da margem direita do relatório. Selecione-o para expandi-lo.   

![relatório no browser](media/end-user-report-filter/power-bi-expanded.png)

O painel Filtros contém filtros que foram adicionados ao relatório pelo *designer* do relatório. Os *consumidores* como você, podem interagir com os filtros e guardar as suas alterações, mas não podem adicionar novos filtros ao relatório. Por exemplo, na captura de ecrã acima, o estruturador adicionou dois filtros de nível de página: Segment (Segmento) e Year (Ano). Pode interagir com estes filtros e alterá-los, mas não pode adicionar um terceiro filtro de nível de página.

No serviço Power BI, os relatórios mantêm todas as alterações que fizer no painel Filtros e essas alterações transitam para a versão para dispositivos móveis do relatório. Para repor o painel Filtros para as predefinições do designer, selecione **Repor para predefinição** na barra de menus superior.     

## <a name="open-the-filters-pane"></a>Abrir o painel Filtros
Quando um relatório está aberto, o painel Filtros é apresentado no lado direito da tela de relatórios. Se não vir o painel, selecione a seta no canto superior direito para expandi-la.  

Neste exemplo selecionámos um visual com 6 filtros. A página de relatórios também tem filtros, listados no cabeçalho **Filtros de nível de página**. Há um [Filtro de pormenorização](../power-bi-report-add-filter.md) e o relatório completo tem também um filtro: **FiscalYear** is 2013 or 2014 (Ano Fiscal é 2013 ou 2014).

![lista de campos](media/end-user-report-filter/power-bi-filter-list.png)

Alguns dos filtros têm a palavra **Tudo** junto aos mesmos, o que significa que todos os valores estão incluídos no filtro.  Por exemplo, na captura de ecrã acima, **Chain (All)** (Cadeia [Tudo]) indica-nos que esta página de relatório inclui dados sobre todas as cadeias de lojas.  Por outro lado, o filtro ao nível de relatório de **FiscalYear is 2013 or 2014** indica que o relatório inclui apenas dados correspondentes aos anos fiscais de 2013 e 2014.

Qualquer pessoa a ver este relatório pode interagir com estes filtros.

- Pesquise na página, no elemento visual, no relatório e nos filtros de pormenorização para localizar e selecionar o valor pretendido. 

    ![Pesquisar num filtro](media/end-user-report-filter/power-bi-filter-search.png)

- Veja os detalhes do filtro ao pairar o rato e selecionar a seta junto ao filtro.
  
   ![mostra Lindseys selecionado](media/end-user-report-filter/power-bi-expan-filter.png)
* Altere o filtro, por exemplo, altere **Lindseys** para **Fashions Direct**.
  
     ![Mostra Fashions Direct selecionado](media/end-user-report-filter/power-bi-filter-chain.png)

* Reponha os filtros para o seu estado original ao selecionar **Repor para predefinição** na barra de menus superior.    
    ![repor para predefinição](media/end-user-report-filter/power-bi-reset-to-default.png)
    
* Elimine o filtro ao selecionar o **x** junto ao nome do filtro.
  
    ![x realçado](media/end-user-report-filter/power-bi-delete-filter.png)

  Eliminar um filtro remove-o da lista, mas não elimina os dados do relatório.  Por exemplo, se eliminar **FiscalYear is 2013 or 2014** (Ano Fiscal é 2013 ou 2014), os dados do ano fiscal permanecerão no relatório, mas já não serão filtrados para mostrar apenas 2013 e 2014; irão mostrar todos os anos fiscais que os dados contêm.  No entanto, após eliminar o filtro, não poderá modificá-lo novamente, uma vez que foi removido da lista. Uma opção melhor é limpar o filtro ao selecionar o ícone da borracha ![ícone da borracha](media/end-user-report-filter/power-bi-eraser-icon.png).
  
  



## <a name="clear-a-filter"></a>Limpar um filtro
 No modo de filtragem avançado ou básico, selecione o ícone da borracha  ![ícone da borracha](media/end-user-report-filter/pbi_erasericon.jpg) para limpar o filtro. 


## <a name="types-of-filters-text-field-filters"></a>Tipos de filtros: filtros de campo de texto
### <a name="list-mode"></a>Modo de lista
Marcar uma caixa de verificação ou seleciona ou deseleciona o valor. A caixa de verificação **Tudo** pode ser utilizada para ativar ou desativar o estado de todas as caixas de verificação. As caixas de verificação representam todos os valores disponíveis para esse campo.  À medida que ajusta o filtro, a reformulação é ajustada para refletir as suas escolhas. 

![filtro de modo de lista](media/end-user-report-filter/power-bi-restatement-new.png)

Observe como a reformulação agora indica "is Mar, Apr or May" (é Mar, Abr ou Mai).

### <a name="advanced-mode"></a>Modo avançado
Selecione **Filtragem Avançada** para mudar para o modo avançado. Utilize os controlos de lista pendente e as caixas de texto para identificar quais campos serão incluídos. Ao escolher entre **And** (E) e **Or** (Ou), pode criar expressões de filtros complexas. Selecione o botão **Aplicar Filtro** quando tiver definido os valores pretendidos.  

![modo avançado](media/end-user-report-filter/power-bi-advanced.png)

## <a name="types-of-filters-numeric-field-filters"></a>Tipos de filtros: filtros de campo numérico
### <a name="list-mode"></a>Modo de lista
Se os valores forem finitos, selecionar o nome do campo apresenta uma lista.  Consulte **Filtros de campos de texto** &gt; **Modo de lista** acima para obter ajuda na utilização de caixas de verificação.   

### <a name="advanced-mode"></a>Modo avançado
Se os valores forem infinitos ou representarem um intervalo, selecionar o nome do campo abre o modo de filtro avançado. Utilize a lista pendente e as caixas de texto para especificar o intervalo de valores que pretende ver. 

![filtragem avançada](media/end-user-report-filter/power-bi-dropdown-and-text.png)

Ao escolher entre **And** (E) e **Or** (Ou), pode criar expressões de filtros complexas. Selecione o botão **Aplicar Filtro** quando tiver definido os valores pretendidos.

## <a name="types-of-filters-date-and-time"></a>Tipos de filtros: data e hora
### <a name="list-mode"></a>Modo de lista
Se os valores forem finitos, selecionar o nome do campo apresenta uma lista.  Consulte **Filtros de campos de texto** &gt; **Modo de lista** acima para obter ajuda na utilização de caixas de verificação.   

### <a name="advanced-mode"></a>Modo avançado
Se os valores de campo representarem a data ou hora, pode especificar uma hora de início/fim quando utilizar os filtros de Data/Hora.  

![filtro datetime](media/end-user-report-filter/pbi_date-time-filters.png)


## <a name="next-steps"></a>Próximos passos
[Saiba como os elementos visuais de relatórios realizam filtragem cruzada e realce cruzado entre si numa página de relatório](end-user-interactions.md)