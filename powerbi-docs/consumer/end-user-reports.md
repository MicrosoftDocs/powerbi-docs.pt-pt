---
title: Relatórios no serviço Power BI
description: Relatórios no serviço Power BI, para consumidores
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/05/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 3f6f534b71ba6d8e8798418275c4758a95fc6fb5
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73851233"
---
# <a name="reports-in-power-bi"></a>Relatórios no Power BI

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Um relatório do Power BI é uma vista de múltiplas perspetivas sobre um conjunto de dados, com elementos visuais que representam diferentes achados e informações desse conjunto de dados.  Um relatório pode ter um único elemento visual ou páginas cheias de elementos visuais. Consoante a sua função, pode ser um *estruturador* de relatórios. Também pode ser alguém que *consome* ou utiliza relatórios. Este artigo é direcionado para os *consumidores*.

![Captura de ecrã a mostrar uma página de relatórios.](./media/end-user-reports/power-bi-report.png)

A. Este relatório tem seis páginas (ou separadores) e está atualmente a ver a página **Sentiment** (Sentimento).    
B. Nesta página, existem cinco elementos visuais diferentes e um título de página.    
C. O painel *Filters* (Filtros) mostra um filtro aplicado a todas as páginas do relatório. Para fechar o painel Filters (Filtros), selecione a seta ( **>** ).    
D. A faixa do Power BI apresenta o nome do relatório e a data da última atualização. Selecione a seta para abrir um menu que também mostra o nome do proprietário do relatório.    
E. A barra de ação contém ações que pode executar neste relatório.  Por exemplo, pode adicionar um comentário, ver um indicador ou exportar dados do relatório.  Selecione **Mais opções** (...) para revelar uma lista de funcionalidades de relatório adicionais.    

Se for um novo utilizador do Power BI, pode obter uma boa base de aprendizagem ao ler os [Conceitos básicos para os consumidores do serviço Power BI](end-user-basic-concepts.md). Os relatórios estão disponíveis para visualização, partilha e criação de notas em dispositivos móveis. Para obter mais informações, veja [Explorar relatórios nas aplicações móveis do Power BI](mobile/mobile-reports-in-the-mobile-apps.md).

## <a name="advantages-of-reports"></a>Vantagens dos relatórios

O Power BI baseia um relatório num único conjunto de dados. Os *estruturadores* de relatórios criam os elementos visuais que representam um grupo de informações num relatório. Os elementos visuais não são estáticos.  São atualizados à medida que os dados subjacentes sofrem alterações. Pode interagir com os elementos visuais e os filtros à medida que explora os dados para descobrir informações e procurar respostas. Tal como um dashboard, um relatório é altamente interativo e personalizável.

### <a name="safely-interact-with-content"></a>Interagir com conteúdos de forma segura

À medida que explora e interage com os seus conteúdos, ao filtrar, segmentar dados, subscrever e exportar, não pode danificar o funcionamento dos relatórios. O seu trabalho não afeta o conjunto de dados subjacente ou os conteúdos partilhados originais. Esta afirmação aplica-se a dashboards, relatórios e aplicações.

> [!NOTE]
> Lembre-se de que não pode danificar os seus dados. O Power BI é um excelente local para explorar e experimentar sem se preocupar com a possibilidade de danificar dados.

### <a name="save-your-changes-or-revert-to-the-default-settings"></a>Guardar as suas alterações ou reverter para as predefinições

Esta ação não significa que não pode guardar as suas alterações. Pode fazê-lo, mas essas alterações só irão afetar a sua vista dos conteúdos. Para reverter para a vista predefinida original do relatório, selecione **Repor para predefinição**.

![Captura de ecrã a mostrar o ícone Reverter para predefinição.](./media/end-user-reports/power-bi-reset.png)

## <a name="dashboards-versus-reports"></a>Dashboards versus relatórios

Os [Dashboards](end-user-dashboards.md) costumam ser confundidos com relatórios pois também são telas preenchidas com elementos visuais. No entanto, existem algumas diferenças importantes.  

| **Capacidade** | **Dashboards** | **Relatórios** |
| --- | --- | --- |
| Páginas |Uma página |Uma ou mais páginas |
| Origens de dados |Um ou mais relatórios e um ou mais conjuntos de dados por dashboard |Um único conjunto de dados por relatório |
| Filtragem |Não pode filtrar nem segmentar |Várias formas diferentes de filtrar, realçar e segmentar |
| Definir alertas |Pode criar alertas para que lhe seja enviado um e-mail quando um dashboard cumpre determinadas condições |Não |
| Feature |Pode definir um dashboard como o seu dashboard em destaque |Não pode criar um relatório em destaque |
| Pode ver as tabelas e os campos de conjuntos de dados subjacentes |Não. Pode exportar dados, mas não pode ver os campos e tabelas do conjunto de dados no próprio dashboard |Yes. Pode ver campos e tabelas de conjuntos de dados e valores para os quais tem permissões de visualização |
| Personalização |Não  |Pode filtrar, exportar, ver conteúdos relacionados, adicionar marcadores, gerar códigos QR, analisar no Excel e mais |

<!--| Available in Power BI Desktop |No |Yes, can create and view reports in Desktop |
| Pinning |Can pin existing visuals (tiles) only from current dashboard to your other dashboards |Can pin visuals (as tiles) to any of your dashboards. Can pin entire report pages to any of your dashboards. | -->

## <a name="report-designers-and-report-consumers"></a>Estruturadores e consumidores de relatórios

Consoante a sua função, pode ser um *estruturador*, isto é, uma pessoa que cria relatórios para sua utilização ou para partilhar com colegas. Assim, vai querer saber como pode criar e partilhar relatórios.

Em alternativa, pode ser um *consumidor*, isto é, uma pessoa que recebe relatórios de terceiros. Vai querer saber como pode compreender e interagir com os relatórios. Se for um *consumidor* de relatórios, veja estas ligações:

* Comece por uma [apresentação do serviço Power BI](end-user-basic-concepts.md) para saber onde procurar relatórios e ferramentas de relatórios.
* Saiba como [abrir um relatório](end-user-report-open.md) e todas as [interações disponíveis para os consumidores](end-user-reading-view.md).
* Conheça melhor os relatórios ao ver uma apresentação de um dos nossos [exemplos](../sample-tutorial-connect-to-the-samples.md).  
* Para ver que conjunto de dados está a ser utilizado pelo relatório e que dashboards estão a apresentar elementos visuais do relatório (*marcadores*), veja [Ver conteúdos relacionados no serviço Power BI](end-user-related.md).

> [!TIP]
> Se não encontrou aqui o que procurava, utilize o índice à esquerda para procurar todos os artigos sobre *Relatórios*.

## <a name="next-steps"></a>Próximos passos

[Abrir e ver um relatório](end-user-report-open.md)    
[Dashboards no serviço Power BI](end-user-dashboards.md)