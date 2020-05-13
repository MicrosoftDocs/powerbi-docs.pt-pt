---
title: Ativar etiquetas de confidencialidade de dados no Power BI
description: Saiba como ativar etiquetas de confidencialidade de dados no Power BI
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/25/2019
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: 60b7c858a98a105454efe0233484120ad4319f62
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83131896"
---
# <a name="enable-data-sensitivity-labels-in-power-bi-preview"></a>Ativar etiquetas de confidencialidade de dados no Power BI (pré-visualização)

Ao ativar [etiquetas de confidencialidade de dados do Microsoft Information Protection](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) no Power BI, aplica-se o seguinte:

* Determinados utilizadores e grupos de segurança numa organização podem classificar e [aplicar etiquetas de confidencialidade](../collaborate-share/service-security-apply-data-sensitivity-labels.md) aos seus dashboards, relatórios, conjuntos de dados e fluxos de dados do Power BI (adiante, designados *ativos*).
* Todos os membros da organização podem ver essas etiquetas.

As etiquetas de confidencialidade de dados promovem a proteção de dados ao sensibilizar os autores e os consumidores do Power BI para a confidencialidade dos dados, fornecendo informações sobre o que significa a classificação e como é que os dados com essa classificação devem ser processados.

Quando os dados do Power BI com uma etiqueta de confidencialidade de dados são exportados para um ficheiro PDF, do Excel ou do PowerPoint, essa etiqueta de confidencialidade de dados é incluída nos mesmos. Isto significa que um utilizador que não tenha permissão de acesso aos dados etiquetados, devido às políticas de etiquetas de confidencialidade, não conseguirá abrir os ficheiros *fora* do Power BI (nas aplicações de PDF, do Excel ou do PowerPoint).

Ativar etiquetas de confidencialidade de dados requer uma licença do Azure Information Protection. Veja [Licenciamento](#licensing) para obter mais detalhes.

## <a name="enable-data-sensitivity-labels"></a>Ativar etiquetas de confidencialidade de dados

Para ativar a utilização de etiquetas de confidencialidade de dados do Microsoft Information Protection no Power BI, aceda ao portal de Administração do Power BI, abra o painel de definições Inquilino e localize a secção Proteção de Informações.

![Localizar a secção Proteção de Informações](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-01.png)

Na secção **Proteção de Informações**, execute os seguintes passos:
1.  Ative o botão de alternar **Ativar etiquetas de confidencialidade do Microsoft Information Protection** e prima **Aplicar**. Este passo *apenas* torna as etiquetas de confidencialidade visíveis para toda a organização; não aplica nenhuma etiqueta. Para definir quem pode aplicar estas etiquetas no Power BI, necessita de concluir o Passo 2.
2.  Defina quem pode aplicar e alterar etiquetas de confidencialidade em ativos do Power BI. Este passo envolve três ações:
    1.  Ative o botão de alternar **Definir etiquetas de confidencialidade para conteúdos e dados do Power BI**.
    2.  Selecione os grupos de segurança relevantes. Por predefinição, todas as pessoas na sua organização poderão aplicar etiquetas de confidencialidade. No entanto, pode optar por ativar a definição de etiquetas de confidencialidade apenas para utilizadores ou grupos de segurança específicos. Ao selecionar toda a organização ou grupos de segurança específicos, pode excluir determinados subconjuntos de utilizadores ou grupos de segurança.
    * Quando as etiquetas de confidencialidade são ativadas para toda a organização, normalmente as exceções são os grupos de segurança.
    * Quando as etiquetas de confidencialidade são ativadas apenas para utilizadores ou grupos de segurança específicos, normalmente as exceções são os utilizadores específicos.  
    Esta abordagem permite impedir que determinados utilizadores apliquem etiquetas de confidencialidade no Power BI, mesmo que pertençam a um grupo com permissões para o fazer.
    
    3. Prima **Aplicar**.

![Ativar etiquetas de confidencialidade](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-02.png)

> [!IMPORTANT]
> Apenas os utilizadores do Power BI Pro com as permissões de *criação* e *edição* do ativo e que fazem parte do grupo de segurança relevante definido nesta secção poderão definir e editar as etiquetas de confidencialidade. Os utilizadores que não fazem parte desse grupo não poderão definir ou editar a etiqueta. 


## <a name="considerations-and-limitations"></a>Considerações e limitações

O Power BI utiliza etiquetas de confidencialidade do Microsoft Information Protection. Como tal, se for apresentada uma mensagem de erro ao tentar ativar etiquetas de confidencialidade, isso poderá dever-se a um dos seguintes motivos:

* Não tem uma [licença](#licensing) do Azure Information Protection.
* As etiquetas de confidencialidade não foram migradas para a versão do Microsoft Information Protection suportada pelo Power BI. Saiba mais sobre como [migrar etiquetas de confidencialidade](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels).
* Nenhuma etiqueta de confidencialidade do Microsoft Information Protection foi definida na organização. Além disso, para que possa utilizá-la, uma etiqueta tem de fazer parte de uma política publicada. [Saiba mais sobre etiquetas de confidencialidade](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels) ou aceda ao [centro de segurança e conformidade da Microsoft](https://sip.protection.office.com/sensitivity?flight=EnableMIPLabels) para saber como definir etiquetas e publicar políticas para a sua organização.

## <a name="licensing"></a>Licenciamento

* Para ver ou aplicar etiquetas do Microsoft Information Protection no Power BI, os utilizadores têm de ter uma licença Premium P1 ou Premium P2 do Azure Information Protection. O Microsoft Azure Information Protection pode ser adquirido como produto autónomo ou como parte de um dos conjuntos de licenciamento da Microsoft. Para obter mais informações, veja [Preços do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/).
* Os utilizadores que precisam de aplicar etiquetas a ativos do Power BI têm de ter uma licença do Power BI Pro.


## <a name="next-steps"></a>Próximas etapas

Este artigo descreveu como ativar etiquetas de confidencialidade de dados no Power BI. Os seguintes artigos fornecem mais detalhes sobre a proteção de dados no Power BI. 

* [Overview of data protection in Power BI](service-security-data-protection-overview.md) (Descrição geral da proteção de dados no Power BI)
* [Apply data sensitivity labels in Power BI](../collaborate-share/service-security-apply-data-sensitivity-labels.md) (Aplicar etiquetas de confidencialidade dos dados no Power BI)
* [Utilizar controlos do Microsoft Cloud App Security no Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Data protection metrics report](service-security-data-protection-metrics-report.md) (Relatório de métricas de proteção de dados)