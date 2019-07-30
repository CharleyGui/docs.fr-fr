---
title: 'Fonctions récursives: Mot clé Rec'
description: Découvrez comment le F# mot clé’Rec’est utilisé avec le mot clé’Let’pour définir une fonction récursive.
ms.date: 05/16/2016
ms.openlocfilehash: 7edaa7206b2109c7b1a405624b9b2330968f9c52
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630653"
---
# <a name="recursive-functions-the-rec-keyword"></a>Fonctions récursives: Mot clé Rec

Le `rec` mot clé est utilisé conjointement avec `let` le mot clé pour définir une fonction récursive.

## <a name="syntax"></a>Syntaxe

```fsharp
// Recursive function:
let rec function-nameparameter-list =
function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
function1-body
and function2-nameparameter-list =
function2-body
...
```

## <a name="remarks"></a>Notes

Les fonctions récursives, les fonctions qui s’appellent, sont identifiées F# explicitement dans le langage. Cela rend l’identificateur qui est défini comme étant disponible dans l’étendue de la fonction.

Le code suivant illustre une fonction récursive qui calcule le *n*<sup>ième</sup> nombre de Fibonacci.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> Dans la pratique, le code comme celui ci-dessus est gaspillant la mémoire et le temps processeur, car il implique le recalcul des valeurs calculées précédemment.

Les méthodes sont implicitement récursives dans le type; Il n’est pas nécessaire d’ajouter `rec` le mot clé. Les liaisons Let dans les classes ne sont pas implicitement récursives.

## <a name="mutually-recursive-functions"></a>Fonctions mutuellement récursives

Parfois, lesfonctions sont mutuellement récursives, ce qui signifie que les appels forment un cercle, où une fonction appelle une autre qui, à son tour, appelle la première, avec un nombre quelconque d’appels entre les deux. Vous devez définir de telles fonctions dans une `let` liaison, en utilisant le `and` mot clé pour les lier ensemble.

L’exemple suivant montre deux fonctions mutuellement récursives.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>Voir aussi

- [Fonctions](index.md)
