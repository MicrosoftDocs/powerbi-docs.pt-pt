---
title: 'Tutorial: explorar o Power BI Report Server numa VM'
description: Neste tutorial, vai criar uma máquina virtual com o Power BI Report Server já instalado e explorar o portal Web.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: tutorial
ms.date: 05/18/2018
ms.author: maggies
ms.openlocfilehash: 38985014407a4d64998e25f6944f57aedcc67309
ms.sourcegitcommit: aa8045e42b979206c600bce4a8d17de1f0620462
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/22/2018
ms.locfileid: "34445009"
---
# <a name="tutorial-explore-the-power-bi-report-server-web-portal-in-a-vm"></a>Tutorial: explorar o portal Web do Power BI Report Server numa VM
Neste tutorial, vai criar uma máquina virtual do Azure com o Power BI Report Server já instalado, para poder experimentar a visualização, edição e gestão de relatórios paginados e do Power BI de exemplo, e KPIs.

![Portal Web do Report Server](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-in-vm-no-numbers.png)

Seguem-se as tarefas que vai desempenhar neste tutorial:

> [!div class="checklist"]
> * Criar e ligar-se a uma VM
> * Iniciar e explorar o portal Web do Power BI Report Server
> * Etiquetar um item favorito
> * Ver e editar um relatório do Power BI
> * Ver, gerir e editar um relatório paginado
> * Ver um livro do Excel no Excel Online

Para este tutorial, precisa de uma subscrição do Azure. Se não tiver uma subscrição, crie uma [conta gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) antes de começar.

## <a name="create-a-power-bi-report-server-vm"></a>Criar uma VM do Power BI Report Server

Felizmente, a equipa do Power BI criou uma VM que inclui um Power BI Report Server já instalado.

1. No Azure Marketplace, abra [Power BI Report Server](https://azuremarketplace.microsoft.com/marketplace/apps/reportingservices.technical-preview?tab=Overview).  

2. Selecione **Obter agora**.
3. Para aceitar os Termos de Utilização e a Política de Privacidade do fornecedor, selecione **Continuar**.

    ![Criar VM do Power BI Report Server](media/tutorial-explore-report-server-web-portal/power-bi-report-server-virtual-machine-create.png)

4. **Passo 1 Noções Básicas**, para **Nome da VM**, atribua-lhe o nome **reportservervm**.

5. Crie um nome de utilizador e uma palavra-passe.

6. Para **Grupo de recursos**, mantenha **Criar novo** e atribua-lhe o nome **reportserverresourcegroup**.

    Se seguir o tutorial mais do que uma vez, tem de dar um nome diferente do que deu na vez anterior ao grupo de recursos. Não pode utilizar o mesmo nome de grupo de recursos duas vezes na mesma subscrição. 

7. Mantenha as outras predefinições > **OK**.

    ![Atribuir nome à VM e ao grupo de recursos](media/tutorial-explore-report-server-web-portal/power-bi-report-server-create-resource-group.png)

8. **Passo 2 Definições**, mantenha as predefinições > **OK**.

9. **Passo 3 Resumo** > **OK**.

10. **Passo 4**, reveja os Termos de Utilização e a Política de Privacidade > **Criar**.

    O processo de **Submissão de implementação para o Power BI Report Server** demora vários minutos.

## <a name="connect-to-your-virtual-machine"></a>Ligar-se à sua máquina virtual

1. No painel de navegação à esquerda do Azure, selecione **Máquinas virtuais**. 

2. Na caixa **Filtrar por nome**, introduza “relatório”. 

3. Selecione a VM com o nome **REPORTSERVERVM**.

    ![Ver a máquina virtual](media/tutorial-explore-report-server-web-portal/power-bi-report-server-view-virtual-machine.png)

4. Em Máquina virtual REPORTSERVERVM, selecione **Ligar**.

    ![Ligar-se à máquina virtual](media/tutorial-explore-report-server-web-portal/power-bi-report-server-connect-to-virtual-machine.png)

5. Na caixa de diálogo Ligação do Ambiente de Trabalho Remoto, selecione **Ligar**.

6. Introduza o nome e a palavra-passe que criou para a VM > **OK**.

7. A caixa de diálogo seguinte indica que não se pode identificar a identidade do computador remoto. Selecionar **Sim**.

   E já está: a sua nova VM é aberta.

## <a name="power-bi-report-server-on-the-vm"></a>Power BI Report Server na VM

Quando abre a sua VM, estes são os itens que aparecem no ambiente de trabalho.

![A máquina virtual do Power BI Report Server é iniciada](media/tutorial-explore-report-server-web-portal/power-bi-report-server-start-vm-numbered.png)

|Número  |O que é  |
|---------|---------|
|![Número 1](media/tutorial-explore-report-server-web-portal/number-1.png) | Inicia o SQL Server Data Tools para criar relatórios paginados (.RDL) |
|![Número 2](media/tutorial-explore-report-server-web-portal/number-2.png) | Relatórios (.PBIX) do Power BI de exemplo  |
|![Número 3](media/tutorial-explore-report-server-web-portal/number-3.png) | Ligações a documentação do Power BI Report Server   |
|![Número 4](media/tutorial-explore-report-server-web-portal/number-4.png) | Inicia o Power BI Desktop otimizado para o Power BI Report Server (março de 2018)  |
|![Número 5](media/tutorial-explore-report-server-web-portal/number-5.png) | Abre o portal Web do Power BI Report Server no browser   |

Faça duplo clique no ícone **Portal Web do Report Server**. O browser abre http://localhost/reports/browse. No portal Web, pode ver vários ficheiros agrupados por tipo. 

![Portal Web do Power BI Report Server](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-in-vm.png)

|Número  |O que é  |
|---------|---------|
|![Número 1](media/tutorial-explore-report-server-web-portal/number-1.png) | KPIs criados no portal Web |
|![Número 2](media/tutorial-explore-report-server-web-portal/number-2.png) |  Relatórios (.PBIX) do Power BI  |
|![Número 3](media/tutorial-explore-report-server-web-portal/number-3.png) | Relatórios móveis criados no SQL Server Mobile Report Publisher  |
|![Número 4](media/tutorial-explore-report-server-web-portal/number-4.png) |  Relatórios paginated criados no Report Builder ou SQL Server Data Tools  |
|![Número 5](media/tutorial-explore-report-server-web-portal/number-5.png) | Livros do Excel   | 
|![Número 6](media/tutorial-explore-report-server-web-portal/number-6.png) | Origens de dados de relatórios paginados | 


## <a name="tag-your-favorites"></a>Etiquetar os favoritos
Pode etiquetar os relatórios e KPIs que quer que sejam favoritos. São mais fáceis de localizar porque estão todos numa única pasta Favoritos, tanto no portal Web como nas aplicações móveis do Power BI. 

1. Selecione as reticências (**…**) no canto superior direito da **Margem de Lucro** KPI > **Adicionar aos Favoritos**.
   
    ![Adicionar aos Favoritos](media/tutorial-explore-report-server-web-portal/power-bi-report-server-add-to-favorites.png)
2. Selecione **Favoritos** no friso do portal Web para vê-lo juntamente com os outros favoritos na página Favoritos no portal Web.
   
    ![Ver Favoritos](media/tutorial-explore-report-server-web-portal/power-bi-report-server-favorites.png)

3. Selecione **Procurar** para voltar para o portal Web.
   
## <a name="view-items-in-list-view"></a>Ver itens na vista Lista
Por predefinição, o portal Web apresenta o conteúdo na vista Mosaico.

Pode mudar para a vista Lista, onde é fácil mover ou eliminar vários itens em simultâneo. 

1. Selecione **Mosaicos** > **Lista**.
   
    ![Alternar entre vistas](media/tutorial-explore-report-server-web-portal/report-server-web-portal-list-view.png)

2. Regresse à vista Mosaicos: selecione **Lista** > **Mosaicos**.

## <a name="power-bi-reports"></a>Relatórios do Power BI

Pode ver e interagir com relatórios do Power BI no portal Web, bem como iniciar o Power BI Desktop a partir do portal Web.

### <a name="view-power-bi-reports"></a>Ver relatórios do Power BI

1. No portal Web em **Relatórios do Power BI**, selecione **Relatório de Descrição Geral de Cliente de Exemplo**. O relatório abre-se no browser.

1. Selecione o bloco dos Estados Unidos no mapa de árvore para ver como destaca os valores relacionados nos outros elementos visuais.

    ![Relatório do Power BI realçado](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi.png)

### <a name="edit-in-power-bi-desktop"></a>Editar no Power BI Desktop

1. Selecione **Editar no Power BI Desktop**.

1. Selecione **Permitir** para permitir que este site abra um programa no seu computador. 

     O relatório abre-se no Power BI Desktop. Tome nota do nome na barra superior, “Power BI Desktop (março de 2018)”. Esta é a versão otimizada para o Power BI Report Server.

    ![Power BI Desktop](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi-desktop.png)

     Utilize a versão do Power BI Desktop que está instalada na VM. Não pode mudar de domínios para carregar um relatório.

3. No painel Campos, expanda a tabela Clientes e arraste o campo Ocupação para Filtros de nível de relatório.

    ![Arraste um campo para o painel Filtros](media/tutorial-explore-report-server-web-portal/power-bi-report-server-desktop-filter.png)

1. Guarde o relatório.

1. Volte para o relatório no browser e selecione o ícone **Atualizar** do browser.

    ![Ícone Atualização do Browser](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-refresh.png)

8. Expanda o painel **Filtros** à direita para ver o filtro **Ocupação** que adicionou. Selecione **Professional**.

    ![Relatório do Power BI filtrado](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi-filtered.png)

3. Selecione **Procurar** para voltar para o portal Web.

## <a name="paginated-rdl-reports"></a>Relatórios paginados (.RDL)

Pode ver e gerir relatórios paginados e iniciar o Report Builder no portal Web.

### <a name="manage-a-paginated-report"></a>Gerir um relatório paginado

1. No portal Web em **Relatórios paginados**, selecione as reticências (…) junto a **Nota de Vendas** > **Gerir**.

1. Selecione **Parâmetros**, altere o valor predefinido para **SalesOrderNumber** para **SO50689** > **Aplicar**.

   ![Definir parâmetros do relatório](media/tutorial-explore-report-server-web-portal/power-bi-report-server-set-parameters.png)

3. Selecione **Procurar** para voltar para o portal Web.

### <a name="view-a-paginated-report"></a>Ver um relatório paginado

1. Selecione **Nota de Vendas** no portal Web.
 
3.  Pode vê-la aberta no parâmetro **Nota** definido, **SO50689**. 

    ![Parâmetro de relatório paginado](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated.png)

    Pode alterar esse parâmetro aqui, juntamente com os outros parâmetros, sem alterar as predefinições.

1. Selecione **Nota** **SO48339** > **Ver Relatório**.

4. Pode ver que se trata da página 1 de 2. Selecione a seta para a direita para ver a segunda página. A tabela continua nessa página.

    ![Página 2 de 2 do relatório paginado](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-2-of-2.png)

5. Selecione **Procurar** para voltar para o portal Web.

### <a name="edit-a-paginated-report"></a>Editar um relatório paginado

Pode editar relatórios paginados no Report Builder e pode iniciar o Report Builder diretamente no browser.

1. No portal Web, selecione as reticências (…) junto a **Nota de Vendas** > **Editar no Report Builder**.

1. Selecione **Permitir** para permitir que este site abra um programa no seu computador.

1. O relatório da Nota de Vendas abre-se na Vista de Estrutura no Report Builder.

    ![Vista de estrutura, relatório paginado](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-design-view.png)

1. Selecione **Executar** para pré-visualizar o relatório.

    ![Pré-visualizar um relatório paginado](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-preview.png)

5. Feche o Report Builder e volte ao browser.

## <a name="view-excel-workbooks"></a>Ver livros do Excel

Pode ver e interagir com os livros do Excel no Excel Online, no Power BI Report Server. 

1. Selecione o livro do Excel **Office Liquidation Sale.xlsx**. Pode solicitar credenciais. Selecione **Cancelar**. 
    Abre-se no portal Web.
1. Selecione **Aplicação** na segmentação de dados.

    ![Excel Online no portal Web](media/tutorial-explore-report-server-web-portal/power-bi-report-server-excel-online.png)

1. Selecione **Procurar** para voltar para o portal Web.

## <a name="clean-up-resources"></a>Limpar recursos

Agora que concluiu este tutorial, elimine o grupo de recursos, a máquina virtual e todos os recursos relacionados. 

- Para tal, selecione o grupo de recursos para a VM e selecione **Eliminar**.

## <a name="next-steps"></a>Próximos passos

Neste tutorial, criou uma VM com o Power BI Report Server. Experimentou algumas das funcionalidades do portal Web e abriu um relatório do Power BI e um relatório paginado nos respetivos editores. Esta VM tem origens de dados do SQL Server Analysis Services, pelo que pode experimentar criar os seus próprios relatórios paginados e do Power BI com essas mesmas origens de dados. 

Para saber mais sobre a criação de relatórios para o Power BI Report Server, continue.

> [!div class="nextstepaction"]
> [Criar um relatório do Power BI para o Power BI Report Server](./quickstart-create-powerbi-report.md)


