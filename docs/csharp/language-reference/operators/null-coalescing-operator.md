---
title: ?? Opérateur - Référence C#
ms.custom: seodec18
ms.date: 06/07/2019
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: a19b5558da36ffb11dabd1b9bec419a3623a0f17
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024991"
---
# <a name="-operator-c-reference"></a>?? Opérateur (référence C#)

L’opérateur de fusion null `??` retourne la valeur de l’opérande de gauche si elle n’est pas `null` ; sinon, il évalue l’opérande de droite et retourne son résultat. L’opérateur `??` n’évalue pas son opérande de droite si l’opérande de gauche n’est pas Null.

L’opérateur de fusion null est associatif à droite ; autrement dit, une expression de la forme

```csharp
a ?? b ?? c
```

est évaluée comme étant

```csharp
a ?? (b ?? c)
```

L’opérateur `??` peut être utile dans les scénarios suivants :

- Dans les expressions avec les [opérateurs conditionnels Null ?. et ?[]](member-access-operators.md#null-conditional-operators--and-), vous pouvez utiliser l’opérateur de fusion Null pour fournir une autre expression à évaluer au cas où le résultat de l’expression avec les opérations conditionnelles Null serait `null` :

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- Quand vous travaillez avec des [types valeur Nullable](../../programming-guide/nullable-types/index.md) et que vous devez fournir une valeur d’un type valeur sous-jacent, utilisez l’opérateur de fusion Null pour spécifier la valeur à fournir au cas où une valeur de type Nullable serait `null` :

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  Utilisez la méthode <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> si la valeur à utiliser quand une valeur de type Nullable est `null` doit être la valeur par défaut du type valeur sous-jacent.

- À compter de C# 7.0, vous pouvez utiliser une [expression `throw`](../keywords/throw.md#the-throw-expression) comme opérande droit de l’opérateur de fusion Null pour rendre le code de vérification d’argument plus concis :

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  L’exemple précédent montre également comment utiliser des [membres expression-bodied](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) pour définir une propriété.

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

L’opérateur de fusion Null ne peut pas être surchargé.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Opérateur de fusion Null](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- [Opérateurs ?. et ?[]](member-access-operators.md#null-conditional-operators--and-)
- [?:, opérateur](conditional-operator.md)
