---
title: O que são as aplicações de modelo do Power BI? (pré-visualização)
description: Este artigo é uma descrição geral do programa de aplicações de modelo do Power BI. Saiba como criar aplicações do Power BI com pouco ou nenhum código e implemente-as para qualquer cliente do Power BI.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/26/2019
ms.author: maggies
ms.openlocfilehash: 600e2ed603773cada415f603202cc72f22e0d25b
ms.sourcegitcommit: 81ba3572531cbe95ea0b887b94e91f94050f3129
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66751102"
---
# <a name="what-are-power-bi-template-apps-preview"></a>O que são as aplicações de modelo do Power BI? (pré-visualização)

As novas *aplicações de modelo* do Power BI permitem que os parceiros do mesmo criem aplicações do Power BI com pouco ou nenhum código e que as implementem para qualquer cliente do Power BI.  Este artigo é uma descrição geral do programa de aplicações de modelo do Power BI.

As aplicações de modelo são um substituto dos atuais pacotes de conteúdos do serviço. Enquanto parceiro do Power BI, pode criar um conjunto de conteúdos prontos a utilizar para os seus clientes e publicá-los manualmente.  

Pode criar aplicações de modelo que permitam que os seus clientes estabeleçam ligação e criem instâncias com as respetivas contas. Como especialistas de domínio, podem desbloquear os dados de forma a serem facilmente consumíveis pelos respetivos utilizadores empresariais.  

Pode submeter as suas aplicações de modelo no Cloud Partner Portal. Em seguida, as aplicações são disponibilizadas publicamente na Galeria de aplicações do Power BI (app.powerbi.com/getdata/services) e no Microsoft AppSource (appsource.microsoft.com). Eis uma descrição geral da experiência pública de criação de aplicações de modelo.  

## <a name="process"></a>Processo
O processo geral para desenvolver e submeter uma aplicação de modelo inclui várias fases. Algumas fases podem incluir mais do que uma atividade em simultâneo.


| Fase | Power BI Desktop |  |serviço Power BI  |  |Cloud Partner Portal  |
|---|--------|--|---------|---------|---------|
| **Um** | Crie um modelo de dados e um relatório num ficheiro .pbix |  | Crie uma área de trabalho. Importe o ficheiro .pbix. Crie um dashboard complementar  |  | Registe-se como um parceiro |
| **Dois** |  |  | Crie um pacote de teste e execute uma validação interna        |  | |
| **Três** | |  | Promova o pacote de teste na pré-produção para validação fora do seu inquilino do Power BI e submeta-o no AppSource  |  | Crie uma oferta de aplicação de modelo do Power BI com o seu pacote de pré-produção e inicie o processo de validação |
| **Quatro** | |  | Promova o pacote de pré-produção para produção |  | Publique a aplicação |

## <a name="requirements"></a>Requirements

Para criar a aplicação de modelo, necessita de permissões para esse efeito. Veja as Definições de aplicação de modelo do portal de administração do Power BI para obter detalhes. 

Para publicar uma aplicação de modelo no serviço Power BI e no AppSource, tem de cumprir os requisitos para se [tornar um Publicador do Cloud Marketplace](https://docs.microsoft.com/azure/marketplace/become-publisher).
 
## <a name="high-level-steps"></a>Passos gerais

Eis os passos gerais. 

1. [Reveja os requisitos](#requirements) para se certificar de que os cumpre. 

1. Crie um relatório no Power BI Desktop. Utilize parâmetros para poder guardá-lo num ficheiro utilizável por outras pessoas. 

1. Crie uma área de trabalho para a aplicação de modelo no seu inquilino no serviço Power BI (app.powerbi.com). 

1. Importe o seu ficheiro .pbix e adicione conteúdos à sua aplicação, como um dashboard. 

1. Crie um pacote de teste para testar a aplicação de modelo na sua organização. 

1. Promova a aplicação de teste na pré-produção para submeter a aplicação para validação no AppSource e para testá-la fora do seu próprio inquilino. 

1. Submeta os conteúdos no Cloud Partner Platform para publicação. 

1. Altere o estado da sua oferta para "Em direto" no AppSource e mude a sua aplicação para produção no Power BI.
2. Agora pode começar a desenvolver a versão seguinte na mesma área de trabalho em pré-produção. 

## <a name="requirements"></a>Requirements

Para criar a aplicação de modelo, necessita de permissões para esse efeito. Veja as [Definições de aplicação de modelo do portal de administração](service-admin-portal.md#template-apps-settings-preview) do Power BI para obter detalhes. 

Para publicar uma aplicação de modelo no serviço Power BI e no AppSource, tem de cumprir os requisitos para se [tornar um Publicador do Cloud Marketplace](https://docs.microsoft.com/azure/marketplace/become-publisher).

## <a name="tips"></a>Sugestões 

- Certifique-se de que a sua aplicação inclui dados de exemplo para que todos a comecem a utilizar com um simples clique. 
- Examine cuidadosamente a sua aplicação ao instalá-la no seu inquilino e num inquilino secundário. Certifique-se de que os clientes só veem aquilo que pretende. 
- Utilize o AppSource como loja online para alojar a sua aplicação. Desta forma, todas as pessoas que utilizarem o Power BI podem encontrar a sua aplicação. 
- Considere disponibilizar mais do que uma aplicação de modelo para cenários exclusivos separados. 
- Ative a personalização de dados, tal como uma ligação de suporte personalizada e a configuração de parâmetro por parte do instalador.

Veja [Tips for authoring template apps in Power BI (preview)](service-template-apps-tips.md) (Sugestões para criar aplicações de modelo no Power BI [pré-visualização]) para obter mais sugestões.

## <a name="support"></a>Suporte
Para obter suporte durante o desenvolvimento, utilize [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support). Monitorizamos e gerimos este site de forma ativa. Os incidentes dos clientes são rapidamente reencaminhados para a equipa adequada.

## <a name="next-steps"></a>Próximos passos

[Create a template app](service-template-apps-create.md) (Criar uma aplicação de modelo)