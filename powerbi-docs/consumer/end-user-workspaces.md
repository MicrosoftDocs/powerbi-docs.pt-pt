---
title: Como os conteúdos são organizados nas áreas de trabalho
description: Saiba mais sobre áreas de trabalho e funções da área de trabalho
author: mihart
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/22/2020
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: 801b5cf5400bbe1cc0487eef596ea3d1cdc5fb1e
ms.sourcegitcommit: 9ec2c608b90bf651df613f0714addd251a885039
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/24/2020
ms.locfileid: "82120193"
---
# <a name="collaborate-in-workspaces"></a>Colaborar em áreas de trabalho

 As *áreas de trabalho* são locais onde colabora com os colegas sobre conteúdos específicos. As áreas de trabalho são criadas pelos *designers* do Power BI para incluírem coleções de dashboards e relatórios. Depois o designer poderá agrupar esta coleção numa *aplicação* e distribuí-la por toda a organização ou por um conjunto de pessoas ou grupo específico. 

 Todos os que utilizam o serviço Power BI também têm uma **A minha área de trabalho**.  A minha área de trabalho é o seu sandbox pessoal onde pode criar conteúdos para si mesmo.

 Pode ver as suas áreas de trabalho a partir do Power BI **Home** ou ao selecionar **Área de Trabalho** ou **A minha área de trabalho** a partir do painel de navegação esquerdo.

 ![painel de navegação a mostrar dois tipos de áreas de trabalho](media/end-user-workspaces/power-bi-home.png)

## <a name="types-of-workspaces"></a>Tipos de áreas de trabalho
**A Minha Área de Trabalho** armazena todos os conteúdos que criou e de que é proprietário. Considere-a a sua sandbox pessoal ou uma área de trabalho para o seu próprio conteúdo. Para muitos *consumidores* do Power BI, **A minha área de trabalho** permanece vazia porque a sua tarefa não envolve criar novos conteúdos. Por definição, os *consumidores* consomem dados criados por outros utilizadores e utilizam esses dados para tomar decisões empresariais. Se vir que está a criar conteúdos, considere ler os [artigos do Power BI para designers](../create-reports/index.yml).

As **Áreas de trabalho da aplicação** incluem todos os conteúdos da aplicação específica. Quando um *designer* cria uma aplicação, este agrupa todos os conteúdos necessários para tirar proveito dessa aplicação. Os conteúdos podem incluir dashboards, relatórios e conjuntos de dados. Nem todas as aplicações irão conter estes três elementos de conteúdos. A aplicação pode conter apenas um dashboard ou três dashboards de cada tipo de conteúdo, ou mesmo 20 relatórios. Tudo depende de o que o *designer* incluir na aplicação. O mais comum é que as áreas de trabalho da aplicação para *consumidores* não incluam conjuntos de dados.

A área de trabalho da aplicação de vendas de figos abaixo contém três relatórios e um dashboard. 

![painel de navegação a mostrar dois tipos de áreas de trabalho](media/end-user-workspaces/power-bi-app-workspace.png)

## <a name="roles-in-the-workspaces"></a>Funções nas áreas de trabalho

As funções determinam as ações que pode fazer numa área de trabalho, para que as equipas possam colaborar.  Ao conceder acesso a uma nova área de trabalho, os *designers* adicionam indivíduos ou grupos a uma das funções da área de trabalho: **Visualizador**, **Membro**, **Contribuidor** ou **Administrador**. 


Enquanto *consumidor* do Power BI, irá normalmente interagir nas áreas de trabalho com a função **Visualizador**. No entanto, um *designer* também poderia atribuir-lhe a função de **Membro** ou **Contribuidor**. A função Visualizador permite-lhe ver e interagir com os conteúdos (dashboards, relatórios, aplicações) criados por outros e partilhados consigo. Além disso, como a função Visualizador não consegue aceder ao conjunto de dados subjacente, é uma forma segura de interagir com os conteúdos e não ter de se preocupar com a possibilidade de "danificar" os dados subjacentes.


Para obter uma lista detalhada do que pode fazer como *consumidor* com a função Visualizador, veja [funcionalidades do Power BI para consumidores](end-user-features.md).


### <a name="workspace-roles"></a>Funções da área de trabalho
Eis as capacidades das quatro funções: administradores, membros, contribuidores e visualizadores. Todas estas funcionalidades, exceto visualizar e interagir, exigem uma licença do Power BI Pro.

|Funcionalidade   | Administrador  | Membro  | Contribuidor  | Visualizador |
|---|---|---|---|---|
| Atualizar e eliminar a área de trabalho.  | X  |   |   |   | 
| Adicionar/remover pessoas, incluindo outros administradores.  | X  |   |   |   |
| Adicionar membros ou outras pessoas com permissões mais baixas.  |  X | X  |   |   |
| Publicar e atualizar uma aplicação. |  X | X  |   |   |
| Partilhar um item ou uma aplicação.<sup>1</sup> |  X | X  |   |   |
| Permitir que outras pessoas voltem a partilhar itens.<sup>1</sup> |  X | X  |   |   |
| Destacar aplicações nas páginas Base dos colegas |  X | X  |   |   |
| Destacar dashboards e relatórios nas páginas Base dos colegas |  X | X  | X |   |
| Criar, editar e eliminar conteúdos na área de trabalho.  |  X | X  | X  |   |
| Publicar relatórios na área de trabalho, eliminar conteúdos.  |  X | X  | X  |   |
| Criar um relatório noutra área de trabalho com base num conjunto de dados desta área de trabalho.<sup>1</sup> |  X | X  | X  |   |
| Copiar um relatório. | X | X | X |  |
| Ver e interagir com um item.<sup>2</sup> |  X | X  | X  | X  |
| Ler dados armazenados nos fluxos de dados da área de trabalho | X | X | X | X |

1. Os Contribuidores e Membros podem partilhar itens numa área de trabalho se tiverem permissões para voltar a partilhar.

2. Mesmo que não tenha uma licença do Power BI Pro, pode ver e interagir com itens no serviço Power BI se estes estiverem na área de trabalho da capacidade Premium.

## <a name="licensing-workspaces-and-capacity"></a>Licenciamento, áreas de trabalho e capacidade
O licenciamento também desempenha um papel na determinação do que pode e não pode fazer numa área de trabalho. Muitas funcionalidades exigem que o utilizador tenha uma licença do Power BI *Pro*. A maioria dos *consumidores* trabalha com uma licença *gratuita*. 

Se tiver uma licença gratuita e a área de trabalho estiver armazenada na *capacidade Premium*, poderá ver e interagir com os conteúdos nessa área de trabalho. Um ícone de diamante identifica as áreas de trabalho e aplicações que estão armazenadas na capacidade Premium.

![Áreas de trabalho selecionadas](media/end-user-workspaces/power-bi-diamond.png) Para saber mais, veja [Qual é a minha licença?](end-user-license.md).



## <a name="next-steps"></a>Próximos passos
* [Aplicações no Power BI](end-user-apps.md)    

* Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

