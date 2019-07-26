---
title: Diretrizes para implementar um gateway de dados para o Power BI
description: Conheça as melhores práticas e considerações para implementar um gateway para o Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 4351804330982b32582c4c782ef7c2fa0e92f197
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271709"
---
# <a name="guidance-for-deploying-a-data-gateway-for-power-bi"></a>Diretrizes para implementar um gateway de dados para o Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Este artigo fornece orientações e considerações para implementar um gateway de dados para o Power BI no seu ambiente de rede.

Para obter informações sobre como transferir, instalar, configurar e gerir o gateway de dados no local, veja [What is an on-premises data gateway?](/data-integration/gateway/service-gateway-onprem) (O que é um gateway de dados no local?). Também pode saber mais sobre o gateway de dados no local e sobre o Power BI ao aceder ao [Blogue do Microsoft Power BI](https://powerbi.microsoft.com/blog/) e ao site da [Comunidade do Microsoft Power BI](https://community.powerbi.com/).

## <a name="installation-considerations-for-the-on-premises-data-gateway"></a>Considerações sobre a instalação do gateway de dados no local

Antes de instalar o gateway de dados no local para o seu serviço cloud do Power BI, existem algumas considerações que deve ter em atenção. As seguintes secções descrevem essas considerações.

### <a name="number-of-users"></a>Número de utilizadores

O número de utilizadores que utilizam um relatório que execute o gateway é uma métrica importante para decidir o local de instalação do gateway. Eis algumas questões a considerar:

* Os utilizadores estão a utilizar estes relatórios em períodos diferentes do dia?
* Que tipos de ligações estão a utilizar (DirectQuery ou Importar)?
* Todos os utilizadores utilizam o mesmo relatório?

Se todos os utilizadores estiverem a aceder em simultâneo a um determinado relatório todos os dias, é aconselhável instalar o gateway num computador que seja capaz de processar todos esses pedidos (veja as seguintes secções sobre contadores de desempenho e sobre os requisitos mínimos que podem ajudá-lo a determinar isto).

Há uma restrição no **Power BI** que permite apenas *um* gateway por *relatório*, por isso, mesmo que um relatório se baseie em várias origens de dados, todas estas origens de dados devem passar por um único gateway. No entanto, se um dashboard se basear em *vários* relatórios, pode utilizar um gateway dedicado para cada relatório e, deste modo, distribuir a carga de gateway entre os vários relatórios que contribuem para esse dashboard individual.

### <a name="connection-type"></a>Tipo de ligação

O **Power BI** oferece dois tipos de ligações: **DirectQuery** e **Importação**. Nem todas as origens de dados suportam os dois tipos de ligação e muitos motivos podem contribuir para escolher um em detrimento de outros, tais como requisitos de segurança, desempenho, limites de dados e tamanhos de modelos de dados. Pode saber mais sobre os tipos de ligações e as origens de dados suportadas na [lista de tipos de origens de dados disponíveis](service-gateway-data-sources.md#list-of-available-data-source-types).

A utilização do gateway pode variar consoante o tipo de ligação utilizada. Por exemplo, deve utilizar origens de dados **DirectQuery** diferentes das origens de dados **Atualização Agendada** sempre que possível (partindo do princípio de que estão em relatórios diferentes e podem ser separadas). Deste modo, impede que o gateway tenha milhares de pedidos DirectQuery em fila, ao mesmo tempo que a atualização agendada da manhã de um modelo de dados de grande dimensão utilizado para o dashboard principal da empresa. Eis o que considerar para cada:

* Para **Atualização Agendada**: consoante o tamanho da consulta e o número de atualizações que ocorrem por dia, pode optar por manter os requisitos mínimos de hardware recomendados ou atualizar para um computador de desempenho superior. Se uma determinada consulta não for integrada, as transformações ocorrem no computador do gateway e, como tal, o computador do gateway beneficia de um maior número de RAM disponível.

* Para o **DirectQuery**: deve ser enviada uma consulta sempre que qualquer utilizador abrir o relatório ou analisar os dados. Por isso, se prever que um número superior a 1000 utilizadores vai aceder os dados em simultâneo, pode ser útil certificar-se de que o seu computador em componentes de hardware robustas e capazes. Um maior número de núcleos de CPU irá resultar num melhor débito de uma ligação **DirectQuery**.

Os requisitos para um computador no qual efetua a instalação podem ser encontrados nos [requisitos de instalação](/data-integration/gateway/service-gateway-install#requirements) do gateway de dados no local.

### <a name="location"></a>Localização

A localização da instalação do gateway pode ter impacto considerável no desempenho da sua consulta, por isso, tente certificar-se de que o gateway, as localizações da origem de dados e o inquilino do Power BI estão o mais próximo possível entre si para minimizar a latência de rede. Para determinar a localização de inquilino do Power BI, no serviço Power BI, selecione o ícone **?** no canto superior direito e, em seguida, selecione **Sobre o Power BI**.

![Determinar a localização do inquilino do Power BI](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_02.png)

Além disso, se tenciona utilizar o gateway do Power BI com o Azure Analysis Services, certifique-se de que as regiões de dados em ambos correspondem. Para obter mais informações sobre como definir regiões de dados para múltiplos serviços, veja [este vídeo](https://guyinacube.com/2018/01/power-bi-azure-analysis-services-gateway-data-region/).

## <a name="next-steps"></a>Próximos passos

* [Configurar definições de proxy](/data-integration/gateway/service-gateway-proxy)  
* [Resolver problemas de gateways – Power BI](service-gateway-onprem-tshoot.md)  
* [FAQ do gateway de dados no local – Power BI](service-gateway-power-bi-faq.md)  

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

