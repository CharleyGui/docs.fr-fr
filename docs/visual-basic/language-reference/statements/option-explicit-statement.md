---
title: Option Explicit (instruction)
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
ms.openlocfilehash: 44bf8205ec071710ee3660968ab3c3e9af33f74d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874942"
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="272e5-102">Option Explicit, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="272e5-102">Option Explicit Statement (Visual Basic)</span></span>

<span data-ttu-id="272e5-103">Force la déclaration explicite de toutes les variables dans un fichier ou autorise les déclarations implicites de variables.</span><span class="sxs-lookup"><span data-stu-id="272e5-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="272e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="272e5-104">Syntax</span></span>  
  
```vb  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="272e5-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="272e5-105">Parts</span></span>  

 `On`  
 <span data-ttu-id="272e5-106">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="272e5-106">Optional.</span></span> <span data-ttu-id="272e5-107">Active la `Option Explicit` vérification.</span><span class="sxs-lookup"><span data-stu-id="272e5-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="272e5-108">Si `On` ou `Off` n’est pas spécifié, la valeur par défaut est `On` .</span><span class="sxs-lookup"><span data-stu-id="272e5-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="272e5-109">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="272e5-109">Optional.</span></span> <span data-ttu-id="272e5-110">Désactive la `Option Explicit` vérification.</span><span class="sxs-lookup"><span data-stu-id="272e5-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="272e5-111">Notes</span><span class="sxs-lookup"><span data-stu-id="272e5-111">Remarks</span></span>  

 <span data-ttu-id="272e5-112">Lorsque `Option Explicit On` ou `Option Explicit` apparaît dans un fichier, vous devez déclarer explicitement toutes les variables à l’aide des `Dim` `ReDim` instructions ou.</span><span class="sxs-lookup"><span data-stu-id="272e5-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="272e5-113">Si vous essayez d’utiliser un nom de variable non déclaré, une erreur se produit au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="272e5-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="272e5-114">L' `Option Explicit Off` instruction autorise la déclaration implicite de variables.</span><span class="sxs-lookup"><span data-stu-id="272e5-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="272e5-115">Si elle est utilisée, l'instruction `Option Explicit` doit apparaître dans un fichier avant toute autre instruction de code source.</span><span class="sxs-lookup"><span data-stu-id="272e5-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="272e5-116">`Option Explicit`La définition de `Off` la valeur n’est généralement pas une bonne pratique.</span><span class="sxs-lookup"><span data-stu-id="272e5-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="272e5-117">Vous risquez de mal orthographier un nom de variable dans un ou plusieurs emplacements, ce qui peut provoquer des résultats inattendus lors de l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="272e5-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="272e5-118">Lorsqu’une instruction Option Explicit n’est pas présente</span><span class="sxs-lookup"><span data-stu-id="272e5-118">When an Option Explicit Statement Is Not Present</span></span>  

 <span data-ttu-id="272e5-119">Si le code source ne contient pas d' `Option Explicit` instruction, le paramètre **Option Explicit** sur la [page compiler, concepteur de projets (Visual Basic),](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) est utilisé.</span><span class="sxs-lookup"><span data-stu-id="272e5-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="272e5-120">Si le compilateur de ligne de commande est utilisé, l’option [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) du compilateur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="272e5-120">If the command-line compiler is used, the [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="272e5-121">Pour définir l’option Explicit dans l’IDE</span><span class="sxs-lookup"><span data-stu-id="272e5-121">To set Option Explicit in the IDE</span></span>  
  
1. <span data-ttu-id="272e5-122">Dans **Explorateur de solutions**, sélectionnez un projet.</span><span class="sxs-lookup"><span data-stu-id="272e5-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="272e5-123">Dans le menu **Projet** , cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="272e5-123">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="272e5-124">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="272e5-124">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="272e5-125">Définissez la valeur dans la zone **Option Explicit** .</span><span class="sxs-lookup"><span data-stu-id="272e5-125">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="272e5-126">Lorsque vous créez un projet, le paramètre **Option Explicit** de l’onglet **compiler** est défini sur le paramètre **Option Explicit** dans la boîte de dialogue **valeurs par défaut VB** .</span><span class="sxs-lookup"><span data-stu-id="272e5-126">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="272e5-127">Pour accéder à la boîte de dialogue **valeurs par défaut VB** , dans le menu **Outils** , cliquez sur **options**.</span><span class="sxs-lookup"><span data-stu-id="272e5-127">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="272e5-128">Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**.</span><span class="sxs-lookup"><span data-stu-id="272e5-128">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="272e5-129">Le paramètre par défaut initial dans les **valeurs par défaut VB** est `On` .</span><span class="sxs-lookup"><span data-stu-id="272e5-129">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="272e5-130">Pour définir l’option Explicit sur la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="272e5-130">To set Option Explicit on the command line</span></span>  
  
- <span data-ttu-id="272e5-131">Incluez l’option [de compilateur-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) dans la commande **vbc** .</span><span class="sxs-lookup"><span data-stu-id="272e5-131">Include the [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="272e5-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="272e5-132">Example</span></span>  

 <span data-ttu-id="272e5-133">L’exemple suivant utilise l' `Option Explicit` instruction pour forcer la déclaration explicite de toutes les variables.</span><span class="sxs-lookup"><span data-stu-id="272e5-133">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="272e5-134">Toute tentative d’utilisation d’une variable non déclarée génère une erreur au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="272e5-134">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a><span data-ttu-id="272e5-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="272e5-135">See also</span></span>

- [<span data-ttu-id="272e5-136">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="272e5-136">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="272e5-137">ReDim (instruction)</span><span class="sxs-lookup"><span data-stu-id="272e5-137">ReDim Statement</span></span>](redim-statement.md)
- [<span data-ttu-id="272e5-138">Option Compare, instruction</span><span class="sxs-lookup"><span data-stu-id="272e5-138">Option Compare Statement</span></span>](option-compare-statement.md)
- [<span data-ttu-id="272e5-139">Option Strict Statement</span><span class="sxs-lookup"><span data-stu-id="272e5-139">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="272e5-140">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="272e5-140">-optioncompare</span></span>](../../reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="272e5-141">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="272e5-141">-optionexplicit</span></span>](../../reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="272e5-142">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="272e5-142">-optionstrict</span></span>](../../reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="272e5-143">Valeurs par défaut VB, Projets, boîte de dialogue Options</span><span class="sxs-lookup"><span data-stu-id="272e5-143">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
