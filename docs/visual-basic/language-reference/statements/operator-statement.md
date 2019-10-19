---
title: Instruction Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.operator
helpviewer_keywords:
- operators [Visual Basic]
- procedures [Visual Basic], operator
- Narrowing keyword [Visual Basic], conversion operators
- Visual Basic code, operators
- Widening keyword [Visual Basic], conversion operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
- Operator statement [Visual Basic]
- CType function [Visual Basic], Operator statement
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
ms.openlocfilehash: c4fae40992fa665121aff637ae427ef0cafbf547
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582385"
---
# <a name="operator-statement"></a><span data-ttu-id="15f8a-102">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="15f8a-102">Operator Statement</span></span>

<span data-ttu-id="15f8a-103">Déclare le symbole d’opérateur, les opérandes et le code qui définissent une procédure d’opérateur sur une classe ou une structure.</span><span class="sxs-lookup"><span data-stu-id="15f8a-103">Declares the operator symbol, operands, and code that define an operator procedure on a class or structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="15f8a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15f8a-104">Syntax</span></span>

```vb
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]
    [ statements ]
    [ statements ]
    Return returnvalue
    [ statements ]
End Operator
```

## <a name="parts"></a><span data-ttu-id="15f8a-105">Composants</span><span class="sxs-lookup"><span data-stu-id="15f8a-105">Parts</span></span>

`attrlist`  
<span data-ttu-id="15f8a-106">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="15f8a-106">Optional.</span></span> <span data-ttu-id="15f8a-107">Consultez la [liste des attributs](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="15f8a-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>

`Public`  
<span data-ttu-id="15f8a-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="15f8a-108">Required.</span></span> <span data-ttu-id="15f8a-109">Indique que cette procédure d’opérateur a un accès [public](../../../visual-basic/language-reference/modifiers/public.md) .</span><span class="sxs-lookup"><span data-stu-id="15f8a-109">Indicates that this operator procedure has [Public](../../../visual-basic/language-reference/modifiers/public.md) access.</span></span>

`Overloads`  
<span data-ttu-id="15f8a-110">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="15f8a-110">Optional.</span></span> <span data-ttu-id="15f8a-111">Consultez [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md).</span><span class="sxs-lookup"><span data-stu-id="15f8a-111">See [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md).</span></span>

`Shared`  
<span data-ttu-id="15f8a-112">Requis.</span><span class="sxs-lookup"><span data-stu-id="15f8a-112">Required.</span></span> <span data-ttu-id="15f8a-113">Indique que la procédure d’opérateur est une procédure [partagée](../../../visual-basic/language-reference/modifiers/shared.md) .</span><span class="sxs-lookup"><span data-stu-id="15f8a-113">Indicates that this operator procedure is a [Shared](../../../visual-basic/language-reference/modifiers/shared.md) procedure.</span></span>

`Shadows`  
<span data-ttu-id="15f8a-114">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="15f8a-114">Optional.</span></span> <span data-ttu-id="15f8a-115">Consultez [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="15f8a-115">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>

`Widening`  
<span data-ttu-id="15f8a-116">Obligatoire pour un opérateur de conversion, sauf si vous spécifiez `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="15f8a-116">Required for a conversion operator unless you specify `Narrowing`.</span></span> <span data-ttu-id="15f8a-117">Indique que cette procédure d’opérateur définit une conversion [étendue](../../../visual-basic/language-reference/modifiers/widening.md) .</span><span class="sxs-lookup"><span data-stu-id="15f8a-117">Indicates that this operator procedure defines a [Widening](../../../visual-basic/language-reference/modifiers/widening.md) conversion.</span></span> <span data-ttu-id="15f8a-118">Pour plus d’informations, consultez « Conversions étendues et restrictives » dans cette page d’aide.</span><span class="sxs-lookup"><span data-stu-id="15f8a-118">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`Narrowing`  
<span data-ttu-id="15f8a-119">Obligatoire pour un opérateur de conversion, sauf si vous spécifiez `Widening`.</span><span class="sxs-lookup"><span data-stu-id="15f8a-119">Required for a conversion operator unless you specify `Widening`.</span></span> <span data-ttu-id="15f8a-120">Indique que cette procédure d’opérateur définit une conversion [restrictive](../../../visual-basic/language-reference/modifiers/narrowing.md) .</span><span class="sxs-lookup"><span data-stu-id="15f8a-120">Indicates that this operator procedure defines a [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) conversion.</span></span> <span data-ttu-id="15f8a-121">Pour plus d’informations, consultez « Conversions étendues et restrictives » dans cette page d’aide.</span><span class="sxs-lookup"><span data-stu-id="15f8a-121">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`operatorsymbol`  
<span data-ttu-id="15f8a-122">Requis.</span><span class="sxs-lookup"><span data-stu-id="15f8a-122">Required.</span></span> <span data-ttu-id="15f8a-123">Symbole ou identificateur de l’opérateur défini par cette procédure d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="15f8a-123">The symbol or identifier of the operator that this operator procedure defines.</span></span>

`operand1`  
<span data-ttu-id="15f8a-124">Requis.</span><span class="sxs-lookup"><span data-stu-id="15f8a-124">Required.</span></span> <span data-ttu-id="15f8a-125">Nom et type de l’opérande unique d’un opérateur unaire (y compris un opérateur de conversion) ou de l’opérande gauche d’un opérateur binaire.</span><span class="sxs-lookup"><span data-stu-id="15f8a-125">The name and type of the single operand of a unary operator (including a conversion operator) or the left operand of a binary operator.</span></span>

`operand2`  
<span data-ttu-id="15f8a-126">Requis pour les opérateurs binaires.</span><span class="sxs-lookup"><span data-stu-id="15f8a-126">Required for binary operators.</span></span> <span data-ttu-id="15f8a-127">Nom et type de l’opérande droit d’un opérateur binaire.</span><span class="sxs-lookup"><span data-stu-id="15f8a-127">The name and type of the right operand of a binary operator.</span></span>

<span data-ttu-id="15f8a-128">`operand1` et `operand2` avoir la syntaxe et les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="15f8a-128">`operand1` and `operand2` have the following syntax and parts:</span></span>

`[ ByVal ] operandname [ As operandtype ]`

|<span data-ttu-id="15f8a-129">Élément</span><span class="sxs-lookup"><span data-stu-id="15f8a-129">Part</span></span>|<span data-ttu-id="15f8a-130">Description</span><span class="sxs-lookup"><span data-stu-id="15f8a-130">Description</span></span>|
|----------|-----------------|
|`ByVal`|<span data-ttu-id="15f8a-131">Facultatif, mais le mécanisme de passage doit être [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="15f8a-131">Optional, but the passing mechanism must be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>|
|`operandname`|<span data-ttu-id="15f8a-132">Requis.</span><span class="sxs-lookup"><span data-stu-id="15f8a-132">Required.</span></span> <span data-ttu-id="15f8a-133">Nom de la variable représentant cet opérande.</span><span class="sxs-lookup"><span data-stu-id="15f8a-133">Name of the variable representing this operand.</span></span> <span data-ttu-id="15f8a-134">Consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="15f8a-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`operandtype`|<span data-ttu-id="15f8a-135">Facultatif, sauf si `Option Strict` n’est `On`.</span><span class="sxs-lookup"><span data-stu-id="15f8a-135">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="15f8a-136">Type de données de cet opérande.</span><span class="sxs-lookup"><span data-stu-id="15f8a-136">Data type of this operand.</span></span>|

`type`  
<span data-ttu-id="15f8a-137">Facultatif, sauf si `Option Strict` n’est `On`.</span><span class="sxs-lookup"><span data-stu-id="15f8a-137">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="15f8a-138">Type de données de la valeur retournée par la procédure d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="15f8a-138">Data type of the value the operator procedure returns.</span></span>

`statements`  
<span data-ttu-id="15f8a-139">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="15f8a-139">Optional.</span></span> <span data-ttu-id="15f8a-140">Bloc d’instructions exécutées par la procédure d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="15f8a-140">Block of statements that the operator procedure runs.</span></span>

`returnvalue`  
<span data-ttu-id="15f8a-141">Requis.</span><span class="sxs-lookup"><span data-stu-id="15f8a-141">Required.</span></span> <span data-ttu-id="15f8a-142">Valeur que la procédure d’opérateur retourne au code appelant.</span><span class="sxs-lookup"><span data-stu-id="15f8a-142">The value that the operator procedure returns to the calling code.</span></span>

<span data-ttu-id="15f8a-143">`End` `Operator`</span><span class="sxs-lookup"><span data-stu-id="15f8a-143">`End` `Operator`</span></span>  
<span data-ttu-id="15f8a-144">Requis.</span><span class="sxs-lookup"><span data-stu-id="15f8a-144">Required.</span></span> <span data-ttu-id="15f8a-145">Met fin à la définition de cette procédure d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="15f8a-145">Terminates the definition of this operator procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="15f8a-146">Notes</span><span class="sxs-lookup"><span data-stu-id="15f8a-146">Remarks</span></span>

<span data-ttu-id="15f8a-147">Vous pouvez utiliser `Operator` uniquement dans une classe ou une structure.</span><span class="sxs-lookup"><span data-stu-id="15f8a-147">You can use `Operator` only in a class or structure.</span></span> <span data-ttu-id="15f8a-148">Cela signifie que le *contexte de déclaration* pour un opérateur ne peut pas être un fichier source, un espace de noms, un module, une interface, une procédure ou un bloc.</span><span class="sxs-lookup"><span data-stu-id="15f8a-148">This means the *declaration context* for an operator cannot be a source file, namespace, module, interface, procedure, or block.</span></span> <span data-ttu-id="15f8a-149">Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="15f8a-149">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="15f8a-150">Tous les opérateurs doivent être `Public Shared`.</span><span class="sxs-lookup"><span data-stu-id="15f8a-150">All operators must be `Public Shared`.</span></span> <span data-ttu-id="15f8a-151">Vous ne pouvez pas spécifier `ByRef`, `Optional` ou `ParamArray` pour les deux opérandes.</span><span class="sxs-lookup"><span data-stu-id="15f8a-151">You cannot specify `ByRef`, `Optional`, or `ParamArray` for either operand.</span></span>

<span data-ttu-id="15f8a-152">Vous ne pouvez pas utiliser le symbole ou l’identificateur d’opérateur pour contenir une valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="15f8a-152">You cannot use the operator symbol or identifier to hold a return value.</span></span> <span data-ttu-id="15f8a-153">Vous devez utiliser l’instruction `Return` et celle-ci doit spécifier une valeur.</span><span class="sxs-lookup"><span data-stu-id="15f8a-153">You must use the `Return` statement, and it must specify a value.</span></span> <span data-ttu-id="15f8a-154">Un nombre quelconque d’instructions `Return` peuvent apparaître n’importe où dans la procédure.</span><span class="sxs-lookup"><span data-stu-id="15f8a-154">Any number of `Return` statements can appear anywhere in the procedure.</span></span>

<span data-ttu-id="15f8a-155">La définition d’un opérateur de cette manière est appelée *surcharge d’opérateur*, que vous utilisiez ou non le mot clé `Overloads`.</span><span class="sxs-lookup"><span data-stu-id="15f8a-155">Defining an operator in this way is called *operator overloading*, whether or not you use the `Overloads` keyword.</span></span> <span data-ttu-id="15f8a-156">Le tableau suivant présente les opérateurs que vous pouvez définir.</span><span class="sxs-lookup"><span data-stu-id="15f8a-156">The following table lists the operators you can define.</span></span>

|<span data-ttu-id="15f8a-157">Tapez</span><span class="sxs-lookup"><span data-stu-id="15f8a-157">Type</span></span>|<span data-ttu-id="15f8a-158">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="15f8a-158">Operators</span></span>|
|----------|---------------|
|<span data-ttu-id="15f8a-159">Unaire</span><span class="sxs-lookup"><span data-stu-id="15f8a-159">Unary</span></span>|<span data-ttu-id="15f8a-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="15f8a-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|
|<span data-ttu-id="15f8a-161">Binaire</span><span class="sxs-lookup"><span data-stu-id="15f8a-161">Binary</span></span>|<span data-ttu-id="15f8a-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="15f8a-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|
|<span data-ttu-id="15f8a-163">Conversion (unaire)</span><span class="sxs-lookup"><span data-stu-id="15f8a-163">Conversion (unary)</span></span>|`CType`|

<span data-ttu-id="15f8a-164">Notez que l’opérateur `=` dans la liste binaire est l’opérateur de comparaison, et non l’opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="15f8a-164">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>

<span data-ttu-id="15f8a-165">Lorsque vous définissez `CType`, vous devez spécifier `Widening` ou `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="15f8a-165">When you define `CType`, you must specify either `Widening` or `Narrowing`.</span></span>

## <a name="matched-pairs"></a><span data-ttu-id="15f8a-166">Paires correspondantes</span><span class="sxs-lookup"><span data-stu-id="15f8a-166">Matched Pairs</span></span>

<span data-ttu-id="15f8a-167">Vous devez définir certains opérateurs comme paires correspondantes.</span><span class="sxs-lookup"><span data-stu-id="15f8a-167">You must define certain operators as matched pairs.</span></span> <span data-ttu-id="15f8a-168">Si vous définissez l’un des opérateurs d’une telle paire, vous devez également définir l’autre opérateur.</span><span class="sxs-lookup"><span data-stu-id="15f8a-168">If you define either operator of such a pair, you must define the other as well.</span></span> <span data-ttu-id="15f8a-169">Les paires correspondantes sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="15f8a-169">The matched pairs are the following:</span></span>

- <span data-ttu-id="15f8a-170">`=` et `<>`</span><span class="sxs-lookup"><span data-stu-id="15f8a-170">`=` and `<>`</span></span>

- <span data-ttu-id="15f8a-171">`>` et `<`</span><span class="sxs-lookup"><span data-stu-id="15f8a-171">`>` and `<`</span></span>

- <span data-ttu-id="15f8a-172">`>=` et `<=`</span><span class="sxs-lookup"><span data-stu-id="15f8a-172">`>=` and `<=`</span></span>

- <span data-ttu-id="15f8a-173">`IsTrue` et `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="15f8a-173">`IsTrue` and `IsFalse`</span></span>

## <a name="data-type-restrictions"></a><span data-ttu-id="15f8a-174">Restrictions relatives aux types de données</span><span class="sxs-lookup"><span data-stu-id="15f8a-174">Data Type Restrictions</span></span>

<span data-ttu-id="15f8a-175">Chaque opérateur que vous définissez doit impliquer la classe ou la structure sur laquelle vous le définissez.</span><span class="sxs-lookup"><span data-stu-id="15f8a-175">Every operator you define must involve the class or structure on which you define it.</span></span> <span data-ttu-id="15f8a-176">Cela signifie que la classe ou la structure doit apparaître comme type de données des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="15f8a-176">This means that the class or structure must appear as the data type of the following:</span></span>

- <span data-ttu-id="15f8a-177">Opérande d’un opérateur unaire.</span><span class="sxs-lookup"><span data-stu-id="15f8a-177">The operand of a unary operator.</span></span>

- <span data-ttu-id="15f8a-178">Au moins l’un des opérandes d’un opérateur binaire.</span><span class="sxs-lookup"><span data-stu-id="15f8a-178">At least one of the operands of a binary operator.</span></span>

- <span data-ttu-id="15f8a-179">L’opérande ou le type de retour d’un opérateur de conversion.</span><span class="sxs-lookup"><span data-stu-id="15f8a-179">Either the operand or the return type of a conversion operator.</span></span>

 <span data-ttu-id="15f8a-180">Certains opérateurs ont des restrictions de type de données supplémentaires, comme suit :</span><span class="sxs-lookup"><span data-stu-id="15f8a-180">Certain operators have additional data type restrictions, as follows:</span></span>

- <span data-ttu-id="15f8a-181">Si vous définissez les opérateurs `IsTrue` et `IsFalse`, ceux-ci doivent retourner le type `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="15f8a-181">If you define the `IsTrue` and `IsFalse` operators, they must both return the `Boolean` type.</span></span>

- <span data-ttu-id="15f8a-182">Si vous définissez les opérateurs `<<` et `>>`, ils doivent spécifier le type de `Integer` pour le `operandtype` de `operand2`.</span><span class="sxs-lookup"><span data-stu-id="15f8a-182">If you define the `<<` and `>>` operators, they must both specify the `Integer` type for the `operandtype` of `operand2`.</span></span>

<span data-ttu-id="15f8a-183">Le type de retour ne doit pas nécessairement correspondre au type de l’un des opérandes.</span><span class="sxs-lookup"><span data-stu-id="15f8a-183">The return type does not have to correspond to the type of either operand.</span></span> <span data-ttu-id="15f8a-184">Par exemple, un opérateur de comparaison tel que `=` ou `<>` peut retourner `Boolean` même si aucun des opérandes n’est `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="15f8a-184">For example, a comparison operator such as `=` or `<>` can return `Boolean` even if neither operand is `Boolean`.</span></span>

## <a name="logical-and-bitwise-operators"></a><span data-ttu-id="15f8a-185">Opérateurs de bits et opérateurs logiques</span><span class="sxs-lookup"><span data-stu-id="15f8a-185">Logical and Bitwise Operators</span></span>

<span data-ttu-id="15f8a-186">Les opérateurs `And`, `Or`, `Not` et `Xor` peuvent effectuer des opérations logiques ou au niveau du bit dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="15f8a-186">The `And`, `Or`, `Not`, and `Xor` operators can perform either logical or bitwise operations in Visual Basic.</span></span> <span data-ttu-id="15f8a-187">Toutefois, si vous définissez l’un de ces opérateurs sur une classe ou une structure, vous pouvez définir uniquement son opération au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="15f8a-187">However, if you define one of these operators on a class or structure, you can define only its bitwise operation.</span></span>

<span data-ttu-id="15f8a-188">Vous ne pouvez pas définir directement l’opérateur `AndAlso` avec une instruction `Operator`.</span><span class="sxs-lookup"><span data-stu-id="15f8a-188">You cannot define the `AndAlso` operator directly with an `Operator` statement.</span></span> <span data-ttu-id="15f8a-189">Toutefois, vous pouvez utiliser `AndAlso` si vous avez rempli les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="15f8a-189">However, you can use `AndAlso` if you have fulfilled the following conditions:</span></span>

- <span data-ttu-id="15f8a-190">Vous avez défini `And` sur les mêmes types d’opérande que ceux que vous souhaitez utiliser pour `AndAlso`.</span><span class="sxs-lookup"><span data-stu-id="15f8a-190">You have defined `And` on the same operand types you want to use for `AndAlso`.</span></span>

- <span data-ttu-id="15f8a-191">Votre définition de `And` retourne le même type que la classe ou la structure sur laquelle vous l’avez défini.</span><span class="sxs-lookup"><span data-stu-id="15f8a-191">Your definition of `And` returns the same type as the class or structure on which you have defined it.</span></span>

- <span data-ttu-id="15f8a-192">Vous avez défini l’opérateur `IsFalse` sur la classe ou la structure sur laquelle vous avez défini `And`.</span><span class="sxs-lookup"><span data-stu-id="15f8a-192">You have defined the `IsFalse` operator on the class or structure on which you have defined `And`.</span></span>

<span data-ttu-id="15f8a-193">De même, vous pouvez utiliser `OrElse` si vous avez défini `Or` sur les mêmes opérandes, avec le type de retour de la classe ou de la structure, et que vous avez défini `IsTrue` sur la classe ou la structure.</span><span class="sxs-lookup"><span data-stu-id="15f8a-193">Similarly, you can use `OrElse` if you have defined `Or` on the same operands, with the return type of the class or structure, and you have defined `IsTrue` on the class or structure.</span></span>

## <a name="widening-and-narrowing-conversions"></a><span data-ttu-id="15f8a-194">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="15f8a-194">Widening and Narrowing Conversions</span></span>

<span data-ttu-id="15f8a-195">Une *conversion étendue* réussit toujours au moment de l’exécution, tandis qu’une *conversion restrictive* peut échouer au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="15f8a-195">A *widening conversion* always succeeds at run time, while a *narrowing conversion* can fail at run time.</span></span> <span data-ttu-id="15f8a-196">Pour plus d’informations, consultez [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="15f8a-196">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>

<span data-ttu-id="15f8a-197">Si vous déclarez une procédure de conversion à `Widening`, votre code de procédure ne doit pas générer d’échec.</span><span class="sxs-lookup"><span data-stu-id="15f8a-197">If you declare a conversion procedure to be `Widening`, your procedure code must not generate any failures.</span></span> <span data-ttu-id="15f8a-198">Par conséquent :</span><span class="sxs-lookup"><span data-stu-id="15f8a-198">This means the following:</span></span>

- <span data-ttu-id="15f8a-199">Elle doit toujours retourner une valeur valide de type `type`.</span><span class="sxs-lookup"><span data-stu-id="15f8a-199">It must always return a valid value of type `type`.</span></span>

- <span data-ttu-id="15f8a-200">Elle doit gérer toutes les exceptions possibles et d’autres conditions d’erreur.</span><span class="sxs-lookup"><span data-stu-id="15f8a-200">It must handle all possible exceptions and other error conditions.</span></span>

- <span data-ttu-id="15f8a-201">Il doit gérer toutes les erreurs renvoyées par les procédures qu’il appelle.</span><span class="sxs-lookup"><span data-stu-id="15f8a-201">It must handle any error returns from any procedures it calls.</span></span>

<span data-ttu-id="15f8a-202">S’il existe une possibilité qu’une procédure de conversion échoue ou qu’elle peut provoquer une exception non gérée, vous devez la déclarer comme étant `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="15f8a-202">If there is any possibility that a conversion procedure might not succeed, or that it might cause an unhandled exception, you must declare it to be `Narrowing`.</span></span>

## <a name="example"></a><span data-ttu-id="15f8a-203">Exemple</span><span class="sxs-lookup"><span data-stu-id="15f8a-203">Example</span></span>

<span data-ttu-id="15f8a-204">L’exemple de code suivant utilise l’instruction `Operator` pour définir le plan d’une structure qui comprend des procédures d’opérateur pour les opérateurs `And`, `Or`, `IsFalse` et `IsTrue`.</span><span class="sxs-lookup"><span data-stu-id="15f8a-204">The following code example uses the `Operator` statement to define the outline of a structure that includes operator procedures for the `And`, `Or`, `IsFalse`, and `IsTrue` operators.</span></span> <span data-ttu-id="15f8a-205">`And` et `Or` chacun prennent deux opérandes de type `abc` et le type de retour `abc`.</span><span class="sxs-lookup"><span data-stu-id="15f8a-205">`And` and `Or` each take two operands of type `abc` and return type `abc`.</span></span> <span data-ttu-id="15f8a-206">`IsFalse` et `IsTrue` prennent chacun un opérande unique de type `abc` et retournent `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="15f8a-206">`IsFalse` and `IsTrue` each take a single operand of type `abc` and return `Boolean`.</span></span> <span data-ttu-id="15f8a-207">Ces définitions permettent au code appelant d’utiliser `And`, `AndAlso`, `Or` et `OrElse` avec des opérandes de type `abc`.</span><span class="sxs-lookup"><span data-stu-id="15f8a-207">These definitions allow the calling code to use `And`, `AndAlso`, `Or`, and `OrElse` with operands of type `abc`.</span></span>

[!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]

## <a name="see-also"></a><span data-ttu-id="15f8a-208">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15f8a-208">See also</span></span>

- [<span data-ttu-id="15f8a-209">IsFalse (opérateur)</span><span class="sxs-lookup"><span data-stu-id="15f8a-209">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="15f8a-210">IsTrue (opérateur)</span><span class="sxs-lookup"><span data-stu-id="15f8a-210">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="15f8a-211">Widening</span><span class="sxs-lookup"><span data-stu-id="15f8a-211">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="15f8a-212">Narrowing</span><span class="sxs-lookup"><span data-stu-id="15f8a-212">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="15f8a-213">Conversions étendues et restrictives</span><span class="sxs-lookup"><span data-stu-id="15f8a-213">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="15f8a-214">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="15f8a-214">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="15f8a-215">Guide pratique : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="15f8a-215">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="15f8a-216">Guide pratique : définir un opérateur de conversion</span><span class="sxs-lookup"><span data-stu-id="15f8a-216">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="15f8a-217">Guide pratique : appeler une procédure d’opérateur</span><span class="sxs-lookup"><span data-stu-id="15f8a-217">How to: Call an Operator Procedure</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="15f8a-218">Guide pratique : utiliser une classe qui définit des opérateurs</span><span class="sxs-lookup"><span data-stu-id="15f8a-218">How to: Use a Class that Defines Operators</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
