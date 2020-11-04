---
title: Sub-relatórios nos relatórios paginados do Power BI
description: Neste artigo, irá saber mais sobre as origens de dados suportadas para relatórios paginados no serviço Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 04/29/2020
ms.openlocfilehash: d2cd4e9f5d6cb8872e266fabacb9f8a5a3e318cb
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/04/2020
ms.locfileid: "93298003"
---
# <a name="subreports-in-power-bi-paginated-reports"></a>Sub-relatórios nos relatórios paginados do Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Um *sub-relatório* é um item de relatório paginado que apresenta outro relatório paginado no corpo de um relatório paginado principal. Em termos conceituais, um sub-relatório num relatório é semelhante a um frame numa página Web. É utilizado para incorporar um relatório num relatório. Pode utilizar qualquer relatório como sub-relatório. O relatório que é apresentado como o sub-relatório é armazenado na mesma área de trabalho Premium que o relatório principal. Pode designar o relatório principal para transmitir os parâmetros ao sub-relatório. Um sub-relatório pode repetir-se em regiões de dados, utilizando um parâmetro para filtrar dados em cada instância do sub-relatório.  
  
 ![Sub-relatório num relatório paginado](media/subreports/paginated-report-subreport.png "Sub-relatórios de relatórios paginados")  
  
 Nesta ilustração, as informações de contacto apresentadas no relatório principal Encomenda de Vendas vêm de um sub-relatório de Contactos.  
  
Os ficheiros de definição de relatório paginado (.rdl) são criados no Power BI Report Builder. Pode carregar sub-relatórios armazenados no SQL Server Reporting Services para uma área de trabalho Premium no serviço Power BI. Os relatórios principais e os sub-relatórios têm de ser publicados na mesma área de trabalho. Instale o [Power BI Report Builder](https://aka.ms/pbireportbuilder).
  
## <a name="work-with-report-builder-and-the-power-bi-service"></a>Trabalhar com o Report Builder e o serviço Power BI

O Power BI Report Builder pode funcionar com relatórios paginados no seu computador (conhecidos como relatórios locais) ou com relatórios no serviço Power BI.  Quando abrir o Report Builder pela primeira vez, ser-lhe-á pedido que inicie sessão na sua conta Power BI. Se não for, selecione **Iniciar Sessão** no canto superior direito.

:::image type="content" source="media/subreports/report-builder-sign-in.png" alt-text="Inicie sessão no Power BI":::

Depois de iniciar sessão, verá uma opção de **Serviço Power BI** no Power BI Report Builder para as opções **Abrir** e **Guardar Como** no menu **Ficheiro**. Quando selecionar a opção **Serviço Power BI** para guardar um relatório, irá criar uma ligação em direto entre o Power BI Report Builder e o serviço Power BI. 

:::image type="content" source="media/subreports/report-builder-subreport-open-service.png" alt-text="Abrir a partir do serviço Power BI":::

## <a name="save-a-local-report-to-the-power-bi-service"></a>Guardar um relatório local no serviço Power BI

Antes de poder adicionar um sub-relatório a um relatório principal, crie os dois relatórios e guarde-os na mesma área de trabalho do Power BI Premium. 

1. Para abrir um relatório local existente, no menu **Ficheiro** , selecione **Abrir** > **Este PC** e selecione um ficheiro .rdl.  

2. No menu **Ficheiro** , selecione **Guardar Como** > **Serviço Power BI**.  Veja [Publicar um relatório paginado no serviço Power BI](paginated-reports-save-to-power-bi-service.md) para obter informações.

    > [!NOTE]
    > Também pode carregar um relatório ao começar no serviço Power BI. O mesmo artigo, [Publicar um relatório paginado no serviço Power BI](paginated-reports-save-to-power-bi-service.md), contém informações.

3. Na caixa de diálogo **Guardar Como** , selecione uma área de trabalho Power BI Premium na qual possa armazenar os seus relatórios paginados.  As áreas de trabalho Premium têm um ícone de losango ![Ícone de losango Premium](media/subreports/report-builder-premium-diamond.png) junto do nome.

    :::image type="content" source="media/subreports/report-builder-subreport-save-as-service.png" alt-text="Guardar como no serviço Power BI":::

4. Selecione **Guardar**.

## <a name="add-a-subreport-to-a-report"></a>Adicionar um sub-relatório a um relatório

Agora que guardou ambos os relatórios na mesma área de trabalho Premium, pode adicionar um ao outro como sub-relatório. Existem duas formas de adicionar um sub-relatório. 

1. No friso **Inserir** , selecione o botão **Sub-relatório** ou clique com o botão direito do rato na tela do relatório e selecione **Inserir** > **Sub-relatório**.

    :::image type="content" source="media/subreports/report-builder-insert-subreport.png" alt-text="Inserir um sub-relatório num relatório":::

    A caixa de diálogo **Properties do Sub-relatório** é apresentada.  

2. Selecione o botão **Navegar** > navegue para o relatório que pretende utilizar como o sub-relatório > especifique o nome do sub-relatório na caixa de texto **Nome**.

3. Configure outras propriedades conforme necessário, incluindo os [parâmetros](#use-parameters-in-subreports).

## <a name="use-parameters-in-subreports"></a>Utilizar parâmetros em sub-relatórios  
 Para transmitir os parâmetros do relatório principal para o sub-relatório, defina um parâmetro de relatório no relatório que utilizará como sub-relatório. Quando colocar o sub-relatório no relatório principal, poderá selecionar o parâmetro de relatório e um valor para transmitir do relatório principal para o parâmetro de relatório no sub-relatório.  
  
> [!NOTE]  
> O parâmetro que selecionar do sub-relatório é um parâmetro de *relatório* , não um parâmetro de *consulta*.  
  
 Pode colocar um sub-relatório no corpo principal do relatório ou numa região de dados. Se colocar um sub-relatório numa região de dados, o sub-relatório repete-se em cada instância do grupo ou linha na região de dados. Pode transmitir um valor do grupo ou da linha para o sub-relatório. Na propriedade de valor do sub-relatório, utilize uma expressão de campo para o campo com o valor que pretende transmitir ao parâmetro do sub-relatório.  
  
 Para obter mais informações sobre trabalhar com parâmetros e sub-relatórios, veja [Adicionar um sub-relatório e parâmetros](/sql/reporting-services/report-design/add-a-subreport-and-parameters-report-builder-and-ssrs) na documentação do SQL Server Reporting Services.  

## <a name="preview-paginated-reports-in-report-builder"></a>Pré-visualizar relatórios paginados no Report Builder

Pode pré-visualizar os seus relatórios no Report Builder.

- No friso **Base** , selecione **Executar**. 

Uma vez que o Report Builder é uma ferramenta de design, a pré-visualização do relatório pode ter um aspeto diferente da composição do relatório no serviço Power BI.

### <a name="notes-about-previewing"></a>Notas sobre a pré-visualização

- O Report Builder não armazena credenciais das origens de dados utilizadas nos relatórios.  O Report Builder pede cada conjunto de credenciais durante a pré-visualização.  
- Se as origens de dados do relatório estiverem no local, terá de configurar um gateway após guardar o relatório na área de trabalho do Power BI.
- Se o Report Builder encontrar um erro durante a pré-visualização, devolverá uma mensagem genérica.  Se o erro for difícil de depurar, considere compor o relatório no serviço Power BI.  

## <a name="considerations"></a>Considerações

### <a name="maintaining-the-connection"></a>Manter a ligação

O Report Builder não persiste a ligação ao Power BI quando fecha o ficheiro.  É possível trabalhar com um relatório local principal em sub-relatórios armazenados na área de trabalho do Power BI. Guarde o relatório principal na área de trabalho do Power BI antes de fechar o relatório.  Caso contrário, poderá receber uma mensagem de "não encontrado" durante a pré-visualização, porque não existe uma ligação em direto ao serviço Power BI.  Se for o caso, aceda a um sub-relatório e selecione as propriedades do mesmo.  Abra o sub-relatório novamente a partir do serviço Power BI.  Isto restabelece a ligação e os restantes relatórios não devem ser afetados.

### <a name="renaming-a-subreport"></a>Mudar o nome de um sub-relatório

Se mudar o nome de um sub-relatório na área de trabalho, terá de corrigir a referência de nome no relatório principal. Caso contrário, o sub-relatório não será composto. O relatório principal será ainda assim composto com uma mensagem de erro dentro do item de sub-relatório.

## <a name="migrate-large-reports"></a>Migrar relatórios grande

Se estiver a migrar relatórios grandes para o Power BI, considere utilizar a [ferramenta RdlMigration](../guidance/migrate-ssrs-reports-to-power-bi.md).  A ferramenta RdlMigration foi atualizada para processar nomes de sub-relatórios duplicados.  Os nomes de sub-relatórios duplicados podem ocorrer quando dois ou mais relatórios têm o mesmo nome, mas situam-se em subdiretórios diferentes.  Se os nomes não forem exclusivos, só será reconhecido o primeiro sub-relatório.

Se quiser utilizar o Report Builder para migrar relatórios grandes, recomendamos que trabalhe primeiro com os sub-relatórios. Guarde cada um na área de trabalho do Power BI para impedir a duplicação de nomes de relatórios.

## <a name="share-reports-with-subreports"></a>Partilhar relatórios com sub-relatórios

Como afirmámos, o relatório principal e os sub-relatórios têm de estar na mesma área de trabalho. Caso contrário, o sub-relatório não será composto. Ao partilhar o relatório principal, também tem de partilhar os sub-relatórios. Se partilhar o relatório principal numa aplicação, certifique-se de que também inclui os sub-relatórios nessa aplicação. Se partilhar o relatório principal com utilizadores ou grupos de utilizadores diretamente, certifique-se de que também partilha todos os sub-relatórios com o mesmo conjunto de utilizadores ou grupos de utilizadores.
  
## <a name="next-steps"></a>Próximos passos

[Resolver problemas de sub-relatórios em relatórios paginados do Power BI](subreports-troubleshoot.md)

[Ver um relatório paginado no serviço Power BI](../consumer/paginated-reports-view-power-bi-service.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)