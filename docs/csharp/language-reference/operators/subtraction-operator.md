---
title: '- - et -=, opérateurs - Référence C#'
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
ms.openlocfilehash: 9f43a863de69122e251204668af2ea989fcc993c
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300091"
---
# <a name="--and---operators-c-reference"></a>- et -=, opérateurs (référence C#)

L’opérateur `-` est pris en charge par les types numériques intégrés et les types [délégués](../keywords/delegate.md).

Pour plus d’informations sur l’opérateur arithmétique `-`, consultez les sections [Opérateurs plus et moins unaires](arithmetic-operators.md#unary-plus-and-minus-operators) et [Opérateur de soustraction -](arithmetic-operators.md#subtraction-operator--) de l’article [Opérateurs arithmétiques](arithmetic-operators.md).

## <a name="delegate-removal"></a>Suppression de délégué

Pour les opérandes du même type [délégué](../keywords/delegate.md), l’opérateur `-` retourne une instance de délégué qui est calculée comme suit :

- Si les deux opérandes ont des valeurs non Null et que la liste d’appel du deuxième opérande est une sous-liste contiguë correcte de la liste d’appel du premier opérande, le résultat de l’opération est une nouvelle liste d’appel qui est obtenue en supprimant les entrées du deuxième opérande à partir de la liste d’appel du premier opérande. Si la liste du deuxième opérande correspond à plusieurs sous-listes contiguës dans la liste du premier opérande, seule la sous-liste correspondante la plus à droite est supprimée. Si la suppression aboutit à une liste vide, le résultat est `null`.
- Si la liste d’appel du second opérande n’est pas une sous-liste contiguë correcte de la liste d’appel du premier opérande, le résultat de l’opération est le premier opérande.
- Si le premier opérande a la valeur `null`, le résultat de l’opération est `null`. Si le second opérande a la valeur `null`, le résultat de l’opération est le premier opérande.

L’exemple suivant montre comment l’opération `-` effectue la suppression de délégué :

[!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

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

Un type défini par l’utilisateur peut [surcharger](../keywords/operator.md) l’opérateur `-`. Quand un opérateur binaire `-` est surchargé, l’opérateur `-=` est aussi implicitement surchargé. Un type défini par l’utilisateur ne peut pas surcharger explicitement l’opérateur `-=`.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections [Opérateur moins unaire](~/_csharplang/spec/expressions.md#unary-minus-operator) et [Opérateur de soustraction](~/_csharplang/spec/expressions.md#subtraction-operator) de la [spécification du langage C#](../language-specification/index.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Opérateurs C#](index.md)
- [Délégués](../../programming-guide/delegates/index.md)
- [Événements](../../programming-guide/events/index.md)
- [Checked et unchecked](../keywords/checked-and-unchecked.md)
- [Opérateurs arithmétiques](arithmetic-operators.md)
- [+ et +=, opérateurs](addition-operator.md)
