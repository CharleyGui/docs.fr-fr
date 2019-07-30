---
title: Propriétés indexées
description: En savoir plus sur les propriétés F#indexées dans, qui permettent un accès de type tableau aux données ordonnées.
ms.date: 10/17/2018
ms.openlocfilehash: 379417e31b8e178d8c939e5b23dc144bfb17e562
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627559"
---
# <a name="indexed-properties"></a>Propriétés indexées

Lors de la définition d’une classe qui soustrait des données ordonnées, il peut parfois être utile de fournir un accès indexé à ces données sans exposer l’implémentation sous-jacente. Cette opération est effectuée avec `Item` le membre.

## <a name="syntax"></a>Syntaxe

```fsharp
// Indexed property that can be read and written to
member self-identifier.Item
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property can only be read
member self-identifier.Item
    with get(index-values) =
        get-member-body

// Indexed property that can only be set
member self-identifier.Item
    with set index-values values-to-set =
        set-member-body
```

## <a name="remarks"></a>Notes

Les formes de la syntaxe précédente montrent comment définir des propriétés indexées qui ont à la `get` fois une `set` méthode et une méthode `get` , une méthode uniquement ou une `set` méthode uniquement. Vous pouvez également combiner la syntaxe indiquée pour obtenir uniquement et la syntaxe indiquée pour Set only, et produire une propriété qui a à la fois la valeur obtenir et définir. Ce dernier formulaire vous permet de placer des modificateurs et des attributs d’accessibilité différents sur les méthodes d’extraction et de définition.

En utilisant le nom `Item`, le compilateur traite la propriété comme une propriété indexée par défaut. Une *propriété indexée par défaut* est une propriété à laquelle vous pouvez accéder à l’aide d’une syntaxe de type tableau sur l’instance d’objet. Par exemple, si `o` est un objet du type qui définit cette propriété, la syntaxe `o.[index]` est utilisée pour accéder à la propriété.

La syntaxe permettant d’accéder à une propriété indexée non définie par défaut consiste à fournir le nom de la propriété et l’index entre parenthèses, tout comme un membre normal. Par exemple, si la propriété sur `o` est appelée `Ordinal`, vous écrivez `o.Ordinal(index)` pour y accéder.

Quel que soit le formulaire que vous utilisez, vous devez toujours utiliser le formulaire curryfiée pour la méthode Set sur une propriété indexée. Pour plus d’informations sur les fonctions curryfiés, consultez [fonctions](../functions/index.md).

## <a name="example"></a>Exemple

L’exemple de code suivant illustre la définition et l’utilisation de propriétés indexées par défaut et non définies par défaut qui ont des méthodes d’extraction et de définition.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>Sortie

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-values"></a>Propriétés indexées avec plusieurs valeurs d’index

Les propriétés indexées peuvent avoir plusieurs valeurs d’index. Dans ce cas, les valeurs sont séparées par des virgules lorsque la propriété est utilisée. La méthode Set dans une telle propriété doit avoir deux arguments curryfiés, le premier étant un tuple contenant les clés et le second est la valeur à définir.

Le code suivant illustre l’utilisation d’une propriété indexée avec plusieurs valeurs d’index.

```fsharp
open System.Collections.Generic

/// Basic implementation of a sparse matrix based on a dictionary
type SparseMatrix() =
    let table = new Dictionary<(int * int), float>()
    member __.Item
        // Because the key is comprised of two values, 'get' has two index values
        with get(key1, key2) = table.[(key1, key2)]

        // 'set' has two index values and a new value to place in the key's position
        and set (key1, key2) value = table.[(key1, key2)] <- value

let sm = new SparseMatrix()
for i in 1..1000 do
    sm.[i, i] <- float i * float i
```

## <a name="see-also"></a>Voir aussi

- [Membres](index.md)
