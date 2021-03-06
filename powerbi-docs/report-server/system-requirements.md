---
title: Requisitos de software e hardware para instalar o Power BI Report Server
description: Este artigo descreve o hardware mínimo e os requisitos de software para instalar e executar o Power BI Report Server.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 12/07/2020
ms.openlocfilehash: 10fb104d1c03ae5d08836b8e865178c347d848ce
ms.sourcegitcommit: 0bf42b6393cab7a37d21a52b934539cf300a08e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/07/2020
ms.locfileid: "96781779"
---
# <a name="hardware-and-software-requirements-for-installing-power-bi-report-server"></a>Requisitos de software e hardware para instalar o Power BI Report Server

Este artigo descreve o hardware mínimo e os requisitos de software para instalar e executar o Power BI Report Server.

## <a name="processor-memory-and-operating-system-requirements"></a>Requisitos de Processador, Memória e Sistema Operativo

| Componente | Requisito |
| --- | --- |
| .NET Framework |4.8<br><br>Se o servidor não tiver acesso à Internet, pode instalar manualmente o .NET Framework a partir do [Microsoft .NET Framework 4.8 (Instalador Offline) para Windows](https://support.microsoft.com/en-us/help/4503548/).<br/><br/> Para obter mais informações, recomendações e orientações sobre o .NET Framework 4.8, veja o [Guia de Implementação do .NET Framework para Programadores](/dotnet/framework/deployment/deployment-guide-for-developers).<br/><br/>O Windows 8.1 e o Windows Server 2012 R2 requerem a atualização [KB2919355](https://support.microsoft.com/kb/2919355) antes de instalar o .NET Framework 4.8. |
| Disco Rígido |O Power BI Report Server requer um mínimo de 1 GB de espaço disponível em disco rígido.<br><br>Será necessário espaço adicional no servidor de base de dados que aloja a base de dados do servidor de relatórios. |
| Memória |**Mínima:** 1 GB<br/><br/> **Recomendada:** Pelo menos 4 GB |
| Velocidade do processador |**Mínima:** Processador x64: 1,4 GHz<br/><br/> **Recomendada:** 2,0 GHz ou mais rápido |
| Tipo de processador |Processador x64: AMD Opteron, AMD Athlon 64, Intel Xeon com suporte Intel EM64T, Intel Pentium IV com suporte EM64T |
| Sistema operativo |Windows Server 2019 Datacenter<br><br>Windows Server 2019 Standard<br><br>Windows Server 2016 Datacenter<br><br>Windows Server 2016 Standard<br><br>Windows 10 Home<br><br>Windows 10 Professional<br><br>Windows 10 Enterprise<br> |

> [!NOTE]
> A instalação do Power BI Report Server é suportada apenas em processadores x64.


## <a name="database-server-version-requirements"></a>Requisitos de versão do servidor de bases de dados

O SQL Server é utilizado para alojar as bases de dados de servidores de relatórios. A instância do Motor de Base de Dados do SQL Server pode ser uma instância local ou remota. São suportadas as seguintes versões no Motor de Base de Dados do SQL Server que podem ser utilizadas para alojar as bases de dados do servidor de relatórios:

* Instância Gerida do SQL do Azure (versão de janeiro de 2020 e posterior do Power BI Report Server)
* SQL Server 2019
* SQL Server 2017
* SQL Server 2016
* SQL Server 2014
* SQL Server 2012

Quando criar a base de dados do servidor de relatórios num computador remoto, tem de configurar a ligação de forma a utilizar uma conta de utilizador de domínio ou uma conta de serviço com acesso à rede. Se decidir utilizar uma instância remota do SQL Server, considere atentamente que credenciais o servidor de relatórios deve utilizar para se ligar à instância do SQL Server. Para obter mais informações, consulte [Configure a Report Server Database Connection (Configurar uma Ligação à Base de Dados do Servidor de Relatórios - em inglês)](/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager).

## <a name="considerations"></a>Considerações

O Power BI Report Server irá instalar os valores predefinidos para configurar as principais definições necessárias para tornar um servidor de relatórios operacional. Tem os seguintes requisitos:

* Os idiomas suportados para o Power BI Report Server são: inglês, alemão, espanhol, japonês, italiano, francês, russo, chinês simplificado, chinês tradicional, português do Brasil e coreano.
* Tem de estar disponível um Motor de Base de Dados do SQL Server após a configuração e antes de configurar a base de dados para o servidor de relatórios. A instância do Motor de Base de Dados aloja a base de dados do servidor de relatórios que o Gestor de Configuração do Reporting Services irá criar. O Motor de Base de Dados não é necessário para a experiência de configuração propriamente dita.
* [Reporting Services Features Supported by the Editions of SQL Server](/sql/reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016) (Recursos do SQL Server Reporting Services Suportados pelas Edições do SQL Server) descreve as diferenças entre as edições do SQL Server.
* A conta de utilizador que executa a Configuração tem de ser de um membro do grupo local de Administradores.
* A conta de utilizador que executa o Gestor de Configuração do SQL Server Reporting Services tem de ter permissão para aceder e criar bases de dados na instância do Motor de Base de Dados que aloja as bases de dados do servidor de relatórios.
* A configuração tem de conseguir utilizar os valores predefinidos para reservar os URLs que fornecem acesso ao servidor de relatórios e ao portal Web. Estes valores são a porta 80, um caráter universal forte, e os nomes de diretório virtual no formato **ReportServer** e **Relatórios**.

## <a name="read-only-domain-controller-rodc"></a>Controlador de domínio só de leitura (RODC)

 Pode instalar o servidor de relatórios num ambiente que tem um Controlador de Domínio Só de Leitura (RODC). No entanto, o SQL Server Reporting Services requer acesso a um Controlador de Domínio de Leitura/Escrita para funcionar corretamente. Se o Reporting Services tiver acesso apenas a um RODC, poderá encontrar erros ao tentar administrar o serviço.

## <a name="power-bi-reports-and-analysis-services-live-connections"></a>Ligações em direto do Analysis Services e relatórios do Power BI

Pode utilizar uma ligação em direto contra instâncias em tabela ou multidimensionais. O seu servidor do Analysis Services tem de ser a versão e edição correta para funcionar devidamente.

| **Versão do servidor** | **SKU necessário** |
| --- | --- |
| 2012 SP1 CU4 ou posterior |Business Intelligence e SKU Enterprise |
| 2014 |Business Intelligence e SKU Enterprise |
| 2016 e posterior |SKU Standard ou superior |

## <a name="next-steps"></a>Passos seguintes

[O que é o Power BI Report Server?](get-started.md)  
[Descrição geral para administradores](admin-handbook-overview.md)  
[Instalar o Power BI Report Server](install-report-server.md)  
[Transferir o Report Builder](https://www.microsoft.com/download/details.aspx?id=53613)  
[Transferir o SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
