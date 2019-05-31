---
title: Incorporar com peças Web de relatórios no SharePoint Online
description: Com a nova peça Web de relatórios do Power BI para o SharePoint Online, pode facilmente incorporar relatórios interativos do Power BI em páginas do SharePoint Online.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 05/16/2019
ms.openlocfilehash: c8789d47ed1b67f9fd6808865514120457a29dfe
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051273"
---
# <a name="embed-with-report-web-part-in-sharepoint-online"></a>Incorporar com peças Web de relatórios no SharePoint Online

Com a nova peça Web de relatórios do Power BI para o SharePoint Online, pode facilmente incorporar relatórios interativos do Power BI em páginas do SharePoint Online.

Ao utilizar a nova **incorporar no SharePoint Online** opção, os relatórios incorporados ficam completamente protegidos, para que pode criar facilmente portais internos seguros.

## <a name="requirements"></a>Requirements

Para **incorporar no SharePoint Online** relatórios para funcionar, é necessário o seguinte:

* Uma licença do Power BI Pro ou um [capacidade do Power BI Premium (EM ou P SKU)](service-premium-what-is.md) com uma licença do Power BI.
* A peça Web do Power BI para o SharePoint Online requer as [Páginas Modernas](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b).

## <a name="embed-your-report"></a>Incorporar o seu relatório
Para incorporar o seu relatório no SharePoint Online, terá de obter o URL de relatório e utilizá-la com peça web do Power BI novo do SharePoint Online.

### <a name="get-a-report-url"></a>Obter um URL de relatório

1. No Power BI, veja o relatório.

2. Selecione o **arquivo** menu pendente, em seguida, selecione **incorporar no SharePoint Online**.

    ![Menu de Ficheiros](media/service-embed-report-spo/powerbi-file-menu.png)

3. Copie o URL de relatório na caixa de diálogo.

    ![Incorporar a ligação](media/service-embed-report-spo/powerbi-embed-link-sharepoint.png)

### <a name="add-the-power-bi-report-to-a-sharepoint-online-page"></a>Adicionar o relatório do Power BI a uma página do SharePoint Online

1. Abra a página de destino no SharePoint Online e selecione **editar**.

    ![Página de edições do SP](media/service-embed-report-spo/powerbi-sharepoint-edit-page.png)

    Ou, no Sharepoint Online, selecione **+ novo** para criar uma nova página de site moderna.

    ![Nova página do SP](media/service-embed-report-spo/powerbi-sharepoint-new-page.png)

2. Selecione o **+** menu pendente e, em seguida, selecione o **Power BI**.

    ![Nova peça Web do SP](media/service-embed-report-spo/powerbi-sharepoint-new-web-part.png)

3. Selecione **Adicionar relatório**.

    ![Novo relatório do SP](media/service-embed-report-spo/powerbi-sharepoint-new-report.png)  

4. Cole o URL de relatório anteriormente copiado para o **ligação de relatório do Power BI** painel. O relatório é carregado automaticamente.

    ![Propriedades da nova peça Web do SP](media/service-embed-report-spo/powerbi-sharepoint-new-web-part-properties.png)

5. Selecione **Publicar** para tornar a alteração visível para os seus utilizadores do SharePoint Online.

    ![Relatório do SP carregado](media/service-embed-report-spo/powerbi-sharepoint-report-loaded.png)

## <a name="grant-access-to-reports"></a>Conceder acesso a relatórios

Incorporar um relatório no SharePoint Online não automaticamente dar aos utilizadores permissão para ver o relatório - precisa definir permissões de visualização no Power BI.

> [!IMPORTANT]
> Certifique-se de que revê quem pode ver o relatório no serviço Power BI e conceda acesso aos que não estão listados.

Existem duas formas de fornecer acesso de relatório no Power BI. A primeira maneira, se estiver a utilizar um grupo do Office 365 para criar o site de equipe do SharePoint Online, consiste em listar o utilizador como membro do **área de trabalho de aplicação no serviço Power BI** e o **página do SharePoint**. Para obter mais informações, veja como [gerir uma área de trabalho de aplicação](service-manage-app-workspace-in-power-bi-and-office-365.md).

A segunda maneira é incorporar um relatório numa aplicação e compartilhá-lo diretamente com os utilizadores:  

1. O autor (tem de ser um utilizador Pro) cria um relatório numa área de trabalho de aplicação. Para partilhar com **utilizadores gratuitos do Power BI**, a área de trabalho de aplicação tem de ser definida como um **área de trabalho Premium**.

2. O autor publica a aplicação e instala-o. O autor tem de certificar-se de que instalar a aplicação para ter acesso para o URL de relatório que é utilizado para incorporar no SharePoint Online.

3. Agora, todos os utilizadores finais também têm de instalar a aplicação. Também pode utilizar o **instalar aplicação automaticamente** recurso, que pode ativar no [portal de administração do Power BI](service-admin-portal.md), para ter a aplicação instalada previamente para os utilizadores finais.

   ![Instalar aplicação automaticamente](media/service-embed-report-spo/install-app-automatically.png)

4. O autor abre a aplicação e vai para o relatório.

5. O autor copia o URL de relatório de incorporação do relatório a aplicação instalada. **Não utilize o URL de relatório original da área de trabalho de aplicação.**

6. Crie um novo site de equipa no SharePoint Online.

7. Adicione o URL de relatório anteriormente copiado para a web part do Power BI.

8. Adicione todos os utilizadores finais e/ou grupos que vão consumir os dados na página do SharePoint Online e na aplicação do Power BI que criou.

    > [!NOTE]
    > **Os utilizadores ou grupos precisam de aceder tanto à página do SharePoint Online como ao relatório na aplicação do Power BI para ver o relatório na página do SharePoint.**

Agora, o utilizador final pode ir para o site de equipa no SharePoint Online e ver os relatórios na página.

## <a name="multi-factor-authentication"></a>Autenticação multifator

Se o seu ambiente do Power BI requerer que inicie sessão através da autenticação multifator, poderá ser-lhe pedido que inicie sessão com um dispositivo de segurança para verificar a sua identidade. Isto ocorre se não iniciaram sessão no SharePoint Online usando a autenticação multifator, mas o seu ambiente do Power BI requer um dispositivo de segurança para validar uma conta.

> [!NOTE]
> O Azure Active Directory 2.0 não suporta autenticação multifator - os utilizadores verão uma mensagem de erro. Se o utilizador voltar a iniciar sessão no SharePoint Online através do respetivo dispositivo de segurança, este conseguirá ver o relatório.

## <a name="web-part-settings"></a>Definições de peças Web

Seguem-se as definições que pode ajustar-se para a web part do Power BI para o SharePoint Online.

![Propriedades da peça Web do SP](media/service-embed-report-spo/powerbi-sharepoint-web-part-properties.png)

| Propriedade | Descrição |
| --- | --- |
| Nome da página |Define a página de padrão da web part. Selecione um valor no menu pendente. Se não forem apresentadas páginas, significa que o seu relatório tem uma página ou que o URL que colou contém um nome de página. Remova a secção de relatório do URL para selecionar uma página específica. |
| Display |Ajusta-se de como o relatório se encaixa na página do SharePoint Online. |
| Mostrar Painel de Navegação |Mostra ou oculta o painel de navegação de páginas. |
| Mostrar Painel de Filtro |Mostra ou oculta o painel de filtro. |

## <a name="reports-that-do-not-load"></a>Relatórios que não são carregados

Se o relatório não é carregado dentro a peça web Power BI, verá a seguinte mensagem:

![Este conteúdo não está disponível mensagem](media/service-embed-report-spo/powerbi-sharepoint-report-not-found.png)

Existem dois motivos comuns para esta mensagem.

1. Não tem acesso de relatório.
2. O relatório foi eliminado.

Contacte o proprietário de página Online do SharePoint para o ajudar a resolver o problema.

## <a name="licensing"></a>Licensing

Os utilizadores que visualizam um relatório no SharePoint precisam de uma **licença do Power BI Pro** ou os conteúdos precisam de estar numa área de trabalho com  **[capacidade do Power BI Premium (SKU EM ou P)](service-admin-premium-purchase.md)** .

## <a name="known-issues-and-limitations"></a>Limitações e problemas conhecidos

* Erro: "Ocorreu um erro; tente terminar e voltar a iniciar sessão e, em seguida, revisite esta página. ID de Correlação: indefinido, estado de resposta de http: 400, código de erro de servidor 10001, mensagem: Token de atualização em falta"
  
  Se receber este erro, experimente um dos passos de resolução de problemas abaixo.
  
  1. Termine a sessão no SharePoint e volte a iniciá-la. Certifique-se de que fecha todas as janelas do browser antes de voltar a iniciar sessão.

  2. Se a sua conta de utilizador exigir autenticação multifator (MFA), em seguida, inicie sessão no SharePoint com o seu dispositivo MFA (aplicação para telemóvel, smart card, etc.).
  
  3. As contas de utilizadores Convidados do Azure B2B não são suportadas. Os utilizadores veem o logótipo do Power BI que mostra que a peça está a ser carregada, mas não será apresentado o relatório.

* O Power BI não suporta os mesmos idiomas localizados que o SharePoint Online. Como tal, poderá não ver uma devida localização no relatório incorporado.

* Poderá encontrar problemas se estiver a utilizar o Internet Explorer 10. Pode ver a [compatibilidade de browsers do Power BI](consumer/end-user-browsers.md) e do [Office 365](https://products.office.com/office-system-requirements#Browsers-section).

* A peça Web do Power BI não está disponível para [clouds nacionais](https://powerbi.microsoft.com/clouds/).

* O SharePoint Server clássico não é suportado com esta peça Web.

* Os [filtros de URL](service-url-filters.md) não são suportados na peça Web do SPO.

## <a name="next-steps"></a>Próximos passos

* [Allow or prevent creation of modern site pages by end users](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b) (Permitir ou impedir a criação de páginas de sites modernos por utilizadores finais)  
* [Create and distribute an app in Power BI](service-create-distribute-apps.md) (Criar e distribuir uma aplicação no Power BI)  
* [Partilhar um dashboard com colegas e outros utilizadores](service-share-dashboards.md)  
* [O que é o Power BI Premium?](service-premium-what-is.md)
* [Incorporar relatório num site ou portal seguro](service-embed-secure.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)