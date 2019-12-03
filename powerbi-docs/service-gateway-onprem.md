---
title: Gateway de dados no local
description: Este artigo é uma descrição geral do gateway de dados no local do Power BI. Pode utilizar este gateway para trabalhar com origens de dados de DirectQuery. Também pode utilizar este gateway para atualizar os conjuntos de dados na cloud com dados no local.
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Gateways
ms.date: 07/15/2019
ms.openlocfilehash: f149b816f7489b6a26e86af6360062d86083a7e5
ms.sourcegitcommit: c839ef7437bc8fb8f7eeda23e59d05c7192a7fe8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/18/2019
ms.locfileid: "74164284"
---
# <a name="what-is-an-on-premises-data-gateway"></a>What is an on-premises data gateway? (O que é um gateway de dados no local?)

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Um gateway de dados no local atua como uma ponte para permitir a transferência rápida e segura de dados entre dados no local (dados que não estão na cloud) e vários serviços cloud da Microsoft. Estes serviços cloud incluem o Power BI, PowerApps, Power Automate, Azure Analysis Services e Azure Logic Apps. Através da utilização de um gateway, as organizações conseguem manter bases de dados e outras origens de dados nas suas redes no local, mas utilizar de forma segura esses dados no local em serviços cloud.

## <a name="how-the-gateway-works"></a>Como funciona o gateway

![Descrição geral do gateway](media/service-gateway-onprem/on-premises-data-gateway.png)

Para obter informações sobre a forma como o gateway funciona, veja [Arquitetura do gateway de dados no local](/data-integration/gateway/service-gateway-onprem-indepth).

## <a name="types-of-gateways"></a>Tipos de gateways

Há dois tipos diferentes de gateway, cada um para um cenário diferente:

* O **gateway de dados no local** permite que múltiplos utilizadores se liguem a múltiplas origens de dados no local. Pode utilizar um gateway de dados no local com todos os serviços suportados através de uma única instalação de gateway. Este gateway é adequado a cenários complexos com múltiplas pessoas que acedem a múltiplas origens de dados.

* O **gateway de dados no local (modo pessoal)** permite que um utilizador se ligue a origens e não pode ser partilhado com outras pessoas. O gateway de dados no local (modo pessoal) só pode ser utilizado com o Power BI. Este gateway é adequado para cenários em que o utilizador é a única pessoa responsável pela criação de relatórios e não precisa de partilhar nenhuma origem de dados com outras pessoas.

## <a name="use-a-gateway"></a>Utilizar um gateway

Existem quatro passos principais para utilizar um gateway.

1. [Transferir e instalar o gateway](/data-integration/gateway/service-gateway-install) num computador local.
1. [Configurar](/data-integration/gateway/service-gateway-app) o gateway com base na sua firewall e noutros requisitos de rede.
1. [Adicionar administradores de gateway](/data-integration/gateway/service-gateway-manage) que também consigam gerir e administrar outros requisitos de rede.
1. [Utilize o gateway](service-gateway-sql-tutorial.md) para atualizar uma origem de dados no local.
1. [Resolver problemas](service-gateway-onprem-tshoot.md) relacionados com o gateway em caso de erros.

## <a name="next-steps"></a>Próximos passos

* [Instalar o gateway de dados no local](/data-integration/gateway/service-gateway-install)

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
