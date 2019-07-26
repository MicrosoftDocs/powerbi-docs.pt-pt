---
title: Utilizar gateways pessoais no Power BI
description: Disponibiliza informações sobre o gateway de dados no local (modo pessoal) para o Power BI que os utilizadores individuais podem utilizar para ligar a dados no local.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 93d2c4358b0f4b4090a2c8bea3daa8eec71c4982
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/16/2019
ms.locfileid: "68270879"
---
# <a name="use-personal-gateways-in-power-bi"></a>Utilizar gateways pessoais no Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

O gateway de dados no local (modo pessoal) é uma versão do gateway de dados no local que só funciona com o Power BI. Um gateway pessoal permite aos utilizadores individuais instalarem um gateway no computador e obter acesso a dados no local.

> [!NOTE]
> Só pode ter um gateway de modo pessoal em execução para cada utilizador do Power BI. Se instalou outro gateway de modo pessoal para o mesmo utilizador, mesmo num computador diferente, a instalação mais recente substitui a instalação anterior.

## <a name="on-premises-data-gateway-vs-on-premises-data-gateway-personal-mode"></a>Gateway de dados no local vs. gateway de dados no local (modo pessoal)

A tabela seguinte descreve as diferenças entre um gateway de dados no local e um gateway de dados no local (modo pessoal).

|   |Gateway de dados no local | Gateway de dados local (modo pessoal) |
| ---- | ---- | ---- |
|Serviços na cloud suportados |Power BI, PowerApps, Azure Logic Apps, Microsoft Flow, Azure Analysis Services, Fluxos de Dados |Power BI |
|Execuções |Conforme configurado pelos utilizadores com acesso ao gateway |Conforme configurado pelo utilizador para autenticação do Windows e para outros tipos de autenticação |
|Só é possível realizar instalações com privilégios de administrador do computador |Sim |Não |
|Gateway centralizado e gestão de origens de dados |Sim |Não |
|Importar dados e agendar atualização |Sim |Sim |
|Suporte sobre o DirectQuery |Sim |Não |
|Suporte do LiveConnect para o Analysis Services |Sim |Não |

## <a name="install-the-on-premises-data-gateway-personal-mode"></a>Instalar o gateway de dados no local (modo pessoal)

Para instalar o gateway de dados no local (modo pessoal):

1. [Transfira o gateway de dados no local](https://go.microsoft.com/fwlink/?LinkId=820925&clcid=0x409).

2. No instalador, selecione o gateway de dados no local (modo pessoal) e, em seguida, selecione o botão **Seguinte**.

   ![Selecionar o gateway de dados no local (modo pessoal)](media/service-gateway-personal-mode/personal-gateway-select.png)

Após a instalação ser concluída com êxito e após iniciar sessão, verá o seguinte ecrã.

![Gateway de dados no local (modo pessoal) com êxito](media/service-gateway-personal-mode/personal-gateway-complete.png)

## <a name="using-fast-combine-with-the-personal-gateway"></a>Utilizar a opção de Combinação Rápida com o gateway pessoal

A Combinação Rápida num gateway pessoal ajuda-o a ignorar níveis de privacidade especificados ao executar consultas. Para ativar a Combinação Rápida para funcionar com o gateway de dados no local (modo pessoal):

1. No Explorador de Ficheiros, abra o ficheiro seguinte:

   `%localappdata%\Microsoft\On-premises data gateway (personal mode)\Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config`

2. Na parte inferior do ficheiro, adicione o seguinte texto:

    ```xml
    <setting name="EnableFastCombine" serializeAs="String">
       <value>true</value>
    </setting>
    ```

3. Assim que estiver concluído, a definição entra em vigor em cerca de um minuto. Para verificar se está a funcionar corretamente, experimente uma atualização a pedido no **serviço do Power BI** para confirmar que a **Combinação Rápida** está a funcionar.

## <a name="frequently-asked-questions-faq"></a>Perguntas Frequentes (FAQ)

**Pergunta:** Posso executar o **gateway de dados no local (modo pessoal)** lado a lado com o **gateway de dados no local** (anteriormente conhecido como a versão Empresarial do gateway)?
  
**Resposta:** Sim, ambas podem ser executadas em simultâneo.

**Pergunta:** Posso executar o **gateway de dados no local (modo pessoal)** como um serviço?
  
**Resposta:** Não. o **gateway de dados no local (modo pessoal)** só pode ser executado como uma aplicação. Se precisa de executar o gateway como um serviço e/ou no modo de administrador, terá de considerar o [**gateway de dados no local**](/data-integration/gateway/service-gateway-onprem) (anteriormente conhecido como o gateway Empresarial).

**Pergunta:** Com que frequência o **gateway de dados no local (modo pessoal)** é atualizado?
  
**Resposta:** Pretendemos atualizar o gateway pessoal mensalmente.

**Pergunta:** Por que razão é-me pedido para atualizar as minhas credenciais?
  
**Resposta:** Muitas situações podem desencadear um pedido de credenciais. A mais comum é a que instalou novamente o **gateway de dados no local (modo pessoal)** num computador diferente do seu gateway do **Power BI - personal**. Também pode ser um problema na origem de dados e o Power BI não ter conseguido realizar uma ligação de teste, ter alcançado o tempo limite ou ocorrido um erro de sistema. Pode atualizar as suas credenciais no **serviço Power BI** ao aceder ao **ícone de engrenagem** e selecionar **Definições**, **Conjuntos de dados**, encontrar o conjunto de dados em questão e selecionar **Credenciais da origem de dados**.

**Pergunta:** Quanto tempo os meus gateways pessoais anteriores estarão offline durante a atualização?
  
**Resposta:** Atualizar o gateway pessoal para a nova versão deve demorar apenas alguns minutos.

**Pergunta:** Estou a utilizar scripts R e Python. É suportado?
  
**Resposta:** Os scripts R e Python são suportados no modo pessoal.

## <a name="next-steps"></a>Próximos passos

* [Configurar definições de proxy para o gateway de dados no local](/data-integration/gateway/service-gateway-proxy)  

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

