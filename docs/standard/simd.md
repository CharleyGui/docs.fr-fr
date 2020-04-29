---
title: Types accélérés SIMD dans .NET
description: Cet article décrit les types SIMD-Enable dans .NET et montre comment utiliser les opérations matérielles SIMD en C# et .NET.
author: FIVIL
ms.author: tagoo
ms.date: 04/28/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 27263931ff0338e194c8fd3d9ec5ba59bfafd9fe
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507781"
---
# <a name="use-simd-accelerated-numeric-types"></a><span data-ttu-id="7b25b-103">Utiliser des types numériques SIMD accélérés</span><span class="sxs-lookup"><span data-stu-id="7b25b-103">Use SIMD-accelerated numeric types</span></span>

<span data-ttu-id="7b25b-104">SIMD (instruction unique, plusieurs données) fournit une prise en charge matérielle pour effectuer une opération sur plusieurs éléments de données, en parallèle, à l’aide d’une seule instruction.</span><span class="sxs-lookup"><span data-stu-id="7b25b-104">SIMD (Single instruction, multiple data) provides hardware support for performing an operation on multiple pieces of data, in parallel, using a single instruction.</span></span> <span data-ttu-id="7b25b-105">Dans .NET, il existe un ensemble de types accélérés SIMD sous l' <xref:System.Numerics> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="7b25b-105">In .NET, there's set of SIMD-accelerated types under the <xref:System.Numerics> namespace.</span></span> <span data-ttu-id="7b25b-106">Les opérations SIMD peuvent être parallèles au niveau du matériel.</span><span class="sxs-lookup"><span data-stu-id="7b25b-106">SIMD operations can be parallelized at the hardware level.</span></span> <span data-ttu-id="7b25b-107">Cela augmente le débit des calculs vectorisés, couramment utilisés dans les applications mathématiques, scientifiques et graphiques.</span><span class="sxs-lookup"><span data-stu-id="7b25b-107">That increases the throughput of the vectorized computations, which are common in mathematical, scientific, and graphics apps.</span></span>

## <a name="net-simd-accelerated-types"></a><span data-ttu-id="7b25b-108">Types accélérés SIMD .NET</span><span class="sxs-lookup"><span data-stu-id="7b25b-108">.NET SIMD-accelerated types</span></span>

<span data-ttu-id="7b25b-109">Les types accélérés par le .NET SIMD incluent les types suivants :</span><span class="sxs-lookup"><span data-stu-id="7b25b-109">The .NET SIMD-accelerated types include the following types:</span></span>

- <span data-ttu-id="7b25b-110">Les types <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3> et <xref:System.Numerics.Vector4>, qui représentent des vecteurs à 2, 3 et 4 valeurs <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="7b25b-110">The <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4> types, which represent vectors with 2, 3, and 4 <xref:System.Single> values.</span></span>

- <span data-ttu-id="7b25b-111">Deux types de matrices, <xref:System.Numerics.Matrix3x2>, qui représente une matrice matrice <xref:System.Numerics.Matrix4x4>, et, qui représente une matrice <xref:System.Single> 4x4 de valeurs.</span><span class="sxs-lookup"><span data-stu-id="7b25b-111">Two matrix types, <xref:System.Numerics.Matrix3x2>, which represents a 3x2 matrix, and <xref:System.Numerics.Matrix4x4>, which represents a 4x4 matrix of <xref:System.Single> values.</span></span>

- <span data-ttu-id="7b25b-112"><xref:System.Numerics.Plane> Type, qui représente un plan dans l’espace tridimensionnel à l’aide <xref:System.Single> de valeurs.</span><span class="sxs-lookup"><span data-stu-id="7b25b-112">The <xref:System.Numerics.Plane> type, which represents a plane in three-dimensional space using <xref:System.Single> values.</span></span>

- <span data-ttu-id="7b25b-113"><xref:System.Numerics.Quaternion> Type, qui représente un vecteur utilisé pour encoder des rotations physiques en trois dimensions à <xref:System.Single> l’aide de valeurs.</span><span class="sxs-lookup"><span data-stu-id="7b25b-113">The <xref:System.Numerics.Quaternion> type, which represents a vector that is used to encode three-dimensional physical rotations using <xref:System.Single> values.</span></span>

- <span data-ttu-id="7b25b-114">Le type <xref:System.Numerics.Vector%601>, qui représente un vecteur d’un type numérique spécifié et fournit un large éventail d’opérateurs bénéficiant d’un support SIMD.</span><span class="sxs-lookup"><span data-stu-id="7b25b-114">The <xref:System.Numerics.Vector%601> type, which represents a vector of a specified numeric type and provides a broad set of operators that benefit from SIMD support.</span></span> <span data-ttu-id="7b25b-115">Le nombre d’une <xref:System.Numerics.Vector%601> instance est fixe pour la durée de vie d’une application, mais <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> sa valeur dépend de l’UC de l’ordinateur qui exécute le code.</span><span class="sxs-lookup"><span data-stu-id="7b25b-115">The count of a <xref:System.Numerics.Vector%601> instance is fixed for the lifetime of an application, but its value <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> depends on the CPU of the machine running the code.</span></span>

  > [!NOTE]
  > <span data-ttu-id="7b25b-116">Le <xref:System.Numerics.Vector%601> type n’est pas inclus dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b25b-116">The <xref:System.Numerics.Vector%601> type is not included in the .NET Framework.</span></span> <span data-ttu-id="7b25b-117">Vous devez installer le package NuGet [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) pour accéder à ce type.</span><span class="sxs-lookup"><span data-stu-id="7b25b-117">You must install the [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) NuGet package to get access to this type.</span></span>
  
<span data-ttu-id="7b25b-118">Les types accélérés SIMD sont implémentés de telle sorte qu’ils peuvent être utilisés avec le matériel ou les compilateurs JIT non-SIMD.</span><span class="sxs-lookup"><span data-stu-id="7b25b-118">The SIMD-accelerated types are implemented in such a way that they can be used with non-SIMD-accelerated hardware or JIT compilers.</span></span> <span data-ttu-id="7b25b-119">Pour tirer parti des instructions SIMD, vos applications 64 bits doivent être exécutées par le runtime qui utilise le compilateur **RyuJIT** .</span><span class="sxs-lookup"><span data-stu-id="7b25b-119">To take advantage of SIMD instructions, your 64-bit apps must be run by the runtime that uses the **RyuJIT** compiler.</span></span> <span data-ttu-id="7b25b-120">Un compilateur **RyuJIT** est inclus dans .net Core et dans .NET Framework 4,6 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="7b25b-120">A **RyuJIT** compiler is included in .NET Core and in .NET Framework 4.6 and later.</span></span> <span data-ttu-id="7b25b-121">La prise en charge SIMD est fournie uniquement lorsque vous ciblez des processeurs 64 bits.</span><span class="sxs-lookup"><span data-stu-id="7b25b-121">SIMD support is only provided when targeting 64-bit processors.</span></span>

## <a name="how-to-use-simd"></a><span data-ttu-id="7b25b-122">Comment utiliser SIMD ?</span><span class="sxs-lookup"><span data-stu-id="7b25b-122">How to use SIMD?</span></span>

<span data-ttu-id="7b25b-123">Avant d’exécuter des algorithmes SIMD personnalisés, il est possible de vérifier si l’ordinateur hôte prend en charge <xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType>SIMD à l’aide <xref:System.Boolean>de, qui retourne un.</span><span class="sxs-lookup"><span data-stu-id="7b25b-123">Before executing custom SIMD algorithms, it's possible to check if the host machine supports SIMD by using <xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType>, which returns a <xref:System.Boolean>.</span></span> <span data-ttu-id="7b25b-124">Cela ne garantit pas que l’accélération SIMD est activée pour un type spécifique, mais qu’elle est prise en charge par certains types.</span><span class="sxs-lookup"><span data-stu-id="7b25b-124">This doesn't guarantee that SIMD-acceleration is enabled for a specific type, but is an indicator that it's supported by some types.</span></span>

## <a name="simple-vectors"></a><span data-ttu-id="7b25b-125">Vecteurs simples</span><span class="sxs-lookup"><span data-stu-id="7b25b-125">Simple Vectors</span></span>

<span data-ttu-id="7b25b-126">Les types accélérés SIMD les plus primitifs dans .NET <xref:System.Numerics.Vector2>sont <xref:System.Numerics.Vector3>les types <xref:System.Numerics.Vector4> , et, qui représentent des vecteurs avec 2, 3 et <xref:System.Single> 4 valeurs.</span><span class="sxs-lookup"><span data-stu-id="7b25b-126">The most primitive SIMD-accelerated types in .NET are <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4> types, which represent vectors with 2, 3, and 4 <xref:System.Single> values.</span></span> <span data-ttu-id="7b25b-127">L’exemple ci- <xref:System.Numerics.Vector2> dessous utilise pour ajouter deux vecteurs.</span><span class="sxs-lookup"><span data-stu-id="7b25b-127">The example below uses <xref:System.Numerics.Vector2> to add two vectors.</span></span>

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResutl = v1 + v2;
```

<span data-ttu-id="7b25b-128">Il est également possible d’utiliser des vecteurs .net pour calculer d’autres propriétés mathématiques de vecteurs `Dot product`tels `Transform`que `Clamp` ,, etc.</span><span class="sxs-lookup"><span data-stu-id="7b25b-128">It's also possible to use .NET vectors to calculate other mathematical properties of vectors such as `Dot product`, `Transform`, `Clamp` and so on.</span></span>

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResutl1 = Vector2.Dot(v1, v2);
var vResutl2 = Vector2.Distance(v1, v2);
var vResutl3 = Vector2.Clamp(v1, Vector2.Zero, Vector2.One);
```

## <a name="matrix"></a><span data-ttu-id="7b25b-129">Matrix</span><span class="sxs-lookup"><span data-stu-id="7b25b-129">Matrix</span></span>

<span data-ttu-id="7b25b-130"><xref:System.Numerics.Matrix3x2>, qui représente une matrice matrice, et <xref:System.Numerics.Matrix4x4>, qui représente une matrice 4x4.</span><span class="sxs-lookup"><span data-stu-id="7b25b-130"><xref:System.Numerics.Matrix3x2>, which represents a 3x2 matrix, and <xref:System.Numerics.Matrix4x4>, which represents a 4x4 matrix.</span></span> <span data-ttu-id="7b25b-131">Peut être utilisé pour les calculs liés à la matrice.</span><span class="sxs-lookup"><span data-stu-id="7b25b-131">Can be used for matrix-related calculations.</span></span> <span data-ttu-id="7b25b-132">L’exemple ci-dessous illustre la multiplication d’une matrice en sa matrice transposée correspondante à l’aide de SIMD.</span><span class="sxs-lookup"><span data-stu-id="7b25b-132">The example below demonstrates multiplication of a matrix to its correspondent transpose matrix using SIMD.</span></span>

```csharp
var m1 = new Matrix4x4(
            1.1f, 1.2f, 1.3f, 1.4f,
            2.1f, 2.2f, 3.3f, 4.4f,
            3.1f, 3.2f, 3.3f, 3.4f,
            4.1f, 4.2f, 4.3f, 4.4f);

var m2 = Matrix4x4.Transpose(m1);
var mResult = Matrix4x4.Multiply(m1, m2);
```

## <a name="vectort"></a><span data-ttu-id="7b25b-133">Vecteur\<T></span><span class="sxs-lookup"><span data-stu-id="7b25b-133">Vector\<T></span></span>

<span data-ttu-id="7b25b-134">Le <xref:System.Numerics.Vector%601> donne la possibilité d’utiliser des vecteurs plus longs.</span><span class="sxs-lookup"><span data-stu-id="7b25b-134">The <xref:System.Numerics.Vector%601> gives the ability to use longer vectors.</span></span> <span data-ttu-id="7b25b-135">Le nombre d’une <xref:System.Numerics.Vector%601> instance est fixe, mais sa valeur <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> dépend de l’UC de l’ordinateur qui exécute le code.</span><span class="sxs-lookup"><span data-stu-id="7b25b-135">The count of a <xref:System.Numerics.Vector%601> instance is fixed, but its value <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> depends on the CPU of the machine running the code.</span></span>

<span data-ttu-id="7b25b-136">L’exemple ci-dessous montre comment ajouter des éléments <xref:System.Numerics.Vector%601>de tableaux longs à l’aide de.</span><span class="sxs-lookup"><span data-stu-id="7b25b-136">The example below demonstrates adding long arrays elements using <xref:System.Numerics.Vector%601>.</span></span>

```csharp
double[] SimdVectorProd(double[] left, double[] right)
{
    var offset = Vector<double>.Count;
    double[] result = new double[left.Length];
    int i = 0;
    for (i = 0; i < left.Length; i += offset)
    {
        var v1 = new Vector<double>(left, i);
        var v2 = new Vector<double>(right, i);
        (v1 * v2).CopyTo(result, i);
    }

    //remaining items
    for (; i < left.Length; ++i)
    {
        result[i] = left[i] * right[i];
    }

    return result;
}
```

## <a name="remarks"></a><span data-ttu-id="7b25b-137">Notes</span><span class="sxs-lookup"><span data-stu-id="7b25b-137">Remarks</span></span>

<span data-ttu-id="7b25b-138">SIMD est plus susceptible de supprimer un goulot d’étranglement et d’exposer le prochain, par exemple le débit de mémoire.</span><span class="sxs-lookup"><span data-stu-id="7b25b-138">SIMD is more likely to remove one bottleneck and expose the next, for example memory throughput.</span></span> <span data-ttu-id="7b25b-139">En général, les avantages en matière de performances de l’utilisation de SIMD varient en fonction du scénario spécifique et, dans certains cas, il peut même s’exécuter pire qu’un code équivalent non-SIMD plus simple.</span><span class="sxs-lookup"><span data-stu-id="7b25b-139">In general the performance benefit of using SIMD varies depending on the specific scenario, and in some cases it can even perform worse than simpler non-SIMD equivalent code.</span></span>
