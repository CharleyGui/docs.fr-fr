---
title: Expressions d'objet
description: 'Apprenez à utiliser des expressions d’objet F # lorsque vous souhaitez éviter le code supplémentaire et la surcharge nécessaires à la création d’un nouveau type nommé.'
ms.date: 02/08/2019
ms.openlocfilehash: 8a3e40b7833b551eefb95ec62b935acd1ba7b1f9
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740300"
---
# <a name="object-expressions"></a><span data-ttu-id="3e454-103">Expressions d'objet</span><span class="sxs-lookup"><span data-stu-id="3e454-103">Object Expressions</span></span>

<span data-ttu-id="3e454-104">Une *expression d’objet* est une expression qui crée une nouvelle instance d’un type d’objet anonyme créé dynamiquement qui est basé sur un type de base, une interface ou un ensemble d’interfaces existant.</span><span class="sxs-lookup"><span data-stu-id="3e454-104">An *object expression* is an expression that creates a new instance of a dynamically created, anonymous object type that is based on an existing base type, interface, or set of interfaces.</span></span>

## <a name="syntax"></a><span data-ttu-id="3e454-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e454-105">Syntax</span></span>

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a><span data-ttu-id="3e454-106">Notes</span><span class="sxs-lookup"><span data-stu-id="3e454-106">Remarks</span></span>

<span data-ttu-id="3e454-107">Dans la syntaxe précédente, *TypeName* représente un type de classe ou d’interface existant.</span><span class="sxs-lookup"><span data-stu-id="3e454-107">In the previous syntax, the *typename* represents an existing class type or interface type.</span></span> <span data-ttu-id="3e454-108">*type-params* décrit les paramètres de type générique facultatifs.</span><span class="sxs-lookup"><span data-stu-id="3e454-108">*type-params* describes the optional generic type parameters.</span></span> <span data-ttu-id="3e454-109">Les *arguments* sont utilisés uniquement pour les types de classe, qui requièrent des paramètres de constructeur.</span><span class="sxs-lookup"><span data-stu-id="3e454-109">The *arguments* are used only for class types, which require constructor parameters.</span></span> <span data-ttu-id="3e454-110">Les *définitions de membres* sont des substitutions de méthodes de classe de base ou des implémentations de méthodes abstraites à partir d’une classe de base ou d’une interface.</span><span class="sxs-lookup"><span data-stu-id="3e454-110">The *member-definitions* are overrides of base class methods, or implementations of abstract methods from either a base class or an interface.</span></span>

<span data-ttu-id="3e454-111">L’exemple suivant illustre plusieurs types différents d’expressions d’objet.</span><span class="sxs-lookup"><span data-stu-id="3e454-111">The following example illustrates several different types of object expressions.</span></span>

```fsharp
// This object expression specifies a System.Object but overrides the
// ToString method.
let obj1 = { new System.Object() with member x.ToString() = "F#" }
printfn $"{obj1}"

// This object expression implements the IFormattable interface.
let delimiter(delim1: string, delim2: string, value: string) =
    { new System.IFormattable with
        member x.ToString(format: string, provider: System.IFormatProvider) =
            if format = "D" then
                delim1 + value + delim2
            else
                value }

let obj2 = delimiter("{","}", "Bananas!");

printfn "%A" (System.String.Format("{0:D}", obj2))

// Define two interfaces
type IFirst =
  abstract F : unit -> unit
  abstract G : unit -> unit

type ISecond =
  inherit IFirst
  abstract H : unit -> unit
  abstract J : unit -> unit

// This object expression implements both interfaces.
let implementer() =
    { new ISecond with
        member this.H() = ()
        member this.J() = ()
      interface IFirst with
        member this.F() = ()
        member this.G() = () }
```

## <a name="using-object-expressions"></a><span data-ttu-id="3e454-112">Utilisation d’expressions d’objet</span><span class="sxs-lookup"><span data-stu-id="3e454-112">Using Object Expressions</span></span>

<span data-ttu-id="3e454-113">Vous utilisez des expressions d’objet lorsque vous souhaitez éviter le code et la surcharge supplémentaires requis pour créer un nouveau type nommé.</span><span class="sxs-lookup"><span data-stu-id="3e454-113">You use object expressions when you want to avoid the extra code and overhead that is required to create a new, named type.</span></span> <span data-ttu-id="3e454-114">Si vous utilisez des expressions d’objet pour réduire le nombre de types créés dans un programme, vous pouvez réduire le nombre de lignes de code et empêcher la prolifération inutile des types.</span><span class="sxs-lookup"><span data-stu-id="3e454-114">If you use object expressions to minimize the number of types created in a program, you can reduce the number of lines of code and prevent the unnecessary proliferation of types.</span></span> <span data-ttu-id="3e454-115">Au lieu de créer de nombreux types juste pour gérer des situations spécifiques, vous pouvez utiliser une expression d’objet qui personnalise un type existant ou fournit une implémentation appropriée d’une interface pour le cas spécifique.</span><span class="sxs-lookup"><span data-stu-id="3e454-115">Instead of creating many types just to handle specific situations, you can use an object expression that customizes an existing type or provides an appropriate implementation of an interface for the specific case at hand.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e454-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e454-116">See also</span></span>

- [<span data-ttu-id="3e454-117">Informations de référence sur le langage F #</span><span class="sxs-lookup"><span data-stu-id="3e454-117">F# Language Reference</span></span>](index.md)
