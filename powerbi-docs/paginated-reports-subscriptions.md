---
title: Subscrever relatórios paginados no serviço Power BI
description: Neste artigo, irá aprender noções importantes da subscrição de relatórios paginados no serviço Power BI.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 05/24/2019
ms.openlocfilehash: 472606fcb3b823cdcb722c9d8d6421d0ec652d24
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "66839562"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Subscrever relatórios paginados no serviço Power BI para si e para outras pessoas 

Agora pode configurar subscrições de e-mail de relatórios paginados no serviço Power BI para si e para outras pessoas. De modo geral, o processo é idêntico a [subscrever relatórios e dashboards no serviço Power BI](service-report-subscribe.md). Este artigo explica as diferenças e indica algumas considerações. 

Ao configurar subscrições, pode selecionar com que frequência quer receber os e-mails: diariamente, semanalmente ou de hora a hora. Se selecionar diariamente ou semanalmente, pode escolher a hora em que pretende que a subscrição seja executada. Pode configurar até 24 subscrições diferentes por dia, para cada relatório. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Considerações sobre subscrições de relatórios paginados 

- Ao contrário das subscrições de dashboards ou relatórios do Power BI, a sua subscrição contém um anexo dos resultados do relatório.  São suportados os seguintes tipos de anexo: PDF, apresentação do PowerPoint (PPTX), Livro do Excel (XLSX), Documento do Word (DOCX), ficheiro CSV e XML.

- Não há uma imagem de pré-visualização do relatório no corpo do e-mail.  Estamos a planear a inclusão da imagem da primeira página do relatório como um item opcional. 

- O tamanho máximo do anexo do relatório é 25 MB. 

- Pode subscrever relatórios paginados que ligam a quaisquer origens de dados atualmente suportadas (incluindo o Azure Analysis Services ou conjuntos de dados do Power BI) para outros utilizadores. Tenha em atenção que o anexo do relatório reflete os dados com base nas suas permissões, tal como o SQL Server Reporting Services faz atualmente. 

- As subscrições de páginas de relatório estão associadas ao nome do relatório.  

- As subscrições de e-mail são enviadas com os valores de parâmetros predefinidos do relatório. 

- Não existe a opção **Depois da Atualização de Dados** para a frequência dos relatórios paginados. Irá obter sempre os valores mais recentes da origem de dados subjacente. 

## <a name="next-steps"></a>Próximos passos

[Subscrever relatórios e dashboards no serviço Power BI para si e para outras pessoas](service-report-subscribe.md)

[O que são relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)
