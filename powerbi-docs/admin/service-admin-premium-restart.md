---
title: Reiniciar uma capacidade do Power BI Premium
description: Saiba como pode reiniciar uma capacidade do Power BI Premium para resolver problemas de desempenho.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 03/12/2020
LocalizationGroup: Premium
ms.openlocfilehash: 0f237efece8403730ea7790d45bca6f5169e53fd
ms.sourcegitcommit: 51b965954377884bef7af16ef3031bf10323845f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/30/2020
ms.locfileid: "91599531"
---
# <a name="restart-a-power-bi-premium-capacity"></a>Reiniciar uma capacidade do Power BI Premium

Enquanto administrador do Power BI, poderá ter de reiniciar uma capacidade Premium. Este artigo explica como pode reiniciar uma capacidade e resolver várias questões de desempenho e reinício.

## <a name="why-does-power-bi-provide-this-option"></a>Porque é que o Power BI disponibiliza esta opção?

O Power BI oferece a possibilidade de os utilizadores realizarem análises complexas de grandes quantidades de dados. Infelizmente, os utilizadores podem provocar problemas de desempenho ao sobrecarregarem o serviço Power BI com tarefas, ao escreverem consultas demasiado complexas, ao criarem referências circulares, etc.

A capacidade partilhada do Power BI proporciona alguma proteção contra estes casos ao impor limites no tamanho dos ficheiros, agendamentos de atualizações, entre outros aspetos do serviço. Por outro lado, numa capacidade do Power BI Premium, a maior parte desses limites é gerada. Como resultado, um relatório com uma expressão DAX incorreta ou um modelo muito complexo pode causar problemas de desempenho significativos. No momento em que é processado, o relatório pode consumir todos os recursos disponíveis na capacidade. 

O Power BI esforça-se por melhorar continuamente a forma como protege os utilizadores da capacidade Premium contra esse tipo de problemas. Também estamos a disponibilizar ferramentas aos administradores que lhes permitem analisar quando e por que motivo as capacidades estão sobrecarregadas. Para obter mais informações, veja a nossa [sessão de formação curta](https://www.youtube.com/watch?v=UgsjMbhi_Bk&feature=youtu.be) e a nossa [sessão de formação mais extensa](https://powerbi.tips/2018/07/). Ao mesmo tempo, terá de conseguir mitigar problemas importantes no momento em que estes ocorrerem. A forma mais rápida de mitigar estes problemas é reiniciar a capacidade.

## <a name="is-the-restart-process-safe-will-i-lose-any-data"></a>O processo de reinício é seguro? Vou perder dados?

Todos os dados, definições, relatórios e dashboards na sua capacidade permanecerão totalmente intactos após reiniciá-la. Ao reiniciar uma capacidade, as atualizações agendadas e ad hoc em curso são, na maioria dos casos, temporariamente interrompidas pelo motor de atualização e, em seguida, são reiniciadas devido à lógica de repetição de atualização incorporada no Power BI. O serviço tenta efetuar novamente quaisquer atualizações afetadas assim que a capacidade ficar disponível. O estado das atualizações poderá não ser alterado na interface do utilizador durante o processo de reinício. 

Os utilizadores que interagirem com a capacidade vão perder o trabalho que não tiverem guardado durante um processo de reinício. É recomendável que estes atualizem os respetivos browsers quando o reinício estiver concluído.

## <a name="how-do-i-restart-a-capacity"></a>Como posso reiniciar uma capacidade?

Siga estes passos para reiniciar uma capacidade.

1. No portal de administração do Power BI, no separador **Definições de Capacidade**, navegue até à capacidade. 

1. Adicione o **sinalizador de funcionalidade** *CapacityRestart* ao URL da capacidade: `https://app.powerbi.com/admin-portal/capacities/<YourCapacityId>?capacityRestartButton=true`.

1. Em **Definições Avançadas** > **REINÍCIO DA CAPACIDADE**, selecione **Reiniciar capacidade**.

    ![Reiniciar capacidade](media/service-admin-premium-restart/restart-capacity.png)

1. Na caixa de diálogo **Reinício da capacidade**, selecione **Sim, reiniciar capacidade**.

    ![Confirmar o reinício](media/service-admin-premium-restart/confirm-restart.png)

## <a name="how-can-i-prevent-issues-from-happening-in-the-future"></a>Como posso evitar a ocorrência de futuros problemas?

A melhor forma de evitar problemas passa por instruir os utilizadores sobre como modelar dados de forma eficiente. Para obter mais informações, veja a nossa [sessão de formação](https://powerbi.tips/2018/07/).

Também recomendamos que [monitorize as suas capacidades](service-admin-premium-monitor-capacity.md) regularmente para detetar tendências que indiquem problemas subjacentes. Planeamos o lançamento regular de versões da aplicação de monitorização e de outras ferramentas, para que possa monitorizar e gerir as suas capacidades com maior eficácia.

## <a name="next-steps"></a>Próximas etapas

[O que é o Power BI Premium?](service-premium-what-is.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
