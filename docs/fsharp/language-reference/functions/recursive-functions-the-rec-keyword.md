---
title: 'Fonctions récursives : mot clé rec'
description: "Découvrez comment le mot clé F # 'Rec’est utilisé avec le mot clé’Let’pour définir une fonction récursive."
ms.date: 08/12/2020
ms.openlocfilehash: 1ab00ff9400129e531fd7320861b3d9625cad08c
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91438071"
---
# <a name="recursive-functions-the-rec-keyword"></a>Fonctions récursives : mot clé rec

Le `rec` mot clé est utilisé conjointement avec le `let` mot clé pour définir une fonction récursive.

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

Fonctions récursives : les fonctions qui s’appellent elles-mêmes sont identifiées explicitement dans le langage F # avec le `rec` mot clé. Le `rec` mot clé rend le nom de la `let` liaison disponible dans son corps.

L’exemple suivant montre une fonction récursive qui calcule le *n*<sup>ième</sup> nombre de Fibonacci à l’aide de la définition mathématique.

```fsharp
let rec fib n =
    match n with
    | 0 | 1 -> 1
    | n -> fib (n-1) + fib (n-2)
```

> [!NOTE]
> Dans la pratique, le code comme l’exemple précédent n’est pas idéal, car il unecessarily recalcule les valeurs qui ont déjà été calculées. Cela est dû au fait qu’elle n’est pas une fin récursive, ce qui est expliqué plus loin dans cet article.

Les méthodes sont implicitement récursives dans le type dans lequel elles sont définies, ce qui signifie qu’il n’est pas nécessaire d’ajouter le `rec` mot clé. Par exemple :

```fsharp
type MyClass() =
    member this.Fib(n) =
        match n with
        | 0 | 1 -> 1
        | n -> this.Fib(n-1) + this.Fib(n-2)
```

Toutefois, les liaisons Let dans les classes ne sont pas implicitement récursives. Toutes les `let` fonctions liées nécessitent le `rec` mot clé.

## <a name="tail-recursion"></a>Récurrence de la fin

Pour certaines fonctions récursives, il est nécessaire de refactoriser une définition plus « pure » vers une définition qui est une [fin récursive](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion). Cela évite les recalculs inutiles. Par exemple, le générateur de nombres Fibonacci précédent peut être réécrit comme suit :

```fsharp
let fib n =
    let rec loop acc1 acc2 n =
        match n with
        | 0 -> acc1
        | 1 -> acc2
        | _ ->
            loop acc2 (acc1 + acc2) (n - 1)
    loop 0 1 n
```

Il s’agit d’une implémentation plus complexe. La génération d’un nombre de Fibonacci est un bon exemple d’algorithme naïve qui est mathématiquement pur, mais inefficace dans la pratique. Plusieurs aspects le rendent efficace en F # tout en restant défini de manière récursive :

* Une fonction interne récursive nommée `loop` , qui est un modèle F # idiomatique.
* Deux paramètres d’accumulation, qui réussissent à accumuler des valeurs à des appels récursifs.
* Contrôle de la valeur de `n` pour retourner un cumul spécifique.

Si cet exemple a été écrit de façon itérative avec une boucle, le code doit ressembler à deux valeurs différentes qui accumulent des nombres jusqu’à ce qu’une condition particulière soit remplie.

La raison pour laquelle il s’agit d’une fin récursive est que l’appel récursif n’a pas besoin d’enregistrer les valeurs sur la pile des appels. Toutes les valeurs intermédiaires calculées sont accumulées via des entrées dans la fonction interne. Cela permet également au compilateur F # d’optimiser le code pour qu’il soit aussi rapide que si vous aviez écrit des éléments tels qu’une `while` boucle.

Il est courant d’écrire du code F # qui traite de manière récursive un événement à l’aide d’une fonction interne et externe, comme le montre l’exemple précédent. La fonction interne utilise la récursivité de fin, tandis que la fonction externe a une meilleure interface pour les appelants.

## <a name="mutually-recursive-functions"></a>Fonctions mutuellement récursives

Parfois, les fonctions sont *mutuellement récursives*, ce qui signifie que les appels forment un cercle, où une fonction appelle une autre qui, à son tour, appelle la première, avec un nombre quelconque d’appels entre les deux. Vous devez définir de telles fonctions dans une `let` liaison, en utilisant le `and` mot clé pour les lier ensemble.

L’exemple suivant montre deux fonctions mutuellement récursives.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="recursive-values"></a>Valeurs récursives

Vous pouvez également définir une `let` valeur liée à une valeur récursive. Cela est parfois fait pour la journalisation. Avec F # 5 et la `nameof` fonction, vous pouvez effectuer cette opération :

```fsharp
let rec nameDoubles = nameof nameDoubles + nameof nameDoubles
```

## <a name="see-also"></a>Voir aussi

- [Fonctions](index.md)
