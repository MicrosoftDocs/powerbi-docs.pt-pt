---
title: 'Tutorial: ligar-se a um repositório do GitHub com o Power BI'
description: Neste tutorial, irá ligar aos dados reais no serviço GitHub com o Power BI e o Power BI criará automaticamente dashboards e relatórios.
author: maggiesMSFT
ms.reviewer: SarinaJoan
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 08/07/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: cf79a5ecf4d98595a033733824a41002a7cd38e0
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "90860561"
---
# <a name="tutorial-connect-to-a-github-repo-with-power-bi"></a>Tutorial: ligar-se a um repositório do GitHub com o Power BI
Neste tutorial, irá ligar a dados reais no serviço GitHub com o Power BI e o Power BI criará automaticamente dashboards e relatórios. Vai ligar-se ao repositório de conteúdos públicos do Power BI (também conhecido como *repositório*) e ver respostas a perguntas como: Quantas pessoas contribuem para os conteúdos públicos do Power BI? Quem contribui mais? Que dia da semana tem mais contribuições? Entre outras perguntas. 

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

- Inscreva-se numa [conta do GitHub](/contribute/get-started-setup-github).


## <a name="how-to-connect"></a>Como se ligar
1. Inicie sessão no serviço Power BI (`https://app.powerbi.com`). 
2. No painel de navegação, selecione **Aplicações** e, em seguida, **Obter aplicações**.
   
   ![Power BI: obter aplicações](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial.png) 

3. Selecione **Aplicações**, escreva **GitHub** na caixa de pesquisa > **Obter agora**.
   
   ![Power BI: obter o GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-app-source.png) 

4. Em **Instalar esta aplicação do Power BI?** , selecione **Instalar**.
5. Em **A sua nova aplicação está pronta**, selecione **Ir para a aplicação**.
6. Em **Comece já com a sua nova aplicação** , selecione **Ligar**.

    ![Comece já com a sua nova aplicação](media/service-tutorial-connect-to-github/power-bi-new-app-connect-get-started.png)

7. Escreva o nome do repositório e também o seu proprietário. O URL deste repositório é https://github.com/MicrosoftDocs/powerbi-docs, pelo que o **Proprietário do Repositório** é **MicrosoftDocs** e o **Repositório** é **powerbi-docs**. 
   
    ![Power BI: nome do repositório do GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. Introduza as credenciais do GitHub que criou. O Power BI poderá ignorar este passo se já tiver iniciado sessão no GitHub no seu browser. 

6. Para **Método de Autenticação**, mantenha **oAuth2** selecionado \>**Iniciar Sessão**.

7. Siga os ecrãs de autenticação do GitHub. Conceda permissão ao Power BI para aceder aos dados do GitHub.
   
   Agora, o Power BI pode ligar ao GitHub e aos dados.  Os dados são atualizados uma vez por dia.

8. Após o Power BI importar os dados, verá os conteúdos da sua nova área de trabalho do GitHub. 
9. Selecione a seta junto ao nome da área de trabalho no painel de navegação. Verá que a área de trabalho contém um dashboard e um relatório. 

    ![Aplicação no painel de navegação](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

10. Selecione **Mais opções** (...) junto ao nome do dashboard > **Mudar o nome** > escreva **Dashboard do GitHub**.
 
    ![Power BI: mosaico do GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav.png) 

8. Selecione o ícone de navegação global para minimizar o painel de navegação e ter mais espaço.

    ![Ícone de navegação global](media/service-tutorial-connect-to-github/power-bi-global-navigation-icon.png)

10. Selecione o dashboard do GitHub.
    
    O dashboard do GitHub contém dados dinâmicos, pelo que os valores apresentados poderão ser diferentes.

    ![Dashboard do GitHub no Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

    

## <a name="ask-a-question"></a>Colocar uma pergunta

1. Coloque o cursor em **Colocar uma questão sobre os dados**. O Power BI oferece **Perguntas para começar**. 

1. Selecione **quantos utilizadores existem**.
 
    ![Quantos utilizadores existem](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-users.png)

13. Entre **quantos** e **utilizadores existem**, escreva **pedidos pull por**. 

     O Power BI cria um gráfico de barras que mostra o número de pedidos pull por pessoa.

    ![Quantos pedidos pull por utilizador existem](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-prs.png)


13. Selecione o ícone de pino para afixar ao dashboard e, em seguida, **Sair das Perguntas e Respostas**.

## <a name="view-the-github-report"></a>Ver o relatório do GitHub 

1. No dashboard do GitHub, selecione o gráfico de colunas **Pull Requests by Month** (Pedidos Pull Por Mês) para abrir o relatório relacionado.

    ![Gráfico de colunas de pedidos pull por mês](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-column-chart.png)

2. Selecione um nome de utilizador no gráfico **Total pull requests by user** (Pedidos pull totais por utilizador). Neste exemplo, vemos que a maioria das horas ocorreu em fevereiro.

    ![Power BI: realce do relatório do GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-cross-filter-total-prs.png)

3. Selecione o separador **Punch Card** para ver a página seguinte no relatório. 
 
    ![Power BI: separador Punch Card do relatório do GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-tues-3pm.png)

    Aparentemente, terças às 15:00 é a hora e o dia da semana mais comum para *consolidações*, quando as pessoas verificam o trabalho.

## <a name="clean-up-resources"></a>Limpar recursos

Agora que concluiu o tutorial, pode eliminar a aplicação GitHub. 

1. No painel de navegação, selecione **Aplicações**.
2. Coloque o cursor sobre o mosaico do GitHub e selecione o caixote do lixo **Eliminar**.

    ![Eliminar a aplicação GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-delete.png)

## <a name="next-steps"></a>Próximos passos

Neste tutorial, ligou a um repositório público do GitHub e obteve dados, que o Power BI formatou num dashboard e num relatório. Respondeu a algumas questões sobre os dados ao explorar o dashboard e o relatório. Agora pode saber mais sobre como ligar a outros serviços, como o Salesforce, o Microsoft Dynamics e o Google Analytics. 
 
> [!div class="nextstepaction"]
> [Ligar aos serviços online que utiliza](service-connect-to-services.md)