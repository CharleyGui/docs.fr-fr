---
title: Programmation orientée objet (C#)
description: C# fournit une prise en charge complète de la programmation orientée objet, notamment l’abstraction, l’encapsulation, l’héritage et le polymorphisme.
ms.date: 05/13/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 0c5495aefad73a2916ad6e2bd2bf3701d0868f24
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302813"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="6a410-103">Programmation orientée objet (C#)</span><span class="sxs-lookup"><span data-stu-id="6a410-103">Object-Oriented programming (C#)</span></span>

<span data-ttu-id="6a410-104">C# fournit une prise en charge complète de la programmation orientée objet, notamment l’abstraction, l’encapsulation, l’héritage et le polymorphisme.</span><span class="sxs-lookup"><span data-stu-id="6a410-104">C# provides full support for object-oriented programming including abstraction, encapsulation, inheritance, and polymorphism.</span></span>

- <span data-ttu-id="6a410-105">L' *abstraction* signifie masquer les détails inutiles des consommateurs de type.</span><span class="sxs-lookup"><span data-stu-id="6a410-105">*Abstraction* means hiding the unnecessary details from type consumers.</span></span>
- <span data-ttu-id="6a410-106">L’*encapsulation* signifie qu’un groupe de propriétés, méthodes et autres membres corrélés est traité comme une unité ou un objet unique.</span><span class="sxs-lookup"><span data-stu-id="6a410-106">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>
- <span data-ttu-id="6a410-107">L’*héritage* décrit la possibilité de créer des classes à partir d’une classe existante.</span><span class="sxs-lookup"><span data-stu-id="6a410-107">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>
- <span data-ttu-id="6a410-108">Le *polymorphisme* signifie que plusieurs classes peuvent être utilisées de manière interchangeable, même si chacune des classes implémente les mêmes propriétés ou méthodes de manière différente.</span><span class="sxs-lookup"><span data-stu-id="6a410-108">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

## <a name="classes-and-objects"></a><span data-ttu-id="6a410-109">Classes et objets</span><span class="sxs-lookup"><span data-stu-id="6a410-109">Classes and objects</span></span>

<span data-ttu-id="6a410-110">Les termes *classe* et *objet* décrivent respectivement le *type* des objets et les *instances* des classes.</span><span class="sxs-lookup"><span data-stu-id="6a410-110">The terms *class* and *object* describe the *type* of objects, and the *instances* of classes, respectively.</span></span> <span data-ttu-id="6a410-111">Cela explique pourquoi l’opération de création d’un objet est appelée *instanciation*.</span><span class="sxs-lookup"><span data-stu-id="6a410-111">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="6a410-112">Si l'on reprend l'analogie avec un plan de construction, une classe est un plan, et un objet est un bâtiment construit à partir de ce plan.</span><span class="sxs-lookup"><span data-stu-id="6a410-112">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="6a410-113">Pour définir une classe :</span><span class="sxs-lookup"><span data-stu-id="6a410-113">To define a class:</span></span>

```csharp
class SampleClass
{
}
```

<span data-ttu-id="6a410-114">C# fournit également des types appelés *structures* qui sont utiles lorsque vous n’avez pas besoin de prise en charge de l’héritage ou du polymorphisme.</span><span class="sxs-lookup"><span data-stu-id="6a410-114">C# also provides types called *structures* that are useful when you don't need support for inheritance or polymorphism.</span></span> <span data-ttu-id="6a410-115">Pour plus d’informations, consultez [Choosing Between Class and struct](../../../standard/design-guidelines/choosing-between-class-and-struct.md).</span><span class="sxs-lookup"><span data-stu-id="6a410-115">For more information, see [Choosing between class and struct](../../../standard/design-guidelines/choosing-between-class-and-struct.md).</span></span>

<span data-ttu-id="6a410-116">Pour définir une structure :</span><span class="sxs-lookup"><span data-stu-id="6a410-116">To define a structure:</span></span>

```csharp
struct SampleStruct
{
}
```

<span data-ttu-id="6a410-117">Pour plus d’informations, consultez les articles sur les mots clés [Class](../../language-reference/keywords/class.md) et [struct](../../language-reference/builtin-types/struct.md) .</span><span class="sxs-lookup"><span data-stu-id="6a410-117">For more information, see the articles on the [class](../../language-reference/keywords/class.md) and [struct](../../language-reference/builtin-types/struct.md) keywords.</span></span>

### <a name="class-members"></a><span data-ttu-id="6a410-118">Membres de classe</span><span class="sxs-lookup"><span data-stu-id="6a410-118">Class members</span></span>

<span data-ttu-id="6a410-119">Chaque classe peut avoir différents *membres de classe* : des propriétés qui décrivent les données de classe, des méthodes qui définissent le comportement de classe et des événements qui permettent la communication entre les différents objets et classes.</span><span class="sxs-lookup"><span data-stu-id="6a410-119">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="6a410-120">Propriétés et champs</span><span class="sxs-lookup"><span data-stu-id="6a410-120">Properties and fields</span></span>

<span data-ttu-id="6a410-121">Les propriétés et les champs sont des informations contenues dans un objet.</span><span class="sxs-lookup"><span data-stu-id="6a410-121">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="6a410-122">Les champs sont similaires aux variables, car ils peuvent être lus ou définis directement, sous réserve de modificateurs d’accès applicables.</span><span class="sxs-lookup"><span data-stu-id="6a410-122">Fields are like variables because they can be read or set directly, subject to applicable access modifiers.</span></span>

<span data-ttu-id="6a410-123">Pour définir un champ accessible à partir d’instances de la classe :</span><span class="sxs-lookup"><span data-stu-id="6a410-123">To define a field that can be accessed from within instances of the class:</span></span>

```csharp
public class SampleClass
{
    string sampleField;
}
```

<span data-ttu-id="6a410-124">Les propriétés ont des `get` `set` accesseurs et, qui fournissent davantage de contrôle sur la façon dont les valeurs sont définies ou retournées.</span><span class="sxs-lookup"><span data-stu-id="6a410-124">Properties have `get` and `set` accessors, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="6a410-125">C# vous permet de créer un champ privé pour stocker la valeur de la propriété ou d’utiliser des propriétés implémentées automatiquement qui créent ce champ automatiquement en arrière-plan et fournissent la logique de base pour les procédures de propriété.</span><span class="sxs-lookup"><span data-stu-id="6a410-125">C# allows you either to create a private field for storing the property value or use auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="6a410-126">Pour définir une propriété implémentée automatiquement :</span><span class="sxs-lookup"><span data-stu-id="6a410-126">To define an auto-implemented property:</span></span>

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

<span data-ttu-id="6a410-127">Si vous devez exécuter des opérations supplémentaires pour la lecture et l'écriture de la valeur de propriété, définissez un champ pour le stockage de la valeur de propriété et fournissez la logique de base pour son stockage et son extraction :</span><span class="sxs-lookup"><span data-stu-id="6a410-127">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

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

<span data-ttu-id="6a410-128">La plupart des propriétés disposent de méthodes ou de procédures destinées à la fois à définir et à obtenir la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="6a410-128">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="6a410-129">Toutefois, vous pouvez créer des propriétés en lecture seule ou en écriture seule pour empêcher qu'elles soient modifiées ou lues.</span><span class="sxs-lookup"><span data-stu-id="6a410-129">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="6a410-130">En C#, vous pouvez omettre la méthode de propriété `get` ou `set`.</span><span class="sxs-lookup"><span data-stu-id="6a410-130">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="6a410-131">Toutefois, les propriétés implémentées automatiquement ne peuvent pas être en écriture seule.</span><span class="sxs-lookup"><span data-stu-id="6a410-131">However, auto-implemented properties cannot be write-only.</span></span> <span data-ttu-id="6a410-132">Les propriétés implémentées automatiquement en lecture seule peuvent être définies dans les constructeurs de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="6a410-132">Read-only auto-implemented properties can be set in constructors of the containing class.</span></span>

<span data-ttu-id="6a410-133">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="6a410-133">For more information, see:</span></span>

- [<span data-ttu-id="6a410-134">get</span><span class="sxs-lookup"><span data-stu-id="6a410-134">get</span></span>](../../language-reference/keywords/get.md)
- [<span data-ttu-id="6a410-135">set</span><span class="sxs-lookup"><span data-stu-id="6a410-135">set</span></span>](../../language-reference/keywords/set.md)

#### <a name="methods"></a><span data-ttu-id="6a410-136">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6a410-136">Methods</span></span>

<span data-ttu-id="6a410-137">Une *méthode* est une action que peut effectuer un objet.</span><span class="sxs-lookup"><span data-stu-id="6a410-137">A *method* is an action that an object can perform.</span></span>

<span data-ttu-id="6a410-138">Pour définir une méthode de classe :</span><span class="sxs-lookup"><span data-stu-id="6a410-138">To define a method of a class:</span></span>

```csharp
class SampleClass
{
    public int SampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

<span data-ttu-id="6a410-139">Une classe peut avoir plusieurs implémentations, ou *surcharges*, de la même méthode qui diffèrent du point de vue du nombre de paramètres ou des types de paramètres.</span><span class="sxs-lookup"><span data-stu-id="6a410-139">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="6a410-140">Pour surcharger une méthode :</span><span class="sxs-lookup"><span data-stu-id="6a410-140">To overload a method:</span></span>

```csharp
public int SampleMethod(string sampleParam) { }
public int SampleMethod(int sampleParam) { }
```

<span data-ttu-id="6a410-141">Dans la plupart des cas, vous déclarez une méthode dans une définition de classe.</span><span class="sxs-lookup"><span data-stu-id="6a410-141">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="6a410-142">Toutefois, C# prend également en charge des *méthodes d’extension*, qui vous permettent d’ajouter des méthodes à une classe existante hors de la définition réelle de la classe.</span><span class="sxs-lookup"><span data-stu-id="6a410-142">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="6a410-143">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="6a410-143">For more information, see:</span></span>

- [<span data-ttu-id="6a410-144">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6a410-144">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="6a410-145">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="6a410-145">Extension Methods</span></span>](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="6a410-146">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="6a410-146">Constructors</span></span>

<span data-ttu-id="6a410-147">Les constructeurs sont des méthodes de classe qui s'exécutent automatiquement lorsqu'un objet d'un type donné est créé.</span><span class="sxs-lookup"><span data-stu-id="6a410-147">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="6a410-148">Les constructeurs initialisent habituellement les données membres du nouvel objet.</span><span class="sxs-lookup"><span data-stu-id="6a410-148">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="6a410-149">Un constructeur ne peut s'exécuter qu'une seule fois lorsqu'une classe est créée.</span><span class="sxs-lookup"><span data-stu-id="6a410-149">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="6a410-150">En outre, le code figurant dans le constructeur s'exécute toujours avant tout autre code dans une classe.</span><span class="sxs-lookup"><span data-stu-id="6a410-150">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="6a410-151">Toutefois, vous pouvez créer plusieurs surcharges de constructeur de la même façon que vous le faites pour toute autre méthode.</span><span class="sxs-lookup"><span data-stu-id="6a410-151">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="6a410-152">Pour définir un constructeur pour une classe :</span><span class="sxs-lookup"><span data-stu-id="6a410-152">To define a constructor for a class:</span></span>

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

<span data-ttu-id="6a410-153">Pour plus d’informations, consultez [Constructeurs](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="6a410-153">For more information, see [Constructors](../classes-and-structs/constructors.md).</span></span>

#### <a name="finalizers"></a><span data-ttu-id="6a410-154">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="6a410-154">Finalizers</span></span>

<span data-ttu-id="6a410-155">Un finaliseur est utilisé pour détruire des instances de classes.</span><span class="sxs-lookup"><span data-stu-id="6a410-155">A finalizer is used to destruct instances of classes.</span></span> <span data-ttu-id="6a410-156">Dans .NET, le garbage collector gère automatiquement l’allocation et la libération de mémoire pour les objets managés dans votre application.</span><span class="sxs-lookup"><span data-stu-id="6a410-156">In .NET, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="6a410-157">Toutefois, vous pouvez avoir besoin de finaliseurs pour nettoyer toutes les ressources non managées créées par votre application.</span><span class="sxs-lookup"><span data-stu-id="6a410-157">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="6a410-158">Il ne peut y avoir qu’un seul finaliseur pour une classe.</span><span class="sxs-lookup"><span data-stu-id="6a410-158">There can be only one finalizer for a class.</span></span>

<span data-ttu-id="6a410-159">Pour plus d’informations sur les finaliseurs et les garbage collection dans .NET, consultez [garbage collection](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="6a410-159">For more information about finalizers and garbage collection in .NET, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="6a410-160">Événements</span><span class="sxs-lookup"><span data-stu-id="6a410-160">Events</span></span>

<span data-ttu-id="6a410-161">Les événements permettent à une classe ou un objet de notifier d'autres classes ou objets lorsqu'une situation intéressante se produit.</span><span class="sxs-lookup"><span data-stu-id="6a410-161">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="6a410-162">La classe qui envoie (ou déclenche) l’événement est appelée *éditeur* et les classes qui reçoivent (ou gèrent) l’événement sont appelées *abonnés*.</span><span class="sxs-lookup"><span data-stu-id="6a410-162">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="6a410-163">Pour plus d’informations sur les événements, leur déclenchement et leur gestion, consultez [Événements](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="6a410-163">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="6a410-164">Pour déclarer un événement dans une classe, utilisez le mot clé [event](../../language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="6a410-164">To declare an event in a class, use the [event](../../language-reference/keywords/event.md) keyword.</span></span>
- <span data-ttu-id="6a410-165">Pour déclencher un événement, appelez le délégué d'événement.</span><span class="sxs-lookup"><span data-stu-id="6a410-165">To raise an event, invoke the event delegate.</span></span>
- <span data-ttu-id="6a410-166">Pour vous abonner à un événement, utilisez l'opérateur `+=` ; pour annuler un abonnement à un événement, utilisez l'opérateur `-=`.</span><span class="sxs-lookup"><span data-stu-id="6a410-166">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="6a410-167">Classes imbriquées</span><span class="sxs-lookup"><span data-stu-id="6a410-167">Nested classes</span></span>

<span data-ttu-id="6a410-168">Une classe définie à l’intérieur d’une autre classe est dite *imbriquée*.</span><span class="sxs-lookup"><span data-stu-id="6a410-168">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="6a410-169">Par défaut, une classe imbriquée est privée.</span><span class="sxs-lookup"><span data-stu-id="6a410-169">By default, the nested class is private.</span></span>

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

<span data-ttu-id="6a410-170">Pour créer une instance de la classe imbriquée, utilisez le nom de la classe de conteneur suivi d'un point, puis du nom de la classe imbriquée :</span><span class="sxs-lookup"><span data-stu-id="6a410-170">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="6a410-171">Modificateurs d’accès et niveaux d’accès</span><span class="sxs-lookup"><span data-stu-id="6a410-171">Access modifiers and access levels</span></span>

<span data-ttu-id="6a410-172">Toutes les classes et tous les membres de classe peuvent spécifier le niveau d’accès qu’ils fournissent aux autres classes à l’aide des *modificateurs d’accès*.</span><span class="sxs-lookup"><span data-stu-id="6a410-172">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="6a410-173">Les modificateurs d’accès suivants sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="6a410-173">The following access modifiers are available:</span></span>

| <span data-ttu-id="6a410-174">Modificateur C#</span><span class="sxs-lookup"><span data-stu-id="6a410-174">C# Modifier</span></span> | <span data-ttu-id="6a410-175">Définition</span><span class="sxs-lookup"><span data-stu-id="6a410-175">Definition</span></span> |
|--|--|
| [<span data-ttu-id="6a410-176">public</span><span class="sxs-lookup"><span data-stu-id="6a410-176">public</span></span>](../../language-reference/keywords/public.md) | <span data-ttu-id="6a410-177">Tout autre code du même assembly ou d'un autre assembly qui y fait référence peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="6a410-177">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span> |
| [<span data-ttu-id="6a410-178">priv</span><span class="sxs-lookup"><span data-stu-id="6a410-178">private</span></span>](../../language-reference/keywords/private.md) | <span data-ttu-id="6a410-179">Seul le code de la même classe peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="6a410-179">The type or member can only be accessed by code in the same class.</span></span> |
| [<span data-ttu-id="6a410-180">protected</span><span class="sxs-lookup"><span data-stu-id="6a410-180">protected</span></span>](../../language-reference/keywords/protected.md) | <span data-ttu-id="6a410-181">Seul le code de la même classe ou d'une classe dérivée peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="6a410-181">The type or member can only be accessed by code in the same class or in a derived class.</span></span> |
| [<span data-ttu-id="6a410-182">intérieurs</span><span class="sxs-lookup"><span data-stu-id="6a410-182">internal</span></span>](../../language-reference/keywords/internal.md) | <span data-ttu-id="6a410-183">Tout code du même assembly, mais pas d'un autre assembly, peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="6a410-183">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span> |
| [<span data-ttu-id="6a410-184">protected internal</span><span class="sxs-lookup"><span data-stu-id="6a410-184">protected internal</span></span>](../../language-reference/keywords/protected-internal.md) | <span data-ttu-id="6a410-185">Tout code du même assembly ou toute classe dérivée dans un autre assembly peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="6a410-185">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span> |
| [<span data-ttu-id="6a410-186">protégé privé</span><span class="sxs-lookup"><span data-stu-id="6a410-186">private protected</span></span>](../../language-reference/keywords/private-protected.md) | <span data-ttu-id="6a410-187">Le code de la même classe ou d'une classe dérivée peut accéder au type ou au membre dans l’assembly de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="6a410-187">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span> |

<span data-ttu-id="6a410-188">Pour plus d’informations, consultez [Modificateurs d’accès](../classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="6a410-188">For more information, see [Access Modifiers](../classes-and-structs/access-modifiers.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="6a410-189">Instanciation de classes</span><span class="sxs-lookup"><span data-stu-id="6a410-189">Instantiating classes</span></span>

<span data-ttu-id="6a410-190">Pour créer un objet, vous devez instancier une classe ou créer une instance de classe.</span><span class="sxs-lookup"><span data-stu-id="6a410-190">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```csharp
SampleClass sampleObject = new SampleClass();
```

<span data-ttu-id="6a410-191">Après avoir instancié une classe, vous pouvez assigner des valeurs aux propriétés et champs de l'instance et appeler des méthodes de classe.</span><span class="sxs-lookup"><span data-stu-id="6a410-191">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.SampleMethod();
```

<span data-ttu-id="6a410-192">Pour assigner des valeurs aux propriétés pendant le processus d'instanciation de la classe, utilisez des initialiseurs d'objets :</span><span class="sxs-lookup"><span data-stu-id="6a410-192">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```csharp
// Set a property value.
var sampleObject = new SampleClass
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

<span data-ttu-id="6a410-193">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="6a410-193">For more information, see:</span></span>

- [<span data-ttu-id="6a410-194">nouvel opérateur</span><span class="sxs-lookup"><span data-stu-id="6a410-194">new Operator</span></span>](../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="6a410-195">Initialiseurs d’objets et de collections</span><span class="sxs-lookup"><span data-stu-id="6a410-195">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a><span data-ttu-id="6a410-196">Classes et membres statiques</span><span class="sxs-lookup"><span data-stu-id="6a410-196">Static Classes and Members</span></span>

<span data-ttu-id="6a410-197">Un membre statique de la classe est une propriété, une procédure ou un champ que toutes les instances d’une classe partagent.</span><span class="sxs-lookup"><span data-stu-id="6a410-197">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

<span data-ttu-id="6a410-198">Pour définir un membre statique :</span><span class="sxs-lookup"><span data-stu-id="6a410-198">To define a static member:</span></span>

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

<span data-ttu-id="6a410-199">Pour accéder au membre statique, utilisez le nom de la classe sans créer d’objet de cette classe :</span><span class="sxs-lookup"><span data-stu-id="6a410-199">To access the static member, use the name of the class without creating an object of this class:</span></span>

```csharp
Console.WriteLine(SampleClass.SampleString);
```

<span data-ttu-id="6a410-200">Les classes statiques dans C# ont uniquement des membres statiques et ne peuvent pas être instanciées.</span><span class="sxs-lookup"><span data-stu-id="6a410-200">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="6a410-201">Les membres statiques ne peuvent pas non plus accéder aux propriétés, champs ou méthodes non statiques</span><span class="sxs-lookup"><span data-stu-id="6a410-201">Static members also cannot access non-static  properties, fields or methods</span></span>

<span data-ttu-id="6a410-202">Pour plus d’informations, consultez [static](../../language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="6a410-202">For more information, see: [static](../../language-reference/keywords/static.md).</span></span>

### <a name="anonymous-types"></a><span data-ttu-id="6a410-203">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="6a410-203">Anonymous types</span></span>

<span data-ttu-id="6a410-204">Les types anonymes vous permettent de créer des objets sans écrire de définition de classe pour le type de données.</span><span class="sxs-lookup"><span data-stu-id="6a410-204">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="6a410-205">À la place, le compilateur se charge de générer une classe.</span><span class="sxs-lookup"><span data-stu-id="6a410-205">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="6a410-206">La classe ne possède pas de nom utilisable et contient les propriétés que vous spécifiez lors de la déclaration de l'objet.</span><span class="sxs-lookup"><span data-stu-id="6a410-206">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="6a410-207">Pour créer une instance de type anonyme :</span><span class="sxs-lookup"><span data-stu-id="6a410-207">To create an instance of an anonymous type:</span></span>

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject = new
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

<span data-ttu-id="6a410-208">Pour plus d’informations, consultez [Types anonymes](../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="6a410-208">For more information, see: [Anonymous Types](../classes-and-structs/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="6a410-209">Héritage</span><span class="sxs-lookup"><span data-stu-id="6a410-209">Inheritance</span></span>

<span data-ttu-id="6a410-210">Il vous permet de créer une nouvelle classe qui réutilise, étend et modifie le comportement défini dans une autre classe.</span><span class="sxs-lookup"><span data-stu-id="6a410-210">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="6a410-211">La classe dont les membres sont hérités porte le nom de *classe de base* et la classe qui hérite de ces membres porte le nom de *classe dérivée*.</span><span class="sxs-lookup"><span data-stu-id="6a410-211">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="6a410-212">Toutefois, toutes les classes dans C# héritent implicitement de la classe <xref:System.Object> qui prend en charge la hiérarchie de classes .NET et fournit des services de bas niveau à toutes les classes.</span><span class="sxs-lookup"><span data-stu-id="6a410-212">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="6a410-213">C# ne prend pas en charge l’héritage multiple.</span><span class="sxs-lookup"><span data-stu-id="6a410-213">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="6a410-214">Vous pouvez donc spécifier une seule classe de base pour une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="6a410-214">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="6a410-215">Pour hériter d'une classe de base :</span><span class="sxs-lookup"><span data-stu-id="6a410-215">To inherit from a base class:</span></span>

```csharp
class DerivedClass:BaseClass { }
```

<span data-ttu-id="6a410-216">Par défaut, toutes les classes peuvent être héritées.</span><span class="sxs-lookup"><span data-stu-id="6a410-216">By default all classes can be inherited.</span></span> <span data-ttu-id="6a410-217">Toutefois, vous pouvez spécifier si une classe ne doit pas être utilisée comme classe de base ou créer une classe qui peut être utilisée uniquement comme classe de base.</span><span class="sxs-lookup"><span data-stu-id="6a410-217">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="6a410-218">Pour spécifier qu'une classe ne peut pas être utilisée comme classe de base :</span><span class="sxs-lookup"><span data-stu-id="6a410-218">To specify that a class cannot be used as a base class:</span></span>

```csharp
public sealed class A { }
```

<span data-ttu-id="6a410-219">Pour spécifier qu'une classe peut être utilisée uniquement comme classe de base et ne peut pas être instanciée :</span><span class="sxs-lookup"><span data-stu-id="6a410-219">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```csharp
public abstract class B { }
```

<span data-ttu-id="6a410-220">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="6a410-220">For more information, see:</span></span>

- [<span data-ttu-id="6a410-221">sealed</span><span class="sxs-lookup"><span data-stu-id="6a410-221">sealed</span></span>](../../language-reference/keywords/sealed.md)
- [<span data-ttu-id="6a410-222">abstraction</span><span class="sxs-lookup"><span data-stu-id="6a410-222">abstract</span></span>](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a><span data-ttu-id="6a410-223">Remplacement de membres</span><span class="sxs-lookup"><span data-stu-id="6a410-223">Overriding Members</span></span>

<span data-ttu-id="6a410-224">Par défaut, une classe dérivée hérite de tous les membres de sa classe de base.</span><span class="sxs-lookup"><span data-stu-id="6a410-224">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="6a410-225">Si vous souhaitez modifier le comportement du membre hérité, vous devez le substituer.</span><span class="sxs-lookup"><span data-stu-id="6a410-225">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="6a410-226">Autrement dit, vous pouvez définir une nouvelle implémentation de la méthode, de la propriété ou de l'événement dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="6a410-226">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="6a410-227">Les modificateurs suivants sont utilisés pour contrôler la façon dont les propriétés et les méthodes sont substituées :</span><span class="sxs-lookup"><span data-stu-id="6a410-227">The following modifiers are used to control how properties and methods are overridden:</span></span>

| <span data-ttu-id="6a410-228">Modificateur C#</span><span class="sxs-lookup"><span data-stu-id="6a410-228">C# Modifier</span></span> | <span data-ttu-id="6a410-229">Définition</span><span class="sxs-lookup"><span data-stu-id="6a410-229">Definition</span></span> |
|--|--|
| [<span data-ttu-id="6a410-230">virtuels</span><span class="sxs-lookup"><span data-stu-id="6a410-230">virtual</span></span>](../../language-reference/keywords/virtual.md) | <span data-ttu-id="6a410-231">Autorise la substitution d'un membre de classe dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="6a410-231">Allows a class member to be overridden in a derived class.</span></span> |
| [<span data-ttu-id="6a410-232">remplacer</span><span class="sxs-lookup"><span data-stu-id="6a410-232">override</span></span>](../../language-reference/keywords/override.md) | <span data-ttu-id="6a410-233">Substitue un membre virtuel (substituable) défini dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="6a410-233">Overrides a virtual (overridable) member defined in the base class.</span></span> |
| [<span data-ttu-id="6a410-234">abstraction</span><span class="sxs-lookup"><span data-stu-id="6a410-234">abstract</span></span>](../../language-reference/keywords/abstract.md) | <span data-ttu-id="6a410-235">Requiert qu'un membre de classe soit substitué dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="6a410-235">Requires that a class member to be overridden in the derived class.</span></span> |
| [<span data-ttu-id="6a410-236">Modificateur new</span><span class="sxs-lookup"><span data-stu-id="6a410-236">new Modifier</span></span>](../../language-reference/keywords/new-modifier.md) | <span data-ttu-id="6a410-237">Masque un membre hérité d'une classe de base.</span><span class="sxs-lookup"><span data-stu-id="6a410-237">Hides a member inherited from a base class</span></span> |

## <a name="interfaces"></a><span data-ttu-id="6a410-238">Interfaces</span><span class="sxs-lookup"><span data-stu-id="6a410-238">Interfaces</span></span>

<span data-ttu-id="6a410-239">Tout comme les classes, les interfaces définissent un ensemble de propriétés, méthodes et événements.</span><span class="sxs-lookup"><span data-stu-id="6a410-239">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="6a410-240">Cependant, contrairement aux classes, les interfaces n'assurent pas l'implémentation.</span><span class="sxs-lookup"><span data-stu-id="6a410-240">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="6a410-241">Elles sont implémentées par les classes et définies en tant qu'entités distinctes des classes.</span><span class="sxs-lookup"><span data-stu-id="6a410-241">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="6a410-242">Une interface représente un contrat, dans le sens où une classe qui implémente une interface doit implémenter tous les aspects de cette interface exactement telle qu'elle a été définie.</span><span class="sxs-lookup"><span data-stu-id="6a410-242">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="6a410-243">Pour définir une interface :</span><span class="sxs-lookup"><span data-stu-id="6a410-243">To define an interface:</span></span>

```csharp
interface ISampleInterface
{
    void DoSomething();
}
```

<span data-ttu-id="6a410-244">Pour implémenter une interface dans une classe :</span><span class="sxs-lookup"><span data-stu-id="6a410-244">To implement an interface in a class:</span></span>

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.DoSomething()
    {
        // Method implementation.
    }
}
```

<span data-ttu-id="6a410-245">Pour plus d’informations, consultez l’article Guide de programmation sur les [interfaces](../interfaces/index.md) et l’article de référence sur le langage sur le mot clé [interface](../../language-reference/keywords/interface.md) .</span><span class="sxs-lookup"><span data-stu-id="6a410-245">For more information, see the programming guide article on [Interfaces](../interfaces/index.md) and the language reference article on the [interface](../../language-reference/keywords/interface.md) keyword.</span></span>

## <a name="generics"></a><span data-ttu-id="6a410-246">Génériques</span><span class="sxs-lookup"><span data-stu-id="6a410-246">Generics</span></span>

<span data-ttu-id="6a410-247">Les classes, structures, interfaces et méthodes dans .NET peuvent inclure des *paramètres de type* qui définissent des types d’objets qu’ils peuvent stocker ou utiliser.</span><span class="sxs-lookup"><span data-stu-id="6a410-247">Classes, structures, interfaces, and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="6a410-248">L’exemple le plus commun de génériques est une collection dans laquelle vous pouvez spécifier le type d’objets à stocker dans une collection.</span><span class="sxs-lookup"><span data-stu-id="6a410-248">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="6a410-249">Pour définir une classe générique :</span><span class="sxs-lookup"><span data-stu-id="6a410-249">To define a generic class:</span></span>

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

<span data-ttu-id="6a410-250">Pour créer une instance de classe générique :</span><span class="sxs-lookup"><span data-stu-id="6a410-250">To create an instance of a generic class:</span></span>

```csharp
var sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

<span data-ttu-id="6a410-251">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="6a410-251">For more information, see:</span></span>

- [<span data-ttu-id="6a410-252">Génériques en .NET</span><span class="sxs-lookup"><span data-stu-id="6a410-252">Generics in .NET</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="6a410-253">Génériques - Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="6a410-253">Generics - C# Programming Guide</span></span>](../generics/index.md)

## <a name="delegates"></a><span data-ttu-id="6a410-254">Délégués</span><span class="sxs-lookup"><span data-stu-id="6a410-254">Delegates</span></span>

<span data-ttu-id="6a410-255">Un *délégué* est un type qui définit une signature de méthode et peut fournir une référence à toute méthode avec une signature compatible.</span><span class="sxs-lookup"><span data-stu-id="6a410-255">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="6a410-256">Vous pouvez appeler la méthode par le biais du délégué.</span><span class="sxs-lookup"><span data-stu-id="6a410-256">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="6a410-257">Les délégués sont utilisés pour passer des méthodes comme arguments à d'autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="6a410-257">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="6a410-258">Les gestionnaires d'événements sont tout simplement des méthodes appelées par le biais de délégués.</span><span class="sxs-lookup"><span data-stu-id="6a410-258">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="6a410-259">Pour plus d’informations sur l’utilisation de délégués dans la gestion des événements, consultez [Événements](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="6a410-259">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="6a410-260">Pour créer un délégué :</span><span class="sxs-lookup"><span data-stu-id="6a410-260">To create a delegate:</span></span>

```csharp
public delegate void SampleDelegate(string str);
```

<span data-ttu-id="6a410-261">Pour créer une référence à une méthode qui correspond à la signature spécifiée par le délégué :</span><span class="sxs-lookup"><span data-stu-id="6a410-261">To create a reference to a method that matches the signature specified by the delegate:</span></span>

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

<span data-ttu-id="6a410-262">Pour plus d’informations, consultez l’article Guide de programmation sur les [délégués](../delegates/index.md) et l’article de référence sur le langage sur le mot clé [Delegate](../../language-reference/builtin-types/reference-types.md) .</span><span class="sxs-lookup"><span data-stu-id="6a410-262">For more information, see the programming guide article on [Delegates](../delegates/index.md) and the language reference article on the [delegate](../../language-reference/builtin-types/reference-types.md) keyword.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a410-263">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a410-263">See also</span></span>

- [<span data-ttu-id="6a410-264">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="6a410-264">C# Programming Guide</span></span>](../index.md)
