---
title: Opérateur C# - Référence C#
ms.date: 08/20/2019
f1_keywords:
- cs.operators
helpviewer_keywords:
- operators [C#]
- operator precedence [C#]
- operator associativity [C#]
- expressions [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 0f7e99aaa171160a813b14dc818846052766551e
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168606"
---
# <a name="c-operators-c-reference"></a>Opérateur C# (Référence C#)

C# fournit plusieurs opérateurs pris en charge par les types intégrés. Par exemple, les [opérateurs arithmétiques](arithmetic-operators.md) effectuent des opérations arithmétiques avec des opérandes numériques et les [opérateurs logiques booléens](boolean-logical-operators.md) effectuent des opérations logiques avec les opérandes [bool](../keywords/bool.md). Certains opérateurs peuvent être [surchargés](operator-overloading.md). Avec la surcharge d’opérateur, vous pouvez spécifier le comportement de l’opérateur pour les opérandes d’un type défini par l’utilisateur.

Dans une [expression](../../programming-guide/statements-expressions-operators/expressions.md), la priorité et l’associativité des opérateurs déterminent l’ordre dans lequel les opérations sont exécutées. Vous pouvez utiliser des parenthèses pour changer l’ordre d’évaluation imposé par la priorité et l’associativité de l’opérateur.

## <a name="operator-precedence"></a>Précédence des opérateurs

Dans une expression avec plusieurs opérateurs, les opérateurs avec une priorité plus élevée sont évalués avant les opérateurs avec une priorité moins élevée. Dans l’exemple suivant, la multiplication est effectuée en premier, car elle a une priorité plus élevée que l’addition :

```csharp-interactive
var a = 2 + 2 * 2;
Console.WriteLine(a); //  output: 6
```

Utilisez des parenthèses pour changer l’ordre d’évaluation imposé par la précédence des opérateurs :

```csharp-interactive
var a = (2 + 2) * 2;
Console.WriteLine(a); //  output: 8
```

La table suivante répertorie les opérateurs C# de la priorité la plus élevée à la plus basse. Les opérateurs dans chaque ligne sont de priorité égale.

| Opérateurs | Catégorie ou nom |
| --------- | ---------------- |
| [x.y](member-access-operators.md#member-access-operator-), [x?.y](member-access-operators.md#null-conditional-operators--and-), [x?[y]](member-access-operators.md#null-conditional-operators--and-), [f(x)](member-access-operators.md#invocation-operator-), [a&#91;i&#93;](member-access-operators.md#indexer-operator-), [x++](arithmetic-operators.md#increment-operator-), [x--](arithmetic-operators.md#decrement-operator---), [nouveau](new-operator.md), [typeof](type-testing-and-cast.md#typeof-operator), [vérifié](../keywords/checked.md), [non vérifié](../keywords/unchecked.md), [par défaut](default.md), [nameof](nameof.md), [délégué](delegate-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [x->y](pointer-related-operators.md#pointer-member-access-operator--) | Principale |
| [+x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [\!x](boolean-logical-operators.md#logical-negation-operator-), [~x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++x](arithmetic-operators.md#increment-operator-), [--x](arithmetic-operators.md#decrement-operator---), [(T)x](type-testing-and-cast.md#cast-operator-), [await](await.md), [&x](pointer-related-operators.md#address-of-operator-), [*x](pointer-related-operators.md#pointer-indirection-operator-), [true and false](true-false-operators.md) | Unaire |
| [x * y](arithmetic-operators.md#multiplication-operator-), [x / y](arithmetic-operators.md#division-operator-), [x % y](arithmetic-operators.md#remainder-operator-) | Multiplication|
| [x + y](arithmetic-operators.md#addition-operator-), [x – y](arithmetic-operators.md#subtraction-operator--) | Addition |
| [x \<\<  y](bitwise-and-shift-operators.md#left-shift-operator-), [x >> y](bitwise-and-shift-operators.md#right-shift-operator-) | Shift |
| [x \< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-), [x \<= y](comparison-operators.md#less-than-or-equal-operator-), [x >= y](comparison-operators.md#greater-than-or-equal-operator-), [is](type-testing-and-cast.md#is-operator), [as](type-testing-and-cast.md#as-operator) | Relations et test de type |
| [x == y](equality-operators.md#equality-operator-), [x != y](equality-operators.md#inequality-operator-) | Égalité |
| `x & y` | [Logique booléen AND](boolean-logical-operators.md#logical-and-operator-) ou [logique bitwise AND](bitwise-and-shift-operators.md#logical-and-operator-) |
| `x ^ y` | [Logique booléen XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) ou [logique bitwise XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) |
| <code>x &#124; y</code> | [Logique booléen OR](boolean-logical-operators.md#logical-or-operator-) ou [logique bitwise OR](bitwise-and-shift-operators.md#logical-or-operator-) |
| [x && y](boolean-logical-operators.md#conditional-logical-and-operator-) | AND conditionnel |
| [x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) | OR conditionnel |
| [x ?? y](null-coalescing-operator.md) | Opérateur de fusion de Null |
| [c ? t : f](conditional-operator.md) | Opérateur conditionnel |
| [x = y](assignment-operator.md), [x += y](arithmetic-operators.md#compound-assignment), [x -= y](arithmetic-operators.md#compound-assignment), [x *= y](arithmetic-operators.md#compound-assignment), [x /= y](arithmetic-operators.md#compound-assignment), [x %= y](arithmetic-operators.md#compound-assignment), [x &= y](boolean-logical-operators.md#compound-assignment), [x &#124;= y](boolean-logical-operators.md#compound-assignment), [x ^= y](boolean-logical-operators.md#compound-assignment), [x <<= y](bitwise-and-shift-operators.md#compound-assignment), [x >>= y](bitwise-and-shift-operators.md#compound-assignment), [=>](lambda-operator.md) | Affectation et déclaration lambda |

## <a name="operator-associativity"></a>Associativité des opérateurs

Quand les opérateurs sont de même priorité, l’associativité des opérateurs détermine l’ordre dans lequel les opérations sont effectuées :

- Les opérateurs *associatifs sur leur gauche* sont évalués dans l’ordre, de gauche à droite. À l’exception des [opérateurs d’assignation](assignment-operator.md) et de l’[opérateur de fusion null`??`](null-coalescing-operator.md), tous les opérateurs binaires sont associatifs sur leur gauche. Par exemple, `a + b - c` est évalué comme étant `(a + b) - c`.
- Les opérateurs *associatifs sur leur droite* sont évalués dans l’ordre, de droite à gauche. Les opérateurs d’assignation, l’opérateur de fusion null `??` et l’[opérateur conditionnel`?:`](conditional-operator.md) sont associatifs sur leur droite. Par exemple, `x = y = z` est évalué comme étant `x = (y = z)`.

Utilisez des parenthèses pour changer l’ordre d’évaluation imposé par l’associativité des opérateurs :

```csharp-interactive
int a = 13 / 5 / 2;
int b = 13 / (5 / 2);
Console.WriteLine($"a = {a}, b = {b}");  // output: a = 1, b = 6
```

## <a name="operand-evaluation"></a>Évaluation des opérandes

Sans rapport avec la priorité et l’associativité des opérateurs, les opérandes dans une expression sont évalués de gauche à droite. Les exemples suivants illustrent l’ordre dans lequel les opérateurs et les opérandes sont évalués :

| Expression | Ordre d'évaluation |
| ---------- | ------------------- |
|`a + b`|a, b, +|
|`a + b * c`|a, b, c, *, +|
|`a / b + c * d`|a, b, /, c, d, *, +|
|`a / (b + c) * d`|a, b, c, +, /, d, *|

En règle générale, tous les opérandes d’opérateur sont évalués. Certains opérateurs évaluent les opérandes de manière conditionnelle. Autrement dit, la valeur du premier opérande d’un opérateur définit si d’autres (ou quels autres) opérandes doivent être évalués. Ces opérateurs sont les opérateurs conditionnels logiques [AND (`&&`)](boolean-logical-operators.md#conditional-logical-and-operator-) et [OR (`||`)](boolean-logical-operators.md#conditional-logical-or-operator-), l’[opérateur de fusion null`??`](null-coalescing-operator.md), les [opérateurs conditionnels nuls `?.` et `?[]`](member-access-operators.md#null-conditional-operators--and-), et l’[opérateur conditionnel `?:`](conditional-operator.md). Reportez-vous à la description de chaque opérateur pour plus de détails.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Opérateurs](~/_csharplang/spec/expressions.md#operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Expressions](../../programming-guide/statements-expressions-operators/expressions.md)
