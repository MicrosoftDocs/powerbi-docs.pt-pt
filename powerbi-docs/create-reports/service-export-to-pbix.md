---
title: Transferir um relatório do serviço Power BI para o Power BI Desktop (Pré-visualização)
description: Transferir um relatório do serviço Power BI para um ficheiro do Power BI Desktop
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 07/14/2020
LocalizationGroup: Reports
ms.openlocfilehash: c83b7d1e52a0d443c52348bec91f935e288830d4
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96388684"
---
# <a name="download-a-report-from-the-power-bi-service-to-power-bi-desktop-preview"></a>Transferir um relatório do serviço Power BI para o Power BI Desktop (Pré-visualização)
      
No Power BI Desktop, pode publicar um relatório (um ficheiro *.pbix*) do seu computador local no serviço Power BI. Os relatórios do Power BI também podem ir noutra direção: Pode transferir um relatório do serviço Power BI para o Power BI Desktop. A extensão de um relatório do Power BI, em ambos os casos, é .pbix.

Existem algumas limitações a ter em conta, que são abrangidas na secção [Considerações e resolução de problemas](#considerations-and-troubleshooting) deste artigo.

![Menu pendente Ficheiro](media/service-export-to-pbix/power-bi-file-export.png)

## <a name="download-the-report-as-a-pbix-file"></a>Transferir o relatório como ficheiro .pbix

Só pode transferir relatórios que tenham [criados com o Power BI Desktop](/learn/modules/publish-share-power-bi/2-publish-reports) após 23 de novembro de 2016 e atualizados desde então. Se tiver sido criado antes disso, a opção **Transferir relatório** no serviço Power BI ficará indisponível.

Para transferir o ficheiro .pbix, siga estes passos:

1. No serviço Power BI, abra o relatório que pretende transferir na [Vista de edição](./service-interact-with-a-report-in-editing-view.md).

2. No painel de navegação superior, selecione **Ficheiro > Transferir relatório**.
   
3. Enquanto o relatório estiver a ser transferido, o progresso será apresentado numa faixa de estado. Quando o ficheiro estiver pronto, terá de escolher onde guardar o ficheiro .pbix. O nome predefinido do ficheiro corresponde ao título do relatório.
   
4. Se ainda não o fez, [instale o Power BI Desktop](../fundamentals/desktop-get-the-desktop.md) e, em seguida, abra o ficheiro .pbix no Power BI Desktop.
   
    Quando abrir o relatório no Power BI Desktop, poderá ver uma mensagem a avisá-lo de que algumas das funcionalidades disponíveis no relatório do serviço Power BI não estarão disponíveis no Power BI Desktop.
   
    ![Caixa de diálogo de aviso](media/service-export-to-pbix/power-bi-export-to-pbix_2.png)

5. O editor de relatórios no Power BI Desktop é semelhante ao editor de relatórios no serviço Power BI.  
   
    ![Editor de relatórios do Power BI Desktop](media/service-export-to-pbix/power-bi-desktop.png)

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas

Existem algumas considerações e limitações importantes associadas à transferência de um ficheiro .pbix do serviço Power BI.

* Para transferir o ficheiro, tem de ter acesso de edição ao relatório.
* O relatório deverá ter sido criado com o Power BI Desktop e *publicado* no serviço Power BI, ou o ficheiro .pbix deverá ter sido *carregado* para o serviço Power BI.
* Os relatórios têm de ter sido publicados ou atualizados após 23 de novembro de 2016. Os relatórios publicados anteriormente não são transferíveis.
* Esta funcionalidade não é compatível com relatórios e pacotes de conteúdos originalmente criados no serviço Power BI.
* Utilize sempre a versão mais recente do Power BI Desktop ao abrir ficheiros transferidos. Os ficheiros .pbix transferidos poderão não ser abertos em versões não atuais do Power BI Desktop.
* Se o seu administrador tiver desativado a capacidade de transferir dados, esta funcionalidade não estará visível no serviço Power BI.
* Não é possível transferir um conjunto de dados com atualização incremental para um ficheiro .pbix.
* Os conjuntos de dados ativados para [grandes modelos](../admin/service-premium-large-models.md) não podem ser transferidos para um ficheiro .pbix.
* Os conjuntos de dados modificados pelo [ponto final XMLA](../admin/service-premium-connect-tools.md) não podem ser transferidos para um ficheiro .pbix.
* Se criar um relatório do Power BI baseado num conjunto de dados numa área de trabalho e o publicar numa área de trabalho diferente, este relatório não poderá ser transferido nem por si nem pelos utilizadores. A funcionalidade de transferência não é suportada neste cenário.

## <a name="next-steps"></a>Próximos passos

Veja o vídeo de um minuto do canal **Guy in a Cube** sobre esta funcionalidade:

<iframe width="560" height="315" src="https://www.youtube.com/embed/ymWqU5jiUl0" frameborder="0" allowfullscreen></iframe>

Eis alguns artigos adicionais que o podem ajudar a saber como utilizar o serviço Power BI:

* [Relatórios no Power BI](../consumer/end-user-reports.md)
* [Conceitos básicos para designers no serviço Power BI](../fundamentals/service-basic-concepts.md)

Após instalar o Power BI Desktop, consulte o seguinte artigo para o ajudar a começar rapidamente:

* [Introdução ao Power BI Desktop](../fundamentals/desktop-getting-started.md)

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/).