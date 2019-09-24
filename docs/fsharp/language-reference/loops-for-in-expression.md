---
title: 'Boucles : expression for...in'
description: Voir comment le F# ... dans, la construction de bouclage d’expression est utilisée pour itérer au sein des correspondances d’un modèle dans une collection énumérable.
ms.date: 05/16/2016
ms.openlocfilehash: 5a2ca59ca4199ece5d78010ff780e86ae2b25181
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216446"
---
# <a name="loops-forin-expression"></a>Boucles : expression for...in

Cette construction de bouclage est utilisée pour itérer au sein des correspondances d’un modèle dans une collection énumérable, telle qu’une expression de plage, une séquence, une liste, un tableau ou une autre construction qui prend en charge l’énumération.

## <a name="syntax"></a>Syntaxe

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a>Notes

L' `for...in` expression peut être comparée à `for each` l’instruction dans d’autres langages .net, car elle est utilisée pour effectuer une boucle sur les valeurs dans une collection énumérable. Toutefois, `for...in` prend également en charge les critères spéciaux sur la collection au lieu d’une itération sur l’ensemble de la collection.

L’expression énumérable peut être spécifiée en tant que collection énumérable ou, `..` à l’aide de l’opérateur, en tant que plage sur un type intégral. Les collections énumérables incluent des listes, des séquences, des tableaux, des ensembles, des mappages, etc. Tout type qui implémente `System.Collections.IEnumerable` peut être utilisé.

Lorsque vous exprimez une plage à `..` l’aide de l’opérateur, vous pouvez utiliser la syntaxe suivante.

*Démarrer* .. *terme*

Vous pouvez également utiliser une version qui comprend un incrément appelé *Skip*, comme dans le code suivant.

*Démarrer* .. *Ignorer* .. *terme*

Lorsque vous utilisez des plages intégrales et une variable de compteur simple en tant que modèle, le comportement standard consiste à incrémenter la variable de compteur de 1 à chaque itération, mais si la plage contient une valeur d’omission, le compteur est incrémenté par la valeur de saut.

Les valeurs correspondantes dans le modèle peuvent également être utilisées dans l’expression de corps.

Les exemples de code suivants illustrent l’utilisation `for...in` de l’expression.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

La sortie est la suivante.

```console
1
5
100
450
788
```

L’exemple suivant montre comment effectuer une boucle sur une séquence et comment utiliser un modèle de tuple à la place d’une variable simple.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

La sortie est la suivante.

```console
1 squared is 1
2 squared is 4
3 squared is 9
4 squared is 16
5 squared is 25
6 squared is 36
7 squared is 49
8 squared is 64
9 squared is 81
10 squared is 100
```

L’exemple suivant montre comment effectuer une boucle sur une plage d’entiers simple.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

La sortie de function1 est la suivante.

```console
1 2 3 4 5 6 7 8 9 10
```

L’exemple suivant montre comment effectuer une boucle sur une plage avec un saut de 2, qui comprend tous les autres éléments de la plage.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

La sortie de `function2` est la suivante.

```console
1 3 5 7 9
```

L’exemple suivant montre comment utiliser une plage de caractères.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

La sortie de `function3` est la suivante.

```console
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

L’exemple suivant montre comment utiliser une valeur Skip négative pour une itération inverse.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

La sortie de `function4` est la suivante.

```console
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

Le début et la fin de la plage peuvent également être des expressions, telles que des fonctions, comme dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

La sortie de `function5` avec cette entrée est la suivante.

```console
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

L’exemple suivant illustre l’utilisation d’un caractère générique (\_) lorsque l’élément n’est pas nécessaire dans la boucle.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

La sortie est la suivante.

```console
Number of elements in list1: 5
```

`Note`Vous pouvez utiliser `for...in` dans les expressions de séquence et d’autres expressions de calcul, auquel cas une version personnalisée `for...in` de l’expression est utilisée. Pour plus d’informations, consultez [séquences](sequences.md), [flux de travail asynchrones](asynchronous-workflows.md) et [expressions de calcul](computation-expressions.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
- [Boucles `for...to`Formule](loops-for-to-expression.md)
- [Boucles `while...do`Formule](loops-while-do-expression.md)
