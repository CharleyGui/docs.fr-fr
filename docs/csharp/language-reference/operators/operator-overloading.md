---
title: Surcharge d’opérateur - Référence C#
description: Découvrez comment surcharger un opérateur C# et quels opérateurs C# sont surchargeables.
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: ec2012a256214dc5f3fb144f1d828634553742c2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744089"
---
# <a name="operator-overloading-c-reference"></a>Surcharge d’opérateur (référence C#)

Un type défini par l’utilisateur peut surcharger un opérateur C# prédéfini. Autrement dit, un type peut fournir l’implémentation personnalisée d’une opération quand l’un des opérandes (ou les deux) sont de ce type. La section [Opérateurs surchargeables](#overloadable-operators) indique les opérateurs C# qui peuvent être surchargés.

Utilisez le mot clé `operator` pour déclarer un opérateur. Une déclaration d’opérateur doit respecter les règles suivantes :

- Elle contient un modificateur `public` et un modificateur `static`.
- Un opérateur unaire accepte un paramètre. Un opérateur binaire accepte deux paramètres. Dans chaque cas, au moins un paramètre doit avoir le type `T` ou `T?`, où `T` est le type qui contient la déclaration d’opérateur.

L’exemple suivant définit une structure simplifiée pour représenter un nombre rationnel. La structure surcharge certains des [opérateurs arithmétiques](arithmetic-operators.md) :

[!code-csharp[fraction example](~/samples/csharp/language-reference/operators/OperatorOverloading.cs)]

Vous pouvez étendre l’exemple précédent en définissant une conversion implicite en passant de `int` à `Fraction`. Les opérateurs surchargés devraient alors prendre en charge les arguments de ces deux types. Autrement dit, il deviendrait possible d’ajouter un entier à une fraction et d’obtenir une fraction en conséquence.

Vous utilisez également le mot clé `operator` pour définir une conversion de type personnalisée. Pour plus d’informations, consultez [Opérateurs de conversion définie par l’utilisateur](user-defined-conversion-operators.md).

## <a name="overloadable-operators"></a>Opérateurs surchargeables

Le tableau suivant fournit des informations sur la possibilité de surcharge des opérateurs C# :

| Opérateurs | Possibilité de surcharge |
| --------- | --------------- |
|[+](arithmetic-operators.md#unary-plus-and-minus-operators), [-](arithmetic-operators.md#unary-plus-and-minus-operators), [!](boolean-logical-operators.md#logical-negation-operator-), [~](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](arithmetic-operators.md#increment-operator-), [--](arithmetic-operators.md#decrement-operator---), [true](true-false-operators.md), [false](true-false-operators.md)|Ces opérateurs unaires peuvent être surchargés.|
|[+](addition-operator.md), [-](subtraction-operator.md), [\*](arithmetic-operators.md#multiplication-operator-), [/](arithmetic-operators.md#division-operator-), [%](arithmetic-operators.md#remainder-operator-), [&](boolean-logical-operators.md#logical-and-operator-), [&#124;](boolean-logical-operators.md#logical-or-operator-), [^](boolean-logical-operators.md#logical-exclusive-or-operator-), [\<\<](bitwise-and-shift-operators.md#left-shift-operator-), [>>](bitwise-and-shift-operators.md#right-shift-operator-), [==](equality-operators.md#equality-operator-), [!=](equality-operators.md#inequality-operator-), [\<](comparison-operators.md#less-than-operator-), [>](comparison-operators.md#greater-than-operator-), [\<=](comparison-operators.md#less-than-or-equal-operator-), [>=](comparison-operators.md#greater-than-or-equal-operator-)|Ces opérateurs binaires peuvent être surchargés. Certains opérateurs doivent être surchargés par paires. Pour plus d’informations, consultez la remarque qui suit ce tableau.|
|[&&](boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;](boolean-logical-operators.md#conditional-logical-or-operator-)|Les opérateurs logiques conditionnels ne peuvent pas être surchargés. Toutefois, si un type avec les [opérateurs `true` et `false`](true-false-operators.md) surchargés surcharge également l’opérateur `&` ou <code>&#124;</code> d’une certaine manière, l’opérateur `&&` ou <code>&#124;&#124;</code> peut être évalué respectivement pour les opérandes de ce type. Pour plus d’informations, consultez la section [Opérateurs logiques conditionnels définis par l’utilisateur](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).|
|[&#91;&#93;](member-access-operators.md#indexer-operator-)|L’accès à un élément n’est pas considéré comme un opérateur surchargeable, mais vous pouvez définir un [indexeur](../../programming-guide/indexers/index.md).|
|[(T)x](type-testing-and-conversion-operators.md#cast-operator-)|L’opérateur de cast ne peut pas être surchargé, mais vous pouvez définir de nouveaux opérateurs de conversion. Pour plus d’informations, consultez [Opérateurs de conversion définie par l’utilisateur](user-defined-conversion-operators.md).|
|[+=](arithmetic-operators.md#compound-assignment), [-=](arithmetic-operators.md#compound-assignment), [\*=](arithmetic-operators.md#compound-assignment), [/=](arithmetic-operators.md#compound-assignment), [%=](arithmetic-operators.md#compound-assignment), [&=](boolean-logical-operators.md#compound-assignment), [&#124;=](boolean-logical-operators.md#compound-assignment), [^=](boolean-logical-operators.md#compound-assignment), [\<\<=](bitwise-and-shift-operators.md#compound-assignment), [>>=](bitwise-and-shift-operators.md#compound-assignment)|Les opérateurs d’assignation composée ne peuvent pas être surchargés explicitement. Toutefois, quand vous surchargez un opérateur binaire, l’opérateur d’assignation composée correspondant, le cas échéant, est aussi implicitement surchargé. Par exemple, `+=` est évalué à l’aide de l’opérateur `+`, qui peut être surchargé.|
|[=](assignment-operator.md), [.](member-access-operators.md#member-access-operator-), [?:](conditional-operator.md), [??](null-coalescing-operator.md), [->](pointer-related-operators.md#pointer-member-access-operator--), [=>](lambda-operator.md), [f(x)](member-access-operators.md#invocation-operator-), [as](type-testing-and-conversion-operators.md#as-operator), [checked](../keywords/checked.md), [unchecked](../keywords/unchecked.md), [default](../../programming-guide/statements-expressions-operators/default-value-expressions.md), [delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md), [is](type-testing-and-conversion-operators.md#is-operator), [nameof](../keywords/nameof.md), [new](new-operator.md), [sizeof](../keywords/sizeof.md), [typeof](type-testing-and-conversion-operators.md#typeof-operator)|Ces opérateurs ne peuvent pas être surchargés.|

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
- Article [Why are overloaded operators always static in C#?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
