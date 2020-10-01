---
title: Criar parâmetros para relatórios paginados no serviço Power BI
description: Neste artigo, vai aprender a criar parâmetros para relatórios paginados no serviço Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 09/28/2020
ms.openlocfilehash: 3a755b2b4eeba407178d7afa0a0250b6897e6dac
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/29/2020
ms.locfileid: "91526358"
---
# <a name="create-parameters-for-paginated-reports-in-the-power-bi-service"></a>Criar parâmetros para relatórios paginados no serviço Power BI

Neste artigo, vai aprender a criar parâmetros para relatórios paginados no serviço Power BI.  Um parâmetro de relatório proporciona uma forma de escolher os dados do relatório e de variar a apresentação do relatório. Pode fornecer um valor predefinido e uma lista de valores disponíveis. Os leitores do relatório podem alterar a seleção. Eles também podem escrever nas caixas de texto de parâmetro para procurar valores. Veja [Ver parâmetros de relatórios paginados](../consumer/paginated-reports-view-parameters.md) para ver como os utilizadores empresariais interagem com os parâmetros no serviço Power BI.  

A ilustração seguinte mostra a vista Estrutura no Report Builder do Power BI para um relatório com os parâmetros @BuyingGroup, @Customer, @FromDate e @ToDate. 
  
![Parâmetros no Report Builder](media/paginated-reports-parameters/power-bi-paginated-parameters-report-builder.png)
  
1.  Os parâmetros do relatório no painel Dados do Relatório.  
  
2.  A tabela com um dos parâmetros no conjunto de dados.  
  
3.  O painel Parâmetros. Pode personalizar o layout dos parâmetros no painel de parâmetros. 
  
4.  Os parâmetros @FromDate e @ToDate têm o tipo de dados **DateTime**. Ao visualizar o relatório, pode escrever uma data na caixa de texto ou escolher uma data no controlo de calendário. 

5.  Um dos parâmetros na caixa de diálogo **Propriedades do conjunto de dados**.  

  
## <a name="create-or-edit-a-report-parameter"></a>Criar ou editar um parâmetro de relatório  
  
1.  Abra o relatório paginado no Report Builder do Power BI.

1. No painel **Dados do Relatório**, clique com o botão direito do rato no nó **Parâmetros** > **Adicionar Parâmetro**. A caixa de diálogo **Propriedades do Parâmetro de Relatório** é apresentada.  
  
2.  Em **Nome**, escreva um nome para o parâmetro ou aceite o nome predefinido.  
  
3.  Em **Pedido**, escreva um texto para aparecer ao lado da caixa de texto do parâmetro quando o utilizador executar o relatório.  
  
4.  Em **Tipo de dados**, selecione o tipo de dados para o valor do parâmetro.  
  
5.  Se o parâmetro puder conter um valor em branco, selecione **Permitir valor em branco**.  
  
6.  Se o parâmetro puder conter um valor nulo, selecione **Permitir valor nulo**.  
  
7.  Para permitir que um utilizador selecione mais do que um valor para o parâmetro, selecione **Permitir vários valores**.  
  
8.  Defina a opção de visibilidade.  
  
    -   Para mostrar o parâmetro na barra de ferramentas na parte superior do relatório, selecione **Visível**.  
  
    -   Para ocultar o parâmetro para que não seja apresentado na barra de ferramentas, selecione **Oculto**.  
  
    -   Para ocultar o parâmetro e protegê-lo de ser modificado no servidor de relatórios depois de o relatório ser publicado, selecione **Interno**. O parâmetro de relatório pode então ser apenas apresentado na definição do relatório. Para esta opção, tem de definir um valor predefinido ou permitir que o parâmetro aceite um valor nulo.  
  
9. Selecione **OK**. 

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas

- Se estiver a utilizar um conjunto de dados do Power BI ou um modelo do Analysis Services como origem de dados, não poderá transmitir mais de 1000 valores de parâmetro num único pedido. O DAX limita os parâmetros a 1000 valores. 

 
## <a name="next-steps"></a>Passos seguintes

Veja [Ver parâmetros dos relatórios paginados](../consumer/paginated-reports-view-parameters.md) para ver o aspeto dos parâmetros no serviço Power BI.

Para obter informações aprofundadas sobre parâmetros em relatórios paginados, veja [Report parameters in Power BI Report Builder](report-builder-parameters.md) (Parâmetros de relatórios no Report Builder do Power BI).
