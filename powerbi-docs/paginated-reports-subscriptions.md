---
title: Subscrever relatórios paginados no serviço Power BI
description: Neste artigo, vai aprender aspetos a ter em mente sobre como assinar os relatórios paginados no serviço Power BI.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 05/24/2019
ms.openlocfilehash: ccec6658808d94728f2a4f14de67c36da0f51def
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222208"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Subscrever-se e outros relatórios paginados no serviço Power BI 

Agora pode configurar subscrições de e-mail para si e para outras pessoas para relatórios paginados no serviço Power BI. Em geral, o processo é o mesmo que [subscrever relatórios e dashboards no serviço Power BI](service-report-subscribe.md). Este artigo descreve as diferenças e considerações. 

Na configuração de subscrições, escolha com que frequência quer receber os e-mails: diária, semanal ou por hora. Se escolher diariamente ou semanalmente, pode escolher o tempo que pretende a subscrição que pretende executar. Em todos, pode definir até 24 diferentes subscrições por dia para cada relatório. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Considerações para subscrições de relatórios paginados 

- Ao contrário das subscrições de dashboards ou relatórios do Power BI, a sua subscrição contém um anexo do resultado completo de relatório.  São suportados os seguintes tipos de anexo: PDF, apresentação do PowerPoint (PPTX), pasta de trabalho (XLSX do Excel), documentos do Word (DOCX), ficheiro CSV e XML.

- Não existe nenhuma imagem de pré-visualização do relatório no corpo do e-mail.  Estamos a planear para que a imagem da primeira página do relatório como um item opcional. 

- O tamanho do anexo de relatório máximo é de 25 MB. 

- Pode subscrever outros utilizadores para relatórios paginados, que se ligam a quaisquer origens de dados atualmente suportadas, incluindo conjuntos de dados do Azure Analysis Services ou o Power BI. Tenha em atenção que o anexo do relatório reflete os dados com base em suas permissões, tal como sucede SQL Server Reporting Services. 

- As subscrições de páginas de relatório estão associadas ao nome do relatório.  

- Subscrições de correio eletrónico são enviadas com os valores de parâmetro predefinidos do relatório. 

- Não existe nenhuma **após a atualização de dados** opção para a frequência com relatórios paginados. Sempre obtém os valores mais recentes da origem de dados subjacente. 

## <a name="next-steps"></a>Próximos passos

[Subscrever-se e outros relatórios e dashboards no serviço Power BI](service-report-subscribe.md)

[O que são relatórios paginados no Power BI Premium? (Pré-visualização)](paginated-reports-report-builder-power-bi.md)
