---
title: Exportar e enviar um relatório por e-mail com o Power Automate
description: Neste artigo, vai usar o Power Automate para automatizar a exportação e a distribuição de relatórios do Power BI numa variedade de formatos e cenários com suporte.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/10/2020
LocalizationGroup: Get started
ms.openlocfilehash: 45bccbefc6e499375d33aa049ead8a6c6e47bc8c
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098832"
---
# <a name="export-and-email-a-power-bi-report-with-power-automate"></a>Exportar e enviar um relatório do Power BI por e-mail com o Power Automate

Com o [Power Automate](/power-automate/getting-started), pode automatizar a exportação e a distribuição de relatórios do Power BI para vários cenários e formatos. Neste artigo, vai criar de raiz o seu próprio fluxo. Use a ação Exportar para Ficheiro para Relatórios do Power BI para distribuir automaticamente um relatório do Power BI por e-mail.

:::image type="content" source="media/service-automate-power-bi-report-export/automate-power-bi-report-overview.png" alt-text="Passos no Power Automate para exportar e enviar um relatório por e-mail.":::

## <a name="prerequisites"></a>Pré-requisitos  

Para acompanhar, confirme que tem:

- Pelo menos, uma área de trabalho no inquilino do Power BI apoiado por uma capacidade reservada. Esta capacidade pode ser qualquer uma das SKUs A1/EM1 – A6/P3. Leia mais sobre as [capacidades reservadas no Power BI Premium](../admin/service-premium-what-is.md).
- Acesso aos conectores padrão no Power Automate, incluído em qualquer subscrição do Office 365.

## <a name="create-a-flow-from-scratch"></a>Criar um fluxo a partir do zero 

Nesta tarefa, vai criar de raiz um fluxo simples. O fluxo exporta um relatório do Power BI como um PDF e anexa-o a um e-mail a ser enviado semanalmente.  

1. Inicie sessão no Power Automate (flow.microsoft.com).
2. Selecione **Criar** > **Fluxo agendado**. 

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-scheduled-flow-2.png" alt-text="Criar um fluxo agendado no Power Automate.":::

3. Em **Criar um fluxo agendado**, atribua um nome ao fluxo. 
4. Em **Executar este fluxo**, selecione a data e a hora de início para o fluxo, bem como a frequência de repetição.
5. Em **Nestes dias**, selecione os dias em que quer que o fluxo seja executado e selecione **Criar**.

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-build-flow-5.png" alt-text="Power Automate, agendar o fluxo.":::

6. Em **Recorrência**, selecione **Mostrar opções avançadas** e introduza um valor em **Nestas horas** e **Nestes minutos** para definir uma hora específica para a execução do fluxo.
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-recurrence-6.png" alt-text="Defina a recorrência no Power Automate.":::

7. Selecione **Novo Passo**.
8. Em **Escolher uma ação**, procure **Power BI** e selecione **Exportar para o Ficheiro para Relatórios do Power BI**.
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-choose-action-8.png" alt-text="Escolher uma ação no Power Automate.":::

9. No **Exportar para o Ficheiro para Relatórios do Power BI**, selecione uma **Área de Trabalho** e **Relatório** nos menus pendentes.
10. Selecione o **Formato de Exportação** pretendido para o seu relatório do Power BI.
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-export-file-10.png" alt-text="Selecione o formato de exportação no Power Automate.":::

11. Opcionalmente, indique páginas específicas para exportar no campo **Páginas PageName-1**. Observe que o parâmetro de nome de página é diferente do nome da página de apresentação. Localize o nome da página ao navegar até à página no serviço do Power BI e copiar a última parte do URL.
 
     :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-copy-url-11.png" alt-text="Selecione o nome do painel no U R L.":::

12. Opcionalmente, indique um marcador específico a ser apresentado no campo **Nome do Marcador de Páginas**. Assim como com o parâmetro de nome da página, pode encontrar o parâmetro de nome do marcador no URL do relatório. Pode especificar parâmetros adicionais para o relatório do Power BI. Encontre descrições detalhadas destes parâmetros na [referência do conector da API REST do Power BI](/connectors/powerbi/#export-to-file-for-power-bi-reports).

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-bookmark-url-12.png" alt-text="Selecione o nome do marcador no U R L.":::

13. Selecione **Novo Passo**.
14. Em **Escolher uma ação**, procure **Outlook** e selecione **Enviar um email (V2)** .
15. Em **Enviar um email (V2)** , preencha os campos **Para**, **Assunto** e **Corpo** do seu e-mail.
16. Selecione **Mostrar opções avançadas**. Em **Nome dos Anexos – 1**, introduza um nome para o anexo. Adicione uma extensão de ficheiro ao nome do ficheiro (por exemplo, .PDF) que corresponda ao seu **Formato de Exportação** desejado.
17. Em **Conteúdo do Anexo**, selecione **Conteúdo do Ficheiro** para anexar o seu relatório do Power BI exportado.  
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-send-email-17.png" alt-text="Selecione o relatório exportado para enviar um e-mail.":::

18. Quando tiver terminado, selecione **Passo seguinte** ou **Guardar**. O Power Automate cria e avalia o fluxo e informa-o se encontrar erros.
1. Se existirem erros, selecione **Editar fluxo**  para os corrigir. Caso contrário, selecione a seta **Para trás** para ver os detalhes do fluxo e executar o novo fluxo.
    Quando executa o fluxo, o Power Automate exporta um relatório do Power BI no formato especificado e envia-o como um anexo de e-mail conforme agendado.  

## <a name="next-steps"></a>Passos seguintes

- [Integrar alertas de dados do Power BI no Power Automate](service-flow-integration.md)
- [Introdução ao Power Automate](/power-automate/getting-started/)
- Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
