---
title: Que podem os programadores fazer com o Power BI?
description: O Power BI oferece uma vasta gama de opções para programadores. Isto varia, desde a incorporação aos elementos visuais personalizados e conjuntos de dados de transmissão em fluxo.
author: markingmyname
ms.author: maghan
ms.date: 05/03/2018
ms.topic: overview
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: mvc
manager: kfile
ms.openlocfilehash: ee9f5b2e89a1746267090da3485076d67a99d6f9
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34290574"
---
# <a name="what-can-developers-do-with-power-bi"></a>O que podem os programadores fazer com o Power BI?

Os programadores têm várias opções para tentar incluir conteúdo do Power BI em aplicações. Estas opções incluem a **incorporação com o Power BI**, **elementos visuais personalizados** e **emitir dados via push para o Power BI**.

## <a name="embedding"></a>Incorporação
O serviço Power BI (SaaS) e o serviço Power BI Embedded no Azure (PaaS) têm APIs para incorporar os seus dashboards e relatórios. Tal significa que, ao incorporar o conteúdo, terá um conjunto de capacidades e acesso às funcionalidades mais recentes do Power BI, como dashboards, gateways e áreas de trabalho de aplicações.

![Exemplo de PBIE](media/what-can-you-do/what-can-you-do-01.png)

## <a name="develop-custom-visuals"></a>Desenvolver elementos visuais personalizados
Os elementos visuais personalizados permitem-lhe criar os seus próprios elementos visuais para utilização nos relatórios do Power BI. Os elementos visuais personalizados são escritos no TypeScript, que é um superconjunto do JavaScript. O TypeScript suporta algumas funcionalidades avançadas e o acesso antecipado à funcionalidade ES6/ES7. O estilo visual é processado através de folhas de estilo (css). Para sua comodidade, utilizamos o pré-compilador Less, que suporta algumas funcionalidades avançadas, como aninhamento, variáveis, condições, ciclos, etc. Se não quiser utilizar algumas dessas funcionalidades, pode escrever css simples no ficheiro less.

![Exemplo de CV](media/what-can-you-do/powerbi-custom-visual-store.png)

## <a name="push-data-into-power-bi"></a>Enviar dados por push para o Power BI
Pode utilizar a API do Power BI para enviar dados por push para um conjunto de dados. Isto permite-lhe adicionar uma linha à tabela dentro de um conjunto de dados. Os novos dados podem então ser refletidos nos mosaicos num dashboard e em elementos visuais dentro do seu relatório.

![Exemplo de dados emitidos via push](media/what-can-you-do/powerbi-push-data.png)

## <a name="next-steps"></a>Próximos passos
[Incorporar com o Power BI](embedding.md)  
[Publicar elementos visuais personalizados na Loja Office](office-store.md)  
[Push data into a dashboard (Enviar dados por push para um dashboard)](walkthrough-push-data.md)
