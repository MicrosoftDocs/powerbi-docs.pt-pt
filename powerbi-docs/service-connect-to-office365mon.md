---
title: Ligue-se ao Office365Mon com o Power BI
description: Office365Mon para o Power BI
author: teddybercovitz
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 8/29/2019
ms.author: tebercov
LocalizationGroup: Connect to services
ms.openlocfilehash: 364220d5d900004252e51184fc9cbd7e03b45b2d
ms.sourcegitcommit: c0f4d00d483121556a1646b413bab75b9f309ae9
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/29/2019
ms.locfileid: "70159913"
---
# <a name="connect-to-office365mon-with-power-bi"></a>Ligue-se ao Office365Mon com o Power BI
Com o Power BI e a aplicação de modelo Office365Mon, é fácil analisar os seus dados de desempenho de estado de funcionamento e falhas do Office 365. O Power BI recupera os seus dados, incluindo investigações de integridade e interrupções e, em seguida, compila um dashboard e relatórios prontos para uso com base nesses dados.

Ligue-se à [aplicação de modelo Office365Mon](https://app.powerbi.com/groups/me/getdata/services/office365mon) para Power BI.

>[!NOTE]
>É necessária uma conta de administrador do Office365Mon para ligar e carregar a aplicação de modelo do Power BI.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-office365mon/pbi_getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-office365mon/pbi_getservices.png) 
3. Selecione **Office365Mon** \> **Obter**.
   
   ![](media/service-connect-to-office365mon/o365mon.png)
4. Como Método de Autenticação, selecione **oAuth2** \> **Iniciar Sessão**.
   
   Quando solicitado, insira as suas credenciais de administrador do Office365Mon e siga o processo de autenticação.
   
   ![](media/service-connect-to-office365mon/creds.png)
   
   ![](media/service-connect-to-office365mon/creds2.png)
5. Após o Power BI importar os dados, verá novos elementos (dashboard, relatório e conjunto de dados) no painel de navegação esquerdo. Os novos itens são marcados com um asterisco amarelo \*; selecione a entrada do Office365Mon.
   
   ![](media/service-connect-to-office365mon/dashboard4.png)

**O que se segue?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento das atualizações ou tentar atualizá-lo a pedido através da opção **Atualizar Agora**

## <a name="troubleshooting"></a>Resolução de problemas
Se receber um erro **"falha no inicio de sessão"** depois de usar as credenciais de subscrição do Office365Mon para iniciar sessão, a conta utilizada não tem permissões para recuperar os dados do Office365Mon da conta. Verifique se é uma conta de administrador e tente novamente.

## <a name="next-steps"></a>Próximos passos
[O que é o Power BI?](power-bi-overview.md)

[Obter Dados para o Power BI](service-get-data.md)

