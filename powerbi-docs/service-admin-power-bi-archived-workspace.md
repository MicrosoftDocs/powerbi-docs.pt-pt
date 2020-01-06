---
title: Área de Trabalho Arquivada do Power BI
description: Área de Trabalho Arquivada do Power BI depois de gerir locatários do Office 365
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/18/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 403bf213cc2da7ad803780946e606433166e3484
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/06/2020
ms.locfileid: "74699964"
---
# <a name="power-bi-archived-workspace"></a>Área de Trabalho Arquivada do Power BI

> [!IMPORTANT]
> O Power BI já não suporta a funcionalidade de Área de Trabalho Arquivada, que será removida no final de 2019. Se estiver a utilizar uma Área de Trabalho Arquivada, deverá recriar imediatamente qualquer conteúdo que deseja manter, numa nova área de trabalho no seu inquilino atual. Não pode contar com o acesso contínuo à Área de Trabalho Arquivada. O Power BI já não suporta a capacidade relacionada, [obtenção de controlo externa de um inquilino do Azure AD](service-admin-faq.md#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users).

Com o Power BI, qualquer pessoa pode inscrever-se e começar a utilizar o serviço em alguns minutos.  Posteriormente, o departamento de TI da sua organização pode optar por assumir a gestão do Power BI para os utilizadores na sua organização.  Se este controlo ocorrer, beneficiará da gestão central dos utilizadores e das permissões na sua organização. Também pode conseguir tirar partido do início de sessão simplificado com o mesmo nome de utilizador e palavra-passe utilizados para outros serviços na sua organização.

Qualquer conteúdo que tenha sido criado antes do início da gestão do Power BI pelo seu departamento de TI será colocado numa Área de Trabalho Arquivada do Power BI, que pode ser acedida no painel de navegação do [Power BI](https://app.powerbi.com). Deve começar ao criar o novo conteúdo do Power BI em O Meu Espaço de Trabalho, que é protegido e gerido pelo departamento de TI da sua organização.  O espaço de trabalho arquivado continuará a existir, mas há restrições sobre as ações que podem ser executadas no conteúdo do Espaço de Trabalho Arquivado.  Para remover essas restrições, terá de migrar o conteúdo da Área de Trabalho Arquivada para A Minha Área de Trabalho, gerida pelo departamento de TI.

## <a name="restrictions-in-your-archived-workspace"></a>Restrições em seu Espaço de Trabalho Arquivado

O Power BI não elimina o conteúdo da Área de Trabalho Arquivada. Pode continuar a obter dados, criar relatórios e dashboards e atualizar conjuntos de dados. Os utilizadores existentes com os quais partilhou conteúdo ainda o podem ver nas Áreas de Trabalho Arquivadas deles. No entanto, há algumas restrições sobre o conteúdo em seu Espaço de Trabalho Arquivado:

* **OneDrive para Empresas**: para conjuntos de dados na Área de Trabalho Arquivada, deixará de poder obter ou atualizar dados através do OneDrive para Empresas.  Se tentar ligar-se a essa fonte, receberá um aviso.

* **Partilhar dashboards**: não pode partilhar dashboards com outros utilizadores da Área de Trabalho Arquivada.  Todos os utilizadores que já têm acesso continuam a poder ver os dashboards partilhados ao acederem às Áreas de Trabalho Arquivadas deles.

* **Criar grupos**: não pode criar grupos na Área de Trabalho Arquivada.

* **Acesso a aplicações móveis do Power BI**: embora ainda possa ver os conteúdos na Web na Área de Trabalho Arquivada, esses conteúdos já não aparecem nas aplicações móveis do Power BI.

## <a name="migrating-content-in-your-archived-workspace"></a>Migração de conteúdo na Área de Trabalho Arquivada

Para continuar a utilizar o Power BI, deve criar novo conteúdo em A Minha Área de Trabalho. Também deve planear migrar qualquer conteúdo na Área de Trabalho Arquivada para A Minha Área de Trabalho.  Como migrar o conteúdo depende do tipo de conteúdo:

* **Conjuntos de dados do Excel ou do Power BI Desktop**: migre estes conjuntos de dados ao alternar da Área de Trabalho Arquivada para A Minha Área de Trabalho e carregue novamente o ficheiro do Excel ou do Power BI Desktop ao selecionar o botão **Os Meus Dados**.  Se configurar a atualização agendada, terá de reconfigurar estas definições para o novo conjunto de dados em A Minha Área de Trabalho.

* **Outros Conjuntos de Dados**: alterne para A Minha Área de Trabalho e selecione o botão **Obter Dados** para restabelecer ligação a todos os outros conjuntos de dados criados na Área de Trabalho Arquivada.  Talvez seja necessário inserir novamente as informações de conexão ou segurança.

* **Relatórios**: os relatórios presentes nos ficheiros do Excel ou do Power BI Desktop são recriados automaticamente assim que voltar a carregar o ficheiro do Excel ou do Power BI Desktop correspondente. Os relatórios instalados como parte de um pacote de conteúdos também são recriados quando restabelecer ligação com o pacote de conteúdos. Se criar os seus próprios relatórios através do serviço Power BI, recrie estes relatórios em A Minha Área de Trabalho.

* **Dashboards**: os dashboards instalados como parte dos pacotes de conteúdos são recriados automaticamente quando restabelecer ligação com o pacote de conteúdos em A Minha Área de Trabalho. Se criar os seus próprios dashboards através do serviço Power BI, recrie estes dashboards em A Minha Área de Trabalho.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

