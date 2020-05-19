---
title: Organizar o trabalho nas novas áreas de trabalho no Power BI
description: Saiba mais sobre as novas áreas de trabalho, que são coleções de dashboards e relatórios criadas para disponibilizar métricas importantes à sua organização.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/07/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: c74e9c3119c9c9a8057672d68e6499d93b46e3f8
ms.sourcegitcommit: 9dd6dc8c06091ea02dee5e9ddc45a2922877b1f2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/08/2020
ms.locfileid: "82991376"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Organizar o trabalho nas novas áreas de trabalho no Power BI

As *áreas de trabalho* são locais onde pode colaborar com colegas para criar coleções de dashboards, relatórios, conjuntos de dados e relatórios paginados. A nova experiência de área de trabalho ajuda a gerir melhor o acesso ao conteúdo. Este artigo descreve as novas áreas de trabalho e como diferem das áreas de trabalho clássicas.  Tal como acontece com as áreas de trabalho clássicas, ainda as utilizar para criar e distribuir aplicações. Pronto para criar uma nova área de trabalho? Leia [Criar uma nova experiência de área de trabalho](service-create-the-new-workspaces.md).

As áreas de trabalho novas e atualizadas podem coexistir lado a lado com as áreas de trabalho clássicas existentes. A nova experiência de área de trabalho é o tipo de área de trabalho predefinido. Se necessário, pode criar e utilizar na mesma [áreas de trabalho clássicas](service-create-workspaces.md) com base nos Grupos do Office 365. Pronto para migrar a área de trabalho clássica? Veja [Atualizar as áreas de trabalho clássicas para as novas áreas de trabalho no Power BI](designer/service-upgrade-workspaces.md) para obter detalhes.

Com as novas áreas de trabalho, pode:

- Atribuir funções de área de trabalho a grupos de utilizadores: grupos de segurança, listas de distribuição, grupos do Office 365 e utilizadores individuais.
- Crie uma área de trabalho no Power BI sem criar um grupo do Office 365 associado subjacente. Todas as tarefas de administração da área de trabalho são efetuadas no Power BI, não no Office 365.
- Continue a gerir o acesso dos utilizadores ao conteúdo através dos grupos do Office 365, se assim quiser. Basta adicionar um grupo do Office 365 à lista de acesso da área de trabalho.
- Utilizar funções de áreas de trabalho mais avançadas para uma gestão de permissões mais flexível numa área de trabalho.

O Power BI continua a listar todos os Grupos do Office 365 dos quais é membro. Tal evita a alteração dos fluxos de trabalho existentes.

## <a name="new-and-classic-workspace-differences"></a>Diferenças entre as áreas de trabalho novas e clássicas

Reestruturámos algumas funcionalidades nas novas áreas de trabalho. Veja a seguir as principais diferenças.

* A criação destas áreas de trabalho não irá criar grupos do Office 365, ao contrário do que acontece nas áreas de trabalho clássicas. No entanto, agora pode utilizar um grupo do Office 365 para conceder aos utilizadores acesso à área de trabalho ao atribuir-lhes uma função. 
* Nas áreas de trabalho clássicas, só pode adicionar utilizadores individuais à lista de membros e administradores. Nas novas áreas de trabalho, pode adicionar vários grupos de segurança do Active Directory, listas de distribuição ou grupos do Office 365 a estas listas para uma gestão de utilizadores mais fácil. 
- Pode criar um pacote de conteúdos organizacionais a partir de uma área de trabalho clássica. Não pode criar um pacote a partir das novas áreas de trabalho.
- Pode utilizar um pacote de conteúdos organizacionais a partir de uma área de trabalho clássica. Não pode utilizar um pacote a partir das novas áreas de trabalho.

### <a name="workspace-features-that-work-differently"></a>Funcionalidades da área de trabalho que funcionam de forma diferente

Algumas funcionalidades funcionam de forma diferente das áreas de trabalho atuais nas novas áreas de trabalho. Estas diferenças são intencionais, com base no feedback que recebemos dos clientes. Permitem uma abordagem mais flexível à colaboração com áreas de trabalho.

- **Imposição de licenciamento**: a publicação de relatórios na nova experiência de área de trabalho impõe as regras de licenciamento existentes. Os utilizadores que colaboram em áreas de trabalho ou partilham conteúdos com outros utilizadores no serviço Power BI precisam de uma licença do Power BI Pro. Os utilizadores sem uma licença do Pro veem o erro "Apenas os utilizadores com licenças do Power BI Pro podem publicar nesta área de trabalho".
- **Os membros podem ou não voltar a partilhar**: a função de Contribuidor substitui esta definição.
- **Áreas de trabalho só de leitura**: ao invés de conceder aos utilizadores um acesso só de leitura a uma área de trabalho, atribua-lhes a função de Visualizador. Tal permite um acesso só de leitura semelhante ao conteúdo numa área de trabalho.
- Os **utilizadores sem uma licença Pro** poderão aceder à área de trabalho se esta estiver numa capacidade do Power BI Premium, mesmo que estes tenham apenas a função de Visualizador.
- **Permitir que os utilizadores exportem dados**: os utilizadores com a função de Visualizador poderão exportar dados se tiverem a Permissão de compilação nos conjuntos de dados na área de trabalho. Saiba mais sobre as [Permissões de compilação para conjuntos de dados](service-datasets-build-permissions.md).
- O botão **Sair da área de trabalho** não existe.

### <a name="workspace-contact-list"></a>Lista de contactos da área de trabalho

A nova funcionalidade **Lista de contactos** permite-lhe especificar os utilizadores que recebem notificações sobre problemas que afetam a área de trabalho. Por predefinição, qualquer utilizador ou grupo especificado como administrador da área de trabalho é notificado, mas pode personalizar a lista. Os utilizadores ou grupos incluídos na lista de contactos serão apresentados na interface de utilizador (IU) para ajudar os utilizadores a obterem ajuda relacionada com a área de trabalho. 

Leia mais sobre a [definição da lista de contactos da área de trabalho](service-create-the-new-workspaces.md#workspace-contact-list).

### <a name="workspace-onedrive"></a>OneDrive da área de trabalho

A funcionalidade OneDrive da área de trabalho permite-lhe configurar um Grupo do Office 365 cujo armazenamento de ficheiros da Biblioteca de Documentos do SharePoint está disponível para os utilizadores da área de trabalho. Crie o grupo fora do Power BI.

O Power BI não sincroniza as permissões de utilizadores ou grupos que estão configurados para terem acesso à área de trabalho com a associação ao Grupo do Office 365. A melhor prática consiste em gerir o acesso à área de trabalho através do mesmo Grupo do Office 365 cujo armazenamento de ficheiros configurar nesta definição. 

Leia mais sobre como [definir e aceder ao OneDrive da área de trabalho](service-create-the-new-workspaces.md#workspace-onedrive).  

## <a name="roles-in-the-new-workspaces"></a>Funções nas novas áreas de trabalho

Para conceder acesso a uma nova área de trabalho, adicione grupos de utilizadores ou indivíduos a uma das funções da área de trabalho: administradores, membros, contribuidores ou visualizadores. Todas as pessoas num grupo de utilizadores obtêm a função que definiu. Se um utilizador estiver em vários grupos de utilizadores, receberá o nível de permissão mais elevado concedido pelas funções que lhe estão atribuídas.

As funções permitem-lhe gerir as ações de cada utilizador numa área de trabalho, para que as equipas possam colaborar. As novas áreas de trabalho permitem-lhe atribuir funções a utilizadores individuais e a grupos de utilizadores: grupos de segurança, grupos do Office 365 e listas de distribuição. 

Quando atribui funções a um grupo de utilizadores, os utilizadores nesse grupo têm acesso aos conteúdos. Se aninhar grupos de utilizadores, todos os utilizadores incluídos nos mesmos têm permissão.

[!INCLUDE [power-bi-workspace-roles-table](includes/power-bi-workspace-roles-table.md)]

> [!NOTE]
> Para impor segurança ao nível da linha (RLS) aos utilizadores que procuram conteúdos numa área de trabalho, utilize a função Visualizador. Para impor a RLS sem dar acesso à área de trabalho, publique uma aplicação do Power BI para estes utilizadores ou utilize a partilha para distribuir conteúdos.

## <a name="licensing"></a>Licensing
Todas as pessoas que adiciona a uma área de trabalho na capacidade partilhada precisam de ter uma licença do Power BI Pro. Na área de trabalho, estes utilizadores podem colaborar nos dashboards e relatórios que planear publicar para um vasto público ou mesmo para toda a organização. 

Se quiser distribuir conteúdos para outras pessoas na sua organização, pode atribuir licenças do Power BI Pro a esses utilizadores ou colocar a área de trabalho numa capacidade do Power BI Premium.

Quando a área de trabalho está numa capacidade do Power BI Premium, os utilizadores com a função Visualizador podem aceder à área de trabalho, mesmo que não tenham uma licença do Power BI Pro. No entanto, se atribuir a estes utilizadores uma função superior, como Administrador, Membro ou Contribuidor, ser-lhes-á pedido para iniciar uma Versão de Avaliação Pro quando tentarem aceder à área de trabalho. Para que os utilizadores sem licenças Pro possam utilizar a função de Visualizador, confirme que estes também não possuem outras funções na área de trabalho, quer individualmente quer através de um grupo de utilizadores.

> [!NOTE]
> As regras de licenciamento existentes são impostas com maior rigor à publicação de relatórios na nova experiência de área de trabalho. Se tentar publicar a partir do Power BI Desktop ou de outras ferramentas cliente sem uma licença Pro, será apresentado o erro “Apenas utilizadores com licenças do Power BI Pro podem publicar nesta área de trabalho”.

## <a name="administering-new-workspace-experience-workspaces"></a>Administrar áreas de trabalho da nova experiência

A administração de áreas de trabalho da nova experiência de área de trabalho está agora no portal de administração do Power BI. Os administradores do Power BI decidem quem na organização pode criar áreas de trabalho e distribuir aplicações. Os administradores podem ver o estado de todas as áreas de trabalho na sua organização. Também podem gerir e recuperar áreas de trabalho. Leia mais sobre como [Criar as novas áreas de trabalho](service-admin-portal.md#create-the-new-workspaces) no artigo sobre o Portal de administração.

## <a name="guest-users"></a>Utilizadores convidados

Por predefinição, os [Utilizadores convidados do Azure AD B2B](service-admin-azure-ad-b2b.md) não podem aceder às áreas de trabalho. Os administradores do Power BI podem [permitir que os utilizadores externos convidados editem e façam a gestão de conteúdos na organização](service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content). Os Utilizadores convidados ativados podem aceder às áreas de trabalho nas quais têm permissão.

## <a name="auditing"></a>Auditoria

O Power BI faz a auditoria das seguintes atividades para as áreas de trabalho da nova experiência.

| Nome amigável | Nome da operação |
|---|---|
| Pasta do Power BI criada | CreateFolder |
| Pasta do Power BI eliminada | DeleteFolder |
| Pasta do Power BI atualizada | UpdateFolder |
| Acesso à pasta do Power BI atualizado| UpdateFolderAccess |

Leia mais sobre a [auditoria do Power BI](service-admin-auditing.md).

## <a name="limitations-and-considerations"></a>Limitações e considerações

Limitações a ter em consideração:

- As áreas de trabalho podem conter um máximo de 1000 conjuntos de dados ou 1000 relatórios por conjunto de dados. 
- Uma pessoa com uma licença do Power BI Pro pode ser membro de um máximo de 1000 áreas de trabalho.
- O Power BI Publisher para Excel não é suportado.

## <a name="frequently-asked-questions"></a>Perguntas frequentes

**As ligações para conteúdo existente são afetadas pela nova experiência de área de trabalho?**

Não. As ligações para itens existentes nas áreas de trabalho clássicas não são afetadas pela nova experiência de área de trabalho. A disponibilidade geral (GA) da nova experiência de área de trabalho altera a área de trabalho predefinida que cria, mas não altera as áreas de trabalho existentes. 

**As áreas de trabalho existentes são atualizadas para a nova experiência de área de trabalho com a disponibilidade geral?**

Não. A disponibilidade geral da nova experiência de área de trabalho apenas altera o tipo de área de trabalho predefinido para a nova experiência de área de trabalho. As áreas de trabalho clássicas existentes que se baseiam em Grupos do Office 365 permanecem inalteradas.

**Continuam a ser criadas automaticamente áreas de trabalho para os Grupos do Office 365?**

Yes. Uma vez que suportamos ambos os tipos de áreas de trabalho lado a lado, continuamos a apresentar todos os Grupos do Office 365 aos quais tem acesso na lista de áreas de trabalho.

## <a name="next-steps"></a>Próximos passos

* [Create the new workspaces in Power BI](service-create-the-new-workspaces.md) (Criar as novas áreas de trabalho no Power BI)
* [Create the classic workspaces](service-create-workspaces.md) (Criar as áreas de trabalho clássicas)
* [Instalar e utilizar aplicações no Power BI](service-create-distribute-apps.md)
* Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
