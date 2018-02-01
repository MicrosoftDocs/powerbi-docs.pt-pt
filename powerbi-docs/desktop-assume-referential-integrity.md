---
title: "Definição Assumir integridade referencial no Power BI Desktop"
description: Com o DirectQuery, saiba como o Power BI Desktop pode assumir a integridade referencial
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
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: 7e3f496980fdd8039b4319bc50753efc1223bde4
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="assume-referential-integrity-settings-in-power-bi-desktop"></a>Definições Assumir Integridade Referencial no Power BI Desktop
Quando ligar a uma origem de dados através do **DirectQuery**, pode utilizar a seleção **Assumir Integridade Referencial** para ativar a execução de consultas mais eficientes relativamente à origem de dados. Esta funcionalidade tem alguns requisitos dos dados subjacentes e só está disponível quando utilizar o **DirectQuery**.

A definição **Assumir Integridade Referencial** permite às consultas na origem de dados utilizar instruções **INNER JOIN** em vez de **OUTER JOIN**, o que melhora a eficiência da consulta.

![](media/desktop-assume-referential-integrity/assume-referential-integrity_1.png)

## <a name="requirements-for-using-assume-referential-integrity"></a>Requisitos para utilizar Assumir Integridade Referencial
Esta é uma definição avançada e só é ativada quando ligar aos dados através do **DirectQuery**. Os requisitos seguintes são necessários para o correto funcionamento de **Assumir Integridade Referencial**:

* Os dados na coluna **De** na relação nunca são *Nulos* nem podem estar *em branco*
* Para cada valor na coluna **De**, existe um valor correspondente na coluna **Para**

Neste contexto, a coluna **De** é a parte *Muitos* na relação *Um-para-Muitos* ou é a coluna na primeira tabela numa relação *Um-para-Um*.

## <a name="example-of-using-assume-referential-integrity"></a>Exemplo da utilização de Assumir Integridade Referencial
O exemplo seguinte demonstra como se comporta a funcionalidade **Assumir Integridade Referencial** quando utilizada em ligações de dados. O exemplo liga a uma origem de dados que inclui as tabelas **Orders**, **Products** e **Depots**.

1. Na imagem seguinte que mostra as tabelas **Orders** e **Products**, tenha em atenção que existe integridade referencial entre **Orders[ProductID]** e **Products[ProductID]**. A coluna **[ProductID]** na tabela **Orders** nunca é *Nula* e cada valor também aparece na tabela **Products**. Como tal, **Assumir Integridade Referencial** deve ser definido para obter consultas mais eficientes (esta definição não altera os valores apresentados nos elementos visuais).
   
   ![](media/desktop-assume-referential-integrity/assume-referential-integrity_2.png)
2. Na imagem seguinte, tenha em atenção que não existe integridade referencial entre **Orders[DepotID]** e **Depots[DepotID]**, uma vez que o **DepotID** é *Nulo* para algumas *Orders*. Como tal, **Assumir Integridade Referencial** *não* deve ser definido.
   
   ![](media/desktop-assume-referential-integrity/assume-referential-integrity_3.png)
3. Por fim, não existe integridade referencial entre **Orders[CustomerID]** e **Customers[CustID]** nas tabelas seguintes; **CustomerID** contém alguns valores (neste caso, *CustX*) que não existem na tabela *Customers*. Como tal, **Assumir Integridade Referencial** *não* deve ser definido.
   
   ![](media/desktop-assume-referential-integrity/assume-referential-integrity_4.png)

## <a name="setting-assume-referential-integrity"></a>Definição Assumir Integridade Referencial
Para ativar esta funcionalidade, selecione a caixa de verificação junto a **Assumir Integridade Referencial**, conforme mostrado na imagem seguinte.

![](media/desktop-assume-referential-integrity/assume-referential-integrity_1.png)

Quando selecionada, a definição é validada com os dados para assegurar que não existem linhas *Nulas* ou sem correspondência. *No entanto*, nos casos com um grande número de valores, a validação não é uma garantia de que não existem problemas de integridade referencial.

Além disso, a validação ocorre no momento da edição da relação e *não* reflete as alterações subsequentes aos dados.

## <a name="what-happens-if-you-incorrectly-set-assume-referential-integrity"></a>O que acontece se definir incorretamente a funcionalidade Assumir Integridade Referencial?
Se definir **Assumir Integridade Referencial** quando existem problemas de integridade referencial nos dados, isto não causará erros. No entanto, resultará em inconsistências aparentes nos dados. Por exemplo, no caso da relação com a tabela **Depots** descrita acima, iria originar o seguinte:

* Um elemento visual que mostra o total de *Order Qty* mostraria um valor de 40
* Um elemento visual que mostra o total de *Order Qty by Depot City* mostraria um valor total de apenas *30*, uma vez que não inclui o ID de Encomenda 1, em que **DepotID** é *Nulo*.

## <a name="next-steps"></a>Próximos passos
Saiba mais sobre o [DirectQuery](desktop-use-directquery.md)

Obtenha mais informações sobre [Relações no Power BI](desktop-create-and-manage-relationships.md)

Saiba mais sobre [Vista de Relações no Power BI Desktop](desktop-relationship-view.md).
