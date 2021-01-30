---
title: Ativar ou desativar a compra e inscrição de gestão personalizada
description: Procedimentos para os administradores desativarem a capacidade dos utilizadores de se inscreverem no serviço Power BI e comprarem ou atualizarem licenças.
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 04/08/2020
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 127fe9c306295619dadc9817056f76b243231093
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2021
ms.locfileid: "99086010"
---
# <a name="enable-or-disable-self-service-sign-up-and-purchasing"></a>Ativar ou desativar a compra e inscrição de gestão personalizada

Na maioria das organizações, a inscrição de gestão personalizada está ativada por predefinição. Os utilizadores individuais da sua organização podem inscrever-se no Power BI com a sua conta de trabalho ou escolar. Os utilizadores também poderão ter a possibilidade de comprarem diretamente uma licença do Power BI Pro se tentarem utilizar uma funcionalidade que requer o Pro. Como administrador, pode determinar se ativa ou desativa a inscrição de gestão personalizada. Também pode controlar se os utilizadores na sua organização podem fazer compras de gestão personalizada para obterem a sua própria licença.

> [!NOTE]
>Se tiver adquirido o Power BI através de um Fornecedor de Soluções Cloud da Microsoft (CSP), a definição poderá estar desativada para impedir que os utilizadores se inscrevam individualmente. O CSP também pode estar a agir como administrador global para a sua organização e exigir que o contacte para o ajudar a alterar esta definição.
>
>

Utiliza os comandos do PowerShell para alterar as definições que controlam a compra e inscrição de gestão personalizada. Existem duas definições que controlam se os utilizadores na sua organização podem realizar a compra ou inscrição de gestão personalizada.

- Se quiser desativar todas as inscrições de gestão personalizada, altere uma definição no Azure Active Directory, denominada **AllowAdHocSubscriptions** com os comandos do Microsoft Azure AD para PowerShell. Siga os passos neste artigo para [ativar ou desativar a inscrição de gestão personalizada](#enable-or-disable-self-service-signup). Esta opção desativa a inscrição de gestão personalizada para *todos* os serviços e aplicações com base na cloud da Microsoft.

- Se quiser impedir que os utilizadores comprem a sua própria licença Pro, altere a definição **AllowSelfServicePurchase** com os comandos do MSCommerce para PowerShell. Esta definição permite-lhe desativar a compra de gestão personalizada de produtos específicos. Siga os passos neste artigo para [ativar ou desativar a compra de gestão personalizada de licenças do Power BI Pro](#enable-or-disable-self-service-purchase).

## <a name="enable-or-disable-self-service-signup"></a>Ativar ou desativar a inscrição de gestão personalizada

Se a inscrição de gestão personalizada estiver ativada, o valor de **AllowAdHocSubscriptions** será *true*. Vamos ver o que acontece quando muda esta definição para *false*:

- Se alterar a definição de true para false, os novos utilizadores na sua organização serão impedidos de se inscreverem individualmente. Os utilizadores que se inscreveram no Power BI antes de alterar a definição mantêm as suas licenças.

- Se alterar a definição para false, os utilizadores que já possuem uma licença do Power BI (gratuito) ainda poderão inscrever-se numa avaliação do Power BI Pro individual.

- O administrador precisa de atribuir todas as licenças do Power BI aos novos utilizadores que precisem de uma.

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

## <a name="enable-or-disable-self-service-purchase"></a>Ativar ou desativar a compra de gestão personalizada

Se a compra de gestão personalizada estiver ativada, o valor de **AllowSelfServicePurchase** será *true*. Vamos ver o que acontece quando altera esta definição para *false*:

- Se alterar a definição de true para false, os utilizadores na sua organização serão impedidos de comprar as suas próprias licenças do Power BI Pro. Os utilizadores que tenham comprado uma licença antes de alterar a definição mantêm as suas licenças.

- Se alterar a definição para false, os utilizadores que possuem uma licença do Power BI (gratuito) não poderão obter uma licença do Power BI Pro individual. 

- O administrador precisa de atribuir uma licença Pro a todos os utilizadores que precisem de uma.

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

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre a compra de gestão personalizada no Power BI e no resto do Power Platform, veja estes artigos:

- [Self-service purchase FAQ](/microsoft-365/commerce/subscriptions/self-service-purchase-faq#admin-capabilities) (FAQ da compra de gestão personalizada)
- [Use AllowSelfServicePurchase for the MSCommerce PowerShell module](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell) (Utilizar AllowSelfServicePurchase do módulo MSCommerce para PowerShell)