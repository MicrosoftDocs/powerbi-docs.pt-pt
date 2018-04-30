---
title: Registo de alterações para o Power BI Report Server
description: Este registo de alterações destina-se ao Power BI Report Server e lista novos itens, juntamente com correções de erros para cada compilação lançada.
services: powerbi
documentationcenter: ''
author: jtarquino
manager: jonhp
backup: maggies
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/11/2017
ms.author: tankas
ms.openlocfilehash: 67b9a162d689a8615a3e2459295eab6dad6d2364
ms.sourcegitcommit: 312390f18b99de1123bf7a7674c6dffa8088529f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="changelog-for-power-bi-report-server"></a>Registo de alterações para o Power BI Report Server

Este registo de alterações destina-se ao Power BI Report Server e lista novos itens, juntamente com correções de erros para cada compilação lançada.

Para obter informações detalhadas sobre as novas funcionalidades, veja [Novidades no Power BI Report Server](whats-new.md). 

## <a name="march-2018"></a>Março de 2018
- **Power BI Report Server**
    - *Versão 1.2.6660.39920 (Compilação 15.0.2.389), Lançamento: 28 de março de 2018*
        - Correções de erros
            - Nos Relatórios do Power BI (PBIX), correção de Exportar Dados que não funcionava com os Elementos Visuais do Power BI
            - Nos Relatórios Power BI (PBIX), correção dos filtros de URL que não funcionavam
            - Nos Relatórios Paginados (RDL), correção das imagens que não são apresentadas corretamente no IE11 após a atualização para a versão de março do Power BI Report Server

    - *Versão 1.2.6648.38132 (Compilação 15.0.2.378), Lançamento: 19 de março de 2018*
        - Atualizações de Segurança
        - Melhorias de Acessibilidade
        - Correções de erros
            - Para os Relatórios Paginados (RDL), correção para a visibilidade dos parâmetros num relatório ligado que é revertido após terem sido editadas as suas propriedades
            - Correção para o portal Web com autenticação de formulários personalizada que está a ignorar o cookie de expiração ajustável
            - Correção para exportação do Word que cria uma altura de linha desigual quando a mesma está vazia
            - Para os Relatórios Paginados (RDL), correção para a cadeia de ligação baseada em expressões que é eliminada quando as credencias da origem de dados são alteradas
            - Correção para a capacidade de utilizar KPI com valores de texto
            - Para Relatórios Paginados (RDL), correção para a capacidade de atribuir um novo conjunto de dados a um Relatório Paginado (RDL) existente
            - Outras correções de usabilidade e estabilidade

- **Power BI Desktop (otimizado para o Power BI Report Server)**
    - Versão: 2.56.5023.1043 (março de 2018), Lançamento: 19 de março de 2018
        - Contém as alterações necessárias para a ligação com o Power BI Report Server (março de 2018)

## <a name="october-2017"></a>Outubro de 2017

- **Power BI Report Server**
    - *Versão 1.1.6582.41691 (Compilação 14.0.600.442), Lançamento: 10 de janeiro de 2018*
        - Atualizações de Segurança
        - Correções de Erros
            - Correção do erro devido ao qual Model.GetParameters devolvia 400
            - Correção para a definição de conjuntos de dados partilhados para Relatórios Paginados (RDL) existentes
            - Correção do erro ExecutionNotFoundException ao exportar relatórios com valores de parâmetros diferentes para PDF

    - *Versão 1.1.6551.5155 (Compilação 14.0.600.438), Lançamento: 11 de dezembro de 2017*
        - Correções de Erros
            - Falha ao guardar os dados depois de atualizar determinados relatórios do Power BI Desktop.

    - *Versão 1.1.6530.30789 (Compilação 14.0.600.437), Lançamento: 17 de novembro de 2017*
        - Correções de Erros
            - Correção para Cenários de Autenticação Básica 
            - Correção para dias da semana que não era possível selecionar na página de agendamento para Subscrições, Planos de Atualização da Cache e Instantâneos do Histórico no Portal
            - Para Relatórios Paginados (RDL), a correção para ter expressões em Caixa de texto com a propriedade CanGrow definida como false faz com que os valores não apresentem cores e os tipos de letra não sejam adequados
            - Para Relatórios do Power BI (PBIX), a correção para adicionar Legendas ao gráfico de linhas compõe um elemento visual vazio

    - *Versão 1.1.6514.9163 (Compilação 14.0.600.434), Lançamento: 1 de novembro de 2017*
        - Correções de Erros
            - Correção para problemas de fiabilidade de carregamento para relatórios PBIX com mais de 500 MB
            - Correção para o problema de carregamento de dados para relatórios PBIX com mais de 1 GB

    - *Versão 1.1.6513.3500 (Compilação 14.0.600.433), Lançamento: 31 de outubro de 2017*
        - Funcionalidades
            - Suporte de Modelo de Dados Incorporados
            - Visualização de Livros do Excel (com a integração do Office Online Server ativada)
            - Atualização de Dados Agendada (PBIX)
            - Suporte de Consulta Direta
            - Suporte de Ficheiros Grandes (até 2 GB)
            - API REST pública
            - Suporte de Conjunto de Dados partilhado no Power BI Desktop (através de oData)
            - Suporte de Parâmetro de URL para ficheiros PBIX
            - Melhorias de acessibilidade

- **Power BI Desktop (otimizado para o Power BI Report Server)**
    - *Versão: 2.51.4885.3981 (outubro de 2017), Lançamento: 10 de abril de 2018*
        - Atualizações de Segurança

    - *Versão: 2.51.4885.2501 (outubro de 2017), Lançamento: 10 de janeiro de 2018*
        - Atualizações de Segurança

    - *Versão: 2.51.4885.1423 (Outubro de 2017), Lançamento: 17 de novembro de 2017*
        - Correções de Erros
            - Correção para a falha de execução do Power BI Desktop de 32 bits em SO x86
            - Para Relatórios do Power BI (PBIX), correção para mostrar as linhas de grelha do eixo x
            - Outras pequenas correções de erros

    - *Versão: 2.51.4885.1041 (Outubro de 2017), Lançamento: 31 de outubro de 2017*
        - Funcionalidades
            - Contém as alterações necessárias para a ligação com o Power BI Report Server (Outubro de 2017)

## <a name="june-2017"></a>Junho de 2017

- **Power BI Report Server**
    - *Compilação 14.0.600.309, Lançamento: 10 de janeiro de 2018*
        - Atualizações de Segurança

    - *Compilação 14.0.600.305, Lançamento: 19 de setembro de 2017*  
        - Correções de Erros
            - Atualização para a versão mais recente do [Controlo Web dos Mapas Bing](https://msdn.microsoft.com/library/mt712542.aspx)

    - *Compilação 14.0.600.301, Lançamento: 11 de julho de 2017*
        - Correções de Erros
            - A etiqueta {{UserId}} é resolvida para as credenciais armazenadas em vez do utilizador que executa o relatório nos Relatórios do Power BI
            - A composição de algumas imagens falha nos relatórios do Power BI Report Server
            - Não é possível alterar o nome de um Relatório do Power BI no Power BI Report Server
            - Não é possível carregar Elementos Visuais Personalizados na aplicação móvel do Power BI (exige a reinstalação da aplicação móvel para limpar a cache local)

    - *Compilação 14.0.600.271, Lançamento: 12 de junho de 2017*
        - Versão inicial do Power BI Report Server

- **Power BI Desktop (otimizado para o Power BI Report Server)**
    - *Versão: 2.47.4766.4901 (junho de 2017), Lançamento: 10 de janeiro 2018*
        - Atualizações de Segurança

## <a name="next-steps"></a>Próximos passos

[Manual do utilizador](user-handbook-overview.md)  
[Manual do administrador](admin-handbook-overview.md)  
[Início rápido: instalar o Power BI Report Server](quickstart-install-report-server.md)  
[Instalar o Report Builder](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Transferir o SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
