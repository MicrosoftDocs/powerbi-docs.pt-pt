---
title: 'Exemplo de Análise de Qualidade do Fornecedor do Power BI: veja uma apresentação'
description: 'Exemplo de Análise de Qualidade do Fornecedor do Power BI: veja uma apresentação'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/19/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 156b00c7f7287f12397afea422a38f3870d6c399
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73858413"
---
# <a name="supplier-quality-analysis-sample-for-power-bi-take-a-tour"></a>Exemplo de Análise de Qualidade do Fornecedor do Power BI: veja uma apresentação

Este dashboard de exemplo do setor e o respetivo relatório subjacente focam-se num dos desafios típicos da cadeia de fornecimento: a análise de qualidade do fornecedor. Esta análise depende de duas métricas principais: o número total de defeitos e o período de indisponibilidade total que estes defeitos causaram. 

Este exemplo tem dois objetivos principais:

* Compreender quem são os melhores e os piores fornecedores, no que respeita à qualidade.
* Identificar as instalações fabris que melhor localizam e rejeitam defeitos, para minimizar o período de indisponibilidade.

![Dashboard do exemplo Supplier Quality Analysis Sample](media/sample-supplier-quality/supplier1.png)

Este exemplo faz parte de uma série que mostra como pode utilizar o Power BI com dados, relatórios e dashboards orientados para negócios. Foi criado com dados reais da [obviEnce](http://www.obvience.com/), que foram mantidos anónimos. Os dados estão disponíveis em vários formatos: pacote de conteúdos, ficheiro .pbix do Power BI Desktop ou livro do Excel. Veja [Exemplos do Power BI](sample-datasets.md). 

Este tutorial explora o pacote de conteúdos do exemplo Supplier Quality Analysis Sample no serviço Power BI. Uma vez que a experiência do relatório é semelhante no Power BI Desktop e no serviço, também pode acompanhar com o ficheiro .pbix de exemplo no Power BI Desktop. 

Não precisa de uma licença do Power BI para explorar os exemplos no Power BI Desktop. Se não tiver uma licença do Power BI Pro, pode guardar o exemplo em A Minha Área de Trabalho no serviço Power BI. 

## <a name="get-the-sample"></a>Obter o exemplo

Para poder utilizar o exemplo, primeiro tem de transferi-lo como um [pacote de conteúdos](#get-the-content-pack-for-this-sample), um [ficheiro .pbix](#get-the-pbix-file-for-this-sample) ou um [livro do Excel](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Obter o pacote de conteúdos para este exemplo

1. Abra o serviço Power BI (app.powerbi.com), inicie sessão e abra a área de trabalho onde quer guardar o exemplo.

   Se não tiver uma licença do Power BI Pro, pode guardar o exemplo em A Minha Área de Trabalho.

2. No canto inferior esquerdo, selecione **Obter Dados**.
   
   ![Selecionar Obter Dados](media/sample-datasets/power-bi-get-data.png)
3. Na página **Obter Dados** apresentada, selecione **Exemplos**.
   
4. Selecione **Supplier Quality Analysis Sample** e, em seguida, selecione **Ligar**.  
   
   ![Ligar ao exemplo](media/sample-supplier-quality/supplier16.png)

5. O Power BI importa o pacote de conteúdos e adiciona um novo dashboard, um relatório e um conjunto de dados à área de trabalho atual.
   
   ![Entrada do exemplo Supplier Quality Analysis Sample](media/sample-supplier-quality/supplier17.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Obter o ficheiro .pbix para este exemplo

Em alternativa, pode transferir o exemplo Supplier Quality Analysis Sample como um [ficheiro .pbix](https://download.microsoft.com/download/8/C/6/8C661638-C102-4C04-992E-9EA56A5D319B/Supplier-Quality-Analysis-Sample-PBIX.pbix), concebido para utilização com o Power BI Desktop.

### <a name="get-the-excel-workbook-for-this-sample"></a>Obter o livro do Excel para este exemplo

Se quiser ver a origem de dados deste exemplo, também está disponível como um [livro do Excel](https://go.microsoft.com/fwlink/?LinkId=529779). O livro contém as folhas do Power View que pode ver e modificar. Para ver os dados não processados, ative os suplementos de Análise de Dados e, em seguida, selecione **Power Pivot > Gerir**. Para ativar os suplementos Power View e Power Pivot, veja [Observe os exemplos de Excel a partir do interior do próprio Excel](sample-datasets.md#optional-take-a-look-at-the-excel-samples-from-inside-excel-itself) para obter detalhes.

## <a name="downtime-caused-by-defective-materials"></a>Tempo de inatividade causado por materiais com defeito
Vamos analisar o tempo de inatividade causado por material defeituoso e ver os fornecedores que são responsáveis.  

1. No dashboard, selecione o mosaico **Total Defect Quantity** ou **Total Downtime Minutes**.

   ![Selecionar mosaico para abrir o relatório](media/sample-supplier-quality/supplier2.png)  

   O relatório Supplier Quality Analysis Sample abre a página **Downtime Analysis**.

   Observe que existem 33 milhões de peças com defeito, o que provoca um tempo de inatividade de 77 000 minutos. Embora alguns materiais contenham menos peças com defeito, estes podem provocar atrasos, o que por sua vez contribuirá para o aumento do tempo de inatividade. Vamos explorá-los na página do relatório.  
2. Se observarmos a linha **Total Downtime Minutes** no gráfico de combinação **Defects and Downtime (min) by Material Type**, podemos ver que os materiais ondulados causam a maior parte do tempo de inatividade.  
3. Selecione a coluna **Corrugate** para ver as fábricas que são mais afetadas por este defeito e o fornecedor responsável.  

   ![Selecionar a coluna Corrugate](media/sample-supplier-quality/supplier3.png)  
4. No mapa **Downtime (min) by Plant**, selecione uma fábrica no mapa de cada vez para ver que fornecedores ou material é responsável pelo tempo de inatividade nessa fábrica.

### <a name="which-are-the-worst-suppliers"></a>Quais são os piores fornecedores?
 Queremos encontrar os oito piores fornecedores e determinar qual é a percentagem de tempo de inatividade pela qual são responsáveis. Podemos fazê-lo ao alterar o gráfico de área **Downtime (min) by Vendor** para um treemap.  

1. Na página **Downtime Analysis** do relatório, selecione **Editar relatório** no canto superior esquerdo.  
2. Selecione o gráfico de área **Downtime (min) by Vendor** e, no painel **Visualizações**, selecione o ícone **Treemap**.  

   ![Selecionar o ícone treemap](media/sample-supplier-quality/supplier4.png)  

    O treemap define automaticamente o campo **Vendor** como **Grupo**.  

    ![Gráfico treemap de Downtime (min) by Vendor](media/sample-supplier-quality/supplier5.png)  

   Neste treemap, podemos ver quais são os oito principais fornecedores nos oito blocos à esquerda do treemap. Também podemos ver que se responsabilizam por cerca de 50% de todos os minutos de inatividade.  
3. Selecione **Supplier Quality Analysis Sample** no painel de navegação superior para voltar ao dashboard.

### <a name="comparing-plants"></a>Comparar fábricas
Agora vamos explorar as fábricas que fazem um trabalho de melhor gestão de material com defeito, resultando num tempo de inatividade inferior.  

1. No dashboard, selecione o mosaico de mapa **Total Defect Reports by Plant, Defect Type**.      

   ![Mosaico Total Defect Reports by Plant, Defect Type](media/sample-supplier-quality/supplier6.png)  

   O relatório abre a página **Supplier Quality Analysis**.  

2. Na legenda da página **Total Defect Reports por Plant e Defect Type**, selecione o círculo **Impact**.  

    ![Selecionar Impact](media/sample-supplier-quality/supplier7.png)  

    No gráfico de bolhas, verá que a categoria **Logistics** é a mais problemática. É a que apresenta maior impacto em termos da quantidade total de defeitos, relatórios de defeitos e minutos de inatividade. Vamos explorar melhor esta categoria.  
3. Selecione a bolha **Logistics** no gráfico de bolhas e observe as fábricas em Springfield e Naperville, IL. Naperville parece fazer um melhor trabalho de gestão de fornecimentos com defeitos, uma vez tem um número alto de rejeição e alguns impactos, comparado ao grande número de impactos de Springfield.  

   ![Selecionar Logistics](media/sample-supplier-quality/supplier8.png)  
4. Selecione **Supplier Quality Analysis Sample** no painel de navegação superior para voltar ao dashboard.

## <a name="which-material-type-is-best-managed"></a>Que tipo de material é melhor gerido?
O melhor tipo de material gerido é o que tem o tempo de inatividade mais baixo ou nenhum impacto, independentemente da quantidade de defeitos.

1. No dashboard, observe o mosaico **Quantidade Total de Defeitos por Tipo de Material, Tipo de Defeito**.

   ![Mosaico Total Defect Quantity by Material Type, Defect Type](media/sample-supplier-quality/supplier9.png)

   Repare que, embora o tipo de material **Raw Materials** tenha um total de defeitos elevado, a maioria dos defeitos é rejeitada ou não tem impacto.

   Vamos ver se este tipo de material não causa demasiado tempo de inatividade, apesar da quantidade de defeitos elevada.

2. No dashboard, observe o mosaico **Quantidade Total de Defeitos, Total de Minutos de Inatividade por Tipo de Material**.

   ![Mosaico Total Defect Qty, Total Downtime Minutes by Material Type](media/sample-supplier-quality/supplier10.png)

   As matérias-primas aparentam ser bem geridas. Embora tenham mais defeitos, apresentam menos minutos de inatividade total.

### <a name="compare-defects-to-downtime-by-year"></a>Comparar defeitos com o tempo de inatividade por ano
1. Selecione o mosaico de mapa **Total Defect Reports by Plant, Defect Type** para abrir o relatório na página **Supplier Quality Analysis**.
2. No gráfico **Total Defect Qty por Month e Year**, repare que a quantidade de defeitos é maior no ano de 2014 do que em 2013.  

    ![Gráfico Total Defect Qty por Month e Year](media/sample-supplier-quality/supplier11.png)  
3. Mais defeitos traduz-se em mais tempo de inatividade? Faça perguntas na caixa de Perguntas e Respostas para descobrir.  
4. Selecione **Supplier Quality Analysis Sample** no painel de navegação superior para voltar ao dashboard.  
5. Como sabemos que as matérias-primas têm o maior número de defeitos, escreva na caixa de perguntas: *show material types, year, and total defect qty* (mostrar tipos de materiais, ano e quantidade total de defeitos).  

    Havia muitos mais defeitos de matérias-primas em 2014 do que em 2013.  

    ![Pergunta nas Perguntas e Respostas: show material types, year and total defect qty (mostrar tipos de materiais, ano e quantidade total de defeitos)](media/sample-supplier-quality/supplier12.png)  
6. Em seguida, altere a pergunta para: _show material types, year, and total **downtime minutes**_ (mostrar tipos de materiais, ano e total de minutos de tempo de inatividade).  

   ![Pergunta nas Perguntas e Respostas: show material types, year and total downtime minutes (mostrar tipos de materiais, ano e total de minutos de tempo de inatividade)](media/sample-supplier-quality/supplier13.png)

   Repare que o tempo de inatividade para matérias-primas foi quase o mesmo em 2013 e 2014, mesmo que tenha havido muito mais defeitos do que matérias-primas em 2014. Aparentemente, a existência de mais defeitos comparativamente a matérias-primas em 2014 não causou um grande tempo de inatividade adicional para as matérias-primas em 2014.

### <a name="compare-defects-to-downtime-month-to-month"></a>Compare defeitos com o tempo de inatividade mês a mês
Vejamos outro mosaico de dashboard relacionado com a quantidade total de defeitos.  

1. Selecione **Sair das Perguntas e Respostas** no canto superior esquerdo para voltar ao dashboard.  

    Observe o mosaico **Total Defect Quantity by Month, Year** mais atentamente. Este permite ver que o primeiro semestre de 2014 teve um número semelhante de defeitos a 2013, mas que, no segundo semestre de 2014, o número de defeitos aumentou significativamente.  

    ![Mosaico Total Defect Quantity by Month, Year](media/sample-supplier-quality/supplier14.png)  

    Vamos ver se este aumento na quantidade de defeitos conduziu a um aumento igual em minutos do tempo de inatividade.  
2. Na caixa de perguntas, escreva *total downtime minutes by month and year as a line chart* (total de minutos de inatividade por mês e ano como um gráfico de linhas).  

   ![Pergunta nas Perguntas e Respostas: Total downtime minutes by month and year as a line chart (total de minutos de inatividade por mês e ano como um gráfico de linhas)](media/sample-supplier-quality/supplier15.png)

   Em vez de um salto nos minutos de inatividade durante junho e outubro, o número de defeitos não resultou num tempo de inatividade consideravelmente maior. Este resultado mostra que estamos a gerir bem os defeitos.  
3. Para afixar este gráfico no seu dashboard, selecione o ícone de afixar ![Ícone de afixar](media/sample-supplier-quality/pin.png) por cima da caixa de perguntas.  
4. Para explorar os meses de exceções, verifique os minutos de tempo de inatividade durante outubro por tipo de material, localização da fábrica, categoria e assim por diante ao fazer perguntas como *total downtime minutes in October by plant* (minutos de tempo de inatividade total em outubro pela fábrica). 
5. Selecione **Sair das Perguntas e Respostas** no canto superior esquerdo para voltar ao dashboard.

## <a name="next-steps-connect-to-your-data"></a>Próximos passos: Ligar aos seus dados
Aqui pode explorar à vontade, pois pode optar por não guardar as alterações. No entanto, se as guardar, pode sempre aceder a **Obter Dados** para obter uma nova cópia deste exemplo.

Esperamos que esta apresentação tenha mostrado como os dashboards, as Perguntas e Respostas e os relatórios do Power BI podem fornecer informações sobre os dados do exemplo. Agora, é a sua vez: ligue-se aos seus próprios dados. Com o Power BI, pode ligar-se a uma grande variedade de origens de dados. Para saber mais, veja [Introdução ao serviço Power BI](service-get-started.md).
