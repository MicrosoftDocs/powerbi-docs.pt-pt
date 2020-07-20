---
title: Classificação de dados dos dashboards
description: Saiba mais sobre a classificação de dados dos dashboards, incluindo como um Administrador os deve configurar e como os proprietários de dashboards podem alterar a classificação.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 08/10/2017
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: d8c7a8532122487bdf3bcd718eb4089cb7c67008
ms.sourcegitcommit: e8ed3d120699911b0f2e508dc20bd6a9b5f00580
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/11/2020
ms.locfileid: "86262809"
---
# <a name="dashboard-data-classification"></a>Classificação de dados dos dashboards
Todos os dashboards são diferentes e, consoante a origem de dados à qual se está a ligar, é provável que o utilizador e os colegas com quem partilha tenham de tomar diferentes precauções, dependendo da confidencialidade dos dados. Alguns dashboards nunca devem ser partilhados com pessoas externas à empresa nem imprimidos. Outros podem ser livremente partilhados. Ao utilizar a classificação de dados de dashboard, poderá sensibilizar as pessoas que virem os seus dashboards sobre o nível de segurança a empregar. Pode marcar os seus dashboards com classificações definidas pelo departamento de TI da sua empresa, para que todas as pessoas a ver os conteúdos tenham o mesmo nível de compreensão sobre a confidencialidade dos dados.

![Captura de ecrã a mostrar um dashboard, com a classificação de dados de uma amostra.](media/service-data-classification/dashboard_tagged_as_hbi.png)

## <a name="data-classification-tags"></a>Etiquetas de classificação de dados
As etiquetas de classificação de dados aparecem junto ao nome do dashboard, para que qualquer pessoa a visualizá-lo saiba o nível de segurança que deve ser aplicado ao dashboard e aos respetivos dados.

![Captura de ecrã a mostrar um dashboard, com uma etiqueta de classificação de dados junto ao nome do dashboard.](media/service-data-classification/tag_next_to_title.png)

Também aparecerá junto ao mosaico do dashboard na sua lista de Favoritos.

![Captura de ecrã a mostrar a lista Favoritos, com uma etiqueta de classificação de dados junto ao mosaico do dashboard na lista de Favoritos.](media/service-data-classification/tag_on_dashboard_tile.png)

Quando passar o cursor sobre a etiqueta, irá ver o nome completo da classificação.

![Captura de ecrã a mostrar a etiqueta H B I, com o nome completo da classificação quando paira o cursor sobre a etiqueta. ](media/service-data-classification/tag_tooltip.png)

Os administradores também podem definir um URL de uma etiqueta para fornecer mais informações.

> [!NOTE]
> Consoante as definições de classificação definidas pelo seu administrador, alguns tipos de classificação poderão não ser apresentados como uma etiqueta no dashboard. Se for um proprietário de dashboard, pode sempre ver o tipo de classificação do dashboard nas definições de dashboard.
> 
> 

## <a name="setting-a-dashboards-classification"></a>Definir a classificação de um dashboard
Se a classificação de dados estiver ativada na sua empresa, todos os dashboards começam com um tipo predefinido de classificação mas, enquanto proprietário do dashboard, pode alterar a classificação para corresponder ao nível de segurança do seu dashboard.

Para alterar o tipo de classificação, faça o seguinte:

1. Aceda às definições do dashboard ao selecionar as **reticências** junto ao nome do dashboard e selecionar **Definições**.
   
    ![Captura de ecrã a mostrar um dashboard com a seleção de Definições.](media/service-data-classification/dashboard_settings.png)
2. Em Definições do dashboard, poderá ver a classificação atual do seu dashboard e utilizar o menu pendente para alterar o tipo de classificação.
   
    ![Captura de ecrã a mostrar as definições do dashboard com uma classificação atual e a seleção pendente da Classificação de dados.](media/service-data-classification/classification_setting_dropdown.png)
3. Selecione **Aplicar** quando concluir.

Após aplicar a alteração, qualquer pessoa com quem tiver partilhado irá ver a atualização da próxima vez que atualizar o dashboard.

## <a name="working-with-data-classification-tags-as-an-admin"></a>Trabalhar com etiquetas de classificação de dados como administrador
A classificação de dados é configurada pelo administrador global da sua organização. Para ativar a classificação de dados, faça o seguinte:

1. Selecione a engrenagem das definições e selecione **Portal de Administração**.
   
    ![Captura de ecrã a mostrar a engrenagem das Definições com a seleção do Portal de Administração.](media/service-data-classification/admin_portal_in_settings.png)
2. Deixe a opção **Classificação de dados para dashboards e relatórios** *ativada* no separador **Definições de inquilino**.
   
    ![Captura de ecrã a mostrar o Portal de Administração, com as definições de Inquilino e a Classificação de dados para os dashboards e seleção de relatórios.](media/service-data-classification/data_classification_switch_location.png)

Depois de ativar, será apresentado um formulário para criar as diversas classificações na sua organização.

![Captura de ecrã a mostrar um formulário, com entradas de campo para diversas classificações na sua organização.](media/service-data-classification/blank_classification_form.png)

Cada classificação tem um **nome** e uma **abreviatura** que aparecerão no dashboard. Para cada classificação, pode decidir se a etiqueta abreviada irá aparecer no dashboard ou não ao selecionar **Mostrar etiqueta**. Se decidir não mostrar o tipo de classificação no dashboard, o proprietário continuará a conseguir ver o tipo ao consultar as definições do dashboard. Além disso, pode optar por adicionar um **URL** que contenha mais informações sobre as diretrizes de classificação e requisitos de utilização da sua organização.  

A última coisa a decidir é qual o tipo de classificação predefinido.  

Após preencher o formulário com os seus tipos de classificação, selecione **Aplicar** para guardar as alterações.

![Captura de ecrã a mostrar um formulário, com entradas preenchidas com os tipos de classificações a aplicar.](media/service-data-classification/filled_in_classification_form.png)

Nesta fase, todos os dashboards serão atribuídos à classificação predefinida. Os proprietários do dashboard podem agora atualizar o tipo de classificação para o que for mais adequado aos respetivos conteúdos. Pode regressar a este local posteriormente para adicionar ou remover tipos de classificação ou alterar a predefinição.  

> [!NOTE]
> Há alguns elementos importantes a ter em conta quando regressar para efetuar alterações:
> 
> * Se desativar a classificação de dados, as etiquetas não serão memorizadas. Terá de começar do início se decidir ativá-la posteriormente.  
> * Se remover um tipo de classificação, os dashboards que tenham recebido o tipo de classificação removido voltarão à predefinição até que o proprietário o defina novamente.  
> * Se alterar a predefinição, todos os dashboards que ainda não tenham recebido um tipo de classificação pelo proprietário serão alterados para a nova predefinição.
> 
> 

