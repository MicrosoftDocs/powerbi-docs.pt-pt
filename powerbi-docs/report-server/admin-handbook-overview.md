---
title: Descrição geral de administração, Power BI Report Server
description: Este artigo é a descrição geral da administração do Power BI Report Server, uma localização no local para armazenar e gerir os relatórios móveis e paginados do Power BI.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: maggies
ms.openlocfilehash: 172bc4cb677ffb4df5719e3c77f12ad10160c247
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861274"
---
# <a name="admin-overview-power-bi-report-server"></a>Descrição geral de administração, Power BI Report Server
Este artigo é a descrição geral da administração do Power BI Report Server, uma localização no local para armazenar e gerir os relatórios móveis e paginados do Power BI. Este artigo apresenta os conceitos de planeamento, implementação e gestão do Power BI Report Server, com ligações para obter mais informações.

![Captura de ecrã a mostrar o Power B I Report Server com as opções de início de sessão.](media/admin-handbook-overview/admin-handbook.png)
 
## <a name="installing-and-migration"></a>Instalação e migração
Tem de instalar o Power BI Report Server para começar a utilizá-lo. Temos artigos que explicam como realizar esta tarefa.

Antes de começar a instalar, atualizar ou migrar para o Power BI Report Server, veja os [requisitos de sistema](system-requirements.md) do servidor de relatórios.

### <a name="installing"></a>Installing
Se estiver a implementar um novo Power BI Report Server, utilize o seguinte documento para ajudá-lo. 

[Instalar o Power BI Report Server](install-report-server.md)

### <a name="migration"></a>Migração
Não é necessário atualizar para o SQL Server Reporting Services. Se tiver uma instância existente do SQL Server Reporting Services que pretenda tornar num Power BI Report Server, tem de a migrar. Também poderá optar por executar uma migração por outras razões. Consulte o documento de migração para obter mais detalhes.

[Migrar uma instalação do servidor de relatórios](migrate-report-server.md)

## <a name="configuring-your-report-server"></a>Configurar o servidor de relatórios
Tem várias opções de configuração do servidor de relatórios. Irá utilizar SSL? Está a configurar um servidor de e-mail? Quer integrar no serviço Power BI para afixar visualizações?

A maioria da configuração irá ocorrer no Gestor de Configuração do Servidor de Relatórios. Veja a documentação do [gestor de configuração](/sql/reporting-services/install-windows/reporting-services-configuration-manager-native-mode) para obter mais detalhes.

## <a name="security"></a>Segurança
A segurança e proteção são importantes para todas as organizações. Pode saber mais sobre a autenticação, a autorização, as funções e as permissões na documentação de [segurança](/sql/reporting-services/security/reporting-services-security-and-protection).

## <a name="next-steps"></a>Próximos passos
[Instalar o Power BI Report Server](install-report-server.md)  
[Encontrar a chave de produto do servidor de relatórios](find-product-key.md)  
[Instalar o Power BI Desktop otimizado para o Power BI Report Server](install-powerbi-desktop.md)  
[Transferir o Report Builder](https://www.microsoft.com/download/details.aspx?id=53613)  
[Transferir o SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)