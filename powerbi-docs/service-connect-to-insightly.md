---
title: Ligar ao Insightly com o Power BI
description: Insightly para o Power BI
services: powerbi
documentationcenter: 
author: joeshoukry
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: yshoukry
ms.openlocfilehash: d506b45cf2a5c41ab1a6d05edb233c214606a316
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/19/2018
---
# <a name="connect-to-insightly-with-power-bi"></a>Ligar ao Insightly com o Power BI
Visualize e partilhe os seus dados de CRM do Insightly no Power BI com o pacote de conteúdos do Insightly. Ligue-se ao Power BI usando a sua chave de API do Insightly para visualizar e criar relatórios e dashboards a partir dos seus dados de CRM. Com o Power BI pode analisar os dados de novas maneiras, criar gráficos poderosos e exibir contactos, clientes potenciais e organizações num mapa.

Ligue-se ao [pacote de conteúdos do Insightly](https://app.powerbi.com/getdata/services/insightly) para o Power BI.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-insightly/getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-insightly/services.png)
3. Selecione **Insightly** \>  **Obter**.
   
   ![](media/service-connect-to-insightly/insightly.png)
4. Selecione **Chave** como o tipo de Autenticação e forneça a sua chave de API Insight. Em seguida, selecione **Iniciar Sessão**. Consulte os detalhes sobre como [encontrar este valor](#FindingParams) mais abaixo.
   
   ![](media/service-connect-to-insightly/creds.png)
5. Após a aprovação, o processo de importação será iniciado automaticamente. Quando concluído, um novo dashboard, relatório e modelo aparecerão no Painel de Navegação. Selecione o dashboard para ver os seus dados importados.
   
     ![](media/service-connect-to-insightly/dashboard.png)

**O que se segue?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](power-bi-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento de atualização ou tentar atualizá-lo a pedido através de **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
O pacote de conteúdos inclui as seguintes tabelas com campos dos registos correspondentes:

| Tabelas |  |  |  |
| --- | --- | --- | --- |
| Contactos |Oportunidades |Estágios de Pipeline |Data de Conclusão da Tarefa |
| Campos Personalizados |Data de Fecho da Oportunidade |Data de Conclusão do Projeto |Tarefas |
| Eventos |Data de Previsão da Oportunidade |Projetos |Equipas/Membros |
| Clientes potenciais |Organizações |Etiquetas |Utilizadores |

Muitas tabelas e relatórios também incluem campos calculados exclusivos, como:  

* Tabelas com datas previstas de fecho de oportunidades, datas reais de fecho de oportunidades, datas de conclusão de projetos e datas de conclusão de tarefas "agrupadas" para análise por mês, trimestre ou ano.  
* Um campo de valor ponderado para oportunidades (valor da oportunidade * probabilidade de ganho).  
* Campos de duração média e total das tarefas, com base nas datas de início e conclusão.  
* Relatórios com campos calculados para taxa de ganhos de oportunidade (número de ganhos/número de oportunidades totais) e valor da taxa de ganhos (valor de ganhos/valor de oportunidades totais).  

## <a name="system-requirements"></a>Requisitos de sistema
É necessária uma conta Insightly com acesso à API do Insightly. As permissões de visibilidade serão baseadas na chave de API usada para estabelecer a ligação com o Power BI. Quaisquer registos do Insightly visíveis para si também estarão visíveis nos relatórios e nos dashboards do Power BI que partilhar com outras pessoas.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Parâmetros de localização
**Chave de API**

Para copiar a chave de API do Insightly, selecione as Definições de Utilizador no menu do perfil do Insightly e desloque o ecrã para baixo. Esta cadeia de caracteres será usada para ligar os seus dados ao Power BI.

![](media/service-connect-to-insightly/findapi.png)

## <a name="troubleshooting"></a>Resolução de problemas
Os dados são importados através da API do Insightly, que inclui um limite diário com base no nível de plano da sua subscrição do Insightly. Os limites são listados na secção Pedidos de Limitação/Limitação de Velocidade da nossa documentação da API: https://api.insight.ly/v2.2/Help#!/Overview/Introduction#ratelimit

Os relatórios fornecidos usam campos predefinidos do Insightly e podem não incluir as suas personalizações. Edite o relatório para ver todos os campos disponíveis.

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Obter dados no Power BI](service-get-data.md)

