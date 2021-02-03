---
title: Ativar ou desativar a compra e inscrição de gestão personalizada
description: Procedimentos para os administradores desativarem a capacidade dos utilizadores de se inscreverem no serviço Power BI e comprarem ou atualizarem licenças.
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 01/31/2021
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 80e263cc6e67c28b7593fcf10aea4c81c9f4af86
ms.sourcegitcommit: f7330dabb9cd8bce90bb2efec3e3273a11578f10
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2021
ms.locfileid: "99494311"
---
# <a name="enable-or-disable-self-service-sign-up-and-purchasing"></a>Ativar ou desativar a compra e inscrição de gestão personalizada

## <a name="what-is-self-service"></a>O que é autosserviço?

O self-service refere-se à capacidade de os indivíduos de uma organização (trabalho ou escola) se inscreverem para utilizar os serviços pagos pela subscrição da sua organização, ou usar serviços gratuitos, sem pedir à sua organização que tome medidas em seu nome. O indivíduo vai a um site da Microsoft, encontra um serviço de nuvem que a sua organização oferece, e usa o seu endereço de e-mail organizacional para se inscrever nesse serviço. 

Em muitos casos, a organização pagou uma taxa por uma subscrição desse serviço. Noutros casos, o indivíduo é o primeiro utilizador e torna-se o administrador do serviço. Para um julgamento ou licença gratuita, não é necessária qualquer compra. Mas para o Power BI Pro, a organização é responsável pelo pagamento da mensalidade. 

Como administrador da Microsoft 365, pode ver quem se inscreve para testes, licenças e subscrições.

> [!NOTE]
> A inscrição de self-service só é aplicável aos clientes comerciais em nuvem, e não a nuvens nacionais ou clientes do governo.

## <a name="when-to-use-self-service-sign-up-and-purchase"></a>Quando utilizar a inscrição e compra de autosserviço

### <a name="self-service-is-a-good-idea"></a>O self-service é uma boa ideia: 

- Em organizações maiores e descentralizadas (trabalho ou escola), onde os indivíduos são muitas vezes dado a flexibilidade para comprar licenças SaaS (Software como serviço) para seu próprio uso. 
- Para uma pessoa ou pequena organização que precise de adquirir apenas uma licença Power BI Pro, ou apenas algumas licenças.
- Para indivíduos interessados em experimentar o Power BI, ficando proficiente, antes de comprar uma subscrição para toda a organização.
- Para os utilizadores atuais com uma licença power bi gratuita, que agora querem criar e partilhar conteúdos e atualizar-se para um teste Power BI Pro. 

### <a name="you-may-want-to-disable-self-service-when"></a>Pode querer desativar o autosserviço quando:

- A sua organização tem processos de aquisição em vigor para atender às necessidades de conformidade, regulação, segurança e governação. Tem de garantir que todas as licenças Power BI Pro são aprovadas e geridas de acordo com os processos definidos. 
- A sua organização tem requisitos para novos utilizadores power BI Pro, como formação obrigatória ou reconhecimento de políticas de proteção de dados.
- A sua organização proíbe a utilização do serviço Power BI devido à privacidade dos dados ou outras preocupações e precisa de controlar de perto a atribuição de licenças livres power bi.
- para garantir que todas as licenças Power BI Pro se enquadram no acordo de empresa, a fim de tirar partido das taxas de licenciamento negociadas/descontadas.
- Para os utilizadores atuais com uma licença power bi gratuita, que estão sendo solicitados a tentar ou comprar diretamente uma licença Power BI Pro. A sua organização pode não querer que estes utilizadores atualizem por segurança, privacidade ou despesas.


## <a name="enable-and-disable-self-service"></a>Ativar e desativar o autosserviço

Como administrador, pode determinar se ativa ou desativa a inscrição de gestão personalizada. Também determina se os utilizadores da sua organização podem fazer compras de self-service para obter a sua própria licença. 

Desativar a inscrição self-service impede os utilizadores de explorar o Power BI para visualização e análise de dados. Se bloquear a inscrição individual, poderá querer obter licenças do Power BI (gratuito) para a sua organização e atribuí-las a todos os utilizadores. 

> [!NOTE]
>Se adquiriu o Power BI através de um Microsoft Cloud Solution Provider (CSP), a definição pode ser desativada para impedir que os utilizadores se inscrevam individualmente. O CSP também pode estar a agir como administrador global para a sua organização e exigir que o contacte para o ajudar a alterar esta definição.
>


 Utilizará comandos PowerShell para alterar as definições que controlam a inscrição e a compra de autosserviço. 

- Se quiser desativar todas as inscrições de gestão personalizada, altere uma definição no Azure Active Directory, denominada **AllowAdHocSubscriptions** com os comandos do Microsoft Azure AD para PowerShell. Siga os passos neste artigo para [ativar ou desativar a inscrição de gestão personalizada](#enable-or-disable-self-service-sign-up-for-your-organization). Esta opção desativa a inscrição de gestão personalizada para *todos* os serviços e aplicações com base na cloud da Microsoft.

- Se quiser impedir que os utilizadores comprem a sua própria licença Pro, altere a definição **AllowSelfServicePurchase** com os comandos do MSCommerce para PowerShell. Esta definição permite-lhe desativar a compra de gestão personalizada de produtos específicos. Siga os passos neste artigo para [ativar ou desativar a compra de gestão personalizada de licenças do Power BI Pro](#enable-or-disable-self-service-purchase-in-your-organization).

## <a name="enable-or-disable-self-service-sign-up-for-your-organization"></a>Ativar ou desativar o autosserviço para a sua organização

Se a inscrição de gestão personalizada estiver ativada, o valor de **AllowAdHocSubscriptions** será *true*. Vamos ver o que acontece quando muda esta definição para *false*:

- Novos utilizadores na sua organização estão impedidos de se inscrever individualmente. Todos os utilizadores que se inscreveram no Power BI antes de alterar a definição mantêm as suas licenças.

- Os utilizadores que já tenham uma licença Power BI (grátis) ainda podem inscrever-se para um teste individual do Power BI Pro.

- Um administrador terá de atribuir todas as licenças power bi a novos utilizadores que precisem de uma.

### <a name="before-you-begin"></a>Before you begin

Estes passos utilizam os comandos do Microsoft Azure AD para PowerShell para alterar o valor da definição **AllowAdHocSubscriptions**. Deve ter o módulo Microsoft Azure AD para PowerShell instalado para estes comandos estarem disponíveis. Para obter mais informações sobre a utilização do PowerShell, veja [Introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

Para instalar o módulo do Azure Active Directory, inicie o Windows PowerShell como administrador. Confirme que a política de execução local lhe permite executar scripts. Se tiver problemas, veja [PowerShell execution policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies#powershell-execution-policies) (Políticas de execução do PowerShell) para saber como alterar a política local.

Execute o seguinte comando para instalar o módulo Microsoft Azure AD:

```powershell
Install-Module MSOnline
```

### <a name="change-the-self-service-signup-policy"></a>Alterar a política de inscrição de gestão personalizada

No PowerShell, execute o seguinte comando para ligar ao Microsoft Azure AD:

```powershell
Connect-MsolService
```

Introduza as credenciais de administrador na caixa de diálogo de início de sessão e complete qualquer autenticação de dois fatores que possa ser necessária. Após a verificação, volta à janela do PowerShell.

Para visualizar a definição atual, execute o seguinte comando. A saída é direcionada para uma lista formatada com o comutador “fl”.

```powershell
Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
```

Para alterar a definição atual, execute este comando:

```powershell
Set-MsolCompanySettings -AllowAdHocSubscriptions $false
```

Depois de executar este comando, a inscrição de gestão personalizada é desativada para todos os utilizadores. Para a voltar a ativar, volte a executar este comando e defina o valor como $true.

## <a name="enable-or-disable-self-service-purchase-in-your-organization"></a>Ativar ou desativar a compra de self-service na sua organização

Se a compra de gestão personalizada estiver ativada, o valor de **AllowSelfServicePurchase** será *true*. Vamos ver o que acontece quando altera esta definição para *false*:

- Os utilizadores da sua organização estão impedidos de comprar a sua própria licença Power BI Pro. Todos os utilizadores que compraram uma licença antes de alterar a definição mantêm as suas licenças.

- Os utilizadores que tenham uma licença Power BI (grátis) não podem obter uma licença Power BI Pro individual. 

- Um administrador precisa atribuir uma licença Pro a todos os utilizadores que precisem de uma.

### <a name="before-you-begin"></a>Before you begin

Estes passos utilizam comandos do MSCommerce para PowerShell para alterar o valor da definição **AllowSelfServicePurchase**. Deve ter o módulo MSCommerce para PowerShell instalado para estes comandos estarem disponíveis. Para obter mais informações sobre a utilização do PowerShell, veja [Introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

Para instalar o módulo MSCommerce, inicie o Windows PowerShell como administrador. Confirme que a política de execução local lhe permite executar scripts. Se tiver problemas, veja [PowerShell execution policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies#powershell-execution-policies) (Políticas de execução do PowerShell) para saber como alterar a política local.

Execute o seguinte comando para instalar o módulo MSCommerce:

```powershell
Install-Module -name MSCommerce
```

### <a name="change-the-self-service-signup-policy"></a>Alterar a política de inscrição de gestão personalizada

No PowerShell, execute o seguinte comando para se ligar:

```powershell
Connect-MSCommerce
```

Introduza as credenciais de administrador na caixa de diálogo de início de sessão e complete qualquer autenticação de dois fatores que possa ser necessária. Após a verificação, a janela do PowerShell mostra uma ligação com êxito.

Para ver a definição atual, execute o seguinte comando. Para evitar que o texto seja truncado, a saída será direcionada para uma lista formatada com o comutador “fl”.

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase | fl
```

Pode desativar a definição que permite a compra de gestão personalizada para um produto individual ao indicar o **ProductId**. Para alterar a definição atual do serviço Power BI, execute este comando:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0L3PB -Enabled $False
```

Depois de executar este comando, a compra de gestão personalizada do Power BI é desativada para todos os utilizadores. Para a voltar a ativar, volte a executar este comando e defina o valor como $true.

## <a name="what-to-do-if-individuals-have-already-used-self-service"></a>O que fazer se os indivíduos já usaram o self-service

A inscrição e a compra de autosserviço são ambas ativadas por padrão. Isto permite que os indivíduos da sua organização já tenham licenças e subscrições power bi. Quer tomes alguma ação ou não, precisas de uma imagem clara do que já existe.

Os utilizadores que se tiverem associado ao seu inquilino através de inscrição de gestão personalizada receberão uma licença exclusiva, que poderá filtrar no painel do utilizador ativo, no dashboard do administrador. Para criar esta nova vista, siga estes passos.

1. Navegue para o centro de administração do Microsoft 365.

1. No painel de navegação, selecione **Utilizadores** > **Utilizadores Ativos**.

1. No menu Vistas, selecione **Adicionar vista personalizada**.

1. Atribua um nome à nova vista e, em Licença de produto atribuída, selecione Power BI (gratuito) ou Power BI Pro.

    Apenas pode ter uma licença selecionada por vista. Se tiver licenças do Power BI (gratuito) e do Power BI Pro na sua organização, poderá criar duas vistas.

1. Introduza quaisquer outras condições que pretenda e selecione **Adicionar**.

    Depois de criar a nova vista, pode vê-la no menu Vistas.


    > [!NOTE]
    > Se a sua organização não tiver um ambiente Microsoft 365 ligado ao seu domínio de e-mail, os utilizadores de self-service foram adicionados a um novo diretório de utilizadores apenas na nuvem. Você pode precisar encontrar, reclamar e [assumir inquilinos que já foram criados.](https://docs.microsoft.com/azure/active-directory/users-groups-roles/domains-admin-takeover) 

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre a compra de gestão personalizada no Power BI e no resto do Power Platform, veja estes artigos:

- [Self-service purchase FAQ](/microsoft-365/commerce/subscriptions/self-service-purchase-faq#admin-capabilities) (FAQ da compra de gestão personalizada)
- [Use AllowSelfServicePurchase for the MSCommerce PowerShell module](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell) (Utilizar AllowSelfServicePurchase do módulo MSCommerce para PowerShell)