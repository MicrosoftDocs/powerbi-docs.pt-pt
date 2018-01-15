## <a name="firewall-or-proxy"></a>Firewall ou Proxy
Para obter informações sobre o fornecimento informações de proxy para o gateway, veja [Configurar definições de proxy para os gateways do Power BI](../service-gateway-proxy.md).

Pode testar para ver se a firewall, ou o proxy, podem estar a bloquear ligações, executando [Test-NetConnection](https://technet.microsoft.com/library/dn372891.aspx) a partir de uma linha de comandos do PowerShell. Isto irá testar a conectividade do Azure Service Bus. Testa apenas a conectividade de rede e não tem nada a ver com o serviço do servidor na cloud ou com o gateway. Ajuda a determinar se a máquina consegue realmente aceder à Internet.

    Test-NetConnection -ComputerName watchdog.servicebus.windows.net -Port 9350

> [!NOTE]
> Test-NetConnection só está disponível no Windows Server 2012 R2 e posterior. Também está disponível no Windows 8.1 e posterior. Em versões de SO anteriores, pode utilizar o Telnet para testar a conectividade de porta.
> 
> 

Os resultados devem ser semelhante ao seguinte. A diferença será com TcpTestSucceeded. Se **TcpTestSucceeded** não for *verdadeiro*, pode estar bloqueado por uma firewall.

    ComputerName           : watchdog.servicebus.windows.net
    RemoteAddress          : 70.37.104.240
    RemotePort             : 5672
    InterfaceAlias         : vEthernet (Broadcom NetXtreme Gigabit Ethernet - Virtual Switch)
    SourceAddress          : 10.120.60.105
    PingSucceeded          : False
    PingReplyDetails (RTT) : 0 ms
    TcpTestSucceeded       : True

Se pretender ser exaustivo, substitua os valores de **ComputerName** e **Porta** pelos valores listados em [portas](../service-gateway-onprem.md#ports)

A firewall também pode estar a bloquear as ligações estabelecidas pelo Azure Service Bus para os datacenters do Azure. Se for esse o caso, poderá ser útil colocar na lista branca (desbloquear) os endereços IP da sua região para esses datacenters. Pode obter uma lista de endereços IP do Azure [aqui](https://www.microsoft.com/download/details.aspx?id=41653).

