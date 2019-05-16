---
title: 'Fonctions récursives : Le mot clé rec'
description: Découvrez comment la F# mot clé « rec » est utilisé avec le mot clé 'let' pour définir une fonction récursive.
ms.date: 05/16/2016
ms.openlocfilehash: 86eaf1c8a5566d8b9cbc4dcb72f945e2497e5439
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645291"
---
# <a name="recursive-functions-the-rec-keyword"></a>Fonctions récursives : Le mot clé rec

Le `rec` mot clé est utilisée conjointement avec la `let` mot clé pour définir une fonction récursive.

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

Fonctions récursives, les fonctions qui appellent elles-mêmes, sont identifiées explicitement dans le F# langage. L’identificateur qui est en cours de définition sont ainsi disponibles dans la portée de la fonction.

Le code suivant illustre une fonction récursive qui calcule le *n*<sup>th</sup> nombre Fibonacci.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> Dans la pratique, code comme celui ci-dessus est inutile de mémoire et le temps processeur, car il implique le recalcul des valeurs précédemment calculées.

Les méthodes sont implicitement récursives dans le type ; Il est inutile d’ajouter le `rec` mot clé. Liaisons let dans les classes ne sont pas implicitement récursifs.

## <a name="mutually-recursive-functions"></a>Fonctions mutuellement récursives

Parfois, les fonctions sont *mutuellement récursives*, ce qui signifie que les appels forment un cercle, où une fonction appelle une autre qui à son tour appelle la première, avec n’importe quel nombre d’appels entre les deux. Vous devez définir de telles fonctions dans celui `let` à l’aide de la liaison la `and` mot clé pour les relier.

L’exemple suivant montre deux mutuellement fonctions récursives.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>Voir aussi

- [Fonctions](index.md)
