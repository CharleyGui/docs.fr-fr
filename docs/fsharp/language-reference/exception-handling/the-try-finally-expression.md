---
title: 'Exceptions : try...finally (expression)'
description: Découvrez comment les F# ... Enfin, l’expression vous permet d’exécuter le code de nettoyage même si un bloc de code lève une exception.
ms.date: 05/16/2016
ms.openlocfilehash: 03fbda1ef5d55560232f0217f603fc04c0af0eb4
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630276"
---
# <a name="exceptions-the-tryfinally-expression"></a>Exceptions : try...finally (expression)

L' `try...finally` expression vous permet d’exécuter le code de nettoyage même si un bloc de code lève une exception.

## <a name="syntax"></a>Syntaxe

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a>Notes

L' `try...finally` expression peut être utilisée pour exécuter le code dans *Expression2* dans la syntaxe précédente, qu’une exception soit générée ou non lors de l’exécution de *expression1*.

Le type de *Expression2* ne contribue pas à la valeur de l’expression entière; le type retourné lorsqu’une exception ne se produit pas est la dernière valeur dans *expression1*. Lorsqu’une exception se produit, aucune valeur n’est retournée et le déroulement du contrôle est transféré vers le gestionnaire d’exceptions correspondant suivant, en haut de la pile des appels. Si aucun gestionnaire d’exceptions n’est trouvé, le programme se termine. Avant que le code d’un gestionnaire correspondant soit exécuté ou que le programme se termine, le `finally` code de la branche est exécuté.

Le code suivant illustre l’utilisation de l' `try...finally` expression.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

La sortie de la console est la suivante.

```
Closing stream
Exception handled.
```

Comme vous pouvez le voir dans la sortie, le flux a été fermé avant le traitement de l’exception externe, `test.txt` et le fichier `test1`contient le texte, ce qui indique que les mémoires tampons ont été vidées et écrites sur le disque, même si l’exception a été transférée contrôle au gestionnaire d’exceptions externe.

Notez que la `try...with` construction est une construction distincte de la `try...finally` construction. Par conséquent, si votre code nécessite à `with` la fois un `finally` bloc et un bloc, vous devez imbriquer les deux constructions, comme dans l’exemple de code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

Dans le contexte des expressions de calcul, y compris les expressions de séquence et les flux de travail asynchrones, **essayez... Enfin** , les expressions peuvent avoir une implémentation personnalisée. Pour plus d’informations, consultez [expressions de calcul](../computation-expressions.md).

## <a name="see-also"></a>Voir aussi

- [Gestion des exceptions](index.md)
- [Exceptions : L' `try...with` expression](the-try-with-expression.md)
