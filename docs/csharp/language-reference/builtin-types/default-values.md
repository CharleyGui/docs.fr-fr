---
title: Valeurs par défaut des types de C - Référence C
description: Apprenez les valeurs par défaut des types de Cmd tels que le bool, l’omble, l’int, le flotteur, le double et plus encore.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 5e34d291ec15c738f3bc9409df321ede454b6710
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507254"
---
# <a name="default-values-of-c-types-c-reference"></a><span data-ttu-id="608bc-103">Valeurs par défaut des types C (référence C)</span><span class="sxs-lookup"><span data-stu-id="608bc-103">Default values of C# types (C# reference)</span></span>

<span data-ttu-id="608bc-104">Le tableau suivant présente les valeurs par défaut des types C# :</span><span class="sxs-lookup"><span data-stu-id="608bc-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="608bc-105">Type</span><span class="sxs-lookup"><span data-stu-id="608bc-105">Type</span></span>|<span data-ttu-id="608bc-106">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="608bc-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="608bc-107">tout type référence ;</span><span class="sxs-lookup"><span data-stu-id="608bc-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="608bc-108">Tout [type numérique intégral intégré](integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="608bc-108">Any [built-in integral numeric type](integral-numeric-types.md)</span></span>|<span data-ttu-id="608bc-109">0 (zéro)</span><span class="sxs-lookup"><span data-stu-id="608bc-109">0 (zero)</span></span>|
|<span data-ttu-id="608bc-110">Tout [type numérique à virgule flottante intégré](floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="608bc-110">Any [built-in floating-point numeric type](floating-point-numeric-types.md)</span></span>|<span data-ttu-id="608bc-111">0 (zéro)</span><span class="sxs-lookup"><span data-stu-id="608bc-111">0 (zero)</span></span>|
|[<span data-ttu-id="608bc-112">Bool</span><span class="sxs-lookup"><span data-stu-id="608bc-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="608bc-113">char</span><span class="sxs-lookup"><span data-stu-id="608bc-113">char</span></span>](char.md)|<span data-ttu-id="608bc-114">`'\0'` (U+0000)</span><span class="sxs-lookup"><span data-stu-id="608bc-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="608bc-115">Enum</span><span class="sxs-lookup"><span data-stu-id="608bc-115">enum</span></span>](enum.md)|<span data-ttu-id="608bc-116">Valeur produite par l’expression `(E)0`, où `E` est l’identificateur de l’enum.</span><span class="sxs-lookup"><span data-stu-id="608bc-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="608bc-117">struct</span><span class="sxs-lookup"><span data-stu-id="608bc-117">struct</span></span>](struct.md)|<span data-ttu-id="608bc-118">Valeur produite en affectant à tous les champs de type valeur leur valeur par défaut et à tous les champs de type référence la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="608bc-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="608bc-119">Tout [type valeur Nullable](nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="608bc-119">Any [nullable value type](nullable-value-types.md)</span></span>|<span data-ttu-id="608bc-120">Instance pour laquelle la propriété <xref:System.Nullable%601.HasValue%2A> a la valeur `false` et la propriété <xref:System.Nullable%601.Value%2A> n’est pas définie.</span><span class="sxs-lookup"><span data-stu-id="608bc-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="608bc-121">Cette valeur par défaut est également connue sous le nom de valeur *nulle* d’un type de valeur nulle.</span><span class="sxs-lookup"><span data-stu-id="608bc-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="608bc-122">Utilisez [ `default` l’opérateur](../operators/default.md#default-operator) pour produire la valeur par défaut d’un type, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="608bc-122">Use the [`default` operator](../operators/default.md#default-operator) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="608bc-123">En commençant par le C 7.1, vous pouvez utiliser le [ `default` littéral](../operators/default.md#default-literal) pour initialiser une variable avec la valeur par défaut de son type :</span><span class="sxs-lookup"><span data-stu-id="608bc-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="608bc-124">Pour un type valeur, le constructeur sans paramètre implicite produit également la valeur par défaut du type, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="608bc-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

<span data-ttu-id="608bc-125">Au moment de <xref:System.Type?displayProperty=nameWithType> l’exécution, si l’instance <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> représente un type de valeur, vous pouvez utiliser la méthode pour invoquer le constructeur sans paramètres pour obtenir la valeur par défaut du type.</span><span class="sxs-lookup"><span data-stu-id="608bc-125">At run time, if the <xref:System.Type?displayProperty=nameWithType> instance represents a value type, you can use the <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> method to invoke the parameterless constructor to obtain the default value of the type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="608bc-126">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="608bc-126">C# language specification</span></span>

<span data-ttu-id="608bc-127">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="608bc-127">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="608bc-128">Valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="608bc-128">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="608bc-129">Constructeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="608bc-129">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="608bc-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="608bc-130">See also</span></span>

- [<span data-ttu-id="608bc-131">Référence C#</span><span class="sxs-lookup"><span data-stu-id="608bc-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="608bc-132">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="608bc-132">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
