---
title: Proteção de dados no Power BI
description: Saiba como a proteção de dados funciona no Power BI
author: paulinbar
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/21/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: fa969f8f738cf09e9e01e284de8f60e2fd8ce9ab
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315678"
---
# <a name="data-protection-in-power-bi"></a>Proteção de dados no Power BI

As empresas modernas têm regulamentos e requisitos empresariais rigorosos sobre como proteger e lidar com dados confidenciais. Para proporcionar controlo e visibilidade relativamente a esses dados, o Power BI está integrado no Microsoft Information Protection e no Microsoft Cloud App Security. Permite-lhe:
* Utilizar as [etiquetas de confidencialidade](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide) do Microsoft Information Protection para classificar e etiquetar conteúdos (dashboards, relatórios, conjuntos de dados e fluxos de dados) no serviço Power BI ao utilizar a mesma taxonomia utilizada para classificar e proteger ficheiros no Office 365.
* Aplicar etiquetas de confidencialidade e proteção do Microsoft Information Protection aos dados ao exportá-los para ficheiros Excel, PowerPoint ou PDF.
* Utilizar o Microsoft Cloud App Security para monitorizar atividades no Power BI, investigar problemas de segurança e proteger conteúdos no Power BI com o Controlo de Aplicações de Acesso Condicional do Microsoft Cloud App Security.

**Notas importantes**
* A etiquetagem de confidencialidade **não** afeta o acesso aos conteúdos no Power BI, uma vez que esse acesso é gerido apenas pelas permissões do Power BI. Embora as etiquetas sejam visíveis, não são aplicadas definições de encriptação associadas (configuradas no [Centro de Segurança do Microsoft 365](https://security.microsoft.com/) ou no [Centro de Conformidade do Microsoft 365](https://compliance.microsoft.com/)). Essas definições aplicam-se apenas aos dados exportados para ficheiros Excel, PowerPoint e PDF.
* As etiquetas de confidencialidade e a encriptação de ficheiros **não são** aplicadas em nenhum caminho de exportação que não seja a exportação para Excel, PowerPoint e PDF. O administrador de inquilinos do Power BI pode desativar qualquer um ou todos os caminhos de exportação que não suportem a aplicação de etiquetas de confidencialidade e as respetivas definições de encriptação de ficheiros associadas.

## <a name="sensitivity-labels-in-power-bi"></a>Etiquetas de confidencialidade no Power BI

As etiquetas de confidencialidade são criadas e geridas no [Centro de segurança do Microsoft 365](https://security.microsoft.com/) ou no [Centro de conformidade do Microsoft 365](https://compliance.microsoft.com/).

Para aceder às etiquetas de confidencialidade em qualquer um destes centros, navegue até **Classificação > Etiquetas de confidencialidade**. Estas etiquetas de confidencialidade podem ser utilizadas por múltiplos serviços da Microsoft, como o Azure Information Protection, aplicações do Office e serviços do Office 365.

> [!Important]
> Se a sua organização utilizar as etiquetas de confidencialidade do Azure Information Protection, terá de [migrá-las](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels) para um dos serviços mencionados anteriormente, para que sejam utilizadas no Power BI.

> [!NOTE]
> As etiquetas de confidencialidade só são suportadas para inquilinos em clouds públicas e não para inquilinos em clouds, como clouds soberanas.

## <a name="how-sensitivity-labels-work-in-power-bi"></a>Como funcionam as etiquetas de confidencialidade no Power BI

Aplicar uma etiqueta de confidencialidade a um dashboard, relatório, conjunto de dados ou fluxo de dados do Power BI é semelhante a aplicar uma etiqueta a esse recurso, o que tem os seguintes benefícios:
* **Personalizável** – pode criar categorias para diferentes níveis de conteúdo confidencial na sua organização, tal como Pessoal, Público, Geral, Confidencial e Altamente Confidencial.
* **Texto não encriptado** – uma vez que a etiqueta está em texto não encriptado, é fácil para os utilizadores entenderem como tratar os conteúdos de acordo com as diretrizes da etiqueta de confidencialidade.
* **Persistente** – após a aplicação de uma etiqueta de confidencialidade ao conteúdo, a mesma acompanha esse conteúdo quando este é exportado para ficheiros Excel, PowerPoint e PDF, e torna-se a base para aplicar e impor políticas.

Isto significa que a etiqueta de confidencialidade segue o conteúdo quando este é exportado para ficheiros Excel, PowerPoint e PDF, tornando-se a base para aplicar e impor políticas.

Os administradores de inquilinos do Power BI podem controlar a [exportação para Excel](service-admin-portal.md#export-to-excel) e a [exportação para PowerPoint e PDF](service-admin-portal.md#export-reports-as-powerpoint-presentations-or-pdf-documents) no [portal de administração do Power BI](service-admin-portal.md).

## <a name="sensitivity-label-example"></a>Exemplo de etiqueta de confidencialidade

Aqui está um exemplo rápido de como pode funcionar uma etiqueta de confidencialidade no Power BI.
1. No serviço Power BI, uma etiqueta de confidencialidade **Altamente Confidencial** é aplicada a um relatório.

   ![Etiquetas de confidencialidade na vista de lista](media/service-security-data-protection-overview/sensitivity-labels-overview-01.png)
   
1. Quando os dados são exportados para um ficheiro do Excel deste relatório, a etiqueta de confidencialidade e a proteção são aplicados ao ficheiro do Excel exportado.

   ![A etiqueta de confidencialidade segue o conteúdo](media/service-security-data-protection-overview/sensitivity-labels-overview-02.png)

Nas aplicações do Microsoft Office, uma etiqueta de confidencialidade é apresentada como uma etiqueta no e-mail ou no documento de forma semelhante à da imagem acima. Também pode atribuir uma classificação ao conteúdo (como um autocolante) que persiste e é enviada com o conteúdo conforme o mesmo é utilizado e partilhado no Power BI. Pode utilizar esta classificação para gerar relatórios de utilização e ver dados de atividade dos seus conteúdos confidenciais. Com base nestas informações, pode sempre escolher aplicar as definições de proteção mais tarde.

## <a name="requirements-for-using-sensitivity-labels-in-power-bi"></a>Requisitos para utilizar etiquetas de confidencialidade no Power BI

Para que as etiquetas de confidencialidade possam ser ativadas e utilizadas no Power BI, tem de cumprir primeiro os seguintes pré-requisitos:
* Certifique-se de que as etiquetas de confidencialidade foram definidas no [Centro de segurança do Microsoft 365](https://security.microsoft.com/) ou no [Centro de conformidade do Microsoft 365](https://compliance.microsoft.com/).
* [Ative as etiquetas de confidencialidade](service-security-enable-data-sensitivity-labels.md) no Power BI.
* Certifique-se de que os utilizadores têm as [licenças adequadas](#licensing).
* Se utilizar o Microsoft Cloud App Security com o Power BI, certifique-se de que tem o [licenciamento adequado](service-security-using-microsoft-cloud-app-security-controls.md#cloud-app-security-licensing).

## <a name="protect-content-using-microsoft-cloud-app-security"></a>Proteção de conteúdos com o Microsoft Cloud App Security

Pode proteger os conteúdos no Power BI contra fugas ou falhas indesejadas com o Microsoft Cloud App Security. Uma vez definido e configurado o Microsoft Cloud App Security, os administradores de segurança podem monitorizar o acesso e a atividade dos utilizadores, executar a análise dos riscos em tempo real e definir controlos específicos de uma etiqueta.

Por exemplo, as organizações podem utilizar o Microsoft Cloud App Security para configurar uma política que impeça os utilizadores de transferirem dados confidenciais do Power BI para dispositivos não geridos. Esta configuração permite que os utilizadores continuem produtivos e se liguem ao Power BI em qualquer lugar, tirando ainda partido do Microsoft Cloud App Security para evitar comprometer as ações dos utilizadores, tudo em tempo real.

**Requisitos**

Antes de as etiquetas de confidencialidade poderem utilizar o Microsoft Cloud App Security, têm de ser cumpridos os seguintes pré-requisitos:
* O Cloud App Security e o Azure Information Protection [têm de estar ativados para o seu inquilino](https://docs.microsoft.com/cloud-app-security/azip-integration).
* A aplicação [tem de estar ligada ao Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/enable-instant-visibility-protection-and-governance-actions-for-your-apps).

## <a name="licensing"></a>Licensing

* A aplicação e visualização de etiquetas de confidencialidade do Microsoft Information Protection no Power BI requerem uma licença Premium P1 ou Premium P2 do Azure Information Protection. O Microsoft Azure Information Protection pode ser adquirido como produto autónomo ou como parte de um dos conjuntos de licenciamento da Microsoft. Para obter mais informações, veja [Preços do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/).
* A visualização e a aplicação de etiquetas em aplicações do Office estão sujeitas a [requisitos de licenciamento](https://docs.microsoft.com/microsoft-365/compliance/get-started-with-sensitivity-labels#subscription-and-licensing-requirements-for-sensitivity-labels).
* Para aplicar etiquetas a conteúdos do Power BI, um utilizador tem de ter uma licença do Power BI Pro, além de uma das licenças do Azure Information Protection mencionadas acima.
* Tem de ter as [licenças necessárias do Microsoft Cloud App Security](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls#microsoft-cloud-app-security-licensing) se quiser utilizá-lo para proteger os conteúdos do Power BI contra fugas e falhas indesejadas.

## <a name="considerations-and-limitations"></a>Considerações e limitações

A lista seguinte fornece algumas limitações de etiquetas de confidencialidade no Power BI:

**Geral**
* As etiquetas de confidencialidade só podem ser aplicadas em dashboards, relatórios, conjuntos de dados e fluxos de dados. Atualmente, não estão disponíveis para [relatórios paginados](../paginated-reports/report-builder-power-bi.md) e livros.
* As etiquetas de confidencialidade em recursos do Power BI estão visíveis nas vistas de lista de áreas de trabalho, linhagem, favoritos, recentes e aplicações. Atualmente, as etiquetas não estão visíveis na vista "Partilhado comigo". No entanto, repare que uma etiqueta aplicada a um recurso do Power BI, mesmo que não esteja visível, persiste sempre nos dados exportados para ficheiros Excel, PowerPoint e PDF.
* As etiquetas de confidencialidade só são suportadas para inquilinos na cloud (pública) global. As etiquetas de confidencialidade não são suportadas para inquilinos noutras clouds.
* As etiquetas de confidencialidade de dados não são suportadas para aplicações de modelo. As etiquetas de confidencialidade definidas pelo criador de aplicações de modelo serão removidas quando a aplicação é extraída e instalada e as etiquetas de confidencialidade adicionadas a artefactos numa aplicação de modelo instalada pelo consumidor de aplicações serão perdidas (repostas a zero) quando a aplicação é atualizada.
* O Power BI não suporta etiquetas de confidencialidade dos tipos de proteção [Não Reencaminhar](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions), [definido pelo utilizador](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions) e [HYOK](https://docs.microsoft.com/azure/information-protection/configure-adrms-restrictions). Os tipos de proteção Não Reencaminhar e definido pelo utilizador fazem referência a etiquetas definidas no [Centro de Segurança do Microsoft 365](https://security.microsoft.com/) ou no [Centro de Conformidade do Microsoft 365](https://compliance.microsoft.com/).
* Não é recomendado permitir que os utilizadores apliquem etiquetas principais no Power BI. Se uma etiqueta principal for aplicada ao conteúdo, a exportação de dados desse conteúdo para um ficheiro (Excel, PowerPoint e PDF) irá falhar. Veja [Sublabels (grouping labels)](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide#sublabels-grouping-labels) (Subetiquetas [etiquetas do agrupamento]).

**Exportar**
* Os controlos de proteção e etiquetas são impostos apenas quando os dados são exportados para ficheiros Excel, PowerPoint e PDF. Os controlos de proteção e etiquetas não são impostos quando os dados são exportado para ficheiros .csv ou .pbix, para a funcionalidade Analisar no Excel ou para qualquer outro caminho de exportação.
* Aplicar uma etiqueta de confidencialidade e proteção a um ficheiro exportado não adiciona marcação de conteúdo ao ficheiro. No entanto, se a etiqueta for configurada para aplicar marcações de conteúdo, estas são automaticamente aplicadas pelo cliente de etiquetagem unificada do Azure Information Protection quando o ficheiro é aberto em aplicações de computador do Office. As marcações de conteúdo não são aplicadas automaticamente ao utilizar a etiquetagem incorporada para aplicações Web, móveis e de computador. Para obter mais detalhes, veja [When Office apps apply content marking and encryption](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide#when-office-apps-apply-content-marking-and-encryption) (Quando é que as aplicações do Office aplicam marcação de conteúdo e encriptação).
* Um utilizador que exporte um ficheiro do Power BI tem permissões para aceder a e editar esse ficheiro de acordo com as definições das etiquetas de confidencialidade. Um utilizador que exporte os dados não obtém permissões de proprietário em relação ao ficheiro.
* A exportação irá falhar se uma etiqueta não puder ser aplicada quando os dados são exportados para um ficheiro. Para verificar se a exportação falhou porque a etiqueta não podia ser aplicada, clique no nome do relatório ou do dashboard no centro da barra de título e verifique se é apresentada a indicação "Não é possível carregar a etiqueta de confidencialidade" no menu pendente informativo aberto. Isto pode acontecer se o administrador de segurança tiver eliminado ou anulado a publicação da etiqueta aplicada, ou em resultado de um problema temporário do sistema.


## <a name="next-steps"></a>Próximos passos

Este artigo apresentou uma descrição geral da proteção de dados no Power BI. Os seguintes artigos fornecem mais detalhes sobre a proteção de dados no Power BI. 

* [Ativar etiquetas de confidencialidade de dados no Power BI](service-security-enable-data-sensitivity-labels.md)
* [Apply data sensitivity labels in Power BI](../collaborate-share/service-security-apply-data-sensitivity-labels.md) (Aplicar etiquetas de confidencialidade dos dados no Power BI)
* [Utilizar controlos do Microsoft Cloud App Security no Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Data protection metrics report](service-security-data-protection-metrics-report.md) (Relatório de métricas de proteção de dados)