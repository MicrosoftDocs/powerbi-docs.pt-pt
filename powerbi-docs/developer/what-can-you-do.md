---
title: Que podem os programadores fazer com o Power BI?
description: O Power BI oferece uma vasta gama de opções para programadores. Isto varia, desde a incorporação aos elementos visuais personalizados e conjuntos de dados de transmissão em fluxo.
author: markingmyname
ms.author: maghan
ms.date: 05/25/2018
ms.topic: overview
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 07fb8d365a6fe4a874b057a71a90a99fc8a9e5fa
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34564702"
---
# <a name="what-can-developers-do-with-power-bi"></a>O que podem os programadores fazer com o Power BI?

Os programadores têm várias opções para tentar incluir conteúdo do Power BI em aplicações. Estas opções incluem a **incorporação com o Power BI**, **elementos visuais personalizados** e **emitir dados via push para o Power BI**.

## <a name="embedding"></a>Incorporação
O serviço Power BI (SaaS) e o serviço Power BI Embedded no Azure (PaaS) têm APIs para incorporar os seus dashboards e relatórios. Tal significa que, ao incorporar o conteúdo, terá um conjunto de capacidades e acesso às funcionalidades mais recentes do Power BI, como dashboards, gateways e áreas de trabalho de aplicações.

Pode utilizar a [Ferramenta de experiência de inclusão](https://aka.ms/embedsetup) para começar rapidamente e transferir uma aplicação de exemplo.

Escolha a solução mais adequada para si:
* A solução [Incorporar para os seus clientes](embedding.md#embedding-for-your-customers) permite-lhe incorporar dashboards e relatórios para utilizadores que não têm uma conta para o Power BI. Execute a solução [Incorporar para os seus clientes](https://aka.ms/embedsetup/AppOwnsData).
* A solução [Incorporar para a sua organização](embedding.md#embedding-for-your-organization) permite-lhe alargar o serviço Power BI. Execute a solução [Incorporar a sua organização](https://aka.ms/embedsetup/UserOwnsData).

![Exemplo de PBIE](media/what-can-you-do/what-can-you-do-02.png)

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
