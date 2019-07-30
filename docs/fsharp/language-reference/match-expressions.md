---
title: Expressions de correspondance
description: Découvrez comment l' F# expression de correspondance fournit un contrôle de branchement basé sur la comparaison d’une expression avec un ensemble de modèles.
ms.date: 04/19/2018
ms.openlocfilehash: 222cb0604300039d86ed0c80293651631d212eb6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627607"
---
# <a name="match-expressions"></a>Expressions de correspondance

L' `match` expression fournit un contrôle de branchement basé sur la comparaison d’une expression avec un ensemble de modèles.

## <a name="syntax"></a>Syntaxe

```fsharp
// Match expression.
match test-expression with
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...

// Pattern matching function.
function
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...
```

## <a name="remarks"></a>Notes

Les expressions de critères spéciaux permettent une branche complexe basée sur la comparaison d’une expression de test avec un ensemble de modèles. Dans l' `match` expression, l’expression de *test* est comparée à chaque modèle, et lorsqu’une correspondance est trouvée, l' *expression de résultat* correspondante est évaluée et la valeur résultante est retournée en tant que valeur de l’expression de correspondance.

La fonction de critères spéciaux indiquée dans la syntaxe précédente est une expression lambda dans laquelle les critères spéciaux sont exécutés immédiatement sur l’argument. La fonction de critères spéciaux indiquée dans la syntaxe précédente est équivalente à ce qui suit.

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

Pour plus d’informations sur les expressions lambda [, consultez Expressions lambda: `fun` Mot clé](./functions/lambda-expressions-the-fun-keyword.md).

L’ensemble des modèles doit couvrir toutes les correspondances possibles de la variable d’entrée. Souvent, vous utilisez le modèle de caractère`_`générique () comme dernier modèle pour faire correspondre toutes les valeurs d’entrée précédemment non appariées.

Le code suivant illustre quelques-unes des façons dont l' `match` expression est utilisée. Pour obtenir une référence et des exemples de tous les modèles possibles qui peuvent être utilisés, consultez [critères spéciaux](pattern-matching.md).

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a>Gardes sur les modèles

Vous pouvez utiliser une `when` clause pour spécifier une condition supplémentaire que la variable doit satisfaire pour correspondre à un modèle. Une telle clause est appelée un *garde*. L’expression qui suit `when` le mot clé n’est pas évaluée, sauf si une correspondance est établie avec le modèle associé à cette protection.

L’exemple suivant illustre l’utilisation d’un garde pour spécifier une plage numérique pour un modèle de variable. Notez que plusieurs conditions sont combinées à l’aide d’opérateurs booléens.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

Notez que les valeurs autres que les littéraux ne peuvent pas être utilisées dans le modèle, vous `when` devez utiliser une clause si vous devez comparer une partie de l’entrée à une valeur. Ceci est illustré dans le code suivant :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

Notez que lorsqu’un modèle d’Union est couvert par une protection, la protection s’applique à **tous** les modèles, pas seulement au dernier. Par exemple, étant donné le code suivant, la `when a > 12` protection s’applique `A a` à `B a`la fois à et à:

```fsharp
type Union =
    | A of int
    | B of int

let foo() =
    let test = A 42
    match test with
    | A a
    | B a when a > 41 -> a // the guard applies to both patterns
    | _ -> 1

foo() // returns 42
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
- [Modèles actifs](active-patterns.md)
- [Critères spéciaux](pattern-matching.md)
