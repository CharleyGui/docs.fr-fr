---
title: Implémentation d’interface explicite - Guide de programmation C#
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: ea32a279b7c464174a7fada5ef93ccf62ef39884
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167671"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="535f7-102">Implémentation d’interface explicite (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="535f7-102">Explicit Interface Implementation (C# Programming Guide)</span></span>

<span data-ttu-id="535f7-103">Si une [classe](../../language-reference/keywords/class.md) implémente deux interfaces qui contiennent un membre avec la même signature, l’implémentation de ce membre sur la classe a pour conséquence que les deux interfaces utilisent ce membre comme leur implémentation.</span><span class="sxs-lookup"><span data-stu-id="535f7-103">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="535f7-104">Dans l’exemple suivant, tous les appels à `Paint` appellent la même méthode.</span><span class="sxs-lookup"><span data-stu-id="535f7-104">In the following example, all the calls to `Paint` invoke the same method.</span></span> <span data-ttu-id="535f7-105">Ce premier échantillon définit les types :</span><span class="sxs-lookup"><span data-stu-id="535f7-105">This first sample defines the types:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

<span data-ttu-id="535f7-106">L’échantillon suivant appelle les méthodes :</span><span class="sxs-lookup"><span data-stu-id="535f7-106">The following sample calls the methods:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

<span data-ttu-id="535f7-107">Lorsque deux membres de l’interface n’exécutent pas la même fonction, cela conduit à une implémentation incorrecte d’une ou des deux interfaces.</span><span class="sxs-lookup"><span data-stu-id="535f7-107">When two interface members don't perform the same function, it leads to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="535f7-108">Il est possible de mettre en œuvre explicitement un membre de l’interface, en créant un membre de classe qui n’est appelé que par l’interface, et qui est spécifique à cette interface.</span><span class="sxs-lookup"><span data-stu-id="535f7-108">It's possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="535f7-109">Nommez le membre de la classe avec le nom de l’interface et une période.</span><span class="sxs-lookup"><span data-stu-id="535f7-109">Name the class member with the name of the interface and a period.</span></span> <span data-ttu-id="535f7-110">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="535f7-110">For example:</span></span>

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

<span data-ttu-id="535f7-111">Le membre de classe `IControl.Paint` est disponible uniquement via l’interface `IControl` et `ISurface.Paint` est disponible uniquement via `ISurface`.</span><span class="sxs-lookup"><span data-stu-id="535f7-111">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="535f7-112">Les deux implémentations de méthode sont séparées, et ni l’un ni l’autre ne sont disponibles directement sur la classe.</span><span class="sxs-lookup"><span data-stu-id="535f7-112">Both method implementations are separate, and neither are available directly on the class.</span></span> <span data-ttu-id="535f7-113">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="535f7-113">For example:</span></span>

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

<span data-ttu-id="535f7-114">La mise en œuvre explicite est également utilisée pour résoudre les cas où deux interfaces déclarent chacune des membres différents du même nom tels qu’une propriété et une méthode.</span><span class="sxs-lookup"><span data-stu-id="535f7-114">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method.</span></span> <span data-ttu-id="535f7-115">Pour implémenter les deux interfaces, une `P`classe doit `P`utiliser une implémentation explicite soit pour la propriété, ou la méthode, ou les deux, pour éviter une erreur de compilateur.</span><span class="sxs-lookup"><span data-stu-id="535f7-115">To implement both interfaces, a class has to use explicit implementation either for the property `P`, or the method `P`, or both, to avoid a compiler error.</span></span> <span data-ttu-id="535f7-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="535f7-116">For example:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

<span data-ttu-id="535f7-117">En commençant par [C 8.0](../../whats-new/csharp-8.md#default-interface-methods), vous pouvez définir une implémentation pour les membres déclarés dans une interface.</span><span class="sxs-lookup"><span data-stu-id="535f7-117">Beginning with [C# 8.0](../../whats-new/csharp-8.md#default-interface-methods), you can define an implementation for members declared in an interface.</span></span> <span data-ttu-id="535f7-118">Si une classe hérite d’une implémentation de méthode à partir d’une interface, cette méthode n’est accessible que par une référence du type d’interface.</span><span class="sxs-lookup"><span data-stu-id="535f7-118">If a class inherits a method implementation from an interface, that method is only accessible through a reference of the interface type.</span></span> <span data-ttu-id="535f7-119">Le membre hérité n’apparaît pas comme faisant partie de l’interface publique.</span><span class="sxs-lookup"><span data-stu-id="535f7-119">The inherited member doesn't appear as part of the public interface.</span></span> <span data-ttu-id="535f7-120">L’échantillon suivant définit une implémentation par défaut pour une méthode d’interface :</span><span class="sxs-lookup"><span data-stu-id="535f7-120">The following sample defines a default implementation for an interface method:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

<span data-ttu-id="535f7-121">L’échantillon suivant invoque la mise en œuvre par défaut :</span><span class="sxs-lookup"><span data-stu-id="535f7-121">The following sample invokes the default implementation:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

<span data-ttu-id="535f7-122">Toute classe qui `IControl` implémente l’interface peut passer outre à la méthode par défaut, `Paint` soit comme méthode publique, soit comme implémentation d’interface explicite.</span><span class="sxs-lookup"><span data-stu-id="535f7-122">Any class that implements the `IControl` interface can override the default `Paint` method, either as a public method, or as an explicit interface implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="535f7-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="535f7-123">See also</span></span>

- [<span data-ttu-id="535f7-124">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="535f7-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="535f7-125">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="535f7-125">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="535f7-126">Interfaces</span><span class="sxs-lookup"><span data-stu-id="535f7-126">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="535f7-127">Héritage</span><span class="sxs-lookup"><span data-stu-id="535f7-127">Inheritance</span></span>](../classes-and-structs/inheritance.md)
