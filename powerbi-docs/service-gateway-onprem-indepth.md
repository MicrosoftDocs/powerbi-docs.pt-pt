---
title: Gateway de dados no local detalhado
description: Este artigo analisa detalhadamente o gateway no local. É abordado o funcionamento do serviço com o Azure Active Directory e o Active Directory local quando é utilizado o Analysis Services
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: ef4f9de49619a26e17fbdf2b0df47bc56ba23f4d
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54279326"
---
# <a name="on-premises-data-gateway-in-depth"></a>Gateway de dados no local detalhado
É possível que os utilizadores na sua organização acedam a dados no local (para os quais já tenham autorização de acesso), mas para se poderem ligar à sua origem de dados no local, é necessário instalar e configurar um Gateway de dados no local. O gateway facilita a comunicação rápida e segura em segundo plano entre um utilizador na cloud, a sua origem de dados no local e, em seguida, de volta para a cloud.

Normalmente, a instalação e configuração de um gateway é feita por um administrador. Pode requerer conhecimento especial dos seus servidores no local e, em alguns casos, pode exigir permissões de Administrador do Servidor.

Este artigo não fornece instruções passo-a-passo sobre como instalar e configurar um gateway. Para tal, veja [Gateway de dados no local](service-gateway-onprem.md). Este artigo serve para lhe fornecer um conhecimento aprofundado sobre a forma como o gateway funciona. Vamos ainda aprofundar os nomes de utilizador e a segurança no Azure Active Directory e no Analysis Services, e como o serviço cloud utiliza o endereço de e-mail de um utilizador que iniciou sessão, o gateway e o Active Directory para ligar e consultar em segurança os seus dados no local.

<!-- Shared Requirements Include -->
[!INCLUDE [gateway-onprem-requirements-include](./includes/gateway-onprem-how-it-works-include.md)]

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

## <a name="sign-in-account"></a>Conta de início de sessão
Os utilizadores vão iniciar sessão com uma conta escolar ou profissional. Esta é a conta da sua organização. Caso se tenha inscrito numa oferta do Office 365 e não indicou o seu e-mail profissional real, pode ter um aspeto semelhante a nancy@contoso.onmicrosoft.com. A sua conta, num serviço cloud, é armazenada num inquilino no Azure Active Directory (AAD). Na maioria dos casos, o UPN da sua conta AAD corresponderá ao endereço de e-mail.

## <a name="authentication-to-on-premises-data-sources"></a>Autenticação em origens de dados no local
Será utilizada uma credencial armazenada para ligar às origens de dados no local a partir do gateway, exceto o Analysis Services. Independentemente do utilizador individual, o gateway utiliza a credencial armazenada para estabelecer a ligação.

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Autenticação numa origem de dados dinâmicos do Analysis Services
Sempre que um utilizador interage com o Analysis Services, o nome de utilizador efetivo é transmitido ao gateway e, em seguida, ao servidor do Analysis Services no local. O nome principal de utilizador (UPN), normalmente o endereço de e-mail com que inicia sessão na cloud, é o que transmitimos ao Analysis Services como utilizador efetivo. O UPN é transmitido na propriedade de ligação EffectiveUserName. Este endereço de e-mail deve corresponder a um UPN definido no domínio do Active Directory local. O UPN é uma propriedade de uma conta do Active Directory. Essa conta do Windows deverá estar presente numa função do Analysis Services para ter acesso ao servidor. O início de sessão não será efetuado com êxito se não for encontrada nenhuma correspondência no Active Directory.

O Analysis Services também pode fornecer a filtragem com base nesta conta. A filtragem pode ocorrer com segurança baseada em funções ou segurança ao nível da linha.

## <a name="role-based-security"></a>Segurança baseada em funções
Os modelos fornecem uma segurança baseada nas funções de utilizadores. As funções são definidas para um determinado projeto modelo durante a criação de conteúdos no SQL Server Data Tools – Business Intelligence (SSDT-BI) ou após a implementação de um modelo com o SQL Server Management Studio (SSMS). As funções contêm membros por nome de utilizador do Windows ou grupo do Windows. As funções definem as permissões que um utilizador tem para consultar ou realizar ações no modelo. A maioria dos utilizadores irá pertencer a uma função com permissões de Leitura. As outras funções são destinadas a administradores com permissões para processar itens, gerir bases de dados e gerir outras funções.

## <a name="row-level-security"></a>Segurança ao nível da linha
A segurança ao nível da linha é específica do Analysis Services. Os modelos podem fornecer uma segurança dinâmica ao nível da linha. A segurança dinâmica não é necessária num modelo tabular, ao contrário do que acontece quando existe pelo menos uma função à qual os utilizadores pertencem. Num nível elevado, a segurança dinâmica define o acesso de leitura de um utilizador aos dados diretamente para uma linha específica numa determinada tabela. De forma semelhante às funções, a segurança ao nível da linha depende do nome de utilizador do Windows de um utilizador.

A capacidade de um utilizador consultar e ver dados de modelo é determinada, primeiro, pelas funções das quais a conta de utilizador do Windows é membro e, em segundo lugar, pela segurança ao nível da linha dinâmica, se estiver configurada.

A implementação de segurança baseada em funções e a segurança ao nível da linha dinâmica em modelos ultrapassa o âmbito deste artigo.  Pode saver mais em [Funções (SSAS Tabular)](https://msdn.microsoft.com/library/hh213165.aspx) e [Funções de Segurança (Analysis Services - Dados Multidimensionais)](https://msdn.microsoft.com/library/ms174840.aspx) no MSDN. Além disso, para obter uma compreensão mais detalhada da segurança do modelo de tabela, transfira e leia o documento técnico [Proteger o Modelo Semântico Tabular do BI](https://msdn.microsoft.com/library/jj127437.aspx).

## <a name="what-about-azure-active-directory"></a>E o Azure Active Directory?
Os serviços cloud da Microsoft utilizam o [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) para lidar com os utilizadores que estão a efetuar a autenticação. O Azure Active Directory é o inquilino que contém nomes de utilizador e grupos de segurança. Normalmente, o endereço de e-mail de início de sessão de um utilizador é o mesmo que o UPN da conta.

Qual é a minha função local do Active Directory?

Para o Analysis Services determinar se um utilizador que esteja a ligar ao mesmo pertence a uma função com permissões para leitura de dados, o servidor tem de converter o nome de utilizador efetivo transmitido do AAD para o gateway e, em seguida, para o servidor do Analysis Services. O servidor do Analysis Services transmite o nome de utilizador efetivo a um controlador de domínio (DC) do Windows Active Directory. Em seguida, o DC do Active Directory valida o nome de utilizador efetivo como um UPN válido numa conta local e devolve esse nome de utilizador do Windows ao servidor do Analysis Services.

Não é possível utilizar EffectiveUserName num servidor do Analysis Services não associado a um domínio. O servidor do Analysis Services tem de estar associado a um domínio para evitar erros de início de sessão.

## <a name="how-do-i-tell-what-my-upn-is"></a>Como posso saber qual é o meu UPN?
Pode não saber qual é o seu UPN nem ser um administrador do domínio. Pode utilizar o seguinte comando na sua estação de trabalho para descobrir o UPN da sua conta.

    whoami /upn

O resultado será semelhante a um endereço de e-mail, mas trata-se do UPN que está na sua conta de domínio local. Se estiver a utilizar uma origem de dados do Analysis Services para ligações em direto, este tem de corresponder ao que foi transmitido ao EffectiveUserName a partir do gateway.

## <a name="mapping-usernames-for-analysis-services-data-sources"></a>Mapeamento de nomes de utilizador para origens de dados do Analysis Services
O Power BI permite o mapeamento de nomes de utilizador para origens de dados do Analysis Services. Pode configurar regras para mapear um nome de utilizador com sessão iniciada no Power BI para um nome transmitido para o EffectiveUserName na ligação do Analysis Services. A funcionalidade de mapeamento nomes de utilizador é uma excelente forma de contornar o problema quando o seu nome de utilizador no AAD não corresponde a um UPN no Active Directory local. Por exemplo, se o seu endereço de e-mail for nancy@contoso.onmicrsoft.com, pode mapeá-lo para nancy@contoso.com, e esse valor será transmitido ao gateway. Pode saber mais sobre como [mapear nomes de utilizador](service-gateway-enterprise-manage-ssas.md#map-user-names).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Sincronizar uma conta do Active Directory no local com o Azure Active Directory
As contas do Active Directory local devem corresponder ao Azure Active Directory se utilizar ligações em direto do Analysis Services. Tal como o UPN tem de corresponder entre as contas.

Os serviços cloud apenas conhecem as contas no Azure Active Directory. É irrelevante se adicionou uma conta no Active Directory local; se esta não existir no AAD, não pode ser utilizada. Existem várias formas de corresponder as contas do Active Directory local ao Azure Active Directory.

1. Pode adicionar contas manualmente ao Azure Active Directory.
   
   Pode criar uma conta no portal do Azure ou no Portal de Administração do Office 365 e o nome da conta tem de corresponder ao UPN da conta do Active Directory local.
2. Pode utilizar a ferramenta [Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-sync-whatis) para sincronizar as contas locais no inquilino do Azure Active Directory.
   
   A ferramenta Azure AD Connect fornece opções para a sincronização de diretórios e a configuração da autenticação, incluindo a sincronização de hash da palavra-passe, autenticação pass-through e federação. Se não for um administrador do inquilino ou um administrador do domínio local, terá de contactar o administrador de TI para efetuar esta configuração.

A utilização do Azure AD Connect assegura que o UPN terá correspondência entre o AAD e o Active Directory local.

> [!NOTE]
> A sincronização de contas com a ferramenta Azure AD Connect criará novas contas no inquilino do AAD.
> 
> 

## <a name="now-this-is-where-the-gateway-comes-in"></a>É aqui que entra o gateway
O gateway funciona como uma ponte entre a cloud e o servidor no local. A transferência de dados entre a cloud e o gateway é protegida pelo [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview). O Service Bus cria um canal seguro entre a cloud e o servidor no local através de uma ligação de saída no gateway.  Não existem ligações de entrada que tenha de abrir na firewall no local.

Se tiver uma origem de dados do Analysis Services, terá de instalar o gateway num computador associado ao mesmo domínio que o seu servidor do Analysis Services.

Quanto mais próximo o gateway estiver do servidor, mais rápida será a ligação. Se conseguir colocar o gateway no mesmo servidor que a origem de dados, será a melhor opção para evitar a latência de rede entre o gateway e o servidor.

## <a name="what-to-do-next"></a>O que fazer a seguir?
Depois de instalar o gateway, tem de criar origens de dados para o mesmo. Pode adicionar origens de dados no ecrã **Gerir gateways**. Para obter mais informações, veja os artigos para gerir origens de dados.

[Gerir a sua origem de dados – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Gerir a sua origem de dados – SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Gerir a sua origem de dados – SQL Server](service-gateway-enterprise-manage-sql.md)  
[Gerir a sua origem de dados – Oracle](service-gateway-onprem-manage-oracle.md)  
[Gerir a sua origem de dados - Atualização Importada/Agendada](service-gateway-enterprise-manage-scheduled-refresh.md)  

## <a name="where-things-can-go-wrong"></a>O que pode correr mal
Por vezes, poderão ocorrer falhas ao instalar o gateway. Ou talvez a instalação do gateway pareça correr sem problemas, mas o serviço ainda não consegue trabalhar com o mesmo. Em muitos casos, é algo simples, como a palavra-passe das credenciais que o gateway utiliza para iniciar sessão na origem de dados.

Noutros casos, poderão existir problemas com o tipo de endereço de e-mail com que os utilizadores iniciam sessão ou o Analysis Services pode não conseguir resolver um nome de utilizador efetivo. Se tem vários domínios com relações de confiança entre eles e o gateway estiver num e o Analysis Services noutro, isto pode por vezes causar alguns problemas.

Em vez de explorar a resolução de problemas do gateway aqui, apresentamos uma série de passos de resolução de problemas noutro artigo: [Resolução de problemas do Gateway de dados no local](service-gateway-onprem-tshoot.md). Esperamos que não tenha nenhum problema. Caso contrário, poderá ser útil ter conhecimentos sobre a forma como tudo isto funciona e ler o artigo de resolução de problemas.

<!-- Account and Port information -->
[!INCLUDE [gateway-onprem-accounts-ports-more](./includes/gateway-onprem-accounts-ports-more.md)]

## <a name="next-steps"></a>Próximos passos

[Resolução de problemas do Gateway de dados no local](service-gateway-onprem-tshoot.md)  
[Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview/)  
[Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-sync-whatis/)  

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

