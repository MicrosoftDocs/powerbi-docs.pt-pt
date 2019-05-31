---
title: 'Tutorial: Ligar a um repo do GitHub com o Power BI'
description: Neste tutorial, irá ligar aos dados reais no serviço GitHub com o Power BI e o Power BI criará automaticamente dashboards e relatórios.
author: maggiesMSFT
manager: kfile
ms.reviewer: SarinaJoan
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 04/19/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: 3aeb1fc16ae200399125a2366a8993d45aad34c4
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "64578646"
---
# <a name="tutorial-connect-to-a-github-repo-with-power-bi"></a>Tutorial: Ligar a um repo do GitHub com o Power BI
Neste tutorial, irá ligar a dados reais no serviço GitHub com o Power BI e o Power BI criará automaticamente dashboards e relatórios. Ligar para o repositório de conteúdo público do Power BI (também conhecido como um *repositório*) e ver respostas a perguntas como: Quantas pessoas contribuem para os conteúdos públicos do Power BI? Quem contribui mais? Que dia da semana tem mais contribuições? E outras perguntas. 

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

- Inscreva-se para uma [conta do GitHub](https://docs.microsoft.com/contribute/get-started-setup-github).


## <a name="how-to-connect"></a>Como se ligar
1. Inicie sessão no serviço Power BI (https://app.powerbi.com). 
2. No painel de navegação à esquerda, selecione **Aplicações** e, em seguida, **Obter aplicações**.
   
   ![Power BI: obter aplicações](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial.png) 

3. Selecione **aplicações**, tipo **GitHub** na caixa de pesquisa > **obter agora**.
   
   ![Power BI: obter o GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-app-source.png) 

4. Na **instalar esta aplicação do Power BI?** selecionar **instalar**.
5. Na **sua nova aplicação está pronta**, selecione **Ir para a aplicação**.
6. Na **introdução à sua nova aplicação**, selecione **ligar a dados**.

    ![Comece a utilizar a sua nova aplicação](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect-data.png)

7. Escreva o nome do repositório e também o seu proprietário. O URL deste repositório é https://github.com/MicrosoftDocs/powerbi-docs, pelo que o **Proprietário do Repositório** é **MicrosoftDocs** e o **Repositório** é **powerbi-docs**. 
   
    ![Power BI: nome do repositório do GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. Introduza as credenciais do GitHub que criou. O Power BI poderá ignorar este passo se já tiver iniciado sessão no GitHub no seu browser. 

6. Para **método de autenticação**, mantenha **oAuth2** selecionado \> **sessão**.

7. Siga os ecrãs de autenticação do GitHub. Conceda permissão ao Power BI para aceder aos dados do GitHub.
   
   Agora, o Power BI pode ligar ao GitHub e aos dados.  Os dados são atualizados uma vez por dia.

8. Depois do Power BI importar os dados, verá o conteúdo da sua nova área de trabalho do GitHub. 
9. Selecione a seta junto ao nome da área de trabalho na barra de navegação esquerdo. Ver a que área de trabalho contém um dashboard e um relatório. 

    ![Aplicação no painel de navegação esquerdo](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

10. Selecione as reticências (...) junto ao nome do dashboard > **mudar o nome** > tipo **dashboard do GitHub**.
 
    ![Power BI: mosaico do GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav.png) 

8. Selecione o ícone de navegação global para minimizar a navegação à esquerda, para ter mais espaço.

    ![Ícone de navegação global](media/service-tutorial-connect-to-github/power-bi-global-navigation-icon.png)

10. Selecione o seu dashboard do GitHub.
    
    O dashboard do GitHub contém dados em direto, portanto, os valores que vir podem ser diferentes.

    ![Dashboard do GitHub no Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

    

## <a name="ask-a-question"></a>Colocar uma pergunta

1. Coloque o cursor na **faça uma pergunta sobre os seus dados**. Power BI disponibiliza **perguntas para começar a utilizar**. 

1. Selecione **quantos utilizadores estão lá**.
 
    ![Quantos utilizadores estão lá](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-users.png)

13. Entre **quantos** e **utilizadores existem**, tipo **pedidos por pull**. 

     O Power BI cria um gráfico de barras que mostra o número de pedidos pull por pessoa.

    ![O número de pedidos pull por utilizador está lá](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-prs.png)


13. Selecione o pin para afixá-lo ao seu dashboard, em seguida, **sair das perguntas e respostas**.

## <a name="view-the-github-report"></a>Ver o relatório do GitHub 

1. No dashboard do GitHub, selecione o gráfico de colunas **pedidos Pull por mês** para abrir o relatório relacionado.

    ![Pedidos pull pelo gráfico de coluna do mês](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-column-chart.png)

2. Selecione um nome de utilizador no **pedidos Total pull por utilizador** gráfico. Neste exemplo, podemos ver a maior parte das suas horas estavam em Fevereiro.

    ![Power BI: realce do relatório do GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-cross-filter-total-prs.png)

3. Selecione o separador **Punch Card** para ver a página seguinte no relatório. 
 
    ![Power BI: separador Punch Card do relatório do GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-tues-3pm.png)

    Aparentemente, Terça-feira às 15:00 é mais comum tempo e o dia da semana para *consolidações*, quando as pessoas verificar em seu trabalho.

## <a name="clean-up-resources"></a>Limpar recursos

Agora que concluiu o tutorial, pode eliminar a aplicação GitHub. 

1. Na barra de navegação à esquerda, selecione **Aplicações**.
2. Coloque o cursor sobre o mosaico do GitHub e selecione o caixote do lixo **Eliminar**.

    ![Eliminar a aplicação GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-delete.png)

## <a name="next-steps"></a>Próximos passos

Neste tutorial, ligou a um repositório público do GitHub e obteve dados, que o Power BI formatou num dashboard e num relatório. Respondeu a algumas questões sobre os dados ao explorar o dashboard e o relatório. Agora pode saber mais sobre como ligar a outros serviços, como o Salesforce, o Microsoft Dynamics e o Google Analytics. 
 
> [!div class="nextstepaction"]
> [Ligar aos serviços online que utiliza](service-connect-to-services.md)


