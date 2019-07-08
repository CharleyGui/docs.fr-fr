---
title: '- et -=, opérateurs - Référence C#'
ms.custom: seodec18
ms.date: 05/27/2019
f1_keywords:
- -_CSharpKeyword
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction operator [C#]
- delegate removal [C#]
- '- operator [C#]'
- subtraction assignment operator [C#]
- event unsubscription [C#]
- -= operator [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: 80603107beb708e76a2c7446f300d71ede411570
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609854"
---
# <a name="--and---operators-c-reference"></a>Opérateurs - et -=, opérateurs - (référence C#)

L’opérateur `-` est pris en charge par les types numériques intégrés et les types [délégués](../keywords/delegate.md).

Pour plus d’informations sur l’opérateur arithmétique `-`, consultez les sections [Opérateurs plus et moins unaires](arithmetic-operators.md#unary-plus-and-minus-operators) et [Opérateur de soustraction -](arithmetic-operators.md#subtraction-operator--) de l’article [Opérateurs arithmétiques](arithmetic-operators.md).

## <a name="delegate-removal"></a>Suppression de délégué

Pour les opérandes du même type [délégué](../keywords/delegate.md), l’opérateur `-` retourne une instance de délégué qui est calculée comme suit :

- Si les deux opérandes ont des valeurs non Null et que la liste d’appel de l’opérande de partie droite est une sous-liste contiguë correcte de la liste d’appel de l’opérande de partie droite, le résultat de l’opération est une nouvelle liste d’appel obtenue en supprimant les entrées de l’opérande de partie droite à partir de la liste d’appel de l’opérande de gauche. Si la liste des opérandes de partie droite correspond à plusieurs sous-listes contiguës dans la liste des opérandes de partie gauche, seule la sous-liste correspondante la plus à droite est supprimée. Si la suppression aboutit à une liste vide, le résultat est `null`.

  [!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

- Si la liste d’appel de l’opérande de partie droite n’est pas une sous-liste contiguë correcte de la liste d’appel de l’opérande de partie gauche, le résultat de l’opération est l’opérande de partie gauche. Par exemple, la suppression d’un délégué qui ne fait pas partie du délégué multicast ne fait rien et génère un délégué multicast inchangé.

  [!code-csharp-interactive[delegate removal with no effect](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalNoChange)]

  L’exemple précédent montre également que durant la suppression de délégué, les instances de délégués sont comparées. Par exemple, les délégués qui sont produits à partir de l’évaluation d’[expressions lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) identiques ne sont pas égaux. Pour plus d’informations sur l’égalité des délégués, consultez la section [Opérateurs d’égalité de délégués](~/_csharplang/spec/expressions.md#delegate-equality-operators) de la [spécification du langage C#](../language-specification/index.md).

- Si l’opérande de partie gauche est `null`, le résultat de l’opération est `null`. Si l’opérande de partie droite est `null`, le résultat de l’opération est l’opérande de partie gauche.

  [!code-csharp-interactive[delegate removal and null](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalAndNull)]

Pour combiner des délégués, utilisez l’[opérateur `+`](addition-operator.md#delegate-combination).

Pour plus d'informations sur les types de délégués, consultez [Délégués](../../programming-guide/delegates/index.md).

## <a name="subtraction-assignment-operator--"></a>Opérateur d’assignation de soustraction -=

Expression utilisant l’opérateur `-=`, par exemple

```csharp
x -= y
```

est équivalent à

```csharp
x = x - y
```

sauf que `x` n’est évalué qu’une seule fois.
  
L’exemple suivant illustre l’utilisation de l’opérateur `-=` :

[!code-csharp-interactive[-= examples](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

Vous utilisez également l’opérateur `-=` pour spécifier une méthode de gestionnaire d’événements à supprimer quand vous vous désabonnez d’un [événement](../keywords/event.md). Pour plus d’informations, consultez [Guide pratique pour s’abonner et annuler l’abonnement à des événements](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Un type défini par l’utilisateur peut [surcharger](operator-overloading.md) l’opérateur `-`. Quand un opérateur binaire `-` est surchargé, l’opérateur `-=` est aussi implicitement surchargé. Un type défini par l’utilisateur ne peut pas surcharger explicitement l’opérateur `-=`.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections [Opérateur moins unaire](~/_csharplang/spec/expressions.md#unary-minus-operator) et [Opérateur de soustraction](~/_csharplang/spec/expressions.md#subtraction-operator) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- [Délégués](../../programming-guide/delegates/index.md)
- [Événements](../../programming-guide/events/index.md)
- [Opérateurs arithmétiques](arithmetic-operators.md)
- [+ et +=, opérateurs](addition-operator.md)
