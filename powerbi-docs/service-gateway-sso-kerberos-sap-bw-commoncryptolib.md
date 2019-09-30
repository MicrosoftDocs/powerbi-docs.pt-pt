---
title: Usar o início de sessão único Kerberos para SSO no SAP BW com CommonCryptoLib (sapcrypto.dll)
description: Configurar o servidor SAP BW para ativar o SSO a partir do serviço Power BI com CommonCryptoLib (sapcrypto.dll)
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 6c4f2b0d8856d5e68e02b9b33cf393ca85ecb580
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/18/2019
ms.locfileid: "71106291"
---
# <a name="use-kerberos-single-sign-on-for-sso-to-sap-bw-using-commoncryptolib-sapcryptodll"></a>Usar o início de sessão único Kerberos para SSO no SAP BW com CommonCryptoLib (sapcrypto.dll)

Este artigo descreve como configurar o servidor SAP BW para ativar o SSO a partir do serviço Power BI com CommonCryptoLib (sapcrypto.dll).

> [!NOTE]
> Conclua os passos neste artigo, além dos passos em [Configurar SSO do Kerberos](service-gateway-sso-kerberos.md) antes de tentar atualizar um relatório baseado em SAP BW que usa o SSO do Kerberos. Utilizar o CommonCryptoLib como a sua biblioteca SNC permite ligações de SSO a Servidores de Aplicações SAP BW e a Servidores de Mensagens SAP BW.

## <a name="configure-sap-bw-server-to-enable-sso-using-commoncryptolib"></a>Configurar o servidor SAP BW para ativar o SSO com a CommonCryptoLib

> [!NOTE]
> O gateway de dados no local é um software de 64 bits, portanto, requer a versão de 64 bits do CommonCryptoLib (sapcrypto.dll). Se tiver planos para testar a ligação de SSO ao seu servidor SAP BW no GUI do SAP antes de tentar uma ligação SSO através do gateway (recomendado), também precisa da versão de 32 bits do CommonCryptoLib, pois o GUI do SAP é um software de 32 bits.

1. Confirme que o seu servidor BW está configurado corretamente para o SSO do Kerberos com CommonCryptoLib. Se estiver, deverá conseguir utilizar o SSO para aceder ao seu servidor BW (diretamente ou através de um Servidor de Mensagens SAP BW) com uma ferramenta SAP como o GUI do SAP que foi configurado para utilizar o CommonCryptoLib. Para obter mais informações sobre os passos de configuração, veja [SAP Single Sign-On: Authenticate with Kerberos/SPNEGO](https://blogs.sap.com/2017/07/27/sap-single-sign-on-authenticate-with-kerberosspnego/) (Início de Sessão Único do SAP: autenticação com Kerberos/SPNEGO). O seu servidor BW deverá utilizar CommonCryptoLib como a respetiva Biblioteca SNC e ter um nome SNC que comece por "CN=", como "CN=BW1". Para obter mais informações sobre os requisitos de nomes SNC, veja [SNC Parameters for Kerberos Configuration](https://help.sap.com/viewer/df185fd53bb645b1bd99284ee4e4a750/3.0/en-US/360534094511490d91b9589d20abb49a.html) (Parâmetros SNC para Configuração do Kerberos [especificamente, o parâmetro snc/identity/as]).

1. Se ainda não o tiver feito, instale a versão x64 do [SAP .NET Connector](https://support.sap.com/en/product/connectors/msnet.html) no computador onde o gateway foi instalado. Pode verificar se o componente foi instalado ao tentar estabelecer ligação ao seu servidor BW no Power BI Desktop. Se não conseguir estabelecer ligação com a implementação 2.0, significa que o .NET Connector não está instalado.

1. Certifique-se de que o SAP Secure Login Client (SLC) não está em execução no computador onde o gateway está instalado. O SLC coloca os pedidos do Kerberos em cache de uma forma que pode interferir com a capacidade de o gateway utilizar o Kerberos para SSO. Se o SLC estiver instalado, desinstale-o ou certifique-se de que sai do SAP Secure Login Client: clique com o botão direito do rato no ícone do tabuleiro do sistema e selecione "Log Out" (Terminar Sessão) e "Exit" (Sair) antes de tentar estabelecer uma ligação SSO com o gateway. A utilização do SLC não é suportada em computadores com o Windows Server. Para obter mais informações, veja [SAP Note 2780475](https://launchpad.support.sap.com/#/notes/2780475) (Nota do SAP 2780475 [é necessário um utilizador S]).

    ![SAP Secure Login Client](media/service-gateway-sso-kerberos/sap-secure-login-client.png)

    Se desinstalar o SLC ou selecionar **Log Out** (Terminar Sessão) e **Exit** (Sair), abra uma janela cmd e introduza `klist purge` para limpar os pedidos do Kerberos em cache existentes antes de tentar uma ligação SSO através do gateway.

1. Transfira a versão **8.5.25 ou superior** de 64 bits ou superior da CommonCryptoLib (sapcrypto.dll) a partir do SAP Launchpad e copie a mesma para uma pasta no computador do seu gateway. No mesmo diretório para onde copiou o ficheiro sapcrypto.dll, crie um ficheiro com o nome sapcrypto.ini com os seguintes conteúdos:

    ```
    ccl/snc/enable_kerberos_in_client_role = 1
    ```

    O ficheiro .ini contém informações de configuração de que a CommonCryptoLib precisa para ativar o SSO no cenário de gateway.

    > [!NOTE]
    > Estes ficheiros têm de ser armazenados na mesma localização. Por outras palavras, o parâmetro _/path/to/sapcrypto/_ deve conter os ficheiros sapcrypto.ini e sapcrypto.dll.

    O Utilizador de Serviço do gateway e o utilizador do Active Directory (AD) que será representado pelo Utilizador de Serviço necessitam de permissões de leitura e execução para ambos os ficheiros. Recomendamos que conceda permissões nos ficheiros .ini e .dll ao grupo Utilizadores Autenticados. Para fins de teste, também pode conceder explicitamente estas permissões ao Utilizador de Serviço do gateway e ao utilizador do Active Directory que vai servir para os testes. Na captura de ecrã abaixo, concedemos permissões de **Leitura e execução** ao grupo Utilizadores Autenticados para o ficheiro sapcrypto.dll:

    ![Utilizadores autenticados](media/service-gateway-sso-kerberos/authenticated-users.png)

1. Se não tiver uma origem de dados do SAP BW, adicione uma origem de dados na página **Gerir gateways** no serviço Power BI. Se já tiver associado uma origem de dados BW ao gateway pelo qual pretende que a ligação SSO flua, prepare-se para editá-la. Escolha **SAP Business Warehouse** como o **Tipo de Origem de Dados** se quiser criar uma ligação de SSO com um Servidor de Aplicações BW. Selecione o **Servidor de Mensagens SAP Business Warehouse** se quiser criar uma ligação de SSO com um Servidor de Mensagens BW.

    Para **Biblioteca SNC**, selecione **Variável de ambiente SNC\_LIB ou SNC\_LIB\_64** ou **Personalizar**. Se selecionar a opção **SNC\_LIB**, terá de definir o valor da variável de ambiente **SNC\_LIB\_64** no computador do gateway para o caminho absoluto da cópia de 64 bits do ficheiro sapcrypto.dll nesse computador do gateway, por exemplo C:\Users\Test\Desktop\sapcrypto.dll. Se selecionar **Personalizar**, cole o caminho absoluto no ficheiro sapcrypto.dll no campo Caminho da Biblioteca SNC Personalizado que aparece na página **Gerir gateways**. Para o **Nome do Parceiro SNC**, introduza o Nome SNC do servidor BW. Nas **definições Avançadas**, confirme que **Utilizar SSO através de Kerberos para consultas de DirectQuery** está selecionado. Os outros campos devem ser preenchidos como seriam se estivesse a estabelecer uma ligação de Autenticação do Windows a partir do PBI Desktop.

1. Crie uma variável de ambiente de sistema CCL\_PROFILE e aponte-a para o ficheiro sapcrypto.ini:

    ![Variável de ambiente de sistema CCL\_PROFILE](media/service-gateway-sso-kerberos/ccl-profile-variable.png)

    Lembre-se de que os ficheiros sapcrypto .dll e .ini têm de existir na mesma localização. No exemplo apresentado acima, onde o ficheiro sapcrypto.ini se encontra no ambiente de trabalho, o ficheiro sapcrypto.dll também deve estar localizado no ambiente de trabalho.

1. Reinicie o serviço de gateway:

    ![Reiniciar o serviço de gateway](media/service-gateway-sso-kerberos/restart-gateway-service.png)

1. [Executar um relatório do Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>Resolução de problemas

Se não conseguir atualizar o relatório no serviço Power BI, pode utilizar o rastreio de gateways, o rastreio de CPIC e o rastreio de CommonCryptoLib para ajudar a diagnosticar o problema. O rastreio de CPIC e de CommonCryptoLib são produtos do SAP, pelo que a Microsoft não pode fornecer suporte direto para os mesmos. Para os utilizadores do Active Directory a quem for concedido acesso de SSO ao BW, algumas configurações do Active Directory poderão exigir que os utilizadores sejam membros do grupo Administradores no computador onde o gateway foi instalado.

1. **Registos do Gateway:** reproduza o problema, abra a [aplicação de gateway](https://docs.microsoft.com/data-integration/gateway/service-gateway-app), aceda ao separador **Diagnósticos** e selecione **Exportar registos**:

    ![Exportar registos do gateway](media/service-gateway-sso-kerberos/export-gateway-logs.png)

1. **Rastreio de CPIC:** para ativar o rastreio de CPIC, defina duas variáveis de ambiente: CPIC\_TRACE e CPIC\_TRACE\_DIR. A primeira variável define o nível de rastreio e a segunda variável define o diretório do ficheiro de rastreio. O diretório tem de ser uma localização na qual os membros do grupo Utilizadores Autenticados possam escrever. Defina a variável CPIC\_TRACE para 3 e a variável CPIC\_TRACE\_DIR para o diretório no qual pretende que os ficheiros de rastreio sejam escritos.

    ![Rastreio de CPIC](media/service-gateway-sso-kerberos/cpic-tracing.png)

    Reproduza o problema e verifique se a variável CPIC\_TRACE\_DIR contém os ficheiros de rastreio.

1. **Rastreio de CommonCryptoLib:** Ative o rastreio de CommonCryptoLib ao adicionar duas linhas no ficheiro sapcrypto.ini que criou anteriormente:

    ```
    ccl/trace/level=5
    ccl/trace/directory=<drive>:\logs\sectrace
    ```

    Certifique-se de que altera a opção _ccl/trace/directory_ para uma localização na qual os membros do grupo Utilizadores Autenticados possam escrever. Em alternativa, crie um novo ficheiro .ini para alterar este comportamento. No mesmo diretório dos ficheiros sapcrypto.ini e sapcrypto.dll, crie um ficheiro com o nome sectrace.ini e com os conteúdos seguintes. Substitua a opção DIRECTORY por uma localização no seu computador onde o Utilizador Autenticado possa escrever:

    ```
    LEVEL = 5

    DIRECTORY = <drive>:\logs\sectrace
    ```

    Agora, reproduza o problema e verifique se a localização apontada por DIRECTORY contém ficheiros de rastreio. Certifique-se de que desativa o rastreio de CPIC e CCL quando terminar.

    Para obter mais informações sobre o rastreio de CommonCryptoLib, veja [SAP Note 2491573](https://launchpad.support.sap.com/#/notes/2491573) (Nota do SAP 2491573 [é necessário um utilizador S]).

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre o **gateway de dados no local** e o **DirectQuery**, consulte os seguintes recursos:

* [What is an on-premises data gateway?](/data-integration/gateway/service-gateway-getting-started) (O que é um gateway de dados no local?)
* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Origens de dados suportadas pelo DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)
