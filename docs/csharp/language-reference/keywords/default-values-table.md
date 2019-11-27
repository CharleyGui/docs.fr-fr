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
# <a name="default-values-table-c-reference"></a>Tableau des valeurs par défaut (référence C#)

Le tableau suivant présente les valeurs par défaut des types C# :

|Type|Valeur par défaut|
|---------|------------------|
|tout type référence ;|`null`|
|Tout [type numérique intégral intégré](../builtin-types/integral-numeric-types.md)|0 (zéro)|
|Tout [type numérique à virgule flottante intégré](../builtin-types/floating-point-numeric-types.md)|0 (zéro)|
|[bool](bool.md)|`false`|
|[char](../builtin-types/char.md)|`'\0'` (U+0000)|
|[enum](enum.md)|Valeur produite par l’expression `(E)0`, où `E` est l’identificateur de l’enum.|
|[struct](struct.md)|Valeur produite en affectant à tous les champs de type valeur leur valeur par défaut et à tous les champs de type référence la valeur `null`.|
|Tout [type valeur Nullable](../builtin-types/nullable-value-types.md)|Instance pour laquelle la propriété <xref:System.Nullable%601.HasValue%2A> a la valeur `false` et la propriété <xref:System.Nullable%601.Value%2A> n’est pas définie. Cette valeur par défaut est également connue sous le nom de valeur *null* d’un type valeur Nullable.|

Utilisez l’[opérateur par défaut](../operators/default.md) pour produire la valeur par défaut d’un type, comme illustré dans l’exemple suivant :

```csharp
int a = default(int);
```

À compter de C# 7.1, vous pouvez utiliser le [littéral `default`](../operators/default.md#default-literal) pour initialiser une variable avec la valeur par défaut de son type :

```csharp
int a = default;
```

Pour un type valeur, le constructeur sans paramètre implicite produit également la valeur par défaut du type, comme le montre l’exemple suivant :

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Valeurs par défaut](~/_csharplang/spec/variables.md#default-values)
- [Constructeurs par défaut](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Mots clés C#](index.md)
- [Tableaux des types intégrés](built-in-types-table.md)
- [Constructeurs](../../programming-guide/classes-and-structs/constructors.md)
