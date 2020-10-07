---
title: API Power BI a utilizar uma política de retenção automática para os dados em tempo real
description: Saiba mais acerca da política de retenção automática no serviço Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: b36a5f819ba39d5a77dafc670e440f3577014570
ms.sourcegitcommit: be424c5b9659c96fc40bfbfbf04332b739063f9c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/01/2020
ms.locfileid: "91635131"
---
# <a name="automatic-retention-policy-for-real-time-data"></a>Automatic retention policy for real-time data (Política de retenção automática para dados em tempo real)

A política de retenção automática no serviço Power BI é um parâmetro de cadeia de consulta que permite a uma política de retenção predefinida limpar automaticamente os dados antigos, enquanto mantém um fluxo constante de dados novos a entrar no dashboard. A primeira política de retenção é denominada *first in first out (FIFO)* . Quando ativada, os dados são recolhidos numa tabela, até que esta atinja as 200 000 linhas. Assim que os dados excedam as 200 000 linhas, as linhas mais antigas são removidas do conjunto de dados. Desta forma, mantém entre 200 000 e 210 000 linhas com apenas os dados mais recentes.  
  
<center>

![política de retenção](media/api-Automatic-retention-policy-for-real-time-data/retention-policy.png) 

</center>

As políticas de retenção são ativadas quando cria pela primeira vez os conjuntos de dados. Tudo o que precisa de fazer é adicionar o parâmetro de consulta "política de retenção predefinida" à sua chamada de conjuntos de dados POST e definir a mesma para que fique igual a *basicFIFO*.  

```console
POST https://api.powerbi.com/v1.0/myorg/datasets?defaultRetentionPolicy={None | basicFIFO}
```
