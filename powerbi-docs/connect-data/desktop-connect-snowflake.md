---
title: Ligar a um armazém de informática de Snowflake no Power BI Desktop
description: Ligar e utilizar facilmente um armazém de informática de Snowflake no Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/04/2021
LocalizationGroup: Connect to data
ms.openlocfilehash: 377ede2171a721a33aa0b70819ef511d721f2590
ms.sourcegitcommit: f7330dabb9cd8bce90bb2efec3e3273a11578f10
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2021
ms.locfileid: "99494449"
---
# <a name="connect-to-snowflake-in-power-bi-desktop"></a>Ligar ao Snowflake no Power BI Desktop
No Power BI Desktop, pode ligar a um armazém de informática de **Snowflake** e utilizar os dados subjacentes, tal como faria com outra origem de dados no Power BI Desktop. 

## <a name="connect-to-a-snowflake-computing-warehouse"></a>Ligar a um armazém de informática de Snowflake
Para ligar a um armazém de informática de **Snowflake**, selecione **Obter Dados** a partir do friso **Base** no Power BI Desktop. Selecione **Base de Dados** nas categorias no lado esquerdo e verá **Snowflake**.

![Captura de ecrã a mostrar a caixa de diálogo Obter Dados, com a seleção da base de dados do Snowflake.](media/desktop-connect-snowflake/connect-snowflake-2b.png)

Na janela do **Snowflake** que é apresentada, escreva ou cole o nome do seu armazém de informática de Snowflake na caixa e selecione **OK**. Tenha em atenção que pode optar por **Importar** dados diretamente para o Power BI ou pode utilizar o **DirectQuery**. Pode saber mais sobre [utilizar o DirectQuery](desktop-use-directquery.md). Tenha em atenção que o SSO do AAD só suporta DirectQuery.

![Captura de ecrã a mostrar a caixa de diálogo do Snowflake, com o botão de opção Importar selecionado.](media/desktop-connect-snowflake/connect-snowflake-3.png)

Quando lhe for pedido, introduza o seu nome de utilizador e a palavra-passe.

![Captura de ecrã a mostrar as credenciais pedidas pelo Snowflake, com os campos Nome de utilizador e Palavra-passe.](media/desktop-connect-snowflake/connect-snowflake-4.png)

> [!NOTE]
> Depois de introduzir o seu nome de utilizador e a palavra-passe para um determinado servidor **Snowflake**, o Power BI Desktop utiliza as mesmas credenciais nas tentativas de ligação subsequentes. Pode modificar essas credenciais, acedendo a **Ficheiro > Opções e definições > Definições da origem de dados**.
> 
> 

Se quiser utilizar a opção de conta Microsoft, a integração do AAD no Snowflake tem de ser configurada do lado do Snowflake. Para tal, leia a secção Introdução da [documentação do Snowflake sobre o tópico](https://docs.snowflake.net/manuals/user-guide/oauth-powerbi.html#power-bi-sso-to-snowflake).

![Tipo de autenticação da conta Microsoft no conector Snowflake.](media/desktop-connect-snowflake/connect-snowflake-6.png)


Depois de a ligação ser concluída com êxito, é apresentada uma janela **Navegador**, que apresenta os dados disponíveis no servidor, dos quais pode selecionar um ou vários elementos para importar e utilizar no **Power BI Desktop**.

![Erro ODBC 28000 faz com que ocorra uma falha ao ligar.](media/desktop-connect-snowflake/connect-snowflake-5.png)

Pode **Carregar** a tabela selecionada, que traz toda a tabela para o **Power BI Desktop**, ou pode **Editar** a consulta, que abre o **Editor de Consultas**, para poder filtrar e refinar o conjunto de dados que pretende utilizar, e carregar o conjunto de dados refinados para o **Power BI Desktop**.

## <a name="custom-roles"></a>Funções Personalizadas

Atualmente, o suporte para 'Função Personalizada' no conector Snowflake só funcionará com a Autenticação Básica. Isto será resolvido num futuro próximo.

## <a name="next-steps"></a>Próximos passos
Existem diversos tipos de dados aos quais se pode ligar através do Power BI Desktop. Para obter mais informações sobre origens de dados, consulte os seguintes recursos:

* [O que é o Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Ligar a livros do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Introduzir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
