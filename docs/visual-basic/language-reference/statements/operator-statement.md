---
title: Operator Statement
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
ms.openlocfilehash: f9e6ffe5a49715592399321ab471d73826e05d8e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404393"
---
# <a name="operator-statement"></a><span data-ttu-id="b90b6-102">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="b90b6-102">Operator Statement</span></span>

<span data-ttu-id="b90b6-103">Déclare le symbole d’opérateur, les opérandes et le code qui définissent une procédure d’opérateur sur une classe ou une structure.</span><span class="sxs-lookup"><span data-stu-id="b90b6-103">Declares the operator symbol, operands, and code that define an operator procedure on a class or structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="b90b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b90b6-104">Syntax</span></span>

```vb
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]
    [ statements ]
    [ statements ]
    Return returnvalue
    [ statements ]
End Operator
```

## <a name="parts"></a><span data-ttu-id="b90b6-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="b90b6-105">Parts</span></span>

`attrlist`  
<span data-ttu-id="b90b6-106">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b90b6-106">Optional.</span></span> <span data-ttu-id="b90b6-107">Consultez la [liste des attributs](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="b90b6-107">See [Attribute List](attribute-list.md).</span></span>

`Public`  
<span data-ttu-id="b90b6-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b90b6-108">Required.</span></span> <span data-ttu-id="b90b6-109">Indique que cette procédure d’opérateur a un accès [public](../modifiers/public.md) .</span><span class="sxs-lookup"><span data-stu-id="b90b6-109">Indicates that this operator procedure has [Public](../modifiers/public.md) access.</span></span>

`Overloads`  
<span data-ttu-id="b90b6-110">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b90b6-110">Optional.</span></span> <span data-ttu-id="b90b6-111">Consultez [Overloads](../modifiers/overloads.md).</span><span class="sxs-lookup"><span data-stu-id="b90b6-111">See [Overloads](../modifiers/overloads.md).</span></span>

`Shared`  
<span data-ttu-id="b90b6-112">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b90b6-112">Required.</span></span> <span data-ttu-id="b90b6-113">Indique que la procédure d’opérateur est une procédure [partagée](../modifiers/shared.md) .</span><span class="sxs-lookup"><span data-stu-id="b90b6-113">Indicates that this operator procedure is a [Shared](../modifiers/shared.md) procedure.</span></span>

`Shadows`  
<span data-ttu-id="b90b6-114">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b90b6-114">Optional.</span></span> <span data-ttu-id="b90b6-115">Consultez [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="b90b6-115">See [Shadows](../modifiers/shadows.md).</span></span>

`Widening`  
<span data-ttu-id="b90b6-116">Obligatoire pour un opérateur de conversion, sauf si vous spécifiez `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="b90b6-116">Required for a conversion operator unless you specify `Narrowing`.</span></span> <span data-ttu-id="b90b6-117">Indique que cette procédure d’opérateur définit une conversion [étendue](../modifiers/widening.md) .</span><span class="sxs-lookup"><span data-stu-id="b90b6-117">Indicates that this operator procedure defines a [Widening](../modifiers/widening.md) conversion.</span></span> <span data-ttu-id="b90b6-118">Pour plus d’informations, consultez « Conversions étendues et restrictives » dans cette page d’aide.</span><span class="sxs-lookup"><span data-stu-id="b90b6-118">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`Narrowing`  
<span data-ttu-id="b90b6-119">Obligatoire pour un opérateur de conversion, sauf si vous spécifiez `Widening` .</span><span class="sxs-lookup"><span data-stu-id="b90b6-119">Required for a conversion operator unless you specify `Widening`.</span></span> <span data-ttu-id="b90b6-120">Indique que cette procédure d’opérateur définit une conversion [restrictive](../modifiers/narrowing.md) .</span><span class="sxs-lookup"><span data-stu-id="b90b6-120">Indicates that this operator procedure defines a [Narrowing](../modifiers/narrowing.md) conversion.</span></span> <span data-ttu-id="b90b6-121">Pour plus d’informations, consultez « Conversions étendues et restrictives » dans cette page d’aide.</span><span class="sxs-lookup"><span data-stu-id="b90b6-121">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`operatorsymbol`  
<span data-ttu-id="b90b6-122">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b90b6-122">Required.</span></span> <span data-ttu-id="b90b6-123">Symbole ou identificateur de l’opérateur défini par cette procédure d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="b90b6-123">The symbol or identifier of the operator that this operator procedure defines.</span></span>

`operand1`  
<span data-ttu-id="b90b6-124">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b90b6-124">Required.</span></span> <span data-ttu-id="b90b6-125">Nom et type de l’opérande unique d’un opérateur unaire (y compris un opérateur de conversion) ou de l’opérande gauche d’un opérateur binaire.</span><span class="sxs-lookup"><span data-stu-id="b90b6-125">The name and type of the single operand of a unary operator (including a conversion operator) or the left operand of a binary operator.</span></span>

`operand2`  
<span data-ttu-id="b90b6-126">Requis pour les opérateurs binaires.</span><span class="sxs-lookup"><span data-stu-id="b90b6-126">Required for binary operators.</span></span> <span data-ttu-id="b90b6-127">Nom et type de l’opérande droit d’un opérateur binaire.</span><span class="sxs-lookup"><span data-stu-id="b90b6-127">The name and type of the right operand of a binary operator.</span></span>

<span data-ttu-id="b90b6-128">`operand1`et `operand2` ont la syntaxe et les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="b90b6-128">`operand1` and `operand2` have the following syntax and parts:</span></span>

`[ ByVal ] operandname [ As operandtype ]`

|<span data-ttu-id="b90b6-129">Élément</span><span class="sxs-lookup"><span data-stu-id="b90b6-129">Part</span></span>|<span data-ttu-id="b90b6-130">Description</span><span class="sxs-lookup"><span data-stu-id="b90b6-130">Description</span></span>|
|----------|-----------------|
|`ByVal`|<span data-ttu-id="b90b6-131">Facultatif, mais le mécanisme de passage doit être [ByVal](../modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="b90b6-131">Optional, but the passing mechanism must be [ByVal](../modifiers/byval.md).</span></span>|
|`operandname`|<span data-ttu-id="b90b6-132">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b90b6-132">Required.</span></span> <span data-ttu-id="b90b6-133">Nom de la variable représentant cet opérande.</span><span class="sxs-lookup"><span data-stu-id="b90b6-133">Name of the variable representing this operand.</span></span> <span data-ttu-id="b90b6-134">Consultez [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="b90b6-134">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`operandtype`|<span data-ttu-id="b90b6-135">Facultatif, sauf si `Option Strict` est `On` .</span><span class="sxs-lookup"><span data-stu-id="b90b6-135">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="b90b6-136">Type de données de cet opérande.</span><span class="sxs-lookup"><span data-stu-id="b90b6-136">Data type of this operand.</span></span>|

`type`  
<span data-ttu-id="b90b6-137">Facultatif, sauf si `Option Strict` est `On` .</span><span class="sxs-lookup"><span data-stu-id="b90b6-137">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="b90b6-138">Type de données de la valeur retournée par la procédure d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="b90b6-138">Data type of the value the operator procedure returns.</span></span>

`statements`  
<span data-ttu-id="b90b6-139">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b90b6-139">Optional.</span></span> <span data-ttu-id="b90b6-140">Bloc d’instructions exécutées par la procédure d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="b90b6-140">Block of statements that the operator procedure runs.</span></span>

`returnvalue`  
<span data-ttu-id="b90b6-141">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b90b6-141">Required.</span></span> <span data-ttu-id="b90b6-142">Valeur que la procédure d’opérateur retourne au code appelant.</span><span class="sxs-lookup"><span data-stu-id="b90b6-142">The value that the operator procedure returns to the calling code.</span></span>

<span data-ttu-id="b90b6-143">`End` `Operator`</span><span class="sxs-lookup"><span data-stu-id="b90b6-143">`End` `Operator`</span></span>  
<span data-ttu-id="b90b6-144">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b90b6-144">Required.</span></span> <span data-ttu-id="b90b6-145">Met fin à la définition de cette procédure d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="b90b6-145">Terminates the definition of this operator procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="b90b6-146">Notes</span><span class="sxs-lookup"><span data-stu-id="b90b6-146">Remarks</span></span>

<span data-ttu-id="b90b6-147">Vous pouvez utiliser `Operator` uniquement dans une classe ou une structure.</span><span class="sxs-lookup"><span data-stu-id="b90b6-147">You can use `Operator` only in a class or structure.</span></span> <span data-ttu-id="b90b6-148">Cela signifie que le *contexte de déclaration* pour un opérateur ne peut pas être un fichier source, un espace de noms, un module, une interface, une procédure ou un bloc.</span><span class="sxs-lookup"><span data-stu-id="b90b6-148">This means the *declaration context* for an operator cannot be a source file, namespace, module, interface, procedure, or block.</span></span> <span data-ttu-id="b90b6-149">Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="b90b6-149">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="b90b6-150">Tous les opérateurs doivent être `Public Shared` .</span><span class="sxs-lookup"><span data-stu-id="b90b6-150">All operators must be `Public Shared`.</span></span> <span data-ttu-id="b90b6-151">Vous ne pouvez pas spécifier `ByRef` , `Optional` ou `ParamArray` pour l’un des opérandes.</span><span class="sxs-lookup"><span data-stu-id="b90b6-151">You cannot specify `ByRef`, `Optional`, or `ParamArray` for either operand.</span></span>

<span data-ttu-id="b90b6-152">Vous ne pouvez pas utiliser le symbole ou l’identificateur d’opérateur pour contenir une valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="b90b6-152">You cannot use the operator symbol or identifier to hold a return value.</span></span> <span data-ttu-id="b90b6-153">Vous devez utiliser l' `Return` instruction et vous devez spécifier une valeur.</span><span class="sxs-lookup"><span data-stu-id="b90b6-153">You must use the `Return` statement, and it must specify a value.</span></span> <span data-ttu-id="b90b6-154">N’importe quel nombre d' `Return` instructions peut apparaître n’importe où dans la procédure.</span><span class="sxs-lookup"><span data-stu-id="b90b6-154">Any number of `Return` statements can appear anywhere in the procedure.</span></span>

<span data-ttu-id="b90b6-155">La définition d’un opérateur de cette manière est appelée *surcharge d’opérateur*, que vous utilisiez ou non le `Overloads` mot clé.</span><span class="sxs-lookup"><span data-stu-id="b90b6-155">Defining an operator in this way is called *operator overloading*, whether or not you use the `Overloads` keyword.</span></span> <span data-ttu-id="b90b6-156">Le tableau suivant présente les opérateurs que vous pouvez définir.</span><span class="sxs-lookup"><span data-stu-id="b90b6-156">The following table lists the operators you can define.</span></span>

|<span data-ttu-id="b90b6-157">Type</span><span class="sxs-lookup"><span data-stu-id="b90b6-157">Type</span></span>|<span data-ttu-id="b90b6-158">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="b90b6-158">Operators</span></span>|
|----------|---------------|
|<span data-ttu-id="b90b6-159">Unaire</span><span class="sxs-lookup"><span data-stu-id="b90b6-159">Unary</span></span>|<span data-ttu-id="b90b6-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="b90b6-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|
|<span data-ttu-id="b90b6-161">Binaire</span><span class="sxs-lookup"><span data-stu-id="b90b6-161">Binary</span></span>|<span data-ttu-id="b90b6-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="b90b6-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|
|<span data-ttu-id="b90b6-163">Conversion (unaire)</span><span class="sxs-lookup"><span data-stu-id="b90b6-163">Conversion (unary)</span></span>|`CType`|

<span data-ttu-id="b90b6-164">Notez que l’opérateur `=` dans la liste binaire est l’opérateur de comparaison, et non l’opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="b90b6-164">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>

<span data-ttu-id="b90b6-165">Lorsque vous définissez `CType` , vous devez spécifier `Widening` ou `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="b90b6-165">When you define `CType`, you must specify either `Widening` or `Narrowing`.</span></span>

## <a name="matched-pairs"></a><span data-ttu-id="b90b6-166">Paires correspondantes</span><span class="sxs-lookup"><span data-stu-id="b90b6-166">Matched Pairs</span></span>

<span data-ttu-id="b90b6-167">Vous devez définir certains opérateurs comme paires correspondantes.</span><span class="sxs-lookup"><span data-stu-id="b90b6-167">You must define certain operators as matched pairs.</span></span> <span data-ttu-id="b90b6-168">Si vous définissez l’un des opérateurs d’une telle paire, vous devez également définir l’autre opérateur.</span><span class="sxs-lookup"><span data-stu-id="b90b6-168">If you define either operator of such a pair, you must define the other as well.</span></span> <span data-ttu-id="b90b6-169">Les paires correspondantes sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b90b6-169">The matched pairs are the following:</span></span>

- <span data-ttu-id="b90b6-170">`=` et `<>`</span><span class="sxs-lookup"><span data-stu-id="b90b6-170">`=` and `<>`</span></span>

- <span data-ttu-id="b90b6-171">`>` et `<`</span><span class="sxs-lookup"><span data-stu-id="b90b6-171">`>` and `<`</span></span>

- <span data-ttu-id="b90b6-172">`>=` et `<=`</span><span class="sxs-lookup"><span data-stu-id="b90b6-172">`>=` and `<=`</span></span>

- <span data-ttu-id="b90b6-173">`IsTrue` et `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="b90b6-173">`IsTrue` and `IsFalse`</span></span>

## <a name="data-type-restrictions"></a><span data-ttu-id="b90b6-174">Restrictions relatives aux types de données</span><span class="sxs-lookup"><span data-stu-id="b90b6-174">Data Type Restrictions</span></span>

<span data-ttu-id="b90b6-175">Chaque opérateur que vous définissez doit impliquer la classe ou la structure sur laquelle vous le définissez.</span><span class="sxs-lookup"><span data-stu-id="b90b6-175">Every operator you define must involve the class or structure on which you define it.</span></span> <span data-ttu-id="b90b6-176">Cela signifie que la classe ou la structure doit apparaître comme type de données des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="b90b6-176">This means that the class or structure must appear as the data type of the following:</span></span>

- <span data-ttu-id="b90b6-177">Opérande d’un opérateur unaire.</span><span class="sxs-lookup"><span data-stu-id="b90b6-177">The operand of a unary operator.</span></span>

- <span data-ttu-id="b90b6-178">Au moins l’un des opérandes d’un opérateur binaire.</span><span class="sxs-lookup"><span data-stu-id="b90b6-178">At least one of the operands of a binary operator.</span></span>

- <span data-ttu-id="b90b6-179">L’opérande ou le type de retour d’un opérateur de conversion.</span><span class="sxs-lookup"><span data-stu-id="b90b6-179">Either the operand or the return type of a conversion operator.</span></span>

 <span data-ttu-id="b90b6-180">Certains opérateurs ont des restrictions de type de données supplémentaires, comme suit :</span><span class="sxs-lookup"><span data-stu-id="b90b6-180">Certain operators have additional data type restrictions, as follows:</span></span>

- <span data-ttu-id="b90b6-181">Si vous définissez les `IsTrue` `IsFalse` opérateurs et, ils doivent tous les deux retourner le `Boolean` type.</span><span class="sxs-lookup"><span data-stu-id="b90b6-181">If you define the `IsTrue` and `IsFalse` operators, they must both return the `Boolean` type.</span></span>

- <span data-ttu-id="b90b6-182">Si vous définissez les `<<` `>>` opérateurs et, ils doivent spécifier le `Integer` type du `operandtype` de `operand2` .</span><span class="sxs-lookup"><span data-stu-id="b90b6-182">If you define the `<<` and `>>` operators, they must both specify the `Integer` type for the `operandtype` of `operand2`.</span></span>

<span data-ttu-id="b90b6-183">Le type de retour ne doit pas nécessairement correspondre au type de l’un des opérandes.</span><span class="sxs-lookup"><span data-stu-id="b90b6-183">The return type does not have to correspond to the type of either operand.</span></span> <span data-ttu-id="b90b6-184">Par exemple, un opérateur de comparaison tel que `=` ou `<>` peut retourner `Boolean` même si aucun des opérandes n’est `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="b90b6-184">For example, a comparison operator such as `=` or `<>` can return `Boolean` even if neither operand is `Boolean`.</span></span>

## <a name="logical-and-bitwise-operators"></a><span data-ttu-id="b90b6-185">Opérateurs de bits et opérateurs logiques</span><span class="sxs-lookup"><span data-stu-id="b90b6-185">Logical and Bitwise Operators</span></span>

<span data-ttu-id="b90b6-186">Les `And` opérateurs,, `Or` `Not` et `Xor` peuvent effectuer des opérations logiques ou au niveau du bit dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b90b6-186">The `And`, `Or`, `Not`, and `Xor` operators can perform either logical or bitwise operations in Visual Basic.</span></span> <span data-ttu-id="b90b6-187">Toutefois, si vous définissez l’un de ces opérateurs sur une classe ou une structure, vous pouvez définir uniquement son opération au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="b90b6-187">However, if you define one of these operators on a class or structure, you can define only its bitwise operation.</span></span>

<span data-ttu-id="b90b6-188">Vous ne pouvez pas définir l' `AndAlso` opérateur directement avec une `Operator` instruction.</span><span class="sxs-lookup"><span data-stu-id="b90b6-188">You cannot define the `AndAlso` operator directly with an `Operator` statement.</span></span> <span data-ttu-id="b90b6-189">Toutefois, vous pouvez utiliser `AndAlso` si vous avez rempli les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="b90b6-189">However, you can use `AndAlso` if you have fulfilled the following conditions:</span></span>

- <span data-ttu-id="b90b6-190">Vous avez défini `And` sur les mêmes types d’opérande que pour `AndAlso` .</span><span class="sxs-lookup"><span data-stu-id="b90b6-190">You have defined `And` on the same operand types you want to use for `AndAlso`.</span></span>

- <span data-ttu-id="b90b6-191">Votre définition de `And` retourne le même type que la classe ou la structure sur laquelle vous l’avez défini.</span><span class="sxs-lookup"><span data-stu-id="b90b6-191">Your definition of `And` returns the same type as the class or structure on which you have defined it.</span></span>

- <span data-ttu-id="b90b6-192">Vous avez défini l' `IsFalse` opérateur sur la classe ou la structure sur laquelle vous avez défini `And` .</span><span class="sxs-lookup"><span data-stu-id="b90b6-192">You have defined the `IsFalse` operator on the class or structure on which you have defined `And`.</span></span>

<span data-ttu-id="b90b6-193">De même, vous pouvez utiliser `OrElse` si vous avez défini `Or` sur les mêmes opérandes, avec le type de retour de la classe ou de la structure, et que vous avez défini `IsTrue` sur la classe ou la structure.</span><span class="sxs-lookup"><span data-stu-id="b90b6-193">Similarly, you can use `OrElse` if you have defined `Or` on the same operands, with the return type of the class or structure, and you have defined `IsTrue` on the class or structure.</span></span>

## <a name="widening-and-narrowing-conversions"></a><span data-ttu-id="b90b6-194">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="b90b6-194">Widening and Narrowing Conversions</span></span>

<span data-ttu-id="b90b6-195">Une *conversion étendue* réussit toujours au moment de l’exécution, tandis qu’une *conversion restrictive* peut échouer au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b90b6-195">A *widening conversion* always succeeds at run time, while a *narrowing conversion* can fail at run time.</span></span> <span data-ttu-id="b90b6-196">Pour plus d’informations, consultez [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="b90b6-196">For more information, see [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>

<span data-ttu-id="b90b6-197">Si vous déclarez une procédure de conversion comme étant `Widening` , votre code de procédure ne doit pas générer d’échec.</span><span class="sxs-lookup"><span data-stu-id="b90b6-197">If you declare a conversion procedure to be `Widening`, your procedure code must not generate any failures.</span></span> <span data-ttu-id="b90b6-198">Cela signifie :</span><span class="sxs-lookup"><span data-stu-id="b90b6-198">This means the following:</span></span>

- <span data-ttu-id="b90b6-199">Elle doit toujours retourner une valeur valide de type `type` .</span><span class="sxs-lookup"><span data-stu-id="b90b6-199">It must always return a valid value of type `type`.</span></span>

- <span data-ttu-id="b90b6-200">Elle doit gérer toutes les exceptions possibles et d’autres conditions d’erreur.</span><span class="sxs-lookup"><span data-stu-id="b90b6-200">It must handle all possible exceptions and other error conditions.</span></span>

- <span data-ttu-id="b90b6-201">Il doit gérer toutes les erreurs renvoyées par les procédures qu’il appelle.</span><span class="sxs-lookup"><span data-stu-id="b90b6-201">It must handle any error returns from any procedures it calls.</span></span>

<span data-ttu-id="b90b6-202">S’il est possible qu’une procédure de conversion échoue ou qu’elle provoque une exception non gérée, vous devez la déclarer comme étant `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="b90b6-202">If there is any possibility that a conversion procedure might not succeed, or that it might cause an unhandled exception, you must declare it to be `Narrowing`.</span></span>

## <a name="example"></a><span data-ttu-id="b90b6-203">Exemple</span><span class="sxs-lookup"><span data-stu-id="b90b6-203">Example</span></span>

<span data-ttu-id="b90b6-204">L’exemple de code suivant utilise l' `Operator` instruction pour définir le plan d’une structure qui comprend des procédures d’opérateur pour les `And` `Or` opérateurs,, `IsFalse` et `IsTrue` .</span><span class="sxs-lookup"><span data-stu-id="b90b6-204">The following code example uses the `Operator` statement to define the outline of a structure that includes operator procedures for the `And`, `Or`, `IsFalse`, and `IsTrue` operators.</span></span> <span data-ttu-id="b90b6-205">`And`et `Or` chacune prennent deux opérandes de type `abc` et de type de retour `abc` .</span><span class="sxs-lookup"><span data-stu-id="b90b6-205">`And` and `Or` each take two operands of type `abc` and return type `abc`.</span></span> <span data-ttu-id="b90b6-206">`IsFalse`et, `IsTrue` chacun prennent un opérande unique de type `abc` et retourne `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="b90b6-206">`IsFalse` and `IsTrue` each take a single operand of type `abc` and return `Boolean`.</span></span> <span data-ttu-id="b90b6-207">Ces définitions permettent au code appelant d’utiliser `And` , `AndAlso` , `Or` et `OrElse` avec des opérandes de type `abc` .</span><span class="sxs-lookup"><span data-stu-id="b90b6-207">These definitions allow the calling code to use `And`, `AndAlso`, `Or`, and `OrElse` with operands of type `abc`.</span></span>

[!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]

## <a name="see-also"></a><span data-ttu-id="b90b6-208">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b90b6-208">See also</span></span>

- [<span data-ttu-id="b90b6-209">IsFalse, opérateur</span><span class="sxs-lookup"><span data-stu-id="b90b6-209">IsFalse Operator</span></span>](../operators/isfalse-operator.md)
- [<span data-ttu-id="b90b6-210">IsTrue, opérateur</span><span class="sxs-lookup"><span data-stu-id="b90b6-210">IsTrue Operator</span></span>](../operators/istrue-operator.md)
- [<span data-ttu-id="b90b6-211">Widening</span><span class="sxs-lookup"><span data-stu-id="b90b6-211">Widening</span></span>](../modifiers/widening.md)
- [<span data-ttu-id="b90b6-212">Narrowing</span><span class="sxs-lookup"><span data-stu-id="b90b6-212">Narrowing</span></span>](../modifiers/narrowing.md)
- [<span data-ttu-id="b90b6-213">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="b90b6-213">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="b90b6-214">Procédures d'opérateur</span><span class="sxs-lookup"><span data-stu-id="b90b6-214">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="b90b6-215">Comment : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="b90b6-215">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="b90b6-216">Guide pratique : définir un opérateur de conversion</span><span class="sxs-lookup"><span data-stu-id="b90b6-216">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="b90b6-217">Comment : appeler une procédure d'opérateur</span><span class="sxs-lookup"><span data-stu-id="b90b6-217">How to: Call an Operator Procedure</span></span>](../../programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="b90b6-218">Comment : utiliser une classe qui définit des opérateurs</span><span class="sxs-lookup"><span data-stu-id="b90b6-218">How to: Use a Class that Defines Operators</span></span>](../../programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
