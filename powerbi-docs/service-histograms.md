---
title: Histogramas
description: Histogramas
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Visualizations
ms.openlocfilehash: 94c1e23fc012e40763247a28e8930a9abdd81425
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="histograms"></a>Histogramas
Existem várias formas de criar histogramas no Power BI. Começaremos com a mais simples e continuamos a partir daí.

## <a name="simple-histograms"></a>Histogramas Simples
Para começar, determine que consulta contém o campo no qual quer criar um histograma.  Utilize a opção *Referência* da consulta para criar uma nova consulta e dê-lhe o nome de *Histograma FieldName*. Utilize a opção **Agrupar por** no friso **Transformar** e selecione a agregação de **contagem de linhas**. Certifique-se de que o tipo de dados é um número para a coluna agregada resultante. Em seguida, pode visualizar estes dados na página de relatórios. Esta abordagem é rápida e fácil de criar, mas não funciona corretamente se tiver muitos pontos de dados e não permite brushing entre elementos visuais.

## <a name="defining-buckets-to-build-a-histogram"></a>Definir registos para criar um histograma
Determine que consulta contém o campo no qual quer criar um histograma. Utilize a opção *Referência* da consulta para criar uma nova consulta e dê-lhe o nome de *FieldName*.  Agora, defina os registos com uma regra. Utilize a opção **Adicionar Coluna Personalizada** no friso **Adicionar Coluna** e crie uma regra personalizada.

![](media/service-histograms/powerbi-service-histograms_1.png)

Certifique-se de que o tipo de dados é um número para a coluna agregada resultante. Agora pode utilizar o grupo pela técnica descrita em **Histogramas Simples** (no início deste artigo) para chegar ao histograma. Esta opção processa mais pontos de dados, mas ainda não ajuda no brushing.

## <a name="defining-a-histogram-that-supports-brushing"></a>Definir um histograma que suporte brushing
Brushing é quando os elementos visuais são associados para que, quando um utilizador selecionar um ponto de dados num elemento visual, os outros elementos visuais na página de relatório realcem ou filtrem os pontos de dados relacionados com o ponto de dados selecionado.  Como estamos a manipular dados no momento da consulta, temos de criar uma relação entre tabelas e garantir que sabemos que item detalhado está relacionado com o registo no histograma e vice-versa.

Inicie o processo através da opção *Referência* na consulta que contém o campo no qual quer criar um histograma.  Nomeie a nova consulta *Grupos*.  Para este exemplo, vamos chamar a consulta original *Detalhes*.  Em seguida, remova todas as colunas, exceto a coluna que utilizará como registo do histograma.  Utilize agora a funcionalidade *Remover Duplicados* na consulta, no menu de atalho ao selecionar a coluna, para que os restantes valores sejam os valores exclusivos na coluna. Se tiver números decimais, pode utilizar primeiro a sugestão de definir registos para criar um histograma para obter um conjunto de registos gerível.  Agora, verifique os dados mostrados na pré-visualização da consulta. Se vir valores nulos ou em branco, terá de os corrigir antes de criar uma relação. Veja "Criar relações se os dados tiverem valores nulos ou em branco". Utilizar esta abordagem pode ser problemático devido à necessidade de ordenação. Para que os registos sejam ordenados corretamente, veja "Ordenação: fazer com que as categorias apareçam na ordem que quero". 

> [!NOTE]
> É bastante útil pensar sobre a ordem de classificação antes de criar qualquer elemento visual.   
> 
> 

A próxima etapa do processo é definir uma relação entre as consultas de *Grupos* e *Detalhes* na coluna de grupos.  No *Power BI Desktop*, selecione *Gerir Relações* no friso.  Crie uma relação onde os *Grupos* estão na tabela esquerda e os *Detalhes* na tabela direita e selecione o campo que está a utilizar para o histograma. 

O último passo é criar o histograma. Arraste o campo Grupo da tabela *Grupos*. Remova o campo predefinido do gráfico de colunas resultante.  Agora, na tabela *Detalhes*, arraste o campo do histograma até ao mesmo elemento visual. No painel do campo, altere a agregação predefinida para Contar. O resultado é o histograma. Se criar outro elemento visual como um treemap a partir da tabela Detalhes, selecione um ponto de dados no treemap para ver o histograma realçado e mostrá-lo para o ponto de dados selecionado em relação à tendência de todo o conjunto de dados.

