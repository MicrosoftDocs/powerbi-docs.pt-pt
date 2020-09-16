---
title: ficheiro de inclusão
description: ficheiro de inclusão
services: powerbi
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 04/28/2020
ms.author: davidi
ms.openlocfilehash: ed87101fe7f5fadd24594d53bbd0ffb6f029faa4
ms.sourcegitcommit: 92b033ee7a6e36808371b247b7b41536cee6c2f6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/10/2020
ms.locfileid: "90012855"
---
## <a name="single-sign-on"></a>Início de sessão único

Depois de publicar um conjunto de dados DirectQuery do SQL do Azure no serviço, pode ativar o início de sessão único (SSO) com o OAuth2 do Azure Active Directory (Azure AD) para os utilizadores finais.

Para ativar o SSO, aceda às definições do conjunto de dados, abra o separador **Origens de Dados** e selecione a caixa SSO.

![Configurar a caixa de diálogo DQ do SQL do Azure](media/direct-query-sso/sso-dialog.png)

Quando a opção SSO está ativada e os utilizadores acedem aos relatórios compilados por cima da origem de dados, o Power BI envia as suas credenciais autenticadas do Azure AD nas consultas para a base de dados SQL do Azure ou armazém de dados. Esta opção permite que o Power BI respeite as definições de segurança configuradas ao nível da origem de dados.

A opção SSO tem efeito em todos os conjuntos de dados que utilizam esta origem de dados. Não afeta o método de autenticação utilizado para os cenários de importação.

> [!Note]
> O Multi-Factor Authentication (MFA) do Microsoft Azure não é suportado. Os utilizadores que quiserem utilizar o SSO com o DirectQuery têm de ser excluídos do MFA.
