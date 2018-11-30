---
title: Início de sessão único na aplicação móvel do Power BI para Windows
description: Leia mais sobre o início de sessão único (SSO) na aplicação móvel do Power BI para Windows. SSO significa que tem acesso a todas as aplicações e recursos de que precisa para trabalhar ao iniciar sessão apenas uma vez, com uma única conta de utilizador.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 09/17/2018
ms.author: maggies
ms.openlocfilehash: f13b6e0a6583bcb66da0fb0a27188c83c4bf6806
ms.sourcegitcommit: 698b788720282b67d3e22ae5de572b54056f1b6c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/17/2018
ms.locfileid: "45975041"
---
# <a name="single-sign-on-in-the-power-bi-mobile-windows-app"></a>Início de sessão único na aplicação móvel do Power BI para Windows

Leia mais sobre o início de sessão único (SSO) na aplicação móvel do Power BI para Windows. SSO significa que tem acesso a todas as aplicações e recursos de que precisa para trabalhar ao iniciar sessão apenas uma vez, com uma única conta de utilizador. Depois de iniciar sessão, pode aceder a todas as essas aplicações sem ter de fazer uma nova autenticação. 

Como a aplicação do Power BI para Windows está integrada no Azure Active Directory, pode utilizar a sua conta profissional primária, não só para iniciar sessão nos dispositivos associados a um domínio, mas também para iniciar sessão no serviço Power BI. Se estiver a ver o Power BI num Windows Phone, certifique-se de que a conta que utiliza para o Power BI está configurada como uma conta escolar ou profissional nas definições do dispositivo.  

O SSO está ativado apenas para dispositivos Windows geridos pelo Windows Azure Active Directory. 

## <a name="sign-in-with-sso"></a>Iniciar sessão com SSO

Para simplificar o processo de início de sessão, a aplicação tenta automaticamente autenticar o utilizador no serviço Power BI através do SSO quando instalar a aplicação pela primeira vez. Só se este processo não for bem-sucedido é que a aplicação lhe pede para fornecer as suas credenciais do Power BI.  

Se já estiver a utilizar a aplicação móvel do Power BI para Windows, também pode utilizar o SSO quando atualizar para a nova versão da aplicação. Termine a sessão na aplicação, feche-a e volte a abri-la. Quando a aplicação volta a abrir, esta tenta automaticamente utilizar as suas credenciais atuais do Windows para fazer a autenticação no serviço Power BI. 

Se não quiser utilizar as suas credenciais de sessão ativa atual do Windows para iniciar sessão no Power BI, basta aceder a **Definições**, terminar sessão e iniciar sessão com outras credenciais. 
 
## <a name="next-steps"></a>Passos seguintes

- [Introdução à aplicação móvel Power BI para Windows 10](mobile-windows-10-phone-app-get-started.md)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
