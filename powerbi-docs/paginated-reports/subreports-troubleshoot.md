---
title: Resolver problemas de sub-relatórios em relatórios paginados do Power BI
description: Neste artigo, irá ficar a conhecer as origens de dados suportadas para relatórios paginados no serviço Power BI e irá saber como ligar a origens de dados da Base de Dados SQL do Azure.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 04/29/2020
ms.openlocfilehash: 6de85f6dda69e902a98d6ee63d1fc4b86fb4180b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82615640"
---
# <a name="troubleshoot-subreports-in-power-bi-paginated-reports"></a>Resolver problemas de sub-relatórios em relatórios paginados do Power BI

Por vezes, ao utilizar sub-relatórios em relatórios paginados, a funcionalidade pode não funcionar conforme esperado ou pode devolver resultados inesperados. Este artigo apresenta soluções para problemas comuns ao utilizar sub-relatórios. Um *sub-relatório* é um item de relatório que apresenta outro relatório no corpo de um relatório paginado principal. Veja [Sub-relatórios em relatórios paginados do Power BI](subreports.md) para obter mais informações de contexto.

## <a name="subreport-couldnt-be-found"></a>Não foi possível encontrar o sub-relatório

**Descrição:** O sub-relatório não é composto. É apresentada uma mensagem de erro.

### <a name="message"></a>Mensagem

"O sub-relatório 'Sub-relatório1' não foi encontrado na localização especificada 'CustomerDetails'. Verifique se o sub-relatório foi publicado se o nome é correto."

### <a name="possible-reasons"></a>Motivos possíveis

- Não existe um sub-relatório com o nome especificado na mesma área de trabalho ou aplicação que o relatório principal.
- O utilizador não tem acesso ao sub-relatório.
- O número de sub-relatórios no relatório principal atingiu o limite de sub-relatórios (50 sub-relatórios).

### <a name="troubleshooting-steps"></a>Passos de resolução de problemas

**Numa área de trabalho**

- Verifique se existe o relatório com o nome na mensagem de erro. O nome não é sensível a maiúsculas e minúsculas.

**Numa aplicação**

- Verifique se existe o relatório com o nome na mensagem de erro na aplicação. Contacte o autor da aplicação para obter mais assistência.

**Se o relatório for partilhado**

1. Verifique se o relatório com o nome na mensagem de erro é partilhado consigo.
2. Se o relatório existir, verifique se o nome do proprietário é igual para o relatório principal e o sub-relatório. Em seguida, contacte o proprietário do relatório principal com essa informação.

## <a name="subreport-renders-with-unexpected-content"></a>O sub-relatório é composto com conteúdo inesperado

### <a name="possible-reason"></a>Motivo possível

O Power BI permite aos utilizadores ter múltiplos relatórios com o mesmo nome na mesma área de trabalho

### <a name="troubleshooting-steps-for-report-authors"></a>Passos de resolução de problemas (para autores de relatórios)

1. Abra o relatório principal no Power BI Report Builder e determine o nome do sub-relatório.
2. Procure relatórios com o mesmo nome na área de trabalho.
3. Localize o relatório esperado e mude o nome dos restantes.

**Para não autores:** Contacte o autor.

## <a name="data-retrieval-fails"></a>Falha na obtenção de dados

**Descrição:** A obtenção de dados falha ao compor o sub-relatório. O sub-relatório não é composto. É apresentada uma mensagem de erro.

### <a name="message"></a>Mensagem

"A obtenção de dados falhou no sub-relatório 'Sub-relatório1', localizado em: 'InvoiceDetails'. Consulte os ficheiros de registo para obter mais informações."

### <a name="troubleshooting-steps"></a>Passos de resolução de problemas

Os mesmos que os passos gerais de resolução de problemas para relatórios com problemas de acesso a dados.

## <a name="rendering-fails-unspecified-parameters"></a>Falha de composição: Parâmetros não especificados

**Descrição:** A composição do sub-relatório falha devido a parâmetros não especificados. O sub-relatório tem parâmetros obrigatórios, mas o relatório principal não define todos.

### <a name="message"></a>Mensagem 
"Um ou mais parâmetros do sub-relatório, 'Sub-relatório1', localizado em: 'SubreportAWithDS', não foram especificados."

### <a name="troubleshooting-steps-for-the-report-author"></a>Passos de resolução de problemas (para o autor do relatório)

1. Abra o relatório principal no Power BI Report Builder.
2. Abra o sub-relatório no Power BI Report Builder.
3. Verifique se o conjunto de parâmetros transmitido no item de relatório do sub-relatório, no relatório principal, corresponde ao conjunto de parâmetros no sub-relatório.

**Para não autores:** Contacte o autor.

## <a name="rendering-fails-recursion-limit"></a>Falha de composição: Limite de recursão

**Descrição:** A composição do sub-relatório falha devido ao limite de recursão. Os sub-relatórios não podem ser aninhados com uma profundidade superior a 20 níveis.

### <a name="message"></a>Mensagem

"O relatório ou o sub-relatório tem um sub-relatório recursivo ('Sub-relatório1') que excedeu o limite de recursão máximo permitido."

### <a name="troubleshooting-steps-for-report-authors"></a>Passos de resolução de problemas (para autores de relatórios)

- Reduza o aninhamento.
- Recrie a estrutura de relatórios.

## <a name="other-errors"></a>Outros erros

**Descrição:** Erros que não se enquadram em nenhuma das categorias anteriores.

### <a name="message"></a>Mensagem

“Erro: não foi possível apresentar sub-relatório. "

### <a name="possible-reasons"></a>Motivos possíveis

- Múltiplos erros durante a composição de sub-relatórios, como uma diferença de parâmetros com problemas de obtenção de dados.
- Erros inesperados.

### <a name="troubleshooting-steps-for-report-authors"></a>Passos de resolução de problemas (para autores de relatórios)

1. Verifique se o sub-relatório pode ser composto diretamente.
2. Se for possível compor o sub-relatório, verifique os parâmetros no sub-relatório e no relatório principal.
3. Certifique-se de que o relatório principal não tem mais de 50 sub-relatórios exclusivos e de que o sub-relatório não tem um aninhamento com profundidade superior a 20 níveis.
4. Se não conseguir resolver o problema, contacte o suporte do Power BI.

**Para não autores:** Contacte o autor.

## <a name="next-steps"></a>Próximos passos

[Sub-relatórios nos relatórios paginados do Power BI](subreports.md)

[Ver um relatório paginado no serviço Power BI](../consumer/paginated-reports-view-power-bi-service.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
