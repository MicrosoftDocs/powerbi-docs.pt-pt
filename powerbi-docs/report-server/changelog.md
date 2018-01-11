---
title: "Registo de alterações para o Power BI Report Server"
description: "Este registo de alterações destina-se ao Power BI Report Server e lista novos itens, juntamente com correções de erros para cada compilação lançada."
services: powerbi
documentationcenter: 
author: jtarquino
manager: jonhp
backup: maggies
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/17/2017
ms.author: jaimeta
ms.openlocfilehash: e56976943e58aba8c9ef36c576a16ab5eba4c796
ms.sourcegitcommit: 7d4ad2ba92a932d7cc6637348e0774be6623559e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/18/2017
---
# <a name="changelog-for-power-bi-report-server"></a>Registo de alterações para o Power BI Report Server

Este registo de alterações destina-se ao Power BI Report Server e lista novos itens, juntamente com correções de erros para cada compilação lançada.

Para obter informações detalhadas sobre as novas funcionalidades, veja [Novidades no Power BI Report Server](whats-new.md).

## <a name="october-2017"></a>Outubro de 2017

- **Power BI Report Server**
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

## <a name="next-steps"></a>Próximos passos

[Manual do utilizador](user-handbook-overview.md)  
[Manual do administrador](admin-handbook-overview.md)  
[Início rápido: instalar o Power BI Report Server](quickstart-install-report-server.md)  
[Instalar o Report Builder](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Transferir o SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)