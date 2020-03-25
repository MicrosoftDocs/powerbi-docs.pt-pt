---
title: Power BI para clientes do US Government – Descrição Geral
description: Os clientes do US Government podem adicionar uma subscrição do Power BI Pro ao plano do Office 365 para o Governo Norte-Americano. Saiba como se inscrever e rever a disponibilidade das funcionalidades nesta descrição do serviço.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/13/2020
ms.author: kfollis
LocalizationGroup: Get started
ms.openlocfilehash: 349b4d51c1649b714c67e61ac42ddcc49b2eeb12
ms.sourcegitcommit: 2c798b97fdb02b4bf4e74cf05442a4b01dc5cbab
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/21/2020
ms.locfileid: "80114894"
---
# <a name="power-bi-for-us-government-customers"></a>Power BI para clientes da Administração Pública dos EUA
Este artigo é para clientes do US Government que estão a implementar o Power BI como parte de um plano do Office 365 para o Governo Norte-Americano. Os planos governamentais destinam-se às necessidades únicas das organizações que devem cumprir as normas de conformidade e segurança dos EUA. O serviço Power BI concebido para clientes do US Government difere da versão comercial do serviço Power BI. Estas capacidades e diferenças das funcionalidades são descritas nas secções seguintes.

## <a name="add-power-bi-to-your-office-365-government-plan"></a>Adicionar o Power BI ao plano do Office 365 para o Governo Norte-Americano

Para poder obter uma subscrição do Power BI US Government e atribuir licenças aos utilizadores, tem de se inscrever num plano do Office 365 para o Governo Norte-Americano. Se a sua organização já tiver um plano do Office 365 para o Governo Norte-Americano, avance para [Comprar uma subscrição do Power BI Pro Government](#purchase-a-power-bi-pro-government-subscription).

### <a name="enroll-in-office-365-government-plan"></a>Inscrever-se no plano do Office 365 para o Governo Norte-Americano

Se for um cliente novo, terá de validar a elegibilidade da sua organização para se poder inscrever num plano governamental.  Comece por preencher o [formulário de validação da elegibilidade do Office 365 para o Governo Norte-Americano](https://www.microsoft.com/microsoft-365/government/eligibility-validation). Para garantir que seleciona o plano correto para a sua organização, veja [Office 365 US Government service descriptions](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government) (Descrições dos serviços do Office 365 para o Governo Norte-Americano).

> [!NOTE]
> Se já tiver implementado o Power BI num ambiente comercial e quiser migrar para a Microsoft Cloud for US Government, terá de adicionar uma nova subscrição do Power BI Pro ao seu plano do Office 365 para o Governo Norte-Americano. Em seguida, replique os dados comerciais para o serviço Power BI para US Government, remova as atribuições de licenças comerciais das contas de utilizadores e, em seguida, atribua uma licença do Power BI Pro Government às contas de utilizadores.
>
>

### <a name="government-cloud-instances"></a>Instâncias da cloud para o Governo Norte-Americano
O Office 365 fornece diferentes ambientes para que as agências governamentais cumpram os diferentes requisitos de conformidade. Veja as descrições do serviço associado para obter detalhes específicos sobre o que cada ambiente proporciona.

* A [Office 365 Government Community Cloud (GCC)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) (Cloud da Comunidade Governamental (GCC) do Office 365) foi concebida para o governo federal, estadual e local.

* A [Office 365 Government Community Cloud High (GCC-High)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) (Cloud da Comunidade Governamental Elevada (GCC-High) do Office 365) foi concebida para as agências federais, a indústria de defesa, a indústria aeroespacial e outras organizações com informações não classificadas controladas. Este ambiente é adequado para organizações de segurança nacional e empresas com dados dos International Traffic in Arms Regulations (ITAR – Regulamentos sobre o Tráfico Internacional de Armas) ou requisitos do Defense Federal Acquisition Regulations Supplement (DFARS – Suplemento dos Regulamentos de Aquisições Federais do Departamento da Defesa).

* O [Office 365 DoD environment](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) (Ambiente DoD do Office 365) foi concebido exclusivamente para o Departamento da Defesa dos EUA. 

### <a name="purchase-a-power-bi-pro-government-subscription"></a>Comprar uma subscrição do Power BI Pro Government

Após a implementação do Office 365, pode adicionar uma subscrição do Power BI. Siga a orientação passo a passo em [Inscrever a sua organização do US Government](service-govus-signup.md#existing-office-government-cloud-customers) para adquirir o serviço do Power BI Pro Government. Compre licenças suficientes para todos os utilizadores que precisam de utilizar o Power BI e, em seguida, atribua essas licenças a contas de utilizadores individuais.

> [!IMPORTANT]
> O Power BI US Government não está disponível com as licenças Gratuitas. Deve ser atribuída a cada utilizador uma licença Pro para aceder à cloud da comunidade governamental. Se uma conta de utilizador tiver uma licença Gratuita atribuída, estará autorizada a aceder apenas à cloud comercial e irá deparar-se com problemas de autenticação e acesso. Se tiver adquirido o Power BI Premium, não tem de atribuir licenças do Pro para permitir o acesso de utilizadores.  Qualquer utilizador na organização pode aceder a relatórios partilhados com os mesmos, desde que o relatório esteja publicado com uma capacidade Premium. Para rever as diferenças entre os tipos de licença, veja [Funcionalidades do serviço Power BI por tipo de licença](service-features-license-type.md).
>
>

## <a name="connect-to-power-bi-for-us-government"></a>Ligar ao Power BI para o Governo dos Estados-Unidos

Deverá utilizar um URL diferente do dos utilizadores comerciais para se ligar ao Power BI para o Governo dos Estados-Unido. Para iniciar sessão no Power BI, utilize os seguintes URLs:

| URL da versão comercial | URL da versão do Governo dos Estados Unidos | URL da Administração Pública da GCC High |
| --- | --- | --- |
| https://app.powerbi.com/ |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) |

A conta pode ser aprovisionada para mais do que uma cloud. Neste caso, ao utilizar o Power BI Desktop, pode escolher a qual cloud ligar quando iniciar sessão.

## <a name="connectivity-between-government-and-global-azure-cloud-services"></a>Conectividade entre os serviços Cloud do Azure global e de Administração Pública

O Azure é distribuído entre várias clouds. Por predefinição, pode ativar regras da firewall para abrir uma ligação para uma instância específica da cloud, mas a rede entre clouds é diferente.  Para comunicar entre serviços na cloud pública e serviços na Cloud da Comunidade Governamental, tem de configurar regras específicas da firewall. Por exemplo, se quiser aceder a instâncias da cloud pública do SQL a partir da sua implementação da cloud governamental do Power BI, precisará de uma regra da firewall no SQL. Configure regras específicas da firewall no SQL para permitir ligações à Cloud do Azure Government para os seguintes datacenters:

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona

Os intervalos de IP estão disponíveis na cloud pública. Para obter os intervalos de IP da Microsoft Cloud for US Government, transfira o ficheiro [Azure IP Ranges and Service Tags – Us Government Cloud](https://www.microsoft.com/download/details.aspx?id=57063) (Intervalos de IP do Azure e Etiquetas de Serviço – Microsoft Cloud for US Government). 

Para configurar firewalls no SQL, siga os passos para [Criar e gerir as regras de firewall de IP](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules).

## <a name="power-bi-feature-availability"></a>Disponibilidade das funcionalidades do Power BI

Para cumprir os requisitos dos clientes da cloud governamental, existem algumas diferenças entre os planos governamentais e os planos comerciais. Veja a tabela seguinte para ver quais as funcionalidades disponíveis em cada ambiente governamental.

|Funcionalidade |   |GCC |GCC-High |DoD|
|------|------|------|------|------|
|Administração|Licenças gratuitas|Não disponível|Não disponível|Não disponível|
|  |Definir limites de armazenamento de dados|Disponível|Disponível|Disponível|
|  |Utilizar grupos do Active Directory para partilha e controlo de acesso|Disponível|Disponível|Disponível|
|  |Auditoria através do centro de administração de Segurança e Conformidade do Office 365|Disponível|Disponível|Disponível|
|  |Partilha de utilizadores externos|Disponível|Disponível|Disponível|
|  |Métricas de utilização para relatórios e dashboards|Não disponível|Não disponível|Não disponível|
|  |Azure B2B entre GCC e cloud comercial|Não disponível|Não disponível|Não disponível|
|Criação de relatórios|Criar e ver dashboards e relatórios|Disponível|Disponível|Disponível|
|  |Atualização de dados agendada|Disponível|Disponível|Disponível|
|  |Dashboards de equipa atualizáveis|Disponível|Disponível|Disponível|
|  |Relatórios paginados|Disponível|Disponível|Previsto|
|  |Aplicações de modelo|Não disponível|Não disponível|Não disponível|
|Ligar-se a dados|Importar dados e relatórios do Excel|Disponível|Disponível|Disponível|
|  |Importar dados de ficheiros CSV|Disponível|Disponível|Disponível|
|  |Importar dados de ficheiros do Power BI Desktop|Disponível|Disponível|Disponível|
|  |Conectividade para CDS|Disponível|Não disponível|Não disponível|
|  |Conector do Azure Data Lake Storage Gen2|Disponível|Não disponível|Não disponível|
|Gestão de dados|Gateway de gestão de dados|Disponível|Disponível|Disponível|
|  |Encriptação de dados no Azure SQL|Disponível|Disponível|Disponível|
|  |Encriptação de dados no Armazenamento de Blobs do Power BI|Disponível|Disponível|Disponível|
|Integração entre produtos|Incorporar no SharePoint Online com a parte Web do Power BI|Não disponível|Não disponível|Não disponível|
|  |Incorporar no SharePoint Online com a parte Web da Incorporação|Disponível|Disponível|Disponível|
|  |Fluxos de dados e funções de IA|Não disponível|Não disponível|Não disponível|
|  |Conectividade do Power Automate para alertas baseados em dados|Não disponível|Não disponível|Não disponível|
|  |Separador Power BI no Teams|Disponível|Não disponível|Não disponível|
|  |Machine Learning Automatizado|Não disponível|Não disponível|Não disponível|
|  |Serviços Cognitivos|Não disponível|Não disponível|Não disponível|
|  |Azure ML|Não disponível|Não disponível|Não disponível|

## <a name="next-steps"></a>Próximos passos

* [Inscrever-se no Power BI para a Administração Pública dos EUA](service-govus-signup.md)
* [Microsoft Power Apps US Government](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
* [Power Automate US Government](https://docs.microsoft.com/power-automate/us-govt)
* <a href="https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government">Demonstração do Power BI para a Administração Pública dos EUA</a>
