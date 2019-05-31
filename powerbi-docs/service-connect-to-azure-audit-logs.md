---
title: Ligue-se aos Registos de Auditoria do Azure com o Power BI
description: Registos de Auditoria do Azure para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 02/06/2018
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 85872b43e984a1cf9c08500bb03f6ed50baef31e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61178987"
---
# <a name="connect-to-azure-audit-logs-with-power-bi"></a>Ligue-se aos Registos de Auditoria do Azure com o Power BI
Com o pacote de conteúdos de Registos de Auditoria do Azure, pode analisar e visualizar as informações armazenadas nos registos de auditoria. O Power BI obtem os seus dados, cria um dashboard pronto a usar e cria relatórios com base nesses dados.

[Ligue-se ao pacote de conteúdos dos Registos de Auditoria do Azure](https://app.powerbi.com/getdata/services/azure-audit-logs) ou leia mais sobre a [integração dos Registos de Auditoria do Azure](https://powerbi.microsoft.com/integrations/azure-audit-logs) com o Power BI.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.  
   
    ![](media/service-connect-to-azure-audit-logs/getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.  
   
    ![](media/service-connect-to-azure-audit-logs/services.png) 
3. Selecione **Registos de Auditoria do Azure** > **Obter**.  
   
   ![](media/service-connect-to-azure-audit-logs/azureauditlogs.png)
4. Quando pedido, introduza o **ID de Subscrição do Azure**. Consulte detalhes sobre como localizar o [ID da subscrição](#FindingParams) abaixo.   
   
    ![](media/service-connect-to-azure-audit-logs/parameters.png)
5. Como **Método de Autenticação**, selecione **oAuth2** \> **Iniciar Sessão**.
   
    ![](media/service-connect-to-azure-audit-logs/creds.png)
6. Introduza as suas credenciais de conta para concluir o processo de início de sessão.
   
    ![](media/service-connect-to-azure-audit-logs/login.png)
7. O Power BI vai obter os seus dados do Registo de Auditoria do Azure e criar um dashboard pronto a usar e um relatório. 
   
    ![](media/service-connect-to-azure-audit-logs/dashboard.png)

**E agora?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento das atualizações ou tentar atualizá-lo a pedido através da opção **Atualizar Agora**

## <a name="system-requirements"></a>Requisitos de sistema
O pacote de conteúdos de registos de Auditoria do Azure requer acesso aos Registos de Auditoria no portal do Azure. Mais detalhes [aqui](/azure/azure-resource-manager/resource-group-audit/).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>A localizar parâmetros
Há duas maneiras fáceis de encontrar o seu ID de Subscrição.

1. Em https://portal.azure.com -&gt; Procurar -&gt; Subscrições -&gt; ID da Subscrição
2. Em https://manage.windowsazure.com -&gt; Definições -&gt; ID da Subscrição

O ID de subscrição será um longo conjunto de números e carateres, semelhante ao exemplo do Passo \#4 acima. 

## <a name="troubleshooting"></a>Resolução de problemas
Se estiver a ver um erro de credenciais ou de tentativa de atualização devido a credenciais inválidas, experimente eliminar todas as instâncias do pacote de conteúdos dos registos de Auditoria do Azure e voltar a ligar.

## <a name="next-steps"></a>Próximos passos
[O que é o Power BI?](power-bi-overview.md)  
[Power BI - Conceitos Básicos](consumer/end-user-basic-concepts.md)  

