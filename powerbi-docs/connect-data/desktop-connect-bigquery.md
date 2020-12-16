---
title: Ligar a uma base de dados Google BigQuery no Power BI Desktop
description: Ligar e utilizar facilmente o Google BigQuery no Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 09/30/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: f3c38b545cfec5c836356db6c4d42d524af129e6
ms.sourcegitcommit: 46cf62d9bb33ac7b7eae7910fbba6756f626c65f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97491926"
---
# <a name="connect-to-a-google-bigquery-database-in-power-bi-desktop"></a>Ligar a uma base de dados Google BigQuery no Power BI Desktop
No Power BI Desktop, pode ligar a uma base de dados Google **BigQuery** e utilizar os dados subjacentes, tal como faria com outra origem de dados no Power BI Desktop.

## <a name="connect-to-google-bigquery"></a>Ligar ao Google BigQuery
Para ligar a uma base de dados **Google BigQuery**, selecione **Obter Dados** no friso **Base** do Power BI Desktop. Selecione **Base de Dados** nas categorias no lado esquerdo e verá **Google BigQuery**.

![Caixa de diálogo Obter Dados para o Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_01.png)

Na janela do **Google BigQuery** que aparece, inicie sessão na sua conta do Google BigQuery e selecione **Ligar**.

![Iniciar sessão no Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_02.png)

Quando iniciar sessão, verá a seguinte janela a indicar que foi autenticado. 

![Iniciou sessão no Google](media/desktop-connect-bigquery/connect_bigquery_02b.png)

Depois de a ligação ser concluída com êxito, é apresentada uma janela **Navegador**, que apresenta os dados disponíveis no servidor, dos quais pode selecionar um ou vários elementos para importar e utilizar no **Power BI Desktop**.

![Dados do Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_03.png)

## <a name="considerations-and-limitations"></a>Considerações e Limitações
Existem alguns limites e aspetos a ter em conta com o conector do **Google BigQuery**:

* O conector do Google BigQuery está disponível no Power BI Desktop e no serviço Power BI. No serviço Power BI, é possível aceder ao conector através da ligação entre clouds do Power BI ao Google BigQuery.

* Pode utilizar o Power BI com o **Billing Project** (Projeto de Faturação) do Google BigQuery. Por predefinição, o Power BI utiliza o primeiro projeto da lista devolvido ao utilizador. 

  Para personalizar o comportamento do Projeto de Faturação quando o utiliza com o Power BI, especifique a seguinte opção no M subjacente no passo Origem de Dados, que pode ser personalizada com o **Editor do Power Query** no Power BI Desktop:

  ```
  Source = GoogleBigQuery.Database([BillingProject="Include-Billing-Project-Id-Here"])
  ```

  A partir da versão de setembro de 2020, permitimos o suporte para a [API de Armazenamento Google BigQuery](https://cloud.google.com/bigquery/docs/reference/storage). Esta funcionalidade está ativada por predefinição e é controlada pelo argumento booleano opcional denominado "UseStorageApi". Alguns clientes poderão encontrar problemas com esta caraterística se usarem permissões granulares. Neste cenário, poderá ver a seguinte mensagem de erro:

  `ERROR [HY000] [Microsoft][BigQuery] (131) Unable to authenticate with Google BigQuery Storage API. Check your account permissions`

  Pode resolver este problema ao ajustar as permissões de utilizador para a API de Armazenamento. Atribua estas permissões da API de Armazenamento:

  - `bigquery.readsessions.create` – Cria uma nova sessão de leitura através da API de Armazenamento BigQuery.
  - `bigquery.readsessions.getData` – Lê dados de uma sessão de leitura através da API de Armazenamento BigQuery.
  - `bigquery.readsessions.update` – Atualiza uma sessão de leitura através da API de Armazenamento BigQuery.

  Estas permissões normalmente são fornecidas na função BigQuery.User. Para obter mais informações, veja [Funções e permissões predefinidas do Google BigQuery](https://cloud.google.com/bigquery/docs/access-control).
  
  Se os passos anteriores não resolverem o problema ou se quiser desativar o suporte da API de Armazenamento, altere a sua consulta para a seguinte:
  ```
  Source = GoogleBigQuery.Database([UseStorageApi=false])
  ```
  Em alternativa, se já estiver a utilizar um projeto de faturação, altere a consulta para a seguinte:
  ```
  Source = GoogleBigQuery.Database([BillingProject="Include-Billing-Project-Id-Here", UseStorageApi=false])
  ```

## <a name="next-steps"></a>Próximos passos
Existem diversos tipos de dados aos quais se pode ligar através do Power BI Desktop. Para obter mais informações sobre origens de dados, consulte os seguintes recursos:

* [O que é o Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Ligar a livros do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Introduzir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
