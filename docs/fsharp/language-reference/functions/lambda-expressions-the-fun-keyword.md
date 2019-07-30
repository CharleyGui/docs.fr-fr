---
title: 'Expressions lambda: Mot clé fun'
description: Découvrez comment utiliser le F# mot clé «fun» pour définir une expression lambda, qui est une fonction anonyme.
ms.date: 05/16/2016
ms.openlocfilehash: 9818724686dd83a7e352fb36819289fa19b002df
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630662"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>Expressions lambda: Mot clé Fun (F#)

Le `fun` mot clé est utilisé pour définir une expression lambda, autrement dit, une fonction anonyme.

## <a name="syntax"></a>Syntaxe

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>Notes

La *liste de paramètres* se compose généralement de noms et, éventuellement, de types de paramètres. Plus généralement, la *liste de paramètres* peut être composée de n' F# importe quel modèle. Pour obtenir la liste complète des modèles possibles, consultez [critères spéciaux](../pattern-matching.md). Les listes de paramètres valides incluent les exemples suivants.

```fsharp
// Lambda expressions with parameter lists.
fun a b c -> ...
fun (a: int) b c -> ...
fun (a : int) (b : string) (c:float) -> ...

// A lambda expression with a tuple pattern.
fun (a, b) -> …

// A lambda expression with a list pattern.
fun head :: tail -> …
```

L' *expression* est le corps de la fonction, la dernière expression de qui génère une valeur de retour. Voici quelques exemples d’expressions lambda valides:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a>Utilisation d’expressions lambda

Les expressions lambda sont particulièrement utiles lorsque vous souhaitez effectuer des opérations sur une liste ou une autre collection et que vous souhaitez éviter le travail supplémentaire de définition d’une fonction. De F# nombreuses fonctions de bibliothèque acceptent des valeurs de fonction comme arguments, et il peut être particulièrement pratique d’utiliser une expression lambda dans ces cas. Le code suivant applique une expression lambda aux éléments d’une liste. Dans ce cas, la fonction anonyme ajoute 1 à chaque élément d’une liste.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a>Voir aussi

- [Fonctions](index.md)
