---
title: Registo de alterações do Power BI Report Server
description: Este registo de alterações destina-se ao Power BI Report Server e lista novos itens, juntamente com correções de erros para cada compilação lançada.
ms.author: jaimeta
author: jtarquino
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 03/02/2020
ms.openlocfilehash: 0a8cf16ddf7fe9e091599f1790a37a83b9923240
ms.sourcegitcommit: d65da4738f011beec8f4423085cbd483511cdfb0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/03/2020
ms.locfileid: "78237966"
---
# <a name="change-log-for-power-bi-report-server"></a>Registo de alterações do Power BI Report Server

Este registo de alterações destina-se ao Power BI Report Server e lista novos itens, juntamente com correções de erros para cada compilação lançada.

Para obter informações detalhadas sobre as novas funcionalidades, veja [Novidades no Power BI Report Server](whats-new.md). 


## <a name="january-2020"></a>Janeiro de 2020
- **Power BI Report Server**
    - *Versão: 1.6.7364.4075 (Compilação 15.0.1102.777), Lançamento: 2 de março de 2020*
         - Correções de Erros
           -  Correção dos relatórios do Power BI em que não é possível carregar para determinadas origens de dados
           -  Correção da localização de transferência da ligação do Power BI Report Server Desktop no portal
           -  Correção do DynamicImageDPI para composição do Excel
           -  Correção das ligações do Oracle que utilizam uma cultura de thread incorreta em determinados cenários de vários utilizadores
           -  Correção do valor predefinido de CustomHeaders que causa falhas na incorporação de relatórios
           -  Correção dos nomes de parâmetros SQL gerados incorretamente em certos casos
    - *Versão: 1.6.7327.3007 (Compilação 15.0.1102.759), Lançamento: 23 de janeiro de 2020*
         - Funcionalidades
            -  Exportar para o Excel a partir dos relatórios do Power BI.
           -  Suporte dos conjuntos de dados do Power BI Premium para relatórios paginados.
           -  Suporte do AltText (texto alternativo) para elementos de relatório paginado.
           -  Suporte dos cabeçalhos personalizados.
           -  Suporte das Instâncias Geridas do SQL do Azure como catálogo.
           -  Encriptação de Base de Dados Transparente do catálogo.
        - Atualizações de segurança
        - Correções de erros
            - Correções da acessibilidade para leitores de ecrã, composição de relatórios e navegação através do teclado.
            - Correção para guardar os títulos dos Relatórios de múltiplos bytes.
            - Correção do registo verboso que afeta a fiabilidade do servidor de relatórios.
          - Correção para garantir dados em direto nos relatórios do Power BI em dispositivos móveis.
          - Correção para aplicar realces entre elementos visuais como elementos visuais numa exportação filtrada nos relatórios do Power BI.
          - Correção da escrita de rodapé ao exportar para o Word com expressão de visibilidade para os relatórios paginados. 
     
- **Power BI Desktop (otimizado para o Power BI Report Server)**
    - *Versão: 2.76.5678.1521 (janeiro de 2020), Lançamento: 23 de janeiro de 2020* (nova compilação e nova versão)
        - Contém as alterações necessárias para a ligação ao Power BI Report Server (janeiro de 2020)        


## <a name="september-2019"></a>Setembro de 2019
- **Power BI Report Server**
    - *Versão: 1.6.7236.4246 (Compilação 15.0.1102.646), Lançamento: 25 de outubro de 2019*
        - Atualizações de segurança
        - Correções de erros
            - Correção para o .NET Framework 4.7 não instalado.
            - Correção para relatórios paginados Teradata com parâmetros de valores múltiplos com o erro 110083.
            - A correção para o valor URLRoot não funciona se houver múltiplos enlaces de URL de serviço Web e um dos mesmos for https://+80/reportserver.
          - Correção para valores de parâmetros com múltiplos valores em relatórios paginados que aparecem fora da área do relatório.
          
    - *Versão: 1.6.7221.30698 (Compilação 15.0.1102.620), Lançamento: 9 de outubro de 2019*
        - Correções de erros
            - Correção do elemento visual personalizado do Filtro de Texto.
            - Correção do desempenho da lista pendente de segmentação de dados.
            - Correção para Retirar o PII da telemetria.
          - Correção para os URLs não serem sensíveis às maiúsculas e minúsculas.
          
    - *Versão 1.6.7206.38019 (Compilação 15.0.1102.597), lançada a: 26 de setembro de 2019*
        - Atualizações de segurança
        - Correções de erros
           - Relatórios paginados
             - Correção dos problemas de acessibilidade encontrados ao utilizar o Internet Explorer e o Microsoft Edge.
             - Correção de problemas de SAP HANA durante testes de ligação.
             - Correção de problemas encontrados ao fornecer a lista de endereços de e-mail.
             - Correção para relatórios do Power BI que utilizem uma origem de dados do DirectQuery e autenticação integrada.
             - Correção para relatórios Paginados para serem compostos com parâmetros de filtro quando o instantâneo é ativado.
             - Correção para a execução dupla de procedimentos armazenados durante a execução do relatório.
             - Correção da concessão de permissões de início de sessão do SQL Server à conta de serviço predefinida, quando a conta de serviço está configurada para executar o Power BI Report Server.
             - Correção para o acesso a relatórios durante a atualização no fuso horário japonês.
             - Correção para modelos obsoletos quando uma nova versão do relatório é carregada durante a atualização.
             - Correção para os valores de parâmetros que contêm o caráter "&".
         - Capacidade de programação
             - API Web atualizada: /PowerBIReports({Id})/DataSources (PATCH) para permitir atualizações de cadeia de ligação.
         
- **Power BI Desktop (otimizado para o Power BI Report Server)**
    - *Versão: 2.73.5586.1501 (setembro de 2019), Lançamento: 25 de outubro de 2019*
        - Correções de erros
            - Correção para Telemetria.
            
    - *Versão: 2.73.5586.1241 (setembro de 2019), Lançamento: 9 de outubro de 2019*
        - Correções de erros
            - Correção do elemento visual personalizado do Filtro de Texto.
            - Correção do desempenho da lista pendente de segmentação de dados.
            - Correção para Retirar o PII da telemetria.
            
    - *Versão: 2.73.5586.821 (setembro de 2019), Lançamento: 26 de setembro de 2019* (nova compilação e nova versão)
        - Contém as alterações necessárias para a ligação ao Power BI Report Server (setembro de 2019)

    
## <a name="may-2019"></a>Maio de 2019

- **Power BI Report Server**          
    - *Versão 1.5.7074.36177 (Compilação 15.0.1102.371), lançada a 21 de maio de 2019*
        - Correções de Erros
            - Relatórios Paginados
                - Correção para permitir sempre a incorporação de tipo de letra de PDF.
                - Correção para definir os cookies enviados por HTTPS como Seguros
                - Correção de problemas com pop-ups devido a erros de script
                - Correção de erros de apresentação da Aplicação Móvel em telemóveis Android
                - Correção para que o Navegador de Tempo de Relatórios Móveis mostre os números da semana corretos, independentemente do início do Ano fiscal
                - Foi adicionada a propriedade configurável "RestrictedResourceMimeTypeForUpload" para administradores especificarem tipos de MIME banidos
         - Funcionalidades
            - Adição de suporte de Elementos Visuais Fidedignos para PBIRS

- **Power BI Desktop (otimizado para o Power BI Report Server)**
    - *Versão: 2.69.5467.1801 (maio de 2019), lançada a 21 de maio de 2019*
        - Correções de erros
            - Correção para evitar a reintrodução de credenciais durante o carregamento de ficheiros PBIX para o PBIRS
            - Correções na abertura de documentos com # no nome de ficheiro
            - Adição de uma ligação para retroceder mais facilmente na Janela de seleção do PBIRS
            - Correção do modo Alto Contraste no PBIRS para apresentar o botão Anterior e mostrar mensagens visuais de aviso.
            - Correções da IU do painel Seleção, dimensionamento da tela.

    - *Versão: 2.69.5467.5201 (maio de 2019). Lançamento: 30 de julho de 2019*
        - Correções de erros
            - Correção do registo de telemetria incorreto

## <a name="january-2019"></a>Janeiro de 2019

- **Power BI Report Server**          
    - *Versão 1.4.7024.16477 (Compilação 15.0.1102.299), lançada a 28 de março de 2019*
        - Correções de Erros
            - Relatórios do Power BI
                - Correção de um problema com as credenciais básicas ao utilizar o DirectQuery para SAP Hana e SAP BW
                - Correção de falhas na atualização de dados do feed OData em que era apresentada a mensagem "Could not load file or assembly 'Microsoft.OData.Core.NetFX35.V7" (Não foi possível carregar o ficheiro ou assemblagem 'Microsoft.OData.Core.NetFX35.V7)

- **Power BI Report Server**            
    - *Versão 1.4.6969.7395 (Compilação 15.0.1102.235), Lançamento: 30 de janeiro de 2019*
        - Correções de Erros
            - Relatórios do Power BI
                - Correção do problema com as credenciais básicas ao utilizar a consulta direta
                - Correção das relações bidirecionais com filtros de segurança ao nível da linha aplicados
                - Correção dos dados obsoletos após uma atualização do modelo num ambiente de escalamento horizontal
                - Correção da barra de deslocamento dupla para a tabela/matriz no Firefox 63 ou superior
                - Correção do tamanho do ícone +/- no Internet Explorer
            - Relatórios Paginados
                - Correção do problema com a atualização da utilização de uma origem de dados partilhada para um relatório

    - *Versão 1.4.6960.38798 (Compilação 15.0.1102.222), Lançamento: 22 de janeiro de 2019*
        - Funcionalidades
            - Relatórios do Power BI 
                - Suporte para a segurança ao nível da linha
                - Ações de expandir e fechar em cabeçalhos de linha de matriz
                - Copiar e colar entre ficheiros .pbix
                - Guias de alinhamento inteligentes
                - Suporte para o Conector do SAP BW 2.0
            - Administradores
                - Capacidade de restringir extensões de recursos que podem ser carregadas para o servidor de relatórios
                - Capacidade de restringir esquemas de hiperligações suportados
            - Capacidade de programação
                - Nova API Web: /PowerBIReports({Id})/DataModelRoles (GET)
                - Nova API Web: /PowerBIReports({Id})/DataModelRoleAssignments (GET & PUT)
                - Ver [API REST do Power BI Report Server](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0) para obter mais detalhes
        - Correções de Erros
            - Vulnerabilidade de Injeção de HMTL
            - A funcionalidade Exportar para PDF não está a apresentar o símbolo de Euro
            - Guardar uma palavra-passe com múltiplas origens de dados em relatórios do Power BI invalida as palavras-passe não alteradas
            - Os elementos visuais apresentam problemas na Aplicação Power BI Mobile após estarem inativos

- **Power BI Desktop (otimizado para o Power BI Report Server)**
    - *Versão: 2.65.5313.1562 (janeiro de 2019), Lançamento: 30 de janeiro de 2019*
        - O atalho e os ícones afixados permanecem depois de desinstalar o Power BI Report Server
        - Correção da afixação do Power BI Report Server apresentar texto preto num ícone preto no menu Iniciar

    - *Versão: 2.65.5313.1421 (janeiro de 2019), Lançamento: 22 de janeiro de 2019* (nova compilação e nova versão)
        - Contém as alterações necessárias para a ligação ao Power BI Report Server (janeiro de 2019) 
    - *Versão: 2.65.5313.5141 (janeiro de 2019). Lançamento: 31 de julho de 2019* (nova compilação e nova versão)
        - Correções de erros
            - Correção do registo de telemetria incorreto

## <a name="august-2018"></a>Agosto de 2018

- **Power BI Report Server**
    - *Versão 1.3.6816.37243 (Compilação 15.0.2.557), Lançamento: 30 de agosto de 2018*
        - Correções de erros
            - Foi corrigido um problema em que o redirecionamento de enlace não era atualizado quando o servidor era atualizado de versões anteriores do Servidor de Relatórios do PBI. Os clientes viam o seguinte:      
            *`
            Failed to load expression host assembly. Details: Could not load file or assembly 'Microsoft.ReportingServices.ProcessingObjectModel, Version=2018.7.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040) (rsErrorLoadingExprHostAssembly)
             `*
             
            - Encontra-se agora corrigido o erro de Transparência da Etiqueta de Dados.
            
    - *Versão 1.3.6801.38816 (Compilação 15.0.2.540), Lançamento: 15 de agosto de 2018*
        - Funcionalidades
            - Agora os Relatórios do Power BI suportam o DirectQuery SSO SAP HANA com o Kerberos
            - API de Elemento Visual Personalizado fornecida com o lançamento – versão 1.13.0
            - Os elementos visuais personalizados serão revertidos para uma versão anterior compatível com a versão atual da API do servidor (caso compatível)

- **Power BI Desktop (otimizado para o Power BI Report Server)**
    - *Versão: 2.61.5192.641 (agosto de 2018), Lançamento: 15 de agosto de 2018*
        - Contém as alterações necessárias para a ligação com o Power BI Report Server (agosto de 2018)         
    - *Versão: 2.61.5192.7701 (agosto de 2018), Lançamento: 8 de agosto de 2019* (nova compilação e nova versão)
        - Correções de erros
            - Correção do registo de telemetria incorreto
            
## <a name="march-2018"></a>Março de 2018

- **Power BI Report Server**
    - *Versão 1.2.6690.34729 (Compilação 15.0.2.402), Lançamento: 27 de abril de 2018*
        - Correções de erros
            - Permitir a migração de catálogos do SQL Server Reporting Services 2017
            - Para Relatórios do Power BI (PBIX)
                - Os Relatórios podem ser atualizados quando um servidor é configurado para utilizar a autenticação personalizada
                - Modificar as propriedades de um relatório não repõe as credenciais de origem de dados
            - Para Relatórios Paginados (RDL)
                - A utilização de funções derivativas ou de `Lookup()`, como `LookupSet()` e `MultiLookup()` em Expressões de RDL já não resulta em `#Error`
                - Os relatórios ligados respeitam o tamanho da página do relatório de destino durante a impressão
                - Podem ser criadas subscrições de relatórios ligados que utilizem parâmetros em cascata
                - As predefinições de parâmetros de valores múltiplos podem ser modificadas com o IE11
                - As opções de entrega de subscrições condicionada por dados são editáveis
                - As subscrições podem ser visualizadas e editadas enquanto a subscrição está a ser executada
                - Definir as credenciais da origem de dados não remove as cadeias de ligação baseadas em expressões
            - Para KPIs
                - As linhas de tendência são atualizadas quando os dados são atualizados
            - Melhorias gerais de estabilidade

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
    - *Versão 1.1.6582.41691 (Compilação 14.0.600.442), Lançamento: 10 de Janeiro de 2018*
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

    - *Versão: 2.51.4885.2501 (outubro de 2017), Lançamento: 10 de Janeiro de 2018*
        - Atualizações de Segurança

    - *Versão: 2.51.4885.1423 (outubro de 2017), Lançamento: 17 de novembro de 2017*
        - Correções de Erros
            - Correção para a falha de execução do Power BI Desktop de 32 bits em SO x86
            - Para Relatórios do Power BI (PBIX), correção para mostrar as linhas de grelha do eixo x
            - Outras pequenas correções de erros

    - *Versão: 2.51.4885.1041 (outubro de 2017), Lançamento: 31 de outubro de 2017*
        - Funcionalidades
            - Contém as alterações necessárias para a ligação com o Power BI Report Server (Outubro de 2017)

## <a name="june-2017"></a>Junho de 2017

- **Power BI Report Server**
    - *Compilação 14.0.600.309, Lançamento: 10 de Janeiro de 2018*
        - Atualizações de Segurança

    - *Compilação 14.0.600.305, Lançamento: 19 de setembro de 2017*  
        - Correções de Erros
            - Atualização para a versão mais recente do [Controlo Web dos Mapas Bing](https://msdn.microsoft.com/library/mt712542.aspx)

    - *Compilação 14.0.600.301, Lançamento: 11 de julho de 2017*
        - Correções de Erros
            - A etiqueta `{{UserId}}` é resolvida para as credenciais armazenadas em vez do utilizador que executa o relatório nos Relatórios do Power BI
            - A composição de algumas imagens falha nos relatórios do Power BI Report Server
            - Não é possível alterar o nome de um Relatório do Power BI no Power BI Report Server
            - Não é possível carregar Elementos Visuais Personalizados na aplicação móvel do Power BI (exige a reinstalação da aplicação móvel para limpar a cache local)

    - *Compilação 14.0.600.271, Lançamento: 12 de junho de 2017*
        - Versão inicial do Power BI Report Server

- **Power BI Desktop (otimizado para o Power BI Report Server)**
    - *Versão: 2.47.4766.4901 (Junho de 2017), Lançamento: 10 de Janeiro de 2018*
        - Atualizações de Segurança

## <a name="next-steps"></a>Próximos passos

[O que é o Power BI Report Server?](get-started.md)
[Descrição geral para administradores](admin-handbook-overview.md)  
[Instalar o Power BI Report Server](install-report-server.md)  
[Transferir o Report Builder](https://www.microsoft.com/download/details.aspx?id=53613)  
[Transferir o SQL Server Data Tools (SSDT)](https://go.microsoft.com/fwlink/?LinkID=616714)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
