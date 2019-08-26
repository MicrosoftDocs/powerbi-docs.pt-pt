---
title: De um livro do Excel a um relatório incrível no serviço Power BI
description: Este artigo explica como pode criar um relatório incrível rapidamente a partir de um livro do Excel.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/12/2019
ms.author: maggies
LocalizationGroup: Data from files
ms.openlocfilehash: ed4bc9d10e3e1512aba559d77ba8729a39cb8a84
ms.sourcegitcommit: d12bc6df16be1f1993232898f52eb80d0c9fb04e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/13/2019
ms.locfileid: "68995110"
---
# <a name="from-excel-workbook-to-stunning-report-in-the-power-bi-service"></a>De um livro do Excel a um relatório incrível no serviço Power BI
A sua gestora quer ver um relatório sobre os números de vendas mais recentes combinado com as impressões da última campanha até ao fim do dia. No entanto, os dados mais recentes residem em vários sistemas de terceiros e em ficheiros no seu portátil. Anteriormente, demorava várias horas a criar elementos visuais e a formatar um relatório e, por isso, começa a sentir algum nervosismo.

Não se preocupe. Com o Power BI, pode criar um relatório incrível em pouco tempo.

Neste exemplo, vamos carregar um ficheiro do Excel a partir de um sistema local, criar um novo relatório e partilhá-lo com colegas, tudo no Power BI.

## <a name="prepare-your-data"></a>Preparar os dados
Vamos utilizar um ficheiro simples do Excel como exemplo. 

1. Antes de carregar o ficheiro do Excel no Power BI, tem de organizar os dados numa tabela simples. Numa tabela simples, cada coluna contém o mesmo tipo de dados, por exemplo, texto, data, número ou moeda. A sua tabela deve ter uma linha de cabeçalho, mas não deve ter colunas ou linhas que apresentem os totais.

   ![Dados organizados no Excel](media/service-from-excel-to-stunning-report/pbi_excel_file.png)

2. Em seguida, formate os dados como uma tabela. No Excel, no separador **Base**, no grupo **Estilos**, selecione **Formatar como Tabela**. 

3. Selecione um estilo de tabela a aplicar à folha de cálculo. 

   A folha de cálculo do Excel está agora pronta para ser carregada para o Power BI.

   ![Dados formatados como uma tabela](media/service-from-excel-to-stunning-report/pbi_excel_table.png)

## <a name="upload-your-excel-file-to-the-power-bi-service"></a>Carregar o ficheiro do Excel para o serviço Power BI
O serviço Power BI liga a muitas origens de dados, incluindo ficheiros do Excel que residem no seu computador. 

 > [!NOTE] 
 > Para acompanhar o resto deste tutorial, utilize o [livro Financial Sample](sample-financial-download.md) (Exemplo de Finanças).

1. Para começar, inicie sessão no serviço Power BI. Se ainda não se inscreveu, [pode fazê-lo gratuitamente](https://powerbi.com).

2. Crie um novo dashboard. Abra **A minha área de trabalho** e selecione o ícone **Criar**.

   ![ícone Criar](media/service-from-excel-to-stunning-report/power-bi-new-dash.png)

3. Selecione **Dashboard**, introduza um nome e, em seguida, selecione **Criar**. 

   O novo dashboard é apresentado sem dados.

   ![Menu pendente Criar](media/service-from-excel-to-stunning-report/power-bi-create-dash.png)

4. Na parte inferior do painel de navegação esquerdo, selecione **Obter dados**. 

5. Na página **Obter Dados**, na caixa **Ficheiros** em **Criar novo conteúdo**, selecione **Obter**.

   ![Obter dados de ficheiros](media/service-from-excel-to-stunning-report/pbi_get_files.png)

6. Na página **Ficheiros**, selecione **Ficheiro Local**. Navegue para o ficheiro de livro do Excel no seu computador e selecione **Abrir** para o carregar no serviço Power BI. 

   ![Janela Obter dados > Ficheiros](media/service-from-excel-to-stunning-report/pbi_local_file.png)

7. Na página **Ficheiro Local**, selecione **Importar**.


## <a name="build-your-report"></a>Criar o relatório
Depois de o serviço Power BI importar o ficheiro do Excel, comece a criar o seu relatório. 

1. Quando a mensagem **O conjunto de dados está pronto** é apresentada, selecione **Ver conjunto de dados**.  

   O Power BI é aberto na vista de edição e apresenta a tela de relatórios. No lado direito, estão os painéis **Visualizações**, **Filtros** e **Campos**. Tenha em atenção que os dados de tabela do livro do Excel aparecem no painel **Campos**. Abaixo do nome da tabela, o Power BI lista os cabeçalhos de coluna como campos individuais.

   ![O aspeto dos dados do Excel no painel Campos](media/service-from-excel-to-stunning-report/pbi_report_fields.png)

2. Agora, pode começar a criar visualizações. Imagine que a sua gestora quer ver o lucro ao longo do tempo. No painel **Campos**, arraste **Lucro** para a tela do relatório. 

   Por predefinição, o Power BI apresenta um gráfico de barras. 

3. Arraste **Data** para a tela do relatório. 

   O Power BI atualiza o gráfico de barras para mostrar o lucro por data.

   ![Gráfico de colunas no editor de relatórios](media/service-from-excel-to-stunning-report/pbi_report_pin-new.png)

   > [!TIP]
   > Se o gráfico não for parecido com o que esperava, verifique as suas agregações. Por exemplo, na área **Valor**, clique com o botão direito do rato no campo que acabou de adicionar e certifique-se de que os dados estão a ser agregados da forma que pretende. Neste exemplo, estamos a utilizar **Soma**.
   > 

A sua gestora quer saber quais os países mais lucrativos. Impressione-a com uma visualização de mapa. 

1. Selecione uma área em branco na tela do seu relatório. 

2. No painel **Campos**, arraste os campos **País** e **Lucro** para a tela do seu relatório.

   O Power BI cria um elemento visual de mapa com bolhas que representam o lucro relativo de cada local.

   ![Elemento visual de mapa no editor de relatórios](media/service-from-excel-to-stunning-report/pbi_report_map-new.png)

Que tal apresentar um elemento visual que mostre as vendas por produto e segmento de mercado? Isso é fácil. 

1. No painel **Campos**, selecione os campos **Vendas**, **Produto** e **Segmento**. 
   
   O Power BI cria um gráfico de barras instantaneamente. 

2. Altere o tipo de gráfico ao selecionar um dos ícones no menu **Visualizações**. Por exemplo, altere o gráfico para um **Gráfico de colunas empilhadas**. 

3. Para ordenar o gráfico, selecione as reticências (...) > **Ordenar por**.

   ![Gráfico de colunas empilhadas no editor de relatórios](media/service-from-excel-to-stunning-report/pbi_barchart-new.png)

Afixe todos os elementos visuais no seu dashboard. Agora já pode partilhá-lo com os seus colegas.

   ![Dashboard com os três elementos visuais afixados](media/service-from-excel-to-stunning-report/pbi_report.png)

## <a name="share-your-dashboard"></a>Partilhar o dashboard
Imagine que pretende partilhar o seu dashboard com o seu gestor. Pode partilhar o dashboard e o relatório subjacente com os colegas que tenham uma conta do Power BI. Os colegas podem interagir com o seu relatório, mas não podem guardar alterações.

1. Para partilhar o relatório, na parte superior do dashboard, selecione **Partilhar**.

   ![Ícone Partilhar](media/service-from-excel-to-stunning-report/power-bi-share.png)

   O Power BI apresenta a página **Partilhar dashboard**. 

2. Introduza os endereços de e-mail dos destinatários na caixa **Introduza os endereços de e-mail** e adicione uma mensagem na caixa abaixo desta. 

3. Para permitir que os destinatários partilhem o dashboard com outras pessoas, selecione **Permitir aos destinatários partilhar o dashboard**. Selecione **Partilhar**.

   ![Janela Partilhar dashboard](media/service-from-excel-to-stunning-report/power-bi-share-dash-new.png)

## <a name="next-steps"></a>Próximos passos

* [Introdução ao serviço Power BI](service-get-started.md)
* [Introdução ao Power BI Desktop](desktop-getting-started.md)
* [Conceitos básicos para designers no serviço Power BI](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/).

