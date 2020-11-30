---
title: Linha de base da segurança do Azure do Power BI
description: A linha de base de segurança do Power BI proporciona diretrizes de procedimento e recursos para implementar as recomendações de segurança especificadas na Referência da Segurança do Azure.
author: msmbaldwin
ms.service: security
ms.topic: conceptual
ms.date: 11/20/2020
ms.author: mbaldwin
ms.custom: subject-security-benchmark
ms.openlocfilehash: b0eb2906463efa95615fa76f3f7dda2a91ef126a
ms.sourcegitcommit: 9d033abd9c01a01bba132972497dda428d7d5c12
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/24/2020
ms.locfileid: "95550571"
---
# <a name="azure-security-baseline-for-power-bi"></a>Linha de base da segurança do Azure do Power BI

Esta linha de base de segurança aplica-se às orientações da [versão 2.0 da Referência de Segurança do Azure](https://docs.microsoft.com/azure/security/benchmarks/overview) para o Power BI. A Referência de Segurança do Azure disponibiliza recomendações para proteger as suas soluções cloud no Azure. O conteúdo é agrupado pelos **controlos de segurança** definidos pela Referência de Segurança do Azure e pelas orientações relacionadas aplicáveis ao Power BI. Os **controlos** não aplicáveis ao Power BI foram excluídos.

Para ver como Power BI é completamente mapeado para a Referência de Segurança do Azure, veja o [ficheiro de mapeamento da linha de base de segurança do Power BI completo](https://github.com/MicrosoftDocs/SecurityBenchmarks/tree/master/Azure%20Offer%20Security%20Baselines).

## <a name="network-security"></a>Segurança de Rede

*Para obter mais informações, veja [Referência de Segurança do Azure: Segurança de Rede](/azure/security/benchmarks/security-controls-v2-network-security).*

### <a name="ns-3-establish-private-network-access-to-azure-services"></a>NS-3: Estabelecer o acesso à rede privada para os serviços do Azure

**Orientação**: o Power BI suporta a ligação do inquilino do Power BI a um ponto final de Ligação privada e desativa o acesso à Internet pública.

- [Ligações privadas para aceder ao Power BI](https://docs.microsoft.com/power-bi/admin/service-security-private-links)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Partilhada

## <a name="identity-management"></a>Gestão de Identidades

*Para obter mais informações, veja [Referência de Segurança do Azure: Gestão de Identidades](/azure/security/benchmarks/security-controls-v2-identity-management).*

### <a name="im-1-standardize-azure-active-directory-as-the-central-identity-and-authentication-system"></a>IM-1: Uniformizar o Azure Active Directory como o sistema central de identidade e autenticação

**Orientação**: o Power BI está integrado no Azure Active Directory (AAD), que é a identidade predefinida do Azure e o serviço de gestão de acesso. Deve padronizar o AAD para governar a identidade da organização e a gestão de acesso.

A proteção do Azure AD deve ser prioritária na prática de segurança da cloud para a sua organização. O AAD proporciona uma pontuação de segurança de identidade para o ajudar a avaliar a postura de segurança de identidade relativamente às recomendações de melhores práticas da Microsoft. Utilize a pontuação para determinar até que ponto é que a sua configuração corresponde às recomendações de melhores práticas e para fazer melhorias à postura de segurança.

Nota: o AAD suporta identidades externas que permitem aos utilizadores sem uma conta da Microsoft iniciarem sessão nas aplicações e nos recursos com a identidade externa.

- [Inquilinos no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/single-and-multi-tenant-apps)

- [Como criar e configurar instâncias do Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-access-create-new-tenant)

- [Utilizar fornecedores de identidade externos para a aplicação](https://docs.microsoft.com/azure/active-directory/b2b/identity-providers)

- [O que é a pontuação de segurança de identidade no Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/fundamentals/identity-secure-score)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="im-2-manage-application-identities-securely-and-automatically"></a>IM-2: Gerir identidades de aplicação de forma segura e automática

**Orientação**: o Power BI e o Power BI Embedded suportam a utilização de Principais de Serviço. Guarde as credenciais do Principal de Serviço utilizadas para encriptar ou aceder ao Power BI num Key Vault, atribua políticas de acesso adequadas ao cofre e analise regularmente as permissões de acesso.

Automatize as tarefas dos conjuntos de dados e das áreas de trabalho Premium com os principais de serviço https://docs.microsoft.com/power-bi/admin/service-premium-service-principal

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="im-3-use-azure-ad-single-sign-on-sso-for-application-access"></a>IM-3: Utilizar o início de sessão único (SSO) do Azure AD para acesso a aplicações

**Orientação**: o Power BI utiliza o Azure Active Directory para permitir a gestão de acesso e identidade a recursos do Azure, aplicações cloud e aplicações no local. Essas identidades incluem identidades empresariais, como colaboradores, bem como identidades externas, como parceiros, fornecedores e distribuidores. Com isto, o início de sessão único (SSO) pode gerir e proteger o acesso aos dados e recursos da sua organização, tanto no ambiente no local, como na cloud. Ligue todos os seus utilizadores, aplicações e dispositivos ao Azure AD para beneficiar de acesso seguro e ininterrupto e de mais visibilidade e controlo.

- [Compreender o SSO de Aplicações com o Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="im-4-use-strong-authentication-controls-for-all-azure-active-directory-based-access"></a>IM-4: Utilizar controlos de autenticação fortes para todos os acessos baseados no Azure Active Directory

**Orientação**: o Power BI está integrado no AAD que suporta controlos de autenticação fortes através da autenticação multifator (MFA) e métodos sem palavra-passe fortes.
- Autenticação multifator - ative o MFA do Azure AD e siga as recomendações de Gestão de Identidades e Acessos do Centro de Segurança do Azure para obter algumas melhores práticas na configuração do MFA. O MFA pode ser imposto em todos os utilizadores, utilizadores específicos ou utilizador a utilizador com base em condições de início de sessão e fatores de risco.
- Autenticação sem palavra-passe - estão disponíveis três opções de autenticação sem palavra-passe: Windows Hello para Empresas, aplicação Microsoft Authenticator e métodos de autenticação no local, como cartões inteligentes.

Para utilizadores privilegiados e administradores, confirme que é utilizado o nível mais elevado de autenticação forte, seguido pela implementação de uma política de autenticação forte para os outros utilizadores.

Nota: a MFA só pode ser imposta para contas de utilizador ativadas no AAD. Os Principais de Serviço do Power BI não suportam a utilização da MFA.

- [Como ativar o MFA no Azure](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted)

- [Introdução às opções de autenticação sem palavra-passe para o Azure Active Directory](https://docs.microsoft.com/azure/active-directory/authentication/concept-authentication-passwordless)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="im-5-monitor-and-alert-on-account-anomalies"></a>IM-5: Monitorizar e alertar para anomalias em contas

**Orientação**: defina as políticas de deteção de anomalias do Microsoft Cloud App Security, que podem ser confinadas de forma independente, de modo a que se apliquem apenas aos utilizadores e grupos que quer incluir. Estas políticas de deteção de anomalias podem ajudar a detetar e a monitorizar anomalias de comportamento relacionadas com o acesso e utilização do Power BI pelos utilizadores.

- [Utilizar os Controlos do Microsoft Cloud App Security no Power BI](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="im-6-restrict-azure-resource-access-based-on-conditions"></a>IM-6: Restringir o acesso aos recursos do Azure com base em condições

**Orientação**: o Power BI suporta o acesso condicional ao AAD para um controlo de acesso mais granular com base em condições definidas pelo utilizador, por exemplo, os inícios de sessão de utilizador de certos intervalos de IP terão de utilizar a MFA para iniciar sessão. A política de gestão de sessão de autenticação granular também pode ser utilizada para diferentes casos de utilização.

- [Descrição geral do acesso condicional do Azure](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)

- [Políticas de acesso condicional comuns](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-policy-common)

- [Configurar a gestão da sessão de autenticação com o acesso condicional](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime)

- [Utilizar os Controlos do Microsoft Cloud App Security no Power BI](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="im-7-eliminate-unintended-credential-exposure"></a>IM-7: Eliminar a exposição de credenciais involuntária

**Orientação**: para as aplicações incorporadas do Power BI, é recomendado implementar o Scanner de Credenciais para identificar as credenciais no código. O Scanner de Credenciais também vai incentivar a movimentação das credenciais descobertas para localizações mais seguras, por exemplo, o Azure Key Vault.

Guarde as chaves de encriptação ou as credenciais do Principal de Serviço utilizadas para encriptar ou aceder ao Power BI num Key Vault, atribua políticas de acesso adequadas ao cofre e analise regularmente as permissões de acesso.
 
No GitHub, pode utilizar a funcionalidade de análise de segredos nativos para identificar as credenciais ou outra forma de segredos no código.

- [Chaves de encriptação por BYOK (Bring Your Own Key) para o Power BI](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

 
Como configurar a Credencial
- [Scanner](https://secdevtools.azurewebsites.net/helpcredscan.html) 

- [Análise de segredos do GitHub](https://docs.github.com/github/administering-a-repository/about-secret-scanning)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Partilhada

## <a name="privileged-access"></a>Acesso Privilegiado

*Para obter mais informações, veja [Referência de Segurança do Azure: Acesso Privilegiado](/azure/security/benchmarks/security-controls-v2-privileged-access).*

### <a name="pa-1-protect-and-limit-highly-privileged-users"></a>PA-1: Proteger e limitar utilizadores com muitos privilégios

**Orientação**: para reduzir o risco e seguir o princípio de privilégios mínimos, é recomendado manter a associação dos administradores do Power BI a um número reduzido de pessoas. Os utilizadores com estas permissões privilegiadas podem, potencialmente, aceder e modificar todas as funcionalidades de gestão da organização. Os administradores globais, através do Microsoft 365 ou do Azure Active Directory, possuem também, implicitamente, direitos de administrador no serviço Power BI.

O Power BI possui as seguintes contas altamente privilegiadas:
- Administrador global
- Administrador de faturação
- Administrador de licenças
- Administrador de utilizadores
- Administração do Power BI
- Administrador de Capacidade do Power BI Premium
- Administrador de Capacidade do Power BI Embedded

O Power BI suporta políticas de sessão no AAD, para ativar políticas de acesso condicional e encaminha sessões utilizadas no Power BI pelo serviço Cloud App Security.

Ative o acesso privilegiado JIT (just-in-time) das contas de administrador do Power BI com a Gestão de acesso privilegiado M365.

- [Funções de administrador relacionadas com o Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-administering-power-bi-in-your-organization#administrator-roles-related-to-power-bi)

- [Gestão de Acesso Privilegiado M365](https://docs.microsoft.com/microsoft-365/compliance/privileged-access-management-overview?view=o365-worldwide&amp;preserve-view=true)

- [Controlos do Cloud App Security no Power BI](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="pa-2-restrict-administrative-access-to-business-critical-systems"></a>PA-2: Restringir o acesso administrativo a sistemas críticos da empresa

**Orientação**: limite o número de contas ou funções altamente privilegiadas com acesso elevado ao Power BI.

Pode ativar o acesso privilegiado JIT (just-in-time) com orientação de Gestão de acesso privilegiado M365, [aqui](https://docs.microsoft.com/microsoft-365/compliance/privileged-access-management-overview?view=o365-worldwide&amp;preserve-view=true).

Pode encontrar detalhes adicionais na página 183 do documento de Implementação do Power BI Enterprise, [aqui](https://aka.ms/PBIEnterpriseDeploymentWP).

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="pa-3-review-and-reconcile-user-access-regularly"></a>PA-3: Rever e reconciliar o acesso dos utilizadores regularmente

**Orientação**: Enquanto administrador do serviço Power BI, pode analisar a utilização de todos os recursos do Power BI ao nível do inquilino ao utilizar relatórios personalizados com base no registo de atividades do Power BI. Pode transferir as atividades ao utilizar a API REST ou o cmdlet do PowerShell. Também pode filtrar os dados de atividade por intervalo de datas, utilizador e tipo de atividade.

Tem de cumprir estes requisitos para aceder aos registos de atividades do Power BI:
- Tem de ser um administrador global ou um administrador do serviço Power BI.
- Instalou os [cmdlets de Gestão do Power BI](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt) localmente ou utiliza os cmdlets de Gestão do Power BI no Azure Cloud Shell.

Após estes requisitos serem cumpridos, pode seguir a orientação abaixo, para monitorizar a atividade do utilizador dentro do Power BI:

- [Monitorizar a atividade dos utilizadores no Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="pa-4-set-up-emergency-access-in-azure-ad"></a>PA-4: Configurar o acesso de emergência no AAD

**Orientação**: o Power BI está integrado no Azure Active Directory e ao M365 para gerir os recursos. Para evitar ficar acidentalmente bloqueado fora do inquilino do M365 ou da organização do AAD, configure uma conta de acesso de emergência para obter acesso quando as contas administrativas normais não puderem ser utilizadas. As contas de acesso de emergência são, normalmente, altamente privilegiadas e não devem ser atribuídas a indivíduos específicos. As contas de acesso de emergência são limitadas a cenários de emergência ou de “interrupção de emergência”, em que as contas administrativas normais não podem ser utilizadas.

Deve garantir que as credenciais (por exemplo, palavra-passe, certificado ou smart card) das contas de acesso de emergência são mantidas em segurança e só são conhecidas por indivíduos que estão autorizados a utilizá-las apenas para uma emergência.

- [Gerir contas de acesso de emergência no AAD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-emergency-access)

- [Proteger as contas do M365](https://docs.microsoft.com/microsoft-365/campaigns/m365-campaigns-protect-admin-accounts)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="pa-6-use-privileged-access-workstations"></a>PA-6: Utilizar estações de trabalho privilegiadas

**Orientação**: As estações de trabalho seguras e isoladas são de importância crítica para a segurança de funções confidenciais, por exemplo, administradores, programadores e operadores de serviço de importância crítica. Utilize estações de trabalho de utilizador altamente seguras e/ou o Azure Bastion para tarefas administrativas relacionadas com a gestão do Power BI. Utilize o Azure Active Directory, a Proteção Avançada Contra Ameaças do Microsoft Defender (ATP) e/ou o Microsoft Intune para implementar uma estação de trabalho de utilizador gerida e segura para tarefas administrativas. As estações de trabalho seguras podem ser geridas centralmente para impor uma configuração segura, incluindo uma autenticação forte e linhas de base de software e hardware e acesso de rede e lógico restrito.

Compreender o acesso privilegiado
- [estações de trabalho](https://docs.microsoft.com/azure/active-directory/devices/concept-azure-managed-workstation)

- [Implementar uma estação de trabalho de acesso privilegiado](https://docs.microsoft.com/azure/active-directory/devices/howto-azure-managed-workstation)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

## <a name="data-protection"></a>Proteção de Dados

*Para obter mais informações, veja [Referência de Segurança do Azure: Proteção de dados](/azure/security/benchmarks/security-controls-v2-data-protection).*

### <a name="dp-1-discovery-classify-and-label-sensitive-data"></a>DP-1: Descobrir, classificar e etiquetar dados confidenciais

**Orientação**: utilize as etiquetas de confidencialidade da Proteção de Informações da Microsoft nos relatórios, dashboards, conjuntos de dados e fluxos de dados para proteger os conteúdos confidenciais contra o acesso não autorizado aos dados e contra a fuga de dados.

Utilize as etiquetas de confidencialidade da Proteção de Informações da Microsoft e etiquete os relatórios, dashboards, conjuntos de dados e fluxos de dados no serviço Power BI para proteger conteúdos confidenciais contra fugas e acessos não autorizado aos dados, quando os conteúdos são exportados do serviço Power BI para ficheiros Excel, PowerPoint e PDF.

- [Como aplicar etiquetas de confidencialidade no Power BI](https://docs.microsoft.com/power-bi/admin/service-security-apply-data-sensitivity-labels)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="dp-2-protect-sensitive-data"></a>DP-2: Proteger dados confidenciais

**Orientação**: o Power BI está integrado nas etiquetas de confidencialidade da Proteção de Informações da Microsoft para proteção de dados confidenciais. Para obter mais detalhes, veja [Etiquetas de confidencialidade da Proteção de Informações da Microsoft no Power BI](https://docs.microsoft.com/power-bi/admin/service-security-sensitivity-label-overview)

O Power BI permite que os utilizadores do serviço tragam a sua própria chave para proteger os dados inativos. Para obter mais detalhes, veja [Chaves de encriptação BYOK (Bring Your Own Key) do Power BI](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

Os clientes têm a opção de manter as origens de dados no local e aproveitar o Direct Query ou Live Connect com um gateway de dados no local para minimizar a exposição dos dados ao serviço cloud. Para obter mais detalhes, veja [O que é um gateway de dados no local?](https://docs.microsoft.com/data-integration/gateway/service-gateway-onprem)

O Power BI suporta a Segurança ao Nível de Linha. Para obter mais detalhes, veja [Segurança ao nível da linha (RLS) com o Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-rls). Tenha em atenção que a RLS pode ser aplicada mesmo em origens de dados do Direct Query e, nesse caso, o ficheiro PBIX age como um proxy que ativa a segurança.

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="dp-3-monitor-for-unauthorized-transfer-of-sensitive-data"></a>DP-3: Monitorizar a transferência não autorizada de dados confidenciais

**Orientação**: este controlo pode ser parcialmente alcançado com o suporte do Microsoft Cloud App Security para o Power BI.

Ao utilizar o Cloud App Security com o Power BI, pode ajudar a proteger os seus relatórios, dados e serviços do Power BI contra fugas ou falhas indesejadas. Com o Cloud App Security, pode criar políticas de acesso condicional para os dados da sua organização ao utilizar controlos de sessão em tempo real no Azure Active Directory (Azure AD), que ajudam a garantir a segurança das suas análises do Power BI. Uma vez definidas estas políticas, os administradores podem monitorizar o acesso e a atividade dos utilizadores, executar a análise dos riscos em tempo real e definir controlos específicos de uma etiqueta.

Utilizar
- [Controlos do Microsoft Cloud App Security no Power BI](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="dp-4-encrypt-sensitive-information-in-transit"></a>DP-4: Encriptar informações confidenciais em trânsito

**Orientação**: garanta que, para o tráfego HTTP, os clientes e as origens de dados que se ligam aos recursos do Power BI conseguem utilizar o TLS v1.2 ou superior.

- [Impor a utilização da versão do TLS](https://docs.microsoft.com/power-bi/admin/service-admin-power-bi-security#enforcing-tls-version-usage)

- [Informações sobre a Segurança TLS](https://docs.microsoft.com/security/engineering/solving-tls1-problem)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="dp-5-encrypt-sensitive-data-at-rest"></a>DP-5: Encripte os dados confidenciais inativos

**Orientação**: O Power BI encripta dados inativos e em processamento. Por predefinição, o Power BI utiliza chaves geridas pela Microsoft para encriptar os seus dados. As organizações podem optar por utilizar chaves próprias para encriptação de conteúdos de utilizadores em inatividade no Power BI, de imagens de relatórios a conjuntos de dados importados em capacidades Premium.

- [Utilizar o BYOK (Bring Your Own Key) no Power BI](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Partilhada

## <a name="asset-management"></a>Gestão de Recursos

*Para obter mais informações, veja [Referência de Segurança do Azure: Gestão de Ativos](/azure/security/benchmarks/security-controls-v2-asset-management).*

### <a name="am-1-ensure-security-team-has-visibility-into-risks-for-assets"></a>AM-1: Certifique-se de que a equipa de segurança tem visibilidade para os riscos dos ativos

**Orientação**: utilize o Azure Sentinel com os Registos de auditoria do Office do Power BI para garantir que a equipa de segurança tem visibilidade sobre os riscos para os recursos do Power BI.

- [Ligar os Registos do Office 365 ao Azure Sentinel](https://docs.microsoft.com/azure/sentinel/connect-office-365)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="am-2-ensure-security-team-has-access-to-asset-inventory-and-metadata"></a>AM-2: Garantir que a equipa de segurança tem acesso aos metadados e inventário dos recursos

**Orientação**: garanta que as equipas de segurança têm acesso a um inventário continuamente atualizado dos recursos do Power BI Embedded. As equipas de segurança, normalmente, precisam deste inventário para avaliar o potencial de exposição da organização a riscos emergentes e como um ponto de entrada para melhorias contínuas à segurança. 

O Azure Resource Graph pode ser consultado para detetar todos os recursos do Power BI Embedded nas subscrições.  

Organize logicamente os recursos de acordo com a taxonomia da organização, com as Etiquetas e com outros metadados no Azure (Nome, Descrição e Categoria).  

- [Como criar consultas com o Explorador do Azure Resource Graph](https://docs.microsoft.com/azure/governance/resource-graph/first-query-portal)

- [Guia de decisão de atribuição de nomes e de identificação de recursos](https://docs.microsoft.com/azure/cloud-adoption-framework/decision-guides/resource-tagging/?toc=/azure/azure-resource-manager/management/toc.json)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="am-3-use-only-approved-azure-services"></a>AM-3: Utilizar apenas os serviços do Azure aprovados

**Orientação**: o Power BI suporta implementações baseadas no Azure Resource Manager para o Power BI Embedded e pode restringir a implementação dos recursos através do Azure Policy com a definição de uma Política personalizada.

Utilize o Azure Policy para auditar e restringir que serviços os utilizadores podem aprovisionar no ambiente. Utilize o Azure Resource Graph para consultar e detetar recursos dentro das subscrições. Também pode utilizar o Azure Monitor para criar regras para acionar alertas quando um serviço não aprovado for detetado.

- [Como configurar e gerir o Azure Policy](https://docs.microsoft.com/azure/governance/policy/tutorials/create-and-manage)

Como negar um tipo de recurso específico com o
- [Azure Policy](https://docs.microsoft.com/azure/governance/policy/samples/built-in-policies#general)

Como criar consultas com o Azure
- [Explorador do Resource Graph](https://docs.microsoft.com/azure/governance/resource-graph/first-query-portal)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

## <a name="logging-and-threat-detection"></a>Registos e Deteção de Ameaças

*Para obter mais informações, veja [Referência de Segurança do Azure: Registos e Deteção de Ameaças](/azure/security/benchmarks/security-controls-v2-logging-threat-protection).*

### <a name="lt-2-enable-threat-detection-for-azure-identity-and-access-management"></a>LT-2: Ative a deteção de ameaças para a gestão de identidades e acessos do Azure

**Orientação**: encaminhe os registos do Power BI para o SIEM, que podem servir para configurar deteções de ameaças personalizadas. Adicionalmente, utilize os controlos do Microsoft Cloud App Security (MCAS) no Power BI para ativar a deteção de anomalias com o guia [aqui](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls).

- [Controlar as atividades dos utilizadores no Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="lt-3-enable-logging-for-azure-network-activities"></a>LT-3: Ativar o registo para atividades de rede do Azure

**Orientação**: o Power BI é uma oferta SaaS totalmente gerida e a configuração de rede subjacente e o início de sessão é da responsabilidade da Microsoft. Para clientes que utilizam Ligações Privadas, existem registos e monitorizações disponíveis que podem ser configuradas.

- [Início de sessão e monitorização da Ligação Privada](https://docs.microsoft.com/azure/private-link/private-link-overview#logging-and-monitoring)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Partilhada

### <a name="lt-4-enable-logging-for-azure-resources"></a>LT-4: Ativar o registo dos recursos do Azure

**Orientação**: Com o Power BI, tem duas opções para controlar a atividade de utilizador: o registo de atividades do Power BI e o registo de auditoria unificado. Estes registos contêm uma cópia completa dos dados de auditoria do Power BI, mas há várias diferenças importantes, tal como resumido abaixo.
 
Registo de Auditoria Unificado:

 
- Inclui eventos do SharePoint Online, do Exchange Online, do Dynamics 365 e de outros serviços para além dos eventos de auditoria do Power BI.

 
- Apenas os utilizadores com a função Ver Apenas Registos de Auditoria ou permissões dos Registos de Auditoria têm acesso, como administradores globais e auditores.

 
- Os administradores globais e os auditores podem pesquisar o registo de auditoria unificado com o Centro de Segurança do Microsoft 365 e o Centro de Conformidade do Microsoft 365.

 
- Os administradores globais e os auditores podem transferir as entradas do registo de auditoria com as APIs de Gestão e os cmdlets do Microsoft 365.

 
- Mantém os dados de auditoria durante 90 dias.

 
- Retém os dados de auditoria, mesmo que o inquilino seja transferido para outra região do Azure.
 
Registo de Atividades do Power BI:

 
- Inclui apenas os eventos de auditoria do Power BI.

 
 
- Os administradores globais e os administradores do serviço Power BI têm acesso.

 
- Ainda não existe uma interface de utilizador para pesquisar o registo de atividades.

 
- Os administradores globais e os administradores do serviço Power BI podem transferir as entradas do registo de atividades com uma API REST do Power BI e o cmdlet de gestão.

 
- Mantém os dados de atividade durante 30 dias.

 
- Não retém dados de auditoria quando o inquilino é transferido para outra região do Azure.

- [Dados de Auditoria do Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#operations-available-in-the-audit-and-activity-logs)

- [Registo de Atividades do Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-activity-log)

- [Registo de Auditoria do Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-audit-log)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Partilhada

### <a name="lt-5-centralize-security-log-management-and-analysis"></a>LT-5: Centralizar a análise e gestão do registo de segurança

**Orientação**: o Power BI centraliza os registos em dois locais: o registo de atividades do Power BI e o registo de auditoria unificado. Estes registos contêm uma cópia completa dos dados de auditoria do Power BI, mas há várias diferenças importantes, tal como resumido abaixo.
 

Registo de Auditoria Unificado:

- Inclui eventos do SharePoint Online, Exchange Online, Dynamics 365 e outros serviços além dos eventos de auditoria do Power BI.

- Apenas os utilizadores com a função Ver Apenas Registos de Auditoria ou permissões dos Registos de Auditoria têm acesso, como os administradores globais e os auditores.

- Os administradores globais e os auditores podem procurar no registo de auditoria unificado através do Centro de Segurança do Microsoft 365 e do Centro de Conformidade do Microsoft 365.

- Os administradores globais e os auditores podem transferir as entradas de registo de auditoria ao utilizar as APIs de Gestão e os cmdlets do Microsoft 365.

- Mantém os dados de auditoria durante 90 dias.

- Retém dados de auditoria, mesmo que o inquilino seja transferido para outra região do Azure.

 

Registo de Atividades do Power BI:

- Inclui apenas os eventos de auditoria do Power BI.

- Os administradores globais e os administradores do serviço Power BI têm acesso.

- Ainda não existe uma interface de utilizador para pesquisar o registo de atividades.

- Os administradores globais e os administradores do serviço Power BI podem transferir as entradas de registo de atividades ao utilizar uma API REST do Power BI e o cmdlet de gestão.

- Mantém os dados de atividade durante 30 dias.

- Não retém dados de auditoria quando o inquilino seja transferido para outra região do Azure.

- [Dados de Auditoria do Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#operations-available-in-the-audit-and-activity-logs)

- [Registo de Atividades do Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-activity-log)

- [Registo de Auditoria do Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-audit-log)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="lt-6-configure-log-storage-retention"></a>LT-6: Configurar a retenção de armazenamento dos registos

**Orientação**: configure as políticas de retenção de armazenamento dos Registos de auditoria do Office de acordo com a conformidade, a regulamentação e as necessidades comerciais.

- [Políticas de Retenção dos Registos de Auditoria do Office](https://docs.microsoft.com/microsoft-365/compliance/audit-log-retention-policies)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

## <a name="incident-response"></a>Resposta a Incidentes

*Para obter mais informações, veja [Referência de Segurança do Azure: Resposta a Incidentes](/azure/security/benchmarks/security-controls-v2-incident-response).*

### <a name="ir-1-preparation--update-incident-response-process-for-azure"></a>IR-1: Preparação – atualizar o processo de resposta a incidentes para o Azure

**Orientação**: Certifique-se de que a sua organização tem processos para responder a incidentes de segurança, que atualizou esses processos para o Azure e que os pratica regularmente para garantir a preparação.

- [Implementar a segurança em todo o ambiente empresarial](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [Guia de referência da resposta a incidentes](https://docs.microsoft.com/microsoft-365/downloads/IR-Reference-Guide.pdf)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="ir-2-preparation--setup-incident-notification"></a>IR-2: Preparação – configurar a notificação de incidentes

**Orientação**: Configure as informações de contacto dos incidentes de segurança no Centro de Segurança do Azure. A Microsoft utiliza estas informações de contacto para o contactar caso o Microsoft Security Response Center (MSRC) descobrir que os seus dados foram acedidos de forma ilícita ou não autorizada. Também tem opções para personalizar os alertas e as notificações de incidentes em diferentes serviços do Azure de acordo com as suas necessidades de resposta aos incidentes. 

- [Como definir o contacto de segurança do Centro de Segurança do Azure](https://docs.microsoft.com/azure/security-center/security-center-provide-security-contact-details)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="ir-3-detection-and-analysis--create-incidents-based-on-high-quality-alerts"></a>IR-3: Deteção e análise – criar incidentes com base em alertas de alta qualidade

**Orientação**: garanta que tem um processo para criar alertas de alta qualidade e medir a qualidade dos alertas. Desta forma, pode aprender lições com os incidentes passados e priorizar os alertas para os analistas, para que estes não percam tempo a lidar com falsos positivos.

Monitorize alertas relacionados com o Power BI no Microsoft Cloud App Security. Podem ser desenvolvidos alertas de alta qualidade com base na experiência de incidentes passados, origens da comunidade validadas e ferramentas designadas para gerar e limpar alertas através da fusão e correlação de origens de sinais diversas.

- [Monitorizar alertas no Cloud App Security](https://docs.microsoft.com/cloud-app-security/monitor-alerts)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="ir-4-detection-and-analysis--investigate-an-incident"></a>IR-4: Deteção e análise – investigar incidentes

**Orientação**: desenvolva um guia de respostas a incidentes para a sua organização. Realize exercícios para testar as capacidades de resposta a incidentes do sistema numa cadência regular. Identifique pontos fracos e lacunas e reavalie o plano, conforme necessário.

Confirme que existem planos escritos de resposta a incidentes, que definem todas as funções do pessoal, assim como as fases de manipulação/gestão de incidentes desde a deteção até à análise pós-incidente.

- [Descrição geral de incidentes na Proteção Contra Ameaças da Microsoft](https://docs.microsoft.com/microsoft-365/security/mtp/incidents-overview)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="ir-5-detection-and-analysis--prioritize-incidents"></a>IR-5: Deteção e análise – priorizar incidentes

**Orientação**: Dê contexto aos analistas quanto aos incidentes em que se devem concentrar primeiro tendo por base a gravidade dos alertas e a sensibilidade dos ativos. 

 
A Proteção Contra Ameaças da Microsoft aplica a análise de correlação e agrega todos as investigações e alertas relacionados a partir de diferentes produtos num incidente. A Proteção Contra Ameaças da Microsoft também aciona alertas exclusivos em atividades que apenas podem ser identificadas como maliciosas, tendo em conta a visibilidade ponto a ponto que a Proteção Contra Ameaças da Microsoft tem entre todo o património e conjunto de produtos. Ao fazê-lo, a Proteção Contra Ameaças da Microsoft relata uma história mais vasta dos ataques e permite que o analista das operações de segurança compreenda e lide com ameaças complexas na organização.

- [Priorizar incidentes na Proteção Contra Ameaças da Microsoft](https://docs.microsoft.com/microsoft-365/security/mtp/incident-queue?view=o365-worldwide&amp;preserve-view=true)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="ir-6-containment-eradication-and-recovery--automate-the-incident-handling"></a>IR-6: Contenção, erradicação e recuperação – automatizar o processamento dos incidentes

**Orientação**: Automatize tarefas manuais repetitivas para acelerar o tempo de resposta e reduzir a carga dos analistas. As tarefas manuais são mais morosas e atrasam todos os incidentes, reduzindo o número daqueles com que um analista pode lidar. Estas tarefas também aumentam a fadiga dos analistas, o que aumenta o risco de erro humanos e provoca atrasos, bem como degrada a capacidade de aqueles se concentrarem em tarefas complexas.  
 
Utilize as funcionalidades de automatização de fluxo de trabalho na Proteção Contra Ameaças da Microsoft para acionar automaticamente as investigações e a remediação em resposta aos alertas de segurança recebidos. 
 
- [Investigação e resposta automatizada na Proteção Contra Ameaças da Microsoft](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

## <a name="posture-and-vulnerability-management"></a>Gestão da Postura e da Vulnerabilidade

*Para obter mais informações, veja [Referência de Segurança do Azure: Gestão da Postura e da Vulnerabilidade](/azure/security/benchmarks/security-controls-v2-vulnerability-management).*

### <a name="pv-1-establish-secure-configurations-for-azure-services"></a>PV-1: Estabelecer configurações seguras para os serviços do Azure 

**Orientação**: configure o serviço Power BI com as definições adequadas para a sua organização e postura de segurança. As definições para acesso ao serviço e ao conteúdo, bem como a segurança das aplicações e das áreas de trabalho, devem ser consideradas cuidadosamente. Veja o documento técnico Segurança do Power BI e Proteção de Dados na Implementação do Power BI Enterprise.

- [Documento técnico de Implementação Empresarial](https://aka.ms/PBIEnterpriseDeploymentWP)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="pv-2-sustain-secure-configurations-for-azure-services"></a>PV-2: Suportar configurações seguras para os serviços do Azure

**Orientação**: monitorize a instância do Power BI com as APIs REST de Administração do Power BI.

- [APIs REST de Administração do Power BI](https://docs.microsoft.com/rest/api/power-bi/admin)

- [Power BI enterprise deployment whitepaper (Documento técnico sobre a implementação empresarial do Power BI)](https://aka.ms/PBIEnterpriseDeploymentWP)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="pv-8-conduct-regular-attack-simulation"></a>PV-8: Realizar simulações de ataques regulares

**Orientação**: Conforme necessário, faça testes de penetração ou atividades de "equipa de ataque" nos seus recursos do Azure e assegure a remediação de todas as descobertas de segurança críticas.

Para ter a certeza de que os seus testes de penetração não infringem as políticas da Microsoft, siga as Regras de Interação para Testes de Penetração da Microsoft Cloud. Utilize a estratégia e a execução de "Equipas de Ataque" e os testes de penetração no local em direto da Microsoft na infraestrutura, nos serviços e nas aplicações cloud geridas pela Microsoft.

- [Testes de Penetração no Azure](https://docs.microsoft.com/azure/security/fundamentals/pen-testing)

- [Regras de Interação para os Testes de Penetração](https://www.microsoft.com/msrc/pentest-rules-of-engagement?rtc=1)

- ["Equipa de Ataque" da Microsoft Cloud](https://gallery.technet.microsoft.com/Cloud-Red-Teaming-b837392e)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Partilhada

## <a name="backup-and-recovery"></a>Cópia de Segurança e Recuperação

*Para obter mais informações, veja [Referência de Segurança do Azure: Cópia de Segurança e Recuperação](/azure/security/benchmarks/security-controls-v2-backup-recovery).*

### <a name="br-3-validate-all-backups-including-customer-managed-keys"></a>BR-3: Validar todas as cópias de segurança, incluindo as chaves geridas pelo cliente

**Orientação**: se estiver a utilizar a funcionalidade Bring Your Own Key (BYOK) no Power BI, será preciso validar periodicamente a capacidade de aceder e restaurar as chaves geridas pelo cliente.

- [BYOK no Power BI](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="br-4-mitigate-risk-of-lost-keys"></a>BR-4: Mitigar o risco de perda de chaves

**Orientação**: se estiver a utilizar a funcionalidade Bring Your Own Key (BYOK) no Power BI, deve garantir que o Key Vault que controla as chaves geridas pelo cliente está configurado com a orientação apresentada na documentação BYOK no Power BI abaixo. Ative a eliminação recuperável e a proteção contra remoção no Azure Key Vault para proteger as chaves contra a eliminação maliciosa ou acidental.

- [BYOK no Power BI](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

- [Como ativar a eliminação recuperável e a proteção contra remoção no Key Vault](https://docs.microsoft.com/azure/storage/blobs/storage-blob-soft-delete?tabs=azure-portal)

Para os recursos de Chave de gateway, garanta que está a seguir as orientações na documentação Chave de recuperação de gateway, abaixo.

- [Chave de recuperação de gateway de dados no local](https://docs.microsoft.com/data-integration/gateway/service-gateway-recovery-key)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

## <a name="governance-and-strategy"></a>Governação e Estratégia

*Para obter mais informações, veja [Referência de Segurança do Azure: Governação e Estratégia](/azure/security/benchmarks/security-controls-v2-governance-strategy).*

### <a name="gs-1-define-asset-management-and-data-protection-strategy"></a>GS-1: Definir a gestão dos ativos e a estratégia de proteção de dados 

**Orientação**: Certifique-se de que documenta e comunica uma estratégia clara para a monitorização e proteção contínua dos sistemas e dos dados. Priorize a descoberta, a avaliação, a proteção e a monitorização de dados e sistemas críticos para a empresa. 

Esta estratégia deve incluir orientações, políticas e normas documentadas para os seguintes elementos: 

-   Norma para a classificação de dados, de acordo com os riscos da atividade

-   Visibilidade da organização de segurança para os riscos e inventário de ativos 

-   Aprovação da organização de segurança dos serviços do Azure a utilizar 

-   Segurança dos ativos ao longo do ciclo de vida

-   Estratégia de controlo de acesso obrigatória, de acordo com a classificação dos dados organizacionais

-   Utilização de capacidades de proteção de dados de terceiros e nativas do Azure

-   Requisitos de encriptação de dados para casos de utilização de dados em trânsito e inativos

-   Normas criptográficas adequadas

Para obter mais informações, veja as seguintes referências:
- [Recomendação de Arquitetura de Segurança do Azure - Armazenamento, dados e encriptação](https://docs.microsoft.com/azure/architecture/framework/security/storage-data-encryption?toc=/security/compass/toc.json&amp;bc=/security/compass/breadcrumb/toc.json)

- [Noções Básicas da Segurança do Azure - Segurança, encriptação e armazenamento de dados do Azure](https://docs.microsoft.com/azure/security/fundamentals/encryption-overview)

- [Cloud Adoption Framework - Melhores práticas de segurança e encriptação de dados do Azure](https://docs.microsoft.com/azure/security/fundamentals/data-encryption-best-practices?toc=/azure/cloud-adoption-framework/toc.json&amp;bc=/azure/cloud-adoption-framework/_bread/toc.json)

- [Referência de Segurança do Azure - Gestão de ativos](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-asset-management)

- [Referência de Segurança do Azure - Proteção de dados](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-data-protection)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="gs-2-define-enterprise-segmentation-strategy"></a>GS-2: Definir a estratégia de segmentação da empresa 

**Orientação**: Estabeleça uma estratégia ao nível de toda a empresa para segmentar o acesso aos ativos através de uma combinação de controlos de identidade, rede, aplicações, subscrições, grupos de gestão, entre outros.

Equilibre cuidadosamente a necessidade de separação da segurança com a necessidade de permitir o funcionamento diário dos sistemas que têm de comunicar entre si e aceder a dados.

Certifique-se de que a estratégia de segmentação está implementada de forma consistente em todos os tipos de controlos, incluindo segurança de rede, modelos de identidade e acesso e modelos de permissão/acesso a aplicações e controlos de processos humanos.

- [Orientação para a estratégia de segmentação no Azure (vídeo)](https://docs.microsoft.com/security/compass/microsoft-security-compass-introduction#azure-components-and-reference-model-2151)

- [Orientação para a estratégia de segmentação no Azure (documento)](https://docs.microsoft.com/security/compass/governance#enterprise-segmentation-strategy)

- [Alinhar a segmentação de rede com a estratégia de segmentação empresarial](https://docs.microsoft.com/security/compass/network-security-containment#align-network-segmentation-with-enterprise-segmentation-strategy)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="gs-3-define-security-posture-management-strategy"></a>GS-3: Definir a estratégia de gestão da postura de segurança

**Orientação**: Meça e mitigue continuamente os riscos para os seus ativos individuais e para o ambiente em que estão alojados. Dê prioridade aos ativos de valor alto e a superfícies de ataque muito expostas, como aplicações publicadas, pontos de entrada e saída de rede, pontos finais de utilizador e administrador, etc.

- [Referência de Segurança do Azure - Gestão da postura e das vulnerabilidades](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-posture-vulnerability-management)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="gs-4-align-organization-roles-responsibilities-and-accountabilities"></a>GS-4: Alinhar as funções, as responsabilidades e as responsabilizações na organização

**Orientação**: Certifique-se de que documenta e comunica uma estratégia clara para as funções e responsabilidades na sua organização de segurança. Estabeleça prioridades ao indicar de forma clara a responsabilização quanto às decisões de segurança, explicando o modelo de responsabilização partilhada a todos e explicando às equipas técnicas a tecnologia para proteger a cloud.

- [Melhor Prática de Segurança do Azure 1 – Pessoas: Explicar às Equipas o Percurso da Segurança da Cloud](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#1-people-educate-teams-about-the-cloud-security-journey)

- [Melhor Prática de Segurança do Azure 2 – Pessoas: Explicar às Equipas a Tecnologia de Segurança da Cloud](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#2-people-educate-teams-on-cloud-security-technology)

- [Melhor Prática de Segurança do Azure 3 – Processo: Atribuir Responsabilização Quanto às Decisões de Segurança da Cloud](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="gs-5-define-network-security-strategy"></a>GS-5: Definir uma estratégia de segurança de rede

**Orientação**: Crie uma abordagem à segurança de rede do Azure como parte da estratégia de controlo de acesso de segurança geral da sua organização.  

Esta estratégia deve incluir orientações, políticas e normas documentadas para os seguintes elementos: 

-   Gestão centralizada da rede e responsabilidade quanto à segurança

-   Modelo de segmentação de rede virtual alinhado com a estratégia de segmentação empresarial

-   Estratégia de remediação em diferentes cenários de ameaças e ataques

-   Estratégia de entrada e saída do edge da Internet

-   Estratégia de interconectividade entre a cloud híbrida e o ambiente no local

-   Artefactos de segurança de rede atualizados (por exemplo, diagramas de rede, arquitetura de rede de referência)

Para obter mais informações, veja as seguintes referências:
- [Melhor Prática de Segurança do Azure 11 – Arquitetura. Estratégia de segurança única e unificada](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Referência de Segurança do Azure - Segurança de Rede](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-network-security)

- [Descrição geral da segurança de rede do Azure](https://docs.microsoft.com/azure/security/fundamentals/network-overview)

- [Estratégia de arquitetura da rede empresarial](https://docs.microsoft.com/azure/cloud-adoption-framework/ready/enterprise-scale/architecture)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="gs-6-define-identity-and-privileged-access-strategy"></a>GS-6: Definir a estratégia de identidades e acessos privilegiados

**Orientação**: Crie uma abordagem às identidades e aos acessos privilegiados do Azure como parte da estratégia de controlo de acesso de segurança geral da sua organização.  

Esta estratégia deve incluir orientações, políticas e normas documentadas para os seguintes elementos: 

-   Um sistema de identidades e autenticação centralizado e respetiva interconectividade com outros sistemas de identidades internas e externas

-   Métodos de autenticação fortes em diferentes casos de utilização e condições

-   Proteção de utilizadores com muitos privilégios

-   Monitorização e processamento de atividades anómalas de utilizadores  

-   Processo de revisão e reconciliação de identidades e acessos dos utilizadores

Para obter mais informações, veja as seguintes referências:

- [Referência de Segurança do Azure - Gestão de identidades](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-identity-management)

- [Referência de Segurança do Azure - Acesso privilegiado](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-privileged-access)

- [Melhor Prática de Segurança do Azure 11 – Arquitetura. Estratégia de segurança única e unificada](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Descrição geral da segurança da gestão de identidades do Azure](https://docs.microsoft.com/azure/security/fundamentals/identity-management-overview)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="gs-7-define-logging-and-threat-response-strategy"></a>GS-7: Definir a estratégia de resposta a ameaças e registos

**Orientação**: Crie uma estratégia de resposta a ameaças e registos para detetar e remediar rapidamente as ameaças e cumprir, em paralelo, os requisitos de conformidade. Dê prioridade a proporcionar aos analistas alertas de alta qualidade e experiências totalmente integradas, para que se possam focar nas ameaças em vez de se focarem na integração e passos manuais. 

Esta estratégia deve incluir orientações, políticas e normas documentadas para os seguintes elementos: 

-   As funções e as responsabilidades da organização quanto às operações de segurança (SecOps) 

-   Processo de resposta a incidentes bem definido e alinhado com as normas da agência norte-americana NIST ou outro framework da indústria 

-   Captura e retenção de registos para suportar a deteção de ameaças, a resposta a incidentes e as necessidades de conformidade

-   Visibilidade centralizada e correlação de informações sobre ameaças, mediante a utilização de SIEM, das capacidades nativas do Azure e de outras origens 

-   Plano de comunicação e notificação com os seus clientes, fornecedores e partes interessadas públicas

-   Utilização de plataformas nativas do Azure e de terceiros para processamento de incidentes, como registo e deteção de ameaças, análises forenses e remediação e erradicação de ataques

-   Processos para lidar com incidentes e atividades pós-incidentes, como lições aprendidas e retenção de provas

Para obter mais informações, veja as seguintes referências:

- [Referência de Segurança do Azure - Registos e deteção de ameaças](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-logging-threat-detection)

- [Referência de Segurança do Azure - Resposta a incidentes](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-incident-response)

- [Melhor Prática de Segurança do Azure 4 – Processo. Atualizar os Processos de Resposta a Incidentes para a Cloud](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [Azure Adoption Framework, registos e guia de decisão de relatórios](https://docs.microsoft.com/azure/cloud-adoption-framework/decision-guides/logging-and-reporting/)

- [Escala, gestão e monitorização empresarial do Azure](https://docs.microsoft.com/azure/cloud-adoption-framework/ready/enterprise-scale/management-and-monitoring)

**Monitorização do Centro de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

## <a name="next-steps"></a>Passos seguintes

- Veja a [Descrição geral da Referência de Segurança do Azure v2](/azure/security/benchmarks/overview)
- Saiba mais sobre as [linhas de base de segurança do Azure](/azure/security/benchmarks/security-baselines-overview)
