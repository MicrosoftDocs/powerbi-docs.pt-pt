---
title: Ligue-se ao SweetIQ com o Power BI
description: SweetIQ para o Power BI
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
ms.openlocfilehash: df80e986a4ad42018c5ba036c2e47e684dba65d3
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-sweetiq-with-power-bi"></a>Ligue-se ao SweetIQ com o Power BI
O pacote de conteúdos para o Power BI extrai dados da sua conta do SweetIQ e gera um conjunto de conteúdos pronto a utilizar, o que permite que explore os seus dados com facilidade. Utilize o pacote de conteúdos do SweetIQ para analisar dados sobre os seus locais, listas, classificações e análises. Os dados são configurados para serem atualizados diariamente, o que garante que os dados que está a monitorizar são atuais.

Conecte-se ao [pacote de conteúdo do SweetIQ](https://app.powerbi.com/groups/me/getdata/services/sweetiq) para o Power BI.

## <a name="how-to-connect"></a>Como se ligar
1. No painel de navegação à esquerda, clique em **Obter Dados.**
   
    ![](media/service-connect-to-sweetiq/getdata.png)
2. Selecione **SweetIQ** e clique em **Obter.**
   
    ![](media/service-connect-to-sweetiq/sweetiq.png)
3. Forneça o ID do Cliente do SweetIQ. Isso é geralmente um valor alfanumérico. Para obter mais detalhes sobre como encontrar esse valor, veja abaixo.
   
    ![](media/service-connect-to-sweetiq/parameter.png)
4. Selecione o tipo de autenticação de **Chave** e forneça a Chave de API do SweetIQ. Isso é geralmente um valor alfanumérico. Para obter mais detalhes sobre como encontrar esse valor, veja abaixo.
   
    ![](media/service-connect-to-sweetiq/credentials.png)
5. O Power BI inicia o carregamento de dados, o que poderá demorar um pouco dependendo do tamanho dos dados na sua conta. Depois de concluído o carregamento, verá um novo dashboard, relatório e conjunto de dados no painel de navegação esquerdo.
   
    ![](media/service-connect-to-sweetiq/dashboard.png)

**O que se segue?**

* Tente [fazer uma pergunta na caixa de Perguntas e Respostas](service-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Enquanto o seu conjunto de dados vai ser agendado para ser atualizado diariamente, pode alterar o agendamento de atualização ou tentar atualizá-lo sob pedido em **Atualizar Agora**

## <a name="finding-parameters"></a>A procurar parâmetros
O ID do Cliente e a Chave de API para esse pacote de conteúdo não são as mesmas que seu nome de utilizador e palavra-passe do SweetIQ.

Selecione um ID do Cliente de um dos clientes aos quais a sua conta tem acesso. Pode encontrar a lista de clientes em “Gestão de Clientes” na sua conta do SweetIQ.

Fale com o seu administrador para obter sua chave de API, para aceder os dados de um cliente específico.

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Obter Dados para o Power BI](service-get-data.md)

