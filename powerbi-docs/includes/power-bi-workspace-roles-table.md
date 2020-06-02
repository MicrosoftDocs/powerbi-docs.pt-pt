---
title: Funções da área de trabalho do Power BI
description: Tabela de funções da área de trabalho do Power BI
services: powerbi
author: maggiesMSFT
ms.service: powerbi
ms.topic: include
ms.date: 05/26/2020
ms.author: maggies
ms.custom: include file
ms.openlocfilehash: 708599eb3f39d4c627a11753cb964d6425f75640
ms.sourcegitcommit: a7b142685738a2f26ae0a5fa08f894f9ff03557b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/28/2020
ms.locfileid: "84120362"
---
|Funcionalidade   | Administrador  | Membro  | Contribuidor  | Visualizador |
|---|---|---|---|---|
| Atualizar e eliminar a área de trabalho.  |  |   |   |   | 
| Adicionar/remover pessoas, incluindo outros administradores.  |  ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) |   |   |   |
| Adicionar membros ou outras pessoas com permissões mais baixas.  |  ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Publicar e atualizar uma aplicação. |  ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Partilhar um item ou uma aplicação.<sup>1</sup> |  ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Permitir que outras pessoas voltem a partilhar itens.<sup>1</sup> |  ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Destacar aplicações nas páginas Base dos colegas |  ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Destacar dashboards e relatórios nas páginas Base dos colegas |  ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) |   |
| Criar, editar e eliminar conteúdos na área de trabalho.  |  ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Publicar relatórios na área de trabalho, eliminar conteúdos.  |  ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Criar um relatório noutra área de trabalho com base num conjunto de dados desta área de trabalho.<sup>2</sup> |  ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Copiar um relatório.<sup>2</sup> | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Agendar atualizações de dados através do gateway no local.<sup>3</sup> | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Modificar definições da ligação do gateway.<sup>3</sup> | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Ver e interagir com um item.<sup>4</sup> |  ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png)  |
| Ler dados armazenados nos fluxos de dados da área de trabalho | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificação Sim](media/power-bi-workspace-roles-table/green-checkmark.png) |

<sup>1</sup> Os Contribuidores e Visualizadores também poderão partilhar itens numa área de trabalho se tiverem Permissões para voltar a partilhar.

<sup>2</sup> Para copiar um relatório e para o criar noutra área de trabalho com base num conjunto de dados nesta área de trabalho, precisa da [Permissão de compilação para o conjunto de dados](../connect-data/service-datasets-build-permissions.md). Para conjuntos de dados nesta área de trabalho, as pessoas com as funções de Administrador, Membro e Contribuidor têm automaticamente Permissão de compilação através da função da área de trabalho.

<sup>3</sup> Lembre-se de que também precisa de permissões no gateway. Essas permissões são geridas noutro local, independentemente das permissões e funções da área de trabalho. Veja [Gerir um gateway no local](https://docs.microsoft.com/data-integration/gateway/service-gateway-manage) para obter detalhes.

<sup>4</sup> Mesmo que não tenha uma licença do Power BI Pro, poderá ver e interagir com itens no serviço Power BI se estes estiverem na área de trabalho de uma capacidade Premium.

