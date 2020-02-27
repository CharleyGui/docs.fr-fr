---
title: Valeurs par défaut C# des types C# -référence
description: Découvrez les valeurs par défaut C# des types tels que bool, Char, int, float, double et More.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 93b6079b9a3bbf6d537094cab9dfb305ace7f6bf
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625863"
---
# <a name="default-values-of-c-types-c-reference"></a><span data-ttu-id="f3ec4-103">Valeurs par défaut C# des typesC# (référence)</span><span class="sxs-lookup"><span data-stu-id="f3ec4-103">Default values of C# types (C# reference)</span></span>

<span data-ttu-id="f3ec4-104">Le tableau suivant présente les valeurs par défaut des types C# :</span><span class="sxs-lookup"><span data-stu-id="f3ec4-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="f3ec4-105">Type</span><span class="sxs-lookup"><span data-stu-id="f3ec4-105">Type</span></span>|<span data-ttu-id="f3ec4-106">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="f3ec4-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="f3ec4-107">tout type référence ;</span><span class="sxs-lookup"><span data-stu-id="f3ec4-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="f3ec4-108">Tout [type numérique intégral intégré](integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="f3ec4-108">Any [built-in integral numeric type](integral-numeric-types.md)</span></span>|<span data-ttu-id="f3ec4-109">0 (zéro)</span><span class="sxs-lookup"><span data-stu-id="f3ec4-109">0 (zero)</span></span>|
|<span data-ttu-id="f3ec4-110">Tout [type numérique à virgule flottante intégré](floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="f3ec4-110">Any [built-in floating-point numeric type](floating-point-numeric-types.md)</span></span>|<span data-ttu-id="f3ec4-111">0 (zéro)</span><span class="sxs-lookup"><span data-stu-id="f3ec4-111">0 (zero)</span></span>|
|[<span data-ttu-id="f3ec4-112">bool</span><span class="sxs-lookup"><span data-stu-id="f3ec4-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="f3ec4-113">char</span><span class="sxs-lookup"><span data-stu-id="f3ec4-113">char</span></span>](char.md)|<span data-ttu-id="f3ec4-114">`'\0'` (U+0000)</span><span class="sxs-lookup"><span data-stu-id="f3ec4-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="f3ec4-115">enum</span><span class="sxs-lookup"><span data-stu-id="f3ec4-115">enum</span></span>](enum.md)|<span data-ttu-id="f3ec4-116">Valeur produite par l’expression `(E)0`, où `E` est l’identificateur de l’enum.</span><span class="sxs-lookup"><span data-stu-id="f3ec4-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="f3ec4-117">struct</span><span class="sxs-lookup"><span data-stu-id="f3ec4-117">struct</span></span>](struct.md)|<span data-ttu-id="f3ec4-118">Valeur produite en affectant à tous les champs de type valeur leur valeur par défaut et à tous les champs de type référence la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="f3ec4-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="f3ec4-119">Tout [type valeur Nullable](nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="f3ec4-119">Any [nullable value type](nullable-value-types.md)</span></span>|<span data-ttu-id="f3ec4-120">Instance pour laquelle la propriété <xref:System.Nullable%601.HasValue%2A> a la valeur `false` et la propriété <xref:System.Nullable%601.Value%2A> n’est pas définie.</span><span class="sxs-lookup"><span data-stu-id="f3ec4-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="f3ec4-121">Cette valeur par défaut est également connue sous le nom de valeur *null* d’un type valeur Nullable.</span><span class="sxs-lookup"><span data-stu-id="f3ec4-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="f3ec4-122">Utilisez l’[opérateur par défaut](../operators/default.md) pour produire la valeur par défaut d’un type, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f3ec4-122">Use the [default operator](../operators/default.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="f3ec4-123">À compter de C# 7.1, vous pouvez utiliser le [littéral `default`](../operators/default.md#default-literal) pour initialiser une variable avec la valeur par défaut de son type :</span><span class="sxs-lookup"><span data-stu-id="f3ec4-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="f3ec4-124">Pour un type valeur, le constructeur sans paramètre implicite produit également la valeur par défaut du type, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f3ec4-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

<span data-ttu-id="f3ec4-125">Au moment de l’exécution, si l’instance <xref:System.Type?displayProperty=nameWithType> représente un type valeur, vous pouvez utiliser la méthode <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> pour appeler le constructeur sans paramètre afin d’obtenir la valeur par défaut du type.</span><span class="sxs-lookup"><span data-stu-id="f3ec4-125">At run time, if the <xref:System.Type?displayProperty=nameWithType> instance represents a value type, you can use the <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> method to invoke the parameterless constructor to obtain the default value of the type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f3ec4-126">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="f3ec4-126">C# language specification</span></span>

<span data-ttu-id="f3ec4-127">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="f3ec4-127">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="f3ec4-128">Valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="f3ec4-128">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="f3ec4-129">Constructeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="f3ec4-129">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="f3ec4-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3ec4-130">See also</span></span>

- [<span data-ttu-id="f3ec4-131">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="f3ec4-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f3ec4-132">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="f3ec4-132">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
