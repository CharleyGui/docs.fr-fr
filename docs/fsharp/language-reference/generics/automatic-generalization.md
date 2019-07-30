---
title: Généralisation automatique
description: Découvrez comment F# généralise automatiquement les arguments et les types de fonctions afin qu’ils fonctionnent avec plusieurs types dans la mesure du possible.
ms.date: 05/16/2016
ms.openlocfilehash: 501749a190d9770cbcd9848e3d528cba32fe6762
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630625"
---
# <a name="automatic-generalization"></a>Généralisation automatique

F#utilise l’inférence de type pour évaluer les types de fonctions et d’expressions. Cette rubrique décrit comment F# généralise automatiquement les arguments et les types de fonctions afin qu’ils fonctionnent avec plusieurs types lorsque cela est possible.

## <a name="automatic-generalization"></a>Généralisation automatique

Lorsqu' F# il exécute l’inférence de type sur une fonction, le compilateur détermine si un paramètre donné peut être générique. Le compilateur examine chaque paramètre et détermine si la fonction a une dépendance vis-à-vis du type spécifique de ce paramètre. Si ce n’est pas le cas, le type est déduit comme étant générique.

L’exemple de code suivant illustre une fonction que le compilateur déduit comme étant générique.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

Le type est déduit comme étant `'a -> 'a -> 'a`.

Le type indique qu’il s’agit d’une fonction qui accepte deux arguments du même type inconnu et retourne une valeur du même type. L’une des raisons pour lesquelles la fonction Previous peut être générique est que l’opérateur «supérieur à`>`» () est lui-même générique. L’opérateur «supérieur à» possède la `'a -> 'a -> bool`signature. Les opérateurs ne sont pas tous génériques, et si le code d’une fonction utilise un type de paramètre avec une fonction ou un opérateur non générique, ce type de paramètre ne peut pas être généralisé.

Étant `max` donné que est générique, il peut être utilisé avec des `int`types `float`tels que,, etc., comme indiqué dans les exemples suivants.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

Toutefois, les deux arguments doivent être du même type. La signature est `'a -> 'a -> 'a`, et `'a -> 'b -> 'a`non. Par conséquent, le code suivant génère une erreur, car les types ne correspondent pas.

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

La `max` fonction fonctionne également avec tout type qui prend en charge l’opérateur supérieur à. Par conséquent, vous pouvez également l’utiliser sur une chaîne, comme illustré dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a>Restriction de valeur

Le compilateur effectue la généralisation automatique uniquement sur les définitions de fonctions complètes qui ont des arguments explicites, et sur les valeurs immuables simples.

Cela signifie que le compilateur émet une erreur si vous essayez de compiler du code qui n’est pas suffisamment restreint pour être un type spécifique, mais qui n’est pas généralisable. Le message d’erreur de ce problème fait référence à cette restriction sur la généralisation automatique pour les valeurs comme *restriction de valeur*.

En général, l’erreur de restriction de valeur se produit lorsque vous souhaitez qu’une construction soit générique, mais que le compilateur ne dispose pas d’informations suffisantes pour la généraliser, ou lorsque vous omettez involontairement des informations de type suffisantes dans une construction non générique. La solution à l’erreur de restriction de valeur consiste à fournir des informations plus explicites pour limiter plus complètement le problème d’inférence de type, de l’une des manières suivantes:

- Contraindre un type à être non générique en ajoutant une annotation de type explicite à une valeur ou un paramètre.

- Si le problème est lié à l’utilisation d’une construction non généralisable pour définir une fonction générique, telle qu’une composition de fonction ou des arguments de fonction curryfiés appliqués de manière incomplète, essayez de réécrire la fonction comme une définition de fonction ordinaire.

- Si le problème est une expression trop complexe pour être généralisée, transformez-la en fonction en ajoutant un paramètre supplémentaire inutilisé.

- Ajoutez des paramètres de type générique explicites. Cette option est rarement utilisée.

- Les exemples de code suivants illustrent chacun de ces scénarios.

Cas 1: Expression trop complexe. Dans cet exemple, la liste `counter` est destinée à être `int option ref`, mais elle n’est pas définie comme une valeur immuable simple.

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

Cas 2: Utilisation d’une construction non généralisable pour définir une fonction générique. Dans cet exemple, la construction est non généralisable, car elle implique une application partielle des arguments de fonction.

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

Cas 3: Ajout d’un paramètre supplémentaire inutilisé. Étant donné que cette expression n’est pas assez simple pour la généralisation, le compilateur émet l’erreur de restriction de valeur.

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

Cas 4: Ajout de paramètres de type.

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

Dans le dernier cas, la valeur devient une fonction de type, qui peut être utilisée pour créer des valeurs de nombreux types différents, par exemple, comme suit:

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a>Voir aussi

- [Inférence de type](../type-inference.md)
- [Génériques](index.md)
- [Paramètres de type résolus statiquement](statically-resolved-type-parameters.md)
- [Contraintes](constraints.md)
