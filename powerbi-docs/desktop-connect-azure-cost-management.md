---
title: Ligar aos dados do Azure Cost Management no Power BI Desktop
description: Ligar facilmente ao Azure e obter informações sobre o Cost Management com o Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/14/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1ef9deac169873d7faee33abdae9f8f38aa09c6d
ms.sourcegitcommit: 549401b0e1fad15c3603fe7f14b9494141fbb100
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2019
ms.locfileid: "72308013"
---
# <a name="connect-to-azure-cost-management-data-in-power-bi-desktop"></a>Ligar aos dados do Azure Cost Management no Power BI Desktop

Pode utilizar o conector do Azure Cost Management do Power BI Desktop para criar relatórios e visualizações poderosos e personalizados para o ajudar a compreender melhor os gastos do Azure. O conector do Azure Cost Management suporta atualmente clientes com o [Contrato de Cliente da Microsoft](https://azure.microsoft.com/pricing/purchase-options/microsoft-customer-agreement/) ou um [Contrato Enterprise (EA)](https://azure.microsoft.com/pricing/enterprise-agreement/).  

O conector do Azure Cost Management utiliza o OAuth 2.0 para autenticação com o Azure. Para se ligar, deve utilizar uma conta de [Administrador do Enterprise](https://docs.microsoft.com/azure/billing/billing-understand-ea-roles) para os Contratos Enterprise ou uma de [Proprietário da conta de faturação](https://docs.microsoft.com/azure/billing/billing-understand-mca-roles) para os Contratos de Cliente da Microsoft. 

> [!NOTE]
> Este conector substitui o conector do [Azure Cost Management (Beta)](desktop-connect-azure-consumption-insights.md) anteriormente disponível. Todos os relatórios criados com o conector anterior devem ser recriados com este conector.

## <a name="connect-using-azure-cost-management"></a>Ligar com o Azure Cost Management

Para utilizar o conector do **Azure Cost Management** no Power BI Desktop, siga estes passos:

1.  No friso **Home Page**, selecione **Obter Dados**.
2.  Selecione **Azure**  na lista de categorias de dados.
3.  Selecione **Azure Cost Management**.

    ![Obter dados](media/desktop-connect-azure-cost-management/azure-cost-management-00b.png)

4. Na caixa de diálogo apresentada, introduza o **ID do Perfil de Faturação** para os **Contratos de Cliente da Microsoft** ou o **Número de Inscrição** para os **Contratos Enterprise (EA)** . 


## <a name="connect-to-a-microsoft-customer-agreement-account"></a>Ligar-se a uma conta a Contrato de Cliente da Microsoft 

Para se ligar a uma conta do **Contrato de Cliente da Microsoft**, pode obter o **ID do Perfil de Faturação** no portal do Azure:

1.  No [portal do Azure](https://portal.azure.com/), navegue para **Cost Management + Faturação**.
2.  Selecione o Perfil de faturação. 
3.  Em **Definições** no menu, selecione **Propriedades** na barra lateral.
4.  Em **Perfil de faturação**, copie o **ID**. 
5.  Para **Escolher Âmbito**, selecione **ID do Perfil de Faturação** e cole o ID do perfil de faturação do passo anterior. 
6.  Introduza o número de meses e selecione **OK**.

    ![Obter o ID de faturação](media/desktop-connect-azure-cost-management/azure-cost-management-01a.png)

7.  Quando pedido, inicie sessão com a conta de utilizador e a palavra-passe do Azure. 


## <a name="connect-to-an-enterprise-agreement-account"></a>Ligar-se a uma conta do Contrato Enterprise

Para se ligar com uma conta do Contrato Enterprise (EA), pode obter o ID de inscrição no portal do Azure:

1.  No [portal do Azure](https://portal.azure.com/), navegue para **Cost Management + Faturação**.
2.  Selecione a sua conta de faturação.
3.  No menu **Descrição geral** , copie o **ID da conta de faturação**.
4.  Para **Escolher Âmbito**, selecione **Número de Inscrição** e cole o ID da conta de faturação do passo anterior. 
5.  Introduza o número de meses e, em seguida, selecione **OK**.

    ![Obter o ID de faturação](media/desktop-connect-azure-cost-management/azure-cost-management-01b.png)

6.  Quando pedido, inicie sessão com a conta de utilizador e a palavra-passe do Azure. 

## <a name="data-available-through-the-connector"></a>Dados disponíveis através do conector

Após ser autenticado com sucesso, é apresentada uma janela do **Navegador** com as seguintes tabelas de dados disponíveis:



| **Tabela** | **Descrição** |
| --- | --- |
| **Resumo de saldo** | Resumo do saldo de um Contrato Enterprise (EA). |
| **Billing events** (Eventos de faturação) | Registo de eventos das novas faturas, compras de crédito, etc. Apenas Contratos de Cliente da Microsoft. |
| **Orçamentos** | Detalhes dos orçamentos para ver os custos reais ou a utilização em comparação com os objetivos orçamentais existentes. |
| **Cobranças** | Um resumo mensal da utilização do Azure, cobranças do Marketplace e cobranças faturadas separadamente. Apenas Contratos de Cliente da Microsoft. |
| **Credit lots** (Lotes de crédito) | Os detalhes de compra de lotes de crédito do Azure para o perfil de faturação fornecido. Apenas Contratos de Cliente da Microsoft. |
| **Pricesheets** (Folhas de preços) | Taxas de medição aplicáveis para o perfil de faturação ou inscrição EA. |
| **RI charges** (Cobranças de RI) | Cobranças associadas às Instâncias Reservadas nos últimos 24 meses. |
| **RI recommendations (shared)** (Recomendações de RI [partilhado]) | Recomendações de compra de Instâncias Reservadas com base em todas as suas tendências de utilização de subscrição nos últimos 7, 30 ou 60 dias. |
| **RI recommendations (single)** (Recomendações de RI [individual]) | Recomendações de compra de Instâncias Reservadas com base nas suas tendências de utilização de subscrição individual nos últimos 7, 30 ou 60 dias. |
| **Detalhes de utilização de RI** | Detalhes de consumo das Instâncias Reservadas existentes no mês anterior. |
| **Resumo de utilização de RI** | Percentagem de utilização da reserva diária do Azure. |
| **Usage details** (Detalhes de utilização) | Uma análise das quantidades consumidas e da estimativa das cobranças para o perfil de faturação ou inscrição EA fornecido. |
| **Detalhes de utilização amortizados** | Uma análise das quantidades consumidas e da estimativa das cobranças amortizadas para o perfil de faturação ou inscrição EA fornecido. |

Pode selecionar uma tabela para ver uma caixa de diálogo de pré-visualização. Pode selecionar uma ou mais tabelas ao selecionar as caixas junto do nome e, em seguida, selecionar **Carregar**.

![Obter o ID de faturação](media/desktop-connect-azure-cost-management/azure-cost-management-01c.png)

Quando selecionar **Carregar**, os dados serão carregados para o Power BI Desktop. 

Quando os dados selecionados tiverem sido carregados, os campos e as tabelas de dados são apresentados no painel **Campos**.


## <a name="next-steps"></a>Próximos passos

Pode ligar a muitas origens de dados diferentes através do Power BI Desktop. Para obter mais informações, veja os seguintes artigos:

* [O que é o Power BI Desktop?](desktop-what-is-desktop.md)
* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Ligar a livros do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Introduzir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
