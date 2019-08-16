---
title: Portée dans Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: 7f7e32d6ac838e250c260987d3d5c375f8697c45
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512848"
---
# <a name="scope-in-visual-basic"></a><span data-ttu-id="0651c-102">Portée dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0651c-102">Scope in Visual Basic</span></span>

<span data-ttu-id="0651c-103">La *portée* d’un élément déclaré est le jeu de tout le code qui peut faire référence à celui-ci sans qualifier son nom ou le rendre disponible via une [instruction Imports (espace de noms et type .net)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="0651c-103">The *scope* of a declared element is the set of all code that can refer to it without qualifying its name or making it available through an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="0651c-104">Un élément peut avoir la portée à l’un des niveaux suivants:</span><span class="sxs-lookup"><span data-stu-id="0651c-104">An element can have scope at one of the following levels:</span></span>

|<span data-ttu-id="0651c-105">Niveau</span><span class="sxs-lookup"><span data-stu-id="0651c-105">Level</span></span>|<span data-ttu-id="0651c-106">Description</span><span class="sxs-lookup"><span data-stu-id="0651c-106">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="0651c-107">Portée de bloc</span><span class="sxs-lookup"><span data-stu-id="0651c-107">Block scope</span></span>|<span data-ttu-id="0651c-108">Disponible uniquement dans le bloc de code dans lequel il est déclaré</span><span class="sxs-lookup"><span data-stu-id="0651c-108">Available only within the code block in which it is declared</span></span>|
|<span data-ttu-id="0651c-109">Portée de la procédure</span><span class="sxs-lookup"><span data-stu-id="0651c-109">Procedure scope</span></span>|<span data-ttu-id="0651c-110">Disponible pour tout le code dans la procédure dans laquelle il est déclaré</span><span class="sxs-lookup"><span data-stu-id="0651c-110">Available to all code within the procedure in which it is declared</span></span>|
|<span data-ttu-id="0651c-111">Portée du module</span><span class="sxs-lookup"><span data-stu-id="0651c-111">Module scope</span></span>|<span data-ttu-id="0651c-112">Disponible pour tout le code au sein du module, de la classe ou de la structure dans laquelle il est déclaré</span><span class="sxs-lookup"><span data-stu-id="0651c-112">Available to all code within the module, class, or structure in which it is declared</span></span>|
|<span data-ttu-id="0651c-113">Portée espace de noms</span><span class="sxs-lookup"><span data-stu-id="0651c-113">Namespace scope</span></span>|<span data-ttu-id="0651c-114">Disponible pour l’ensemble du code dans l’espace de noms dans lequel il est déclaré</span><span class="sxs-lookup"><span data-stu-id="0651c-114">Available to all code in the namespace in which it is declared</span></span>|

<span data-ttu-id="0651c-115">Ces niveaux de la portée progressent du plus étroit (bloc) au plus large (espace de noms), où l’étendue la plus *étroite* correspond au plus petit ensemble de code qui peut faire référence à l’élément sans qualification.</span><span class="sxs-lookup"><span data-stu-id="0651c-115">These levels of scope progress from the narrowest (block) to the widest (namespace), where *narrowest scope* means the smallest set of code that can refer to the element without qualification.</span></span> <span data-ttu-id="0651c-116">Pour plus d’informations, consultez «niveaux d’étendue» dans cette page.</span><span class="sxs-lookup"><span data-stu-id="0651c-116">For more information, see "Levels of Scope" on this page.</span></span>

## <a name="specifying-scope-and-defining-variables"></a><span data-ttu-id="0651c-117">Spécification de l’étendue et définition de variables</span><span class="sxs-lookup"><span data-stu-id="0651c-117">Specifying Scope and Defining Variables</span></span>

<span data-ttu-id="0651c-118">Vous spécifiez l’étendue d’un élément lorsque vous le déclarez.</span><span class="sxs-lookup"><span data-stu-id="0651c-118">You specify the scope of an element when you declare it.</span></span> <span data-ttu-id="0651c-119">L’étendue peut dépendre des facteurs suivants:</span><span class="sxs-lookup"><span data-stu-id="0651c-119">The scope can depend on the following factors:</span></span>

- <span data-ttu-id="0651c-120">Région (bloc, procédure, module, classe ou structure) dans laquelle vous déclarez l’élément</span><span class="sxs-lookup"><span data-stu-id="0651c-120">The region (block, procedure, module, class, or structure) in which you declare the element</span></span>

- <span data-ttu-id="0651c-121">Espace de noms contenant la déclaration de l’élément.</span><span class="sxs-lookup"><span data-stu-id="0651c-121">The namespace containing the element's declaration</span></span>

- <span data-ttu-id="0651c-122">Le niveau d’accès que vous déclarez pour l’élément</span><span class="sxs-lookup"><span data-stu-id="0651c-122">The access level you declare for the element</span></span>

<span data-ttu-id="0651c-123">Soyez vigilant lorsque vous définissez des variables portant le même nom mais avec une étendue différente, car cela peut entraîner des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="0651c-123">Use care when you define variables with the same name but different scope, because doing so can lead to unexpected results.</span></span> <span data-ttu-id="0651c-124">Pour plus d'informations, consultez [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="0651c-124">For more information, see [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

## <a name="levels-of-scope"></a><span data-ttu-id="0651c-125">Niveaux d’étendue</span><span class="sxs-lookup"><span data-stu-id="0651c-125">Levels of Scope</span></span>

<span data-ttu-id="0651c-126">Un élément de programmation est disponible dans l’ensemble de la région dans laquelle vous le déclarez.</span><span class="sxs-lookup"><span data-stu-id="0651c-126">A programming element is available throughout the region in which you declare it.</span></span> <span data-ttu-id="0651c-127">Tout le code dans la même région peut faire référence à l’élément sans qualifier son nom.</span><span class="sxs-lookup"><span data-stu-id="0651c-127">All code in the same region can refer to the element without qualifying its name.</span></span>

### <a name="block-scope"></a><span data-ttu-id="0651c-128">Portée de bloc</span><span class="sxs-lookup"><span data-stu-id="0651c-128">Block Scope</span></span>

<span data-ttu-id="0651c-129">Un bloc est un ensemble d’instructions placées dans des instructions de déclaration de début et de fin, comme suit:</span><span class="sxs-lookup"><span data-stu-id="0651c-129">A block is a set of statements enclosed within initiating and terminating declaration statements, such as the following:</span></span>

- <span data-ttu-id="0651c-130">`Do` et `Loop`</span><span class="sxs-lookup"><span data-stu-id="0651c-130">`Do` and `Loop`</span></span>

- <span data-ttu-id="0651c-131">`For`[`Each`] et`Next`</span><span class="sxs-lookup"><span data-stu-id="0651c-131">`For` [`Each`] and `Next`</span></span>

- <span data-ttu-id="0651c-132">`If` et `End If`</span><span class="sxs-lookup"><span data-stu-id="0651c-132">`If` and `End If`</span></span>

- <span data-ttu-id="0651c-133">`Select` et `End Select`</span><span class="sxs-lookup"><span data-stu-id="0651c-133">`Select` and `End Select`</span></span>

- <span data-ttu-id="0651c-134">`SyncLock` et `End SyncLock`</span><span class="sxs-lookup"><span data-stu-id="0651c-134">`SyncLock` and `End SyncLock`</span></span>

- <span data-ttu-id="0651c-135">`Try` et `End Try`</span><span class="sxs-lookup"><span data-stu-id="0651c-135">`Try` and `End Try`</span></span>

- <span data-ttu-id="0651c-136">`While` et `End While`</span><span class="sxs-lookup"><span data-stu-id="0651c-136">`While` and `End While`</span></span>

- <span data-ttu-id="0651c-137">`With` et `End With`</span><span class="sxs-lookup"><span data-stu-id="0651c-137">`With` and `End With`</span></span>

<span data-ttu-id="0651c-138">Si vous déclarez une variable dans un bloc, vous pouvez l’utiliser uniquement dans ce bloc.</span><span class="sxs-lookup"><span data-stu-id="0651c-138">If you declare a variable within a block, you can use it only within that block.</span></span> <span data-ttu-id="0651c-139">Dans l’exemple suivant, la portée de la `cube` variable de type entier est le bloc entre `If` et `End If`, et vous ne pouvez plus `cube` faire référence à lorsque l’exécution passe en dehors du bloc.</span><span class="sxs-lookup"><span data-stu-id="0651c-139">In the following example, the scope of the integer variable `cube` is the block between `If` and `End If`, and you can no longer refer to `cube` when execution passes out of the block.</span></span>

```vb
If n < 1291 Then
    Dim cube As Integer
    cube = n ^ 3
End If
```

> [!NOTE]
> <span data-ttu-id="0651c-140">Même si l’étendue d’une variable est limitée à un bloc, sa durée de vie est toujours celle de la procédure entière.</span><span class="sxs-lookup"><span data-stu-id="0651c-140">Even if the scope of a variable is limited to a block, its lifetime is still that of the entire procedure.</span></span> <span data-ttu-id="0651c-141">Si vous entrez le bloc plus d’une fois pendant la procédure, chaque variable de bloc conserve sa valeur précédente.</span><span class="sxs-lookup"><span data-stu-id="0651c-141">If you enter the block more than once during the procedure, each block variable retains its previous value.</span></span> <span data-ttu-id="0651c-142">Pour éviter des résultats inattendus dans ce cas, il est préférable d’initialiser les variables de bloc au début du bloc.</span><span class="sxs-lookup"><span data-stu-id="0651c-142">To avoid unexpected results in such a case, it is wise to initialize block variables at the beginning of the block.</span></span>

### <a name="procedure-scope"></a><span data-ttu-id="0651c-143">Portée de la procédure</span><span class="sxs-lookup"><span data-stu-id="0651c-143">Procedure Scope</span></span>

<span data-ttu-id="0651c-144">Un élément déclaré dans une procédure n’est pas disponible en dehors de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="0651c-144">An element declared within a procedure is not available outside that procedure.</span></span> <span data-ttu-id="0651c-145">Seule la procédure qui contient la déclaration peut l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="0651c-145">Only the procedure that contains the declaration can use it.</span></span> <span data-ttu-id="0651c-146">Les variables à ce niveau sont également appelées *variables locales*.</span><span class="sxs-lookup"><span data-stu-id="0651c-146">Variables at this level are also known as *local variables*.</span></span> <span data-ttu-id="0651c-147">Vous les déclarez avec l' [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md), avec ou sans le mot clé [static](../../../../visual-basic/language-reference/modifiers/static.md) .</span><span class="sxs-lookup"><span data-stu-id="0651c-147">You declare them with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), with or without the [Static](../../../../visual-basic/language-reference/modifiers/static.md) keyword.</span></span>

<span data-ttu-id="0651c-148">La portée de la procédure et du bloc sont étroitement liées.</span><span class="sxs-lookup"><span data-stu-id="0651c-148">Procedure and block scope are closely related.</span></span> <span data-ttu-id="0651c-149">Si vous déclarez une variable à l’intérieur d’une procédure mais en dehors d’un bloc au sein de cette procédure, vous pouvez considérer la variable comme ayant une portée de bloc, où le bloc correspond à la procédure entière.</span><span class="sxs-lookup"><span data-stu-id="0651c-149">If you declare a variable inside a procedure but outside any block within that procedure, you can think of the variable as having block scope, where the block is the entire procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="0651c-150">Tous les éléments locaux, même s’il `Static` s’agit de variables, sont privés pour la procédure dans laquelle ils apparaissent.</span><span class="sxs-lookup"><span data-stu-id="0651c-150">All local elements, even if they are `Static` variables, are private to the procedure in which they appear.</span></span> <span data-ttu-id="0651c-151">Vous ne pouvez pas déclarer d’élément à l’aide du mot clé [public](../../../../visual-basic/language-reference/modifiers/public.md) dans une procédure.</span><span class="sxs-lookup"><span data-stu-id="0651c-151">You cannot declare any element using the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword within a procedure.</span></span>

### <a name="module-scope"></a><span data-ttu-id="0651c-152">Portée du module</span><span class="sxs-lookup"><span data-stu-id="0651c-152">Module Scope</span></span>

<span data-ttu-id="0651c-153">Pour plus de commodité, le *niveau de module* à simple terme s’applique de la même manière aux modules, aux classes et aux structures.</span><span class="sxs-lookup"><span data-stu-id="0651c-153">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="0651c-154">Vous pouvez déclarer des éléments à ce niveau en plaçant l’instruction de déclaration en dehors d’une procédure ou d’un bloc, mais au sein du module, de la classe ou de la structure.</span><span class="sxs-lookup"><span data-stu-id="0651c-154">You can declare elements at this level by placing the declaration statement outside of any procedure or block but within the module, class, or structure.</span></span>

<span data-ttu-id="0651c-155">Lorsque vous faites une déclaration au niveau du module, le niveau d’accès que vous choisissez détermine l’étendue.</span><span class="sxs-lookup"><span data-stu-id="0651c-155">When you make a declaration at the module level, the access level you choose determines the scope.</span></span> <span data-ttu-id="0651c-156">L’espace de noms qui contient le module, la classe ou la structure affecte également la portée.</span><span class="sxs-lookup"><span data-stu-id="0651c-156">The namespace that contains the module, class, or structure also affects the scope.</span></span>

<span data-ttu-id="0651c-157">Les éléments pour lesquels vous déclarez le niveau d’accès [privé](../../../../visual-basic/language-reference/modifiers/private.md) sont disponibles pour chaque procédure dans ce module, mais pas pour le code d’un autre module.</span><span class="sxs-lookup"><span data-stu-id="0651c-157">Elements for which you declare [Private](../../../../visual-basic/language-reference/modifiers/private.md) access level are available to every procedure in that module, but not to any code in a different module.</span></span> <span data-ttu-id="0651c-158">L' `Dim` instruction au niveau du module est définie `Private` par défaut sur si vous n’utilisez pas de mots clés de niveau d’accès.</span><span class="sxs-lookup"><span data-stu-id="0651c-158">The `Dim` statement at module level defaults to `Private` if you do not use any access level keywords.</span></span> <span data-ttu-id="0651c-159">Toutefois, vous pouvez rendre l’étendue et le niveau d’accès plus évidents `Private` à l’aide `Dim` du mot clé dans l’instruction.</span><span class="sxs-lookup"><span data-stu-id="0651c-159">However, you can make the scope and access level more obvious by using the `Private` keyword in the `Dim` statement.</span></span>

<span data-ttu-id="0651c-160">Dans l’exemple suivant, toutes les procédures définies dans le module peuvent faire référence à la `strMsg`variable de chaîne.</span><span class="sxs-lookup"><span data-stu-id="0651c-160">In the following example, all procedures defined in the module can refer to the string variable `strMsg`.</span></span> <span data-ttu-id="0651c-161">Lorsque la deuxième procédure est appelée, elle affiche le contenu de la variable `strMsg` de chaîne dans une boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="0651c-161">When the second procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>

```vb
' Put the following declaration at module level (not in any procedure).
Private strMsg As String
' Put the following Sub procedure in the same module.
Sub initializePrivateVariable()
    strMsg = "This variable cannot be used outside this module."
End Sub
' Put the following Sub procedure in the same module.
Sub usePrivateVariable()
    MsgBox(strMsg)
End Sub
```

### <a name="namespace-scope"></a><span data-ttu-id="0651c-162">Portée espace de noms</span><span class="sxs-lookup"><span data-stu-id="0651c-162">Namespace Scope</span></span>

<span data-ttu-id="0651c-163">Si vous déclarez un élément au niveau du module à l’aide du mot clé [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) ou [public](../../../../visual-basic/language-reference/modifiers/public.md) , il devient disponible pour toutes les procédures dans l’espace de noms dans lequel l’élément est déclaré.</span><span class="sxs-lookup"><span data-stu-id="0651c-163">If you declare an element at module level using the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword, it becomes available to all procedures throughout the namespace in which the element is declared.</span></span> <span data-ttu-id="0651c-164">Avec la modification suivante apporte à l’exemple précédent, la `strMsg` variable de chaîne peut être référencée par du code n’importe où dans l’espace de noms de sa déclaration.</span><span class="sxs-lookup"><span data-stu-id="0651c-164">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>

```vb
' Include this declaration at module level (not inside any procedure).
Public strMsg As String
```

<span data-ttu-id="0651c-165">La portée espace de noms comprend des espaces de noms imbriqués.</span><span class="sxs-lookup"><span data-stu-id="0651c-165">Namespace scope includes nested namespaces.</span></span> <span data-ttu-id="0651c-166">Un élément disponible à partir d’un espace de noms est également disponible à partir de n’importe quel espace de noms imbriqué dans cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="0651c-166">An element available from within a namespace is also available from within any namespace nested inside that namespace.</span></span>

<span data-ttu-id="0651c-167">Si votre projet ne contient pas d' [instruction d’espace de noms](../../../../visual-basic/language-reference/statements/namespace-statement.md), tous les éléments du projet se trouvent dans le même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="0651c-167">If your project does not contain any [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md)s, everything in the project is in the same namespace.</span></span> <span data-ttu-id="0651c-168">Dans ce cas, l’étendue de l’espace de noms peut être considérée comme la portée du projet.</span><span class="sxs-lookup"><span data-stu-id="0651c-168">In this case, namespace scope can be thought of as project scope.</span></span> <span data-ttu-id="0651c-169">`Public`les éléments d’un module, d’une classe ou d’une structure sont également disponibles pour tous les projets qui font référence à leur projet.</span><span class="sxs-lookup"><span data-stu-id="0651c-169">`Public` elements in a module, class, or structure are also available to any project that references their project.</span></span>

## <a name="choice-of-scope"></a><span data-ttu-id="0651c-170">Choix de l’étendue</span><span class="sxs-lookup"><span data-stu-id="0651c-170">Choice of Scope</span></span>

<span data-ttu-id="0651c-171">Lorsque vous déclarez une variable, gardez à l’esprit les points suivants lorsque vous choisissez son étendue.</span><span class="sxs-lookup"><span data-stu-id="0651c-171">When you declare a variable, you should keep in mind the following points when choosing its scope.</span></span>

### <a name="advantages-of-local-variables"></a><span data-ttu-id="0651c-172">Avantages des variables locales</span><span class="sxs-lookup"><span data-stu-id="0651c-172">Advantages of Local Variables</span></span>

<span data-ttu-id="0651c-173">Les variables locales sont un bon choix pour tout type de calcul temporaire, pour les raisons suivantes:</span><span class="sxs-lookup"><span data-stu-id="0651c-173">Local variables are a good choice for any kind of temporary calculation, for the following reasons:</span></span>

- <span data-ttu-id="0651c-174">**Évitement des conflits de noms.**</span><span class="sxs-lookup"><span data-stu-id="0651c-174">**Name Conflict Avoidance.**</span></span> <span data-ttu-id="0651c-175">Les noms de variables locales ne sont pas susceptibles d’être en conflit.</span><span class="sxs-lookup"><span data-stu-id="0651c-175">Local variable names are not susceptible to conflict.</span></span> <span data-ttu-id="0651c-176">Par exemple, vous pouvez créer plusieurs procédures différentes contenant une variable appelée `intTemp`.</span><span class="sxs-lookup"><span data-stu-id="0651c-176">For example, you can create several different procedures containing a variable called `intTemp`.</span></span> <span data-ttu-id="0651c-177">Tant que chaque `intTemp` est déclarée en tant que variable locale, chaque procédure reconnaît uniquement sa propre version `intTemp`de.</span><span class="sxs-lookup"><span data-stu-id="0651c-177">As long as each `intTemp` is declared as a local variable, each procedure recognizes only its own version of `intTemp`.</span></span> <span data-ttu-id="0651c-178">Toute procédure peut modifier la valeur de son local `intTemp` sans affecter `intTemp` les variables dans d’autres procédures.</span><span class="sxs-lookup"><span data-stu-id="0651c-178">Any one procedure can alter the value in its local `intTemp` without affecting `intTemp` variables in other procedures.</span></span>

- <span data-ttu-id="0651c-179">**Consommation de mémoire.**</span><span class="sxs-lookup"><span data-stu-id="0651c-179">**Memory Consumption.**</span></span> <span data-ttu-id="0651c-180">Les variables locales consomment de la mémoire uniquement lorsque leur procédure est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0651c-180">Local variables consume memory only while their procedure is running.</span></span> <span data-ttu-id="0651c-181">Leur mémoire est libérée lorsque la procédure retourne au code appelant.</span><span class="sxs-lookup"><span data-stu-id="0651c-181">Their memory is released when the procedure returns to the calling code.</span></span> <span data-ttu-id="0651c-182">En revanche, les variables [partagées](../../../../visual-basic/language-reference/modifiers/shared.md) et [statiques](../../../../visual-basic/language-reference/modifiers/static.md) consomment des ressources mémoire jusqu’à ce que votre application cesse de s’exécuter. Utilisez-les uniquement lorsque cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="0651c-182">By contrast, [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) and [Static](../../../../visual-basic/language-reference/modifiers/static.md) variables consume memory resources until your application stops running, so use them only when necessary.</span></span> <span data-ttu-id="0651c-183">Les *variables d’instance* consomment de la mémoire, tandis que leur instance continue à exister, ce qui les rend moins `Shared` efficaces que les variables locales, mais potentiellement plus efficaces que les variables ou. `Static`</span><span class="sxs-lookup"><span data-stu-id="0651c-183">*Instance variables* consume memory while their instance continues to exist, which makes them less efficient than local variables, but potentially more efficient than `Shared` or `Static` variables.</span></span>

### <a name="minimizing-scope"></a><span data-ttu-id="0651c-184">Réduire l’étendue</span><span class="sxs-lookup"><span data-stu-id="0651c-184">Minimizing Scope</span></span>

<span data-ttu-id="0651c-185">En général, lors de la déclaration d’une variable ou d’une constante, il est recommandé de faire de la portée le plus étroit possible (la portée de bloc est la plus étroite).</span><span class="sxs-lookup"><span data-stu-id="0651c-185">In general, when declaring any variable or constant, it is good programming practice to make the scope as narrow as possible (block scope is the narrowest).</span></span> <span data-ttu-id="0651c-186">Cela permet d’économiser de la mémoire et réduit les chances que votre code fasse référence à la mauvaise variable.</span><span class="sxs-lookup"><span data-stu-id="0651c-186">This helps conserve memory and minimizes the chances of your code erroneously referring to the wrong variable.</span></span> <span data-ttu-id="0651c-187">De même, vous devez déclarer une variable comme étant [statique](../../../../visual-basic/language-reference/modifiers/static.md) uniquement lorsqu’il est nécessaire de conserver sa valeur entre les appels de procédure.</span><span class="sxs-lookup"><span data-stu-id="0651c-187">Similarly, you should declare a variable to be [Static](../../../../visual-basic/language-reference/modifiers/static.md) only when it is necessary to preserve its value between procedure calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="0651c-188">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0651c-188">See also</span></span>

- [<span data-ttu-id="0651c-189">Caractéristiques d’éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="0651c-189">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="0651c-190">Guide pratique pour Contrôler l’étendue d’une variable</span><span class="sxs-lookup"><span data-stu-id="0651c-190">How to: Control the Scope of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="0651c-191">Durée de vie dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0651c-191">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="0651c-192">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0651c-192">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="0651c-193">Références aux éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="0651c-193">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="0651c-194">Déclaration de variable</span><span class="sxs-lookup"><span data-stu-id="0651c-194">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
