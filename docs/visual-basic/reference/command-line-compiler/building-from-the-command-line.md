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
# <a name="building-from-the-command-line-visual-basic"></a><span data-ttu-id="e89be-102">Génération à partir de la ligne de commande (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e89be-102">Building from the Command Line (Visual Basic)</span></span>

<span data-ttu-id="e89be-103">Un projet de Visual Basic est constitué d’un ou de plusieurs fichiers sources distincts.</span><span class="sxs-lookup"><span data-stu-id="e89be-103">A Visual Basic project is made up of one or more separate source files.</span></span> <span data-ttu-id="e89be-104">Pendant le processus appelé compilation, ces fichiers sont rassemblés dans un package, un fichier exécutable unique qui peut être exécuté en tant qu’application.</span><span class="sxs-lookup"><span data-stu-id="e89be-104">During the process known as compilation, these files are brought together into one package—a single executable file that can be run as an application.</span></span>

<span data-ttu-id="e89be-105">Visual Basic fournit un compilateur de ligne de commande comme alternative à la compilation de programmes à partir de l’environnement de développement intégré (IDE) de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e89be-105">Visual Basic provides a command-line compiler as an alternative to compiling programs from within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="e89be-106">Le compilateur de ligne de commande est conçu pour les situations dans lesquelles vous n’avez pas besoin de l’ensemble complet des fonctionnalités de l’IDE, par exemple lorsque vous utilisez ou écrivez pour des ordinateurs avec une mémoire système ou un espace de stockage limité.</span><span class="sxs-lookup"><span data-stu-id="e89be-106">The command-line compiler is designed for situations in which you do not require the full set of features in the IDE—for example, when you are using or writing for computers with limited system memory or storage space.</span></span>

<span data-ttu-id="e89be-107">Pour compiler les fichiers sources à partir de l’IDE de Visual Studio, choisissez la commande **générer** dans le menu **générer** .</span><span class="sxs-lookup"><span data-stu-id="e89be-107">To compile source files from within the Visual Studio IDE, choose the **Build** command from the **Build** menu.</span></span>

> [!TIP]
> <span data-ttu-id="e89be-108">Quand vous générez des fichiers projet à l’aide de l’IDE de Visual Studio, vous pouvez afficher des informations sur la commande **vbc** associée et ses commutateurs dans la fenêtre sortie.</span><span class="sxs-lookup"><span data-stu-id="e89be-108">When you build project files by using the Visual Studio IDE, you can display information about the associated **vbc** command and its switches in the output window.</span></span> <span data-ttu-id="e89be-109">Pour afficher ces informations, ouvrez la [boîte de dialogue Options, projets et solutions, générer et exécuter](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), puis définissez le niveau de détail de la **sortie de génération du projet MSBuild** sur **normal** ou sur un niveau de détail plus élevé.</span><span class="sxs-lookup"><span data-stu-id="e89be-109">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="e89be-110">Pour plus d’informations, consultez [Comment : afficher, enregistrer et configurer des fichiers journaux de génération](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).</span><span class="sxs-lookup"><span data-stu-id="e89be-110">For more information, see [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).</span></span>

<span data-ttu-id="e89be-111">Vous pouvez compiler des fichiers projet (. vbproj) à partir d’une invite de commandes à l’aide de MSBuild.</span><span class="sxs-lookup"><span data-stu-id="e89be-111">You can compile project (.vbproj) files at a command prompt by using MSBuild.</span></span> <span data-ttu-id="e89be-112">Pour plus d’informations, consultez informations de [référence sur la ligne de commande](/visualstudio/msbuild/msbuild-command-line-reference) et [procédure pas à pas : utilisation de MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span><span class="sxs-lookup"><span data-stu-id="e89be-112">For more information, see [Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) and [Walkthrough: Using MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e89be-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="e89be-113">In This Section</span></span>

<span data-ttu-id="e89be-114">[Comment : appeler le compilateur de ligne de commande](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) </span><span class="sxs-lookup"><span data-stu-id="e89be-114">[How to: Invoke the Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) </span></span>\
<span data-ttu-id="e89be-115">Décrit comment appeler le compilateur de ligne de commande à l’invite MS-DOS ou à partir d’un sous-répertoire spécifique.</span><span class="sxs-lookup"><span data-stu-id="e89be-115">Describes how to invoke the command-line compiler at the MS-DOS prompt or from a specific subdirectory.</span></span>

<span data-ttu-id="e89be-116">[Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="e89be-116">[Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>\
<span data-ttu-id="e89be-117">Fournit une liste d’exemples de lignes de commande que vous pouvez modifier pour votre propre usage.</span><span class="sxs-lookup"><span data-stu-id="e89be-117">Provides a list of sample command lines that you can modify for your own use.</span></span>

## <a name="related-sections"></a><span data-ttu-id="e89be-118">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="e89be-118">Related Sections</span></span>

<span data-ttu-id="e89be-119">[Visual Basic du compilateur de ligne de commande](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="e89be-119">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>\
<span data-ttu-id="e89be-120">Fournit des listes d’options du compilateur classées par ordre alphabétique ou par objectif.</span><span class="sxs-lookup"><span data-stu-id="e89be-120">Provides lists of compiler options, organized alphabetically or by purpose.</span></span>

<span data-ttu-id="e89be-121">[Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span><span class="sxs-lookup"><span data-stu-id="e89be-121">[Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span></span>\
<span data-ttu-id="e89be-122">Décrit comment compiler des sections de code particulières.</span><span class="sxs-lookup"><span data-stu-id="e89be-122">Describes how to compile particular sections of code.</span></span>

<span data-ttu-id="e89be-123">[Génération et nettoyage de projets et de solutions dans Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) </span><span class="sxs-lookup"><span data-stu-id="e89be-123">[Building and Cleaning Projects and Solutions in Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) </span></span>\
<span data-ttu-id="e89be-124">Décrit comment organiser ce qui sera inclus dans les différentes builds, choisir des propriétés de projet et vérifier que les projets sont générés dans le bon ordre.</span><span class="sxs-lookup"><span data-stu-id="e89be-124">Describes how to organize what will be included in different builds, choose project properties, and ensure that projects build in the correct order.</span></span>
