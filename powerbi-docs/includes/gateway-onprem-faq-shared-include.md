## <a name="general"></a>Geral
**Pergunta:** Como se chama realmente o serviço Windows?  
**Resposta:** O gateway é chamado Serviço de gateway de dados no local em Serviços

**Pergunta:** Quais são os requisitos do gateway?  
**Resposta:** Consulte a secção de requisitos do principal [artigo sobre gateways](../service-gateway-onprem.md).

**Pergunta:** Que origens de dados são suportadas com o gateway?  
**Resposta:** Veja a tabela de origens de dados no principal [artigo sobre gateways](../service-gateway-onprem.md).

**Pergunta:** É necessário um gateway para origens de dados na cloud, como a Base de Dados SQL do Azure?  
**Resposta:** Não. O serviço conseguirá ligar a essa origem de dados sem um gateway.

**Pergunta:** Existem ligações de entrada para o gateway a partir da cloud?  
**Resposta:** Não. O gateway utiliza ligações de saída para o Azure Service Bus.

**Pergunta:** E se eu bloquear ligações de saída? O que preciso de abrir?  
**Resposta:** Veja a [lista de portas](../service-gateway-onprem.md#ports) e os anfitriões que o gateway utiliza.

**Pergunta:** O gateway tem de ser instalado no mesmo computador da origem de dados?  
**Resposta:** Não. O gateway irá ligar à origem de dados com as informações de ligação que foram fornecidas. Pense no gateway como uma aplicação cliente neste sentido. Terá apenas de conseguir ligar ao nome do servidor que foi fornecido.

**Pergunta:** Qual é a latência para a execução de consultas para uma origem de dados a partir do gateway? Qual é a melhor arquitetura?  
**Resposta:** É recomendado ter o gateway o mais perto possível da origem de dados para evitar a latência da rede. Se puder instalar o gateway na própria origem de dados, irá minimizar a latência introduzida. Considere também os datacenters. Por exemplo, se o serviço estiver a utilizar o datacenter E.U.A. Oeste e tiver o SQL Server alojado numa VM do Azure, deverá ter também a VM do Azure em E.U.A. Oeste. Este procedimento irá minimizar a latência e evitar custos de saída na VM do Azure.

**Pergunta:** Existem requisitos de largura de banda de rede?  
**Resposta:** Recomenda-se que tenha bom débito para a ligação à rede. Cada ambiente é diferente e também depende da quantidade de dados enviados. A utilização do ExpressRoute pode garantir um nível de débito entre os datacenters no local e do Azure.

Pode utilizar a aplicação de terceiros [Azure Speed Test](http://azurespeedtest.azurewebsites.net/) para ajudar a calcular o débito.

**Pergunta:** O serviço Windows do gateway pode ser executado com uma conta do Azure Active Directory?  
**Resposta:** Não. O serviço Windows precisa de uma conta Windows válida. Por predefinição, será executado com o SID de Serviço, *NT SERVICE\PBIEgwService*.

**Pergunta:** Como é que os resultados são enviados de volta para a cloud?  
**Resposta:** Este procedimento é executado através do Azure Service Bus. Para obter mais informações, veja [como funciona](../service-gateway-onprem.md#how-the-gateway-works).

**Pergunta:** Onde estão armazenadas as minhas credenciais?  
**Resposta:** As credenciais que introduz para uma origem de dados são armazenadas de forma encriptada no serviço cloud do gateway. As credenciais são desencriptadas no gateway no local.

**Pergunta:** Posso colocar o gateway numa rede de perímetro (também conhecida como DMZ, zona desmilitarizada e sub-rede filtrada)?  
**Resposta:** O gateway precisa de conectividade à origem de dados. Se a origem de dados não estiver acessível na sua rede de perímetro, o gateway pode não conseguir ligar à mesma. Por exemplo, o SQL Server pode não estar na sua rede de perímetro. Além disso, não pode ligar ao SQL Server a partir da rede de perímetro. Se tiver colocado o gateway na rede de perímetro, este não consegue aceder ao SQL Server.

**Pergunta:** É possível forçar o gateway a utilizar o tráfego HTTPS com o Azure Service Bus em vez de TCP?  
**Resposta:** Yes. Contudo, isto irá reduzir significativamente o desempenho. Modifique o ficheiro *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*. Altere o valor de `AutoDetect` para `Https`. Este ficheiro está localizado, por predefinição, em *C:\Programas\Gateway de dados no local*.

**Pergunta:** Preciso de colocar a lista de IPs do Azure Datacenter na lista de permissões? Onde posso obter a lista?  
**Resposta:** Se estiver a bloquear o tráfego IP de saída, poderá ter de colocar a lista de IPs do Azure Datacenter na lista de permissões. Atualmente, o gateway comunica com o Azure Service Bus através do endereço IP, além do nome de domínio completamente qualificado. A lista de IPs do Azure Datacenter é atualizada semanalmente. Pode transferir a [lista de IPs do Microsoft Azure Datacenter](https://www.microsoft.com/download/details.aspx?id=41653).

```xml
<setting name="ServiceBusSystemConnectivityModeString" serializeAs="String">
    <value>Https</value>
</setting>
```

## <a name="high-availabilitydisaster-recovery"></a>Elevada Disponibilidade/Recuperação Após Desastre
**Pergunta:** Existem planos para ativar cenários de elevada disponibilidade com o gateway?  
**Resposta:** Sim, esta é uma área de investimento ativa da equipa do Power BI. Mantenha-se atento ao [blogue do Power BI](https://powerbi.microsoft.com/blog/) para obter mais atualizações sobre esta funcionalidade.

**Pergunta:** Que opções estão disponíveis para a recuperação após desastre?  
**Resposta:** Pode utilizar a chave de recuperação para restaurar ou mover um gateway. Quando instalar o gateway, forneça a chave de recuperação.

**Pergunta:** Qual é a vantagem da chave de recuperação?  
**Resposta:** Fornece uma forma de migrar ou recuperar as definições do gateway. Também é utilizada na recuperação após desastre.

## <a name="troubleshooting"></a>Resolução de problemas
**Pergunta:** Onde estão localizados os registos do gateway?  
**Resposta:** Veja a secção de ferramentas do [artigo de resolução de problemas](../service-gateway-onprem-tshoot.md#tools-for-troubleshooting).

**Pergunta:** Como posso ver que consultas estão a ser enviadas para a origem de dados no local?  
**Resposta:** Pode ativar o rastreio de consultas.  Isto irá incluir as consultas enviadas. Lembre-se de alterá-lo novamente para o valor original quando terminar a resolução de problemas. Se deixar o rastreio de consultas ativado, os registos serão maiores.

Também pode ver as ferramentas que a sua origem de dados tem para o rastreio de consultas. Por exemplo, para o SQL Server e os Analysis Services, pode utilizar os Eventos Expandidos ou o SQL Profiler.

