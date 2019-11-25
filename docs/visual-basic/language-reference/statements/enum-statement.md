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
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="a47ee-102">Enum, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a47ee-102">Enum Statement (Visual Basic)</span></span>

<span data-ttu-id="a47ee-103">Declares an enumeration and defines the values of its members.</span><span class="sxs-lookup"><span data-stu-id="a47ee-103">Declares an enumeration and defines the values of its members.</span></span>

## <a name="syntax"></a><span data-ttu-id="a47ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a47ee-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]
Enum enumerationname [ As datatype ]
   memberlist
End Enum
```

## <a name="parts"></a><span data-ttu-id="a47ee-105">Composants</span><span class="sxs-lookup"><span data-stu-id="a47ee-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="a47ee-106">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="a47ee-106">Optional.</span></span> <span data-ttu-id="a47ee-107">List of attributes that apply to this enumeration.</span><span class="sxs-lookup"><span data-stu-id="a47ee-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="a47ee-108">You must enclose the [attribute list](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span><span class="sxs-lookup"><span data-stu-id="a47ee-108">You must enclose the [attribute list](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

  <span data-ttu-id="a47ee-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span><span class="sxs-lookup"><span data-stu-id="a47ee-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>

- `accessmodifier`

  <span data-ttu-id="a47ee-110">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="a47ee-110">Optional.</span></span> <span data-ttu-id="a47ee-111">Specifies what code can access this enumeration.</span><span class="sxs-lookup"><span data-stu-id="a47ee-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="a47ee-112">Il peut s'agir d'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="a47ee-112">Can be one of the following:</span></span>

  - [<span data-ttu-id="a47ee-113">Public</span><span class="sxs-lookup"><span data-stu-id="a47ee-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)

  - [<span data-ttu-id="a47ee-114">Protected</span><span class="sxs-lookup"><span data-stu-id="a47ee-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)

  - [<span data-ttu-id="a47ee-115">Friend</span><span class="sxs-lookup"><span data-stu-id="a47ee-115">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)

  - [<span data-ttu-id="a47ee-116">Private</span><span class="sxs-lookup"><span data-stu-id="a47ee-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)

  - [<span data-ttu-id="a47ee-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="a47ee-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

  - [<span data-ttu-id="a47ee-118">Private Protected</span><span class="sxs-lookup"><span data-stu-id="a47ee-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

- `Shadows`

  <span data-ttu-id="a47ee-119">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="a47ee-119">Optional.</span></span> <span data-ttu-id="a47ee-120">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span><span class="sxs-lookup"><span data-stu-id="a47ee-120">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="a47ee-121">You can specify [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span><span class="sxs-lookup"><span data-stu-id="a47ee-121">You can specify [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>

- `enumerationname`

  <span data-ttu-id="a47ee-122">Requis.</span><span class="sxs-lookup"><span data-stu-id="a47ee-122">Required.</span></span> <span data-ttu-id="a47ee-123">Name of the enumeration.</span><span class="sxs-lookup"><span data-stu-id="a47ee-123">Name of the enumeration.</span></span> <span data-ttu-id="a47ee-124">For information on valid names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="a47ee-124">For information on valid names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `datatype`

  <span data-ttu-id="a47ee-125">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="a47ee-125">Optional.</span></span> <span data-ttu-id="a47ee-126">Data type of the enumeration and all its members.</span><span class="sxs-lookup"><span data-stu-id="a47ee-126">Data type of the enumeration and all its members.</span></span>

- `memberlist`

  <span data-ttu-id="a47ee-127">Requis.</span><span class="sxs-lookup"><span data-stu-id="a47ee-127">Required.</span></span> <span data-ttu-id="a47ee-128">List of member constants being declared in this statement.</span><span class="sxs-lookup"><span data-stu-id="a47ee-128">List of member constants being declared in this statement.</span></span> <span data-ttu-id="a47ee-129">Multiple members appear on individual source code lines.</span><span class="sxs-lookup"><span data-stu-id="a47ee-129">Multiple members appear on individual source code lines.</span></span>

  <span data-ttu-id="a47ee-130">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="a47ee-130">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>

  |<span data-ttu-id="a47ee-131">Élément</span><span class="sxs-lookup"><span data-stu-id="a47ee-131">Part</span></span>|<span data-ttu-id="a47ee-132">Description</span><span class="sxs-lookup"><span data-stu-id="a47ee-132">Description</span></span>|
  |---|---|
  |`membername`|<span data-ttu-id="a47ee-133">Requis.</span><span class="sxs-lookup"><span data-stu-id="a47ee-133">Required.</span></span> <span data-ttu-id="a47ee-134">Name of this member.</span><span class="sxs-lookup"><span data-stu-id="a47ee-134">Name of this member.</span></span>|
  |`initializer`|<span data-ttu-id="a47ee-135">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="a47ee-135">Optional.</span></span> <span data-ttu-id="a47ee-136">Expression that is evaluated at compile time and assigned to this member.</span><span class="sxs-lookup"><span data-stu-id="a47ee-136">Expression that is evaluated at compile time and assigned to this member.</span></span>|

- <span data-ttu-id="a47ee-137">`End` `Enum`</span><span class="sxs-lookup"><span data-stu-id="a47ee-137">`End` `Enum`</span></span>

  <span data-ttu-id="a47ee-138">Met fin au bloc `Enum`.</span><span class="sxs-lookup"><span data-stu-id="a47ee-138">Terminates the `Enum` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="a47ee-139">Notes</span><span class="sxs-lookup"><span data-stu-id="a47ee-139">Remarks</span></span>

<span data-ttu-id="a47ee-140">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span><span class="sxs-lookup"><span data-stu-id="a47ee-140">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="a47ee-141">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span><span class="sxs-lookup"><span data-stu-id="a47ee-141">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="a47ee-142">You can then use the enumeration members in many places in your code.</span><span class="sxs-lookup"><span data-stu-id="a47ee-142">You can then use the enumeration members in many places in your code.</span></span>

<span data-ttu-id="a47ee-143">The benefits of using enumerations include the following:</span><span class="sxs-lookup"><span data-stu-id="a47ee-143">The benefits of using enumerations include the following:</span></span>

- <span data-ttu-id="a47ee-144">Reduces errors caused by transposing or mistyping numbers.</span><span class="sxs-lookup"><span data-stu-id="a47ee-144">Reduces errors caused by transposing or mistyping numbers.</span></span>

- <span data-ttu-id="a47ee-145">Makes it easy to change values in the future.</span><span class="sxs-lookup"><span data-stu-id="a47ee-145">Makes it easy to change values in the future.</span></span>

- <span data-ttu-id="a47ee-146">Makes code easier to read, which means it is less likely that errors will be introduced.</span><span class="sxs-lookup"><span data-stu-id="a47ee-146">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>

- <span data-ttu-id="a47ee-147">Ensures forward compatibility.</span><span class="sxs-lookup"><span data-stu-id="a47ee-147">Ensures forward compatibility.</span></span> <span data-ttu-id="a47ee-148">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span><span class="sxs-lookup"><span data-stu-id="a47ee-148">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>

<span data-ttu-id="a47ee-149">An enumeration has a name, an underlying data type, and a set of members.</span><span class="sxs-lookup"><span data-stu-id="a47ee-149">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="a47ee-150">Each member represents a constant.</span><span class="sxs-lookup"><span data-stu-id="a47ee-150">Each member represents a constant.</span></span>

<span data-ttu-id="a47ee-151">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span><span class="sxs-lookup"><span data-stu-id="a47ee-151">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="a47ee-152">It is a member of the class, structure, module, or interface that declares it.</span><span class="sxs-lookup"><span data-stu-id="a47ee-152">It is a member of the class, structure, module, or interface that declares it.</span></span>

<span data-ttu-id="a47ee-153">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span><span class="sxs-lookup"><span data-stu-id="a47ee-153">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="a47ee-154">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span><span class="sxs-lookup"><span data-stu-id="a47ee-154">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="a47ee-155">You can avoid the need to use fully qualified names by adding an [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statement to the source file.</span><span class="sxs-lookup"><span data-stu-id="a47ee-155">You can avoid the need to use fully qualified names by adding an [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>

<span data-ttu-id="a47ee-156">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span><span class="sxs-lookup"><span data-stu-id="a47ee-156">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>

<span data-ttu-id="a47ee-157">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span><span class="sxs-lookup"><span data-stu-id="a47ee-157">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="a47ee-158">Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a47ee-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="a47ee-159">You can apply attributes to an enumeration as a whole, but not to its members individually.</span><span class="sxs-lookup"><span data-stu-id="a47ee-159">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="a47ee-160">An attribute contributes information to the assembly's metadata.</span><span class="sxs-lookup"><span data-stu-id="a47ee-160">An attribute contributes information to the assembly's metadata.</span></span>

## <a name="data-type"></a><span data-ttu-id="a47ee-161">Type de données</span><span class="sxs-lookup"><span data-stu-id="a47ee-161">Data Type</span></span>

<span data-ttu-id="a47ee-162">The `Enum` statement can declare the data type of an enumeration.</span><span class="sxs-lookup"><span data-stu-id="a47ee-162">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="a47ee-163">Each member takes the enumeration's data type.</span><span class="sxs-lookup"><span data-stu-id="a47ee-163">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="a47ee-164">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span><span class="sxs-lookup"><span data-stu-id="a47ee-164">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>

<span data-ttu-id="a47ee-165">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span><span class="sxs-lookup"><span data-stu-id="a47ee-165">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="a47ee-166">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span><span class="sxs-lookup"><span data-stu-id="a47ee-166">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="a47ee-167">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span><span class="sxs-lookup"><span data-stu-id="a47ee-167">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>

## <a name="initializing-members"></a><span data-ttu-id="a47ee-168">Initializing Members</span><span class="sxs-lookup"><span data-stu-id="a47ee-168">Initializing Members</span></span>

<span data-ttu-id="a47ee-169">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span><span class="sxs-lookup"><span data-stu-id="a47ee-169">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="a47ee-170">You use `initializer` to supply an expression to be assigned to the member.</span><span class="sxs-lookup"><span data-stu-id="a47ee-170">You use `initializer` to supply an expression to be assigned to the member.</span></span>

<span data-ttu-id="a47ee-171">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span><span class="sxs-lookup"><span data-stu-id="a47ee-171">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>

<span data-ttu-id="a47ee-172">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span><span class="sxs-lookup"><span data-stu-id="a47ee-172">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="a47ee-173">You can use arithmetic and logical operators to combine such elements.</span><span class="sxs-lookup"><span data-stu-id="a47ee-173">You can use arithmetic and logical operators to combine such elements.</span></span>

<span data-ttu-id="a47ee-174">You cannot use variables or functions in `initializer`.</span><span class="sxs-lookup"><span data-stu-id="a47ee-174">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="a47ee-175">However, you can use conversion keywords such as `CByte` and `CShort`.</span><span class="sxs-lookup"><span data-stu-id="a47ee-175">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="a47ee-176">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span><span class="sxs-lookup"><span data-stu-id="a47ee-176">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>

<span data-ttu-id="a47ee-177">Enumerations cannot have floating-point values.</span><span class="sxs-lookup"><span data-stu-id="a47ee-177">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="a47ee-178">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span><span class="sxs-lookup"><span data-stu-id="a47ee-178">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="a47ee-179">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span><span class="sxs-lookup"><span data-stu-id="a47ee-179">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>

<span data-ttu-id="a47ee-180">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span><span class="sxs-lookup"><span data-stu-id="a47ee-180">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>

## <a name="modifiers"></a><span data-ttu-id="a47ee-181">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="a47ee-181">Modifiers</span></span>

<span data-ttu-id="a47ee-182">Class, structure, module, and interface member enumerations default to public access.</span><span class="sxs-lookup"><span data-stu-id="a47ee-182">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="a47ee-183">You can adjust their access levels with the access modifiers.</span><span class="sxs-lookup"><span data-stu-id="a47ee-183">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="a47ee-184">Namespace member enumerations default to friend access.</span><span class="sxs-lookup"><span data-stu-id="a47ee-184">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="a47ee-185">You can adjust their access levels to public, but not to private or protected.</span><span class="sxs-lookup"><span data-stu-id="a47ee-185">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="a47ee-186">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a47ee-186">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="a47ee-187">All enumeration members have public access, and you cannot use any access modifiers on them.</span><span class="sxs-lookup"><span data-stu-id="a47ee-187">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="a47ee-188">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span><span class="sxs-lookup"><span data-stu-id="a47ee-188">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>

<span data-ttu-id="a47ee-189">By default, all enumerations are types and their fields are constants.</span><span class="sxs-lookup"><span data-stu-id="a47ee-189">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="a47ee-190">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span><span class="sxs-lookup"><span data-stu-id="a47ee-190">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>

## <a name="assigning-multiple-values"></a><span data-ttu-id="a47ee-191">Assigning Multiple Values</span><span class="sxs-lookup"><span data-stu-id="a47ee-191">Assigning Multiple Values</span></span>

<span data-ttu-id="a47ee-192">Enumerations typically represent mutually exclusive values.</span><span class="sxs-lookup"><span data-stu-id="a47ee-192">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="a47ee-193">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span><span class="sxs-lookup"><span data-stu-id="a47ee-193">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="a47ee-194">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span><span class="sxs-lookup"><span data-stu-id="a47ee-194">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="a47ee-195">These are called *bitwise* enumerations.</span><span class="sxs-lookup"><span data-stu-id="a47ee-195">These are called *bitwise* enumerations.</span></span>

<span data-ttu-id="a47ee-196">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span><span class="sxs-lookup"><span data-stu-id="a47ee-196">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="a47ee-197">We also recommend that "None" be the name of a member whose value is 0.</span><span class="sxs-lookup"><span data-stu-id="a47ee-197">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="a47ee-198">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span><span class="sxs-lookup"><span data-stu-id="a47ee-198">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>

## <a name="example"></a><span data-ttu-id="a47ee-199">Exemple</span><span class="sxs-lookup"><span data-stu-id="a47ee-199">Example</span></span>

<span data-ttu-id="a47ee-200">L’exemple suivant montre comment utiliser l’instruction `Enum`.</span><span class="sxs-lookup"><span data-stu-id="a47ee-200">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="a47ee-201">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span><span class="sxs-lookup"><span data-stu-id="a47ee-201">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a><span data-ttu-id="a47ee-202">Exemple</span><span class="sxs-lookup"><span data-stu-id="a47ee-202">Example</span></span>

<span data-ttu-id="a47ee-203">The method in the following example is outside the `Egg` class.</span><span class="sxs-lookup"><span data-stu-id="a47ee-203">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="a47ee-204">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span><span class="sxs-lookup"><span data-stu-id="a47ee-204">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a><span data-ttu-id="a47ee-205">Exemple</span><span class="sxs-lookup"><span data-stu-id="a47ee-205">Example</span></span>

<span data-ttu-id="a47ee-206">The following example uses the `Enum` statement to define a related set of named constant values.</span><span class="sxs-lookup"><span data-stu-id="a47ee-206">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="a47ee-207">In this case, the values are colors you might choose to design data entry forms for a database.</span><span class="sxs-lookup"><span data-stu-id="a47ee-207">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a><span data-ttu-id="a47ee-208">Exemple</span><span class="sxs-lookup"><span data-stu-id="a47ee-208">Example</span></span>

<span data-ttu-id="a47ee-209">The following example shows values that include both positive and negative numbers.</span><span class="sxs-lookup"><span data-stu-id="a47ee-209">The following example shows values that include both positive and negative numbers.</span></span>

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a><span data-ttu-id="a47ee-210">Exemple</span><span class="sxs-lookup"><span data-stu-id="a47ee-210">Example</span></span>

<span data-ttu-id="a47ee-211">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span><span class="sxs-lookup"><span data-stu-id="a47ee-211">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a><span data-ttu-id="a47ee-212">Exemple</span><span class="sxs-lookup"><span data-stu-id="a47ee-212">Example</span></span>

<span data-ttu-id="a47ee-213">The following example shows how to use a bitwise enumeration.</span><span class="sxs-lookup"><span data-stu-id="a47ee-213">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="a47ee-214">Multiple values can be assigned to an instance of a bitwise enumeration.</span><span class="sxs-lookup"><span data-stu-id="a47ee-214">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="a47ee-215">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span><span class="sxs-lookup"><span data-stu-id="a47ee-215">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a><span data-ttu-id="a47ee-216">Exemple</span><span class="sxs-lookup"><span data-stu-id="a47ee-216">Example</span></span>

<span data-ttu-id="a47ee-217">The following example iterates through an enumeration.</span><span class="sxs-lookup"><span data-stu-id="a47ee-217">The following example iterates through an enumeration.</span></span> <span data-ttu-id="a47ee-218">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span><span class="sxs-lookup"><span data-stu-id="a47ee-218">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="a47ee-219">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a47ee-219">See also</span></span>

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="a47ee-220">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="a47ee-220">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="a47ee-221">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="a47ee-221">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="a47ee-222">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="a47ee-222">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="a47ee-223">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="a47ee-223">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="a47ee-224">Constantes et énumérations</span><span class="sxs-lookup"><span data-stu-id="a47ee-224">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
