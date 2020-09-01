---
description: -recurse (Options du compilateur C#)
title: -recurse (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: 3edd7e23358bc0569dae6204d519209df1ade290
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124823"
---
# <a name="-recurse-c-compiler-options"></a>-recurse (Options du compilateur C#)
L’option -recurse permet de compiler des fichiers de code source dans tous les répertoires enfants du répertoire spécifié (dir) ou du répertoire du projet.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir` (facultatif)  
 Répertoire dans lequel vous voulez commencer la recherche. Si ce répertoire n’est pas spécifié, la recherche commence dans le répertoire du projet.  
  
 `file`  
 Le ou les fichiers à rechercher. Les caractères génériques sont autorisés.  
  
## <a name="remarks"></a>Remarques  
 L’option **-recurse** vous permet de compiler des fichiers de code source dans tous les répertoires enfants du répertoire spécifié ( `dir` ) ou du répertoire du projet.  
  
 Vous pouvez utiliser des caractères génériques dans un nom de fichier pour compiler tous les fichiers correspondants dans le répertoire du projet sans utiliser **-recurse**.  
  
 Cette option de compilateur n’est pas disponible dans Visual Studio et ne peut pas être changée par programmation.  
  
## <a name="example"></a>Exemple  
 Compile tous les fichiers C# qui se trouvent dans le répertoire actif :  
  
```console  
csc *.cs  
```  
  
 Compile tous les fichiers C# du répertoire dir1\dir2 et de tous les sous-répertoires qui se situent en dessous de celui-ci, puis génère dir2.dll :  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](./index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
