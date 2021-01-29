---
title: Verificação de revogação de certificado no Power BI Desktop
description: Como revogar certificados no Power BI Desktop na UI e no registo
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 01/25/2021
LocalizationGroup: Create reports
ms.openlocfilehash: 482f0f8279de9818b631ff79e7b37a215e7397bd
ms.sourcegitcommit: 7ed995eed0fd6e718748accf87bae384211cd95d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/29/2021
ms.locfileid: "99057011"
---
# <a name="certificate-revocation-in-power-bi-desktop"></a>Revogação do certificado no Power BI Desktop

O Power BI oferece duas formas de ativar ou desativar um controlo de certificado. Em novembro de 2020, introduzimos uma verificação simples de revogação de certificados de entrada/saída para ligações web no Power BI Desktop. Agora pode ter mais controlo de grãos finos sobre a verificação de revogação do certificado.

## <a name="simple-certificate-revocation"></a>Revogação simples do certificado

Na interface do utilizador no Power BI Desktop, pode ativar ou desativar a funcionalidade.

- No menu **'Ficheiro'** > **Opções e definições**  >  **Opções**, selecione **Segurança**, em seguida, selecione ou **limpe a verificação de revogação do certificado**.

## <a name="more-fine-grained-control"></a>Controlo mais fino

Pode ter um controlo mais fino sobre a verificação de revogação do certificado com uma terceira opção. 

- **Básico**  O cheque de base aceita certificados cujo estado de revogação é desconhecido, por exemplo, porque o certificado não o especifica. Este cheque é importante para organizações que usam servidores proxy corporativos. É o mesmo que selecionar a caixa de verificação no Power BI Desktop.
- **Deficientes** O mesmo que desativar a caixa de verificação no Power BI Desktop.
- **Abrangente** Pode desativar ou ativar o check-in de revogação em modo *abrangente,* que não aceita certificados com estatuto de revogação desconhecida. 


|Estatuto de informação de revogação do certificado | Verificação abrangente | Verificação básica | Nenhum |
|---------|---------|---------|---------|
|Revoked     |  ❌  | ❌  | ✔   |
|Desconhecido  |  ❌    |  ✔   |    ✔  |
|Não revogado  | ✔  |    ✔ |    ✔  |

A caixa de verificação simples Enable ou Disable ainda se encontra na interface de utilizador power BI Desktop. Para utilizar o controlo mais fino, defina o seguinte valor de registo DWORD: `DisableCertificateRevocationCheck` . Definiu este valor na chave de registo de desktop Power BI. É um destes, dependendo do seu sistema operativo:

```
HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Microsoft Power BI Desktop
```

Arte

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Power BI Desktop
```

Desaguise o valor do registo para um dos seguintes valores: 

|Valor  |Modo  |Configuração  |
|---------|---------|---------|
|0     | Básico   | São aceites certificados com estatuto de revogação desconhecida. Equivalente a ativar a caixa de verificação no Power BI Desktop. |
|1     | Desativado  | Ignora todos os cheques de revogação. Equivalente a desativar a caixa de verificação no Power BI Desktop.  |
|2     | Abrangente  |  Não requer a revogação de certificados. Não aceita certificados com estatuto de revogação desconhecida |

Configure esta definição de registo para aproveitar um controlo mais fino hoje.