---
title: Ligar a dados de Informações sobre Consumo do Azure no Power BI Desktop (Beta)
description: Ligue facilmente ao Azure e obtenha informações sobre consumo e utilização com o Power BI Desktop
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
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1e82ec988389790a3d96cb6f98f0db5d1a385fda
ms.sourcegitcommit: 00b4911ab5fbf4c2d5ffc000a3d95b3149909c28
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
# <a name="connect-to-azure-consumption-insights-in-power-bi-desktop-beta"></a>Ligar a Informações sobre Consumo do Azure no Power BI Desktop (Beta)
O conector **Informações sobre Consumo do Azure** permite utilizar o **Power BI Desktop** para ligar ao Azure e obter dados e informações aprofundados sobre a utilização dos serviços do Azure por parte da sua organização. Também pode criar medidas, colunas personalizadas e elementos visuais para documentar e partilhar informações sobre a utilização do Azure por parte da sua organização. Esta versão do conector **Informações sobre Consumo do Azure** encontra-se em fase experimental (Beta) e está sujeita a alterações.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_01.png)

Neste artigo, serão disponibilizadas informações sobre como ligar através do conector **Informações sobre Consumo do Azure** e obter os dados de que precisa, e como migrar a partir do Conector Empresarial do Azure, além de que encontrará um mapeamento das *colunas de detalhes de utilização* disponível na API **ACI** (Informações sobre Consumo do Azure).

## <a name="connect-to-azure-consumption-insights"></a>Ligar a Informações sobre Consumo do Azure
Para ligar com êxito através do conector **Informações sobre Consumo do Azure**, tem de ter acesso às funcionalidades empresariais (Enterprise) no portal do Azure.

Para ligar através do conector **Informações sobre Consumo do Azure**, selecione **Obter Dados** no friso **Base** do **Power BI Desktop**. Selecione **Serviços Online** na lista de categorias no lado esquerdo para encontrar **Informações sobre Consumo do Microsoft Azure (Beta)**. Selecione **Ligar**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_01b.png)

Na caixa de diálogo apresentada, forneça o seu *Número de Inscrição*.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_02.png)

* Pode obter o seu número de inscrição no [Azure Enterprise Portal](https://ea.azure.com), na localização indicada na seguinte imagem:
  
  ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_08.png)
  
  Esta versão do conector só suporta inscrições de empresas provenientes de https://ea.azure.com. Não são atualmente suportadas inscrições oriundas da China.

Em seguida, forneça a sua *Chave de acesso* para ligar.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_03.png)

* Pode encontrar a sua Chave de acesso para a inscrição no [Azure Enterprise Portal](https://ea.azure.com).
  
  ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_09.png)

Depois de fornecer a *Chave de acesso* e selecionar **Ligar**, é apresentada uma janela **Navegador** com quatro tabelas à sua disposição: *Resumo*, *Utilização*, *Folha de Preços* e *Mercado*. Pode selecionar a caixa de verificação ao lado de qualquer uma das tabelas para ver uma pré-visualização. Pode selecionar uma ou mais tabelas ao marcar a caixa junto do respetivo nome; em seguida, selecione **Carregar**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_04.png)

> [!NOTE]
> As tabelas *Resumo* e *Folha de Preços* só estão disponíveis para a Chave de API do nível de inscrição. Além disso, os dados nestas tabelas contêm, por predefinição, os dados do mês atual em termos de *Utilização* e *Folha de Preços*. As tabelas *Resumo* e *Mercado* não estão limitadas ao mês atual.
> 
> 

Ao selecionar **Carregar**, os dados são carregados no **Power BI Desktop**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_05.png)

Após o carregamento dos dados selecionados, as tabelas e os campos que selecionou podem ser vistos no painel **Campos**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_06.png)

## <a name="using-azure-consumption-insights"></a>Utilizar o conector Informações sobre Consumo do Azure
Para utilizar o conector **Informações sobre Consumo do Azure**, tem de ter acesso às funcionalidades empresariais no portal do Azure.

Depois de carregar os dados com êxito através do conector **Informações sobre Consumo do Azure**, pode criar as suas próprias medidas e colunas personalizadas com o **Editor de Consultas**. Além disso, pode criar elementos visuais, relatórios e dashboards que pode partilhar no **serviço Power BI**.

O Azure também inclui uma coleção de exemplos de consultas personalizadas, que pode obter mediante a utilização de uma consulta em branco. Para tal, no friso **Página Inicial** do **Power BI Desktop**, selecione a seta pendente em **Obter Dados** e, em seguida, selecione **Consulta em Branco**. Também pode fazê-lo no **Editor de Consultas** ao clicar com o botão direito do rato no painel **Consultas** no lado esquerdo e selecionar **Nova Consulta > Consulta em Branco** no menu apresentado.

Na **Barra de fórmulas**, escreva o seguinte:

    = MicrosoftAzureConsumptionInsights.Contents

Será apresentada uma coleção de exemplos, conforme mostrado na seguinte imagem:

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_07.png)

Quando estiver a trabalhar com relatórios e a criar consultas, utilize o seguinte:

* Para definir o número de meses a contar da data atual, utilize *numberOfMonth*
  * Utilize um valor entre um e 36 para representar o número de meses, a contar da data atual, que quer importar. Recomendamos que não obtenha mais de 12 meses de dados para evitar limiares com restrições de importação e o volume de dados permitidos para consultas no Power BI.
* Para definir um período de meses numa janela de tempo do histórico, utilize *startBillingDataWindow* e *endBillingDataWindow*
* *Não* utilize *numberOfMonth* em conjunto com *startBillingDataWindow* ou *endBillingDataWindow*

## <a name="migrating-from-the-azure-enterprise-connector"></a>Migrar a partir do Conector Empresarial do Azure
Alguns clientes criaram elementos visuais com o *Conector Empresarial do Azure (Beta)*, o qual será eventualmente descontinuado e está a ser substituído pelo conector **Informações sobre Consumo do Azure**. O conector **Informações sobre Consumo do Azure** tem funcionalidades e melhoramentos que incluem o seguinte:

* Origens de dados adicionais disponíveis para *Resumo do Saldo* e *Compras no Mercado*
* Novos parâmetros avançados, como *startBillingDataWindow* e *endBillingDataWindow*
* Melhor desempenho e maior capacidade de resposta

Para ajudar os clientes a efetuar a transição para o conector **Informações sobre Consumo do Azure** mais recente, bem como para preservar o trabalho já realizado em termos de criação de relatórios ou dashboards personalizados, os passos que se seguem mostram como mudar para o novo conector.

### <a name="step-1-connect-to-azure-using-the-new-connector"></a>Passo 1: Ligar ao Azure através do novo conector
O primeiro passo consiste em ligar através do conector **Informações sobre Consumo do Azure**, descrito anteriormente neste artigo em detalhe. Neste passo, selecione **Obter Dados > Consulta em Branco** no friso **Página Inicial** do **Power BI Desktop**.

### <a name="step-2-use-the-advanced-editor-to-create-a-query"></a>Passo 2: Utilizar o Editor Avançado para criar uma consulta
No **Editor de Consultas**, selecione **Editor Avançado** na secção **Consulta** do friso **Página Inicial**. Na janela **Editor Avançado** apresentada, introduza a seguinte consulta:

    let    
        enrollmentNumber = "100",
        optionalParameters = [ numberOfMonth = 6, dataType="DetailCharges" ],
        data = MicrosoftAzureConsumptionInsights.Contents(enrollmentNumber, optionalParameters)   
    in     
        data

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_10.png)

Naturalmente, terá de substituir o valor de *enrollmentNumber* pelo seu número de inscrição, que pode obter a partir do [Azure Enterprise Portal](https://ea.azure.com). O parâmetro *numberOfMonth* corresponde ao número de meses de dados que pretende andar para trás, a partir dos dados atuais. Utilize zero (0) para o mês atual.

Depois de selecionar **Concluído** na janela **Editor Avançado**, a pré-visualização é atualizada e os dados relativos ao intervalo de meses especificado serão apresentados na tabela. Selecione **Fechar e Aplicar** e regresse.

### <a name="step-3-move-measures-and-custom-columns-to-the-new-report"></a>Passo 3: Mover medidas e colunas personalizadas para o novo relatório
Em seguida, terá de mover todas as medidas ou colunas personalizadas que criou para a nova tabela de detalhes. Seguem-se os passos necessários.

1. Abra o Bloco de Notas (ou outro editor de texto).
2. Selecione a medida que quer mover, copie o texto do campo *Fórmula* e coloque-o no Bloco de Notas.
   
   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_11.png)
3. Mude o nome *Query1* para o nome da tabela de detalhes original.
4. Crie novas medidas e colunas personalizadas na sua tabela ao clicar com o botão direito do rato na tabela e escolher **Nova Medida**. Em seguida, corte e cole as medidas e colunas armazenadas até chegar ao fim das mesmas.

### <a name="step-4-re-link-tables-that-had-relationships"></a>Passo 4: Voltar a ligar as tabelas que tinham relações
Muitos dashboards têm tabelas adicionais que são utilizadas para pesquisa ou filtragem, tais como tabelas de datas ou tabelas utilizadas para projetos personalizados. O restabelecimento dessas relações resolve a maioria dos problemas restantes. Saiba como o fazer a seguir.

- No separador **Modelação** do **Power BI Desktop**, selecione **Gerir Relações** para abrir uma janela que permite gerir as relações no modelo. Volte a ligar as tabelas, conforme necessário.
   
    ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_12.png)

### <a name="step-5-verify-your-visuals-and-adjust-field-formatting-as-needed"></a>Passo 5: Verificar os elementos visuais e ajustar a formatação dos campos, conforme necessário
Quando chegar a esta fase, a maior parte dos elementos visuais, tabelas e desagregações originais deverão estar a funcionar conforme esperado. No entanto, poderão ser necessários alguns pequenos ajustes em termos de formatação, para que tudo tenha o aspeto desejado. Dedique algum tempo à visualização de cada um dos dashboards e elementos visuais, para garantir que está tudo de acordo com os seus padrões estéticos.

## <a name="using-the-azure-consumption-and-insights-aci-api-to-get-consumption-data"></a>Utilizar a API Informações sobre Consumo do Azure (ACI) para obter dados de consumo
O Azure também disponibiliza a [**API Informações sobre Consumo do Azure (ACI)**](https://azure.microsoft.com/blog/announcing-general-availability-of-consumption-and-charge-apis-for-enterprise-azure-customers/). Pode criar as suas próprias soluções personalizadas para recolher, comunicar e visualizar informações sobre consumo do Azure através da API ACI.

### <a name="mapping-names-and-usage-details-between-the-portal-the-connector-and-the-api"></a>Mapear nomes e detalhes de utilização entre o portal, o conector e a API
As colunas e os nomes dos detalhes no Portal do Azure são semelhantes na API e no conector, mas nem sempre são idênticos. Para ajudar a esclarecer as diferenças, a tabela seguinte fornece um mapeamento entre a API, o conector e as colunas apresentadas no Portal do Azure. Também é indicado se a coluna está obsoleta. Para obter mais informações e definições sobre estes termos, consulte o [Dicionário de dados de faturação do Azure](https://docs.microsoft.com/azure/billing/billing-enterprise-api-usage-detail).

| Nome da Coluna do Conector ACI/Pacote de Conteúdos | Nome da Coluna da API ACI | Nome da Coluna de EA | Obsoleto/Presente para retrocompatibilidade |
| --- | --- | --- | --- |
| AccountName |accountName |Nome da Conta |Não |
| AccountId |accountId | |Sim |
| AccountOwnerId |accountOwnerEmail |AccountOwnerId |Não |
| AdditionalInfo |additionalInfo |AdditionalInfo |Não |
| AdditionalInfold | | |Sim |
| Quantidade Consumida |consumedQuantity |Quantidade Consumida |Não |
| Serviço Consumido |consumedService |Serviço Consumido |Não |
| ConsumedServiceId |consumedServiceId | |Sim |
| Custo |custo |ExtendedCost |Não |
| Centro de Custos |costCenter |Centro de Custos |Não |
| Data |data |Data |Não |
| Dia | |Dia |Não |
| DepartmentName |departmentName |Nome do Departamento |Não |
| DepartmentID |departmentId | |Sim |
| ID da Instância | | |Sim |
| InstanceId |instanceId |ID da Instância |Não |
| Localização | | |Sim |
| Categoria de Medidor |meterCategory |Categoria de Medidor |Não |
| ID do Medidor | | |Sim |
| Nome do Medidor |meterName |Nome do Medidor |Não |
| Região do Medidor |meterRegion |Região do Medidor |Não |
| Subcategoria do Medidor |meterSubCategory |Subcategoria do Medidor |Não |
| MeterId |meterId |ID do Medidor |Não |
| Mês | |Mês |Não |
| Produto |produto |Produto |Não |
| ProductId |productId | |Sim |
| Grupo de Recursos |resourceGroup |Grupo de Recursos |Não |
| Localização do Recurso |resourceLocation |Localização do Recurso |Não |
| ResourceGroupId | | |Sim |
| ResourceLocationId |resourceLocationId | |Sim |
| ResourceRate |resourceRate |ResourceRate |Não |
| ServiceAdministratorId |serviceAdministratorId |ServiceAdministratorId |Não |
| ServiceInfo1 |serviceInfo1 |ServiceInfo1 |Não |
| ServiceInfo1Id | | |Sim |
| ServiceInfo2 |serviceInfo2 |ServiceInfo2 |Não |
| ServiceInfo2Id | | |Sim |
| Identificador do Serviço de Arquivo |storeServiceIdentifier |Identificador do Serviço de Arquivo |Não |
| StoreServiceIdentifierId | | |Sim |
| Nome da Subscrição |subscriptionName |Nome da Subscrição |Não |
| Etiquetas |etiquetas |Etiquetas |Não |
| TagsId | | |Sim |
| Unidade de Medida |unitOfMeasure |Unidade de Medida |Não |
| Ano | |Ano |Não |
| SubscriptionId |subscriptionId |SubscriptionId |Sim |
| SubscriptionGuid |subscriptionGuid |SubscriptionGuid |Não |

## <a name="next-steps"></a>Passos seguintes
Existem diversos tipos de dados aos quais se pode ligar através do Power BI Desktop. Para obter mais informações sobre origens de dados, consulte os seguintes recursos:

* [Introdução ao Power BI Desktop](desktop-getting-started.md)
* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Ligar a livros do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Introduzir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

