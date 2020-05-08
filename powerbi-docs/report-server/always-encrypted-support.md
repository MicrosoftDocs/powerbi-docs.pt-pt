---
title: Funcionalidade Always Encrypted no Power BI Report Server
description: Este artigo descreve o suporte da funcionalidade Always Encrypted no Power BI Report Server ao utilizar os tipos de origens de dados Microsoft SQL Server e Base de Dados SQL do Microsoft Azure.
author: maggiesMSFT
ms.reviewer: cfinlan
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/22/2020
ms.author: maggies
ms.openlocfilehash: f8d711bba8dc7570f2d470554fd1d971639bbb7b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "76710212"
---
# <a name="always-encrypted-in-power-bi-report-server"></a>Funcionalidade Always Encrypted no Power BI Report Server

Este artigo descreve o suporte da funcionalidade Always Encrypted no Power BI Report Server ao utilizar os tipos de origens de dados Microsoft SQL Server e Base de Dados SQL do Microsoft Azure. Para obter mais informações sobre a funcionalidade Always Encrypted no SQL Server, veja o artigo [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine).

## <a name="always-encrypted-user-isolation"></a>Isolamento de utilizadores da funcionalidade Always Encrypted

Neste momento, o Power BI Report Server não restringe o acesso a colunas Always Encrypted nos relatórios se um utilizador tiver acesso ao relatório.  Portanto, se o servidor tiver acesso às chaves de encriptação de coluna através da chave mestra da coluna, os utilizadores terão acesso a todas as colunas dos relatórios a que podem aceder.

## <a name="always-encrypted-column-usage"></a>Utilização da coluna Always Encrypted

### <a name="key-storage-strategies"></a>Principais estratégias de armazenamento

|Armazenamento  |Suportado  |
|---------|---------|
|Arquivo de Certificados do Windows | Yes |
|Azure Key Vault | No |
| Cryptography Next Generation (CNG) | No |

### <a name="certificate-storage-and-access"></a>Acesso e armazenamento de certificados

A conta que requer acesso ao certificado é a conta de serviço. O certificado deve ser armazenado no arquivo de certificados do computador local. Para obter mais informações, veja:

- [Configure the Report Server Service Account](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager) (Configurar a Conta de Serviço do Servidor de Relatórios) (Configuration Manager)
- Secção [Making certificates available to applications and users](https://docs.microsoft.com/sql/relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted#making-certificates-available-to-applications-and-users) (Disponibilizar certificados para aplicações e utilizadores) no artigo do SQL Server "Create and store column master keys for Always Encrypted" (Criar e armazenar chaves mestras de coluna para o Always Encrypted).

### <a name="column-encryption-strategy"></a>Estratégia de encriptação de coluna

No Power BI Report Server, a estratégia de encriptação de coluna pode ser *determinista* ou *aleatória*. A tabela seguinte descreve as diferenças, dependendo da estratégia utilizada.

|Utilização  |Determinista  |Aleatório  |
|---------|---------|---------|
|Pode ser lido tal como está nos resultados de uma consulta, por exemplo, instruções SELECT. | Yes  | Yes  |
|Pode ser utilizado como uma entidade Agrupar Por na consulta. | Yes | No |
|Pode ser utilizado como um campo agregado, exceto para COUNT e DISTINCT. | Não, exceto para COUNT e DISTINCT | No |
|Pode ser utilizado como um parâmetro de relatório | Yes | No |

Saiba mais sobre [encriptação determinista vs. aleatória](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption).

### <a name="parameter-usage"></a>Utilização de parâmetros

A utilização de parâmetros aplica-se apenas à encriptação determinista.

**Parâmetro de valor único**.  Pode utilizar um parâmetro de valor único numa coluna Always Encrypted.

**Parâmetro de valores múltiplos**. Não pode utilizar um parâmetro de valores múltiplos com mais de um valor numa coluna Always Encrypted.

**Parâmetros em cascata**. Pode utilizar parâmetros em cascata com Always Encrypted se *todos* os seguintes forem verdadeiros:

- Todas as colunas Always Encrypted têm de ser Always Encrypted com a estratégia determinista.
- Todos os parâmetros utilizados nas colunas Always Encrypted são parâmetros de valor único.
- Todas as comparações SQL utilizam o operador Igual a (=).

## <a name="datatype-support"></a>Suporte de tipo de dados

| Tipos de Dados SQL | Suporta o campo de leitura | Suporta a utilização como um elemento Agrupar Por | Agregações suportadas (COUNT, DISTINCT, MAX, MIN, SUM, entre outros) | Suporta a filtragem através da igualdade com parâmetros | Notas |
| --- | --- | --- | --- | --- | --- |
| int | Yes | Yes | COUNT, DISTINCT | Sim, como Número Inteiro |   |
| float | Yes | Yes | COUNT, DISTINCT | Sim, como Flutuante |   |
| nvarchar | Yes | Yes | COUNT, DISTINCT | Sim, como Texto | A encriptação determinista tem de utilizar um agrupamento de colunas com uma sequência de ordenação binary2 para colunas de carateres. Veja o artigo [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption) do SQL Server para obter detalhes.  |
| varchar | Yes | Yes | COUNT, DISTINCT | No |   |
| decimal | Yes | Yes | COUNT, DISTINCT | No |   |
| numeric | Yes | Yes | COUNT, DISTINCT | No |   |
| datetime | Yes | Yes | COUNT, DISTINCT | No |   |
| datetime2 | Yes | Yes | COUNT, DISTINCT | Sim, como Data/Hora | Suportado se a coluna não tiver precisão de milissegundos (por outras palavras, não é datetime2(0)) |

## <a name="aggregation-alternatives"></a>Alternativas de agregação

Atualmente, as únicas agregações suportadas nas colunas deterministas Always Encrypted são as agregações que utilizam diretamente o operador Igual a (=). Esta limitação do SQL Server deve-se à natureza das colunas Always Encrypted. Os utilizadores têm de agregar no relatório em vez de na base de dados.

## <a name="always-encrypted-in-connection-strings"></a>Always Encrypted nas cadeias de ligação

Tem de ativar a funcionalidade Always Encrypted na cadeia de ligação de uma origem de dados do SQL Server. Saiba mais sobre como ativar a funcionalidade [Always Encrypted nas consultas da aplicação](https://docs.microsoft.com/sql/relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider#enabling-always-encrypted-for-application-queries).

## <a name="next-steps"></a>Próximas etapas

[Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine) no SQL Server e Base de Dados SQL do Azure

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

