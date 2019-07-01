---
title: Opérateurs surchargeables - Guide de programmation C#
ms.custom: seodec18
ms.date: 08/27/2018
helpviewer_keywords:
- C# language, operator overloading
- operator overloading [C#]
ms.assetid: 390d9d01-79fc-40ab-9ed3-0bf448da1b6a
ms.openlocfilehash: c1f8570600d4479bcd07547ba643f2aeecaed0d3
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398018"
---
# <a name="overloadable-operators-c-programming-guide"></a>Opérateurs surchargeables (Guide de programmation C#)

Dans C#, les types définis par l’utilisateur peuvent surcharger des opérateurs en définissant des fonctions membres statiques à l’aide du mot clé [operator](../../language-reference/keywords/operator.md). Toutefois, tous les opérateurs ne peuvent pas être surchargés et d'autres présentent des restrictions, comme indiqué dans ce tableau :

| Opérateurs | Possibilité de surcharge |
| --------- | --------------- |
|[+](../../language-reference/operators/addition-operator.md), [-](../../language-reference/operators/subtraction-operator.md), [!](../../language-reference/operators/boolean-logical-operators.md#logical-negation-operator-), [~](../../language-reference/operators/bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](../../language-reference/operators/arithmetic-operators.md#increment-operator-), [--](../../language-reference/operators/arithmetic-operators.md#decrement-operator---), [true](../../language-reference/operators/true-false-operators.md), [false](../../language-reference/operators/true-false-operators.md)|Ces opérateurs unaires peuvent être surchargés.|
|[+](../../language-reference/operators/addition-operator.md), [-](../../language-reference/operators/subtraction-operator.md), [\*](../../language-reference/operators/arithmetic-operators.md#multiplication-operator-), [/](../../language-reference/operators/arithmetic-operators.md#division-operator-), [%](../../language-reference/operators/arithmetic-operators.md#remainder-operator-), [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-), [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-), [^](../../language-reference/operators/boolean-logical-operators.md#logical-exclusive-or-operator-), [\<\<](../../language-reference/operators/bitwise-and-shift-operators.md#left-shift-operator-), [>>](../../language-reference/operators/bitwise-and-shift-operators.md#right-shift-operator-)|Ces opérateurs binaires peuvent être surchargés.|
|[==](../../language-reference/operators/equality-operators.md#equality-operator-), [!=](../../language-reference/operators/equality-operators.md#inequality-operator-), [\<](../../language-reference/operators/comparison-operators.md#less-than-operator-), [>](../../language-reference/operators/comparison-operators.md#greater-than-operator-), [\<=](../../language-reference/operators/comparison-operators.md#less-than-or-equal-operator-), [>=](../../language-reference/operators/comparison-operators.md#greater-than-or-equal-operator-)|Les opérateurs de comparaison peuvent être surchargés (mais consultez la remarque qui suit ce tableau).|
|[&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-)|Les opérateurs logiques conditionnels ne peuvent pas être surchargés, mais ils sont évalués à l’aide des opérateurs surchargeables `&` et <code>&#124;</code>.|
|[&#91;&#93;](../../language-reference/operators/member-access-operators.md#indexer-operator-)|L’opérateur d’indexation de tableau ne peut pas être surchargé, mais vous pouvez définir des [indexeurs](../indexers/index.md).|
|[(T)x](../../language-reference/operators/type-testing-and-conversion-operators.md#cast-operator-)|L’opérateur de cast ne peut pas être surchargé, mais vous pouvez définir de nouveaux opérateurs de conversion (consultez [explicit](../../language-reference/keywords/explicit.md) et [implicit](../../language-reference/keywords/implicit.md)).|
|[+=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [-=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [\*=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [/=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [%=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [&=](../../language-reference/operators/boolean-logical-operators.md#compound-assignment), [&#124;=](../../language-reference/operators/boolean-logical-operators.md#compound-assignment), [^=](../../language-reference/operators/boolean-logical-operators.md#compound-assignment), [\<\<=](../../language-reference/operators/bitwise-and-shift-operators.md#compound-assignment), [>>=](../../language-reference/operators/bitwise-and-shift-operators.md#compound-assignment)|Les opérateurs d’assignation ne peuvent pas être surchargés explicitement. Toutefois, quand vous surchargez un opérateur binaire, l’opérateur d’assignation correspondant, le cas échéant, est aussi implicitement surchargé. Par exemple, `+=` est évalué à l’aide de l’opérateur `+`, qui peut être surchargé.|
|[=](../../language-reference/operators/assignment-operator.md), [.](../../language-reference/operators/member-access-operators.md#member-access-operator-), [?:](../../language-reference/operators/conditional-operator.md), [??](../../language-reference/operators/null-coalescing-operator.md), [->](../../language-reference/operators/pointer-related-operators.md#pointer-member-access-operator--), [=>](../../language-reference/operators/lambda-operator.md), [f(x)](../../language-reference/operators/member-access-operators.md#invocation-operator-), [as](../../language-reference/operators/type-testing-and-conversion-operators.md#as-operator), [checked](../../language-reference/keywords/checked.md), [unchecked](../../language-reference/keywords/unchecked.md), [default](../../programming-guide/statements-expressions-operators/default-value-expressions.md), [delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md), [is](../../language-reference/operators/type-testing-and-conversion-operators.md#is-operator), [new](../../language-reference/operators/new-operator.md), [sizeof](../../language-reference/keywords/sizeof.md), [typeof](../../language-reference/operators/type-testing-and-conversion-operators.md#typeof-operator)|Ces opérateurs ne peuvent pas être surchargés.|

> [!NOTE]
> Les opérateurs de comparaison, s'ils sont surchargés, doivent l'être par paires ; autrement dit, si `==` est surchargé, `!=` doit également l'être. L’inverse est vrai aussi, quand la surcharge de `!=` nécessite une surcharge de `==`. Il en est de même pour les opérateurs de comparaison `<` et `>`, et pour `<=` et `>=`.

Pour savoir comment surcharger un opérateur, consultez l’article sur le mot clé [operator](../../language-reference/keywords/operator.md).

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Instructions, expressions et opérateurs](index.md)
- [Opérateurs](operators.md)
- [Opérateurs C#](../../language-reference/operators/index.md)
- Article [Why are overloaded operators always static in C#?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
