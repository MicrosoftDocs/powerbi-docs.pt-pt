---
title: Ligue-se ao Smartsheet com o Power BI
description: Smartsheet para Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 55d61e89b1fb01de472d967a312b25340d482951
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54008473"
---
# <a name="connect-to-smartsheet-with-power-bi"></a>Ligue-se ao Smartsheet com o Power BI
O Smartsheet oferece uma plataforma fácil para colaboração e partilha de ficheiros. O pacote de conteúdos Smartsheet para Power BI fornece um dashboard, relatórios e o conjunto de dados que mostra uma visão geral da sua conta de Smartsheet. Também é possível usar o [Power BI Desktop](desktop-connect-to-data.md) para se conectar diretamente às folhas individuais na sua conta. 

Ligue-se ao [pacote de conteúdos do Smartsheet](https://app.powerbi.com/groups/me/getdata/services/smartsheet) para o Power BI.

>[!NOTE]
>A conta de administrador Smartsheet é preferida para ligar e carregar o pacote de conteúdo do Power BI, visto que tem acesso adicional.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-smartsheet/pbi_getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-smartsheet/pbi_getservices.png) 
3. Selecione **Smartsheet \> Obter**.
   
   ![](media/service-connect-to-smartsheet/smartsheet.png)
4. Como Método de Autenticação, selecione **oAuth2 \> Iniciar Sessão**.
   
   Quando solicitado, insira as suas credenciais do Smartsheet e siga o processo de autenticação.
   
   ![](media/service-connect-to-smartsheet/creds.png)
   
   ![](media/service-connect-to-smartsheet/creds2.png)
5. Após o Power BI importar os dados, verá novos elementos (dashboard, relatório e conjunto de dados) no painel de navegação esquerdo. Os novos itens são marcados com um asterisco amarelo \*; selecione a entrada do Smartsheet.
   
   ![](media/service-connect-to-smartsheet/dashboard.png)

**E agora?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento das atualizações ou tentar atualizá-lo a pedido através da opção **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
O pacote de conteúdo do Smartsheet para o Power BI inclui uma visão geral de sua conta do Smartsheet, tais como o número de espaços de trabalho, os relatórios e os livros existentes, informações sobre a data em que são modificados, etc. Os utilizadores administradores também podem ver algumas informações sobre os utilizadores no seu sistema, como os principais criadores de livros.  

Para se ligar diretamente a planilhas livros na sua conta, é possível utilizar o conector do Smartsheet no [Power BI Desktop](desktop-connect-to-data.md).  

## <a name="next-steps"></a>Próximos passos:

[O que é o Power BI?](power-bi-overview.md)

[Obter Dados para o Power BI](service-get-data.md)