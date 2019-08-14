---
title: Opérateur C# - Référence C#
ms.date: 04/30/2019
f1_keywords:
- cs.operators
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 0e49c28f05d52c704a46806559407381c7eb3530
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971247"
---
# <a name="c-operators-c-reference"></a>Opérateur C# (Référence C#)

C# fournit plusieurs opérateurs prédéfinis pris en charge par les types intégrés. Par exemple, les [opérateurs arithmétiques](arithmetic-operators.md) effectuent des opérations arithmétiques avec des opérandes de types numériques intégrés et les [opérateurs logiques booléens](boolean-logical-operators.md) effectuent des opérations logiques avec les opérandes [bool](../keywords/bool.md).

Un type défini par l’utilisateur peut surcharger certains opérateurs pour définir le comportement correspondant des opérandes de ce type. Pour plus d’informations, consultez [Surcharge d’opérateur](operator-overloading.md).

La table suivante répertorie les opérateurs C# de la priorité la plus élevée à la plus basse. Les opérateurs inclus dans chaque ligne partagent le même niveau de priorité.

| Opérateurs | Catégorie ou nom |
| --------- | ---------------- |
| [x.y](member-access-operators.md#member-access-operator-), [x?.y](member-access-operators.md#null-conditional-operators--and-), [x?[y]](member-access-operators.md#null-conditional-operators--and-), [f(x)](member-access-operators.md#invocation-operator-), [a&#91;x&#93;](member-access-operators.md#indexer-operator-), [x++](arithmetic-operators.md#increment-operator-), [x--](arithmetic-operators.md#decrement-operator---), [new](new-operator.md), [typeof](type-testing-and-conversion-operators.md#typeof-operator), [checked](../keywords/checked.md), [unchecked](../keywords/unchecked.md), [default](default.md), [nameof](nameof.md), [delegate](delegate-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [->](pointer-related-operators.md#pointer-member-access-operator--) | Principale |
| [+x](addition-operator.md), [-x](subtraction-operator.md), [\!x](boolean-logical-operators.md#logical-negation-operator-), [~x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++x](arithmetic-operators.md#increment-operator-), [--x](arithmetic-operators.md#decrement-operator---), [(T)x](type-testing-and-conversion-operators.md#cast-operator-), [await](../keywords/await.md), [&x](pointer-related-operators.md#address-of-operator-), [*x](pointer-related-operators.md#pointer-indirection-operator-), [true and false](true-false-operators.md) | Unaire |
| [x * y](arithmetic-operators.md#multiplication-operator-), [x / y](arithmetic-operators.md#division-operator-), [x % y](arithmetic-operators.md#remainder-operator-) | Multiplication|
| [x + y](arithmetic-operators.md#addition-operator-), [x – y](arithmetic-operators.md#subtraction-operator--) | Addition |
| [x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-), [x >> y](bitwise-and-shift-operators.md#right-shift-operator-) | Shift |
| [x \< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-), [x \<= y](comparison-operators.md#less-than-or-equal-operator-), [x >= y](comparison-operators.md#greater-than-or-equal-operator-), [is](type-testing-and-conversion-operators.md#is-operator), [as](type-testing-and-conversion-operators.md#as-operator) | Relations et test de type |
| [x == y](equality-operators.md#equality-operator-), [x != y](equality-operators.md#inequality-operator-) | Égalité |
| `x & y` | [Logique booléen AND](boolean-logical-operators.md#logical-and-operator-) ou [logique bitwise AND](bitwise-and-shift-operators.md#logical-and-operator-) |
| `x ^ y` | [Logique booléen XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) ou [logique bitwise XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) |
| <code>x &#124; y</code> | [Logique booléen OR](boolean-logical-operators.md#logical-or-operator-) ou [logique bitwise OR](bitwise-and-shift-operators.md#logical-or-operator-) |
| [x && y](boolean-logical-operators.md#conditional-logical-and-operator-) | AND conditionnel |
| [x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) | OR conditionnel |
| [x ?? y](null-coalescing-operator.md) | Opérateur de fusion de Null |
| [t ? x : y](conditional-operator.md) | Opérateur conditionnel |
| [x = y](assignment-operator.md), [x += y](arithmetic-operators.md#compound-assignment), [x -= y](arithmetic-operators.md#compound-assignment), [x *= y](arithmetic-operators.md#compound-assignment), [x /= y](arithmetic-operators.md#compound-assignment), [x %= y](arithmetic-operators.md#compound-assignment), [x &= y](boolean-logical-operators.md#compound-assignment), [x &#124;= y](boolean-logical-operators.md#compound-assignment), [x ^= y](boolean-logical-operators.md#compound-assignment), [x <<= y](bitwise-and-shift-operators.md#compound-assignment), [x >>= y](bitwise-and-shift-operators.md#compound-assignment), [=>](lambda-operator.md) | Affectation et déclaration lambda |

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs](../../programming-guide/statements-expressions-operators/operators.md)
