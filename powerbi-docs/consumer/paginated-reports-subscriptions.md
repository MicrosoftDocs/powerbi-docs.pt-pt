---
title: Subscrever relatórios paginados no serviço Power BI
description: Neste artigo, irá aprender noções importantes da subscrição de relatórios paginados no serviço Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 01/22/2021
ms.openlocfilehash: 5817bf3752a03361be4e982faf10dffb67bda0b5
ms.sourcegitcommit: 1872a167d1e4d731ad00cf8a6d951c31aa54bcce
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/28/2021
ms.locfileid: "98925788"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Subscrever relatórios paginados no serviço Power BI para si e para outras pessoas 

Agora pode configurar subscrições de e-mail de relatórios paginados no serviço Power BI para si e para outras pessoas. De modo geral, o processo é idêntico a [subscrever relatórios e dashboards no serviço Power BI](end-user-subscribe.md). Este artigo explica as diferenças e indica algumas considerações. 

Ao configurar subscrições, pode selecionar com que frequência quer receber os e-mails: diariamente, semanalmente, mensalmente ou de hora a hora. Também pode escolher a(s) hora(s) em que pretende que a subscrição seja executada. Não existe um limite para o número de subscrições que pode configurar para cada relatório. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Considerações sobre subscrições de relatórios paginados 

- Você não precisa de editar permissões para o relatório paginado para criar uma subscrição para si mesmo, mas você deve ter permissões de edição para criar uma para outra pessoa. Se tiver pelo menos um papel de Contribuinte no espaço de trabalho onde está o relatório paginated, então pode criar subscrições para outros. Leia mais sobre [Papéis em espaços de trabalho.](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)

- Ao contrário das subscrições de dashboards ou relatórios do Power BI, a sua subscrição contém um anexo dos resultados do relatório.  São suportados os seguintes tipos de anexo: PDF, apresentação do PowerPoint (PPTX), Livro do Excel (XLSX), Documento do Word (DOCX), ficheiro CSV e XML.

- Pode incluir uma imagem de pré-visualização do relatório no corpo do e-mail.  Isto é opcional e pode ser ligeiramente diferente da primeira página do documento de relatório anexado, consoante o formato do anexo selecionado. 

- O tamanho máximo do anexo do relatório é 25 MB. 

- Pode subscrever outros utilizadores a relatórios paginados que se conectem a quaisquer fontes de dados atualmente suportadas, incluindo serviços de análise Azure ou conjuntos de dados power bi. Tenha em atenção que o anexo do relatório reflete os dados com base nas suas permissões, tal como o SQL Server Reporting Services faz atualmente. 

- As subscrições de e-mail podem ser enviadas com os parâmetros atualmente selecionados ou com os parâmetros predefinidos do seu relatório.  Pode definir valores de parâmetros diferentes para cada subscrição que criar para o relatório. 

- Se o autor do relatório tiver definido parâmetros baseados em expressões (por exemplo, o parâmetro predefinido é sempre a data de hoje), a subscrição utilizará os mesmos como o valor predefinido. Pode alterar outros valores de parâmetros e optar por utilizar valores atuais. No entanto, a menos que também altere explicitamente esses valores, a subscrição utilizará os parâmetros baseados em expressões.

- Não existe a opção **Depois da Atualização de Dados** para a frequência dos relatórios paginados. Irá obter sempre os valores mais recentes da origem de dados subjacente. 

## <a name="next-steps"></a>Próximos passos

[Subscrever relatórios e dashboards no serviço Power BI para si e para outras pessoas](../collaborate-share/service-report-subscribe.md)

[Relatórios paginados no serviço Power BI](end-user-paginated-report.md)
