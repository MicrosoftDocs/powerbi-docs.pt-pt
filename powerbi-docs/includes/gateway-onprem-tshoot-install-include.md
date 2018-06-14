## <a name="update-to-the-latest-version"></a>Atualize para a versão mais recente
Muitos problemas podem surgir quando a versão de gateway está desatualizada.  É uma boa prática geral ter a certeza de que está na última versão.  Se não tiver atualizado o gateway durante um mês ou mais, considere a possibilidade de instalar a última versão do gateway e tentar reproduzir o problema.

## <a name="common-issues"></a>Problemas comuns
Seguem-se alguns problemas comuns e resoluções que ajudaram vários clientes em ambientes que restringem o acesso à Internet.

### <a name="authentication-to-proxy-server"></a>Autenticação no servidor proxy
O proxy pode exigir a autenticação de uma conta de utilizador de domínio. Por predefinição, o gateway utiliza um SID de Serviço para o utilizador de início de sessão no serviço Windows. Alterar o utilizador de início de sessão para um utilizador de domínio pode ajudar. Para obter mais informações, veja [Alterar a conta do serviço de gateway para um utilizador de domínio](../service-gateway-proxy.md#changing-the-gateway-service-account-to-a-domain-user).

### <a name="your-proxy-only-allows-ports-80-and-443-traffic"></a>O proxy só permite tráfego das portas 80 e 443
Alguns proxies restringem o tráfego apenas das portas 80 e 443. Por predefinição, a comunicação com o Azure Service Bus ocorrerá nas portas sem ser a 443.

Pode forçar o gateway a comunicar com o Azure Service Bus através de HTTPS, em vez de TCP direto. Tem de modificar o ficheiro *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*. Altere o valor de `AutoDetect` para `Https`. Este ficheiro está localizado, por predefinição, em *C:\Programas\Gateway de dados no local*.

```
<setting name="ServiceBusSystemConnectivityModeString" serializeAs="String">
    <value>Https</value>
</setting>
```

## <a name="installation"></a>Instalação
### <a name="error-failed-to-add-user-to-group---2147463168---pbiegwservice---performance-log-users---"></a>Erro: falha ao adicionar utilizador ao grupo.  (-2147463168   PBIEgwService   Utilizadores de Registo de Desempenho)
Poderá receber este erro se estiver a tentar instalar o gateway num controlador de domínio. A implementação num controlador de domínio não é suportada. Tem de implementar o gateway num computador que não seja um controlador de domínio.

### <a name="installation-fails"></a>Falhas na instalação
Poderá deparar-se com falhas na instalação se o software antivírus no computador de instalação estiver desatualizado. Pode atualizar a instalação do antivírus ou desativar o antivírus apenas até a instalação do gateway ser concluída e, em seguida, voltar a ativar o antivírus.

