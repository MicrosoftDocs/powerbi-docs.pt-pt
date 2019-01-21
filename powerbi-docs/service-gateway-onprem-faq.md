---
title: FAQ do gateway de dados no local
description: Estas são as FAQ do Gateway de dados no local. Esta secção reúne as perguntas mais frequentes sobre o gateway num único local.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 01/24/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: b1c74968365db59d51f7c0a7bdb356552cc75596
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54283788"
---
# <a name="on-premises-data-gateway-faq"></a>FAQ do gateway de dados no local
<!-- Shared FAQ shared Include -->
[!INCLUDE [gateway-onprem-faq-shared-include](./includes/gateway-onprem-faq-shared-include.md)]

## <a name="analysis-services"></a>Analysis Services
**Pergunta:** Posso utilizar msdmpump.dll para criar mapeamentos personalizados de nome de utilizador em vigor para o Analysis Services?  
**Resposta:** Não. Não há atualmente suporte para esta operação.

**Pergunta:** Posso utilizar o gateway para me ligar a uma instância multidimensional (OLAP)?  
**Resposta:** Sim! O Gateway de dados no local suporta ligações em direto para os modelos em Tabela do Analysis Services e para os modelos Multidimensionais.

**Pergunta:** E se eu instalar o gateway num computador num domínio diferente do meu servidor no local que utiliza a autenticação do Windows?  
**Resposta:** Não é possível dar garantias. Tudo depende a relação de confiança entre os dois domínios. Se os dois domínios diferentes estiverem num modelo de domínio fidedigno, o gateway pode ser capaz de se ligar ao servidor do Analysis Services e o nome de utilizador em vigor pode ser resolvido. Caso contrário, poderá deparar-se com uma falha de início de sessão.

**Pergunta:** Como posso descobrir que nome de utilizador em vigor está a ser transmitido para o meu servidor no local do Analysis Services?  
**Resposta:** Esta pergunta é respondida no [artigo de resolução de problemas](service-gateway-onprem-tshoot.md).

**Pergunta:** Tenho 25 bases de dados no Analysis Services. Existe forma de as ter todas ativadas para o gateway em simultâneo?  
**Resposta:** Não. Está nos nossos planos, mas ainda não temos um prazo.

## <a name="administration"></a>Administração
**Pergunta:** Posso ter mais do que um administrador para um gateway?  
**Resposta:** Sim! Quando gere um gateway, pode aceder ao separador do administrador para adicionar outros administradores.

**Pergunta:** O administrador de gateway precisa de ser um administrador no computador onde o gateway está instalado?  
**Resposta:** Não. O administrador de gateway é utilizado para gerir o gateway do interior do serviço.

**Pergunta:** Posso impedir os utilizadores na minha organização de criar um gateway?  
**Resposta:** Não. Está nos nossos planos, mas ainda não temos um prazo.

**Pergunta:** Posso obter informações de utilização e estatísticas relativas aos gateways na minha organização?  
**Resposta:** Não. Está nos nossos planos, mas ainda não temos um prazo.

## <a name="power-bi"></a>Power BI
**Pergunta:** Preciso de atualizar o gateway pessoal?
**Resposta:** Não: Pode continuar a utilizar o gateway pessoal do Power BI.

**Pergunta:** No Power BI, com que frequência são os mosaicos num dashboard atualizados quando ligados através do Gateway de dados no local?  
**Resposta:** Sensivelmente a cada dez minutos. As ligações do DirectQuery são exatamente assim. Não significa que um mosaico emita uma consulta ao servidor no local e mostre novos dados a cada dez minutos.

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

## <a name="next-steps"></a>Próximos passos
[Gateway de dados no local](service-gateway-onprem.md)  
[Gateway de dados no local detalhado](service-gateway-onprem-indepth.md)  
[Resolução de problemas do Gateway de dados no local](service-gateway-onprem-tshoot.md)  
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

