---
ms.openlocfilehash: e24218e2a465619fdfbfc279d3cc45370202dd6e
ms.sourcegitcommit: aef57ff94a5d452d6b54a90598bd6a0dd1299a46
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/07/2019
ms.locfileid: "66814872"
---
## <a name="sign-in-account"></a>Conta de início de sessão

Os utilizadores iniciam sessão com uma conta escolar ou profissional. Esta é a **conta da sua organização**. Caso se tenha inscrito numa oferta do Office 365 e não indicou o seu e-mail profissional real, pode ter um aspeto semelhante a nancy@contoso.onmicrosoft.com. A conta é armazenada num inquilino no Azure Active Directory (AAD). Na maioria dos casos, o UPN da sua conta AAD corresponderá ao endereço de e-mail.

## <a name="windows-service-account"></a>Conta de Serviço Windows

O Gateway de dados no local está configurado para utilizar *NT SERVICE\PBIEgwService* para as credenciais de início de sessão do serviço Windows. Por predefinição, tem o direito de Iniciar sessão como um serviço, no contexto do computador em que está a instalar o gateway. Esta não é a mesma conta utilizada para se ligar às origens de dados no local. Esta também não é a conta escolar ou profissional com a qual inicia sessão nos serviços da cloud.

> [!NOTE]
> Se tiver selecionado o modo pessoal, irá configurar a conta de serviço Windows separadamente.

Se ocorrerem problemas de autenticação no servidor proxy, experimente alterar a conta do serviço Windows para uma conta de utilizador do domínio ou conta de serviço gerida. Para obter mais informações, veja [configuração do proxy](../service-gateway-proxy.md#changing-the-gateway-service-account-to-a-domain-user).

## <a name="ports"></a>Portas

O gateway cria uma ligação de saída ao Azure Service Bus. Este comunica com as portas de saída: TCP 443 (predefinição), 5671, 5672 e 9350 a 9354.  O gateway não precisa de portas de entrada.

Recomendamos que adicione os endereços IP a uma lista de permissões, para a sua região de dados, na firewall. Pode transferir a [lista de IPs do Microsoft Azure Datacenter](https://www.microsoft.com/download/details.aspx?id=41653), que é atualizada semanalmente. Em alternativa, pode obter a lista de portas necessárias ao efetuar o [Teste de porta de rede](../service-gateway-onprem-tshoot.md#network-ports-test) na aplicação de gateway de dados no local. O gateway comunica com o Azure Service Bus utilizando o IP em conjunto com o nome de domínio completamente qualificado (FQDN). Se estiver a forçar o gateway para comunicar através de HTTPS, este utiliza estritamente apenas FQDN e não ocorre qualquer comunicação com os endereços IP.


> [!NOTE]
> Os Endereços IP listados na lista de IPs do Azure Datacenter estão em notação CIDR. Por exemplo, 10.0.0.0/24 não significa 10.0.0.0 a 10.0.0.24. Saiba mais sobre a [notação CIDR](http://whatismyipaddress.com/cidr).

Eis uma lista dos nomes de domínio completamente qualificados utilizados pelo gateway.

| Nomes de domínio | Portas de saída | Descrição |  |
|-----------------------------|----------------|--------------------------------------------------------------------------------------------------------------------|---|
| *.download.microsoft.com | 80 | Utilizado para transferir o instalador. Também é utilizado pela aplicação de gateway de dados para verificar a versão e a região do gateway. |  |
| *.powerbi.com | 443 | Utilizado para identificar o cluster do Power BI relevante. |  |
| *.analysis.windows.net | 443 | Utilizado para identificar o cluster do Power BI relevante. |  |
| *.login.windows.net | 443 | Utilizado para autenticar a aplicação de gateway de dados com o Azure Active Directory/OAuth2. |  |
| *.servicebus.windows.net | 5671-5672 | Utilizado para o Advance Message Queuing Protocol (AMQP). |  |
| *.servicebus.windows.net | 443, 9350-9354 | Utilizado por ouvintes no Reencaminhamento do Service Bus por TCP (precisa de 443 para aquisição do token de controlo de acesso). |  |
| *.frontend.clouddatahub.net | 443 | Descontinuado – não é mais necessário. Será removido da documentação que for lançada posteriormente. |  |
| *.core.windows.net | 443 | Utilizado por fluxos de dados no Power BI para escrever dados no Azure Data Lake. |  |
| login.microsoftonline.com | 443 | Utilizado para autenticar a aplicação de gateway de dados com o Azure Active Directory/OAuth2. |  |
| *.msftncsi.com | 443 | Utilizado para testar a conectividade à Internet e quando o serviço Power BI não conseguir aceder ao gateway. |  |
| *.microsoftonline-p.com | 443 | Utilizado para autenticar a aplicação de gateway de dados com o Azure Active Directory/OAuth2. |  |
| | |

> [!NOTE]
> Assim que o gateway for instalado e registado, as únicas portas/endereços IP necessários serão aqueles de que o Azure Service Bus precisar (ver servicebus.windows.net acima). Pode obter a lista de portas necessárias ao efetuar o [Teste de porta de rede](../service-gateway-onprem-tshoot.md#network-ports-test) na aplicação de gateway de dados no local.

## <a name="forcing-https-communication-with-azure-service-bus"></a>Forçar a comunicação HTTPS com o Azure Service Bus

Pode forçar o gateway a comunicar com o Azure Service Bus através de HTTPS, em vez de TCP direto.

> [!NOTE]
> A partir da versão de junho de 2019, as novas instalações (e não atualizações) passam a utilizar por predefinição o protocolo HTTPS em vez de TCP, com base nas recomendações do Azure Service Bus.

Para forçar a comunicação através de HTTPS, modifique o ficheiro *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config* ao alterar o valor de `AutoDetect` para `Https`, conforme mostrado no fragmento de código logo a seguir a este parágrafo. Este ficheiro está localizado, por predefinição, em *C:\Programas\Gateway de dados no local*.

```xml
<setting name="ServiceBusSystemConnectivityModeString" serializeAs="String">
    <value>Https</value>
</setting>
```

O valor do parâmetro *ServiceBusSystemConnectivityModeString* é sensível a maiúsculas e minúsculas. Os valores válidos são *AutoDetect* e *Https*.

Em alternativa, pode forçar o gateway a adotar este comportamento ao utilizar a interface de utilizador do gateway. Na interface de utilizador do gateway, selecione **Rede**e mude o **modo de conectividade Azure Service Bus** para **Ativado**.

![](./media/gateway-onprem-accounts-ports-more/gw-onprem_01.png)

Depois da alteração, quando selecionar **Aplicar** (um botão que surge apenas depois de efetuar alterações), o *serviço Windows de gateway* reinicia automaticamente, para que a alteração entre em vigor.

Futuramente, poderá reiniciar o *serviço Windows de gateway* da caixa de diálogo da interface de utilizador ao selecionar **Definições de Serviço** e, em seguida, selecionar *Reiniciar Agora*.

![](./media/gateway-onprem-accounts-ports-more/gw-onprem_02.png)

## <a name="support-for-tls-12"></a>Suporte para TLS 1.2

Por predefinição, o Gateway de dados no local utiliza o TLS (Transport Layer Security) 1.2 para comunicar com o serviço Power BI. Para garantir que todo o tráfego do gateway utiliza o TLS 1.2, poderá ter de adicionar ou modificar as seguintes chaves de registo no computador que executa o serviço de gateway:

```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]"SchUseStrongCrypto"=dword:00000001
[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319]"SchUseStrongCrypto"=dword:00000001
```

> [!NOTE]
> Adicionar ou modificar estas chaves de registo aplica a alteração a todas as aplicações .NET. Para obter informações sobre as alterações de registo que afetam o TLS de outras aplicações, consulte [Definições de registo do TLS (Transport Layer Security)](https://docs.microsoft.com/windows-server/security/tls/tls-registry-settings).

## <a name="how-to-restart-the-gateway"></a>Como reiniciar o gateway

O gateway é executado como um serviço Windows. Pode iniciar e pará-lo como qualquer serviço Windows. Veja como pode fazê-lo na linha de comandos.

1. No computador em que o gateway está em execução, inicie uma linha de comandos de administrador.
2. Use o seguinte comando para parar o serviço.
   
   net stop PBIEgwService
3. Use o seguinte comando para iniciar o serviço.
   
   net start PBIEgwService

