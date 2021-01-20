---
title: Criar uma ligação para uma localização específica nas aplicações móveis do Power BI
description: Saiba como criar uma ligação avançada para um dashboard, mosaico ou relatório específico na aplicação móvel do Power BI com um identificador de recurso uniforme (URI).
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 11/16/2020
ms.openlocfilehash: 8c5b3c394d54df390d690d58b56e9084f9829733
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565669"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>Criar uma ligação para uma localização específica nas aplicações móveis do Power BI
Pode utilizar ligações para aceder diretamente a conteúdos específicos do Power BI, como um relatório, página de relatório, dashboard, mosaico, entre outros.

Existem dois cenários principais de utilização de ligações para aceder a conteúdos nas aplicações móveis do Power BI: 

* Abrir o Power BI **fora da aplicação móvel** e aceder diretamente a conteúdos específicos. Este é normalmente um cenário de integração, no qual abre a aplicação móvel do Power BI a partir de outra aplicação. 
* Para **navegar** dentro do Power BI. Este procedimento é geralmente seguido quando quer criar uma navegação personalizada no Power BI.

Este artigo abrange os seguintes casos:
* Utilizar ligações para abrir conteúdos específicos do Power BI fora da aplicação móvel. São descritos dois formatos de ligação. Um formato tira partido de um método de redirecionamento e pode ser utilizado independentemente do local onde o Power BI for aberto. O outro formato é aberto diretamente na aplicação móvel do Power BI e funciona apenas em dispositivos móveis que tenham a aplicação móvel instalada.
* Utilizar ligações dentro do Power BI para aceder a conteúdos específicos do Power BI.

## <a name="use-links-from-outside-the-mobile-app"></a>Utilizar ligações fora da aplicação móvel
Existem duas opções para criar uma ligação para um item específico no Power BI a partir de fora da aplicação móvel, dependendo do local onde a ligação será aberta:

* Pode criar uma ligação que seja aberta de forma correta, independentemente do local onde for clicada num browser de um computador ou num dispositivo móvel. Esta ligação tem uma sintaxe de redirecionamento especial para permitir este comportamento inteligente.

* Se souber que a ligação só será aberta num dispositivo móvel que tenha a aplicação móvel do Power BI instalada, pode evitar a sobrecarga de redirecionamento do método acima e utilizar outra sintaxe de ligação que abra a ligação diretamente na aplicação móvel do Power BI no dispositivo móvel. No entanto, é importante ter em conta que, apesar de esta ligação evitar a sobrecarga de redirecionamento do primeiro método, apenas funcionará em dispositivos móveis que tenham a aplicação móvel do Power BI instalada.

### <a name="create-a-link-that-works-anywhere"></a>Criar uma ligação que funcione em qualquer local
O formato de ligação descrito nesta secção utiliza o redirecionamento para garantir que a ligação funciona independentemente do local onde for clicada.
* Se a ligação for clicada num dispositivo móvel, garante que o dispositivo utiliza a aplicação móvel do Power BI para abri-la. Se a aplicação móvel não estiver instalada no dispositivo, sugere que o utilizador aceda à loja para a obter.
* Se a ligação for clicada num PC, irá abrir o item relevante no portal Web do Power BI.

A ligação tem de começar com um prefixo especial, seguido de parâmetros de consulta:

https<nolink>://app.powerbi.com/Redirect? **[PARAMETROSDECONSULTA]** </code>

> [!IMPORTANT]
> Se os conteúdos estiverem alojados num datacenter especial, como na Administração Pública, China, entre outros, a ligação deve começar com o endereço do Power BI adequado, tal como **app.powerbigov.us** ou **app.powerbi.cn**.

Eis os parâmetros de consulta:

|Parâmetro  | Valor  | Descrição |
|---------|---------|---------|
|**action** (obrigatório)    | OpenApp<br>OpenReport<br>OpenDashboard<br>OpenTile | |
|**appId**| GUID de 36 carateres | Tem de ser especificado se quiser abrir um relatório ou dashboard que faça parte de uma aplicação.<br>Exemplo: **appId=baf4b16d-b5bd-4360-8a3a-51d11242c09b** |
|**groupObjectId**| GUID de 36 carateres | Especifica a área de trabalho quando quer abrir um relatório ou dashboard que não faça parte de A Minha Área de Trabalho.<br>Exemplo: **groupObjectId=9a3841c6-74b3-46f1-85fd-bdd78f27b30e** |
| **dashboardObjectId** | GUID de 36 carateres | ID de objeto do dashboard (se a ação for OpenDashboard ou OpenTile)<br>Exemplo: **dashboardObjectId=033bb049-5b68-4392-b3ef-ae9a43738a4a** |
| **reportObjectId** | GUID de 36 carateres | ID de objeto do relatório (se a ação for OpenReport)<br>Exemplo: **reportObjectId=6114cec7-78e1-4926-88ff-0bc5338452cf** |
| **tileObjectId** | GUID de 36 carateres | ID de objeto do mosaico (se a ação for OpenTile)<br>Exemplo: **tileObjectId=a845dcb8-a289-43a8-94ea-67a8c0a068f9** |
| **reportPage** | ReportSection&lt;num&gt; | Nome da página se quiser abrir uma página de relatório específica (se a ação for OpenReport)<br>Exemplo: **reportPage=ReportSection6**  |
| **bookmarkGuid** | GUID de 36 carateres | ID de marcador, se quiser abrir uma vista específica que tenha sido adicionada aos marcadores (se a ação for OpenReport)<br>Exemplo: **bookmarkGuid=18e8872f-6db8-4cf8-8298-3b2ab254cc7f** |
| **ctid** | GUID de 36 carateres | ID da organização do item (relevante para cenários B2B. Pode ser omitido se o item pertencer à organização do utilizador)<br>Exemplo: **ctid=5367c770-09d0-4110-bf6a-d760cb5ef681** . |
||||

**Exemplos:**

Nos seguintes exemplos, os marcadores de posição dos valores de parâmetros estão realçados a negrito. Para obter os valores reais, aceda ao serviço Power BI, abra o item para o qual quer criar uma ligação e extraia os valores necessários do URL do item.

* **Abrir uma aplicação**

    https<nolink>://app.powerbi.com/Redirect?action=OpenApp&appId= **&lt;appid-guid&gt;** &ctid= **&lt;ctid-guid&gt;**
   
* **Abrir um dashboard que faz parte de uma aplicação**

    https<nolink>://app.powerbi.com/Redirect?action=OpenDashboard&appId= **&lt;appid-guid&gt;** &dashboardObjectId= **&lt;dashboardid-guid&gt;** &ctid= **&lt;ctid-guid&gt;**

* **Abrir um relatório que faça parte de uma área de trabalho que não seja A Minha Área de Trabalho**

    https<nolink>://app.powerbi.com/Redirect?Action=OpenReport&reportObjectId= **&lt;reportid-guid&gt;** &groupObjectId= **&lt;groupobjectid-guid&gt;** &reportPage=**ReportSection&lt;num&gt;**

### <a name="how-to-get-the-correct-link-format"></a>Como obter o formato de ligação correto

#### <a name="links-to-apps-and-items-in-apps"></a>Ligações para aplicações e itens em aplicações

Para **aplicações, relatórios e dashboards que fazem parte de uma aplicação**, a forma mais fácil de obter a ligação é aceder à área de trabalho da aplicação e selecionar **Atualizar aplicação**. Esta ação abre a experiência de publicação de aplicações. Abra o separador de permissões e expanda a secção de ligações para ver as ligações para a aplicação e todos os respetivos conteúdos. Pode utilizar estas ligações fora do Power BI para aceder diretamente à aplicação e aos respetivos conteúdos.

![Ligações de Publicar aplicação do Power BI ](./media/mobile-apps-links/mobile-link-copy-app-links.png)

#### <a name="links-to-items-that-are-not-in-an-app"></a>Ligações para itens que não estão numa aplicação 

Para relatórios e dashboards que não fazem parte de uma aplicação, tem de extrair os IDs de objeto necessários do URL do item. Para fazê-lo, aceda ao serviço Power BI, navegue para o item para o qual quer criar uma ligação e procure os valores necessários no URL que vê na barra de endereço do browser.

Os exemplos abaixo mostram onde pode encontrar os IDs necessários nos URLs dos itens para os quais quer criar ligações.

* Para encontrar um ID de objeto do dashboard de 36 carateres navegue para o dashboard específico para o qual quer criar uma ligação no serviço Power BI e procure o ID de objeto do dashboard e os restantes IDs necessários nos locais indicados abaixo:

    https<nolink>://app.powerbi.com/groups/me/dashboards/ **&lt;dashboard-object-id&gt;** ?ctid= **&lt;org-object-id&gt;**

* Para encontrar um ID de objeto do relatório de 36 carateres, navegue para o relatório específico para o qual quer criar uma ligação no serviço Power BI e procure os IDs necessários, como mostramos abaixo. Tenha em atenção que este exemplo contém uma referência a uma página de relatório específica e um marcador específico.

    https<nolink>://app.powerbi.com/groups/me/reports/ **&lt;report-object-id&gt;** /**ReportSection&lt;num&gt;** ?bookmarkGuid= **&lt;bookmark-id&gt;**

* Para criar uma ligação para um item numa área de trabalho que não seja A Minha Área de Trabalho, tem de extrair o ID de objeto do grupo. Este exemplo mostra um relatório de uma área de trabalho que não é A Minha Área de Trabalho.

    https<nolink>://app.powerbi.com/groups/ **&lt;group-object-id&gt;** /reports/ **&lt;report-object-id&gt;** /**ReportSection&lt;report-section-num&gt;** ?ctid= **&lt;org-object-id&gt;**

### <a name="create-a-link-that-opens-only-on-a-device-that-has-the-power-bi-mobile-app-installed"></a>Criar uma ligação que seja aberta apenas num dispositivo que tenha a aplicação móvel do Power BI instalada

O formato de ligação descrito nesta secção liga a uma localização específica nas aplicações móveis do Power BI em todas as plataformas móveis: iOS, Android e Windows 10. Este formato de ligação abre diretamente a localização, sem o redirecionamento envolvido no método descrito na secção anterior. **Este formato só pode ser aberto em dispositivos móveis que tenham a aplicação móvel Power BI instalada**.

As ligações deste formato podem apontar diretamente para dashboards, mosaicos e relatórios. O destino da ligação avançada determina o respetivo formato. Siga estes passos para criar ligações avançadas para localizações diferentes. 

* **Abra a aplicação móvel do Power BI**

    Utilize esta ligação para abrir a aplicação móvel do Power BI em qualquer dispositivo:

    mspbi://app/

* **Abrir num dashboard específico**

    Esta ligação abre a aplicação móvel do Power BI num dashboard específico:

    mspbi://app/OpenDashboard?DashboardObjectId= **<id-do-dashboard-de-36-carateres>**

    Para obter o ID de objeto do dashboard de 36 carateres, navegue para o dashboard específico no serviço Power BI e extraia-o do URL. Por exemplo, o ID de objeto do dashboard está realçado no seguinte URL do serviço Power BI:

    https<nolink>://app.powerbi.com/groups/me/dashboards/ **&lt;61b7e871-cb98-48ed-bddc-6572c921e270&gt;**

    Se o dashboard não estiver em A Minha Área de Trabalho, também terá de adicionar o ID de objeto do grupo antes ou depois do ID do dashboard. A ligação avançada mostrada abaixo tem o parâmetro de ID de objeto do grupo adicionado depois do ID de objeto do dashboard:

    mspbi://app/OpenDashboard?DashboardObjectId=**e684af3a-9e7f-44ee-b679-b9a1c59b5d60**&GroupObjectId=**8cc900cc-7339-467f-8900-fec82d748248**</code>

    Repare na existência de um "E" comercial (&) entre os dois parâmetros.

* **Abrir com um mosaico específico em foco**

    Esta ligação abre um mosaico específico no modo de detalhe na aplicação móvel do Power BI:

    mspbi://app/OpenTile?DashboardObjectId= **<36-character-dashboard-id>** &TileObjectId= **<36-character-tile-id>**

    Para encontrar os IDs de objeto de mosaico e dashboard de 36 carateres navegue para o dashboard específico no serviço Power BI e abra o mosaico no modo de detalhe. No exemplo abaixo, os IDs de mosaico e dashboard estão realçados.

    https<nolink>://app.powerbi.com/groups/me/dashboards/**3784f99f-b460-4d5e-b86c-b6d8f7ec54b7**/tiles/**565f9740-5131-4648-87f2-f79c4cf9c5f5**/infocus

    Para abrir este ficheiro diretamente, a ligação seria:

    mspbi://app/OpenTile?DashboardObjectId=3784f99f-b460-4d5e-b86c-b6d8f7ec54b7&TileObjectId=565f9740-5131-4648-87f2-f79c4cf9c5f5

    Repare na existência de um "E" comercial (&) entre os dois parâmetros.

    Se o dashboard não estiver em A Minha Área de Trabalho, adicione o parâmetro GroupObjectId. Por exemplo: &GroupObjectId=<36-character-group-id>

* **Abrir num relatório específico**

    Esta ligação abre um relatório específico na aplicação móvel do Power BI:

    mspbi://app/OpenReport?ReportObjectId= **<id-do-relatorio-de-36-carateres>**

    Para encontrar o ID de objeto do relatório de 36 carateres, navegue para o relatório específico no serviço Power BI. O seguinte URL do serviço Power BI mostra o ID de relatório que precisa de extrair.

    https<nolink>://app.powerbi.com/groups/me/reports/**df9f0e94-31df-450b-b97f-4461a7e4d300**

    Se o relatório não estiver em A Minha Área de Trabalho, também terá de adicionar **&GroupObjectId=<id-do-grupo-de-36-carateres>** antes ou depois do ID de relatório. Por exemplo, neste caso a ligação avançada seria:

    mspbi://app/OpenReport?ReportObjectId=**e684af3a-9e7f-44ee-b679-b9a1c59b5d60**&GroupObjectId=**8cc900cc-7339-467f-8900-fec82d748248**

    Repare na existência de um "E" comercial (&) entre os dois parâmetros.

* **Abrir uma página de relatório específica**

    Esta ligação abre uma página de relatório específica na aplicação móvel do Power BI:

    mspbi://app/OpenReport?ReportObjectId= **<id-do-relatorio-de-36-carateres>** &reportPage=**ReportSection&lt;number&gt;**

    A página de relatório tem o nome **ReportSection**, seguido de um número. Relembramos que, para encontrar os valores necessários, tem de abrir o relatório no serviço Power BI, navegar para a página de relatório específica e extrair os valores necessários do URL. Por exemplo, as secções realçadas deste URL representam os valores de que precisa para abrir uma página de relatório específica:

    https<nolink>://app.powerbi.com/groups/me/reports/**df9f0e94-31df-450b-b97f-4461a7e4d300**/**ReportSection11**</code>

* **Abrir no modo de ecrã inteiro (apenas para dispositivos Windows)**

    Em dispositivos Windows, também pode adicionar o parâmetro **openFullScreen** para abrir um relatório específico no modo de ecrã inteiro. O exemplo seguinte abre uma página de relatório no modo de ecrã inteiro:

    mspbi://app/OpenReport?ReportObjectId=500217de-50f0-4af1-b345-b81027224033&**openFullScreen=true**

* **Adicionar contexto** (opcional)

    Também pode adicionar contexto à cadeia. Depois, se precisar de nos contactar, poderemos utilizar esse contexto para filtrar os nossos dados de modo a encontrar o que é relevante para a sua aplicação. Para adicionar contexto, adicione o parâmetro **context=&lt;app-name&gt;** à ligação:

    Por exemplo, o exemplo seguinte mostra uma ligação que inclui um parâmetro de contexto: 

    mspbi://app/OpenReport?ReportObjectId=**e684af3a-9e7f-44ee-b679-b9a1c59b5d60**&GroupObjectId=**8cc900cc-7339-467f-8900-fec82d748248**&**context=SlackDeepLink**

## <a name="use-links-inside-power-bi"></a>Utilizar ligações dentro do Power BI

Nas aplicações móveis do Power BI, as ligações dentro do Power BI funcionam da mesma forma que no serviço Power BI.

Se quiser adicionar uma ligação ao seu relatório que aponte para outro item do Power BI, basta copiar o URL desse item da barra de endereço do browser. Saiba mais sobre [como adicionar uma hiperligação a uma caixa de texto num relatório](../../create-reports/service-add-hyperlink-to-text-box.md).

## <a name="next-steps"></a>Passos seguintes
Os seus comentários ajudam-nos a decidir o que implementar no futuro, portanto, não se esqueça de votar noutros recursos que gostaria de ver nas aplicações móveis do Power BI. 

* [Power BI apps for mobile devices (Aplicações do Power BI para dispositivos móveis)](mobile-apps-for-mobile-devices.md)
* Siga o @MSPowerBI no Twitter
* Participe na conversa na [Comunidade do Power BI](http://community.powerbi.com/)
* [O que é o Power BI?](../../fundamentals/power-bi-overview.md)