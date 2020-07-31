---
title: Utilizar ferramentas externas no Power BI (pré-visualização)
description: Expandir a utilização do Power BI Desktop com ferramentas externas
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/24/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: c1d483b6a29d2463af05cd224ac6b03dd149eb33
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/28/2020
ms.locfileid: "87252895"
---
# <a name="using-external-tools-in-power-bi-desktop-preview"></a>Utilizar ferramentas externas no Power BI Desktop (pré-visualização)

A partir do lançamento de julho de 2020 do Power BI Desktop, pode utilizar ferramentas externas para proporcionar valor e funcionalidades adicionais ao Power BI Desktop. O suporte a ferramentas externas permite-lhe tirar partido do vasto leque de ferramentas da comunidade para o Analysis Services para profissionais de BI, tais como a otimização e a criação de expressões/consultas DAX, e da gestão do ciclo de vida das aplicações (ALM).

O friso **Ferramentas Externas** no Power BI Desktop contém botões para ferramentas externas instaladas no computador e registadas no Power BI Desktop. As ferramentas externas lançadas no Power BI Desktop estão automaticamente ligadas ao motor do Analysis Services, que funciona como parte do Power BI Desktop e proporcionam uma experiência perfeita aos utilizadores.

![Friso das ferramentas externas no Power BI Desktop](media/desktop-external-tools/desktop-external-tools-01.png)

Estas ferramentas externas em destaque incluem as seguintes, com ligações à sua localização de instalação. Cada ferramenta externa é suportada pelos respetivos autores:

* [Tabular Editor](https://tabulareditor.com/)
* [DAX Studio](https://daxstudio.org)
* [ALM Toolkit](http://alm-toolkit.com)


As seguintes secções descrevem as operações suportadas pelas ferramentas externas, uma lista de ferramentas em destaque incluídas no Power BI Desktop e instruções sobre como registar ferramentas adicionais.

## <a name="supported-write-operations"></a>Operações de escrita suportadas

As ferramentas externas podem ligar-se ao conjunto de dados do Power BI Desktop (modelo do Analysis Services) para editar os seguintes objetos. A edição de um ficheiro de modelo do Power BI Desktop (PBIT) não é suportada.

* [Medidas](https://docs.microsoft.com/analysis-services/tabular-models/measures-ssas-tabular) para os cálculos
* [Grupos de cálculo](https://docs.microsoft.com/analysis-services/tabular-models/calculation-groups) para a reutilização de cálculos em modelos complexos
* As [Perspetivas](https://docs.microsoft.com/analysis-services/tabular-models/perspectives-ssas-tabular) para definir vistas dos metadados dos conjuntos de dados específicas do domínio empresarial em destaque

A gestão de traduções de metadados através de ferramentas externas pode ser possível, mas não é suportada atualmente nesta versão de pré-visualização. Se a região do utilizador atual for uma região com tradução, a edição de objetos na lista de campos não funcionará corretamente com a versão atual do Power BI Desktop. 

Há um problema conhecido quando cria relatórios em modelos que têm grupos de cálculo definidos. Se o grupo de cálculo definir uma formatação dinâmica dependendo do cálculo/medida selecionado, essa formatação só estará atualmente disponível nos elementos visuais da tabela, matriz e cartão.

Todos os metadados do conjunto de dados [Modelo de Objeto em Tabela](https://docs.microsoft.com/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo) podem ser acedidos apenas para fins de leitura, mas os objetos não abrangidos pela lista descrita no artigo [Modelo de Objeto em Tabela](https://docs.microsoft.com/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo) ainda não são suportados para edição na instância do Analysis Services do Power BI Desktop.


## <a name="featured-external-tools"></a>Ferramentas externas em destaque

As seguintes ferramentas open-source da comunidade funcionam com o Power BI Desktop. São suportadas pelos respetivos autores. O respetivo instalador de cada ferramenta regista-a no Power BI Desktop após a instalação:

* Tabular Editor
* DAX Studio
* ALM Toolkit

Vamos abordar cada uma dessas ferramentas, caso a caso.

### <a name="tabular-editor"></a>Tabular Editor

Pode instalar o [Tabular Editor](https://tabulareditor.com/) a partir da seguinte ligação: [Site do Tabular Editor](https://tabulareditor.com/)

O Tabular Editor permite aos profissionais de BI criar, manter e gerir facilmente modelos tabulares através de um editor intuitivo e leve. Uma vista hierárquica mostra todos os objetos no modelo tabular, organizados por pastas de apresentação com suporte para edição de propriedades de seleção múltipla e realce da sintaxe DAX.

![Captura de ecrã do Tabular Editor](media/desktop-external-tools/desktop-external-tools-02.png)

O código de origem do Tabular Editor pode ser encontrado no seguinte repositório GitHub: [Tabular Editor no GitHub](https://github.com/otykier/TabularEditor)

O autor da ferramenta principal do Tabular Editor é [Daniel Otykier](https://www.linkedin.com/in/daniel-otykier-2231876).


### <a name="dax-studio"></a>DAX Studio

Pode instalar o [DAX Studio](https://daxstudio.org) a partir da seguinte ligação: [Site do DAX Studio](https://daxstudio.org)

O DAX Studio é conhecido por ser uma ferramenta completa para a criação, o diagnóstico, a otimização do desempenho e a análise DAX. As funcionalidades incluem navegação de objetos, rastreio integrado, discriminações de execução de consultas com estatísticas detalhadas, realce da sintaxe e formatação DAX. A imagem seguinte mostra um ecrã do DAX Studio. 

![Captura de ecrã do DAX Studio](media/desktop-external-tools/desktop-external-tools-03.png)

O código de origem do DAX Studio pode ser encontrado no seguinte repositório GitHub: [DAX Studio no GitHub](https://github.com/DaxStudio/DaxStudio)

O autor da ferramenta principal do DAX Studio é [Darren Gosbell](https://www.linkedin.com/in/darrengosbell).

### <a name="alm-toolkit"></a>ALM Toolkit

Pode instalar o [ALM Toolkit](http://alm-toolkit.com) a partir da seguinte ligação: [Site do ALM Toolkit](http://alm-toolkit.com)

O ALM Toolkit é uma ferramenta de comparação de esquemas para conjuntos de dados do Power BI, utilizado para cenários de gestão de ciclos de vida das aplicações (ALM). Com esta ferramenta, pode implementar diretamente em vários ambientes e reter dados históricos de atualizações incrementais. Com o ALM Toolkit, pode diferenciar e intercalar ficheiros, ramos e repositórios de metadados. Também pode reutilizar definições comuns entre conjuntos de dados.

![Captura de ecrã do ALM Toolkit](media/desktop-external-tools/desktop-external-tools-04.png)

O código de origem do ALM Toolkit pode ser encontrado no seguinte repositório GitHub: [ALM Toolkit no GitHub](https://github.com/microsoft/analysis-services)

O autor da ferramenta principal do ALM Toolkit é [Christian Wade](https://www.linkedin.com/in/christianwade1).


## <a name="how-to-register-external-tools"></a>Como registar ferramentas externas

Para registar outras ferramentas externas no Power BI Desktop, crie um ficheiro JSON com o seguinte conteúdo:

```json
{
    "name": "<tool name>",
    "description": "<tool description>",
    "path": "<tool executable path>",
    "arguments": "<optional command line arguments>",
    "iconData": "image/png;base64,<encoded png icon data>"
}
```

A seguinte lista descreve a lista de elementos do ficheiro JSON:
 
* **nome:** introduza um nome para a ferramenta, que aparecerá como uma legenda de botão no friso Ferramentas Externas dentro do Power BI Desktop.
* **descrição:** (opcional) introduza uma descrição, que aparecerá como uma descrição no botão do friso Ferramentas Externas dentro do Power BI Desktop.
* **caminho:** introduza o caminho totalmente qualificado para a ferramenta executável.
* **argumentos:** (opcional) introduza uma cadeia de argumentos da linha de comandos com os quais a ferramenta executável deve ser iniciada. Pode utilizar qualquer um dos seguintes marcadores de posição:
    * **%server%:** Substituído pelo nome do servidor e número de porta da instância local da Tabela do Analysis Services para modelos de dados importados/DirectQuery.
    * **%database%:** substituído pelo nome da base de dados do modelo alojado na instância local da Tabela do Analysis Services para modelos de dados importados/DirectQuery.
* **iconData:** introduza os dados das imagens, que serão compostos como um ícone de botão no friso Ferramentas Externas dentro do Power BI Desktop. A cadeia deve ser formatada de acordo com a sintaxe dos URIs de Dados sem o prefixo “dados:”.
 
Atribua um nome ao ficheiro `"<tool name>.pbitool.json"` e coloque-o na seguinte pasta:

* `%commonprogramfiles%\Microsoft Shared\Power BI Desktop\External Tools`

Em ambientes de 64 bits, coloque os ficheiros na seguinte pasta:

* **Programas (x86)\Common Files\Microsoft Shared\Power BI Desktop\External Tools**

Os ficheiros nessa localização especificada com a extensão **.pbitool.json** são carregados pelo Power BI Desktop no arranque.

## <a name="disabling-external-tools-using-the-registry"></a>Desativar ferramentas externas através do registo

As Ferramentas Externas podem ser desativadas através das **Políticas de Grupo** ou ao editar o registo, que é semelhante ao processo de desativação dos  **Elementos Visuais Personalizados**.

    Registry key: ```Software\Policies\Microsoft\Power BI Desktop\```

    Registry value: ```EnableExternalTools```

Um valor de 1 (decimal) ativa a utilização de ferramentas externas do Power BI no Power BI, que é o valor predefinido.

Um valor de 0 (decimal) desativa a utilização de ferramentas externas no Power BI.


## <a name="next-steps"></a>Próximos passos

Poderá também estar interessado nos seguintes artigos:

* [Utilizar a pormenorização de relatórios cruzados em relatórios do Power BI](desktop-cross-report-drill-through.md)
* [Utilizar a segmentação de dados no Power BI Desktop](../visuals/power-bi-visualization-slicers.md)


