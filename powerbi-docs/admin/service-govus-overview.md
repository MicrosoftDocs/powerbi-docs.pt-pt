---
title: Power BI para clientes do Governo Norte-Americano – Descrição Geral
description: Os clientes do Governo Norte-Americano podem adicionar uma subscrição do Power BI Pro ao plano do Microsoft 365 para o Governo Norte-Americano. Saiba como se inscrever e rever a disponibilidade das funcionalidades nesta descrição do serviço.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/27/2020
ms.author: kfollis
ms.custom: licensing support
LocalizationGroup: Get started
ms.openlocfilehash: f4f0bc5de0480748344fa029c774c4d262facc08
ms.sourcegitcommit: 3f864ec22f99ca9e25cda3a5abda8a5f69ccfa8e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2020
ms.locfileid: "84159703"
---
# <a name="power-bi-for-us-government-customers"></a>Power BI para clientes do Governo Norte-Americano
Este artigo é para clientes do Governo dos EUA que estão a implementar o Power BI como parte de um plano do Microsoft 365 para o Governo Norte-Americano. Os planos governamentais destinam-se às necessidades únicas das organizações que devem cumprir as normas de conformidade e segurança dos EUA. O serviço Power BI concebido para clientes do Governo Norte-Americano difere da versão comercial do serviço Power BI. Estas capacidades e diferenças das funcionalidades são descritas nas secções seguintes.

## <a name="add-power-bi-to-your-microsoft-365-government-plan"></a>Adicionar o Power BI ao Plano do Microsoft 365 para o Governo Norte-Americano

Para poder obter uma subscrição do Governo dos EUA do Power BI e atribuir licenças aos utilizadores, tem de se inscrever num plano do Microsoft 365 para o Governo Norte-Americano. Se a sua organização já tiver um plano do Microsoft 365 para o Governo Norte-Americano, avance para [Comprar uma subscrição do Power BI Pro para clientes do Governo Norte-Americano](#buy-a-power-bi-pro-subscription-for-government-customers).

### <a name="enroll-in-a-microsoft-365-government-plan"></a>Inscrever-se num Plano do Microsoft 365 para o Governo Norte-Americano

Se for um cliente novo, terá de validar a elegibilidade da sua organização para se poder inscrever num plano do Microsoft 365 para o Governo Norte-Americano.  Comece por preencher o [formulário de validação da elegibilidade do Microsoft 365 para o Governo Norte-Americano](https://www.microsoft.com/microsoft-365/government/eligibility-validation). Para garantir que seleciona o plano correto para a sua organização, veja [Descrições dos serviços do Microsoft 365 para o Governo dos EUA](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government).

> [!NOTE]
> Se já tiver implementado o Power BI num ambiente comercial e quiser migrar para a cloud do Governo dos EUA, terá de adicionar uma nova subscrição do Power BI Pro ao plano do Microsoft 365 para o Governo Norte-Americano. Em seguida, replique os dados comerciais para o serviço Power BI para o Governo Norte-Americano, remova as atribuições de licenças comerciais das contas dos utilizadores e, em seguida, atribua uma licença do Power BI Pro para o Governo às contas de utilizadores.
>
>
## <a name="government-cloud-instances"></a>Instâncias da cloud para o Governo Norte-Americano
O Microsoft 365 disponibiliza diferentes ambientes para que as agências governamentais cumpram os diferentes requisitos de conformidade. Para obter mais informações sobre cada ambiente, veja:

* A [Cloud da Comunidade Governamental (GCC) do Microsoft 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) foi concebida para o governo federal, estadual e local.

* A [Cloud da Comunidade Governamental Elevada (GCC High) do Microsoft 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) foi concebida para as agências federais, a indústria de defesa, a indústria aeroespacial e outras organizações com informações não classificadas controladas. Este ambiente é adequado para organizações de segurança nacional e empresas com dados dos International Traffic in Arms Regulations (ITAR – Regulamentos sobre o Tráfico Internacional de Armas) ou requisitos do Defense Federal Acquisition Regulations Supplement (DFARS – Suplemento dos Regulamentos de Aquisições Federais do Departamento da Defesa).

* O [Ambiente DoD do Microsoft 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) foi concebido exclusivamente para o Departamento da Defesa dos EUA. 

## <a name="connect-to-power-bi-for-us-government"></a>Ligar ao Power BI para o Governo Norte-Americano

O URL para ligação ao Power BI é diferente para utilizadores do Governo Norte-Americano e utilizadores comerciais. Para iniciar sessão no Power BI, utilize os seguintes URLs:

| Versão comercial  | GCC  | GCC High | DoD |
| --- | --- | --- | --- |
| [https://app.powerbi.com/](https://app.powerbi.com) |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) | [https://app.mil.powerbigov.us](https://app.mil.powerbigov.us) |

A sua conta pode estar configurada em mais de uma cloud. Se a conta estiver configurada desta forma, ao iniciar sessão no Power BI Desktop, poderá escolher a qual cloud ligar quando iniciar sessão.

## <a name="buy-a-power-bi-pro-subscription-for-government-customers"></a>Compre uma subscrição do Power BI Pro para clientes do Governo Norte-Americano

Após implementar o Microsoft 365, pode adicionar uma subscrição do Power BI Pro. Siga a orientação passo a passo em [Inscrever a sua organização do Governo Norte-Americano](service-govus-signup.md) para comprar o serviço do Power BI Pro para o Governo Norte-Americano. Compre licenças suficientes para todos os utilizadores que precisam de utilizar o Power BI e, em seguida, atribua as licenças a contas de utilizadores individuais.

> [!IMPORTANT]
> O Power BI para o Governo Norte-Americano não está disponível com as licenças *Gratuitas*. Para aceder à cloud da comunidade governamental deve ser atribuída a cada utilizador uma licença *Pro*. Se uma conta de utilizador tiver atribuída uma licença Gratuita, estará autorizada a aceder apenas à cloud comercial e irá deparar-se com problemas de autenticação e acesso. Se tiver adquirido o Power BI Premium, não tem de atribuir licenças do Pro para permitir o acesso de utilizadores.  Os utilizadores na organização podem aceder aos relatórios partilhados com eles, desde que os relatórios sejam publicados com uma capacidade Premium. Para rever as diferenças entre os tipos de licença, veja [Funcionalidades do serviço Power BI por tipo de licença](../fundamentals/service-features-license-type.md).
>

## <a name="connect-government-and-global-azure-cloud-services"></a>Ligar serviços cloud do Azure global e do Governo Norte-Americano

O Azure é distribuído entre várias clouds. Por predefinição, pode ativar regras da firewall para abrir uma ligação para uma instância específica da cloud, mas a rede entre clouds é diferente.  Para comunicar entre serviços na cloud pública e serviços na Cloud da Comunidade Governamental, tem de configurar regras específicas da firewall. Por exemplo, se quiser aceder a instâncias da cloud pública de uma base de dados do SQL a partir da sua implementação da cloud governamental do Power BI, precisará de uma regra da firewall na base de dados do SQL. Configure regras específicas da firewall para as bases de dados do SQL para permitir ligações à Cloud do Azure Government para os seguintes datacenters:

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona

Os intervalos de IP estão disponíveis na cloud pública. Para obter os intervalos de IP do Microsoft Cloud for US Government, transfira o ficheiro [Azure IP Ranges and Service Tags – Us Government Cloud](https://www.microsoft.com/download/details.aspx?id=57063) (Intervalos de IP do Azure e Etiquetas de Serviço – Microsoft Cloud for US Government). 

Para configurar firewalls para bases de dados do SQL, veja [Criar e gerir as regras de firewall de IP](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules).

## <a name="power-bi-feature-availability"></a>Disponibilidade das funcionalidades do Power BI

Para cumprir os requisitos dos clientes da cloud governamental, existem algumas diferenças entre os planos governamentais e os planos comerciais. Para ver quais as funcionalidades disponíveis em cada ambiente governamental, veja a tabela seguinte:

|Funcionalidade |   |GCC |GCC High |DoD|
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
|  |Relatórios paginados|Disponível|Previsto|Previsto|
|  |Aplicações de modelo|Não disponível|Não disponível|Não disponível|
|Ligar-se a dados|Importar dados e relatórios do Excel|Disponível|Disponível|Disponível|
|  |Importar dados de ficheiros CSV|Disponível|Disponível|Disponível|
|  |Importar dados de ficheiros do Power BI Desktop|Disponível|Disponível|Disponível|
|  |Conectividade para CDS|Disponível|Não disponível|Não disponível|
|  |Conector do Azure Data Lake Storage Gen2|Disponível|Não disponível|Não disponível|
|Gestão de dados|Gateway de gestão de dados|Disponível|Disponível|Disponível|
|  |Encriptação de dados na Base de Dados SQL do Azure|Disponível|Disponível|Disponível|
|  |Encriptação de dados no Armazenamento de Blobs do Power BI|Disponível|Disponível|Disponível|
|Integração entre produtos|Incorporar no SharePoint Online com a parte Web do Power BI|Disponível|Não disponível|Não disponível|
|  |Incorporar no SharePoint Online com a parte Web da Incorporação|Disponível|Disponível|Disponível|
|  |Fluxos de dados e funções de IA|Não disponível|Não disponível|Não disponível|
|  |Conectividade do Power Automate para alertas baseados em dados|Não disponível|Não disponível|Não disponível|
|  |Separador Power BI no Teams|Disponível|Não disponível|Não disponível|
|  |Machine Learning Automatizado|Não disponível|Não disponível|Não disponível|
|  |Serviços Cognitivos do Azure|Não disponível|Não disponível|Não disponível|
|  |Azure Machine Learning|Não disponível|Não disponível|Não disponível|

## <a name="next-steps"></a>Próximos passos

* [Inscrever-se no Power BI para o Governo dos Estados-Unidos](service-govus-signup.md)
* [Microsoft Power Apps US Government](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
* [Power Automate US Government](https://docs.microsoft.com/power-automate/us-govt)
* <a href="https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government">Demonstração do Power BI para a Administração Pública dos EUA</a>
