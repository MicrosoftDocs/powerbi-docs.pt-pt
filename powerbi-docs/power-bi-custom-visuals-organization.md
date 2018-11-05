---
title: Utilizar elementos visuais personalizados da organização no Power BI
description: Utilizar, gerir e criar elementos visuais personalizados organizacionais no Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 10/29/2018
LocalizationGroup: Visualizations
ms.openlocfilehash: 6fc21a9b8558b554cae6e9096aaee0fbaabcdaf3
ms.sourcegitcommit: f9dd6098ca57d4d6cad34284126d4e58eab1c92c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/29/2018
ms.locfileid: "50222088"
---
# <a name="use-organizational-custom-visuals-in-power-bi"></a>Utilizar elementos visuais personalizados organizacionais no Power BI

Pode utilizar elementos visuais personalizados no Power BI para criar um tipo de elemento visual único adaptado a si ou utilizar as informações de dados que está a tentar transmitir. Muitas vezes, estes elementos visuais personalizados são criados pelos programadores e são frequentemente criados quando os diversos elementos visuais que estão incluídos no Power BI não satisfazem as necessidades. 

Em algumas organizações, os elementos visuais personalizados são ainda mais importantes – podem ser precisos para transmitir dados específicos ou informações exclusivas para a organização, podem ter requisitos especiais de dados ou podem realçar métodos de negócio privados. Tais organizações precisam de desenvolver elementos visuais personalizados e de os partilhar em toda a organização, pelo que garanta que estão corretamente mantidos. Os elementos visuais personalizados do Power BI permitem às organizações fazer isso mesmo.

A imagem seguinte mostra o processo pelo qual os elementos visuais personalizados organizacionais no Power BI são transmitidos do administrador, passando pelo desenvolvimento e manutenção, até chegarem ao analista de dados.

![Imagem dos elementos visuais personalizados](media/power-bi-custom-visuals-organizational/custom-visual-org-01.jpg)

Os elementos visuais da organização são implementados e geridos pelo administrador do Power BI no Portal de administração. Depois de implementados no repositório organizacional, os utilizadores na organização podem facilmente descobri-los e importar os elementos visuais personalizados organizacionais para os relatórios diretamente a partir do Power BI Desktop.

Para obter mais informações sobre como utilizar os elementos visuais personalizados organizacionais nos relatórios que criou, veja o seguinte artigo: [Saiba mais sobre como importar os elementos visuais organizacionais para os relatórios](power-bi-custom-visuals.md).

## <a name="administer-organizational-custom-visuals"></a>Administrar os elementos visuais personalizados organizacionais

Para saber mais sobre como administrar, implementar e gerir os elementos visuais personalizados organizacionais na sua organização, veja o seguinte artigo: [Saiba mais sobre a implementação e gestão dos elementos visuais personalizados da organização](https://go.microsoft.com/fwlink/?linkid=866790).

> [!WARNING]
> Um elemento visual personalizado pode conter código com riscos de privacidade ou segurança. Garanta que confia no autor e na origem de qualquer elemento visual personalizado antes de o implementar no repositório da organização.

## <a name="considerations-and-limitations"></a>Considerações e limitações

Existem várias considerações e limitações que deve ter em consideração.

Administrador:

* Os elementos visuais personalizados legados (por exemplo, os elementos visuais personalizados que não foram criados sobre as APIs da nova versão) não são suportados

* Se um elemento visual personalizado for eliminado do repositório, todos os relatórios existentes que utilizem o elemento visual eliminado deixarão de ser compostos. A operação de eliminação do repositório não é reversível. Para desativar temporariamente um elemento visual personalizado, utilize a funcionalidade “Desativar”.

Utilizador final:

* Os elementos visuais personalizados organizacionais são os elementos visuais privados importados do repositório da organização. À semelhança de qualquer elemento visual privado, não podem ser [exportados para o PowerPoint](https://docs.microsoft.com/power-bi/consumer/end-user-powerpoint) nem apresentados nos e-mails recebidos quando um utilizador [subscreve páginas de relatórios](https://docs.microsoft.com/power-bi/consumer/end-user-subscribe). Apenas os [elementos visuais personalizados certificados](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified) importados diretamente do Marketplace suportam estas funcionalidades.

* Os elementos visuais do Visio, do PowerApps, do Mapbox e do GlobeMap do marketplace do AppSource não serão compostos se forem implementados através do repositório da organização.

Para obter mais informações e respostas a perguntas, aceda às [perguntas frequentes](power-bi-custom-visuals-faq.md#organizational-custom-visuals).