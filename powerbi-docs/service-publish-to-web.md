---
title: Publicar na Web do Power BI
description: Com a funcionalidade Publicar na Web do Power BI, pode facilmente incorporar visualizações interativas online do Power BI, como publicações de blogue e sites, através de e-mails ou redes sociais, em qualquer dispositivo.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/16/2019
LocalizationGroup: Share your work
ms.openlocfilehash: 1b5dfc0b05595e96c9a297a5be3700e71cdbe229
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051568"
---
# <a name="publish-to-web-from-power-bi"></a>Publicar na Web do Power BI

Com o Power BI **publicar na web** opção, pode facilmente incorporar visualizações interativas do Power BI online, como em mensagens de blogue, sites, através de e-mails ou redes sociais, de qualquer dispositivo. Também pode facilmente editar, atualizar ou anular a partilha dos seus elementos visuais publicados.

> [!WARNING]
> Quando utiliza **publicar na web**, qualquer pessoa na Internet pode ver o relatório publicado ou elemento visual. Isso requer sem autenticação e inclui a visualização de dados de nível de detalhe seus relatórios agregados. Antes de publicar um relatório, certifique-se de que há problema para partilhar os dados e as visualizações publicamente. Não publique informações confidenciais ou proprietárias. Se tiver dúvidas, consulte as políticas da sua organização antes da publicação.

>[!Note]
>Para incorporar o conteúdo de forma segura num portal interno ou site, utilize as opções [Incorporar](service-embed-secure.md) ou [Incorporar no SharePoint Online](service-embed-report-spo.md). Isto garante que todas as permissões e segurança de dados são impostas quando os utilizadores estão a visualizar os dados internos.

## <a name="how-to-use-publish-to-web"></a>Como utilizar a funcionalidade Publicar na Web

**Publicar na web** está disponível para os relatórios em suas áreas de trabalho pessoais ou de grupo pode editar.  Não está disponível para os relatórios partilhados consigo ou aqueles que contar com segurança ao nível da linha para proteger os dados. Consulte a [ **limitações** ](#limitations) secção abaixo para obter uma lista completa dos casos em que **publicar na web** não é suportada. Reveja os **aviso** mencionadas anteriormente neste artigo antes de utilizar **publicar na web**.

O seguinte procedimento *breve vídeo* mostra como funciona esse recurso. Em seguida, experimente mesmo nos passos abaixo.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UF9QtqE7s4Y" frameborder="0" allowfullscreen></iframe>

Os passos seguintes descrevem como utilizar a funcionalidade **Publicar na Web**.

1. Abra um relatório na sua área de trabalho que pode editar e selecione **ficheiro > publicar na web**.

   ![PtW1](media/service-publish-to-web/publish_to_web1.png)

2. Reveja a caixa de diálogo conteúda e selecione **criar código de incorporação**.

   ![PtW2](media/service-publish-to-web/publish_to_web2_ga.png)

3. Leia o aviso, conforme mostrado aqui e confirme que os dados são podem ser incorporados num site público. Se estiver, selecione **publicar**.

   ![PtW3](media/service-publish-to-web/publish_to_web3_ga.png)

4. É apresentada uma caixa de diálogo com uma ligação. Pode enviar esta ligação num e-mail, incorporá-la no código como uma iFrame ou cole-o diretamente para uma página web ou blogue.

   ![PtW4](media/service-publish-to-web/publish_to_web4.png)

5. Se tiver criado anteriormente um código de incorporação para um relatório e selecionar **publicar na web**, não verá as caixas de diálogo nos passos 2 a 4. Em vez disso, o **código de incorporação** é apresentada a caixa de diálogo:

   ![PtW5](media/service-publish-to-web/publish_to_web5.png)

   Só pode criar um código de incorporação para cada relatório.


## <a name="tips-and-tricks-for-view-modes"></a>Dicas e truques para modos de exibição

Ao incorporar conteúdos dentro de uma mensagem de blogue, normalmente, tem de ajustá-los dentro de um tamanho de tela específica.  Pode ajustar a altura e a largura da tag iFrame conforme necessário. No entanto, precisa garantir o que seu relatório se ajusta a área de determinado iFrame, por isso também terá de definir um modo de visualização adequado ao editar o relatório.

A seguinte tabela fornece instruções sobre o Modo de Visualização e a forma como será apresentado quando for incorporado.

| Modo de Visualização | O aspeto que terá quando incorporado |
| --- | --- |
| ![PtW6b](media/service-publish-to-web/publish_to_web6b.png) |**Ajustar à página** irá respeitar a altura da página e a largura do seu relatório. Se definir a página em proporções "Dinâmicas", como 16:9 ou 4:3 seus conteúdos serão dimensionados para caber no iFrame. Quando incorporado num iFrame, usando **ajustar à página** pode resultar em **letterboxing**, onde um fundo cinzento seja mostrado em áreas do iFrame após o conteúdo dimensionado para caber no iFrame. Para minimizar o letterboxing, defina altura e largura do iFrame adequadamente. |
| ![PtW6d](media/service-publish-to-web/publish_to_web6d.png) |**Tamanho real** garante que o relatório mantém o tamanho conforme definido na página do relatório. Isso pode resultar em barras de deslocamento aparecer na sua iFrame. Defina a altura do iFrame e a largura para evitar barras de rolagem. |
| ![PtW6c](media/service-publish-to-web/publish_to_web6c.png) |**Ajustar à largura** garante que o conteúdo cabe na área de horizontal do iFrame. Uma borda ainda é mostrada, mas o conteúdo é dimensionado para utilizar todo o espaço horizontal disponível. |

## <a name="tips-and-tricks-for-iframe-height-and-width"></a>Dicas e truques para a altura e largura do iFrame

R **publicar na web** incorporar código parece o seguinte:

![PtW7](media/service-publish-to-web/publish_to_web7.png)
 
Pode editar a largura e altura manualmente para garantir que é exatamente como pretende que para caber na página em que está a incorporar.

Para atingir um ajuste melhor, pode experimentar adicionar 56 pixels à altura do iFrame para acomodar o tamanho atual da barra inferior. Se a sua página de relatório utilizar o tamanho dinâmico, a tabela seguinte apresenta alguns tamanhos que pode utilizar para atingir um ajuste sem letterboxing.

| Proporção | Tamanho | Dimensão (Largura x Altura) |
| --- | --- | --- |
| 16:9 |Pequeno |640 x 416 px |
| 16:9 |Médio |800 x 506 px |
| 16:9 |Grande |960 x 596 px |
| 4:3 |Pequeno |640 x 536 px |
| 4:3 |Médio |800 x 656 px |
| 4:3 |Grande |960 x 776 px |

## <a name="manage-embed-codes"></a>Gerir códigos de incorporação

Depois de criar uma **publicar na web** código de incorporação, pode gerenciar seus códigos da **definições** menu no Power BI. Gerir códigos de incorporação inclui a capacidade de remover o elemento visual de destino ou o relatório para um código (tornando o código de incorporação inutilizável), ou obter o código de incorporação.

1. Para gerir os seus códigos de incorporação da funcionalidade **Publicar na Web**, abra a engrenagem das **Definições** e selecione **Gerir códigos de incorporação**.

   ![PtW8](media/service-publish-to-web/publish_to_web8.png)

2. São apresentados os códigos de incorporação.

   ![PtW9](media/service-publish-to-web/publish_to_web9.png)

3. Pode obter ou eliminar um código de incorporação. Excluí-lo desativa todas as ligações para esse relatório ou elemento visual.

   ![PtW10](media/service-publish-to-web/publish_to_web10.png)

4. Se selecionou **eliminar**, lhe forem pedidas uma confirmação.

   ![PtW11](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>Atualizações a relatórios e atualização de dados

Depois de criar sua **publicar na web** código de incorporação e partilha-lo, o relatório é atualizado com as alterações que fizer e a ligação do código de incorporação é imediatamente Active Directory e qualquer pessoa que abre a ligação pode vê-lo. No entanto, depois desta ação inicial, as atualizações a relatórios ou elementos visuais podem de demorar aproximadamente uma hora antes de se tornarem visíveis para os seus utilizadores. Se precisar que as atualizações fiquem imediatamente disponíveis, pode eliminar o código de incorporação e criar um novo. Para obter mais informações, consulte a [ **como ele funciona** ](#howitworks) seção mais adiante neste artigo. 

## <a name="data-refresh"></a>Atualização de dados

As atualizações de dados são refletidas automaticamente no relatório ou visual incorporado. Pode demorar aproximadamente 1 hora para que os dados atualizados sejam visíveis nos códigos de incorporação. Para desativar a atualização automática, pode selecionar **não atualizar** na agenda do conjunto de dados utiliza o relatório.  

## <a name="custom-visuals"></a>Elementos visuais personalizados

Os visuais personalizados são suportados na funcionalidade **Publicar na Web**. Quando utiliza **publicar na web**, os utilizadores com quem partilhar o seu elemento visual publicado não é necessário ativar elementos visuais personalizados ver o relatório.

## <a name="limitations"></a>Limitações

**Publicar na web** é suportada para a grande maioria dos dados de fontes e os relatórios no serviço Power BI, no entanto, a seguir são **não atualmente suportados ou disponibilizados** com **publicar na web** :

- Relatórios com segurança a nível de linha.
- Relatórios que utilizam qualquer origem de dados de Ligação em Direto, incluindo Tabelas do Analysis Services no local, modelos Multidimensionais do Analysis Services e o Azure Analysis Services.
- Relatórios partilhados diretamente consigo ou através de um pacote de conteúdos organizacionais.
- Relatórios num grupo no qual não é um membro de edição.
- Visuais "R" não são atualmente suportados no **publicar na web** relatórios.
- Exportar dados de elementos visuais num relatório, que foi publicado na Web.
- ArcGIS Maps for Power BI visuais.
- Relatórios que contém medidas DAX de nível de relatório.
- Modelos de consulta de dados de início de sessão único.
- [Proteger informações confidenciais ou proprietárias](#publish-to-web-from-power-bi).
- A capacidade de autenticação automática fornecida com a opção **Incorporar** não funciona com a API de JavaScript do Power BI. Para a API de JavaScript do Power BI, utilize a abordagem [O utilizador detém os dados](developer/embed-sample-for-your-organization.md) para incorporar. Saiba mais sobre o [utilizador detém os dados](developer/embed-sample-for-your-organization.md).

## <a name="tenant-setting"></a>Definição de inquilino

Os administradores do Power BI podem ativar ou desativar a **publicar na web** funcionalidade. Eles também podem restringir o acesso a grupos específicos, que podem afetar a capacidade de criar um código de incorporação.

|Feature |Ativada para toda a organização |Desativada para toda a organização |Grupos de segurança específicos   |
|---------|---------|---------|---------|
|**Publicar na web** sob do relatório **ficheiro** menu|Ativada para todos|Não visível para todos|Visível apenas para utilizadores ou grupos autorizados.|
|**Gerir códigos de incorporação**, em **Definições**|Ativada para todos|Ativada para todos|Está ativada para todos.<br><br>* A opção **Eliminar** está ativada apenas para utilizadores e grupos autorizados.<br>* A opção **Obter códigos** está ativada para todos.|
|**Incorporar códigos** no portal de administração|O estado será um dos seguintes:<br>* Ativo<br>* Não suportado<br>* Bloqueado|O estado apresentado será **Desativado**|O estado será um dos seguintes:<br>* Ativo<br>* Não suportado<br>* Bloqueado<br><br>Se um utilizador não estiver autorizado com base na definição do inquilino, o estado apresentado será **Em violação**.|
|Relatórios publicados existentes|Todos ativados|Todos desativados|Os relatórios continuam a ser compostos para todos.|

## <a name="understanding-the-embed-code-status-column"></a>Compreender a coluna do estado do código de incorporação

O **gerir códigos de incorporação** página inclui uma coluna de status. Por predefinição, códigos de incorporação estão **Active Directory**, mas também poderia ser um dos Estados listados abaixo.

| Estado | Descrição |
| --- | --- |
| **Ativo** |O relatório está disponível para visualização e interação por utilizadores da Internet. |
| **Bloqueado** |O conteúdo do relatório viola os [termos de serviço Power BI](https://powerbi.microsoft.com/terms-of-service). Microsoft bloqueou a ele. Se achar que o bloqueio dos conteúdos foi um erro, contacte o suporte. |
| **Não suportado** |O conjunto de dados do relatório está a utilizar segurança ao nível de linha ou outra configuração não suportada. Consulte a [ **limitações** ](#limitations) secção para obter uma lista completa. |
| **Em violação** |O código de incorporação está fora da política de inquilino definida. Normalmente, isto ocorre quando um código de incorporação foi criado e, em seguida, o **publicar na web** definição do inquilino foi alterado para excluir o utilizador proprietário o código de incorporação. Se a definição de inquilino está desabilitado ou se o utilizador já não tem permissão para criar códigos de incorporação, show de códigos de incorporação existentes uma **violação** estado. |

## <a name="how-to-report-a-concern-with-publish-to-web-content"></a>Como comunicar um problema relacionado com conteúdos da funcionalidade Publicar na Web

Para reportar um problema relacionado com a **publicar na web** conteúdo incorporado um Web site ou blogue, utilize o **sinalizador** ícone na barra inferior, conforme mostrado na imagem seguinte. Deverá enviar um e-mail para a Microsoft explicando sua preocupação. A Microsoft irá avaliar o conteúdo com base no serviço Power BI termos de e tomar as medidas adequadas.

Para reportar um problema, selecione o **sinalizador** ícone na barra inferior do **publicar na web** vir de relatório.

![PtW12](media/service-publish-to-web/publish_to_web12_ga.png)

## <a name="licensing-and-pricing"></a>Licenciamento e Preços

Tem de ser utilizador do Microsoft Power BI para utilizar a funcionalidade **Publicar na Web**. Visualizadores do seu relatório não é necessário ser utilizadores do Power BI.

<a name="howitworks"></a>
## <a name="how-it-works-technical-details"></a>Como funciona (detalhes técnicos)

Quando cria um código de incorporação através de **publicar na web**, o relatório fica visível para os usuários da Internet. Está disponível publicamente, pode esperar que os visualizadores partilhem facilmente o relatório através de redes sociais no futuro. Quando os utilizadores virem o relatório, quer ao abrir o URL público direto ou ao vê-lo incorporado numa página Web ou blogue, o Power BI regista a definição do relatório e os resultados das consultas necessários para ver o relatório. Isto garante que milhares de usuários simultâneos podem ver o relatório sem afetar o desempenho.

O cache é duradoura, pelo que, se atualizar a definição de relatório (por exemplo, se alterar o modo de visualização) ou atualizar os dados de relatório, pode demorar aproximadamente uma hora antes das alterações são refletidas na versão do relatório que ver os seus utilizadores. Por isso, recomenda-se que teste o seu trabalho antecipadamente e crie o código de incorporação **Publicar na Web** apenas quando estiver satisfeito com as definições.

## <a name="next-steps"></a>Próximos passos

- [Peça Web de relatórios do SharePoint Online](service-embed-report-spo.md) 

- [Incorporar relatório num site ou portal seguro](service-embed-secure.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)
