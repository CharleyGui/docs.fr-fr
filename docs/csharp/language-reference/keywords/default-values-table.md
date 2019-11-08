---
title: Tableau des valeurs par défaut - Référence C#
ms.custom: seodec18
description: Découvrez quelles sont les valeurs par défaut des types C#.
ms.date: 07/29/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 02f86ef8ee73ff31a6c5c9d17a44a443f72ef05e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739281"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="4a09a-103">Tableau des valeurs par défaut (référence C#)</span><span class="sxs-lookup"><span data-stu-id="4a09a-103">Default values table (C# reference)</span></span>

<span data-ttu-id="4a09a-104">Le tableau suivant présente les valeurs par défaut des types C# :</span><span class="sxs-lookup"><span data-stu-id="4a09a-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="4a09a-105">Tapez</span><span class="sxs-lookup"><span data-stu-id="4a09a-105">Type</span></span>|<span data-ttu-id="4a09a-106">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="4a09a-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="4a09a-107">tout type référence ;</span><span class="sxs-lookup"><span data-stu-id="4a09a-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="4a09a-108">Tout [type numérique intégral intégré](../builtin-types/integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="4a09a-108">Any [built-in integral numeric type](../builtin-types/integral-numeric-types.md)</span></span>|<span data-ttu-id="4a09a-109">0 (zéro)</span><span class="sxs-lookup"><span data-stu-id="4a09a-109">0 (zero)</span></span>|
|<span data-ttu-id="4a09a-110">Tout [type numérique à virgule flottante intégré](../builtin-types/floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="4a09a-110">Any [built-in floating-point numeric type](../builtin-types/floating-point-numeric-types.md)</span></span>|<span data-ttu-id="4a09a-111">0 (zéro)</span><span class="sxs-lookup"><span data-stu-id="4a09a-111">0 (zero)</span></span>|
|[<span data-ttu-id="4a09a-112">bool</span><span class="sxs-lookup"><span data-stu-id="4a09a-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="4a09a-113">char</span><span class="sxs-lookup"><span data-stu-id="4a09a-113">char</span></span>](char.md)|<span data-ttu-id="4a09a-114">`'\0'` (U+0000)</span><span class="sxs-lookup"><span data-stu-id="4a09a-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="4a09a-115">enum</span><span class="sxs-lookup"><span data-stu-id="4a09a-115">enum</span></span>](enum.md)|<span data-ttu-id="4a09a-116">Valeur produite par l’expression `(E)0`, où `E` est l’identificateur de l’enum.</span><span class="sxs-lookup"><span data-stu-id="4a09a-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="4a09a-117">struct</span><span class="sxs-lookup"><span data-stu-id="4a09a-117">struct</span></span>](struct.md)|<span data-ttu-id="4a09a-118">Valeur produite en affectant à tous les champs de type valeur leur valeur par défaut et à tous les champs de type référence la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="4a09a-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="4a09a-119">Tout [type valeur Nullable](../builtin-types/nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="4a09a-119">Any [nullable value type](../builtin-types/nullable-value-types.md)</span></span>|<span data-ttu-id="4a09a-120">Instance pour laquelle la propriété <xref:System.Nullable%601.HasValue%2A> a la valeur `false` et la propriété <xref:System.Nullable%601.Value%2A> n’est pas définie.</span><span class="sxs-lookup"><span data-stu-id="4a09a-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="4a09a-121">Cette valeur par défaut est également connue sous le nom de valeur *null* d’un type valeur Nullable.</span><span class="sxs-lookup"><span data-stu-id="4a09a-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="4a09a-122">Utilisez l’[opérateur par défaut](../operators/default.md) pour produire la valeur par défaut d’un type, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4a09a-122">Use the [default operator](../operators/default.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="4a09a-123">À compter de C# 7.1, vous pouvez utiliser le [littéral `default`](../operators/default.md#default-literal) pour initialiser une variable avec la valeur par défaut de son type :</span><span class="sxs-lookup"><span data-stu-id="4a09a-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="4a09a-124">Pour un type valeur, le constructeur sans paramètre implicite produit également la valeur par défaut du type, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4a09a-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

## <a name="c-language-specification"></a><span data-ttu-id="4a09a-125">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="4a09a-125">C# language specification</span></span>

<span data-ttu-id="4a09a-126">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="4a09a-126">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="4a09a-127">Valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="4a09a-127">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="4a09a-128">Constructeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="4a09a-128">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="4a09a-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a09a-129">See also</span></span>

- [<span data-ttu-id="4a09a-130">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="4a09a-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4a09a-131">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="4a09a-131">C# keywords</span></span>](index.md)
- [<span data-ttu-id="4a09a-132">Tableaux des types intégrés</span><span class="sxs-lookup"><span data-stu-id="4a09a-132">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="4a09a-133">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="4a09a-133">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
