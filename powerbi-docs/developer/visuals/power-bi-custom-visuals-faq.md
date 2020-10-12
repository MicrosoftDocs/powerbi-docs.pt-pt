---
title: Perguntas frequentes sobre os elementos visuais do Power BI
description: Consulte uma lista de perguntas frequentes e respostas sobre elementos visuais do Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.custom: ''
ms.date: 09/30/2020
ms.openlocfilehash: 10790ef963a11fd78c41a28b54e7d177bd96a157
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/06/2020
ms.locfileid: "91747925"
---
# <a name="power-bi-visuals-faq"></a>FAQ sobre elementos visuais do Power BI

## <a name="organizational-power-bi-visuals"></a>Elementos visuais organizacionais do Power BI

O portal de administração permite gerir os elementos visuais do Power BI da sua organização.

### <a name="how-can-the-admin-manage-organizational-power-bi-visuals"></a>Como é que o administrador pode gerir os elementos visuais organizacionais do Power BI?

No Portal de administração, no separador *Elementos visuais organizacionais*, o administrador pode ver e [gerir todos os elementos visuais organizacionais do Power BI da empresa](../../admin/organizational-visuals.md#organizational-visuals), incluindo adicionar, desativar, ativar e eliminar elementos visuais do Power BI.

Os utilizadores na organização podem facilmente encontrar elementos visuais do Power BI e importá-los para os relatórios diretamente do Power BI Desktop ou do Serviço Power BI.

Quando o administrador carrega uma nova versão de um elemento visual organizacional do Power BI, todas as pessoas na organização recebem a mesma versão atualizada. Todos os relatórios que utilizam elementos visuais atualizados do Power BI são atualizados automaticamente.

Os utilizadores podem encontrar os elementos visuais organizacionais do Power BI no arquivo da organização incorporado do Power BI Desktop e do serviço Power BI, no separador *A MINHA ORGANIZAÇÃO*. 

### <a name="if-an-admin-uploads-a-power-bi-visual-from-the-public-marketplace-to-the-organization-store-using-add-visual--from-appsource-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>Se um administrador carregar um elemento visual do Power BI do marketplace público para o arquivo da organização com *Adicionar elemento visual > do AppSource*, este será automaticamente atualizado assim que o fornecedor atualizar o elemento visual no marketplace público?

Sim, o elemento visual é automaticamente atualizado no marketplace público. Se o elemento visual for certificado, a certificação será retida, incluindo as funcionalidades adicionais como Exportar para PDF ou para PowerPoint.

### <a name="is-there-a-way-to-disable-the-organization-store"></a>Existe alguma forma de desativar o arquivo da organização?

Não. Os utilizadores veem sempre o separador *A MINHA ORGANIZAÇÃO* no Power BI Desktop e no serviço Power BI. Se um administrador desativar ou eliminar todos os elementos visuais organizacionais do Power BI no portal de administração, o arquivo organizacional ficará vazio.
  
### <a name="if-the-admin-disables-power-bi-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-power-bi-visuals"></a>Se o administrador desativar os elementos visuais do Power BI no Portal de administração (definições do inquilino), os utilizadores ainda terão acesso aos elementos visuais organizacionais do Power BI?

Sim, se o administrador desativar os elementos visuais do Power BI no portal de administração, a loja organizacional não será afetada.

Algumas organizações desativam os elementos visuais do Power BI e ativam apenas os elementos visuais selecionados manualmente que foram importados e carregados pelo administrador do Power BI para o arquivo organizacional.

No Power BI Desktop, não é imposta a desativação dos elementos visuais do Power BI no Portal de administração. Os utilizadores do Power BI Desktop continuam a poder adicionar e utilizar os elementos visuais do Power BI do marketplace público nos respetivos relatórios. No entanto, esses elementos visuais do Power BI públicos deixam de ser compostos assim que são publicados no Serviço Power BI e emitem um erro apropriado. 

Quando for aplicada a definição de elementos visuais do Power BI no portal de administração, os utilizadores no serviço Power BI não poderão importar os elementos visuais do Power BI do marketplace público. Apenas os elementos visuais do arquivo organizacional poderão ser importados.

### <a name="what-are-the-advantages-of-power-bi-visuals-in-the-organizational-store"></a>Quais são as vantagens de ter elementos visuais do Power BI no arquivo organizacional?

* Todos recebem a mesma versão do elemento visual, que é controlada pelo administrador do Power BI. Assim que o administrador atualiza a versão do elemento visual no portal de administração, todos os utilizadores da organização recebem automaticamente a versão atualizada.

* Não terá de partilhar ficheiros de elementos visuais por e-mail ou pastas partilhadas. As ofertas do arquivo organizacional estão visíveis para todos os membros com sessão iniciada.

* Segurança e compatibilidade: as novas versões dos elementos visuais organizacionais do Power BI são atualizadas automaticamente em todos os relatórios.

* Os administradores podem controlar quais são os elementos visuais do Power BI disponíveis na organização.

* Os administradores podem ativar/desativar os elementos visuais para fins de teste no portal de administração.

## <a name="certified-power-bi-visuals"></a>Elementos visuais do Power BI certificados

### <a name="what-are-certified-power-bi-visuals"></a>O que são elementos visuais do Power BI certificados?

Os elementos visuais do Power BI certificados cumprem determinados [requisitos](power-bi-custom-visuals-certified.md) e são certificados pela Microsoft.

No [marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals), os elementos visuais do Power BI certificados têm um destaque amarelo que indica que são certificados.

A Microsoft não é responsável pela criação de elementos visuais do Power BI de terceiros. Recomendamos que os clientes contactem diretamente o autor para verificar a funcionalidade dos elementos visuais de terceiros.

### <a name="what-tests-are-done-during-the-certification-process"></a>Que testes são realizados durante o processo de certificação?

Os testes do processo de certificação incluem, mas não estão limitados a: 
* Revisões de código
* Análise de código estático
* Fuga de dados
* Fuzzing de dados
* Testes de penetração
* Testes XSS de acesso
* Injeção de dados maliciosos
* Validação de entrada
* Testes funcionais
 
### <a name="are-certified-power-bi-visual-checked-again-with-every-new-submission-upgrade"></a>Os elementos visuais do Power BI certificados são novamente verificados em cada nova submissão (atualização)?

Yes. Sempre que a nova versão de um elemento visual certificado é submetida para o Marketplace, a atualização da versão do elemento visual passa pelas mesmas verificações de certificação.

A certificação da atualização da versão é automática. Se existir uma violação que faça com que a atualização seja rejeitada, será enviado um e-mail ao programador a explicar o que tem de ser corrigido.

### <a name="can-a-certified-power-bi-visual-stop-lose-its-certification-after-a-new-update"></a>Um elemento visual do Power BI certificado pode perder a certificação após uma nova atualização?

Não, isto não é possível. Um elemento visual certificado não pode perder a certificação com uma nova atualização. No entanto, a atualização é rejeitada.
 
### <a name="do-i-need-to-share-my-code-in-a-public-repository-if-im-certifying-my-power-bi-visual"></a>Tenho de partilhar o meu código num repositório público se estiver a certificar um elemento visual do Power BI?

Não precisa de partilhar o seu código para o público.

Forneça permissões de leitura para verificar o código do elemento visual do Power BI. Por exemplo, através de um repositório privado no GitHub.
 
### <a name="does-a-certified-power-bi-visual-have-to-be-in-the-marketplace"></a>Um elemento visual do Power BI certificado tem de estar no marketplace?

Yes. Os elementos visuais privados não são certificados.
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>A certificação do meu elemento visual demora quanto tempo?

A certificação de um novo elemento visual do Power BI (primeira certificação) pode demorar até quatro semanas. 

A certificação de uma versão atualizada de um elemento visual do Power BI pode demorar até três semanas. 

### <a name="does-the-certification-process-ensure-that-there-is-no-data-leakage"></a>O processo de Certificação garante que não ocorrem fugas de dados?

Os testes realizados são concebidos para verificar que o elemento visual não acede a serviços ou recursos externos. 

A Microsoft não é responsável pela criação de elementos visuais do Power BI de terceiros. Recomendamos que os clientes contactem diretamente o autor para verificar a funcionalidade dos elementos visuais do Power BI de terceiros.
 
### <a name="are-uncertified-power-bi-visuals-safe-to-use"></a>É seguro utilizar elementos visuais do Power BI não certificados?

Os elementos visuais do Power BI não certificados não são necessariamente inseguros.

Alguns elementos visuais não são certificados porque não cumprem um ou mais [requisitos de certificação](power-bi-custom-visuals-certified.md#certification-requirements). Um exemplo disto é a ligação a um serviço externo, como elementos visuais de mapa, ou elementos visuais que utilizam bibliotecas comerciais.
 
## <a name="visuals-with-additional-purchases"></a>Elementos visuais com possibilidade de compras adicionais

### <a name="what-is-a-visual-with-additional-purchases"></a>O que é um elemento visual com possibilidade de compras adicionais?

Um elemento visual com compras adicionais é semelhante aos suplementos de compra na aplicação (IAP). Estes suplementos incluem uma etiqueta de preço **Pode ser necessária uma compra adicional**.

Os elementos visuais do Power BI IAP são gratuitos e podem ser transferidos. Os utilizadores não pagam nada pela transferência destes elementos visuais do Power BI a partir do marketplace.

Os elementos visuais de IAP disponibilizam compras via aplicação adicionais opcionais para obter funcionalidades avançadas.  

### <a name="what-is-changing-in-the-submission-process"></a>O que será alterado no processo de submissão?

O processo de submissão de elementos visuais do Power BI IAP e de elementos visuais do Power BI gratuitos para o marketplace é o mesmo. Pode submeter um elemento visual do Power BI para ser certificado através do [Centro de Parceiros](/partner-center/).


Ao registar o elemento visual do Power BI, navegue para o separador *Configuração do produto* e selecione a caixa de verificação *O meu produto requer a compra de um serviço*.

### <a name="what-should-i-do-beforesubmittingmy-iap-power-bi-visual"></a>O que devo fazer antes de submeter o meu elemento visual do Power BI IAP?

Se estiver a trabalhar num elemento visual do Power BI IAP, confirme que cumpre as [diretrizes](guidelines-powerbi-visuals.md).  

> [!NOTE]
> Os elementos visuais gratuitos do Power BI com uma funcionalidade IAP têm de manter as mesmas funcionalidades gratuitas disponibilizadas anteriormente. Opcionalmente, pode adicionar funcionalidades avançadas pagas para além das antigas funcionalidades gratuitas. Recomendamos submeter o elemento visual do Power BI IAP com as funcionalidades avançadas como um novo elemento visual do Power BI e não atualizar o antigo gratuito.

### <a name="do-iap-power-bi-visuals-need-to-be-certified"></a>Os elementos visuais do Power BI IAP têm de ser certificados?

O processo de [certificação](power-bi-custom-visuals-certified.md) é opcional. O programador é que decide se quer certificar o elemento visual do Power BI IAP ou não.

### <a name="can-i-get-my-iap-power-bi-visual-certified"></a>Posso certificar o meu elemento visual do Power BI IAP?

Sim. Quando o elemento visual do Power BI IAP for aprovado pela equipa do AppSource, poderá submetê-lo para [certificação](power-bi-custom-visuals-certified.md).

A certificação é um processo opcional. Cabe-lhe a si decidir se quer certificar o elemento visual IAP.

## <a name="additional-questions"></a>Perguntas adicionais

### <a name="how-to-get-support"></a>Como posso obter suporte?

Não hesite em enviar perguntas, fazer comentários ou comunicar problemas à equipa de suporte de elementos visuais do Power BI para o endereço pbicvsupport@microsoft.com.  

## <a name="next-steps"></a>Próximos passos

Para obter mais informações, visite [Resolver problemas com os elementos visuais do Power BI](power-bi-custom-visuals-troubleshoot.md).