---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 7ded2b7d102430d8d4e545da5ab6ce8bafe3609e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095420"
---
# <a name="-recurse"></a>-recurse

Compile les fichiers de code source dans tous les répertoires enfants du répertoire spécifié ou du répertoire du projet.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  

 `dir`  
 Optionnel. Répertoire dans lequel vous voulez commencer la recherche. S’il n’est pas spécifié, la recherche commence dans le répertoire du projet.  
  
 `file`  
 Obligatoire. Le ou les fichiers à rechercher. Les caractères génériques sont autorisés.  
  
## <a name="remarks"></a>Notes  

 Vous pouvez utiliser des caractères génériques dans un nom de fichier pour compiler tous les fichiers correspondants dans le répertoire du projet sans utiliser `-recurse` . Si aucun nom de fichier de sortie n’est spécifié, le compilateur base le nom du fichier de sortie sur le premier fichier d’entrée traité. Il s’agit généralement du premier fichier de la liste des fichiers compilés lorsqu’ils sont affichés par ordre alphabétique. Pour cette raison, il est préférable de spécifier un fichier de sortie à l’aide de l' `-out` option.  
  
> [!NOTE]
> L' `-recurse` option n’est pas disponible dans l’environnement de développement Visual Studio ; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  

 La commande suivante compile tous les fichiers Visual Basic dans le répertoire actif.  
  
```console
vbc *.vb  
```  
  
 La commande suivante compile tous les fichiers Visual Basic dans le `Test\ABC` répertoire et tous les répertoires situés en dessous de celui-ci, puis génère `Test.ABC.dll` .  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
- [-out (Visual Basic)](out.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
