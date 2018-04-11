---
title: Ligar-se ao Xero com o Power BI
description: Xero para Power BI
services: powerbi
documentationcenter: ''
author: SarinaJoan
manager: kfile
backup: maggiesMSFT
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: d9f61067f89fb031926428109ef5dac5bcfd6392
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="connect-to-xero-with-power-bi"></a>Ligar-se ao Xero com o Power BI
O Xero é um software de contabilidade online fácil de utilizar e especificamente concebido para as pequenas empresas. Crie visualizações apelativas com base nos seus dados financeiros do Xero através deste pacote de conteúdos do Power BI. O seu dashboard predefinido inclui muitas métricas para pequenas empresas, como fundo de maneio, receita versus despesa, tendência de perda de lucro, dias de vencimento e retorno sobre o investimento.

Ligue-se ao [Pacote de conteúdos do Xero](https://app.powerbi.com/getdata/services/xero) para o Power BI ou saiba mais sobre a integração do [Xero e Power BI](https://help.xero.com/Power-BI).

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-xero/getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-xero/services.png)
3. Selecione **Xero** \>  **Obter**.
   
   ![](media/service-connect-to-xero/connect.png)
4. Introduza uma alcunha para a organização associada à sua conta Xero. Qualquer uma serve. Trata-se de uma forma de ajudar os utilizadores com múltiplas organizações Xero a saber onde estão. Veja os detalhes [abaixo](#FindingParams).
   
   ![](media/service-connect-to-xero/params.png)
5. Em **Método de Autenticação**, selecione **OAuth**. Quando lhe for pedido, inicie sessão na sua conta Xero e selecione a organização à qual se pretende ligar. Quando o início de sessão for concluído, selecione **Iniciar sessão** para iniciar o processo de carregamento.
   
    ![](media/service-connect-to-xero/creds.png)
   
    ![](media/service-connect-to-xero/creds2.png)
6. Após a aprovação, o processo de importação será iniciado automaticamente. Quando concluído, um novo dashboard, relatório e modelo aparecerão no Painel de Navegação. Selecione o dashboard para ver os seus dados importados.
   
     ![](media/service-connect-to-xero/dashboard.png)

**O que se segue?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](power-bi-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento de atualização ou tentar atualizá-lo a pedido através de **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
O dashboard do pacote de conteúdos inclui mosaicos e métricas que abrangem uma variedade de áreas, com relatórios correspondentes para saber mais:  

| Área | Mosaicos de Dashboard | Relatório |
| --- | --- | --- |
| Dinheiro |Fluxo de caixa diário <br>Entrada de caixa <br>Saída de caixa <br>Saldo de encerramento por conta <br>Saldo de encerramento de hoje |Contas Bancárias |
| Cliente |Vendas faturadas <br>Vendas faturadas por cliente <br>Tendência de crescimento de vendas faturadas <br>Faturas por liquidar <br>Montantes por receber pendentes <br>Montantes por receber em atraso |Cliente <br>Inventário |
| Fornecedor |Compras faturadas <br>Compras faturadas por fornecedor <br>Tendência de crescimento de compras faturadas <br> Faturas em dívida <br>Montantes a pagar pendentes <br>Montantes a pagar em atraso |Fornecedores <br>Inventário |
| Inventário |Montante de vendas mensais por produto |Inventário |
| Lucro e perda |Lucro e perda mensal <br>Lucro líquido no ano fiscal atual <br>Lucro líquido no mês atual <br>Principais contas de despesas |Lucro e perda |
| Balanço |Ativos totais <br>Passivo total <br>Capital |Balanço |
| Solidez |Rácio atual <br>Percentagem de lucro bruto <br> Retorno total sobre ativos <br>Rácio de passivo total para capital |Solidez <br>Glossário e Notas Técnicas |

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
As seguintes funções são necessárias para ter acesso ao pacote de conteúdos Xero: "Padrão + Relatórios" ou "Consultor".

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Parâmetros de localização
Indique um nome da sua organização para a controlar no Power BI. Isto permite-lhe ligar-se a múltiplas organizações diferentes. Note que não pode ligar-se à mesma organização várias vezes, pois irá interferir com a atualização agendada.   

## <a name="troubleshooting"></a>Resolução de problemas
* Os utilizadores Xero requerem as seguintes funções para acederem ao pacote de conteúdos Xero para o Power BI: "Padrão + Relatórios" ou "Consultor". O pacote de conteúdos serve-se de permissões baseadas em utilizadores para aceder aos dados de relatórios através do Power BI.  
* Se receber uma mensagem de falha após algum tempo de carregamento, verifique quanto tempo demorou até que a mensagem de erro surgisse. Note que o token de acesso fornecido para o Xero só é válido durante 30 minutos, pelo que as contas com mais dados do que aqueles que podem ser carregados nesse tempo irão falhar. Estamos a trabalhar ativamente para resolver este problema.
* Durante o carregamento, os mosaicos no dashboard permanecerão num estado genérico de carregamento. Não é esperado que este estado mude até o carregamento ser completamente efetuado. Se receber uma notificação a indicar que o seu carregamento foi concluído, mas os mosaicos continuam a carregar, experimente atualizar os mosaicos do dashboard através das reticências no canto superior direito do dashboard.
* Se o seu pacote de conteúdos não for atualizado, verifique se se ligou mais do que uma vez à mesma organização no Power BI. O Xero só permite uma única ligação ativa a uma organização, e o utilizador poderá ver um erro a indicar que as suas credenciais são inválidas se se ligar mais do que uma vez à mesma organização.  
* Se tiver problemas na ligação ao pacote de conteúdos Xero para Power BI, como mensagens de erros ou temos de carregamento bastante lentos, comece por limpar a cache e os cookies ou reiniciar o browser e, em seguida, ligar-se novamente ao Power BI.  

Para outros problemas, envie um ticket para http://support.powerbi.com, caso o problema persista.

## <a name="next-steps"></a>Passos seguintes
[Introdução ao Power BI](service-get-started.md)

[Obter dados no Power BI](service-get-data.md)

