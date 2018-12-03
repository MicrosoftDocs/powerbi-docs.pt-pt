---
title: Ligar a uma base de dados Oracle
description: Passos e transferências necessários para ligar o Oracle ao Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 5b5dc41ee3f4d41f2e38053470054a8f453e4fb3
ms.sourcegitcommit: 2ae660a7b70fce23eb58b159d049eca44a664f2c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/30/2018
ms.locfileid: "52670303"
---
# <a name="connect-to-an-oracle-database"></a>Ligar a uma base de dados Oracle
Para se ligar a uma base de dados do Oracle com o **Power BI Desktop**, tem de ser instalado o software cliente Oracle correto no computador a executar o Power BI Desktop. O software cliente Oracle que utiliza depende da versão do Power BI Desktop que tem instalada: a versão de **32 bits** ou a versão de **64 bits**.

**Versões suportadas**: Oracle 9 e posterior, software cliente Oracle 8.1.7 ou posterior.

## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>Determinar que versão do Power BI Desktop está instalada
Para determinar qual a versão do Power BI Desktop que está instalada, selecione **Ficheiro > Ajuda > Acerca de** e, em seguida, veja a linha de **Versão:**. Na imagem seguinte, está instalada a versão de 64 bits do Power BI Desktop:

![](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="installing-the-oracle-client"></a>Instalar o cliente Oracle
Para as versões de **32 bits** do Power BI Desktop, utilize a seguinte ligação para transferir e instalar o cliente Oracle de **32 bits**:

* [Oracle Data Access Components (ODAC) de 32 bits com o Oracle Developer Tools for Visual Studio (12.1.0.2.4)](http://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)

Para as versões de **64 bits** do Power BI Desktop, utilize a seguinte ligação para transferir e instalar o cliente Oracle de **64 bits**:

* [64-bit ODAC 12c Release 4 (12.1.0.2.4) para o Windows x64](http://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)

## <a name="connect-to-an-oracle-database"></a>Ligar a uma base de dados Oracle
Após ser instalado o controlador de cliente Oracle adequado, pode ligá-lo a uma base de dados do Oracle. Para estabelecer ligação, efetue os seguintes passos:

1. A partir da janela Obter Dados, selecione **Base de Dados > Base de Dados Oracle**
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
2. Na caixa de diálogo **Base de Dados Oracle** que for apresentada, indique o nome do servidor e selecione **Ligar**. Se for necessário um SID, poderá especificá-lo com o formato: *ServerName/SID*, em que o SID é o nome exclusivo da base de dados. Se o formato *ServerName/SID* não funcionar, experimente utilizar *ServerName/ServiceName*, em que ServiceName é o alias utilizado ao estabelecer ligação.
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_3.png)
3. Se pretender importar dados utilizando uma consulta de base de dados nativa, pode colocar a sua consulta na caixa **Instrução SQL**, disponível ao expandir a secção **Opções avançadas** da caixa de diálogo **Base de Dados Oracle**.
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_4.png)
4. Quando as informações da base de dados Oracle forem introduzidas na caixa de diálogo Base de Dados Oracle (incluindo informações opcionais, como um SID ou uma consulta de base de dados nativa), selecione **OK** para ligar.
5. Se a base de dados Oracle requerer credenciais de utilizador de base de dados, introduza essas credenciais na caixa de diálogo quando lhe for pedido.

