---
title: Ligar a dados criados por fluxos de dados do Power BI no Power BI Desktop (Beta)
description: Ligar a e utilizar facilmente fluxos de dados no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/06/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f87db1f715118f346e3b8069897e92fd157f881c
ms.sourcegitcommit: b23fdcc0ceff5acd2e4d52b15b310068236cf8c7
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/07/2018
ms.locfileid: "51265938"
---
# <a name="connect-to-data-created-by-power-bi-dataflows-in-power-bi-desktop-beta"></a>Ligar a dados criados por fluxos de dados do Power BI no Power BI Desktop (Beta)
No **Power BI Desktop**, pode ligar a dados criados por **fluxos de dados do Power BI** tal como faria com outra origem de dados no Power BI Desktop.

![Ligar a fluxos de dados](media/desktop-connect-dataflows/connect-dataflows_01.png)

O conector de **fluxos de dados do Power BI (Beta)** permite-lhe ligar a entidades criadas por fluxos de dados no serviço Power BI. 

## <a name="considerations-and-limitations"></a>Considerações e limitações

Para utilizar esta versão Beta do **conector de fluxos de dados do Power BI**, tem de executar a versão mais recente do **Power BI Desktop**. Pode sempre [transferir o Power BI Desktop](desktop-get-the-desktop.md) e instalá-lo no seu computador para se certificar de que tem a versão mais recente.  

> [!NOTE]
> A versão anterior do conector de fluxos de dados do Power BI exigia que transferisse um ficheiro .MEZ e o colocasse numa pasta. As versões atuais do **Power BI Desktop** incluem o conector de fluxos de dados do Power BI, ou seja, esse ficheiro já não é necessário e pode entrar em conflito com a versão incluída do conector. Se tiver colocado manualmente esse ficheiro .MEZ na pasta, *terá* de eliminar esse ficheiro .MEZ da pasta **Documentos > Power BI Desktop > Conectores personalizados** para evitar conflitos. 

## <a name="desktop-performance"></a>Desempenho do Desktop
O **Power BI Desktop** é executado localmente no computador em que está instalado. O desempenho da ingestão de fluxos de dados é determinado por uma variedade de fatores. Esses fatores incluem o tamanho dos dados, a CPU e a RAM do computador, a largura de banda de rede, a distância do centro de dados e outros fatores.

Pode melhorar o desempenho da ingestão de dados dos fluxos de dados. Por exemplo, se o tamanho dos dados ingeridos for demasiado grande para o **Power BI Desktop** gerir no computador, poderá utilizar entidades ligadas e calculadas nos fluxos de dados para agregar os dados (dentro dos fluxos de dados) e ingerir apenas os dados preparados previamente e agregados. Dessa forma, o processamento de dados de grandes dimensões é realizado online nos fluxos de dados, em vez de ser feito localmente na instância em execução do **Power BI Desktop**. Essa abordagem permite ingerir quantidades mais pequenas de dados do Power BI Desktop e a experiência com os fluxos de dados permanece rápida e reativa.


## <a name="next-steps"></a>Próximos passos
Existem inúmeras coisas interessantes que pode fazer com os fluxos de dados do Power BI. Para obter mais informações, consulte os seguintes recursos:

* [Preparação personalizada de dados com fluxos de dados](service-dataflows-overview.md)
* [Criar e utilizar fluxos de dados no Power BI](service-dataflows-create-use.md)
* [Utilizar entidades calculadas no Power BI Premium (Pré-visualização)](service-dataflows-computed-entities-premium.md)
* [Utilizar fluxos de dados com origens de dados no local (Pré-visualização)](service-dataflows-on-premises-gateways.md)
* [Recursos para programadores de fluxos de dados do Power BI (Pré-visualização)](service-dataflows-developer-resources.md)

Também existem artigos sobre o **Power BI Desktop** que poderão ser úteis:

* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Introduzir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

