---
title: Parâmetros de URL em relatórios paginados no Power BI
description: Este tópico descreve as utilizações comuns dos parâmetros de relatórios do Paginated Report Builder do Power BI, as propriedades que pode definir e muito mais.
ms.service: powerbi
ms.subservice: report-builder
ms.custom: ''
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.date: 08/29/2019
ms.openlocfilehash: bda35bfb4690d8109f7bd611e3d319278d235f33
ms.sourcegitcommit: 09ee1b4697aad84d8f4c9421015d7e4dbd3cf25f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70302681"
---
# <a name="url-parameters-in-paginated-reports-in-power-bi"></a>Parâmetros de URL em relatórios paginados no Power BI

Pode enviar comandos para relatórios paginados no Power BI ao adicionar um parâmetro a um URL. Por exemplo, pode ter visto o relatório através de um conjunto específico de valores de parâmetro de relatório. Deverá incorporar estas informações no URL ao utilizar parâmetros de acesso por URL predefinidos. Pode personalizar a forma como o Power BI processa o relatório ao incorporar parâmetros para formatos de composição ou para obter o aspeto e funcionalidade da barra de ferramentas de relatórios. Em seguida, irá colar este URL diretamente num e-mail ou página Web para que outras pessoas possam experimentar o seu relatório da mesma forma que no browser. 

Eis algumas ações que pode efetuar através de parâmetros de acesso por URL: 

- Envie os parâmetros de relatório para um relatório. 
- Inicie a exportação dos conteúdos do relatório num formato de ficheiro suportado. 
- Mostre ou oculte o painel de parâmetros. 
- Especifique a definição DeviceInfo. 

Para obter uma lista completa dos comandos e definições disponíveis através de acesso por URL, veja a secção  [Referência do parâmetro de acesso por URL](#url-access-parameter-reference) mais à frente neste artigo. 

## <a name="url-access-concepts"></a>Conceitos de acesso por URL 

Os pedidos de URL para o Power BI contêm parâmetros que são processados pelo serviço. A forma como o serviço processa pedidos de URL depende dos parâmetros, dos prefixos dos parâmetros e dos tipos de itens que estão incluídos no URL. A funcionalidade de URL de relatório paginado é compatível com a maioria dos browsers e aplicações que suportam endereços URL padrão. 

## <a name="url-access-syntax"></a>Sintaxe de acesso por URL 

Os pedidos de URL podem conter múltiplos parâmetros indicados em qualquer ordem. Os parâmetros são separados por um E comercial (&). Os pares nome/valor são separados por um sinal de igual (=). Por exemplo:

```
powerbiserviceurl?rp:parametervalueh&rdl:parameter=value  
```

## <a name="syntax-description"></a>Descrição da sintaxe 

### <a name="powerbiserviceurl"></a>powerbiserviceurl 

O URL do serviço Web do seu inquilino no Power BI. Por exemplo: 

**&** – utilizado para separar os pares nome/valor dos parâmetros de acesso por URL.

**prefixo** – um prefixo do parâmetro do URL (por exemplo, rp: ou rdl:) que especifica uma ação no serviço Power BI. 

> [!NOTE]
> Os parâmetros de relatório necessitam de um prefixo de parâmetro e são sensíveis a maiúsculas e minúsculas. 

**parâmetro** – o nome do parâmetro. 

### <a name="value"></a>valor 

O texto do URL correspondente ao valor do parâmetro que está a ser utilizado. 

Para obter exemplos da transmissão de parâmetros de relatório no URL, veja  [Transmitir um parâmetro de relatório num URL](report-builder-url-pass-parameters.md).

## <a name="url-access-parameter-reference"></a>Referência de parâmetros de acesso por URL

Pode utilizar os seguintes parâmetros como parte de um URL para configurar o aspeto e funcionalidade dos seus relatórios paginados no Power BI. Os parâmetros mais comuns estão indicados nesta secção. Os parâmetros não são sensíveis a maiúsculas e minúsculas e começam pelo prefixo de parâmetro  `rdl:`  se estiverem relacionados com o formato de saída.  

### <a name="report-commands-rdl"></a>Comandos de relatório (`rdl:`) 

**Formato de exportação** – especifica o formato no qual deve ser realizada a composição e exportação do relatório. Os valores disponíveis são: 
- PPTX (PowerPoint)
- MHTML 
- IMAGEM 
- EXCELOPENXML (EXCEL) 
- WORDOPENXML (WORD) 
- CSV 
- PDF 
- XML 

## <a name="next-steps"></a>Próximos passos

- [Transmitir um parâmetro de relatório num URL para um relatório paginado no Power BI](report-builder-url-pass-parameters.md)
- [O que são relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)
