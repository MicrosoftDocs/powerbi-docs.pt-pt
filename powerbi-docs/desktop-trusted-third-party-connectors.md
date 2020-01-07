---
title: Conectores de Terceiros Fidedignos no Power BI
description: Como confiar num conector de terceiros no Power BI
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/3/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: ac3f795d6a80d5f143daf68436f41f5771b3c2bb
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/06/2020
ms.locfileid: "73876168"
---
# <a name="trusting-third-party-connectors"></a>Confiar em conectores de terceiros

## <a name="why-do-you-need-trusted-third-party-connectors"></a>Por que precisa de conectores de terceiros fidedignos?

No Power BI, regra geral, recomendamos que mantenha o seu nível de "Segurança de extensões de dados" no nível mais elevado, o que impede o carregamento de código não certificado pela Microsoft. No entanto, pode haver muitos casos em que pretende carregar conectores específicos: os que escreveu ou os que lhe foram fornecidos por um consultor ou fornecedor fora do percurso de certificação da Microsoft.

O programador de um determinado conector pode assiná-lo com um certificado e fornecer-lhe as informações de que precisa para carregá-los de forma segura sem reduzir as suas definições de segurança.

Se quiser saber mais sobre definições de segurança, pode ler sobre as mesmas [aqui](https://docs.microsoft.com/power-bi/desktop-connector-extensibility).

## <a name="using-the-registry-to-trust-third-party-connectors"></a>Utilizar o registo para confiar em conectores de terceiros

Para confiar em conectores de terceiros no Power BI, liste o thumbprint do certificado em que pretende confiar num valor de registo especificado. Se este thumbprint corresponder ao thumbprint do certificado no conector que pretende carregar, poderá carregá-lo no nível de segurança "Recomendado" do Power BI. 

O caminho do registo é HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Power BI Desktop. Certifique-se de que o caminho existe ou crie-o. Escolhemos esta localização porque é principalmente controlada pela política das TI, além de exigir acesso de administrador do computador local para editar. 

![Registo do Power BI Desktop sem chaves de terceiros fidedignas definidas](media/desktop-trusted-third-party-connectors/desktoptrustedthird1.png)

Adicione um novo valor no caminho especificado acima. O tipo deverá ser "Multi-String Value" (REG_MULTI_SZ) e deverá ter o nome "TrustedCertificateThumbprints" 

![Registo do Power BI Desktop com uma entrada para conectores de terceiros fidedignos, mas sem chaves](media/desktop-trusted-third-party-connectors/desktoptrustedthird2.png)

Adicione os thumbprints dos certificados em que pretende confiar. Pode adicionar diversos certificados utilizando "\0" como delimitador. Em alternativa, no editor de registo, clique com o botão direito do rato -> modificar e coloque cada thumbprint numa nova linha. Exemplo de thumbprint retirado de um certificado autoassinado. 

 ![Registo do Power BI Desktop com uma chave de terceiros fidedigna definida](media/desktop-trusted-third-party-connectors/desktoptrustedthird3.png)

Se tiver seguido corretamente as instruções e tiver recebido o thumbprint adequado do seu programador, deverá agora poder confiar em segurança nos conectores assinados com o certificado associado.

## <a name="how-to-sign-connectors"></a>Como Assinar Conectores

Se tiver um conector que você ou um programador precisem de assinar, pode ler sobre o mesmo na documentação do Power Query [aqui](https://docs.microsoft.com/power-query/handlingconnectorsigning).
