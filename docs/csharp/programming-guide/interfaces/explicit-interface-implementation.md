---
title: Implémentation d’interface explicite - Guide de programmation C#
description: Une classe peut implémenter des interfaces qui contiennent un membre avec la même signature en C#. L’implémentation explicite crée un membre de classe spécifique à une interface.
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: a6ec328c08d1da84a11431d9400a094df8c72223
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303085"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="33f8f-104">Implémentation d’interface explicite (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="33f8f-104">Explicit Interface Implementation (C# Programming Guide)</span></span>

<span data-ttu-id="33f8f-105">Si une [classe](../../language-reference/keywords/class.md) implémente deux interfaces qui contiennent un membre avec la même signature, l’implémentation de ce membre sur la classe a pour conséquence que les deux interfaces utilisent ce membre comme leur implémentation.</span><span class="sxs-lookup"><span data-stu-id="33f8f-105">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="33f8f-106">Dans l’exemple suivant, tous les appels à `Paint` appellent la même méthode.</span><span class="sxs-lookup"><span data-stu-id="33f8f-106">In the following example, all the calls to `Paint` invoke the same method.</span></span> <span data-ttu-id="33f8f-107">Ce premier exemple définit les types :</span><span class="sxs-lookup"><span data-stu-id="33f8f-107">This first sample defines the types:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

<span data-ttu-id="33f8f-108">L’exemple suivant appelle les méthodes :</span><span class="sxs-lookup"><span data-stu-id="33f8f-108">The following sample calls the methods:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

<span data-ttu-id="33f8f-109">Lorsque deux membres d’interface n’exécutent pas la même fonction, il en résulte une implémentation incorrecte de l’une ou des deux interfaces.</span><span class="sxs-lookup"><span data-stu-id="33f8f-109">When two interface members don't perform the same function, it leads to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="33f8f-110">Il est possible d’implémenter un membre d’interface explicitement, en créant un membre de classe qui est appelé uniquement par le biais de l’interface, et est spécifique à cette interface.</span><span class="sxs-lookup"><span data-stu-id="33f8f-110">It's possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="33f8f-111">Nommez le membre de classe avec le nom de l’interface et un point.</span><span class="sxs-lookup"><span data-stu-id="33f8f-111">Name the class member with the name of the interface and a period.</span></span> <span data-ttu-id="33f8f-112">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="33f8f-112">For example:</span></span>

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

<span data-ttu-id="33f8f-113">Le membre de classe `IControl.Paint` est disponible uniquement via l’interface `IControl` et `ISurface.Paint` est disponible uniquement via `ISurface`.</span><span class="sxs-lookup"><span data-stu-id="33f8f-113">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="33f8f-114">Les deux implémentations de méthode sont distinctes et ne sont pas directement disponibles sur la classe.</span><span class="sxs-lookup"><span data-stu-id="33f8f-114">Both method implementations are separate, and neither are available directly on the class.</span></span> <span data-ttu-id="33f8f-115">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="33f8f-115">For example:</span></span>

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

<span data-ttu-id="33f8f-116">L’implémentation explicite est également utilisée pour résoudre les cas où deux interfaces déclarent chacune des membres différents du même nom, tels qu’une propriété et une méthode.</span><span class="sxs-lookup"><span data-stu-id="33f8f-116">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method.</span></span> <span data-ttu-id="33f8f-117">Pour implémenter les deux interfaces, une classe doit utiliser l’implémentation explicite pour la propriété `P` , la méthode `P` , ou les deux, pour éviter une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="33f8f-117">To implement both interfaces, a class has to use explicit implementation either for the property `P`, or the method `P`, or both, to avoid a compiler error.</span></span> <span data-ttu-id="33f8f-118">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="33f8f-118">For example:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

<span data-ttu-id="33f8f-119">À compter de [C# 8,0](../../whats-new/csharp-8.md#default-interface-methods), vous pouvez définir une implémentation pour les membres déclarés dans une interface.</span><span class="sxs-lookup"><span data-stu-id="33f8f-119">Beginning with [C# 8.0](../../whats-new/csharp-8.md#default-interface-methods), you can define an implementation for members declared in an interface.</span></span> <span data-ttu-id="33f8f-120">Si une classe hérite d’une implémentation de méthode d’une interface, cette méthode est uniquement accessible par le biais d’une référence du type interface.</span><span class="sxs-lookup"><span data-stu-id="33f8f-120">If a class inherits a method implementation from an interface, that method is only accessible through a reference of the interface type.</span></span> <span data-ttu-id="33f8f-121">Le membre hérité n’apparaît pas dans le cadre de l’interface publique.</span><span class="sxs-lookup"><span data-stu-id="33f8f-121">The inherited member doesn't appear as part of the public interface.</span></span> <span data-ttu-id="33f8f-122">L’exemple suivant définit une implémentation par défaut pour une méthode d’interface :</span><span class="sxs-lookup"><span data-stu-id="33f8f-122">The following sample defines a default implementation for an interface method:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

<span data-ttu-id="33f8f-123">L’exemple suivant appelle l’implémentation par défaut :</span><span class="sxs-lookup"><span data-stu-id="33f8f-123">The following sample invokes the default implementation:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

<span data-ttu-id="33f8f-124">Toute classe qui implémente l' `IControl` interface peut substituer la méthode par défaut `Paint` , en tant que méthode publique, ou en tant qu’implémentation d’interface explicite.</span><span class="sxs-lookup"><span data-stu-id="33f8f-124">Any class that implements the `IControl` interface can override the default `Paint` method, either as a public method, or as an explicit interface implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="33f8f-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33f8f-125">See also</span></span>

- [<span data-ttu-id="33f8f-126">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="33f8f-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="33f8f-127">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="33f8f-127">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="33f8f-128">Interfaces</span><span class="sxs-lookup"><span data-stu-id="33f8f-128">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="33f8f-129">Héritage</span><span class="sxs-lookup"><span data-stu-id="33f8f-129">Inheritance</span></span>](../classes-and-structs/inheritance.md)
