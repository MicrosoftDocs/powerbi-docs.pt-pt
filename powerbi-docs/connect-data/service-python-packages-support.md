---
title: Saber quais os pacotes Python suportados
description: Pacotes Python suportados e não suportados no Power BI
author: otarb
ms.author: otarb
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 06/26/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 07b16bb90b548f071472f9f7d22095ccdff78f56
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96401725"
---
# <a name="create-visuals-by-using-python-packages-in-the-power-bi-service"></a>Criar elementos visuais com pacotes Python no serviço Power BI
Pode utilizar a poderosa [linguagem de programação Python](https://www.python.org/) para criar elementos visuais no serviço Power BI. Inúmeros pacotes Python são suportados no serviço Power BI (e muitos mais estão a ser suportados).

As secções seguintes apresentam uma tabela alfabética dos pacotes Python suportados no Power BI. 

## <a name="request-support-for-a-new-python-package"></a>Pedido de suporte de um novo pacote Python
Os pacotes Python suportados para o **serviço Power BI** encontram-se na secção seguinte, intitulada **Pacotes Suportados**. Se quiser pedir suporte para um pacote Python não presente na lista, envie o pedido para o [Power BI Ideas](https://ideas.powerbi.com).

## <a name="requirements-and-limitations-of-python-packages"></a>Requisitos e Limitações dos pacotes Python
Existem alguns requisitos e limitações para os pacotes Python:

* Runtime do Python atual: Python 3.7.7.
* O serviço Power BI suporta, na maioria das vezes, pacotes Python com licenças de software gratuitas e open source, como GPL-2, GPL-3, MIT+, etc.
* O serviço Power BI suporta pacotes publicados no PyPI. O serviço não suporta pacotes Python privados ou personalizados. É recomendável que os utilizadores disponibilizem os pacotes privados no PyPl CRAN antes de pedirem que o pacote esteja disponível no serviço Power BI.
* Para elementos visuais do Python no **Power BI Desktop**, pode instalar qualquer pacote, incluindo pacotes Python personalizados.
* Por motivos de segurança e privacidade, os pacotes Python que proporcionam consultas cliente/servidor através da Web no serviço não são suportados. O funcionamento em rede é bloqueado para essas tentativas.
* O processo de aprovação para incluir um novo pacote Python tem uma árvore de dependências; algumas dependências que têm de ser instaladas no serviço não são suportadas.

## <a name="python-packages-that-are-supported-in-power-bi"></a>Pacotes Python suportados no Power BI
A tabela seguinte mostra os pacotes **suportados** no serviço Power BI.


|        Pacote        |   Versão   |                                   Ligação                                   |
|-----------------------|-------------|--------------------------------------------------------------------------|
|matplotlib|3.2.1|https://pypi.org/project/matplotlib|
|numpy|1.18.4|https://pypi.org/project/numpy|
|pandas|1.0.1|https://pypi.org/project/pandas|
|scikit-learn|0.23.0|https://pypi.org/project/scikit-learn|
|scipy|1.4.1|https://pypi.org/project/scipy|
|seaborn|0.10.1|https://pypi.org/project/seaborn|
|statsmodels|0.11.1|https://pypi.org/project/statsmodels|
|xgboost|1.1.0|https://pypi.org/project/xgboost|

## <a name="next-steps"></a>Próximos passos
Para obter mais informações sobre o Python no Power BI, veja os seguintes artigos:

* [Criar elementos visuais do Power BI através de Python](desktop-python-visuals.md)
* [Executar scripts Python no Power BI Desktop](desktop-python-scripts.md)
* [Utilizar o Python no Editor de Consultas](desktop-python-in-query-editor.md)
