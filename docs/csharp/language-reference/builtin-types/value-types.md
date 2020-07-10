---
title: Types valeur-référence C#
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 0a05b2b0f3f2a8377fdba6144b8aeb12bdee1086
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86172949"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="dd54b-102">Types valeur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="dd54b-102">Value types (C# reference)</span></span>

<span data-ttu-id="dd54b-103">Les types *valeur* et les [types référence](../keywords/reference-types.md) sont les deux principales catégories de types C#.</span><span class="sxs-lookup"><span data-stu-id="dd54b-103">*Value types* and [reference types](../keywords/reference-types.md) are the two main categories of C# types.</span></span> <span data-ttu-id="dd54b-104">Une variable d’un type valeur contient une instance du type.</span><span class="sxs-lookup"><span data-stu-id="dd54b-104">A variable of a value type contains an instance of the type.</span></span> <span data-ttu-id="dd54b-105">Cela diffère d’une variable d’un type référence, qui contient une référence à une instance du type.</span><span class="sxs-lookup"><span data-stu-id="dd54b-105">This differs from a variable of a reference type, which contains a reference to an instance of the type.</span></span> <span data-ttu-id="dd54b-106">Par défaut, lors de l' [assignation](../operators/assignment-operator.md), en passant un argument à une méthode et en retournant un résultat de méthode, les valeurs des variables sont copiées.</span><span class="sxs-lookup"><span data-stu-id="dd54b-106">By default, on [assignment](../operators/assignment-operator.md), passing an argument to a method, and returning a method result, variable values are copied.</span></span> <span data-ttu-id="dd54b-107">Dans le cas des variables de type valeur, les instances de type correspondantes sont copiées.</span><span class="sxs-lookup"><span data-stu-id="dd54b-107">In the case of value-type variables, the corresponding type instances are copied.</span></span> <span data-ttu-id="dd54b-108">L’exemple suivant illustre ce comportement :</span><span class="sxs-lookup"><span data-stu-id="dd54b-108">The following example demonstrates that behavior:</span></span>

[!code-csharp[copy of values](snippets/ValueTypes.cs#ValueTypeCopied)]

<span data-ttu-id="dd54b-109">Comme le montre l’exemple précédent, les opérations sur une variable de type valeur affectent uniquement cette instance du type valeur, stockée dans la variable.</span><span class="sxs-lookup"><span data-stu-id="dd54b-109">As the preceding example shows, operations on a value-type variable affect only that instance of the value type, stored in the variable.</span></span>

<span data-ttu-id="dd54b-110">Si un type valeur contient un membre de données d’un type référence, seule la référence à l’instance du type référence est copiée lorsqu’une instance de type valeur est copiée.</span><span class="sxs-lookup"><span data-stu-id="dd54b-110">If a value type contains a data member of a reference type, only the reference to the instance of the reference type is copied when a value-type instance is copied.</span></span> <span data-ttu-id="dd54b-111">La copie et l’instance de type valeur d’origine ont accès à la même instance de type référence.</span><span class="sxs-lookup"><span data-stu-id="dd54b-111">Both the copy and original value-type instance have access to the same reference-type instance.</span></span> <span data-ttu-id="dd54b-112">L’exemple suivant illustre ce comportement :</span><span class="sxs-lookup"><span data-stu-id="dd54b-112">The following example demonstrates that behavior:</span></span>

[!code-csharp[shallow copy](snippets/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> <span data-ttu-id="dd54b-113">Pour que votre code soit moins sujet aux erreurs et plus robuste, définissez et utilisez des types de valeurs immuables.</span><span class="sxs-lookup"><span data-stu-id="dd54b-113">To make your code less error-prone and more robust, define and use immutable value types.</span></span> <span data-ttu-id="dd54b-114">Cet article utilise des types de valeur mutable uniquement à des fins de démonstration.</span><span class="sxs-lookup"><span data-stu-id="dd54b-114">This article uses mutable value types only for demonstration purposes.</span></span>

## <a name="kinds-of-value-types"></a><span data-ttu-id="dd54b-115">Genres de types valeur</span><span class="sxs-lookup"><span data-stu-id="dd54b-115">Kinds of value types</span></span>

<span data-ttu-id="dd54b-116">Un type valeur peut être l’un des deux types suivants :</span><span class="sxs-lookup"><span data-stu-id="dd54b-116">A value type can be one of the two following kinds:</span></span>

- <span data-ttu-id="dd54b-117">[type structure](struct.md), qui encapsule les données et les fonctionnalités associées</span><span class="sxs-lookup"><span data-stu-id="dd54b-117">a [structure type](struct.md), which encapsulates data and related functionality</span></span>
- <span data-ttu-id="dd54b-118">[type énumération](enum.md), qui est défini par un ensemble de constantes nommées et qui représente un choix ou une combinaison de choix</span><span class="sxs-lookup"><span data-stu-id="dd54b-118">an [enumeration type](enum.md), which is defined by a set of named constants and represents a choice or a combination of choices</span></span>

<span data-ttu-id="dd54b-119">Un [type valeur Nullable](nullable-value-types.md) `T?` représente toutes les valeurs de son type valeur sous-jacent `T` et une valeur [null](../keywords/null.md) supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="dd54b-119">A [nullable value type](nullable-value-types.md) `T?` represents all values of its underlying value type `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="dd54b-120">Vous ne pouvez pas assigner `null` à une variable d’un type valeur, sauf s’il s’agit d’un type valeur Nullable.</span><span class="sxs-lookup"><span data-stu-id="dd54b-120">You cannot assign `null` to a variable of a value type, unless it's a nullable value type.</span></span>

## <a name="built-in-value-types"></a><span data-ttu-id="dd54b-121">Types valeur intégrés</span><span class="sxs-lookup"><span data-stu-id="dd54b-121">Built-in value types</span></span>

<span data-ttu-id="dd54b-122">C# fournit les types valeur intégrés suivants, également appelés *types simples*:</span><span class="sxs-lookup"><span data-stu-id="dd54b-122">C# provides the following built-in value types, also known as *simple types*:</span></span>

- [<span data-ttu-id="dd54b-123">Types numériques intégraux</span><span class="sxs-lookup"><span data-stu-id="dd54b-123">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="dd54b-124">Types numériques à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="dd54b-124">Floating-point numeric types</span></span>](floating-point-numeric-types.md)
- <span data-ttu-id="dd54b-125">[booléen](bool.md) qui représente une valeur booléenne</span><span class="sxs-lookup"><span data-stu-id="dd54b-125">[bool](bool.md) that represents a Boolean value</span></span>
- <span data-ttu-id="dd54b-126">[char](char.md) qui représente un caractère Unicode UTF-16</span><span class="sxs-lookup"><span data-stu-id="dd54b-126">[char](char.md) that represents a Unicode UTF-16 character</span></span>

<span data-ttu-id="dd54b-127">Tous les types simples sont des types structure et diffèrent des autres types de structure en ce qu’ils autorisent certaines opérations supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="dd54b-127">All simple types are structure types and differ from other structure types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="dd54b-128">Vous pouvez utiliser des littéraux pour fournir une valeur d’un type simple.</span><span class="sxs-lookup"><span data-stu-id="dd54b-128">You can use literals to provide a value of a simple type.</span></span> <span data-ttu-id="dd54b-129">Par exemple, `'A'` est un littéral de type `char`, tandis que `2001` est un littéral de type `int`.</span><span class="sxs-lookup"><span data-stu-id="dd54b-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="dd54b-130">Vous pouvez déclarer des constantes des types simples avec le mot clé [const](../keywords/const.md).</span><span class="sxs-lookup"><span data-stu-id="dd54b-130">You can declare constants of the simple types with the [const](../keywords/const.md) keyword.</span></span> <span data-ttu-id="dd54b-131">Il n’est pas possible d’avoir des constantes d’autres types de structure.</span><span class="sxs-lookup"><span data-stu-id="dd54b-131">It's not possible to have constants of other structure types.</span></span>

- <span data-ttu-id="dd54b-132">Les expressions constantes, dont les opérandes sont toutes des constantes des types simples, sont évaluées au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="dd54b-132">Constant expressions, whose operands are all constants of the simple types, are evaluated at compile time.</span></span>

<span data-ttu-id="dd54b-133">À compter de C# 7,0, C# prend en charge les [tuples de valeur](value-tuples.md).</span><span class="sxs-lookup"><span data-stu-id="dd54b-133">Beginning with C# 7.0, C# supports [value tuples](value-tuples.md).</span></span> <span data-ttu-id="dd54b-134">Un tuple de valeur est un type valeur, mais pas un type simple.</span><span class="sxs-lookup"><span data-stu-id="dd54b-134">A value tuple is a value type, but not a simple type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dd54b-135">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="dd54b-135">C# language specification</span></span>

<span data-ttu-id="dd54b-136">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="dd54b-136">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="dd54b-137">Types valeur</span><span class="sxs-lookup"><span data-stu-id="dd54b-137">Value types</span></span>](~/_csharplang/spec/types.md#value-types)
- [<span data-ttu-id="dd54b-138">Types simples</span><span class="sxs-lookup"><span data-stu-id="dd54b-138">Simple types</span></span>](~/_csharplang/spec/types.md#simple-types)
- [<span data-ttu-id="dd54b-139">Variables</span><span class="sxs-lookup"><span data-stu-id="dd54b-139">Variables</span></span>](~/_csharplang/spec/variables.md)

## <a name="see-also"></a><span data-ttu-id="dd54b-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd54b-140">See also</span></span>

- [<span data-ttu-id="dd54b-141">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="dd54b-141">C# reference</span></span>](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [<span data-ttu-id="dd54b-142">Types référence</span><span class="sxs-lookup"><span data-stu-id="dd54b-142">Reference types</span></span>](../keywords/reference-types.md)
