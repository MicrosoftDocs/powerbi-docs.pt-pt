---
title: Criar um relatório paginado com um conjunto de dados partilhado do Power BI – Power BI Report Builder
description: Crie um relatório paginado no Power BI Report Builder com base num conjunto de dados partilhado do Power BI.
ms.date: 01/03/2020
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 335b93720718bb72027c29c6093aad952cc4cdb2
ms.sourcegitcommit: b09de56e971b8844a3771413d1f56d49b31baaaf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/07/2020
ms.locfileid: "75691475"
---
# <a name="create-a-paginated-report-based-on-a-power-bi-shared-dataset"></a>Criar um relatório paginado com base num conjunto de dados partilhado do Power BI

Pode utilizar um conjunto de dados que criou no Power BI Desktop como uma origem de dados para relatórios paginados do Power BI Report Builder. Imagine este cenário: criou um relatório do Power BI no Power BI Desktop. Passou muito tempo a criar o modelo de dados e, em seguida, criou um relatório apelativo do Power BI com vários tipos de elementos visuais. O seu relatório tem uma matriz com várias linhas, pelo que tem de se deslocar para ver todas. Os leitores do seu relatório querem imprimir o relatório e apresentar todas as linhas nessa matriz. Um relatório paginado do Power BI pode fazer isso: imprima uma tabela ou matriz com múltiplas páginas, com cabeçalhos e rodapés de página e um esquema de página perfeito que criou. Irá complementar o relatório do Power BI Desktop. Quer que se baseie nos mesmos dados, sem discrepâncias, por isso utiliza o mesmo conjunto de dados.

![Power BI Desktop para o relatório paginado do Report Builder](media/report-builder-shared-datasets/power-bi-desktop-report-builder-arrow-26-pgs.png)

O conjunto de dados não tem de estar numa área de trabalho na capacidade Premium e não tem de ser membro dessa área de trabalho. Só tem de ter [Permissão de compilação](service-datasets-build-permissions.md) para a base de dados. Para publicar o seu relatório paginado, precisa de uma licença do Power BI Pro. Também precisa de pelo menos uma função de Contribuidor numa área de trabalho numa capacidade Premium.

## <a name="what-you-need"></a>O que precisa

Eis uma lista do que precisa e não precisa para utilizar um conjunto de dados partilhado no Power BI Report Builder.

- Power BI Report Builder. [Transferir e instalar o Power BI Report Builder](https://go.microsoft.com/fwlink/?linkid=2086513).
- Para aceder a um conjunto de dados do Power BI, tem de ter permissão de compilação no conjunto de dados. Leia sobre a [permissão de compilação](service-datasets-build-permissions.md).
- Não precisa de uma licença do Power BI Pro para criar um relatório paginado no Report Builder. 
- Precisa de uma licença do Power BI Pro para publicar o seu relatório paginado. Também precisa de pelo menos uma função de Contribuidor numa área de trabalho numa capacidade Premium. 
- Opcional: se quiser acompanhar este artigo, transfira o ficheiro [Exemplo de Análise de Revenda.pbix](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) do Power BI Desktop, abra-o no Power BI Desktop e adicione uma tabela com várias colunas. No painel **Formatar**, desative a opção **Totais**. Em seguida, publique numa área de trabalho no serviço Power BI.

    ![Totais desativados](media/report-builder-shared-datasets/power-bi-desktop-totals-off.png)

## <a name="connect-to-the-power-bi-dataset"></a>Ligar ao conjunto de dados do Power BI

1. Abra o Report Builder do Power BI.
1. Selecione **Iniciar sessão** no canto superior direito do Report Builder para iniciar sessão na sua conta do Power BI.
1. No painel Dados do Relatório, selecione **Novo** > **Ligação do Conjunto de Dados do Power BI**.

    ![Novo conjunto de dados no painel Dados do Relatório](media/report-builder-shared-datasets/power-bi-report-builder-new-dataset.png)

    > [!NOTE]
    > Não pode criar a origem de dados ou conjunto de dados para um conjunto de dados do Power BI com os assistentes de tabelas, de matrizes ou de gráficos do Report Builder. Depois de criá-los, pode utilizar os assistentes para criar tabelas, matrizes ou gráficos com base nos mesmos.

1. Procure o conjunto de dados ou a área de trabalho em que reside > **Selecionar**.
    O Report Builder preenche o nome do conjunto de dados.

    ![Selecionar conjunto de dados](media/report-builder-shared-datasets/power-bi-report-builder-select-dataset.png)
    
1. O conjunto de dados é indicado em Origens de Dados no painel Dados do Relatório.

    ![Conjunto de dados em Origens de Dados no painel Dados do Relatório](media/report-builder-shared-datasets/power-bi-report-builder-data-source.png)

    Lembre-se de que pode ligar a múltiplos conjuntos de dados do Power BI e outras origens de dados no mesmo relatório paginado.


## <a name="get-the-query-for-the-dataset"></a>Obter a consulta para o conjunto de dados

Quando quer que os dados no seu relatório do Power BI e no seu relatório do Report Builder sejam os mesmos, não basta ligar ao conjunto de dados. Também precisa da consulta incorporada nesse conjunto de dados.

1. Abra o relatório do Power BI (.pbix) no Power BI Desktop.
1. Certifique-se de que tem uma tabela no seu relatório que contém todos os dados que pretende no relatório paginado.

1. No friso **Ver**, selecione **Analisador de Desempenho**.

    ![Abrir o Analisador de Desempenho](media/report-builder-shared-datasets/power-bi-performance-analyzer.png)

1. No painel **Analisador de Desempenho**, selecione **Iniciar gravação** e, em seguida, selecione **Atualizar elementos visuais**.

    ![Atualizar elementos visuais](media/report-builder-shared-datasets/power-bi-performance-analyzer-refresh-visuals.png)

1. Expanda o sinal de adição ( **+** ) junto ao nome da tabela e selecione **Copiar consulta**. A consulta é a fórmula DAX de que precisa para o conjunto de dados no Power BI Report Builder.

    ![Copiar a consulta](media/report-builder-shared-datasets/power-bi-performance-analyzer-copy-query.png)

## <a name="create-the-dataset-with-the-query"></a>Criar o conjunto de dados com a consulta

1. Regresse ao Report Builder do Power BI.
1. Clique com o botão direito do rato no conjunto de dados em **Origens de Dados** e selecione **Adicionar Conjunto de Dados**.

    ![Adicionar conjunto de dados](media/report-builder-shared-datasets/power-bi-report-builder-add-dataset.png)

1. Em Propriedades do Conjunto de Dados, atribua um nome e selecione **Estruturador de Consulta**.

4. Certifique-se de que o **DAX** está selecionado e desselecione o ícone **Modo de Estrutura**.

    ![Estruturador de Consulta do Report Builder](media/report-builder-shared-datasets/power-bi-report-builder-query-designer.png)

1. Na caixa superior, cole a consulta que copiou do Power BI Desktop.

1. Selecione **Executar Consulta** (o ponto de exclamação vermelho, !) para garantir que a sua consulta funciona. 

    ![Executar a consulta](media/report-builder-shared-datasets/power-bi-report-builder-run-query.png)

    Verá os resultados da consulta na caixa inferior.

    ![Resultados da consulta](media/report-builder-shared-datasets/power-bi-report-builder-query-results.png)

1. Selecione **OK**.

    Verá a sua consulta na janela **Consulta** da caixa de diálogo **Propriedades do Conjunto de Dados**.

    ![Caixa de diálogo Propriedades do conjunto de dados](media/report-builder-shared-datasets/power-bi-report-builder-dataset-properties.png)

1. Selecione **OK**.

    Agora vê o seu novo conjunto de dados com uma lista de campos no painel Dados do Relatório.

    ![Conjunto de dados no painel Dados do Relatório](media/report-builder-shared-datasets/power-bi-report-builder-dataset.png)

## <a name="create-a-table-in-the-report"></a>Criar uma tabela no relatório

Uma forma rápida de criar uma tabela é através do Assistente de Tabelas.

1. No friso **Inserir**, selecione **Tabela** > **Assistente de Tabelas**.

    ![Iniciar o Assistente de Tabelas](media/report-builder-shared-datasets/power-bi-report-builder-table-wizard.png)

1. Selecione o conjunto de dados que criou com a consulta DAX > **Seguinte**.

    ![Escolher um conjunto de dados](media/report-builder-shared-datasets/power-bi-report-builder-choose-dataset.png)

1. Para criar uma tabela simples, selecione os campos que pretende em **Campos disponíveis**. Pode selecionar múltiplos campos de cada vez ao selecionar o primeiro que pretende, premir a tecla Shift e selecionar o último.

    ![Selecionar múltiplos campos](media/report-builder-shared-datasets/power-bi-report-builder-select-fields.png)

1. Arraste os campos para a caixa **Valores** > **Seguinte**.

    ![Assistente de Tabelas](media/report-builder-shared-datasets/power-bi-report-builder-value-fields.png)

1. Selecione as opções de esquema que pretende > **Seguinte**.

1. Selecione **Concluir**.
    Verá a sua tabela na Vista Estrutura.

    ![Vista de Estrutura do Relatório](media/report-builder-shared-datasets/power-bi-report-builder-design-view.png)

1. Selecione **Clique para adicionar o título** e adicione um título.

1. Selecione **Executar** para pré-visualizar o seu relatório.

    ![Pré-visualizar Relatório](media/report-builder-shared-datasets/power-bi-report-builder-preview.png)

1. Selecione **Esquema de Impressão** para ver o aspeto do seu relatório impresso. 

    O esquema deste relatório tem de ser trabalhado. Tem 54 páginas porque as colunas e margens fazem com que a tabela tenha duas páginas.

    ![Esquema de Impressão do Relatório](media/report-builder-shared-datasets/power-bi-report-builder-print-layout-2-p1-p2.png)

## <a name="format-the-report"></a>Formatar o relatório

Tem várias opções de formatação para ajustar a sua tabela numa página. 

1. Pode diminuir as margens da página no painel Propriedades. Se não vir o painel Propriedades, no friso **Ver**, selecione a caixa de verificação **Propriedades**.

1. Selecione o relatório, não selecione a tabela ou título.
1. No painel **Propriedades do Relatório**, em **Página**, expanda **Margens** e altere cada uma para **0,75 pol**.

    ![Definir as margens da página](media/report-builder-shared-datasets/power-bi-report-builder-page-margins.png)

1. Também pode diminuir a largura das colunas. Selecione o limite da coluna e arraste o lado direito para a esquerda.

    ![Definir a largura da coluna](media/report-builder-shared-datasets/power-bi-report-builder-column-width.png)

1. Outra opção é garantir que os valores numéricos estão bem formatados. Selecione uma célula com um valor numérico. 
    > [!TIP]
    > Pode formatar mais do que uma célula de cada vez ao premir a tecla Shift enquanto seleciona as outras células.

    ![Selecionar mais do que uma célula](media/report-builder-shared-datasets/power-bi-report-builder-select-cells.png)

1. No friso **Base**, na secção **Número**, altere o formato **Predefinido** para um formato numérico, tal como **Moeda**.

    ![Definir o formato de número](media/report-builder-shared-datasets/power-bi-report-builder-number-format.png)

1. Altere o estilo **Marcador de Posição** para **Valores de Exemplo**, para que possa ver a formatação na célula. 

    ![Ver valores de exemplo](media/report-builder-shared-datasets/power-bi-report-builder-sample-values.png)

1. Se for adequado, na secção **Número**, diminua as casas decimais para poupar mais espaço.

### <a name="getting-rid-of-blank-pages"></a>Eliminar páginas em branco

Mesmo que tenha diminuído as margens e as colunas da tabela, ainda tem algumas páginas em branco. Porquê? Por causa da matemática. 

Quando soma as margens da página que definiu, mais a largura do *corpo* do relatório, tem de ser menor do que a largura do formato do relatório.

Por exemplo, digamos que o seu relatório tem o formato 8,5x11 pol. e definiu as margens laterais como 0,75. As duas margens juntas têm 1,5 pol., pelo que o corpo tem de ter menos de 7 pol.

1. Selecione o limite direito da superfície de desenho do relatório e arraste para que seja menor do que o número pretendido na régua. 

    > [!TIP]
    > Pode definir com mais precisão nas Propriedades do **corpo**. Em **Tamanho**, defina a **Largura** de forma adequada.

    ![Definir o tamanho do corpo](media/report-builder-shared-datasets/power-bi-report-builder-body-size.png)

1. Selecione **Executar** para pré-visualizar o seu relatório e garantir que eliminou as páginas em branco. Este relatório tem apenas 26 páginas, em vez das 54 iniciais. Sucesso!

    ![Não imprimir páginas em branco](media/report-builder-shared-datasets/power-bi-report-builder-print-26-pgs.png)

## <a name="limitations-and-considerations"></a>Limitações e considerações 

- Para conjuntos de dados que utilizam uma Ligação em Direto ao Analysis Services, pode ligar diretamente ao utilizar a ligação subjacente do Analysis Services em vez de um conjunto de dados partilhado.
- Os conjuntos de dados com recomendações certificadas ou promovidas aparecem na lista de conjuntos de dados disponíveis, mas não são marcados como tal. 

## <a name="next-steps"></a>Próximos passos

- [O que são relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)