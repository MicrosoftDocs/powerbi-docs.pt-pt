---
title: O que é a administração do Power BI?
description: Saiba mais sobre a configuração de políticas de governação do Power BI, monitorização de utilização e o aprovisionamento de licenças, capacidades e recursos organizacionais.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: overview
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 9e9ed930cc557250a9e1702d6010536ed069cd7b
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83129525"
---
# <a name="what-is-power-bi-administration"></a>O que é a administração do Power BI?

A administração do Power BI é a gestão de um inquilino do Power BI, incluindo a configuração de políticas de governação, monitorização de utilização e o aprovisionamento de licenças, capacidades e recursos organizacionais. Este artigo fornece uma descrição geral das funções, tarefas e ferramentas de administração; e ligações para artigos que entram em maior detalhe.

![Portal de administração do Power BI](media/service-admin-administering-power-bi-in-your-organization/admin-portal.png)

O Power BI foi concebido para business intelligence de gestão personalizada e o administrador é o guardião dos dados, processos e políticas no inquilino do Power BI. Um administrador do Power BI é um membro chave de uma equipa que inclui os programadores, os analistas e outras funções do BI. O administrador pode ajudar prestar suporte a uma organização para confirmar que são cumpridos os objetivos críticos:

- Compreender os KPIs e as métricas de que os utilizadores _realmente_ precisam
- Diminuir o tempo de entrega para relatórios empresariais orientados para TI
- Aumentar a adoção e retorno do investimento de uma implementação do Power BI

A tarefa é tornar os utilizadores empresariais produtivos e garantir a segurança e a conformidade com as leis e regulamentos. As responsabilidades podem incluir a ajuda e o suporte e, em muitos casos, prestar assistência a utilizadores empresariais para agirem corretamente.

## <a name="administrator-roles-related-to-power-bi"></a>Funções de administrador relacionadas com o Power BI

Existem várias funções relacionadas com a administração do Power BI, abordadas na tabela seguinte.

| **Tipo de administrator** | **Âmbito administrativo** | **Âmbito do Power BI** |
| --- | --- | --- |
| Administrador Global do Office 365 | Office 365 | Pode gerir todos os aspetos de um inquilino do Power BI e outros serviços. |
| Administrador de Faturação do Office 365 | Office 365 | Pode adquirir licenças do Power BI através de subscrições do Office 365. |
| Administrador do Serviço Power BI | Inquilino do Power BI | Tem controlo total sobre um inquilino do Power BI e as funcionalidades administrativas (exceto para licenciamento). |
| Administrador de Capacidade do Power BI Premium | Uma capacidade Premium única | Tem controlo total sobre uma capacidade Premium e as funcionalidades administrativas. |
| Administrador de Capacidade do Power BI Embedded | Uma capacidade Embedded única | Tem controlo total sobre uma capacidade Embedded e as funcionalidades administrativas. |

Os administradores Globais no Office 365 ou no Azure Active Directory têm direitos de administrador no Power BI. Um Administrador Global do Office 365 pode atribuir outros utilizadores para a função de Administrador de Serviço Power BI, o que concede direitos administrativos através apenas para funcionalidades do Power BI.

Os Administradores de Serviço Power BI têm acesso ao portal de administração do Power BI, que inclui várias definições ao nível do inquilino relativamente a funcionalidades, segurança e monitorização. Os Administradores de Serviço têm acesso total a todos os recursos de um inquilino do Power BI. Na maioria dos casos, os Administradores de Serviço identificam problemas e, em seguida, acompanham os proprietários dos recursos para tomar medidas corretivas.

A função de Administrador de Serviço do Power BI não concede a capacidade de atribuir licenças a utilizadores ou visualizar registos de auditoria no Office 365. Por conseguinte, a tarefa de administrar o Power BI não pode de momento ser realizada pelos utilizadores que sejam apenas os membros da função de Administrador de Serviço do Power BI.

## <a name="administrative-tasks"></a>Tarefas administrativas

Os administradores executam bastantes tarefas para suportar o Power BI da organização, abordadas na tabela seguinte.

| **Área de tarefa** | **Tarefas comuns** |
| --- | --- |
| Gerir o inquilino do Power BI |<ul><li>Ativar e desativar as principais funcionalidades do Power BI<br><li>Relatório sobre a utilização e o desempenho<br><li>Rever e gerir auditoria de eventos</ul>|
| Adquirir e atribuir licenças do Power BI |<ul><li>Gerir a inscrição de utilizadores<br><li>Comprar e atribuir licenças Pro<br><li>Impedir que os utilizadores acedam ao Power BI</ul>|
| Gerir capacidade Premium |<ul><li>Adquirir e trabalhar com capacidade Premium<br><li>Garantir a qualidade do serviço|
| Gerir a capacidade Embedded |<ul><li>Adquirir a capacidade Embedded para simplificar como os ISVs e os programadores de utilizam as capacidades do Power BI</ul>|
| Garantir a conformidade com políticas internas, leis e regulamentos | <ul><li>Gerir a classificação de dados de negócio<br><li>Ajudar a impor políticas de partilha e publicação de conteúdos</ul>|
| Gerir recursos do Power BI |<ul><li>Gerir áreas de trabalho<br><li>Publicar elementos visuais do Power BI<br><li>Validar códigos que servem para incorporar o Power BI noutras aplicações|
| Fornecer ajuda e suporte aos utilizadores inquilinos |<ul><li>Resolver problemas de acesso a dados e outros problemas</ul>|
| Outras tarefas |<ul><li>Implementar o Power BI Desktop, por exemplo, com o Microsoft Endpoint Configuration Manager<br><li>Gerir a implementação de aplicações móveis do Power BI com o Intune<br><li>Gerir a privacidade e a segurança dos dados,como a segurança dos dados de origem</ul>|

## <a name="administrative-tools"></a>Ferramentas administrativas

Existem várias ferramentas relacionadas com a administração do Power BI, abordadas na tabela seguinte. Normalmente, os administradores passam a maior parte do tempo no portal de Administração do Power BI e utilizam outras ferramentas conforme necessário.

| **Ferramenta** | **Tarefas comuns** |
| --- | --- |
| Portal de administração do Power BI |<ul><li>Adquirir e trabalhar com capacidade Premium</li><li>Garantir a qualidade do serviço</li><li>Gerir a classificação de dados de negócio</li><li>Ajudar a impor políticas de partilha e publicação de conteúdos</li><li>Gerir áreas de trabalho<br><li>Publicar elementos visuais do Power BI</li><li>Validar códigos que servem para incorporar o Power BI noutras aplicações</li><li>Resolver problemas de acesso a dados e outros problemas</li></ul>|
| Centro de administração do Microsoft 365 |<ul><li>Gerir a inscrição de utilizadores</li><li>Comprar e atribuir licenças Pro</li><li>Impedir que os utilizadores acedam ao Power BI</li></ul>|
| Centro de Conformidade e Segurança do Office 365 |<ul><li>Rever e gerir auditoria de eventos</li></ul>|
| Azure Active Directory (AAD) no portal do Azure |<ul><li>Configurar acesso condicional a recursos do Power BI através do AAD</li><li>Aprovisionar capacidade do Power BI Embedded</li></ul>|
| Cmdlets do PowerShell |<ul><li>Gerir áreas de trabalho e outros aspetos do Power BI através de scripts</li></ul>|
| SDK e APIs Administrativas |<ul><li>Crie ferramentas administrativas personalizadas para facilitar o trabalho de um administrador do Power BI. Por exemplo, o Power BI Desktop pode utilizar estas APIs para criar relatórios com base nos dados relacionados com a administração</li></ul>|

## <a name="next-steps"></a>Próximos passos

Esperamos que este artigo lhe tenha fornecido algumas informações rápidas relativas à função do administrador do Power BI, bem como as funções, tarefas e ferramentas específicas envolvidas. Recomendamos os seguintes artigos para saber mais.

- [Utilizar o portal de administração do Power BI](service-admin-portal.md)
- [Orientação sobre as definições para administradores de inquilinos](../guidance/admin-tenant-settings.md)
- [Utilizar cmdlets do PowerShell](/powershell/power-bi/overview)
- [FAQ de administração do Power BI](service-admin-faq.md)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)
