---
title: Clientes dedicados do Office 365 - problemas conhecidos
description: "Suporte para clientes dedicados do Office 365 - problemas conhecidos. Este tópico descreve problemas específicos a um cliente Dedicado do Office 365. Isso inclui limitações à funcionalidade de grupo, bem como à aplicação do iPhone com domínios intuitivos."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 06/28/2017
ms.author: asaxton
ms.openlocfilehash: 8ee54e64ecbb72354a70a2aeb1d8fda87b3b876b
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="office-365-dedicated-customers---known-issues"></a>Clientes dedicados do Office 365 - problemas conhecidos
Agora há suporte para o Power BI para clientes do Office 365 Dedicado.  Se for um cliente do O365 Dedicado, pode entrar com uma conta de inquilino e utilizar o Power BI. Há dois problemas conhecidos no momento.

## <a name="groups"></a>Grupos
Ao selecionar **Membros** ou **Calendário** no menu de contexto de Grupo, é redirecionado para a aplicação Correio.  Os **Ficheiros** e **Conversas** funcionam como esperado.

![](media/service-admin-office-365-dedicated-known-issues/group-menu.png)

## <a name="iphone-app---sign-in-with-vanity-domain-leads-to-error"></a>Aplicação do iPhone - entrar com domínio banido causa erros
Quando se liga na aplicaçao do iPhone, com um início de sessão com um domínio banido, pode encontrar um erro.

*Erro no Início de Sessão*  
*ocorreu um erro interno inesperado. Tente novamente.*

Para contornar o problema, inicie a sessão com o endereço de e-mail listado quando clica no ícone do utilizador no serviço Power BI, em vez de com o domínio intuitivo.

![](media/service-admin-office-365-dedicated-known-issues/sign-in-address.png)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)
