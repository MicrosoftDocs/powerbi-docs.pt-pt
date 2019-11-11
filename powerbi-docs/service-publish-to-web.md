---
title: Publicar na Web do Power BI
description: Com a funcionalidade Publicar na Web do Power BI, pode facilmente incorporar visualizações interativas online do Power BI, como publicações de blogue e sites, através de e-mails ou redes sociais, em qualquer dispositivo.
author: rkarlin
ms.author: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/16/2019
LocalizationGroup: Share your work
ms.openlocfilehash: 9f8da4a5f37eb1e652dd2125dd588febf49fb01b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871855"
---
# <a name="publish-to-web-from-power-bi"></a>Publicar na Web do Power BI

Com a funcionalidade **Publicar na Web** do Power BI, pode facilmente incorporar visualizações interativas do Power BI online, por exemplo em mensagens de blogue, sites, e-mails ou redes sociais, em qualquer dispositivo. Também pode facilmente editar, atualizar ou anular a partilha dos seus elementos visuais publicados.

> [!WARNING]
> Quando utilizar a funcionalidade **Publicar na Web**, qualquer pessoa poderá ver os seus relatórios ou elementos visuais publicados. Isto não requer autenticação e inclui ver os dados detalhados que os seus relatórios agregam. Antes de publicar um relatório, certifique-se de que pode partilhar publicamente os dados e visualizações. Não publique informações confidenciais ou proprietárias. Se tiver dúvidas, consulte as políticas da sua organização antes da publicação.

>[!Note]
>Para incorporar o conteúdo de forma segura num portal interno ou site, utilize as opções [Incorporar](service-embed-secure.md) ou [Incorporar no SharePoint Online](service-embed-report-spo.md). Isto garante que todas as permissões e segurança de dados são impostas quando os utilizadores estão a visualizar os dados internos.

## <a name="how-to-use-publish-to-web"></a>Como utilizar a funcionalidade Publicar na Web

A funcionalidade **Publicar na Web** está disponível para relatórios editáveis na sua área de trabalho pessoal ou de grupo.  Não está disponível para relatórios partilhados consigo ou cuja segurança de dados dependa da segurança ao nível da linha. Consulte a secção [**Limitações**](#limitations) para obter uma lista completa dos casos em que a funcionalidade **Publicar na Web** não é suportada. Consulte o **Aviso** indicado anteriormente neste artigo antes de utilizar a funcionalidade **Publicar na Web**.

O seguinte vídeo mostra como funciona esta funcionalidade. Depois, experimente por si mesmo ao seguir os passos descritos abaixo.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UF9QtqE7s4Y" frameborder="0" allowfullscreen></iframe>

Os passos seguintes descrevem como utilizar a funcionalidade **Publicar na Web**.

1. Abra um relatório na sua área de trabalho que possa editar e selecione **Ficheiro > Publicar na Web**.

   ![PtW1](media/service-publish-to-web/publish_to_web1.png)

2. Consulte o conteúdo da caixa de diálogo e selecione **Criar código de incorporação**.

   ![PtW2](media/service-publish-to-web/publish_to_web2_ga.png)

3. Consulte o aviso, como aqui mostrado, e certifique-se de que os dados podem ser incorporados num site público. Se sim, selecione **Publicar**.

   ![PtW3](media/service-publish-to-web/publish_to_web3_ga.png)

4. É apresentada uma caixa de diálogo com uma ligação. Pode enviar esta ligação por e-mail, incorporá-la em código, por exemplo num iFrame, ou colá-la diretamente num blogue ou página Web.

   ![PtW4](media/service-publish-to-web/publish_to_web4.png)

5. Se já tiver criado um código de incorporação para um relatório e selecionar **Publicar na Web**, não verá as caixas de diálogo nos passos 2-4. Em vez disso, será apresentada a caixa de diálogo **Código de incorporação**:

   ![PtW5](media/service-publish-to-web/publish_to_web5.png)

   Só pode criar um código de incorporação para cada relatório.


## <a name="tips-and-tricks-for-view-modes"></a>Sugestões e truques para os modos de visualização

Normalmente, ao incorporar conteúdos numa publicação de um blogue, é necessário ajustá-los a um tamanho de ecrã específico.  Pode ajustar a altura e largura na etiqueta iFrame, conforme necessário. No entanto, deve certificar-se de que o seu relatório cabe na área de iFrame fornecida. Assim, deve também definir um Modo de Visualização adequado ao editar o relatório.

A seguinte tabela fornece instruções sobre o Modo de Visualização e a forma como será apresentado quando for incorporado.

| Modo de Visualização | O aspeto que terá quando incorporado |
| --- | --- |
| ![PtW6b](media/service-publish-to-web/publish_to_web6b.png) |A opção **Ajustar à página** respeita a altura e a largura de página do seu relatório. Se definir a sua página para proporções *dinâmicas*, como 16:9 ou 4:3, os conteúdos serão dimensionados para caber no iFrame. Ao incorporar num iFrame, a opção **Ajustar à página** poderá resultar em *letterboxing*, fazendo com que seja apresentado um fundo cinzento na área do iFrame após os conteúdos serem ajustados de forma a caber no mesmo. Para minimizar o letterboxing, defina adequadamente a altura e a largura do iFrame. |
| ![PtW6d](media/service-publish-to-web/publish_to_web6d.png) |A opção **Tamanho real** garante que o relatório mantém o tamanho definido na página de relatórios. Isto poderá originar barras de deslocamento no seu iFrame. Defina a altura e largura do iFrame para evitar as barras de deslocamento. |
| ![PtW6c](media/service-publish-to-web/publish_to_web6c.png) |A opção **Ajustar à largura** garante que os conteúdos cabem na área horizontal do iFrame. Continua a ser apresentado um limite, mas os conteúdos ajustam-se de forma a ocupar todo o espaço horizontal disponível. |

## <a name="tips-and-tricks-for-iframe-height-and-width"></a>Dicas e truques para a altura e largura do iFrame

Um código de incorporação da funcionalidade **Publicar na Web** tem o seguinte aspeto:

![PtW7](media/service-publish-to-web/publish_to_web7.png)
 
Pode editar a largura e altura manualmente para garantir um melhor dimensionamento na página em que está a fazer a incorporação.

Para obter um melhor ajuste, experimente adicionar 56 pixéis à altura do iFrame para acomodar o tamanho atual da barra inferior. Se a sua página de relatório utilizar o tamanho dinâmico, a seguinte tabela apresenta alguns tamanhos que pode utilizar para obter um ajuste sem letterboxing.

| Proporção | Tamanho | Dimensão (Largura x Altura) |
| --- | --- | --- |
| 16:9 |Pequeno |640 x 416 px |
| 16:9 |Médio |800 x 506 px |
| 16:9 |Grande |960 x 596 px |
| 4:3 |Pequeno |640 x 536 px |
| 4:3 |Médio |800 x 656 px |
| 4:3 |Grande |960 x 776 px |

## <a name="manage-embed-codes"></a>Gerir códigos de incorporação

Depois de criar um código de incorporação **Publicar na Web**, poderá gerir os seus códigos a partir do menu **Definições** no Power BI. A gestão de códigos de incorporação inclui a capacidade de remover o relatório ou elemento visual de destino de um código (tornando o código de incorporação inutilizável) ou de obter o código de incorporação novamente.

1. Para gerir os seus códigos de incorporação da funcionalidade **Publicar na Web**, abra a engrenagem das **Definições** e selecione **Gerir códigos de incorporação**.

   ![PtW8](media/service-publish-to-web/publish_to_web8.png)

2. Os seus códigos de incorporação são apresentados.

   ![PtW9](media/service-publish-to-web/publish_to_web9.png)

3. Pode obter ou eliminar um código de incorporação. Eliminá-lo desativa todas as ligações para esse relatório ou elemento visual.

   ![PtW10](media/service-publish-to-web/publish_to_web10.png)

4. Se selecionar **Eliminar**, ser-lhe-á pedida uma confirmação.

   ![PtW11](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>Atualizações a relatórios e atualização de dados

Depois de criar e partilhar o seu código de incorporação da funcionalidade **Publicar na Web**, o relatório será atualizado com as alterações que fizer e a ligação do código de incorporação ficará imediatamente ativa. Qualquer pessoa que abra a ligação poderá vê-lo. No entanto, após esta ação inicial, as atualizações dos relatórios ou elementos visuais poderão demorar aproximadamente uma hora até ficarem visíveis para os seus utilizadores. Para obter mais informações, consulte a secção [**Como funciona**](#howitworks), mais à frente neste artigo. 

## <a name="data-refresh"></a>Atualização de dados

As atualizações de dados são refletidas automaticamente no relatório ou visual incorporado. Poderá demorar aproximadamente uma hora para que os dados atualizados fiquem visíveis nos códigos de incorporação. Para desativar as atualizações automáticas, selecione **não atualizar** no agendamento do conjunto de dados que o relatório utiliza.  

## <a name="custom-visuals"></a>Elementos visuais personalizados

Os visuais personalizados são suportados na funcionalidade **Publicar na Web**. Quando utiliza a funcionalidade **Publicar na Web**, os utilizadores com quem partilha os elementos visuais publicados não precisam de ativar os elementos visuais personalizados para ver o relatório.

## <a name="limitations"></a>Limitações

A funcionalidade **Publicar na Web** é suportada na grande maioria das origens de dados e relatórios no serviço Power BI. No entanto, os seguintes elementos não são atualmente suportados ou disponibilizados com a funcionalidade **Publicar na Web**:

- Relatórios com segurança a nível de linha.
- Relatórios que utilizam qualquer origem de dados de Ligação em Direto, incluindo Tabelas do Analysis Services no local, modelos Multidimensionais do Analysis Services e o Azure Analysis Services.
- Relatórios partilhados diretamente consigo ou através de um pacote de conteúdos organizacionais.
- Relatórios num grupo no qual não é um membro de edição.
- Os elementos visuais "R" não são atualmente suportados nos relatórios da funcionalidade **Publicar na Web**.
- Exportar dados de elementos visuais num relatório publicado na Web.
- ArcGIS Maps para elementos visuais do Power BI.
- Relatórios que contêm medidas DAX ao nível do relatório.
- Modelos de consulta de dados de início de sessão único.
- [Informações confidenciais proprietárias](#publish-to-web-from-power-bi).
- A capacidade de autenticação automática fornecida com a opção **Incorporar** não funciona com a API de JavaScript do Power BI. Para a API de JavaScript do Power BI, utilize a abordagem [O utilizador detém os dados](developer/embed-sample-for-your-organization.md) para incorporar.

## <a name="tenant-setting"></a>Definição de inquilino

Os administradores do Power BI podem ativar ou desativar a funcionalidade **Publicar na Web**. Também podem restringir o acesso a grupos específicos, o que poderá afetar a sua permissão para criar um código de incorporação.

|Feature |Ativada para toda a organização |Desativada para toda a organização |Grupos de segurança específicos   |
|---------|---------|---------|---------|
|**Publicar na Web**, no menu **Ficheiro** do relatório.|Ativada para todos|Não visível para todos|Visível apenas para utilizadores ou grupos autorizados.|
|**Gerir códigos de incorporação**, em **Definições**|Ativada para todos|Ativada para todos|Ativada para todos.<br><br>* A opção **Eliminar** está ativada apenas para utilizadores e grupos autorizados.<br>* A opção **Obter códigos** está ativada para todos.|
|**Incorporar códigos** no portal de administração|O estado será um dos seguintes:<br>* Ativo<br>* Não suportado<br>* Bloqueado|O estado apresentado será **Desativado**|O estado será um dos seguintes:<br>* Ativo<br>* Não suportado<br>* Bloqueado<br><br>Se um utilizador não estiver autorizado com base na definição do inquilino, o estado apresentado será **Em violação**.|
|Relatórios publicados existentes|Todos ativados|Todos desativados|Os relatórios continuam a ser compostos para todos.|

## <a name="understanding-the-embed-code-status-column"></a>Compreender a coluna do estado do código de incorporação

A página **Gerir códigos de incorporação** inclui uma coluna de estado. Os códigos de incorporação estão predefinidos como **Ativos**, mas também poderá encontrar um dos estados descritos abaixo.

| Estado | Descrição |
| --- | --- |
| **Ativo** |O relatório está disponível para visualização e interação por utilizadores da Internet. |
| **Bloqueado** |O conteúdo do relatório infringe os [Termos de Serviço do Power BI](https://powerbi.microsoft.com/terms-of-service). A Microsoft bloqueou o relatório. Se achar que o bloqueio dos conteúdos foi um erro, contacte o suporte. |
| **Não suportado** |O conjunto de dados do relatório está a utilizar segurança ao nível de linha ou outra configuração não suportada. Consulte a secção [**Limitações**](#limitations) para obter uma lista completa. |
| **Em violação** |O código de incorporação está fora da política de inquilino definida. Normalmente, isto ocorre quando um código de incorporação foi criado e a definição de inquilino da funcionalidade **Publicar na Web** foi alterada para excluir o utilizador a quem pertence o código de incorporação. Se a definição de inquilino tiver sido desativada ou o utilizador já não tiver permissão para criar códigos de incorporação, os códigos de incorporação existentes apresentarão o estado **Em violação**. |

## <a name="how-to-report-a-concern-with-publish-to-web-content"></a>Como comunicar um problema relacionado com conteúdos da funcionalidade Publicar na Web

Para comunicar um problema relacionado com os conteúdos da funcionalidade **Publicar na Web** incorporados num site ou blogue, utilize o ícone de **Sinalização** na barra inferior, apresentado na seguinte imagem. Ser-lhe-á pedido que envie um e-mail para a Microsoft a explicar o problema. A Microsoft irá avaliar os conteúdos com base nos Termos de Serviço do Power BI e tomar as medidas adequadas.

Para comunicar um problema, selecione o ícone de **sinalização** na barra inferior do relatório **Publicar na Web**.

![PtW12](media/service-publish-to-web/publish_to_web12_ga.png)

## <a name="licensing-and-pricing"></a>Licenciamento e Preços

Tem de ser utilizador do Microsoft Power BI para utilizar a funcionalidade **Publicar na Web**. As pessoas que veem os seus relatórios não têm de ser utilizadores do Power BI.

<a name="howitworks"></a>
## <a name="how-it-works-technical-details"></a>Como funciona (detalhes técnicos)

Quando cria um código de incorporação através da funcionalidade **Publicar na Web**, o relatório fica visível para os utilizadores na Internet. Encontra-se disponível publicamente, pelo que é expectável que os utilizadores partilhem facilmente o relatório através das redes sociais. Quando os utilizadores virem o relatório, quer ao abrir o URL público direto ou ao vê-lo incorporado numa página Web ou blogue, o Power BI regista a definição do relatório e os resultados das consultas necessários para ver o relatório. Isto garante que milhares de utilizadores podem ver o relatório em simultâneo, sem afetar o desempenho.

A cache é duradoura, pelo que se atualizar a definição de relatório (por exemplo, se alterar o Modo de Visualização) ou atualizar os dados relatório, poderá demorar aproximadamente uma hora até que as alterações entrem em vigor na versão do relatório vista pelos seus utilizadores. Por isso, recomenda-se que teste o seu trabalho antecipadamente e crie o código de incorporação **Publicar na Web** apenas quando estiver satisfeito com as definições.

## <a name="next-steps"></a>Próximos passos

- [Peça Web de relatórios do SharePoint Online](service-embed-report-spo.md) 

- [Incorporar relatório num site ou portal seguro](service-embed-secure.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
