---
title: Extensibilidade de Conectores no Power BI
description: Ferramentas de extensibilidade de conectores, funcionalidades, definições de segurança e conectores certificados
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 16b96d91a9dd37fa8a502bbcca772438c703cb63
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66413000"
---
# <a name="connector-extensibility-in-power-bi"></a>Extensibilidade de conectores no Power BI

No Power BI, os clientes e os desenvolvedores podem estender as origens de dados aos quais estabelecem ligação de várias maneiras. Eles usam conectores existentes e as origens de dados genéricos (por exemplo, ODBC, OData, Oledb, Web, CSV, XML, JSON). Em alternativa, os programadores criar extensões de dados, conhecidas como **conectores personalizados**e torná-los **Certified conectores**.

Atualmente, ative **conectores personalizados** utilizando um menu que lhe permita em segurança a controlar o nível de código personalizado, deseja permitir que executar no seu sistema. Pode escolher todos os conectores personalizados ou apenas os conectores certified e distribuídas pela Microsoft na **obter dados** caixa de diálogo.

## <a name="custom-connectors"></a>Conectores personalizados

**Conectores personalizados** pode incluir um vasto leque de possibilidades, desde pequenas APIs críticas para o seu negócio, para os serviços específicos da indústria grandes que a Microsoft ainda não lançado um conector para. Muitos conetores são distribuídos pelo fornecedor. Se tiver uma necessidade de um conector de dados específicos, deve contactar um fornecedor.

Para utilizar um **conector personalizado**, colocá-lo na  *\[documentos]\\Power BI Desktop\\conectores personalizados* pasta e ajustar as configurações de segurança, conforme descrito em a secção seguinte.

Não precisa de ajustar as definições de segurança para utilizar **Conectores Certificados**.

## <a name="data-extension-security"></a>Segurança da extensão de dados

Para alterar configurações de segurança de extensão de dados, em **Power BI Desktop** selecionar **ficheiro > Opções e definições > Opções > segurança**.

![Controlar se deseja carregar conectores personalizados com opções de segurança de extensão de dados](media/desktop-connector-extensibility/data-extension-security-1.png)

Em **Extensões de Dados** pode optar entre dois níveis de segurança:

* (Recomendado) Permitir apenas o carregamento de extensões certificadas
* (Não Recomendado) Permitir o carregamento de qualquer extensão sem validação ou aviso

Se pretender utilizar **conectores personalizados** ou conectores que desenvolveram ou uma aplicação de terceiros, tem de selecionar **"(Not Recommended) permitir qualquer extensão carregar sem aviso"** . Não recomendamos esta definição de segurança, a menos que confia absolutamente seus conectores personalizados. Uma vez, o código aqui pode lidar com as credenciais, incluindo a enviá-los através de HTTP e ignorar os níveis de privacidade.

Com o **"(recomendado)"** segurança definição, se existem conectores personalizados no seu sistema, obterá um erro que descreve os conectores que não é possível carregar devido à segurança.

![Uma caixa de diálogo descreve conectores personalizados que não é possível carregar devido a definições de segurança, neste TripPin maiúsculas](media/desktop-connector-extensibility/data-extension-security-2.png)

Para resolver o erro e utilizar os conectores, alterar suas configurações de segurança para o **"(Not Recommended) permitir qualquer extensão carregar sem aviso"** definição conforme descrito anteriormente. Em seguida, reinicie **Power BI Desktop**.

## <a name="certified-connectors"></a>Conectores certificados

Um subconjunto limitado das extensões de dados é considerado **Certified**. Acessar os conectores de certificados no **obter dados** caixa de diálogo. No entanto, o desenvolvedor de terceiros que criou o conector é responsável por seu suporte e manutenção. Embora a Microsoft distribui os conectores, não é responsável por seu desempenho ou a função contínua.

Se pretender que um conector personalizado seja certificado, peça ao seu fornecedor que contacte a dataconnectors@microsoft.com.
