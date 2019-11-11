---
title: Criar um certificado SSL
description: Descubra alternativas às instruções para criar certificados manualmente para o servidor de programação
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: d24135cc55ebc8cdfd2a1279cb2a2a46f8f0bc3e
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880189"
---
# <a name="create-an-ssl-certificate"></a>Criar um certificado SSL

Este artigo descreve como criar um certificado SSL.

Para gerar o certificado ao utilizar o cmdlet `New-SelfSignedCertificate` do PowerShell no Windows 8 ou superior, execute o seguinte comando:

```cmd
pbiviz --create-cert
```

A ferramenta necessita de uma instalação do OpenSSL para o Windows 7. O utilitário OpenSSL tem de estar disponível a partir da linha de comandos.

Para instalar o OpenSSL, aceda aos sites [OpenSSL](https://www.openssl.org) ou [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries).



## <a name="create-a-certificate-mac-os-x"></a>Criar um certificado (Mac OS X)

Normalmente, o utilitário OpenSSL está disponível nos sistemas operativos Linux ou Mac OS X.

Também pode instalar o utilitário ao executar um dos seguintes comandos:
* A partir do gestor de pacotes *Brew*:

    ```cmd
    brew install openssl
    brew link openssl --force
    ```

* Através do *MacPorts*:

    ```cmd
    sudo port install openssl
    ```

Após a instalação do OpenSSL, para gerar uma nova chamada ao certificado, execute o seguinte comando:

```cmd
pbiviz --create-cert
```

## <a name="create-a-certificate-linux"></a>Criar um certificado (Linux)

Se o utilitário OpenSSL não estiver disponível no seu sistema operativo Linux, pode instalá-lo através de um dos seguintes comandos:

* Para o gestor de pacotes *APT*:

    ```cmd
    sudo apt-get install openssl
    ```

* Para o *Yellowdog Updater*:

    ```cmd
    yum install openssl
    ```

* Para o *Redhat Package Manager*:

    ```cmd
    rpm install openssl
    ```

Se o utilitário OpenSSL já estiver disponível no seu sistema operativo, pode gerar um novo certificado ao executar o seguinte comando:

```cmd
pbiviz --create-cert
```

Em alternativa, pode obter o utilitário OpenSSL através dos sites [OpenSSL](https://www.openssl.org) ou [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries).

## <a name="generate-the-certificate-manually"></a>Gerar o certificado manualmente

Pode especificar que os seus certificados sejam gerados por qualquer ferramenta.

Se o utilitário OpenSSL já estiver instalado no sistema, pode gerar um novo certificado ao executar os seguintes comandos:

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

Normalmente, pode encontrar os certificados de servidor Web PowerBI-visuals-tools ao executar um dos seguintes procedimentos:

* Para a instância global das ferramentas:

    ```cmd
    %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
    ```

* Para a instância local das ferramentas:

    ```cmd
    <custom visual project root>\node_modules\PowerBI-visuals-tools\certs
    ```

Se utilizar o formato PEM, guarde o ficheiro de certificado como *PowerBICustomVisualTest_public.crt* e guarde a chave privada como *PowerBICustomVisualTest_public.key*.

Se utilizar o formato PFX, guarde o ficheiro de certificado como *PowerBICustomVisualTest_public.pfx*.

Se o ficheiro de certificado PFX exigir uma frase de acesso, faça o seguinte:
1. No ficheiro de configuração, especifique:

    ```cmd
    \PowerBI-visuals-tools\config.json
    ```

1. Na secção `server`, especifique a frase de acesso ao substituir o marcador de posição "*A SUA FRASE DE ACESSO*":

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
