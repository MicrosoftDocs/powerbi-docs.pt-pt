---
title: ficheiro de inclusão
description: ficheiro de inclusão
services: powerbi
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 04/28/2020
ms.author: davidi
ms.openlocfilehash: d56988986cfd994bb21c9bc25d024903719472cf
ms.sourcegitcommit: c772c544ce2e1e2a147b9b62e5579ac3cb59d54c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/29/2020
ms.locfileid: "82255834"
---
## <a name="single-sign-on"></a>Início de sessão único

Depois de publicar um conjunto de dados DirectQuery do SQL do Azure no serviço, pode ativar o início de sessão único (SSO) com o OAuth2 do Azure Active Directory (Azure AD) para os utilizadores finais.

Para ativar o SSO, aceda às definições do conjunto de dados, abra o separador **Origens de Dados** e selecione a caixa SSO.

![Configurar a caixa de diálogo DQ do SQL do Azure](media/direct-query-sso/sso-dialog.png)

Quando a opção SSO está ativada e os utilizadores acedem aos relatórios compilados por cima da origem de dados, o Power BI envia as suas credenciais autenticadas do Azure AD nas consultas para a base de dados SQL do Azure ou armazém de dados. Esta opção permite que o Power BI respeite as definições de segurança configuradas ao nível da origem de dados.

A opção SSO tem efeito em todos os conjuntos de dados que utilizam esta origem de dados. Não afeta o método de autenticação utilizado para os cenários de importação.

