---
title: Vista de Relatório no Power BI Desktop
description: Vista de Relatório no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/13/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: a840a549e5dee79406ddfb2a07877895ce7b6c0f
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79206798"
---
# <a name="work-with-report-view-in-power-bi-desktop"></a>Trabalhar com a Vista de Relatório no Power BI Desktop

Se já trabalhou com o Power BI, sabe como é fácil criar relatórios que fornecem informações e perspetivas dinâmicas sobre os seus dados. O Power BI também conta com funcionalidades mais avançadas no Power BI Desktop. Com o Power BI Desktop, cria consultas avançadas, realiza mashup dos dados provenientes de várias origens, cria relações entre tabelas e muito mais.

O Power BI Desktop inclui uma *Vista de relatório*, onde pode criar as páginas de relatório que quiser com visualizações. A vista de relatório no Power BI Desktop permite uma experiência de design semelhante à da vista de edição do relatório no *serviço Power BI*. Pode mover as visualizações de um lado para o outro, copiar e colar, unir, etc.

A diferença é que ao utilizar o Power BI Desktop, pode trabalhar com as suas consultas e modelar os seus dados para certificar-se que os seus dados suportam as melhores informações nos seus relatórios. Então pode guardar o seu ficheiro do Power BI Desktop onde quiser, quer seja na sua unidade local ou na cloud.

## <a name="lets-take-a-look"></a>Vamos dar uma olhadela!

Quando carrega dados pela primeira vez no Power BI Desktop, verá a Vista de relatório em branco.

![Power BI Desktop](media/desktop-report-view/pbi_reportviewinpbidesigner_reportview.png)

Pode alternar entre as vistas **Relatório**, **Dados** e **Relações** ao selecionar os ícones no painel de navegação esquerdo:

![Ícone da vista de relatório](media/desktop-report-view/pbi_reportviewinpbidesigner_changeview.png)

Depois de adicionar alguns dados, pode adicionar campos a uma nova visualização na tela.

![Adicionar um elemento visual ao arrastar do painel Campos](media/desktop-report-view/pbid_reportview_addvis.gif)

Para alterar o tipo de visualização, pode selecioná-lo na tela e, em seguida, selecionar um novo tipo em **Visualizações**.

![Alterar um elemento visual ao selecionar um novo](media/desktop-report-view/pbid_reportview_changevis.gif)

> [!TIP]
> Certifique-se de que experimenta diferentes tipos de visualização. É importante que a visualização transmita com clareza as informações presentes nos dados.

Um relatório terá pelo menos uma página em branco inicialmente. As páginas são apresentadas no painel do navegador à esquerda da tela. Pode adicionar todos os tipos de visualizações a uma página, mas é importante não exagerar. Se existirem visualizações em excesso numa página, poderá fazer com que pareça demasiado cheia e dificultar a localização das informações corretas. Pode adicionar novas páginas ao seu relatório. Basta clicar em **Nova Página** no friso.

![Ícone de nova página](media/desktop-report-view/pbidesignerreportviewnewpage.png)

Para eliminar uma página, clique em **X** no separador da página na parte inferior da Vista de relatório.

![Adicionar uma página a um relatório](media/desktop-report-view/pbi_reportviewinpbidesigner_deletepage.png)

> [!NOTE]
> Não pode afixar relatórios e visualizações num dashboard a partir do Power BI Desktop. Para o fazer, precisará de publicar no seu site do Power BI. Para obter mais informações, veja [Publicar conjuntos de dados e relatórios a partir do Power BI Desktop](desktop-upload-desktop-files.md).

## <a name="copy-and-paste-between-reports"></a>Copiar e colar entre relatórios

Pode facilmente copiar um elemento visual de um relatório do Power BI Desktop e colá-lo noutro relatório. Basta utilizar o atalho de teclado CTRL+C para copiar o elemento visual do relatório. No outro relatório do Power BI Desktop, utilize Ctrl+V para colar o elemento visual no outro relatório. Pode selecionar um elemento visual de cada vez ou todos os elementos visuais numa página para copiar e, em seguida, colar no relatório do Power BI Desktop de destino.

A capacidade de copiar e colar os elementos visuais é útil para quem cria e atualiza vários relatórios com frequência. Quando copia entre ficheiros, as definições e a formatação que tiverem sido explicitamente definidas no painel de formatação serão transportadas, enquanto os elementos visuais que dependem de um tema ou das definições predefinidas são automaticamente atualizados para corresponder ao tema do relatório de destino. Por isso, quando receber um elemento visual formatado e com o aspeto pretendido, pode copiar e colar esse elemento visual em novos relatórios e preservar todo o bom trabalho de formatação.

Se os campos do seu modelo forem diferentes, verá um erro no elemento visual e um aviso sobre os campos que não existem. O erro é semelhante à experiência que é apresentada quando elimina um campo no modelo que um elemento visual está a utilizar.

![Erro ao copiar/colar elemento visual – nenhum campo de dados](media/desktop-report-view/report-view_07.png)

Para corrigir o erro, basta substituir os campos com problemas pelos campos do modelo que quer utilizar no relatório em que colou o elemento visual. Se estiver a utilizar um elemento visual personalizado, também terá de importar esse elemento visual personalizado para o relatório de destino.

## <a name="hide-report-pages"></a>Ocultar páginas do relatório

Quando cria relatórios, também pode ocultar as páginas de um relatório. Esta abordagem poderá ser útil se precisar de criar dados subjacentes ou elementos visuais num relatório, mas não quiser que essas páginas estejam visíveis para outras pessoas, por exemplo, quando criar tabelas ou elementos visuais de suporte que são utilizados nas páginas de outros relatórios. Existem muitos outros motivos criativos pelos quais pode querer criar uma página do relatório e, em seguida, ocultá-la de um relatório que quer publicar.

É fácil ocultar uma página do relatório. Basta clicar com o botão direito do rato no separador da página do relatório e selecionar **Ocultar** no menu apresentado.

![Opção Ocultar página](media/desktop-report-view/report-view_05.png)

Deve ter em conta as seguintes considerações quando ocultar uma página de relatório:

* Ainda poderá ver uma vista do relatório oculta quando estiver no Power BI Desktop, apesar de o título da página estar desativado. Na imagem seguinte, a Página 4 foi ocultada.

    ![página oculta a cinzento](media/desktop-report-view/report-view_06.png)

* *Não poderá* ver uma página do relatório oculta quando visualizar o relatório no serviço Power BI.

* Ocultar uma página do relatório *não* é uma medida de segurança. A página ainda pode ser acedida por utilizadores e o seu conteúdo continua acessível através da exploração e de outros métodos.

* Quando uma página está oculta e estiver no Modo de visualização, não são apresentadas as setas de navegação do modo de visualização.
