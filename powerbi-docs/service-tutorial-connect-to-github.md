---
title: 'Tutorial: Ligar a um exemplo do GitHub com o Power BI'
description: Neste tutorial, irá ligar aos dados reais no serviço GitHub com o Power BI e o Power BI criará automaticamente dashboards e relatórios.
author: maggiesMSFT
manager: kfile
ms.reviewer: SarinaJoan
ms.service: powerbi
ms.component: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 05/17/2018
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: 88be0aa477b5e4b2df4f53c42dfb6fde3dda0184
ms.sourcegitcommit: b03912343a5a214c6bb972aaa6aa051c2a5f4332
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2018
ms.locfileid: "52900503"
---
# <a name="tutorial-connect-to-a-github-sample-with-power-bi"></a>Tutorial: Ligar a um exemplo do GitHub com o Power BI
Neste tutorial, irá ligar a dados reais no serviço GitHub com o Power BI e o Power BI criará automaticamente dashboards e relatórios. Irá ligar ao repositório de conteúdos públicos do Power BI (também conhecido apenas como *repositório*) e ver informações: quantas pessoas contribuem para os conteúdos públicos do Power BI? Quem contribui mais? Que dia da semana tem mais contribuições? Assim como respostas a outras perguntas. 

![O relatório do GitHub no Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-punch-card.png)

Neste tutorial, irá concluir os seguintes passos:

> [!div class="checklist"]
> * Inscrever-se numa conta do GitHub, se ainda não tiver uma 
> * Iniciar sessão na sua conta do Power BI ou inscrever-se, se ainda não tiver uma
> * Abrir o serviço Power BI
> * Localizar a aplicação GitHub
> * Introduzir as informações do repositório público do GitHub do Power BI
> * Ver o dashboard e o relatório com dados do GitHub
> * Limpar os recursos ao eliminar a aplicação

Se não estiver inscrito no Power BI, [inscreva-se para uma avaliação gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) antes de começar.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este tutorial, precisa de uma conta do GitHub, se ainda não tiver uma. 

- Inscreva-se numa [conta do GitHub](https://docs.microsoft.com/contribute/get-started-setup-github)


## <a name="how-to-connect"></a>Como se ligar
1. Inicie sessão no serviço Power BI (http://powerbi.com). 
2. No painel de navegação à esquerda, selecione **Aplicações** e, em seguida, **Obter aplicações**.
   
   ![Power BI: obter aplicações](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial.png) 

3. Selecione **Aplicações**, escreva **github** na caixa de pesquisa > **Obter agora**.
   
   ![Power BI: obter o GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-get-it-now.png) 

4. Escreva o nome do repositório e também o seu proprietário. O URL deste repositório é https://github.com/MicrosoftDocs/powerbi-docs, pelo que o **Proprietário do Repositório** é **MicrosoftDocs** e o **Repositório** é **powerbi-docs**. 
   
    ![Power BI: nome do repositório do GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-repo-name.png)

5. Introduza as credenciais do GitHub que criou. O Power BI poderá ignorar este passo se já tiver iniciado sessão no GitHub no seu browser. 

6. Como **Método de Autenticação**, selecione **oAuth2** \> **Iniciar Sessão**.

7. Siga os ecrãs de autenticação do Github. Conceda permissão ao Power BI para aceder aos dados do GitHub.
   
   Agora, o Power BI pode ligar ao GitHub e aos dados.  Os dados são atualizados uma vez por dia.

8. Depois de o Power BI importar os dados, verá o novo mosaico do GitHub. 
 
   ![Power BI: mosaico do GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-tile.png) 

8. Selecione o ícone de navegação global para minimizar a navegação à esquerda, para ter mais espaço.

    ![Ícone de navegação global](media/service-tutorial-connect-to-github/power-bi-global-navigation-icon.png)

10. Selecione o mosaico do GitHub do passo 8. 
    
    É aberto o dashboard do GitHub. São dados dinâmicos, pelo que os valores que vir poderão ser diferentes.

    ![Dashboard do GitHub no Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-dashboard.png)

    

## <a name="ask-a-question"></a>Colocar uma pergunta

11. Coloque o cursor em **Colocar uma questão sobre os dados** e, em seguida, selecione **pull requests**. 

    ![Power BI: colocar uma questão sobre os dados](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-ask-question.png)

12. Escreva **by month**.
 
    ![Pedidos pull por mês](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-ask-question-by-month.png)

     O Power BI cria um gráfico de barras que mostra o número de pedidos pull por mês.

13. Selecione **Sair das Perguntas e Respostas**.

## <a name="view-the-github-report"></a>Ver o relatório do GitHub 

1. No dashboard do GitHub, selecione o gráfico de colunas e linhas de combinação **Pull Requests by Month** para abrir o relatório relacionado.

    ![Gráfico de combinação de pedidos pull por mês](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-pull-requests-combo-chart.png)

2. Selecione um nome de utilizador no gráfico **Total pull requests by user** e veja, como neste exemplo, que tinham uma média de horas superior à média total de março.

    ![Power BI: realce do relatório do GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-report-highlight.png)

3. Selecione o separador **Punch Card** para ver a página seguinte no relatório. 
 
    ![Power BI: separador Punch Card do relatório do GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-tues-3pm.png)

    Aparentemente, terças às 15:00 é a hora e o dia da semana mais comum para *consolidações* (commits), quando as pessoas comparecem no trabalho.

## <a name="clean-up-resources"></a>Limpar recursos

Agora que concluiu o tutorial, pode eliminar a aplicação GitHub. 

1. Na barra de navegação à esquerda, selecione **Aplicações**.
2. Coloque o cursor sobre o mosaico do GitHub e selecione o caixote do lixo **Eliminar**.

    ![Eliminar a aplicação GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-delete.png)

## <a name="next-steps"></a>Próximos passos

Neste tutorial, ligou a um repositório público do GitHub e obteve dados, que o Power BI formatou num dashboard e num relatório. Respondeu a algumas questões sobre os dados ao explorar o dashboard e o relatório. Agora pode saber mais sobre como ligar a outros serviços, como o Salesforce, o Microsoft Dynamics e o Google Analytics. 
 
> [!div class="nextstepaction"]
> [Ligar aos serviços online que utiliza](service-connect-to-services.md)


