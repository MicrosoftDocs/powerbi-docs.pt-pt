---
title: Gateway de dados local
description: Esta é uma descrição geral do gateway de dados no local para o Power BI. Pode utilizar este gateway para trabalhar com origens de dados de DirectQuery. Também pode utilizar este gateway para atualizar os conjuntos de dados na cloud com dados no local.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Gateways
ms.date: 07/15/2019
ms.openlocfilehash: 57c4292913a2056ab285716de1e1b83e2313f723
ms.sourcegitcommit: 9d13ef7a257b5006fca5f92acf5b611f5cd143a2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/18/2019
ms.locfileid: "68307105"
---
# <a name="what-is-an-on-premises-data-gateway"></a>What is an on-premises data gateway? (O que é um gateway de dados no local?)

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

O gateway de dados no local funciona como uma ponte ao proporcionar a transferência de dados de forma rápida e segura entre dados no local (dados que não estão na cloud) e vários serviços cloud da Microsoft, incluindo o Power BI, o PowerApps, o Microsoft Flow, o Azure Analysis Services e o Logic Apps. Através da utilização de um gateway, as organizações conseguem manter bases de dados e outras origens de dados nas suas redes no local, mas utilizar de forma segura esses dados no local em serviços cloud.

## <a name="how-the-gateway-works"></a>Como funciona o gateway

![Descrição geral do gateway](media/service-gateway-onprem/on-premises-data-gateway.png)

Para obter informações detalhadas sobre a forma como o gateway funciona, veja [Arquitetura do gateway de dados no local](/data-integration/gateway/service-gateway-onprem-indepth).

## <a name="types-of-gateways"></a>Tipos de gateways

Há dois tipos diferentes de gateway, cada um para um cenário diferente:

* **Gateway de dados no local** – permite que vários utilizadores se liguem a várias origens de dados no local. Pode utilizar um gateway de dados no local com todos os serviços suportados através de uma única instalação de gateway. Este gateway é adequado a cenários complexos com múltiplas pessoas que acedem a múltiplas origens de dados.

* **Gateway de dados no local (modo pessoal)** – permite que um utilizador estabeleça ligação a origens e não pode ser partilhado com outras pessoas. O gateway de dados no local (modo pessoal) só pode ser utilizado com o Power BI. Este gateway é adequado para cenários em que o utilizador é a única pessoa responsável pela criação de relatórios e não precisa de partilhar nenhuma origem de dados com outras pessoas.

## <a name="using-a-gateway"></a>Utilizar um gateway

Existem quatro passos principais para utilizar um gateway:

1. [Transferir e instalar o gateway](/data-integration/gateway/service-gateway-install) num computador local.
2. [Configurar](/data-integration/gateway/service-gateway-app) o gateway com base na sua firewall e noutros requisitos de rede.
3. [Adicionar administradores de gateway](/data-integration/gateway/service-gateway-manage) que também consigam gerir e administrar outros requisitos de rede.
4. [Resolver problemas](service-gateway-onprem-tshoot.md) relacionados com o gateway em caso de erros.

## <a name="next-steps"></a>Próximos passos

* [Instalar o gateway de dados no local](/data-integration/gateway/service-gateway-install)


Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)
