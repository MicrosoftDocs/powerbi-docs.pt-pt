---
title: Ligar-se ao Salesforce com o Power BI
description: Salesforce para o Power BI
author: SarinaJoan
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/30/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 9fcf67a52bde69e62816af09a8fed69c8383927d
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2020
ms.locfileid: "86216179"
---
# <a name="connect-to-salesforce-with-power-bi"></a>Ligar-se ao Salesforce com o Power BI
Com o Power BI, pode ligar-se facilmente à sua conta do Salesforce.com. Com esta ligação, pode obter os seus dados do Salesforce, bem como receber automaticamente um dashboard e relatórios.

Leia mais sobre a [Integração do Salesforce](https://powerbi.microsoft.com/integrations/salesforce) no Power BI.

## <a name="how-to-connect"></a>Como se ligar
1. No Power BI, selecione **Obter Dados** na parte inferior do painel de navegação.
   
   ![Captura de ecrã a mostrar o botão Obter Dados no painel de navegação.](media/service-connect-to-salesforce/pbi_getdata.png) 
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![Captura de ecrã a mostrar a caixa de diálogo Serviços com o botão Obter.](media/service-connect-to-salesforce/pbi_getservices.png) 
3. Selecione **Analytics for Salesforce** (Análise para Salesforce) e selecione **Obter**.  
   
   ![Captura de ecrã a mostrar a caixa de diálogo da Análise para o Salesforce, com a ligação Obter agora.](media/service-connect-to-salesforce/salesforce.png)
4. Selecione **Iniciar Sessão** para começar o fluxo de início de sessão.
   
    ![Captura de ecrã a mostrar a caixa de diálogo Ligar ao Salesforce, com o botão Iniciar sessão.](media/service-connect-to-salesforce/dialog.png)
5. Quando pedido, insira as suas credenciais do Salesforce. Selecione **Permitir** para que o Power BI possa aceder aos seus dados e informações básicos do Salesforce.
   
   ![Captura de ecrã a mostrar as credenciais do Salesforce, a indicar que o Power B I está a pedir permissão para aceder às suas informações.](media/service-connect-to-salesforce/sf_authorize.png)
6. Configure o que pretende importar para o Power BI com a opção de lista pendente:
   
   * **Dashboard**
     
     Selecione um dashboard predefinido com base numa persona (como **Gestor de Vendas**). Estes dashboards obtêm um conjunto específico de dados padrão do Salesforce, que não incluem campos personalizados.
     
     ![Captura de ecrã a mostrar o dashboard do Salesforce, com a opção de selecionar um dashboard predefinido baseado numa pessoa.](media/service-connect-to-salesforce/pbi_salesforcechooserole.png)
   * **Relatórios**
     
     Selecione um ou mais relatórios personalizados da conta do Salesforce. Esses relatórios correspondem às suas visualizações no Salesforce e podem incluir dados de objetos ou campos personalizados.
     
     ![Captura de ecrã a mostrar os relatórios do Salesforce, com uma lista de relatórios personalizados.](media/service-connect-to-salesforce/pbi_salesforcereports.png)
     
     Se não vir quaisquer relatórios, adicione ou crie-os em sua conta do Salesforce e tente ligar-se novamente.

7. Clique em **Ligar** para iniciar o processo de importação. Durante a importação, verá uma notificação a indicar que a importação está em curso. Quando a importação for concluída, verá um dashboard, um relatório e um conjunto de dados para os seus dados do Salesforce listados no painel de navegação.
   
   ![Captura de ecrã a mostrar o dashboard do Gestor de Vendas, com o dashboard, o relatório e conjuntos de dados.](media/service-connect-to-salesforce/pbi_getdatasalesforcedash.png)

Pode alterar o dashboard para apresentar os seus dados da forma pretendida. Pode colocar perguntas com a funcionalidade de Perguntas e Respostas ou [selecionar um mosaico](../consumer/end-user-tiles.md) para abrir o relatório subjacente e [editar ou remover mosaicos do dashboard](../create-reports/service-dashboard-edit-tile.md).

**O que se segue?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](../consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Editar ou remover um mosaico](../create-reports/service-dashboard-edit-tile.md) no dashboard
* [Selecionar um bloco](../create-reports/service-dashboard-tiles.md) para abrir o relatório subjacente
* Apesar de o seu conjunto de dados estar agendado para atualizações diárias, pode alterar a atualização agendada ou tentar atualizá-la a pedido através da opção **Atualizar Agora**

## <a name="system-requirements-and-considerations"></a>Requisitos de sistema e considerações

- Estar conectado a uma conta do Salesforce que tenha acesso ativado à API

- Permissão concedida à aplicação Power BI durante o início de sessão

- A conta ter chamadas à API suficientes disponíveis para efetuar pull dos dados e atualizá-los

- Um token de autenticação válido é necessário para a atualização. O Salesforce tem um limite de cinco tokens de autenticação por aplicação, pelo que deve garantir que só importa até cinco conjuntos de dados do Salesforce.

- A API Relatórios do Salesforce tem uma restrição para suportar até 2000 linhas de dados.


## <a name="troubleshooting"></a>Resolução de problemas

Caso se depare com erros, veja os requisitos acima. 

Atualmente, não é suportado iniciar sessão num domínio personalizado ou do sandbox.

### <a name="unable-to-connect-to-the-remote-server-message"></a>Mensagem "Não é possível ligar ao servidor remoto"

Se for apresentada a mensagem "Não é possível ligar ao servidor remoto" quando tentar ligar-se à sua conta do Salesforce, veja esta solução no seguinte fórum: [Salesforce Connector sign in Error Message: Unable to connect to the remote server](https://www.outsystems.com/forums/Forum_TopicView.aspx?TopicId=17674&TopicName=log-in-error-message-unable-to-connect-to-the-remote-server&) (Mensagem de erro de início de sessão do Conector do Salesforce: não é possível ligar ao servidor remoto).


## <a name="next-steps"></a>Próximos passos
[O que é o Power BI?](../fundamentals/power-bi-overview.md)

[Origens de dados para o serviço Power BI](service-get-data.md)
