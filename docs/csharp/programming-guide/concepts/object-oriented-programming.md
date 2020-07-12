---
title: Programmation orientée objet (C#)
ms.date: 05/13/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 83140a9dbd16f60f04f50ba18c71099cdd862f15
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226632"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="3f756-102">Programmation orientée objet (C#)</span><span class="sxs-lookup"><span data-stu-id="3f756-102">Object-Oriented programming (C#)</span></span>

<span data-ttu-id="3f756-103">C# fournit une prise en charge complète de la programmation orientée objet, notamment l’abstraction, l’encapsulation, l’héritage et le polymorphisme.</span><span class="sxs-lookup"><span data-stu-id="3f756-103">C# provides full support for object-oriented programming including abstraction, encapsulation, inheritance, and polymorphism.</span></span>

- <span data-ttu-id="3f756-104">L' *abstraction* signifie masquer les détails inutiles des consommateurs de type.</span><span class="sxs-lookup"><span data-stu-id="3f756-104">*Abstraction* means hiding the unnecessary details from type consumers.</span></span>
- <span data-ttu-id="3f756-105">L’*encapsulation* signifie qu’un groupe de propriétés, méthodes et autres membres corrélés est traité comme une unité ou un objet unique.</span><span class="sxs-lookup"><span data-stu-id="3f756-105">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>
- <span data-ttu-id="3f756-106">L’*héritage* décrit la possibilité de créer des classes à partir d’une classe existante.</span><span class="sxs-lookup"><span data-stu-id="3f756-106">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>
- <span data-ttu-id="3f756-107">Le *polymorphisme* signifie que plusieurs classes peuvent être utilisées de manière interchangeable, même si chacune des classes implémente les mêmes propriétés ou méthodes de manière différente.</span><span class="sxs-lookup"><span data-stu-id="3f756-107">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

## <a name="classes-and-objects"></a><span data-ttu-id="3f756-108">Classes et objets</span><span class="sxs-lookup"><span data-stu-id="3f756-108">Classes and objects</span></span>

<span data-ttu-id="3f756-109">Les termes *classe* et *objet* décrivent respectivement le *type* des objets et les *instances* des classes.</span><span class="sxs-lookup"><span data-stu-id="3f756-109">The terms *class* and *object* describe the *type* of objects, and the *instances* of classes, respectively.</span></span> <span data-ttu-id="3f756-110">Cela explique pourquoi l’opération de création d’un objet est appelée *instanciation*.</span><span class="sxs-lookup"><span data-stu-id="3f756-110">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="3f756-111">Si l'on reprend l'analogie avec un plan de construction, une classe est un plan, et un objet est un bâtiment construit à partir de ce plan.</span><span class="sxs-lookup"><span data-stu-id="3f756-111">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="3f756-112">Pour définir une classe :</span><span class="sxs-lookup"><span data-stu-id="3f756-112">To define a class:</span></span>

```csharp
class SampleClass
{
}
```

<span data-ttu-id="3f756-113">C# fournit également des types appelés *structures* qui sont utiles lorsque vous n’avez pas besoin de prise en charge de l’héritage ou du polymorphisme.</span><span class="sxs-lookup"><span data-stu-id="3f756-113">C# also provides types called *structures* that are useful when you don't need support for inheritance or polymorphism.</span></span> <span data-ttu-id="3f756-114">Pour plus d’informations, consultez [Choosing Between Class and struct](../../../standard/design-guidelines/choosing-between-class-and-struct.md).</span><span class="sxs-lookup"><span data-stu-id="3f756-114">For more information, see [Choosing between class and struct](../../../standard/design-guidelines/choosing-between-class-and-struct.md).</span></span>

<span data-ttu-id="3f756-115">Pour définir une structure :</span><span class="sxs-lookup"><span data-stu-id="3f756-115">To define a structure:</span></span>

```csharp
struct SampleStruct
{
}
```

<span data-ttu-id="3f756-116">Pour plus d’informations, consultez les articles sur les mots clés [Class](../../language-reference/keywords/class.md) et [struct](../../language-reference/builtin-types/struct.md) .</span><span class="sxs-lookup"><span data-stu-id="3f756-116">For more information, see the articles on the [class](../../language-reference/keywords/class.md) and [struct](../../language-reference/builtin-types/struct.md) keywords.</span></span>

### <a name="class-members"></a><span data-ttu-id="3f756-117">Membres de classe</span><span class="sxs-lookup"><span data-stu-id="3f756-117">Class members</span></span>

<span data-ttu-id="3f756-118">Chaque classe peut avoir différents *membres de classe* : des propriétés qui décrivent les données de classe, des méthodes qui définissent le comportement de classe et des événements qui permettent la communication entre les différents objets et classes.</span><span class="sxs-lookup"><span data-stu-id="3f756-118">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="3f756-119">Propriétés et champs</span><span class="sxs-lookup"><span data-stu-id="3f756-119">Properties and fields</span></span>

<span data-ttu-id="3f756-120">Les propriétés et les champs sont des informations contenues dans un objet.</span><span class="sxs-lookup"><span data-stu-id="3f756-120">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="3f756-121">Les champs sont similaires aux variables, car ils peuvent être lus ou définis directement, sous réserve de modificateurs d’accès applicables.</span><span class="sxs-lookup"><span data-stu-id="3f756-121">Fields are like variables because they can be read or set directly, subject to applicable access modifiers.</span></span>

<span data-ttu-id="3f756-122">Pour définir un champ accessible à partir d’instances de la classe :</span><span class="sxs-lookup"><span data-stu-id="3f756-122">To define a field that can be accessed from within instances of the class:</span></span>

```csharp
public class SampleClass
{
    string sampleField;
}
```

<span data-ttu-id="3f756-123">Les propriétés ont des `get` `set` accesseurs et, qui fournissent davantage de contrôle sur la façon dont les valeurs sont définies ou retournées.</span><span class="sxs-lookup"><span data-stu-id="3f756-123">Properties have `get` and `set` accessors, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="3f756-124">C# vous permet de créer un champ privé pour stocker la valeur de la propriété ou d’utiliser des propriétés implémentées automatiquement qui créent ce champ automatiquement en arrière-plan et fournissent la logique de base pour les procédures de propriété.</span><span class="sxs-lookup"><span data-stu-id="3f756-124">C# allows you either to create a private field for storing the property value or use auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="3f756-125">Pour définir une propriété implémentée automatiquement :</span><span class="sxs-lookup"><span data-stu-id="3f756-125">To define an auto-implemented property:</span></span>

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

<span data-ttu-id="3f756-126">Si vous devez exécuter des opérations supplémentaires pour la lecture et l'écriture de la valeur de propriété, définissez un champ pour le stockage de la valeur de propriété et fournissez la logique de base pour son stockage et son extraction :</span><span class="sxs-lookup"><span data-stu-id="3f756-126">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```csharp
class SampleClass
{
    private int _sample;
    public int Sample
    {
        // Return the value stored in a field.
        get => _sample;
        // Store the value in the field.
        set =>  _sample = value;
    }
}
```

<span data-ttu-id="3f756-127">La plupart des propriétés disposent de méthodes ou de procédures destinées à la fois à définir et à obtenir la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="3f756-127">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="3f756-128">Toutefois, vous pouvez créer des propriétés en lecture seule ou en écriture seule pour empêcher qu'elles soient modifiées ou lues.</span><span class="sxs-lookup"><span data-stu-id="3f756-128">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="3f756-129">En C#, vous pouvez omettre la méthode de propriété `get` ou `set`.</span><span class="sxs-lookup"><span data-stu-id="3f756-129">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="3f756-130">Toutefois, les propriétés implémentées automatiquement ne peuvent pas être en écriture seule.</span><span class="sxs-lookup"><span data-stu-id="3f756-130">However, auto-implemented properties cannot be write-only.</span></span> <span data-ttu-id="3f756-131">Les propriétés implémentées automatiquement en lecture seule peuvent être définies dans les constructeurs de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="3f756-131">Read-only auto-implemented properties can be set in constructors of the containing class.</span></span>

<span data-ttu-id="3f756-132">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="3f756-132">For more information, see:</span></span>

- [<span data-ttu-id="3f756-133">get</span><span class="sxs-lookup"><span data-stu-id="3f756-133">get</span></span>](../../language-reference/keywords/get.md)
- [<span data-ttu-id="3f756-134">set</span><span class="sxs-lookup"><span data-stu-id="3f756-134">set</span></span>](../../language-reference/keywords/set.md)

#### <a name="methods"></a><span data-ttu-id="3f756-135">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3f756-135">Methods</span></span>

<span data-ttu-id="3f756-136">Une *méthode* est une action que peut effectuer un objet.</span><span class="sxs-lookup"><span data-stu-id="3f756-136">A *method* is an action that an object can perform.</span></span>

<span data-ttu-id="3f756-137">Pour définir une méthode de classe :</span><span class="sxs-lookup"><span data-stu-id="3f756-137">To define a method of a class:</span></span>

```csharp
class SampleClass
{
    public int SampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

<span data-ttu-id="3f756-138">Une classe peut avoir plusieurs implémentations, ou *surcharges*, de la même méthode qui diffèrent du point de vue du nombre de paramètres ou des types de paramètres.</span><span class="sxs-lookup"><span data-stu-id="3f756-138">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="3f756-139">Pour surcharger une méthode :</span><span class="sxs-lookup"><span data-stu-id="3f756-139">To overload a method:</span></span>

```csharp
public int SampleMethod(string sampleParam) { }
public int SampleMethod(int sampleParam) { }
```

<span data-ttu-id="3f756-140">Dans la plupart des cas, vous déclarez une méthode dans une définition de classe.</span><span class="sxs-lookup"><span data-stu-id="3f756-140">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="3f756-141">Toutefois, C# prend également en charge des *méthodes d’extension*, qui vous permettent d’ajouter des méthodes à une classe existante hors de la définition réelle de la classe.</span><span class="sxs-lookup"><span data-stu-id="3f756-141">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="3f756-142">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="3f756-142">For more information, see:</span></span>

- [<span data-ttu-id="3f756-143">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3f756-143">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="3f756-144">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="3f756-144">Extension Methods</span></span>](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="3f756-145">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="3f756-145">Constructors</span></span>

<span data-ttu-id="3f756-146">Les constructeurs sont des méthodes de classe qui s'exécutent automatiquement lorsqu'un objet d'un type donné est créé.</span><span class="sxs-lookup"><span data-stu-id="3f756-146">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="3f756-147">Les constructeurs initialisent habituellement les données membres du nouvel objet.</span><span class="sxs-lookup"><span data-stu-id="3f756-147">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="3f756-148">Un constructeur ne peut s'exécuter qu'une seule fois lorsqu'une classe est créée.</span><span class="sxs-lookup"><span data-stu-id="3f756-148">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="3f756-149">En outre, le code figurant dans le constructeur s'exécute toujours avant tout autre code dans une classe.</span><span class="sxs-lookup"><span data-stu-id="3f756-149">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="3f756-150">Toutefois, vous pouvez créer plusieurs surcharges de constructeur de la même façon que vous le faites pour toute autre méthode.</span><span class="sxs-lookup"><span data-stu-id="3f756-150">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="3f756-151">Pour définir un constructeur pour une classe :</span><span class="sxs-lookup"><span data-stu-id="3f756-151">To define a constructor for a class:</span></span>

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

<span data-ttu-id="3f756-152">Pour plus d’informations, consultez [Constructeurs](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="3f756-152">For more information, see [Constructors](../classes-and-structs/constructors.md).</span></span>

#### <a name="finalizers"></a><span data-ttu-id="3f756-153">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="3f756-153">Finalizers</span></span>

<span data-ttu-id="3f756-154">Un finaliseur est utilisé pour détruire des instances de classes.</span><span class="sxs-lookup"><span data-stu-id="3f756-154">A finalizer is used to destruct instances of classes.</span></span> <span data-ttu-id="3f756-155">Dans .NET, le garbage collector gère automatiquement l’allocation et la libération de mémoire pour les objets managés dans votre application.</span><span class="sxs-lookup"><span data-stu-id="3f756-155">In .NET, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="3f756-156">Toutefois, vous pouvez avoir besoin de finaliseurs pour nettoyer toutes les ressources non managées créées par votre application.</span><span class="sxs-lookup"><span data-stu-id="3f756-156">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="3f756-157">Il ne peut y avoir qu’un seul finaliseur pour une classe.</span><span class="sxs-lookup"><span data-stu-id="3f756-157">There can be only one finalizer for a class.</span></span>

<span data-ttu-id="3f756-158">Pour plus d’informations sur les finaliseurs et les garbage collection dans .NET, consultez [garbage collection](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="3f756-158">For more information about finalizers and garbage collection in .NET, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="3f756-159">Événements</span><span class="sxs-lookup"><span data-stu-id="3f756-159">Events</span></span>

<span data-ttu-id="3f756-160">Les événements permettent à une classe ou un objet de notifier d'autres classes ou objets lorsqu'une situation intéressante se produit.</span><span class="sxs-lookup"><span data-stu-id="3f756-160">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="3f756-161">La classe qui envoie (ou déclenche) l’événement est appelée *éditeur* et les classes qui reçoivent (ou gèrent) l’événement sont appelées *abonnés*.</span><span class="sxs-lookup"><span data-stu-id="3f756-161">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="3f756-162">Pour plus d’informations sur les événements, leur déclenchement et leur gestion, consultez [Événements](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="3f756-162">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="3f756-163">Pour déclarer un événement dans une classe, utilisez le mot clé [event](../../language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="3f756-163">To declare an event in a class, use the [event](../../language-reference/keywords/event.md) keyword.</span></span>
- <span data-ttu-id="3f756-164">Pour déclencher un événement, appelez le délégué d'événement.</span><span class="sxs-lookup"><span data-stu-id="3f756-164">To raise an event, invoke the event delegate.</span></span>
- <span data-ttu-id="3f756-165">Pour vous abonner à un événement, utilisez l'opérateur `+=` ; pour annuler un abonnement à un événement, utilisez l'opérateur `-=`.</span><span class="sxs-lookup"><span data-stu-id="3f756-165">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="3f756-166">Classes imbriquées</span><span class="sxs-lookup"><span data-stu-id="3f756-166">Nested classes</span></span>

<span data-ttu-id="3f756-167">Une classe définie à l’intérieur d’une autre classe est dite *imbriquée*.</span><span class="sxs-lookup"><span data-stu-id="3f756-167">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="3f756-168">Par défaut, une classe imbriquée est privée.</span><span class="sxs-lookup"><span data-stu-id="3f756-168">By default, the nested class is private.</span></span>

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

<span data-ttu-id="3f756-169">Pour créer une instance de la classe imbriquée, utilisez le nom de la classe de conteneur suivi d'un point, puis du nom de la classe imbriquée :</span><span class="sxs-lookup"><span data-stu-id="3f756-169">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="3f756-170">Modificateurs d’accès et niveaux d’accès</span><span class="sxs-lookup"><span data-stu-id="3f756-170">Access modifiers and access levels</span></span>

<span data-ttu-id="3f756-171">Toutes les classes et tous les membres de classe peuvent spécifier le niveau d’accès qu’ils fournissent aux autres classes à l’aide des *modificateurs d’accès*.</span><span class="sxs-lookup"><span data-stu-id="3f756-171">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="3f756-172">Les modificateurs d’accès suivants sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="3f756-172">The following access modifiers are available:</span></span>

| <span data-ttu-id="3f756-173">Modificateur C#</span><span class="sxs-lookup"><span data-stu-id="3f756-173">C# Modifier</span></span> | <span data-ttu-id="3f756-174">Définition</span><span class="sxs-lookup"><span data-stu-id="3f756-174">Definition</span></span> |
|--|--|
| [<span data-ttu-id="3f756-175">public</span><span class="sxs-lookup"><span data-stu-id="3f756-175">public</span></span>](../../language-reference/keywords/public.md) | <span data-ttu-id="3f756-176">Tout autre code du même assembly ou d'un autre assembly qui y fait référence peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="3f756-176">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span> |
| [<span data-ttu-id="3f756-177">priv</span><span class="sxs-lookup"><span data-stu-id="3f756-177">private</span></span>](../../language-reference/keywords/private.md) | <span data-ttu-id="3f756-178">Seul le code de la même classe peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="3f756-178">The type or member can only be accessed by code in the same class.</span></span> |
| [<span data-ttu-id="3f756-179">protected</span><span class="sxs-lookup"><span data-stu-id="3f756-179">protected</span></span>](../../language-reference/keywords/protected.md) | <span data-ttu-id="3f756-180">Seul le code de la même classe ou d'une classe dérivée peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="3f756-180">The type or member can only be accessed by code in the same class or in a derived class.</span></span> |
| [<span data-ttu-id="3f756-181">intérieurs</span><span class="sxs-lookup"><span data-stu-id="3f756-181">internal</span></span>](../../language-reference/keywords/internal.md) | <span data-ttu-id="3f756-182">Tout code du même assembly, mais pas d'un autre assembly, peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="3f756-182">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span> |
| [<span data-ttu-id="3f756-183">protected internal</span><span class="sxs-lookup"><span data-stu-id="3f756-183">protected internal</span></span>](../../language-reference/keywords/protected-internal.md) | <span data-ttu-id="3f756-184">Tout code du même assembly ou toute classe dérivée dans un autre assembly peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="3f756-184">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span> |
| [<span data-ttu-id="3f756-185">protégé privé</span><span class="sxs-lookup"><span data-stu-id="3f756-185">private protected</span></span>](../../language-reference/keywords/private-protected.md) | <span data-ttu-id="3f756-186">Le code de la même classe ou d'une classe dérivée peut accéder au type ou au membre dans l’assembly de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="3f756-186">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span> |

<span data-ttu-id="3f756-187">Pour plus d’informations, consultez [Modificateurs d’accès](../classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="3f756-187">For more information, see [Access Modifiers](../classes-and-structs/access-modifiers.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="3f756-188">Instanciation de classes</span><span class="sxs-lookup"><span data-stu-id="3f756-188">Instantiating classes</span></span>

<span data-ttu-id="3f756-189">Pour créer un objet, vous devez instancier une classe ou créer une instance de classe.</span><span class="sxs-lookup"><span data-stu-id="3f756-189">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```csharp
SampleClass sampleObject = new SampleClass();
```

<span data-ttu-id="3f756-190">Après avoir instancié une classe, vous pouvez assigner des valeurs aux propriétés et champs de l'instance et appeler des méthodes de classe.</span><span class="sxs-lookup"><span data-stu-id="3f756-190">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.SampleMethod();
```

<span data-ttu-id="3f756-191">Pour assigner des valeurs aux propriétés pendant le processus d'instanciation de la classe, utilisez des initialiseurs d'objets :</span><span class="sxs-lookup"><span data-stu-id="3f756-191">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```csharp
// Set a property value.
var sampleObject = new SampleClass
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

<span data-ttu-id="3f756-192">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="3f756-192">For more information, see:</span></span>

- [<span data-ttu-id="3f756-193">nouvel opérateur</span><span class="sxs-lookup"><span data-stu-id="3f756-193">new Operator</span></span>](../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="3f756-194">Initialiseurs d’objets et de collections</span><span class="sxs-lookup"><span data-stu-id="3f756-194">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a><span data-ttu-id="3f756-195">Classes et membres statiques</span><span class="sxs-lookup"><span data-stu-id="3f756-195">Static Classes and Members</span></span>

<span data-ttu-id="3f756-196">Un membre statique de la classe est une propriété, une procédure ou un champ que toutes les instances d’une classe partagent.</span><span class="sxs-lookup"><span data-stu-id="3f756-196">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

<span data-ttu-id="3f756-197">Pour définir un membre statique :</span><span class="sxs-lookup"><span data-stu-id="3f756-197">To define a static member:</span></span>

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

<span data-ttu-id="3f756-198">Pour accéder au membre statique, utilisez le nom de la classe sans créer d’objet de cette classe :</span><span class="sxs-lookup"><span data-stu-id="3f756-198">To access the static member, use the name of the class without creating an object of this class:</span></span>

```csharp
Console.WriteLine(SampleClass.SampleString);
```

<span data-ttu-id="3f756-199">Les classes statiques dans C# ont uniquement des membres statiques et ne peuvent pas être instanciées.</span><span class="sxs-lookup"><span data-stu-id="3f756-199">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="3f756-200">Les membres statiques ne peuvent pas non plus accéder aux propriétés, champs ou méthodes non statiques</span><span class="sxs-lookup"><span data-stu-id="3f756-200">Static members also cannot access non-static  properties, fields or methods</span></span>

<span data-ttu-id="3f756-201">Pour plus d’informations, consultez [static](../../language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="3f756-201">For more information, see: [static](../../language-reference/keywords/static.md).</span></span>

### <a name="anonymous-types"></a><span data-ttu-id="3f756-202">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="3f756-202">Anonymous types</span></span>

<span data-ttu-id="3f756-203">Les types anonymes vous permettent de créer des objets sans écrire de définition de classe pour le type de données.</span><span class="sxs-lookup"><span data-stu-id="3f756-203">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="3f756-204">À la place, le compilateur se charge de générer une classe.</span><span class="sxs-lookup"><span data-stu-id="3f756-204">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="3f756-205">La classe ne possède pas de nom utilisable et contient les propriétés que vous spécifiez lors de la déclaration de l'objet.</span><span class="sxs-lookup"><span data-stu-id="3f756-205">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="3f756-206">Pour créer une instance de type anonyme :</span><span class="sxs-lookup"><span data-stu-id="3f756-206">To create an instance of an anonymous type:</span></span>

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject = new
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

<span data-ttu-id="3f756-207">Pour plus d’informations, consultez [Types anonymes](../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="3f756-207">For more information, see: [Anonymous Types](../classes-and-structs/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="3f756-208">Héritage</span><span class="sxs-lookup"><span data-stu-id="3f756-208">Inheritance</span></span>

<span data-ttu-id="3f756-209">Il vous permet de créer une nouvelle classe qui réutilise, étend et modifie le comportement défini dans une autre classe.</span><span class="sxs-lookup"><span data-stu-id="3f756-209">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="3f756-210">La classe dont les membres sont hérités porte le nom de *classe de base* et la classe qui hérite de ces membres porte le nom de *classe dérivée*.</span><span class="sxs-lookup"><span data-stu-id="3f756-210">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="3f756-211">Toutefois, toutes les classes dans C# héritent implicitement de la classe <xref:System.Object> qui prend en charge la hiérarchie de classes .NET et fournit des services de bas niveau à toutes les classes.</span><span class="sxs-lookup"><span data-stu-id="3f756-211">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="3f756-212">C# ne prend pas en charge l’héritage multiple.</span><span class="sxs-lookup"><span data-stu-id="3f756-212">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="3f756-213">Vous pouvez donc spécifier une seule classe de base pour une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="3f756-213">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="3f756-214">Pour hériter d'une classe de base :</span><span class="sxs-lookup"><span data-stu-id="3f756-214">To inherit from a base class:</span></span>

```csharp
class DerivedClass:BaseClass { }
```

<span data-ttu-id="3f756-215">Par défaut, toutes les classes peuvent être héritées.</span><span class="sxs-lookup"><span data-stu-id="3f756-215">By default all classes can be inherited.</span></span> <span data-ttu-id="3f756-216">Toutefois, vous pouvez spécifier si une classe ne doit pas être utilisée comme classe de base ou créer une classe qui peut être utilisée uniquement comme classe de base.</span><span class="sxs-lookup"><span data-stu-id="3f756-216">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="3f756-217">Pour spécifier qu'une classe ne peut pas être utilisée comme classe de base :</span><span class="sxs-lookup"><span data-stu-id="3f756-217">To specify that a class cannot be used as a base class:</span></span>

```csharp
public sealed class A { }
```

<span data-ttu-id="3f756-218">Pour spécifier qu'une classe peut être utilisée uniquement comme classe de base et ne peut pas être instanciée :</span><span class="sxs-lookup"><span data-stu-id="3f756-218">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```csharp
public abstract class B { }
```

<span data-ttu-id="3f756-219">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="3f756-219">For more information, see:</span></span>

- [<span data-ttu-id="3f756-220">sealed</span><span class="sxs-lookup"><span data-stu-id="3f756-220">sealed</span></span>](../../language-reference/keywords/sealed.md)
- [<span data-ttu-id="3f756-221">abstraction</span><span class="sxs-lookup"><span data-stu-id="3f756-221">abstract</span></span>](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a><span data-ttu-id="3f756-222">Remplacement de membres</span><span class="sxs-lookup"><span data-stu-id="3f756-222">Overriding Members</span></span>

<span data-ttu-id="3f756-223">Par défaut, une classe dérivée hérite de tous les membres de sa classe de base.</span><span class="sxs-lookup"><span data-stu-id="3f756-223">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="3f756-224">Si vous souhaitez modifier le comportement du membre hérité, vous devez le substituer.</span><span class="sxs-lookup"><span data-stu-id="3f756-224">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="3f756-225">Autrement dit, vous pouvez définir une nouvelle implémentation de la méthode, de la propriété ou de l'événement dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="3f756-225">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="3f756-226">Les modificateurs suivants sont utilisés pour contrôler la façon dont les propriétés et les méthodes sont substituées :</span><span class="sxs-lookup"><span data-stu-id="3f756-226">The following modifiers are used to control how properties and methods are overridden:</span></span>

| <span data-ttu-id="3f756-227">Modificateur C#</span><span class="sxs-lookup"><span data-stu-id="3f756-227">C# Modifier</span></span> | <span data-ttu-id="3f756-228">Définition</span><span class="sxs-lookup"><span data-stu-id="3f756-228">Definition</span></span> |
|--|--|
| [<span data-ttu-id="3f756-229">virtuels</span><span class="sxs-lookup"><span data-stu-id="3f756-229">virtual</span></span>](../../language-reference/keywords/virtual.md) | <span data-ttu-id="3f756-230">Autorise la substitution d'un membre de classe dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="3f756-230">Allows a class member to be overridden in a derived class.</span></span> |
| [<span data-ttu-id="3f756-231">remplacer</span><span class="sxs-lookup"><span data-stu-id="3f756-231">override</span></span>](../../language-reference/keywords/override.md) | <span data-ttu-id="3f756-232">Substitue un membre virtuel (substituable) défini dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="3f756-232">Overrides a virtual (overridable) member defined in the base class.</span></span> |
| [<span data-ttu-id="3f756-233">abstraction</span><span class="sxs-lookup"><span data-stu-id="3f756-233">abstract</span></span>](../../language-reference/keywords/abstract.md) | <span data-ttu-id="3f756-234">Requiert qu'un membre de classe soit substitué dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="3f756-234">Requires that a class member to be overridden in the derived class.</span></span> |
| [<span data-ttu-id="3f756-235">Modificateur new</span><span class="sxs-lookup"><span data-stu-id="3f756-235">new Modifier</span></span>](../../language-reference/keywords/new-modifier.md) | <span data-ttu-id="3f756-236">Masque un membre hérité d'une classe de base.</span><span class="sxs-lookup"><span data-stu-id="3f756-236">Hides a member inherited from a base class</span></span> |

## <a name="interfaces"></a><span data-ttu-id="3f756-237">Interfaces</span><span class="sxs-lookup"><span data-stu-id="3f756-237">Interfaces</span></span>

<span data-ttu-id="3f756-238">Tout comme les classes, les interfaces définissent un ensemble de propriétés, méthodes et événements.</span><span class="sxs-lookup"><span data-stu-id="3f756-238">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="3f756-239">Cependant, contrairement aux classes, les interfaces n'assurent pas l'implémentation.</span><span class="sxs-lookup"><span data-stu-id="3f756-239">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="3f756-240">Elles sont implémentées par les classes et définies en tant qu'entités distinctes des classes.</span><span class="sxs-lookup"><span data-stu-id="3f756-240">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="3f756-241">Une interface représente un contrat, dans le sens où une classe qui implémente une interface doit implémenter tous les aspects de cette interface exactement telle qu'elle a été définie.</span><span class="sxs-lookup"><span data-stu-id="3f756-241">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="3f756-242">Pour définir une interface :</span><span class="sxs-lookup"><span data-stu-id="3f756-242">To define an interface:</span></span>

```csharp
interface ISampleInterface
{
    void DoSomething();
}
```

<span data-ttu-id="3f756-243">Pour implémenter une interface dans une classe :</span><span class="sxs-lookup"><span data-stu-id="3f756-243">To implement an interface in a class:</span></span>

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.DoSomething()
    {
        // Method implementation.
    }
}
```

<span data-ttu-id="3f756-244">Pour plus d’informations, consultez l’article Guide de programmation sur les [interfaces](../interfaces/index.md) et l’article de référence sur le langage sur le mot clé [interface](../../language-reference/keywords/interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3f756-244">For more information, see the programming guide article on [Interfaces](../interfaces/index.md) and the language reference article on the [interface](../../language-reference/keywords/interface.md) keyword.</span></span>

## <a name="generics"></a><span data-ttu-id="3f756-245">Génériques</span><span class="sxs-lookup"><span data-stu-id="3f756-245">Generics</span></span>

<span data-ttu-id="3f756-246">Les classes, structures, interfaces et méthodes dans .NET peuvent inclure des *paramètres de type* qui définissent des types d’objets qu’ils peuvent stocker ou utiliser.</span><span class="sxs-lookup"><span data-stu-id="3f756-246">Classes, structures, interfaces, and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="3f756-247">L’exemple le plus commun de génériques est une collection dans laquelle vous pouvez spécifier le type d’objets à stocker dans une collection.</span><span class="sxs-lookup"><span data-stu-id="3f756-247">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="3f756-248">Pour définir une classe générique :</span><span class="sxs-lookup"><span data-stu-id="3f756-248">To define a generic class:</span></span>

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

<span data-ttu-id="3f756-249">Pour créer une instance de classe générique :</span><span class="sxs-lookup"><span data-stu-id="3f756-249">To create an instance of a generic class:</span></span>

```csharp
var sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

<span data-ttu-id="3f756-250">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="3f756-250">For more information, see:</span></span>

- [<span data-ttu-id="3f756-251">Génériques en .NET</span><span class="sxs-lookup"><span data-stu-id="3f756-251">Generics in .NET</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="3f756-252">Génériques - Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3f756-252">Generics - C# Programming Guide</span></span>](../generics/index.md)

## <a name="delegates"></a><span data-ttu-id="3f756-253">Délégués</span><span class="sxs-lookup"><span data-stu-id="3f756-253">Delegates</span></span>

<span data-ttu-id="3f756-254">Un *délégué* est un type qui définit une signature de méthode et peut fournir une référence à toute méthode avec une signature compatible.</span><span class="sxs-lookup"><span data-stu-id="3f756-254">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="3f756-255">Vous pouvez appeler la méthode par le biais du délégué.</span><span class="sxs-lookup"><span data-stu-id="3f756-255">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="3f756-256">Les délégués sont utilisés pour passer des méthodes comme arguments à d'autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="3f756-256">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="3f756-257">Les gestionnaires d'événements sont tout simplement des méthodes appelées par le biais de délégués.</span><span class="sxs-lookup"><span data-stu-id="3f756-257">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="3f756-258">Pour plus d’informations sur l’utilisation de délégués dans la gestion des événements, consultez [Événements](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="3f756-258">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="3f756-259">Pour créer un délégué :</span><span class="sxs-lookup"><span data-stu-id="3f756-259">To create a delegate:</span></span>

```csharp
public delegate void SampleDelegate(string str);
```

<span data-ttu-id="3f756-260">Pour créer une référence à une méthode qui correspond à la signature spécifiée par le délégué :</span><span class="sxs-lookup"><span data-stu-id="3f756-260">To create a reference to a method that matches the signature specified by the delegate:</span></span>

```csharp
class SampleClass
{
    // Method that matches the SampleDelegate signature.
    public static void SampleMethod(string message)
    {
        // Add code here.
    }

    // Method that instantiates the delegate.
    void SampleDelegate()
    {
        SampleDelegate sd = sampleMethod;
        sd("Sample string");
    }
}
```

<span data-ttu-id="3f756-261">Pour plus d’informations, consultez l’article Guide de programmation sur les [délégués](../delegates/index.md) et l’article de référence sur le langage sur le mot clé [Delegate](../../language-reference/builtin-types/reference-types.md) .</span><span class="sxs-lookup"><span data-stu-id="3f756-261">For more information, see the programming guide article on [Delegates](../delegates/index.md) and the language reference article on the [delegate](../../language-reference/builtin-types/reference-types.md) keyword.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f756-262">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f756-262">See also</span></span>

- [<span data-ttu-id="3f756-263">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3f756-263">C# Programming Guide</span></span>](../index.md)
