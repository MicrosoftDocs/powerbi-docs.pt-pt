---
title: Parâmetros de URL em relatórios paginados no Power BI
description: Aprenda a enviar comandos a relatórios paginados no Power BI ao adicionar um parâmetro a um URL, que pode incluir num e-mail ou numa página Web.
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 09/09/2020
ms.openlocfilehash: 0816ba6f3ff606a73c835ac71af66655fd49acfd
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/04/2020
ms.locfileid: "93298068"
---
# <a name="url-parameters-in-paginated-reports-in-power-bi"></a>Parâmetros de URL em relatórios paginados no Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

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

**Formato de exportação** – especifica o formato no qual deve ser realizada a composição e exportação do relatório.

Exemplo: rdl:format=PDF

Os valores disponíveis são:
 
- PPTX (PowerPoint)
- MHTML 
- IMAGEM 
- EXCELOPENXML (EXCEL) 
- WORDOPENXML (WORD) 
- CSV 
- PDF 
- ACCESSIBLEPDF (PDF)
- XML 

**Vista de Relatório** – especifica o tipo de vista utilizado para apresentar o relatório.

-   rdl:reportView

    - “interativo” (predefinição): carregue o relatório no modo interativo.
    - “pageView”: carregue o relatório no modo de vista de página.

**Painel de parâmetros** – especifica se o painel de parâmetros está fechado ou aberto quando o relatório é carregado, ou se está oculto.

-   rdl:parameterPanel

    - "fechado": carregar o relatório com o painel de parâmetros fechado. O botão de parâmetro está ativado para que os utilizadores possam clicar no botão para expandir;
    - "oculto": carregar o relatório com o painel de parâmetros fechado e o botão de parâmetro desativado;
    - "expandido" (predefinição): carregar o relatório com o painel de parâmetros aberto e o botão de parâmetro ativado;

**Informações do dispositivo** – pode especificar parâmetros de saída adicionais para os seguintes formatos de exportação. 

PDF/ACCESSIBLEPDF:

- rdl:AccessiblePDF=true/false
- rdl:Columns=integer
- rdl:ColumnSpacing=decimal(in)
- rdl:DpiX=integer
- rdl:DpiY=integer
- rdl:EndPage=integer
- rdl:HumanReadablePDF=true/false
- rdl:MarginBottom=decimal(in)
- rdl:MarginLeft=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:MarginTop=decimal(in)
- rdl:PageHeight=decimal(in)
- rdl:PageWidth=decimal(in)
    - rdl:StartPage=integer
    
CSV:

- rdl:Encoding=string
- rdl:ExcelMode=true/false
- rdl:FieldDelimiter=string
- rdl:NoHeader=true/false
- rdl:Qualifier=string
- rdl:RecordDelimiter=string
- rdl:SuppressLineBreaks=true/false
    - rdl:UseFormattedValues=true/false
    
WORDOPENXML (WORD):

- rdl:AutoFit=string -> True/False/Never/Default
- rdl:ExpandToggles=true/false
- rdl:FixedPageWidth=true/false
- rdl:OmitHyperlinks=true/false
- rdl:OmitDrillthroughs=true/false

EXCELOPENXML (EXCEL):

- rdl:OmitDocumentMap=true/false
- rdl:OmitFormulas=true/false
    - rdl:SimplePageHeaders=true/false
    
PPTX (PowerPoint):
 
- rdl:Columns=integer
- rdl:ColumnSpacing=decimal(in)
- rdl:DpiX=integer
- rdl:DpiY=integer
- rdl:EndPage=integer
- rdl:MarginBottom=decimal(in)
- rdl:MarginLeft=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:MarginTop=decimal(in)
- rdl:PageHeight=decimal(in)
- rdl:PageWidth=decimal(in)
- rdl:StartPage=integer
    - rdl:UseReportPageSize=true/false

XML:

- rdl:XSLT=string
- rdl:MIMEType=string
- rdl:UseFormattedValues=true/false
- rdl:Indented=true/false
- rdl:OmitNamespace=true/false
- rdl:OmitSchema=true/false
- rdl:Encoding=string
- rdl:Schema=true/false

**Abrir a hiperligação na mesma janela do browser** Pode acrescentar "rdl:targetSameWindow=true" ao URL da hiperligação no seu relatório para que o Power BI abra esta hiperligação na mesma janela do browser. Para obter informações sobre como adicionar hiperligações a um relatório, veja [Add a hyperlink to a URL](/sql/reporting-services/report-design/add-a-hyperlink-to-a-url-report-builder-and-ssrs) (Adicionar uma hiperligação a um URL) na documentação do SQL Server Reporting Services.

## <a name="next-steps"></a>Próximos passos

- [Transmitir um parâmetro de relatório num URL para um relatório paginado no Power BI](report-builder-url-pass-parameters.md)
- [O que são relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)