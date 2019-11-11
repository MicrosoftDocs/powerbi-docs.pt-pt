---
title: Extensibilidade de Conectores no Power BI
description: Ferramentas de extensibilidade de conectores, funcionalidades, definições de segurança e conectores certificados
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: e493e4a41e7b357a23677c1c50f654dbee51e0ca
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878406"
---
# <a name="connector-extensibility-in-power-bi"></a>Extensibilidade de conectores no Power BI

Com o Power BI, os clientes e programadores podem expandir as origens de dados às quais se ligam de muitas formas. Estes utilizam conectores existentes e origens de dados genéricas (ex.: ODBC, OData, Oledb, Web, CSV, XML, JSON). Em alternativa, os programadores podem criar extensões de dados, denominadas **Conectores Personalizados**, e torná-las **Conectores Certificados**.

Atualmente, pode ativar os **Conectores Personalizados** através de um menu que lhe permite controlar de forma segura o nível de código personalizado que pretende que seja executado no seu sistema. Pode escolher todos os conectores personalizados ou apenas conectores certificados e distribuídos pela Microsoft na caixa de diálogo **Obter Dados**.

## <a name="custom-connectors"></a>Conectores personalizados

Os **Conectores Personalizados** podem incluir uma vasta seleção de possibilidades, desde pequenas APIs importantes para a sua empresa até grandes serviços específicos da indústria para os quais a Microsoft não lançou um conector. Muitos conectores são distribuídos pelos fornecedores. Se precisar de um conector de dados específico, deve contactar um fornecedor.

Para utilizar um **Conector Personalizado**, coloque-o na pasta *\[Documentos\\Power BI Desktop\\Conectores Personalizados* e ajuste as definições de segurança como descrito na secção seguinte.

Não precisa de ajustar as definições de segurança para utilizar **Conectores Certificados**.

## <a name="data-extension-security"></a>Segurança da extensão de dados

Para alterar as definições de segurança da extensão de dados no **Power BI Desktop**, selecione **Ficheiro > Opções e definições > Opções > Segurança**.

![Controlar o carregamento de conectores personalizados com as opções de Segurança da Extensão de Dados](media/desktop-connector-extensibility/data-extension-security-1.png)

Em **Extensões de Dados** pode optar entre dois níveis de segurança:

* (Recomendado) Permitir apenas o carregamento de extensões certificadas
* (Não Recomendado) Permitir o carregamento de qualquer extensão sem validação ou aviso

Se planeia utilizar **Conectores Personalizados** ou conectores desenvolvidos por si ou por terceiros, selecione **"(Não Recomendado) Permitir o carregamento de qualquer extensão sem validação ou aviso"** . Não recomendamos esta definição de segurança, a menos que confie plenamente nos seus Conectores Personalizados, pois o respetivo código pode processar credenciais, incluindo enviá-las através de HTTP e ignorar os níveis de privacidade.

Na definição de segurança **"(Recomendado)"** , se existirem conectores personalizados no seu sistema, será apresentada a seguinte mensagem de erro: "O seguinte conector não foi certificado e não conseguimos verificar se está seguro para utilizar". Junto à mensagem, segue-se uma lista de conectores que não podem ser carregados em segurança.

![Uma caixa de diálogo irá descrever os Conectores Personalizados que não podem ser carregados devido às definições de segurança, neste caso a TripPin.](media/desktop-connector-extensibility/data-extension-security-2.png)

Para resolver o erro sem alterar as definições de segurança, remova os conectores não atribuídos da pasta "Conectores Personalizados".

Para resolver o erro e utilizar esses conectores, altere as suas definições de segurança para **"(Não Recomendado) Permitir o carregamento de qualquer extensão sem validação ou aviso"** , como descrito anteriormente. Em seguida, reinicie o **Power BI Desktop**.

## <a name="certified-connectors"></a>Conectores certificados

Um subconjunto limitado de extensões de dados é considerado **Certificado**. Aceda aos conectores certificados na caixa de diálogo **Obter Dados**. No entanto, o programador de terceiros que criou o conector é responsável pela respetiva manutenção e suporte. Apesar de distribuir os conectores, a Microsoft não é responsável pelo respetivo desempenho ou funcionamento contínuo.

Se pretender que um conector personalizado seja certificado, peça ao seu fornecedor que contacte a dataconnectors@microsoft.com.
