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
# <a name="default-values-of-c-types-c-reference"></a>Valeurs par défaut des types C (référence C)

Le tableau suivant présente les valeurs par défaut des types C# :

|Type|Valeur par défaut|
|---------|------------------|
|tout type référence ;|`null`|
|Tout [type numérique intégral intégré](integral-numeric-types.md)|0 (zéro)|
|Tout [type numérique à virgule flottante intégré](floating-point-numeric-types.md)|0 (zéro)|
|[Bool](bool.md)|`false`|
|[char](char.md)|`'\0'` (U+0000)|
|[Enum](enum.md)|Valeur produite par l’expression `(E)0`, où `E` est l’identificateur de l’enum.|
|[struct](struct.md)|Valeur produite en affectant à tous les champs de type valeur leur valeur par défaut et à tous les champs de type référence la valeur `null`.|
|Tout [type valeur Nullable](nullable-value-types.md)|Instance pour laquelle la propriété <xref:System.Nullable%601.HasValue%2A> a la valeur `false` et la propriété <xref:System.Nullable%601.Value%2A> n’est pas définie. Cette valeur par défaut est également connue sous le nom de valeur *nulle* d’un type de valeur nulle.|

Utilisez [ `default` l’opérateur](../operators/default.md#default-operator) pour produire la valeur par défaut d’un type, comme le montre l’exemple suivant :

```csharp
int a = default(int);
```

En commençant par le C 7.1, vous pouvez utiliser le [ `default` littéral](../operators/default.md#default-literal) pour initialiser une variable avec la valeur par défaut de son type :

```csharp
int a = default;
```

Pour un type valeur, le constructeur sans paramètre implicite produit également la valeur par défaut du type, comme le montre l’exemple suivant :

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

Au moment de <xref:System.Type?displayProperty=nameWithType> l’exécution, si l’instance <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> représente un type de valeur, vous pouvez utiliser la méthode pour invoquer le constructeur sans paramètres pour obtenir la valeur par défaut du type.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Valeurs par défaut](~/_csharplang/spec/variables.md#default-values)
- [Constructeurs par défaut](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Constructeurs](../../programming-guide/classes-and-structs/constructors.md)
