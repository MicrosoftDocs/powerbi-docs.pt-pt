---
title: "Incorporar com peças Web de relatórios no SharePoint Online"
description: "Com a nova peça Web de relatórios do Power BI para o SharePoint Online, pode facilmente incorporar relatórios interativos do Power BI em páginas do SharePoint Online."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/19/2017
ms.author: asaxton
ms.openlocfilehash: a60682f9da2befe5f87b11749c089f72949a8f6f
ms.sourcegitcommit: 6e8fbbbcbe3e1a38207b29a9ca66ea94fb2a51fb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/19/2017
---
# <a name="embed-with-report-web-part-in-sharepoint-online"></a>Incorporar com peças Web de relatórios no SharePoint Online

Com a nova peça Web de relatórios do Power BI para o SharePoint Online, pode facilmente incorporar relatórios interativos do Power BI em páginas do SharePoint Online.

Ao utilizar a nova opção **Incorporar no SharePoint Online**, os relatórios incorporados ficam completamente seguros, para que possa facilmente criar portais internos seguros.

## <a name="requirements"></a>Requisitos

Eis alguns requisitos para conseguir **Incorporar no SharePoint Online**.

* A peça Web do Power BI para o SharePoint Online requer as [Páginas Modernas](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b).

## <a name="embed-your-report"></a>Incorporar o seu relatório

Para incorporar o seu relatório no SharePoint Online, terá primeiro de obter o URL do relatório e, em seguida, utilizar esse URL com a nova peça Web do Power BI no SharePoint Online.

### <a name="get-a-url-to-your-report"></a>Obter um URL do seu relatório

1. Veja o relatório no serviço Power BI.

2. Selecione o item de menu **Ficheiro**.

3. Selecione **Incorporar no SharePoint Online**.
   
    ![](media/service-embed-report-spo/powerbi-file-menu.png)

4. Copie o URL da caixa de diálogo.

    ![](media/service-embed-report-spo/powerbi-embed-link-sharepoint.png)

   > [!NOTE]
   > Pode também utilizar o URL apresentado na barra de endereço do seu browser ao visualizar um relatório. O URL contém a página de relatório que está atualmente a ver. Terá de remover a secção de relatório do URL se pretender utilizar uma página diferente.

### <a name="add-the-power-bi-report-to-a-sharepoint-online-page"></a>Adicionar o relatório do Power BI a uma página do SharePoint Online

1. Abra a página pretendida no SharePoint Online e selecione **Editar**.

    ![](media/service-embed-report-spo/powerbi-sharepoint-edit-page.png)

    Também pode criar uma nova página de site moderna ao selecionar **+ Novo** no SharePoint Online.

    ![](media/service-embed-report-spo/powerbi-sharepoint-new-page.png)

2. Selecione **+** e selecione a peça Web do **Power BI**.

    ![](media/service-embed-report-spo/powerbi-sharepoint-new-web-part.png)

3. Selecione **Adicionar relatório**.

    ![](media/service-embed-report-spo/powerbi-sharepoint-new-report.png)

4. Cole o URL do relatório no painel da propriedade. Este é o URL que copiou nos passos anteriores. O relatório será carregado automaticamente.

    ![](media/service-embed-report-spo/powerbi-sharepoint-new-web-part-properties.png)

5. Selecione **Publicar** para tornar a alteração visível para os seus utilizadores do SharePoint Online.

    ![](media/service-embed-report-spo/powerbi-sharepoint-report-loaded.png)

## <a name="granting-access-to-reports"></a>Conceder acesso a relatórios

Incorporar um relatório no SharePoint Online não dá automaticamente permissão aos utilizadores para ver o relatório. As permissões para ver o relatório são definidas no serviço Power BI.

> [!IMPORTANT]
> Certifique-se de que revê quem pode ver o relatório no serviço Power BI e conceder acesso aos que não estão listados.

Existem duas formas de dar acesso ao relatório no serviço Power BI. Se estiver a utilizar um Grupo do Office 365 para criar o seu site de equipa do SharePoint Online, deve listar o utilizador como membro da área de trabalho de aplicação no serviço Power BI. Isto garante que os utilizadores podem ver o conteúdo desse grupo. Para obter mais informações, consulte [Criar e distribuir uma aplicação no Power BI](service-create-distribute-apps.md).

Em alternativa, pode conceder aos utilizadores acesso ao seu relatório ao fazer o seguinte.

1. Adicione um mosaico de um relatório a um dashboard.

2. Partilhe o dashboard com os utilizadores que precisam de acesso ao relatório. Para obter mais informações, consulte [Partilhar um dashboard com colegas e outras pessoas](service-share-dashboards.md).

## <a name="allowing-free-users-access-to-reports"></a>Permitir o acesso a relatórios a utilizadores Gratuitos

Os utilizadores gratuitos podem ver relatórios incorporados com a peça Web do Power BI para o SharePoint Online. O acesso aos utilizadores gratuitos é proporcionado da mesma forma que aos utilizadores Pro, conforme descrito anteriormente em [Conceder acesso a relatórios](#granting-access-to-reports). A área de trabalho, onde o relatório se encontra, também tem de ter a capacidade do Power BI Premium. 

Por exemplo, se tiver um relatório, numa área de trabalho de aplicação, tem de atribuir a área de trabalho de aplicação a uma capacidade do Power BI Premium. Também precisaria de adicionar o utilizador Gratuito à lista de membros dessa área de trabalho de aplicação.

## <a name="web-part-settings"></a>Definições de peças Web

Segue-se uma descrição das definições que podem ser ajustadas na peça Web do Power BI para o SharePoint Online.

![](media/service-embed-report-spo/powerbi-sharepoint-web-part-properties.png)

| Propriedade | Descrição |
| --- | --- |
| Nome da página |Predefine a página que é mostrada pela peça Web. Selecione um valor no menu pendente. Se não forem apresentadas páginas, significa que o seu relatório tem uma página ou que o URL que colou contém um nome de página. Remova a secção de relatório do URL para selecionar uma página específica. |
| Apresentar |Opção para personalizar o ajuste do relatório na página do SharePoint Online. |
| Mostrar Painel de Navegação |Mostra ou oculta o painel de navegação de páginas. |
| Mostrar Painel de Filtro |Mostra ou oculta o painel de filtro. |

## <a name="multi-factor-authentication"></a>Autenticação multifator

Se o seu ambiente do Power BI requerer que inicie sessão através da autenticação multifator, poderá ser-lhe pedido que inicie sessão com um dispositivo de segurança para verificar a sua identidade. Isto irá ocorrer se não tiver iniciado sessão no SharePoint Online através da autenticação multifator, mas o seu ambiente do Power BI requerer uma conta validada por um dispositivo de segurança.

> [!NOTE]
> A autenticação multifator ainda não é suportada no Azure Active Directory 2.0. Os utilizadores receberão uma mensagem a indicar *erro*. Se o utilizador voltar a iniciar sessão no SharePoint Online através do respetivo dispositivo de segurança, este poderá ver o relatório.

## <a name="reports-that-do-not-load"></a>Relatórios que não são carregados

O seu relatório poderá não ser carregado na peça Web do Power BI, apresentando a seguinte mensagem.

*Este conteúdo não está disponível.*

![](media/service-embed-report-spo/powerbi-sharepoint-report-not-found.png)

Existem dois motivos comuns para esta mensagem.

1. Não tem acesso ao relatório.
2. O relatório foi eliminado.

Deve contactar o proprietário da página do SharePoint Online para que este o ajude a resolver o problema.

## <a name="known-issues-and-limitations"></a>Limitações e problemas conhecidos

* **Erro: "Ocorreu um erro, tente terminar e voltar a iniciar sessão e, em seguida, revisitar esta página. ID de correlação: não definido, estado de resposta http: 400, código de erro de servidor 10001, mensagem: Token atualizado em falta"**
  
  Se receber este erro, experimente uma das seguintes soluções.
  
  1. Termine sessão no SharePoint e volte a iniciar sessão. Certifique-se de que fecha todas as janelas do browser antes de voltar a iniciar sessão.

  2. Se a sua conta de utilizador requer autenticação multifator (MFA), certifique-se de que inicia sessão no SharePoint através do seu dispositivo de autenticação multifator (aplicação para telemóvel, smart card, etc.)

* O Power BI não suporta os mesmos idiomas localizados que o SharePoint Online. Como tal, poderá não ver uma devida localização no relatório incorporado.

* Poderá encontrar problemas se estiver a utilizar o Internet Explorer 10. Pode ver a [compatibilidade de browsers do Power BI](service-browser-support.md) e do [Office 365](https://products.office.com/office-system-requirements#Browsers-section).

## <a name="next-steps"></a>Próximas etapas

[Permitir ou impedir a criação de páginas de sites modernos por utilizadores finais](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)  
[Criar e distribuir uma aplicação no Power BI](service-create-distribute-apps.md)  
[Partilhar um dashboard com colegas e outros utilizadores](service-share-dashboards.md)  
[Power BI Premium – o que é?](service-premium.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

