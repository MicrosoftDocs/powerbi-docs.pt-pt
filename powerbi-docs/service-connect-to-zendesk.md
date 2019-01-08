---
title: Ligue-se ao Zendesk com Power BI
description: Zendesk para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 72b934357ec4208fa07266143b08af861659e465
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54008333"
---
# <a name="connect-to-zendesk-with-power-bi"></a>Ligue-se ao Zendesk com Power BI
O pacote de conteúdos do Zendesk oferece um dashboard e um conjunto de relatórios do Power BI que fornecem informações sobre os volumes de pedidos e o desempenho do agente. Pode utilizar o dashboard e os relatórios fornecidos, ou então personalizá-los para destacar as informações que mais interessam.  Os dados são atualizados automaticamente uma vez por dia. 

Ligue-se ao [pacote de conteúdos do Zendesk](https://app.powerbi.com/getdata/services/zendesk) ou leia mais sobre a [Integração do Zendesk](https://powerbi.microsoft.com/integrations/zendesk) com o Power BI.

>[!NOTE]
>Uma conta de administrador do Zendesk é necessária para ligar-se. Mais detalhes sobre os [requisitos](#Requirements) abaixo.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-zendesk/pbi_getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-zendesk/pbi_getservices.png) 
3. Selecione **Zendesk** \> **Obter.**
   
   ![](media/service-connect-to-zendesk/zendesk.png)
4. Forneça o URL associado à sua conta. O URL terá o formato **https://company.zendesk.com**. Veja os detalhes sobre como [encontrar esses parâmetros](#FindingParams) abaixo.
   
   ![](media/service-connect-to-zendesk/pbi_zendeskconnect.png)
5. Quando solicitado, insira as suas credenciais do Zendesk.  Selecione **oAuth 2** como o Mecanismo de Autenticação e clique em **Entrar**. Siga o fluxo de autenticação do Zendesk. (Se já tiver iniciado a sessão no Zendesk no seu browser, talvez as suas credenciais não sejam solicitadas.)
   
   > [!NOTE]
   > Este pacote de conteúdo requer a conexão com uma conta de Administrador do Zendesk. 
   > 
   > 
   
   ![](media/service-connect-to-zendesk/pbi_zendesksignin.png)
6. Clique em **Permitir** para permitir que o Power BI aceda aos seus dados do Zendesk.
   
   ![](media/service-connect-to-zendesk/zendesk2.jpg)
7. Clique em **Conectar** para iniciar o processo de importação. Depois do Power BI importar os dados, verá um novo dashboard, relatório e conjunto de dados no painel de navegação esquerdo. Os novos itens estão marcados com um asterisco amarelo \*.
   
   ![](media/service-connect-to-zendesk/pbi_zendeskdash.png)

**O que se segue?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento das atualizações ou tentar atualizá-lo a pedido através da opção **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
O pacote de conteúdos do Power BI inclui dados sobre o seguinte:  

* Utilizadores (utilizadores finais e agentes)  
* Organizações  
* Grupos  
* Pedidos  

Há também um conjunto de medidas que foram calculadas, como tempo médio de espera e pedidos resolvidos nos últimos sete dias. Uma lista completa está incluída no pacote de conteúdos.

<a name="Requirements"></a>

## <a name="system-requirements"></a>Requisitos do sistema
Uma conta de administrador do Zendesk é necessária para aceder ao pacote de conteúdos do Zendesk. Se é um agente ou um utilizador final e estiver interessado em ver os seus dados no Zendesk, adicione uma sugestão e examine o conector do Zendesk no [Power BI Desktop](desktop-connect-to-data.md).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>A localizar parâmetros
O URL do Zendesk vai ser igual ao URL que utiliza para se ligar à sua conta do Zendesk. Se não se lembrar do URL do Zendesk, utilize a [ajuda de início de sessão](https://www.zendesk.com/login/) do Zendesk.

## <a name="troubleshooting"></a>Resolução de problemas
Se estiver com problemas para se ligar, verifique o URL do Zendesk e confirme que está a utilizar uma conta de administrador do Zendesk.

## <a name="next-steps"></a>Próximos passos
* [O que é o Power BI?](power-bi-overview.md)
* [Obter Dados](service-get-data.md)

