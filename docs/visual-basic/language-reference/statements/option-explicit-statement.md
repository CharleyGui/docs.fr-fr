---
title: Option Explicit, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
helpviewer_keywords:
- declaring variables [Visual Basic], explicit
- forced variable declaration in Option Explicit statement [Visual Basic]
- Explicit keyword
- explicit variable declaration
- Option Explicit statement [Visual Basic]
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
ms.openlocfilehash: 3c70d958fdcbb1782af22c3a4715676abbeeac0c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353783"
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="5c0a6-102">Option Explicit, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c0a6-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="5c0a6-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c0a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c0a6-104">Syntax</span></span>  
  
```vb  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="5c0a6-105">Composants</span><span class="sxs-lookup"><span data-stu-id="5c0a6-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="5c0a6-106">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-106">Optional.</span></span> <span data-ttu-id="5c0a6-107">Enables `Option Explicit` checking.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="5c0a6-108">If `On` or `Off` is not specified, the default is `On`.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="5c0a6-109">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-109">Optional.</span></span> <span data-ttu-id="5c0a6-110">Disables `Option Explicit` checking.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c0a6-111">Notes</span><span class="sxs-lookup"><span data-stu-id="5c0a6-111">Remarks</span></span>  
 <span data-ttu-id="5c0a6-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="5c0a6-113">If you try to use an undeclared variable name, an error occurs at compile time.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="5c0a6-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="5c0a6-115">Si elle est utilisée, l'instruction `Option Explicit` doit apparaître dans un fichier avant toute autre instruction de code source.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5c0a6-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="5c0a6-117">Vous risquez de mal orthographier un nom de variable dans un ou plusieurs emplacements, ce qui peut provoquer des résultats inattendus lors de l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="5c0a6-118">When an Option Explicit Statement Is Not Present</span><span class="sxs-lookup"><span data-stu-id="5c0a6-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="5c0a6-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="5c0a6-120">If the command-line compiler is used, the [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-120">If the command-line compiler is used, the [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="5c0a6-121">To set Option Explicit in the IDE</span><span class="sxs-lookup"><span data-stu-id="5c0a6-121">To set Option Explicit in the IDE</span></span>  
  
1. <span data-ttu-id="5c0a6-122">Dans l’**Explorateur de solutions**, sélectionnez un projet.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="5c0a6-123">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-123">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="5c0a6-124">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-124">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="5c0a6-125">Set the value in the **Option Explicit** box.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-125">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="5c0a6-126">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-126">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="5c0a6-127">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-127">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="5c0a6-128">Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-128">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="5c0a6-129">The initial default setting in **VB Defaults** is `On`.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-129">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="5c0a6-130">To set Option Explicit on the command line</span><span class="sxs-lookup"><span data-stu-id="5c0a6-130">To set Option Explicit on the command line</span></span>  
  
- <span data-ttu-id="5c0a6-131">Include the [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-131">Include the [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c0a6-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="5c0a6-132">Example</span></span>  
 <span data-ttu-id="5c0a6-133">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-133">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="5c0a6-134">Attempting to use an undeclared variable causes an error at compile time.</span><span class="sxs-lookup"><span data-stu-id="5c0a6-134">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a><span data-ttu-id="5c0a6-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c0a6-135">See also</span></span>

- [<span data-ttu-id="5c0a6-136">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="5c0a6-136">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="5c0a6-137">ReDim (instruction)</span><span class="sxs-lookup"><span data-stu-id="5c0a6-137">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="5c0a6-138">Option Compare (instruction)</span><span class="sxs-lookup"><span data-stu-id="5c0a6-138">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="5c0a6-139">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="5c0a6-139">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="5c0a6-140">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="5c0a6-140">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="5c0a6-141">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="5c0a6-141">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="5c0a6-142">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="5c0a6-142">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="5c0a6-143">Valeurs par défaut VB, Projets, boîte de dialogue Options</span><span class="sxs-lookup"><span data-stu-id="5c0a6-143">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
