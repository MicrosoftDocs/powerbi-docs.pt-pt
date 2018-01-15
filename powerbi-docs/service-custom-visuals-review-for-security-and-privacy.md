---
title: "Rever a segurança e a privacidade dos elementos visuais personalizados"
description: "Antes de ativar um visual personalizado, deverá consultar a segurança e privacidade desse visual para garantir que este cumpre os padrões da sua organização."
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
ms.date: 09/05/2017
ms.author: asaxton
ms.openlocfilehash: 20a697cbc4698e237f3ac09b031ea0c4cb734a52
ms.sourcegitcommit: 12236d08c27c7ee3fabb7ef9d767e9dee693f8aa
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/21/2017
---
# <a name="review-custom-visuals-for-security-and-privacy"></a>Rever a segurança e a privacidade dos elementos visuais personalizados
Antes de ativar um visual personalizado, deverá consultar a segurança e privacidade desse visual para garantir que este cumpre os padrões da sua organização.

## <a name="enable-a-custom-visual"></a>Ativar um elemento visual personalizado
<a name="enable"></a>Um elemento visual personalizado no relatório está desativado até selecionar **Ativar elementos visuais personalizados**, conforme mostrado abaixo.  

![](media/service-custom-visuals-review-for-security-and-privacy/emptyvisual.png)

## <a name="considerations-before-you-enable-a-custom-visual"></a>Considerações antes de ativar um elemento visual personalizado
<a name="considerations"></a>

> [!WARNING]
> Um elemento visual personalizado pode conter código com riscos de segurança ou privacidade; assim, um elemento visual personalizado no relatório está desativado até selecionar Ativar elementos visuais personalizados. Seguem-se algumas considerações para decidir se é necessário ativar um elemento visual personalizado:
> 
> 

1. Certifique-se de que confia no autor e na origem dos elementos visuais personalizados utilizados no relatório
2. Se não souber o que fazer, contacte a equipa de TI para decidir se deve ativar os elementos visuais personalizados para os relatórios visualizados.
3. Se alguém partilhar um relatório consigo com um elemento visual personalizado, mesmo se for um colega de trabalho próximo, não se sinta obrigado a ativar o elemento visual personalizado. Não há problema em voltar atrás e considerar se isso é essencial para a tarefa em questão. É sempre bom pedir que alguém forneça um relatório sem elementos visuais personalizados, caso não tenha confiança no elemento visual personalizado.

## <a name="security-best-practices-for-it-professionals-to-enable-a-custom-visual"></a>Melhores práticas de segurança para profissionais de TI para ativar um elemento visual personalizado
<a name="security"></a>

> [!WARNING]
> Um elemento visual personalizado pode conter código com riscos de segurança ou privacidade; assim, um elemento visual personalizado no relatório está desativado até selecionar Ativar elementos visuais personalizados. Existem várias melhores práticas que pode seguir para avaliar a segurança e a privacidade de um elemento visual personalizado.
> 
> 

1. Implemente um processo de aprovação de elementos visuais personalizados na organização. Os elementos visuais personalizados aprovados seriam partilhados com os utilizadores internos através de um site interno, como uma biblioteca de documentos do SharePoint ou um documento do OneNote.
2. Fornece orientações para utilizadores empresariais sobre a utilização adequada de elementos visuais personalizados e um grupo de e-mail para que os utilizadores empresariais enviem perguntas sobre privacidade e segurança.
3. Avalie o código JavaScript no ficheiro pbiviz do elemento visual personalizado.

**Para avaliar o código JavaScript num visual personalizado**

Um elemento visual personalizado utiliza JavaScript, pelo que pode conter riscos de segurança ou privacidade. Se receber um elemento visual personalizado ou um ficheiro pbix com um elemento visual personalizado de uma origem desconhecida, convém verificar se o JavaScript é seguro.

Para avaliar o código JavaScript num elemento visual personalizado, extraia o código do elemento visual personalizado. Veja aqui como extrair o código:  

1. Guarde o ficheiro .pbiviz numa pasta.
2. Mude o nome do ficheiro para um ficheiro .zip.
3. Extraia o ficheiro zip para uma pasta local.

## <a name="custom-visual-file-contents"></a>Conteúdo do ficheiro do elemento visual personalizado
Veja abaixo o conteúdo de um ficheiro pbiviz:

| **Ficheiro** | **Descrição** |
|:--- |:--- |
| ./package.json |Um ficheiro de manifesto que indica quais os ficheiros a carregar para o elemento visual personalizado. |
| ./resources |Contém o CSS, TypeScript e JavaScript utilizados pelo elemento visual personalizado. |
| ./resources/&lt;name&gt; |&lt;name&gt; é o nome do visual personalizado. |
| ./resources/&lt;name&gt;.css |O ficheiro de recurso css do elemento visual personalizado. |
| ./resources/&lt;name&gt;.js |O código executado quando um utilizador clica em Ativar elementos visuais personalizados ou depois de um utilizador Importar um elemento visual personalizado. O código JavaScript de aviso pode conter riscos de segurança ou privacidade. |
| ./resources/&lt;name&gt;.ts |O código fonte JavaScript para o elemento visual no formato TypeScript. O código JavaScript ou TypeScript de aviso pode conter riscos de segurança ou privacidade. |
| ./resources/&lt;name&gt;.png |O ícone mostrado ao utuilizador para o elemento visual. |

Depois de extrair o ficheiro pbiviz, pode avaliar o código. Seguem-se algumas melhores práticas e as ameaças a procurar.

## <a name="best-practices-to-evaluate-the-javascript-or-typescript-code"></a>Melhores práticas para avaliar o código JavaScript ou TypeScript
O código **JavaScript** ou **TypeScript** pode conter riscos de segurança ou de privacidade. Seguem-se algumas melhores práticas e as ameaças a procurar.

### <a name="best-practices-to-evaluate-javascript-code"></a>Melhores práticas para avaliar o código JavaScript
* Avalie sempre o conteúdo do ficheiro .js. Este é o código que é realmente executado. É possível que o conteúdo do ficheiro .ts não seja compilado para o ficheiro .js incluído no elemento visual personalizado.
* Avalie sempre o conteúdo do ficheiro .ts. Pode carregar o ficheiro .ts para as **Ferramentas de Programador**, exportar o elemento visual e comparar o ficheiro .js resultante no ficheiro .pbiviz recém-criado com o ficheiro .js original contido no elemento visual
* Verifique se o ícone do elemento visual personalizado não se assemelha muito a outros elementos visuais com que o utilizador esteja familiarizado.
* Avalie sempre o elemento visual numa conta de teste com privilégios mínimos e sem acesso a dados confidenciais. O ideal é que a conta de teste seja uma conta local sem informações de início de sessão para serviços diferentes do Power BI.

### <a name="threats-to-look-for-in-javascript-code"></a>Ameaças que devem ser procuradas num código JavaScript
* Verifique a atividade de rede quando o elemento visual estiver a ser utilizado no modo de edição e visualização. Certifique-se de que está satisfeito com os pedidos que estão a ser feitos. Não deve ver pedidos aos recursos fora do domínio do Power BI, a menos que o autor do elemento visual o tenha comunicado antecipadamente.
* Quaisquer dados que veja a sair do domínio do Power BI devem corresponder às suas expetativas de uma utilização "normal". Por exemplo, se o elemento visual implementar um leitor de vídeo que utilize um iFrame para ver um vídeo de outro site, algumas informações devem percorrer os pedidos do IFrame para compor o vídeo corretamente. No entanto, se vir todo o conjunto de dados enviado pela rede, pode investigar mais detalhadamente se isto é necessário e desejado.
* Verifique se estão a ser enviados ou armazenados dados pessoais pelo elemento visual personalizado.
* Verifique se o elemento visual personalizado está a tentar aceder aos recursos do computador local, como gravar ficheiros no disco ou aceder a cookies.
* Verifique se o elemento visual personalizado tem o que parece ser código ofuscado ou código sem um objetivo claro.
* Guarde cópias de cada elemento visual revisto anteriormente.
* Se estiver a rever uma atualização a um elemento visual que analisou anteriormente, certifique-se de que verifica as alterações. Aplique sempre o mesmo rigor às atualizações como da primeira vez que recebeu o elemento visual para revisão
* Se encontrar algo suspeito ou incorreto, contacte-nos; estamos aqui para ajudar.

## <a name="next-steps"></a>Passos seguintes
[Visualizações no Power BI](power-bi-report-visualizations.md)  
[Visualizações personalizadas no Power BI](power-bi-custom-visuals.md)  
[Publicar elementos visuais personalizados na Loja do Office](developer/office-store.md)  
[Introdução às ferramentas de programador de visuais personalizados](service-custom-visuals-getting-started-with-developer-tools.md)  
[Como certificar um visual personalizado](power-bi-custom-visuals-certified.md)    
[Vídeo: criar visualizações personalizadas para o Power BI com Sachin Patney e Nico Cristache](https://www.youtube.com/watch?v=kULc2VbwjCc)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

