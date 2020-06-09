---
title: Ativar etiquetas de confidencialidade de dados no Power BI
description: Saiba como ativar etiquetas de confidencialidade de dados no Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/23/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: ba1cacfa930bcc0ed51234dea13639420ac8fab7
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315655"
---
# <a name="enable-data-sensitivity-labels-in-power-bi"></a>Ativar etiquetas de confidencialidade de dados no Power BI

Para que as [etiquetas de confidencialidade de dados do Microsoft Information Protection](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) sejam utilizadas no Power BI, têm de ser ativadas no inquilino. Este artigo explica como os administradores de inquilinos do Power BI podem fazê-lo. Para obter uma descrição geral das etiquetas de confidencialidade de dados no Power BI, veja [Proteção de dados no Power BI](service-security-data-protection-overview.md). Para obter informações sobre a aplicação de etiquetas de confidencialidade no Power BI, veja [Aplicar etiquetas de confidencialidade](../collaborate-share/service-security-apply-data-sensitivity-labels.md). 

Quando as etiquetas de confidencialidade estão ativadas:

* Os utilizadores e os grupos de segurança especificados na organização podem classificar e [aplicar etiquetas de confidencialidade](../collaborate-share/service-security-apply-data-sensitivity-labels.md) aos seus relatórios, dashboards, conjuntos de dados e fluxos de dados do Power BI.
* Todos os membros da organização podem ver essas etiquetas.

Ativar etiquetas de confidencialidade de dados requer uma licença do Azure Information Protection. Veja [Licenciamento](service-security-data-protection-overview.md#licensing) para obter detalhes.

## <a name="enable-data-sensitivity-labels"></a>Ativar etiquetas de confidencialidade de dados

Aceda ao **Portal de administração** do Power BI, abra o painel **Definições de inquilino** e localize a secção **Proteção de informações**.

![Localizar a secção Proteção de Informações](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-01.png)

Na secção **Proteção de Informações**, execute os seguintes passos:
1. Abra a opção **Permitir que os utilizadores apliquem etiquetas de confidencialidade para conteúdo do Power BI**.
1. Utilize o botão de alternar para ativar.
1. Defina quem pode aplicar e alterar etiquetas de confidencialidade em ativos do Power BI. Por predefinição, todas as pessoas na sua organização poderão aplicar etiquetas de confidencialidade. No entanto, pode optar por ativar a definição de etiquetas de confidencialidade apenas para utilizadores ou grupos de segurança específicos. Ao selecionar toda a organização ou grupos de segurança específicos, pode excluir determinados subconjuntos de utilizadores ou grupos de segurança.
   
   * Quando as etiquetas de confidencialidade são ativadas para toda a organização, normalmente as exceções são os grupos de segurança.
   * Quando as etiquetas de confidencialidade são ativadas apenas para utilizadores ou grupos de segurança específicos, normalmente as exceções são os utilizadores específicos.  
    Esta abordagem permite impedir que determinados utilizadores apliquem etiquetas de confidencialidade no Power BI, mesmo que pertençam a um grupo com permissões para o fazer.

1. Prima **Aplicar**.

![Ativar etiquetas de confidencialidade](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-02.png)

> [!IMPORTANT]
> Apenas os utilizadores do Power BI Pro com as permissões de *criação* e *edição* do ativo e que fazem parte do grupo de segurança relevante definido nesta secção poderão definir e editar as etiquetas de confidencialidade. Os utilizadores que não fazem parte desse grupo não poderão definir ou editar a etiqueta.  

## <a name="troubleshooting"></a>Resolução de problemas

O Power BI utiliza etiquetas de confidencialidade do Microsoft Information Protection. Como tal, se for apresentada uma mensagem de erro ao tentar ativar etiquetas de confidencialidade, isso poderá dever-se a um dos seguintes motivos:

* Não tem uma [licença](service-security-data-protection-overview.md#licensing) do Azure Information Protection.
* As etiquetas de confidencialidade não foram migradas para a versão do Microsoft Information Protection suportada pelo Power BI. Saiba mais sobre como [migrar etiquetas de confidencialidade](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels).
* Nenhuma etiqueta de confidencialidade do Microsoft Information Protection foi definida na organização. Tenha em atenção que, para que possa utilizá-la, uma etiqueta tem de fazer parte de uma política publicada. [Saiba mais sobre etiquetas de confidencialidade](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels) ou aceda ao [centro de segurança e conformidade da Microsoft](https://sip.protection.office.com/sensitivity?flight=EnableMIPLabels) para saber como definir etiquetas e publicar políticas para a sua organização.

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

Este artigo descreveu como ativar etiquetas de confidencialidade de dados no Power BI. Os seguintes artigos fornecem mais detalhes sobre a proteção de dados no Power BI. 

* [Overview of data protection in Power BI](service-security-data-protection-overview.md) (Descrição geral da proteção de dados no Power BI)
* [Apply data sensitivity labels in Power BI](../collaborate-share/service-security-apply-data-sensitivity-labels.md) (Aplicar etiquetas de confidencialidade dos dados no Power BI)
* [Utilizar controlos do Microsoft Cloud App Security no Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Data protection metrics report](service-security-data-protection-metrics-report.md) (Relatório de métricas de proteção de dados)