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
# <a name="indexed-properties"></a><span data-ttu-id="bee2a-103">Propriétés indexées</span><span class="sxs-lookup"><span data-stu-id="bee2a-103">Indexed Properties</span></span>

<span data-ttu-id="bee2a-104">Lors de la définition d’une classe qui soustrait des données ordonnées, il peut parfois être utile de fournir un accès indexé à ces données sans exposer l’implémentation sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="bee2a-104">When defining a class that abstracts over ordered data, it can sometimes be helpful to provide indexed access to that data without exposing the underlying implementation.</span></span> <span data-ttu-id="bee2a-105">Cette opération est effectuée avec `Item` le membre.</span><span class="sxs-lookup"><span data-stu-id="bee2a-105">This is done with the `Item` member.</span></span>

## <a name="syntax"></a><span data-ttu-id="bee2a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bee2a-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="bee2a-107">Notes</span><span class="sxs-lookup"><span data-stu-id="bee2a-107">Remarks</span></span>

<span data-ttu-id="bee2a-108">Les formes de la syntaxe précédente montrent comment définir des propriétés indexées qui ont à la `get` fois une `set` méthode et une méthode `get` , une méthode uniquement ou une `set` méthode uniquement.</span><span class="sxs-lookup"><span data-stu-id="bee2a-108">The forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="bee2a-109">Vous pouvez également combiner la syntaxe indiquée pour obtenir uniquement et la syntaxe indiquée pour Set only, et produire une propriété qui a à la fois la valeur obtenir et définir.</span><span class="sxs-lookup"><span data-stu-id="bee2a-109">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="bee2a-110">Ce dernier formulaire vous permet de placer des modificateurs et des attributs d’accessibilité différents sur les méthodes d’extraction et de définition.</span><span class="sxs-lookup"><span data-stu-id="bee2a-110">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="bee2a-111">En utilisant le nom `Item`, le compilateur traite la propriété comme une propriété indexée par défaut.</span><span class="sxs-lookup"><span data-stu-id="bee2a-111">By using the name `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="bee2a-112">Une *propriété indexée par défaut* est une propriété à laquelle vous pouvez accéder à l’aide d’une syntaxe de type tableau sur l’instance d’objet.</span><span class="sxs-lookup"><span data-stu-id="bee2a-112">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="bee2a-113">Par exemple, si `o` est un objet du type qui définit cette propriété, la syntaxe `o.[index]` est utilisée pour accéder à la propriété.</span><span class="sxs-lookup"><span data-stu-id="bee2a-113">For example, if `o` is an object of the type that defines this property, the syntax `o.[index]` is used to access the property.</span></span>

<span data-ttu-id="bee2a-114">La syntaxe permettant d’accéder à une propriété indexée non définie par défaut consiste à fournir le nom de la propriété et l’index entre parenthèses, tout comme un membre normal.</span><span class="sxs-lookup"><span data-stu-id="bee2a-114">The syntax for accessing a non-default indexed property is to provide the name of the property and the index in parentheses, just like a regular member.</span></span> <span data-ttu-id="bee2a-115">Par exemple, si la propriété sur `o` est appelée `Ordinal`, vous écrivez `o.Ordinal(index)` pour y accéder.</span><span class="sxs-lookup"><span data-stu-id="bee2a-115">For example, if the property on `o` is called `Ordinal`, you write `o.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="bee2a-116">Quel que soit le formulaire que vous utilisez, vous devez toujours utiliser le formulaire curryfiée pour la méthode Set sur une propriété indexée.</span><span class="sxs-lookup"><span data-stu-id="bee2a-116">Regardless of which form you use, you should always use the curried form for the set method on an indexed property.</span></span> <span data-ttu-id="bee2a-117">Pour plus d’informations sur les fonctions curryfiés, consultez [fonctions](../functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="bee2a-117">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="bee2a-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="bee2a-118">Example</span></span>

<span data-ttu-id="bee2a-119">L’exemple de code suivant illustre la définition et l’utilisation de propriétés indexées par défaut et non définies par défaut qui ont des méthodes d’extraction et de définition.</span><span class="sxs-lookup"><span data-stu-id="bee2a-119">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="bee2a-120">Sortie</span><span class="sxs-lookup"><span data-stu-id="bee2a-120">Output</span></span>

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-values"></a><span data-ttu-id="bee2a-121">Propriétés indexées avec plusieurs valeurs d’index</span><span class="sxs-lookup"><span data-stu-id="bee2a-121">Indexed Properties with multiple index values</span></span>

<span data-ttu-id="bee2a-122">Les propriétés indexées peuvent avoir plusieurs valeurs d’index.</span><span class="sxs-lookup"><span data-stu-id="bee2a-122">Indexed properties can have more than one index value.</span></span> <span data-ttu-id="bee2a-123">Dans ce cas, les valeurs sont séparées par des virgules lorsque la propriété est utilisée.</span><span class="sxs-lookup"><span data-stu-id="bee2a-123">In that case, the values are separated by commas when the property is used.</span></span> <span data-ttu-id="bee2a-124">La méthode Set dans une telle propriété doit avoir deux arguments curryfiés, le premier étant un tuple contenant les clés et le second est la valeur à définir.</span><span class="sxs-lookup"><span data-stu-id="bee2a-124">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value to set.</span></span>

<span data-ttu-id="bee2a-125">Le code suivant illustre l’utilisation d’une propriété indexée avec plusieurs valeurs d’index.</span><span class="sxs-lookup"><span data-stu-id="bee2a-125">The following code demonstrates the use of an indexed property with multiple index values.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bee2a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bee2a-126">See also</span></span>

- [<span data-ttu-id="bee2a-127">Membres</span><span class="sxs-lookup"><span data-stu-id="bee2a-127">Members</span></span>](index.md)
