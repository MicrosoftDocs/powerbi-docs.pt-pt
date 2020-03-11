---
title: Transmitir um parâmetro de relatório num URL para um relatório paginado – Power BI Report Builder
description: Este tópico descreve como pode transmitir parâmetros de relatório para um relatório ao incluí-los num URL de relatório paginado.
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 08/29/2019
ms.openlocfilehash: b8301ca17559b81d4db132fbeaa0955ce68a4c6e
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/07/2020
ms.locfileid: "78922534"
---
# <a name="pass-a-report-parameter-in-a-url-for-a-paginated-report-in-power-bi"></a>Transmitir um parâmetro de relatório num URL para um relatório paginado no Power BI 

Pode transmitir parâmetros de relatório para um relatório ao incluí-los num URL de relatório paginado. Todos os parâmetros de consulta podem ter parâmetros de relatório correspondentes. Por conseguinte, pode transmitir um parâmetro de consulta para um relatório ao transmitir o parâmetro de relatório correspondente. Tem de colocar o prefixo `rp:` no nome do parâmetro para que o Power BI o reconheça no URL. 

Os parâmetros de relatório são sensíveis às maiúsculas e minúsculas e utilizam os seguintes carateres especiais: 

- Os espaços na porção de parâmetro do URL são substituídos por sinais de adição (+).  Por exemplo: 

    ```rp:Holiday=Christmas+Day```

- Os sinais de ponto e vírgula em qualquer porção da cadeia são substituídos pelos carateres `%3A`.

Os browsers deverão efetuar automaticamente a codificação do URL mais adequada. Não tem de codificar nenhum dos carateres manualmente. 

Para definir um parâmetro de relatório num URL, utilize a seguinte sintaxe: 

```
rp:parameter=value
```

Por exemplo, para especificar dois parâmetros – "Salesperson" (Representante de Vendas) e "State" (Estado) – definidos num relatório na sua área A Minha Área de Trabalho, terá de utilizar o seguinte URL: 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:State=Utah 
```

Para especificar os mesmos dois parâmetros definidos num relatório numa aplicação, terá de utilizar o seguinte URL: 

```
https://app.powerbi.com/groups/me/apps/xxxxxxx-c4c4-4217-afd9-3920a0d1e2b0/rdlreports/b1d5e659-639e-41d0-b733-05d2bca9853c?rp:Salesperson=Tiggee&State=Utah 
```

Para transmitir um valor nulo a um parâmetro, utilize a seguinte sintaxe: 

```
parameter:isnull=true
```

Por exemplo:

```
rp:SalesOrderNumber:isnull=true
```

Para transmitir um valor booleano, utilize 0 para falso e 1 verdadeiro. Para transmitir um valor Flutuante, inclua o separador decimal da região do servidor.

> [!NOTE]
> Se o seu relatório contiver um parâmetro de relatório com um valor predefinido e o valor da propriedade **Prompt** for **falso** (ou seja, se a propriedade **Prompt User** não estiver selecionada no Report Manager), não poderá transmitir um valor a esse parâmetro de relatório num URL. Isto permite que os administradores possam impedir os utilizadores finais de adicionarem ou modificarem os valores de determinados parâmetros de relatório.

> O Power BI não suporta uma cadeia de consulta com mais de 900 carateres.  Este valor pode ser excedido se estiver a utilizar parâmetros de URL para ver o seu relatório paginado.  Isto aplica-se sobretudo se estiver a utilizar parâmetros de múltiplos valores.

## <a name="additional-examples"></a>Exemplos adicionais 

O seguinte URL de exemplo inclui um parâmetro "Salesperson" de múltiplos valores. O formato para um parâmetro de múltiplos valores consiste em repetir o nome do parâmetro para cada valor. 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:Salesperson=Mickey 
```

O seguinte URL de exemplo transmite um único parâmetro de  SellStartDate  com um valor de "7/1/2005" a um servidor de relatórios de modo nativo.

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:SellStartDate=7/1/2005
```

## <a name="next-steps"></a>Próximos passos

- [Parâmetros de URL em relatórios paginados no Power BI](report-builder-url-parameters.md)
- [O que são relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)
