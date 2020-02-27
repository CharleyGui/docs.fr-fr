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
# <a name="default-values-of-c-types-c-reference"></a>Valeurs par défaut C# des typesC# (référence)

Le tableau suivant présente les valeurs par défaut des types C# :

|Type|Valeur par défaut|
|---------|------------------|
|tout type référence ;|`null`|
|Tout [type numérique intégral intégré](integral-numeric-types.md)|0 (zéro)|
|Tout [type numérique à virgule flottante intégré](floating-point-numeric-types.md)|0 (zéro)|
|[bool](bool.md)|`false`|
|[char](char.md)|`'\0'` (U+0000)|
|[enum](enum.md)|Valeur produite par l’expression `(E)0`, où `E` est l’identificateur de l’enum.|
|[struct](struct.md)|Valeur produite en affectant à tous les champs de type valeur leur valeur par défaut et à tous les champs de type référence la valeur `null`.|
|Tout [type valeur Nullable](nullable-value-types.md)|Instance pour laquelle la propriété <xref:System.Nullable%601.HasValue%2A> a la valeur `false` et la propriété <xref:System.Nullable%601.Value%2A> n’est pas définie. Cette valeur par défaut est également connue sous le nom de valeur *null* d’un type valeur Nullable.|

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

Au moment de l’exécution, si l’instance <xref:System.Type?displayProperty=nameWithType> représente un type valeur, vous pouvez utiliser la méthode <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> pour appeler le constructeur sans paramètre afin d’obtenir la valeur par défaut du type.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Valeurs par défaut](~/_csharplang/spec/variables.md#default-values)
- [Constructeurs par défaut](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Constructeurs](../../programming-guide/classes-and-structs/constructors.md)
