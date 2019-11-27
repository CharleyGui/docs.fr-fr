---
title: Enum, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: 48220fd1e88cf38e67db5dd3a2ad90638eb6b6df
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343711"
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="c3963-102">Enum, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3963-102">Enum Statement (Visual Basic)</span></span>

<span data-ttu-id="c3963-103">Déclare une énumération et définit les valeurs de ses membres.</span><span class="sxs-lookup"><span data-stu-id="c3963-103">Declares an enumeration and defines the values of its members.</span></span>

## <a name="syntax"></a><span data-ttu-id="c3963-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3963-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]
Enum enumerationname [ As datatype ]
   memberlist
End Enum
```

## <a name="parts"></a><span data-ttu-id="c3963-105">Composants</span><span class="sxs-lookup"><span data-stu-id="c3963-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="c3963-106">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="c3963-106">Optional.</span></span> <span data-ttu-id="c3963-107">Liste des attributs qui s’appliquent à cette énumération.</span><span class="sxs-lookup"><span data-stu-id="c3963-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="c3963-108">Vous devez placer la [liste des attributs](../../../visual-basic/language-reference/statements/attribute-list.md) entre crochets pointus («`<`» et «`>`»).</span><span class="sxs-lookup"><span data-stu-id="c3963-108">You must enclose the [attribute list](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

  <span data-ttu-id="c3963-109">L’attribut <xref:System.FlagsAttribute> indique que la valeur d’une instance de l’énumération peut inclure plusieurs membres de l’énumération, et que chaque membre représente un champ de bits dans la valeur d’énumération.</span><span class="sxs-lookup"><span data-stu-id="c3963-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>

- `accessmodifier`

  <span data-ttu-id="c3963-110">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="c3963-110">Optional.</span></span> <span data-ttu-id="c3963-111">Spécifie le code qui peut accéder à cette énumération.</span><span class="sxs-lookup"><span data-stu-id="c3963-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="c3963-112">Il peut s'agir de l'un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="c3963-112">Can be one of the following:</span></span>

  - [<span data-ttu-id="c3963-113">Public</span><span class="sxs-lookup"><span data-stu-id="c3963-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)

  - [<span data-ttu-id="c3963-114">Protected</span><span class="sxs-lookup"><span data-stu-id="c3963-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)

  - [<span data-ttu-id="c3963-115">Friend</span><span class="sxs-lookup"><span data-stu-id="c3963-115">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)

  - [<span data-ttu-id="c3963-116">Private</span><span class="sxs-lookup"><span data-stu-id="c3963-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)

  - [<span data-ttu-id="c3963-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="c3963-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

  - [<span data-ttu-id="c3963-118">Private Protected</span><span class="sxs-lookup"><span data-stu-id="c3963-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

- `Shadows`

  <span data-ttu-id="c3963-119">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="c3963-119">Optional.</span></span> <span data-ttu-id="c3963-120">Spécifie que cette énumération redéclare et masque un élément de programmation portant le même nom, ou un ensemble d’éléments surchargés, dans une classe de base.</span><span class="sxs-lookup"><span data-stu-id="c3963-120">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="c3963-121">Vous pouvez spécifier des [ombres](../../../visual-basic/language-reference/modifiers/shadows.md) uniquement sur l’énumération elle-même, et non sur l’un de ses membres.</span><span class="sxs-lookup"><span data-stu-id="c3963-121">You can specify [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>

- `enumerationname`

  <span data-ttu-id="c3963-122">Requis.</span><span class="sxs-lookup"><span data-stu-id="c3963-122">Required.</span></span> <span data-ttu-id="c3963-123">Nom de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="c3963-123">Name of the enumeration.</span></span> <span data-ttu-id="c3963-124">Pour plus d’informations sur les noms valides, consultez [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="c3963-124">For information on valid names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `datatype`

  <span data-ttu-id="c3963-125">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="c3963-125">Optional.</span></span> <span data-ttu-id="c3963-126">Type de données de l’énumération et de tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="c3963-126">Data type of the enumeration and all its members.</span></span>

- `memberlist`

  <span data-ttu-id="c3963-127">Requis.</span><span class="sxs-lookup"><span data-stu-id="c3963-127">Required.</span></span> <span data-ttu-id="c3963-128">Liste des constantes membres déclarées dans cette instruction.</span><span class="sxs-lookup"><span data-stu-id="c3963-128">List of member constants being declared in this statement.</span></span> <span data-ttu-id="c3963-129">Plusieurs membres apparaissent sur des lignes de code source individuelles.</span><span class="sxs-lookup"><span data-stu-id="c3963-129">Multiple members appear on individual source code lines.</span></span>

  <span data-ttu-id="c3963-130">Chaque `member` possède la syntaxe et les parties suivantes : `[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="c3963-130">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>

  |<span data-ttu-id="c3963-131">Élément</span><span class="sxs-lookup"><span data-stu-id="c3963-131">Part</span></span>|<span data-ttu-id="c3963-132">Description</span><span class="sxs-lookup"><span data-stu-id="c3963-132">Description</span></span>|
  |---|---|
  |`membername`|<span data-ttu-id="c3963-133">Requis.</span><span class="sxs-lookup"><span data-stu-id="c3963-133">Required.</span></span> <span data-ttu-id="c3963-134">Nom de ce membre.</span><span class="sxs-lookup"><span data-stu-id="c3963-134">Name of this member.</span></span>|
  |`initializer`|<span data-ttu-id="c3963-135">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="c3963-135">Optional.</span></span> <span data-ttu-id="c3963-136">Expression évaluée au moment de la compilation et assignée à ce membre.</span><span class="sxs-lookup"><span data-stu-id="c3963-136">Expression that is evaluated at compile time and assigned to this member.</span></span>|

- <span data-ttu-id="c3963-137">`End` `Enum`</span><span class="sxs-lookup"><span data-stu-id="c3963-137">`End` `Enum`</span></span>

  <span data-ttu-id="c3963-138">Met fin au bloc `Enum`.</span><span class="sxs-lookup"><span data-stu-id="c3963-138">Terminates the `Enum` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3963-139">Notes</span><span class="sxs-lookup"><span data-stu-id="c3963-139">Remarks</span></span>

<span data-ttu-id="c3963-140">Si vous avez un ensemble de valeurs immuables qui sont logiquement liées entre elles, vous pouvez les définir ensemble dans une énumération.</span><span class="sxs-lookup"><span data-stu-id="c3963-140">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="c3963-141">Cela fournit des noms explicites pour l’énumération et ses membres, qui sont plus faciles à mémoriser que leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="c3963-141">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="c3963-142">Vous pouvez ensuite utiliser les membres de l’énumération à de nombreux emplacements de votre code.</span><span class="sxs-lookup"><span data-stu-id="c3963-142">You can then use the enumeration members in many places in your code.</span></span>

<span data-ttu-id="c3963-143">Les avantages de l’utilisation des énumérations sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="c3963-143">The benefits of using enumerations include the following:</span></span>

- <span data-ttu-id="c3963-144">Réduit les erreurs dues à la transposition ou à la frappe de nombres.</span><span class="sxs-lookup"><span data-stu-id="c3963-144">Reduces errors caused by transposing or mistyping numbers.</span></span>

- <span data-ttu-id="c3963-145">Facilite la modification des valeurs à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="c3963-145">Makes it easy to change values in the future.</span></span>

- <span data-ttu-id="c3963-146">Rend le code plus facile à lire, ce qui signifie qu’il est moins probable que des erreurs soient introduites.</span><span class="sxs-lookup"><span data-stu-id="c3963-146">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>

- <span data-ttu-id="c3963-147">Garantit la compatibilité ascendante.</span><span class="sxs-lookup"><span data-stu-id="c3963-147">Ensures forward compatibility.</span></span> <span data-ttu-id="c3963-148">Si vous utilisez des énumérations, votre code risque d’échouer si, à l’avenir, un utilisateur modifie les valeurs correspondant aux noms des membres.</span><span class="sxs-lookup"><span data-stu-id="c3963-148">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>

<span data-ttu-id="c3963-149">Une énumération a un nom, un type de données sous-jacent et un ensemble de membres.</span><span class="sxs-lookup"><span data-stu-id="c3963-149">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="c3963-150">Chaque membre représente une constante.</span><span class="sxs-lookup"><span data-stu-id="c3963-150">Each member represents a constant.</span></span>

<span data-ttu-id="c3963-151">Une énumération déclarée au niveau de la classe, de la structure, du module ou de l’interface, en dehors de toute procédure, est une *énumération de membre*.</span><span class="sxs-lookup"><span data-stu-id="c3963-151">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="c3963-152">Il est membre de la classe, de la structure, du module ou de l’interface qui le déclare.</span><span class="sxs-lookup"><span data-stu-id="c3963-152">It is a member of the class, structure, module, or interface that declares it.</span></span>

<span data-ttu-id="c3963-153">Les énumérations de membres sont accessibles à partir de n’importe quel emplacement dans leur classe, structure, module ou interface.</span><span class="sxs-lookup"><span data-stu-id="c3963-153">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="c3963-154">Le code en dehors d’une classe, d’une structure ou d’un module doit qualifier le nom d’une énumération de membre avec le nom de la classe, de la structure ou du module.</span><span class="sxs-lookup"><span data-stu-id="c3963-154">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="c3963-155">Vous pouvez éviter d’avoir à utiliser des noms qualifiés complets en ajoutant une instruction [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) au fichier source.</span><span class="sxs-lookup"><span data-stu-id="c3963-155">You can avoid the need to use fully qualified names by adding an [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>

<span data-ttu-id="c3963-156">Une énumération déclarée au niveau de l’espace de noms, en dehors d’une classe, d’une structure, d’un module ou d’une interface, est un membre de l’espace de noms dans lequel elle apparaît.</span><span class="sxs-lookup"><span data-stu-id="c3963-156">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>

<span data-ttu-id="c3963-157">Le *contexte de déclaration* pour une énumération doit être un fichier source, un espace de noms, une classe, une structure, un module ou une interface, et ne peut pas être une procédure.</span><span class="sxs-lookup"><span data-stu-id="c3963-157">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="c3963-158">Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c3963-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="c3963-159">Vous pouvez appliquer des attributs à une énumération dans son ensemble, mais pas à ses membres individuellement.</span><span class="sxs-lookup"><span data-stu-id="c3963-159">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="c3963-160">Un attribut fournit des informations aux métadonnées de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="c3963-160">An attribute contributes information to the assembly's metadata.</span></span>

## <a name="data-type"></a><span data-ttu-id="c3963-161">Type de données</span><span class="sxs-lookup"><span data-stu-id="c3963-161">Data Type</span></span>

<span data-ttu-id="c3963-162">L’instruction `Enum` peut déclarer le type de données d’une énumération.</span><span class="sxs-lookup"><span data-stu-id="c3963-162">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="c3963-163">Chaque membre prend le type de données de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="c3963-163">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="c3963-164">Vous pouvez spécifier `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`ou `UShort`.</span><span class="sxs-lookup"><span data-stu-id="c3963-164">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>

<span data-ttu-id="c3963-165">Si vous ne spécifiez pas `datatype` pour l’énumération, chaque membre prend le type de données de son `initializer`.</span><span class="sxs-lookup"><span data-stu-id="c3963-165">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="c3963-166">Si vous spécifiez à la fois `datatype` et `initializer`, le type de données de `initializer` doit être convertible en `datatype`.</span><span class="sxs-lookup"><span data-stu-id="c3963-166">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="c3963-167">Si ni `datatype` ni `initializer` n’est présent, le type de données prend par défaut la valeur `Integer`.</span><span class="sxs-lookup"><span data-stu-id="c3963-167">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>

## <a name="initializing-members"></a><span data-ttu-id="c3963-168">Initialisation des membres</span><span class="sxs-lookup"><span data-stu-id="c3963-168">Initializing Members</span></span>

<span data-ttu-id="c3963-169">L’instruction `Enum` peut initialiser le contenu des membres sélectionnés dans `memberlist`.</span><span class="sxs-lookup"><span data-stu-id="c3963-169">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="c3963-170">Vous utilisez `initializer` pour fournir une expression à assigner au membre.</span><span class="sxs-lookup"><span data-stu-id="c3963-170">You use `initializer` to supply an expression to be assigned to the member.</span></span>

<span data-ttu-id="c3963-171">Si vous ne spécifiez pas `initializer` pour un membre, Visual Basic l’initialise soit sur zéro (s’il s’agit du premier `member` dans `memberlist`), soit sur une valeur supérieure à celle de la `member`précédente.</span><span class="sxs-lookup"><span data-stu-id="c3963-171">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>

<span data-ttu-id="c3963-172">L’expression fournie dans chaque `initializer` peut être n’importe quelle combinaison de littéraux, d’autres constantes déjà définies et de membres d’énumération qui sont déjà définis, y compris un membre précédent de cette énumération.</span><span class="sxs-lookup"><span data-stu-id="c3963-172">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="c3963-173">Vous pouvez utiliser des opérateurs arithmétiques et logiques pour combiner de tels éléments.</span><span class="sxs-lookup"><span data-stu-id="c3963-173">You can use arithmetic and logical operators to combine such elements.</span></span>

<span data-ttu-id="c3963-174">Vous ne pouvez pas utiliser de variables ou de fonctions dans `initializer`.</span><span class="sxs-lookup"><span data-stu-id="c3963-174">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="c3963-175">Toutefois, vous pouvez utiliser des mots clés de conversion tels que `CByte` et `CShort`.</span><span class="sxs-lookup"><span data-stu-id="c3963-175">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="c3963-176">Vous pouvez également utiliser `AscW` si vous l’appelez avec une constante `String` ou `Char` argument, car cela peut être évalué au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="c3963-176">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>

<span data-ttu-id="c3963-177">Les énumérations ne peuvent pas avoir de valeurs à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="c3963-177">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="c3963-178">Si une valeur à virgule flottante est assignée à un membre et que `Option Strict` a la valeur on, une erreur de compilateur se produit.</span><span class="sxs-lookup"><span data-stu-id="c3963-178">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="c3963-179">Si `Option Strict` a la valeur OFF, la valeur est automatiquement convertie en type `Enum`.</span><span class="sxs-lookup"><span data-stu-id="c3963-179">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>

<span data-ttu-id="c3963-180">Si la valeur d’un membre dépasse la plage autorisée pour le type de données sous-jacent, ou si vous initialisez un membre avec la valeur maximale autorisée par le type de données sous-jacent, le compilateur signale une erreur.</span><span class="sxs-lookup"><span data-stu-id="c3963-180">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>

## <a name="modifiers"></a><span data-ttu-id="c3963-181">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="c3963-181">Modifiers</span></span>

<span data-ttu-id="c3963-182">Les énumérations des classes, des structures, des modules et des membres d’interface sont par défaut accessibles au public.</span><span class="sxs-lookup"><span data-stu-id="c3963-182">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="c3963-183">Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès.</span><span class="sxs-lookup"><span data-stu-id="c3963-183">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="c3963-184">Les énumérations de membres d’espaces de noms ont par défaut accès Friend.</span><span class="sxs-lookup"><span data-stu-id="c3963-184">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="c3963-185">Vous pouvez régler leurs niveaux d’accès sur public, mais pas sur privé ou protégé.</span><span class="sxs-lookup"><span data-stu-id="c3963-185">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="c3963-186">Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c3963-186">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="c3963-187">Tous les membres de l’énumération ont un accès public et vous ne pouvez pas utiliser de modificateurs d’accès sur ceux-ci.</span><span class="sxs-lookup"><span data-stu-id="c3963-187">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="c3963-188">Toutefois, si l’énumération elle-même a un niveau d’accès plus restreint, le niveau d’accès de l’énumération spécifié est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="c3963-188">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>

<span data-ttu-id="c3963-189">Par défaut, toutes les énumérations sont des types et leurs champs sont des constantes.</span><span class="sxs-lookup"><span data-stu-id="c3963-189">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="c3963-190">Par conséquent, les mots clés `Shared`, `Static`et `ReadOnly` ne peuvent pas être utilisés lors de la déclaration d’une énumération ou de ses membres.</span><span class="sxs-lookup"><span data-stu-id="c3963-190">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>

## <a name="assigning-multiple-values"></a><span data-ttu-id="c3963-191">Attribution de plusieurs valeurs</span><span class="sxs-lookup"><span data-stu-id="c3963-191">Assigning Multiple Values</span></span>

<span data-ttu-id="c3963-192">Les énumérations représentent généralement des valeurs mutuellement exclusives.</span><span class="sxs-lookup"><span data-stu-id="c3963-192">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="c3963-193">En incluant l’attribut <xref:System.FlagsAttribute> dans la déclaration `Enum`, vous pouvez à la place assigner plusieurs valeurs à une instance de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="c3963-193">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="c3963-194">L’attribut <xref:System.FlagsAttribute> spécifie que l’énumération doit être traitée comme un champ de bits, c’est-à-dire un ensemble d’indicateurs.</span><span class="sxs-lookup"><span data-stu-id="c3963-194">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="c3963-195">Il s’agit des énumérations de *bits* .</span><span class="sxs-lookup"><span data-stu-id="c3963-195">These are called *bitwise* enumerations.</span></span>

<span data-ttu-id="c3963-196">Quand vous déclarez une énumération à l’aide de l’attribut <xref:System.FlagsAttribute>, nous vous recommandons d’utiliser les puissances de 2, c’est-à-dire 1, 2, 4, 8, 16, et ainsi de suite, pour les valeurs.</span><span class="sxs-lookup"><span data-stu-id="c3963-196">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="c3963-197">Nous recommandons également que « None » soit le nom d’un membre dont la valeur est 0.</span><span class="sxs-lookup"><span data-stu-id="c3963-197">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="c3963-198">Pour obtenir des instructions supplémentaires, consultez <xref:System.FlagsAttribute> et <xref:System.Enum>.</span><span class="sxs-lookup"><span data-stu-id="c3963-198">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>

## <a name="example"></a><span data-ttu-id="c3963-199">Exemple</span><span class="sxs-lookup"><span data-stu-id="c3963-199">Example</span></span>

<span data-ttu-id="c3963-200">L’exemple suivant montre comment utiliser l’instruction `Enum`.</span><span class="sxs-lookup"><span data-stu-id="c3963-200">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="c3963-201">Notez que le membre est appelé `EggSizeEnum.Medium`et non pas comme `Medium`.</span><span class="sxs-lookup"><span data-stu-id="c3963-201">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a><span data-ttu-id="c3963-202">Exemple</span><span class="sxs-lookup"><span data-stu-id="c3963-202">Example</span></span>

<span data-ttu-id="c3963-203">La méthode de l’exemple suivant est en dehors de la classe `Egg`.</span><span class="sxs-lookup"><span data-stu-id="c3963-203">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="c3963-204">Par conséquent, `EggSizeEnum` est entièrement qualifié en tant que `Egg.EggSizeEnum`.</span><span class="sxs-lookup"><span data-stu-id="c3963-204">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a><span data-ttu-id="c3963-205">Exemple</span><span class="sxs-lookup"><span data-stu-id="c3963-205">Example</span></span>

<span data-ttu-id="c3963-206">L’exemple suivant utilise l’instruction `Enum` pour définir un ensemble de valeurs constantes nommées.</span><span class="sxs-lookup"><span data-stu-id="c3963-206">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="c3963-207">Dans ce cas, les valeurs sont des couleurs que vous pouvez choisir pour concevoir des formulaires d’entrée de données pour une base de données.</span><span class="sxs-lookup"><span data-stu-id="c3963-207">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a><span data-ttu-id="c3963-208">Exemple</span><span class="sxs-lookup"><span data-stu-id="c3963-208">Example</span></span>

<span data-ttu-id="c3963-209">L’exemple suivant montre des valeurs qui incluent à la fois des nombres positifs et négatifs.</span><span class="sxs-lookup"><span data-stu-id="c3963-209">The following example shows values that include both positive and negative numbers.</span></span>

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a><span data-ttu-id="c3963-210">Exemple</span><span class="sxs-lookup"><span data-stu-id="c3963-210">Example</span></span>

<span data-ttu-id="c3963-211">Dans l’exemple suivant, une clause `As` est utilisée pour spécifier le `datatype` d’une énumération.</span><span class="sxs-lookup"><span data-stu-id="c3963-211">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a><span data-ttu-id="c3963-212">Exemple</span><span class="sxs-lookup"><span data-stu-id="c3963-212">Example</span></span>

<span data-ttu-id="c3963-213">L’exemple suivant montre comment utiliser une énumération au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="c3963-213">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="c3963-214">Plusieurs valeurs peuvent être assignées à une instance d’une énumération au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="c3963-214">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="c3963-215">La déclaration `Enum` comprend l’attribut <xref:System.FlagsAttribute>, qui indique que l’énumération peut être traitée comme un jeu d’indicateurs.</span><span class="sxs-lookup"><span data-stu-id="c3963-215">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a><span data-ttu-id="c3963-216">Exemple</span><span class="sxs-lookup"><span data-stu-id="c3963-216">Example</span></span>

<span data-ttu-id="c3963-217">L’exemple suivant itère au sein d’une énumération.</span><span class="sxs-lookup"><span data-stu-id="c3963-217">The following example iterates through an enumeration.</span></span> <span data-ttu-id="c3963-218">Elle utilise la méthode <xref:System.Enum.GetNames%2A> pour récupérer un tableau de noms de membres de l’énumération, et <xref:System.Enum.GetValues%2A> pour récupérer un tableau de valeurs de membre.</span><span class="sxs-lookup"><span data-stu-id="c3963-218">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="c3963-219">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3963-219">See also</span></span>

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="c3963-220">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="c3963-220">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="c3963-221">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="c3963-221">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="c3963-222">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="c3963-222">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="c3963-223">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="c3963-223">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="c3963-224">Constantes et énumérations</span><span class="sxs-lookup"><span data-stu-id="c3963-224">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
