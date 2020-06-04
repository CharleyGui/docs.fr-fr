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
ms.openlocfilehash: 496627d3b77b0382ae7d15c8225a6fbd41f1db73
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403120"
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="a118f-102">Exemples de lignes de commande de compilation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a118f-102">Sample compilation command lines (Visual Basic)</span></span>

<span data-ttu-id="a118f-103">En guise d’alternative à la compilation de Visual Basic programmes dans Visual Studio, vous pouvez compiler à partir de la ligne de commande pour produire des fichiers exécutables (. exe) ou des fichiers de bibliothèque de liens dynamiques (. dll).</span><span class="sxs-lookup"><span data-stu-id="a118f-103">As an alternative to compiling Visual Basic programs from within Visual Studio, you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>

<span data-ttu-id="a118f-104">Le Visual Basic compilateur de ligne de commande prend en charge un ensemble complet d’options qui contrôlent les fichiers d’entrée et de sortie, les assemblys, ainsi que les options de débogage et de préprocesseur.</span><span class="sxs-lookup"><span data-stu-id="a118f-104">The Visual Basic command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="a118f-105">Chaque option est disponible dans deux formulaires interchangeables : `-option` et `/option` .</span><span class="sxs-lookup"><span data-stu-id="a118f-105">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="a118f-106">Cette documentation affiche uniquement le `-option` formulaire.</span><span class="sxs-lookup"><span data-stu-id="a118f-106">This documentation shows only the `-option` form.</span></span>

<span data-ttu-id="a118f-107">Le tableau suivant répertorie quelques exemples de lignes de commande que vous pouvez modifier pour votre propre usage.</span><span class="sxs-lookup"><span data-stu-id="a118f-107">The following table lists some sample command lines you can modify for your own use.</span></span>

|<span data-ttu-id="a118f-108">À</span><span class="sxs-lookup"><span data-stu-id="a118f-108">To</span></span>|<span data-ttu-id="a118f-109">Utilisation</span><span class="sxs-lookup"><span data-stu-id="a118f-109">Use</span></span>|
|--------|---------|
|<span data-ttu-id="a118f-110">Compiler file. vb et créer file. exe</span><span class="sxs-lookup"><span data-stu-id="a118f-110">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|
|<span data-ttu-id="a118f-111">Compiler file. vb et créer file. dll</span><span class="sxs-lookup"><span data-stu-id="a118f-111">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|
|<span data-ttu-id="a118f-112">Compiler file. vb et créer My. exe</span><span class="sxs-lookup"><span data-stu-id="a118f-112">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|
|<span data-ttu-id="a118f-113">Compiler file. vb et créer une bibliothèque et un assembly de référence nommé file. dll</span><span class="sxs-lookup"><span data-stu-id="a118f-113">Compile File.vb and create both a library and a reference assembly named File.dll</span></span>|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|<span data-ttu-id="a118f-114">Compiler tous les fichiers Visual Basic dans le répertoire actif, avec les optimisations sur et le `DEBUG` symbole défini, générant fichier2. exe</span><span class="sxs-lookup"><span data-stu-id="a118f-114">Compile all Visual Basic files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|
|<span data-ttu-id="a118f-115">Compilez tous les fichiers Visual Basic dans le répertoire actif, en générant une version de débogage du fichier fichier2. dll sans afficher le logo ou les avertissements</span><span class="sxs-lookup"><span data-stu-id="a118f-115">Compile all Visual Basic files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|
|<span data-ttu-id="a118f-116">Compiler tous les fichiers Visual Basic du répertoire actif dans un fichier. dll</span><span class="sxs-lookup"><span data-stu-id="a118f-116">Compile all Visual Basic files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|

> [!TIP]
> <span data-ttu-id="a118f-117">Quand vous générez un projet à l’aide de l’IDE de Visual Studio, vous pouvez afficher des informations sur la commande **vbc** associée avec ses options de compilateur dans la fenêtre sortie.</span><span class="sxs-lookup"><span data-stu-id="a118f-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="a118f-118">Pour afficher ces informations, ouvrez la [boîte de dialogue Options, projets et solutions, générer et exécuter](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), puis définissez le niveau de détail de la **sortie de génération du projet MSBuild** sur **normal** ou sur un niveau de détail plus élevé.</span><span class="sxs-lookup"><span data-stu-id="a118f-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span>

## <a name="see-also"></a><span data-ttu-id="a118f-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a118f-119">See also</span></span>

- [<span data-ttu-id="a118f-120">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a118f-120">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="a118f-121">Compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="a118f-121">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
