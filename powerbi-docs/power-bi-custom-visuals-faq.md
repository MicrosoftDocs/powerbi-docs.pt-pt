---
title: Perguntas frequentes sobre os elementos visuais personalizados do Power BI
description: Navegue numa lista de perguntas frequentes e respostas sobre os elementos visuais personalizados do Power BI
author: sranins
ms.author: rasala
manager: kfile
ms.reviewer: maghan
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.custom: ''
ms.date: 12/17/2018
ms.openlocfilehash: 9c5d2665f012881f951a186c3ec8c9fd94031a28
ms.sourcegitcommit: ac63b08a4085de35e1968fa90f2f49ea001b50c5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/18/2019
ms.locfileid: "57980364"
---
# <a name="frequently-asked-questions-about-power-bi-custom-visuals"></a>Perguntas frequentes sobre os elementos visuais personalizados do Power BI

## <a name="organizational-custom-visuals"></a>Elementos visuais personalizados organizacionais

### <a name="how-can-the-admin-manage-the-organizational-custom-visuals"></a>Como é que o administrador pode gerir os elementos visuais personalizados organizacionais?

No portal de administração, no separador "Elementos visuais personalizados organizacionais", o administrador pode ver e [gerir todos os elementos visuais personalizados organizacionais da empresa](service-admin-portal.md#organizational-visuals): adicionar, desativar, ativar e eliminar.
Nunca mais terá de partilhar esses elementos visuais através de e-mails ou pastas partilhadas! Depois de implementados no repositório organizacional, os utilizadores na organização poderão facilmente localizá-los e importar os elementos visuais personalizados organizacionais para os respetivos relatórios diretamente a partir do Power BI Desktop ou do Serviço Power BI. Os elementos visuais personalizados organizacionais encontram-se na loja integrada (no Power BI Desktop ou no serviço Power BI) no separador *A MINHA ORGANIZAÇÃO*. Quando o administrador carrega uma nova versão de um elemento visual personalizado organizacional, todas as pessoas na organização recebem a mesma versão atualizada. Os autores do relatório não precisam de eliminar o elemento visual nos respetivos relatórios para obter a nova versão dos mesmos, pois todos os relatórios que utilizarem esses elementos visuais serão atualizados automaticamente! O mecanismo de atualização é semelhante ao dos elementos visuais do marketplace.

### <a name="if-an-admin-uploads-a-custom-visual-from-the-public-marketplace-to-the-organization-store-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>Se um administrador carregar um elemento visual personalizado do marketplace público para a loja da organização, este será automaticamente atualizado assim que o fornecedor atualizar o elemento visual no marketplace público?

Não, não existem atualizações automáticas no marketplace público.
O Administrador é responsável por atualizar a versão dos elementos visuais personalizados organizacionais.

### <a name="is-there-a-way-to-disable-the-organizational-store"></a>Há alguma forma de desativar a loja organizacional?

Não, os utilizadores veem sempre o separador “A MINHA ORGANIZAÇÃO” no Power BI Desktop e no serviço. O administrador pode desativar ou eliminar todos os elementos visuais personalizados organizacionais no portal de administração e a loja organizacional fica vazia.
  
### <a name="if-the-administrator-disables-custom-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-custom-visuals"></a>Se o administrador desativar os elementos visuais personalizados no Portal de administração (Definições de inquilino), os utilizadores ainda terão acesso aos elementos visuais personalizados organizacionais?

Sim, se o administrador desativar os elementos visuais personalizados no portal de administração, a loja organizacional não será afetada. Algumas organizações desativam os elementos visuais personalizados e ativam apenas os elementos visuais selecionados manualmente que foram importados e carregados pelo administrador do Power BI para a loja organizacional. No Power BI Desktop, não é imposta a desativação dos elementos visuais personalizados no Portal de administração. Os utilizadores do Power BI Desktop continuam a poder adicionar e utilizar os elementos visuais personalizados do marketplace público nos respetivos relatórios. No entanto, esses elementos visuais personalizados públicos deixam de ser compostos assim que são publicados no Serviço Power BI e emitem um erro apropriado. Quando utilizar o serviço Power BI, não poderá importar elementos visuais personalizados do marketplace público. Pode importar apenas os elementos visuais da loja organizacional porque a definição dos elementos visuais personalizados no portal de administração é imposta no serviço Power BI.

### <a name="why-does-the-organizational-store-and-organizational-custom-visuals-make-a-great-enterprise-solution"></a>Porque é que a loja organizacional e os elementos visuais personalizados organizacionais são uma ótima solução empresarial?

* Todos recebem a mesma versão do elemento visual, que é controlada pelo administrador do Power BI. Assim que o administrador atualiza a versão do elemento visual no portal de administração, todos os utilizadores da organização recebem automaticamente a versão atualizada.

* Nunca mais terá de partilhar ficheiros de elementos visuais por e-mail ou pastas partilhadas! Um único local, visíveis para todos os membros com sessão iniciada.

* Segurança e compatibilidade: as novas versões dos elementos visuais personalizados organizacionais são atualizadas automaticamente em todos os relatórios, à semelhança dos elementos visuais do marketplace.

* Os utilizadores da organização que utilizam os elementos visuais personalizados organizacionais têm de ter sessão iniciada para ver e utilizar esses elementos visuais, que representam um elemento de segurança para a organização.

* Os administradores podem controlar quais são os elementos visuais personalizados disponíveis na organização.

* Os administradores podem ativar/desativar os elementos visuais para fins de teste no portal de administração. Esse procedimento resulta numa melhor imposição da segurança, uma vez que esses elementos visuais apenas serão disponibilizados aos membros da organização.

## <a name="certified-custom-visuals"></a>Elementos visuais personalizados certificados

### <a name="what-are-certified-custom-visuals"></a>O que são os elementos visuais personalizados certificados?

São elementos visuais do [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) que cumprem determinados testes e requisitos de código [especificados](power-bi-custom-visuals-certified.md) pela equipa do Power BI.  Os testes realizados são concebidos para verificar que o elemento visual não acede a serviços ou recursos externos. Contudo, a Microsoft não é responsável pela criação dos elementos visuais personalizados de terceiros e recomenda que os clientes entrem diretamente em contacto com o criador para verificar a funcionalidade desses elementos visuais.

### <a name="what-tests-are-done-during-the-certification-process"></a>Que testes são realizados durante o processo de certificação?

Os testes do processo de certificação incluem, mas não estão limitados a: Análises de código, análises de código estático, fugas de dados, fuzzing de dados, testes de penetração, testes de acesso XSS, injeção de dados maliciosos, testes funcionais e validação de entrada.
 
### <a name="do-you-certify-visuals-every-submission"></a>Todas as submissões de elementos visuais são certificadas?

Yes. Sempre que a nova versão de um elemento visual certificado é submetida para o Marketplace, a atualização da versão do elemento visual passa pelas mesmas verificações de certificação.

Nota para os programadores: se estiver a submeter a atualização de versão de um elemento visual certificado, não precisa de enviar um e-mail separado como [primeiro pedido de certificação](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified#process-for-submitting-a-custom-visual-for-certification). A certificação de atualizações de versões é efetuada automaticamente. Para todas as violações que causem uma rejeição, é enviado um e-mail a explicar o que precisa de ser corrigido. 

### <a name="is-it-possible-that-a-certified-visual-stops-being-certified-with-a-new-update"></a>É possível que um elemento visual certificado deixe de o ser após uma nova atualização?

Não, isto não é possível. Um elemento visual não pode perder a certificação após uma nova atualização. No entanto, a atualização é rejeitada.
 
### <a name="do-i-need-to-share-my-code-in-public-repository-if-i-am-submitting-to-the-certification-process"></a>Preciso de partilhar o meu código no repositório público se estiver a efetuar uma submissão para o processo de certificação?

Não precisa de partilhar o seu código para o público. No entanto, precisa de nos conceder permissões de leitura para verificar o código dos elementos visuais. Por exemplo: um repositório privado no GitHub.
 
### <a name="do-we-have-to-publishhttpsdocsmicrosoftcompower-bideveloperoffice-store-the-visual-in-the-marketplacehttpsappsourcemicrosoftcommarketplaceappspage1productpower-bi-visuals-to-certify-it"></a>É necessário [publicar](https://docs.microsoft.com/power-bi/developer/office-store) o elemento visual no [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) para o certificar?

Yes. Publicar o elemento visual primeiro no Marketplace é um requisito de certificação obrigatório.
Para certificar um elemento visual personalizado, o mesmo tem de estar nos nossos servidores. Não podemos certificar elementos visuais privados.
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>A certificação do meu elemento visual demora quanto tempo?

Uma versão atualizada pode demorar até duas semanas. Uma nova submissão (primeira certificação) pode demorar até três semanas. 

### <a name="does-the-certification-process-ensure-that-no-data-leakage-occurs"></a>O processo de Certificação garante que não ocorrem fugas de dados?

Os testes realizados são concebidos para verificar que o elemento visual não acede a serviços ou recursos externos. Contudo, a Microsoft não é responsável pela criação dos elementos visuais personalizados de terceiros e recomenda que os clientes entrem diretamente em contacto com o criador para verificar a funcionalidade desses elementos visuais.
 
### <a name="are-uncertified-custom-visuals-safe-to-use"></a>É seguro utilizar elementos visuais personalizados não certificados?

Os elementos visuais personalizados não certificados não são necessariamente inseguros.
Alguns elementos visuais não estão certificados porque não cumprem um ou mais [requisitos de certificação](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Um exemplo disto é a ligação a um serviço externo, como elementos visuais de mapa, ou elementos visuais que utilizam bibliotecas comerciais.
 
## <a name="visuals-with-additional-purchases"></a>Elementos visuais com possibilidade de compras adicionais

### <a name="what-is-a-visual-with-additional-purchases"></a>O que é um elemento visual com possibilidade de compras adicionais?

Um elemento visual com possibilidade de compras adicionais é semelhante aos suplementos com compras via aplicação (IAP) no marketplace. Estes suplementos têm uma etiqueta **Pode ser necessária uma compra adicional**.

Os utilizadores podem transferir e utilizar gratuitamente estes elementos visuais personalizados de IAP a partir do marketplace. Os elementos visuais de IAP disponibilizam compras via aplicação adicionais opcionais para obter funcionalidades avançadas.  

### <a name="whats-the-benefit-to-developers"></a>Quais são as vantagens para programadores?

Os elementos visuais personalizados de IAP no AppSource serão detetáveis para vários visitantes diários, o que gera tráfego útil e proporciona um maior reconhecimento dos seus elementos visuais personalizados de IAP e do seu papel como programador.

Se até recentemente geria esses elementos visuais através do seu site, agora pode submetê-los para o AppSource. Isto irá aumentar o nível de deteção e visibilidade dos elementos visuais de IAP na comunidade do Power BI.

Os elementos visuais no AppSource tiram partido de um canal de feedback Direto dos seus clientes que utilizam os elementos visuais personalizados de IAP, através de um sistema de críticas e classificações na loja.  

Assim que um elemento visual de IAP for aprovado pela equipa de validação do AppSource, também poderá submetê-lo para certificação. Este é um processo opcional.  

Quando um elemento visual personalizado de IAP for certificado, poderá ser exportado para o PowerPoint e apresentado nos e-mails recebidos quando um utilizador subscrever páginas de relatórios. Agora, ao submeter elementos visuais personalizados de IAP para o marketplace, os mesmos também poderão ser certificados e suportar um conjunto adicional de funcionalidades.  

### <a name="do-iap-visuals-need-to-be-certified"></a>Os elementos visuais de IAP precisam de ser certificados?

O processo de certificação é opcional. O programador é que decide se quer certificar os respetivos elementos visuais personalizados de IAP ou os elementos visuais gratuitos.

### <a name="what-is-changing-in-the-submission-process"></a>O que será alterado no processo de submissão?

O processo de submissão de elementos visuais personalizados de IAP e de elementos visuais gratuitos para o marketplace é o mesmo. Pode ser feito através do Dashboard de Vendedor.  A única alteração ao processo de submissão é que os programadores têm de indicar nas notas de programador no Dashboard de Vendedor o seguinte: "Elemento visual com compra na aplicação". Caso seja necessário, também terá de fornecer uma chave de licença/token para validar as funcionalidades pagas/avançadas.  

Não estará disponível nenhuma opção nova no Dashboard de Vendedor: *gratuito com compras via aplicação*. Terá de submeter os seus elementos visuais de IAP como *gratuitos*.

Além disso, forneça uma descrição longa na loja para os seus utilizadores saberem quais as funcionalidades gratuitas e as funcionalidades que necessitam de compras adicionais.  

### <a name="what-should-i-do-beforesubmittingmy-iap-custom-visual"></a>O que devo fazer antes de submeter o meu elemento visual personalizado de IAP?

Se estiver a trabalhar num elemento visual personalizado de IAP ou já tiver criado um, certifique-se de que cumpre as diretrizes.  

Se tiver um logótipo no elemento visual, certifique-se de que cumpre as diretrizes de logótipo (cor, localização, tamanho e acionador de ação).

Também encontrará notas de melhores práticas nas diretrizes.  
> [!Note]
> Todos os elementos visuais gratuitos deverão manter as mesmas funcionalidades gratuitas oferecidas anteriormente. Opcionalmente, pode adicionar funcionalidades avançadas pagas para além das antigas funcionalidades gratuitas. Recomendamos que submeta os elementos visuais de IAP com as funcionalidades avançadas como novos elementos visuais e que não atualize as antigas funcionalidades gratuitas.

### <a name="can-i-get-my-iap-custom-visual-certified"></a>Posso certificar o meu elemento visual personalizado de IAP?

Sim. O processo de certificação é o mesmo para elementos visuais gratuitos.  Quando o seu elemento visual personalizado de IAP for aprovado pela equipa do AppSource, poderá submetê-lo para o processo de certificação.

Para certificar o seu elemento visual, o mesmo deverá cumprir os requisitos de certificação. Por exemplo, o elemento visual não pode aceder a serviços externos para a validação de licenças.

O pedido de certificação é um processo opcional. É você que decide se quer certificar um elemento visual de IAP.

## <a name="additional-questions"></a>Perguntas adicionais

### <a name="how-to-get-support"></a>Como posso obter suporte?

Não hesite em enviar perguntas, comentários ou comunicar problemas à equipa de suporte de elementos visuais personalizados para o endereço:  *pbicvsupport@microsoft.com* .  

## <a name="next-steps"></a>Próximos passos

Para obter mais informações, visite [Resolver problemas com os seus elementos visuais personalizados do Power BI](power-bi-custom-visuals-troubleshoot.md).
