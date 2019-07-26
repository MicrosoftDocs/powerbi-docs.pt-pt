---
title: FAQ do gateway de dados no local – Power BI
description: Estas são as FAQ do gateway de dados no local do Power BI. Esta secção reúne as perguntas mais frequentes sobre o gateway utilizado no Power BI num único local.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 99a03f88ed5f6585ca8ed6d64f396e70cdd046e5
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/16/2019
ms.locfileid: "68272752"
---
# <a name="on-premises-data-gateway-faq---power-bi"></a>FAQ do gateway de dados no local – Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

## <a name="power-bi"></a>Power BI

**Pergunta:** Preciso de atualizar o gateway pessoal?  
**Resposta:** Não: Pode continuar a utilizar o gateway pessoal do Power BI.

**Pergunta:** São necessárias permissões especiais para instalar o gateway e geri-lo no serviço Power BI?
**Resposta:** Não são necessárias permissões especiais.

**Pergunta:** Posso carregar livros do Excel com modelos de dados do Power Pivot que se liguem a origens de dados no local? É necessário um gateway para este cenário?  
**Resposta:** Sim, pode carregar o livro. E não precisa de gateway. Mas, como os dados residem no modelo de dados do Excel, os relatórios do Power BI baseados no livro do Excel não serão dinâmicos. Para poder atualizar relatórios no Power BI, precisa de carregar novamente um livro atualizado por cada vez. Pode também utilizar o gateway com atualização agendada.

**Pergunta:** Se os utilizadores partilharem dashboards com uma ligação DirectQuery, os outros utilizadores poderão ver os dados mesmo que talvez não tenham as mesmas permissões?  
**Resposta:** Num dashboard ligado ao Analysis Services, os utilizadores verão apenas os dados aos quais tiverem acesso. Se os utilizadores não tiverem as mesmas permissões, não poderão ver os dados. Para outras origens de dados, todos os utilizadores vão partilhar as credenciais inseridas pelo administrador para aquela origem de dados.

**Pergunta:** Por que não consigo ligar ao meu servidor do Oracle?  
**Resposta:** Pode ter de instalar o cliente do Oracle e configurar o ficheiro tnsnames.ora com as devidas informações de servidor para se ligar ao servidor Oracle. Trata-se de uma instalação separada fora do gateway. Para obter mais informações, consulte [Instalar o Cliente Oracle](service-gateway-onprem-manage-oracle.md#installing-the-oracle-client).

**Pergunta:** O gateway funciona com o ExpressRoute?  
**Resposta:** Yes. Para obter mais informações sobre o ExpressRoute e o Power BI, consulte [Power BI e ExpressRoute](service-admin-power-bi-expressroute.md).

**Pergunta:** Estou a utilizar o script R. É suportado?
**Resposta**: Os scripts R são suportados apenas no modo pessoal.

## <a name="analysis-services-in-power-bi"></a>Analysis Services no Power BI

**Pergunta:** Posso utilizar msdmpump.dll para criar mapeamentos personalizados de nome de utilizador em vigor para o Analysis Services?  
**Resposta:** Não. Não há atualmente suporte para esta operação.

**Pergunta:** Posso utilizar o gateway para me ligar a uma instância multidimensional (OLAP)?  
**Resposta:** Sim! O gateway empresarial no local suporta ligações em direto tanto com modelos de Tabela como Multidimensionais do Analysis Services.

**Pergunta:** E se eu instalar o gateway num computador num domínio diferente do meu servidor no local que utiliza a autenticação do Windows?  
**Resposta:** Não é possível dar garantias. Tudo depende a relação de confiança entre os dois domínios. Se os dois domínios diferentes estiverem num modelo de domínio fidedigno, o gateway pode ser capaz de se ligar ao servidor do Analysis Services e o nome de utilizador em vigor pode ser resolvido. Caso contrário, poderá deparar-se com uma falha de início de sessão.

**Pergunta:** Como posso descobrir que nome de utilizador em vigor está a ser transmitido para o meu servidor no local do Analysis Services?  
**Resposta:** Esta pergunta é respondida no [artigo de resolução de problemas](service-gateway-onprem-tshoot.md).

## <a name="next-steps"></a>Próximos passos

* [Resolução de problemas do gateway de dados no local](/data-integration/gateway/service-gateway-tshoot)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

