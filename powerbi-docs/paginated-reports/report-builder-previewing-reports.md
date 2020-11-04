---
title: Pré-visualização de relatórios no Report Builder do Power BI
description: Ao criar um relatório paginado do Report Builder, é útil pré-visualizar frequentemente o relatório para verificar se este apresenta aquilo que pretende.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: ba6b5bdd-d8c6-4aa8-ba32-3a10b11969d4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b12937ec758202345166e520397a52e52b67165d
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/04/2020
ms.locfileid: "93298161"
---
# <a name="previewing-reports-in-power-bi-report-builder"></a>Pré-visualização de relatórios no Report Builder do Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Ao criar um relatório paginado do Report Builder, é útil pré-visualizar frequentemente o relatório para verificar se este apresenta aquilo que pretende. Para pré-visualizar o relatório, clique em **Executar**. O relatório é apresentado no modo de pré-visualização.  
  
 O Report Builder melhora a experiência de pré-visualização através de sessões de edição quando ligado a um servidor de relatórios. A sessão de edição cria uma cache de dados e disponibiliza os conjuntos de dados na cache para pré-visualizações de relatórios repetidas. Uma sessão de edição não é uma funcionalidade com a qual interaja diretamente, mas compreender quando o conjunto de dados em cache é atualizado irá ajudá-lo a melhorar o desempenho sempre que pré-visualizar um relatório e compreender porque é que o relatório demora mais ou menos tempo a ser apresentado.  

  
> [!NOTE]  
> Existem algumas diferenças entre pré-visualizar no Report Builder e ver num browser. Por exemplo, um controlo de calendário, que é adicionado a um relatório ao especificar um parâmetro de tipo de data/hora, é diferente no Report Builder e num browser. 
  
## <a name="improving-preview-performance"></a>Melhorar o desempenho de pré-visualização  
 O modo como cria e atualiza relatórios afeta a rapidez com que o relatório é apresentado em pré-visualização. A primeira vez que pré-visualiza um relatório que se baseia numa referência de servidor, é criada uma sessão de edição para si e os dados utilizados quando o relatório é executado são adicionados a uma cache de dados que está armazenada. Quando fizer alterações ao relatório que não afetem os dados, a cópia em cache dos dados será utilizada pelo relatório. Isso significa que não verá a alteração de dados sempre que pré-visualizar o relatório. Se quiser novos dados, clique no botão **Atualizar** no friso.  
  
 As seguintes ações fazem com que a cache seja atualizada e atrasem a apresentação do relatório da próxima vez que pré-visualizar o relatório:  
  
-   Adicionar, alterar ou eliminar um conjunto de dados. O conjunto de dados em cache contém todos os conjuntos de dados que um relatório utiliza e a modificação de qualquer conjunto de dados invalida o conjunto de dados em cache. Isto inclui a alteração do nome, consulta ou campos no conjunto de dados.  
  
    > [!NOTE]  
    >  Se o conjunto de dados tiver um grande número de campos que não espera utilizar, deve considerar atualizar o conjunto de dados para omitir esses campos. Embora isto crie uma nova sessão de edição e a primeira pré-visualização do relatório seja mais lenta, o conjunto de dados em cache beneficia principalmente o desempenho do servidor de relatórios.  
  
-   Adicionar, alterar ou eliminar uma origem de dados. Isto inclui alterar o nome ou as propriedades da origem de dados, a extensão de dados da origem de dados ou as propriedades da ligação à origem de dados.  
  
-   Alterar a origem de dados que o relatório utiliza para uma origem de dados diferente.  
  
-   Alterar o idioma do relatório.  
  
-   Alterar as assemblagens ou personalizar o código que o relatório utiliza.  
  
-   Adicionar, alterar ou eliminar os parâmetros de consulta nos valores de parâmetro ou relatório.  
  
 As alterações no esquema do relatório e na formatação de dados não afetam o conjunto de dados em cache. Pode realizar as seguintes ações sem atualizar o conjunto de dados em cache:  
  
-   Adicionar ou remover regiões de dados, como tabelas, matrizes ou gráficos.  
  
-   Adicionar ou eliminar colunas a partir do relatório. Todos os campos do conjunto de dados estão disponíveis para utilizar no relatório. Adicionar ou remover campos no relatório não tem qualquer efeito no conjunto de dados.  
  
-   Alterar a ordem dos campos em tabelas e matrizes.  
  
-   Adicionar, alterar ou eliminar grupos de colunas e linhas.  
  
-   Adicionar, alterar ou eliminar a formatação dos valores de dados nos campos.  
  
-   Adicionar, alterar ou eliminar imagens, linhas ou caixas de texto.  
  
-   Alterar as quebras de página.  
  
A sessão de edição é criada pela primeira vez que pré-visualizar um relatório. Por predefinição, uma sessão de edição dura 7200 segundos (2 horas). A sessão é reposta para as duas horas, sempre que executar o relatório. Quando a sessão de edição expirar, a cache de dados é eliminada. Se a sessão de edição expirar, voltará a ser criada uma automaticamente na próxima vez que pré-visualizar o relatório.
  
Por predefinição, a cache de dados pode conter até cinco conjuntos de dados. Se utilizar muitas combinações diferentes de valores de parâmetros, o relatório poderá precisar de mais dados. Isto requer que a cache seja atualizada e o relatório seja apresentado mais lentamente na próxima vez que o pré-visualizar. 
  
## <a name="concurrency-of-report-updates"></a>Simultaneidade de atualizações de relatórios  
De um modo geral, pré-visualiza um relatório como um passo no processo de atualizar e depois guardar um relatório no serviço Power BI. Quando estiver a atualizar um relatório, é possível que outra pessoa esteja ao mesmo tempo a atualizar e, em seguida, a guardar o relatório. O relatório que é guardado pela última vez é a versão do relatório que fica disponível para visualização futura e atualização. Isto significa que a versão do relatório que pré-visualizou pode não ser a versão que irá reabrir. Tem a opção de guardar o relatório com um novo nome através da opção **Guardar como** no menu do Report Builder.  
  
## <a name="external-report-items"></a>Itens de relatório externo  
 O seu relatório pode incluir itens tais como imagens externas que estão armazenadas em separado do relatório. Como os itens estão armazenados em separado, é possível que sejam movidos para uma localização diferente ou eliminados. Se isto acontecer, a pré-visualização do relatório poderá falhar. Pode atualizar o relatório para indicar o local atualizado do item ou, se o item tiver sido eliminado, substituí-lo por um item existente ou remover a referência ao item a partir do relatório.  
  
## <a name="next-steps"></a>Próximos passos

- [O que são relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)
  
