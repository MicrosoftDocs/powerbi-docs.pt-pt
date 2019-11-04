---
title: Ligar ao IntelliBoard com o Power BI
description: IntelliBoard para Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 06fc561d3fbe07cbf553be63c7b19de3ab11992e
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060948"
---
# <a name="connect-to-intelliboard-with-power-bi"></a>Ligar ao IntelliBoard com o Power BI
O IntelliBoard fornece acesso simplificado aos dados do sistema de gestão de aprendizagem Moodle através do SQL Server Reporting Services. O pacote de conteúdo do IntelliBoard para o Power BI oferece análises adicionais, incluindo métricas sobre cursos, utilizadores registados, desempenho geral e atividade de LMS.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Conecte-se ao [pacote de conteúdo do IntelliBoard](https://app.powerbi.com/getdata/services/intelliboard) para o Power BI.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.  
   
    ![](media/service-connect-to-intelliboard/getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.  
   
    ![](media/service-connect-to-intelliboard/services.png)
3. Selecione **IntelliBoard** e, em seguida **Obter**.  
   
    ![](media/service-connect-to-intelliboard/intelliboard.png)
4. Selecione **OAuth 2** e **Entrar**. Quando solicitado, forneça suas credenciais do IntelliBoard.
   
    ![](media/service-connect-to-intelliboard/creds.png)
   
    ![](media/service-connect-to-intelliboard/creds2.png)
5. Depois de estar ligado, um dashboard, relatório e conjunto de dados são carregados automaticamente. Após a conclusão, os blocos são atualizados com os dados da sua conta do IntelliBoard.
   
    ![](media/service-connect-to-intelliboard/dashboard.png)

**O que se segue?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento das atualizações ou tentar atualizá-lo a pedido através da opção **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
O pacote de conteúdos inclui dados das seguintes tabelas:  

    - Atividade  
    - Agentes  
    - Autenticação  
    - Países  
    - Progresso dos Cursos  
    - Registos
    - Idioma  
    - Plataforma  
    - Totais  
    - Progresso dos Utilizadores    

## <a name="system-requirements"></a>Requisitos do sistema
É necessário ter uma conta do IntelliBoard com permissões de acesso às tabelas acima para criar uma instância deste pacote de conteúdos.

## <a name="next-steps"></a>Próximos passos
[O que é o Power BI?](fundamentals/power-bi-overview.md)

[Conceitos básicos para designers no serviço Power BI](service-basic-concepts.md)

