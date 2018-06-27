---
title: Ligue-se ao SweetIQ com o Power BI
description: SweetIQ para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 6592405de2d76c14334c8c31e4af84cd5a090ed9
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/26/2018
ms.locfileid: "34247556"
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

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](power-bi-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento de atualização ou tentar atualizá-lo a pedido através de **Atualizar Agora**

## <a name="finding-parameters"></a>A procurar parâmetros
O ID do Cliente e a Chave de API para esse pacote de conteúdo não são as mesmas que seu nome de utilizador e palavra-passe do SweetIQ.

Selecione um ID do Cliente de um dos clientes aos quais a sua conta tem acesso. Pode encontrar a lista de clientes em “Gestão de Clientes” na sua conta do SweetIQ.

Fale com o seu administrador para obter sua chave de API, para aceder os dados de um cliente específico.

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Obter Dados para o Power BI](service-get-data.md)

