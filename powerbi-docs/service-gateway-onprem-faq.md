---
title: FAQ do gateway de dados no local
description: Estas são as FAQ do Gateway de dados no local. Esta secção reúne as perguntas mais frequentes sobre o gateway num único local.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 01/24/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: b4ecec3b2e53c2fea0fcbb7d78d1114da1a105ed
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34299637"
---
# <a name="on-premises-data-gateway-faq"></a>FAQ do gateway de dados no local
<!-- Shared FAQ shared Include -->
[!INCLUDE [gateway-onprem-faq-shared-include](./includes/gateway-onprem-faq-shared-include.md)]

## <a name="analysis-services"></a>Analysis Services
**Pergunta:** Posso usar msdmpump.dll para criar mapeamentos personalizados de nome de utilizador em vigor para o Analysis Services?  
**Resposta:** não. Não há atualmente suporte para esta operação.

**Pergunta:** Posso utilizar o gateway para me ligar a uma instância multidimensional (OLAP)?  
**Resposta:** Sim! O Gateway de dados no local suporta ligações em direto para os modelos em Tabela do Analysis Services e para os modelos Multidimensionais.

**Pergunta:** E se eu instalar o gateway num computador num domínio diferente do meu servidor no local que usa a autenticação do Windows?  
**Resposta:** Não é possível dar garantias. Tudo depende a relação de confiança entre os dois domínios. Se os dois domínios diferentes estiverem num modelo de domínio fidedigno, o gateway pode ser capaz de se ligar ao servidor do Analysis Services e o nome de utilizador em vigor pode ser resolvido. Caso contrário, poderá deparar-se com uma falha de início de sessão.

**Pergunta:** Como posso descobrir que nome de utilizador em vigor está a ser transmitido para o meu servidor no local do Analysis Services?  
**Resposta:** Esta pergunta é respondida no [artigo de resolução de problemas](service-gateway-onprem-tshoot.md).

**Pergunta:** Tenho 25 bases de dados no Analysis Services. Existe forma de as ter todas ativadas para o gateway em simultâneo?  
**Resposta:** não. Está nos nossos planos, mas ainda não temos um prazo.

## <a name="administration"></a>Administração
**Pergunta:** Posso ter mais do que um administrador para um gateway?  
**Resposta:** Sim! Quando gere um gateway, pode aceder ao separador do administrador para adicionar outros administradores.

**Pergunta:** O administrador de gateway precisa de ser um administrador no computador onde o gateway está instalado?  
**Resposta:** não. O administrador de gateway é utilizado para gerir o gateway do interior do serviço.

**Pergunta:** Posso impedir os utilizadores na minha organização de criar um gateway?  
**Resposta:** não. Está nos nossos planos, mas ainda não temos um prazo.

**Pergunta:** Posso obter informações de utilização e estatísticas relativas aos gateways na minha organização?  
**Resposta:** não. Está nos nossos planos, mas ainda não temos um prazo.

## <a name="power-bi"></a>Power BI
**Pergunta:** Preciso de atualizar o gateway pessoal?
**Resposta:** Não, pode continuar a utilizar o gateway pessoal para o Power BI.

**Pergunta:** Com que frequência são os mosaicos num dashboard, no Power BI, atualizados quando ligados através do Gateway de dados no local?  
**Resposta:** Sensivelmente a cada dez minutos. As ligações do DirectQuery são exatamente assim. Não significa que um mosaico emita uma consulta ao servidor no local e mostre novos dados a cada dez minutos.

**Pergunta:** Posso carregar livros do Excel com modelos de dados do Power Pivot que se liguem a origens de dados no local? É necessário um gateway para este cenário?  
**Resposta:** Sim, pode carregar o livro. E não precisa de gateway. Mas, como os dados residem no modelo de dados do Excel, os relatórios do Power BI baseados no livro do Excel não serão dinâmicos. Para poder atualizar relatórios no Power BI, precisa de carregar novamente um livro atualizado por cada vez. Pode também utilizar o gateway com atualização agendada.

**Pergunta:** Se os utilizadores partilharem dashboards com uma ligação DirectQuery, os outros utilizadores poderão ver os dados mesmo que talvez não tenham as mesmas permissões?  
**Resposta:** Para um dashboard ligado ao Analysis Services, os utilizadores verão apenas os dados aos quais tiverem acesso. Se os utilizadores não tiverem as mesmas permissões, não poderão ver os dados. Para outras origens de dados, todos os utilizadores vão partilhar as credenciais inseridas pelo administrador para aquela origem de dados.

**Pergunta:** Por que não me posso ligar ao meu servidor do Oracle?  
**Resposta:** Poderá ter de instalar o cliente do Oracle e configurar o ficheiro tnsnames.ora com as devidas informações de servidor para se ligar ao seu servidor Oracle. Trata-se de uma instalação separada fora do gateway. Para obter mais informações, consulte [Instalar o Cliente Oracle](service-gateway-onprem-manage-oracle.md#installing-the-oracle-client).

**Pergunta:** O gateway funciona com ExpressRoute?  
**Resposta:** sim. Para obter mais informações sobre o ExpressRoute e o Power BI, consulte [Power BI e ExpressRoute](service-admin-power-bi-expressroute.md).

## <a name="next-steps"></a>Próximos passos
[Gateway de dados no local](service-gateway-onprem.md)  
[Gateway de dados no local detalhado](service-gateway-onprem-indepth.md)  
[Resolução de problemas do Gateway de dados no local](service-gateway-onprem-tshoot.md)  
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

