---
title: Creating SSL certificate (Criar um certificado SSL)
description: Descubra alternativas às instruções para criar certificados manualmente para o servidor de programação
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: 3287e8a7eb1c36c3f0d8a1fc24faa0442de2dddf
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425442"
---
# <a name="creating-ssl-certificate"></a>Creating SSL certificate (Criar um certificado SSL)

Execute o seguinte comando para gerar o certificado ao utilizar o cmdlet New-SelfSignedCertificate do PowerShell no Windows 8 ou superior.

A ferramenta requer a instalação do OpenSSL para o **Windows** **7**. O utilitário `openssll` tem de estar disponível a partir da linha de comandos.

Para instalar o OpenSSL, aceda a [https://www.openssl.org](https://www.openssl.org) ou a [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries)

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-mac-os-x"></a>Criar certificado (Mac OS X)

Normalmente, os utilitários OpenSSL estão disponíveis nos sistemas operativos Linux ou Mac OS X.

Caso contrário, pode instalá-los através do

gestor de pacotes *Brew*

```cmd
brew install openssl
brew link openssl --force
```

ou através do gestor de pacotes *MacPorts*

```cmd
sudo port install openssl
```

Após a instalação do OpenSSL, para gerar uma nova chamada ao certificado:

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-linux"></a>Criar certificado (Linux)

Se os utilitários OpenSSL não estiverem disponíveis no seu sistema operativo Linux, pode instalá-los através dos seguintes comandos.

Para o gestor de pacotes *APT*:

```cmd
sudo apt-get install openssl
```

Para o *Yellowdog Updater*:

```cmd
yum install openssl
```

Para o *Redhat Package Manager*:

```cmd
rpm install openssl
```

Se o OpenSSL já estiver disponível no seu sistema operativo, efetue a chamada

```cmd
pbiviz --create-cert
```

para gerar um novo certificado.

Caso contrário, obtenha-o em [https://www.openssl.org](https://www.openssl.org) ou em [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries)

## <a name="generate-certificate-manually"></a>Gerar um certificado manualmente

Pode especificar os seus certificados gerados por qualquer ferramenta.

Se tiver o OpenSSL instalado no seu sistema, pode executar o seguinte comando para gerar um novo certificado

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

Normalmente, os certificados de servidor Web PowerBI-visuals-tools encontram-se em

```cmd
%appdata%\npm\node_modules\PowerBI-visuals-tools\certs
```

para a instância global das ferramentas

ou

```cmd
<custom visual project root>\node_modules\PowerBI-visuals-tools\certs
```

para a instância local das ferramentas.

Deve guardar o ficheiro de certificado como `PowerBICustomVisualTest_public.cer` e a chave privada como `PowerBICustomVisualTest_public.key` se utilizar o formato PEM.
Guarde o ficheiro de certificado como `PowerBICustomVisualTest_public.pfx`, se utilizar o formato PFX.

Se o seu ficheiro de certificado PFX exigir uma frase de acesso, deverá especificá-la

```cmd
\PowerBI-visuals-tools\config.json
```

na secção "server":

```cmd
"server":{
    "root":"webRoot",
    "assetsRoute":"/assets",
    "privateKey":"certs/PowerBICustomVisualTest_private.key",
    "certificate":"certs/PowerBICustomVisualTest_public.crt",
    "pfx":"certs/PowerBICustomVisualTest_public.pfx",
    "port":"8080",
    "passphrase":"YOUR PASSPHRASE"
}
```
