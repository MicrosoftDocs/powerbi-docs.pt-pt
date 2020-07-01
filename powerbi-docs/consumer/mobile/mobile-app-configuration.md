---
title: Definições de configuração da aplicação Power BI
description: Como personalizar o comportamento do Power BI com a ferramenta MDM
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 04/05/2020
ms.author: painbar
ms.openlocfilehash: 62d95c09761a22f514bb55b5eadd82a6214fdbeb
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85235120"
---
# <a name="remotely-configure-power-bi-app-using-mobile-device-management-mdm-tool"></a>Configurar remotamente a aplicação Power BI com a ferramenta de gestão de dispositivos móveis (MDM)

A aplicação Power BI Mobile para iOS e Android suporta as definições da aplicação que permitem que os administradores dos serviços de gestão de dispositivos móveis (MDM), como o Intune, personalizem o comportamento da aplicação.

A aplicação Power BI Mobile suporta os seguintes cenários de configuração:

* Configuração do Servidor de Relatórios (iOS e Android)
* Definições de proteção de dados (iOS e Android)
* Definições de interação (iOS e Android)

## <a name="report-server-configuration-ios-and-android"></a>Configuração do servidor de relatórios (iOS e Android)

A aplicação Power BI para iOS e Android permite que os administradores “emitam” remotamente a configuração do Servidor de Relatórios com os dispositivos inscritos.

| Chave | Tipo | Descrição |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | Cadeia | URL do Servidor de Relatórios.<br><br>Deve começar por http/https.|
| com.microsoft.powerbi.mobile.ServerUsername | Cadeia | [opcional]<br><br>O nome de utilizador a utilizar para ligar o servidor.<br><br>Se não existir, a aplicação pedirá ao utilizador para escrever o nome de utilizador para a ligação.|
| com.microsoft.powerbi.mobile.ServerDisplayName | Cadeia | [opcional]<br><br>O valor predefinido é “Servidor de relatórios”<br><br>Um nome amigável utilizado na aplicação para representar o servidor. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Booleano | [opcional]<br><br>O valor predefinido é Verdadeiro. Quando definido como Verdadeiro, substitui todas as definições do Servidor de Relatórios já existente no dispositivo móvel. Os servidores existentes que já estiverem configurados serão eliminados. Quando a substituição está definida como Verdadeiro, isto impede também que o utilizador remova essa configuração.<br><br>Se estiver definido como Falso, adicionará os valores emitidos, mantendo as definições existentes. Se o mesmo URL do servidor já estiver configurado na aplicação móvel, esta manterá essa configuração tal como está. A aplicação não pedirá ao utilizador para voltar a autenticar para o mesmo servidor. |

## <a name="data-protection-settings-ios-and-android"></a>Definições de proteção de dados (iOS e Android)

A aplicação móvel Power BI para iOS e Android permite que os administradores personalizem a configuração predefinida para as definições de privacidade e segurança. Para iOS, pode forçar os utilizadores a fornecer o Face ID, o Touch ID ou um código de acesso para acederem à aplicação móvel Power BI. Para Android, pode forçar os utilizadores a utilizar autenticação biométrica (ID de Impressão Digital).

| Chave | Tipo | Descrição |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Booleano | O valor predefinido é Falso. <br><br>Podem ser necessários dados biométricos, tais como o TouchID ou o FaceID (iOS) ou o ID de Impressão Digital (Android), para que os utilizadores acedam à aplicação no respetivo dispositivo. Nesse caso, são utilizados dados biométricos além da autenticação.<br><br>Se forem utilizadas políticas de proteção de aplicações, a Microsoft recomenda a desativação desta definição para evitar pedidos de acesso duplo. |

>[!NOTE]
>As definições de proteção de dados serão aplicadas apenas em dispositivos Android que suportam a autenticação biométrica.

## <a name="interaction-settings-ios-and-android"></a>Definições de interação (iOS e Android)

A aplicação Power BI para iOS e Android oferece aos administradores a capacidade de configurar definições de interação, caso se decida que as predefinições de interação têm de ser alteradas nos diferentes grupos de utilizadores numa organização.

>[!NOTE]
>Nem todas as interações são atualmente suportadas em todos os dispositivos. Veja [Configurar definições de interação do relatório](mobile-app-interaction-settings.md) para obter um gráfico que mostra a disponibilidade atual entre dispositivos.

| Chave | Tipo | Valores | Descrição |
|---|---|---|---|
| com.microsoft.powerbi.mobile.ReportTapInteraction | Cadeia |  <nobr>single-tap</nobr><br><nobr>double-tap</nobr> | Configure se um toque num elemento visual também criará uma seleção de ponto de dados. |
| com.microsoft.powerbi.mobile.EnableMultiSelect | Booleano |  <nobr>Verdadeiro</nobr><br><nobr>Falso</nobr> | Configure se um toque num ponto de dados substituirá a seleção atual ou será adicionado à seleção atual. |
| com.microsoft.powerbi.mobile.RefreshAction | Cadeia |  <nobr>pull-to-refresh</nobr><br>. | Configure se o utilizador terá um botão para atualizar o relatório ou se deve utilizar a funcionalidade “pull to refresh” (puxar para atualizar). |
| com.microsoft.powerbi.mobile.FooterAppearance | Cadeia |  docked<br>dynamic | Configure se o rodapé do relatório será ancorado à parte inferior do relatório ou ocultado automaticamente. |

## <a name="deploying-app-configuration-settings"></a>Implementar definições de configuração da aplicação

Em seguida, encontrará os passos de que necessita para criar uma política de configuração da aplicação. Depois de ter criado a política de configuração, pode atribuir as definições aos grupos de utilizadores.

1. Ligue a sua ferramenta MDM.
2. Crie e dê um nome a uma nova política de configuração da aplicação.
3. Escolha os utilizadores pelos quais pretende distribuir esta política de configuração da aplicação.
4. Crie pares chave-valor para a definição que pretende emitir para os seus utilizadores.

O portal do Intune permite que os administradores implementem estas definições facilmente na aplicação Power BI através de políticas de configuração da aplicação. No entanto, é suportado qualquer fornecedor de MDM. Se não utilizar o Intune, terá de consultar a documentação relativa à MDM para saber como implementar estas definições.

## <a name="next-steps"></a>Próximas etapas

* Obtenha a aplicação móvel do Power BI na [App Store](https://apps.apple.com/app/microsoft-power-bi/id929738808) e no [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.powerbim&amp;amp;clcid=0x409)
* Siga o [@MSPowerBI no Twitter](https://twitter.com/MSPowerBI)
* Participe na conversa na [Comunidade do Power BI](https://community.powerbi.com/)
