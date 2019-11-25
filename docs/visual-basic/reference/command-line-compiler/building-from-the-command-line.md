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
# <a name="building-from-the-command-line-visual-basic"></a><span data-ttu-id="33346-102">Génération à partir de la ligne de commande (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33346-102">Building from the Command Line (Visual Basic)</span></span>

<span data-ttu-id="33346-103">A Visual Basic project is made up of one or more separate source files.</span><span class="sxs-lookup"><span data-stu-id="33346-103">A Visual Basic project is made up of one or more separate source files.</span></span> <span data-ttu-id="33346-104">During the process known as compilation, these files are brought together into one package—a single executable file that can be run as an application.</span><span class="sxs-lookup"><span data-stu-id="33346-104">During the process known as compilation, these files are brought together into one package—a single executable file that can be run as an application.</span></span>

<span data-ttu-id="33346-105">Visual Basic provides a command-line compiler as an alternative to compiling programs from within the Visual Studio integrated development environment (IDE).</span><span class="sxs-lookup"><span data-stu-id="33346-105">Visual Basic provides a command-line compiler as an alternative to compiling programs from within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="33346-106">The command-line compiler is designed for situations in which you do not require the full set of features in the IDE—for example, when you are using or writing for computers with limited system memory or storage space.</span><span class="sxs-lookup"><span data-stu-id="33346-106">The command-line compiler is designed for situations in which you do not require the full set of features in the IDE—for example, when you are using or writing for computers with limited system memory or storage space.</span></span>

<span data-ttu-id="33346-107">To compile source files from within the Visual Studio IDE, choose the **Build** command from the **Build** menu.</span><span class="sxs-lookup"><span data-stu-id="33346-107">To compile source files from within the Visual Studio IDE, choose the **Build** command from the **Build** menu.</span></span>

> [!TIP]
> <span data-ttu-id="33346-108">When you build project files by using the Visual Studio IDE, you can display information about the associated **vbc** command and its switches in the output window.</span><span class="sxs-lookup"><span data-stu-id="33346-108">When you build project files by using the Visual Studio IDE, you can display information about the associated **vbc** command and its switches in the output window.</span></span> <span data-ttu-id="33346-109">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span><span class="sxs-lookup"><span data-stu-id="33346-109">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="33346-110">Pour plus d’informations, consultez l’article [Comment : afficher, enregistrer et configurer des fichiers journaux de génération](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).</span><span class="sxs-lookup"><span data-stu-id="33346-110">For more information, see [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).</span></span>

<span data-ttu-id="33346-111">You can compile project (.vbproj) files at a command prompt by using MSBuild.</span><span class="sxs-lookup"><span data-stu-id="33346-111">You can compile project (.vbproj) files at a command prompt by using MSBuild.</span></span> <span data-ttu-id="33346-112">For more information, see [Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) and [Walkthrough: Using MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span><span class="sxs-lookup"><span data-stu-id="33346-112">For more information, see [Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) and [Walkthrough: Using MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="33346-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="33346-113">In This Section</span></span>

<span data-ttu-id="33346-114">[How to: Invoke the Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) </span><span class="sxs-lookup"><span data-stu-id="33346-114">[How to: Invoke the Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) </span></span>\
<span data-ttu-id="33346-115">Describes how to invoke the command-line compiler at the MS-DOS prompt or from a specific subdirectory.</span><span class="sxs-lookup"><span data-stu-id="33346-115">Describes how to invoke the command-line compiler at the MS-DOS prompt or from a specific subdirectory.</span></span>

<span data-ttu-id="33346-116">[Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="33346-116">[Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>\
<span data-ttu-id="33346-117">Provides a list of sample command lines that you can modify for your own use.</span><span class="sxs-lookup"><span data-stu-id="33346-117">Provides a list of sample command lines that you can modify for your own use.</span></span>

## <a name="related-sections"></a><span data-ttu-id="33346-118">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="33346-118">Related Sections</span></span>

<span data-ttu-id="33346-119">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="33346-119">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>\
<span data-ttu-id="33346-120">Provides lists of compiler options, organized alphabetically or by purpose.</span><span class="sxs-lookup"><span data-stu-id="33346-120">Provides lists of compiler options, organized alphabetically or by purpose.</span></span>

<span data-ttu-id="33346-121">[Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span><span class="sxs-lookup"><span data-stu-id="33346-121">[Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span></span>\
<span data-ttu-id="33346-122">Describes how to compile particular sections of code.</span><span class="sxs-lookup"><span data-stu-id="33346-122">Describes how to compile particular sections of code.</span></span>

<span data-ttu-id="33346-123">[Génération et nettoyage de solutions et de projets dans Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) </span><span class="sxs-lookup"><span data-stu-id="33346-123">[Building and Cleaning Projects and Solutions in Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) </span></span>\
<span data-ttu-id="33346-124">Describes how to organize what will be included in different builds, choose project properties, and ensure that projects build in the correct order.</span><span class="sxs-lookup"><span data-stu-id="33346-124">Describes how to organize what will be included in different builds, choose project properties, and ensure that projects build in the correct order.</span></span>
