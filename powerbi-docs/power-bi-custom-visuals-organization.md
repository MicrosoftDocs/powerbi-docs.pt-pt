---
title: Utilizar elementos visuais personalizados da organização no Power BI
description: Utilizar, gerir e criar elementos visuais personalizados organizacionais no Power BI
services: powerbi
documentationcenter: ''
author: markingmyname
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/06/2018
ms.author: maghan
LocalizationGroup: Visualizations
ms.openlocfilehash: 1f3a3586b3aecb10b07bd171ab7349c4e1089cec
ms.sourcegitcommit: afa10c016433cf72d6d366c024b862187a8692fd
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/04/2018
---
# <a name="using-organization-custom-visuals-in-power-bi"></a>Utilizar elementos visuais personalizados da organização no Power BI

Pode utilizar elementos visuais personalizados no Power BI para criar um tipo de elemento visual único adaptado a si ou utilizar as informações de dados que está a tentar transmitir. Muitas vezes, estes elementos visuais personalizados são criados pelos programadores e são frequentemente criados quando os diversos elementos visuais que estão incluídos no Power BI não satisfazem as necessidades. 

Em algumas organizações, os elementos visuais personalizados são ainda mais importantes – podem ser precisos para transmitir dados específicos ou informações exclusivas para a organização, podem ter requisitos especiais de dados ou podem realçar métodos de negócio privados. Tais organizações precisam de desenvolver elementos visuais personalizados e de os partilhar em toda a organização, pelo que garanta que estão corretamente mantidos. Os elementos visuais personalizados do Power BI permitem às organizações fazer isso mesmo.

A imagem seguinte mostra o processo pelo qual os elementos visuais personalizados da organização no Power BI fluem do administrador, passando pelo desenvolvimento e manutenção, até chegarem ao analista de dados.

![](media/power-bi-custom-visuals-organizational/custom-visual-org-01.jpg)

Os elementos visuais da organização são implementados e geridos pelo administrador do Power BI no Portal de administração. Depois de implementados no repositório organizacional, os utilizadores na organização podem facilmente descobri-los e importar os elementos visuais personalizados organizacionais para os relatórios diretamente a partir do Power BI Desktop.

## <a name="using-organizational-custom-visuals"></a>Utilizar os elementos visuais personalizados organizacionais

Para obter mais informações sobre como utilizar os elementos visuais personalizados organizacionais nos relatórios que criou, veja o seguinte artigo: [Saiba mais sobre como importar os elementos visuais organizacionais para os relatórios](power-bi-custom-visuals.md).
 
## <a name="administering-organizational-custom-visuals"></a>Administrar os elementos visuais personalizados organizacionais

Para saber mais sobre como administrar, implementar e gerir os elementos visuais personalizados organizacionais na sua organização, veja o seguinte artigo: [Saiba mais sobre a implementação e gestão dos elementos visuais personalizados da organização](https://go.microsoft.com/fwlink/?linkid=866790).

> [!WARNING]
> Um elemento visual personalizado pode conter código com riscos de privacidade ou segurança. Garanta que confia no autor e na origem de qualquer elemento visual personalizado antes de o implementar no repositório da organização. 
> 

## <a name="considerations-and-limitations"></a>Considerações e limitações
 
Existem várias considerações e limitações que deve ter em consideração.
 
Administrador:

* Os elementos visuais personalizados legados (por exemplo, os elementos visuais personalizados que não foram criados sobre as APIs da nova versão) não são suportados

* Se um elemento visual personalizado for eliminado do repositório, todos os relatórios existentes que utilizem o elemento visual eliminado deixarão de ser compostos. A operação de eliminação do repositório não é reversível. Para desativar temporariamente um elemento visual personalizado, utilize a funcionalidade “Desativar”.
 
Utilizador final:

* Coleção de Espaços de Trabalho do Power BI não é suportada para os elementos visuais da organização

* O elemento visual do Visio, o elemento visual do PowerApps e o elemento visual do GlobeMap do marketplace do AppSource não serão compostos se forem implementados através do repositório da organização
