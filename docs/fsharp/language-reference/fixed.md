---
title: Mot clé Fixed
description: 'Découvrez comment vous pouvez « épingler » un local sur la pile pour empêcher la collecte avec le mot clé F # « Fixed ».'
ms.date: 08/15/2020
ms.openlocfilehash: b4b0d1ae101d5f7b65bff80fa070c9fd54de8d66
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740352"
---
# <a name="the-fixed-keyword"></a><span data-ttu-id="a50da-103">Mot clé Fixed</span><span class="sxs-lookup"><span data-stu-id="a50da-103">The fixed keyword</span></span>

<span data-ttu-id="a50da-104">Le `fixed` mot clé vous permet d’épingler une variable locale sur la pile pour l’empêcher d’être collectée ou déplacée pendant le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="a50da-104">The `fixed` keyword allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="a50da-105">Il est utilisé pour les scénarios de programmation de bas niveau.</span><span class="sxs-lookup"><span data-stu-id="a50da-105">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="a50da-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a50da-106">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="a50da-107">Notes</span><span class="sxs-lookup"><span data-stu-id="a50da-107">Remarks</span></span>

<span data-ttu-id="a50da-108">Cela étend la syntaxe des expressions pour permettre l’extraction d’un pointeur et sa liaison à un nom qui ne peut pas être collecté ou déplacé pendant le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="a50da-108">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="a50da-109">Un pointeur à partir d’une expression est fixe via le `fixed` mot clé est lié à un identificateur via le `use` mot clé.</span><span class="sxs-lookup"><span data-stu-id="a50da-109">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="a50da-110">La sémantique de cette valeur est similaire à la gestion des ressources via le `use` mot clé.</span><span class="sxs-lookup"><span data-stu-id="a50da-110">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="a50da-111">Le pointeur est fixe alors qu’il est dans la portée et, une fois qu’il est hors de portée, il n’est plus résolu.</span><span class="sxs-lookup"><span data-stu-id="a50da-111">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="a50da-112">`fixed` ne peut pas être utilisé en dehors du contexte d’une `use` liaison.</span><span class="sxs-lookup"><span data-stu-id="a50da-112">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="a50da-113">Vous devez lier le pointeur à un nom avec `use` .</span><span class="sxs-lookup"><span data-stu-id="a50da-113">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="a50da-114">L’utilisation de `fixed` doit se produire dans une expression d’une fonction ou d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="a50da-114">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="a50da-115">Elle ne peut pas être utilisée au niveau du script ou au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="a50da-115">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="a50da-116">Comme tout comme le code de pointeur, il s’agit d’une fonctionnalité non sécurisée qui émet un avertissement quand elle est utilisée.</span><span class="sxs-lookup"><span data-stu-id="a50da-116">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="a50da-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="a50da-117">Example</span></span>

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
printfn $"pnt before - X: %d{pnt.X} Y: %d{pnt.Y}" // prints 1 and 2

// Note that the use of 'fixed' is inside a function.
// You cannot fix a pointer at a script-level or module-level scope.
let doPointerWork() =
    use ptr = fixed &pnt.Y

    // Square the Y value
    squareWithPointer ptr
    printfn $"pnt after - X: %d{pnt.X} Y: %d{pnt.Y}" // prints 1 and 4

doPointerWork()
```

## <a name="see-also"></a><span data-ttu-id="a50da-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a50da-118">See also</span></span>

- [<span data-ttu-id="a50da-119">Module NativePtr</span><span class="sxs-lookup"><span data-stu-id="a50da-119">NativePtr Module</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-nativeinterop-nativeptrmodule.html)
