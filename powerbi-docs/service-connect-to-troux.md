---
title: Ligar ao Troux com o Power BI
description: Trouxe para o Power BI
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
ms.openlocfilehash: c2d8e22758e3d28a3851b99140876ff1646a6be0
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/19/2018
---
# <a name="connect-to-troux-for-power-bi"></a>Ligar ao Troux para o Power BI
Com o pacote de conteúdos do Troux, pode visualizar o seu repositório de Arquitetura Empresarial de formas totalmente novas diretamente no Power BI. O pacote de conteúdos fornece um conjunto de informações sobre as suas capacidades de negócios, as aplicações que fornecem essas funcionalidades e as tecnologias que suportam essas aplicações que podem ser totalmente personalizadas com o Power BI.

Conecte-se ao [pacote de conteúdos do Troux](https://app.powerbi.com/getdata/services/troux) para o Power BI.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-troux/getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-troux/services.png)
3. Selecione **Troux** \> **Obter**.
   
   ![](media/service-connect-to-troux/troux.png)
4. Especifique o URL do OData do Troux. Veja detalhes sobre como [encontrar os parâmetros](#FindingParams) abaixo.
   
   ![](media/service-connect-to-troux/params.png)
5. Para o **Método de Autenticação**, selecione **Básico** e forneça o seu nome de utilizador e palavra-chave (diferencia maiúsculas de minúsculas) e selecione **Entrar**.
   
    ![](media/service-connect-to-troux/creds.png)
6. Após a aprovação, o processo de importação será iniciado automaticamente. Quando concluído, um novo dashboard, relatório e modelo aparecerão no Painel de Navegação. Selecione o dashboard para ver os seus dados importados.
   
     ![](media/service-connect-to-troux/dashboard.png)

**O que se segue?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](power-bi-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento de atualização ou tentar atualizá-lo a pedido através de **Atualizar Agora**

## <a name="system-requirements"></a>Requisitos do sistema
É necessário o acesso ao feed OData do Troux e o Troux 9.5.1 ou posterior.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>A procurar parâmetros
A sua equipa de Atendimento ao Cliente pode fornecer o URL do feed OData do Troux exclusivo para si

## <a name="troubleshooting"></a>Resolução de problemas
Se vir um erro de tempo limite depois de fornecer as credenciais, tente ligar-se novamente.

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Obter dados no Power BI](service-get-data.md)

