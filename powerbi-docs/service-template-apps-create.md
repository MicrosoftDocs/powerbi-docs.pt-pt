---
title: Criar aplicações de modelo no Power BI (pré-visualização)
description: Como criar aplicações de modelo no Power BI que podem ser distribuídas para qualquer cliente do Power BI.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/22/2019
ms.author: maggies
ms.openlocfilehash: 2dc9ae7eb7ecd82cdd6c9ea7ddbc6aa1fc70ca8b
ms.sourcegitcommit: 81ba3572531cbe95ea0b887b94e91f94050f3129
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66751182"
---
# <a name="create-a-template-app-in-power-bi-preview"></a>Criar uma aplicação de modelo no Power BI (pré-visualização)

As novas *aplicações de modelo* do Power BI permitem que os parceiros do mesmo criem aplicações do Power BI com pouco ou nenhum código e que as implementem para qualquer cliente do Power BI.  Este artigo contém instruções passo a passo para criar uma aplicação de modelo do Power BI.

Se conseguir criar relatórios e dashboards do Power BI, pode tornar-se um *criador de aplicações de modelo* que cria e empacota conteúdos de análise numa *aplicação*. Pode implementar a sua aplicação noutros inquilinos do Power BI através de qualquer plataforma disponível, como o AppSource, ou ao utilizá-la no seu próprio serviço Web. Enquanto criador, pode criar um pacote de análise protegido para distribuição.

Os administradores de inquilinos do Power BI gerem e controlam quem na sua organização pode criar aplicações de modelo e quem pode instalá-las. Os utilizadores que tiverem autorização para tal podem instalar a aplicação de modelo e, em seguida, modificar e distribuí-la para os consumidores do Power BI na organização.

## <a name="prerequisites"></a>Pré-requisitos

Eis os requisitos para a criação de uma aplicação de modelo:  

- Uma [licença do Power BI Pro](service-self-service-signup-for-power-bi.md)
- Uma [instalação do Power BI Desktop](desktop-get-the-desktop.md) (opcional)
- Conhecer os [conceitos básicos do Power BI](service-basic-concepts.md)
- Permissões para criar uma aplicação de modelo. Veja as [Definições de aplicação de modelo do portal de administração](service-admin-portal.md#template-apps-settings-preview) do Power BI para obter detalhes.

## <a name="enable-app-developer-mode"></a>Ativar o modo de programador da aplicação

Para criar uma aplicação de modelo que possa distribuir para outros inquilinos do Power BI, terá de estar no modo de Programador da Aplicação. Caso contrário, estará apenas a criar uma aplicação para consumidores do Power BI na sua própria organização.

1. Abra o serviço Power BI num browser.
2. Aceda a **Definições** > **Geral** > **Programador** > **Ativar o modo de desenvolvimento de aplicações de modelos**.

    ![Ativar aplicações de modelo](media/service-template-apps-create/power-bi-dev-template-app.png)

    Se não vir essa opção, contacte o seu administrador do Power BI para que lhe conceda [permissões para a programação de aplicações de modelo](service-admin-portal.md#template-apps-settings-preview) no portal de administração.

3. Selecione **Aplicar**.

## <a name="create-the-template-app-workspace"></a>Criar a área de trabalho de aplicação de modelo

Para criar uma aplicação de modelo que possa distribuir para outros inquilinos do Power BI, terá de o fazer numa das novas áreas de trabalho de aplicações.

1. No serviço Power BI, selecione **Áreas de trabalho** > **Criar área de trabalho de aplicação**.

    ![Criar área de trabalho de aplicação](media/service-template-apps-create/power-bi-new-workspace.png)

2. Em **Criar uma área de trabalho de aplicação**, em **Pré-visualizar as áreas de trabalho melhoradas**, selecione **Experimente agora**.

    ![Experimentar novas áreas de trabalho](media/service-template-apps-create/power-bi-try-now-new-workspace.png)

3. Introduza um nome, uma descrição (opcional) e uma imagem de logótipo (opcional) para a sua área de trabalho de aplicação.

4. Selecione **Desenvolver uma aplicação de modelo**.

    ![Desenvolver uma aplicação de modelo](media/service-template-apps-create/power-bi-template-app-develop.png)

5. Selecione **Guardar**.
>[!NOTE]
>Necessita de permissões do administrador do Power BI para promover aplicações de modelo.

## <a name="create-the-content-in-your-template-app"></a>Criar os conteúdos na sua aplicação de modelo

Tal como acontece com uma área de trabalho de aplicação do Power BI normal, o próximo passo é criar os conteúdos na área de trabalho.  Nesta versão de pré-visualização das aplicações de modelo, suportamos apenas um conteúdo de cada tipo: um conjunto de dados, um relatório e um dashboard.

- [Crie os seus conteúdos do Power BI](power-bi-creator-landing.md) na sua área de trabalho de aplicação.

Se estiver a utilizar parâmetros no Power Query, certifique-se de que define corretamente o tipo (por exemplo, Texto). Os tipos Qualquer e Binário não são suportados.

O artigo [Tips for authoring template apps in Power BI (preview)](service-template-apps-tips.md) (Sugestões para a criação de aplicações de modelo no Power BI [pré-visualização]) apresenta sugestões a considerar ao criar relatórios e dashboards para a sua aplicação de modelo.

## <a name="create-the-test-template-app"></a>Criar a aplicação de modelo de teste

Agora que tem conteúdos na sua área de trabalho, está tudo pronto para os empacotar numa aplicação de modelo. O primeiro passo é criar uma aplicação de modelo de teste que seja acessível apenas a partir do seu inquilino na sua organização.

1. Na área de trabalho de aplicação de modelo, selecione **Criar aplicação**.

    ![Criar aplicação](media/service-template-apps-create/power-bi-create-app.png)

    Neste passo, irá preencher as opções de criação adicionais da sua aplicação de modelo em cinco categorias:

    **Personalização**

    ![Imagem corporativa](media/service-template-apps-create/power-bi-create-branding.png)
    - Nome da aplicação
    - Descrição
    - Site de suporte (a ligação é apresentada nas informações da aplicação, após a redistribuição da aplicação de modelo como aplicação de organização)
    - Logótipo da aplicação (limite de tamanho do ficheiro de 45 KB, proporção de 1:1, formatos .png, .jpg e .jpeg)
    - Cor do tema da aplicação

    **Conteúdo**

    **Página de destino da aplicação:** Defina um relatório ou dashboard como a página de destino da sua aplicação. Utilize uma página de destino que dê uma impressão certa:

    ![Conteúdo](media/service-template-apps-create/power-bi-create-content.png)

    **Controlo**

    Defina limites e restrições que os utilizadores da aplicação terão relativamente aos conteúdos da sua aplicação. Pode utilizar este controlo para proteger propriedades intelectuais na sua aplicação.

    ![Controlo](media/service-template-apps-create/power-bi-create-control.png)

    >[!NOTE]
    >A exportação para o formato .pbix é sempre bloqueada aos utilizadores que instalam a aplicação.

    **Parâmetros**

    Utilize esta categoria para gerir o comportamento dos parâmetros ao ligar a origens de dados. Saiba mais sobre a [criação de parâmetros de consulta](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/).

    ![Parâmetros](media/service-template-apps-create/power-bi-create-parameters.png)
    - **Valor**: valor de parâmetro predefinido.
    - **Obrigatório**: utilize esta opção para exigir que o instalador introduza um parâmetro específico do utilizador.
    - **Bloquear**: o bloqueio impede que o instalador atualize um parâmetro.
    - **Estático**: ative esta opção se a aplicação *apenas* tiver dados de exemplo. Ao selecionar **Estático**, o assistente de instalação não irá pedir aos utilizadores para ligar uma origem de dados.

    **Acesso**: na fase de teste, decida que pessoas na sua organização podem instalar e testar a sua aplicação. Não se preocupe, pode sempre regressar e alterar estas definições mais tarde (as definições não afetam o acesso à Aplicação de modelo distribuída).

2. Selecione **Criar aplicação**.

    Verá uma mensagem a informar que a aplicação de teste está pronta, com uma ligação para copiar e partilhar com os técnicos de teste da sua aplicação.

    ![A aplicação de teste está pronta](media/service-template-apps-create/power-bi-template-app-test-ready.png)

    Também já concluiu o primeiro passo do processo de gestão de versões que segue.

## <a name="manage-the-template-app-release"></a>Gerir a versão da aplicação de modelo

Antes de lançar esta aplicação de modelo publicamente, é importante garantir que está pronta para tal. O Power BI criou o painel de gestão de versões, onde pode acompanhar e inspecionar o caminho de versão completo da aplicação. Também pode acionar a transição de uma fase para outra. As fases comuns são:

- Gerar aplicação de teste: para testar apenas na sua organização.
- Promover o pacote de teste para a fase de pré-produção: testar fora da sua organização.
- Promover o pacote de pré-produção para Produção: versão de produção.
- Eliminar um pacote ou começar a partir da fase anterior.

O URL não sofre alterações à medida que avança nas fases de lançamento. A promoção não afeta o URL.

Vamos percorrer todas as fases:

1. Na área de trabalho de aplicação de modelo, selecione **Gestão de Versões**.

    ![Ícone de gestão de versões](media/service-template-apps-create/power-bi-release-management-icon.png)

2. Selecione **Criar aplicação**.

    Se tiver criado a aplicação de teste na secção **Criar a aplicação de modelo de teste** acima, o ponto amarelo junto a **Teste** já está preenchido e não precisa de selecionar a opção **Criar aplicação** nesta fase. Se a selecionar, voltará ao processo de criação de aplicações do modelo.

3. Selecione **Obter ligação**.

    ![Criar aplicação, obter ligação](media/service-template-apps-create/power-bi-dev-template-create-app-get-link.png)

4. Para testar a experiência de instalação da aplicação, copie a ligação na janela de notificação e cole-a numa nova janela do browser.

    A partir daqui, estará a seguir o mesmo procedimento que seguirão os seus clientes. Veja [Install and distribute template apps in your organization](service-template-apps-install-distribute.md) (Instalar e distribuir aplicações de modelo na sua organização) para saber a respetiva versão.

5. Na caixa de diálogo, selecione **Instalar**.

    Quando a instalação for concluída com êxito, será apresentada uma notificação a informar que a nova aplicação está pronta.

6. Selecione **Ir para a aplicação**.
7. Em **Comece já com a sua nova aplicação**, verá a sua aplicação tal como os seus clientes a irão ver.

    ![Comece já com a sua aplicação](media/service-template-apps-create/power-bi-template-app-get-started.png)
8. Selecione **Explorar a aplicação** para verificar a aplicação de teste com os dados de exemplo.
9. Para fazer alterações, volte à aplicação na área de trabalho original. Atualize a aplicação de teste até obter os resultados que pretende.
10. Quando estiver pronto para promover a sua aplicação para pré-produção para que sejam feitos testes adicionais fora do seu inquilino, regresse ao painel **Gestão de Versões** e selecione **Promover aplicação**. 

    ![Promover aplicação para pré-produção](media/service-template-apps-create/power-bi-template-app-promote.png)

    >[!NOTE]
    > Quando a aplicação é promovida, fica publicamente disponível fora da sua organização.

11. Selecione **Promover** para confirmar a sua escolha.
12. Copie este novo URL para partilhar fora do seu inquilino para fins de teste. Esta ligação é a mesma que irá submeter para iniciar o processo de distribuição da sua aplicação no AppSource ao criar uma [nova oferta do Cloud Partner Portal](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-publish-offer). Submeta apenas ligações de pré-produção no Cloud Partner Portal. Só após a aplicação ser aprovada e receber uma notificação de que esta foi publicada no AppSource, poderá promover este pacote para produção no Power BI.
13. Quando a aplicação está pronta para produção ou partilha através do AppSource, regresse ao painel **Gestão de Versões** e selecione **Promover aplicação** junto a **Pré-produção**.
14. Selecione **Promover** para confirmar a sua escolha.

    Agora a sua aplicação está em produção e pronta para distribuição.

    ![Aplicação em produção](media/service-template-apps-create/power-bi-template-app-production.png)

Para disponibilizar a sua aplicação para milhares de utilizadores do Power BI em todo o mundo, recomendamos que a submeta no AppSource. Veja a [Oferta da aplicação Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) para obter detalhes.

## <a name="update-your-app"></a>Atualizar a sua aplicação

Agora que a aplicação está em produção, pode recomeçar a fase de teste sem interromper a aplicação em produção.

1. No painel **Gestão de Versões**, selecione **Criar aplicação**.
2. Repita o processo de criação de aplicações.
3. Após definir as categorias **Personalização**, **Conteúdo**, **Controlo** e **Acesso**, selecione novamente **Criar aplicação**.
4. Selecione **Fechar** e regresse ao painel **Gestão de Versões**.

   Verá que agora tem duas versões: A versão em produção e uma nova versão em modo de teste.

    ![Duas versões de uma aplicação de modelo](media/service-template-apps-create/power-bi-template-app-2-versions.png)

5. Quando estiver pronto para promover a sua aplicação para pré-produção para que sejam feitos testes adicionais fora do seu inquilino, regresse ao painel Gestão de Versões e selecione **Promover aplicação** junto a **Teste**.
6. A sua ligação está agora ativada. Submeta-a novamente no Cloud Partner Portal ao seguir os passos em [Atualização da oferta da Aplicação Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-update-existing-offer).

>[!NOTE]
>Promova a sua aplicação para a fase de produção apenas após a sua aplicação ser aprovada pelo Cloud Partner Portal e após publicá-la.

## <a name="next-steps"></a>Próximos passos

Veja como os seus clientes interagem com a sua aplicação de modelo em [Install, customize, and distribute template apps in your organization](service-template-apps-install-distribute.md) (Instalar, personalizar e distribuir aplicações de modelo na sua organização).

Veja a [Oferta da aplicação Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) para obter detalhes sobre como distribuir a sua aplicação.
