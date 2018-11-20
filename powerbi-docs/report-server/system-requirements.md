---
title: Requisitos de software e hardware para instalar o Power BI Report Server
description: Este artigo descreve o hardware mínimo e os requisitos de software para instalar e executar o Power BI Report Server.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 11/08/2018
ms.author: maghan
ms.openlocfilehash: c8904f3025a0a60557b1d3efb54ea6bc18c20da4
ms.sourcegitcommit: a1b7ca499f4ca7e90421511e9dfa61a33333de35
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/10/2018
ms.locfileid: "51507912"
---
# <a name="hardware-and-software-requirements-for-installing-power-bi-report-server"></a>Requisitos de software e hardware para instalar o Power BI Report Server
Este artigo descreve o hardware mínimo e os requisitos de software para instalar e executar o Power BI Report Server.

## <a name="processor-memory-and-operating-system-requirements"></a>Requisitos de Processador, Memória e Sistema Operativo

| Componente | Requisito |
| --- | --- |
| .NET Framework |4.6<br><br>Pode instalar manualmente o .NET Framework do [Microsoft .NET Framework 4.6 (Instalador Web) para Windows](http://support.microsoft.com/kb/3045560).<br/><br/> Para obter mais informações, recomendações e orientações sobre o .NET Framework 4.6, consulte o [Guia de Implementação do .NET Framework para Programadores](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).<br/><br/>O Windows 8.1 e o Windows Server 2012 R2 requerem o [KB2919355](http://support.microsoft.com/kb/2919355) antes de instalar o .NET Framework 4.6. |
| Disco Rígido |O Power BI Report Server requer um mínimo de 1 GB de espaço disponível em disco rígido.<br><br>Será necessário espaço adicional no servidor de base de dados que aloja a base de dados do servidor de relatórios. |
| Memória |**Mínima:** 1 GB<br/><br/> **Recomendada:** Pelo menos 4 GB |
| Velocidade do processador |**Mínima:** Processador x64: 1,4 GHz<br/><br/> **Recomendada:** 2,0 GHz ou mais rápido |
| Tipo de processador |Processador x64: AMD Opteron, AMD Athlon 64, Intel Xeon com suporte Intel EM64T, Intel Pentium IV com suporte EM64T |
| Sistema operativo |Windows Server 2016 Datacenter<br><br>Windows Server 2016 Standard<br><br>Windows Server 2012 R2 Datacenter<br><br>Windows Server 2012 R2 Standard<br><br>Windows Server 2012 R2 Essentials<br><br>Windows Server 2012 R2 Foundation<br><br>Windows Server 2012 Datacenter<br><br>Windows Server 2012 Standard<br><br>Windows Server 2012 Essentials<br><br>Windows Server 2012 Foundation<br><br>Windows 10 Home<br><br>Windows 10 Professional<br><br>Windows 10 Enterprise<br><br>Windows 8.1<br><br>Windows 8.1 Pro<br><br>Windows 8.1 Enterprise<br><br>Windows 8<br><br>Windows 8 Pro<br><br>Windows 8 Enterprise |

> [!NOTE]
> A instalação do Power BI Report Server é suportada apenas em processadores x64.
> 
> 

## <a name="database-server-version-requirements"></a>Requisitos de versão do servidor de bases de dados
O SQL Server é utilizado para alojar as bases de dados de servidores de relatórios. A instância do Motor de Base de Dados do SQL Server pode ser uma instância local ou remota. São suportadas as seguintes versões no Motor de Base de Dados do SQL Server que podem ser utilizadas para alojar as bases de dados do servidor de relatórios:

* SQL Server 2017
* SQL Server 2016
* SQL Server 2014
* SQL Server 2012

Quando criar a base de dados do servidor de relatórios num computador remoto, tem de configurar a ligação de forma a utilizar uma conta de utilizador de domínio ou uma conta de serviço com acesso à rede. Se decidir utilizar uma instância remota do SQL Server, considere atentamente que credenciais o servidor de relatórios deve utilizar para se ligar à instância do SQL Server. Para obter mais informações, consulte [Configure a Report Server Database Connection (Configurar uma Ligação à Base de Dados do Servidor de Relatórios - em inglês)](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager).

## <a name="considerations"></a>Considerações
O Power BI Report Server irá instalar os valores predefinidos para configurar as principais definições necessárias para tornar um servidor de relatórios operacional. Tem os seguintes requisitos:

* Tem de estar disponível um Motor de Base de Dados do SQL Server após a configuração e antes de configurar a base de dados para o servidor de relatórios. A instância do Motor de Base de Dados aloja a base de dados do servidor de relatórios que o Gestor de Configuração do Reporting Services irá criar. O Motor de Base de Dados não é necessário para a experiência de configuração propriamente dita.
- [Reporting Services Features Supported by the Editions of SQL Server](https://docs.microsoft.com/sql/reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016) (Recursos do SQL Server Reporting Services Suportados pelas Edições do SQL Server) descreve as diferenças entre as edições do SQL Server.
* A conta de utilizador que executa a Configuração tem de ser de um membro do grupo local de Administradores.
* A conta de utilizador que executa o Gestor de Configuração do SQL Server Reporting Services tem de ter permissão para aceder e criar bases de dados na instância do Motor de Base de Dados que aloja as bases de dados do servidor de relatórios.
* A configuração tem de conseguir utilizar os valores predefinidos para reservar os URLs que fornecem acesso ao servidor de relatórios e ao portal Web. Estes valores são a porta 80, um caráter universal forte, e os nomes de diretório virtual no formato **ReportServer** e **Relatórios**.

## <a name="read-only-domain-controller-rodc"></a>Controlador de domínio só de leitura (RODC)
 Pode instalar o servidor de relatórios num ambiente que tem um Controlador de Domínio Só de Leitura (RODC). No entanto, o SQL Server Reporting Services requer acesso a um Controlador de Domínio de Leitura/Escrita para funcionar corretamente. Se o Reporting Services tiver acesso apenas a um RODC, poderá encontrar erros ao tentar administrar o serviço.

## <a name="power-bi-reports-and-analysis-services-live-connections"></a>Ligações em direto do Analysis Services e relatórios do Power BI
Pode utilizar uma ligação em direto para instâncias em tabela ou multidimensionais. O seu servidor do Analysis Services tem de ser a versão e edição correta para funcionar devidamente.

| **Versão do servidor** | **SKU necessário** |
| --- | --- |
| 2012 SP1 CU4 ou posterior |Business Intelligence e SKU Enterprise |
| 2014 |Business Intelligence e SKU Enterprise |
| 2016 e posterior |SKU Standard ou superior |

## <a name="next-steps"></a>Próximos passos
[O que é o Power BI Report Server?](get-started.md)  
[Descrição geral para administradores](admin-handbook-overview.md)  
[Instalar o Power BI Report Server](install-report-server.md)  
[Transferir o Report Builder](https://www.microsoft.com/download/details.aspx?id=53613)  
[Transferir o SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

