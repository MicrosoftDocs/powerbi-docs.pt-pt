---
title: "Atualizar um conjunto de dados criado por meio de um ficheiro .csv (valor separado por vírgulas) no OneDrive"
description: "Atualizar um conjunto de dados criado por meio de um ficheiro .csv (valor separado por vírgulas) no OneDrive"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: 214f78c86a43341d177d72f60a2a5ecce4d8f8d5
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2017
---
# <a name="refresh-a-dataset-created-from-a-csv-file-on-onedrive-or-sharepoint-online"></a>Atualizar um conjunto de dados criado com base num ficheiro .CSV no OneDrive ou SharePoint Online
## <a name="what-are-the-advantages"></a>Quais são as vantagens?
Quando se liga a um ficheiro .csv no OneDrive ou SharePoint Online, é criado um conjunto de dados no Power BI. Os dados do ficheiro .csv são então importados para o conjunto de dados no Power BI. Em seguida, o Power BI se conecta automaticamente ao ficheiro e atualiza todas as alterações com o conjunto de dados no Power BI. Se editar o ficheiro .csv no OneDrive ou SharePoint Online, depois de salvar, essas alterações aparecem no Power BI, normalmente, em menos de uma hora. Todas as visualizações no Power BI baseadas no conjunto de dados também são atualizadas automaticamente.

Se os ficheiros estiverem numa pasta partilhada no OneDrive for Business ou SharePoint Online, outros utilizadores podem trabalhar no mesmo ficheiro. Depois de salvas, quaisquer alterações feitas são atualizadas automaticamente no Power BI, geralmente numa hora.

Muitas organizações realizam processos que consultam automaticamente nas bases de dados os dados que são então guardados diariamente num ficheiro .csv. Se o ficheiro estiver armazenado no OneDrive ou SharePoint Online e o mesmo ficheiro for substituído todos os dias, em vez de criar um novo ficheiro com um nome diferente todos os dias, será possível se conectar a esse ficheiro no Power BI. O conjunto de dados que se conecta ao ficheiro será sincronizado logo depois que o ficheiro no OneDrive ou SharePoint Online for atualizado. Todas as visualizações com base no conjunto de dados também são atualizadas automaticamente.

## <a name="whats-supported"></a>O que é suportado?
Os ficheiros de valores separados por vírgulas são ficheiros de texto simples; portanto, não há suporte para conexões a relatórios e origens de dados externas. Não é possível agendar uma atualização num conjunto de dados criado por meio de um ficheiro delimitado por vírgulas. No entanto, quando o ficheiro estiver no OneDrive ou SharePoint Online, o Power BI sincronizará todas as alterações no ficheiro com o conjunto de dados automaticamente em intervalos aproximados de sessenta minutos.

## <a name="onedrive-or-onedrive-for-business-whats-the-difference"></a>OneDrive ou OneDrive para Empresas. Qual é a diferença?
Se tiver um OneDrive Pessoal e um OneDrive para Empresas, é recomendável manter todos os ficheiros aos quais deseja se conectar no Power BI no OneDrive para Empresas. Eis o porquê: provavelmente utiliza duas contas diferentes para entrar neles.

A ligação ao OneDrive para Empresas no Power BI é normalmente contínua, porque a mesma conta com a qual utiliza para entrar no Power BI é geralmente a mesma conta utilizada para entrar no OneDrive para Empresas. Mas, com o OneDrive pessoal, provavelmente entra com outra [conta da Microsoft](http://www.microsoft.com/account/default.aspx).

Quando iniciar a sessão com a sua conta Microsoft, certifique-se de seleciona Mantenha-me conectado. Em seguida, o Power BI pode sincronizar as atualizações com conjuntos de dados no Power BI

![](media/refresh-csv-file-onedrive/refresh_signin_keepmesignedin.png)

Se fizer alterações no ficheiro .csv no OneDrive que não podem ser sincronizadas com o conjunto de dados no Power BI devido à possibilidade de as suas credenciais de conta da Microsoft terem sido alteradas, precisará de se ligar ao ficheiro e importá-lo novamente do seu OneDrive pessoal.

## <a name="when-things-go-wrong"></a>Quando algo dá errado
Se os dados no ficheiro .csv no OneDrive forem alterados e essas alterações não forem refletidas no Power BI, isso ocorre provavelmente porque o Power BI não pode se conectar ao OneDrive. Tente se conectar ao ficheiro e importá-lo novamente. Se for solicitado a iniciar a sessão, certifique-se de selecionar **Manter-me ligado**.

## <a name="next-steps"></a>Próximos passos
[Ferramentas para resolver problemas de atualização](service-gateway-onprem-tshoot.md)
[Resolver problemas de cenários de atualização](refresh-troubleshooting-refresh-scenarios.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
