---
title: Criar certificados SSL para elementos visuais do Power BI
description: Saiba como gerar certificados SSL com as Ferramentas dos Elementos Visuais do Power BI no Windows, Mac ou Linux, ou manualmente.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 05/08/2020
ms.openlocfilehash: 37bd8f15dcf17cd0f967e819338a719edf2a3054
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83276381"
---
# <a name="create-an-ssl-certificate"></a>Criar um certificado SSL

Este artigo descreve como gerar e instalar certificados Secure Sockets Layer (SSL) para elementos visuais do Power BI.

Para os procedimentos do Windows, macOS X e Linux, deve ter o pacote **pbiviz** das Ferramentas dos Elementos Visuais do Power BI instalado. Para obter mais informações, veja [Configurar o ambiente de programador](https://docs.microsoft.com/power-bi/developer/visuals/custom-visual-develop-tutorial#setting-up-the-developer-environment). 

## <a name="create-a-certificate-on-windows"></a>Criar um certificado no Windows

Para gerar um certificado com o cmdlet `New-SelfSignedCertificate` do PowerShell no Windows 8 e superior, execute o seguinte comando:

```powershell
pbiviz --install-cert
```

Para o Windows 7, a ferramenta `pbiviz` requer que o utilitário OpenSSL esteja disponível na linha de comandos. Para instalar o OpenSSL, aceda a [OpenSSL](https://www.openssl.org) ou [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries).

Para obter mais informações e instruções para a instalação de um certificado, veja [Criar e instalar um certificado para o Windows](https://docs.microsoft.com/power-bi/developer/visuals/custom-visual-develop-tutorial#windows).

## <a name="create-a-certificate-on-macos-x"></a>Criar um certificado no macOS X

O utilitário OpenSSL está normalmente disponível no sistema operativo macOS X.

Também pode instalar o utilitário OpenSSL ao executar um dos seguintes comandos:

- A partir do gestor de pacotes *Brew*:
  
  ```cmd
  brew install openssl
  brew link openssl --force
  ```

- Através do *MacPorts*:
  
  ```cmd
  sudo port install openssl
  ```

Após a instalação do utilitário OpenSSL, execute o seguinte comando para gerar um novo certificado:

```cmd
pbiviz --install-cert
```

Para obter mais informações e instruções, veja [Criar e instalar um certificado para o OS X](https://docs.microsoft.com/power-bi/developer/visuals/custom-visual-develop-tutorial#osx).

## <a name="create-a-certificate-on-linux"></a>Criar um certificado no Linux

O utilitário OpenSSL está normalmente disponível no sistema operativo Linux.

Antes de começar, execute os seguintes comandos para confirmar que `openssl` e `certutil` estão instalados:

```sh
which openssl
which certutil
```

Se `openssl` e `certutil` não estiverem instalados, instale os utilitários `openssl` e `libnss3`.

### <a name="create-the-ssl-configuration-file"></a>Criar o ficheiro de configuração SSL

Crie um ficheiro chamado */tmp/openssl.cnf* que contenha o seguinte texto:

```
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName = @alt_names

[ alt_names ]
DNS.1=localhost
```

### <a name="generate-root-certificate-authority"></a>Gerar a autoridade de certificação de raiz

Para gerar a autoridade de certificação (AC) de raiz para assinar certificados locais, execute os seguintes comandos:

```sh
touch $HOME/.rnd
openssl req -x509 -nodes -new -sha256 -days 1024 -newkey rsa:2048 -keyout /tmp/local-root-ca.key -out /tmp/local-root-ca.pem -subj "/C=US/CN=Local Root CA/O=Local Root CA"
openssl x509 -outform pem -in /tmp/local-root-ca.pem -out /tmp/local-root-ca.crt
```

### <a name="generate-a-certificate-for-localhost"></a>Gerar um certificado para localhost 

Para gerar um certificado para `localhost` com a AC gerada e o *openssl.cnf*, execute os seguintes comandos:

```sh
PBIVIZ=`which pbiviz`
PBIVIZ=`dirname $PBIVIZ`
PBIVIZ="$PBIVIZ/../lib/node_modules/powerbi-visuals-tools/certs"
# Make sure that $PBIVIZ contains the correct certificate directory path. ls $PBIVIZ should list 'blank' file.
openssl req -new -nodes -newkey rsa:2048 -keyout $PBIVIZ/PowerBIVisualTest_private.key -out $PBIVIZ/PowerBIVisualTest.csr -subj "/C=US/O=PowerBI Visuals/CN=localhost"
openssl x509 -req -sha256 -days 1024 -in $PBIVIZ/PowerBIVisualTest.csr -CA /tmp/local-root-ca.pem -CAkey /tmp/local-root-ca.key -CAcreateserial -extfile /tmp/openssl.cnf -out $PBIVIZ/PowerBIVisualTest_public.crt
```

### <a name="add-root-certificates"></a>Adicionar certificados de raiz

Para adicionar um certificado de raiz à base de dados do browser Chrome, execute:

```sh
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:$HOME/.pki/nssdb
```

Para adicionar um certificado de raiz à base de dados do browser Mozilla Firefox, execute:

```sh
for certDB in $(find $HOME/.mozilla* -name "cert*.db")
do
certDir=$(dirname ${certDB});
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:${certDir}
done
```

Para adicionar um certificado de raiz em todo o sistema, execute:

```sh
sudo cp /tmp/local-root-ca.pem /usr/local/share/ca-certificates/
sudo update-ca-certificates
```

### <a name="remove-root-certificates"></a>Remover certificados de raiz

Para remover um certificado de raiz, execute:

```sh
sudo rm /usr/local/share/ca-certificates/local-root-ca.pem
sudo update-ca-certificates --fresh
```

## <a name="generate-a-certificate-manually"></a>Gerar um certificado manualmente

Também pode gerar um certificado SSL manualmente com o OpenSSL. Pode especificar quaisquer ferramentas para gerar os certificados.

Se o utilitário OpenSSL já estiver instalado, poderá gerar um novo certificado ao executar:

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBIVisualTest_private.key -out PowerBIVisualTest_public.crt -days 365
```

Normalmente, pode encontrar os certificados do servidor Web `PowerBI-visuals-tools` ao executar um dos seguintes comandos:

- Para a instância global das ferramentas:
  
  ```cmd
  %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
  ```

- Para a instância local das ferramentas:
  
  ```cmd
  <Power BI visual project root>\node_modules\PowerBI-visuals-tools\certs
  ```

### <a name="pem-format"></a>Formato PEM

Se utilizar o formato de certificado Privacy Enhanced Mail (PEM), guarde o ficheiro do certificado como *PowerBIVisualTest_public.crt* e guarde a chave privada como *PowerBIVisualTest_private.key*.

### <a name="pfx-format"></a>Formato PFX

Se utilizar o formato de certificado Personal Information Exchange (PFX), guarde o ficheiro do certificado como *PowerBIVisualTest_public.pfx*.

Se o ficheiro de certificado PFX exigir uma frase de acesso:

1. No ficheiro de configuração, especifique:
   
   ```cmd
   \PowerBI-visuals-tools\config.json
   ```
   
1. Na secção `server`, especifique a frase de acesso ao substituir o marcador de posição \<A SUA FRASE DE ACESSO:

    ```cmd
    "server":{
        "root":"webRoot",
        "assetsRoute":"/assets",
        "privateKey":"certs/PowerBIVisualTest_private.key",
        "certificate":"certs/PowerBIVisualTest_public.crt",
        "pfx":"certs/PowerBIVisualTest_public.pfx",
        "port":"8080",
        "passphrase":"<YOUR PASSPHRASE>"
    }
    ```

## <a name="next-steps"></a>Próximos passos
- [Desenvolver um elemento visual do Power BI](custom-visual-develop-tutorial.md)
- [Exemplos de elementos visuais do Power BI](samples.md)
- [Publicar elementos visuais do Power BI no AppSource](office-store.md)
