---
title: Colaborar no Microsoft Teams com o Power BI
description: À medida que a força de trabalho distribuída se torna a norma, cada vez mais organizações dependem do Microsoft Teams para permitir o trabalho remoto e manter os colaboradores ligados.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 12/14/2020
ms.openlocfilehash: 80aa8097ce38a9b1bac228ea61dcc959e4aba60d
ms.sourcegitcommit: 46cf62d9bb33ac7b7eae7910fbba6756f626c65f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97492018"
---
# <a name="collaborate-in-microsoft-teams-with-power-bi"></a>Colaborar no Microsoft Teams com o Power BI

À medida que a força de trabalho distribuída se torna a norma, cada vez mais organizações dependem do Microsoft Teams para permitir o trabalho remoto e manter os colaboradores ligados. Este artigo destaca as opções para partilhar e colaborar nos conteúdos interativos do Power BI nos canais e chats do Microsoft Teams. 

- Com o **separador Power BI** do Microsoft Teams, pode [incorporar relatórios interativos em canais e chats do Microsoft Teams](service-embed-report-microsoft-teams.md). O separador Power BI ajuda os seus colegas a encontrar os dados da sua equipa e debater sobre os mesmos nos canais da equipa. 
- Crie uma [pré-visualização da ligação](service-teams-link-preview.md) quando cola uma ligação para os seus relatórios, dashboards e aplicações na caixa de mensagens do Microsoft Teams. A pré-visualização da ligação mostra informações sobre a ligação. 
- Quando estiver a ver relatórios e dashboards no serviço Power BI, utilize a funcionalidade [Conversar no Microsoft Teams](service-share-report-teams.md) para iniciar rapidamente conversações no Microsoft Teams.
- Utilize a [aplicação do Power BI no Microsoft Teams](service-microsoft-teams-app.md) para trazer toda a experiência básica do serviço Power BI para o Microsoft Teams.
 
:::image type="content" source="media/service-collaborate-microsoft-teams/power-bi-embed-teams-report.png" alt-text="Captura de ecrã a mostrar um relatório do Power BI incorporado num canal do Microsoft Teams":::.

## <a name="requirements"></a>Requirements

Em geral, para que o Power BI funcione no Microsoft Teams, certifique-se de que estes elementos estão presentes:

- Os seus utilizadores têm uma licença do Power BI Pro ou que o relatório está incluído numa [capacidade Premium do Power BI (EM ou P SKU)](../admin/service-premium-what-is.md) com uma licença do Power BI.
- Os utilizadores têm de iniciar sessão no serviço Power BI para ativar a respetiva licença do Power BI.
- Os utilizadores cumprem os requisitos para utilizar o separador **Power BI** no Microsoft Teams.

## <a name="grant-access-to-reports"></a>Conceder acesso a relatórios

Incorporar um relatório no Microsoft Teams ou enviar uma ligação para um item não dá automaticamente permissão aos utilizadores para verem o relatório. Tem de [permitir que os utilizadores vejam o relatório no Power BI](service-share-dashboards.md). Para facilitar o processo, pode utilizar um Grupo do Microsoft 365 para a equipa.

> [!IMPORTANT]
> Certifique-se de que revê quem pode ver o relatório no serviço Power BI e conceda acesso aos que não estão listados.

Uma forma de garantir que todas as pessoas numa equipa têm acesso aos relatórios é ao colocá-los numa única área de trabalho e dar acesso ao Grupo do Microsoft 365 da sua equipa.

## <a name="known-issues-and-limitations"></a>Limitações e problemas conhecidos

- O Power BI não suporta os mesmos idiomas localizados que o Microsoft Teams. Como tal, poderá não ver uma localização correta no relatório incorporado.
- Os dashboards do Power BI não podem ser incorporados no separador **Power BI** do Microsoft Teams.
- Os utilizadores sem uma licença do Power BI ou permissão para aceder ao relatório verão uma mensagem a indicar “Conteúdo não disponível”.
- Poderá ter problemas se utilizar o Internet Explorer 10. <!--You can look at the [browsers support for Power BI](../fundamentals/power-bi-browsers.md) and for [Microsoft 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- Os [filtros de URL](service-url-filters.md) não são suportados no separador **Power BI** do Microsoft Teams.
- Nas clouds nacionais, o novo separador **Power BI** não está disponível. Poderá estar disponível uma versão mais antiga que não suporta a nova experiência de área de trabalho ou relatórios em aplicações do Power BI.
- Depois de guardar o separador, não pode alterar o nome do separador através das definições do separador. Utilize a opção **Mudar nome** para o alterar.
- O serviço de pré-visualização da ligação não suporta o início de sessão único.
- As pré-visualizações de ligações não funcionam em chats de reuniões ou canais privados.

## <a name="microsoft-power-platform-in-microsoft-teams"></a>Microsoft Power Platform no Microsoft Teams

As outras aplicações do Microsoft Power Platform também se integram ao Microsoft Teams.

- [Experiência de administração do Power Platform](/power-platform/admin/about-teams-environment)
- [Power Automate](/power-automate/teams/overview)
- [Power Apps](/powerapps/teams/overview)
- [Power Virtual Agents](/power-virtual-agents/)

## <a name="next-steps"></a>Próximos passos

- [Incorporar conteúdos do Power BI no Microsoft Teams](service-embed-report-microsoft-teams.md)
- [Obter uma pré-visualização da ligação do Power BI no Microsoft Teams](service-teams-link-preview.md)
- [Conversar no Microsoft Teams diretamente do serviço Power BI](service-share-report-teams.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/).
