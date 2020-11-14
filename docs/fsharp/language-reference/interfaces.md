---
title: Interfaces
description: 'Découvrez comment les interfaces F # spécifient des jeux de membres connexes que d’autres classes implémentent.'
ms.date: 08/15/2020
ms.openlocfilehash: 0cef2932045dae401f5aa069107815543457ca4a
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557049"
---
# <a name="interfaces"></a><span data-ttu-id="39a15-103">Interfaces</span><span class="sxs-lookup"><span data-stu-id="39a15-103">Interfaces</span></span>

<span data-ttu-id="39a15-104">Les *interfaces* spécifient des ensembles de membres associés que d’autres classes implémentent.</span><span class="sxs-lookup"><span data-stu-id="39a15-104">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="39a15-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39a15-105">Syntax</span></span>

```fsharp
// Interface declaration:
[ attributes ]
type [accessibility-modifier] interface-name =
    [ interface ]     [ inherit base-interface-name ...]
    abstract member1 : [ argument-types1 -> ] return-type1
    abstract member2 : [ argument-types2 -> ] return-type2
    ...
[ end ]

// Implementing, inside a class type definition:
interface interface-name with
    member self-identifier.member1argument-list = method-body1
    member self-identifier.member2argument-list = method-body2

// Implementing, by using an object expression:
[ attributes ]
let class-name (argument-list) =
    { new interface-name with
        member self-identifier.member1argument-list = method-body1
        member self-identifier.member2argument-list = method-body2
        [ base-interface-definitions ]
    }
    member-list
```

## <a name="remarks"></a><span data-ttu-id="39a15-106">Notes</span><span class="sxs-lookup"><span data-stu-id="39a15-106">Remarks</span></span>

<span data-ttu-id="39a15-107">Les déclarations d’interface ressemblent aux déclarations de classe, à ceci près qu’aucun membre n’est implémenté.</span><span class="sxs-lookup"><span data-stu-id="39a15-107">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="39a15-108">Au lieu de cela, tous les membres sont abstraits, comme indiqué par le mot clé `abstract` .</span><span class="sxs-lookup"><span data-stu-id="39a15-108">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="39a15-109">Vous ne fournissez pas de corps de méthode pour les méthodes abstraites.</span><span class="sxs-lookup"><span data-stu-id="39a15-109">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="39a15-110">Toutefois, vous pouvez fournir une implémentation par défaut en incluant également une définition distincte du membre en tant que méthode avec le `default` mot clé.</span><span class="sxs-lookup"><span data-stu-id="39a15-110">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="39a15-111">Cela revient à créer une méthode virtuelle dans une classe de base dans d’autres langages .NET.</span><span class="sxs-lookup"><span data-stu-id="39a15-111">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="39a15-112">Une telle méthode virtuelle peut être substituée dans les classes qui implémentent l’interface.</span><span class="sxs-lookup"><span data-stu-id="39a15-112">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="39a15-113">L’accessibilité par défaut pour les interfaces est `public` .</span><span class="sxs-lookup"><span data-stu-id="39a15-113">The default accessibility for interfaces is `public`.</span></span>

<span data-ttu-id="39a15-114">Vous pouvez éventuellement attribuer un nom à chaque paramètre de méthode à l’aide d’une syntaxe F # normale :</span><span class="sxs-lookup"><span data-stu-id="39a15-114">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="39a15-115">Dans l’exemple ci-dessus `ISprintable` , la `Print` méthode a un seul paramètre du type `string` portant le nom `format` .</span><span class="sxs-lookup"><span data-stu-id="39a15-115">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="39a15-116">Il existe deux façons d’implémenter des interfaces : en utilisant des expressions d’objet et des types de classe.</span><span class="sxs-lookup"><span data-stu-id="39a15-116">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="39a15-117">Dans les deux cas, le type de classe ou l’expression d’objet fournit des corps de méthode pour les méthodes abstraites de l’interface.</span><span class="sxs-lookup"><span data-stu-id="39a15-117">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="39a15-118">Les implémentations sont spécifiques à chaque type qui implémente l’interface.</span><span class="sxs-lookup"><span data-stu-id="39a15-118">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="39a15-119">Par conséquent, les méthodes d’interface sur des types différents peuvent être différentes les unes des autres.</span><span class="sxs-lookup"><span data-stu-id="39a15-119">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="39a15-120">Les mots clés `interface` et `end` , qui marquent le début et la fin de la définition, sont facultatifs lorsque vous utilisez la syntaxe simplifiée.</span><span class="sxs-lookup"><span data-stu-id="39a15-120">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="39a15-121">Si vous n’utilisez pas ces mots clés, le compilateur tente de déduire si le type est une classe ou une interface en analysant les constructions que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="39a15-121">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="39a15-122">Si vous définissez un membre ou utilisez une autre syntaxe de classe, le type est interprété comme une classe.</span><span class="sxs-lookup"><span data-stu-id="39a15-122">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="39a15-123">Le style de codage .NET consiste à commencer toutes les interfaces en majuscules `I` .</span><span class="sxs-lookup"><span data-stu-id="39a15-123">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>

<span data-ttu-id="39a15-124">Vous pouvez spécifier plusieurs paramètres de deux manières : le style F # et le. Style NET.</span><span class="sxs-lookup"><span data-stu-id="39a15-124">You can specify multiple parameters in two ways: F#-style and .NET-style.</span></span> <span data-ttu-id="39a15-125">Les deux seront compilés de la même façon pour les consommateurs .NET, mais le style F # forcera les appelants F # à utiliser l’application de paramètre de style F # et. NET-style forcera les appelants F # à utiliser l’application d’arguments avec des tuples.</span><span class="sxs-lookup"><span data-stu-id="39a15-125">Both will compile the same way for .NET consumers, but F#-style will force F# callers to use F#-style parameter application and .NET-style will force F# callers to use tupled argument application.</span></span>

```fsharp
type INumeric1 =
    abstract Add: x: int -> y: int -> int

type INumeric2 =
    abstract Add: x: int * y: int -> int
```

## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="39a15-126">Implémentation d’interfaces à l’aide de types de classe</span><span class="sxs-lookup"><span data-stu-id="39a15-126">Implementing Interfaces by Using Class Types</span></span>

<span data-ttu-id="39a15-127">Vous pouvez implémenter une ou plusieurs interfaces dans un type de classe en utilisant le `interface` mot clé, le nom de l’interface et le `with` mot clé, suivis par les définitions de membres d’interface, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="39a15-127">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="39a15-128">Les implémentations d’interface sont héritées, de sorte que toutes les classes dérivées n’ont pas besoin de les réimplémenter.</span><span class="sxs-lookup"><span data-stu-id="39a15-128">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>

## <a name="calling-interface-methods"></a><span data-ttu-id="39a15-129">Appeler des méthodes d’interface</span><span class="sxs-lookup"><span data-stu-id="39a15-129">Calling Interface Methods</span></span>

<span data-ttu-id="39a15-130">Les méthodes d’interface peuvent être appelées uniquement par le biais de l’interface, et non par l’intermédiaire d’un objet du type qui implémente l’interface.</span><span class="sxs-lookup"><span data-stu-id="39a15-130">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="39a15-131">Par conséquent, vous devrez peut-être effectuer une conversion vers le type d’interface à l’aide de l' `:>` opérateur ou `upcast` de l’opérateur pour appeler ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="39a15-131">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="39a15-132">Pour appeler la méthode d’interface quand vous avez un objet de type `SomeClass` , vous devez effectuer un upcast de l’objet vers le type d’interface, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="39a15-132">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="39a15-133">Une alternative consiste à déclarer une méthode sur l’objet qui effectue un upcast et appelle la méthode d’interface, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="39a15-133">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="39a15-134">Implémentation d’interfaces à l’aide d’expressions d’objet</span><span class="sxs-lookup"><span data-stu-id="39a15-134">Implementing Interfaces by Using Object Expressions</span></span>

<span data-ttu-id="39a15-135">Les expressions d’objet fournissent un bref moyen d’implémenter une interface.</span><span class="sxs-lookup"><span data-stu-id="39a15-135">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="39a15-136">Elles sont utiles lorsque vous n’avez pas besoin de créer un type nommé et que vous souhaitez simplement un objet qui prend en charge les méthodes d’interface, sans aucune méthode supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="39a15-136">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="39a15-137">Une expression d’objet est illustrée dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="39a15-137">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a><span data-ttu-id="39a15-138">Héritage de l'interface</span><span class="sxs-lookup"><span data-stu-id="39a15-138">Interface Inheritance</span></span>

<span data-ttu-id="39a15-139">Les interfaces peuvent hériter d’une ou de plusieurs interfaces de base.</span><span class="sxs-lookup"><span data-stu-id="39a15-139">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="implementing-interfaces-with-default-implementations"></a><span data-ttu-id="39a15-140">Implémentation d’interfaces avec des implémentations par défaut</span><span class="sxs-lookup"><span data-stu-id="39a15-140">Implementing interfaces with default implementations</span></span>

<span data-ttu-id="39a15-141">C# prend en charge la définition d’interfaces avec des implémentations par défaut, comme suit :</span><span class="sxs-lookup"><span data-stu-id="39a15-141">C# supports defining interfaces with default implementations, like so:</span></span>

```csharp
using System;

namespace CSharp
{
    public interface MyDim
    {
        public int Z => 0;
    }
}
```

<span data-ttu-id="39a15-142">Celles-ci sont directement consommables à partir de F # :</span><span class="sxs-lookup"><span data-stu-id="39a15-142">These are directly consumable from F#:</span></span>

```fsharp
open CSharp

// You can implement the interface via a class
type MyType() =
    member _.M() = ()

    interface MyDim

let md = MyType() :> MyDim
printfn $"DIM from C#: %d{md.Z}"

// You can also implement it via an object expression
let md' = { new MyDim }
printfn $"DIM from C# but via Object Expression: %d{md'.Z}"
```

<span data-ttu-id="39a15-143">Vous pouvez substituer une implémentation par défaut avec `override` , comme remplacer n’importe quel membre virtuel.</span><span class="sxs-lookup"><span data-stu-id="39a15-143">You can override a default implementation with `override`, like overriding any virtual member.</span></span>

<span data-ttu-id="39a15-144">Les membres d’une interface qui n’ont pas d’implémentation par défaut doivent tout de même être implémentés de manière explicite.</span><span class="sxs-lookup"><span data-stu-id="39a15-144">Any members in an interface that do not have a default implementation must still be explicitly implemented.</span></span>

## <a name="implementing-the-same-interface-at-different-generic-instantiations"></a><span data-ttu-id="39a15-145">Implémentation de la même interface à différentes instanciations génériques</span><span class="sxs-lookup"><span data-stu-id="39a15-145">Implementing the same interface at different generic instantiations</span></span>

<span data-ttu-id="39a15-146">F # prend en charge l’implémentation de la même interface à différentes instanciations génériques, comme ceci :</span><span class="sxs-lookup"><span data-stu-id="39a15-146">F# supports implementing the same interface at different generic instantiations like so:</span></span>

```fsharp
type IA<'T> =
    abstract member Get : unit -> 'T

type MyClass() =
    interface IA<int> with
        member x.Get() = 1
    interface IA<string> with
        member x.Get() = "hello"

let mc = MyClass()
let iaInt = mc :> IA<int>
let iaString = mc :> IA<string>

iaInt.Get() // 1
iaString.Get() // "hello"
```

## <a name="see-also"></a><span data-ttu-id="39a15-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39a15-147">See also</span></span>

- [<span data-ttu-id="39a15-148">Informations de référence sur le langage F #</span><span class="sxs-lookup"><span data-stu-id="39a15-148">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="39a15-149">Expressions d'objet</span><span class="sxs-lookup"><span data-stu-id="39a15-149">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="39a15-150">Classes</span><span class="sxs-lookup"><span data-stu-id="39a15-150">Classes</span></span>](classes.md)
