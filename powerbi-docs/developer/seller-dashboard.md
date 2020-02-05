---
title: Submeter um elemento visual do Power BI no AppSource com o Dashboard de Vendedor
description: Submeter um elemento visual do Power BI no AppSource com o Dashboard de Vendedor
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 12/03/2019
ms.openlocfilehash: 73a6a3d16ae2515af41a3232a37579e18876f38b
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/04/2020
ms.locfileid: "75223670"
---
# <a name="submit-a-power-bi-visual-to-appsource-using-seller-dashboard"></a>Submeter um elemento visual do Power BI no AppSource com o Dashboard de Vendedor

Tem de enviar um e-mail com o ficheiro **.pbiviz** e o ficheiro **.pbix** à equipa do Power BI antes de efetuar a submissão no AppSource. Este passo permite que a equipa do Power BI carregue os ficheiros para o servidor de partilha público. Caso contrário, a loja não conseguirá obter os ficheiros. Tem de enviar os ficheiros com novas submissões de elementos visuais do Power BI, atualizações aos elementos visuais do Power BI existentes e correções às submissões rejeitadas.

>[!NOTE]
>O [Dashboard de Vendedor](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) está a ser retirado. Está a ser substituído pelo [Centro de Parceiros](https://docs.microsoft.com/partner-center/). Só deverá utilizar o Dashboard de Vendedor se estiver a meio da submissão de um elemento visual do Power BI. Se estiver a submeter um novo elemento visual do Power BI no AppSource, utilize o [método do Centro de Parceiros](office-store.md#submitting-to-appsource).

### <a name="seller-dashboard-submission-process"></a>Processo de submissão do Dashboard de Vendedor

Tem de ter uma conta de programador do Office válida para iniciar sessão no [Centro de Programadores do Office](https://dev.office.com/). Uma conta de programador do Office tem de ser uma Conta Live ID da Microsoft, por exemplo, hotmail.com ou outlook.com.

1. Navegue até ao [centro de programadores](https://sellerdashboard.microsoft.com/Application/Summary).

2. Selecione **Adicionar uma nova aplicação**.

    ![Adicionar uma aplicação](media/office-store/powerbi-custom-visual-add-an-app.png)

3. Selecione **Visual personalizado do Power BI** e depois selecione **Seguinte**.

4. Selecione o símbolo **+** em **Pacote de aplicação** e, em seguida, selecione o ficheiro XML do pacote de aplicação que recebeu da equipa do Power BI na caixa de diálogo para abrir o ficheiro.

    ![Pacote de aplicações](media/office-store/powerbi-custom-visual-apppackage.png)

5. Deverá receber uma aprovação de que se trata de um pacote de aplicação válido do Power BI.

    ![Manifesto aprovado](media/office-store/powerbi-custom-visual-manifest-approved.png)

6. Preencha os detalhes de **Informações Gerais**.

   * *Título da submissão:* o nome a utilizar para a submissão no centro de programadores.
   * *Versão:* O número da versão é povoado automaticamente com base no pacote de aplicação do suplemento.
   * *Data de Lançamento (UTC):* selecione uma data para a aplicação ser lançada na loja. Se for escolhida uma data no futuro, a aplicação só estará disponível na Loja a partir dessa data.
   * *Categoria:* A primeira categoria será povoada automaticamente como "Visualização de Dados + BI". Esta é a forma como todos os elementos visuais do Power BI são etiquetados. Para facilitar a pesquisa do elemento visual por parte dos utilizadores, pode indicar até duas categorias adicionais.
   * *Notas de teste:* é opcional, no caso de querer fornecer algumas instruções aos técnicos de testes da Microsoft.
   * *A minha aplicação chama, suporta, contém ou utiliza criptografia ou encriptação:* deixe desmarcado.
   * *Disponibilizar este suplemento no catálogo de suplementos do Office no iPad:* deixe desmarcado.
7. Carregue o logótipo do elemento visual selecionando o símbolo **+** em **Logótipo da aplicação**. Em seguida, selecione o ficheiro de ícone na caixa de diálogo para abrir o ficheiro. O ficheiro tem de ter o formato .png, .jpg, .jpeg ou .gif. Tem de ter exatamente 300 x 300 px (largura x altura) e o tamanho não pode ser superior a 512 KB.

    ![Logótipo da aplicação](media/office-store/powerbi-custom-visual-app-logo.png)

8. Preencha os detalhes de **Documentos de suporte**.

   * Ligação para documento sobre suporte
   * Ligação para documento sobre privacidade
   * Ligação para vídeo
   * Contrato de Licença do Utilizador Final (EULA)

       Tem de carregar um ficheiro EULA. Pode ser o seu próprio EULA ou pode utilizar o EULA predefinido existente na Loja Office para os elementos visuais do Power BI. Para utilizar o EULA predefinido, cole o seguinte URL na caixa de diálogo de carregamento do ficheiro "Contrato de Licença do Utilizador Final" do dashboard de vendedor: [https://visuals.azureedge.net/app-store/Power BI - Default Custom Visual EULA.pdf](https://visuals.azureedge.net/app-store/Power%20BI%20-%20Default%20Custom%20Visual%20EULA.pdf).

9. Selecione **Seguinte** para avançar para a página **Detalhes**.

10. Selecione **Idioma** e escolha um idioma na lista.

    ![Idioma](media/office-store/powerbi-custom-visual-language.png)

11. Preencha os detalhes de "Descrição".

    * *Nome da aplicação (para este idioma):* Introduza o título da aplicação conforme deverá aparecer na loja.
    * *Descrição breve:* Introduza uma breve descrição da aplicação, até 100 carateres, conforme deverá aparecer na loja. Esta descrição será apresentada nas páginas de nível superior juntamente com o logótipo. Pode utilizar a descrição do pacote pbiviz.
    * *Descrição longa:* Forneça uma descrição mais detalhada da aplicação, que será apresentada aos clientes na página de detalhes da aplicação. Se quiser o contributo da comunidade para melhorar o elemento visual, disponibilizando-o em código fonte aberto, forneça a ligação para o repositório público, como o GitHub, aqui.

12. Carregue, pelo menos, uma captura de ecrã. Os formatos possíveis são .png, .jpg, .jpeg ou .gif. Tem de ter exatamente 1366 x 768 px (largura x altura). O tamanho do ficheiro não pode ser superior a 1024 KB. *Para promover uma maior utilização, adicione balões de texto para articular a proposta de valor das principais funcionalidades mostradas em cada captura de ecrã.*

12. Se quiser adicionar mais idiomas, selecione **Adicionar um idioma** e repita os passos 10 e 11. Ao adicionar mais idiomas, permite que os utilizadores vejam os detalhes do elemento visual personalizado nos seus idiomas. Os idiomas que não constarem da lista assumem como predefinição o primeiro idioma selecionado.

13. Quando tiver terminado de adicionar idiomas, selecione **Seguinte** para avançar para a página **Bloquear acesso**.

14. Se quiser impedir a utilização ou compra da sua aplicação por parte de clientes em países ou regiões específicos, marque a caixa e selecione-os na lista.

15. Selecione **Seguinte** para avançar para a página **Preços**.

16. Atualmente, só são suportados elementos visuais *gratuitos* e não são permitidas compras adicionais dentro do elemento visual (compra via aplicação). Selecione **Esta aplicação é gratuita**.

    > [!NOTE]
    > Se selecionar qualquer outra opção sem ser "gratuita" ou se tiver conteúdo com compra via aplicação inserido no elemento visual submetido, a submissão será rejeitada.

17. Agora, pode selecionar **Guardar como rascunho** e submeter mais tarde ou pode selecionar **Submeter para aprovação** para submeter o elemento visual personalizado na Microsoft Store.

## <a name="seller-dashboard-certification-submission-process"></a>Processo de submissão da certificação do Dashboard de Vendedor

Siga as instruções nesta secção para enviar um elemento visual do Power BI para certificação no Dashboard de Vendedor. Utilize este método se tiver submetido um elemento visual do Power BI anteriormente para o AppSource com o Dashboard de Vendedor.

1. Envie um e-mail para a equipa de suporte dos elementos visuais do Power BI (pbicvsupport@microsoft.com). No e-mail, inclua as seguintes informações:
    * Título: Pedido de Certificação de Elemento Visual
    * Forneça uma ligação para o repositório do GitHub em que está alojado o código-fonte legível por humanos
    * [Cumprir os requisitos](power-bi-custom-visuals-certified.md#certification-requirements)
    * Passar na análise de código

2. A equipa dos elementos visuais do Power BI da Microsoft vai enviar-lhe uma notificação a informar que o elemento visual do Power BI foi certificado e adicionado à [lista de elementos visuais do Power BI certificados](power-bi-custom-visuals-certified.md#certified-power-bi-visuals) ou que foi rejeitado. No segundo caso, será enviado um relatório dos problemas a corrigir. O programador é responsável por manter a comunicação aberta com a Microsoft e atualizar os seus elementos visuais certificados consoante necessário.

## <a name="tracking-submission-status-and-usage"></a>Controlar o estado da submissão e a utilização

Pode rever as [políticas de validação](https://dev.office.com/officestore/docs/validation-policies#13-power-bi-custom-visuals).

Após a submissão, poderá ver o estado da submissão no [dashboard da aplicação](https://sellerdashboard.microsoft.com/Application/Summary/).

## <a name="certify-your-visual"></a>Certificar o elemento visual

Uma vez criado o elemento visual, se assim o pretender, pode proceder à [certificação](../developer/power-bi-custom-visuals-certified.md) do elemento visual.

## <a name="next-steps"></a>Próximos passos

[Developing a Power BI custom visual](visuals/custom-visual-develop-tutorial.md) (Desenvolver um elemento visual personalizado do Power BI)  
[Visualizações no Power BI](../visuals/power-bi-report-visualizations.md)  
[Visualizações Personalizadas no Power BI](../developer/power-bi-custom-visuals.md)  
[Obter a certificação de um elemento visual do Power BI](../developer/power-bi-custom-visuals-certified.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
