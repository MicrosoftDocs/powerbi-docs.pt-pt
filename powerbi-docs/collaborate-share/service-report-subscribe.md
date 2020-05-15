---
title: 'Subscrever relatórios e dashboards: para si e para os seus colegas'
description: Saiba como subscrever um instantâneo de uma página de relatórios, de um dashboard ou de um relatório paginado do Power BI para si e para outras pessoas.
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/10/2020
ms.author: maggies
LocalizationGroup: Common tasks
ms.openlocfilehash: 9ee04211c44fb342e4baf904bcfa73bab489a1ba
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83273644"
---
# <a name="subscribe-yourself-and-others-to-reports-and-dashboards-in-the-power-bi-service"></a>Subscrever relatórios e dashboards no serviço Power BI para si e para outras pessoas

Pode subscrever as páginas de relatórios, os dashboards e os relatórios paginados mais importantes para si e para os seus colegas. As subscrições de e-mail do Power BI permitem-lhe:

- Decidir a frequência com que quer receber os e-mails: diariamente, semanalmente, mensalmente, de hora a hora ou uma vez por dia depois da atualização de dados inicial.
- Escolher a hora a que quer receber o e-mail, se escolher de hora a hora, diariamente, semanalmente ou mensalmente.
- Configurar 24 subscrições diferentes por relatório ou dashboard do Power BI.  Não existe um limite para o número de subscrições que pode configurar para relatórios paginados.
- Pedir que lhe seja enviado um e-mail com uma imagem do relatório e uma ligação para o relatório no serviço.  Nos dispositivos móveis com aplicações do Power BI instaladas, a seleção desta ligação inicia a aplicação Power BI, em vez de abrir o relatório ou dashboard no site do Power BI.
- Inclui um anexo do relatório completo, se subscrever um relatório paginado.
- Enviar e-mails para utilizadores fora do seu inquilino, se o conteúdo do Power BI estiver alojado numa capacidade Premium.  Os administradores podem controlar o acesso a quem pode enviar subscrições de e-mail a utilizadores externos ao aproveitar as definições de controlo de partilha externa existentes no centro de administração do Power BI.

![instantâneo do dashboard num e-mail](media/service-report-subscribe/power-bi-dashboard-email-new.jpg) 

## <a name="requirements"></a>Requirements

Uma subscrição pode ser **criada** por:

- Utilizadores com uma licença do Power BI Pro 
- Os utilizadores que visualizam o conteúdo numa área de trabalho ou aplicação Premium também podem subscrever os conteúdos aí localizados, mesmo sem uma licença do Power BI Pro. 

Não precisa de permissões de edição para o conteúdo (dashboard ou relatório) para criar uma subscrição para si próprio, mas tem de ter permissões de edição para criar uma subscrição para outra pessoa.

## <a name="subscribe-to-a-dashboard-report-page-or-paginated-report"></a>Subscrever um dashboard, uma página de relatórios ou um relatório paginado

Quer esteja a subscrever um dashboard, um relatório ou um relatório paginado, o processo é semelhante. O mesmo botão permite-lhe subscrever os dashboards e os relatórios do serviço Power BI.

A subscrição de relatórios paginados é ligeiramente diferente. Veja [Subscrever um relatório paginado no serviço Power BI para si e para outras pessoas](../consumer/paginated-reports-subscriptions.md) para obter mais informações.
 
![selecionar o ícone Subscrever](media/service-report-subscribe/power-bi-subscribe-orientation.png).

1. Abra o dashboard ou o relatório.
2. Na barra de menus superior, selecione **Subscrever** ou selecione o ícone de envelope ![ícone Subscrever](media/service-report-subscribe/power-bi-icon-envelope.png).
   
    ![ícone Subscrever](media/service-report-subscribe/power-bi-subscribe-icon.png)

1. Utilize o controlo de deslize amarelo para ativar e desativar a subscrição. Definir o controlo de deslize para **Desativado** não elimina a subscrição. Para eliminar a subscrição, selecione o ícone de recipiente do lixo.

2. O seu e-mail já está na caixa **Subscrever**. Também pode adicionar outros endereços de e-mail no mesmo domínio à subscrição. Se o relatório ou dashboard estiver alojado na [capacidade Premium](https://docs.microsoft.com/power-bi/service-premium-what-is), poderá subscrever outros endereços de e-mail individuais e de aliases de grupo, estejam no seu domínio ou não. Se o relatório ou dashboard não estiver alojado numa capacidade Premium, poderá subscrever outras pessoas, mas estas também terão de ter licenças do Power BI Pro. Para obter detalhes, veja [Considerações e resolução de problemas](#considerations-and-troubleshooting) abaixo.

3. Preencha os detalhes **Assunto** e **Mensagem** do e-mail.

4. Selecione uma **Frequência** para a sua subscrição:  **Diariamente**, **Hora a Hora**, **Semanalmente**, **Mensalmente** ou **Depois da Atualização de Dados (Uma Vez por Dia)** . Para receber o e-mail de subscrição apenas em determinados dias, selecione **Hora a hora** ou **Semanalmente** e selecione os dias em que o pretende receber. Por exemplo, se quiser receber o e-mail de subscrição apenas durante os dias úteis, selecione **Semanalmente** e desselecione as caixas **Sáb** e **Dom**. Se selecionar **Mensalmente**, introduza os dias do mês nos quais quer receber o e-mail de subscrição.

5. Se escolher **Diariamente**, **Hora a Hora**, **Mensalmente** ou **Semanalmente**, também pode escolher uma **Hora Agendada** para a subscrição. Pode definir para que seja executada a cada hora ou a cada 15, 30 ou 45 minutos. Selecione manhã ou tarde/noite. Também pode especificar o fuso horário. Se escolher **Hora a Hora**, selecione a **Hora Agendada** para o início da subscrição e esta será executada a cada hora.

6. Por predefinição, a data de início da sua subscrição é a data em que a criou. Tem a opção de selecionar uma data de fim. Se não definir uma data de fim, esta será definida automaticamente para um ano após a data de início. Pode alterá-la para qualquer data no futuro (até ao ano 9999) em qualquer altura antes de a subscrição terminar. Quando uma subscrição atinge a data de fim, esta é interrompida até que a volte a ativar. Receberá notificações antes da data de fim agendada a perguntar se quer prolongar a subscrição.

    Nas capturas de ecrã abaixo, repare que, na realidade, está a subscrever uma _página_ de relatórios ao subscrever um relatório. Para subscrever mais do que uma página num relatório, selecione **Adicionar outra subscrição** e selecione uma página diferente.
     
    ![Painel Subscrever](media/service-report-subscribe/power-bi-subscribe-pane.png)  

1. (Opcional) Selecione se quer incluir uma ligação de regresso ao conteúdo no Power BI e se quer conceder aos utilizadores acesso aos conteúdos aos quais os subscreveu.  Se optar por incluir uma ligação, para a melhor experiência, certifique-se de que todos os utilizadores têm acesso ao relatório.
2. Selecione **Guardar e fechar**. Os utilizadores subscritos receberão um e-mail e um instantâneo do dashboard ou da página de relatório com a frequência e na hora que selecionou. Pode criar até 24 subscrições por relatório ou dashboard e pode indicar frequências, horas e destinatários exclusivos para cada subscrição. Todas as subscrições definidas para **Depois da Atualização de Dados** para o dashboard ou relatório só enviarão um e-mail após a primeira atualização agendada.

    > [!TIP]
    > Quer enviar o e-mail de uma subscrição diretamente ou a pedido a qualquer momento? Selecione **Executar Agora** para as subscrições do dashboard ou relatório que pretende enviar. Verá uma notificação a informar que será enviado um e-mail para todos os utilizadores dessa subscrição específica. Realizar esta ação não conta para o seu limite de 24 execuções de subscrições agendadas por dia e por relatório ou dashboard. Esta ação NÃO irá acionar uma atualização de dados no conjunto de dados subjacente.
    >

## <a name="manage-your-subscriptions"></a>Gerir as subscrições

A subscrição só pode ser gerida pela pessoa que a criou. Existem dois caminhos para gerir as suas subscrições. O primeiro é selecionar **Gerir todas as subscrições** na caixa de diálogo **Subscrever e-mails** (ver passo 4 acima). O segundo é selecionar o ícone de engrenagem do Power BI ![ícone de engrenagem](media/service-report-subscribe/power-bi-settings-icon.png) na barra de menus superior e selecionar **Definições**.

![selecionar Definições](media/service-report-subscribe/power-bi-subscribe-settings.png)

As subscrições apresentadas dependem da área de trabalho atualmente ativa. Para ver todas as subscrições de uma só vez para todas as áreas de trabalho, certifique-se de que a opção **A Minha Área de Trabalho** está ativa. Para ajudar a compreender as áreas de trabalho, veja [Áreas de Trabalho no Power BI](service-create-workspaces.md).

![ver todas as subscrições em A Minha Área de Trabalho](media/service-report-subscribe/power-bi-subscriptions.png)

Uma subscrição termina em qualquer um dos seguintes casos:

- Expiração da licença do Pro.
- O proprietário eliminou o dashboard ou o relatório.
- A conta de utilizador utilizada para criar a subscrição foi eliminada.

Os administradores do Power BI podem utilizar os registos de auditoria do Power BI para visualizar detalhes relativos às subscrições. Estes detalhes incluem:

- Criada Por
- Data de Criação
- Conteúdo Subscrito
- Destinatários
- Frequência
- Modificado Por/
- Data de Modificação

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas

### <a name="general"></a>Geral

- Em ocasiões raras, as subscrições de e-mail poderão demorar mais de 15 minutos a serem entregues aos destinatários. Se for o caso, recomendamos que execute a atualização de dados e a subscrição de e-mail separadamente para assegurar uma entrega atempada. Se o problema persistir, contacte o suporte do Power BI.
- Para evitar que os e-mails da subscrição vão para a pasta de spam, adicione o alias de e-mail do Power BI ([no-reply-powerbi@microsoft.com](mailto:no-reply-powerbi@microsoft.com)) aos contactos. Se estiver a utilizar o Microsoft Outlook, clique com o botão direito do rato no alias e selecione **Adicionar aos contactos do Outlook**.
- Atualmente, as subscrições por e-mail para relatórios e dashboards que utilizem conjuntos de dados com ligações em tempo real só são suportadas ao subscrever utilizadores que não o próprio, exceto para relatórios paginados. Pode subscrever outras pessoas num relatório paginado, com o seu contexto de segurança. Saiba mais sobre como [subscrever os relatórios paginados](../consumer/paginated-reports-subscriptions.md).
- O Power BI interrompe automaticamente a atualização nos conjuntos de dados associados a dashboards e relatórios que não tenham sido acedidos durante mais de dois meses. No entanto, se adicionar uma subscrição a um dashboard ou relatório, este não será interrompido, mesmo se não for acedido.
- Se não estiver a receber os e-mails de subscrição, certifique-se de que o Nome Principal de Utilizador (UPN) pode receber e-mails.
- Se o dashboard ou relatório estiver em capacidade Premium, pode utilizar aliases de e-mail de grupo para subscrições, em vez de subscrever colegas individualmente através dos endereços de e-mail. Os aliases são baseados no Active Directory atual.

### <a name="dashboards"></a>Dashboards

- É possível que os dashboards com mais de 25 mosaicos afixados ou mais de 4 páginas de relatórios dinâmicos afixadas não sejam apresentados por inteiro nos e-mails de subscrição enviados para os utilizadores. As subscrições de dashboards que ultrapassarem estes números de mosaicos não serão bloqueadas. No entanto, se tiver problemas, estas não terão suporte. Pondere modificá-las para ficar dentro de um intervalo suportado.
- Em ocasiões raras, as subscrições de e-mail poderão demorar mais de 15 minutos a serem entregues aos destinatários. Se for o caso, recomendamos que execute a atualização de dados e a subscrição de e-mail separadamente para assegurar uma entrega atempada. Se o problema persistir, contacte o suporte do Power BI.
- Para subscrições de e-mail do dashboard, se um mosaico tiver segurança ao nível da linha (RLS) aplicada, o mesmo não será apresentado.
- Para subscrições de dashboards, determinados tipos de mosaicos ainda não são suportados. Estes incluem: transmissão em fluxo de mosaicos, mosaicos de vídeos e mosaicos de conteúdo Web personalizados.
- Se partilhar um dashboard com um colega fora do seu inquilino, também não poderá criar uma subscrição para esse colega, *a não ser que* o dashboard esteja numa aplicação ou área de trabalho Premium. Por isso, se for aaron@contoso.com, poderá partilhar com anyone@fabrikam.com, mas ainda não poderá subscrever anyone@fabrikam.com e o mesmo não poderá subscrever o conteúdo partilhado.

### <a name="reports"></a>Relatórios

- Para subscrições de e-mail do relatório, se o conjunto de dados utilizar RLS, poderá criar uma subscrição para si próprio. Não pode subscrever outras pessoas num relatório com segurança ao nível da linha (RLS) aplicada, exceto em relatórios paginados. Pode subscrever outras pessoas num relatório paginado, com o seu contexto de segurança. Saiba mais sobre como [subscrever os relatórios paginados](../consumer/paginated-reports-subscriptions.md).
- As subscrições de páginas de relatório estão associadas ao nome da página de relatório. Se subscrever uma página de relatório e, em seguida, mudar o nome da mesma, terá de voltar a criar a sua subscrição.
- A sua organização pode configurar determinadas definições no Azure Active Directory que podem limitar a capacidade de utilizar as subscrições de e-mail no Power BI. Estas limitações incluem, mas não se limitam a, ter uma autenticação multifator ou restrições de intervalos de IP quando se acede a recursos.
- As subscrições de e-mail não suportam a maioria dos [elementos visuais personalizados](../developer/power-bi-custom-visuals.md). A única exceção são os elementos visuais personalizados que foram [certificados](../developer/power-bi-custom-visuals-certified.md).
- Neste momento, as subscrições de e-mail não suportam elementos visuais personalizados baseados em R.
- As subscrições por e-mail são enviadas com as estatísticas de filtro e segmentação de dados predefinidas do relatório. Quaisquer alterações às predefinições efetuadas depois da subscrição não irão aparecer no e-mail. Os Relatórios paginados suportam esta funcionalidade e permitem-lhe definir os valores de parâmetros específicos por subscrição.

## <a name="next-steps"></a>Próximos passos

- [Subscrever um relatório paginado no serviço Power BI para si e para outras pessoas](../consumer/paginated-reports-subscriptions.md)
- Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)    
- [Ler a mensagem de blogue](https://powerbi.microsoft.com/blog/introducing-dashboard-email-subscriptions-a-360-degree-view-of-your-business-in-your-inbox-every-day/)