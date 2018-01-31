---
title: Que podem os programadores fazer com o Power BI?
description: "O Power BI oferece uma vasta gama de opções para programadores. Isto varia, desde a incorporação aos elementos visuais personalizados e conjuntos de dados de transmissão em fluxo."
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
ms.date: 07/20/2017
ms.author: maghan
ms.openlocfilehash: b310562ac31694f398a659018743b8fa7aa46e35
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2018
---
# <a name="what-can-developers-do-with-power-bi"></a>Que podem os programadores fazer com o Power BI?
O Power BI oferece uma vasta gama de opções para programadores. Isto varia, desde a incorporação aos elementos visuais personalizados e conjuntos de dados de transmissão em fluxo.

## <a name="embedding"></a>Incorporação
O serviço Power BI e o Power BI Embedded no Azure estão disponíveis em conjunto para oferecer uma única API para incorporar os seus dashboards e relatórios. Isto significa que, ao incorporar o conteúdo, terá uma superfície de API, um conjunto consistente de capacidades e acesso às funcionalidades mais recentes do Power BI, como dashboards, gateways e áreas de trabalho de aplicações. Para obter mais informações, veja [Incorporar no Power BI](embedding.md).

![](media/what-can-you-do/powerbi-embed-sample.png)

## <a name="custom-visuals"></a>Elementos visuais personalizados
Os elementos visuais personalizados permitem-lhe criar os seus próprios elementos visuais para utilização nos relatórios do Power BI. Os elementos visuais personalizados são escritos em TypeScript, um superconjunto de JavaScript que suporta algumas funcionalidades avançadas e acesso atempado à funcionalidade ES6/ES7. O estilo visual é processado através de folhas de estilo (css). Para sua comodidade, utilizamos o pré-compilador Less, que suporta algumas funcionalidades avançadas, como aninhamento, variáveis, misturas, condições, ciclos, etc. Se não quiser utilizar algumas dessas funcionalidades, pode escrever css simples no ficheiro less.

Para obter mais informações sobre como desenvolver e publicar um elemento visual personalizado, consulte [Publicar elementos visuais personalizados na Loja Office](office-store.md).

![](media/what-can-you-do/powerbi-custom-visual-store.png)

## <a name="push-data-into-power-bi"></a>Enviar dados por push para o Power BI
Pode utilizar a API do Power BI para enviar dados por push para um conjunto de dados. Isto permite-lhe adicionar uma linha à tabela dentro de um conjunto de dados. Os novos dados podem então ser refletidos nos mosaicos num dashboard e em elementos visuais dentro do seu relatório.

Para obter mais informações, veja [Enviar dados por push para um dashboard](walkthrough-push-data.md)

## <a name="next-steps"></a>Passos seguintes
[Incorporar com o Power BI](embedding.md)  
[Como migrar conteúdo da coleção de áreas de trabalho do Power BI Embedded para o Power BI](migrate-from-powerbi-embedded.md)  
[Repositório Git da API JavaScript](https://github.com/Microsoft/PowerBI-JavaScript)  
[Repositório Git C# do Power BI](https://github.com/Microsoft/PowerBI-CSharp)  
[Publicar elementos visuais personalizados na Loja Office](office-store.md)  
[Reposição Git de Elementos Visuais do Power BI](https://github.com/Microsoft/PowerBI-visuals)  
[Exemplo de incorporação de JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[Documento técnico do Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

