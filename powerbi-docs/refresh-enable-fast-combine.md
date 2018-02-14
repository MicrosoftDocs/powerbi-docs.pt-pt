---
title: "Desativar as definições de privacidade"
description: "Como ativar a Combinação Rápida no Personal Gateway para desativar as definições de privacidade para atualização."
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
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 02/06/2018
ms.author: davidi
ms.openlocfilehash: 5d754dbdd5d52e7a5b123755015e656d9fb2cea2
ms.sourcegitcommit: db37f5cef31808e7882bbb1e9157adb973c2cdbc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/09/2018
---
# <a name="disable-privacy-setting-in-power-bi-gateway---personal"></a>Desativar a definição de privacidade no Power BI Gateway - Personal
> [!NOTE]
> Há uma nova versão do gateway pessoal para Power BI, com o nome de **gateway de dados no local (modo pessoal)**. O artigo seguinte descreve a versão anterior do gateway pessoal, com o nome de **Power BI Gateway - Personal**, que vai ser descontinuado e deixa de funcionar após 31 de julho de 2017. Para obter informações sobre a nova versão do gateway pessoal, incluindo como instalar a nova versão, consulte o artigo [**Gateway de dados no local (modo pessoal)**](service-gateway-personal-mode.md). A combinação rápida também está disponível na nova versão do gateway pessoal e também está descrita nesse artigo.
> 
> 

Pode receber o seguinte erro com base nas definições de privacidade para as suas origens de dados quando utilizadas com o gateway pessoal.

> *Ocorreu um erro ao processar os dados no conjunto de dados.*
> 
> *[Não é possível combinar dados] &lt;parte da consulta&gt;/&lt;…&gt;/&lt;…&gt; está a aceder a origens de dados com níveis e privacidade que não podem ser utilizados em conjunto. Recompile esta combinação de dados.*
> 
> 

Para resolver este erro, pode ativar a **Combinação Rápida**. A **Combinação Rápida** ignorará as definições de privacidade ao permitir que sejam combinadas diferentes origens de dados.

> [!NOTE]
> Os níveis de privacidade não são considerados ao combinar dados. Isto poderia expor dados confidenciais a outra origem de dados ao combinar os dados.
> 
> 

## <a name="what-is-fast-combine"></a>O que é a Combinação Rápida?
Para saber mais sobre níveis de privacidade e a Combinação Rápida, veja [Níveis de Privacidade](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540). Por predefinição, o nível de privacidade será definido para privado, o que poderá resultar no erro mencionado acima. Isto ocorre porque uma definição privada isolará a origem de dados de outras origens. Um exemplo de onde isto seria um problema é uma consulta parametrizada que está a obter entradas de outra origem de dados.

A ativação da Combinação Rápida ignorará a definição privada e permitirá que a execução ocorra.

## <a name="turn-on-fast-combine"></a>Ativar a Combinação Rápida
Pode utilizar os passos a seguir para ativar a Combinação Rápida para o seu gateway. O gateway de dados no local não tem esta definição.

1. Abra **ConnectorConfig.xml**.  Isto pode estar numa de duas localizações no seu computador.  Se for um administrador no computador, será a seguinte.
   
    <pre><code>C:\Program Files\Power BI Personal Gateway\1.0\Configurator\Connector</code></pre>
   
    Se não for um administrador, a localização será a seguinte.
   
    <pre><code>C:\Users\[username]\AppData\Local\Power BI Personal Gateway\1.0\Configurator\Connector</code></pre>
    
2. Adicione o elemento**&lt;EnableFastCombine&gt;** com um valor true ao ficheiro de configuração. A adição deste elemento ativará a **Combinação Rápida**.
   
   <pre><code>&lt;EnableFastCombine&gt;true&lt;/EnableFastCombine&gt;</code></pre>
   
   ![](media/refresh-enable-fast-combine/configfile.png)
3. Saia e reinicie o ecrã de configuração do gateway.
4. Verá um estado a informar que a Combinação Rápida está ativada.
   
   ![](media/refresh-enable-fast-combine/fastcombineenabled.png)

## <a name="turn-off-fast-combine"></a>Desativar a Combinação Rápida
1. Abra **ConnectorConfig.xml**.  Isto pode estar numa de duas localizações no seu computador.  Se for um administrador no computador, será a seguinte.
   
    <pre><code>C:\Program Files\Power BI Personal Gateway\1.0\Configurator\Connector</code></pre>
   
    Se não for um administrador, a localização será a seguinte.
   
    <pre><code>C:\Users\[username]\AppData\Local\Power BI Personal Gateway\1.0\Configurator\Connector</code></pre>

2. Remova o elemento **&lt;EnableFastCombine&gt;** do ficheiro de configuração. A remoção deste elemento desativará a **Combinação Rápida**.
3. Saia e reinicie o ecrã de configuração do gateway.
4. Deixará de ver um estado a indicar que a **Combinação Rápida** está ativada.

## <a name="next-steps"></a>Próximos passos
[Gateway de dados local (modo pessoal) - a nova versão do gateway pessoal](service-gateway-personal-mode.md)
[Níveis de Privacidade](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)  
[Tarefas comuns de consulta no Power BI Desktop](desktop-common-query-tasks.md)  
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

