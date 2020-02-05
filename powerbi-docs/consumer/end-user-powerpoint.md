---
title: Exportar relatórios do Power BI para o PowerPoint
description: Saiba como exportar um relatório do Power BI para o PowerPoint.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 12/04/2019
ms.author: mihart
LocalizationGroup: Share your work
ms.openlocfilehash: 25422b2503caed78e6e6518a855f6b23a0571a8c
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/04/2020
ms.locfileid: "74830542"
---
# <a name="export-reports-from-power-bi-to-powerpoint"></a>Exportar relatórios do Power BI para o PowerPoint

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Com o Power BI, pode publicar o seu relatório no Microsoft PowerPoint e criar facilmente um conjunto de diapositivos com base no seu relatório do Power BI. Quando exporta para o PowerPoint, acontece o seguinte:

* Cada página no relatório do Power BI torna-se um diapositivo no PowerPoint.
* Cada página no relatório do Power BI é exportada como uma só imagem de alta resolução no PowerPoint.
* Pode preservar as definições de filtragem e de segmentação de dados que adicionou ao relatório.
* É criada uma ligação no PowerPoint que direciona para o relatório do Power BI.

É rápido exportar o seu **relatório do Power BI** para o **PowerPoint**. Siga os passos descritos na secção seguinte.

## <a name="export-your-power-bi-report-to-powerpoint"></a>Exportar o seu relatório do Power BI para o PowerPoint
No **serviço Power BI**, selecione um relatório para apresentá-lo na tela. Também pode selecionar um relatório a partir do contentor **Página inicial**, **Aplicações** ou de qualquer outro contentor do painel de navegação.

Quando o relatório que pretende exportar para o PowerPoint for apresentado na tela, selecione **Exportar** > **PowerPoint** na barra de menus.

![Selecione Exportar na barra de menus](media/end-user-powerpoint/power-bi-export.png)

Será apresentado um pop-up onde terá a opção de selecionar **Valores atuais** ou **Valores predefinidos**. A opção **Valores atuais** exporta o relatório no estado atual, que inclui as alterações ativas que efetuou na segmentação de dados e nos valores de filtro. A maioria dos utilizadores seleciona esta opção. Em alternativa, selecionar a opção **Valores predefinidos** exporta o relatório no estado original (conforme partilhado pelo *designer*) e não reflete as alterações que tiver feito ao estado original.

> [!NOTE]
> A opção **Valores atuais** não inclui o estado de deslocamento dos elementos visuais.

![Selecione o que Exportar](media/end-user-powerpoint/power-bi-current-values.png)
 
Além disso, existe uma caixa de verificação para selecionar se quer exportar os separadores ocultos de um relatório. Selecione esta caixa de verificação se quiser exportar apenas os separadores do relatório que estiverem visíveis no seu browser. Se preferir incluir todos os separadores ocultos na exportação, mantenha esta caixa de verificação desselecionada. Se a caixa de verificação aparecer a cinzento, significa que não existem separadores ocultos no relatório. Um exemplo de separador oculto seria um separador de descrição. As [descrições personalizadas](../desktop-tooltips.md) são criadas por *designers* de relatórios e não são apresentadas como separadores de relatório no serviço Power BI para *consumidores*. 

Depois de fazer as suas seleções, selecione **Exportar** para continuar. Verá uma faixa de notificação no canto superior direito da janela de browser do serviço Power BI a informar que o relatório está a ser exportado para o PowerPoint. A exportação poderá demorar alguns minutos. Pode continuar a trabalhar no Power BI enquanto o relatório estiver a ser exportado.

![Notificação de exportação para o PowerPoint em curso](media/end-user-powerpoint/power-bi-export-progress.png)

Quando o serviço Power BI concluir o processo de exportação, a faixa de notificação será alterada para o informar. Quando isto acontecer, o seu ficheiro ficará disponível onde o browser mostra os ficheiros descarregados. Na imagem seguinte, é mostrado como faixa de transferência na parte inferior da janela do browser.

![notificação do browser, na parte inferior do ecrã](media/end-user-powerpoint/power-bi-browsers.png)

E é tudo. Pode transferir o ficheiro, abri-lo com o PowerPoint e, em seguida, modificar ou melhorá-lo tal como faria com qualquer outro conjunto de diapositivos do PowerPoint.

## <a name="check-out-your-exported-powerpoint-file"></a>Consultar o ficheiro do PowerPoint exportado
Quando abrir o ficheiro PowerPoint que o Power BI exportou, tem alguns elementos úteis à disposição. Veja a seguinte imagem e consulte os elementos numerados que descrevem algumas destas funcionalidades úteis.

![o PowerPoint é aberto](media/end-user-powerpoint/power-bi-powerpoint.png)

1. A primeira página do conjunto de diapositivos inclui o nome do seu relatório e uma ligação que lhe permite **Ver no Power BI** o relatório no qual o conjunto de diapositivos se baseia.
2. Também obterá algumas informações úteis sobre o relatório. **Última atualização dos dados** mostra a data e hora em que o relatório exportado se baseia. **Transferido às** mostra a data e hora em que o relatório do Power BI foi exportado para um ficheiro do PowerPoint.
3. Cada página do relatório é um diapositivo diferente, conforme apresentado no painel de navegação. 
4. O relatório publicado é composto no idioma das suas definições do Power BI ou da definição de região do seu browser. Para ver ou definir a sua preferência de idioma, selecione o ícone de engrenagem ![Ícone de Engrenagem](media/end-user-powerpoint/power-bi-settings-icon.png) > **Definições** > **Geral** > **Idioma**. Para obter informações sobre a região, veja [Idiomas e países/regiões com suporte no Power BI](../supported-languages-countries-regions.md).


Quando aceder a um diapositivo individual, verá que cada página do relatório é uma imagem diferente.

![Ecrã a mostrar cada elemento visual como uma imagem separada](media/end-user-powerpoint/power-bi-images.png)

A partir daí, pode fazer o que quiser com o conjunto do PowerPoint ou com as imagens de alta resolução.

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
Existem algumas considerações e limitações a ter em conta ao trabalhar com a funcionalidade **Exportar para o PowerPoint**.

* Os elementos visuais de R não são atualmente suportados. Estes elementos visuais são exportados como imagens em branco para o PowerPoint, com uma mensagem de erro a indicar que o elemento visual não é suportado.
* Os elementos visuais personalizados que tiverem sido certificados são suportados. Para obter mais informações sobre os elementos visuais personalizados certificados, incluindo como certificar um elemento visual, veja [Certificar um elemento visual personalizado](../developer/power-bi-custom-visuals-certified.md). Não são suportados elementos visuais personalizados que não tenham sido certificados. Estes serão exportados como imagens em branco para o PowerPoint, com uma mensagem de erro a indicar que o elemento visual não é suportado.
* Atualmente, não pode exportar relatórios com mais de 30 páginas.
* Os elementos visuais com barras de deslocamento são exportados no respetivo estado predefinido. O elemento visual no PowerPoint mostrará apenas a parte superior dos dados. O deslocamento no PowerPoint não está disponível, dado que cada diapositivo é uma imagem. 
* O processo de exportar o relatório para o PowerPoint poderá demorar alguns minutos, pelo que pedimos que seja paciente. Os fatores que podem afetar o tempo necessário incluem a estrutura do relatório e a carga atual no serviço Power BI.
* Se o item de menu **Exportar para PowerPoint** não estiver disponível no serviço Power BI, é provável que o seu administrador de inquilinos tenha desativado a funcionalidade. Contacte o seu administrador de inquilinos para obter informações.
* As imagens de fundo serão recortadas de acordo com a área delimitadora do gráfico. Recomendamos que remova as imagens de fundo antes de exportar para o PowerPoint.
* As páginas no PowerPoint são sempre criadas no tamanho padrão de 9:16, independentemente dos tamanhos ou dimensões de página originais no relatório do Power BI.
* Os relatórios pertencentes a um utilizador fora do seu domínio de inquilino do Power BI (por exemplo, um relatório pertencente a alguém fora da sua organização e partilhado consigo) não podem ser publicados no PowerPoint.
* Se partilhar um dashboard com alguém fora da sua organização (e, portanto, um utilizador que não está no seu inquilino do Power BI), esse utilizador não poderá exportar os relatórios associados do dashboard partilhado para o PowerPoint. Por exemplo, se for aaron@contoso.com, pode partilhar com david@cohowinery.com. No entanto, david@cohowinery.com não poderá exportar os relatórios associados para o PowerPoint.
* A exportação poderá não funcionar com versões mais antigas do PowerPoint.
* Como anteriormente mencionado, cada página do relatório é exportada como uma imagem única no ficheiro do PowerPoint.
* O serviço Power BI utiliza a sua definição de idioma do Power BI como o idioma da exportação do PowerPoint. Para ver ou definir a sua preferência de idioma, selecione o ícone de engrenagem ![Ícone de Engrenagem](media/end-user-powerpoint/power-bi-settings-icon.png) > **Definições** > **Geral** > **Idioma**.
* A hora em **Transferido às** no diapositivo da capa do ficheiro PowerPoint exportado está definida para o fuso horário do seu computador na altura da exportação.
* Os filtros de URL não são atualmente respeitados quando seleciona **Valores Atuais** na exportação.

## <a name="next-steps"></a>Próximos passos
[Imprimir um relatório](end-user-print.md)
