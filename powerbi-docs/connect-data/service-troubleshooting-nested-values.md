---
title: Resolução de Problemas de Valores Aninhados devolvidos como Texto no serviço Power BI
description: Aprenda a corrigir a conversão de valores aninhados numa cadeia devido à utilização de definições de privacidade de origens de dados inadequadas
author: cpopell
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 6/4/2019
ms.author: gepopell
LocalizationGroup: Reports
ms.openlocfilehash: ab40ca9c415dacf52f4d82eb2c157d57aef92f93
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83332780"
---
# <a name="troubleshooting-nested-values-returned-as-text-in-power-bi-service"></a>Resolução de Problemas de Valores Aninhados devolvidos como Texto no serviço Power BI

## <a name="cause"></a>Motivo

Anteriormente, ocorreram casos em que era possível atualizar um relatório do Power BI no Power BI Desktop, mas a atualização falhava no serviço Power BI, com uma mensagem de erro como "Não conseguimos converter o valor "[Table]" para o tipo Tabela". Uma das causas deste problema é o facto de os valores não escalares aninhados (como tabelas, registos, listas e funções) serem automaticamente convertidos em valores de texto (como "[Table]" ou "[Record]") quando a Firewall de Privacidade de Dados coloca uma origem de dados em memória intermédia.

Agora que o serviço Power BI suporta a definição de níveis de privacidade (ou a desativação total da Firewall), estes problemas podem ser evitados ao [configurar as definições de privacidade de origens de dados](https://powerbi.microsoft.com/blog/privacy-levels-for-cloud-data-sources/) no serviço Power BI para que as origens não sejam privadas.

A partir da versão de junho do Power BI, quando a Firewall colocar um(a) tabela/registo/lista/etc. aninhado(a) em memória intermédia, em vez de estes valores serem automaticamente convertidos em texto, será apresentada a seguinte mensagem de erro: 

`We cannot return a value of type Table in this context`

## <a name="effect-on-loadrefresh"></a>Efeito no Carregamento ou na Atualização

Embora a alteração seja motivada pela colocação em memória intermédia por parte da Firewall, também afeta o Carregamento ou a Atualização. Para resolver o comportamento de colocação em memória intermédia assumido pela Firewall, também tivemos de alterar o comportamento do carregamento de tabelas/registos/etc. aninhados(as) para o Modelo do Power BI e o Modelo de Dados do Excel no PQ para Excel. Anteriormente, os(as) tabelas/registos/etc. aninhados(as) eram carregados(as) como valores de texto (como "[Table]" ou "[Record]"). Agora, serão tratados como erros, o que irá resultar num valor nulo na tabela carregada e num aumento do número de erros nos resultados do carregamento.

Como estes erros apenas ocorrem durante o Carregamento ou a Atualização, não irão aparecer no Editor do Power Query.

### <a name="before"></a>Antes de

- Carregamento ou Atualização sem erros
- A tabela carregada continha "[Table]", "[Record]", etc.
 

### <a name="after"></a>Depois de

- Carregamento ou Atualização com erros
- A tabela carregada contém valores NULL (em vez de "[Table]", "[Record]", etc.)
 

## <a name="resolution"></a>Resolução

Quer carregar uma coluna que contém valores não escalares (por exemplo, tabelas, listas, registos, etc.)?
Se for este o caso, deve conseguir eliminar os erros ao remover a coluna.
Se não conseguir remover a coluna, deve conseguir replicar o comportamento antigo ao adicionar uma coluna personalizada e utilizar lógica como a do seguinte exemplo:

`if [MyColumn] is table then "[Table]" else if [MyColumn] is record then "[Record]" else if [MyColumn] is list then "[List]" else if [MyColumn] is function then "[Function]" else [MyColumn]`

O problema ocorre no Power BI Desktop se definir todas as definições de privacidade de origens de dados para Privado?
Se for este o caso, deve conseguir resolver o erro ao [configurar as definições de privacidade de origens de dados](https://powerbi.microsoft.com/blog/privacy-levels-for-cloud-data-sources/) no serviço Power BI para que as origens não sejam privadas.
