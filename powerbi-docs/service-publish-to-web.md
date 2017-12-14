---
title: Publicar na Web do Power BI
description: "Com a funcionalidade Publicar na Web do Power BI, pode facilmente incorporar visualizações interativas online do Power BI, como publicações de blogue e sites, através de e-mails ou redes sociais, em qualquer dispositivo."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/11/2017
ms.author: asaxton
ms.openlocfilehash: 7038ea8c4591fb0f1ab8dfc95d70e7deaa7155e5
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="publish-to-web-from-power-bi"></a>Publicar na Web do Power BI
Com a funcionalidade **Publicar na Web** do Power BI, pode facilmente incorporar visualizações interativas online do Power BI, como publicações de blogue e sites, através de e-mails ou redes sociais, em qualquer dispositivo.

Também é possível editar, atualizar ou descompartilhar com facilidade os visuais publicados.

> [!WARNING]
> Quando utilizar a funcionalidade **Publicar na Web**, o relatório ou visual publicado pode ser visualizado por qualquer pessoa na Internet. Não há nenhuma autenticação usada ao exibir esses relatórios. Somente use Publicar na Web com relatórios e dados que qualquer pessoa na Internet (membros não autenticados do público) possa ver. Isto inclui dados detalhados que são agregados nos seus relatórios. Antes de publicar este relatório, certifique-se de que tem o direito a partilhar os dados e as visualizações publicamente. Não publique informações confidenciais proprietárias. Se tiver dúvidas, consulte as políticas da sua organização antes da publicação.
> 
> [!IMPORTANT]
> Os administradores do Power BI podem desativar a capacidade de os utilizadores recorrerem à funcionalidade Publicar na Web a partir do Portal de administração. Nas **Definições de inquilino**, deixe a funcionalidade **Publicar na Web** **Desativada**. Esta é uma definição que abrange todo o inquilino. Para obter mais informações, consulte o [portal de administração do Power BI](service-admin-portal.md).
> 
> 

## <a name="how-to-use-publish-to-web"></a>Como usar o recurso Publicar na Web
A funcionalidade **Publicar na Web** está disponível nos relatórios nas áreas de trabalho pessoais ou de grupo que pode editar.  Não pode utilizar a funcionalidade Publicar na Web com relatórios que foram partilhados consigo nem em relatórios com segurança ao nível de linha para proteger os dados. Consulte a secção **Limitações** abaixo para obter uma lista completa dos casos em que a funcionalidade Publicar na Web não é suportada. Consulte o **Aviso** indicado acima neste artigo antes de utilizar a funcionalidade Publicar na Web.

Pode ver como esta funcionalidade funciona no seguinte *breve vídeo*. Depois, siga as etapas abaixo para testá-lo por conta própria.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UF9QtqE7s4Y" frameborder="0" allowfullscreen></iframe>


Os passos seguintes descrevem como utilizar a funcionalidade **Publicar na Web**.

1. Num relatório na sua área de trabalho que possa editar, selecione **Ficheiro  > Publicar na Web**.
   
   ![](media/service-publish-to-web/publish_to_web1.png)
2. Consulte o conteúdo na caixa de diálogo e selecione **Criar código de incorporação**, conforme apresentado na seguinte caixa de diálogo.
   
   ![](media/service-publish-to-web/publish_to_web2_ga.png)
3. Leia o aviso, mostrado no diálogo a seguir, e confirme se os dados estão corretos para ser inseridos em um site público. Se for o caso, selecione **Publicar**.
   
   ![](media/service-publish-to-web/publish_to_web3_ga.png)
4. Será exibido um diálogo que fornece um link que pode ser enviado por email, inserido no código (como um iFrame) ou colado diretamente em sua página da Web ou em seu blog.
   
   ![](media/service-publish-to-web/publish_to_web4.png)
5. Se você tiver criado anteriormente um código de inserção para o relatório, ele será exibido rapidamente. Você pode criar apenas um código de inserção para cada relatório.
   
   ![](media/service-publish-to-web/publish_to_web5.png)

## <a name="tips-and-tricks-for-view-modes"></a>Dicas e truques para modos de Exibição
Quando você insere o conteúdo em uma postagem no blog, normalmente, é necessário ajustá-lo em um tamanho específico da tela.  Você também pode ajustar a altura e a largura na marca iFrame, conforme necessário, mas também precisa garantir que seu relatório se ajuste na área determinada do iFrame; por isso, é necessário definir um Modo de Exibição apropriado ao editar o relatório.

A tabela a seguir fornece diretrizes sobre o Modo de Exibição e como ele aparecerá quando for inserido.

| Modo de Exibição | Sua aparência quando inserido |
| --- | --- |
| ![](media/service-publish-to-web/publish_to_web6b.png) |**Ajustar à página** irá respeitar a altura e a largura de página do seu relatório. Se definir a página em proporções "Dinâmicas", como 16:9 ou 4:3, os seus conteúdos serão dimensionados para caber no iFrame que forneceu. Quando incorporado num iFrame, utilizar a funcionalidade **Ajustar à página** pode resultar em **letterboxing**, fazendo com que um fundo cinzento seja mostrado em áreas do iFrame após o conteúdo ser dimensionado para caber no iFrame. Para minimizar o letterboxing, defina apropriadamente a altura e a largura do iFrame. |
| ![](media/service-publish-to-web/publish_to_web6d.png) |O **Tamanho real** garante que o relatório mantém o tamanho conforme definido na página de relatórios. Isso pode resultar na exibição de barras de rolagem no iFrame. Defina a altura e a largura do iFrame para evitar barras de deslocamento. |
| ![](media/service-publish-to-web/publish_to_web6c.png) |**Ajustar à largura** garante que o conteúdo cabe na área horizontal do iFrame. Uma borda ainda será mostrada, mas o conteúdo será dimensionado para usar todo o espaço horizontal disponível. |

## <a name="tips-and-tricks-for-iframe-height-and-width"></a>Dicas e truques para a altura e largura do iFrame
O código de inserção recebido depois que você Publicar na Web será semelhante ao seguinte:

![](media/service-publish-to-web/publish_to_web7.png)

É possível editar a largura e a altura manualmente para garantir que o código se ajuste exatamente da forma como você deseja na página em que é inserido.

Para obter um ajuste melhor, pode experimentar adicionar 56 pixels à dimensão de altura do iFrame. Tal acomoda o tamanho atual da barra inferior. Se a sua página de relatório utilizar o tamanho dinâmico, a tabela seguinte apresenta alguns tamanhos que pode utilizar para atingir um ajuste sem letterboxing.

| Proporção | Tamanho | Dimensão (Largura x Altura) |
| --- | --- | --- |
| 16:9 |Pequeno |640 x 416 px |
| 16:9 |Médio |800 x 506 px |
| 16:9 |Grande |960 x 596 px |
| 4:3 |Pequeno |640 x 536 px |
| 4:3 |Médio |800 x 656 px |
| 4:3 |Grande |960 x 776 px |

## <a name="managing-embed-codes"></a>Gerenciando códigos de inserção
Depois de criar um código de incorporação na funcionalidade **Publicar na Web**, pode gerir os códigos que cria no menu **Definições** do serviço Power BI. O gerenciamento de códigos de inserção inclui a capacidade de remover o visual ou relatório de destino de um código (tornando o código de inserção inutilizável) ou de obter o código de inserção novamente.

1. Para gerir os seus códigos de incorporação da funcionalidade **Publicar na Web**, abra a engrenagem das **Definições** e selecione **Gerir códigos de incorporação**.
   
   ![](media/service-publish-to-web/publish_to_web8.png)
2. A lista de códigos de inserção que você criou será exibida, conforme mostrado na imagem a seguir.
   
   ![](media/service-publish-to-web/publish_to_web9.png)
3. Para cada código de incorporação de **Publicar na Web** na lista, é possível obter ou eliminar o código de incorporação e, portanto, fazer com que todas as ligações para esse relatório ou visual deixem de funcionar.
   
   ![](media/service-publish-to-web/publish_to_web10.png)
4. Se selecionar **Eliminar**, ser-lhe-á perguntado se tem a certeza de que pretende eliminar o código de incorporação.
   
   ![](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>Atualizações em relatórios e atualização de dados
Depois de criar o seu código de incorporação de **Publicar na Web** e partilhá-lo, o relatório será atualizado com as alterações que fizer. No entanto, é importante saber que pode levar algum tempo até que a atualização esteja visível para os usuários. As atualizações em um relatório ou visual levam aproximadamente uma hora para serem refletidas nos códigos de inserção de Publicar na Web.

Quando utilizar inicialmente a funcionalidade **Publicar na Web** para obter um código de incorporação, a ligação do código de incorporação fica imediatamente ativa e pode ser vista por qualquer pessoa que abrir a ligação.  Após a ação inicial de Publicar na Web, as atualizações posteriores em relatórios ou visuais para os quais um link Publicar na Web é apontado podem levar aproximadamente uma hora para estar visíveis para os usuários.

Para obter mais informações, consulte a secção **Como funciona**, mais à frente neste artigo. Se precisar que as atualizações fiquem imediatamente disponíveis, pode eliminar o código de incorporação e criar um novo.

## <a name="data-refresh"></a>Atualização de dados
As atualizações de dados são refletidas automaticamente no relatório ou visual incorporado. Pode levar aproximadamente uma hora para que os dados atualizados estejam visíveis nos códigos de inserção. Pode desativar a atualização automática ao selecionar **não atualizar** na agenda do conjunto de dados utilizado pelo relatório.  

## <a name="custom-visuals"></a>Elementos visuais personalizados
Os visuais personalizados são suportados na funcionalidade **Publicar na Web**. Quando você usa Publicar na Web, os usuários com os quais você compartilha seu visual publicado não precisam habilitar visuais personalizados para exibir o relatório.

## <a name="limitations"></a>Limitações
A funcionalidade **Publicar na Web** é suportada para a grande maioria das origens de dados e relatórios no serviço do Power BI; no entanto, os seguintes elementos não são atualmente suportados ou disponibilizados com a funcionalidade Publicar na Web:

1. Relatórios com segurança a nível de linha.
2. Relatórios com Analysis Services Tabular alojado no local.
3. Relatórios partilhados diretamente consigo ou através de um pacote de conteúdos organizacionais.
4. Relatórios num grupo no qual não é um membro de edição.
5. Visuais "R" que atualmente não são suportados em relatórios para Publicar na Web.

## <a name="understanding-the-embed-code-status-column"></a>Noções básicas sobre a coluna de status do código de inserção
Ao ver a página **Gerir códigos de incorporação** para os seus códigos de incorporação da funcionalidade **Publicar na Web**, é apresentada uma coluna de estado. Os códigos de incorporação estão ativos por predefinição, mas pode encontrar qualquer um dos estados abaixo indicados.  

| Estado | Descrição |
| --- | --- |
| **Ativo** |O relatório está disponível para visualização e interação por utilizadores da Internet. |
| **Bloqueado** |O conteúdo do relatório viola os [Termos de Serviço do Power BI](https://powerbi.microsoft.com/terms-of-service). Foi bloqueado pela Microsoft. Se achar que o bloqueio dos conteúdos foi um erro, contacte o suporte. |
| **Não suportado** |O conjunto de dados do relatório está a utilizar segurança ao nível de linha ou outra configuração não suportada. Consulte a secção **Limitações** para obter uma lista completa. |

## <a name="how-to-report-a-concern-with-publish-to-web-content"></a>Como relatar um problema com o conteúdo de Publicar na Web
Para reportar um problema relacionado com os conteúdos **Publicar na Web** incorporados num site ou blogue, utilize o ícone de **Sinalização** na barra inferior, apresentado na imagem seguinte. Será solicitado que você envie um email à Microsoft explicando o problema. A Microsoft avaliará o conteúdo com base nos Termos de Serviço do Power BI e tomará as devidas providências.

Para reportar um problema, selecione o ícone de **sinalização** na barra inferior do relatório Publicar na Web que vê.

![](media/service-publish-to-web/publish_to_web12_ga.png)

## <a name="licensing-and-pricing"></a>Licenciamento e preços
Tem de ser utilizador do Microsoft Power BI para utilizar a funcionalidade **Publicar na Web**. Os consumidores do seu relatório (leitores, visualizadores) não precisam de ser utilizadores do Power BI.

## <a name="how-it-works-technical-details"></a>Como isso funciona (detalhes técnicos)
Ao criar um código de incorporação através da funcionalidade **Publicar na Web**, o relatório fica visível para utilizadores na Internet. Encontra-se publicamente disponível, pelo que é expectável que os visualizadores partilhem facilmente o relatório através das redes sociais. Conforme os usuários exibem o relatório, abrindo a URL pública direta ou exibindo-o inserido em uma página da Web ou em um blog, o Power BI armazena em cache a definição do relatório e os resultados das consultas necessárias para exibi-lo. Essa abordagem garante que o relatório pode ser exibido por milhares de usuários simultâneos, sem nenhum impacto sobre o desempenho.  

O cache é duradouro; portanto, se você atualizar a definição do relatório (por exemplo, se alterar seu modo de Exibição) ou se atualizar os dados do relatório, poderá levar aproximadamente uma hora até que as alterações sejam refletidas na versão do relatório exibida pelos usuários. Por isso, recomenda-se que teste o seu trabalho antecipadamente e crie o código de incorporação **Publicar na Web** apenas quando estiver satisfeito com as definições.

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

