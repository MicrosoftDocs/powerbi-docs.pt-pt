---
title: Ligar ao Webtrends com o Power BI
description: Webtrends para o Power BI
services: powerbi
documentationcenter: ''
author: SarinaJoan
manager: kfile
backup: maggiesMSFT
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 9c8772430143b974fb389eac2f2ad3e74748fd3f
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="connect-to-webtrends-with-power-bi"></a>Ligar ao Webtrends com o Power BI
O pacote de conteúdos do Webtrends para o Power BI inclui uma variedade de métricas prontas a usar, como o total de visualizações e visitas de página por origem do tráfego. A visualização dos seus dados do Webtrends no Power BI começa com a ligação à sua conta do Webtrends. Pode usar o dashboard e os relatórios fornecidos, ou personalizá-los de modo a realçar as informações mais importantes para si.  Os dados serão atualizados automaticamente uma vez por dia.

Ligue-se ao [pacote de conteúdos do Webtrends para o Power BI](https://app.powerbi.com/getdata/services/webtrends).

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-webtrends/getdata3.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-webtrends/services.png)
3. Selecione **Webtrends** \> **Obter**.
   
   ![](media/service-connect-to-webtrends/webtrends.png)
4. O pacote de conteúdos liga-se a um ID de perfil específico do Webtrends. Veja detalhes sobre como [encontrar esse parâmetro](#FindingParams) abaixo.
   
   ![](media/service-connect-to-webtrends/parameters.png)
5. Forneça as suas credenciais do Webtrends para ligar. É importante observar que no campo do nome de utilizador é esperado que insira a sua conta e nome de utilizador. Veja os [detalhes](#FindingParams) abaixo.
   
   ![](media/service-connect-to-webtrends/creds.png)
6. Após a aprovação, o processo de importação será iniciado automaticamente. Quando concluído, um novo dashboard, relatório e modelo aparecerão no Painel de Navegação. Selecione o dashboard para ver os seus dados importados.
   
   ![](media/service-connect-to-webtrends/dashboard.png)

**O que se segue?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](power-bi-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento de atualização ou tentar atualizá-lo a pedido através de **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
<a name="Included"></a>

O pacote de conteúdos do Webtrends efetua pull de dados dos seguintes relatórios:  

| Nome do Relatório | ID do Relatório |
| --- | --- |
| Métrica-chave | |
| Pesquisas no Site |34awBVEP0P6 |
| Páginas de Saída |7FshY8eP0P6 |
| Páginas Seguintes |CTd5rpeP0P6 |
| Páginas Anteriores |aSdOeaUgnP6 |
| Páginas do site |oOEWQj3sUo6 |
| Clickthroughs de Anúncios no Site |41df19b6d9f |
| Cidades |aUuHskcP0P6 |
| Países |JHWXJNcP0P6 |
| Visitantes |xPcmTDDP0P6 |
| Duração da Visita |U5KAyqdP0P6 |
| Frases de Pesquisa |IKYEDxIP0P6 |
| Orugens de Tráfego |JmttAoIP0P6 |
| Motores de busca |yGz3gAGP0P6 |
| Páginas de Entrada |i6LrkNVRUo6 |

>[!NOTE]
>Para os perfis do SharePoint, os nomes de métrica podem ser um pouco diferentes do que é mostrado na IU do Webtrends. O seguinte mapeamento é feito para manter a consistência entre os perfis do SharePoint e da Web:   

    - Sessões = Visitas  
    - Novos Utilizadores = Novos Visitantes  
    - Vistas Por Sessão = Visualizações de Página por Visita  
    - Duração Média do Utilizador Diário = Tempo Médio no Site por Visitante  

## <a name="system-requirements"></a>Requisitos de sistema
O pacote de conteúdos requer acesso a um perfil do Webtrends com o [conjunto correto de relatórios](#Included) ativado.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Parâmetros de localização
O seu ID de perfil do Webtrends pode ser encontrado no URL depois de selecionar um perfil:

![](media/service-connect-to-webtrends/webtrendsparameters.png)

As credenciais são as mesmas que introduz ao entrar no Webtrends, no entanto, contamos que insira a sua conta e nome de utilizador na mesma linha, separados por uma barra invertida:

![](media/service-connect-to-webtrends/webtrendscreds.png)

## <a name="troubleshooting"></a>Resolução de problemas
Pode encontrar um problema durante o carregamento do pacote de conteúdos, depois de fornecer as credenciais. Se vir a mensagem “Oops” durante o carregamento, veja as sugestões de resolução de problemas abaixo. Se continuar a ter problemas, registe um pedido de suporte em https://support.powerbi.com

1. O ID de Perfil correto está a ser usado; consulte [Parâmetros de localização](#FindingParams) para mais detalhes.
2. O utilizador tem acesso aos relatórios listados na secção [“O que está incluído”](#Included)

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Power BI - Conceitos Básicos](service-basic-concepts.md)

