---
title: Origens de dados suportadas para relatórios paginados do Power BI
description: Neste artigo, irá ficar a conhecer as origens de dados suportadas para relatórios paginados no serviço Power BI e irá saber como ligar a origens de dados da Base de Dados SQL do Azure.
author: onegoodsausage
ms.author: andremi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/30/2020
ms.openlocfilehash: ec299ceb5862be3f1e121e0e7d67eca6447f2da6
ms.sourcegitcommit: 2c798b97fdb02b4bf4e74cf05442a4b01dc5cbab
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/21/2020
ms.locfileid: "80113744"
---
# <a name="supported-data-sources-for-power-bi-paginated-reports"></a>Origens de dados suportadas para relatórios paginados do Power BI

Este artigo descreve as origens de dados suportadas para relatórios paginados no serviço Power BI e explica como ligar a origens de dados da Base de Dados SQL do Azure. Algumas origens de dados são suportadas nativamente. Pode ligar-se a outras pessoas através de gateways de dados.

## <a name="natively-supported-data-sources"></a>Origens de dados suportadas nativamente

Os relatórios paginados suportam nativamente a seguinte lista de origens de dados:

| Origem de dados | Autenticação | Notas |
| --- | --- | --- |
| Base de Dados SQL do Azure <br>Azure SQL Data Warehouse | Básico, início de sessão único (SSO), OAuth2 |   |
| Instância Gerida do SQL do Azure | Básico | Através de Ponto Final Público com a Extensão Base de Dados SQL do Azure  |
| Azure Analysis Services | SSO, OAuth2 | A firewall AAS deve ser desativada ou configurada para permitir todos os intervalos de IP.|
| Conjunto de dados do Power BI | SSO | Conjuntos de dados do Power BI Premium e não Premium Requer permissão de leitura |
| Conjunto de dados do Power BI Premium (XMLA) | SSO |   |
| Introduzir Dados | N/D | Os dados são incorporados no relatório. |

Exceto no caso da Base de Dados SQL do Azure, todas as origens de dados estão prontas a utilizar depois de carregar o relatório para o serviço Power BI. A predefinição das origens de dados é a utilização do início de sessão único (SSO), quando aplicável. No caso do Azure Analysis Services, pode alterar o tipo de autenticação para OAuth2.

No caso das origens de dados da Base de Dados SQL do Azure, precisa de fornecer mais informações, conforme descrito na secção [Autenticação da Base de Dados SQL do Azure](#azure-sql-database-authentication).

## <a name="other-data-sources"></a>Outras origens de dados

Além das origens de dados suportadas nativamente acima, as seguintes origens de dados podem ser acedidas através de um [gateway de dados do Power BI](../service-gateway-onprem.md):

- SQL Server
- SQL Server Analysis Services
- Oracle
- Teradata

No caso dos relatórios paginados, a Base de Dados SQL do Azure e o Azure Analysis Services não podem atualmente ser acedidos através de um gateway de dados do Power BI.

## <a name="azure-sql-database-authentication"></a>Autenticação da Base de Dados SQL do Azure

No caso das origens de dados da Base de Dados SQL do Azure, precisa de definir um tipo de autenticação antes de executar o relatório. Isto aplica-se apenas à utilização de uma origem de dados pela primeira vez numa área de trabalho. Nessa primeira vez, é apresentada a seguinte mensagem:

![Publicar no Power BI](media/paginated-reports-data-sources/power-bi-paginated-publishing.png)

Se não fornecer credenciais, ocorrerá um erro quando executar o relatório. Selecione **Continue** (Continuar) para ir para a página **Data source credentials** (Credenciais da origem de dados) do relatório que acabou de carregar:

![Definições da Base de Dados SQL do Azure](media/paginated-reports-data-sources/power-bi-paginated-settings-azure-sql.png)

Selecione a ligação **Edit credentials** (Editar credenciais) de uma determinada origem de dados para abrir a caixa de diálogo **Configure** (Configurar):

![Configurar a Base de Dados SQL do Azure](media/paginated-reports-data-sources/power-bi-paginated-configure-azure-sql.png)

Para as origens de dados da Base de Dados SQL do Azure, eis os tipos de autenticação suportados:

- Básico (nome de utilizador e palavra-passe)
- SSO (início de sessão único)
- OAuth2 (token do AAD armazenado)

Para que o SSO e o OAuth2 funcionem corretamente, o servidor da Base de Dados SQL do Azure ao qual a origem de dados está a ligar tem de ter o [suporte de autenticação do AAD ativado](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure). No caso do método de autenticação OAuth2, o AAD gera um token e armazena-o para acesso futuro à origem de dados. Em alternativa, para utilizar o [método de autenticação SSO](https://docs.microsoft.com/power-bi/service-azure-sql-database-with-direct-connect#single-sign-on), selecione a opção de SSO **Os utilizadores finais utilizam as suas próprias credenciais do OAuth2 ao aceder a esta origem de dados através de DirectQuery** imediatamente abaixo.
  
## <a name="next-steps"></a>Próximos passos

[Ver um relatório paginado no serviço Power BI](../consumer/paginated-reports-view-power-bi-service.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
