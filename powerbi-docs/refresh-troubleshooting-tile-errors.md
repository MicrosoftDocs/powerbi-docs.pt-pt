---
title: Resolver problemas de erros de mosaico
description: Erros comuns que podem ser encontrados quando um mosaico tenta ser atualizado
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 8b68ce7af749b7e7f292592f6debdc7e964d6c17
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/26/2018
ms.locfileid: "34242892"
---
# <a name="troubleshooting-tile-errors"></a>Resolver problemas de erros de mosaico
Veja abaixo os erros comuns que podem ser encontrados com mosaicos e uma explicação.

> [!NOTE]
> Se encontrar um erro que não esteja listado abaixo e que esteja a causar problemas, peça ajuda no [site da comunidade](http://community.powerbi.com/) ou crie um [pedido de suporte](https://powerbi.microsoft.com/support/).
> 
> 

## <a name="errors"></a>Erros
**O Power BI encontrou um erro inesperado ao carregar o modelo. Tente novamente mais tarde.**
ou **Não foi possível recuperar o modelo de dados. Entre em contacto com o proprietário do dashboard para ter certeza de que as origens e o modelo de dados existem e estão acessíveis.**

Não conseguimos aceder aos dados, porque a origem de dados não estava acessível. Isso pode ocorrer se a origem de dados tiver sido removida, ter tido o nome alterado, movida, estivesse offline ou se as permissões fossem alteradas. Verifique se a origem ainda está no local para o qual estamos apontando e se ainda tem permissão para aceder a ela. Se esse não for o problema, a origem pode estar lenta. Tente novamente mais tarde numa hora em que a carga na origem seja menor. Se for uma origem local, o proprietário da origem de dados pode conseguir fornecer mais informações.

**Não tem permissão para ver este bloco ou abrir o livro.**

Entre em contacto com o proprietário do dashboard para ter certeza de que as origem e o modelo de dados existem e estão acessíveis para sua conta.

**As formas de dados devem conter pelo menos um grupo ou cálculo que produza dados. Entre em contacto com o proprietário do dashboard.**

Não temos nenhum dado para exibir, pois a consulta está vazia. Tente adicionar alguns campos na lista de campos ao visual e fixá-lo novamente.

**Não é possível exibir os dados, porque o Power BI não pode determinar a relação entre dois ou mais campos.**

Está a tentar utilizar dois ou mais campos de tabelas que não estão relacionadas. Precisa de remover os campos não relacionados com visual e, em seguida, criar um relacionamento entre as tabelas. Depois disso, pode adicionar os campos de volta ao visual. Isso pode ser feito no Power BI Desktop ou no Power Pivot para Excel. [Saiba mais](desktop-create-and-manage-relationships.md)

**Os grupos no eixo primário e no eixo secundário sobrepõem-se. Os grupos no eixo primário não podem ter as mesmas chaves que os grupos no eixo secundário.**

Isso geralmente é um problema temporário. Isso geralmente acontece quando está a mover grupos de linhas para colunas. Nesse caso, o erro deverá desaparecer quando terminar de mover todos os grupos. Se ainda vir a mensagem, tente alternar os campos entre as linhas e colunas ou a legenda de eixo ou remover campos do visual.  

**Este elemento visual excedeu os recursos disponíveis. Tente filtrar para diminuir a quantidade de dados exibidos.**

O visual tentou consultar um número excessivo de dados para que possamos concluir o resultado com os recursos disponíveis. Tente filtrar o visual para reduzir a quantidade de dados no resultado.

**Não conseguimos identificar os seguintes campos: {0}. Atualize o visual com campos existentes no conjunto de dados.**

O campo provavelmente foi eliminado ou o seu nome foi alterado. É possível remover o campo quebrado do elemento visual, adicionar outro campo e fixá-lo novamente.

**Não foi possível recuperar os dados deste elemento visual. Tente novamente mais tarde.**

Isso geralmente é um problema temporário. Se tentar novamente mais tarde e continuar a receber essa mensagem, entre em contacto com o suporte.

## <a name="contact-support"></a>Contactar o suporte
Se ainda estiver tendo problemas, [entre em contacto com o suporte](https://support.powerbi.com) para investigá-los mais detalhadamente.

## <a name="next-steps"></a>Próximos passos
[Resolução de problemas do Gateway de dados no local](service-gateway-onprem-tshoot.md)  
[Resolução de Problemas do Power BI Personal Gateway](service-admin-troubleshooting-power-bi-personal-gateway.md)  
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

