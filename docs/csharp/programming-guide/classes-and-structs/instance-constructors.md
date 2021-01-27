---
title: Constructeurs d'instances - Guide de programmation C#
description: Les constructeurs d’instance en C# créent et initialisent toutes les variables de membre d’instance lorsque vous utilisez la nouvelle expression pour créer un objet d’une classe.
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: 0f9372c744a7bdfab44c8cd020a4378cff729c57
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899033"
---
# <a name="instance-constructors-c-programming-guide"></a><span data-ttu-id="e6133-103">Constructeurs d'instances (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="e6133-103">Instance Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="e6133-104">Les constructeurs d’instances sont utilisés pour créer et initialiser toutes les variables membres d’instance quand vous utilisez l’expression [new](../../language-reference/operators/new-operator.md) pour créer un objet d’une [classe](../../language-reference/keywords/class.md).</span><span class="sxs-lookup"><span data-stu-id="e6133-104">Instance constructors are used to create and initialize any instance member variables when you use the [new](../../language-reference/operators/new-operator.md) expression to create an object of a [class](../../language-reference/keywords/class.md).</span></span> <span data-ttu-id="e6133-105">Pour initialiser une classe [statique](../../language-reference/keywords/static.md) ou des variables statiques dans une classe non statique, vous devez définir un constructeur statique.</span><span class="sxs-lookup"><span data-stu-id="e6133-105">To initialize a [static](../../language-reference/keywords/static.md) class, or static variables in a non-static class, you define a static constructor.</span></span> <span data-ttu-id="e6133-106">Pour plus d’informations, consultez [Constructeurs statiques](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="e6133-106">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
 <span data-ttu-id="e6133-107">L’exemple suivant présente un constructeur d’instance :</span><span class="sxs-lookup"><span data-stu-id="e6133-107">The following example shows an instance constructor:</span></span>  
  
 [!code-csharp[CoordsWithParameterlessConstructorOnly#1](snippets/instance-constructors/coords/Program.cs#1)]
  
> [!NOTE]
> <span data-ttu-id="e6133-108">Pour plus de clarté, cette classe contient des champs publics.</span><span class="sxs-lookup"><span data-stu-id="e6133-108">For clarity, this class contains public fields.</span></span> <span data-ttu-id="e6133-109">L’utilisation de champs publics n’est pas une pratique de programmation recommandée, car elle octroie à n’importe quelle méthode n’importe où dans un programme un accès sans restriction ni vérification aux mécanismes internes d’un objet.</span><span class="sxs-lookup"><span data-stu-id="e6133-109">The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings.</span></span> <span data-ttu-id="e6133-110">Les données membres doivent généralement être privées et doivent être accessibles uniquement via les propriétés et les méthodes de classe.</span><span class="sxs-lookup"><span data-stu-id="e6133-110">Data members should generally be private, and should be accessed only through class methods and properties.</span></span>  
  
 <span data-ttu-id="e6133-111">Ce constructeur d’instance est appelé chaque fois qu’un objet basé sur la classe `Coords` est créé.</span><span class="sxs-lookup"><span data-stu-id="e6133-111">This instance constructor is called whenever an object based on the `Coords` class is created.</span></span> <span data-ttu-id="e6133-112">Un constructeur comme celui-ci, qui n’accepte aucun argument, est un *constructeur sans paramètre*.</span><span class="sxs-lookup"><span data-stu-id="e6133-112">A constructor like this one, which takes no arguments, is called a *parameterless constructor*.</span></span> <span data-ttu-id="e6133-113">Toutefois, il est souvent utile de fournir des constructeurs supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="e6133-113">However, it is often useful to provide additional constructors.</span></span> <span data-ttu-id="e6133-114">Par exemple, nous pouvons ajouter un constructeur à la classe `Coords` qui nous permet de spécifier les valeurs initiales pour les données membres :</span><span class="sxs-lookup"><span data-stu-id="e6133-114">For example, we can add a constructor to the `Coords` class that allows us to specify the initial values for the data members:</span></span>  
  
 [!code-csharp[TwoArgumentConstructor#2](snippets/instance-constructors/coords/Program.cs#2)]
  
 <span data-ttu-id="e6133-115">Cela permet de créer des objets `Coords` avec des valeurs par défaut ou initiales spécifiques, comme suit :</span><span class="sxs-lookup"><span data-stu-id="e6133-115">This allows `Coords` objects to be created with default or specific initial values, like this:</span></span>  
  
 [!code-csharp[InstantiatingCoords#3](snippets/instance-constructors/coords/Program.cs#3)]
  
 <span data-ttu-id="e6133-116">Si une classe n’a pas de constructeur, un constructeur sans paramètre est généré automatiquement, et les valeurs par défaut sont utilisées pour initialiser les champs objet.</span><span class="sxs-lookup"><span data-stu-id="e6133-116">If a class does not have a constructor, a parameterless constructor is automatically generated and default values are used to initialize the object fields.</span></span> <span data-ttu-id="e6133-117">Par exemple, [int](../../language-reference/builtin-types/integral-numeric-types.md) est initialisé à 0.</span><span class="sxs-lookup"><span data-stu-id="e6133-117">For example, an [int](../../language-reference/builtin-types/integral-numeric-types.md) is initialized to 0.</span></span> <span data-ttu-id="e6133-118">Pour plus d’informations sur les valeurs par défaut de type, consultez [valeurs par défaut des types C#](../../language-reference/builtin-types/default-values.md).</span><span class="sxs-lookup"><span data-stu-id="e6133-118">For information about the type default values, see [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="e6133-119">Par conséquent, comme le constructeur sans paramètre de la classe `Coords` initialise toutes les données membres à zéro, il peut être supprimé entièrement sans modification du fonctionnement de la classe.</span><span class="sxs-lookup"><span data-stu-id="e6133-119">Therefore, because the `Coords` class parameterless constructor initializes all data members to zero, it can be removed altogether without changing how the class works.</span></span> <span data-ttu-id="e6133-120">Un exemple complet d’utilisation de plusieurs constructeurs est fourni dans l’exemple 1, plus loin dans cette rubrique, et un exemple d’un constructeur généré automatiquement est fourni dans l’exemple 2.</span><span class="sxs-lookup"><span data-stu-id="e6133-120">A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.</span></span>  
  
 <span data-ttu-id="e6133-121">Les constructeurs d’instances peuvent également servir à appeler les constructeurs d’instances des classes de base.</span><span class="sxs-lookup"><span data-stu-id="e6133-121">Instance constructors can also be used to call the instance constructors of base classes.</span></span> <span data-ttu-id="e6133-122">Le constructeur de classe peut appeler le constructeur de la classe de base via l’initialiseur, comme suit :</span><span class="sxs-lookup"><span data-stu-id="e6133-122">The class constructor can invoke the constructor of the base class through the initializer, as follows:</span></span>  
  
```csharp
class Circle : Shape
{
    public Circle(double radius)
        : base(radius, 0)
    {
    }
}
```
  
 <span data-ttu-id="e6133-123">Dans cet exemple, la classe `Circle` passe des valeurs représentant le rayon et la hauteur au constructeur fourni par `Shape` duquel `Circle` est dérivé.</span><span class="sxs-lookup"><span data-stu-id="e6133-123">In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived.</span></span> <span data-ttu-id="e6133-124">Un exemple complet d’utilisation de `Shape` et `Circle` s’affiche dans cette rubrique en tant qu’exemple 3.</span><span class="sxs-lookup"><span data-stu-id="e6133-124">A complete example using `Shape` and `Circle` appears in this topic as Example 3.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="e6133-125">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="e6133-125">Example 1</span></span>  

 <span data-ttu-id="e6133-126">L’exemple suivant illustre une classe avec deux constructeurs de classe, l’un sans argument et l’autre avec deux arguments.</span><span class="sxs-lookup"><span data-stu-id="e6133-126">The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.</span></span>  
  
 [!code-csharp[CoordsFullExample#4](snippets/instance-constructors/coords/Program.cs#4)]
  
## <a name="example-2"></a><span data-ttu-id="e6133-127">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="e6133-127">Example 2</span></span>  

 <span data-ttu-id="e6133-128">Dans cet exemple, la classe `Person` n’a aucun constructeur, auquel cas un constructeur sans paramètre est fourni automatiquement, et les champs sont initialisés à leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="e6133-128">In this example, the class `Person` does not have any constructors, in which case, a parameterless constructor is automatically provided and the fields are initialized to their default values.</span></span>  
  
 [!code-csharp[Person](snippets/instance-constructors/person/Program.cs)]
  
 <span data-ttu-id="e6133-129">Notez que la valeur par défaut d’`age` est `0` et que celle de `name` est `null`.</span><span class="sxs-lookup"><span data-stu-id="e6133-129">Notice that the default value of `age` is `0` and the default value of `name` is `null`.</span></span>
  
## <a name="example-3"></a><span data-ttu-id="e6133-130">Exemple 3</span><span class="sxs-lookup"><span data-stu-id="e6133-130">Example 3</span></span>  

 <span data-ttu-id="e6133-131">L’exemple suivant illustre l’utilisation de l’initialiseur de classe de base.</span><span class="sxs-lookup"><span data-stu-id="e6133-131">The following example demonstrates using the base class initializer.</span></span> <span data-ttu-id="e6133-132">La classe `Circle` est dérivée de la classe générale `Shape` et la classe `Cylinder` est dérivée de la classe `Circle`.</span><span class="sxs-lookup"><span data-stu-id="e6133-132">The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class.</span></span> <span data-ttu-id="e6133-133">Le constructeur de chaque classe dérivée utilise son initialiseur de classe de base.</span><span class="sxs-lookup"><span data-stu-id="e6133-133">The constructor on each derived class is using its base class initializer.</span></span>  
  
 [!code-csharp[ShapesExample](snippets/instance-constructors/shapes/Program.cs)]
  
 <span data-ttu-id="e6133-134">Pour obtenir d’autres exemples sur l’appel des constructeurs de classe de base, consultez [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md) et [base](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="e6133-134">For more examples on invoking the base class constructors, see [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), and [base](../../language-reference/keywords/base.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6133-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6133-135">See also</span></span>

- [<span data-ttu-id="e6133-136">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="e6133-136">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e6133-137">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="e6133-137">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="e6133-138">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="e6133-138">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="e6133-139">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="e6133-139">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="e6133-140">static</span><span class="sxs-lookup"><span data-stu-id="e6133-140">static</span></span>](../../language-reference/keywords/static.md)
