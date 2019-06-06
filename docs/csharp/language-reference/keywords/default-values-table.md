---
title: Tableau des valeurs par défaut - Référence C#
ms.custom: seodec18
description: Découvrez quelles sont les valeurs par défaut des types valeur C#.
ms.date: 08/23/2018
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- parameterless constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], parameterless constructor
- types [C#], parameterless constructor return values
ms.openlocfilehash: 4fc9a35f69540e047a97c21788015ca8e54068a0
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422033"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="3d46b-103">Tableau des valeurs par défaut (référence C#)</span><span class="sxs-lookup"><span data-stu-id="3d46b-103">Default values table (C# Reference)</span></span>

<span data-ttu-id="3d46b-104">Le tableau suivant présente les valeurs par défaut des [types valeur](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="3d46b-104">The following table shows the default values of [value types](value-types.md).</span></span>

|<span data-ttu-id="3d46b-105">Type de valeur</span><span class="sxs-lookup"><span data-stu-id="3d46b-105">Value type</span></span>|<span data-ttu-id="3d46b-106">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="3d46b-106">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="3d46b-107">bool</span><span class="sxs-lookup"><span data-stu-id="3d46b-107">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="3d46b-108">byte</span><span class="sxs-lookup"><span data-stu-id="3d46b-108">byte</span></span>](byte.md)|<span data-ttu-id="3d46b-109">0</span><span class="sxs-lookup"><span data-stu-id="3d46b-109">0</span></span>|
|[<span data-ttu-id="3d46b-110">char</span><span class="sxs-lookup"><span data-stu-id="3d46b-110">char</span></span>](char.md)|<span data-ttu-id="3d46b-111">'\0'</span><span class="sxs-lookup"><span data-stu-id="3d46b-111">'\0'</span></span>|
|[<span data-ttu-id="3d46b-112">decimal</span><span class="sxs-lookup"><span data-stu-id="3d46b-112">decimal</span></span>](decimal.md)|<span data-ttu-id="3d46b-113">0M</span><span class="sxs-lookup"><span data-stu-id="3d46b-113">0M</span></span>|
|[<span data-ttu-id="3d46b-114">double</span><span class="sxs-lookup"><span data-stu-id="3d46b-114">double</span></span>](double.md)|<span data-ttu-id="3d46b-115">0.0D</span><span class="sxs-lookup"><span data-stu-id="3d46b-115">0.0D</span></span>|
|[<span data-ttu-id="3d46b-116">enum</span><span class="sxs-lookup"><span data-stu-id="3d46b-116">enum</span></span>](enum.md)|<span data-ttu-id="3d46b-117">Valeur produite par l’expression `(E)0`, où `E` est l’identificateur de l’enum.</span><span class="sxs-lookup"><span data-stu-id="3d46b-117">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="3d46b-118">float</span><span class="sxs-lookup"><span data-stu-id="3d46b-118">float</span></span>](float.md)|<span data-ttu-id="3d46b-119">0.0F</span><span class="sxs-lookup"><span data-stu-id="3d46b-119">0.0F</span></span>|
|[<span data-ttu-id="3d46b-120">int</span><span class="sxs-lookup"><span data-stu-id="3d46b-120">int</span></span>](int.md)|<span data-ttu-id="3d46b-121">0</span><span class="sxs-lookup"><span data-stu-id="3d46b-121">0</span></span>|
|[<span data-ttu-id="3d46b-122">long</span><span class="sxs-lookup"><span data-stu-id="3d46b-122">long</span></span>](long.md)|<span data-ttu-id="3d46b-123">0L</span><span class="sxs-lookup"><span data-stu-id="3d46b-123">0L</span></span>|
|[<span data-ttu-id="3d46b-124">sbyte</span><span class="sxs-lookup"><span data-stu-id="3d46b-124">sbyte</span></span>](sbyte.md)|<span data-ttu-id="3d46b-125">0</span><span class="sxs-lookup"><span data-stu-id="3d46b-125">0</span></span>|
|[<span data-ttu-id="3d46b-126">short</span><span class="sxs-lookup"><span data-stu-id="3d46b-126">short</span></span>](short.md)|<span data-ttu-id="3d46b-127">0</span><span class="sxs-lookup"><span data-stu-id="3d46b-127">0</span></span>|
|[<span data-ttu-id="3d46b-128">struct</span><span class="sxs-lookup"><span data-stu-id="3d46b-128">struct</span></span>](struct.md)|<span data-ttu-id="3d46b-129">Valeur produite en affectant à tous les champs de type valeur leur valeur par défaut et à tous les champs de type référence la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="3d46b-129">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="3d46b-130">uint</span><span class="sxs-lookup"><span data-stu-id="3d46b-130">uint</span></span>](uint.md)|<span data-ttu-id="3d46b-131">0</span><span class="sxs-lookup"><span data-stu-id="3d46b-131">0</span></span>|
|[<span data-ttu-id="3d46b-132">ulong</span><span class="sxs-lookup"><span data-stu-id="3d46b-132">ulong</span></span>](ulong.md)|<span data-ttu-id="3d46b-133">0</span><span class="sxs-lookup"><span data-stu-id="3d46b-133">0</span></span>|
|[<span data-ttu-id="3d46b-134">ushort</span><span class="sxs-lookup"><span data-stu-id="3d46b-134">ushort</span></span>](ushort.md)|<span data-ttu-id="3d46b-135">0</span><span class="sxs-lookup"><span data-stu-id="3d46b-135">0</span></span>|

## <a name="remarks"></a><span data-ttu-id="3d46b-136">Remarques</span><span class="sxs-lookup"><span data-stu-id="3d46b-136">Remarks</span></span>

<span data-ttu-id="3d46b-137">Vous ne pouvez pas utiliser des variables non initialisées en C#.</span><span class="sxs-lookup"><span data-stu-id="3d46b-137">You cannot use uninitialized variables in C#.</span></span> <span data-ttu-id="3d46b-138">Vous pouvez initialiser une variable avec la valeur par défaut de son type.</span><span class="sxs-lookup"><span data-stu-id="3d46b-138">You can initialize a variable with the default value of its type.</span></span> <span data-ttu-id="3d46b-139">Vous pouvez également utiliser la valeur par défaut d’un type pour spécifier la valeur par défaut de l’[argument facultatif](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments) d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="3d46b-139">You also can use the default value of a type to specify the default value of a method's [optional argument](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments).</span></span>

<span data-ttu-id="3d46b-140">Utilisez l’[expression de valeur par défaut](../../programming-guide/statements-expressions-operators/default-value-expressions.md) pour produire la valeur par défaut d’un type, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3d46b-140">Use the [default value expression](../../programming-guide/statements-expressions-operators/default-value-expressions.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="3d46b-141">À compter de C# 7.1, vous pouvez utiliser le [littéral `default`](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) pour initialiser une variable avec la valeur par défaut de son type :</span><span class="sxs-lookup"><span data-stu-id="3d46b-141">Beginning with C# 7.1, you can use the [`default` literal](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="3d46b-142">Vous pouvez également utiliser le constructeur sans paramètre ou le constructeur sans paramètre implicite pour produire la valeur par défaut d’un type valeur, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3d46b-142">You also can use the parameterless constructor or the implicit parameterless constructor to produce the default value of a value type, as the following example shows.</span></span> <span data-ttu-id="3d46b-143">Pour plus d’informations sur les constructeurs, consultez l’article [Constructeurs](../../programming-guide/classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="3d46b-143">For more information about constructors, see the [Constructors](../../programming-guide/classes-and-structs/constructors.md) article.</span></span>

```csharp
int a = new int();
```

<span data-ttu-id="3d46b-144">La valeur par défaut de tout [type référence](reference-types.md) est `null`.</span><span class="sxs-lookup"><span data-stu-id="3d46b-144">The default value of any [reference type](reference-types.md) is `null`.</span></span> <span data-ttu-id="3d46b-145">La valeur par défaut d’un [type nullable](../../programming-guide/nullable-types/index.md) est une instance pour laquelle la propriété <xref:System.Nullable%601.HasValue%2A> est `false` et la propriété <xref:System.Nullable%601.Value%2A> n’est pas définie.</span><span class="sxs-lookup"><span data-stu-id="3d46b-145">The default value of a [nullable type](../../programming-guide/nullable-types/index.md) is an instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d46b-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d46b-146">See also</span></span>

- [<span data-ttu-id="3d46b-147">Référence C#</span><span class="sxs-lookup"><span data-stu-id="3d46b-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3d46b-148">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3d46b-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3d46b-149">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="3d46b-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3d46b-150">Types valeur</span><span class="sxs-lookup"><span data-stu-id="3d46b-150">Value types</span></span>](value-types.md)
- [<span data-ttu-id="3d46b-151">Tableau des types valeur</span><span class="sxs-lookup"><span data-stu-id="3d46b-151">Value types table</span></span>](value-types-table.md)
- [<span data-ttu-id="3d46b-152">Tableaux des types intégrés</span><span class="sxs-lookup"><span data-stu-id="3d46b-152">Built-in types table</span></span>](built-in-types-table.md)
