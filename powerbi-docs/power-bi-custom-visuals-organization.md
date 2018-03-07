---
title: "Utilizar elementos visuais personalizados da organização no Power BI"
description: "Utilizar, gerir e criar elementos visuais personalizados organizacionais no Power BI"
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 02/06/2018
ms.author: maghan
LocalizationGroup: Visualizations
ms.openlocfilehash: 6f7827f7804fcd52e7d922ebc8ffad5a8036b33c
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="using-organization-custom-visuals-in-power-bi-preview"></a>Utilizar elementos visuais personalizados da organização no Power BI (Pré-visualização)

Pode utilizar elementos visuais personalizados no Power BI para criar um tipo de elemento visual único adaptado a si ou utilizar as informações de dados que está a tentar transmitir. Muitas vezes, estes elementos visuais personalizados são criados pelos programadores e são frequentemente criados quando os diversos elementos visuais que estão incluídos no Power BI não satisfazem as necessidades. 

Em algumas organizações, os elementos visuais personalizados são ainda mais importantes – podem ser precisos para transmitir dados específicos ou informações exclusivas para a organização, podem ter requisitos especiais de dados ou podem realçar métodos de negócio privados. Tais organizações precisam de desenvolver elementos visuais personalizados e de os partilhar em toda a organização, pelo que garanta que estão corretamente mantidos. Os elementos visuais personalizados do Power BI (agora em pré-visualização) permitem às organizações fazer isso mesmo. 

A imagem seguinte mostra o processo pelo qual os elementos visuais personalizados da organização (pré-visualização) no Power  BI fluem do administrador, passando pelo desenvolvimento e manutenção, até chegarem ao analista de dados.

![](media/power-bi-custom-visuals-organizational/custom-visual-org-01.jpg)

## <a name="how-to-enable-organizational-custom-visuals-preview"></a>Como ativar elementos visuais personalizados organizacionais (pré-visualização)

Os elementos visuais personalizados da organização estão atualmente em Pré-visualização, pelo que tem de ativar a funcionalidade no Power BI Desktop. Para ativar esta funcionalidade de pré-visualização, no friso, selecione Ficheiro > Opções e definições > Opções, em seguida, no painel esquerdo, selecione Funcionalidades de pré-visualização, selecione a caixa de verificação junto a Os elementos visuais personalizados da minha organização, conforme mostrado na imagem seguinte.

![](media/power-bi-custom-visuals-organizational/custom-visual-org-02.jpg)

Os elementos visuais da organização são implementados e geridos pelo administrador do Power BI no Portal de administração. Depois de implementados no repositório organizacional, os utilizadores na organização podem facilmente descobri-los e importar os elementos visuais personalizados organizacionais para os relatórios diretamente a partir do Power BI Desktop.

## <a name="using-organizational-custom-visuals"></a>Utilizar os elementos visuais personalizados organizacionais

Para obter mais informações sobre como utilizar os elementos visuais personalizados organizacionais nos relatórios que criou, veja o seguinte artigo: [Saiba mais sobre como importar os elementos visuais organizacionais para os relatórios](power-bi-custom-visuals.md).
 
## <a name="administering-organizational-custom-visuals"></a>Administrar os elementos visuais personalizados organizacionais

Para saber mais sobre como administrar, implementar e gerir os elementos visuais personalizados organizacionais na sua organização, veja o seguinte artigo: [Saiba mais sobre a implementação e gestão dos elementos visuais personalizados da organização](https://go.microsoft.com/fwlink/?linkid=866790).

> [!WARNING]
> Um elemento visual personalizado pode conter código com riscos de privacidade ou segurança. Garanta que confia no autor e na origem de qualquer elemento visual personalizado antes de o implementar no repositório da organização. 
> 

## <a name="considerations-and-limitations"></a>Considerações e limitações
 
Uma vez que os elementos visuais personalizados organizacionais estão em pré-visualização, existem algumas considerações e limitações que tem de ter em consideração.
 
Administrador:

* Os elementos visuais personalizados legados (por exemplo, os elementos visuais personalizados que não foram criados sobre as APIs da nova versão) não são suportados

* A atualização no local ainda não é suportada. Para atualizar um elemento visual, tem de carregar uma nova versão do elemento visual para o repositório da organização (confirme também que tem o mesmo ID de Elemento Visual no ficheiro PBIVIZ). Os autores do relatório podem, em seguida, importar a nova versão para o relatório deles e fazer uma substituição no local da versão atual do elemento visual no relatório.

* Se um elemento visual personalizado for eliminado do repositório, todos os relatórios existentes que utilizem o elemento visual eliminado deixarão de ser compostos. A operação de eliminação do repositório não é reversível.
 
Utilizador final:

* Não é suportada a utilização do mesmo elemento visual (o mesmo ID de Elemento Visual) do marketplace público (AppSource) e do repositório da organização. Nessa circunstância, será utilizado o mais recente elemento visual que foi importado.

* Não é suportada a partilha externa de elementos visuais organizacionais nos dashboards e nos relatórios. Os utilizadores externos à organização que visualizem um dashboard com um elemento visual personalizado organizacional verão um elemento visual em branco. 

* Coleção de Espaços de Trabalho do Power BI não é suportada para os elementos visuais da organização

* Os elementos visuais personalizados da organização nos relatórios que são publicados na Web não serão compostos

* O elemento visual do Visio, o elemento visual do PowerApps e o elemento visual do GlobeMap do marketplace do AppSource não serão compostos se forem implementados através do repositório da organização

* Se o administrador eliminar um elemento visual personalizado do repositório e esse elemento visual for utilizado num relatório, o elemento visual deixará de compor e terá de ser removido do relatório para poder guardar o relatório