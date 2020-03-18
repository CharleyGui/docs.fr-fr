---
title: + et +=, opérateurs - Référence C#
ms.date: 05/24/2019
f1_keywords:
- +_CSharpKeyword
- +=_CSharpKeyword
helpviewer_keywords:
- addition operator [C#]
- concatenation operator [C#]
- delegate combination [C#]
- + operator [C#]
- addition assignment operator [C#]
- event subscription [C#]
- += operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: cafd07f4b4aefdcc4b43750d61c155fe3d65aa46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399300"
---
# <a name="-and--operators-c-reference"></a>+ et +=, opérateurs (référence C#)

Les `+` `+=` opérateurs et les opérateurs sont pris en charge par les types [numériques intégrés](../builtin-types/integral-numeric-types.md) et [flottants,](../builtin-types/floating-point-numeric-types.md) le type [de chaîne](../builtin-types/reference-types.md#the-string-type) et les types [de délégués.](../builtin-types/reference-types.md#the-delegate-type)

Pour plus d’informations sur l’opérateur arithmétique `+`, consultez les sections [Opérateurs plus et moins unaires](arithmetic-operators.md#unary-plus-and-minus-operators) et [Opérateur d’addition +](arithmetic-operators.md#addition-operator-) de l’article [Opérateurs arithmétiques](arithmetic-operators.md).

## <a name="string-concatenation"></a>Concaténation de chaînes

Quand les deux opérandes ou l’un d’entre eux sont de [type chaîne](../builtin-types/reference-types.md#the-string-type), l’opérateur `+` concatène les représentations sous forme de chaîne de ses opérandes :

[!code-csharp-interactive[string concatenation](snippets/AdditionOperator.cs#AddStrings)]

En commençant par le C 6, [l’interpolation](../tokens/interpolated.md) des cordes offre un moyen plus pratique de formater les chaînes :

[!code-csharp-interactive[string interpolation](snippets/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>Combinaison de délégués

Pour les opérandes du même type [délégué](../builtin-types/reference-types.md#the-delegate-type), l’opérateur `+` retourne une nouvelle instance de délégué qui, lorsqu’elle est appelée, appelle l’opérande de partie gauche, puis l’opérande de partie droite. Si un des opérandes est `null`, l’opérateur `+` retourne la valeur de l’autre opérande (qui peut également être `null`). L’exemple suivant montre comment les délégués peuvent être combinés avec l’opérateur `+` :

[!code-csharp-interactive[delegate combination](snippets/AdditionOperator.cs#AddDelegates)]

Pour effectuer le retrait des délégués, utilisez [ `-` l’opérateur](subtraction-operator.md#delegate-removal).

Pour plus d'informations sur les types de délégués, consultez [Délégués](../../programming-guide/delegates/index.md).

## <a name="addition-assignment-operator-"></a>Opérateur d’assignation d’addition +=

Expression utilisant l’opérateur `+=`, par exemple

```csharp
x += y
```

équivaut à :

```csharp
x = x + y
```

sauf que `x` n’est évalué qu’une seule fois.

L’exemple suivant illustre l’utilisation de l’opérateur `+=` :

[!code-csharp-interactive[+= examples](snippets/AdditionOperator.cs#AddAndAssign)]

Vous utilisez également l’opérateur `+=` pour spécifier une méthode de gestionnaire d’événements lorsque vous vous abonnez à un [événement](../keywords/event.md). Pour plus d’informations, consultez [Guide pratique pour s’abonner et annuler l’abonnement à des événements](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Un type défini par l’utilisateur peut [surcharger](operator-overloading.md) l’opérateur `+`. Quand un opérateur binaire `+` est surchargé, l’opérateur `+=` est aussi implicitement surchargé. Un type défini par l’utilisateur ne peut pas surcharger explicitement l’opérateur `+=`.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections [Opérateur unaire plus](~/_csharplang/spec/expressions.md#unary-plus-operator) et [Opérateur d’addition](~/_csharplang/spec/expressions.md#addition-operator) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Opérateurs CMD](index.md)
- [Comment concatenate plusieurs cordes](../../how-to/concatenate-multiple-strings.md)
- [Événements](../../programming-guide/events/index.md)
- [Opérateurs d’arithmétique](arithmetic-operators.md)
- [- et -- opérateurs](subtraction-operator.md)
