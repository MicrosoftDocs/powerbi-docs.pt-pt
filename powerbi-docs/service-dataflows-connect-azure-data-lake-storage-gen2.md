---
title: Saiba como ligar o Azure Data Lake Storage Gen2 ao Power BI para armazenar fluxos de dados
description: Incorpore os seus dados nos fluxos de dados com o Azure Data Lake Storage Gen2
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/15/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 8000397e5d8f26847349c35b541aa82c5907292e
ms.sourcegitcommit: ba95d4979f1869f49a7d266c591f95e2810fdb29
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69621244"
---
# <a name="connect-azure-data-lake-storage-gen2-for-dataflow-storage-preview"></a>Ligar o Azure Data Lake Storage Gen2 para armazenar fluxos de dados (Pré-visualização)

Pode configurar áreas de trabalho do Power BI para armazenar fluxos de dados na conta do Azure Data Lake Storage Gen2 da sua organização. Este artigo descreve os passos gerais necessários para o fazer, além de fornecer orientações e melhores práticas ao longo do processo. Há algumas vantagens em configurar áreas de trabalho para armazenar definições de fluxos de dados e ficheiros de dados no data lake, incluindo as que se seguem:

* O Azure Data Lake Storage Gen2 disponibiliza um local de armazenamento de dados extremamente dimensionável
* Os programadores do departamento de TI podem utilizar os dados de fluxos de dados e os ficheiros de definição para tirar partido dos serviços de inteligência artificial (IA) e de Dados do Azure, conforme demonstrado nos [exemplos de GitHub dos Serviços de Dados do Azure](https://aka.ms/cdmadstutorial)
* Permite aos programadores da sua organização integrar dados de fluxos de dados nas aplicações internas e soluções de linha de negócio, com a utilização de recursos de programadores para fluxos de dados e o Azure

Para utilizar o Azure Data Lake Storage Gen2 para fluxos de dados, precisa do seguinte:

* **Inquilino do Power BI**: pelo menos uma conta no inquilino do Azure Active Directory (AAD) tem de estar inscrita no Power BI
* **Uma conta de Administrador Global**: esta conta é necessária para ligar e configurar o Power BI de modo a armazenar a definição de fluxos de dados, assim como os dados, na sua conta do Azure Data Lake Storage Gen2
* **Uma subscrição do Azure**: precisa de uma subscrição do Azure para utilizar o Azure Data Lake Storage Gen2
* **Grupo de recursos**: utilize um grupo de recursos que já tenha ou crie um novo
* **Uma Conta de Armazenamento do Azure com a funcionalidade Data Lake Storage Gen2 ativada** 

> [!TIP]
> Se não tiver uma subscrição do Azure, crie uma [conta gratuita](https://azure.microsoft.com/free/) antes de começar.

> [!WARNING]
> Depois de configurar uma localização de armazenamento de fluxos de dados, esta não pode ser alterada. Veja a secção [considerações e limitações](#considerations-and-limitations) perto do final deste artigo para obter outros elementos importantes a considerar.

## <a name="prepare-your-azure-data-lake-storage-gen2-for-power-bi"></a>Preparar o Azure Data Lake Storage Gen2 para o Power BI

Antes de configurar o Power BI com uma conta do Data Lake Storage Gen2, tem de criar e configurar uma conta de armazenamento. Vejamos quais são os requisitos do Power BI:

1. A conta de armazenamento tem de ser criada no mesmo inquilino do AAD que o seu inquilino do Power BI.
2. A conta de armazenamento tem de ser criada na mesma região que o seu inquilino do Power BI. Para determinar a localização do seu inquilino do Power BI, veja [onde está localizado o meu inquilino do Power BI](service-admin-where-is-my-tenant-located.md).
3. A conta de armazenamento tem de ter a funcionalidade *Espaço de Nomes Hierárquico*  ativada.
4. É necessário conceder uma função de *Leitor* ao serviço Power BI na conta de armazenamento.
5. É necessário criar um sistema de ficheiros com o nome **powerbi**.
6. O serviço Power BI tem de estar autorizado no sistema de ficheiros **powerbi** criado.

As secções que se seguem explicam os passos necessários para configurar a sua conta do Azure Data Lake Storage Gen2 ao pormenor.

### <a name="create-the-storage-account"></a>Criar a conta de armazenamento

Siga os passos descritos no artigo [Criar a conta de armazenamento do Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account).

1. Certifique-se de que seleciona a mesma localização do seu inquilino do Power BI e defina o armazenamento como **StorageV2 (fins gerais v2)**
2. Certifique-se de que ativa a funcionalidade Espaço de nomes hierárquico
3. Recomendamos que especifique a definição de replicação como **Armazenamento georredundante com acesso de leitura (RA-GRS)**

### <a name="grant-the-power-bi-service-a-reader-role"></a>Conceder uma função de leitor ao serviço Power BI

Em seguida, tem de conceder uma função de leitor ao serviço Power BI na sua conta de armazenamento criada. Trata-se de uma função incorporada, pelo que os passos não colocam dificuldades. 

Siga os passos em [Atribuir uma função RBAC incorporada](https://docs.microsoft.com/azure/storage/common/storage-auth-aad-rbac#assign-a-built-in-rbac-role).

Na janela **Adicionar atribuição de função**, selecione a função **Leitor** para a atribuir ao serviço Power BI. Em seguida, utilize a pesquisa para localizar o **Serviço Power BI**. A imagem seguinte mostra a função **Leitor** atribuída ao serviço Power BI.

![Função Leitor atribuída ao serviço Power BI](media/service-dataflows-connect-azure-data-lake-storage-gen2/dataflows-connect-adlsg2_05.jpg)


> [!NOTE]
> Aguarde pelo menos 30 minutos para que a permissão seja propagada para o Power BI a partir do portal. Sempre que alterar as permissões no portal, aguarde 30 minutos para que essas permissões sejam refletidas no Power BI. 


### <a name="create-a-file-system-for-power-bi"></a>Criar um sistema de ficheiros para o Power BI

Tem de criar um sistema de ficheiros com o nome *powerbi* antes de ser possível adicionar a conta de armazenamento ao Power BI. Existem várias maneiras de criar esse sistema de ficheiros, incluindo através do Azure Databricks, do HDInsight, do AZCopy ou do Explorador de Armazenamento do Azure. Esta secção mostra-lhe uma maneira simples de criar um sistema de ficheiros com o Explorador de Armazenamento do Azure.

Para realizar este passo, tem de instalar a versão 1.6.2 ou superior do Explorador de Armazenamento do Azure. Para instalar o Explorador de Armazenamento do Azure para Windows, Macintosh ou Linux, veja o artigo [Explorador de Armazenamento do Azure](https://azure.microsoft.com/features/storage-explorer/).

1. Depois de instalar o Explorador de Armazenamento do Azure com êxito, quando este for iniciado pela primeira vez, a janela Explorador de Armazenamento do Azure – Ligar é apresentada. Apesar de o Explorador de Armazenamento oferecer várias maneiras de estabelecer ligação às contas de armazenamento, apenas uma delas é atualmente suportada para a configuração necessária. 

2. No painel esquerdo, localize e expanda a conta de armazenamento que criou acima.

3. Clique com o botão direito do rato em Contentores de Blobs e, no menu de contexto, selecione Criar Contentor de Blobs.

   ![clicar com o botão direito do rato em Contentores de Blobs](media/service-dataflows-connect-azure-data-lake-storage-gen2/dataflows-connect-adlsg2_05a.jpg)

4. É apresentada uma caixa de texto abaixo da pasta Contentores de Blobs. Introduza o nome *powerbi* 

   ![introduzir o nome "powerbi"](media/service-dataflows-connect-azure-data-lake-storage-gen2/dataflows-connect-adlsg2_05b.jpg)

5. Quando tiver terminado, prima Enter para criar o contentor de blobs

   ![premir Enter para criar o contentor de blobs](media/service-dataflows-connect-azure-data-lake-storage-gen2/dataflows-connect-adlsg2_05c.jpg)

Na secção seguinte, vai conceder à família de serviços Power BI acesso total ao sistema de ficheiros que criou. 

### <a name="grant-power-bi-permissions-to-the-file-system"></a>Conceder permissões do Power BI ao sistema de ficheiros

Para conceder permissões ao sistema de ficheiros, vai aplicar as definições da Lista de Controlo de Acesso (ACL) que concedem o acesso ao serviço Power BI. O primeiro passo para atingir esse objetivo consiste em obter a identidade dos serviços Power BI no seu inquilino. Pode ver as aplicações do Azure Active Directory (AAD) na secção **Aplicações empresariais** do portal do Azure.

Para encontrar aplicações do inquilino, siga estes passos:

1. No [portal do Azure](https://portal.azure.com/), selecione **Azure Active Directory** no painel de navegação à esquerda.
2. No painel **Azure Active Directory**, selecione **Aplicações empresariais**.
3. No menu pendente **Tipo de Aplicação**, selecione **Todas as Aplicações** e, em seguida, selecione **Aplicar**. É apresentado um exemplo das aplicações do inquilino, semelhante à imagem seguinte.

    ![Aplicações empresariais do AAD](media/service-dataflows-connect-azure-data-lake-storage-gen2/dataflows-connect-adlsg2_06.jpg)

4. Na barra de pesquisa, escreva *Power* para visualizar uma coleção de IDs de Objeto das aplicações Power BI e Power Query. Precisará dos três valores nos passos subsequentes.  

    ![Procurar aplicações começadas por Power](media/service-dataflows-connect-azure-data-lake-storage-gen2/dataflows-connect-adlsg2_07.jpg)

5. Selecione e copie os IDs de Objeto do serviço Power BI e do Power Query online nos resultados da pesquisa. Prepare-se para colar esses valores em passos subsequentes.

7. Em seguida, utilize o **Explorador de Armazenamento do Azure** para navegar para o sistema de ficheiros *powerbi* que criou na secção anterior. Siga as instruções apresentadas na secção [Gerir o acesso](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-how-to-set-permissions-storage-explorer#managing-access) do artigo [Definir permissões ao nível do ficheiro e do diretório com o Explorador de Armazenamento do Azure](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-how-to-set-permissions-storage-explorer).

8. Para cada um dos dois IDs de Objeto do Power BI recolhidos no passo 5, atribua ACLs de Predefinição e Acesso de **Leitura**, **Escrita** e **Execução** ao seu sistema de ficheiros *powerbi*.

   ![para ambos, atribuir as três](media/service-dataflows-connect-azure-data-lake-storage-gen2/dataflows-connect-adlsg2_07a.jpg)

9. Para o ID de Objeto Online do Power Query recolhido no passo 4, atribua ACLs de Predefinição e Acesso de **Escrita** e **Execução** ao seu sistema de ficheiros *powerbi*.

   ![em seguida, atribua permissões de escrita e execução](media/service-dataflows-connect-azure-data-lake-storage-gen2/dataflows-connect-adlsg2_07b.jpg)

10. Além disso, para a opção **Outro**, atribua ACLs de Predefinição e Acesso de **Execução**.

    ![por último, para a opção Outro, atribua a permissão de execução](media/service-dataflows-connect-azure-data-lake-storage-gen2/dataflows-connect-adlsg2_07c.jpg)

## <a name="connect-your-azure-data-lake-storage-gen2-to-power-bi"></a>Ligar o Azure Data Lake Storage Gen2 ao Power BI

Depois de configurar a sua conta do Azure Data Lake Storage Gen2 no portal do Azure, pode ligá-la ao Power BI no **portal de administração do Power BI**. Também pode gerir o armazenamento de fluxos de dados do Power BI na secção de definições de **Armazenamento de fluxos de dados** do portal de administração do Power BI. Para receber orientações sobre abertura e utilização básica, consulte a secção [Como aceder ao portal de administração](service-admin-portal.md) para obter informações detalhadas.

Para ligar a sua conta do **Azure Data Lake Storage Gen2**, siga estes passos:

1. Navegue para o separador **Definições de fluxos de dados** do **portal de administração do Power BI**

    ![Portal de administração do Power BI](media/service-dataflows-connect-azure-data-lake-storage-gen2/dataflows-connect-08b.png) 

2. Selecione o botão **Ligar o Azure Data Lake Storage Gen2**. A janela a seguir é apresentada.

    ![Azure Data Lake Storage Gen2](media/service-dataflows-connect-azure-data-lake-storage-gen2/dataflows-connect-adlsg2_09.jpg) 

3. Indique o **ID de Subscrição** da Conta de Armazenamento.
4. Indique o **Nome do Grupo de Recursos** no qual foi criada a conta de armazenamento.
5. Indique o **Nome da Conta de Armazenamento**.
6. Selecione **Ligar**.

Após a conclusão bem-sucedida desses passos, a sua conta do Azure Data Lake Storage Gen2 está ligada ao Power BI. 

> [!NOTE]
> Para configurar uma ligação ao Azure Data Lake Storage Gen2 no portal de administração do Power BI, tem de ter permissões de Administrador Global. No entanto, os Administradores Globais não podem ligar o armazenamento externo no portal de administração.  

Em seguida, precisa de ativar as pessoas da sua organização para configurar as respetivas áreas de trabalho, o que lhes permite utilizar esta conta de armazenamento para definir fluxos de dados e armazenar dados. Esse será o próximo passo a efetuar na secção seguinte. 


## <a name="allow-admins-to-assign-workspaces"></a>Permitir a atribuição de áreas de trabalho por parte dos administradores

Por predefinição, a definição de fluxos de dados e os ficheiros de dados são armazenados no armazenamento fornecido pelo Power BI. Para aceder aos ficheiros de fluxos de dados na sua própria conta de armazenamento, os administradores de áreas de trabalho têm de configurar primeiro a área de trabalho para permitir a atribuição e o armazenamento de fluxos de dados na conta de armazenamento nova. Para um administrador de áreas de trabalho poder configurar definições de armazenamento de fluxos de dados, é necessário conceder permissões de atribuição de armazenamento ao administrador no **Portal de administração do Power BI**.

Para conceder permissões de atribuição de armazenamento, aceda ao separador **Definições de fluxos de dados** no **Portal de administração do Power BI**. Há um botão de opção para *Permitir que os administradores de áreas de trabalho atribuam áreas de trabalho a esta conta de armazenamento* que deve ser definido como **permitir**. Depois de ativar esse controlo de deslize, selecione o botão **Aplicar** para que a alteração produza efeito. 

![Permitir a atribuição de áreas de trabalho por parte dos administradores](media/service-dataflows-connect-azure-data-lake-storage-gen2/dataflows-connect-adlsg2_10.jpg) 

Já está! Agora, os administradores de áreas de trabalho do Power BI já podem atribuir fluxos de trabalho ao sistema de ficheiros que criou.


## <a name="considerations-and-limitations"></a>Considerações e limitações

Esta é uma funcionalidade de pré-visualização e seu comportamento pode sofrer alterações à medida que se aproxima a data de lançamento. Há algumas considerações e limitações a ter em conta quando trabalhar com o seu armazenamento de fluxos de dados:

* Depois de configurar uma localização de armazenamento de fluxos de dados, esta não pode ser alterada.
* Por predefinição, apenas os proprietários de um fluxo de dados armazenado no Azure Data Lake Storage Gen2 podem aceder aos dados do mesmo. Para autorizar o acesso de outras pessoas aos fluxos de dados armazenados no Azure, tem de os adicionar à pasta de CDM dos fluxos de dados 
* A criação de fluxos de dados com entidades ligadas só é possível quando são armazenados na mesma conta de armazenamento
* As origens de dados no local, em capacidades partilhadas do Power BI, não são suportadas em fluxos de dados armazenados no data lake da sua organização
* Os instantâneos não são eliminados automaticamente no ADLS Gen2. Se quiser libertar espaço, pode criar uma função do Azure para limpar os instantâneos antigos periodicamente.

Também existem alguns problemas conhecidos, conforme descrito nesta secção.

Os clientes do Power BI Desktop não podem aceder a fluxos de dados armazenados numa **Conta do Azure Data Lake Storage**, salvo se forem os proprietários do fluxo de dados ou se lhes tiver sido dada autorização à pasta de CDM no data lake. O cenário é o seguinte:

1. A Ana criou uma nova área de trabalho da aplicação e configurou-a para armazenar fluxos de dados no data lake da organização. 
2. O Nuno, que também é membro da área de trabalho criada pela Ana, quer tirar partido do Power BI Desktop e do conector de fluxos de dados para obter dados do Fluxo de Dados criado pela Ana.
3. O Miguel recebe um erro semelhante porque não lhe foi dada autorização para a pasta de CDM do fluxo de dados no data lake.

Seguem-se algumas perguntas e respostas comuns:

**Pergunta:** O que acontece se tivesse criado anteriormente fluxos de dados numa área de trabalho e quisesse alterar a localização de armazenamento dos mesmos?

**Resposta:** Não pode alterar a localização de armazenamento de um fluxo de dados depois de o criar. 

**Pergunta:** Em que circunstâncias posso alterar a localização de armazenamento do fluxo de dados de uma área de trabalho?

**Resposta:** A alteração da localização de armazenamento do fluxo de dados de uma área de trabalho só é permitida se a área de trabalho não contiver fluxos de dados.


## <a name="next-steps"></a>Próximos passos

Este artigo disponibilizou orientação sobre como ligar um Azure Data Lake Gen2 para armazenamento de fluxos de dados. Para obter informações adicionais, veja os seguintes artigos:

Para obter mais informações sobre fluxos de dados, CDM e o Azure Data Lake Storage Gen2, veja os seguintes artigos:

* [Fluxos de dados e integração do Azure Data Lake (Pré-visualização)](service-dataflows-azure-data-lake-integration.md)
* [Configure workspace dataflow settings (Preview) (Configurar as definições de fluxos de dados da área de trabalho [Pré-visualização])](service-dataflows-configure-workspace-storage-settings.md)
* [Add a CDM folder to Power BI as a dataflow (Preview) (Adicionar uma pasta de CDM ao Power BI como um fluxo de dados [Pré-visualização])](service-dataflows-add-cdm-folder.md)

Para obter informações sobre fluxos de dados em geral, veja estes artigos:

* [Criar e utilizar fluxos de dados no Power BI](service-dataflows-create-use.md)
* [Utilizar entidades calculadas no Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Utilizar fluxos de dados com origens de dados no local](service-dataflows-on-premises-gateways.md)
* [Recursos para programadores para fluxos de dados do Power BI](service-dataflows-developer-resources.md)

Para obter mais informações sobre o armazenamento do Azure, leia estes artigos:
* [Guia de segurança de Armazenamento do Azure](https://docs.microsoft.com/azure/storage/common/storage-security-guide)

Para obter mais informações sobre o Common Data Service, pode ler o seguinte artigo de descrição geral:
* [Common Data Service – descrição geral](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [Pastas de CDM](https://go.microsoft.com/fwlink/?linkid=2045304)
* [Definição do ficheiro de modelo do CDM](https://go.microsoft.com/fwlink/?linkid=2045521)

Pode sempre experimentar [colocar perguntas à Comunidade do Power BI](http://community.powerbi.com/).
