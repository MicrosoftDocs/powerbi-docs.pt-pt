---
title: Perguntas frequentes sobre os elementos visuais personalizados do Power BI
description: Navegue numa lista de perguntas frequentes e respostas sobre os elementos visuais personalizados do Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 10/29/2018
LocalizationGroup: Visualizations
ms.openlocfilehash: 064d32944f52f6e391d4a7ec4df41ecbf09b7e3f
ms.sourcegitcommit: 02f918a4f27625b6f4e47473193ebc8219db40e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223082"
---
# <a name="frequently-asked-questions-about-power-bi-custom-visuals"></a>Perguntas frequentes sobre os elementos visuais personalizados do Power BI

## <a name="organizational-custom-visuals"></a>Elementos visuais personalizados organizacionais

**Como é que o administrador pode gerir os elementos visuais personalizados organizacionais?**

No Portal de administração, no separador “Elementos visuais personalizados organizacionais”, o administrador pode ver e [gerir todos os elementos visuais personalizados organizacionais da empresa](https://docs.microsoft.com/power-bi/service-admin-portal#organization-visuals): adicionar, desativar, ativar e eliminar.
Nunca mais terá de partilhar esses elementos visuais por mensagens de e-mail ou pasta partilhada! Depois de implementados no repositório organizacional, os utilizadores na organização podem facilmente localizá-los e importar os elementos visuais personalizados organizacionais para os relatórios diretamente do Power BI Desktop ou do Serviço. Os elementos visuais personalizados organizacionais podem ser encontrados na loja integrada (no Power BI Desktop ou no serviço) no separador “A MINHA ORGANIZAÇÃO”. Quando o administrador carrega uma nova versão de um elemento visual personalizado organizacional, todas as pessoas na organização recebem a mesma versão atualizada. Os autores do relatório não precisam de eliminar o elemento visual nos seus relatórios para obter a nova versão destes elementos visuais, uma vez que todos os relatórios com estes elementos visuais são atualizados automaticamente! O mecanismo de atualização é semelhante ao dos elementos visuais do marketplace.

**Se um administrador carregar um elemento visual personalizado do marketplace público para a loja da organização, este será automaticamente atualizado assim que o fornecedor atualizar o elemento visual no marketplace público?**

Não, não existe nenhuma atualização automática no marketplace público.
O Administrador é responsável por atualizar a versão dos elementos visuais personalizados organizacionais, se assim o pretender.

**Há alguma forma de desativar a loja organizacional?**

Não, os utilizadores veem sempre o separador “A MINHA ORGANIZAÇÃO” no Power BI Desktop e no serviço. O administrador pode desativar ou eliminar todos os elementos visuais personalizados organizacionais no portal de administração e a loja organizacional fica vazia.
  
**Se o administrador desativar os elementos visuais personalizados no Portal de administração (Definições de inquilino), os utilizadores ainda terão acesso aos elementos visuais personalizados organizacionais?**

Sim, se o administrador desativar os elementos visuais personalizados no portal de administração, a loja organizacional não será afetada. Algumas organizações desativam os elementos visuais personalizados e ativam apenas os elementos visuais selecionados manualmente que foram importados e carregados pelo administrador do Power BI para a loja organizacional. No Power BI Desktop, não é imposta a desativação dos elementos visuais personalizados no Portal de administração. Os utilizadores do Power BI Desktop continuam a poder adicionar e utilizar os elementos visuais personalizados do marketplace público nos seus relatórios. No entanto, esses elementos visuais personalizados públicos deixam de ser compostos assim que são publicados no Serviço Power BI e emitem um erro apropriado. Quando utiliza o serviço Power BI, não poderá importar elementos visuais personalizados do marketplace público. Pode importar apenas os elementos visuais da loja organizacional porque a definição dos elementos visuais personalizados no portal de administração é imposta no serviço Power BI.

**Por que motivo a loja organizacional e os elementos visuais personalizados organizacionais são uma ótima solução empresarial?**

* Todos recebem a mesma versão do elemento visual, que é controlada pelo administrador do Power BI. Assim que o administrador atualiza a versão do elemento visual no portal de administração, todos os utilizadores da organização recebem automaticamente a versão atualizada.

* Nunca mais terá de partilhar ficheiros de elementos visuais por e-mail ou pastas partilhadas! Um único local, visíveis para todos os membros com sessão iniciada.

* Segurança e compatibilidade: as novas versões dos elementos visuais personalizados organizacionais são atualizadas automaticamente em todos os relatórios, à semelhança dos elementos visuais do marketplace.

* Os utilizadores da organização que utilizam os elementos visuais personalizados organizacionais têm de ter sessão iniciada para ver e utilizar esses elementos visuais, que representam um elemento de segurança para a organização.

* Os administradores podem controlar quais são os elementos visuais personalizados disponíveis na organização.

* Os administradores podem ativar/desativar os elementos visuais para fins de teste no portal de administração. Esse procedimento resulta numa melhor imposição da segurança, uma vez que esses elementos visuais apenas serão disponibilizados aos membros da organização.

## <a name="certified-custom-visuals"></a>Elementos visuais personalizados certificados

**O que são os elementos visuais personalizados certificados?**

Os elementos visuais personalizados certificados são os elementos visuais do [marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) que cumprem determinados testes e requisitos de código [especificados](power-bi-custom-visuals-certified.md) pela equipa do Power BI.  Os testes realizados foram concebidos para verificar se o elemento visual não acede a serviços ou a recursos externos. No entanto, a Microsoft não cria elementos visuais personalizados de terceiros e aconselha os clientes a contactarem o autor diretamente para verificarem a funcionalidade desses elementos visuais.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre resoluções de problemas, aceda a [Troubleshooting your Power BI custom visuals](power-bi-custom-visuals-troubleshoot.md) (Resolver problemas com os elementos visuais personalizados do Power BI).
