---
title: "Exportar relatórios do Power BI para o PowerPoint (Pré-visualização)"
description: "Saiba como exportar um relatório do Power BI para o PowerPoint."
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: complete
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: ec5d5de3d29ccbe857f6fd40320353c357e6539e
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2017
---
# <a name="export-reports-from-power-bi-to-powerpoint-preview"></a>Exportar relatórios do Power BI para o PowerPoint (Pré-visualização)
Com o Power BI, já pode publicar o seu relatório no **Microsoft PowerPoint** e criar facilmente um conjunto de diapositivos com base no seu relatório do Power BI. Quando **exportar para o PowerPoint**, acontece o seguinte:

* Cada página no relatório do Power BI torna-se um diapositivo no PowerPoint
* Cada visual no relatório do Power BI é exportado como uma imagem de alta resolução no PowerPoint
* As caixas de texto no relatório do Power BI tornam-se caixas editáveis no PowerPoint
* É criada uma ligação no PowerPoint que direciona para o relatório do Power BI

É fácil exportar o seu **relatório do Power BI** para o **PowerPoint**. Basta seguir os passos enumerados na secção seguinte.

## <a name="how-to-export-your-power-bi-report-to-powerpoint"></a>Como exportar o seu relatório do Power BI para o PowerPoint
No serviço Power BI, selecione a secção **Relatórios** no painel de navegação à esquerda para expandir essa secção e, em seguida, selecione o seu relatório para apresentá-lo na tela. Também pode selecionar um relatório da secção **A Minha Área de Trabalho** ou dos seus **Favoritos**, se o relatório estiver num destes locais.

![](media/service-publish-to-powerpoint/powerbi_to_powerpoint_0.png)

Quando o relatório que pretende exportar para o PowerPoint for apresentado na tela, selecione **Ficheiro > Exportar para o PowerPoint (Pré-visualização)** a partir da barra de menus no serviço Power BI, conforme apresentado na imagem seguinte.

![](media/service-publish-to-powerpoint/powerbi_to_powerpoint_1.png)

Irá ver uma faixa de notificação no canto superior direito da janela de browser do serviço Power BI a informar que o relatório está a ser exportado para o PowerPoint. Poderão demorar alguns minutos e pode continuar a trabalhar no Power BI enquanto o relatório estiver a ser exportado.

![](media/service-publish-to-powerpoint/powerbi_to_powerpoint_2.png)

Quando a exportação for concluída, a faixa de notificação será alterada para informar que o serviço Power BI concluiu o processo de exportação.

![](media/service-publish-to-powerpoint/powerbi_to_powerpoint_3.png)

Quando isto acontecer, o seu ficheiro ficará disponível onde o browser mostra os ficheiros descarregados. Na imagem seguinte, é mostrado como faixa de transferência na parte inferior da janela do browser.

![](media/service-publish-to-powerpoint/powerbi_to_powerpoint_4.png)

E é tudo. Pode transferir o ficheiro, abri-lo com o PowerPoint e, em seguida, modificá-lo ou melhorá-lo tal como faria com outro conjunto do PowerPoint.

## <a name="checking-out-your-exported-powerpoint-file"></a>Consultar o ficheiro PowerPoint exportado
Quando abrir o ficheiro PowerPoint que o Power BI exportou, tem alguns elementos úteis à disposição. Veja a imagem seguinte e consulte os elementos numerados abaixo que descrevem algumas destas funcionalidades úteis.

![](media/service-publish-to-powerpoint/powerbi_to_powerpoint_5.png)

1. A primeira página do conjunto de diapositivos inclui o nome do seu relatório e uma ligação que lhe permite **Ver no Power BI** o relatório no qual o conjunto de diapositivos se baseia.
2. Obtém também algumas informações úteis sobre o relatório, incluindo a *última atualização de dados* na qual o relatório exportado se baseia e a data e hora de *transferência*, que corresponde à data e hora em que o relatório do Power BI foi exportado para um ficheiro PowerPoint.
3. Cada página do relatório é um diapositivo diferente, conforme apresentado no painel de navegação à esquerda.

Quando aceder a um diapositivo individual, irá reparar que cada visual é uma imagem diferente (conforme mencionado anteriormente). Desta forma, pode copiar essa imagem e colá-la noutro diapositivo ou noutro local que prefira.

![](media/service-publish-to-powerpoint/powerbi_to_powerpoint_6.png)

O que fazer com o conjunto do PowerPoint a partir daí, ou com as imagens de alta resolução, é decisão sua!

## <a name="limitations"></a>Limitações
Há algumas considerações e limitações a ter em conta ao trabalhar com a funcionalidade **Exportar para o PowerPoint**.

* Os **visuais R** não são atualmente suportados. Estes visuais são exportados como imagem em branco para o PowerPoint com uma mensagem de erro a indicar que o visual não é suportado.
* Os **visuais personalizados** que tenham sido **certificados** são suportados. Para obter mais informações sobre visuais personalizados certificados, incluindo como certificar um visual personalizado, consulte [certificar um visual personalizado](power-bi-custom-visuals-certified.md). Os visuais personalizados que não tenham sido certificados não são suportados, sendo exportados como imagem em branco para o PowerPoint com uma mensagem de erro a indicar que o visual não é suportado.
* Os **visuais personalizados certificados** são suportados. Foi aprovado um visual personalizado certificado para utilização com o Power BI, que cumpre determinados requisitos de código e passou testes de segurança exigentes. [Saiba mais sobre os **visuais personalizados certificados**](power-bi-custom-visuals-certified.md).
* Atualmente, não é possível exportar relatórios com mais de 15 páginas de relatório.
* O processo de exportar o relatório para o PowerPoint pode demorar alguns minutos, pelo que pedimos que seja paciente. Os fatores que podem afetar o tempo necessário incluem a estrutura do relatório e a carga atual no serviço Power BI.
* Se o item de menu **Exportar para PowerPoint (Pré-visualização)** não estiver disponível no serviço Power BI, tal pode dever-se ao facto de o seu administrador de inquilino ter desativado a funcionalidade. Contacte o seu administrador de inquilino para obter informações.
* As imagens de fundo serão recortadas com a área delimitadora do gráfico. Recomenda-se vivamente que remova as imagens de fundo antes de exportar para o PowerPoint.
* A **Interatividade em sessão**, como realçar e filtrar, desagregar, entre outros, ainda não é suportada ao exportar para o PowerPoint. O PowerPoint exportado mostra os visuais originais conforme estes foram guardados no relatório.
* As páginas no PowerPoint são sempre criadas no tamanho padrão de 9:16, independentemente dos tamanhos ou dimensões de página originais no relatório do Power BI.
* Os relatórios pertencentes a um utilizador fora do seu domínio de inquilino do Power BI (por exemplo, um relatório pertencente a alguém fora da sua organização e partilhado consigo) não podem ser publicados no PowerPoint.
* Se partilhar um dashboard com alguém fora da sua organização (e, portanto, um utilizador que não esteja no seu inquilino do Power BI), esse utilizador já não poderá exportar os relatórios associados do dashboard partilhado para o PowerPoint. Por exemplo, se for aaron@contoso.com, pode partilhar com david@cohowinery.com. No entanto, david@cohowinery.com não pode exportar os relatórios associados para o PowerPoint.

## <a name="next-steps"></a>Passos seguintes
[Analisar no Excel](service-analyze-in-excel.md)

[Dados do Excel no Power BI](service-excel-workbook-files.md)

[Obter um visual personalizado certificado](power-bi-custom-visuals-certified.md)
