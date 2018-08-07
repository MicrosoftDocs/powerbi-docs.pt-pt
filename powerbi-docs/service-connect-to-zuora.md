---
title: Ligue-se ao Zuora com o Power BI
description: Zuora para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 48246d61789a0b1e160109c1f2fb0e81838b3965
ms.sourcegitcommit: fbb7924603f8915d07b5e6fc8f4d0c7f70c1a1e1
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/02/2018
ms.locfileid: "39280323"
---
# <a name="connect-to-zuora-with-power-bi"></a>Ligue-se ao Zuora com o Power BI
O Zuora para o Power BI permite que visualize dados importantes de receitas, faturação e subscrição. Utilize o dashboard e os relatórios predefinidos para analisar tendências de utilização, acompanhar cobranças e pagamentos e monitorizar receitas recorrentes ou personalizá-las para atender às suas necessidades exclusivas do dashboard e do relatório.

Ligue-se ao [Zuora](https://app.powerbi.com/getdata/services/Zuora) para o Power BI.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.

   ![](media/service-connect-to-zuora/getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.

   ![](media/service-connect-to-zuora/services.png)
3. Selecione **Zuora** \>  **Obter**.

   ![](media/service-connect-to-zuora/zuora.png)
4. Especifique o URL do Zuora. Geralmente, o URL é "<https://www.zuora.com>". Veja os detalhes sobre como [encontrar esses parâmetros](#FindingParams) abaixo.

   ![](media/service-connect-to-zuora/params.png)
5. Para o **Método de Autenticação**, selecione **Básico** e forneça o seu nome de utilizador e a sua palavra-passe (diferencia maiúsculas de minúsculas) e selecione **Iniciar Sessão**.

    ![](media/service-connect-to-zuora/creds.png)
6. Após a aprovação, o processo de importação será iniciado automaticamente. Quando concluído, um novo dashboard, relatório e modelo aparecerão no Painel de Navegação. Selecione o dashboard para ver os seus dados importados.

     ![](media/service-connect-to-zuora/dashboard.png)

**O que se segue?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](power-bi-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento de atualização ou tentar atualizá-lo a pedido através de **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
O pacote de conteúdos utiliza a API AQUA do Zuora para efetuar pull das seguintes tabelas:

| Tabelas |  |  |
| --- | --- | --- |
| Account |InvoiceItemAdjustment |Refund |
| AccountingCode |Payment |RevenueSchedule |
| AccountingPeriod |PaymentMethod |RevenueScheduleItem |
| BillTo |Product |Subscription |
| DateDim |ProductRatePlan |TaxationItem |
| Invoice |ProductRatePlanCharge |Uso |
| InvoiceAdjustment |RatePlan | |
| InvoiceItem |RatePlanCharge | |

Também inclui as medidas calculadas abaixo:

| Medida | Descrição | Pseudocálculo |
| --- | --- | --- |
| Conta: Pagamentos |Valores totais de pagamento num período de tempo, com base na data de realização do pagamento. |SUM (Payment.Amount) <br>WHERE<br>Payment.EffectiveDate =< TimePeriod.EndDate<br>AND    Payment.EffectiveDate >= TimePeriod.StartDate |
| Conta: Reembolsos |Valores totais de reembolso num período de tempo, com base na data de reembolso. O valor é comunicado como um número negativo. |-1*SUM (Refund.Amount)<br>WHERE<br>Refund.RefundDate =< TimePeriod.EndDate<br>AND    Refund.RefundDate >= TimePeriod.StartDate |
| Conta: Pagamentos Líquidos |Pagamentos de Conta mais Reembolsos de Conta num período de tempo. |Account.Payments + Account.Refunds |
| Conta: Contas Ativas |A contagem de contas ativas num período de tempo. As subscrições devem ter sido iniciadas na data de início de um período de tempo ou antes. |COUNT (Account.AccountNumber)<br>WHERE<br>    Subscription.Status != "Expired"<br>AND    Subscription.Status != "Draft"<br>AND    Subscription.SubscriptionStartDate <= TimePeriod.StartDate<br>AND    (Subscription.SubscriptionEndDate > TimePeriod.StartDate<br>OR<br>Subscription.SubscriptionEndDate = null) – assinatura evergreen |
| Conta: Receita Média Recorrente |MRR bruto por conta ativa num período de tempo. |Gross MRR/Account.ActiveAccounts |
| Conta: Assinaturas Canceladas |O número de contas que cancelaram uma assinatura num período de tempo. |COUNT (Account.AccountNumber)<br>WHERE<br>Subscription.Status = "Cancelled"<br>AND    Subscription.SubscriptionStartDate <= TimePeriod.StartDate<br>AND    Subscription.CancelledDate >= TimePeriod.StartDate |
| Contas: Erros de Pagamento |Valor total de erros de pagamento. |SUM (Payment.Amount)<br>WHERE<br>Payment.Status = "Error" |
| Item de Agendamento de Receita: Receita Reconhecida |Receita total reconhecida num período de contabilidade. |SUM (RevenueScheduleItem.Amount)<br>WHERE<br>AccountingPeriod.StartDate = TimePeriod.StartDate |
| Assinatura: Novas Assinaturas |Contagem de novas assinaturas num período de tempo. |COUNT (Subscription.ID)<br>WHERE<br>Subscription.Version = "1"<br>AND    Subscription.CreatedDate <= TimePeriod.EndDate<br>AND    Subscription.CreatedDate >= TimePeriod.StartDate |
| Fatura: Itens da Fatura |Valores totais de encargos de item da fatura num período de tempo. |SUM (InvoiceItem.ChargeAmount)<br>WHERE<br>    Invoice.Status = "Posted"<br>AND    Invoice.InvoiceDate <= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate >= TimePeriod.StartDate |
| Fatura: Itens de Tributação |Valores totais de item de tributação num período de tempo. |SUM (TaxationItem.TaxAmount)<br>WHERE<br>Invoice.Status = "Posted"<br>AND    Invoice.InvoiceDate <= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate >= TimePeriod.StartDate |
| Fatura: Ajustes de Item da Fatura |Valores totais de ajuste de item da fatura num período de tempo. |SUM (InvoiceItemAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    InvoiceItemAdjustment.AdjustmentDate <= TimePeriod.EndDate<br>AND    InvoiceItemAdjustment.AdjustmentDate >= TimePeriod.StartDate |
| Fatura: Ajustes de Fatura |Valores totais de ajuste de fatura num período de tempo. |SUM (InvoiceAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    InvoiceAdjustment.AdjustmentDate <= TimePeriod.EndDate<br>AND    InvoiceAdjustment.AdjustmentDate >= TimePeriod.StartDate |
| Fatura: Faturações Líquidas |Soma dos itens da fatura, itens de tributação, ajustes de item da fatura e ajustes da fatura num período de tempo. |Invoice.InvoiceItems + Invoice.TaxationItems + Invoice.InvoiceItemAdjustments + Invoice.InvoiceAdjustments |
| Fatura: Balanço de Faturação em Vencimento |Soma do balanço de faturas lançadas. |SUM (Invoice.Balance) <br>WHERE<br>    Invoice.Status = "Posted" |
| Fatura: Cobranças Brutas |Soma dos valores de cobrança de item da fatura para faturas lançadas num período de tempo. |SUM (InvoiceItem.ChargeAmount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    Invoice.InvoiceDate <= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate >= TimePeriod.StartDate |
| Fatura: Ajustes Totais |Soma de ajustes de fatura processados e ajustes de item de fatura associados às faturas lançadas. |SUM (InvoiceAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    InvoiceAdjustment.Status = "Processed"<br>+<br>SUM (InvoiceItemAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    invoiceItemAdjustment.Status = "Processed" |
| Despesas de Plano de Taxa: MRR Bruto |Soma da receita mensal recorrente das subscrições num período de tempo. |SUM (RatePlanCharge.MRR) <br>WHERE<br>    Subscription.Status != "Expired"<br>AND    Subscription.Status != "Draft"<br>AND    RatePlanCharge.EffectiveStartDate <= TimePeriod.StartDate<br>AND        RatePlanCharge.EffectiveEndDate > TimePeriod.StartDate<br>    OR    RatePlanCharge.EffectiveEndDate = null --evergreen subscription |

## <a name="system-requirements"></a>Requisitos do sistema
É necessário ter acesso à API do Zuora.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>A localizar parâmetros
Forneça o URL com a qual se liga normalmente para aceder aos seus dados do Zuora. As opções válidas são:  

* https://www.zuora.com  
* https://www.apisandbox.zuora.com  
* O URL correspondente à instância do serviço  

## <a name="troubleshooting"></a>Resolução de problemas
O pacote de conteúdos do Zuora mantém vários aspetos diferentes da sua conta do Zuora. Se não utilizar determinadas funcionalidades, pode ver os mosaicos/relatórios correspondentes vazios. Se tiver problemas ao carregar, contacte o Suporte do Power BI.

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Obter dados no Power BI](service-get-data.md)
