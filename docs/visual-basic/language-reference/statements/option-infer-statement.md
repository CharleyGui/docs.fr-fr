---
title: Instruction Option Infer
ms.date: 07/20/2015
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
ms.openlocfilehash: 53bc9d41f28f63061db2012395480aa6be7515dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346494"
---
# <a name="option-infer-statement"></a><span data-ttu-id="a51cb-102">Instruction Option Infer</span><span class="sxs-lookup"><span data-stu-id="a51cb-102">Option Infer Statement</span></span>

<span data-ttu-id="a51cb-103">Permet l'utilisation de l'inférence de type de variable locale dans les variables déclaratives.</span><span class="sxs-lookup"><span data-stu-id="a51cb-103">Enables the use of local type inference in declaring variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="a51cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a51cb-104">Syntax</span></span>

```vb
Option Infer { On | Off }
```

## <a name="parts"></a><span data-ttu-id="a51cb-105">Composants</span><span class="sxs-lookup"><span data-stu-id="a51cb-105">Parts</span></span>

|<span data-ttu-id="a51cb-106">Terme</span><span class="sxs-lookup"><span data-stu-id="a51cb-106">Term</span></span>|<span data-ttu-id="a51cb-107">Définition</span><span class="sxs-lookup"><span data-stu-id="a51cb-107">Definition</span></span>|
|---|---|
|`On`|<span data-ttu-id="a51cb-108">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="a51cb-108">Optional.</span></span> <span data-ttu-id="a51cb-109">Active l'inférence de type de variable locale.</span><span class="sxs-lookup"><span data-stu-id="a51cb-109">Enables local type inference.</span></span>|
|`Off`|<span data-ttu-id="a51cb-110">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="a51cb-110">Optional.</span></span> <span data-ttu-id="a51cb-111">Désactive l'inférence de type de variable locale.</span><span class="sxs-lookup"><span data-stu-id="a51cb-111">Disables local type inference.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a51cb-112">Notes</span><span class="sxs-lookup"><span data-stu-id="a51cb-112">Remarks</span></span>

<span data-ttu-id="a51cb-113">Pour définir `Option Infer` dans un fichier, tapez `Option Infer On` ou `Option Infer Off` en haut du fichier, avant tout autre code source.</span><span class="sxs-lookup"><span data-stu-id="a51cb-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="a51cb-114">Si la valeur définie pour `Option Infer` dans un fichier est en conflit avec la valeur définie dans l'IDE ou sur la ligne de commande, la valeur contenue dans le fichier est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="a51cb-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>

<span data-ttu-id="a51cb-115">Quand vous affectez à `Option Infer` la valeur `On`, vous pouvez déclarer des variables locales sans déclarer explicitement un type de données.</span><span class="sxs-lookup"><span data-stu-id="a51cb-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="a51cb-116">Le compilateur déduit le type de données d'une variable à partir du type de son expression d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="a51cb-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>

<span data-ttu-id="a51cb-117">Dans l'illustration suivante, `Option Infer` est activé.</span><span class="sxs-lookup"><span data-stu-id="a51cb-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="a51cb-118">La variable contenue dans la déclaration `Dim someVar = 2` est déclarée en tant qu'entier par l'inférence de type.</span><span class="sxs-lookup"><span data-stu-id="a51cb-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>

<span data-ttu-id="a51cb-119">The following screenshot shows IntelliSense when Option Infer is on:</span><span class="sxs-lookup"><span data-stu-id="a51cb-119">The following screenshot shows IntelliSense when Option Infer is on:</span></span>

![Screenshot showing IntelliSense view when Option Infer is on.](./media/option-infer-statement/option-infer-as-integer-on.png)

<span data-ttu-id="a51cb-121">Dans l'illustration suivante, `Option Infer` est désactivé.</span><span class="sxs-lookup"><span data-stu-id="a51cb-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="a51cb-122">La variable contenue dans la déclaration `Dim someVar = 2` est déclarée comme `Object` par l'inférence de type.</span><span class="sxs-lookup"><span data-stu-id="a51cb-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="a51cb-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="a51cb-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>

<span data-ttu-id="a51cb-124">The following screenshot shows IntelliSense when Option Infer is off:</span><span class="sxs-lookup"><span data-stu-id="a51cb-124">The following screenshot shows IntelliSense when Option Infer is off:</span></span>

![Screenshot showing IntelliSense view when Option Infer is off.](./media/option-infer-statement/option-infer-as-object-off.png)

> [!NOTE]
> <span data-ttu-id="a51cb-126">Quand une variable est déclarée comme `Object`, le type au moment de l'exécution peut changer pendant que le programme s'exécute.</span><span class="sxs-lookup"><span data-stu-id="a51cb-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> <span data-ttu-id="a51cb-127">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span><span class="sxs-lookup"><span data-stu-id="a51cb-127">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="a51cb-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](~/_vblang/spec/conversions.md#value-type-conversions).</span><span class="sxs-lookup"><span data-stu-id="a51cb-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](~/_vblang/spec/conversions.md#value-type-conversions).</span></span>

<span data-ttu-id="a51cb-129">L'inférence de type s'applique au niveau de la procédure, mais pas à l'extérieur d'une procédure de classe, de structure, de module ou d'interface.</span><span class="sxs-lookup"><span data-stu-id="a51cb-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>

<span data-ttu-id="a51cb-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="a51cb-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>

## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="a51cb-131">En l'absence d'instruction Option Infer</span><span class="sxs-lookup"><span data-stu-id="a51cb-131">When an Option Infer Statement Is Not Present</span></span>

<span data-ttu-id="a51cb-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span><span class="sxs-lookup"><span data-stu-id="a51cb-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="a51cb-133">If the command-line compiler is used, the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span><span class="sxs-lookup"><span data-stu-id="a51cb-133">If the command-line compiler is used, the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>

#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="a51cb-134">Pour définir Option Infer dans l'IDE</span><span class="sxs-lookup"><span data-stu-id="a51cb-134">To set Option Infer in the IDE</span></span>

1. <span data-ttu-id="a51cb-135">Dans l’**Explorateur de solutions**, sélectionnez un projet.</span><span class="sxs-lookup"><span data-stu-id="a51cb-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="a51cb-136">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="a51cb-136">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="a51cb-137">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="a51cb-137">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="a51cb-138">Set the value in the **Option infer** box.</span><span class="sxs-lookup"><span data-stu-id="a51cb-138">Set the value in the **Option infer** box.</span></span>

<span data-ttu-id="a51cb-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span><span class="sxs-lookup"><span data-stu-id="a51cb-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="a51cb-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span><span class="sxs-lookup"><span data-stu-id="a51cb-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="a51cb-141">Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**.</span><span class="sxs-lookup"><span data-stu-id="a51cb-141">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="a51cb-142">The initial default setting in **VB Defaults** is `On`.</span><span class="sxs-lookup"><span data-stu-id="a51cb-142">The initial default setting in **VB Defaults** is `On`.</span></span>

#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="a51cb-143">Pour définir Option Infer sur la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="a51cb-143">To set Option Infer on the command line</span></span>

<span data-ttu-id="a51cb-144">Include the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span><span class="sxs-lookup"><span data-stu-id="a51cb-144">Include the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>

## <a name="default-data-types-and-values"></a><span data-ttu-id="a51cb-145">Types de données et valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="a51cb-145">Default Data Types and Values</span></span>

<span data-ttu-id="a51cb-146">Le tableau suivant décrit les résultats des diverses combinaisons de spécification du type de données et d'un initialiseur dans une instruction `Dim`.</span><span class="sxs-lookup"><span data-stu-id="a51cb-146">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>

|<span data-ttu-id="a51cb-147">Type de données spécifié ?</span><span class="sxs-lookup"><span data-stu-id="a51cb-147">Data type specified?</span></span>|<span data-ttu-id="a51cb-148">Initialiseur spécifié ?</span><span class="sxs-lookup"><span data-stu-id="a51cb-148">Initializer specified?</span></span>|<span data-ttu-id="a51cb-149">Exemple</span><span class="sxs-lookup"><span data-stu-id="a51cb-149">Example</span></span>|<span data-ttu-id="a51cb-150">Résultat</span><span class="sxs-lookup"><span data-stu-id="a51cb-150">Result</span></span>|
|---|---|---|---|
|<span data-ttu-id="a51cb-151">Non</span><span class="sxs-lookup"><span data-stu-id="a51cb-151">No</span></span>|<span data-ttu-id="a51cb-152">Non</span><span class="sxs-lookup"><span data-stu-id="a51cb-152">No</span></span>|`Dim qty`|<span data-ttu-id="a51cb-153">Si `Option Strict` est désactivé (par défaut), la valeur affectée à la variable est `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="a51cb-153">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="a51cb-154">Si `Option Strict` est activé, une erreur se produit au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="a51cb-154">If `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="a51cb-155">Non</span><span class="sxs-lookup"><span data-stu-id="a51cb-155">No</span></span>|<span data-ttu-id="a51cb-156">Oui</span><span class="sxs-lookup"><span data-stu-id="a51cb-156">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="a51cb-157">Si `Option Infer` est activée (par défaut), la variable prend le type de données de l'initialiseur.</span><span class="sxs-lookup"><span data-stu-id="a51cb-157">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="a51cb-158">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="a51cb-158">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="a51cb-159">Si `Option Infer` est désactivé et que `Option Strict` est désactivé, la variable prend le type de données de `Object`.</span><span class="sxs-lookup"><span data-stu-id="a51cb-159">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="a51cb-160">Si `Option Infer` est désactivé et que `Option Strict` est activé, une erreur se produit au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="a51cb-160">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="a51cb-161">Oui</span><span class="sxs-lookup"><span data-stu-id="a51cb-161">Yes</span></span>|<span data-ttu-id="a51cb-162">Non</span><span class="sxs-lookup"><span data-stu-id="a51cb-162">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="a51cb-163">La variable est initialisée avec la valeur par défaut du type de données.</span><span class="sxs-lookup"><span data-stu-id="a51cb-163">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="a51cb-164">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a51cb-164">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|
|<span data-ttu-id="a51cb-165">Oui</span><span class="sxs-lookup"><span data-stu-id="a51cb-165">Yes</span></span>|<span data-ttu-id="a51cb-166">Oui</span><span class="sxs-lookup"><span data-stu-id="a51cb-166">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="a51cb-167">Si le type de données de l’initialiseur ne peut pas être converti dans le type de données spécifié, une erreur se produit au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="a51cb-167">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|

## <a name="example"></a><span data-ttu-id="a51cb-168">Exemple</span><span class="sxs-lookup"><span data-stu-id="a51cb-168">Example</span></span>

<span data-ttu-id="a51cb-169">Les exemples suivants montrent comment l'instruction `Option Infer` active l'inférence de type de variable locale.</span><span class="sxs-lookup"><span data-stu-id="a51cb-169">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>

[!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]

## <a name="example"></a><span data-ttu-id="a51cb-170">Exemple</span><span class="sxs-lookup"><span data-stu-id="a51cb-170">Example</span></span>

<span data-ttu-id="a51cb-171">L'exemple suivant montre que le type au moment de l'exécution peut être différent quand une variable est identifiée comme `Object`.</span><span class="sxs-lookup"><span data-stu-id="a51cb-171">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>

[!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]

## <a name="see-also"></a><span data-ttu-id="a51cb-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a51cb-172">See also</span></span>

- [<span data-ttu-id="a51cb-173">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="a51cb-173">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="a51cb-174">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="a51cb-174">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="a51cb-175">Option Compare (instruction)</span><span class="sxs-lookup"><span data-stu-id="a51cb-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="a51cb-176">Option Explicit (instruction)</span><span class="sxs-lookup"><span data-stu-id="a51cb-176">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="a51cb-177">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="a51cb-177">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="a51cb-178">Valeurs par défaut VB, Projets, boîte de dialogue Options</span><span class="sxs-lookup"><span data-stu-id="a51cb-178">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="a51cb-179">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="a51cb-179">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="a51cb-180">Conversion boxing et unboxing</span><span class="sxs-lookup"><span data-stu-id="a51cb-180">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
