---
title: Mot clé Fixed
description: 'Découvrez comment vous pouvez « épingler » un local sur la pile pour empêcher la collecte avec le mot clé F # « Fixed ».'
ms.date: 08/15/2020
ms.openlocfilehash: 786ffd706c243fc83f8fb3afc2201d2a34536372
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559178"
---
# <a name="the-fixed-keyword"></a>Mot clé Fixed

Le `fixed` mot clé vous permet d’épingler une variable locale sur la pile pour l’empêcher d’être collectée ou déplacée pendant le garbage collection.  Il est utilisé pour les scénarios de programmation de bas niveau.

## <a name="syntax"></a>Syntaxe

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a>Notes

Cela étend la syntaxe des expressions pour permettre l’extraction d’un pointeur et sa liaison à un nom qui ne peut pas être collecté ou déplacé pendant le garbage collection.  

Un pointeur à partir d’une expression est fixe via le `fixed` mot clé est lié à un identificateur via le `use` mot clé.  La sémantique de cette valeur est similaire à la gestion des ressources via le `use` mot clé.  Le pointeur est fixe alors qu’il est dans la portée et, une fois qu’il est hors de portée, il n’est plus résolu.  `fixed` ne peut pas être utilisé en dehors du contexte d’une `use` liaison.  Vous devez lier le pointeur à un nom avec `use` .

L’utilisation de `fixed` doit se produire dans une expression d’une fonction ou d’une méthode.  Elle ne peut pas être utilisée au niveau du script ou au niveau du module.

Comme tout comme le code de pointeur, il s’agit d’une fonctionnalité non sécurisée qui émet un avertissement quand elle est utilisée.

## <a name="example"></a>Exemple

```fsharp
open Microsoft.FSharp.NativeInterop

type Point = { mutable X: int; mutable Y: int}

let squareWithPointer (p: nativeptr<int>) =
    // Dereference the pointer at the 0th address.
    let mutable value = NativePtr.get p 0

    // Perform some work
    value <- value * value

    // Set the value in the pointer at the 0th address.
    NativePtr.set p 0 value

let pnt = { X = 1; Y = 2 }
printfn "pnt before - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 2

// Note that the use of 'fixed' is inside a function.
// You cannot fix a pointer at a script-level or module-level scope.
let doPointerWork() =
    use ptr = fixed &pnt.Y

    // Square the Y value
    squareWithPointer ptr
    printfn "pnt after - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 4

doPointerWork()
```

## <a name="see-also"></a>Voir aussi

- [Module NativePtr](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-nativeinterop-nativeptrmodule.html)
