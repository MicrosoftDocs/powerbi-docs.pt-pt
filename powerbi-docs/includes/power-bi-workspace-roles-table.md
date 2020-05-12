---
title: Funções da área de trabalho do Power BI
description: Tabela de funções da área de trabalho do Power BI
services: powerbi
author: maggiesMSFT
ms.service: powerbi
ms.topic: include
ms.date: 04/23/2020
ms.author: maggies
ms.custom: include file
ms.openlocfilehash: 5ed3a65f1ef65640c76ada765931a85714aad3af
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82781362"
---
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
| Copiar um relatório.<sup>2</sup> | X | X | X |  |
| Agendar atualizações de dados através do gateway no local.<sup>3</sup> | X | X | X |  |
| Modificar definições da ligação do gateway.<sup>3</sup> | X | X | X |  |
| Ver e interagir com um item.<sup>4</sup> |  X | X  | X  | X  |
| Ler dados armazenados nos fluxos de dados da área de trabalho | X | X | X | X |

1. Os Contribuidores e Visualizadores podem partilhar itens numa área de trabalho se tiverem permissões para voltar a partilhar.
2. Para copiar um relatório e para criar um relatório noutra área de trabalho com base num conjunto de dados nessa área de trabalho, necessita de permissão de Compilação para o conjunto de dados. Para conjuntos de dados nessa área de trabalho, as pessoas com as funções Administrador, Membro e Contribuidor têm permissão de Compilação através da função da área de trabalho.
3. Lembre-se de que também precisa de permissões no gateway. Estas permissões são geridas noutro local, independentemente das permissões e funções da área de trabalho. Veja [Gerir um gateway no local](https://docs.microsoft.com/data-integration/gateway/service-gateway-manage) para obter detalhes.
4. Mesmo que não tenha uma licença do Power BI Pro, pode ver e interagir com itens no serviço Power BI se estes estiverem na área de trabalho de uma capacidade Premium.

