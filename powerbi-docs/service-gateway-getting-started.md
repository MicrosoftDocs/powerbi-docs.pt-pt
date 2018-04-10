---
title: Introdução aos gateways do Power BI
description: Conheça as noções básicas sobre gateways de dados para o Power BI.
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 01/24/2018
ms.author: davidi
LocalizationGroup: Gateways
ms.openlocfilehash: bf01bb7764db09d6afe24e520f2d185c191ef56c
ms.sourcegitcommit: 65426de556cd7207cbc4f478198664e25c33a769
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/30/2018
---
# <a name="getting-started-with-power-bi-gateways"></a>Introdução aos gateways do Power BI
Bem-vindo ao guia **Introdução aos gateways do Power BI**. Este guia resumido permite-lhe saber o que faz um gateway, como funciona e o que fazer para instalar, configurar e executar o seu próprio gateway.  

![](media/service-gateway-getting-started/gw_gettingstarted_0a.png)

Os gateways podem ser um problema técnico e, uma vez que cada rede e empresa é diferente, podem ser bastante complexos. Para resolver essa questão, vamos começar pelas noções básicas.

## <a name="how-power-bi-gateways-work"></a>Como funcionam os gateways do Power BI
O **gateway** é um software que facilita o acesso a dados que residem numa rede privada, no local, para utilização posterior num serviço em nuvem, como o Power BI. É como um controlador de chamadas que escuta pedidos de ligação e concede-os apenas se os pedidos dos utilizadores cumprirem determinados critérios (por exemplo, se têm autorização para utilizar o gateway). Isto permite às organizações guardar as bases de dados e armazéns nas respetivas redes no local, mas utilizar subconjuntos de dados em segurança para criar relatórios e dashboards interessantes no Power BI.

Um gateway também protege o acesso e os dados, ao encriptar e comprimir todos os dados que passam por ele, bem como quaisquer palavras-passe utilizadas para ligação a origens de dados. Tudo isto parece bastante convencional, mas há muitos aspetos a ter em conta.

Por vezes, pretende um gateway apenas para si, talvez tenha um livro Excel grande, bem como três bases de dados SQL com vendas e dados de marketing e pretende criar um dashboard do Power BI que mostre as vendas de todas as perspetivas. É a única pessoa que cria relatórios, é o seu livro do Excel e apenas utiliza essas bases de dados para criar relatórios do Power BI. Basta um gateway para a sua utilização pessoal, não quer partilhar essas origens de dados com outras pessoas.

Noutros casos, pode trabalhar numa organização com todos os tipos de bases de dados de fornecedores diferentes, incluindo Analysis Services, SAP, Oracle, IBM e várias outras origens de dados, e necessita que muitas pessoas acedem aos mesmos, para que podem criar vários relatórios. Neste caso, necessita de um gateway que lhe permita configurar o acesso a todas essas origens e necessita de partilhá-lo com muitas pessoas na sua organização. Isso é um gateway totalmente diferente.

Felizmente, o Power BI oferece dois gateways, que se ajusta a cada um desses cenários. Estes dois tipos de gateways do Power BI são:

* **Gateway de dados no local (modo pessoal)** – permite que um utilizador estabeleça ligação a origens e não pode ser partilhado com outras pessoas. Só pode ser utilizado com o Power BI.
* **Gateway de dados no local** – permite que vários utilizadores estabeleçam ligação a várias origens de dados no local e podem ser utilizados por aplicações Power BI, PowerApps e Azure Logic, tudo numa única instalação de gateways.

Os gateways desempenham uma função semelhante: facilitam o acesso aos dados que residem numa rede privada no local, para que os dados podem ser utilizados em serviços baseados na nuvem, como o Power BI. O gateway pessoal pode ser utilizado por uma pessoa e apenas pelo Power BI, o **Gateway de dados no local** pode ser utilizado por vários utilizadores e vários serviços.

São necessárias três partes ou fases, para colocar um gateway em funcionamento:

* Instalar o gateway
* Adicionar utilizadores ao gateway (deixe-os utilizar o gateway)
* Ligar a origens de dados

Além disso, utilizar um gateway permite-lhe fazer outra coisa que pode ser importante:

* Atualizar dados no local, pelo que os relatórios do Power BI possam ser atualizados com novos dados

Atualizar dados significa que os relatórios e os dashboards do Power BI tenham um aspeto novo e reflitam os dados mais recentes. Por isso, quando alguém visualiza um relatório que criou com dados no local, esse relatório pode mostrar as informações mais recentes, mesmo que tenha criado o relatório há algum tempo.

A primeira parte, instalar um gateway, é fácil. Permitir que os utilizadores acedam ao gateway também é fácil – basta adicioná-los a uma caixa de diálogo no Power BI e estão prontos a ser utilizados. A ligação a origens de dados pode ser complexa, porque há muitas origens de dados e cada uma tem requisitos e características de ligação próprias. Vamos abordar a questão da atualização noutro guia, para que este guia se concentre apenas no gateway.

Por isso, vamos começar pelas questões simples e orientá-lo pelo processo de instalação de um gateway.

## <a name="install-the-gateway"></a>Instalar o gateway
Para instalar um gateway, abra o serviço Power BI (pode utilizar esta ligação para iniciar o serviço Power BI no seu browser e iniciar sessão) e inicie sessão com a sua conta do Power BI. No serviço Power BI, selecione o **ícone de transferência** no canto superior direito, como mostrado na imagem seguinte e selecione **Gateway de Dados**.

![](media/service-gateway-getting-started/gw_gettingstarted_01.png)

Isso permite-lhe aceder a uma página de transferência, onde pode clicar no botão **Transferir gateway** para iniciar a transferência.

![](media/service-gateway-getting-started/gw_gettingstarted_02.png)

Este ecrã fornece-lhe uma explicação muito resumida sobre o funcionamento de um gateway. Fornece também alguns **avisos** importantes: quando instala um gateway, este é executado no computador no qual efetuar a instalação. E se esse computador for desativado, o gateway também será (para que não funcione quando não estiver em execução). Além disso, instalar num computador com uma rede sem fios não é a melhor opção, pelo que deve utilizar um computador ligado a uma rede com fios.

Quando estiver pronto, selecione **Seguinte** para continuar a configuração.

![](media/service-gateway-getting-started/gw_gettingstarted_03.png)

Aqui pode decidir que gateway irá instalar: um gateway no local ou um gateway pessoal. Neste guia, vamos instalar o **Gateway de dados no local**.

Há algumas questões a salientar nesta fase de decisão:

* Ambos os gateways necessitam de sistemas operativos do Windows de 64 bits.
* Os gateways não podem ser instalados num controlador de domínio.
* Pode instalar, no máximo, dois Gateways de dados no local no mesmo computador, um em execução em cada modo (pessoal e padrão). 
* Não pode ter mais de um gateway em execução da mesma maneira no mesmo computador.
* Pode instalar vários Gateways de dados no local em computadores diferentes e geri-los a todos a partir da mesma interface de gestão do gateway do Power BI (à exceção do modo pessoal, veja o ponto seguinte).
* Só pode ter um gateway de modo pessoal em execução para cada utilizador do Power BI. Se instalou outro gateway de modo pessoal para o mesmo utilizador, mesmo num computador diferente, a instalação mais recente substitui a instalação anterior.

Quando selecionamos **Seguinte**, a instalação do gateway é iniciada. Tem de especificar onde será instalada e a localização predefinida é, normalmente, a melhor.

![](media/service-gateway-getting-started/gw_gettingstarted_06.png)

O processo de instalação é rápido e é apresentada uma barra de estado.

![](media/service-gateway-getting-started/gw_gettingstarted_06a.png)

Quando estiver quase concluída, tem de identificar a conta a utilizar com o gateway. Esta deve ser a conta (nome de utilizador e palavra-passe) que utiliza para iniciar sessão no Power BI; o gateway está associado à sua conta do Power BI e configura gateways a partir do serviço Power BI.

![](media/service-gateway-getting-started/gw_gettingstarted_07.png)

A sua sessão vai ser iniciada, conforme indicado na imagem seguinte.

![](media/service-gateway-getting-started/gw_gettingstarted_08.png)

Depois de iniciar sessão, terá de criar um **chave de recuperação**. Vamos abordar este assunto de maneira mais aprofundada noutro artigo, mas por agora é necessário para recuperar ou mover o gateway.

![](media/service-gateway-getting-started/gw_gettingstarted_09.png)

Se tudo correr bem, verá uma janela que indica que o gateway está pronto.

![](media/service-gateway-getting-started/gw_gettingstarted_10.png)

A instalação de um gateway no local está concluída. Como indicámos, é um processo muito fácil. Em seguida, pode **adicionar utilizadores** ou **adicionar origens de dados**. Pode optar pelas duas opções e adicioná-los após a configuração inicial.

A secção que se segue descreve como adicionar utilizadores ao gateway e, em seguida, vamos abordar o passo seguinte para adicionar origens de dados ao gateway.

## <a name="add-users-to-a-gateway"></a>Adicionar utilizadores a um gateway
Agora que temos um gateway instalado, podemos geri-lo a partir do **Serviço Power BI**. Para aceder ao ecrã de gestão de gateways, no serviço Power BI, selecione o ícone de engrenagem no canto superior direito e depois selecione **Gerir gateways**.

![](media/service-gateway-getting-started/gw_gettingstarted_15.png)

É apresentada uma página na tela de serviço Power BI, onde pode gerir os seus gateways. A página **Definições do Gateway** tem o seguinte aspeto.

![](media/service-gateway-getting-started/gw_gettingstarted_12.png)

Se tocar ou clicar em **Administradores**, verá a seguinte página de gestão de administradores. Tenha em atenção que, neste caso, referimos apenas aos utilizadores que podem *administrar* o gateway e que utilizadores do gateway são adicionados (ou removidos) de cada origem de dados individuais, utilizando uma página diferente, que vamos rever nos parágrafos que se seguem.

![](media/service-gateway-getting-started/gw_gettingstarted_13.png)

Depois de instalar e validar (aceder com êxito) uma origem de dados, esta é apresentada debaixo do respetivo gateway associado no lado esquerdo deste ecrã **Gerir gateways**, conforme mostrado na imagem seguinte. Tenha em atenção que, no painel da direita, pode alternar entre duas secções: **Definições da Origem de Dados** e **Utilizadores**. O ecrã que aparece imediatamente a seguir é a secção **Definições da Origem de Dados**.

![](media/service-gateway-getting-started/gw_gettingstarted_16.png)

Se selecionar **Utilizadores** aparece uma caixa de texto na qual pode escrever os utilizadores da sua organização a quem pretende conceder acesso à origem de dados selecionada. No ecrã seguinte, pode ver o que adicionei à Margarida e ao André.

Quando começa a escrever um endereço de e-mail na caixa de texto, o Power BI mostra uma lista de utilizadores cujo e-mail corresponde ao está a escrever, permitindo-lhe clicar no nome e adicioná-los à lista.

Também pode adicionar 	grupos de e-mail (nomes alternativos) para permitir acesso a grupos de pessoas, bem como a indivíduos.

![](media/service-gateway-getting-started/gw_gettingstarted_17.png)

Depois de selecionar **Adicionar**, os membros adicionados são apresentados na caixa e pode adicionar mais, se quiser. A remoção de utilizadores é igualmente fácil. Basta selecionar a caixa de verificação junto ao respetivo nome e, em seguida, selecionar o botão **Remover** abaixo da caixa.

![](media/service-gateway-getting-started/gw_gettingstarted_18.png)

E é tudo. Lembre-se que tem de adicionar utilizadores a cada origem de dados para o qual pretende conceder acesso. Cada origem de dados tem uma lista de utilizadores separada, e deve adicionar utilizadores a cada origem de dados em separado.

## <a name="adding-data-sources"></a>Adicionar origens de dados
Como é óbvio, para que o seu gateway seja útil, deve adicionar origens de dados. É aqui que surge alguma da complexidade dos gateways do Power BI: há muitas origens de dados diferentes disponíveis e cada uma tem requisitos próprios (e muitas vezes, controladores próprios necessários).

Mas antes de lhe mostrarmos outro artigo, saiba como adicionar uma origem de dados. Na página **Gerir gateways** do **Serviço Power BI**, selecione o gateway ao qual pretende adicionar uma origem de dados e selecione **Adicionar Origem de Dados** no canto superior esquerdo da página, imediatamente acima da lista dos seus gateways.

Depois de o fazer, o painel **Definições da Origem de Dados** aparece no painel direito, conforme mostrado na imagem seguinte. Aqui pode atribuir o nome à origem de dados (introduzido na caixa de texto **Nome da Origem de Dados**) e selecione o respetivo tipo na lista pendente **Tipo de Origem de Dados**.

![](media/service-gateway-getting-started/gw_gettingstarted_14.png)

Agora o gateway está instalado e pode adicionar origens de dados. Ótimo! Consulte os recursos na secção seguinte para obter informações sobre origens de dados, mais detalhes sobre como utilizar gateways e outras informações úteis.

## <a name="next-steps"></a>Próximos passos
[Utilizar o Gateway de dados no local](service-gateway-onprem.md)  
[Gateway de dados no local detalhado](service-gateway-onprem-indepth.md)  
[Gateway de dados no local (modo pessoal)](service-gateway-personal-mode.md)
[Resolução de problemas do Gateway de dados no local](service-gateway-onprem-tshoot.md)  

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

