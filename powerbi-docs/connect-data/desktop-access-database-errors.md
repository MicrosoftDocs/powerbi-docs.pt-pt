---
title: Resolver problemas de importação de .XLS e Access no Power BI Desktop
description: Resolver problemas de importação de bases de dados do Access e folhas de cálculo .XLS no Power BI Desktop e Power Query
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/21/2019
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 1816fb7926ed378cdb70ce2e0ade08893828ce4c
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83301339"
---
# <a name="troubleshoot-importing-access-and-excel-xls-files-in-power-bi-desktop"></a>Resolver problemas de importação de ficheiros .xls do Access e do Excel no Power BI Desktop

No Power BI Desktop, as Bases de dados do Access e as versões mais antigas dos Livros do Excel (ficheiros .XLS do tipo Excel 97-2003) utilizam o *Motor de Base de Dados do Access*. Há três situações comuns que podem impedir que o Motor de Base de Dados do Access funcione corretamente.

## <a name="situation-1-no-access-database-engine-is-installed"></a>Situação 1: Nenhum Motor de Base de Dados do Access está instalado

Se a mensagem de erro do Power BI Desktop indica que o Motor de Base de Dados do Access não está instalado, deve instalar a versão de 32 ou 64 bits do Motor de Base de Dados do Access que corresponde à sua versão do Power BI Desktop. Pode instalar o Motor de Base de Dados do Access a partir da [página de transferências](https://www.microsoft.com/download/details.aspx?id=13255).

>[!NOTE]
>Se a versão de bits instalada do Motor de Base de Dados do Access for diferente da versão de bits de instalação do Microsoft Office, as aplicações do Office não poderão utilizar o Motor de Base de Dados do Access.

## <a name="situation-2-the-access-database-engine-bit-version-32-bit-or-64-bit-is-different-from-your-power-bi-desktop-bit-version"></a>Situação 2: a versão de bits do Motor de Base de Dados do Access (32 ou 64 bits) é diferente da versão de bits do Power BI Desktop

Esta situação geralmente ocorre quando a versão instalada do Microsoft Office é de 32 bits e a versão do Power BI Desktop instalada é de 64 bits. O contrário também pode acontecer e a incompatibilidade da versão de bits ocorrerá em ambos os casos. Se estiver a utilizar uma subscrição do Office 365, veja [Situação 3](#situation-3-trouble-using-access-or-xls-files-with-an-office-365-subscription) para um problema e resolução diferentes. Qualquer uma das seguintes soluções pode solucionar este erro de inconsistência de versão de bits:

### <a name="solution-1"></a>Solução 1

Altere a versão do Power BI Desktop para corresponder à versão de bits de instalação do Microsoft Office. 

1. Para alterar a versão de bits do Power BI Desktop, desinstale o Power BI Desktop e, em seguida, instale a versão do Power BI Desktop que corresponde à sua instalação do Office. 

1. Para selecionar uma versão do Power BI Desktop, selecione **Opções de transferência avançadas** na página de transferência do Power BI Desktop.
   
   ![Opções de transferência avançadas na página de transferência do Power BI Desktop](media/desktop-access-database-errors/desktop-access-errors-1.png)
   
1. Na página de transferência que for apresentada, selecione o seu idioma e, em seguida, selecione o botão **Transferir**. 
 
1. No ecrã apresentado, selecione a caixa de verificação ao lado de PBIDesktop.msi para a versão de 32 bits ou PBIDesktop_x64.msi para a versão de 64 bits. 

   Na seguinte captura de ecrã, está selecionada a versão de 64 bits.
   
   ![Escolher o tipo de transferência do Power BI Desktop](media/desktop-access-database-errors/desktop-access-errors-2.png)
   
   >[!NOTE]
   >Se utilizar a versão de 32 bits do Power BI Desktop, quando criar modelos de dados muito grandes, poderá ter problemas de memória insuficiente.

### <a name="solution-2"></a>Solução 2

Altere a versão de bits do Microsoft Office para corresponder à versão de bits da instalação do Power BI Desktop:

1. Desinstalar o Microsoft Office

2. Instale a versão do Office que corresponde à sua instalação do Power BI Desktop.

### <a name="solution-3"></a>Solução 3

Se o erro ocorrer ao tentar abrir um ficheiro .XLS (um livro do Excel 97-2003), poderá evitar a utilização do Motor de Base de Dados do Access ao abrir o ficheiro .XLS no Excel e guardando-o como um ficheiro XLSX.

### <a name="solution-4"></a>Solução 4

Se as três soluções anteriores não forem viáveis, é possível instalar as duas versões do Motor de Base de Dados do Access. No entanto, esta solução não é recomendada. Embora instalar ambas as versões resolva este problema para o Power Query para Excel e o Power BI Desktop, apresentará erros e problemas de qualquer aplicação que utilize automaticamente (por predefinição) a versão de bits do Motor de Base de Dados do Access que foi instalado pela primeira vez. 

Para instalar as duas versões de bits do Motor de Base de Dados do Access, siga estes passos:

1. Instale as duas versões de bits do Motor de Base de Dados do Access a partir da [página de transferência](https://www.microsoft.com/download/details.aspx?id=13255). 

1. Execute cada versão do Motor de Base de Dados do Access com a opção */passive*. Por exemplo:
   
       c:\users\joe\downloads\AccessDatabaseEngine.exe /passive
   
       c:\users\joe\downloads\AccessDatabaseEngine_x64.exe /passive

## <a name="situation-3-trouble-using-access-or-xls-files-with-an-office-365-subscription"></a>Situação 3: Problemas ao utilizar ficheiros .XLS ou do Access com uma subscrição do Office 365

Se estiver a utilizar uma subscrição do Office 365, seja o **Office 2013** ou o **Office 2016**, o fornecedor do Motor de Base de Dados do Access é registado numa localização de registo virtual que *só* está acessível para os processos do Microsoft Office. Como resultado, o Motor de Aplicação Híbrida (que é responsável por executar o Excel não Office 365 e o Power BI Desktop e não é um processo do Office), não pode utilizar o fornecedor do Motor de Base de Dados do Access.

Para solucionar esta situação, [transfira e instale o Motor de Base de Dados do Access redistribuível](https://www.microsoft.com/download/details.aspx?id=13255) correspondente à versão de bits da sua instalação do Power BI Desktop. Para obter mais informações sobre as versões de bits, veja as secções anteriores neste artigo.

## <a name="other-situations-that-can-cause-import-issues"></a>Outras situações que podem originar problemas de importação

Esforçamo-nos por cobrir o máximo possível de problemas que ocorram com ficheiros .XLS ou Access. Caso se depare com problemas que não são abrangidos neste artigo, submeta uma pergunta sobre o problema ao [Suporte do Power BI](https://powerbi.microsoft.com/support/). Estamos regularmente à procura de problemas que possam afetar muitos clientes para incluí-los nos nossos artigos.

