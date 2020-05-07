---
title: Documento de orientação da resolução de problemas de relações
description: Documento de orientação da resolução de problemas de relações de modelos.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/02/2020
ms.author: v-pemyer
ms.openlocfilehash: e2854d82d858bb1963b691d32d561c7b3bbfc11a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "78263651"
---
# <a name="relationship-troubleshooting-guidance"></a>Documento de orientação da resolução de problemas de relações

Este artigo destina-se aos modeladores de dados que trabalham com o Power BI Desktop. Proporciona orientações sobre como resolver problemas específicos que poderá encontrar ao desenvolver modelos e relatórios.

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

## <a name="troubleshooting-checklist"></a>Lista de verificação de resolução de problemas

Quando um elemento visual do relatório está configurado para utilizar campos de duas (ou mais) tabelas e não apresentar o resultado correto (ou qualquer resultado), é possível que o problema esteja relacionado com as relações de modelos.

Neste caso, deverá seguir a lista de verificação geral de resolução de problemas. Pode trabalhar progressivamente na lista de verificação até identificar o(s) problema(s).

1. Mude o elemento visual para uma tabela ou matriz ou, em alternativa, abra o painel “Ver Dados”: é mais fácil resolver problemas quando pode ver o resultado da consulta
1. Se houver um resultado de consulta vazio, mude para a vista Dados e verifique se as tabelas foram carregadas com linhas de dados
1. Mude para a vista Modelo: é fácil ver as relações e determinar rapidamente as propriedades delas
1. Verifique se existem relações entre as tabelas
1. Verifique se as propriedades de cardinalidade estão configuradas corretamente. Poderão estar incorretas se uma coluna no lado “muitos” tiver atualmente valores únicos e tiver sido configurada incorretamente como um lado “um”
1. Verifique se as relações estão ativas (linha sólida)
1. Verifique se as direções do filtro suportam a propagação (interprete as pontas de seta)
1. Verifique se estão relacionadas as colunas corretas: selecione a relação ou paire o cursor sobre a mesma para revelar as colunas relacionadas
1. Verifique se os tipos de dados das colunas relacionadas são os mesmos ou, pelo menos, compatíveis: é possível relacionar uma coluna de texto com uma coluna de números inteiros, mas os filtros não encontrarão correspondências para a propagação
1. Mude para a vista Dados e verifique se podem ser encontrados valores correspondentes em colunas relacionadas

## <a name="troubleshooting-guide"></a>Guia de resolução de problemas

Segue-se uma lista de problemas juntamente com as possíveis soluções.

|Problema|Motivos possíveis|
|---------|---------|
|O elemento visual não apresenta nenhum resultado|- O modelo ainda vai ser carregado com dados<br />- Não existem dados no contexto do filtro<br />- A segurança ao nível da linha está aplicada<br />- As relações não estão a ser propagadas entre as tabelas – _siga a lista de verificação acima_<br />- A segurança ao nível da linha está aplicada, mas não está ativada uma relação bidirecional para propagação — veja [Segurança ao nível da linha (RLS) com o Power BI Desktop](../desktop-rls.md)|
|O elemento visual apresenta o mesmo valor para cada agrupamento |- As relações não existem<br />- As relações não estão a ser propagadas entre as tabelas – _siga a lista de verificação acima_|
|O elemento visual apresenta resultados, mas não estão corretos|- O elemento visual está configurado incorretamente<br />- A lógica da medida é incorreta<br />- Os dados do modelo têm de ser atualizados<br />- Os dados de origem estão incorretos<br />- As colunas de relação estão relacionadas incorretamente (por exemplo, a coluna **IDProduto** mapeia para **IDCliente**)<br />- É uma relação entre duas tabelas DirectQuery e a coluna do lado “um” de uma relação contém valores duplicados|
|Aparecem agrupamentos ou itens de segmentação de dados/filtro EM BRANCO e as colunas de origem não contêm valores EM BRANCO|- É uma relação forte e a coluna do lado “muitos” tem valores não armazenados na coluna do lado “um” – veja [Relações de modelos no Power BI Desktop (Relações fortes)](../desktop-relationships-understand.md#strong-relationships)<br />- É uma relação um-para-um forte e as colunas relacionadas contêm valores EM BRANCO — veja [Relações de modelos no Power BI Desktop (Relações fortes)](../desktop-relationships-understand.md#strong-relationships)<br />- Uma coluna do lado “muitos” da relação inativa armazena valores EM BRANCO ou não tem valores armazenados no lado “um”|
|O elemento visual tem dados em falta|- São aplicados filtros incorretos/inesperados<br />- A segurança ao nível da linha está aplicada<br />- É uma relação fraca e existem valores EM BRANCO em colunas relacionadas ou problemas de integridade de dados — veja [Relações de modelos no Power BI Desktop (Relações fracas)](../desktop-relationships-understand.md#weak-relationships)<br />- É uma relação entre duas tabelas DirectQuery e a relação está configurada para [assumir a integridade referencial](../desktop-relationships-understand.md#assume-referential-integrity), mas existem problemas de integridade de dados (valores não correspondentes em colunas relacionadas)|
|A segurança ao nível da linha não está aplicada corretamente|- As relações não estão a ser propagadas entre as tabelas – _siga a lista de verificação acima_<br />- A segurança ao nível da linha está aplicada, mas não está ativada uma relação bidirecional para propagação — veja [Segurança ao nível da linha (RLS) com o Power BI Desktop](../desktop-rls.md)|
|||

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações relacionadas com este artigo, consulte os seguintes recursos:

- [Relações de modelos no Power BI Desktop](../desktop-relationships-understand.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)
