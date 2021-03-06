---
description: -debug (Options du compilateur C#)
title: -debug (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /debug
helpviewer_keywords:
- debug compiler option [C#]
- -debug compiler option [C#]
- /debug compiler option [C#]
ms.assetid: e2b48c07-01bc-45cc-a52c-92e9085eb969
ms.openlocfilehash: 77aa9bf0fc0911f441d00403d773ee5ae03ae99b
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91173293"
---
# <a name="-debug-c-compiler-options"></a>-debug (Options du compilateur C#)

L’option **-debug** fait en sorte que le compilateur génère des informations de débogage et les place dans les fichiers de sortie.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-debug[+ | -]  
-debug:{full | pdbonly}  
```  
  
## <a name="arguments"></a>Arguments  

 `+` &#124; `-`  
 Si vous spécifiez `+` ou simplement **-debug**, le compilateur génère des informations de débogage et les place dans un fichier de base de données du programme (.pdb). Si vous spécifiez `-`, qui est en vigueur si vous ne spécifiez pas **-debug**, aucune information de débogage n’est créée.  
  
 `full` &#124; `pdbonly`  
 Indique le type d'informations de débogage générées par le compilateur. L’argument complet, qui est en vigueur si vous ne spécifiez pas **-debug:pdbonly**, permet d’attacher un débogueur au programme en cours d’exécution. Le fait de spécifier pdbonly active le débogage du code source quand le programme est démarré dans le débogueur, mais affiche uniquement un assembleur quand le programme en cours d’exécution est attaché au débogueur.  
  
## <a name="remarks"></a>Notes  

 Utilisez cette option pour créer des versions Debug. Si **-debug**, **-debug+** ou **-debug:full** n’est pas spécifié, vous ne pourrez pas déboguer le fichier de sortie de votre programme.  
  
 Si vous utilisez **-debug:full**, sachez qu’il y a un impact sur la vitesse et la taille du code optimisé JIT, ainsi qu’un faible impact sur la qualité du code avec **-debug:full**. Nous vous recommandons d’utiliser **-debug:pdbonly** ou aucun PDB pour la génération du code de version finale.  
  
> [!NOTE]
> L’une des différences entre **-debug:pdbonly** et **-debug:full** est qu’avec **-debug:full**, le compilateur émet un <xref:System.Diagnostics.DebuggableAttribute>, qui est utilisé pour signaler au compilateur JIT que des informations de débogage sont disponibles. Ainsi, une erreur se produit si votre code contient un <xref:System.Diagnostics.DebuggableAttribute> avec la valeur false si vous utilisez **-debug:full**.  
  
 Pour plus d’informations sur la façon de configurer les performances de débogage d’une application, consultez [Simplification du débogage d’une image](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
 Pour changer l’emplacement du fichier .pdb, consultez [-pdb (Options du compilateur C#)](./pdb-compiler-option.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1. Ouvrez la page **Propriétés** du projet.  
  
2. Cliquez sur la page de propriétés **Générer**.  
  
3. Cliquez sur le bouton **Avancé** .  
  
4. Modifiez la propriété **Infos de débogage**.  
  
 Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DebugSymbols%2A>.  
  
## <a name="example"></a>Exemple  

 Placez les informations de débogage dans le fichier de sortie `app.pdb` :  
  
```console  
csc -debug -pdb:app.pdb test.cs  
```  
  
## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](./index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
