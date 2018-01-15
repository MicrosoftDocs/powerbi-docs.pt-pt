---
title: Utilizar etiquetas de hierarquia inline no Power BI Desktop
description: Utilizar etiquetas de hierarquia inline no Power BI Desktop
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: 6246e46cae9b44fbc9858b8fa9979dd01b80a6ab
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2017
---
# <a name="use-inline-hierarchy-labels-in-power-bi-desktop"></a>Utilizar etiquetas de hierarquia inline no Power BI Desktop
O **Power BI Desktop** suporta a utilização de **etiquetas de hierarquia inline**, a primeira de duas funcionalidades destinadas a melhorar a desagregação hierárquica. A segunda funcionalidade, atualmente em desenvolvimento, é a capacidade de utilizar etiquetas de hierarquia aninhadas (esteja atento; as nossas atualizações ocorrem frequentemente).   

## <a name="how-inline-hierarchy-labels-work"></a>Como funcionam as etiquetas de hierarquia inline
Com as etiquetas de hierarquia inline, pode ver as etiquetas de hierarquia à medida que expande os elementos visuais através da funcionalidade **Expandir Tudo**. Uma vantagem excelente para ver estas etiquetas de hierarquia é o facto de também poder optar por **ordenar** por estas etiquetas de hierarquia diferentes à medida que expande os dados hierárquicos.

### <a name="using-the-built-in-expand-all-feature-without-sorting-by-hierarchy-labels"></a>Utilizar a funcionalidade Expandir Tudo incorporada (sem ordenar por etiquetas de hierarquia)
Antes de vermos as etiquetas de hierarquia inline em ação, vamos rever o comportamento da funcionalidade **Expandir Tudo**. Fazê-lo ajuda-nos a compreender (e a agradecer) a utilidade das etiquetas de hierarquia inline.

A imagem seguinte mostra um elemento visual de gráfico de barras de vendas anuais. Ao clicar com o botão direito do rato, pode selecionar **Expandir Tudo**.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_4.png)

Depois de selecionar **Expandir Tudo**, o elemento visual expande a hierarquia de datas de *Ano* até *Trimestre*, conforme mostrado na imagem seguinte.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_5.png)

Tenha em atenção que as etiquetas *Ano* e *Trimestre* são apresentadas inline... este esquema de etiquetas continua à medida que seleciona **Expandir Tudo** até à parte inferior da hierarquia.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_6.png)

É assim que se comporta a hierarquia *Data* incorporada, associada a campos que tenham um tipo de dados *data/hora*. Vamos avançar para a secção seguinte e ver como é diferente a nova funcionalidade de etiquetas de hierarquia inline.

### <a name="using-inline-hierarchy-labels"></a>Utilizar etiquetas de hierarquia inline
Agora, vamos ver um gráfico diferente, através de dados com hierarquias informais. No elemento visual seguinte, está um gráfico de barras com **Valor de Vendas**, com *Cor* como eixo. Nestes dados, *Cor* e *Classe* formam uma hierarquia informal. A partir daqui, pode selecionar novamente *Expandir Tudo* para desagregar a hierarquia.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_7.png)

A seleção de **Expandir Tudo** mostra o nível seguinte com a apresentação inline das etiquetas de hierarquia. Por predefinição, as hierarquias inline são ordenadas pelo valor de medida, neste caso, **SalesAmount**. Com as etiquetas de hierarquia inline ativadas, pode optar por ordenar estes dados pela hierarquia, ao selecionar as reticências no canto superior direito (**...**) e, em seguida, ao selecionar **Ordenar Por > Classe de Cor**, conforme mostrado na imagem seguinte.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_8.png)

Quando **Classe de Cor** estiver selecionado, os dados são ordenados com base na seleção de hierarquia informal, conforme mostrado na imagem seguinte.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_9.png)

> [!NOTE]
> A funcionalidade de etiquetas de hierarquia inline ainda não permite ordenar a hierarquia de tempo incorporada por valor; é ordenada apenas pela ordem de hierarquia.
> 
> 

## <a name="troubleshooting"></a>Resolução de problemas
É possível que os elementos visuais fiquem bloqueados num estado de nível de hierarquia inline expandido. Em alguns casos, pode verificar que alguns dos elementos visuais estão bloqueados no modo a partir do qual foram expandidos. Nesse caso, a agregação não funciona. Isto pode acontecer se seguiu os passos seguintes (a correção está *abaixo* destes passos):

Passos que podem bloquear os elementos visuais num estado expandido:

1. Ativar a funcionalidade de **etiquetas de hierarquia inline**
2. Criar alguns elementos visuais com hierarquias
3. **Expandir Tudo** e guardar o ficheiro
4. *Desativar* a funcionalidade de **etiquetas de hierarquia inline** e reiniciar o Power BI Desktop
5. Voltar a abrir o ficheiro

Se seguiu esses passos e os elementos visuais estiverem bloqueados no modo expandido, pode efetuar o seguinte procedimento para resolver o problema:

1. Volte a ativar a funcionalidade de **etiquetas de hierarquia inline** e reinicie o Power BI Desktop
2. Volte a abrir o ficheiro e agregue até ao topo dos elementos visuais afetados
3. Guarde o ficheiro
4. Desative a funcionalidade de **etiquetas de hierarquia inline** e reinicie o Power BI Desktop
5. Volte a abrir o ficheiro

Em alternativa, pode simplesmente eliminar o elemento visual e recriá-lo.

