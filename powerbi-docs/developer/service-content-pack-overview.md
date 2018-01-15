---
title: "Descrição geral do programa de pacotes de conteúdos do serviço Power BI"
description: "Programa de Certificação do Pacote de Conteúdos"
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.date: 10/09/2017
ms.author: asaxton
ms.openlocfilehash: 4a8ea2acfcfe41192b82addfe52dbe67a0df8088
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="overview-of-the-power-bi-service-content-pack-program"></a>Descrição geral do programa de pacotes de conteúdos do serviço Power BI
Um pacote de conteúdos é um conjunto de conteúdos que permite aos utilizadores obter imediatamente informações a partir de uma origem. Um pacote de conteúdos concentra-se normalmente num cenário empresarial específico que fornece informações para uma função, domínio ou fluxo de trabalho.

Os ISVs podem criar pacotes de conteúdos de modelo que permitem aos clientes ligar e instanciar com as suas próprias contas. Como especialistas de domínio, podem desbloquear os dados de uma forma facilmente consumível por um utilizador empresarial. Os pacotes de conteúdos oferecem monitorização e análise ad-hoc aos seus clientes sem elevados investimentos na infraestrutura de relatórios. 

Estes pacotes de conteúdos de modelo criados por ISVs podem ser submetidos para a equipa do Power BI para serem disponibilizados publicamente na galeria de pacotes de conteúdos do Power BI (app.powerbi.com/getdata/services) e no Microsoft AppSource (appsource.microsoft.com). Pode encontrar um exemplo de experiência de pacotes de conteúdos públicos [aqui](template-content-pack-experience.md).

## <a name="overview"></a>Descrição geral
O processo geral para desenvolver e submeter um pacote de conteúdos de modelo envolve vários passos.

 ![Processo](media/service-content-pack-overview/developer-content-pack-overview.png)

1. [Reveja os requisitos](#requirements) e certifique-se de que os cumpre
2. [Crie conteúdos](template-content-pack-authoring.md#queries) no Power BI Desktop
3. [Crie um dashboard](template-content-pack-authoring.md#dashboard) no PowerBI.com
4. [Teste o pacote de conteúdos](template-content-pack-testing.md) na sua organização
5. [Submeta](template-content-pack-testing.md#submission) o conteúdo para o Power BI para publicação

<a name="requirements"></a>

## <a name="requirements"></a>Requisitos
Para criar e submeter um pacote de conteúdos a publicar no serviço Power BI e no AppSource, tem de cumprir os seguintes requisitos:

* Ter uma aplicação SaaS utilizada por utilizadores empresariais.
* A aplicação SaaS tem dados de utilizador que podem ser visualizados no Power BI.
* A aplicação SaaS tem uma API acessível através da Internet pública. Idealmente, trata-se de uma API REST ou um feed OData. Os pacotes de conteúdos do Power BI suportam vários tipos de autenticação, como Autenticação Básica, OAuth 2.0 e Chave de API. 
* Contrato de parceiro assinado. Vai fazê-lo no [passo de submissão](template-content-pack-testing.md#submission).

Reveja a secção de [criação](template-content-pack-authoring.md) para obter mais detalhes sobre os requisitos técnicos.

## <a name="business-scenario"></a>Cenário empresarial
Os pacotes de conteúdos fornecem informações e métricas concentradas num cenário empresarial específico. Compreender o seu público-alvo e o benefício que receberão do pacote de conteúdos irá ajudar a assegurar que os utilizadores são bem-sucedidos com o conteúdo que fornece.

### <a name="tips"></a>Sugestões
* Identificar o público-alvo e a tarefa que estão a tentar realizar  
* Concentrar-se num determinado período de tempo (últimos 90 dias) ou nos últimos N resultados  
* Importar apenas as tabelas/colunas relacionadas com o seu cenário  
* Considerar disponibilizar mais do que um pacote de conteúdos para cenários exclusivos separados  

## <a name="frequently-asked-questions"></a>Perguntas frequentes
**Posso criar um pacote de conteúdos do serviço Power BI para uma aplicação SaaS de terceiros que não possuo?**

Não. Atualmente, é necessário assinar um contrato de parceiro com o proprietário da aplicação SaaS antes de publicar o pacote de conteúdos no serviço.

**Não tenho uma API para programadores pública para o meu serviço. Posso continuar a criar um pacote de conteúdos do serviço Power BI que obtenha os dados diretamente a partir do armazenamento de dados?**

Não. Os pacotes de conteúdos do serviço Power BI requerem uma API para programadores acessível através da Internet pública.

**Que tipo de APIs são suportados pelos pacotes de conteúdos do serviço e que tipos de autenticação podem utilizar?**

Os pacotes de conteúdos do serviço Power BI suportam qualquer API REST ou feed OData. O Power BI pode utilizar diversos tipos de autenticação, incluindo Autenticação Básica, OAuth2.0 e Chave de API Web. Pode obter mais detalhes sobre os requisitos técnicos no artigo [Criação](template-content-pack-authoring.md#dashboard).

**Tenho mais perguntas sobre Pacotes de Conteúdos do serviço. Como posso contactá-lo?**

Não hesite em enviar-nos um e-mail com as suas perguntas para pbiservicesapps@microsoft.com

## <a name="support"></a>Suporte
Para obter suporte durante o desenvolvimento, utilize [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support). Esta conta é ativamente monitorizada e gerida. Os incidentes dos clientes são rapidamente reencaminhados para a equipa adequada.

## <a name="next-step"></a>Passo seguinte
[Criação](template-content-pack-authoring.md)

