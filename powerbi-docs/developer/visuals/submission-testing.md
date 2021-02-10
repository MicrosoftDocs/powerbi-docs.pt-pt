---
title: Teste de submissão de um elemento visual do Power BI
description: Este artigo descreve casos de testes que o elemento visual deve passar antes de ser publicado no AppSource. Há também casos de teste de opção.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 02/09/2021
ms.openlocfilehash: 391282b7868ba24b14c0859d431e6868b3fcbc2d
ms.sourcegitcommit: 7e0cc3b1ed9cf38da134ef7221648cb758ceea98
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/10/2021
ms.locfileid: "100100839"
---
# <a name="testing-a-power-bi-visual-before-submission"></a>Testar um visual Power BI antes da submissão

Antes de publicar o seu elemento visual no [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals), este tem de passar os testes listados neste artigo. Teste o elemento visual antes de o submeter. Se o elemento visual não passar nos casos de teste necessários, será rejeitado.

Para obter mais informações sobre o processo de publicação, veja [Publicar elementos visuais do Power BI no Centro de Parceiros](./office-store.md).

## <a name="testing-a-new-version-of-a-published-visual"></a>Testar uma nova versão de um elemento visual publicado

Por predefinição, o Power BI carrega a versão mais recente publicada do visual a partir do AppSource, mesmo que importe o visual a partir de um ficheiro local.

Se estiver a testar ou depurar uma nova versão de um visual já publicado, pode substituir a versão AppSource com uma versão de ficheiro local, permitindo o modo Developer em Power BI Desktop ou serviço Power BI.

### <a name="enable-developer-mode-in-power-bi-desktop"></a>Ativar o modo de desenvolvedor no Power BI Desktop

No Power BI Desktop, o Modo de Programador é válido apenas para uma sessão. Se abrir uma instância do Power BI Desktop para testar, irá precisar de ativar o Modo de Programador novamente.

Para ativar o Modo de Programador, siga estes passos:

1. Abra o Power BI Desktop.

2.  Selecione **Ficheiro** > **Opções e definições**.

3.  Selecione **Opções**.

4. Na janela Opções, na lista FICHEIRO ATUAL, selecione **Definições de relatório**.

5. No Modo de Programador, selecione a opção **Ativar o modo de programador para esta sessão**.

### <a name="enable-developer-mode-in-power-bi-service"></a>Ativar o modo developer no serviço Power BI

No serviço Power BI, o modo Desenvolvedor é mantido por conta de utilizador. Sempre que um utilizador carrega o pacote a partir do ficheiro local, o Power BI ignorará a versão AppSource do visual.

Para ativar o modo Developer no serviço Power BI, siga as instruções no [serviço Power UP BI para desenvolver um visual](environment-setup.md#set-up-power-bi-service-for-developing-a-visual).

## <a name="general-test-cases"></a>Casos de teste gerais

Verifique se o seu elemento visual passa os casos de teste gerais.

| Caso de teste | Resultados esperados
| --------- | ----------------
| Crie um **Gráfico de colunas empilhadas** com **Categoria** e **Valor**. Converta-o no elemento visual e, em seguida, de novo em gráfico de colunas. | Não é apresentado nenhum erro após estas conversões. |
| Crie um **Medidor** com três medidas. Converta-o no elemento visual e, em seguida, de novo em **Medidor**. | Não é apresentado nenhum erro após estas conversões. |
| Faça seleções no elemento visual. | Os outros elementos visuais refletem as seleções. |
| Selecione elementos noutros elementos visuais. | O elemento visual mostra os dados filtrados de acordo com a seleção nos outros elementos visuais. |
| Verifique as condições mín./máx. de **ViewMapping**. | Os registos do campo podem aceitar vários campos, um único campo ou são determinados por outros registos. As condições mín./máx. de **dataViewMapping** devem ser corretamente configuradas nas capacidades do elemento visual. |
| Remova todos os campos por ordens diferentes. | O elemento visual limpa de forma adequada os campos à medida que são removidos de forma arbitrária. Não existem erros na consola ou no browser. |
| Abra o painel **Formato** com cada configuração de registo possível. | Este teste não aciona exceções de referência nulas. |
| Filtre os dados com o painel **Filtro** ao nível do elemento visual, da página e do relatório. | As descrições estão corretas após a aplicação dos filtros. As descrições mostram o valor filtrado. |
| Filtre os dados com uma **Segmentação de Dados**. | As descrições estão corretas após a aplicação dos filtros. As descrições mostram o valor filtrado. |
| Filtre os dados com um elemento visual publicado. Por exemplo, selecione um setor do gráfico circular ou uma coluna. | As descrições estão corretas após a aplicação dos filtros. As descrições mostram o valor filtrado. |
| Se a filtragem cruzada for suportada, verifique se os filtros funcionam corretamente. | A seleção aplicada filtra outros elementos visuais nesta página do relatório. |
| Selecione com as teclas Ctrl, Alt e Shift. | Não ocorrem comportamentos inesperados. |
| Altere o **Modo de Visualização** para **Tamanho real**, **Ajustar à página** e **Ajustar à largura**. | As coordenadas do rato são precisas. |
| Redimensione o elemento visual. | O elemento visual reage corretamente ao redimensionamento. |
| Defina o tamanho do relatório para o mínimo. | Não há erros de apresentação. |
| Confirme que as barras de deslocamento funcionam corretamente. | As barras de deslocamento devem existir, se necessário. Verifique os tamanhos das barras de deslocamento. As barras de deslocamento não devem ser demasiado largas nem demasiado altas. A posição e o tamanho das barras de deslocamento devem estar de acordo com os outros elementos do elemento visual. Verifique se são necessárias barras de deslocamento para diferentes tamanhos do elemento visual. |
| Afixe o elemento visual num **Dashboard**. | O elemento visual deve ser apresentado corretamente. |
| Adicione várias versões do elemento visual a única página do relatório. | Todas as versões do elemento visual são apresentadas e funcionam corretamente. |
| Adicione várias versões do elemento visual a várias páginas do relatório. | Todas as versões do elemento visual são apresentadas e funcionam corretamente. |
| Alterne entre as páginas do relatório. | O elemento visual é apresentado corretamente. |
| Teste a Vista de leitura e a Vista de edição do elemento visual. | Todas as funções funcionam corretamente. |
| Se o elemento visual utilizar animações, adicione, altere e elimine elementos do elemento visual. | A animação dos elementos visuais funciona corretamente. |
| Abra o painel **Propriedade**. Ative ou desative as propriedades, introduza texto personalizado, sublinhe as opções disponíveis e insira dados inválidos. | O elemento visual responde corretamente. |
| Guarde o relatório e reabra-o. | Todas as definições das propriedades são mantidas. |
| Alterne as páginas no relatório e, em seguida, volte a alternar. | Todas as definições das propriedades são mantidas. |
| Teste toda a funcionalidade do elemento visual, incluindo as diferentes opções proporcionadas pelo elemento visual. | Todos os ecrãs e as funcionalidades funcionam corretamente. |
| Teste todos os tipos de dados numéricos, data e carateres, tal como nos testes seguintes. | Todos os dados estão devidamente formatados. |
| Reveja a formatação dos valores das descrições, das etiquetas dos eixos, das etiquetas de dados e de outros elementos visuais com formatação. | Todos os elementos estão formatados corretamente. |
| Verifique se as etiquetas de dados utilizam a cadeia de formato. | Todas as etiquetas de dados estão formatadas corretamente. |
| Ative e desative a formatação automática dos valores numéricos nas Descrições. | As descrições apresentam corretamente os valores. |
| Teste as entradas de dados com diferentes tipos de dados, incluindo numéricos, texto, data/hora e diferentes cadeias de formato do modelo. Teste diferentes volumes de dados, tais como milhares de linhas, uma linha e duas linhas. | Todos os ecrãs e as funcionalidades funcionam corretamente. |
| Introduza dados inválidos no elemento visual, tais como tipos de valores nulos, infinitos, negativos e incorretos. | Todos os ecrãs e as funcionalidades funcionam corretamente. |

## <a name="optional-browser-testing"></a>Teste opcional do browser

A equipa do AppSource valida o elemento visual nas versões mais recentes do Windows dos browsers Google Chrome, Microsoft Edge e Mozilla Firefox.
Opcionalmente, teste o elemento visual nos seguintes browsers.

| Caso de teste | Resultados esperados
| --------- | ----------------
| **Windows** |
| Google Chrome (versão anterior) | Todos os ecrãs e as funcionalidades funcionam corretamente. |
| Mozilla Firefox (versão anterior) | Todos os ecrãs e as funcionalidades funcionam corretamente. |
| Microsoft Edge (versão anterior) | Todos os ecrãs e as funcionalidades funcionam corretamente. |
| Microsoft Internet Explorer 11 (opcional) | Todos os ecrãs e as funcionalidades funcionam corretamente. |
| **macOS** |
| Chrome (versão anterior) | Todos os ecrãs e as funcionalidades funcionam corretamente. |
| Firefox (versão anterior) | Todos os ecrãs e as funcionalidades funcionam corretamente. |
| Safari (versão anterior) | Todos os ecrãs e as funcionalidades funcionam corretamente. |
| **Linux** |
| Firefox (versões mais recente e anterior) | Todos os ecrãs e as funcionalidades funcionam corretamente. |
| **iOS para Dispositivos Móveis** |
| iPad Apple Safari (versão anterior do Safari) | Todos os ecrãs e as funcionalidades funcionam corretamente. |
| iPad Chrome (versão mais recente do Safari) | Todos os ecrãs e as funcionalidades funcionam corretamente. |
| **Android Dispositivos Móveis** |
| Chrome (versões mais recente e anterior) | Todos os ecrãs e as funcionalidades funcionam corretamente. |

## <a name="desktop-testing"></a>Teste do ambiente de trabalho

Teste o elemento visual na versão atual do [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/).

| Caso de teste | Resultados esperados
| --------- | ----------------
| Teste todas as funcionalidades do elemento visual. | Todos os ecrãs e as funcionalidades funcionam corretamente. |
| Importe, guarde, abra um ficheiro e publique no serviço Web do Power BI com o botão **Publicar** do Power BI Desktop. | Todos os ecrãs e as funcionalidades funcionam corretamente. |
| Mude a cadeia de formato numérico para ter zero casas decimais ou três casas decimais ao aumentar ou diminuir a precisão. | O elemento visual é apresentado corretamente. |

## <a name="performance-testing"></a>Teste de desempenho

O elemento visual deve funcionar a um nível aceitável. Utilize ferramentas de programador para validar o desempenho. Não confie nas ajudas visuais nem nos registos de tempo da consola.

| Caso de teste | Resultados esperados
| --------- | ----------------
| Crie um elemento visual com muitos elementos visuais. | O elemento visual deve funcionar bem e não deve bloquear a aplicação. Não deve haver problemas de desempenho com elementos como a velocidade de animação, o redimensionamento, a filtragem e a seleção.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre o processo de publicação, veja [Publicar elementos visuais do Power BI no Centro de Parceiros](./office-store.md).

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/).
