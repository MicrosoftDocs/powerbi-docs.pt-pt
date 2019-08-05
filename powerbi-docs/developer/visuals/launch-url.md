---
title: Launch URL (Iniciar URL)
description: Os elementos visuais do Power BI podem abrir o URL num novo separador
author: Guy-Moses
ms.author: guymos
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 1a7002c3b45f341c0cbc0db683bc4f8a113e21f9
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424867"
---
# <a name="launch-url"></a>Launch URL (Iniciar URL)

Iniciar URL permite abrir um novo separador (ou janela) do browser ao delegar o trabalho real no Power BI.

## <a name="sample"></a>Exemplo

```typescript
   this.host.launchUrl('https://powerbi.microsoft.com');
```

## <a name="usage"></a>Utilização

Utilize a chamada à API `host.launchUrl()` ao transmitir o seu URL de destino como argumento de cadeia de carateres:

```typescript
this.host.launchUrl('http://some.link.net');
```

## <a name="restrictions"></a>Restrições

* Utilize apenas caminhos absolutos e não relativos. `http://some.link.net/subfolder/page.html` está bem; `/page.html` não será aberto.
* De momento, só são suportados os protocolos `http` e `https`. Evite `ftp`, `mailto`, etc.

## <a name="best-practices"></a>Melhores práticas

1. Na maioria dos casos, é melhor abrir apenas uma ligação como resposta a uma ação explícita de um utilizador. Faça com que seja fácil o utilizador compreender que, se clicar na ligação ou no botão, será aberto um novo separador. O utilizador poderá ficar confuso ou frustrado se acionar uma chamada `launchUrl()` sem ter realizado uma ação ou como efeito secundário de uma ação diferente.
2. Se a ligação não for essencial para o funcionamento do elemento visual, recomenda-se fornecer ao autor do relatório uma forma de desativar e ocultar a ligação. Isto é especialmente relevante em casos de utilização do Power BI especiais, tais como a incorporação de um relatório numa aplicação de terceiros ou a respetiva publicação na Web.
3. Evite acionar uma chamada `launchUrl()` dentro de um ciclo, da função `update` do elemento visual ou de outro código que surja frequentemente.

## <a name="step-by-step-example"></a>Exemplo passo a passo

### <a name="adding-a-link-launching-element"></a>Adicionar um elemento de inicialização de ligação

As seguintes linhas foram adicionadas à função `constructor` do elemento visual:

```typescript
    this.helpLinkElement = this.createHelpLinkElement();
    options.element.appendChild(this.helpLinkElement);
```

Além disso, adicionou-se uma função privada que cria e anexa o elemento de âncora:

```typescript
private createHelpLinkElement(): Element {
    let linkElement = document.createElement("a");
    linkElement.textContent = "?";
    linkElement.setAttribute("title", "Open documentation");
    linkElement.setAttribute("class", "helpLink");
    linkElement.addEventListener("click", () => {
        this.host.launchUrl("https://docs.microsoft.com/power-bi/developer/custom-visual-develop-tutorial");
    });
    return linkElement;
};
```

Por último, uma entrada no ficheiro visual.less define o estilo para o elemento de ligação:

```less
.helpLink {
    position: absolute;
    top: 0px;
    right: 12px;
    display: block;
    width: 20px;
    height: 20px;
    border: 2px solid #80B0E0;
    border-radius: 20px;
    color: #80B0E0;
    text-align: center;
    font-size: 16px;
    line-height: 20px;
    background-color: #FFFFFF;
    transition: all 900ms ease;

    &:hover {
        background-color: #DDEEFF;
        color: #5080B0;
        border-color: #5080B0;
        transition: all 250ms ease;
    }

    &.hidden {
        display: none;
    }
}
```

### <a name="adding-a-toggling-mechanism"></a>Adicionar um mecanismo de alternância

Isto requer a adição de um objeto estático (veja o [tutorial relativo a objetos estáticos](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties)) para que o autor do relatório possa alternar a visibilidade do elemento de ligação (a predefinição está definida como oculto).
Foi adicionado um objeto estático booleano `showHelpLink` à entrada de objetos `capabilities.json`:

```typescript
"objects": {
    "generalView": {
            "displayName": "General View",
            "properties":
                "showHelpLink": {
                    "displayName": "Show Help Button",
                    "type": {
                        "bool": true
                    }
                }
            }
        }
    }
```

![Iniciar o botão de ativar/desativar o URL](./media/launchurl-toggle.png)

Além disso, foram adicionadas as seguintes linhas na função `update` do elemento visual:

```typescript
if (settings.generalView.showHelpLink) {
    this.helpLinkElement.classList.remove("hidden");
} else {
    this.helpLinkElement.classList.add("hidden");
}
```

A classe `hidden` está definida em visual.less para controlar a apresentação do elemento.
