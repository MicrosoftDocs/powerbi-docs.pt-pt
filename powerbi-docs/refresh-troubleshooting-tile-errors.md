---
title: Resolver problemas de erros de mosaico
description: Erros comuns que podem ser encontrados quando um mosaico tenta ser atualizado no Power BI
author: mgblythe
ms.reviewer: kayu
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 12/06/2018
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: dbae4c82fb350242ed0fefadeeec217666fc3005
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877488"
---
# <a name="troubleshooting-tile-errors"></a>Resolver problemas de erros de mosaico
Veja abaixo os erros comuns que podem ser encontrados com mosaicos e uma explicação.

> [!NOTE]
> Se encontrar um erro que não esteja listado abaixo e que esteja a causar problemas, peça ajuda no [site da comunidade](https://community.powerbi.com/) ou crie um [pedido de suporte](https://powerbi.microsoft.com/support/).
> 
> 

## <a name="errors"></a>Erros
**O Power BI encontrou um erro inesperado ao carregar o modelo. Tente novamente mais tarde.**
ou **Não foi possível recuperar o modelo de dados. Entre em contacto com o proprietário do dashboard para ter certeza de que as origens e o modelo de dados existem e estão acessíveis.**

Não conseguimos aceder aos dados, porque a origem de dados não estava acessível. Este problema pode ocorrer se o nome da origem de dados tiver sido alterado ou se a mesma tiver sido removida ou movida, estiver offline ou se as permissões tiverem sido alteradas. Verifique se a origem ainda está no local para o qual estamos apontando e se ainda tem permissão para aceder a ela. Se esse não for o problema, a origem pode estar lenta. Tente novamente mais tarde numa hora em que a carga na origem seja menor. Se for uma origem local, o proprietário da origem de dados pode conseguir fornecer mais informações.

**Não tem permissão para ver este bloco ou abrir o livro.**

Entre em contacto com o proprietário do dashboard para ter a certeza de que as origens e o modelo de dados existem e estão acessíveis para a sua conta.

**Os elementos visuais personalizados foram desativados pelo administrador.**

O administrador do Power BI desativou a utilização de elementos visuais personalizados para a sua organização ou o seu grupo de segurança. Não poderá utilizar elementos visuais personalizados a partir do [Microsoft Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) ou importar elementos visuais privados de um ficheiro. Só poderá utilizar o conjunto de elementos visuais pré-empacotados.


**As formas de dados devem conter pelo menos um grupo ou cálculo que produza dados. Entre em contacto com o proprietário do dashboard.**

Não temos nenhum dado para exibir, pois a consulta está vazia. Tente adicionar alguns campos na lista de campos ao visual e fixá-lo novamente.

**Não é possível exibir os dados, porque o Power BI não pode determinar a relação entre dois ou mais campos.**

Está a tentar utilizar dois ou mais campos de tabelas que não estão relacionadas. Precisa de remover os campos não relacionados com visual e, em seguida, criar um relacionamento entre as tabelas. Depois de fazer esta alteração, pode adicionar os campos de volta ao elemento visual. Isso pode ser feito no Power BI Desktop ou no Power Pivot para Excel. [Saiba mais](desktop-create-and-manage-relationships.md)

**Os grupos no eixo primário e no eixo secundário sobrepõem-se. Os grupos no eixo primário não podem ter as mesmas chaves que os grupos no eixo secundário.**

Isto é geralmente um problema temporário. Isso geralmente acontece quando está a mover grupos de linhas para colunas. Nesse caso, o erro deverá desaparecer quando terminar de mover todos os grupos. Se ainda vir a mensagem, tente alternar os campos entre as linhas e colunas ou a legenda de eixo ou remover campos do visual.  

**Este elemento visual excedeu os recursos disponíveis. Tente filtrar para diminuir a quantidade de dados exibidos.**

O visual tentou consultar um número excessivo de dados para que possamos concluir o resultado com os recursos disponíveis. Tente filtrar o visual para reduzir a quantidade de dados no resultado.

**Não conseguimos identificar os seguintes campos: {0}. Atualize o visual com campos existentes no conjunto de dados.**

O campo provavelmente foi eliminado ou o seu nome foi alterado. É possível remover o campo quebrado do elemento visual, adicionar outro campo e fixá-lo novamente.

**Não foi possível recuperar os dados deste elemento visual. Tente novamente mais tarde.**

Isso geralmente é um problema temporário. Se tentar novamente mais tarde e continuar a receber essa mensagem, entre em contacto com o suporte.

**Os mosaicos continuam a mostrar os dados não filtrados após ativar o início de sessão único (SSO).**

Este problema poderá ocorrer se o conjunto de dados subjacente estiver configurado para utilizar o modo DirectQuery ou uma Ligação em Direto para o Analysis Services através de um gateway de dados no local. Neste caso, os mosaicos continuam a mostrar os dados não filtrados depois de ativar o SSO para a origem de dados até que o próximo mosaico seja atualizado. Na próxima atualização do mosaico, o Power BI utiliza o SSO conforme configurado e os mosaicos mostram os dados filtrados de acordo com a identidade do utilizador. 

Se quiser ver os dados filtrados imediatamente, poderá forçar uma atualização do mosaico ao selecionar **Mais opções** (...) no canto superior direito de um dashboard e, em seguida, **Atualizar mosaicos do dashboard**.

Como proprietário de um conjunto de dados, também pode alterar a frequência de atualização dos mosaicos e defini-la como 15 minutos para acelerar a atualização dos mosaicos. Selecione o ícone da engrenagem no canto superior direito do serviço Power BI e, em seguida, selecione **Definições**. Na página **Definições**, selecione o separador **Conjunto de dados**. Expanda **Atualização de cache agendada** e altere a **Frequência de atualização**. Confirme que repõe a configuração da frequência de atualização original após o Power BI executar a próxima atualização de mosaico.

> [!NOTE]
> A seção **Atualização de cache agendada** só está disponível para conjuntos de dados no modo DirectQuery/LiveConnection. Os conjuntos de dados no modo de Importação não precisam de uma atualização de mosaico em separado, dado que os mosaicos são atualizados automaticamente durante a próxima atualização de dados agendada.

## <a name="contact-support"></a>Contact support
Se ainda estiver com problemas, [entre em contacto com o suporte](https://support.powerbi.com) para investigá-los mais aprofundadamente.

## <a name="next-steps"></a>Próximos passos
[Resolução de problemas do Gateway de dados no local](service-gateway-onprem-tshoot.md)  
[Resolução de Problemas do Power BI Personal Gateway](service-admin-troubleshooting-power-bi-personal-gateway.md)  
Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)

