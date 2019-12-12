---
title: Subscrever relatórios paginados no serviço Power BI
description: Neste artigo, irá aprender noções importantes da subscrição de relatórios paginados no serviço Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 12/03/2019
ms.openlocfilehash: d3813636010dcbf5c866248111755beb0dca99b8
ms.sourcegitcommit: e492895259aa39960063f9b337a144a60c20125a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74834638"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Subscrever relatórios paginados no serviço Power BI para si e para outras pessoas 

Agora pode configurar subscrições de e-mail de relatórios paginados no serviço Power BI para si e para outras pessoas. De modo geral, o processo é idêntico a [subscrever relatórios e dashboards no serviço Power BI](end-user-subscribe.md). Este artigo explica as diferenças e indica algumas considerações. 

Ao configurar subscrições, pode selecionar com que frequência quer receber os e-mails: diariamente, semanalmente, mensalmente ou de hora a hora. Também pode escolher a(s) hora(s) em que pretende que a subscrição seja executada. Pode configurar até 24 subscrições diferentes para cada relatório. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Considerações sobre subscrições de relatórios paginados 

- Ao contrário das subscrições de dashboards ou relatórios do Power BI, a sua subscrição contém um anexo dos resultados do relatório.  São suportados os seguintes tipos de anexo: PDF, apresentação do PowerPoint (PPTX), Livro do Excel (XLSX), Documento do Word (DOCX), ficheiro CSV e XML.

- Pode incluir uma imagem de pré-visualização do relatório no corpo do e-mail.  Isto é opcional e pode ser ligeiramente diferente da primeira página do documento de relatório anexado, consoante o formato do anexo selecionado. 

- O tamanho máximo do anexo do relatório é 25 MB. 

- Pode subscrever relatórios paginados que ligam a quaisquer origens de dados atualmente suportadas (incluindo o Azure Analysis Services ou conjuntos de dados do Power BI) para outros utilizadores. Tenha em atenção que o anexo do relatório reflete os dados com base nas suas permissões, tal como o SQL Server Reporting Services faz atualmente. 

- As subscrições de e-mail podem ser enviadas com os parâmetros atualmente selecionados ou com os parâmetros predefinidos do seu relatório.  Pode definir valores de parâmetros diferentes para cada subscrição que criar para o relatório. 

- Se o autor do relatório tiver definido parâmetros baseados em expressões (por exemplo, o parâmetro predefinido é sempre a data de hoje), a subscrição utilizará os mesmos como o valor predefinido. Pode alterar outros valores de parâmetros e optar por utilizar valores atuais. No entanto, a menos que também altere explicitamente esses valores, a subscrição utilizará os parâmetros baseados em expressões.

- Não existe a opção **Depois da Atualização de Dados** para a frequência dos relatórios paginados. Irá obter sempre os valores mais recentes da origem de dados subjacente. 

## <a name="next-steps"></a>Próximos passos

[Subscrever relatórios e dashboards no serviço Power BI para si e para outras pessoas](../service-report-subscribe.md)

[Relatórios paginados no serviço Power BI](end-user-paginated-report.md)

