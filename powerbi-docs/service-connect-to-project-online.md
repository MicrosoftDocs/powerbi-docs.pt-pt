---
title: Ligue-se ao Project Online com o Power BI
description: Project Online para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: dd6698cab5b9fed407e6e8f45ceb160209a38fae
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54007574"
---
# <a name="connect-to-project-online-with-power-bi"></a>Ligue-se ao Project Online com o Power BI
Microsoft Project Online é uma solução online flexível para PPM (gestão de portefólios de projetos) e para o trabalho quotidiano. O Project Online permite que as organizações comecem, atribuam prioridades a investimentos de portefólio de projetos e entreguem o valor comercial pretendido. O pacote de conteúdos do Project Online para o Power BI permite-lhe obter informações do Project Online para ajudar na gestão de projetos, portefólios e recursos.

Ligue-se ao [pacote de conteúdo do Project Online](https://app.powerbi.com/getdata/services/project-online) para o Power BI.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
    ![](media/service-connect-to-project-online/getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-project-online/services.png)
3. Selecione **Microsoft Project Online** \> **Obter**.
   
   ![](media/service-connect-to-project-online/mproject.png)
4. Na caixa de texto **URL do Project Web App**, introduza o URL para o PWA (Project Web Add) ao qual pretende ligar-se e clique em **Avançar**. Observe que isso pode ser diferente do exemplo, caso tenha um domínio personalizado. Na caixa de texto **Idioma do Site do PWA**, escreva o número que corresponde ao seu idioma do site do PWA. Escreva o dígito "1" para inglês, "2" para francês, "3" para alemão, "4" para português (Brasil), "5" para português (Portugal) e "6" para espanhol. 
   
    ![](media/service-connect-to-project-online/params.png)
5. Como Método de Autenticação, selecione **oAuth2** \> **Iniciar Sessão**. Quando solicitado, insira as suas credenciais do Project Online e siga o processo de autenticação.
   
    ![](media/service-connect-to-project-online/creds.png)
    
Tenha em atenção que é necessário ter permissões de Visualizador de Portefólio, Gestor de Portefólio ou Administrador para o Project Web App ao qual se está a ligar.

6. Vai ver uma notificação a indicar que os dados estão a ser carregados. Dependendo do tamanho da sua conta, pode levar algum tempo. Depois de o Power BI importar os dados, verá um novo dashboard, 13 relatórios e um conjunto de dados no painel de navegação esquerdo. Esse é o dashboard padrão criado pelo Power BI para exibir os seus dados. Pode alterar este dashboard para apresentar os dados da forma que quiser.

   ![](media/service-connect-to-project-online/dashboard2.png)

7. Quando o seu dashboard e relatórios estiverem prontos, pode começar a explorar os seus dados do Project Online! O Pacote de Conteúdos inclui 13 relatórios avançados e detalhados de Descrição Geral do Portefólio (6 páginas de relatórios), Descrição Geral do Recurso (5 páginas de relatórios) e Estado do Projeto (2 páginas de relatórios). 

   ![](media/service-connect-to-project-online/report1.png)
   
   ![](media/service-connect-to-project-online/report3.png)
   
   ![](media/service-connect-to-project-online/report2.png)

**O que se segue?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento das atualizações ou tentar atualizá-lo a pedido através da opção **Atualizar Agora**

**Expandir o Pacote de Conteúdos**

Transfira o [ficheiro PBIT do GitHub](https://github.com/OfficeDev/Project-Power-BI-Content-Packs) para atualizar e personalizar ainda mais o Pacote de Conteúdos

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Obter dados no Power BI](service-get-data.md)

