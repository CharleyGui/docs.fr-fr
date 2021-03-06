---
title: Types accélérés SIMD dans .NET
description: Cet article décrit les types SIMD-Enable dans .NET et montre comment utiliser les opérations matérielles SIMD en C# et .NET.
author: FIVIL
ms.author: tagoo
ms.date: 04/28/2020
ms.openlocfilehash: 9ac437fd78ed81cd4c2d786f52bac80c5cf22e8f
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826622"
---
# <a name="use-simd-accelerated-numeric-types"></a>Utiliser des types numériques SIMD accélérés

SIMD (instruction unique, plusieurs données) fournit une prise en charge matérielle pour effectuer une opération sur plusieurs éléments de données, en parallèle, à l’aide d’une seule instruction. Dans .NET, il existe un ensemble de types accélérés SIMD sous l' <xref:System.Numerics> espace de noms. Les opérations SIMD peuvent être parallèles au niveau du matériel. Cela augmente le débit des calculs vectorisés, couramment utilisés dans les applications mathématiques, scientifiques et graphiques.

## <a name="net-simd-accelerated-types"></a>Types accélérés SIMD .NET

Les types accélérés par le .NET SIMD incluent les types suivants :

- Les types <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3> et <xref:System.Numerics.Vector4>, qui représentent des vecteurs à 2, 3 et 4 valeurs <xref:System.Single>.

- Deux types de matrices, <xref:System.Numerics.Matrix3x2> , qui représente une matrice matrice, et <xref:System.Numerics.Matrix4x4> , qui représente une matrice 4x4 de <xref:System.Single> valeurs.

- <xref:System.Numerics.Plane>Type, qui représente un plan dans l’espace tridimensionnel à l’aide de <xref:System.Single> valeurs.

- <xref:System.Numerics.Quaternion>Type, qui représente un vecteur utilisé pour encoder des rotations physiques en trois dimensions à l’aide de <xref:System.Single> valeurs.

- Le type <xref:System.Numerics.Vector%601>, qui représente un vecteur d’un type numérique spécifié et fournit un large éventail d’opérateurs bénéficiant d’un support SIMD. Le nombre d’une <xref:System.Numerics.Vector%601> instance est fixe pour la durée de vie d’une application, mais sa valeur <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> dépend de l’UC de l’ordinateur qui exécute le code.

  > [!NOTE]
  > Le <xref:System.Numerics.Vector%601> type n’est pas inclus dans le .NET Framework. Vous devez installer le package NuGet [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) pour accéder à ce type.
  
Les types accélérés SIMD sont implémentés de telle sorte qu’ils peuvent être utilisés avec le matériel ou les compilateurs JIT non-SIMD. Pour tirer parti des instructions SIMD, vos applications 64 bits doivent être exécutées par le runtime qui utilise le compilateur **RyuJIT** . Un compilateur **RyuJIT** est inclus dans .net Core et dans .NET Framework 4,6 et versions ultérieures. La prise en charge SIMD est fournie uniquement lorsque vous ciblez des processeurs 64 bits.

## <a name="how-to-use-simd"></a>Comment utiliser SIMD ?

Avant d’exécuter des algorithmes SIMD personnalisés, il est possible de vérifier si l’ordinateur hôte prend en charge SIMD à l’aide de <xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType> , qui retourne un <xref:System.Boolean> . Cela ne garantit pas que l’accélération SIMD est activée pour un type spécifique, mais qu’elle est prise en charge par certains types.

## <a name="simple-vectors"></a>Vecteurs simples

Les types accélérés SIMD les plus primitifs dans .NET sont les <xref:System.Numerics.Vector2> <xref:System.Numerics.Vector3> types, et <xref:System.Numerics.Vector4> , qui représentent des vecteurs avec 2, 3 et 4 <xref:System.Single> valeurs. L’exemple ci-dessous utilise <xref:System.Numerics.Vector2> pour ajouter deux vecteurs.

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResult = v1 + v2;
```

Il est également possible d’utiliser des vecteurs .net pour calculer d’autres propriétés mathématiques de vecteurs tels que `Dot product` , `Transform` , etc `Clamp` .

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResult1 = Vector2.Dot(v1, v2);
var vResult2 = Vector2.Distance(v1, v2);
var vResult3 = Vector2.Clamp(v1, Vector2.Zero, Vector2.One);
```

## <a name="matrix"></a>Matrix

<xref:System.Numerics.Matrix3x2>, qui représente une matrice matrice, et <xref:System.Numerics.Matrix4x4> , qui représente une matrice 4x4. Peut être utilisé pour les calculs liés à la matrice. L’exemple ci-dessous illustre la multiplication d’une matrice en sa matrice transposée correspondante à l’aide de SIMD.

```csharp
var m1 = new Matrix4x4(
            1.1f, 1.2f, 1.3f, 1.4f,
            2.1f, 2.2f, 3.3f, 4.4f,
            3.1f, 3.2f, 3.3f, 3.4f,
            4.1f, 4.2f, 4.3f, 4.4f);

var m2 = Matrix4x4.Transpose(m1);
var mResult = Matrix4x4.Multiply(m1, m2);
```

## <a name="vectort"></a>Vecteur\<T>

Le <xref:System.Numerics.Vector%601> donne la possibilité d’utiliser des vecteurs plus longs. Le nombre d’une <xref:System.Numerics.Vector%601> instance est fixe, mais sa valeur <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> dépend de l’UC de l’ordinateur qui exécute le code.

L’exemple ci-dessous montre comment ajouter des éléments de tableaux longs à l’aide de <xref:System.Numerics.Vector%601> .

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

## <a name="remarks"></a>Notes

SIMD est plus susceptible de supprimer un goulot d’étranglement et d’exposer le prochain, par exemple le débit de mémoire. En général, les avantages en matière de performances de l’utilisation de SIMD varient en fonction du scénario spécifique et, dans certains cas, il peut même s’exécuter pire qu’un code équivalent non-SIMD plus simple.
