---
title: Área de Trabalho Arquivada do Power BI
description: Área de Trabalho Arquivada do Power BI depois de gerir locatários do Office 365
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 06/28/2017
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 8b9fcf1c6121c4aeecfdf948b77493f1f2a7f825
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="power-bi-archived-workspace"></a>Área de Trabalho Arquivada do Power BI
Com o Power BI, qualquer pessoa pode inscrever-se e começar a utilizar o serviço em alguns minutos.  Posteriormente, o departamento de TI da sua organização pode optar por assumir a gestão do Power BI para utilizadores na sua organização.  Se esse controlo ocorrer, beneficia da gestão central de utilizadores e permissões na sua organização e pode tirar proveito do início de sessão simplificado ao utilizar o mesmo nome de utilizador e palavra-passe utilizados para outros serviços na sua organização. 

Qualquer conteúdo que tenha sido criado antes do início da gestão do Power BI pelo seu departamento de TI será colocado num Espaço de Trabalho Arquivado do Power BI, que pode ser acessado na barra de navegação à esquerda do [Power BI](https://app.powerbi.com).  Deve começar ao criar o novo conteúdo do Power BI em O Meu Espaço de Trabalho, que é protegido e gerido pelo departamento de TI da sua organização.  O espaço de trabalho arquivado continuará a existir, mas há restrições sobre as ações que podem ser executadas no conteúdo do Espaço de Trabalho Arquivado.  Para remover essas restrições, precisará de migrar o conteúdo do seu Espaço de Trabalho Arquivado para o Meu Espaço de Trabalho, gerido pelo departamento de TI.

## <a name="restrictions-in-your-archived-workspace"></a>Restrições em seu Espaço de Trabalho Arquivado
Nenhum conteúdo será excluído do Espaço de Trabalho Arquivado.  Pode continuar a obter dados, criar relatórios e dashboards e atualizar conjuntos de dados.  Os utilizadores existentes com os quais partilhou conteúdo ainda podem mostrar o conteúdo no seu Espaço de Trabalho Arquivado.

No entanto, há algumas restrições sobre o conteúdo em seu Espaço de Trabalho Arquivado:

* **OneDrive for Business.  ** Não será mais possível obter dados para conjuntos de dados ou atualizá-los por meio do OneDrive for Business no Espaço de Trabalho Arquivado.  Se tentar ligar-se a essa fonte, recebe um aviso.
* **A partilhar dashboards.  ** Não é possível partilhar dashboards com outros utilizadores por meio do Espaço de Trabalho Arquivado.  Todos os utilizadores que já têm acesso continuam a poder ver os dashboards partilhados ao acessar a sua Área de Trabalho Arquivado.
* **Criando grupos.  ** Não é possível criar grupos no Espaço de Trabalho Arquivado.
* **Acesso em aplicações móveis do Power BI.  **Embora ainda possa ver os conteúdos na web no seu Espaço de Trabalho Arquivado, este conteúdo já não aparece nas aplicações móveis do Power BI.

## <a name="migrating-content-in-your-archived-workspace"></a>Migração de conteúdo na Área de Trabalho Arquivada
Para continuar a utilizar o Power BI, deve criar o novo conteúdo no Meu Espaço de Trabalho, gerido pelo departamento de TI.   Também deve planear migrar qualquer conteúdo em seu Espaço de Trabalho Arquivado para o Meu Espaço de Trabalho.  Como migrar o conteúdo depende do tipo de conteúdo:

* **Conjuntos de dados do Excel ou do Power BI Desktop.  ** Migre esses conjuntos de dados ao alternar da Área de Trabalho Arquivada para o Meu Espaço de Trabalho e carregue novamente o ficheiro do Excel ou do Power BI Desktop ao clicar no botão “Meus Dados”.  Se configurar a atualização agendada, precisa de reconfigurar as configurações para o novo conjunto de dados no Meu Espaço de Trabalho.
* **Outros conjuntos de dados.  ** Alterne para Meu Espaço de Trabalho e clique no botão Obter Dados para se reconectar a todos os outros conjuntos de dados criados no Espaço de Trabalho Arquivado.  Talvez seja necessário inserir novamente as informações de conexão ou segurança.
* **Relatórios.  ** Os relatórios contidos em ficheiros do Excel ou do Power BI Desktop ou os relatórios instalados como parte de pacotes de conteúdo serão recriados automaticamente depois que carregar novamente o ficheiro do Excel ou do Power BI Desktop correspondente ou se reconectar ao pacote de conteúdo.  Se criar os seus próprios relatórios através do serviço Power BI, precisa de recriar esses relatórios no Meu Espaço de Trabalho.
* **Dashboards.  ** Dashboards instalados como parte dos pacotes de conteúdo serão recriados automaticamente quando se reconectar ao pacote de conteúdo no Meu Espaço de Trabalho.  Se criar os seus próprios dashboards através do serviço Power BI, precisa de recriar esses dashboards no Meu Espaço de Trabalho.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

