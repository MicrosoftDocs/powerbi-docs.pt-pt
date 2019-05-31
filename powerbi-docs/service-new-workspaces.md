---
title: Organizar o trabalho em áreas de trabalho nova - Power BI
description: Saiba mais sobre as novas áreas de trabalho, o que são coleções de dashboards e relatórios criados para proporcionar métricas importantes para a sua organização.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 9f5dfaa5a23ae46fef131a52355531b5fbde3051
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100697"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Organizar o trabalho em novas áreas de trabalho no Power BI

 *Áreas de trabalho* são locais para colaborar com colegas para criar coleções de dashboards, relatórios e os relatórios paginados. A nova experiência de área de trabalho ajuda a gerenciar melhor o acesso ao conteúdo. Este artigo descreve as novas áreas de trabalho e como diferem das áreas de trabalho clássicas.  Como com áreas de trabalho clássicas, ainda usá-los para criar e distribuir aplicações. Saiba mais sobre como [criar uma nova experiência de área de trabalho](service-create-the-new-workspaces.md).

A nova experiência de área de trabalho atingiu a disponibilidade geral (GA) e está agora a área de trabalho predefinida. Pode continuar a criar e utilizar [áreas de trabalho clássicas](service-create-workspaces.md) com base nos grupos do Office 365. 

> [!NOTE]
> Para impor a segurança ao nível da linha (RLS) para utilizadores do Power BI Pro conteúdo numa área de trabalho de navegação, continuar a utilizar [áreas de trabalho clássicas](service-create-workspaces.md). Selecione o **os membros podem visualizar apenas conteúdo do Power BI** opção. Em alternativa, publicar uma aplicação do Power BI para esses utilizadores ou utilizar a partilha de mensagens em fila para distribuir conteúdo. A função de Visualizador de lançamento permitirá que este cenário no futuro em novas áreas de trabalho de experiência de área de trabalho.

Com as novas áreas de trabalho, pode:

- Atribuir funções de área de trabalho a grupos de utilizadores: grupos de segurança, listas de distribuição, grupos do Office 365 e utilizadores individuais.
- Criar uma área de trabalho no Power BI sem criar um grupo do Office 365.
- Utilizar funções de áreas de trabalho mais avançadas para uma gestão de permissões mais flexível numa área de trabalho.

Ao criar uma das novas áreas de trabalho, não está a criar um grupo do Office 365 subjacente associado. Todas as tarefas de administração da área de trabalho são efetuadas no Power BI, não no Office 365. Na nova experiência de área de trabalho, agora pode adicionar um grupo do Office 365 na lista de acesso à área de trabalho para continuar a gerir o acesso de utilizador a conteúdos através de grupos do Office 365.

## <a name="administering-new-workspace-experience-workspaces"></a>Administrando a novas áreas de trabalho de experiência de área de trabalho
A administração para novas áreas de trabalho de experiência de área de trabalho é agora no Power BI, os administradores do Power BI decidir o que numa organização podem criar áreas de trabalho. Também podem gerir e recuperar a área de trabalho. Para fazer isso têm de utilizar o portal de administração do Power BI ou os CmdLets do PowerShell. Para áreas de trabalho clássicas com base nos grupos do Office 365, administração continua a ocorrer no portal de administração do Office 365 e Azure Active Directory.

Na **definições de área de trabalho** no portal de administração, os administradores podem utilizar as criar áreas de trabalho (nova experiência de área de trabalho) na definição de permitir que todas as pessoas ou ninguém numa organização para criar nova área de trabalho a experiência de áreas de trabalho. Também podem limitar a criação a membros de grupos de segurança específicos.

> [!NOTE]
> As criar áreas de trabalho (nova experiência de área de trabalho) Definir predefinições para permitir apenas os utilizadores que podem criar grupos do Office 365 para criar novas áreas de trabalho no Power BI. Certifique-se de que definir um valor no portal de administração do Power BI para garantir que os utilizadores apropriados podem criar nova área de trabalho, experiência de áreas de trabalho.

![Definições de área de trabalho no portal de administração](media/service-new-workspaces/power-bi-workspace-admin-settings.png)

O [lista de áreas de trabalho está disponível](service-admin-portal.md#workspaces) no portal de administração do Power BI. 

![Lista de áreas de trabalho](media/service-admin-portal/workspaces-list.png)

## <a name="new-workspaces-side-by-side-with-classic-workspaces"></a>Novas áreas de trabalho lado a lado com áreas de trabalho clássicas

Áreas de trabalho novas e atualizadas e áreas de trabalho clássicas existentes podem coexistir lado a lado e pode criar qualquer um. A nova experiência de área de trabalho é o tipo de área de trabalho padrão. Power BI continua a listar todos os grupos do Office 365 do utilizador é membro no Power BI para evitar a alteração de fluxos de trabalho existentes. Para saber como criar uma nova área de trabalho, leia [criar novas áreas de trabalho](service-create-the-new-workspaces.md). Para saber como criar uma área de trabalho clássica, leia [criar áreas de trabalho clássicas](service-create-workspaces.md).

## <a name="roles-in-the-new-workspaces"></a>Funções nas novas áreas de trabalho

Para conceder acesso a uma nova área de trabalho, adicionar grupos de utilizadores ou indivíduos para uma das funções de área de trabalho: membros, os contribuintes ou administradores. Todas as pessoas num grupo de utilizadores obtêm a função que definiu. Se for um indivíduo em vários grupos de utilizadores, eles recebem o maior nível de permissão fornecido pelas funções que são atribuídas.

As funções permitem-lhe gerir as ações de cada utilizador numa área de trabalho, para que as equipas possam colaborar. As novas áreas de trabalho permitem-lhe atribuir funções a utilizadores individuais e a grupos de utilizadores: grupos de segurança, grupos do Office 365 e listas de distribuição. 

Quando atribui funções a um grupo de utilizadores, os utilizadores nesse grupo têm acesso aos conteúdos. Se aninhar grupos de utilizadores, todos os utilizadores incluídos nos mesmos têm permissão. Um utilizador que esteja em vários grupos de utilizadores com diferentes funções obtém o nível mais elevado de permissão concedida. 

As novas áreas de trabalho dispõem de três funções: administradores, membros e contribuidores.

|Capacidade   | Admin  | Membro  | Contribuidor  | 
|---|---|---|---|
| Atualizar e eliminar a área de trabalho.  | X  |   |   |
| Adicionar/remover pessoas, incluindo outros administradores.  | X  |   |   |
| Adicionar membros ou outras pessoas com permissões mais baixas.  |  X | X  |   |
| Publicar e atualizar uma aplicação. |  X | X  |   |
| Partilhar um item ou uma aplicação. |  X | X  |   |
| Permitir que outras pessoas voltem a partilhar itens. |  X | X  |   |
| Criar, editar e eliminar conteúdos na área de trabalho.  |  X | X  | X  |
| Publicar relatórios na área de trabalho, eliminar conteúdos. |  X | X  | X  |
 
 
## <a name="licensing"></a>Licensing
Todas as pessoas que adicionar à área de trabalho precisam de ter uma licença do Power BI Pro. Na área de trabalho, estes utilizadores podem colaborar nos dashboards e relatórios que planear publicar para um vasto público ou mesmo para toda a organização. Se quiser distribuir conteúdos para outras pessoas na sua organização, pode atribuir licenças do Power BI Pro a esses utilizadores ou colocar a área de trabalho numa capacidade do Power BI Premium.

> [!NOTE]
> A publicação de relatórios para a nova experiência de área de trabalho tiver existentes de imposição mais estritas regras de licenciamento. Os utilizadores que tentarem para publicar do Power BI Desktop ou de outros clientes ferramentas sem uma licença Pro ver o erro "apenas os utilizadores com licenças do Power BI Pro podem publicar esta área de trabalho."

## <a name="how-are-the-new-workspaces-different-from-current-workspaces"></a>Como é que as novas áreas de trabalho diferem das áreas de trabalho atuais?

Com as novas áreas de trabalho, estamos a reestruturar algumas funcionalidades. Seguem-se as alterações que pode esperar a ser permanente. 

* Criar estas áreas de trabalho não irá criar grupos do Office 365, como nas áreas de trabalho clássico. No entanto, agora, pode utilizar um grupo do Office 365 para dar aos utilizadores acesso à área de trabalho ao atribuir-lhe uma função. 
* Em áreas de trabalho clássicas, só pode adicionar indivíduos aos membros e listas de administrador. Nas novas áreas de trabalho, pode adicionar múltiplos grupos de segurança do AD, listas de distribuição ou grupos do Office 365 a estas listas para uma gestão de utilizadores mais fácil. 
- Pode criar um pacote de conteúdos organizacional a partir de uma área de trabalho clássica. Não pode criar um pacote a partir das novas áreas de trabalho.
- Pode consumir um pacote de conteúdos organizacional de uma área de trabalho clássico. Não pode utilizar um pacote a partir das novas áreas de trabalho.

## <a name="workspace-contact-list"></a>Lista de contatos da área de trabalho
A nova **lista de contacto** funcionalidade permite-lhe especificar os utilizadores que recebem a notificação sobre problemas que ocorrem na área de trabalho. Por predefinição, nenhum usuário ou grupo especificado como uma área de trabalho administração é notificada, mas pode personalizar a lista. Os utilizadores ou grupos listados na lista de contactos serão apresentados na interface do usuário (IU) para ajudar a utilizadores obter ajuda relacionados com a área de trabalho. 

Leia mais sobre o [definir a lista de contatos da área de trabalho](service-create-the-new-workspaces.md#workspace-contact-list).

## <a name="workspace-onedrive"></a>Workspace OneDrive
O recurso do OneDrive da área de trabalho permite-lhe configurar um grupo do Office 365 cujo armazenamento de ficheiros de biblioteca de documentos do SharePoint está disponível para utilizadores de área de trabalho. O grupo tem de ser criado fora do Power BI. 

Power BI não sincronizar as permissões de utilizadores ou grupos que estão configurados para terem acesso a área de trabalho com a associação de grupo do Office 365. A melhor prática é gerir o acesso de área de trabalho através do mesmo grupo do Office 365 cujo armazenamento de ficheiros que configurar nesta definição. 

Saiba mais sobre como [definir e aceder ao OneDrive a área de trabalho](service-create-the-new-workspaces.md#workspace-onedrive).  
   
## <a name="auditing"></a>A auditoria
As seguintes atividades são auditadas pelo Power BI para novas áreas de trabalho de experiência de área de trabalho.

| Nome amigável |   Nome da operação |
|---|---|
| Pasta do Power BI criada | CreateFolder |
| Pasta do Power BI eliminada | DeleteFolder |
| Pasta do Power BI atualizada | UpdateFolder |
| Acesso à pasta do Power BI atualizado| UpdateFolderAccess |

Leia mais sobre [auditoria do Power BI](service-admin-auditing.md#activities-audited-by-power-bi).

## <a name="limitations-and-considerations"></a>Limitações e considerações

Limitações a ter em consideração:

- As áreas de trabalho podem conter um máximo de 1000 conjuntos de dados ou 1000 relatórios por conjunto de dados. 
- Uma pessoa com uma licença do Power BI Pro pode ser um membro de um máximo 1000 as áreas de trabalho.
- Power BI publisher para Excel não é suportado.

## <a name="workspace-features-that-work-differently"></a>Funcionalidades da área de trabalho que funcionam de forma diferente

Algumas funcionalidades funcionam de forma diferente das áreas de trabalho atuais nas novas áreas de trabalho. Essas diferenças são intencionais, com base nos comentários que recebemos dos clientes e permitir uma abordagem mais flexível para a colaboração com áreas de trabalho:

- Imposição de licenciamento: A publicação de relatórios para a nova experiência de área de trabalho impõe regras de licenciamento existentes que necessitem de uma licença do Power BI Pro para utilizadores colaborar em áreas de trabalho ou da partilha de conteúdo para outras pessoas no serviço Power BI. Os utilizadores sem uma licença Pro veem o erro "apenas os utilizadores com licenças Powre BI Pro podem publicar esta área de trabalho."
- Os membros podem ou não podem voltar a partilhar: esta opção foi substituída pela função Contribuidor
- Áreas de trabalho só de leitura: em vez de conceder aos utilizadores acesso só de leitura a uma área de trabalho, terá de atribuir os utilizadores a uma futura função de Visualizador, que permite um semelhante acesso só de leitura ao conteúdo numa área de trabalho.
- O botão **Sair da área de trabalho** não existe.

## <a name="frequently-asked-questions"></a>Perguntas frequentes

**São ligações para conteúdo existente afetados pela área de trabalho nova experiência de disponibilidade geral**

Não. Links para os itens existentes em áreas de trabalho clássicas não são afetados pela nova experiência de área de trabalho. A disponibilidade geral (GA) da nova experiência de área de trabalho muda a área de trabalho do padrão para criar, mas não altera a áreas de trabalho existentes. 

**Áreas de trabalho atualizadas para a nova experiência de área de trabalho com o GA existentes**

Não. A nova experiência de GA da área de trabalho apenas altera o tipo de área de trabalho predefinido para a nova experiência de área de trabalho. Clássicas áreas de trabalho existentes que se baseiam em grupos do Office 365 permanecem inalteradas.

**Áreas de trabalho são criadas automaticamente ainda para grupos do Office 365**

Yes. Uma vez que suportamos a ambos os tipos de áreas de trabalho lado a lado, podemos continuar listar todos os grupos do Office 365 do utilizador tem acesso na lista de áreas de trabalho.

## <a name="next-steps"></a>Próximos passos
* [Criar novas áreas de trabalho no Power BI](service-create-the-new-workspaces.md)
* [Criar as áreas de trabalho clássicas](service-create-workspaces.md)
* [Instalar e utilizar aplicações no Power BI](service-create-distribute-apps.md)
* Perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
