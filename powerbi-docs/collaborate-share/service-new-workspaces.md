---
title: Organizar o trabalho nas novas áreas de trabalho no Power BI
description: Saiba mais sobre as novas áreas de trabalho, que são coleções de dashboards e relatórios criadas para disponibilizar métricas importantes à sua organização.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: conceptual
ms.date: 10/21/2020
ms.custom: contperf-fy20q4
LocalizationGroup: Share your work
ms.openlocfilehash: 5aabc825ecd22ed49d05428148133be17156645d
ms.sourcegitcommit: 7bf09116163afaae312eb2b232eb7967baee2c92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/17/2020
ms.locfileid: "97621493"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Organizar o trabalho nas novas áreas de trabalho no Power BI

As *áreas de trabalho* são locais onde pode colaborar com colegas para criar coleções de dashboards, relatórios, conjuntos de dados e relatórios paginados. A nova experiência de área de trabalho ajuda a gerir melhor o acesso ao conteúdo. Este artigo descreve as novas áreas de trabalho e como diferem das áreas de trabalho clássicas.  Tal como acontece com as áreas de trabalho clássicas, ainda as utilizar para criar e distribuir aplicações. 

Pronto para criar uma nova área de trabalho? Leia [Criar uma nova experiência de área de trabalho](service-create-the-new-workspaces.md).

:::image type="content" source="media/service-new-workspaces/power-bi-workspace-opportunity.png" alt-text="Nova experiência de área de trabalho do Power BI":::

As áreas de trabalho novas e atualizadas podem coexistir lado a lado com as áreas de trabalho clássicas existentes. A nova experiência de área de trabalho é o tipo de área de trabalho predefinido. Se for necessário, ainda pode criar e utilizar [áreas de trabalho clássicas](service-create-workspaces.md) baseadas em grupos do Microsoft 365. Pronto para migrar a área de trabalho clássica? Veja [Atualizar as áreas de trabalho clássicas para as novas áreas de trabalho no Power BI](service-upgrade-workspaces.md) para obter detalhes.

## <a name="new-and-classic-workspace-differences"></a>Diferenças entre as áreas de trabalho novas e clássicas

Reestruturámos algumas funcionalidades nas novas áreas de trabalho. Veja a seguir as principais diferenças.

- **A criação das novas áreas de trabalho não irá criar grupos do Microsoft 365**, ao contrário do que acontece nas áreas de trabalho clássicas. Todas as tarefas de administração das novas áreas de trabalho são efetuadas no Power BI, não no Office 365. Pode continuar a gerir o acesso dos utilizadores ao conteúdo através dos grupos do Microsoft 365, se assim quiser. Basta adicionar um grupo do Microsoft 365 na lista de acesso da área de trabalho.
- **Utilize funções de áreas de trabalho mais avançadas** para uma gestão de permissões mais flexível nas novas áreas de trabalho.  Nas áreas de trabalho clássicas, só pode adicionar utilizadores individuais à lista de membros e administradores. 
- **Atribua grupos de utilizadores a funções de área de trabalho**: nas novas áreas de trabalho, pode adicionar vários grupos de segurança do Active Directory, listas de distribuição ou grupos dos Microsoft 365 a estas funções para uma gestão de utilizadores mais fácil. 
- **Lista de contactos**: nas novas áreas de trabalho, pode especificar quem recebe notificações acerca da atividade da área de trabalho.
- **Crie aplicações de modelo**: apenas pode criar *aplicações de modelo* nas novas áreas de trabalho. As aplicações de modelo são aplicações que pode distribuir para clientes fora da sua organização. Esses clientes podem então ligar aos seus próprios dados com a sua aplicação de modelo. Leia mais sobre as [aplicações de modelo](../connect-data/service-template-apps-overview.md).
- **Partilhe conjuntos de dados**: para partilhar um conjunto de dados fora de uma área de trabalho específica, tem de guardar o relatório que contém o conjunto de dados numa das novas áreas de trabalho. Não pode partilhar conjuntos de dados de áreas de trabalho clássicas. Leia mais sobre os [conjuntos de dados partilhados](../connect-data/service-datasets-across-workspaces.md).
- **Pacotes de conteúdos organizacionais**: nas áreas de trabalho clássicas, cria e consome pacotes de conteúdos organizacionais. Não os pode criar ou consumir nas novas áreas de trabalho. Nas novas áreas de trabalho, as aplicações e as aplicações de modelo substituem os pacotes de conteúdos organizacionais.

Este artigo explica estas funcionalidades mais detalhadamente.

> [!NOTE]
> O Power BI continua a listar todos os grupos do Microsoft 365 dos quais é membro. Tal evita a alteração dos fluxos de trabalho existentes.

### <a name="features-that-work-differently"></a>Funcionalidades que funcionam de forma diferente

Nas novas áreas de trabalho, algumas funcionalidades funcionam de forma diferente. Estas diferenças são intencionais, com base no feedback que recebemos dos clientes. Permitem uma abordagem mais flexível à colaboração em áreas de trabalho.

- **Imposição de licenciamento**: a publicação de relatórios numa nova experiência de área de trabalho impõe as regras de licenciamento existentes. Os utilizadores que colaboram em novas áreas de trabalho ou partilham conteúdos com outros utilizadores no serviço Power BI precisam de uma licença do Power BI Pro. Os utilizadores sem uma licença do Pro veem o erro "Apenas os utilizadores com licenças do Power BI Pro podem publicar nesta área de trabalho".
- **Definição "Os membros podem voltar a partilhar"** : a função de Contribuidor nas novas áreas de trabalho substitui a definição "Os membros podem voltar a partilhar" nas áreas de trabalho clássicas.
- **Áreas de trabalho só de leitura**: a função de Visualizador nas novas áreas de trabalho substitui a concessão de acesso só de leitura aos utilizadores numa área de trabalho clássica. A função de Visualizador permite um acesso só de leitura semelhante ao conteúdo nas novas áreas de trabalho.
- Os **utilizadores sem uma licença Pro** poderão aceder a uma nova área de trabalho se esta estiver numa capacidade do Power BI Premium, mas apenas se tiverem a função de Visualizador.
- **Permitir que os utilizadores exportem dados**: até mesmo os utilizadores com a função de Visualizador na nova área de trabalho poderão exportar dados se tiverem a Permissão de compilação nos conjuntos de dados na mesma. Saiba mais sobre as [Permissões de compilação para conjuntos de dados](../connect-data/service-datasets-build-permissions.md).
- O botão **Sair da área de trabalho** não existe nas novas áreas de trabalho.

### <a name="workspace-contact-list"></a>Lista de contactos da área de trabalho

A nova funcionalidade **Lista de contactos** permite-lhe especificar os utilizadores que recebem notificações sobre problemas que afetam as novas áreas de trabalho. Por predefinição, qualquer utilizador ou grupo especificado como administrador na nova área de trabalho é notificado. Pode adicionar outras pessoas a essa lista. Os utilizadores ou grupos incluídos na lista de contactos também são apresentados na interface de utilizador (IU) das novas áreas de trabalho para que os utilizadores finais das mesmas saibam quem devem contactar. 

Leia mais sobre [como criar a lista de contactos da área de trabalho](service-create-the-new-workspaces.md#create-a-contact-list).

### <a name="workspace-onedrive"></a>OneDrive da área de trabalho

Como já dissemos, o Power BI não cria um grupo do Microsoft 365 nos bastidores quando cria uma das novas áreas de trabalho. Mesmo assim, poderá considerar útil ter um OneDrive associado à nova área de trabalho. A funcionalidade OneDrive da Área de Trabalho nas novas áreas de trabalho permite-lhe configurar um grupo do Microsoft 365 cujo armazenamento de ficheiros da Biblioteca de Documentos do SharePoint está disponível para os utilizadores da área de trabalho. Crie o grupo fora do Power BI.
 
O Power BI não sincroniza as permissões de utilizadores ou grupos com acesso à nova área de trabalho com a associação ao grupo do Microsoft 365. Pode sincronizá-las ao gerir o acesso à área de trabalho através do mesmo grupo do Microsoft 365 cujo armazenamento de ficheiros configurar nesta definição. 

Leia mais sobre [como definir o OneDrive da área de trabalho](service-create-the-new-workspaces.md#set-a-workspace-onedrive).  

## <a name="roles-in-the-new-workspaces"></a>Funções nas novas áreas de trabalho

As funções permitem-lhe gerir as ações de cada utilizador nas novas área de trabalho, para que as equipas possam colaborar. As novas áreas de trabalho permitem-lhe atribuir funções a utilizadores individuais e a grupos de utilizadores: grupos de segurança, grupos do Microsoft 365 e listas de distribuição. 

Para conceder acesso a uma nova área de trabalho, atribua grupos de utilizadores ou indivíduos a uma das funções da área de trabalho: Administrador, Membro, Contribuidor ou Visualizador. Todas as pessoas num grupo de utilizadores obtêm a função que atribuiu. Se um utilizador estiver em vários grupos de utilizadores, receberá o nível de permissão mais elevado concedido pelas funções que lhe estão atribuídas. Se aninhar grupos de utilizadores, todos os utilizadores incluídos nos mesmos têm permissão. Todas estas funcionalidades, exceto visualizar e interagir, exigem uma licença do Power BI Pro. Leia mais sobre o [licenciamento](#licenses) neste artigo.

[!INCLUDE [power-bi-workspace-roles-table](../includes/power-bi-workspace-roles-table.md)]

> [!NOTE]
> - Pode atribuir utilizadores a funções, individualmente ou num grupo, mesmo que não possam utilizar a função. Por outras palavras, pode atribuir utilizadores que não têm licenças do Power BI Pro a uma função que exige uma licença. Veja a secção [Licenças](#licenses) neste artigo para obter mais detalhes.
> - Para impor [segurança ao nível da linha (RLS)](../admin/service-admin-rls.md) aos utilizadores que procuram conteúdos numa área de trabalho, utilize a função de Visualizador. Também pode impor a RLS sem dar acesso à nova área de trabalho. [Publique uma aplicação](service-create-distribute-apps.md) e distribua-a para esses utilizadores ou utilize a [partilha para distribuir conteúdos](service-share-dashboards.md) para os mesmos.

## <a name="licensing-and-administering"></a>Licenciamento e administração

### <a name="licenses"></a>Licenças
Se uma das novas áreas de trabalho estiver numa capacidade partilhada, todas as pessoas que adicionar à mesma precisam de uma licença do Power BI Pro. Estes utilizadores podem colaborar nos dashboards e relatórios na nova área de trabalho. Se quiser distribuir conteúdos para outras pessoas na sua organização, pode atribuir licenças do Power BI Pro a esses utilizadores ou colocar a área de trabalho numa capacidade do Power BI Premium.

Quando a nova área de trabalho está numa capacidade do Power BI Premium, os utilizadores com a função de Visualizador podem aceder à área de trabalho, mesmo que não tenham uma licença do Power BI Pro. No entanto, se atribuir a estes utilizadores uma função superior, como Administrador, Membro ou Contribuidor, ser-lhes-á pedido para iniciar uma avaliação Pro quando tentarem aceder à área de trabalho. Se quiser que os utilizadores sem licenças Pro utilizem a função de Visualizador, confirme que estes também não possuem outras funções na área de trabalho, quer individualmente quer através de um grupo de utilizadores.

As regras de licenciamento existentes são impostas com maior rigor à publicação de relatórios na nova experiência de área de trabalho. Se tentar publicar a partir do Power BI Desktop ou de outras ferramentas cliente sem uma licença Pro, será apresentado o erro “Apenas utilizadores com licenças do Power BI Pro podem publicar nesta área de trabalho”.

> [!NOTE]
> O Power BI para o Governo Norte-Americano não está disponível com as licenças Gratuitas. Para obter detalhes de licenciamento, veja [Power BI para clientes do Governo Norte-Americano](../admin/service-govus-overview.md).

### <a name="guest-users"></a>Utilizadores convidados

Por predefinição, os [Utilizadores convidados do Azure AD B2B](../admin/service-admin-azure-ad-b2b.md) não podem aceder às áreas de trabalho. Os administradores do Power BI podem [permitir que os utilizadores externos convidados editem e façam a gestão de conteúdos na organização](../admin/service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content). Os Utilizadores convidados ativados podem aceder às áreas de trabalho nas quais têm permissão.

### <a name="administering-new-workspace-experience-workspaces"></a>Administrar áreas de trabalho da nova experiência

A administração de áreas de trabalho da nova experiência é efetuada no portal de administração do Power BI. Os administradores do Power BI decidem quem na organização pode criar áreas de trabalho e distribuir aplicações. Leia sobre como [gerir a capacidade de os utilizadores criarem áreas de trabalho](../admin/service-admin-portal.md#create-the-new-workspaces) no artigo "Portal de administração". 

Os administradores também podem ver o estado de todas as áreas de trabalho na sua organização. Podem gerir, recuperar e até mesmo eliminar áreas de trabalho. Leia sobre como [gerir as áreas de trabalho](../admin/service-admin-portal.md#workspaces) no artigo "Portal de administração".

### <a name="auditing"></a>Auditoria

O Power BI faz a auditoria das seguintes atividades para as áreas de trabalho da nova experiência.

| Nome amigável | Nome da operação |
|---|---|
| Pasta do Power BI criada | CreateFolder |
| Pasta do Power BI eliminada | DeleteFolder |
| Pasta do Power BI atualizada | UpdateFolder |
| Acesso à pasta do Power BI atualizado| UpdateFolderAccess |

Leia mais sobre a [auditoria do Power BI](../admin/service-admin-auditing.md).

## <a name="limitations-and-considerations"></a>Limitações e considerações

Limitações a ter em consideração:

- As áreas de trabalho podem conter um máximo de 1000 conjuntos de dados ou 1000 relatórios por conjunto de dados. 
- Uma pessoa com uma licença do Power BI Pro pode ser membro de um máximo de 1000 áreas de trabalho.
- O Power BI Publisher para Excel não é suportado.

## <a name="frequently-asked-questions"></a>Perguntas frequentes

**As ligações para conteúdo existente são afetadas pela nova experiência de área de trabalho?**

Não. As ligações para itens existentes nas áreas de trabalho clássicas não são afetadas pela nova experiência de área de trabalho. A disponibilidade geral (GA) da nova experiência de área de trabalho altera a área de trabalho predefinida que cria, mas não altera as áreas de trabalho existentes. 

**As áreas de trabalho existentes são atualizadas para a nova experiência de área de trabalho com a disponibilidade geral?**

Não. A disponibilidade geral da nova experiência de área de trabalho apenas altera o tipo de área de trabalho predefinido para a nova experiência de área de trabalho. As áreas de trabalho clássicas existentes que se baseiam em grupos do Microsoft 365 permanecem inalteradas.

**Continuam a ser criadas automaticamente áreas de trabalho para os grupos do Microsoft 365?**

Yes. Uma vez que suportamos ambos os tipos de áreas de trabalho lado a lado, continuamos a apresentar todos os grupos do Microsoft 365 aos quais tem acesso na lista de áreas de trabalho.

## <a name="next-steps"></a>Próximos passos

* [Create the new workspaces in Power BI](service-create-the-new-workspaces.md) (Criar as novas áreas de trabalho no Power BI)
* [Create the classic workspaces](service-create-workspaces.md) (Criar as áreas de trabalho clássicas)
* [Instalar e utilizar aplicações no Power BI](service-create-distribute-apps.md)
* Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

