---
title: Génération à partir de la ligne de commande
ms.date: 07/20/2015
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers [Visual Basic], invoking from command line
- command-line builds
- compiling source code
- command-line compilers [Visual Basic], Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
ms.openlocfilehash: c7219c0497bb87f0cc44f27229eaf25f9b3eebce
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344794"
---
# <a name="building-from-the-command-line-visual-basic"></a>Génération à partir de la ligne de commande (Visual Basic)

Un projet de Visual Basic est constitué d’un ou de plusieurs fichiers sources distincts. Pendant le processus appelé compilation, ces fichiers sont rassemblés dans un package, un fichier exécutable unique qui peut être exécuté en tant qu’application.

Visual Basic fournit un compilateur de ligne de commande comme alternative à la compilation de programmes à partir de l’environnement de développement intégré (IDE) de Visual Studio. Le compilateur de ligne de commande est conçu pour les situations dans lesquelles vous n’avez pas besoin de l’ensemble complet des fonctionnalités de l’IDE, par exemple lorsque vous utilisez ou écrivez pour des ordinateurs avec une mémoire système ou un espace de stockage limité.

Pour compiler les fichiers sources à partir de l’IDE de Visual Studio, choisissez la commande **générer** dans le menu **générer** .

> [!TIP]
> Quand vous générez des fichiers projet à l’aide de l’IDE de Visual Studio, vous pouvez afficher des informations sur la commande **vbc** associée et ses commutateurs dans la fenêtre sortie. Pour afficher ces informations, ouvrez la [boîte de dialogue Options, projets et solutions, générer et exécuter](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), puis définissez le niveau de détail de la **sortie de génération du projet MSBuild** sur **normal** ou sur un niveau de détail plus élevé. Pour plus d’informations, consultez [Comment : afficher, enregistrer et configurer des fichiers journaux de génération](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).

Vous pouvez compiler des fichiers projet (. vbproj) à partir d’une invite de commandes à l’aide de MSBuild. Pour plus d’informations, consultez informations de [référence sur la ligne de commande](/visualstudio/msbuild/msbuild-command-line-reference) et [procédure pas à pas : utilisation de MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).

## <a name="in-this-section"></a>Dans cette section

[Comment : appeler le compilateur de ligne de commande](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) \
Décrit comment appeler le compilateur de ligne de commande à l’invite MS-DOS ou à partir d’un sous-répertoire spécifique.

[Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) \
Fournit une liste d’exemples de lignes de commande que vous pouvez modifier pour votre propre usage.

## <a name="related-sections"></a>Sections connexes

[Visual Basic du compilateur de ligne de commande](../../../visual-basic/reference/command-line-compiler/index.md) \
Fournit des listes d’options du compilateur classées par ordre alphabétique ou par objectif.

[Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) \
Décrit comment compiler des sections de code particulières.

[Génération et nettoyage de projets et de solutions dans Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) \
Décrit comment organiser ce qui sera inclus dans les différentes builds, choisir des propriétés de projet et vérifier que les projets sont générés dans le bon ordre.
