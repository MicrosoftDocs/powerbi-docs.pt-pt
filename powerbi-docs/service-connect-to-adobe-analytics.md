---
title: Ligar ao Adobe Analytics com o Power BI
description: Ligue ao Adobe Analytics a partir do Power BI para uma aplicação que apresenta os dados da sua conta num dashboard e relatórios.
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: bcd92dc0288fc347c5f5931d40b94cf769f5293f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61180340"
---
# <a name="connect-to-adobe-analytics-with-power-bi"></a>Ligar ao Adobe Analytics com o Power BI
A ligação ao Adobe Analytics através do Power BI começa pela ligação à sua conta do Adobe Analytics Marketing Cloud. Obtém uma aplicação com um dashboard e um conjunto de relatórios do Power BI que fornecem informações sobre as dimensões de tráfego e utilizadores do seu site. Os dados são atualizados automaticamente uma vez por dia. Pode interagir com o dashboard e os relatórios, mas não pode guardar as alterações.

Ligue ao [Adobe Analytics](https://app.powerbi.com/getdata/services/adobe-analytics) ou leia mais sobre a [integração do Adobe Analytics](https://powerbi.microsoft.com/integrations/adobe-analytics) com o Power BI.

## <a name="how-to-connect"></a>Como se ligar
[!INCLUDE [powerbi-service-apps-get-more-apps](./includes/powerbi-service-apps-get-more-apps.md)]

3. Selecione **Adobe Analytics** \> **Ligar**.
   
   ![](media/service-connect-to-adobe-analytics/adobe.png)
4. O Power BI liga a um ID do Pacote de Relatórios ou Empresa específico do Adobe Analytics (não ao nome do Pacote de Relatórios). Veja detalhes sobre como [encontrar esses parâmetros](#FindingParams) abaixo.
   
   ![](media/service-connect-to-adobe-analytics/parameters.png)
5. Para **Método de Autenticação**, selecione **oAuth2** \> **Iniciar Sessão**. Quando pedido, insira as suas credenciais do Adobe Analytics. 
   
    ![](media/service-connect-to-adobe-analytics/creds.png)
   
    ![](media/service-connect-to-adobe-analytics/adobe_signin.png)
6. Clique em **Aceitar** para permitir que o Power BI aceda aos dados do Adobe Analytics.
   
   ![](media/service-connect-to-adobe-analytics/adobe_authorize.png)
7. Após a aprovação, o processo de importação é iniciado automaticamente. 

## <a name="view-the-adobe-analytics-dashboard-and-reports"></a>Ver o dashboard e os relatórios do Adobe Analytics
[!INCLUDE [powerbi-service-apps-open-app](./includes/powerbi-service-apps-open-app.md)]

   ![Dashboard do Adobe Analytics](media/service-connect-to-adobe-analytics/dashboard.png)

[!INCLUDE [powerbi-service-apps-open-app](./includes/powerbi-service-apps-what-now.md)]

## <a name="whats-included"></a>O que está incluído
O Power BI utiliza a API de Relatório do Adobe Analytics para definir e executar relatórios para as seguintes tabelas:

| **Nome da Tabela** | **Detalhes da Coluna** |
| --- | --- |
| Produtos |elementos = "product" (os 25 primeiros) <br> métricas= "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units" |
| Navegadores |elementos= "browser" (os 25 primeiros)<br>  métricas= "bounces", "bouncerate", "visitors", "visits", "uniquevisitors", "totaltimespent", "pageviews" |
| Páginas |elementos= "page" (as 25 primeiras)<br>  métricas= "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units", "visits", "uniquevisitors", "pageviews", "bounces", "bouncerate", "totaltimespent" |
| JavaScript Ativado |elementos= "javascriptenabled”, “browser” (os 25 primeiros) |
| SO Móvel |elementos= "mobileos" (os 25 primeiros)<br> métricas= "bounces", "bouncerate", "visitors", "visits", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "checkouts", "revenue", "units", "pageviews" |
| Palavras-chave de Mecanismos de Pesquisa |elementos= "searchengine" "searchenginekeyword"<br>  métricas= "bounces", "bouncerate", "visitors", "visits", "entries", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units", "pageviews" |
| Mecanismo de Pesquisa para Produtos |elementos= "searchengine", "product"<br>  métricas= "bounces", "bouncerate", "visitors", "visits", "entries", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units", "pageviews" |
| Páginas de Referência |elementos= "referrer" (os 15 primeiros), "page" (as 10 primeiras)<br>  métricas= "bounces", "bouncerate", "visitors", "visits", "entries", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units", "pageviews" |
| Páginas de Geocountry |elementos= "geocountry" (os 20 primeiros), "page"<br>  métricas= "bounces", "bouncerate", "visitors", "visits", "entries", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units", "pageviews" |
| Produto de Geocountry |elementos= "geocountry" (os 20 primeiros), "product"<br> métricas= "bounces", "bouncerate", "visitors", "visits", "entries", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units" |
| Pesquisa de Região e País |elementos = "geocountry" (os 200 primeiros)<br>  métricas= "bounces", "bouncerate", "visitors", "visits", "entries", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units" |
| Idioma |elementos= "language", "browser" (os 25 primeiros)<br>  métricas= "bounces", "bouncerate", "visitors", "visits", "uniquevisitors", "totaltimespent", "pageviews", "cartadditions", "cartremovals", "checkouts", "carts", "cartviews" |
| Pesquisa de mecanismos de pesquisa |elementos= "searchengine" (os 100 primeiros)<br>  métricas= "bounces", "bouncerate", "visitors", "visits", "entries", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units" |
| Pesquisa de navegador |elementos= "browser" (os 25 primeiros) |

## <a name="system-requirements"></a>Requisitos de sistema
Tem de ter acesso ao [Adobe Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), incluindo o acesso aos parâmetros corretos, conforme descrito abaixo.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Encontrar parâmetros
**Empresa**

O valor de Empresa pode ser encontrado no canto superior direito da sua conta quando tiver sessão iniciada. O valor é sensível às maiúsculas e minúsculas e ao espaçamento. Introduza-o exatamente como o vê na sua conta.

![](media/service-connect-to-adobe-analytics/adobe_companies.png)

**ID do Pacote de Relatórios**

O ID do Pacote é criado quando o Pacote de Relatórios é criado. Entre em contacto com o administrador para identificar o valor de ID. Este não é o nome do Pacote de Relatórios.

Da [documentação](https://marketing.adobe.com/resources/help/en_US/reference/new_report_suite.html) do Adobe:

![](media/service-connect-to-adobe-analytics/reportsuiteid.png)

## <a name="troubleshooting"></a>Resolução de problemas
Se estiver a ver um erro depois de fornecer as suas credenciais a indicar que não tem permissões, confirme junto do seu administrador se tem acesso à API do Adobe Analytics. Além disso, confirme se o ID do Adobe fornecido está vinculado à sua Organização de Marketing da Cloud (associada a uma empresa do Adobe Analytics).

Se tiver acedido ao ecrã de credenciais antes de receber um erro, é possível que os relatórios estejam a demorar demasiado tempo a concluir. Um erro comum é o formato *"Falha ao obter dados do relatório Adobe Analytics. Conteúdo incluído &quot;referência, página&quot;, duração aproximada de xx segundos"* . Consulte a secção "O que está incluído" e compare com o tamanho da sua instância do Adobe. Lamentamos, mas não existe uma forma de contornar este tempo limite atualmente. No entanto, estamos a considerar atualizações para melhorar o suporte de instâncias de maiores dimensões. Forneça os seus comentários à equipa do Power BI em https://ideas.powerbi.com

## <a name="next-steps"></a>Próximos passos
* [O que são aplicações no Power BI?](service-create-distribute-apps.md)
* [Obter dados no Power BI](service-get-data.md)
* Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

