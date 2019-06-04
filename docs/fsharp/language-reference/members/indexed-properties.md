---
title: Propriétés indexées
description: En savoir plus sur les propriétés indexées dans F#, qui permettent l’accès de type tableau aux données ordonnées.
ms.date: 10/17/2018
ms.openlocfilehash: 7fc8f46e029255c6ed985a43b92c8f7c2908c428
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489481"
---
# <a name="indexed-properties"></a>Propriétés indexées

Lorsque vous définissez une classe qui effectue l’abstraction sur le tri des données, il peut parfois être utile de fournir un accès indexé à ces données sans exposer l’implémentation sous-jacente. Cette opération est effectuée avec la `Item` membre.

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

Les formes de la syntaxe précédente montrent comment définir des propriétés indexées qui ont les deux un `get` et un `set` (méthode), ont un `get` méthode uniquement, ou avoir un `set` méthode uniquement. Vous pouvez également combiner les deux la syntaxe indiquée pour get uniquement et la syntaxe indiquée pour set uniquement et produire une propriété qui possède à la fois get et set. Cette dernière forme vous permet de placer des modificateurs d’accessibilité différente et des attributs sur la méthode get et de définir des méthodes.

En utilisant le nom `Item`, le compilateur traite la propriété comme une propriété indexée par défaut. Un *propriété indexée par défaut* est une propriété que vous pouvez accéder à l’aide de la syntaxe de type tableau sur l’instance d’objet. Par exemple, si `o` est un objet du type qui définit cette propriété, la syntaxe `o.[index]` est utilisé pour accéder à la propriété.

La syntaxe permettant d’accéder à une propriété indexée par défaut consiste à fournir le nom de la propriété et l’index entre parenthèses, comme un membre régulier. Par exemple, si la propriété sur `o` est appelée `Ordinal`, vous écrivez `o.Ordinal(index)` pour y accéder.

Quelle que soit la forme que vous utilisez, vous devez toujours utiliser la forme curryfiée pour la méthode set sur une propriété indexée. Pour plus d’informations sur les fonctions curryfiées, consultez [fonctions](../functions/index.md).

## <a name="example"></a>Exemple

L’exemple de code suivant illustre la définition et l’utilisation de la valeur par défaut et les propriétés indexées par défaut qui ont get et définir des méthodes.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>Sortie

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-values"></a>Propriétés indexées avec plusieurs valeurs d’index

Propriétés indexées peuvent avoir plusieurs valeurs d’index. Dans ce cas, les valeurs sont séparées par des virgules lorsque la propriété est utilisée. La méthode set dans une telle propriété doit avoir deux arguments curryfiés, le premier d'entre eux est un tuple qui contient les clés et le second est la valeur à définir.

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
