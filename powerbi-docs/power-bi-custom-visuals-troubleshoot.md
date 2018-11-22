---
title: Resolver problemas com o desenvolvimento de elementos visuais personalizados do Power BI
description: Este artigo aborda alguns problemas comuns que poderá encontrar ao desenvolver ou criar um elemento visual personalizado do Power BI.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 11/06/2018
ms.openlocfilehash: 3d9e8e46fdd84edbeb5b4ff5e8f7efe4a4291049
ms.sourcegitcommit: a739a99e1006834a0f56e387c0bd9d945fb8a76b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51679261"
---
# <a name="troubleshoot-power-bi-custom-visuals"></a>Troubleshoot Power BI custom visuals (Resolver problemas com elementos visuais personalizados do Power BI)

## <a name="debug"></a>Debug

**Comando Pbiviz não encontrado (ou erros semelhantes)**

Ao executar `pbiviz` na linha de comandos do seu terminal, deverá ver o ecrã de ajuda. Caso contrário, o comando não está instalado corretamente. Certifique-se de que tem, pelo menos, a versão 4.0 do NodeJS instalada.

**Não é possível localizar o elemento visual de depuração no separador Visualizações**

O elemento visual de depuração é parecido com um ícone de linha de comandos no separador **Visualizações**.

![Seleção de elementos visuais](media/power-bi-custom-visuals-troubleshoot/powerbi-developer-visual-selection.png)

Se não o vir, certifique-se de que está ativado nas definições do Power BI.

> [!NOTE]
> O elemento visual de depuração está apenas disponível no serviço Power BI e não no Power BI Desktop ou na aplicação móvel. O elemento visual vai continuar a funcionar por todo o lado.

**Não é possível contactar o servidor visual**

Execute o servidor do elemento visual com o comando `pbiviz start` na linha de comandos do seu terminal a partir da raiz do projeto do seu elemento visual. Se o servidor não estiver em execução, é provável que os seus certificados SSL não tenham sido instalados corretamente.

## <a name="next-steps"></a>Passos seguintes

Para obter mais informações e respostas a perguntas, aceda às [Perguntas frequentes sobre os elementos visuais personalizados do Power BI](power-bi-custom-visuals-faq.md#organizational-custom-visuals).
