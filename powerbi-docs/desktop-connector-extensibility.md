---
title: Extensibilidade de Conectores no Power BI
description: Ferramentas de extensibilidade de conectores, funcionalidades, definições de segurança e conectores certificados
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/25/2018
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: a5774fe6979516a0fe70364fea5dd91b7a2a48ae
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54275738"
---
# <a name="connector-extensibility-in-power-bi"></a>Extensibilidade de conectores no Power BI

No Power BI, os clientes e os programadores podem expandir as origens de dados às quais se ligam de várias formas, por exemplo, ao utilizar conectores existentes e origens de dados genéricas (como ODBC, OData, Oledb, Web, CSV, XML e JSON). Além dessas origens de dados, os programadores podem criar extensões de dados designadas por **Conectores Personalizados** e certificar um conector para os tornar **Conectores Certificados**.

Atualmente, a capacidade para utilizar **Conectores Personalizados** está ativada com um comutador de funcionalidade. Antes de movermos esta funcionalidade da versão beta para a versão disponível para o público, adicionámos um menu que lhe permite controlar de forma segura o nível de código personalizado que pretende permitir que seja executado no seu sistema: todos os conectores personalizados ou apenas os conectores certificados e distribuídos pela Microsoft na caixa de diálogo **Obter Dados**.

## <a name="custom-connectors"></a>Conectores personalizados

Os **Conectores Personalizados** podem incluir uma vasta seleção de possibilidades, desde pequenas APIs que são importantes para o seu negócio, até grandes serviços específicos da indústria para os quais a Microsoft não lançou um conector. Muitos conectores são distribuídos pelos próprios fornecedores e, se precisar de um conector de dados específico, deverá contactar um fornecedor.

Para utilizar um **Conector Personalizado**, coloque-o na pasta *\[Documentos\\Power BI Desktop\\Conectores Personalizados* e ajuste as definições de segurança como descrito na seguinte secção.

Não precisa de ajustar as definições de segurança para utilizar **Conectores Certificados**.

## <a name="data-extension-security"></a>Segurança da extensão de dados

Para alterar as definições de segurança da extensão de dados, no **Power BI Desktop**, selecione **Ficheiro > Opções e Definições > Opções > Segurança**.

![Controlar se pretende conseguir carregar conectores personalizados com as opções de Segurança da Extensão de Dados](media/desktop-connector-extensibility/data-extension-security-1.png)

Em **Extensões de Dados** pode optar entre dois níveis de segurança:

* (Recomendado) Permitir apenas o carregamento de extensões certificadas
* (Não Recomendado) Permitir o carregamento de qualquer extensão sem validação ou aviso

Se estiver a planear utilizar **Conectores Personalizados** ou conectores desenvolvidos e distribuídos por si ou por terceiros, tem de selecionar **"(Não Recomendado) Permitir o carregamento de qualquer extensão sem validação ou aviso"**. Não recomendamos essa definição de segurança a não ser que confie nos seus Conectores Personalizados, uma vez que o código é capaz de utilizar credenciais (incluindo o envio através de HTTP) e ignorar níveis de privacidade.

Na definição de segurança **"(Recomendado)"**, se existirem conectores personalizados no seu sistema, será apresentado um erro a descrever os conectores que não podem ser carregados devido à segurança.

![Uma caixa de diálogo irá descrever os Conectores Personalizados que não podem ser carregados devido às definições de segurança, neste caso, TripPin](media/desktop-connector-extensibility/data-extension-security-2.png)

Para corrigir o erro e utilizar esses conectores, tem de alterar as suas definições de segurança para a definição **"(Não Recomendado)"** como descrito anteriormente e reiniciar o **Power BI Desktop**.

## <a name="certified-connectors"></a>Conectores certificados

Um subconjunto limitado de extensões de dados é considerado **Certificado** e tais conectores certificados estão disponíveis ao utilizar a caixa de diálogo **Obter Dados**. Porém, a parte responsável pela manutenção e suporte continua a ser a empresa de programadores terceiros que criou o conector. Apesar de distribuir estes conectores, a Microsoft não é responsável pelo respetivo desempenho ou funcionalidade continuada.

Se pretender que um conector personalizado seja certificado, peça ao seu fornecedor que contacte a dataconnectors@microsoft.com.
