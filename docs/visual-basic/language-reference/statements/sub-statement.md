---
title: Sub (instruction)
ms.date: 05/12/2018
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
ms.openlocfilehash: e50b79c31c92ac116d6c82bcececba3340894d74
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404172"
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="205fa-102">Sub, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="205fa-102">Sub Statement (Visual Basic)</span></span>

<span data-ttu-id="205fa-103">Déclare le nom, les paramètres et le code qui définissent une `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="205fa-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="205fa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="205fa-104">Syntax</span></span>

```vb
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a><span data-ttu-id="205fa-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="205fa-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="205fa-106">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="205fa-106">Optional.</span></span> <span data-ttu-id="205fa-107">Consultez la [liste des attributs](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="205fa-107">See [Attribute List](attribute-list.md).</span></span>

- `Partial`

  <span data-ttu-id="205fa-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="205fa-108">Optional.</span></span> <span data-ttu-id="205fa-109">Indique la définition d’une méthode partielle.</span><span class="sxs-lookup"><span data-stu-id="205fa-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="205fa-110">Consultez [méthodes partielles](../../programming-guide/language-features/procedures/partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="205fa-110">See [Partial Methods](../../programming-guide/language-features/procedures/partial-methods.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="205fa-111">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="205fa-111">Optional.</span></span> <span data-ttu-id="205fa-112">Il peut s'agir d'une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="205fa-112">Can be one of the following:</span></span>

  - [<span data-ttu-id="205fa-113">Public</span><span class="sxs-lookup"><span data-stu-id="205fa-113">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="205fa-114">Protect</span><span class="sxs-lookup"><span data-stu-id="205fa-114">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="205fa-115">Contact</span><span class="sxs-lookup"><span data-stu-id="205fa-115">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="205fa-116">Privé</span><span class="sxs-lookup"><span data-stu-id="205fa-116">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="205fa-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="205fa-117">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="205fa-118">Protégé privé</span><span class="sxs-lookup"><span data-stu-id="205fa-118">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="205fa-119">Consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="205fa-119">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="205fa-120">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="205fa-120">Optional.</span></span> <span data-ttu-id="205fa-121">Il peut s'agir d'une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="205fa-121">Can be one of the following:</span></span>

  - [<span data-ttu-id="205fa-122">Surcharges</span><span class="sxs-lookup"><span data-stu-id="205fa-122">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="205fa-123">Remplacements</span><span class="sxs-lookup"><span data-stu-id="205fa-123">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="205fa-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="205fa-124">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="205fa-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="205fa-125">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="205fa-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="205fa-126">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="205fa-127">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="205fa-127">Optional.</span></span> <span data-ttu-id="205fa-128">Consultez [partagé](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="205fa-128">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="205fa-129">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="205fa-129">Optional.</span></span> <span data-ttu-id="205fa-130">Consultez [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="205fa-130">See [Shadows](../modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="205fa-131">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="205fa-131">Optional.</span></span> <span data-ttu-id="205fa-132">Consultez [Async](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="205fa-132">See [Async](../modifiers/async.md).</span></span>

- `name`

  <span data-ttu-id="205fa-133">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="205fa-133">Required.</span></span> <span data-ttu-id="205fa-134">Nom de la procédure.</span><span class="sxs-lookup"><span data-stu-id="205fa-134">Name of the procedure.</span></span> <span data-ttu-id="205fa-135">Consultez [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="205fa-135">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="205fa-136">Pour créer une procédure constructeur pour une classe, définissez le nom d’une `Sub` procédure sur le `New` mot clé.</span><span class="sxs-lookup"><span data-stu-id="205fa-136">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="205fa-137">Pour plus d’informations, consultez durée de vie d’un [objet : comment les objets sont créés et détruits](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="205fa-137">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="205fa-138">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="205fa-138">Optional.</span></span> <span data-ttu-id="205fa-139">Liste des paramètres de type pour une procédure générique.</span><span class="sxs-lookup"><span data-stu-id="205fa-139">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="205fa-140">Consultez la [liste des types](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="205fa-140">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="205fa-141">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="205fa-141">Optional.</span></span> <span data-ttu-id="205fa-142">Liste des noms de variables locales représentant les paramètres de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="205fa-142">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="205fa-143">Consultez la [liste des paramètres](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="205fa-143">See [Parameter List](parameter-list.md).</span></span>

- `Implements`

  <span data-ttu-id="205fa-144">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="205fa-144">Optional.</span></span> <span data-ttu-id="205fa-145">Indique que cette procédure implémente une ou plusieurs `Sub` procédures, chacune d’elles étant définie dans une interface implémentée par la classe ou la structure conteneur de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="205fa-145">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="205fa-146">Consultez [Implements, instruction](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="205fa-146">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="205fa-147">Obligatoire si `Implements` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="205fa-147">Required if `Implements` is supplied.</span></span> <span data-ttu-id="205fa-148">Liste des procédures `Sub` en cours d'implémentation.</span><span class="sxs-lookup"><span data-stu-id="205fa-148">List of `Sub` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="205fa-149">Chaque `implementedprocedure` emploie la syntaxe et les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="205fa-149">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="205fa-150">Élément</span><span class="sxs-lookup"><span data-stu-id="205fa-150">Part</span></span>|<span data-ttu-id="205fa-151">Description</span><span class="sxs-lookup"><span data-stu-id="205fa-151">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="205fa-152">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="205fa-152">Required.</span></span> <span data-ttu-id="205fa-153">Nom d’une interface implémentée par la classe ou la structure conteneur de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="205fa-153">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="205fa-154">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="205fa-154">Required.</span></span> <span data-ttu-id="205fa-155">Nom par lequel la procédure est définie dans `interface`.</span><span class="sxs-lookup"><span data-stu-id="205fa-155">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="205fa-156">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="205fa-156">Optional.</span></span> <span data-ttu-id="205fa-157">Indique que cette procédure peut gérer un ou plusieurs événements spécifiques.</span><span class="sxs-lookup"><span data-stu-id="205fa-157">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="205fa-158">Consultez [Handles](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="205fa-158">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="205fa-159">Obligatoire si `Handles` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="205fa-159">Required if `Handles` is supplied.</span></span> <span data-ttu-id="205fa-160">Liste des événements gérés par cette procédure.</span><span class="sxs-lookup"><span data-stu-id="205fa-160">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="205fa-161">Chaque `eventspecifier` emploie la syntaxe et les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="205fa-161">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="205fa-162">Élément</span><span class="sxs-lookup"><span data-stu-id="205fa-162">Part</span></span>|<span data-ttu-id="205fa-163">Description</span><span class="sxs-lookup"><span data-stu-id="205fa-163">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="205fa-164">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="205fa-164">Required.</span></span> <span data-ttu-id="205fa-165">Variable objet déclarée avec le type de données de la classe ou de la structure qui déclenche l’événement.</span><span class="sxs-lookup"><span data-stu-id="205fa-165">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="205fa-166">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="205fa-166">Required.</span></span> <span data-ttu-id="205fa-167">Nom de l’événement géré par cette procédure.</span><span class="sxs-lookup"><span data-stu-id="205fa-167">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="205fa-168">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="205fa-168">Optional.</span></span> <span data-ttu-id="205fa-169">Bloc d’instructions à exécuter dans cette procédure.</span><span class="sxs-lookup"><span data-stu-id="205fa-169">Block of statements to run within this procedure.</span></span>

- `End Sub`

  <span data-ttu-id="205fa-170">Met fin à la définition de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="205fa-170">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="205fa-171">Notes</span><span class="sxs-lookup"><span data-stu-id="205fa-171">Remarks</span></span>

<span data-ttu-id="205fa-172">Tout le code exécutable doit être à l’intérieur d’une procédure.</span><span class="sxs-lookup"><span data-stu-id="205fa-172">All executable code must be inside a procedure.</span></span> <span data-ttu-id="205fa-173">Utilisez une `Sub` procédure lorsque vous ne souhaitez pas retourner une valeur au code appelant.</span><span class="sxs-lookup"><span data-stu-id="205fa-173">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="205fa-174">Utilisez une `Function` procédure lorsque vous souhaitez retourner une valeur.</span><span class="sxs-lookup"><span data-stu-id="205fa-174">Use a `Function` procedure when you want to return a value.</span></span>

## <a name="defining-a-sub-procedure"></a><span data-ttu-id="205fa-175">Définition d’une procédure Sub</span><span class="sxs-lookup"><span data-stu-id="205fa-175">Defining a Sub Procedure</span></span>

<span data-ttu-id="205fa-176">Vous pouvez définir une `Sub` procédure uniquement au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="205fa-176">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="205fa-177">Le contexte de déclaration d’une procédure Sub doit, par conséquent, être une classe, une structure, un module ou une interface et ne peut pas être un fichier source, un espace de noms, une procédure ou un bloc.</span><span class="sxs-lookup"><span data-stu-id="205fa-177">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="205fa-178">Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="205fa-178">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="205fa-179">`Sub`les procédures ont par défaut accès public.</span><span class="sxs-lookup"><span data-stu-id="205fa-179">`Sub` procedures default to public access.</span></span> <span data-ttu-id="205fa-180">Vous pouvez ajuster leurs niveaux d’accès à l’aide des modificateurs d’accès.</span><span class="sxs-lookup"><span data-stu-id="205fa-180">You can adjust their access levels by using the access modifiers.</span></span>

<span data-ttu-id="205fa-181">Si la procédure utilise le `Implements` mot clé, la classe ou la structure conteneur doit avoir une `Implements` instruction qui suit immédiatement son `Class` `Structure` instruction ou.</span><span class="sxs-lookup"><span data-stu-id="205fa-181">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="205fa-182">L' `Implements` instruction doit inclure chaque interface spécifiée dans `implementslist` .</span><span class="sxs-lookup"><span data-stu-id="205fa-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="205fa-183">Toutefois, le nom par lequel une interface définit `Sub` (dans `definedname` ) ne doit pas nécessairement correspondre au nom de cette procédure (dans `name` ).</span><span class="sxs-lookup"><span data-stu-id="205fa-183">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>

## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="205fa-184">Retour d’une procédure Sub</span><span class="sxs-lookup"><span data-stu-id="205fa-184">Returning from a Sub Procedure</span></span>

<span data-ttu-id="205fa-185">Quand une `Sub` procédure revient au code appelant, l’exécution se poursuit avec l’instruction qui suit l’instruction qui l’a appelée.</span><span class="sxs-lookup"><span data-stu-id="205fa-185">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>

<span data-ttu-id="205fa-186">L’exemple suivant montre un retour d’une `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="205fa-186">The following example shows a return from a `Sub` procedure.</span></span>

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

<span data-ttu-id="205fa-187">Les `Exit Sub` `Return` instructions et provoquent une sortie immédiate d’une `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="205fa-187">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="205fa-188">Un nombre quelconque `Exit Sub` d' `Return` instructions et peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger des `Exit Sub` `Return` instructions et.</span><span class="sxs-lookup"><span data-stu-id="205fa-188">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>

## <a name="calling-a-sub-procedure"></a><span data-ttu-id="205fa-189">Appel d’une procédure Sub</span><span class="sxs-lookup"><span data-stu-id="205fa-189">Calling a Sub Procedure</span></span>

<span data-ttu-id="205fa-190">Vous appelez une `Sub` procédure en utilisant le nom de la procédure dans une instruction, puis en suivant ce nom avec sa liste d’arguments entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="205fa-190">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="205fa-191">Vous pouvez omettre les parenthèses uniquement si vous ne fournissez pas d’arguments.</span><span class="sxs-lookup"><span data-stu-id="205fa-191">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="205fa-192">Toutefois, votre code est plus lisible si vous incluez toujours les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="205fa-192">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="205fa-193">Une `Sub` procédure et une `Function` procédure peuvent avoir des paramètres et exécuter une série d’instructions.</span><span class="sxs-lookup"><span data-stu-id="205fa-193">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="205fa-194">Toutefois, une `Function` procédure retourne une valeur, et une `Sub` procédure ne le fait pas.</span><span class="sxs-lookup"><span data-stu-id="205fa-194">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="205fa-195">Par conséquent, vous ne pouvez pas utiliser une `Sub` procédure dans une expression.</span><span class="sxs-lookup"><span data-stu-id="205fa-195">Therefore, you can't use a `Sub` procedure in an expression.</span></span>

<span data-ttu-id="205fa-196">Vous pouvez utiliser le `Call` mot clé lorsque vous appelez une `Sub` procédure, mais ce mot clé n’est pas recommandé pour la plupart des utilisations.</span><span class="sxs-lookup"><span data-stu-id="205fa-196">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="205fa-197">Pour plus d’informations, consultez [Call, instruction](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="205fa-197">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="205fa-198">Visual Basic réorganise parfois des expressions arithmétiques pour augmenter l’efficacité interne.</span><span class="sxs-lookup"><span data-stu-id="205fa-198">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="205fa-199">Pour cette raison, si votre liste d’arguments comprend des expressions qui appellent d’autres procédures, vous ne devez pas supposer que ces expressions seront appelées dans un ordre particulier.</span><span class="sxs-lookup"><span data-stu-id="205fa-199">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>

## <a name="async-sub-procedures"></a><span data-ttu-id="205fa-200">Procédures Sub Async</span><span class="sxs-lookup"><span data-stu-id="205fa-200">Async Sub Procedures</span></span>

<span data-ttu-id="205fa-201">À l’aide de la fonctionnalité Async, vous pouvez appeler des fonctions asynchrones sans utiliser de rappels explicites ni fractionner manuellement votre code entre plusieurs fonctions ou expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="205fa-201">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="205fa-202">Si vous marquez une procédure avec le modificateur [Async](../modifiers/async.md) , vous pouvez utiliser l’opérateur [await](../operators/await-operator.md) dans la procédure.</span><span class="sxs-lookup"><span data-stu-id="205fa-202">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="205fa-203">Quand le contrôle atteint une `Await` expression dans la `Async` procédure, le contrôle retourne à l’appelant, et la progression dans la procédure est suspendue jusqu’à ce que la tâche attendue se termine.</span><span class="sxs-lookup"><span data-stu-id="205fa-203">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="205fa-204">Une fois la tâche terminée, l’exécution peut reprendre dans la procédure.</span><span class="sxs-lookup"><span data-stu-id="205fa-204">When the task is complete, execution can resume in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="205fa-205">Une `Async` procédure retourne à l’appelant lorsque le premier objet attendu qui n’est pas encore terminé est rencontré ou jusqu’à la fin de la `Async` procédure, selon ce qui se produit en premier.</span><span class="sxs-lookup"><span data-stu-id="205fa-205">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>

<span data-ttu-id="205fa-206">Vous pouvez également marquer une [instruction de fonction](function-statement.md) avec le `Async` modificateur.</span><span class="sxs-lookup"><span data-stu-id="205fa-206">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="205fa-207">Une `Async` fonction peut avoir un type de retour <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="205fa-207">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="205fa-208">Un exemple plus loin dans cette rubrique montre une `Async` fonction qui a un type de retour <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="205fa-208">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="205fa-209">`Async`les `Sub` procédures sont principalement utilisées pour les gestionnaires d’événements, où une valeur ne peut pas être retournée.</span><span class="sxs-lookup"><span data-stu-id="205fa-209">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="205fa-210">Une `Async` `Sub` procédure ne peut pas être attendue, et l’appelant d’une `Async` `Sub` procédure ne peut pas intercepter les exceptions `Sub` levées par la procédure.</span><span class="sxs-lookup"><span data-stu-id="205fa-210">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>

<span data-ttu-id="205fa-211">Une `Async` procédure ne peut pas déclarer de paramètres [ByRef](../modifiers/byref.md) .</span><span class="sxs-lookup"><span data-stu-id="205fa-211">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="205fa-212">Pour plus d’informations sur les `Async` procédures, consultez [programmation asynchrone avec Async et await](../../programming-guide/concepts/async/index.md), [Workflow de contrôle dans les programmes Async](../../programming-guide/concepts/async/control-flow-in-async-programs.md)et [types de retour Async](../../programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="205fa-212">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="example"></a><span data-ttu-id="205fa-213">Exemple</span><span class="sxs-lookup"><span data-stu-id="205fa-213">Example</span></span>

<span data-ttu-id="205fa-214">L’exemple suivant utilise l' `Sub` instruction pour définir le nom, les paramètres et le code qui forment le corps d’une `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="205fa-214">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a><span data-ttu-id="205fa-215">Exemple</span><span class="sxs-lookup"><span data-stu-id="205fa-215">Example</span></span>

<span data-ttu-id="205fa-216">Dans l’exemple suivant, `DelayAsync` est un `Async` `Function` qui a un type de retour <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="205fa-216">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="205fa-217">`DelayAsync` a une instruction `Return` qui retourne un entier.</span><span class="sxs-lookup"><span data-stu-id="205fa-217">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="205fa-218">Par conséquent, la déclaration de fonction de `DelayAsync` doit avoir un type de retour `Task(Of Integer)` .</span><span class="sxs-lookup"><span data-stu-id="205fa-218">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="205fa-219">Étant donné que le type de retour est `Task(Of Integer)` , l’évaluation de l' `Await` expression dans `DoSomethingAsync` produit un entier, comme le montre l’instruction suivante : `Dim result As Integer = Await delayTask` .</span><span class="sxs-lookup"><span data-stu-id="205fa-219">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="205fa-220">La `startButton_Click` procédure est un exemple de `Async Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="205fa-220">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="205fa-221">Étant donné que `DoSomethingAsync` est une `Async` fonction, la tâche pour l’appel à `DoSomethingAsync` doit être attendue, comme le montre l’instruction suivante : `Await DoSomethingAsync()` .</span><span class="sxs-lookup"><span data-stu-id="205fa-221">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="205fa-222">La `startButton_Click` `Sub` procédure doit être définie avec le `Async` modificateur, car elle a une `Await` expression.</span><span class="sxs-lookup"><span data-stu-id="205fa-222">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="205fa-223">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="205fa-223">See also</span></span>

- [<span data-ttu-id="205fa-224">Implements, instruction</span><span class="sxs-lookup"><span data-stu-id="205fa-224">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="205fa-225">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="205fa-225">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="205fa-226">Liste de paramètres</span><span class="sxs-lookup"><span data-stu-id="205fa-226">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="205fa-227">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="205fa-227">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="205fa-228">Call (instruction)</span><span class="sxs-lookup"><span data-stu-id="205fa-228">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="205fa-229">Of</span><span class="sxs-lookup"><span data-stu-id="205fa-229">Of</span></span>](of-clause.md)
- [<span data-ttu-id="205fa-230">Tableaux de paramètres</span><span class="sxs-lookup"><span data-stu-id="205fa-230">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="205fa-231">Procédure : Utiliser une classe générique</span><span class="sxs-lookup"><span data-stu-id="205fa-231">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="205fa-232">Procédures de dépannage</span><span class="sxs-lookup"><span data-stu-id="205fa-232">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="205fa-233">Méthodes partielles</span><span class="sxs-lookup"><span data-stu-id="205fa-233">Partial Methods</span></span>](../../programming-guide/language-features/procedures/partial-methods.md)
