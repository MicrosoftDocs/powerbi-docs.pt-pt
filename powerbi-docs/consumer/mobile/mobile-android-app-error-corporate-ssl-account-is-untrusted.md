---
title: Corrigir o erro “O certificado SSL empresarial não é fidedigno”
description: Quando iniciar sessão na aplicação Android do Power BI, pode ver a mensagem, "Não foi possível autenticar porque o seu certificado SSL empresarial não é fidedigno
.": ''
author: paulinbar
manager: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 08/28/2019
ms.author: mshenhav
ms.openlocfilehash: 19bcdf08d4eacff5e080bf1a2f987ea848e4bfb9
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/16/2019
ms.locfileid: "70840915"
---
# <a name="fixing-corporate-ssl-certificate-is-untrusted---power-bi"></a>Corrigir “O certificado SSL empresarial não é fidedigno” – Power BI
Quando iniciar sessão na aplicação móvel Android do Microsoft Power BI, pode ver a mensagem "Não foi possível autenticar porque o seu certificado SSL empresarial não é fidedigno para este dispositivo. Contacte o administrador de TI da empresa”. 

As medidas a tomar dependem normalmente do sistema operativo do dispositivo Android, mas existem alguns outros problemas que podem causar este erro.

## <a name="on-android-7-or-later"></a>No Android 7 ou versões posteriores
Procure uma atualização para uma aplicação com o nome **Chrome**e instale a atualização.

## <a name="on-android-6-and-earlier"></a>No Android 6 e versões anteriores
O dispositivo poderá precisar de uma versão atualizada do System Webview. Poderá estar instalado no seu dispositivo e só terá de clicar em **Atualizar**.

Se o System Webview não estiver instalado no dispositivo:

1. No dispositivo Android, feche o Power BI.
2. Abra a Google Play Store e procure **System Webview** da Google Inc.
3. Instale-o.
4. Reinicie a aplicação do Power BI e inicie a sessão.

## <a name="time-zone-settings"></a>Definições de fuso horário
As definições de fuso horário no dispositivo poderão estar incorretas. 

Aceda a **Definições** > **Sistema** > **Data e hora** para verificar.

## <a name="custom-authentication-server"></a>Servidor de autenticação personalizada
Se estiver a utilizar um servidor de autenticação personalizada, o certificado SSL no servidor de autenticação empresarial pode não ser válido. Trabalhe em conjunto com o departamento de TI da sua organização para testar a configuração do servidor de autenticação empresarial. Para tal, siga as orientações [neste artigo](https://support.microsoft.com/en-us/help/3203929/using-adal-to-authenticate-from-android-devices-fails-if-additional-ce).

## <a name="next-steps"></a>Próximos passos
* [Transfira a aplicação Android](http://go.microsoft.com/fwlink/?LinkID=544867) da loja de aplicações Android.
* Perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/) 

