---
title: FAQ do gateway de dados no local – Power BI
description: Este artigo inclui as FAQ do gateway de dados no local do Power BI. Este artigo reúne as perguntas mais frequentes sobre o gateway utilizado no Power BI num único local.
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: f9a51e6150c7ae351cea968c0d7ea39d2d0d6c32
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96392226"
---
# <a name="on-premises-data-gateway-faq---power-bi"></a>FAQ do gateway de dados no local – Power BI

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

## <a name="power-bi"></a>Power BI

**Pergunta:** Tenho de atualizar o gateway de dados no local (modo pessoal)?

**Resposta:** Não. Pode continuar a utilizar o gateway (modo pessoal) do Power BI.

**Pergunta:** São necessárias permissões especiais para instalar o gateway e geri-lo no serviço Power BI?

**Resposta:** Não são necessárias permissões especiais.

**Pergunta:** Posso carregar livros do Excel com modelos de dados do Power Pivot que se liguem a origens de dados no local? É necessário um gateway para este cenário? 

**Resposta:** Sim, pode carregar o livro. E não precisa de gateway. No entanto, como os dados residem no modelo de dados do Excel, os relatórios do Power BI baseados no livro do Excel não serão dinâmicos. Para atualizar relatórios no Power BI, terá sempre de carregar novamente um livro atualizado. Pode também utilizar o gateway com atualização agendada.

**Pergunta:** Se os utilizadores partilharem dashboards com uma ligação do DirectQuery, os outros utilizadores conseguirão ver os dados mesmo que não tenham as mesmas permissões? 

**Resposta:** Num dashboard ligado ao Azure Analysis Services, os utilizadores veem apenas os dados aos quais têm acesso. Se os utilizadores não tiverem as mesmas permissões, não conseguirão ver os dados. Para outras origens de dados, todos os utilizadores vão partilhar as credenciais inseridas pelo administrador para aquela origem de dados.

**Pergunta:** Por que não consigo ligar ao meu servidor do Oracle? 

**Resposta:** Poderá ter de instalar o cliente Oracle e configurar o ficheiro tnsnames.ora com as devidas informações de servidor para se ligar ao servidor Oracle. Trata-se de uma instalação separada fora do gateway. Para obter mais informações, veja [Instalar o cliente Oracle](service-gateway-onprem-manage-oracle.md#install-the-oracle-client).

**Pergunta:** Estou a utilizar o script R. É suportado?

**Resposta**: Os scripts R são suportados apenas no modo pessoal.

## <a name="analysis-services-in-power-bi"></a>Analysis Services no Power BI

**Pergunta:** Posso utilizar msmdpump.dll para criar mapeamentos personalizados de nome de utilizador em vigor para o Analysis Services? 

**Resposta:** Não. Neste momento, esta utilização não é suportada.

**Pergunta:** Posso utilizar o gateway para ligar a uma instância multidimensional (OLAP)? 

**Resposta:** Yes. O gateway empresarial no local suporta ligações em direto tanto com modelos de Tabela como Multidimensionais do Analysis Services.

**Pergunta:** E se eu instalar o gateway num computador num domínio diferente do meu servidor no local que utiliza a autenticação do Windows? 

**Resposta:** Não é possível dar garantias. Tudo depende a relação de confiança entre os dois domínios. Se os dois domínios diferentes estiverem num modelo de domínio de confiança, o gateway poderá ligar-se ao servidor do Analysis Services e o nome de utilizador em vigor poderá ser resolvido. Caso contrário, poderá deparar-se com uma falha de início de sessão.

**Pergunta:** Como posso descobrir que nome de utilizador em vigor está a ser transmitido para o meu servidor no local do Analysis Services? 

**Resposta:** Respondemos a esta questão no [artigo de resolução de problemas](service-gateway-onprem-tshoot.md).

## <a name="next-steps"></a>Próximos passos

* [Resolução de problemas do gateway de dados no local](/data-integration/gateway/service-gateway-tshoot)

Mais perguntas? Experimente perguntar à [Comunidade do Power BI](https://community.powerbi.com/).
