---
title: Service interruption notifications (Notificações de interrupção do serviço)
description: Saiba mais sobre como receber notificações por e-mail em caso de interrupção ou degradação do serviço Power BI.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/11/2020
ms.author: kfollis
ms.openlocfilehash: 344ce3b83bbb9922e0359e04e65c01a1a088bcb3
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83135374"
---
# <a name="service-interruption-notifications"></a>Service interruption notifications (Notificações de interrupção do serviço)

É fundamental ter informações sobre a disponibilidade das aplicações empresariais essenciais para a sua atividade. O Power BI fornece notificações de incidentes para que possa, opcionalmente, receber e-mails em caso de interrupção ou degradação do serviço. Apesar de o SLA (Contrato de Nível de Serviço) de 99,9% do Power BI faça com que estas ocorrências sejam raras, queremos garantir que se mantém informado. A seguinte captura de ecrã mostra o tipo de e-mail que receberá se ativar as notificações:

![E-mail de notificação relativamente à atualização](media/service-interruption-notifications/refresh-notification-email.png)

De momento, enviamos e-mails relativos aos seguintes _cenários de fiabilidade_:

- Fiabilidade da abertura dos relatórios
- Fiabilidade das atualizações dos modelos
- Fiabilidade das atualizações das consultas

As notificações são enviadas quando houver um _atraso maior_ em operações, tais como: abertura de relatórios, atualização de conjuntos de dados ou execuções de consultas. Após a resolução de um incidente, receberá um e-mail de seguimento.

> [!NOTE]
> De momento, esta funcionalidade só está disponível para capacidades dedicadas no Power BI Premium. Não está disponível para capacidade partilhada ou incorporada.

## <a name="capacity-and-reliability-notifications"></a>Notificações de fiabilidade e capacidade

Quando uma capacidade do Power BI Premium tem longos períodos de alta utilização de recursos que afetam potencialmente a fiabilidade, é enviado um e-mail de notificação. Exemplos de tais impactos incluem atrasos alargados em operações como a abertura de um relatório, atualização do conjunto de dados e execuções de consultas. 

O e-mail de notificação fornece informações sobre o motivo da alta utilização de recursos, incluindo o seguinte:

* ID do conjunto de dados responsável
* Tipo de operação
* Tempo de CPU associado à alta utilização de recursos

O Power BI também envia notificações de e-mail quando é detetada uma sobrecarga na capacidade do Power BI Premium. O e-mail explica o motivo provável da sobrecarga, que operações geraram a carga nos 10 minutos anteriores e a quantidade de carga gerada por cada operação. 


Se tiver mais do que uma capacidade Premium, o e-mail incluirá informações sobre essas capacidades durante o período sobrecarregado, para que possa considerar mover áreas de trabalho que contenham itens com muitos recursos para capacidades com menor carga.

As notificações de e-mail de sobrecarga só são enviadas quando é acionado um limiar de sobrecarga. Não receberá um segundo e-mail quando a carga nessa capacidade Premium voltar a níveis não sobrecarregados.

A imagem seguinte mostra um e-mail de notificação de exemplo:

![e-mail de notificação de capacidade sobrecarregada](media/service-interruption-notifications/refresh-notification-email-2.png)


## <a name="enable-notifications"></a>Ativar notificações

Os administradores de inquilinos do Power BI têm de seguir os passos abaixo para ativar notificações no portal de administração.

1. Identifique ou crie o grupo de segurança com o e-mail ativado que deve receber notificações.

1. No portal de administração, selecione **Definições de inquilino**. Em **Definições de ajuda e suporte**, expanda **Receber notificações por e-mail se ocorrerem falhas ou incidentes de serviço**.

1. Ative as notificações, insira um grupo de segurança e selecione **Aplicar**.

    ![Ativar notificações de serviço](media/service-interruption-notifications/enable-notifications.png)

> [!NOTE]
> O Power BI envia notificações da conta no-reply-powerbi@microsoft.com. Certifique-se de que essa conta está na lista de permissões para que as notificações não acabem numa pasta de spamou de lixo.

## <a name="next-steps"></a>Próximos passos

[Opções de suporte para o Power BI Pro e Power BI Premium](service-support-options.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
