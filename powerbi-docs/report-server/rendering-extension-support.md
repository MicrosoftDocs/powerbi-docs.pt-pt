---
title: Conformidade da Extensão de Composição de PDF com a ISO 14289-1 – Power BI Report Server e SSRS
description: Este documento descreve a conformidade da Extensão de Composição de PDF do Power BI Report Server e do SQL Server Reporting Services com as especificações da ISO 14289-1 (PDF/UA).
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/04/2019
ms.author: maggies
ms.openlocfilehash: bfefcef18b8cd92a5c3b15c2dcbd4653a6c7c9cd
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "76819520"
---
# <a name="pdf-rendering-extension-conformance-to-iso-14289-1---power-bi-report-server--ssrs"></a>Conformidade da Extensão de Composição de PDF com a ISO 14289-1 – Power BI Report Server e SSRS

Aplica-se a: Power BI Report Server e SQL Server Reporting Services (SSRS)

Este documento descreve a conformidade da Extensão de Composição de PDF do Power BI Report Server e do SQL Server Reporting Services com as especificações da [ISO 14289-1 (PDF/UA)](https://www.pdfa.org/publication/pdfua-in-a-nutshell/).

> [!NOTE]
> Pode guardar ou imprimir este documento técnico ao selecionar **Imprimir** no seu browser e, em seguida, ao selecionar **Guardar como PDF**.

## <a name="1--scope"></a>1.  Âmbito

Não aplicável

## <a name="2--normative-references"></a>2.  Referências normativas

Não aplicável

## <a name="3--terms-and-definitions"></a>3.  Termos e definições

Não aplicável

## <a name="4--notation"></a>4.  Anotações

Não aplicável

## <a name="5-version-identification"></a>5. Identificação da Versão

A Extensão de Composição de PDF oferece suporte para PDF/UA, conforme descrito neste documento. Em alguns casos, anotados abaixo, o utilizador é responsável por tomar medidas para garantir que um PDF está em conformidade total com o PDF/UA.  Esperamos que o utilizador adicione a versão e os identificadores de conformidade apropriados do PDF/UA como o último passo neste processo, indicando que foram tomadas as medidas necessárias para tornar o PDF totalmente compatível com o PDF/UA.

Todos os itens listados neste documento baseiam-se na composição de um documento PDF com a definição de informações do dispositivo AccessiblePdf definida como `true`. Em alguns casos, as limitações de conformidade devem-se a limitações na linguagem RDL (Report Definition Language).

## <a name="6--conformance-requirements"></a>6.  Requisitos de conformidade

|     Critérios     |     Funcionalidade de suporte     |     Observações      |
|----|--------|--------|
|    6.1 Geral    |                 Suportado    |    A Extensão de Composição de PDF cria a versão 1.7 do PDF.    |
|    6.2 Ficheiros de conformidade    |                 Suportado com Exceções    |    Veja os comentários na secção 7 – Requisitos do formato de ficheiro.    |
|    6.3 Leitor em conformidade    |     Not Applicable     |         |
|    6.4 Tecnologia de apoio em conformidade    |     Not Applicable     |         |

## <a name="7--file-format-requirements"></a>7.  Requisitos do formato de ficheiro

|     Critérios     |     Funcionalidade de suporte     |     Observações      |
|-----|-------|------------------------|
|    7.1 Geral    |                 Suportado com Exceções    |    Todo o conteúdo real deve ser identificado conforme definido na ISO 32000-1:2008, 14,8. Os artefactos (ISO 32000-1:2008, 14.8.2.2.2) não devem ser identificados na árvore de estrutura. <li> A Extensão de Composição de PDF não oferece flexibilidade para marcar explicitamente itens individuais como artefactos, portanto, em vez disso, ela fará o artefacto de tudo o que é mapeado para os critérios na ISO 32000-1:2008, 14.8.2.2.2.<br>O conteúdo deve ser marcado na árvore de estrutura com etiquetas semanticamente apropriadas por ordem lógica de leitura. <br> **Observação** 4 WCAG 2.0, a Diretriz 1.4 explica os problemas relacionados com o contraste, cor e outras formatações para acessibilidade. <br><li> O utilizador teria de garantir que o documento não está sujeito a estes problemas. <br>As etiquetas standard definidas na ISO 32000-1:2008, 14.8.4, não devem ser remapeadas. <li> A Extensão de Composição de PDF não faz o remapeamento das etiquetas standard. Os documentos começam com o elemento raiz do Documento. <br>Os ficheiros que reivindicam conformidade com este Padrão Internacional deve ter um valor Suspeito de falso (ISO 32000-1:2008, Tabela 321). <li> A Extensão de Composição de PDF não tem a entrada Suspeita. Esta propriedade é opcional.    |
|    7.2 Texto    |                 Suportado com Exceções    |    O conteúdo deve ser identificado por ordem lógica de leitura. A etiqueta mais semanticamente apropriada deve ser utilizada para cada elemento lógico no conteúdo do documento. <br><li> A Extensão de Composição de PDF identifica o conteúdo por ordem lógica de leitura, tanto quanto possível.<br>Os códigos de carateres devem ser mapeados para Unicode, conforme descrito na ISO 32000-1:2008, 14.8.2.4.2. Os carateres não incluídos na especificação Unicode podem utilizar a área de utilização particular Unicode ou declarar outra codificação de carateres. <br>A linguagem natural deve ser declarada como discutida na ISO 32000-1:2008, 14.9.2 e/ou conforme descrito na ISO 32000-1:2008, 7.9.2. As alterações na linguagem natural devem ser declaradas. As alterações na linguagem natural dentro de cadeias de carateres de texto (por exemplo, dentro de descrições alternativas) devem ser declaradas com um identificador de linguagem, conforme descrito na ISO 32000-1:2008, 14.9.2.2. <br><li> A Extensão de Composição de PDF declara apenas a linguagem natural ao nível do documento    |
|    7.3 Gráficos    |                 Suportado com Exceções    |    Os objetos gráficos, além de objetos de texto, devem ser identificados com uma etiqueta de Figura, conforme descrito na ISO 32000-1:2008, 14.8.4.5, Tabela 340. Se qualquer uma das seguintes exceções for verdadeira, o gráfico deverá ser identificado como um artefacto: <br><li> o gráfico não representa conteúdo significativo ou <li>  o gráfico aparece como um plano de fundo para uma anotação de ligação; neste caso, o texto alternativo na ligação deve descrever o gráfico e a ligação. <li> A Extensão de Composição de PDF identifica objetos gráficos com a etiqueta Figura. <br>A legenda que acompanha uma figura deve ser identificada com uma etiqueta de Legenda. <li> Atualmente, a Extensão de Composição de PDF não identifica legendas em figuras com uma etiqueta de Legenda. <br>As etiquetas de Figura devem incluir uma representação alternativa ou um texto de substituição que represente os conteúdos marcados com a etiqueta de Figura, conforme indicado na ISO 32000-1:2008, 14.7.2, Tabela 323. <br>**Observação** 1 Veja também WCAG 2.0, Diretriz 1.1. <br>Se o texto representado num gráfico não for um texto em linguagem natural para ser lido por um leitor humano, será apresentado um texto alternativo que descreve a natureza ou a finalidade do gráfico. <br>**Observação** 2 Texto que é uma amostra do tipo ou uma amostra do sistema de escrita utilizado por uma linguagem são exemplos de texto que não está numa linguagem natural.   A Extensão de Composição de PDF suporta texto alternativo em figuras, embora caiba ao utilizador adicionar o texto alternativo. <br>Observação adicional sobre o atributo BBox: <br><li> A Extensão de Composição de PDF não grava o atributo BBox no momento. <li> Uma solução alternativa é voltar a identificar manualmente as ilustrações como novas Figuras ou Artefactos.    |
|    7.4 Títulos    |                 Not Applicable    |    O RDL não suporta a marcação de títulos de forma alguma. Cabe ao utilizador identificá-los conforme apropriado.    |
|    7.5 Tabelas    |                 Suportado com Exceções    |    As tabelas devem incluir cabeçalhos. Os cabeçalhos da tabela devem ser identificados de acordo com a ISO 32000-1:2008, Tabela 337 e Tabela 349. <br>**Observação** 1 As tabelas podem conter cabeçalhos de coluna, cabeçalhos de linha ou ambos. <br>**Observação** 2 Tem de estar disponível o máximo de informações sobre a estrutura de tabelas quando a tecnologia de apoio é confiada. Os cabeçalhos desempenham uma função fundamental no fornecimento de informações estruturais. <br><li> Cabe ao utilizador incluir cabeçalhos nas suas tabelas. O RDL e a Extensão de Composição de PDF oferecem suporte para cabeçalhos de linha. <br>  Elementos de estrutura do tipo TH devem ter um atributo de Âmbito.   <li> A Extensão de Composição de PDF inclui um atributo de Âmbito nos elementos TH para Membros de Coluna e Linha, mas não para células de Canto.<br>As estruturas de identificação de tabela devem ser utilizadas apenas para identificar conteúdo apresentado dentro das relações lógicas de linha e/ou coluna.   <li> O que depende da forma como o utilizador optou por utilizar tabelas no seu RDL.    |
|    7.6 Listas    |                 Not Applicable    |    O RDL não suporta a identificação de listas. No RDL, elas são estruturalmente uma tabela com uma única célula de tabela. <br>Cabe ao utilizador voltar a identificá-los conforme apropriado.    |
|    7.7 Expressões matemáticas    |                 Suportado com Exceções    |    Todas as expressões matemáticas devem ser colocadas dentro de uma etiqueta de Fórmula, conforme detalhado na ISO 32000-1:2008, 14.8.4.5 e devem ter um atributo Alt. <br><li> Atualmente, a Extensão de Composição de PDF não coloca expressões matemáticas dentro de uma etiqueta de Fórmula. <br>Os requisitos relacionados com o mapeamento de carateres para Unicode devem aplicar-se a expressões matemáticas, conforme indicado na ISO 32000-1:2008, 9.10.2 e 14.8.2.4. <br><li> É suportado pela Extensão de Composição de PDF.    |
|    7.8 Cabeçalhos e rodapés de página    |                 Suportado    |    Os cabeçalhos e rodapés em execução devem ser identificados como artefactos de Paginação e devem ser classificados como subtipos de Cabeçalho ou Rodapé, de acordo com a ISO 32000-1:2008, 14.8.2.2.2, Tabela 330. <br><li> Cabeçalhos ou Rodapés são tratados e identificados como Artefactos.    |
|    7.9 Observações e referências    |                 Not Applicable    |    A Extensão de Composição de PDF não suporta a identificação de notas e referências. <br>Cabe ao utilizador identificá-las conforme apropriado.    |
|    7.10 Conteúdo opcional    |                 Not Applicable    |         |
|    7.11 Ficheiros incorporados    |                 Not Applicable    |         |
|    7.12 Threads de artigos    |                 Not Applicable    |         |
|    7.13 Assinaturas digitais    |                 Not Applicable    |         |
|    7.14 Formulários não interativos    |                 Not Applicable    |         |
|    7.15 XFA    |                 Not Applicable    |         |
|    7.16 Segurança    |                 Not Applicable    |         |
|    7.17 Navegação    |                 Suportado    |    Um documento deve incluir uma estrutura do documento que corresponda à ordem de leitura e ao nível de destinos de navegação (ISO 32000-1:2008, 12.3.3). <br><li> O RDL suporta marcadores para um item de relatório, mas o utilizador deve selecionar esta opção. Esses indicadores são, em seguida, compostos como uma estrutura do documento pela Extensão de Composição de PDF. <br>Se existirem, as entradas na árvore de números PageLabels (ISO 32000-1:2008, 7.7.2, Tabela 28) devem ser semanticamente apropriadas. <br><li> A Extensão de Composição de PDF não inclui uma árvore de números PageLabels.    |
|    7.18 Anotações    |                 Not Applicable    |    O RDL não suporta anotações    |
|    7.21 Fontes    |                 Suportado    |         |
|    7.21.1 Geral    |                 Suportado    |         |
|    7.21.2 Tipos de fonte    |                 Suportado    |         |
|    7.21.3 Fontes compostas    |                 Suportado    |         |
|    7.21.3.1 Geral    |                 Suportado    |         |
|    7.21 3.2 CIDFonts    |                 Suportado    |         |
|    7.21.3.3 CMaps    |                 Suportado    |         |
|    7.21.4 Incorporação    |                 Suportado    |         |
|    7.21.4.1 Geral    |                 Suportado    |         |
|    7.21.4.2 Incorporação de subconjunto    |                 Suportado    |         |
|    7.21.5 Métricas da fonte    |                 Suportado    |         |
|    7.21.6 Codificação de carateres    |                 Suportado    |         |
|    7.21.7 Mapas de carateres Unicode    |                 Suportado    |         |
|    7.21.8 Utilização do glifo .notdef    |                 Suportado    |         |

## <a name="8--conforming-reader-requirements"></a>8.  Conformidade com os requisitos do leitor

Não aplicável

## <a name="9--at-requirements"></a>9.  Requisitos do AT

Não aplicável

## <a name="disclaimer"></a>Disclaimer

© 2017 Microsoft Corporation. All rights reserved. The names of actual companies and products mentioned herein may be the trademarks of their respective owners. The information contained in this document represents the current view of Microsoft Corporation on the issues discussed as of the date of publication. Microsoft cannot guarantee the accuracy of any information presented after the date of publication. Microsoft regularly updates its websites with new information about the accessibility of products as that information becomes available.

Customization of the product voids this conformance statement from Microsoft. Please consult with Assistive Technology (AT) vendors for compatibility specifications of specific AT products.

This document is for informational purposes only. MICROSOFT MAKES NO WARRANTIES, EXPRESS OR IMPLIED, IN THIS DOCUMENT.


## <a name="next-steps"></a>Próximos passos
[Descrição geral para administradores](admin-handbook-overview.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

