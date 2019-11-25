---
title: 'Comment : appeler le compilateur de ligne de commande'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: 3b34ebba68c9c9b2a8335822d0ffaef2a9b06d7c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344257"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="57d6a-102">Comment : appeler le compilateur de ligne de commande (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57d6a-102">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>

<span data-ttu-id="57d6a-103">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span><span class="sxs-lookup"><span data-stu-id="57d6a-103">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="57d6a-104">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span><span class="sxs-lookup"><span data-stu-id="57d6a-104">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="57d6a-105">To override this default behavior, you can either use the Developer Command Prompt for Visual Studio, or modify the PATH environment variable.</span><span class="sxs-lookup"><span data-stu-id="57d6a-105">To override this default behavior, you can either use the Developer Command Prompt for Visual Studio, or modify the PATH environment variable.</span></span> <span data-ttu-id="57d6a-106">Both allow you to compile from any directory by simply typing the compiler name.</span><span class="sxs-lookup"><span data-stu-id="57d6a-106">Both allow you to compile from any directory by simply typing the compiler name.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a><span data-ttu-id="57d6a-107">To invoke the compiler using the Developer Command Prompt for Visual Studio</span><span class="sxs-lookup"><span data-stu-id="57d6a-107">To invoke the compiler using the Developer Command Prompt for Visual Studio</span></span>

1. <span data-ttu-id="57d6a-108">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span><span class="sxs-lookup"><span data-stu-id="57d6a-108">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>

2. <span data-ttu-id="57d6a-109">You can use the Developer Command Prompt for Visual Studio to access the compiler from any directory on your machine, if Visual Studio is installed.</span><span class="sxs-lookup"><span data-stu-id="57d6a-109">You can use the Developer Command Prompt for Visual Studio to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>

3. <span data-ttu-id="57d6a-110">Invoke the Developer Command Prompt for Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="57d6a-110">Invoke the Developer Command Prompt for Visual Studio.</span></span>

4. <span data-ttu-id="57d6a-111">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span><span class="sxs-lookup"><span data-stu-id="57d6a-111">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>

    <span data-ttu-id="57d6a-112">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span><span class="sxs-lookup"><span data-stu-id="57d6a-112">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="57d6a-113">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="57d6a-113">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="57d6a-114">To set the PATH environment variable to the compiler for the Windows Command Prompt</span><span class="sxs-lookup"><span data-stu-id="57d6a-114">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>

1. <span data-ttu-id="57d6a-115">Use the Windows Search feature to find Vbc.exe on your local disk.</span><span class="sxs-lookup"><span data-stu-id="57d6a-115">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>

    <span data-ttu-id="57d6a-116">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span><span class="sxs-lookup"><span data-stu-id="57d6a-116">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span></span> <span data-ttu-id="57d6a-117">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span><span class="sxs-lookup"><span data-stu-id="57d6a-117">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span></span>

2. <span data-ttu-id="57d6a-118">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span><span class="sxs-lookup"><span data-stu-id="57d6a-118">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>

3. <span data-ttu-id="57d6a-119">Click the **Advanced** tab, and then click **Environment Variables**.</span><span class="sxs-lookup"><span data-stu-id="57d6a-119">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>

4. <span data-ttu-id="57d6a-120">In the **System** variables pane, select **Path** from the list and click **Edit**.</span><span class="sxs-lookup"><span data-stu-id="57d6a-120">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>

5. <span data-ttu-id="57d6a-121">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span><span class="sxs-lookup"><span data-stu-id="57d6a-121">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>

6. <span data-ttu-id="57d6a-122">Click **OK** to confirm your edits and close the dialog boxes.</span><span class="sxs-lookup"><span data-stu-id="57d6a-122">Click **OK** to confirm your edits and close the dialog boxes.</span></span>

     <span data-ttu-id="57d6a-123">After you change the PATH environment variable, you can run the Visual Basic compiler at the Windows Command Prompt from any directory on the computer.</span><span class="sxs-lookup"><span data-stu-id="57d6a-123">After you change the PATH environment variable, you can run the Visual Basic compiler at the Windows Command Prompt from any directory on the computer.</span></span>

## <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="57d6a-124">To invoke the compiler using the Windows Command Prompt</span><span class="sxs-lookup"><span data-stu-id="57d6a-124">To invoke the compiler using the Windows Command Prompt</span></span>

1. <span data-ttu-id="57d6a-125">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span><span class="sxs-lookup"><span data-stu-id="57d6a-125">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>

2. <span data-ttu-id="57d6a-126">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span><span class="sxs-lookup"><span data-stu-id="57d6a-126">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>

     <span data-ttu-id="57d6a-127">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span><span class="sxs-lookup"><span data-stu-id="57d6a-127">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="57d6a-128">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="57d6a-128">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="see-also"></a><span data-ttu-id="57d6a-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57d6a-129">See also</span></span>

- [<span data-ttu-id="57d6a-130">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57d6a-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="57d6a-131">Compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="57d6a-131">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
