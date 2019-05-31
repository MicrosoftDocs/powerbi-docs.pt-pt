---
title: Incorporar um relatório num site ou portal seguro
description: O Power BI incorpora a funcionalidade permite aos utilizadores facilmente e com segurança incorporar relatórios em portais da web internos.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
LocalizationGroup: Share your work
ms.openlocfilehash: bf9d7bcdf6ddaf7d0063843a5314233989b2dadd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222246"
---
# <a name="embed-a-report-in-a-secure-portal-or-website"></a>Incorporar um relatório num site ou portal seguro

Com o novo **incorporação** relatórios de opção para o Power BI, pode facilmente e com segurança incorporar relatórios em portais da web interno. Podem ser estes portais **baseado na nuvem** ou **alojadas no local**, como o SharePoint 2019. Todos os itens permissões e segurança de dados por meio de respeitam a relatórios incorporados [ao nível da linha (RLS) de segurança](service-admin-rls.md). Eles fornecem sem código de incorporação em qualquer portal que aceita um URL ou um iFrame. 

O **incorporação** opção suporta [filtros de URL](service-url-filters.md) e definições de URL. Ele permite-lhe integrar portais usando uma abordagem de codificação reduzida que requerem apenas conhecimento HTML e JavaScript básico.

## <a name="how-to-embed-power-bi-reports-into-portals"></a>Como **Incorporar** relatórios do Power BI em portais

1. A nova opção **Incorporar** está disponível no menu **Ficheiro** para relatórios no serviço Power BI.

    ![Opção de menu pendente da opção Incorporar segura](media/service-embed-secure/secure-embed-drop-down-menu.png)

2. Selecione o **incorporação** opção de abrir uma caixa de diálogo que fornece uma ligação e um iFrame, pode usar para incorporar o relatório de forma segura.

    ![Caixa de diálogo da opção Incorporar](media/service-embed-secure/secure-embed-code-dialog.png)

3. Se um utilizador abre um URL de relatório diretamente ou um incorporada num web portal, o acesso de relatório requer autenticação. É apresentado o ecrã seguinte se um utilizador não iniciou sessão no Power BI na sua sessão de browser. Quando seleciona **início de sessão**, foi possível abrir uma nova janela do browser ou separador. Tê-los a verificar a existência de fatores que impedem a pop-up se eles não recebe o pedido para iniciar sessão.

    ![Iniciar sessão para ver este relatório](media/service-embed-secure/secure-embed-sign-in.png)

4. Depois do utilizador tem sessão iniciada, o relatório é aberto, mostrando os dados e permitindo a navegação de página e a definição de filtro. Apenas os utilizadores que têm permissão de visualização, podem ver o relatório no Power BI. Todos os [ao nível da linha (RLS) de segurança](service-admin-rls.md) também são aplicadas as regras. Por último, o utilizador tem de estar licenciado corretamente, seja porque precisa de uma licença do Power BI Pro ou porque o relatório tem de estar numa área de trabalho que esteja numa capacidade do Power BI Premium. O utilizador tem de iniciar sessão sempre que abrem uma nova janela do browser. No entanto, depois de iniciar sessão, outros relatórios carregado automaticamente.

    ![Incorporar relatório](media/service-embed-secure/secure-embed-report.png)

5. Ao usar um iFrame, poderá ter de editar a **altura** e **largura** para que ela se encaixe na página da web do seu portal.

    ![Definir altura e largura](media/service-embed-secure/secure-embed-size.png)

## <a name="granting-report-access"></a>Conceder acesso de relatório

O **incorporação** opção automaticamente não permite aos utilizadores ver o relatório. Ver permissões são definidas no serviço Power BI.

No serviço Power BI, pode partilhar relatórios incorporados com utilizadores que necessitam de acesso. Se estiver a utilizar um grupo do Office 365, pode listar o utilizador como membro da área de trabalho de aplicação. Para obter mais informações, consulte como [gerir a sua área de trabalho de aplicação no Power BI e do Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md).

## <a name="licensing"></a>Licensing

Para ver o relatório incorporado, os utilizadores precisam de qualquer uma licença do Power BI Pro ou os conteúdos precisam de estar numa área de trabalho que está numa [capacidade do Power BI Premium (EM ou P SKU)](service-admin-premium-purchase.md).

## <a name="customize-your-embed-experience-using-url-settings"></a>Personalizar a experiência de incorporação com definições de URL

Pode personalizar a experiência do usuário com as definições de entrada o URL de incorporação. Em iFrame fornecido, pode atualizar o URL **src** definições.

| Propriedade  | Descrição  |  |  |  |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|---|
| pageName  | Pode utilizar o **pageName** consultar o parâmetro de cadeia de caracteres para definir qual página de relatório para abrir. Pode encontrar este valor no final do URL do relatório ao visualizar um relatório no serviço Power BI, conforme mostrado abaixo. |  |  |  |
| Filtros de URL  | Pode usar [filtros de URL](service-url-filters.md) no URL de incorporação que recebeu da interface do Usuário do Power BI para filtrar o conteúdo de incorporação. Desta forma, pode criar integrações de código reduzido tendo apenas experiência básica de HTML e JavaScript.  |  |  |  |

## <a name="set-which-page-opens-for-an-embedded-report"></a>Conjunto a página que abre-se para um relatório incorporado 

Pode encontrar os **pageName** valor no final do URL do relatório ao visualizar um relatório no serviço Power BI.

1. Abra o relatório a partir do serviço Power BI no seu navegador da web e, em seguida, copie o URL da barra de endereço.

    ![Secção Relatório](media/service-embed-secure/secure-embed-report-section.png)

2. Anexe a definição **pageName** ao URL.

    ![Anexar pageName](media/service-embed-secure/secure-embed-append-page-name.png)

## <a name="filter-report-content-using-url-filters"></a>Filtrar conteúdo do relatório com filtros de URL 

Pode usar [filtros de URL](service-url-filters.md) para fornecer vistas de relatório diferente. Por exemplo, o URL abaixo filtra o relatório para mostrar dados do setor da Energia.

A utilização da combinação de **pageName** e [Filtros de URL](service-url-filters.md) pode ser eficiente. Pode criar experiências com HTML e JavaScript básicos.

Por exemplo, aqui está um botão, que pode adicionar a uma página HTML:

```html
<button class="textLarge" onclick='show("ReportSection", "Energy");' style="display: inline-block;">Show Energy</button>
```

Quando selecionada, o botão chama uma função para atualizar a iFrame com um URL atualizada, o que inclui o filtro de setor da energia.

```javascript
function show(pageName, filterValue)

{

var newUrl = baseUrl + "&pageName=" + pageName;

if(null != filterValue && "" != filterValue)

{

newUrl += "&$filter=Industries/Industry eq '" + filterValue + "'";

}

//Assumes there’s an iFrame on the page with id=”iFrame”

var report = document.getElementById("iFrame")

report.src = newUrl;

}
```

![Filtrar](media/service-embed-secure/secure-embed-filter.png)

Pode adicionar quantos botões quiser para criar uma experiência personalizada com código reduzido. 

## <a name="considerations-and-limitations"></a>Considerações e limitações

* Não suporta utilizadores convidados externos com a capacidade empresa-empresa (B2B) do Azure.

* A incorporação segura funciona para os relatórios publicados no serviço Power BI.

* O utilizador tem de iniciar sessão ver o relatório, sempre que abrirem uma nova janela do browser.

* Alguns browsers requerem que Atualize a página após o início de sessão, especialmente quando se utilizam modos InPrivate ou Incognito.

* Para obter uma experiência de início de sessão único, utilize a incorporação no SharePoint Online opção ou crie uma utilizando a integração personalizada a [utilizador detém os dados](developer/embed-sample-for-your-organization.md) incorporar o método. 

* A capacidade de autenticação automática fornecida com a opção **Incorporar** não funciona com a API de JavaScript do Power BI. Para a API de JavaScript do Power BI, utilize o [utilizador detém os dados](developer/embed-sample-for-your-organization.md) incorporar o método. 

## <a name="next-steps"></a>Próximos passos

* [Formas de partilhar o seu trabalho no Power BI](service-how-to-collaborate-distribute-dashboards-reports.md)

* [Filtrar um relatório com parâmetros de cadeia de caracteres de consulta no URL](service-url-filters.md)

* [Incorporar com a peça web relatório no SharePoint Online](service-embed-report-spo.md)

* [Publicar na Web do Power BI](service-publish-to-web.md)