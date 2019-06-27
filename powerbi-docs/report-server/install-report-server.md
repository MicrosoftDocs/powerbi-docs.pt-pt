---
title: Instalar o Power BI Report Server
description: Saiba como instalar o Power BI Report Server.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/22/2019
ms.openlocfilehash: c0e3666a5838ae8e3849f5defd3858c9ea205a42
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "66839435"
---
# <a name="install-power-bi-report-server"></a>Instalar o Power BI Report Server

Saiba como instalar o Power BI Report Server.

## <a name="download-power-bi-report-server"></a>Transferir o Power BI Report Server

[Transfira o Power BI Report Server](https://www.microsoft.com/download/details.aspx?id=56722) no Centro de Transferências da Microsoft.

Também existe uma versão de avaliação gratuita. Na página [Relatórios no local com o Power BI Report Server](https://powerbi.microsoft.com/report-server/), selecione **Transferir avaliação gratuita**.

## <a name="before-you-install"></a>Antes da instalação

Antes de instalar o Power BI Report Server, recomendamos que veja os [Requisitos de Software e Hardware para instalar o Power BI Report Server](system-requirements.md).

 > [!IMPORTANT]
 > Embora possa instalá-lo num ambiente com um Controlador de Domínio Só de Leitura (RODC), o Power BI Report Server requer acesso a um Controlador de Domínio de Leitura/Escrita para funcionar devidamente. Se o Power BI Report Server tiver acesso apenas a um RODC, poderá encontrar erros ao tentar administrar o serviço.

### <a name="power-bi-report-server-product-key"></a>Chave de produto do Power BI Report Server

Pode obter a chave de produto do Power BI Report Server a partir de duas origens diferentes:

- Power BI Premium
- SQL Server Enterprise Software Assurance (SA)

Continue a ler para obter mais informações.

#### <a name="power-bi-premium"></a>Power BI Premium

Se tiver adquirido o Power BI Premium, no separador **Definições Premium** do portal de administração do Power BI, terá acesso à sua chave de produto do Power BI Report Server. Esta opção está apenas disponível para Administradores Globais ou utilizadores com a função de administrador de serviços do Power BI atribuída.

![Definições Premium](../report-server/media/install-report-server/pbirs-product-key.png "Chave do Power BI Report Server nas definições Premium")

Ao selecionar **chave do Power BI Report Server**, é apresentada uma caixa de diálogo com a sua chave de produto. Pode copiá-la e utilizá-la na instalação.

![Chave de produto](../report-server/media/install-report-server/pbirs-product-key-dialog.png "Chave de produto do Power BI Report Server")

#### <a name="sql-server-enterprise-software-assurance-sa"></a>SQL Server Enterprise Software Assurance (SA)

Se tem um contrato do SQL Server Enterprise SA, pode obter a sua chave de produto no [Centro de Serviços de Licenciamento de Volume](https://www.microsoft.com/Licensing/servicecenter/).

## <a name="install-your-report-server"></a>Instalar o servidor de relatório

É simples instalar o Power BI Report Server. Bastam alguns passos para instalar os ficheiros.

Não precisa de um servidor de Motor de Base de Dados do SQL Server aquando da instalação. Precisará de um para configurar o Reporting Services após a instalação.

1. Procure a localização do ficheiro PowerBIReportServer.exe e inicie o instalador.

2. Selecione **Instalar o Power BI Report Server**.

    ![Instalar o Power BI Report Server](media/install-report-server/pbireportserver-install.png)
3. Selecione uma edição para instalar e, em seguida, selecione **Seguinte**.

    ![Selecionar uma edição](media/install-report-server/pbireportserver-choose-edition.png)

    Pode selecionar a edição de Avaliação ou de Programador no menu pendente.

    ![Edição 2](media/install-report-server/pbireportserver-choose-edition2.png)

    Em alternativa, introduza a chave de produto que obteve no serviço Power BI ou no Centro de Serviços de Licenciamento em Volume. Para obter mais informações sobre como obter a sua chave de produto, veja a secção [Antes da instalação](#before-you-install) apresentada acima.
4. Leia e aceite os termos e condições de licenciamento e, em seguida, selecione **Seguinte**.

    ![Termos de licenciamento](media/install-report-server/pbireportserver-eula.png)
5. Precisa de ter um Motor de Base de Dados disponível para armazenar a base de dados do servidor de relatório. Selecione **Seguinte** para instalar apenas o servidor de relatório.

    ![Instalar apenas ficheiros](media/install-report-server/pbireportserver-install-files-only.png)
6. Especifique a localização de instalação para o servidor de relatório. Selecione **Instalar** para continuar.

    ![Especificar caminho de instalação](media/install-report-server/pbireportserver-install-file-path.png)

    O caminho predefinido é C:\Program Files\Microsoft Power BI Report Server.

7. Após configurar com êxito, selecione **Configurar Report Server** para iniciar o Gestor de Configuração do Reporting Services.

    ![Configurar o servidor de relatório](media/install-report-server/pbireportserver-configure.png)

## <a name="configure-your-report-server"></a>Configurar o seu servidor de relatórios

Após selecionar **Configurar Servidor de Relatórios** na configuração, é-lhe apresentado o Gestor de Configuração do Reporting Services. Para obter mais informações, consulte [Reporting Services Configuration Manager (Gestor de Configuração do Reporting Services - em inglês)](https://docs.microsoft.com/sql/reporting-services/install-windows/reporting-services-configuration-manager-native-mode).

Terá de [criar uma base de dados do servidor de relatório](https://docs.microsoft.com/sql/reporting-services/install-windows/ssrs-report-server-create-a-report-server-database) para concluir a configuração inicial do Reporting Services. É necessário um servidor de Base de dados do SQL Server para concluir este passo.

### <a name="creating-a-database-on-a-different-server"></a>Criar uma base de dados num servidor diferente

Se estiver a criar a base de dados do servidor de relatório num servidor de base de dados num computador diferente, precisará de alterar a conta de serviço do servidor de relatório para uma credencial que seja reconhecida no servidor de base de dados. 

Por predefinição, o servidor de relatório utiliza a conta de serviços virtuais. Se tentar criar uma base de dados num servidor diferente, poderá receber o seguinte erro no passo Aplicar direitos de ligação.

`System.Data.SqlClient.SqlException (0x80131904): Windows NT user or group '(null)' not found. Check the name again.`

Para contornar este erro, pode alterar a conta de serviço para uma conta de domínio ou Serviço de Rede. Alterar a conta de serviço para Serviço de Rede aplica os direitos no contexto da conta de computador para o servidor de relatório.

![Configurar a conta de serviço do servidor de relatório](media/install-report-server/pbireportserver-configure-account.png)

Para obter mais informações, consulte [Configure the report server service account (Configurar a conta de serviço do servidor de relatório - em inglês)](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager).

## <a name="windows-service"></a>Serviço Windows

Um serviço Windows é criado como parte da instalação. É apresentado como **Power BI Report Server**. O nome de serviço é **PowerBIReportServer**.

![Serviço Windows do Report Server](media/install-report-server/pbireportserver-windows-service.png)

![Propriedades do Serviço Windows do Report Server](media/install-report-server/pbireportserver-windows-service2.png)

## <a name="default-url-reservations"></a>Reservas de URL predefinidas

As reservas de URL contêm um prefixo, nome de anfitrião, porta e diretório virtual:

| Parte | Descrição |
| --- | --- |
| Prefixo |O prefixo predefinido é HTTP. Se instalou anteriormente um certificado Secure Sockets Layer (SSL), a Configuração tenta criar reservas de URL que utilizem o prefixo HTTPS. |
| Nome do anfitrião |O nome de anfitrião predefinido é um caráter universal forte (+). Especifica que o servidor de relatório aceita qualquer pedido HTTP na porta designada para qualquer nome de anfitrião que resolva para o computador, incluindo `http://<computername>/reportserver`, `http://localhost/reportserver` ou `http://<IPAddress>/reportserver.` |
| Porta |A porta predefinida é 80. Se utilizar uma porta que não a 80, tem de adicioná-la explicitamente ao URL quando abrir o portal Web numa janela do browser. |
| Diretório virtual |Por predefinição, os diretórios virtuais são criados no formato de ReportServer para o serviço Web do Report Server e Relatórios para o portal Web. Para o serviço Web do Report Server, o diretório virtual predefinido é **reportserver**. No portal Web, o diretório virtual predefinido é **reports**. |

Eis um exemplo da cadeia de URL completa:

* `http://+:80/reportserver` fornece acesso ao servidor de relatório.
* `http://+:80/reports` fornece acesso ao portal Web.

## <a name="firewall"></a>Firewall

Se estiver a aceder a um servidor de relatório num computador remoto, deve garantir que configurou eventuais regras de firewall, caso esta exista.

Terá de abrir a porta TCP que configurou para o seu URL de Serviço Web e URL do Portal Web. Por predefinição, estão configurados na porta TCP 80.

## <a name="additional-configuration"></a>Configuração adicional

* Para configurar a integração com o serviço Power BI para poder afixar itens de relatório a um dashboard do Power BI, consulte [Integrate with the Power BI service (Integração com o serviço Power BI - em inglês)](https://docs.microsoft.com/sql/reporting-services/install-windows/power-bi-report-server-integration-configuration-manager).
* Para configurar o e-mail para o processamento de subscrições, consulte [Definições de e-mails](https://docs.microsoft.com/sql/reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager) e [Entrega de e-mails num servidor de relatório](https://docs.microsoft.com/sql/reporting-services/subscriptions/e-mail-delivery-in-reporting-services).
* Para configurar o portal Web para que possa aceder ao mesmo num computador de relatório para ver e gerir relatórios, consulte [Configurar uma firewall para acesso ao servidor de relatórios](https://docs.microsoft.com/sql/reporting-services/report-server/configure-a-firewall-for-report-server-access) e [Configurar um servidor de relatórios para administração remota](https://docs.microsoft.com/sql/reporting-services/report-server/configure-a-report-server-for-remote-administration).

## <a name="next-steps"></a>Próximos passos

[Descrição geral para administradores](admin-handbook-overview.md)  
[Como encontrar a chave de produto do servidor de relatórios](find-product-key.md)  
[Instalar o Power BI Desktop otimizado para o Power BI Report Server](install-powerbi-desktop.md)  
[Verify a Reporting Services installation](https://docs.microsoft.com/sql/reporting-services/install-windows/verify-a-reporting-services-installation) (Verificar uma instalação do Reporting Services)  
[Configurar a conta de serviço do servidor de relatórios](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager)  
[Configurar URLs do servidor de relatórios](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager)  
[Configurar uma ligação à base de dados do servidor de relatórios](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager)  
[Inicializar um servidor de relatórios](https://docs.microsoft.com/sql/reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server)  
[Configurar ligações SSL num servidor de relatório](https://docs.microsoft.com/sql/reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server)  
[Configurar permissões e contas de serviço Windows](https://docs.microsoft.com/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions)  
[Suporte de browser para o Power BI Report Server](browser-support.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)