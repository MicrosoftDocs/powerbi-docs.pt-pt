---
title: Não é possível adicionar o Power BI ao parceiro do O365
description: Não é possível adicionar o Power BI a um parceiro de distribuição do Office 365. O modelo de distribuição é um modelo de compra utilizado pelo Office 365.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 09/05/2017
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 39f40c4b8aaf53e81f15c1ad29d1d8425f017468
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="unable-to-add-power-bi-to-office-365-partner-subscription"></a>Não é possível adicionar o Power BI a uma subscrição de parceiro do Office 365
O Office 365 permite que as empresas o revendam acompanhado e integrado com as suas próprias soluções, fornecendo aos clientes finais um único ponto de contacto para compra, faturação e suporte.

Se estiver interessado em adquirir o Power BI, juntamente com a sua subscrição do Office 365, recomendamos que contacte o seu parceiro. Se o seu parceiro não oferecer o Power BI, existem opções diferentes que pode considerar.

1. Pode comprar o serviço a partir de outro canal, diretamente à Microsoft ou a outro parceiro. Esta opção não está disponível para todos os clientes, consoante a relação com o parceiro. É possível verificar isto através do **Portal de Administração do Office 365** > **Faturação** > **Subscrições**. Se vir **Subscrições**, é possível adquirir o serviço da Microsoft diretamente ou também pode entrar em contacto com um parceiro que ofereça o Power BI.
   
    ![](media/service-admin-syndication-partner/billingsub.png)
2. Se não vir a opção **Subscrições** listada em **Faturação**, não é possível comprar diretamente através da Microsoft ou de outro parceiro. 
   
   ![](media/service-admin-syndication-partner/billing.png)

Se não conseguir comprar o Power BI diretamente, ainda terá algumas opções, consoante o tipo de subscrição do Power BI em que esteja interessado.

[Power BI (gratuito)](#power-bi-free)

[Power BI Pro e Premium](#power-bi-pro)

## <a name="power-bi-free"></a>Power BI (gratuito)
Se estiver satisfeito com a oferta gratuita do Power BI, pode inscrever-se para obter o serviço gratuito. Por predefinição, as inscrições individuais, também conhecidas como subscrições ad-hoc, estão desativadas. Quando tentar inscrever-se no Power BI, verá uma mensagem a indicar que o departamento de TI desativou a inscrição do Microsoft Power BI.

    Your IT department has turned off signup for Microsoft Power BI.

![](media/service-admin-syndication-partner/sorry.png)

Para ativar as subscrições ad-hoc, contacte o seu parceiro e peça-lhe que as ative. Se for um Administrador do seu inquilino e souber utilizar comandos do PowerShell no Azure Active Directory, pode ativar as subscrições ad-hoc. [Saiba mais](https://technet.microsoft.com/library/jj151815.aspx)

1. Primeiro, tem de iniciar sessão no Azure Active Directory com a sua credencial do Office 365. Na primeira linha serão solicitadas as suas credenciais. Na segunda linha, é ligado ao Azure Active Directory.
   
        $msolcred = get-credential
        connect-msolservice -credential $msolcred
   
    ![](media/service-admin-syndication-partner/aad-signin.png)
2. Quando tiver sessão iniciada, pode emitir o comando seguinte para ativar as subscrições gratuitas.
   
        Set-MsolCompanySettings -AllowAdHocSubscriptions $true

## <a name="power-bi-pro-and-premium"></a>Power BI Pro e Premium
Se quiser comprar uma subscrição do Power BI Pro ou Power BI Premium, será necessário trabalhar com o seu parceiro para considerar as opções que estão disponíveis.

* O seu parceiro concorda em adicionar o Power BI ao respetivo portefólio para que possa fazer compras através dele.
* O seu parceiro consegue fazer a sua transição para um modelo a partir do qual pode comprar o Power BI diretamente à Microsoft ou a outro parceiro que ofereça o Power BI.

Este vídeo aborda a distribuição do Office 365 e a compra do Power BI:

<iframe width="560" height="315" src="https://www.youtube.com/embed/C357phT94A8" frameborder="0" allowfullscreen></iframe>

## <a name="next-steps"></a>Próximos passos
[Gerir o Azure AD através do Windows PowerShell](https://technet.microsoft.com/library/jj151815.aspx)  
[Power BI Premium – o que é?](service-premium.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

