---
title: Adicionar bibliotecas externas aos elementos visuais do Power BI na análise incorporada do Power BI para melhores informações de BI incorporadas
description: Este artigo descreve como utilizar as bibliotecas externas nos elementos visuais do Power BI. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/24/2020
ms.openlocfilehash: b9a443040384e4d38bd7440eae0a5582cc422836
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889185"
---
# <a name="adding-external-libraries"></a>Adding external libraries (Adicionar bibliotecas externas)

Este artigo descreve como utilizar as bibliotecas externas nos elementos visuais do Power BI. Inclui informações sobre a instalação, a importação e a chamada de bibliotecas externas a partir do código do elemento visual do Power BI.

## <a name="javascript-libraries"></a>Bibliotecas de JavaScript

1. Instale uma biblioteca de JavaScript externa com qualquer gestor de pacotes como o *npm* ou o *yarn*.
2. Importe os módulos necessários para os ficheiros de origem com a biblioteca externa.

>[!NOTE]
>Se quiser adicionar digitações à biblioteca de JavaScript e obter o Intellisense e segurança de tempo de compilação, confirme que instala o pacote adequado.

### <a name="installing-the-d3-library"></a>Instalar a biblioteca d3

Segue-se um exemplo de instalação da [biblioteca d3](https://www.npmjs.com/package/d3) e do pacote [@types/d3](https://www.npmjs.com/package/@types/d3) com o [npm](https://www.npmjs.com/).

Para obter um exemplo completo, veja o código das [Power BI visualizations](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L29) (Visualizações do Power BI).

1. Instale o pacote *d3* e o pacote *d3 types*.

    ```powershell
    npm install d3@5 --save
    npm install @types/d3@5 --save
    ```

2. Importe a biblioteca *d3* para os ficheiros que a utilizam, tal como o `visual.ts`.

    ```typescript
    import * as d3 from "d3";
    ```

## <a name="css-framework"></a>Estrutura CSS

1. Instale uma estrutura CSS externa com qualquer gestor de pacotes como o *npm* ou o *yarn*.
2. No ficheiro `.less` do elemento visual, inclua a instrução `import`.

### <a name="installing-bootstrap"></a>Instalar o bootstrap

Segue-se um exemplo de instalação do [bootstrap](https://www.npmjs.com/package/bootstrap) com o [npm](https://www.npmjs.com/).

Para obter um exemplo completo, veja o código das [Power BI visualizations](https://github.com/Microsoft/powerbi-visuals-sankey/blob/c8200da56913cd8b253be949a35fad0f4472b6de/style/visual.less#L32) (Visualizações do Power BI).

1. Instale o pacote *bootstrap*.

    ```powershell
    npm install bootstrap --save
    ```

2. Inclua a instrução `import` em `visual.less`.

    ```less
    @import (less) "node_modules/bootstrap/dist/css/bootstrap.css";
    ```
