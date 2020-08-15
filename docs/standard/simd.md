---
title: Types accélérés SIMD dans .NET
description: Cet article décrit les types SIMD-Enable dans .NET et montre comment utiliser les opérations matérielles SIMD en C# et .NET.
author: FIVIL
ms.author: tagoo
ms.date: 04/28/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 5c1ad01ea15a9c4352cf7f87e5fba3bf74b4679c
ms.sourcegitcommit: 2987e241e2f76c9248d2146bf2761a33e2c7a882
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "88228734"
---
# <a name="use-simd-accelerated-numeric-types"></a><span data-ttu-id="12a3f-103">Utiliser des types numériques SIMD accélérés</span><span class="sxs-lookup"><span data-stu-id="12a3f-103">Use SIMD-accelerated numeric types</span></span>

<span data-ttu-id="12a3f-104">SIMD (instruction unique, plusieurs données) fournit une prise en charge matérielle pour effectuer une opération sur plusieurs éléments de données, en parallèle, à l’aide d’une seule instruction.</span><span class="sxs-lookup"><span data-stu-id="12a3f-104">SIMD (Single instruction, multiple data) provides hardware support for performing an operation on multiple pieces of data, in parallel, using a single instruction.</span></span> <span data-ttu-id="12a3f-105">Dans .NET, il existe un ensemble de types accélérés SIMD sous l' <xref:System.Numerics> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="12a3f-105">In .NET, there's set of SIMD-accelerated types under the <xref:System.Numerics> namespace.</span></span> <span data-ttu-id="12a3f-106">Les opérations SIMD peuvent être parallèles au niveau du matériel.</span><span class="sxs-lookup"><span data-stu-id="12a3f-106">SIMD operations can be parallelized at the hardware level.</span></span> <span data-ttu-id="12a3f-107">Cela augmente le débit des calculs vectorisés, couramment utilisés dans les applications mathématiques, scientifiques et graphiques.</span><span class="sxs-lookup"><span data-stu-id="12a3f-107">That increases the throughput of the vectorized computations, which are common in mathematical, scientific, and graphics apps.</span></span>

## <a name="net-simd-accelerated-types"></a><span data-ttu-id="12a3f-108">Types accélérés SIMD .NET</span><span class="sxs-lookup"><span data-stu-id="12a3f-108">.NET SIMD-accelerated types</span></span>

<span data-ttu-id="12a3f-109">Les types accélérés par le .NET SIMD incluent les types suivants :</span><span class="sxs-lookup"><span data-stu-id="12a3f-109">The .NET SIMD-accelerated types include the following types:</span></span>

- <span data-ttu-id="12a3f-110">Les types <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3> et <xref:System.Numerics.Vector4>, qui représentent des vecteurs à 2, 3 et 4 valeurs <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="12a3f-110">The <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4> types, which represent vectors with 2, 3, and 4 <xref:System.Single> values.</span></span>

- <span data-ttu-id="12a3f-111">Deux types de matrices, <xref:System.Numerics.Matrix3x2> , qui représente une matrice matrice, et <xref:System.Numerics.Matrix4x4> , qui représente une matrice 4x4 de <xref:System.Single> valeurs.</span><span class="sxs-lookup"><span data-stu-id="12a3f-111">Two matrix types, <xref:System.Numerics.Matrix3x2>, which represents a 3x2 matrix, and <xref:System.Numerics.Matrix4x4>, which represents a 4x4 matrix of <xref:System.Single> values.</span></span>

- <span data-ttu-id="12a3f-112"><xref:System.Numerics.Plane>Type, qui représente un plan dans l’espace tridimensionnel à l’aide de <xref:System.Single> valeurs.</span><span class="sxs-lookup"><span data-stu-id="12a3f-112">The <xref:System.Numerics.Plane> type, which represents a plane in three-dimensional space using <xref:System.Single> values.</span></span>

- <span data-ttu-id="12a3f-113"><xref:System.Numerics.Quaternion>Type, qui représente un vecteur utilisé pour encoder des rotations physiques en trois dimensions à l’aide de <xref:System.Single> valeurs.</span><span class="sxs-lookup"><span data-stu-id="12a3f-113">The <xref:System.Numerics.Quaternion> type, which represents a vector that is used to encode three-dimensional physical rotations using <xref:System.Single> values.</span></span>

- <span data-ttu-id="12a3f-114">Le type <xref:System.Numerics.Vector%601>, qui représente un vecteur d’un type numérique spécifié et fournit un large éventail d’opérateurs bénéficiant d’un support SIMD.</span><span class="sxs-lookup"><span data-stu-id="12a3f-114">The <xref:System.Numerics.Vector%601> type, which represents a vector of a specified numeric type and provides a broad set of operators that benefit from SIMD support.</span></span> <span data-ttu-id="12a3f-115">Le nombre d’une <xref:System.Numerics.Vector%601> instance est fixe pour la durée de vie d’une application, mais sa valeur <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> dépend de l’UC de l’ordinateur qui exécute le code.</span><span class="sxs-lookup"><span data-stu-id="12a3f-115">The count of a <xref:System.Numerics.Vector%601> instance is fixed for the lifetime of an application, but its value <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> depends on the CPU of the machine running the code.</span></span>

  > [!NOTE]
  > <span data-ttu-id="12a3f-116">Le <xref:System.Numerics.Vector%601> type n’est pas inclus dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="12a3f-116">The <xref:System.Numerics.Vector%601> type is not included in the .NET Framework.</span></span> <span data-ttu-id="12a3f-117">Vous devez installer le package NuGet [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) pour accéder à ce type.</span><span class="sxs-lookup"><span data-stu-id="12a3f-117">You must install the [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) NuGet package to get access to this type.</span></span>
  
<span data-ttu-id="12a3f-118">Les types accélérés SIMD sont implémentés de telle sorte qu’ils peuvent être utilisés avec le matériel ou les compilateurs JIT non-SIMD.</span><span class="sxs-lookup"><span data-stu-id="12a3f-118">The SIMD-accelerated types are implemented in such a way that they can be used with non-SIMD-accelerated hardware or JIT compilers.</span></span> <span data-ttu-id="12a3f-119">Pour tirer parti des instructions SIMD, vos applications 64 bits doivent être exécutées par le runtime qui utilise le compilateur **RyuJIT** .</span><span class="sxs-lookup"><span data-stu-id="12a3f-119">To take advantage of SIMD instructions, your 64-bit apps must be run by the runtime that uses the **RyuJIT** compiler.</span></span> <span data-ttu-id="12a3f-120">Un compilateur **RyuJIT** est inclus dans .net Core et dans .NET Framework 4,6 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="12a3f-120">A **RyuJIT** compiler is included in .NET Core and in .NET Framework 4.6 and later.</span></span> <span data-ttu-id="12a3f-121">La prise en charge SIMD est fournie uniquement lorsque vous ciblez des processeurs 64 bits.</span><span class="sxs-lookup"><span data-stu-id="12a3f-121">SIMD support is only provided when targeting 64-bit processors.</span></span>

## <a name="how-to-use-simd"></a><span data-ttu-id="12a3f-122">Comment utiliser SIMD ?</span><span class="sxs-lookup"><span data-stu-id="12a3f-122">How to use SIMD?</span></span>

<span data-ttu-id="12a3f-123">Avant d’exécuter des algorithmes SIMD personnalisés, il est possible de vérifier si l’ordinateur hôte prend en charge SIMD à l’aide de <xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType> , qui retourne un <xref:System.Boolean> .</span><span class="sxs-lookup"><span data-stu-id="12a3f-123">Before executing custom SIMD algorithms, it's possible to check if the host machine supports SIMD by using <xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType>, which returns a <xref:System.Boolean>.</span></span> <span data-ttu-id="12a3f-124">Cela ne garantit pas que l’accélération SIMD est activée pour un type spécifique, mais qu’elle est prise en charge par certains types.</span><span class="sxs-lookup"><span data-stu-id="12a3f-124">This doesn't guarantee that SIMD-acceleration is enabled for a specific type, but is an indicator that it's supported by some types.</span></span>

## <a name="simple-vectors"></a><span data-ttu-id="12a3f-125">Vecteurs simples</span><span class="sxs-lookup"><span data-stu-id="12a3f-125">Simple Vectors</span></span>

<span data-ttu-id="12a3f-126">Les types accélérés SIMD les plus primitifs dans .NET sont les <xref:System.Numerics.Vector2> <xref:System.Numerics.Vector3> types, et <xref:System.Numerics.Vector4> , qui représentent des vecteurs avec 2, 3 et 4 <xref:System.Single> valeurs.</span><span class="sxs-lookup"><span data-stu-id="12a3f-126">The most primitive SIMD-accelerated types in .NET are <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4> types, which represent vectors with 2, 3, and 4 <xref:System.Single> values.</span></span> <span data-ttu-id="12a3f-127">L’exemple ci-dessous utilise <xref:System.Numerics.Vector2> pour ajouter deux vecteurs.</span><span class="sxs-lookup"><span data-stu-id="12a3f-127">The example below uses <xref:System.Numerics.Vector2> to add two vectors.</span></span>

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResult = v1 + v2;
```

<span data-ttu-id="12a3f-128">Il est également possible d’utiliser des vecteurs .net pour calculer d’autres propriétés mathématiques de vecteurs tels que `Dot product` , `Transform` , etc `Clamp` .</span><span class="sxs-lookup"><span data-stu-id="12a3f-128">It's also possible to use .NET vectors to calculate other mathematical properties of vectors such as `Dot product`, `Transform`, `Clamp` and so on.</span></span>

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResult1 = Vector2.Dot(v1, v2);
var vResult2 = Vector2.Distance(v1, v2);
var vResult3 = Vector2.Clamp(v1, Vector2.Zero, Vector2.One);
```

## <a name="matrix"></a><span data-ttu-id="12a3f-129">Matrix</span><span class="sxs-lookup"><span data-stu-id="12a3f-129">Matrix</span></span>

<span data-ttu-id="12a3f-130"><xref:System.Numerics.Matrix3x2>, qui représente une matrice matrice, et <xref:System.Numerics.Matrix4x4> , qui représente une matrice 4x4.</span><span class="sxs-lookup"><span data-stu-id="12a3f-130"><xref:System.Numerics.Matrix3x2>, which represents a 3x2 matrix, and <xref:System.Numerics.Matrix4x4>, which represents a 4x4 matrix.</span></span> <span data-ttu-id="12a3f-131">Peut être utilisé pour les calculs liés à la matrice.</span><span class="sxs-lookup"><span data-stu-id="12a3f-131">Can be used for matrix-related calculations.</span></span> <span data-ttu-id="12a3f-132">L’exemple ci-dessous illustre la multiplication d’une matrice en sa matrice transposée correspondante à l’aide de SIMD.</span><span class="sxs-lookup"><span data-stu-id="12a3f-132">The example below demonstrates multiplication of a matrix to its correspondent transpose matrix using SIMD.</span></span>

```csharp
var m1 = new Matrix4x4(
            1.1f, 1.2f, 1.3f, 1.4f,
            2.1f, 2.2f, 3.3f, 4.4f,
            3.1f, 3.2f, 3.3f, 3.4f,
            4.1f, 4.2f, 4.3f, 4.4f);

var m2 = Matrix4x4.Transpose(m1);
var mResult = Matrix4x4.Multiply(m1, m2);
```

## <a name="vectort"></a><span data-ttu-id="12a3f-133">Vecteur\<T></span><span class="sxs-lookup"><span data-stu-id="12a3f-133">Vector\<T></span></span>

<span data-ttu-id="12a3f-134">Le <xref:System.Numerics.Vector%601> donne la possibilité d’utiliser des vecteurs plus longs.</span><span class="sxs-lookup"><span data-stu-id="12a3f-134">The <xref:System.Numerics.Vector%601> gives the ability to use longer vectors.</span></span> <span data-ttu-id="12a3f-135">Le nombre d’une <xref:System.Numerics.Vector%601> instance est fixe, mais sa valeur <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> dépend de l’UC de l’ordinateur qui exécute le code.</span><span class="sxs-lookup"><span data-stu-id="12a3f-135">The count of a <xref:System.Numerics.Vector%601> instance is fixed, but its value <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> depends on the CPU of the machine running the code.</span></span>

<span data-ttu-id="12a3f-136">L’exemple ci-dessous montre comment ajouter des éléments de tableaux longs à l’aide de <xref:System.Numerics.Vector%601> .</span><span class="sxs-lookup"><span data-stu-id="12a3f-136">The example below demonstrates adding long arrays elements using <xref:System.Numerics.Vector%601>.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="12a3f-137">Notes</span><span class="sxs-lookup"><span data-stu-id="12a3f-137">Remarks</span></span>

<span data-ttu-id="12a3f-138">SIMD est plus susceptible de supprimer un goulot d’étranglement et d’exposer le prochain, par exemple le débit de mémoire.</span><span class="sxs-lookup"><span data-stu-id="12a3f-138">SIMD is more likely to remove one bottleneck and expose the next, for example memory throughput.</span></span> <span data-ttu-id="12a3f-139">En général, les avantages en matière de performances de l’utilisation de SIMD varient en fonction du scénario spécifique et, dans certains cas, il peut même s’exécuter pire qu’un code équivalent non-SIMD plus simple.</span><span class="sxs-lookup"><span data-stu-id="12a3f-139">In general the performance benefit of using SIMD varies depending on the specific scenario, and in some cases it can even perform worse than simpler non-SIMD equivalent code.</span></span>
