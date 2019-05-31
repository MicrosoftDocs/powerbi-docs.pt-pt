---
ms.openlocfilehash: 3e89344ef1298864b485f465b28c56397a7e1511
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61194089"
---
## <a name="using-the-username-or-userprincipalname-dax-function"></a>Utilizar as funções DAX username() ou userprincipalname()
Pode tirar partido das funções DAX *username()* ou *userprincipalname()* dentro do conjunto de dados. Pode utilizá-las nas expressões no Power BI Desktop. Quando publicar o seu modelo, este será utilizado no âmbito do serviço Power BI.

No Power BI Desktop, *username()* irá devolver um utilizador no formato de *DOMÍNIO\Utilizador* e *userprincipalname()* irá devolver um utilizador no formato de  <em>user@contoso.com</em>.

No âmbito do serviço Power BI, *username()* e *userprincipalname()* irão devolver o Nome Principal de Utilizador (UPN) do utilizador. Isto parece ser semelhante a um endereço de e-mail.

