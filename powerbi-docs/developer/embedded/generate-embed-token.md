---
title: Considerações para gerar um token de incorporação na análise incorporada do Power BI para obter melhores informações de BI incorporada
description: Saiba mais sobre as considerações, as limitações e as permissões necessárias para gerar um token de incorporação. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.custom: ''
ms.date: 10/15/2020
ms.openlocfilehash: 2f8da415b40bc5d9a621e5a0df8c1edffbbc8791
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97886862"
---
# <a name="considerations-when-generating-an-embed-token"></a>Considerações ao gerar um token de incorporação

[Gerar token](/rest/api/power-bi/embedtoken) é uma API REST que permite gerar um token para incorporar um item do Power BI numa aplicação Web ou num portal. O token serve para autorizar o seu pedido em relação ao serviço Power BI.

A API gerar token usa uma identidade individual (um utilizador principal ou um principal de serviço) para gerar um token para um utilizador individual, consoante as credenciais do utilizador na aplicação (identidade efetiva).

Após a autenticação bem-sucedida, o acesso aos dados relevantes é concedido.

>[!NOTE]
>Gerar token só é aplicável quando está a [*incorporar para os seus clientes*](embed-sample-for-customers.md) (também conhecido como cenário *os dados pertencem à aplicação*).

Pode usar as seguintes APIs para gerar um token:

* [Dashboards](/rest/api/power-bi/embedtoken/dashboards_generatetokeningroup)

* [Conjuntos de dados](/rest/api/power-bi/embedtoken/datasets_generatetokeningroup)

* [Gerar token para vários relatórios](/rest/api/power-bi/embedtoken/generatetoken)


* [Criação de relatórios](/rest/api/power-bi/embedtoken/reports_generatetokenforcreateingroup)

* [Relatórios](/rest/api/power-bi/embedtoken/reports_generatetokeningroup)

* [Mosaicos](/rest/api/power-bi/embedtoken/tiles_generatetokeningroup)

## <a name="workspace-versions"></a>Versões da área de trabalho

O Power BI tem duas versões de área de trabalho, uma área de trabalho *clássica* e uma área de trabalho *nova*. Pode saber mais sobre as diferenças entre estas áreas de trabalho em [diferenças entre área de trabalho nova e clássica](../../collaborate-share/service-new-workspaces.md#new-and-classic-workspace-differences).

Ao criar um token de incorporação, as diferentes áreas de trabalho têm considerações diferentes e exigem permissões diferentes.

|                  |Área de trabalho *clássica* |Área de trabalho *nova*|
|------------------|---------|--------|
|**Considerações**|<li>O conjunto de dados e o item têm de estar na mesma área de trabalho</li><li>O principal de serviço não pode ser usado</li>  |O conjunto de dados e o item podem estar em duas áreas de trabalho *novas* diferentes |
|**Permissões de áreas de trabalho**|O utilizador principal tem de ser um administrador da área de trabalho  |O principal de serviço ou o utilizador principal tem de ser pelo menos um membro de ambas as áreas de trabalho |

>[!NOTE]
>* Não é possível criar um token de incorporação para [A minha área de trabalho](../../consumer/end-user-workspaces.md#types-of-workspaces).
>* A palavra *item* refere-se a um item do Power BI, como um dashboard, mosaico, Perguntas e Respostas ou relatório.

## <a name="securing-your-data"></a>Proteger os seus dados

Ao criar sua solução, considere estas duas abordagens para proteger os seus dados:

* [Isolamento baseado na área de trabalho](embed-multi-tenancy.md#power-bi-workspace-based-isolation)

* [Isolamento baseado na segurança ao nível da linha](embed-multi-tenancy.md#row-level-security-based-isolation)

Se pretende usar a abordagem RLS, reveja as [considerações e limitações da RLS](generate-embed-token.md#row-level-security) no final deste artigo.

## <a name="token-permissions"></a>Permissões de tokens

Nas APIs gerar tokens, a secção *GenerateTokenRequest* descreve as permissões de tokens.

>[!NOTE]
>As permissões de token listadas nesta secção não são aplicáveis para a API [Gerar token para vários relatórios](/rest/api/power-bi/embedtoken/generatetoken).

### <a name="access-level"></a>Nível de Acesso

Use o parâmetro *accessLevel* para determinar o nível de acesso do utilizador.

* **Ver** – Conceda ao utilizador permissões de visualização.

* **Editar** – Conceda ao utilizador permissões de visualização e edição (aplica-se apenas quando gerar um token de incorporação para um relatório).

    Se estiver a utilizar a API [Gerar token para vários relatórios](/rest/api/power-bi/embedtoken/generatetoken), use o parâmetro *allowEdit* para conceder ao utilizador as permissões de visualização e edição.

* **Criar** – Conceda ao utilizador permissões para criar um relatório (aplicável apenas quando gerar um token de incorporação para criar um relatório).

    Para a criação de relatórios, também tem de fornecer o parâmetro *datasetId*.

### <a name="saving-a-copy-of-the-report"></a>Guardar uma cópia do relatório

Utilize o booleano *allowSaveAs* para permitir que os utilizadores guardem o relatório como um novo relatório. Por predefinição, esta definição encontra-se definida como *falsa*.

Este parâmetro só é aplicável quando gerar um token de incorporação para um relatório.

### <a name="row-level-security"></a>Segurança a Nível da Linha

Com a [Segurança ao Nível da Linha (RLS)](embedded-row-level-security.md), pode optar por usar uma identidade diferente da identidade da entidade do principal de serviço ou do utilizador principal com o qual está a gerar o token. Através desta opção, pode apresentar informações incorporadas de acordo com o utilizador que está a visar. Por exemplo, na sua aplicação, pode solicitar que os utilizadores iniciem sessão e, em seguida, apresentar um relatório que contém apenas informações de vendas se o utilizador com sessão iniciada for um funcionário de vendas.

Se estiver a utilizar RLS, poderá, em certos casos, não incluir a identidade do utilizador (o parâmetro *EffectiveIdentity*). Isto permite que o token tenha acesso à base de dados completa. Este método pode ser usado para conceder acesso a utilizadores como administradores e gestores, que têm as permissões para ver o conjunto de dados completo. No entanto, não pode utilizar este método em todos os cenários. A tabela seguinte lista os diferentes tipos de RLS e mostra qual método de autenticação pode ser usado sem especificar a identidade de um utilizador.

A tabela também mostra as considerações e a limitação aplicáveis a cada tipo de RLS.

|Tipo de RLS  |Posso gerar um token de incorporação sem especificar a ID de utilizador efetiva?  |Considerações e limitações  |
|---------|---------|---------|
|Segurança ao Nível da Linha na Cloud (RLS de Cloud)      |✔ Utilizador principal<br/>✖ Principal de serviço          |         |
|RDL (relatórios paginados)     |✖ Utilizador principal<br/>✔ Principal de serviço        |Não pode usar um utilizador principal para gerar um token de incorporação para RDL.         |
|Ligação em direto no local do Analysis Services (AS)    |✔ Utilizador principal<br/>✖ Principal de serviço         |O utilizador que gera o token de incorporação também precisa de uma das seguintes permissões:<li>Permissões de administrador de gateway</li><li>Permissão de representação de DataSource (*ReadOverrideEffectiveIdentity*)</li>         |
|Ligação em direto no Azure do Analysis Services (AS)    |✔ Utilizador principal<br/>✖ Principal de serviço         |A identidade do utilizador que está a gerar o token de incorporação não pode ser substituída. Os dados personalizados podem servir para implementar a RLS dinâmica ou a filtragem segura.<br/><br/>**Nota:** O principal de serviço deve fornecer a respetiva ID de objeto como a identidade efetiva (nome de utilizador de RLS).         |
|Início de Sessão Único (SSO)     |✔ Utilizador principal<br/>✖ Principal de serviço         |Uma identidade explícita (SSO) pode ser fornecida através da propriedade de blob de identidade num objeto de identidade efetiva         |
|SSO e RLS de cloud     |✔ Utilizador principal<br/>✖ Principal de serviço         |Tem de fornecer as seguintes informações:<li>Identidade explícita (SSO) na propriedade de blob de identidade num objeto de identidade efetiva</li><li>Identidade efetiva (RLS) (nome de utilizador)</li>         |

>[!NOTE]
>O principal de serviço tem sempre de fornecer o seguinte:
>* Uma identidade para qualquer item com um conjunto de dados de RLS.
>* Para um conjunto de dados de SSO, uma identidade de RLS efetiva com a propriedade de nome de utilizador definida.

## <a name="next-steps"></a>Próximos passos

>[!div class="nextstepaction"]
>[Registar uma aplicação](register-app.md)

> [!div class="nextstepaction"]
>[Power BI Embedded para clientes](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Objetos do principal de serviço e aplicação no Azure Active Directory](/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[Segurança ao nível da linha com o gateway de dados no local com o principal de serviço](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)

>[!div class="nextstepaction"]
>[Incorporar conteúdos do Power BI com o principal de serviço](embed-service-principal.md)