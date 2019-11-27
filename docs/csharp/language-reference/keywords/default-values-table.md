---
title: Tableau des valeurs par défaut - Référence C#
ms.custom: seodec18
description: Découvrez quelles sont les valeurs par défaut des types C#.
ms.date: 07/29/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 2f1ad5cc029b93261153e46d854cd8bf3e31ce92
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428536"
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="a6a00-103">Tableau des valeurs par défaut (référence C#)</span><span class="sxs-lookup"><span data-stu-id="a6a00-103">Default values table (C# reference)</span></span>

<span data-ttu-id="a6a00-104">Le tableau suivant présente les valeurs par défaut des types C# :</span><span class="sxs-lookup"><span data-stu-id="a6a00-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="a6a00-105">Type</span><span class="sxs-lookup"><span data-stu-id="a6a00-105">Type</span></span>|<span data-ttu-id="a6a00-106">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="a6a00-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="a6a00-107">tout type référence ;</span><span class="sxs-lookup"><span data-stu-id="a6a00-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="a6a00-108">Tout [type numérique intégral intégré](../builtin-types/integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="a6a00-108">Any [built-in integral numeric type](../builtin-types/integral-numeric-types.md)</span></span>|<span data-ttu-id="a6a00-109">0 (zéro)</span><span class="sxs-lookup"><span data-stu-id="a6a00-109">0 (zero)</span></span>|
|<span data-ttu-id="a6a00-110">Tout [type numérique à virgule flottante intégré](../builtin-types/floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="a6a00-110">Any [built-in floating-point numeric type](../builtin-types/floating-point-numeric-types.md)</span></span>|<span data-ttu-id="a6a00-111">0 (zéro)</span><span class="sxs-lookup"><span data-stu-id="a6a00-111">0 (zero)</span></span>|
|[<span data-ttu-id="a6a00-112">bool</span><span class="sxs-lookup"><span data-stu-id="a6a00-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="a6a00-113">char</span><span class="sxs-lookup"><span data-stu-id="a6a00-113">char</span></span>](../builtin-types/char.md)|<span data-ttu-id="a6a00-114">`'\0'` (U+0000)</span><span class="sxs-lookup"><span data-stu-id="a6a00-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="a6a00-115">enum</span><span class="sxs-lookup"><span data-stu-id="a6a00-115">enum</span></span>](enum.md)|<span data-ttu-id="a6a00-116">Valeur produite par l’expression `(E)0`, où `E` est l’identificateur de l’enum.</span><span class="sxs-lookup"><span data-stu-id="a6a00-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="a6a00-117">struct</span><span class="sxs-lookup"><span data-stu-id="a6a00-117">struct</span></span>](struct.md)|<span data-ttu-id="a6a00-118">Valeur produite en affectant à tous les champs de type valeur leur valeur par défaut et à tous les champs de type référence la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="a6a00-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="a6a00-119">Tout [type valeur Nullable](../builtin-types/nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="a6a00-119">Any [nullable value type](../builtin-types/nullable-value-types.md)</span></span>|<span data-ttu-id="a6a00-120">Instance pour laquelle la propriété <xref:System.Nullable%601.HasValue%2A> a la valeur `false` et la propriété <xref:System.Nullable%601.Value%2A> n’est pas définie.</span><span class="sxs-lookup"><span data-stu-id="a6a00-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="a6a00-121">Cette valeur par défaut est également connue sous le nom de valeur *null* d’un type valeur Nullable.</span><span class="sxs-lookup"><span data-stu-id="a6a00-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="a6a00-122">Utilisez l’[opérateur par défaut](../operators/default.md) pour produire la valeur par défaut d’un type, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a6a00-122">Use the [default operator](../operators/default.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="a6a00-123">À compter de C# 7.1, vous pouvez utiliser le [littéral `default`](../operators/default.md#default-literal) pour initialiser une variable avec la valeur par défaut de son type :</span><span class="sxs-lookup"><span data-stu-id="a6a00-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="a6a00-124">Pour un type valeur, le constructeur sans paramètre implicite produit également la valeur par défaut du type, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a6a00-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

## <a name="c-language-specification"></a><span data-ttu-id="a6a00-125">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="a6a00-125">C# language specification</span></span>

<span data-ttu-id="a6a00-126">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="a6a00-126">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="a6a00-127">Valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="a6a00-127">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="a6a00-128">Constructeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="a6a00-128">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="a6a00-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6a00-129">See also</span></span>

- [<span data-ttu-id="a6a00-130">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="a6a00-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a6a00-131">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="a6a00-131">C# keywords</span></span>](index.md)
- [<span data-ttu-id="a6a00-132">Tableaux des types intégrés</span><span class="sxs-lookup"><span data-stu-id="a6a00-132">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="a6a00-133">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="a6a00-133">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
