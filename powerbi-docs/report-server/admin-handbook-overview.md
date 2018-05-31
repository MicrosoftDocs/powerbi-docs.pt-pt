---
title: Descrição geral de administração, Power BI Report Server
description: Este artigo é a descrição geral da administração do Power BI Report Server, uma localização no local para armazenar e gerir os relatórios móveis e paginados do Power BI.
services: powerbi
documentationcenter: ''
author: markingmyname
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/07/2018
ms.author: maghan
ms.openlocfilehash: 52b2c9cac7fd07564480fdbf3a6a91e04e72db11
ms.sourcegitcommit: c29525cbac2e747edb4dd3a1841084bb0ce42582
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883095"
---
# <a name="admin-overview-power-bi-report-server"></a>Descrição geral de administração, Power BI Report Server
Este artigo é a descrição geral da administração do Power BI Report Server, uma localização no local para armazenar e gerir os relatórios móveis e paginados do Power BI. Este artigo apresenta os conceitos de planeamento, implementação e gestão do seu Power BI Report Server, com ligações para obter mais informações.

![](media/admin-handbook-overview/admin-handbook.png)



## <a name="installing-and-migration"></a>Instalação e migração
Terá de instalar o Power BI Report Server para começar a utilizá-lo. Temos informações que lhe permitirão processar esta tarefa.

Antes de começar a instalar, atualizar ou migrar para o Power BI Report Server, veja os [requisitos de sistema](system-requirements.md) do servidor de relatórios.

### <a name="installing"></a>Instalação
Se estiver a implementar um novo Power BI Report Server, utilize o seguinte documento para ajudá-lo. 

[Instalar o Power BI Report Server](install-report-server.md)

### <a name="migration"></a>Migração
Não é necessário atualizar para o SQL Server Reporting Services. Se tiver uma instância existente do SQL Server Reporting Services que queira tornar num Power BI Report Server, terá de migrá-la. Existem outras razões para efetuar uma migração. Consulte o documento de migração para obter mais detalhes.

[Migrar uma instalação do servidor de relatórios](migrate-report-server.md)

## <a name="configuring-your-report-server"></a>Configurar o servidor de relatórios
Tem várias opções de configuração do servidor de relatórios. Irá utilizar SSL? Está a configurar um servidor de e-mail? Quer integrar no serviço Power BI para afixar visualizações?

A maioria da configuração irá ocorrer no Gestor de Configuração do Servidor de Relatórios. Veja a documentação do [gestor de configuração](https://docs.microsoft.com/sql/reporting-services/install-windows/reporting-services-configuration-manager-native-mode) para obter mais detalhes.

## <a name="security"></a>Segurança
A segurança e proteção são importantes para todas as organizações. Pode saber mais sobre autenticação, autorização, funções e permissões ao longo da documentação de [segurança](https://docs.microsoft.com/sql/reporting-services/security/reporting-services-security-and-protection).

## <a name="next-steps"></a>Próximos passos
[Instalar o Power BI Report Server](install-report-server.md)  
[Encontrar a chave de produto do servidor de relatórios](find-product-key.md)  
[Instalar o Power BI Desktop otimizado para o Power BI Report Server](install-powerbi-desktop.md)  
[Instalar o Report Builder](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Transferir o SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

