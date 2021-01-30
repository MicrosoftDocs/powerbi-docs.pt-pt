---
title: Etiquetas de confidencialidade do Microsoft Information Protection no Power BI
description: Saiba como funcionam as Etiquetas de confidencialidade do Microsoft Information Protection no Power BI
author: paulinbar
ms.author: painbar
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: conceptual
ms.custom: contperf-fy21q2
ms.date: 12/20/2020
LocalizationGroup: Data from files
ms.openlocfilehash: 3bc9a946d8f9091f8a2939ad9865460c1f22a446
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2021
ms.locfileid: "99085818"
---
# <a name="sensitivity-labels-in-power-bi"></a>Etiquetas de confidencialidade no Power BI

Este artigo descreve a funcionalidade Etiquetas de confidencialidade do Microsoft Information Protection no Power BI.

Para obter informações sobre a ativação da etiqueta de confidencialidade no inquilino, incluindo os pré-requisitos e requisitos de licenciamento, veja [Ativar as etiquetas de confidencialidade de dados no Power BI](service-security-enable-data-sensitivity-labels.md).

Para obter informações sobre como aplicar etiquetas de confidencialidade nos ficheiros e conteúdo do Power BI, veja [Como aplicar etiquetas de confidencialidade no Power BI](./service-security-apply-data-sensitivity-labels.md).

>[!NOTE]
>O suporte de etiquetas de confidencialidade no Power BI Desktop está atualmente em pré-visualização.

## <a name="introduction"></a>Introdução

As etiquetas de confidencialidade da Microsoft Information Protection fornecem aos utilizadores uma forma simples de classificar conteúdos críticos no Power BI, sem comprometer a produtividade ou a capacidade de colaborar. Podem ser aplicadas no Power BI Desktop (pré-visualização) e no serviço Power BI, o que possibilita a proteção dos dados confidenciais desde o momento em que começa a desenvolver pela primeira vez o conteúdo, até ao momento em que o mesmo está a ser acedido no Excel através de uma ligação dinâmica. As etiquetas de confidencialidade são retidas quando move o conteúdo alternadamente entre o Desktop e o serviço na forma de ficheiros .pbix.

No serviço Power BI, as etiquetas de confidencialidade podem ser aplicadas a conjuntos de dados, relatórios, dashboards e fluxos de dados. Quando os dados etiquetados saem do Power BI, através da exportação para ficheiros Excel, PowerPoint, PDF ou .pbix ou através de outros cenários de exportação suportados, tal como Analisar no Excel ou Tabelas Dinâmicas de ligação dinâmica no Excel de ligação em direto, o Power BI aplica automaticamente a etiqueta ao ficheiro exportado e protege-o de acordo com as definições de encriptação do ficheiro da etiqueta. Desta forma, os dados confidenciais permanecem protegidos, mesmo quando saem do Power BI.

Além disso, pode aplicar as etiquetas de confidencialidade a ficheiros .pbix no Power BI Desktop, de forma a que os dados e os conteúdos fiquem seguros quando são partilhados fora do Power BI (por exemplo, para que apenas os utilizadores da organização possam abrir um ficheiro .pbix confidencial que tenha sido partilhado ou anexado num e-mail), mesmo antes de terem sido publicados no serviço Power BI. Para obter mais detalhes, veja [Restringir o acesso ao conteúdo com etiquetas de confidencialidade para aplicar encriptação](/microsoft-365/compliance/encryption-sensitivity-labels).

As etiquetas de confidencialidade nos relatórios, dashboards, conjuntos de dados e fluxos de dados são visíveis em muitos locais no serviço Power BI. As etiquetas de confidencialidade em relatórios e dashboards são também visíveis nas aplicações móveis Power BI para iOS e Android e em elementos visuais incorporados. No Desktop, pode ver a etiqueta de confidencialidade na barra de estado.

Um [relatório de métricas de proteção](service-security-data-protection-metrics-report.md) disponível no portal de administração do Power BI fornece aos administradores do Power BI uma visibilidade total sobre os dados confidenciais no inquilino do Power BI. Além disso, os registos de auditoria do Power BI incluem informações de etiquetas de confidencialidade sobre atividades como a aplicação, remoção e alteração de etiquetas, bem como sobre atividades como relatórios de visualização, dashboards, entre outros, o que dá visibilidade ao Power BI e aos administradores de segurança sobre o consumo de dados confidenciais para efeitos de monitorização e investigação de alertas de segurança.

## <a name="important-considerations"></a>Considerações importantes

No serviço Power BI, a etiquetagem de confidencialidade **não** afeta o acesso aos conteúdos. O acesso aos conteúdos no serviço é gerido exclusivamente pelas permissões do Power BI. Embora as etiquetas sejam visíveis, não são aplicadas definições de encriptação associadas (configuradas no [Centro de Segurança do Microsoft 365](https://security.microsoft.com/) ou no [Centro de Conformidade do Microsoft 365](https://compliance.microsoft.com/)). São aplicadas apenas a dados que saem do serviço através de um caminho de exportação suportado, tal como exportar para o Excel, PowerPoint ou PDF ou transferir para .pbix.

No Power BI Desktop (pré-visualização), as etiquetas de confidencialidade com definições de encriptação **afetam** o acesso aos conteúdos. Se um utilizador não tiver [permissões](#power-bi-desktop-preview) suficientes de acordo com as definições de encriptação da etiqueta de confidencialidade no ficheiro .pbix, não poderá abrir o ficheiro. Além disso, no Desktop, ao guardar o trabalho, qualquer etiqueta de confidencialidade adicionada e as definições de encriptação associadas serão aplicadas ao ficheiro .pbix guardado.

As etiquetas de confidencialidade e a encriptação de ficheiros **não são** aplicados em caminhos de exportação não suportados. O administrador do Power BI pode bloquear a exportação de caminhos de exportação não suportados.

>[!NOTE]
> Os utilizadores a quem é concedido acesso a um relatório têm acesso a todo o conjunto de dados subjacente, a menos que [a segurança ao nível da linha (RLS)](./service-admin-rls.md) limite o acesso. Os autores do relatório podem classificar e etiquetar relatórios com as etiquetas de confidencialidade. Se a etiqueta de confidencialidade tiver definições de proteção, o Power BI aplicará estas definições de proteção quando os dados do relatório saírem do Power BI através de um caminho de exportação suportado, tal como exportar para Excel, PowerPoint ou PDF, transferir para .pbix e **Guardar** (Desktop). Apenas os utilizadores autorizados podem abrir ficheiros protegidos.

### <a name="supported-export-paths"></a>Caminhos de exportação suportados
Atualmente, a aplicação de etiquetas de confidencialidade e a proteção associada aos dados que saem do serviço Power BI suporta os seguintes caminhos de exportação:
* Exportar para o Excel, ficheiros PDF (apenas Serviço) e PowerPoint.
* Analisar no Excel a partir do serviço do Power BI, que aciona a transferência de um ficheiro do Excel com uma ligação em direto a um conjunto de dados do Power BI.
* Tabela Dinâmica no Excel com uma ligação em direto ao conjunto de dados do Power BI, para utilizadores com o M365 E3 e superior.
* Transferir para .pbix (Serviço)

>[!NOTE]
>Ao utilizar **Transferir para .pbix** no serviço Power BI, se o relatório transferido e o conjunto de dados tiverem etiquetas diferentes, a etiqueta mais restritiva será aplicada ao ficheiro .pbix. 

## <a name="how-sensitivity-labels-work-in-power-bi"></a>Como funcionam as etiquetas de confidencialidade no Power BI

Aplicar uma etiqueta de confidencialidade a ficheiros e conteúdos do Power BI é semelhante a aplicar uma etiqueta a esse recurso, o que tem os seguintes benefícios:
* **Personalizável** – pode criar categorias para diferentes níveis de conteúdo confidencial na sua organização, tal como Pessoal, Público, Geral, Confidencial e Altamente Confidencial.
* **Texto não encriptado** – uma vez que a etiqueta está em texto não encriptado, é fácil para os utilizadores entenderem como tratar os conteúdos de acordo com as diretrizes da etiqueta de confidencialidade.
* **Persistente** – após a aplicação de uma etiqueta de confidencialidade ao conteúdo, a mesma acompanha esse conteúdo quando este é exportado para ficheiros Excel, PowerPoint e PDF, transferido para .pbix ou guardado (no Desktop) e torna-se a base para aplicar e impor políticas.

Eis um exemplo rápido de como as etiquetas de confidencialidade funcionam no Power BI. A imagem abaixo mostra como uma etiqueta de confidencialidade é aplicada a um relatório no serviço Power BI, como os dados do relatório são depois exportados para um ficheiro do Excel e, por fim, como a etiqueta de confidencialidade e as suas proteções persistem no ficheiro exportado.

![Um GIF animado mostra a aplicação e persistência das etiquetas de confidencialidade](media/service-security-sensitivity-label-overview/ApplyLabelandProtection.gif)

As etiquetas de confidencialidade que aplica ao conteúdo são mantidas e movidas com o conteúdo conforme é utilizado e partilhado no Power BI. Pode utilizar esta etiquetagem para gerar relatórios de utilização e para ver os dados de atividade dos conteúdos confidenciais.

## <a name="sensitivity-labels-in-power-bi-desktop-preview"></a>Etiquetas de confidencialidade no Power BI Desktop (pré-visualização)

As etiquetas de confidencialidade também podem ser aplicadas no Power BI Desktop, o que permite proteger os dados desde o momento em que começa a desenvolver pela primeira vez o conteúdo. Ao guardar o trabalho no Desktop, a etiqueta de confidencialidade aplicada, juntamente com quaisquer definições de encriptação associadas, é aplicada ao ficheiro .pbix resultante. Se a etiqueta tiver definições de encriptação, o ficheiro ficará protegido, independentemente do local para onde vá e da forma como é transmitido. Apenas os utilizadores com as [permissões RMS necessárias](#power-bi-desktop-preview) o poderão abrir.

>[!NOTE]
>* Nesta versão de pré-visualização, podem existir algumas limitações. Veja [Limitações](#limitations).
>* Para poder utilizar etiquetas de confidencialidade no Power BI Desktop, primeiro tem de [ativar a funcionalidade de pré-visualização da proteção de informações](service-security-apply-data-sensitivity-labels.md#apply-sensitivity-labels-in-power-bi-desktop-preview) e reiniciar o programa. Se o programa falhar depois de reiniciar, pode dever-se ao facto de o computador não possuir a versão da biblioteca de runtime do Visual C++ redistributable necessária. Caso se depare com essa falha, visite a [página de transferência da Atualização 3 do Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53587) para obter instruções sobre como transferir e instalar a atualização. Depois de instalar a atualização, tente iniciar novamente o Power BI Desktop.

Se aplicar uma etiqueta de confidencialidade no Desktop, quando publicar o trabalho no serviço ou quando carregar um ficheiro .pbix desse trabalho para o serviço, a etiqueta acompanha os dados para o serviço. No serviço, a etiqueta é aplicada ao conjunto de dados e ao relatório que obtém com o ficheiro. Se o conjunto de dados e o relatório já tiverem etiquetas de confidencialidade, essas etiquetas serão substituídas pela etiqueta proveniente do Desktop.
 
Se carregar um ficheiro .pbix que nunca tenha sido publicado no serviço anteriormente e que tenha o mesmo nome de um relatório ou conjunto de dados que já exista no serviço, o carregamento só será concluído com êxito se o carregador tiver as permissões RMS necessárias para alterar a etiqueta.

O mesmo também acontece na direção oposta: quando transferir para .pbix no serviço e, em seguida, carregar o .pbix para o Desktop, a etiqueta que estava no serviço será aplicada ao ficheiro .pbix transferido e carregada no Desktop. Se o relatório e o conjunto de dados no serviço tiverem etiquetas diferentes, será aplicada a mais restritiva das duas ao ficheiro .pbix transferido.

Quando aplica uma etiqueta no Desktop, a mesma é apresentada na barra de estado.

![Captura de ecrã da etiqueta de confidencialidade na barra de estado do Desktop.](media/service-security-sensitivity-label-overview/sensitivity-label-in-desktop-status-bar.png)

[Saiba como aplicar etiquetas de confidencialidade a ficheiros e conteúdos do Power BI](./service-security-apply-data-sensitivity-labels.md).


## <a name="sensitivity-label-inheritance-upon-creation-of-new-content"></a>Herança de etiquetas de confidencialidade na criação de novos conteúdos

Quando novos relatórios e dashboards são criados no serviço Power BI, herdam automaticamente a etiqueta de confidencialidade anteriormente aplicada no conjunto de dados principal ou no relatório. Por exemplo, um novo relatório criado sobre um conjunto de dados que tenha uma etiqueta de confidencialidade "Altamente Confidencial" também receberá automaticamente a etiqueta "Altamente Confidencial".

A seguinte imagem mostra como a etiqueta de confidencialidade de um conjunto de dados é automaticamente aplicada a um novo relatório que é construído sobre o conjunto de dados.

![Um GIF animado mostra a herança de etiquetas de confidencialidade](media/service-security-sensitivity-label-overview/InheritanceUponCreation.gif)

>[!NOTE]
>Se, por qualquer motivo, a etiqueta de confidencialidade não puder ser aplicada ao novo relatório ou dashboard, o Power BI **não irá** bloquear a criação do novo item.

## <a name="sensitivity-labels-and-protection-on-exported-data"></a>Etiquetas de confidencialidade e proteção dos dados exportados

Quando os dados são exportados do Power BI para o Excel, ficheiros PDF (apenas no serviço) ou ficheiros PowerPoint, o Power BI aplica automaticamente uma etiqueta de confidencialidade ao ficheiro exportado e protege-o de acordo com as definições de encriptação do ficheiro da etiqueta. Desta forma, os seus dados confidenciais permanecem protegidos, estejam onde estiverem.

Um utilizador que exporta um ficheiro do Power BI tem permissão para aceder e editar esse ficheiro de acordo com as definições da etiqueta de confidencialidade, mas não obtém permissões de proprietário no ficheiro.

>[!NOTE]
>Ao utilizar **Transferir para .pbix** no serviço Power BI, se o relatório transferido e o conjunto de dados tiverem etiquetas diferentes, a etiqueta mais restritiva será aplicada ao ficheiro .pbix. 

As etiquetas de confidencialidade e proteções não são aplicadas quando os dados são exportados para ficheiros .csv ou qualquer outro caminho de exportação não suportado.

Aplicar uma etiqueta de confidencialidade e proteção a um ficheiro exportado não adiciona marcação de conteúdos ao ficheiro. No entanto, se a etiqueta for configurada para aplicar marcações de conteúdos, estas são automaticamente aplicadas pelo cliente de etiquetagem unificada do Azure Information Protection, quando o ficheiro é aberto em aplicações de computador do Office. As marcações de conteúdo não são aplicadas automaticamente quando utiliza a etiquetagem incorporada para computadores, dispositivos móveis ou aplicações Web. Para obter mais detalhes, veja [When Office apps apply content marking and encryption](/microsoft-365/compliance/sensitivity-labels-office-apps#when-office-apps-apply-content-marking-and-encryption) (Quando é que as aplicações do Office aplicam marcação de conteúdo e encriptação).

A exportação falha se uma etiqueta não puder ser aplicada quando os dados são exportados para um ficheiro. Para verificar se a exportação falhou porque a etiqueta não podia ser aplicada, clique no nome do relatório ou do dashboard no centro da barra de título e verifique se é apresentada a indicação "Não é possível carregar a etiqueta de confidencialidade" no menu pendente informativo aberto. Isto pode acontecer se o administrador de segurança tiver eliminado ou anulado a publicação da etiqueta aplicada, ou em resultado de um problema temporário do sistema.

## <a name="sensitivity-label-inheritance-in-analyze-in-excel"></a>Herança de etiquetas de confidencialidade em Analisar no Excel

Quando cria uma tabela dinâmica no Excel com uma ligação em direto a um conjunto de dados do Power BI (pode fazê-lo a partir do Power BI através de [Analisar no Excel](../collaborate-share/service-analyze-in-excel.md) ou a partir do [Excel](https://support.microsoft.com/office/create-a-pivottable-from-power-bi-datasets-31444a04-9c38-4dd7-9a45-22848c666884?ui=en-US&rs=en-US&ad=US)), a etiqueta de confidencialidade do conjunto de dados é herdada e aplicada ao ficheiro do Excel, juntamente com qualquer proteção associada. Se a etiqueta do conjunto de dados for posteriormente alterada para uma mais restritiva, a etiqueta aplicada ao ficheiro do Excel ligado será atualizada de forma automática ao atualizar os dados.

![Captura de ecrã do Excel a mostrar a etiqueta de confidencialidade herdada do conjunto de dados através de uma ligação em direto.](media/service-security-sensitivity-label-overview/live-connection-inheritance.png)
 
As etiquetas de confidencialidade no Excel que tenham sido definidas manualmente não são substituídas de forma automática pela etiqueta de confidencialidade do conjunto de dados. Em vez disso, uma faixa notifica-o de que o conjunto de dados tem uma etiqueta de confidencialidade e recomenda que a aplique.

>[!NOTE]
>Se a etiqueta de confidencialidade do conjunto de dados for menos restritiva do que a etiqueta de confidencialidade do ficheiro do Excel, não ocorre a herança nem a atualização de etiquetas. Um ficheiro do Excel nunca herda uma etiqueta de confidencialidade menos restritiva.

## <a name="sensitivity-label-persistence-in-embedded-reports-and-dashboards"></a>Persistência da etiqueta de confidencialidade em relatórios e dashboards incorporados

Pode incorporar relatórios, dashboards e elementos visuais do Power BI em aplicações empresariais, como o Microsoft Teams e o SharePoint, ou no site de uma organização. Quando incorporar um elemento visual, relatório ou dashboard que tenha uma etiqueta de confidencialidade aplicada, a etiqueta de confidencialidade será visível na vista incorporada, e a etiqueta e a sua proteção irão persistir quando os dados forem exportados para o Excel.

![Captura de ecrã a mostrar o relatório incorporado no SharePoint Online](media/service-security-sensitivity-label-overview/embedded-report-sensitivity-label.png)

São suportados os seguintes cenários de incorporação:
* [Incorporar para a sua organização](../developer/embedded/embed-sample-for-your-organization.md)
* Aplicações do Microsoft 365 (por exemplo, [Teams](../collaborate-share/service-embed-report-microsoft-teams.md) e [SharePoint](../collaborate-share/service-embed-report-spo.md))
* [Incorporação segura de URL](../collaborate-share/service-embed-secure.md) (incorporação a partir do serviço Power BI) 

## <a name="sensitivity-labels-in-the-power-bi-mobile-apps"></a>Etiqueta de confidencialidade nas aplicações móveis do Power BI

As etiquetas de confidencialidade podem ser vistas em relatórios e dashboards nas aplicações móveis do Power BI. Um ícone junto ao nome do relatório ou dashboard indica que tem uma etiqueta de confidencialidade, e o tipo de etiqueta e a sua descrição podem ser encontrados na caixa de informações do relatório ou do dashboard.

![Captura de ecrã a mostrar a etiqueta de confidencialidade na aplicação móvel](media/service-security-sensitivity-label-overview/mobile-app-sensitivity-label2.png)

## <a name="supported-clouds"></a>Clouds suportadas
As etiquetas de confidencialidade só são suportadas para inquilinos em clouds globais (públicas) e não para inquilinos em clouds, como clouds nacionais.

## <a name="licensing-and-requirements"></a>Licenciamento e requisitos

Veja [Licenciamento e requisitos](service-security-enable-data-sensitivity-labels.md#licensing-and-requirements).

## <a name="sensitivity-label-creation-and-management"></a>Criação e gestão de etiquetas de confidencialidade

As etiquetas de confidencialidade são criadas e geridas no [Centro de segurança do Microsoft 365](https://security.microsoft.com/) ou no [Centro de conformidade do Microsoft 365](https://compliance.microsoft.com/).

Para aceder às etiquetas de confidencialidade em qualquer um destes centros, navegue até **Classificação > Etiquetas de confidencialidade**. Estas etiquetas de confidencialidade podem ser utilizadas por múltiplos serviços da Microsoft, como o Azure Information Protection, aplicações do Office e serviços do Office 365.

>[!Important]
> Se a sua organização utilizar as etiquetas de confidencialidade do Azure Information Protection, terá de [migrá-las](/azure/information-protection/configure-policy-migrate-labels) para um dos serviços mencionados anteriormente, para que sejam utilizadas no Power BI.

## <a name="limitations"></a>Limitações

### <a name="general"></a>Geral

* Não é recomendável permitir que os utilizadores apliquem etiquetas principais dentro do Power BI (uma etiqueta será considerada como sendo uma etiqueta principal apenas se possuir subetiquetas). Se uma etiqueta principal for aplicada ao conteúdo, a exportação de dados desse conteúdo para um ficheiro (Excel, PowerPoint e PDF) irá falhar. Veja [Sublabels (grouping labels)](/microsoft-365/compliance/sensitivity-labels#sublabels-grouping-labels) (Subetiquetas [etiquetas do agrupamento]).

* As etiquetas de confidencialidade de dados não são suportadas para aplicações de modelo. As etiquetas de confidencialidade definidas pelo criador de aplicações de modelo serão removidas quando a aplicação é extraída e instalada e as etiquetas de confidencialidade adicionadas a artefactos numa aplicação de modelo instalada pelo consumidor de aplicações serão perdidas (repostas a zero) quando a aplicação é atualizada.

* No serviço Power BI, se um conjunto de dados tiver uma etiqueta que tenha sido eliminada do centro de administração de etiquetas, não poderá exportar nem transferir os dados. Na opção Analisar no Excel, será emitido um aviso e os dados serão exportados para um ficheiro .odc sem etiquetas de confidencialidade. No Desktop, se um ficheiro .pbix tiver uma etiqueta inválida, não o poderá guardar.

* O Power BI não suporta etiquetas de confidencialidade dos tipos de proteção [Não Reencaminhar](/microsoft-365/compliance/encryption-sensitivity-labels#let-users-assign-permissions), [definido pelo utilizador](/microsoft-365/compliance/encryption-sensitivity-labels#let-users-assign-permissions) e [HYOK](/azure/information-protection/configure-adrms-restrictions). Os tipos de proteção Não Reencaminhar e definido pelo utilizador fazem referência a etiquetas definidas no [Centro de Segurança do Microsoft 365](https://security.microsoft.com/) ou no [Centro de Conformidade do Microsoft 365](https://compliance.microsoft.com/).

### <a name="power-bi-service"></a>Serviço Power BI

* As etiquetas de confidencialidade só podem ser aplicadas em dashboards, relatórios, conjuntos de dados e fluxos de dados. Atualmente, não estão disponíveis para [relatórios paginados](../paginated-reports/report-builder-power-bi.md) e livros.

* As etiquetas de confidencialidade em recursos do Power BI estão visíveis nas vistas de lista de áreas de trabalho, linhagem, favoritos, recentes e aplicações. Atualmente, as etiquetas não estão visíveis na vista "Partilhado comigo". No entanto, repare que uma etiqueta aplicada a um recurso do Power BI, mesmo que não esteja visível, persiste sempre nos dados exportados para ficheiros Excel, PowerPoint e PDF.

### <a name="power-bi-desktop-preview"></a>Power BI Desktop (pré-visualização)

* Os ficheiros .pbix protegidos só podem ser abertos e/ou publicados por um utilizador que seja o proprietário RMS do ficheiro (o utilizador que aplicou a etiqueta ao ficheiro originalmente) ou que tenha [**Controlo total** e/ou direitos de utilização para **Exportar**](/microsoft-365/compliance/encryption-sensitivity-labels) para a etiqueta relevante. O proprietário RMS tem controlo total e nunca pode ser bloqueado. [Veja mais detalhes](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner)

* Se a etiqueta aplicada a um ficheiro .pbix não tiver sido publicada para o utilizador no centro de segurança do Microsoft 365 ou no centro de conformidade do Microsoft 365, o utilizador não poderá guardar o ficheiro no Desktop.

* Os utilizadores do Power BI Desktop podem deparar-se com problemas ao guardar o trabalho quando a conectividade Internet é perdida, tal como após ficarem offline. Sem ligação à Internet, algumas ações relacionadas com as etiquetas de confidencialidade e a gestão de direitos podem não ser concluídas adequadamente. Nesses casos, recomenda-se voltar a ficar online e tentar guardar novamente.

* Se tiver criado um modelo grande e o ficheiro .pbix protegido resultante for muito grande (mais de 2 GB), será possível que ocorra uma falha ao tentar guardá-lo ou abri-lo. Para contornar este problema, considere remover a proteção do ficheiro .pbix e voltar a aplicá-la depois de o ficheiro ter sido publicado no serviço Power BI.

    Em geral, quando protege um ficheiro com uma etiqueta de confidencialidade que aplica encriptação, recomenda-se utilizar também outro método de encriptação, como a encriptação do ficheiro de paginação, encriptação NTFS, bitlockers, antimalware, etc.

* Os ficheiros temporários não são encriptados.

* A opção **Obter dados** só poderá carregar ficheiros protegidos se forem locais. Os ficheiros protegidos de serviços online como o SharePoint Online ou OneDrive para Empresas não podem ser carregados. Para um ficheiro protegido, pode carregá-lo a partir do dispositivo local ou remover primeiro a etiqueta do ficheiro no Power BI Desktop e, em seguida, carregá-lo através de um dos serviços online.

* A opção **Exportar para PDF** não suporta etiquetas de confidencialidade. Se exportar um ficheiro que tenha uma etiqueta de confidencialidade para PDF, o PDF não receberá a etiqueta e não será aplicada qualquer proteção.

* A proteção de informações no Power BI Desktop não suporta **cenários B2B** e **multi-inquilinos**.

* Se substituir um conjunto de dados rotulado ou reportar no serviço com um ficheiro .pbix não rotulado, as etiquetas do serviço serão mantidas.

## <a name="next-steps"></a>Próximos passos

Este artigo apresentou uma descrição geral da proteção de dados no Power BI. Os seguintes artigos fornecem mais detalhes sobre a proteção de dados no Power BI. 

* [Ativar as etiquetas de confidencialidade no Power BI](service-security-enable-data-sensitivity-labels.md)
* [Como aplicar etiquetas de confidencialidade no Power BI](service-security-apply-data-sensitivity-labels.md)
* [Utilizar controlos do Microsoft Cloud App Security no Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Relatório de métricas de proteção](service-security-data-protection-metrics-report.md)