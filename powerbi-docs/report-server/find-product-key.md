---
title: Como localizar a chave de produto do servidor de relatórios
description: Saiba como pode encontrar a chave de produto do Microsoft Power BI Report Server para instalar o servidor num ambiente de produção.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 10/24/2018
ms.author: maggies
ms.openlocfilehash: 86d3bf34a8b222e72d76a5471fe6bfca93390afc
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861136"
---
# <a name="how-to-find-your-report-server-product-key"></a>Como localizar a chave de produto do servidor de relatórios
Saiba como pode encontrar a chave de produto do Microsoft Power BI Report Server para instalar o servidor num ambiente de produção.

<iframe width="640" height="360" src="https://www.youtube.com/embed/6CQnf-NGtpU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

Transferiu o Power BI Report Server e tem um contrato SQL Server Enterprise Software Assurance. Ou comprou o Premium do Power BI. Quer instalar o servidor num ambiente de produção, mas precisa de uma chave de produto para fazê-lo. Onde está a chave de produto? 

A chave de produto estará num de dois lugares, consoante o que comprou.

## <a name="purchased-power-bi-premium"></a>Adquiri o Power BI Premium
Se adquiriu o Power BI Premium, no separador **Definições de capacidade** do portal de administração do Power BI, terá acesso à sua chave de produto do Power BI Report Server. Esta opção estará apenas disponível para Administradores Globais ou utilizadores com a função de administrador de serviço do Power BI atribuída.

![Chave do Power BI Report Server nas definições Premium](media/find-product-key/pbirs-product-key.png)

Ao selecionar **chave do Power BI Report Server**, será apresentada uma caixa de diálogo com a sua chave de produto. Pode copiá-la e utilizá-la na instalação.

![Chave de produto do Power BI Report Server](media/find-product-key/pbirs-product-key-dialog.png)

## <a name="purchased-software-assurance-agreement"></a>Adquiri o contrato Software Assurance
Se tem um contrato do SQL Server Enterprise SA, pode obter a sua chave de produto no [Centro de Serviços de Licenciamento de Volume](https://www.microsoft.com/Licensing/servicecenter/). Procure no service pack mais recente para a versão mais recente do SQL Server. Se não encontrar aí a chave, procure na versão RTM da versão mais recente do SQL Server.

> [!NOTE]
> Terá de procurar na secção de transferências. Não na secção de chaves.
> 
> 

![Captura de ecrã a mostrar o SQL Server Enterprise, com o separador Transferências e Chaves com informações de integração do Power B I Report](media/find-product-key/vlsc-download.png "Volume Licensing Service Center").
 
## <a name="next-steps"></a>Próximos passos
[Instalar o Power BI Report Server](install-report-server.md)  
[Instalar o Power BI Desktop otimizado para o Power BI Report Server](install-powerbi-desktop.md)  
[Transferir o Report Builder](https://www.microsoft.com/download/details.aspx?id=53613)  
[Transferir o SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)