---
title: Power BI para clientes do Governo Norte-Americano – Descrição Geral
description: Os clientes do Governo Norte-Americano podem adicionar uma subscrição do Power BI Pro ao plano do Microsoft 365 para o Governo Norte-Americano. Saiba como se inscrever, estabelecer ligação e rever a disponibilidade das funcionalidades nesta descrição do serviço.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/23/2020
ms.author: kfollis
ms.custom: licensing support
LocalizationGroup: Get started
ms.openlocfilehash: 45d89fe7a224d56e710765e533a7c075c24b8a66
ms.sourcegitcommit: 02484b2d7a352e96213353702d60c21e8c07c6c0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/13/2020
ms.locfileid: "91981510"
---
# <a name="power-bi-for-us-government-customers"></a>Power BI para clientes do Governo Norte-Americano

Este artigo é para clientes do Governo dos EUA que estão a implementar o Power BI como parte de um plano do Microsoft 365 para o Governo Norte-Americano. Os planos governamentais destinam-se às necessidades únicas das organizações que devem cumprir as normas de conformidade e segurança dos EUA. O serviço Power BI concebido para clientes do Governo Norte-Americano difere da versão comercial do serviço Power BI. Estas capacidades e diferenças das funcionalidades são descritas nas secções seguintes.

## <a name="add-power-bi-to-your-microsoft-365-government-plan"></a>Adicionar o Power BI ao Plano do Microsoft 365 para o Governo Norte-Americano

Para poder obter uma subscrição do Governo dos EUA do Power BI e atribuir licenças aos utilizadores, tem de se inscrever num plano do Microsoft 365 para o Governo Norte-Americano. Se a sua organização já tiver um plano do Microsoft 365 para o Governo Norte-Americano, avance para [Comprar uma subscrição do Power BI Pro para clientes do Governo Norte-Americano](#buy-a-power-bi-pro-subscription-for-government-customers).

### <a name="enroll-in-a-microsoft-365-government-plan"></a>Inscrever-se num Plano do Microsoft 365 para o Governo Norte-Americano

Se for um cliente novo, terá de validar a elegibilidade da sua organização para se poder inscrever num plano do Microsoft 365 para o Governo Norte-Americano.  Comece por preencher o [formulário de validação da elegibilidade do Microsoft 365 para o Governo Norte-Americano](https://www.microsoft.com/microsoft-365/government/eligibility-validation). Para garantir que seleciona o plano correto para a sua organização, veja [Descrições dos serviços do Microsoft 365 para o Governo dos EUA](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government).

> [!NOTE]
> Se já tiver implementado o Power BI num ambiente comercial e quiser migrar para a cloud do Governo dos EUA, terá de adicionar uma nova subscrição do Power BI Pro ao plano do Microsoft 365 para o Governo Norte-Americano. Em seguida, replique os dados comerciais para o serviço Power BI para o Governo Norte-Americano, remova as atribuições de licenças comerciais das contas dos utilizadores e, em seguida, atribua uma licença do Power BI Pro para o Governo às contas de utilizadores.
>
>
### <a name="buy-a-power-bi-pro-subscription-for-government-customers"></a>Compre uma subscrição do Power BI Pro para clientes do Governo Norte-Americano

Após implementar o Microsoft 365, pode adicionar uma subscrição do Power BI Pro. Siga a orientação passo a passo em [Inscrever a sua organização do Governo Norte-Americano](service-govus-signup.md) para comprar o serviço do Power BI Pro para o Governo Norte-Americano. Compre licenças suficientes para todos os utilizadores que precisam de utilizar o Power BI e, em seguida, atribua as licenças a contas de utilizadores individuais.

> [!IMPORTANT]
> O Power BI para o Governo Norte-Americano não está disponível com as licenças *Gratuitas* . Para aceder à cloud da comunidade governamental deve ser atribuída a cada utilizador uma licença *Pro* . Se uma conta de utilizador tiver atribuída uma licença Gratuita, estará autorizada a aceder apenas à cloud comercial e irá deparar-se com problemas de autenticação e acesso. Se tiver adquirido o Power BI Premium, não tem de atribuir licenças do Pro para permitir o acesso de utilizadores.  Os utilizadores na organização podem aceder aos relatórios partilhados com eles, desde que os relatórios sejam publicados com uma capacidade Premium. Para rever as diferenças entre os tipos de licença, veja [Funcionalidades do serviço Power BI por tipo de licença](../fundamentals/service-features-license-type.md).
>

## <a name="government-cloud-instances"></a>Instâncias da cloud para o Governo Norte-Americano

O Microsoft 365 disponibiliza diferentes ambientes para que as agências governamentais cumpram os diferentes requisitos de conformidade. Para obter mais informações sobre cada ambiente, veja:

* A [Cloud da Comunidade Governamental (GCC) do Microsoft 365](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) foi concebida para o governo federal, estadual e local.

* A [Cloud da Comunidade Governamental Elevada (GCC High) do Microsoft 365](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) foi concebida para as agências federais, a indústria de defesa, a indústria aeroespacial e outras organizações com informações não classificadas controladas. Este ambiente é adequado para organizações de segurança nacional e empresas com dados dos International Traffic in Arms Regulations (ITAR – Regulamentos sobre o Tráfico Internacional de Armas) ou requisitos do Defense Federal Acquisition Regulations Supplement (DFARS – Suplemento dos Regulamentos de Aquisições Federais do Departamento da Defesa).

* O [Ambiente DoD do Microsoft 365](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) foi concebido exclusivamente para o Departamento da Defesa dos EUA.


## <a name="sign-in-to-power-bi-for-us-government"></a>Iniciar sessão no Power BI para o governo norte-americano

O URL para ligação ao Power BI é diferente para utilizadores do Governo Norte-Americano e utilizadores comerciais. Para iniciar sessão no Power BI, utilize os seguintes URLs:

| Versão comercial  | GCC  | GCC High | DoD |
| --- | --- | --- | --- |
| [https://app.powerbi.com/](https://app.powerbi.com) |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) | [https://app.mil.powerbigov.us](https://app.mil.powerbigov.us) |

A sua conta pode estar configurada em mais de uma cloud. Se a conta estiver configurada desta forma, ao iniciar sessão no Power BI Desktop, poderá escolher a qual cloud ligar quando iniciar sessão.

## <a name="allow-connections-to-power-bi"></a>Permitir ligações ao Power BI

Para utilizar o serviço Power BI, tem de permitir ligações aos pontos finais necessários na Internet. Estes destinos têm de ser acessíveis, de modo a permitir a comunicação entre a sua rede, o Power BI e outros serviços dependentes.

Na tabela abaixo, apresentamos os pontos finais necessários a adicionar à lista de permissões para permitir a ligação ao serviço Power BI para utilização geral no site. Estes pontos finais são exclusivos à cloud do governo norte-americano. O serviço Power BI apenas requer que a Porta TCP 443 esteja aberta para os pontos finais listados. Os pontos finais de integração de dados, dashboards e relatórios, os elementos visuais do Power BI e outros serviços opcionais não são exclusivos à cloud do governo norte-americano. Para também adicionar estes URLs à lista de permissões, veja o artigo [Adicionar URLs do Power BI à lista de permissões](power-bi-whitelist-urls.md).

A autenticação, identidade e a administração do Power BI depende da conectividade aos serviços do Microsoft 365. Também tem de estabelecer ligação ao Microsoft 365 para ver os registos de auditoria. Para identificar os pontos finais destes serviços, veja a integração do Microsoft 365 na tabela abaixo.

### <a name="power-bi-urls-for-general-site-usage"></a>URLs do Power BI para utilização geral no site

|  Objetivo | Destino |
| ---- | ----- |
| APIs de back-end | **GCC** : api.powerbigov.us |
| | **GCC-High** : api.high.powerbigov.us |
| | **DoD** : api.mil.powerbi.gov.us |
| APIs de back-end | **GCC** : *analysis.usgovcloudapi.net |
| | **GCC High** : *.high.analysis.usgovcloudapi.net |
| | **DoD** : *.mil.analysis.usgovcloudapi.net |
| APIs de back-end | **Tudo** : *.pbidedicated.usgovcloudapi.net |
| Rede de Entrega de Conteúdos (CDN) | **GCC** : gov.content.powerapps.us |
| | **GCC High** : high.content.powerapps.us |
| | **DoD** : mil.content.powerapps.us |
| Integração do Microsoft 365 | **GCC** : [Pontos finais globais](/microsoft-365/enterprise/urls-and-ip-address-ranges) |
| | **GCC High** : [Pontos finais da GCC High do Governo Norte-Americano](/microsoft-365/enterprise/microsoft-365-u-s-government-gcc-high-endpoints) |
| | **DoD** : [Pontos finais do DoD do Governo Norte-Americano](/microsoft-365/enterprise/microsoft-365-u-s-government-dod-endpoints) |
| Portal |**GCC** : *.powerbigov.us |
| | **GCC-High** : *.high.powerbigov.us |
| | **DoD** : *.mil.powerbigov.us |
| Telemetria do serviço | **Tudo** : dc.services.visualstudio.us |
| Mensagens informativas (opcional) | **Tudo** : dynmsg.modpim.com |
| Inquéritos do NPS (opcional) | **Tudo** : nps.onyx.azure.net |

## <a name="connect-government-and-global-azure-cloud-services"></a>Ligar serviços cloud do Azure global e do Governo Norte-Americano

O Azure é distribuído entre várias clouds. Por predefinição, pode ativar regras da firewall para abrir uma ligação para uma instância específica da cloud, mas a rede entre clouds é diferente.  Para comunicar entre serviços na cloud pública e serviços na Cloud da Comunidade Governamental, tem de configurar regras específicas da firewall. Por exemplo, se quiser aceder a instâncias da cloud pública de uma base de dados do SQL a partir da sua implementação da cloud governamental do Power BI, precisará de uma regra da firewall na base de dados do SQL. Configure regras específicas da firewall para as bases de dados do SQL para permitir ligações à Cloud do Azure Government para os seguintes datacenters:

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona
* US DoD - Leste
* US DoD Centro

Para obter os intervalos de IP do Microsoft Cloud for US Government, transfira o ficheiro [Azure IP Ranges and Service Tags – Us Government Cloud](https://www.microsoft.com/download/details.aspx?id=57063) (Intervalos de IP do Azure e Etiquetas de Serviço – Microsoft Cloud for US Government). Os intervalos estão listados para o Power BI e Power Query.

Para obter mais informações sobre os serviços cloud do Microsoft Azure Government, veja a [documentação do Azure Government](/azure/azure-government/).

Para configurar firewalls para bases de dados do SQL, veja [Criar e gerir as regras de firewall de IP](/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules).

## <a name="power-bi-feature-availability"></a>Disponibilidade das funcionalidades do Power BI

Para cumprir os requisitos dos clientes da cloud governamental, existem algumas diferenças entre os planos governamentais e os planos comerciais. O nosso objetivo é tornar todas as funcionalidades disponíveis em clouds governamentais dentro de 30 dias da disponibilidade geral. Em alguns casos, as dependências subjacentes impedem-nos de tornar uma funcionalidade disponível.

A tabela seguinte apresenta as funcionalidades que não estão disponíveis num ambiente governamental específico. Incluímos a previsão de disponibilidade se a versão for planeado:

|Funcionalidade |GCC |GCC High |DoD|
|------|------|------|------|
|[Colaboração B2B do Azure entre a cloud comercial e governamental](service-admin-azure-ad-b2b.md)<sup>1</sup>|![disponível](../media/yes.png)|![não disponível](../media/no.png)|![não disponível](../media/no.png)|
|[Incorporar no SharePoint Online com a parte Web do Power BI](/sharepoint/dev/spfx/web-parts/overview-client-side-web-parts)|![disponível](../media/yes.png)|![Disponível](../media/yes.png)|![não disponível](../media/no.png)|
|[Conectividade do Power Automate para alertas baseados em dados](../connect-data/power-bi-data-sources.md)|![disponível](../media/yes.png)|![disponível](../media/yes.png)|![não disponível](../media/no.png)|
|[Separador Power BI no Teams](../collaborate-share/service-collaborate-microsoft-teams.md)<sup>2</sup>|![disponível](../media/yes.png)|![não disponível](../media/no.png)|![não disponível](../media/no.png)|
|[Modelos grandes](service-premium-large-models.md) | T4 de 2020 |T4 de 2020| ![não disponível](../media/no.png) |
|[Fluxos de dados – otimização do motor de computação SQL](../transform-model/service-dataflows-enhanced-compute-engine.md) | T4 de 2020 |T4 de 2020| ![não disponível](../media/no.png) |
|[Fluxos de dados – Direct Query](../transform-model/service-dataflows-directquery.md) | T4 de 2020 |T4 de 2020|![não disponível](../media/no.png)|
|[Service interruption notifications (Notificações de interrupção do serviço)](service-premium-large-models.md)|T4 de 2020 |T4 de 2020|T4 de 2020|
|[Proteção de Dados (Etiquetas da MIP)](service-security-sensitivity-label-overview.md)|T4 de 2020|T4 de 2020 |T4 de 2020|
|[Aplicações de modelo](../connect-data/service-template-apps-overview.md)<sup>3</sup>|T4 de 2020 |T4 de 2020| T4 de 2020|
|[Elementos Visuais Personalizados](../developer/visuals/power-bi-custom-visuals.md)<sup>3</sup>|T4 de 2020 |T4 de 2020| T4 de 2020|
|[Conector de Dados de Qualidade da Chamada](/microsoftteams/cqd-power-bi-connector)|![não disponível](../media/no.png)|![não disponível](../media/no.png)|![não disponível](../media/no.png)|
|[Geração de códigos QR](../create-reports/service-create-qr-code-for-tile.md)|![não disponível](../media/no.png)|![não disponível](../media/no.png)|![não disponível](../media/no.png)|

<sup>1</sup> Embora a Colaboração B2B esteja disponível para GCC, o utilizador externo deverá receber uma licença nesse ambiente. As licenças da cloud comercial não são válidas no GCC. Para obter mais informações sobre as limitações conhecidas com a Colaboração B2B para administração pública dos EUA, [Compare o Azure Government e o Azure global](/azure/azure-government/compare-azure-government-global-azure#azure-active-directory-premium-p1-and-p2)

<sup>2</sup> A experiência do Power BI no Teams para GCC é limitada e funciona apenas para áreas de trabalho clássicas. Não inclui a funcionalidade melhorada descrita em [Incorporar conteúdos do Power BI no Microsoft Teams](../collaborate-share/service-embed-report-microsoft-teams.md).

<sup>3</sup> As funcionalidades Aplicações de Modelo e Elementos Visuais Personalizados na versão serão limitadas a clouds governamentais. Serão publicadas mais informações sobre limites específicos na altura do lançamento.

## <a name="next-steps"></a>Próximos passos

* [Inscrever-se no Power BI para o Governo dos Estados-Unidos](service-govus-signup.md)
* [Microsoft Power Apps US Government](/power-platform/admin/powerapps-us-government)
* [Power Automate US Government](/power-automate/us-govt)
* [Demonstração do Power BI para a Administração Pública dos EUA](https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government)
