---
title: Resolução de problemas relacionados com a programação de elementos visuais do Power BI na análise incorporada do Power BI para melhores informações de BI incorporadas
description: Este artigo aborda alguns problemas comuns que poderá encontrar ao desenvolver ou criar um elemento visual personalizado do Power BI. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: troubleshooting
ms.date: 11/06/2018
ms.openlocfilehash: 440bb6648dca1eaa85b697a10e9fd41180c66d7e
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888104"
---
# <a name="troubleshoot-power-bi-visuals"></a>Troubleshoot Power BI visuals (Resolver problemas com os elementos visuais do Power BI)

## <a name="debug"></a>Depurar

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

Não hesite em enviar perguntas, fazer comentários ou comunicar problemas à equipa de suporte de elementos visuais do Power BI para o endereço: pbicvsupport@microsoft.com.

## <a name="next-steps"></a>Passos seguintes

Para obter mais informações, veja [Perguntas frequentes sobre os elementos visuais do Power BI](power-bi-custom-visuals-faq.md#organizational-power-bi-visuals).