---
title: Resolver problemas com o desenvolvimento de elementos visuais personalizados do Power BI
description: Este artigo aborda alguns problemas comuns que poderá encontrar ao desenvolver ou criar um elemento visual personalizado do Power BI.
author: sranins
ms.author: rasala
manager: kfile
ms.reviewer: maghan
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 11/06/2018
ms.openlocfilehash: cbda8cca80c32056f06788e53540d7f2d6ed972d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61421799"
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

Não hesite em enviar perguntas, comentários ou comunicar problemas à equipa de suporte de elementos visuais personalizados para o endereço:  *pbicvsupport@microsoft.com*  .

## <a name="next-steps"></a>Próximos passos

Para obter mais informações, visite [Perguntas frequentes sobre os elementos visuais personalizados do Power BI](power-bi-custom-visuals-faq.md#organizational-custom-visuals).
