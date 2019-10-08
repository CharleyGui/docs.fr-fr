---
title: -rootnamespace
ms.date: 03/13/2018
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
ms.openlocfilehash: 4df4e74fc13c922f51f5b74c3c152bdea28b4431
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005212"
---
# <a name="-rootnamespace"></a>-rootnamespace
Spécifie un espace de noms pour toutes les déclarations de type.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`namespace`|Nom de l’espace de noms dans lequel placer toutes les déclarations de type pour le projet actuel.|  
  
## <a name="remarks"></a>Notes  
 Si vous utilisez le fichier exécutable Visual Studio (devenv. exe) pour compiler un projet créé dans l’environnement de développement intégré de Visual Studio, utilisez `-rootnamespace` pour spécifier la valeur de la propriété <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A>. Pour plus d’informations, consultez [commutateurs de ligne de commande devenv](/visualstudio/ide/reference/devenv-command-line-switches) .  
  
 Utilisez l’common language runtime désassembleur MSIL (`Ildasm.exe`) pour afficher les noms des espaces de noms dans votre fichier de sortie.  
  
|Pour Set-RootNamespace dans l’environnement de développement intégré Visual Studio|  
|---|  
|1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Dans le menu **Projet**, cliquez sur **Propriétés**. <br />2.  Cliquez sur l’onglet **Application** .<br />3.  Modifiez la valeur dans la zone **espace de noms racine** .|  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `In.vb` et encadre toutes les déclarations de type dans l’espace de noms `mynamespace`.  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Ildasm.exe (désassembleur IL)](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
