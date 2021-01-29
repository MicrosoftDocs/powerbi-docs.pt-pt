---
title: Instale power BI desktop para power bi report server
description: Saiba como instalar o Power BI Desktop para power BI Report Server
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 10/16/2020
ms.openlocfilehash: 068d4a025bda878899e2d54f93bc56eaea336f3e
ms.sourcegitcommit: 7ed995eed0fd6e718748accf87bae384211cd95d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/29/2021
ms.locfileid: "99044086"
---
# <a name="install-power-bi-desktop-for-power-bi-report-server"></a>Instale power BI desktop para power bi report server

Para criar relatórios do Power BI para o Power BI Report Server, tem de transferir e instalar a versão do Power BI Desktop otimizada para o Power BI Report Server. Esta versão é diferente da do Power BI Desktop utilizada no serviço Power BI. Por exemplo, a versão do Power BI Desktop para o serviço Power BI inclui funcionalidades de pré-visualização. Estas funcionalidades não serão incluídas na versão do Power BI Report Server até ficarem disponíveis para todos. A utilização desta versão garante que o servidor de relatórios pode interagir com uma versão conhecida dos relatórios e do modelo. 

Não se preocupe. Pode instalar o Power BI Desktop e o Power BI Desktop para Power BI Report Server, lado a lado no mesmo computador.

## <a name="download-and-install-power-bi-desktop"></a>Transferir e instalar o Power BI Desktop

A forma mais fácil de ter a certeza de que tem a versão mais atualizada do Power BI Desktop para Power BI Report Server é começar a partir do portal web do seu servidor de relatórios.

1. No portal Web do Report Server, selecione a seta **Transferir** > **Power BI Desktop**.

    ![Transferir o Power BI Desktop a partir do portal Web](media/install-powerbi-desktop/report-server-download-web-portal.png)

    Em alternativa, aceda à home page do [Power BI Report Server](https://powerbi.microsoft.com/report-server/) e selecione **Opções de transferência avançadas**.

2. Na página do Centro de Transferências, selecione um idioma e, em seguida, selecione **Transferir**.

3. Consoante o seu computador, selecione: 

    - **PBIDesktopRS.msi** (a versão de 32 bits) ou
    - **PBIDesktopRS_x64.msi** (a versão de 64 bits).

1. Após transferir o instalador, execute o Assistente de Configuração do Power BI Desktop.

2. No final da instalação, selecione **Iniciar o Power BI Desktop**.

    Este inicia automaticamente e está pronto para começar.

## <a name="verify-youre-using-the-correct-version"></a>Confirmar que está a utilizar a versão correta
É fácil verificar se está a utilizar a versão correta do Power BI Desktop: observe o ecrã inicial ou a barra de título no Power BI Desktop. Pode dizer-se que tem a versão certa porque **power BI Desktop (janeiro de 2021)** ou mais tarde está na barra de títulos. Além disso, as cores do logótipo do Power BI estão invertidas: o logótipo surge a amarelo sobre um fundo preto em vez de aparecer a preto sobre um fundo amarelo.

![Power BI Desktop janeiro 2021](media/install-powerbi-desktop/power-bi-report-server-desktop.png)

A versão do Power BI Desktop para o serviço Power BI não tem o mês e ano na barra de título.

## <a name="file-extension-association"></a>Associação de extensões de ficheiros
Digamos que instalou tanto o Power BI Desktop como o Power BI Desktop para power BI Report Server na mesma máquina. A instalação do Power BI Desktop mais recente será associada a ficheiros .pbix. Por conseguinte, ao fazer duplo clique num ficheiro .pbix, este irá iniciar a versão do Power BI Desktop que instalou mais recentemente.

Se tiver Power BI Desktop e, em seguida, instalar Power BI Desktop para Power BI Report Server, todos os ficheiros .pbix abrem no Power BI Desktop para Power BI Report Server por predefinição. Se preferir que o Power BI Desktop seja iniciado por predefinição ao abrir um ficheiro pbix, reinstale o [Power BI Desktop a partir da Microsoft Store](https://aka.ms/pbidesktopstore).

Pode sempre começar por abrir a versão do Power BI Desktop que pretende utilizar. Em seguida, abra o ficheiro no Power BI Desktop.

Aqui está a forma mais segura de abrir sempre a versão correta do Power BI Desktop. Comece a editar um relatório do Power BI a partir do Power BI Report Server ou crie um novo relatório do Power BI a partir do serviço Power BI.

## <a name="considerations-and-limitations"></a>Considerações e limitações

Os relatórios do Power BI no Power BI Report Server, no serviço Power BI (`https://app.powerbi.com`) e nas aplicações móveis do Power BI têm um comportamento quase igual, mas com algumas diferenças em funcionalidades.

### <a name="selecting-a-language"></a>Selecionar um idioma

Para Power BI Desktop for Power BI Report Server, selecione o idioma quando instalar a aplicação. Não pode alterar o idioma mais tarde, mas pode instalar uma versão noutro idioma.

### <a name="report-visuals-in-a-browser"></a>Elementos visuais de relatórios num browser

Os relatórios do Power BI Report Server suportam quase todas as visualizações, incluindo elementos visuais do Power BI. Os relatórios do Power BI Report Server não suportam:

* Visuais R
* Trilhos
* Funcionalidades de pré-visualização do Power BI Desktop

### <a name="reports-in-the-power-bi-mobile-apps"></a>Reports in the Power BI mobile apps (Relatórios nas aplicações móveis do Power BI)

Os relatórios do Power BI Report Server suportam todas as funcionalidades básicas nas [aplicações móveis do Power BI](../consumer/mobile/mobile-apps-for-mobile-devices.md), incluindo:

* [Esquema de relatório de telemóvel](../create-reports/desktop-create-phone-report.md): pode otimizar um relatório para as aplicações móveis do Power BI. No telemóvel, os relatórios otimizados têm um ícone ![Ícone de esquema de relatório em telemóvel](media/install-powerbi-desktop/power-bi-rs-mobile-optimized-icon.png) e um esquema especiais.
  
    ![Relatório otimizado para telemóveis](media/install-powerbi-desktop/power-bi-rs-mobile-optimized-report.png)

Os relatórios do Power BI Report Server não suportam estas funcionalidades nas aplicações móveis do Power BI:

* Visuais R
* Elementos Visuais do Power BI
* Trilhos
* Geofiltragem ou códigos de barras

### <a name="custom-security"></a>Segurança Personalizada

Power BI Desktop for Power BI Report Server não suporta segurança personalizada. Se o seu Power BI Report Server estiver configurado com uma extensão de segurança personalizada, não pode guardar um relatório Power BI do Power BI Desktop (otimizado para Power BI Report Server) para a instância do Power BI Report Server. Tem de guardar o ficheiro de relatório .pbix do Power BI Desktop e carregá-lo no site do portal do Power BI Report Server.

### <a name="saving-reports-to-a-power-bi-report-server-in-a-different-domain"></a>Guardar relatórios num Power BI Report Server num domínio diferente

Ao guardar um relatório do Power BI num Power BI Report Server, são utilizadas as suas credenciais do Windows. A opção de guardar diretamente num servidor de relatórios num domínio diferente para as suas credenciais do Windows não é suportada. Pode utilizar um browser para ver o servidor de relatórios e carregar manualmente o ficheiro a partir do seu computador.

## <a name="next-steps"></a>Próximos passos

Agora que o Power BI Desktop está instalado, pode começar a criar relatórios do Power BI.

[Criar um relatório do Power BI para o Power BI Report Server](quickstart-create-powerbi-report.md)  
[O que é o Power BI Report Server?](get-started.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

