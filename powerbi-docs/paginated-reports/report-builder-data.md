---
title: Dados de relatórios no Report Builder do Power BI
description: O primeiro passo para estruturar um relatório no Report Builder do Power BI é criar origens de dados e conjuntos de dados que representem os dados subjacentes do relatório.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.custom: seodec18
ms.date: 06/06/2019
ms.openlocfilehash: fea4e4927b009e30bc040593f9237cc49ff73956
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/07/2020
ms.locfileid: "78921453"
---
# <a name="report-data-in-power-bi-report-builder"></a>Dados de relatórios no Report Builder do Power BI

Os dados de relatórios podem ser provenientes de múltiplas origens de dados na sua organização. O primeiro passo para estruturar um relatório no Report Builder do Power BI é criar origens de dados e conjuntos de dados que representem os dados subjacentes do relatório. Cada origem de dados inclui informações de ligação de dados. Cada conjunto de dados inclui um comando de consulta que define o conjunto de campos a utilizar como dados de uma origem de dados. Para visualizar os dados de cada conjunto de dados, adicione uma região de dados, como uma tabela, matriz, gráfico ou mapa. Quando o relatório é processado, as consultas são executadas na origem de dados e cada região de dados aumenta, conforme necessário, para apresentar os resultados da consulta para o conjunto de dados.  

Saiba como [Criar uma origem de dados incorporada para relatórios paginados no Report Builder do Power BI](paginated-reports-embedded-data-source.md).


##  <a name="BkMk_ReportDataTerms"></a> Termos  
  
- **Ligação de dados.** Também conhecida como uma *origem de dados*. Uma ligação de dados inclui um nome e propriedades de ligação que dependem do tipo de ligação. Por predefinição, uma ligação de dados não inclui credenciais. Uma ligação de dados não especifica os dados a recuperar a partir da origem de dados externa. Para tal, especifique uma consulta ao criar um conjunto de dados.  
  
- **Cadeia de ligação.** Uma cadeia de ligação é uma versão da cadeia de carateres das propriedades de ligação que são necessárias para ligar a uma origem de dados. As propriedades de ligação variam com base no tipo de ligação de dados.  
  
- **Origem de dados incorporada.** Também conhecida como uma *origem de dados específica do relatório*. Uma origem de dados que é definida num relatório e utilizada apenas por esse relatório.  
  
- **Credenciais.** As credenciais são as informações de autenticação que têm de ser fornecidas para lhe permitir aceder a dados externos.  
  
##  <a name="BkMk_ReportDataTips"></a> Sugestões para especificar os dados de relatório

 Utilize as seguintes informações para estruturar a sua estratégia de dados do relatório.  
  
- **Filtrar dados** Os dados de relatório podem ser filtrados na consulta ou no relatório. Pode utilizar variáveis de conjuntos de dados e de consulta para criar parâmetros em cascata e fornecer a um utilizador a capacidade para restringir as opções de milhares de seleções para um número mais gerível. Pode filtrar dados numa tabela ou gráfico com base nos valores de parâmetros ou noutros valores que especifique.  
  
- **Parâmetros** Comandos de consulta de conjuntos de dados que incluem variáveis de consulta criam automaticamente parâmetros de relatório correspondentes. Também pode criar parâmetros manualmente. Ao ver um relatório, a barra de ferramentas do relatório apresenta os parâmetros. Os utilizadores podem selecionar valores para controlar os dados de relatório ou o aspeto do relatório. Para personalizar os dados de relatório para públicos específicos, pode criar conjuntos de parâmetros de relatório com valores predefinidos diferentes associados à mesma definição de relatório ou utilizar o campo **UserID** incorporado. 
  
- **Agrupar e agregar dados** Os dados de relatório podem ser agrupados e agregados na consulta ou no relatório. Se agregar valores na consulta, pode continuar a combinar os valores no relatório de acordo com as restrições do que é significativo.  
  
- **Ordenar dados** Os dados de relatório podem ser ordenados na consulta ou no relatório. Nas tabelas, também pode adicionar um botão de ordenação interativo para permitir que o utilizador controle a sequência de ordenação.  
  
- **Dados com base em expressões** Porque a maioria das propriedades do relatório pode ser baseada em expressões e as expressões podem incluir referências a campos do conjunto de dados e a parâmetros de relatório, pode escrever expressões avançadas para controlar os dados de relatório e o aspeto. Pode fornecer a um utilizador a capacidade de controlar os dados que vê através da definição de parâmetros.  
  
- **Apresentar dados de um conjunto de dados** Os dados de um conjunto de dados são normalmente apresentados numa ou mais regiões de dados, por exemplo, uma tabela e um gráfico.  
  
- **Apresentar dados de múltiplos conjuntos de dados** Pode escrever expressões numa região de dados com base num conjunto de dados que procura valores ou está agregado noutros conjuntos de dados. Pode incluir sub-relatórios numa tabela com base num conjunto de dados para apresentar dados de uma origem de dados diferente.  
  
 Utilize a seguinte lista para ajudar a definir origens de dados para um relatório.  
  
- Compreenda a arquitetura de camada de dados de software para a sua organização e os potenciais problemas resultantes dos tipos de dados. Compreenda como as extensões de dados e as extensões de processamento de dados podem afetar os resultados da consulta. Os tipos de dados variam entre a origem de dados, os fornecedores de dados e os tipos de dados armazenados no ficheiro de definição do relatório (.rdl).  
  
- As origens de dados e os conjuntos de dados são criados num relatório e publicados no serviço Power BI. Depois de serem publicados, pode configurar as credenciais diretamente no serviço Power BI ou no Gateway da Empresa. 

## <a name="next-steps"></a>Próximos passos

- [O que são relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
- [Orientação para a obtenção de dados para relatórios paginados](../guidance/report-paginated-data-retrieval.md)
