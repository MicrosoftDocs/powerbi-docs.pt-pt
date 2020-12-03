---
title: Introduzir dados diretamente num relatório paginado no Report Builder
description: Neste artigo, irá aprender a introduzir dados diretamente num relatório paginado no Report Builder.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 07/10/2020
ms.openlocfilehash: 5719a5d6e8f559f1dba9f87bc9937ed925195072
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418216"
---
# <a name="enter-data-directly-in-a-paginated-report-in-report-builder---power-bi"></a>Introduzir dados diretamente num relatório paginado no Report Builder – Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Neste artigo, irá conhecer uma funcionalidade da nova versão do Power BI Report Builder que lhe permite introduzir dados diretamente num relatório de RDL como um conjunto de dados incorporado.  Esta funcionalidade é semelhante ao Power BI Desktop. Pode introduzir diretamente os dados num conjunto de dados do seu relatório ou colá-los a partir de outro programa, como o Microsoft Excel. Após introduzir os dados e criar um conjunto de dados, poderá utilizá-lo tal como utilizaria qualquer outro conjunto incorporado que tivesse criado. Além disto, pode adicionar mais de uma tabela e utilizar uma como um filtro para outra. Esta funcionalidade é particularmente útil para conjuntos de dados estáticos e pequenos que poderá ter de utilizar no seu relatório, como parâmetros de relatórios.
 
## <a name="prerequisites"></a>Pré-requisitos

- Para introduzir dados diretamente num relatório paginado, [transfira e instale o Power BI Report Builder](https://aka.ms/pbireportbuilder). 
- Para guardar o seu relatório paginado no serviço Power BI, precisa de uma [conta do Power BI Pro](../fundamentals/service-self-service-signup-for-power-bi.md) e de acesso de escrita a uma área de trabalho numa [capacidade do Power BI Premium](../admin/service-premium-what-is.md).
- Para guardar o seu relatório paginado num servidor de relatórios, precisa de permissões para [editar o ficheiro RsReportServer.config](#upload-the-paginated-report-to-a-report-server).

## <a name="create-a-data-source-and-dataset"></a>Criar uma origem e um conjunto de dados

Após a transferência e instalação do Report Builder, deverá seguir o mesmo fluxo de trabalho utilizado para adicionar um conjunto de dados e uma origem de dados incorporados ao seu relatório. No procedimento seguinte, em **Origens de Dados**, é apresentada uma nova opção: **Introduzir Dados**.  Só tem de configurar esta origem de dados uma vez por relatório. Após a configuração, pode criar múltiplas tabelas a partir dos dados introduzidos como conjuntos de dados separados que utilizam a mesma origem de dados.

1. No painel **Dados do Relatório**, selecione **Novo** > **Conjunto de Dados**.

    ![Captura de Ecrã a mostrar o Novo Conjunto de Dados do Report Builder.](media/paginated-reports-enter-data/paginated-new-dataset.png)

1. Na caixa de diálogo **Propriedades do Conjunto de Dados**, selecione **Utilizar um conjunto de dados incorporado no meu relatório**.

1. Junto a **Origem de dados**, selecione **Novo**.

    ![Captura de ecrã a mostrar a Nova origem de dados incorporada.](media/paginated-reports-enter-data/paginated-new-data-source.png)

1. Na caixa de diálogo **Propriedades da Origem de Dados**, selecione **Utilizar uma ligação incorporada no meu relatório**.
2. Na caixa **Selecionar o tipo de ligação**, selecione **INTRODUZIR DADOS** > **OK**.

    ![Captura de ecrã a mostrar a origem de dados INTRODUZIR DADOS.](media/paginated-reports-enter-data/paginated-data-source-properties-enter-data.png)

1. Regresse à caixa de diálogo **Propriedades do Conjunto de Dados** e selecione **Estruturador de Consulta**.
2. No painel **Estruturador de Consulta**, clique com o botão direito do rato e cole os seus dados na tabela.

    ![Captura de ecrã a mostrar Introduzir dados no Estruturador de Consulta.](media/paginated-reports-enter-data/paginated-enter-data.png)

1. Para definir os nomes das colunas, faça duplo clique em cada **NovaColuna** e escreva o nome da coluna.

    ![Captura de ecrã a mostrar os nomes definidos das colunas.](media/paginated-reports-enter-data/paginated-column-name.png)

1. Se a primeira linha tiver cabeçalhos de coluna dos dados originais, clique nela com o botão direito do rato e elimine-a.
    
9. Por predefinição, o tipo de dados de cada coluna é Cadeia. Para alterar o tipo de dados, clique com o botão direito do rato no cabeçalho da coluna > **Alterar o Tipo** e defina outro tipo de dados, como Data ou Flutuante.

    ![Captura de ecrã a mostrar a coluna Alterar tipo de dados.](media/paginated-reports-enter-data/paginated-data-type.png)

1. Quando tiver terminado a criação da tabela, selecione **OK**.  

    A consulta gerada é a mesma que seria apresentada com uma origem de dados XML. Vamos utilizar XML como o fornecedor de dados.  Redefinimos a sua finalidade para também permitir este cenário.

    ![Captura de ecrã a mostrar a estrutura de dados XML.](media/paginated-reports-enter-data/paginated-xml-data.png)

12. Na caixa de diálogo **Propriedades do Conjunto de Dados**, selecione **OK**.

13. A sua origem de dados e o seu conjunto de dados são apresentados no painel **Dados do Relatório**.

    ![Captura de ecrã a mostrar o Conjunto de dados no painel Dados do Relatório.](media/paginated-reports-enter-data/paginated-report-data-pane.png)

Pode utilizar o seu conjunto de dados como a base para visualizações de dados no seu relatório. Também pode adicionar outro conjunto de dados e utilizar a mesma origem de dados para o mesmo.

## <a name="design-the-report"></a>Estruturar o relatório

Agora que tem uma origem e um conjunto de dados, está tudo pronto para criar um relatório. O seguinte procedimento cria um relatório simples baseado nos dados apresentados na secção anterior.

1. No menu **Inserir**, selecione **Tabela** > **Assistente de Tabelas**.

    :::image type="content" source="media/paginated-reports-enter-data/paginated-table-wizard.png" alt-text="Captura de ecrã a mostrar a seleção da opção Assistente de Tabelas.":::

1. Selecione o conjunto de dados que acabou de criar > **Seguinte**.

    :::image type="content" source="media/paginated-reports-enter-data/paginated-choose-dataset.png" alt-text="Captura de ecrã a mostrar a caixa de diálogo Selecionar um conjunto de dados.":::

2.  Na página Dispor campos, arraste os campos que pretende agrupar da caixa **Campos disponíveis** para a caixa **Grupos de linhas**. Neste exemplo:

    - RegiãoDoPaís
    - VendasPorAno

3.  Arraste os campos que pretende agregar da caixa **Campos disponíveis** para a caixa **Valores**. Neste exemplo:

    - MontanteDeVendas

    Por predefinição, o Report Builder soma os campos na caixa **Valores**, mas pode escolher outra agregação.

    :::image type="content" source="media/paginated-reports-enter-data/paginated-select-aggregation.png" alt-text="Captura de ecrã a mostrar várias agregações à escolha.":::
 
1. Selecione **Seguinte**.
4.  Na página **Escolher o layout**, mantenha todas as configurações padrão, mas desmarque **Expandir/fechar grupos**. Em geral, é recomendável expandir e reduzir grupos. No entanto, desta vez, vamos ver todos os dados.

5.  Selecione **Seguinte** > **Concluir**. A tabela é apresentada na superfície da estrutura.

    :::image type="content" source="media/paginated-reports-enter-data/paginated-design-view-matrix.png" alt-text="Captura de ecrã a mostrar o relatório na vista Estrutura.":::

### <a name="run-the-report"></a>Executar o relatório

Para ver os valores e pré-visualizar o relatório, execute-o.

1. Selecione **Executar** no friso **Página Principal**.

    :::image type="content" source="media/paginated-reports-enter-data/paginated-run-report.png" alt-text="Captura de ecrã a mostrar a seleção da opção Executar no friso Página Principal.":::

    Agora, pode ver os valores. A matriz tem mais linhas do que as que viu na vista Estrutura!  Pode formatar a página ou optar por utilizar as predefinições antes de guardar a mesma no computador local ou publicá-la no serviço.

1. Para ver o aspeto do relatório no momento da impressão, selecione **Esquema de Impressão**.

    :::image type="content" source="media/paginated-reports-enter-data/paginated-select-print.png" alt-text="Captura de ecrã a mostrar a seleção do Esquema de Impressão.":::

    Agora, pode ver qual será o respetivo aspeto numa página impressa.

    :::image type="content" source="media/paginated-reports-enter-data/paginated-print-layout.png" alt-text="Captura de ecrã a mostrar o relatório na vista do esquema de impressão.":::

## <a name="upload-the-paginated-report-to-the-power-bi-service"></a>Carregar o relatório paginado para o serviço Power BI

Agora que os relatórios paginado são suportados no serviço Power BI, pode carregar os seus relatórios paginados para uma capacidade Premium. Veja [Carregar um relatório paginado](paginated-reports-save-to-power-bi-service.md) para obter detalhes.

## <a name="upload-the-paginated-report-to-a-report-server"></a>Carregar o relatório paginado para um servidor de relatórios

Também pode carregar o seu relatório paginado para um servidor de relatórios do Power BI Report Server ou SQL Server Reporting Services 2016 ou 2017. Antes de o fazer, tem de adicionar o seguinte item ao seu ficheiro RsReportServer.config como uma extensão de dados adicional. Crie uma cópia de segurança do seu ficheiro RsReportServer.config antes de fazer a alteração, para a eventualidade de vir a ter problemas.

```xml
<Extension Name="ENTERDATA" Type="Microsoft.ReportingServices.DataExtensions.XmlDPConnection,Microsoft.ReportingServices.DataExtensions">
    <Configuration>
        <ConfigName>ENTERDATA</ConfigName>
    </Configuration>
</Extension>
```

Após a edição do ficheiro, a lista de fornecedores de dados no ficheiro de configuração deve ter o seguinte aspeto:

![Captura de ecrã a mostrar o ficheiro de configuração RsReportServer.](media/paginated-reports-enter-data/paginated-rsreportserver-config-file.png)

Agora está tudo pronto e já pode publicar relatórios que utilizem esta nova funcionalidade no seu servidor de relatórios.

## <a name="next-steps"></a>Próximos passos

- [O que são relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)
- [O que é o Power BI Report Server?](../report-server/get-started.md)
