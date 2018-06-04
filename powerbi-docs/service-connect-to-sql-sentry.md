---
title: Ligar ao SQL Sentry com o Power BI
description: SQL Sentry para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 8ad41917c887cff7db991051aa35d5dad6b6a8fa
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34242429"
---
# <a name="connect-to-sql-sentry-with-power-bi"></a>Ligar ao SQL Sentry com o Power BI
É fácil analisar os dados de desempenho recolhidos pelo SQL Sentry com o Power BI. O Power BI obtém os dados e cria um dashboard predefinido e relatórios relacionados com base nesses dados.

Ligue-se ao [pacote de conteúdos do SQL Sentry](https://app.powerbi.com/groups/me/getdata/services/sql-sentry) para o Power BI.

>[!NOTE]
>A ligação precisa do acesso a uma conta do SQL Sentry utilizada para ligar ao http://cloud.sqlsentry.com e um ID de Base de Dados que irá monitorizar.  Veja abaixo as instruções sobre onde encontrar o ID de Base de Dados.

## <a name="how-to-connect"></a>Como ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-sql-sentry/pbi_getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-sql-sentry/pbi_getservices.png) 
3. Selecione **SQL Sentry \> Obter**.
   
   ![](media/service-connect-to-sql-sentry/sqlsentry.png)
4. Forneça o **ID da Base de Dados** da base de dados que gostaria de monitorizar no Power BI. Veja mais detalhes sobre como [encontrar isto](#FindingParams) abaixo.
   
   ![](media/service-connect-to-sql-sentry/img2400.png)
5. Para o Método de Autenticação, selecione **oAuth2 \> Iniciar Sessão**.
   
   Quando solicitado, introduza as credenciais do cloud.sqlsentry.com e siga o processo de autenticação do SQL Sentry.
   
   ![](media/service-connect-to-sql-sentry/img6400.png)
   
   Quando ligar pela primeira vez, o Power BI pede-lhe para permitir acesso só de leitura à sua conta. Selecione Conceder para iniciar o processo de importação.  O processo de importação pode demorar alguns minutos, dependendo do volume de dados na sua conta.
   
   ![](media/service-connect-to-sql-sentry/img7400.png)
6. Depois de o Power BI importar os dados, verá um novo dashboard, relatório e conjunto de dados no dashboard de navegação esquerdo. Os novos itens são marcados com um asterisco amarelo \*:
   
   ![](media/service-connect-to-sql-sentry/img8200.png)
7. Selecione o dashboard do SQL Sentry.
   
   Este é o dashboard predefinido criado pelo Power BI para apresentar os seus dados. Pode alterar este dashboard para apresentar os dados da forma que quiser.
   
   ![](media/service-connect-to-sql-sentry/img9dashboard800.png)

**E agora?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](power-bi-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento de atualização ou tentar atualizá-lo a pedido através de **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
Os seguintes dados estão disponíveis no SQL Sentry no Power BI:

| Nome da tabela | Descrição |
| --- | --- |
| Ligação |Esta tabela fornece informações sobre as ligações definidas do SQL Sentry. |
| Data<br /> |Esta tabela contém as datas de hoje até à primeira data a partir da qual os dados de desempenho foram recolhidos e mantidos. |
| Tempo de inatividade<br /> |Esta tabela contém informações relacionadas com o tempo de inatividade e o tempo de atividade para cada servidor monitorizado no seu ambiente. |
| Utilização de Memória<br /> |Esta tabela contém dados sobre a quantidade de memória está disponível ou livre em cada um dos seus servidores.<br /> |
| Servidor<br /> |Esta tabela contém registos para cada servidor no seu ambiente. |
| Estado de Funcionamento do Servidor<br /> |Esta tabela contém dados para todos os eventos gerados por condições personalizadas no seu ambiente, incluindo gravidade e contagem. |

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>A localizar Parâmetros
O **ID da Base de Dados** pode ser encontrado ao iniciar sessão em <https://cloud.sqlsentry.com> numa nova janela de browser.  O **ID de Base de Dados** está listado na página de visão geral principal:

    ![](media/service-connect-to-sql-sentry/database2.png)

O **ID de Base de Dados** está também mostrado no ecrã de Detalhes de Base de Dados:

    ![](media/service-connect-to-sql-sentry/database.png)


## <a name="troubleshooting"></a>Resolução de problemas
Se os dados de algumas das suas aplicações não estiverem a aparecer no Power BI, certifique-se de que está a utilizar o ID de Base de Dados correta e tem autoridade para ver os dados. 

Se não é o proprietário da base de dados do SQL Sentry que está a ser sincronizada com <https://cloud.sqlsentry.com>, entre em contacto com o seu administrador para verificar se tem direitos para ver os dados recolhidos.

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Obter Dados para o Power BI](service-get-data.md)

