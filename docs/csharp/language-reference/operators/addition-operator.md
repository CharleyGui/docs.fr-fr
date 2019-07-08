---
title: + et +=, opérateurs - Référence C#
ms.custom: seodec18
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
ms.openlocfilehash: 41355dbadd566648b45d825cdd6515bfc6d411aa
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610037"
---
# <a name="-and--operators-c-reference"></a>+ et +=, opérateurs (référence C#)

L’opérateur `+` est pris en charge par les types numériques intégrés, le type [chaîne](../keywords/string.md) et les types [délégués](../keywords/delegate.md).

Pour plus d’informations sur l’opérateur arithmétique `+`, consultez les sections [Opérateurs plus et moins unaires](arithmetic-operators.md#unary-plus-and-minus-operators) et [Opérateur d’addition +](arithmetic-operators.md#addition-operator-) de l’article [Opérateurs arithmétiques](arithmetic-operators.md).

## <a name="string-concatenation"></a>Concaténation de chaînes

Quand les deux opérandes ou l’un d’entre eux sont de [type chaîne](../keywords/string.md), l’opérateur `+` concatène les représentations sous forme de chaîne de ses opérandes :

[!code-csharp-interactive[string concatenation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddStrings)]

À partir de C# 6, l’[interpolation de chaîne](../tokens/interpolated.md) fournit un moyen plus pratique de mettre en format les chaînes :

[!code-csharp-interactive[string interpolation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>Combinaison de délégués

Pour les opérandes du même type [délégué](../keywords/delegate.md), l’opérateur `+` retourne une nouvelle instance de délégué qui, lorsqu’elle est appelée, appelle l’opérande de partie gauche, puis l’opérande de partie droite. Si un des opérandes est `null`, l’opérateur `+` retourne la valeur de l’autre opérande (qui peut également être `null`). L’exemple suivant montre comment les délégués peuvent être combinés avec l’opérateur `+` :

[!code-csharp-interactive[delegate combination](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddDelegates)]

Pour effectuer la suppression de délégué, utilisez l’[opérateur `-`](subtraction-operator.md#delegate-removal).

Pour plus d'informations sur les types de délégués, consultez [Délégués](../../programming-guide/delegates/index.md).

## <a name="addition-assignment-operator-"></a>Opérateur d’assignation d’addition +=

Expression utilisant l’opérateur `+=`, par exemple

```csharp
x += y
```

est équivalent à

```csharp
x = x + y
```

sauf que `x` n’est évalué qu’une seule fois.
  
L’exemple suivant illustre l’utilisation de l’opérateur `+=` :

[!code-csharp-interactive[+= examples](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddAndAssign)]

Vous utilisez également l’opérateur `+=` pour spécifier une méthode de gestionnaire d’événements lorsque vous vous abonnez à un [événement](../keywords/event.md). Pour plus d’informations, consultez [Guide pratique pour s’abonner et annuler l’abonnement à des événements](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Un type défini par l’utilisateur peut [surcharger](operator-overloading.md) l’opérateur `+`. Quand un opérateur binaire `+` est surchargé, l’opérateur `+=` est aussi implicitement surchargé. Un type défini par l’utilisateur ne peut pas surcharger explicitement l’opérateur `+=`.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections [Opérateur unaire plus](~/_csharplang/spec/expressions.md#unary-plus-operator) et [Opérateur d’addition](~/_csharplang/spec/expressions.md#addition-operator) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- [Interpolation de chaîne](../tokens/interpolated.md)
- [Guide pratique pour concaténer plusieurs chaînes](../../how-to/concatenate-multiple-strings.md)
- [Délégués](../../programming-guide/delegates/index.md)
- [Événements](../../programming-guide/events/index.md)
- [Opérateurs arithmétiques](arithmetic-operators.md)
- [- et -=, opérateurs](subtraction-operator.md)
