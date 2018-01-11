---
title: "Ligar ao Centro de Segurança do Azure com o Power BI"
description: "Centro de Segurança do Azure para o Power BI"
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
ms.openlocfilehash: d052bc054e55eabfab53ad3b1ac9229f0a750785
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-azure-security-center-with-power-bi"></a>Ligar ao Centro de Segurança do Azure com o Power BI
Obtenha informações sobre a segurança da carga de trabalho do Azure ao ligar os Dados de Segurança do Azure ao Power BI. O Power BI cria automaticamente um dashboard e relatórios sobre os dados do Centro de Segurança do Azure, o que lhe permite analisar e explorar os dados.

Ligar ao [Pacote de conteúdos do Centro de Segurança do Azure](https://app.powerbi.com/getdata/services/azure-security-center) para o Power BI.

## <a name="how-to-connect"></a>Como ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-azure-security-center/getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-azure-security-center/services.png)
3. Selecione **Centro de Segurança do Azure** \>  **Obter**.
   
   ![](media/service-connect-to-azure-security-center/asc.png)
4. Especifique o seu ID de Subscrição. Veja detalhes sobre como [encontrar esses parâmetros](#FindingParams) abaixo.
   
   ![](media/service-connect-to-azure-security-center/params.png)
5. Como **Método de Autenticação**, selecione **oAuth2** \> **Iniciar sessão**. Quando solicitado, introduza as suas credenciais do Azure.
   
    ![](media/service-connect-to-azure-security-center/creds.png)
6. Após a aprovação, o processo de importação será iniciado automaticamente. Quando concluído, um novo dashboard, relatório e modelo aparecem no Painel de Navegação. Selecione o dashboard para ver os dados importados.
   
     ![](media/service-connect-to-azure-security-center/dashboard.png)

**O que vem em seguida?**

* Tente [fazer uma pergunta na caixa de Perguntas e Respostas](service-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Enquanto o conjunto de dados é agendado para ser atualizado diariamente, pode alterar o agendamento de atualização ou tentar atualizá-lo a pedido através de **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
O pacote de conteúdos inclui informações sobre estatísticas de segurança de recursos, análise de alerta e análise de prevenção.

## <a name="system-requirements"></a>Requisitos de sistema
Este pacote de conteúdos requer acesso a um ID de subscrição com o Centro de Segurança do Azure ativado. Veja mais detalhes no [Centro de Segurança do Azure](https://portal.azure.com/#blade/Microsoft_Azure_Security/SecurityDashboardStartBladeV2) no Portal do Azure.

O pacote de conteúdos também exige que o utilizador se ligue com uma conta institucional (não uma conta pessoal).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>A localizar parâmetros
Existem duas formas fáceis de localizar o seu ID de Subscrição.

1. A partir de https://portal.azure.com -&gt; Procurar -&gt; Subscrições -&gt; Id de subscrição
2. A partir de https://manage.windowsazure.com -&gt; Definições -&gt; Id de subscrição

O seu ID de subscrição será um longo conjunto de números e caracteres, semelhante ao exemplo do Passo \#4 acima. 

## <a name="troubleshooting"></a>Resolução de problemas
Os dados podem levar algum tempo a carregar consoante o tamanho da sua conta. Se encontrou um erro durante o início de sessão, confirme os parâmetros e que a conta tem o Centro de Segurança do Azure ativado.

Se o pacote de conteúdos carrega, mas não mostra os dados, verifique que está a ligar com uma conta organizacional. Embora as contas pessoais sejam suportadas pelo Centro de Segurança do Azure, a API (e, por conseguinte, o pacote de conteúdos) não devolve os valores esperados se o utilizador ligar com uma conta não organizacional. Forneça acesso a uma conta organizacional e tente ligar novamente.

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Obter dados no Power BI](service-get-data.md)

