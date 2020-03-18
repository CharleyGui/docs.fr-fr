---
title: -addmodule (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: 148a63c37cfbc4c60448adccde10947e91e22bb9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970184"
---
# <a name="-addmodule-c-compiler-options"></a>-addmodule (Options du compilateur C#)
Cette option ajoute un module créé avec le commutateur target:module à la compilation actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a>Arguments  
 `file`, `file2`  
 Fichier de sortie qui contient des métadonnées. Le fichier ne peut pas contenir un manifeste d’assembly. Pour importer plusieurs fichiers, séparez les noms des fichiers par une virgule ou un point-virgule.  
  
## <a name="remarks"></a>Notes   
 Tous les modules ajoutés par **-addmodule** doivent se trouver dans le même répertoire que le fichier de sortie au moment de l’exécution. Vous pouvez donc spécifier un module dans n’importe quel répertoire au moment de la compilation, mais le module doit se trouver dans le répertoire de l’application au moment de l’exécution. Si le module n’est pas dans le répertoire de l’application au moment de l’exécution, vous obtiendrez <xref:System.TypeLoadException>.  
  
 `file` ne peut pas contenir un assembly. Si, par exemple, le fichier de sortie a été créé avec [-target:module](./target-module-compiler-option.md), ses métadonnées peuvent être importées avec **-addmodule**.  
  
 Si le fichier de sortie a été créé avec une option **-target** autre que **-target:module**, ses métadonnées ne peuvent pas être importées avec **-addmodule**, mais peuvent l’être avec [-reference](./reference-compiler-option.md).  
  
 Cette option du compilateur n’est pas disponible dans Visual Studio ; un projet ne peut pas référencer un module. Par ailleurs, cette option du compilateur ne peut pas être changée par programmation.  
  
## <a name="example"></a> Exemple  
 Compilez le fichier source `input.cs` et ajoutez les métadonnées de `metad1.netmodule` et `metad2.netmodule` pour produire `out.exe` :  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a>Voir aussi

- [Options de compilateur C](./index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
- [Assemblages multifils](../../../framework/app-domains/multifile-assemblies.md)
- [Guide pratique pour générer un assembly multifichier](../../../framework/app-domains/build-multifile-assembly.md)
