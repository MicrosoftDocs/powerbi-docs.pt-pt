---
title: Sugestões de Desempenho
description: Como criar um elemento visual Power BI de elevado desempenho
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/20/2020
ms.openlocfilehash: 7ebc02b2c459517957425e78438e12e89dc2e1bb
ms.sourcegitcommit: 1059c6222458f189fb5301dcb689dad2b2c00bc1
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/28/2020
ms.locfileid: "82196566"
---
# <a name="how-to-build-a-high-performance-power-bi-visual"></a>Como criar um elemento visual Power BI de elevado desempenho
Este artigo abrangerá técnicas sobre a forma como um programador pode alcançar elevado desempenho ao compor elementos visuais. 

Ninguém quer que um elemento visual demore demasiado tempo na composição, e conseguir o máximo desempenho possível do código é essencial à composição. 

> [!NOTE]
> À medida que continuamos a melhorar e a otimizar a plataforma, estão constantemente a ser lançadas novas versões da API. Para tirar o máximo partido da plataforma e conjunto de funcionalidades dos elementos visuais do Power BI, recomenda-se que se mantenha atualizado com a versão mais recente.
>
> Desde a mais recente **versão 2.1**, os tempos de carregamento de elementos visuais do Power BI melhoraram em média 20%.

## <a name="power-bi-visual-performance-tips"></a>Sugestões de desempenho de elementos visuais do Power BI
Aqui ficam algumas recomendações sobre como conseguir um desempenho ideal dos elementos visuais. 

### <a name="use-user-timing-api"></a>Utilizar a API de Tempo de Utilizador
A utilização da **API de Tempo de Utilizador** para medir o desempenho do JavaScript da sua aplicação pode ajudar a decidir quais as partes do script que precisam de otimização.

Para obter mais informações, veja [User Timing API (API Tempo de Utilizador)](https://msdn.microsoft.com/library/hh772738(v=vs.85).aspx).

### <a name="review-animation-loops"></a>Rever ciclos de animação
O ciclo de animação redesenha elementos não alterados? 

 - Problema: Perde tempo a desenhar elementos que não mudam de estrutura para estrutura.

 - Solução: Atualize as estruturas seletivamente. 
 
Quando chega a altura de animar visualizações estáticas, é tentador colocar código numa única função de atualização e chamá-lo repetidamente com novos dados para cada iteração do ciclo de animação.

Em vez disso, considere o seguinte padrão de atualização: utilize um método de construção de elementos visuais para desenhar tudo estático e, assim, a função de atualização só precisa de desenhar elementos de visualização que mudem. 

   > [!TIP]
   > Os ciclos de animação ineficientes são geralmente encontrados em eixos e legendas.

### <a name="cache-dom-nodes"></a>Nós de cache do DOM 
Quando um nó ou lista de nós é obtido do DOM, tem de pensar se pode reutilizá-los em computações posteriores (às vezes até mesmo na próxima iteração do ciclo). Desde que não precise de adicionar ou eliminar nós adicionais na área relevante, colocá-los em cache pode melhorar a eficiência global da sua aplicação.

Para garantir que o seu código é rápido e não abranda o browser, mantenha o acesso ao DOM no mínimo. 

- Antes: 

   ```javascript
   public update(options: VisualUpdateOptions) { 
       let axis = $(".axis"); 
   }
   ```

- Depois: 

   ```javascript
   public constructor(options: VisualConstructorOptions) { 
       this.$root = $(options.element); 
       this.xAxis = this.$root.find(".xAxis"); 
   } 
 
   public update(options: VisualUpdateOptions) { 
       let axis = this.axis; 
   }
   ```

### <a name="avoid-dom-manipulation"></a>Evitar a manipulação do DOM 
Limite a manipulação do DOM o máximo possível.  As operações de inserção como `prepend()`, `append()` e `after()` são morosas e não devem ser utilizadas a menos que seja necessário.

Por exemplo:

  ```javascript
  for (let i=0; i<1000; i++) { 
      $('#list').append('<li>'+i+'</li>');
  }
  ```

O exemplo acima poderia ser acelerado com `html()` e ao compilar a lista previamente: 

  ```javascript
  let list = ''; 
  for (let i=0; i<1000; i++) { 
      list += '<li>'+i+'</li>'; 
  } 

  $('#list').html(list); 
  ```

### <a name="reconsider-jquery"></a>Reconsiderar o JQuery

Limitar as suas estruturas JS e utilizar JS nativo sempre que possível pode aumentar a largura de banda disponível e diminuir a sobrecarga do processamento. Isto também pode limitar problemas de compatibilidade com browsers mais antigos. 

Para obter mais informações, veja [youmightnotneedjquery.com](http://youmightnotneedjquery.com/) para obter exemplos alternativos a funções como `show`, `hide`, `addClass` de JQuery e mais.  

### <a name="use-canvas-or-webgl"></a>Utilizar tela ou WebGL 
Para a utilização repetida de animações, considere utilizar **Tela** ou **WebGL** em vez de SVG. Ao contrário do SVG, com estas opções o desempenho é determinado pelo tamanho e não pelos conteúdos. 

Pode ler mais sobre as diferenças em [SVG vs Canvas: How to Choose (SVG vs Tela: Como escolher)](https://msdn.microsoft.com/library/gg193983(v=vs.85).aspx). 

### <a name="use-requestanimationframe-instead-of-settimeout"></a>Utilize requestAnimationFrame em vez de setTimeout 
Se utilizar [requestAnimationFrame](https://www.w3.org/TR/animation-timing/) para atualizar as animações no ecrã, as suas funções de animação são chamadas **antes** de o browser chamar outro redesenho.

Para obter mais informações, veja esta [amostra](https://testdrive-archive.azurewebsites.net/Graphics/RequestAnimationFrame/Default.html) em animação uniforme com `requestAnimationFrame`.

## <a name="next-steps"></a>Próximos passos

Saiba mais sobre técnicas de otimização no [Guia de otimização para Power BI](/power-bi/guidance/power-bi-optimization).
