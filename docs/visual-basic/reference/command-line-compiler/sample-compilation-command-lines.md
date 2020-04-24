---
title: Exemples de lignes de commande de compilation
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
ms.openlocfilehash: 27a20a5a3525353ffbced729b8ac9c98b3e48fc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350852"
---
# <a name="sample-compilation-command-lines-visual-basic"></a>Exemples de lignes de commande de compilation (Visual Basic)

En guise d’alternative à la compilation de Visual Basic programmes dans Visual Studio, vous pouvez compiler à partir de la ligne de commande pour produire des fichiers exécutables (. exe) ou des fichiers de bibliothèque de liens dynamiques (. dll).

Le Visual Basic compilateur de ligne de commande prend en charge un ensemble complet d’options qui contrôlent les fichiers d’entrée et de sortie, les assemblys, ainsi que les options de débogage et de préprocesseur. Chaque option est disponible dans deux formulaires interchangeables : `-option` et `/option`. Cette documentation affiche uniquement le `-option` formulaire.

Le tableau suivant répertorie quelques exemples de lignes de commande que vous pouvez modifier pour votre propre usage.

|À|Utiliser|
|--------|---------|
|Compiler file. vb et créer file. exe|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|
|Compiler file. vb et créer file. dll|`vbc -target:library File.vb`|
|Compiler file. vb et créer My. exe|`vbc -out:My.exe File.vb`|
|Compiler file. vb et créer une bibliothèque et un assembly de référence nommé file. dll|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|Compiler tous les fichiers Visual Basic dans le répertoire actif, avec les optimisations sur `DEBUG` et le symbole défini, générant fichier2. exe|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|
|Compilez tous les fichiers Visual Basic dans le répertoire actif, en générant une version de débogage du fichier fichier2. dll sans afficher le logo ou les avertissements|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|
|Compiler tous les fichiers Visual Basic du répertoire actif dans un fichier. dll|`vbc -target:library -out:Something.dll *.vb`|

> [!TIP]
> Quand vous générez un projet à l’aide de l’IDE de Visual Studio, vous pouvez afficher des informations sur la commande **vbc** associée avec ses options de compilateur dans la fenêtre sortie. Pour afficher ces informations, ouvrez la [boîte de dialogue Options, projets et solutions, générer et exécuter](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), puis définissez le niveau de détail de la **sortie de génération du projet MSBuild** sur **normal** ou sur un niveau de détail plus élevé.

## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
