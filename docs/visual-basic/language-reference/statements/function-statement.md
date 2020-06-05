---
title: Function (instruction)
ms.date: 05/12/2018
f1_keywords:
- vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
ms.openlocfilehash: 49cf4fead2c5594b7ac6815f82fea0dc995ea436
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404626"
---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="0a4e6-102">Function, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a4e6-102">Function Statement (Visual Basic)</span></span>

<span data-ttu-id="0a4e6-103">Déclare le nom, les paramètres et le code qui définissent une `Function` procédure.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="0a4e6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a4e6-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a><span data-ttu-id="0a4e6-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="0a4e6-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="0a4e6-106">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-106">Optional.</span></span> <span data-ttu-id="0a4e6-107">Consultez la [liste des attributs](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e6-107">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="0a4e6-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-108">Optional.</span></span> <span data-ttu-id="0a4e6-109">Il peut s'agir d'une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="0a4e6-109">Can be one of the following:</span></span>

  - [<span data-ttu-id="0a4e6-110">Public</span><span class="sxs-lookup"><span data-stu-id="0a4e6-110">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="0a4e6-111">Protect</span><span class="sxs-lookup"><span data-stu-id="0a4e6-111">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="0a4e6-112">Contact</span><span class="sxs-lookup"><span data-stu-id="0a4e6-112">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="0a4e6-113">Privé</span><span class="sxs-lookup"><span data-stu-id="0a4e6-113">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="0a4e6-114">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="0a4e6-114">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="0a4e6-115">Protégé privé</span><span class="sxs-lookup"><span data-stu-id="0a4e6-115">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="0a4e6-116">Consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e6-116">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="0a4e6-117">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-117">Optional.</span></span> <span data-ttu-id="0a4e6-118">Il peut s'agir d'une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="0a4e6-118">Can be one of the following:</span></span>

  - [<span data-ttu-id="0a4e6-119">Surcharges</span><span class="sxs-lookup"><span data-stu-id="0a4e6-119">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="0a4e6-120">Remplacements</span><span class="sxs-lookup"><span data-stu-id="0a4e6-120">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="0a4e6-121">Overridable</span><span class="sxs-lookup"><span data-stu-id="0a4e6-121">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="0a4e6-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="0a4e6-122">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="0a4e6-123">MustOverride</span><span class="sxs-lookup"><span data-stu-id="0a4e6-123">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="0a4e6-124">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-124">Optional.</span></span> <span data-ttu-id="0a4e6-125">Consultez [partagé](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e6-125">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="0a4e6-126">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-126">Optional.</span></span> <span data-ttu-id="0a4e6-127">Consultez [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e6-127">See [Shadows](../modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="0a4e6-128">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-128">Optional.</span></span> <span data-ttu-id="0a4e6-129">Consultez [Async](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e6-129">See [Async](../modifiers/async.md).</span></span>

- `Iterator`

  <span data-ttu-id="0a4e6-130">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-130">Optional.</span></span> <span data-ttu-id="0a4e6-131">Consultez [iterator](../modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e6-131">See [Iterator](../modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="0a4e6-132">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-132">Required.</span></span> <span data-ttu-id="0a4e6-133">Nom de la procédure.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-133">Name of the procedure.</span></span> <span data-ttu-id="0a4e6-134">Consultez [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e6-134">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="0a4e6-135">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-135">Optional.</span></span> <span data-ttu-id="0a4e6-136">Liste des paramètres de type pour une procédure générique.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-136">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="0a4e6-137">Consultez la [liste des types](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e6-137">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="0a4e6-138">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-138">Optional.</span></span> <span data-ttu-id="0a4e6-139">Liste des noms de variables locales représentant les paramètres de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-139">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="0a4e6-140">Consultez la [liste des paramètres](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e6-140">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="0a4e6-141">Obligatoire si `Option Strict` est `On` .</span><span class="sxs-lookup"><span data-stu-id="0a4e6-141">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="0a4e6-142">Type de données de la valeur retournée par cette procédure.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-142">Data type of the value returned by this procedure.</span></span>

- `Implements`

  <span data-ttu-id="0a4e6-143">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-143">Optional.</span></span> <span data-ttu-id="0a4e6-144">Indique que cette procédure implémente une ou plusieurs `Function` procédures, chacune d’elles étant définie dans une interface implémentée par la classe ou la structure conteneur de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-144">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="0a4e6-145">Consultez [Implements, instruction](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e6-145">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="0a4e6-146">Obligatoire si `Implements` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-146">Required if `Implements` is supplied.</span></span> <span data-ttu-id="0a4e6-147">Liste des procédures `Function` en cours d'implémentation.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-147">List of `Function` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="0a4e6-148">Chaque `implementedprocedure` emploie la syntaxe et les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="0a4e6-148">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="0a4e6-149">Élément</span><span class="sxs-lookup"><span data-stu-id="0a4e6-149">Part</span></span>|<span data-ttu-id="0a4e6-150">Description</span><span class="sxs-lookup"><span data-stu-id="0a4e6-150">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="0a4e6-151">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-151">Required.</span></span> <span data-ttu-id="0a4e6-152">Nom d’une interface implémentée par la classe ou la structure conteneur de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-152">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="0a4e6-153">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-153">Required.</span></span> <span data-ttu-id="0a4e6-154">Nom par lequel la procédure est définie dans `interface`.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-154">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="0a4e6-155">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-155">Optional.</span></span> <span data-ttu-id="0a4e6-156">Indique que cette procédure peut gérer un ou plusieurs événements spécifiques.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-156">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="0a4e6-157">Consultez [Handles](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e6-157">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="0a4e6-158">Obligatoire si `Handles` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-158">Required if `Handles` is supplied.</span></span> <span data-ttu-id="0a4e6-159">Liste des événements gérés par cette procédure.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-159">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="0a4e6-160">Chaque `eventspecifier` emploie la syntaxe et les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="0a4e6-160">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="0a4e6-161">Élément</span><span class="sxs-lookup"><span data-stu-id="0a4e6-161">Part</span></span>|<span data-ttu-id="0a4e6-162">Description</span><span class="sxs-lookup"><span data-stu-id="0a4e6-162">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="0a4e6-163">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-163">Required.</span></span> <span data-ttu-id="0a4e6-164">Variable objet déclarée avec le type de données de la classe ou de la structure qui déclenche l’événement.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-164">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="0a4e6-165">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-165">Required.</span></span> <span data-ttu-id="0a4e6-166">Nom de l’événement géré par cette procédure.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-166">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="0a4e6-167">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-167">Optional.</span></span> <span data-ttu-id="0a4e6-168">Bloc d’instructions à exécuter dans cette procédure.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-168">Block of statements to be executed within this procedure.</span></span>

- `End Function`

  <span data-ttu-id="0a4e6-169">Met fin à la définition de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-169">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a4e6-170">Notes</span><span class="sxs-lookup"><span data-stu-id="0a4e6-170">Remarks</span></span>

<span data-ttu-id="0a4e6-171">Tout le code exécutable doit être à l’intérieur d’une procédure.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-171">All executable code must be inside a procedure.</span></span> <span data-ttu-id="0a4e6-172">Chaque procédure, à son tour, est déclarée dans une classe, une structure ou un module qui est désigné comme la classe, la structure ou le module qui le contient.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-172">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>

<span data-ttu-id="0a4e6-173">Pour retourner une valeur au code appelant, utilisez une `Function` procédure ; sinon, utilisez une `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-173">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>

## <a name="defining-a-function"></a><span data-ttu-id="0a4e6-174">Définition d’une fonction</span><span class="sxs-lookup"><span data-stu-id="0a4e6-174">Defining a Function</span></span>

<span data-ttu-id="0a4e6-175">Vous pouvez définir une `Function` procédure uniquement au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-175">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="0a4e6-176">Par conséquent, le contexte de déclaration pour une fonction doit être une classe, une structure, un module ou une interface et ne peut pas être un fichier source, un espace de noms, une procédure ou un bloc.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-176">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="0a4e6-177">Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e6-177">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="0a4e6-178">`Function`les procédures ont par défaut accès public.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-178">`Function` procedures default to public access.</span></span> <span data-ttu-id="0a4e6-179">Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-179">You can adjust their access levels with the access modifiers.</span></span>

<span data-ttu-id="0a4e6-180">Une `Function` procédure peut déclarer le type de données de la valeur retournée par la procédure.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-180">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="0a4e6-181">Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération, d’une structure, d’une classe ou d’une interface.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-181">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="0a4e6-182">Si vous ne spécifiez pas le `returntype` paramètre, la procédure retourne `Object` .</span><span class="sxs-lookup"><span data-stu-id="0a4e6-182">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>

<span data-ttu-id="0a4e6-183">Si cette procédure utilise le `Implements` mot clé, la classe ou la structure conteneur doit également avoir une `Implements` instruction qui suit immédiatement son `Class` `Structure` instruction ou.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-183">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="0a4e6-184">L' `Implements` instruction doit inclure chaque interface spécifiée dans `implementslist` .</span><span class="sxs-lookup"><span data-stu-id="0a4e6-184">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="0a4e6-185">Toutefois, le nom par lequel une interface définit `Function` (dans `definedname` ) ne doit pas nécessairement correspondre au nom de cette procédure (dans `name` ).</span><span class="sxs-lookup"><span data-stu-id="0a4e6-185">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>

> [!NOTE]
> <span data-ttu-id="0a4e6-186">Vous pouvez utiliser des expressions lambda pour définir des expressions de fonction Inline.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-186">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="0a4e6-187">Pour plus d’informations, consultez [expression de fonction](../operators/function-expression.md) et [expressions lambda](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e6-187">For more information, see [Function Expression](../operators/function-expression.md) and [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="returning-from-a-function"></a><span data-ttu-id="0a4e6-188">Retour à partir d’une fonction</span><span class="sxs-lookup"><span data-stu-id="0a4e6-188">Returning from a Function</span></span>

<span data-ttu-id="0a4e6-189">Lorsque la `Function` procédure revient au code appelant, l’exécution se poursuit avec l’instruction qui suit l’instruction qui a appelé la procédure.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-189">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>

<span data-ttu-id="0a4e6-190">Pour retourner une valeur à partir d’une fonction, vous pouvez affecter la valeur au nom de la fonction ou l’inclure dans une `Return` instruction.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-190">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>

<span data-ttu-id="0a4e6-191">L' `Return` instruction assigne simultanément la valeur de retour et quitte la fonction, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-191">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

<span data-ttu-id="0a4e6-192">L’exemple suivant affecte la valeur de retour au nom de la fonction `myFunction` , puis utilise l' `Exit Function` instruction pour retourner.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-192">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

<span data-ttu-id="0a4e6-193">Les `Exit Function` `Return` instructions et provoquent une sortie immédiate d’une `Function` procédure.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-193">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="0a4e6-194">Un nombre quelconque `Exit Function` d' `Return` instructions et peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger des `Exit Function` `Return` instructions et.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-194">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>

<span data-ttu-id="0a4e6-195">Si vous utilisez `Exit Function` sans assigner de valeur à `name` , la procédure retourne la valeur par défaut pour le type de données spécifié dans `returntype` .</span><span class="sxs-lookup"><span data-stu-id="0a4e6-195">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="0a4e6-196">Si `returntype` n’est pas spécifié, la procédure retourne `Nothing` , qui est la valeur par défaut pour `Object` .</span><span class="sxs-lookup"><span data-stu-id="0a4e6-196">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>

## <a name="calling-a-function"></a><span data-ttu-id="0a4e6-197">Appel d’une fonction</span><span class="sxs-lookup"><span data-stu-id="0a4e6-197">Calling a Function</span></span>

<span data-ttu-id="0a4e6-198">Vous appelez une `Function` procédure en utilisant le nom de la procédure, suivi de la liste d’arguments entre parenthèses, dans une expression.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-198">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="0a4e6-199">Vous pouvez omettre les parenthèses uniquement si vous ne fournissez pas d’arguments.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-199">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="0a4e6-200">Toutefois, votre code est plus lisible si vous incluez toujours les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-200">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="0a4e6-201">Vous appelez une `Function` procédure de la même façon que vous appelez une fonction de bibliothèque telle que `Sqrt` , `Cos` ou `ChrW` .</span><span class="sxs-lookup"><span data-stu-id="0a4e6-201">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>

<span data-ttu-id="0a4e6-202">Vous pouvez également appeler une fonction à l’aide du `Call` mot clé.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-202">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="0a4e6-203">Dans ce cas, la valeur de retour est ignorée.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-203">In that case, the return value is ignored.</span></span> <span data-ttu-id="0a4e6-204">L’utilisation du `Call` mot clé n’est pas recommandée dans la plupart des cas.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-204">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="0a4e6-205">Pour plus d’informations, consultez [Call, instruction](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e6-205">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="0a4e6-206">Visual Basic réorganise parfois des expressions arithmétiques pour augmenter l’efficacité interne.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-206">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="0a4e6-207">Pour cette raison, vous ne devez pas utiliser une `Function` procédure dans une expression arithmétique lorsque la fonction modifie la valeur des variables dans la même expression.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-207">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>

## <a name="async-functions"></a><span data-ttu-id="0a4e6-208">Fonctions Async</span><span class="sxs-lookup"><span data-stu-id="0a4e6-208">Async Functions</span></span>

<span data-ttu-id="0a4e6-209">La fonctionnalité *Async* vous permet d’appeler des fonctions asynchrones sans utiliser de rappels explicites ou de fractionner manuellement votre code entre plusieurs fonctions ou expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-209">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="0a4e6-210">Si vous marquez une fonction avec le modificateur [Async](../modifiers/async.md) , vous pouvez utiliser l’opérateur [await](../operators/await-operator.md) dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-210">If you mark a function with the [Async](../modifiers/async.md) modifier, you can use the [Await](../operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="0a4e6-211">Quand le contrôle atteint une `Await` expression dans la `Async` fonction, le contrôle retourne à l’appelant, et la progression dans la fonction est suspendue jusqu’à ce que la tâche attendue se termine.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-211">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="0a4e6-212">Une fois la tâche terminée, l’exécution peut reprendre dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-212">When the task is complete, execution can resume in the function.</span></span>

> [!NOTE]
> <span data-ttu-id="0a4e6-213">Une `Async` procédure est renvoyée à l’appelant lorsqu’elle rencontre le premier objet attendu qui n’est pas encore terminé ou qu’elle atteint la fin de la `Async` procédure, selon ce qui se produit en premier.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-213">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>

<span data-ttu-id="0a4e6-214">Une `Async` fonction peut avoir un type de retour <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="0a4e6-214">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="0a4e6-215">Vous trouverez `Async` ci-dessous un exemple de fonction qui a un type de retour <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="0a4e6-215">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>

<span data-ttu-id="0a4e6-216">Une `Async` fonction ne peut pas déclarer de paramètres [ByRef](../modifiers/byref.md) .</span><span class="sxs-lookup"><span data-stu-id="0a4e6-216">An `Async` function cannot declare any [ByRef](../modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="0a4e6-217">Une [sous-instruction](sub-statement.md) peut également être marquée avec le `Async` modificateur.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-217">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="0a4e6-218">Il est principalement utilisé pour les gestionnaires d’événements, où une valeur ne peut pas être retournée.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-218">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="0a4e6-219">Une `Async` `Sub` procédure ne peut pas être attendue, et l’appelant d’une `Async` `Sub` procédure ne peut pas intercepter les exceptions levées par la `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-219">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>

<span data-ttu-id="0a4e6-220">Pour plus d’informations sur les `Async` fonctions, consultez [programmation asynchrone avec Async et await](../../programming-guide/concepts/async/index.md), [Workflow de contrôle dans les programmes Async](../../programming-guide/concepts/async/control-flow-in-async-programs.md)et [types de retour Async](../../programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e6-220">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="iterator-functions"></a><span data-ttu-id="0a4e6-221">Fonctions d’itérateur</span><span class="sxs-lookup"><span data-stu-id="0a4e6-221">Iterator Functions</span></span>

<span data-ttu-id="0a4e6-222">Une fonction d' *itérateur* effectue une itération personnalisée sur une collection, telle qu’une liste ou un tableau.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-222">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="0a4e6-223">Une fonction d’itérateur utilise l’instruction [yield](yield-statement.md) pour retourner chaque élément un par un.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-223">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="0a4e6-224">Quand une instruction [yield](yield-statement.md) est atteinte, l’emplacement actuel dans le code est mémorisé.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-224">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="0a4e6-225">L’exécution est redémarrée à partir de cet emplacement lors de l’appel suivant de la fonction d’itérateur.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-225">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="0a4e6-226">Vous appelez un itérateur à partir du code client à l’aide [d’un for each... Instruction suivante](for-each-next-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="0a4e6-226">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>

<span data-ttu-id="0a4e6-227">Le type de retour d’une fonction d’itérateur peut être <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="0a4e6-227">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="0a4e6-228">Pour plus d’informations, consultez [itérateurs](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e6-228">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>

## <a name="example"></a><span data-ttu-id="0a4e6-229">Exemple</span><span class="sxs-lookup"><span data-stu-id="0a4e6-229">Example</span></span>

<span data-ttu-id="0a4e6-230">L’exemple suivant utilise l' `Function` instruction pour déclarer le nom, les paramètres et le code qui forment le corps d’une `Function` procédure.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-230">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="0a4e6-231">Le `ParamArray` modificateur permet à la fonction d’accepter un nombre variable d’arguments.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-231">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a><span data-ttu-id="0a4e6-232">Exemple</span><span class="sxs-lookup"><span data-stu-id="0a4e6-232">Example</span></span>

<span data-ttu-id="0a4e6-233">L’exemple suivant appelle la fonction déclarée dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-233">The following example invokes the function declared in the preceding example.</span></span>

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a><span data-ttu-id="0a4e6-234">Exemple</span><span class="sxs-lookup"><span data-stu-id="0a4e6-234">Example</span></span>

<span data-ttu-id="0a4e6-235">Dans l’exemple suivant, `DelayAsync` est un `Async` `Function` qui a un type de retour <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="0a4e6-235">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="0a4e6-236">`DelayAsync` a une instruction `Return` qui retourne un entier.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-236">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="0a4e6-237">Par conséquent, la déclaration de fonction de `DelayAsync` doit avoir un type de retour `Task(Of Integer)` .</span><span class="sxs-lookup"><span data-stu-id="0a4e6-237">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="0a4e6-238">Étant donné que le type de retour est `Task(Of Integer)` , l’évaluation de l' `Await` expression dans `DoSomethingAsync` produit un entier.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-238">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="0a4e6-239">Cela est illustré dans cette instruction : `Dim result As Integer = Await delayTask` .</span><span class="sxs-lookup"><span data-stu-id="0a4e6-239">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="0a4e6-240">La `startButton_Click` procédure est un exemple de `Async Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-240">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="0a4e6-241">Étant donné que `DoSomethingAsync` est une `Async` fonction, la tâche pour l’appel à `DoSomethingAsync` doit être attendue, comme le montre l’instruction suivante : `Await DoSomethingAsync()` .</span><span class="sxs-lookup"><span data-stu-id="0a4e6-241">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="0a4e6-242">La `startButton_Click` `Sub` procédure doit être définie avec le `Async` modificateur, car elle a une `Await` expression.</span><span class="sxs-lookup"><span data-stu-id="0a4e6-242">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="0a4e6-243">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a4e6-243">See also</span></span>

- [<span data-ttu-id="0a4e6-244">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="0a4e6-244">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="0a4e6-245">Function, procédures</span><span class="sxs-lookup"><span data-stu-id="0a4e6-245">Function Procedures</span></span>](../../programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="0a4e6-246">Liste de paramètres</span><span class="sxs-lookup"><span data-stu-id="0a4e6-246">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="0a4e6-247">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="0a4e6-247">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="0a4e6-248">Call (instruction)</span><span class="sxs-lookup"><span data-stu-id="0a4e6-248">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="0a4e6-249">Of</span><span class="sxs-lookup"><span data-stu-id="0a4e6-249">Of</span></span>](of-clause.md)
- [<span data-ttu-id="0a4e6-250">Tableaux de paramètres</span><span class="sxs-lookup"><span data-stu-id="0a4e6-250">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="0a4e6-251">Procédure : Utiliser une classe générique</span><span class="sxs-lookup"><span data-stu-id="0a4e6-251">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="0a4e6-252">Procédures de dépannage</span><span class="sxs-lookup"><span data-stu-id="0a4e6-252">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="0a4e6-253">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="0a4e6-253">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="0a4e6-254">Expression de fonction</span><span class="sxs-lookup"><span data-stu-id="0a4e6-254">Function Expression</span></span>](../operators/function-expression.md)
