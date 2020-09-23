---
title: -baseaddress
ms.date: 08/09/2018
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
ms.openlocfilehash: c794d1fc1c9d20e22ffa747e3175c846341ad8ad
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097759"
---
# <a name="-baseaddress"></a>-baseaddress

Spécifie une adresse de base par défaut lors de la création d’une DLL.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`address`|Obligatoire. Adresse de base de la DLL. Cette adresse doit être spécifiée sous la forme d’un nombre hexadécimal.|  
  
## <a name="remarks"></a>Notes  

 L’adresse de base par défaut d’une DLL est définie par le .NET Framework.  
  
 N’oubliez pas que le mot de poids faible dans cette adresse est arrondi. Par exemple, si vous spécifiez 0x11110001, il est arrondi à 0x11110000.  
  
 Pour terminer le processus de signature pour une DLL, utilisez l' `–R` option de l’outil Strong Naming Tool (Sn.exe).  
  
 Cette option est ignorée si la cible n’est pas une DLL.  
  
|Pour définir-baseaddress dans l’IDE de Visual Studio|  
|---|  
|1. Sélectionnez un projet dans **Explorateur de solutions**. Dans le menu **Projet** , cliquez sur **Propriétés**. <br />2. cliquez sur l’onglet **compiler** .<br />3. cliquez sur **avancé**.<br />4. modifiez la valeur dans la zone adresse de base de la **dll :** . **Remarque :**      La zone **adresse de base** de la dll est en lecture seule, sauf si la cible est une dll.|  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
- [-cible (Visual Basic)](target.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
- [Sn.exe (outil Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))
