---
title: Ligar-se ao Xero com o Power BI
description: Xero para Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 03/06/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: adb2f66b043b09ecb584870cf96f4c491960d59b
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348442"
---
# <a name="connect-to-xero-with-power-bi"></a>Ligar-se ao Xero com o Power BI
O Xero é um software de contabilidade online fácil de utilizar e especificamente concebido para as pequenas empresas. Crie visualizações apelativas com base nos dados financeiros do Xero com esta aplicação de modelo do Power BI. O dashboard predefinido inclui muitas métricas para pequenas empresas, como fundo de maneio, receita versus despesa, tendência de perda de lucro, dias de vencimento e retorno sobre o investimento.

Ligue-se à [aplicação de modelo Xero](https://app.powerbi.com/getdata/services/xero) para Power BI ou saiba mais sobre a integração do [Xero e Power BI](https://help.xero.com/Power-BI).

## <a name="how-to-connect"></a>Como se ligar

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. Selecione **Xero** \> **Obter agora**.
4. Em **Instalar esta aplicação do Power BI?** , selecione **Instalar**.

    ![Instalar o Xero](media/service-connect-to-xero/power-bi-install-xero.png)

4. No painel **Aplicações**, selecione o mosaico **Xero**.

   ![Selecionar o mosaico Xero](media/service-connect-to-xero/power-bi-start-xero.png)

6. Em **Comece já com a sua nova aplicação** , selecione **Ligar**.

    ![Comece já com a sua nova aplicação](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. Introduza uma alcunha para a organização associada à sua conta do Xero. Qualquer uma serve, trata-se de uma forma de ajudar os utilizadores com múltiplas organizações Xero a saber onde estão. Veja mais detalhes sobre como [localizar parâmetros](#FindingParams) posteriormente neste artigo.

    ![Alcunha da organização](media/service-connect-to-xero/params.png)

5. Como **Método de Autenticação**, selecione **OAuth**. Quando lhe for pedido, inicie sessão na conta do Xero e selecione a organização à qual se quer ligar. Quando o início de sessão for concluído, selecione **Iniciar sessão** para iniciar o processo de carregamento.
   
    ![Método de autenticação](media/service-connect-to-xero/creds.png)
   
    ![Welcome to Xero](media/service-connect-to-xero/creds2.png)
6. Após a aprovação, o processo de importação será iniciado automaticamente. Quando concluído, um novo dashboard, relatório e modelo aparecerão no painel de navegação. Selecione o dashboard para ver os seus dados importados.
   
     ![Dashboard Xero](media/service-connect-to-xero/power-bi-xero-dashboard.png)

**O que se segue?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](../consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](../create-reports/service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](../consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento das atualizações ou tentar atualizá-lo a pedido através da opção **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
O dashboard da aplicação de modelo inclui mosaicos e métricas que abrangem uma variedade de áreas, com relatórios correspondentes para saber mais:  

| Área | Mosaicos de Dashboard | Relatório |
| --- | --- | --- |
| Dinheiro |Fluxo de caixa diário <br>Entrada de caixa <br>Saída de caixa <br>Saldo de encerramento por conta <br>Saldo de encerramento de hoje |Contas Bancárias |
| Cliente |Vendas faturadas <br>Vendas faturadas por cliente <br>Tendência de crescimento de vendas faturadas <br>Faturas por liquidar <br>Montantes por receber pendentes <br>Montantes por receber em atraso |Cliente <br>Inventário |
| Fornecedor |Compras faturadas <br>Compras faturadas por fornecedor <br>Tendência de crescimento de compras faturadas <br> Faturas em dívida <br>Montantes a pagar pendentes <br>Montantes a pagar em atraso |Fornecedores <br>Inventário |
| Inventário |Montante de vendas mensais por produto |Inventário |
| Lucro e perda |Lucro e perda mensal <br>Lucro líquido no ano fiscal atual <br>Lucro líquido no mês atual <br>Principais contas de despesas |Lucro e perda |
| Balanço |Ativos totais <br>Passivo total <br>Capital |Balanço |
| Estado de Funcionamento |Rácio atual <br>Percentagem de lucro bruto <br> Retorno total sobre ativos <br>Rácio de passivo total para capital |Solidez <br>Glossário e Notas Técnicas |

Este conjunto de dados inclui também as seguintes tabelas para personalizar os seus relatórios e dashboards:  

* Endereços  
* Alertas  
* Saldo Diário de Extrato Bancário  
* Extratos Bancários  
* Contactos  
* Pedidos de Reembolso por Despesas  
* Itens de Linha de Faturas  
* Faturas  
* Itens  
* Fim do Mês  
* Organização  
* Balancete  
* Contas Xero

## <a name="system-requirements"></a>Requisitos de sistema
As seguintes funções são necessárias para ter acesso à aplicação de modelo Xero: "Padrão + Relatórios" ou "Assistente".

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Parâmetros de localização
Indique o nome da sua organização para a controlar no Power BI. Um nome específico permite-lhe ligar-se a múltiplas organizações diferentes. Não se pode ligar à mesma organização várias vezes, pois irá interferir com a atualização agendada.   

## <a name="troubleshooting"></a>Resolução de problemas
* Os utilizadores Xero têm de ter as seguintes funções para acederem à aplicação de modelo Xero para Power BI: "Padrão + Relatórios" ou "Assistente". A aplicação de modelo serve-se de permissões baseadas em utilizadores para aceder aos dados de relatórios através do Power BI.
* Durante o carregamento, os mosaicos no dashboard permanecem num estado genérico de carregamento. Permanecem assim até o carregamento ser totalmente concluído. Se receber uma notificação a indicar que o seu carregamento foi concluído, mas os mosaicos continuam a carregar, experimente atualizar os mosaicos do dashboard através das reticências no canto superior direito do dashboard.
* Se a aplicação de modelo não for atualizada, verifique se se ligou mais do que uma vez à mesma organização no Power BI. O Xero só permite uma única ligação ativa a uma organização, pelo que se se ligar mais de uma vez à mesma organização, poderá ver um erro a indicar que as credenciais são inválidas.  
* Se tiver problemas na ligação da aplicação de modelo Xero para Power BI, como mensagens de erro ou tempos de carregamento lentos, comece por limpar a cache e os cookies ou reiniciar o browser e, em seguida, ligue-se novamente ao Power BI.  

Para outros problemas, envie um pedido em https://support.powerbi.com se o problema persistir.

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](../fundamentals/service-get-started.md)

[Obter dados no Power BI](service-get-data.md)
