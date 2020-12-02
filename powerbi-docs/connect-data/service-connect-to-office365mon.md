---
title: Ligue-se ao Office365Mon com o Power BI
description: Office365Mon para o Power BI
author: paulinbar
ms.author: painbar
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 11/26/2019
LocalizationGroup: Connect to services
ms.openlocfilehash: c7433bcc75da316e2e705a63dbcc2f17745ad573
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403059"
---
# <a name="connect-to-office365mon-with-power-bi"></a>Ligue-se ao Office365Mon com o Power BI
Com o Power BI e a aplicação de modelo Office365Mon, é fácil analisar os seus dados de desempenho de estado de funcionamento e falhas do Office 365. O Power BI recupera os seus dados, incluindo investigações de integridade e interrupções e, em seguida, compila um dashboard e relatórios prontos para uso com base nesses dados.

Ligue-se à [aplicação de modelo Office365Mon](https://msit.powerbi.com/groups/me/getapps/services/office365mon.office365mon_powerbi_v3) para Power BI.

>[!NOTE]
>É necessária uma conta de administrador do Office365Mon para ligar e carregar a aplicação de modelo do Power BI.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação.
   
   ![Captura de ecrã a mostrar o botão Obter Dados no painel de navegação.](media/service-connect-to-office365mon/pbi_getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![Captura de ecrã a mostrar a caixa de diálogo Serviços com o botão Obter.](media/service-connect-to-office365mon/pbi_getservices.png) 
3. Selecione **Office365Mon** \> **Obter**.
   
   ![Captura de ecrã a mostrar a caixa de diálogo Office365Mon com a ligação Obter.](media/service-connect-to-office365mon/o365mon.png)
4. Para o Método de Autenticação, selecione **oAuth2**\> **Iniciar Sessão**.
   
   Quando solicitado, insira as suas credenciais de administrador do Office365Mon e siga o processo de autenticação.
   
   ![Captura de ecrã a mostrar a caixa de diálogo Ligar ao Office365Mon com o Auth2 no campo Método de Autenticação.](media/service-connect-to-office365mon/creds.png)
   
   ![Captura de ecrã a mostrar o início de sessão do Office365Mon a pedir as credenciais.](media/service-connect-to-office365mon/creds2.png)
5. Depois de o Power BI importar os dados, verá um novo dashboard, relatório e conjunto de dados no painel de navegação. Os novos itens são marcados com um asterisco amarelo \*; selecione a entrada do Office365Mon.
   
   ![Captura de ecrã a mostrar o painel de navegação no Power B I com o dashboard, o relatório e o conjunto de dados.](media/service-connect-to-office365mon/dashboard4.png)

**O que se segue?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](../consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](../create-reports/service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](../consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento das atualizações ou tentar atualizá-lo a pedido através da opção **Atualizar Agora**

## <a name="troubleshooting"></a>Resolução de problemas
Se receber um erro **"falha no inicio de sessão"** depois de usar as credenciais de subscrição do Office365Mon para iniciar sessão, a conta utilizada não tem permissões para recuperar os dados do Office365Mon da conta. Verifique se é uma conta de administrador e tente novamente.

## <a name="next-steps"></a>Próximos passos
[O que é o Power BI?](../fundamentals/power-bi-overview.md)

[Obter Dados para o Power BI](service-get-data.md)
