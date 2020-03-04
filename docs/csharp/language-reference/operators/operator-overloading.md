---
title: Surcharge d’opérateur - Référence C#
description: Découvrez comment surcharger un opérateur C# et quels opérateurs C# sont surchargeables.
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: c59ae6960a77efd866db4748ca537d9e5218fd1e
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78238973"
---
# <a name="operator-overloading-c-reference"></a>Surcharge d’opérateur (référence C#)

Un type défini par l’utilisateur peut surcharger un opérateur C# prédéfini. Autrement dit, un type peut fournir l’implémentation personnalisée d’une opération dans le cas où un ou les deux opérandes sont de ce type. La section [Opérateurs surchargeables](#overloadable-operators) indique les opérateurs C# qui peuvent être surchargés.

Utilisez le mot clé `operator` pour déclarer un opérateur. Une déclaration d’opérateur doit respecter les règles suivantes :

- Elle contient un modificateur `public` et un modificateur `static`.
- Un opérateur unaire possède un paramètre d’entrée. Un opérateur binaire a deux paramètres d’entrée. Dans chaque cas, au moins un paramètre doit avoir le type `T` ou `T?`, où `T` est le type qui contient la déclaration d’opérateur.

L’exemple suivant définit une structure simplifiée pour représenter un nombre rationnel. La structure surcharge certains des [opérateurs arithmétiques](arithmetic-operators.md) :

[!code-csharp[fraction example](~/samples/snippets/csharp/language-reference/operators/OperatorOverloading.cs)]

Vous pouvez étendre l’exemple précédent en [définissant une conversion implicite](user-defined-conversion-operators.md) de `int` en `Fraction`. Les opérateurs surchargés devraient alors prendre en charge les arguments de ces deux types. Autrement dit, il deviendrait possible d’ajouter un entier à une fraction et d’obtenir une fraction en conséquence.

Vous utilisez également le mot clé `operator` pour définir une conversion de type personnalisée. Pour plus d’informations, consultez [Opérateurs de conversion définie par l’utilisateur](user-defined-conversion-operators.md).

## <a name="overloadable-operators"></a>Opérateurs surchargeables

Le tableau suivant fournit des informations sur la possibilité de surcharge des opérateurs C# :

| Opérateurs | Possibilité de surcharge |
| --------- | --------------- |
|[+x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [!x](boolean-logical-operators.md#logical-negation-operator-), [~x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](arithmetic-operators.md#increment-operator-), [--](arithmetic-operators.md#decrement-operator---), [true](true-false-operators.md), [false](true-false-operators.md)|Ces opérateurs unaires peuvent être surchargés.|
|[x + y](addition-operator.md), [x - y](subtraction-operator.md), [x \* y](arithmetic-operators.md#multiplication-operator-), [x / y](arithmetic-operators.md#division-operator-), [x % y](arithmetic-operators.md#remainder-operator-), [x & y](boolean-logical-operators.md#logical-and-operator-), [x &#124; y](boolean-logical-operators.md#logical-or-operator-), [x ^ y](boolean-logical-operators.md#logical-exclusive-or-operator-), [x \<\< y](bitwise-and-shift-operators.md#left-shift-operator-), [x >> y](bitwise-and-shift-operators.md#right-shift-operator-), [x == y](equality-operators.md#equality-operator-), [x != y](equality-operators.md#inequality-operator-), [x \< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-), [x \<= y](comparison-operators.md#less-than-or-equal-operator-), [x >= y](comparison-operators.md#greater-than-or-equal-operator-)|Ces opérateurs binaires peuvent être surchargés. Certains opérateurs doivent être surchargés par paires. Pour plus d’informations, consultez la remarque qui suit ce tableau.|
|[x && y](boolean-logical-operators.md#conditional-logical-and-operator-), [x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-)|Les opérateurs logiques conditionnels ne peuvent pas être surchargés. Toutefois, si un type avec les [opérateurs `true` et `false`](true-false-operators.md) surchargés surcharge également l’opérateur `&` ou <code>&#124;</code> d’une certaine manière, l’opérateur `&&` ou <code>&#124;&#124;</code> peut être évalué respectivement pour les opérandes de ce type. Pour plus d’informations, consultez la section [Opérateurs logiques conditionnels définis par l’utilisateur](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).|
|[a&#91;i&#93;](member-access-operators.md#indexer-operator-)|L’accès à un élément n’est pas considéré comme un opérateur surchargeable, mais vous pouvez définir un [indexeur](../../programming-guide/indexers/index.md).|
|[(T)x](type-testing-and-cast.md#cast-operator-)|L’opérateur de cast ne peut pas être surchargé, mais vous pouvez définir de nouveaux opérateurs de conversion. Pour plus d’informations, consultez [Opérateurs de conversion définie par l’utilisateur](user-defined-conversion-operators.md).|
|[+=](arithmetic-operators.md#compound-assignment), [-=](arithmetic-operators.md#compound-assignment), [\*=](arithmetic-operators.md#compound-assignment), [/=](arithmetic-operators.md#compound-assignment), [%=](arithmetic-operators.md#compound-assignment), [&=](boolean-logical-operators.md#compound-assignment), [&#124;=](boolean-logical-operators.md#compound-assignment), [^=](boolean-logical-operators.md#compound-assignment), [\<\<=](bitwise-and-shift-operators.md#compound-assignment), [>>=](bitwise-and-shift-operators.md#compound-assignment)|Les opérateurs d’assignation composée ne peuvent pas être surchargés explicitement. Toutefois, quand vous surchargez un opérateur binaire, l’opérateur d’assignation composée correspondant, le cas échéant, est aussi implicitement surchargé. Par exemple, `+=` est évalué à l’aide de l’opérateur `+`, qui peut être surchargé.|
|[^ x](member-access-operators.md#index-from-end-operator-), [x = y](assignment-operator.md), [x. y](member-access-operators.md#member-access-operator-), [c ? t : f](conditional-operator.md), [x ?? y](null-coalescing-operator.md), [x ?? = y](null-coalescing-operator.md), [x.. y](member-access-operators.md#range-operator-), [x-> y](pointer-related-operators.md#pointer-member-access-operator--), [=>](lambda-operator.md), [f (x)](member-access-operators.md#invocation-operator-), [As](type-testing-and-cast.md#as-operator), [await](await.md), [activé](../keywords/checked.md), [désactivé,](../keywords/unchecked.md) [par défaut](default.md), [délégué](delegate-operator.md), [est](type-testing-and-cast.md#is-operator), [nameof](nameof.md), [New](new-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [typeof](type-testing-and-cast.md#typeof-operator)|Ces opérateurs ne peuvent pas être surchargés.|

> [!NOTE]
> Les opérateurs de comparaison doivent être surchargés par paires. Autrement dit, si l’un des opérateurs d’une paire est surchargé, l’autre doit également l’être. Il s’agit de paires telles que les suivantes :
>
> - Opérateurs `==` et `!=`
> - Opérateurs `<` et `>`
> - Opérateurs `<=` et `>=`

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Surcharge d’opérateur](~/_csharplang/spec/expressions.md#operator-overloading)
- [Opérateurs](~/_csharplang/spec/classes.md#operators)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- [Opérateurs de conversion définie par l’utilisateur](user-defined-conversion-operators.md)
- [Directives de conception-surcharges d’opérateur](../../../standard/design-guidelines/operator-overloads.md)
- [Directives de conception-opérateurs d’égalité](../../../standard/design-guidelines/equality-operators.md)
- Article [Why are overloaded operators always static in C#?](https://docs.microsoft.com/archive/blogs/ericlippert/why-are-overloaded-operators-always-static-in-c)
