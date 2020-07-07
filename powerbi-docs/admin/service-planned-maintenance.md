---
title: Manutenção planeada do Power BI
description: Informação para administradores sobre como a manutenção planeada do Power BI afetará a organização e os próximos passos que podem ter de tomar.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/19/2020
ms.author: kfollis
ms.custom: MC
ROBOTS: NOINDEX
LocalizationGroup: Admin
ms.openlocfilehash: cc9364129159b5527d309f125d42e661d0b4c206
ms.sourcegitcommit: a58d10ca62bc55e83b58cf8e8495ac01a4bd6532
ms.contentlocale: pt-PT
ms.lasthandoff: 06/20/2020
ms.locfileid: "85120573"
---
# <a name="power-bi-planned-maintenance"></a>Manutenção planeada do Power BI

A manutenção planeada do serviço Power BI é uma parte necessária do nosso compromisso de disponibilizar um produto fiável aos nossos clientes. Quando a manutenção planeada está a decorrer, o serviço Power BI ficará indisponível para a organização durante algum tempo. Os utilizadores podem não conseguir aceder ao serviço Power BI e as operações em segundo plano podem não ser bem-sucedidas. Após o período de manutenção, esperamos que o serviço funcione normalmente e que ambas as operações, interativa e de segundo plano, sejam bem-sucedidas.  

A manutenção está prevista ocorrer fora do horário normal de expediente para ajudar a minimizar eventuais impactos na sua organização. Para as organizações que têm utilizadores em todo o mundo, reconhecemos que “fora do horário normal de expediente” pode afetá-lo de forma diferente. Pedimos desculpa por qualquer impacto nos utilizadores. Estamos a trabalhar arduamente para melhorar o Power BI e minimizar estes períodos de manutenção.

Se a sua organização for afetada, disponibilizaremos um aviso prévio. Os administradores do Microsoft 365 verão um aviso prévio no Centro de mensagens do Microsoft 365 e receberão um e-mail. Além disso, os clientes com contratos de Suporte Premier serão notificados através da equipa da conta Microsoft.

## <a name="actions-to-take-now"></a>Ações a tomar agora

* Os administradores do Microsoft 365 devem [verificar o Centro de mensagens](https://admin.microsoft.com/Adminportal/Home#/MessageCenter) quanto à existência de mensagens sobre manutenção planeada do Power BI. Partilhe a mensagem com as pessoas que devem ter conhecimento, mas que podem não ter acesso ao Centro de mensagens.
* Se não for administrador do Microsoft 365, contacte o departamento de TI ou as equipas de suporte interno para se informar sobre qualquer manutenção futura.

## <a name="actions-to-take-when-maintenance-is-complete"></a>Ações a tomar quando a manutenção for concluída

* Os utilizadores devem atualizar as janelas abertas do browser.
* Os utilizadores da aplicação Power BI Mobile terão de verificar se estão a utilizar a versão mais recente e, depois, terminar sessão e voltar a iniciar sessão na aplicação. Veja a loja de aplicações do telemóvel ou a nossa página [Power BI Mobile](https://powerbi.microsoft.com/mobile/).
* Os clientes que estavam ativamente a editar ou publicar relatórios que utilizam elementos visuais organizacionais, localmente ou a partir de localizações do OneDrive e do SharePoint, terão de reimportar o elemento visual através da loja de elementos visuais da organização ou transferir um PBIX atualizado antes de serem republicados. Para obter mais informações sobre os elementos visuais organizacionais, veja [Elementos visuais da organização](service-admin-portal.md#organization-visuals).
* Se os livros do Excel que utilizam a funcionalidade Analisar no Excel não forem atualizados, poderá ter de atualizar a cadeia de ligação ou transferir novamente a ligação ODC desse conjunto de dados. Para obter mais informações, veja [Analisar no Excel](../collaborate-share/service-analyze-in-excel.md#connect-to-power-bi-data).
* As ligações ao Power BI incorporadas no conteúdo podem não conseguir ligar-se enquanto a manutenção estiver a ser realizada. Por exemplo, uma ligação incorporada no SharePoint ou Teams pode resultar num erro do utilizador. Para resolver este problema, tem de regenerar a ligação incorporada no Power BI e, em seguida, atualizar as localizações onde são utilizadas. Para obter mais informações sobre as ligações incorporadas, veja [Incorporar uma peça Web de relatórios no SharePoint Online](../collaborate-share/service-embed-report-spo.md) e [Colaborar com o Microsoft Teams Power BI](../collaborate-share/service-embed-report-microsoft-teams.md).

## <a name="next-steps"></a>Próximos passos

* [Ativar as notificações de interrupção do serviço](service-interruption-notifications.md)
* [Controlar a próxima alteração no Centro de mensagens](https://docs.microsoft.com/microsoft-365/admin/manage/message-center?view=o365-worldwide)
