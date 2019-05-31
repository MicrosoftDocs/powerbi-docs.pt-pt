---
title: Trusted conectores de terceiros no Power BI
description: Como um conector de terceiros assinado no Power BI de confiança
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/3/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 30b7457c6149320c43f24b967a842382821b01b1
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65607788"
---
# <a name="trusting-third-party-connectors"></a>Conectores de terceiros fidedignas

## <a name="why-do-you-need-trusted-third-party-connectors"></a>Por que precisa de conectores de terceiros fidedignas?

No Power BI, em geral, recomendamos que mantenha sua "segurança de extensão de dados" nível no nível mais elevado, que impeça o carregamento de código não está certificado pela Microsoft. No entanto, pode haver muitos casos em que pretende carregar conectores específicos – aqueles que escreveu, ou aquelas fornecidas a por um consultor ou um fornecedor fora do caminho de certificação da Microsoft.

O desenvolvedor de um determinado conector pode assiná-la com um certificado e fornecer-lhe as informações necessárias para carregá-lo com segurança sem reduzir as definições de segurança.

Se quiser saber mais sobre as definições de segurança, pode ler sobre as mesmas [aqui](https://docs.microsoft.com/power-bi/desktop-connector-extensibility).

## <a name="using-the-registry-to-trust-third-party-connectors"></a>Usando o Registro para confiar conectores de terceiros

Confiar conectores de terceiros no Power BI é feito, listando o thumbprint do certificado que pretende para confiar num valor de registo especificada. Se este thumbprint coincidir com o thumbprint do certificado no conector que pretende carregar, poderá carregá-lo ao nível da segurança "Recomendados" do Power BI. 

O caminho do registo é HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Power BI Desktop. Certifique-se de que o caminho existe ou criá-la. Escolhemos esta localização devido a ele principalmente a ser controlada pela política de TI, bem como exigir acesso de administração do computador local para editar. 

![Definir registo de ambiente de trabalho do Power BI sem chaves de terceiros fidedigna](media/desktop-trusted-third-party-connectors/desktoptrustedthird1.png)

Adicione um novo valor no caminho especificado acima. O tipo deve ser "Valor de cadeia de caracteres múltipla" (REG_MULTI_SZ) e deve ser chamado "TrustedCertificateThumbprints" 

![Registo de ambiente de trabalho do Power BI com uma entrada para os conectores de terceiros confiáveis, mas não existem chaves](media/desktop-trusted-third-party-connectors/desktoptrustedthird2.png)

Adicione os thumbprints dos certificados que pretende confiar. Pode adicionar vários certificados utilizando "\0" como delimitador, ou no editor do Registro, direito clique -> modificar e colocar cada thumbprint numa nova linha. Thumbprint do exemplo é obtido a partir de um certificado autoassinado. 

 ![Registo de ambiente de trabalho do Power BI com um conjunto de chaves de terceiros fidedigno](media/desktop-trusted-third-party-connectors/desktoptrustedthird3.png)

Se tive seguido as instruções corretamente e receberam o thumbprint adequado ao seu desenvolvedor, deve ser capaz de forma segura os conectores de confiança assinados com o certificado associado.

## <a name="how-to-sign-connectors"></a>Como os conectores de início de sessão

Se tiver um conector que ou um programador tem de iniciar sessão, pode ler sobre isso da documentação do Power Query [aqui](https://docs.microsoft.com/power-query/handlingconnectorsigning).
