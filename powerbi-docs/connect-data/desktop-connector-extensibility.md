---
title: Extensibilidade de Conectores no Power BI
description: Ferramentas de extensibilidade de conectores, funcionalidades, definições de segurança e conectores certificados
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/02/2020
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: b604ade56335e65b25501eb9fe3d3c2fd185a6f0
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83293519"
---
# <a name="connector-extensibility-in-power-bi"></a>Extensibilidade de conectores no Power BI

O Power BI pode ligar a dados ao utilizar conectores existentes e origens de dados genéricas, como ODBC, OData, OLE DB, Web, CSV, XML e JSON. Em alternativa, os programadores podem ativar novas origens de dados com extensões de dados personalizadas chamadas *conectores personalizados*. Alguns conectores personalizados são certificados e distribuídos pela Microsoft como *conectores certificados*.

Para utilizar conectores personalizados não certificados que você ou terceiros desenvolveram, tem de ajustar as definições de segurança do Power BI Desktop para permitir que as extensões carreguem sem validação ou aviso. Uma vez que este código é capaz de utilizar credenciais, incluindo o envio através de HTTP, e ignorar níveis de privacidade, só deve utilizar esta definição de segurança se confiar totalmente nos seus conectores personalizados.

Outra opção é que o programador assine o conector com um certificado e forneça as informações necessárias para utilizá-lo sem alterar as suas definições de segurança. Para obter mais informações, veja [Acerca dos conectores de terceiros fidedignos](desktop-trusted-third-party-connectors.md).

## <a name="custom-connectors"></a>Conectores personalizados

Os conectores personalizados não certificados podem variar desde pequenas APIs importantes para a sua empresa até grandes serviços específicos da indústria para os quais a Microsoft não lançou um conector. Muitos conectores são distribuídos pelos fornecedores. Se precisar de um conector de dados específico, contacte o fornecedor. 

Para utilizar um conector personalizado não certificado, coloque o ficheiro de conector *.pq*, *.pqx*, *.m* ou *.mez* na pasta *\[Documentos]\\Power BI Desktop\\Conectores Personalizados*. Se a pasta não existir, crie-a.

Ajuste as definições de segurança da extensão de dados da seguinte forma:

No Power BI Desktop, selecione **Ficheiro** > **Opções e definições** > **Opções** > **Segurança**.

Em **Extensões de Dados**, selecione **(Não Recomendado) Permitir o carregamento de qualquer extensão sem validação ou aviso**. Selecione **OK** e, em seguida, reinicie o Power BI Desktop. 

![Permitir conectores personalizados não certificados nas opções de Segurança da extensão de dados](media/desktop-connector-extensibility/data-extension-security-1.png)

A predefinição de segurança da extensão de dados do Power BI Desktop é **(Recomendado) Permitir apenas o carregamento de extensões certificadas da Microsoft e de outras extensões de terceiros fidedignas**. Com esta definição, se existirem conectores personalizados não certificados no seu sistema, a caixa de diálogo **Conectores Não Certificados** aparece no arranque do Power BI Desktop e indica os conectores que não podem ser carregados de forma segura.

![Caixa de diálogo Conectores Não Certificados](media/desktop-connector-extensibility/data-extension-security-2.png)

Para resolver o erro, pode alterar a definição de segurança **Extensões de Dados** ou remover os conectores não certificados da pasta *Conectores Personalizados*.

## <a name="certified-connectors"></a>Conectores certificados

Um subconjunto limitado de extensões de dados é considerado *certificado*. Apesar de distribuir os conectores, a Microsoft não é responsável pelo respetivo desempenho ou funcionamento contínuo. O programador de terceiros que criou o conector é responsável pela respetiva manutenção e suporte. 

No Power BI Desktop, os conectores de terceiros certificados aparecem na lista na caixa de diálogo **Obter Dados**, juntamente com conectores comuns e genéricos. Não precisa de ajustar as definições de segurança para utilizar conectores certificados.

Se pretender que um conector personalizado seja certificado, peça ao seu fornecedor que contacte dataconnectors@microsoft.com.
