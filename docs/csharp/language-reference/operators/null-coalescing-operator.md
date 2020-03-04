---
title: ?? et ?? = Operators C# -référence
ms.date: 09/10/2019
f1_keywords:
- ??_CSharpKeyword
- ??=_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
- null-coalescing assignment [C#]
- ??= operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: ce16f732fae0eec38b2a55af055e51c5fe70773a
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239155"
---
# <a name="-and--operators-c-reference"></a>?? et ?? =, opérateursC# (référence)

L’opérateur de fusion null `??` retourne la valeur de l’opérande de gauche si elle n’est pas `null` ; sinon, il évalue l’opérande de droite et retourne son résultat. L’opérateur `??` n’évalue pas son opérande de droite si l’opérande de gauche n’est pas Null.

Disponible dans C# 8,0 et versions ultérieures, l’opérateur d’assignation de fusion Null `??=` affecte la valeur de son opérande droit à son opérande de gauche uniquement si l’opérande de gauche prend la valeur `null`. L’opérateur `??=` n’évalue pas son opérande de droite si l’opérande de gauche n’est pas Null.

[!code-csharp[null-coalescing assignment](~/samples/snippets/csharp/language-reference/operators/NullCoalescingOperator.cs#Assignment)]

L’opérande gauche de l’opérateur `??=` doit être une variable, une [propriété](../../programming-guide/classes-and-structs/properties.md)ou un élément [indexeur](../../programming-guide/indexers/index.md) .

Dans C# 7,3 et les versions antérieures, le type de l’opérande gauche de l’opérateur `??` doit être un type [référence](../keywords/reference-types.md) ou un [type valeur Nullable](../builtin-types/nullable-value-types.md). À partir C# de 8,0, cette exigence est remplacée par ce qui suit : le type de l’opérande gauche des opérateurs `??` et `??=` ne peut pas être un type valeur non Nullable. En particulier, à partir C# de 8,0, vous pouvez utiliser les opérateurs de fusion Null avec des paramètres de type sans contrainte :

[!code-csharp[unconstrained type parameter](~/samples/snippets/csharp/language-reference/operators/NullCoalescingOperator.cs#UnconstrainedType)]

Les opérateurs de fusion Null sont associatifs à droite. Autrement dit, les expressions de la forme

```csharp
a ?? b ?? c
d ??= e ??= f
```

sont évaluées comme

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a>Exemples

Les opérateurs `??` et `??=` peuvent être utiles dans les scénarios suivants :

- Dans les expressions avec les [opérateurs conditionnels null ?. et ? []](member-access-operators.md#null-conditional-operators--and-), vous pouvez utiliser l’opérateur `??` pour fournir une autre expression à évaluer au cas où le résultat de l’expression avec des opérations conditionnelles null est `null`:

  [!code-csharp-interactive[with null-conditional](~/samples/snippets/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- Quand vous utilisez des [types valeur Nullable](../builtin-types/nullable-value-types.md) et que vous devez fournir une valeur d’un type valeur sous-jacent, utilisez l’opérateur `??` pour spécifier la valeur à fournir dans le cas où une valeur de type nullable est `null`:

  [!code-csharp-interactive[with nullable types](~/samples/snippets/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  Utilisez la méthode <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> si la valeur à utiliser quand une valeur de type Nullable est `null` doit être la valeur par défaut du type valeur sous-jacent.

- À partir C# de 7,0, vous pouvez utiliser une [expression`throw`](../keywords/throw.md#the-throw-expression) comme opérande de droite de l’opérateur `??` pour rendre le code de vérification des arguments plus concis :

  [!code-csharp[with throw expression](~/samples/snippets/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  L’exemple précédent montre également comment utiliser des [membres expression-bodied](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) pour définir une propriété.

- À partir C# de 8,0, vous pouvez utiliser l’opérateur `??=` pour remplacer le code du formulaire.

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  par le code suivant :

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Les opérateurs `??` et `??=` ne peuvent pas être surchargés.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations sur l’opérateur `??`, consultez [la section opérateur de fusion Null](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) de la [ C# spécification du langage](~/_csharplang/spec/introduction.md).

Pour plus d’informations sur l’opérateur `??=`, consultez la [Remarque relative](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md)à la proposition de fonctionnalité.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- [Opérateurs ?. et ?[]](member-access-operators.md#null-conditional-operators--and-)
- [?:, opérateur](conditional-operator.md)
