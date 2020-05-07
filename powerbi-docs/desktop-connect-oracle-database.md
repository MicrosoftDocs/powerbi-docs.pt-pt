---
title: Ligar a uma base de dados Oracle
description: Passos e transferências necessários para ligar o Oracle ao Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/24/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a118cd0874410e538ca8329e0b8c0ed1bdb430b7
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82149605"
---
# <a name="connect-to-an-oracle-database"></a>Ligar a uma base de dados Oracle
Para se ligar a uma base de dados do Oracle com o Power BI Desktop, tem de ser instalado o software cliente Oracle correto no computador que está a executar o Power BI Desktop. O software cliente Oracle que utiliza depende da versão do Power BI Desktop que tem instalada: a versão de 32 bits ou a versão de 64 bits.

Versões do Oracle suportadas: 
- Oracle 9 e posterior
- Software de cliente Oracle 8.1.7 e posterior

> [!NOTE]
> Se estiver a configurar uma base de dados Oracle para o Power BI Report Server, consulte as informações no artigo [Oracle Connection Type](https://docs.microsoft.com/sql/reporting-services/report-data/oracle-connection-type-ssrs?view=sql-server-ver15) (Tipo de Ligação Oracle). 


## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>Determinar que versão do Power BI Desktop está instalada
Para determinar qual é a versão do Power BI Desktop que está instalada, selecione **Ficheiro** > **Ajuda** > **Acerca de** e, em seguida, veja a linha **Versão**. Na imagem seguinte, está instalada a versão de 64 bits do Power BI Desktop:

![Versão do Power BI Desktop](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="installing-the-oracle-client"></a>Instalar o cliente Oracle
- Para a versão de 32 bits do Power BI Desktop, [transfira e instale o cliente Oracle de 32 bits](https://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html).

- Para a versão de 64 bits do Power BI Desktop, [transfira e instale o cliente Oracle de 64 bits](https://www.oracle.com/technetwork/database/windows/downloads/index-090165.html).

## <a name="connect-to-an-oracle-database"></a>Ligar a uma base de dados Oracle
Depois de instalar o controlador cliente Oracle adequado, pode estabelecer ligação com uma base de dados do Oracle. Para estabelecer ligação, efetue os seguintes passos:

1. No separador **Base**, selecione **Obter Dados**. 

2. Na janela **Obter Dados** que é apresentada, selecione **Mais** (se for necessário), selecione **Base de dados** > **Base de dados Oracle** e, em seguida, selecione **Ligar**.
   
   ![Ligar à base de dados Oracle](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
2. Na caixa de diálogo **Base de dados Oracle** que é apresentada, indique o nome do **Servidor** e selecione **OK**. Se for necessário um SID, especifique-o com o formato: *ServerName/SID*, em que *SID* é o nome exclusivo da base de dados. Se o formato *ServerName/SID* não funcionar, utilize *ServerName/ServiceName*, em que *ServiceName* é o alias que utiliza para ligar.


   ![Introduzir o nome do servidor Oracle](media/desktop-connect-oracle-database/connect-oracle-database_3.png)

   > [!TIP]
   > Se estiver com problemas de ligação neste passo, experimente utilizar o seguinte formato no campo **Server**: *(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=host_name)(PORT=port_num))(CONNECT_DATA=(SERVICE_NAME=service_name)))*
   
3. Se pretender importar dados com recurso a uma consulta de base de dados nativa, coloque a sua consulta na caixa **Instrução SQL**, que aparece quando expande a secção **Opções avançadas** da caixa de diálogo **Base de dados Oracle**.
   
   ![Expandir opções avançadas](media/desktop-connect-oracle-database/connect-oracle-database_4.png)
4. Depois de introduzir as informações da base de dados Oracle na caixa de diálogo **Base de dados Oracle** (incluindo informações opcionais, tais como um SID ou uma consulta de base de dados nativa), selecione **OK** para ligar.
5. Se a base de dados Oracle requerer credenciais de utilizador de base de dados, introduza essas credenciais na caixa de diálogo quando lhe for pedido.


## <a name="troubleshooting"></a>Resolução de problemas

Se transferiu o Power BI Desktop a partir da Microsoft Store, é possível que não consiga ligar a bases de dados Oracle devido a um problema no controlador da Oracle. Caso se depare com este problema, será devolvida a mensagem de erro: *A referência do objeto não foi definida*. Para resolver o problema, siga um dos seguintes passos:

* Transfira o Power BI Desktop a partir do [Centro de Transferências](https://www.microsoft.com/download/details.aspx?id=58494) em vez de a partir da Microsoft Store.

* Se quiser utilizar a versão da Microsoft Store: no seu computador local, copie o ficheiro oraons.dll de _12.X.X\client_X_ para _12.X.X\client_X\bin_, em que _X_ representa os números da versão e do diretório.

Se vir a mensagem de erro *A referência do objeto não foi definida* no Power BI Gateway quando ligar a uma base de dados Oracle, siga as instruções presentes no artigo [Gerir a origem de dados – Oracle](service-gateway-onprem-manage-oracle.md).

Se estiver a utilizar o Power BI Report Server, consulte a orientação no artigo [Oracle Connection Type](https://docs.microsoft.com/sql/reporting-services/report-data/oracle-connection-type-ssrs?view=sql-server-ver15) (Tipo de Ligação Oracle).