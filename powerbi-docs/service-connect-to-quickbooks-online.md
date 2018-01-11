---
title: Ligue-se ao QuickBooks Online com o Power BI
description: QuickBooks Online para o Power BI
services: powerbi
documentationcenter: 
author: joeshoukry
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: yshoukry
ms.openlocfilehash: def174cb86b701f628e4637d3a9933a42c5a5740
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-quickbooks-online-with-power-bi"></a>Ligue-se ao QuickBooks Online com o Power BI
Quando se liga aos seus dados do QuickBooks Online através do Power BI, obtém imediatamente um dashboard e relatórios do Power BI que fornecem informações sobre o fluxo de caixa da sua empresa, rentabilidade, clientes e muito mais. Utilize o dashboard e os relatórios como fornecidos, ou então personalize-os para realçar as informações que mais interessam. Os dados são atualizados automaticamente uma vez por dia.

Ligue-se ao [pacote de conteúdo do QuickBooks Online](https://dxt.powerbi.com/getdata/services/quickbooks-online) para o Power BI.

>[!NOTE]
>Para importar dados do QuickBooks Online para o Power BI, é necessário ser um administrador da conta do QuickBooks Online e entrar com as credenciais da conta de administrador.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-quickbooks-online/pbi_getdata.png) 
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-quickbooks-online/pbi_getservices.png) 
3. Selecione **QuickBooks Online** e selecione **Obter**.
   
   ![](media/service-connect-to-quickbooks-online/qbo.png)
4. Selecione **oAuth2** como Método de Autenticação e selecione **Iniciar Sessão**. 
5. Quando solicitado, insira as suas credenciais do QuickBooks Online e siga o processo de autenticação do QuickBooks Online. Se já tiver a sessão iniciada no QuickBooks Online no seu browser, talvez as suas credenciais não sejam solicitadas.
   >[!NOTE]
   >É necessário ter credenciais de administrador para a conta do QuickBooks Online.
6. Selecione a empresa a que seja deseja ligar ao Power BI no próximo ecrã.
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_almost.png)
7. Selecione **Autorizar** no próximo ecrã para iniciar o processo de importação. Isso pode levar alguns minutos, dependendo do tamanho dos dados da sua empresa. 
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_authorizesm.png)
   
   Depois do Power BI importar os dados, vai ver um novo dashboard, relatório e conjunto de dados no painel de navegação esquerdo. Os novos itens são marcados com um asterisco amarelo \*.
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_leftnavnew.png)
8. Selecione o dashboard QuickBooks Online. Este é o dashboard do Power BI criado automaticamente para mostrar os dados importados. Pode alterar este dashboard para mostrar os seus dados de qualquer forma que queira. 
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_dash.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de Perguntas e Respostas](service-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento de atualização ou tentar atualizá-lo a pedido através de **Atualizar Agora**

## <a name="troubleshooting"></a>Resolução de problemas
**“Ups! Ocorreu um erro.”**

Se receber esta mensagem depois de selecionar **Autorizar**:

“Ups! Ocorreu um erro.” Feche esta janela e tente novamente.

A aplicação já foi assinada para esta empresa por outro utilizador. Entre em contacto com [e-mail do administrador] para fazer alterações a essa subscrição.”

![](media/service-connect-to-quickbooks-online/pbi_qbo_oopssm.png)

... isso significa que outro administrador na sua empresa já se ligou aos dados da empresa com o Power BI. Peça ao admin que partilhe o dashboard consigo. Atualmente, apenas um utilizador administrador pode ligar a um determinado conjunto de dados empresariais do QuickBooks Online para o Power BI. Depois do Power BI criar o dashboard, o administrador pode partilhá-lo com vários colegas no mesmos inquilinos do Power BI.

**"Esta aplicação não está configurada para permitir ligações do seu país"**

Atualmente o Power BI só dá suporte às edições dos EUA do QuickBooks Online. 

![](media/service-connect-to-quickbooks-online/pbi_qbo_countrynotsupported.png)

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Power BI - Conceitos Básicos](service-basic-concepts.md)

