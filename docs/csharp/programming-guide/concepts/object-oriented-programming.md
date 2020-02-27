---
title: Programmation orientée objet (C#)
ms.date: 02/08/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 01d6f55bf0752f902f351675c4596abbb8ac85c2
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627888"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="33ec3-102">Programmation orientée objet (C#)</span><span class="sxs-lookup"><span data-stu-id="33ec3-102">Object-Oriented programming (C#)</span></span>

<span data-ttu-id="33ec3-103">C# offre une prise en charge complète de la programmation orientée objet, y compris l’encapsulation, l’héritage et le polymorphisme.</span><span class="sxs-lookup"><span data-stu-id="33ec3-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

- <span data-ttu-id="33ec3-104">L’*encapsulation* signifie qu’un groupe de propriétés, méthodes et autres membres corrélés est traité comme une unité ou un objet unique.</span><span class="sxs-lookup"><span data-stu-id="33ec3-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>
- <span data-ttu-id="33ec3-105">L’*héritage* décrit la possibilité de créer des classes à partir d’une classe existante.</span><span class="sxs-lookup"><span data-stu-id="33ec3-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>
- <span data-ttu-id="33ec3-106">Le *polymorphisme* signifie que plusieurs classes peuvent être utilisées de manière interchangeable, même si chacune des classes implémente les mêmes propriétés ou méthodes de manière différente.</span><span class="sxs-lookup"><span data-stu-id="33ec3-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

## <a name="classes-and-objects"></a><span data-ttu-id="33ec3-107">Classes et objets</span><span class="sxs-lookup"><span data-stu-id="33ec3-107">Classes and objects</span></span>

<span data-ttu-id="33ec3-108">Les termes *classe* et *objet* décrivent respectivement le *type* des objets et les *instances* des classes.</span><span class="sxs-lookup"><span data-stu-id="33ec3-108">The terms *class* and *object* describe the *type* of objects, and the *instances* of classes, respectively.</span></span> <span data-ttu-id="33ec3-109">Cela explique pourquoi l’opération de création d’un objet est appelée *instanciation*.</span><span class="sxs-lookup"><span data-stu-id="33ec3-109">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="33ec3-110">Si l'on reprend l'analogie avec un plan de construction, une classe est un plan, et un objet est un bâtiment construit à partir de ce plan.</span><span class="sxs-lookup"><span data-stu-id="33ec3-110">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="33ec3-111">Pour définir une classe :</span><span class="sxs-lookup"><span data-stu-id="33ec3-111">To define a class:</span></span>

```csharp
class SampleClass
{
}
```

<span data-ttu-id="33ec3-112">C#fournit également des types appelés *structures* qui sont utiles lorsque vous n’avez pas besoin de prise en charge de l’héritage ou du polymorphisme.</span><span class="sxs-lookup"><span data-stu-id="33ec3-112">C# also provides types called *structures* that are useful when you don't need support for inheritance or polymorphism.</span></span>

<span data-ttu-id="33ec3-113">Pour définir une structure :</span><span class="sxs-lookup"><span data-stu-id="33ec3-113">To define a structure:</span></span>

```csharp
struct SampleStruct
{
}
```

<span data-ttu-id="33ec3-114">Pour plus d’informations, consultez les articles sur les mots clés [Class](../../language-reference/keywords/class.md) et [struct](../../language-reference/builtin-types/struct.md) .</span><span class="sxs-lookup"><span data-stu-id="33ec3-114">For more information, see the articles on the [class](../../language-reference/keywords/class.md) and [struct](../../language-reference/builtin-types/struct.md) keywords.</span></span>

### <a name="class-members"></a><span data-ttu-id="33ec3-115">Membres de classe</span><span class="sxs-lookup"><span data-stu-id="33ec3-115">Class members</span></span>

<span data-ttu-id="33ec3-116">Chaque classe peut avoir différents *membres de classe* : des propriétés qui décrivent les données de classe, des méthodes qui définissent le comportement de classe et des événements qui permettent la communication entre les différents objets et classes.</span><span class="sxs-lookup"><span data-stu-id="33ec3-116">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="33ec3-117">Propriétés et champs</span><span class="sxs-lookup"><span data-stu-id="33ec3-117">Properties and fields</span></span>

<span data-ttu-id="33ec3-118">Les propriétés et les champs sont des informations contenues dans un objet.</span><span class="sxs-lookup"><span data-stu-id="33ec3-118">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="33ec3-119">Les champs sont similaires aux variables, car ils peuvent être lus ou définis directement, sous réserve de modificateurs d’accès applicables.</span><span class="sxs-lookup"><span data-stu-id="33ec3-119">Fields are like variables because they can be read or set directly, subject to applicable access modifiers.</span></span>

<span data-ttu-id="33ec3-120">Pour définir un champ accessible à partir d’instances de la classe :</span><span class="sxs-lookup"><span data-stu-id="33ec3-120">To define a field that can be accessed from within instances of the class:</span></span>

```csharp
public class SampleClass
{
    string sampleField;
}
```

<span data-ttu-id="33ec3-121">Les propriétés ont des accesseurs `get` et `set`, qui offrent davantage de contrôle sur la façon dont les valeurs sont définies ou retournées.</span><span class="sxs-lookup"><span data-stu-id="33ec3-121">Properties have `get` and `set` accessors, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="33ec3-122">C#vous permet de créer un champ privé pour stocker la valeur de la propriété ou d’utiliser des propriétés implémentées automatiquement qui créent ce champ en arrière-plan et fournissent la logique de base des procédures de propriété.</span><span class="sxs-lookup"><span data-stu-id="33ec3-122">C# allows you either to create a private field for storing the property value or use auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="33ec3-123">Pour définir une propriété implémentée automatiquement :</span><span class="sxs-lookup"><span data-stu-id="33ec3-123">To define an auto-implemented property:</span></span>

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

<span data-ttu-id="33ec3-124">Si vous devez exécuter des opérations supplémentaires pour la lecture et l'écriture de la valeur de propriété, définissez un champ pour le stockage de la valeur de propriété et fournissez la logique de base pour son stockage et son extraction :</span><span class="sxs-lookup"><span data-stu-id="33ec3-124">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

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

<span data-ttu-id="33ec3-125">La plupart des propriétés disposent de méthodes ou de procédures destinées à la fois à définir et à obtenir la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="33ec3-125">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="33ec3-126">Toutefois, vous pouvez créer des propriétés en lecture seule ou en écriture seule pour empêcher qu'elles soient modifiées ou lues.</span><span class="sxs-lookup"><span data-stu-id="33ec3-126">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="33ec3-127">En C#, vous pouvez omettre la méthode de propriété `get` ou `set`.</span><span class="sxs-lookup"><span data-stu-id="33ec3-127">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="33ec3-128">Toutefois, les propriétés implémentées automatiquement ne peuvent pas être en écriture seule.</span><span class="sxs-lookup"><span data-stu-id="33ec3-128">However, auto-implemented properties cannot be write-only.</span></span> <span data-ttu-id="33ec3-129">Les propriétés implémentées automatiquement en lecture seule peuvent être définies dans les constructeurs de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="33ec3-129">Read-only auto-implemented properties can be set in constructors of the containing class.</span></span>

<span data-ttu-id="33ec3-130">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="33ec3-130">For more information, see:</span></span>

- [<span data-ttu-id="33ec3-131">get</span><span class="sxs-lookup"><span data-stu-id="33ec3-131">get</span></span>](../../language-reference/keywords/get.md)

- [<span data-ttu-id="33ec3-132">set</span><span class="sxs-lookup"><span data-stu-id="33ec3-132">set</span></span>](../../language-reference/keywords/set.md)

#### <a name="methods"></a><span data-ttu-id="33ec3-133">Méthodes</span><span class="sxs-lookup"><span data-stu-id="33ec3-133">Methods</span></span>

<span data-ttu-id="33ec3-134">Une *méthode* correspond à une action qu’un objet peut effectuer.</span><span class="sxs-lookup"><span data-stu-id="33ec3-134">A *method* is an action that an object can perform.</span></span>

<span data-ttu-id="33ec3-135">Pour définir une méthode de classe :</span><span class="sxs-lookup"><span data-stu-id="33ec3-135">To define a method of a class:</span></span>

```csharp
class SampleClass
{
    public int sampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

<span data-ttu-id="33ec3-136">Une classe peut avoir plusieurs implémentations, ou *surcharges*, de la même méthode qui diffèrent du point de vue du nombre de paramètres ou des types de paramètres.</span><span class="sxs-lookup"><span data-stu-id="33ec3-136">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="33ec3-137">Pour surcharger une méthode :</span><span class="sxs-lookup"><span data-stu-id="33ec3-137">To overload a method:</span></span>

```csharp
public int sampleMethod(string sampleParam) {}
public int sampleMethod(int sampleParam) {}
```

<span data-ttu-id="33ec3-138">Dans la plupart des cas, vous déclarez une méthode dans une définition de classe.</span><span class="sxs-lookup"><span data-stu-id="33ec3-138">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="33ec3-139">Toutefois, C# prend également en charge des *méthodes d’extension*, qui vous permettent d’ajouter des méthodes à une classe existante hors de la définition réelle de la classe.</span><span class="sxs-lookup"><span data-stu-id="33ec3-139">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="33ec3-140">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="33ec3-140">For more information, see:</span></span>

- [<span data-ttu-id="33ec3-141">Méthodes</span><span class="sxs-lookup"><span data-stu-id="33ec3-141">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="33ec3-142">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="33ec3-142">Extension Methods</span></span>](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="33ec3-143">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="33ec3-143">Constructors</span></span>

<span data-ttu-id="33ec3-144">Les constructeurs sont des méthodes de classe qui s'exécutent automatiquement lorsqu'un objet d'un type donné est créé.</span><span class="sxs-lookup"><span data-stu-id="33ec3-144">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="33ec3-145">Les constructeurs initialisent habituellement les données membres du nouvel objet.</span><span class="sxs-lookup"><span data-stu-id="33ec3-145">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="33ec3-146">Un constructeur ne peut s'exécuter qu'une seule fois lorsqu'une classe est créée.</span><span class="sxs-lookup"><span data-stu-id="33ec3-146">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="33ec3-147">En outre, le code figurant dans le constructeur s'exécute toujours avant tout autre code dans une classe.</span><span class="sxs-lookup"><span data-stu-id="33ec3-147">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="33ec3-148">Toutefois, vous pouvez créer plusieurs surcharges de constructeur de la même façon que vous le faites pour toute autre méthode.</span><span class="sxs-lookup"><span data-stu-id="33ec3-148">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="33ec3-149">Pour définir un constructeur pour une classe :</span><span class="sxs-lookup"><span data-stu-id="33ec3-149">To define a constructor for a class:</span></span>

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

<span data-ttu-id="33ec3-150">Pour plus d’informations, consultez [Constructeurs](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="33ec3-150">For more information, see [Constructors](../classes-and-structs/constructors.md).</span></span>

#### <a name="finalizers"></a><span data-ttu-id="33ec3-151">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="33ec3-151">Finalizers</span></span>

<span data-ttu-id="33ec3-152">Les finaliseurs permettent de détruire des instances de classes.</span><span class="sxs-lookup"><span data-stu-id="33ec3-152">Finalizers are used to destruct instances of classes.</span></span> <span data-ttu-id="33ec3-153">Dans le .NET Framework, le garbage collector gère automatiquement l'allocation et la libération de mémoire pour les objets managés figurant dans votre application.</span><span class="sxs-lookup"><span data-stu-id="33ec3-153">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="33ec3-154">Toutefois, vous pouvez avoir besoin de finaliseurs pour nettoyer toutes les ressources non managées créées par votre application.</span><span class="sxs-lookup"><span data-stu-id="33ec3-154">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="33ec3-155">Il ne peut y avoir qu'un seul finaliseur pour une même classe.</span><span class="sxs-lookup"><span data-stu-id="33ec3-155">There can be only one finalizers for a class.</span></span>

<span data-ttu-id="33ec3-156">Pour plus d’informations sur les finaliseurs et l’opération de garbage collection dans le .NET Framework, consultez [Garbage collection](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="33ec3-156">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="33ec3-157">Événements</span><span class="sxs-lookup"><span data-stu-id="33ec3-157">Events</span></span>

<span data-ttu-id="33ec3-158">Les événements permettent à une classe ou un objet de notifier d'autres classes ou objets lorsqu'une situation intéressante se produit.</span><span class="sxs-lookup"><span data-stu-id="33ec3-158">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="33ec3-159">La classe qui envoie (ou déclenche) l’événement est appelée *éditeur* et les classes qui reçoivent (ou gèrent) l’événement sont appelées *abonnés*.</span><span class="sxs-lookup"><span data-stu-id="33ec3-159">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="33ec3-160">Pour plus d’informations sur les événements, leur déclenchement et leur gestion, consultez [Événements](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="33ec3-160">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="33ec3-161">Pour déclarer un événement dans une classe, utilisez le mot clé [event](../../language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="33ec3-161">To declare an event in a class, use the [event](../../language-reference/keywords/event.md) keyword.</span></span>

- <span data-ttu-id="33ec3-162">Pour déclencher un événement, appelez le délégué d'événement.</span><span class="sxs-lookup"><span data-stu-id="33ec3-162">To raise an event, invoke the event delegate.</span></span>

- <span data-ttu-id="33ec3-163">Pour vous abonner à un événement, utilisez l'opérateur `+=` ; pour annuler un abonnement à un événement, utilisez l'opérateur `-=`.</span><span class="sxs-lookup"><span data-stu-id="33ec3-163">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="33ec3-164">Classes imbriquées</span><span class="sxs-lookup"><span data-stu-id="33ec3-164">Nested classes</span></span>

<span data-ttu-id="33ec3-165">Une classe définie à l’intérieur d’une autre classe est dite *imbriquée*.</span><span class="sxs-lookup"><span data-stu-id="33ec3-165">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="33ec3-166">Par défaut, une classe imbriquée est privée.</span><span class="sxs-lookup"><span data-stu-id="33ec3-166">By default, the nested class is private.</span></span>

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

<span data-ttu-id="33ec3-167">Pour créer une instance de la classe imbriquée, utilisez le nom de la classe de conteneur suivi d'un point, puis du nom de la classe imbriquée :</span><span class="sxs-lookup"><span data-stu-id="33ec3-167">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="33ec3-168">Modificateurs d’accès et niveaux d’accès</span><span class="sxs-lookup"><span data-stu-id="33ec3-168">Access modifiers and access levels</span></span>

<span data-ttu-id="33ec3-169">Toutes les classes et tous les membres de classe peuvent spécifier le niveau d’accès qu’ils fournissent aux autres classes à l’aide des *modificateurs d’accès*.</span><span class="sxs-lookup"><span data-stu-id="33ec3-169">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="33ec3-170">Les modificateurs d’accès suivants sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="33ec3-170">The following access modifiers are available:</span></span>

|<span data-ttu-id="33ec3-171">Modificateur C#</span><span class="sxs-lookup"><span data-stu-id="33ec3-171">C# Modifier</span></span>|<span data-ttu-id="33ec3-172">Définition</span><span class="sxs-lookup"><span data-stu-id="33ec3-172">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="33ec3-173">public</span><span class="sxs-lookup"><span data-stu-id="33ec3-173">public</span></span>](../../language-reference/keywords/public.md)|<span data-ttu-id="33ec3-174">Tout autre code du même assembly ou d'un autre assembly qui y fait référence peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="33ec3-174">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="33ec3-175">private</span><span class="sxs-lookup"><span data-stu-id="33ec3-175">private</span></span>](../../language-reference/keywords/private.md)|<span data-ttu-id="33ec3-176">Seul le code de la même classe peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="33ec3-176">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="33ec3-177">protected</span><span class="sxs-lookup"><span data-stu-id="33ec3-177">protected</span></span>](../../language-reference/keywords/protected.md)|<span data-ttu-id="33ec3-178">Seul le code de la même classe ou d'une classe dérivée peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="33ec3-178">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="33ec3-179">internal</span><span class="sxs-lookup"><span data-stu-id="33ec3-179">internal</span></span>](../../language-reference/keywords/internal.md)|<span data-ttu-id="33ec3-180">Tout code du même assembly, mais pas d'un autre assembly, peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="33ec3-180">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|[<span data-ttu-id="33ec3-181">protected internal</span><span class="sxs-lookup"><span data-stu-id="33ec3-181">protected internal</span></span>](../../language-reference/keywords/protected-internal.md)|<span data-ttu-id="33ec3-182">Tout code du même assembly ou toute classe dérivée dans un autre assembly peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="33ec3-182">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|
|[<span data-ttu-id="33ec3-183">private protected</span><span class="sxs-lookup"><span data-stu-id="33ec3-183">private protected</span></span>](../../language-reference/keywords/private-protected.md)|<span data-ttu-id="33ec3-184">Le code de la même classe ou d'une classe dérivée peut accéder au type ou au membre dans l’assembly de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="33ec3-184">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span>|

<span data-ttu-id="33ec3-185">Pour plus d’informations, consultez la page [Modificateurs d’accès](../classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="33ec3-185">For more information, see [Access Modifiers](../classes-and-structs/access-modifiers.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="33ec3-186">Instanciation de classes</span><span class="sxs-lookup"><span data-stu-id="33ec3-186">Instantiating classes</span></span>

<span data-ttu-id="33ec3-187">Pour créer un objet, vous devez instancier une classe ou créer une instance de classe.</span><span class="sxs-lookup"><span data-stu-id="33ec3-187">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```csharp
SampleClass sampleObject = new SampleClass();
```

<span data-ttu-id="33ec3-188">Après avoir instancié une classe, vous pouvez assigner des valeurs aux propriétés et champs de l'instance et appeler des méthodes de classe.</span><span class="sxs-lookup"><span data-stu-id="33ec3-188">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.sampleMethod();
```

<span data-ttu-id="33ec3-189">Pour assigner des valeurs aux propriétés pendant le processus d'instanciation de la classe, utilisez des initialiseurs d'objets :</span><span class="sxs-lookup"><span data-stu-id="33ec3-189">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```csharp
// Set a property value.
SampleClass sampleObject = new SampleClass
    { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="33ec3-190">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="33ec3-190">For more information, see:</span></span>

- [<span data-ttu-id="33ec3-191">Opérateur new</span><span class="sxs-lookup"><span data-stu-id="33ec3-191">new Operator</span></span>](../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="33ec3-192">Initialiseurs d’objets et de collections</span><span class="sxs-lookup"><span data-stu-id="33ec3-192">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a><span data-ttu-id="33ec3-193">Classes et membres statiques</span><span class="sxs-lookup"><span data-stu-id="33ec3-193">Static Classes and Members</span></span>

<span data-ttu-id="33ec3-194">Un membre statique de la classe est une propriété, une procédure ou un champ que toutes les instances d’une classe partagent.</span><span class="sxs-lookup"><span data-stu-id="33ec3-194">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

<span data-ttu-id="33ec3-195">Pour définir un membre statique :</span><span class="sxs-lookup"><span data-stu-id="33ec3-195">To define a static member:</span></span>

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

<span data-ttu-id="33ec3-196">Pour accéder au membre statique, utilisez le nom de la classe sans créer d’objet de cette classe :</span><span class="sxs-lookup"><span data-stu-id="33ec3-196">To access the static member, use the name of the class without creating an object of this class:</span></span>

```csharp
Console.WriteLine(SampleClass.SampleString);
```

<span data-ttu-id="33ec3-197">Les classes statiques dans C# ont uniquement des membres statiques et ne peuvent pas être instanciées.</span><span class="sxs-lookup"><span data-stu-id="33ec3-197">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="33ec3-198">Les membres statiques ne peuvent pas non plus accéder aux propriétés, champs ou méthodes non statiques</span><span class="sxs-lookup"><span data-stu-id="33ec3-198">Static members also cannot access non-static  properties, fields or methods</span></span>

<span data-ttu-id="33ec3-199">Pour plus d’informations, consultez [static](../../language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="33ec3-199">For more information, see: [static](../../language-reference/keywords/static.md).</span></span>

### <a name="anonymous-types"></a><span data-ttu-id="33ec3-200">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="33ec3-200">Anonymous types</span></span>

<span data-ttu-id="33ec3-201">Les types anonymes vous permettent de créer des objets sans écrire de définition de classe pour le type de données.</span><span class="sxs-lookup"><span data-stu-id="33ec3-201">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="33ec3-202">À la place, le compilateur se charge de générer une classe.</span><span class="sxs-lookup"><span data-stu-id="33ec3-202">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="33ec3-203">La classe ne possède pas de nom utilisable et contient les propriétés que vous spécifiez lors de la déclaration de l'objet.</span><span class="sxs-lookup"><span data-stu-id="33ec3-203">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="33ec3-204">Pour créer une instance de type anonyme :</span><span class="sxs-lookup"><span data-stu-id="33ec3-204">To create an instance of an anonymous type:</span></span>

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject =
    new { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="33ec3-205">Pour plus d’informations, consultez [Types anonymes](../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="33ec3-205">For more information, see: [Anonymous Types](../classes-and-structs/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="33ec3-206">Héritage</span><span class="sxs-lookup"><span data-stu-id="33ec3-206">Inheritance</span></span>

<span data-ttu-id="33ec3-207">Il vous permet de créer une nouvelle classe qui réutilise, étend et modifie le comportement défini dans une autre classe.</span><span class="sxs-lookup"><span data-stu-id="33ec3-207">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="33ec3-208">La classe dont les membres sont hérités est la *classe de base* et la classe qui hérite de ces membres s’appelle la *classe dérivée*.</span><span class="sxs-lookup"><span data-stu-id="33ec3-208">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="33ec3-209">Toutefois, toutes les classes dans C# héritent implicitement de la classe <xref:System.Object> qui prend en charge la hiérarchie de classes .NET et fournit des services de bas niveau à toutes les classes.</span><span class="sxs-lookup"><span data-stu-id="33ec3-209">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="33ec3-210">C# ne prend pas en charge l’héritage multiple.</span><span class="sxs-lookup"><span data-stu-id="33ec3-210">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="33ec3-211">Vous pouvez donc spécifier une seule classe de base pour une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="33ec3-211">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="33ec3-212">Pour hériter d'une classe de base :</span><span class="sxs-lookup"><span data-stu-id="33ec3-212">To inherit from a base class:</span></span>

```csharp
class DerivedClass:BaseClass {}
```

<span data-ttu-id="33ec3-213">Par défaut, toutes les classes peuvent être héritées.</span><span class="sxs-lookup"><span data-stu-id="33ec3-213">By default all classes can be inherited.</span></span> <span data-ttu-id="33ec3-214">Toutefois, vous pouvez spécifier si une classe ne doit pas être utilisée comme classe de base ou créer une classe qui peut être utilisée uniquement comme classe de base.</span><span class="sxs-lookup"><span data-stu-id="33ec3-214">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="33ec3-215">Pour spécifier qu'une classe ne peut pas être utilisée comme classe de base :</span><span class="sxs-lookup"><span data-stu-id="33ec3-215">To specify that a class cannot be used as a base class:</span></span>

```csharp
public sealed class A { }
```

<span data-ttu-id="33ec3-216">Pour spécifier qu'une classe peut être utilisée uniquement comme classe de base et ne peut pas être instanciée :</span><span class="sxs-lookup"><span data-stu-id="33ec3-216">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```csharp
public abstract class B { }
```

<span data-ttu-id="33ec3-217">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="33ec3-217">For more information, see:</span></span>

- [<span data-ttu-id="33ec3-218">sealed</span><span class="sxs-lookup"><span data-stu-id="33ec3-218">sealed</span></span>](../../language-reference/keywords/sealed.md)

- [<span data-ttu-id="33ec3-219">abstract</span><span class="sxs-lookup"><span data-stu-id="33ec3-219">abstract</span></span>](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a><span data-ttu-id="33ec3-220">Remplacement de membres</span><span class="sxs-lookup"><span data-stu-id="33ec3-220">Overriding Members</span></span>

<span data-ttu-id="33ec3-221">Par défaut, une classe dérivée hérite de tous les membres de sa classe de base.</span><span class="sxs-lookup"><span data-stu-id="33ec3-221">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="33ec3-222">Si vous souhaitez modifier le comportement du membre hérité, vous devez le substituer.</span><span class="sxs-lookup"><span data-stu-id="33ec3-222">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="33ec3-223">Autrement dit, vous pouvez définir une nouvelle implémentation de la méthode, de la propriété ou de l'événement dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="33ec3-223">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="33ec3-224">Les modificateurs suivants sont utilisés pour contrôler la façon dont les propriétés et les méthodes sont substituées :</span><span class="sxs-lookup"><span data-stu-id="33ec3-224">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="33ec3-225">Modificateur C#</span><span class="sxs-lookup"><span data-stu-id="33ec3-225">C# Modifier</span></span>|<span data-ttu-id="33ec3-226">Définition</span><span class="sxs-lookup"><span data-stu-id="33ec3-226">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="33ec3-227">virtual</span><span class="sxs-lookup"><span data-stu-id="33ec3-227">virtual</span></span>](../../language-reference/keywords/virtual.md)|<span data-ttu-id="33ec3-228">Autorise la substitution d'un membre de classe dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="33ec3-228">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="33ec3-229">override</span><span class="sxs-lookup"><span data-stu-id="33ec3-229">override</span></span>](../../language-reference/keywords/override.md)|<span data-ttu-id="33ec3-230">Substitue un membre virtuel (substituable) défini dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="33ec3-230">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="33ec3-231">abstract</span><span class="sxs-lookup"><span data-stu-id="33ec3-231">abstract</span></span>](../../language-reference/keywords/abstract.md)|<span data-ttu-id="33ec3-232">Requiert qu'un membre de classe soit substitué dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="33ec3-232">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="33ec3-233">new, modificateur</span><span class="sxs-lookup"><span data-stu-id="33ec3-233">new Modifier</span></span>](../../language-reference/keywords/new-modifier.md)|<span data-ttu-id="33ec3-234">Masque un membre hérité d'une classe de base.</span><span class="sxs-lookup"><span data-stu-id="33ec3-234">Hides a member inherited from a base class</span></span>|

## <a name="interfaces"></a><span data-ttu-id="33ec3-235">Interfaces</span><span class="sxs-lookup"><span data-stu-id="33ec3-235">Interfaces</span></span>

<span data-ttu-id="33ec3-236">Tout comme les classes, les interfaces définissent un ensemble de propriétés, méthodes et événements.</span><span class="sxs-lookup"><span data-stu-id="33ec3-236">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="33ec3-237">Cependant, contrairement aux classes, les interfaces n'assurent pas l'implémentation.</span><span class="sxs-lookup"><span data-stu-id="33ec3-237">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="33ec3-238">Elles sont implémentées par les classes et définies en tant qu'entités distinctes des classes.</span><span class="sxs-lookup"><span data-stu-id="33ec3-238">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="33ec3-239">Une interface représente un contrat, dans le sens où une classe qui implémente une interface doit implémenter tous les aspects de cette interface exactement telle qu'elle a été définie.</span><span class="sxs-lookup"><span data-stu-id="33ec3-239">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="33ec3-240">Pour définir une interface :</span><span class="sxs-lookup"><span data-stu-id="33ec3-240">To define an interface:</span></span>

```csharp
interface ISampleInterface
{
    void doSomething();
}
```

<span data-ttu-id="33ec3-241">Pour implémenter une interface dans une classe :</span><span class="sxs-lookup"><span data-stu-id="33ec3-241">To implement an interface in a class:</span></span>

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.doSomething()
    {
        // Method implementation.
    }
}
```

<span data-ttu-id="33ec3-242">Pour plus d’informations, consultez l’article Guide de programmation sur les [interfaces](../interfaces/index.md) et l’article de référence sur le langage sur le mot clé [interface](../../language-reference/keywords/interface.md) .</span><span class="sxs-lookup"><span data-stu-id="33ec3-242">For more information, see the programming guide article on [Interfaces](../interfaces/index.md) and the language reference article on the [interface](../../language-reference/keywords/interface.md) keyword.</span></span>

## <a name="generics"></a><span data-ttu-id="33ec3-243">Génériques</span><span class="sxs-lookup"><span data-stu-id="33ec3-243">Generics</span></span>

<span data-ttu-id="33ec3-244">Les classes, les structs, les interfaces et les méthodes dans le .NET Framework peuvent inclure des *paramètres de type*, qui définissent les types d’objets qu’ils peuvent stocker ou utiliser.</span><span class="sxs-lookup"><span data-stu-id="33ec3-244">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="33ec3-245">L’exemple le plus commun de génériques est une collection dans laquelle vous pouvez spécifier le type d’objets à stocker dans une collection.</span><span class="sxs-lookup"><span data-stu-id="33ec3-245">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="33ec3-246">Pour définir une classe générique :</span><span class="sxs-lookup"><span data-stu-id="33ec3-246">To define a generic class:</span></span>

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

<span data-ttu-id="33ec3-247">Pour créer une instance de classe générique :</span><span class="sxs-lookup"><span data-stu-id="33ec3-247">To create an instance of a generic class:</span></span>

```csharp
SampleGeneric<string> sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

<span data-ttu-id="33ec3-248">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="33ec3-248">For more information, see:</span></span>

- [<span data-ttu-id="33ec3-249">Génériques</span><span class="sxs-lookup"><span data-stu-id="33ec3-249">Generics</span></span>](../../../standard/generics/index.md)

- [<span data-ttu-id="33ec3-250">Génériques</span><span class="sxs-lookup"><span data-stu-id="33ec3-250">Generics</span></span>](../generics/index.md)

## <a name="delegates"></a><span data-ttu-id="33ec3-251">Délégués</span><span class="sxs-lookup"><span data-stu-id="33ec3-251">Delegates</span></span>

<span data-ttu-id="33ec3-252">Un *délégué* est un type qui définit une signature de méthode et peut fournir une référence à toute méthode avec une signature compatible.</span><span class="sxs-lookup"><span data-stu-id="33ec3-252">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="33ec3-253">Vous pouvez appeler la méthode par le biais du délégué.</span><span class="sxs-lookup"><span data-stu-id="33ec3-253">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="33ec3-254">Les délégués sont utilisés pour passer des méthodes comme arguments à d'autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="33ec3-254">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="33ec3-255">Les gestionnaires d'événements sont tout simplement des méthodes appelées par le biais de délégués.</span><span class="sxs-lookup"><span data-stu-id="33ec3-255">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="33ec3-256">Pour plus d’informations sur l’utilisation de délégués dans la gestion des événements, consultez [Événements](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="33ec3-256">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="33ec3-257">Pour créer un délégué :</span><span class="sxs-lookup"><span data-stu-id="33ec3-257">To create a delegate:</span></span>

```csharp
public delegate void SampleDelegate(string str);
```

<span data-ttu-id="33ec3-258">Pour créer une référence à une méthode qui correspond à la signature spécifiée par le délégué :</span><span class="sxs-lookup"><span data-stu-id="33ec3-258">To create a reference to a method that matches the signature specified by the delegate:</span></span>

```csharp
class SampleClass
{
    // Method that matches the SampleDelegate signature.
    public static void sampleMethod(string message)
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

<span data-ttu-id="33ec3-259">Pour plus d’informations, consultez l’article Guide de programmation sur les [délégués](../delegates/index.md) et l’article de référence sur le langage sur le mot clé [Delegate](../../language-reference/builtin-types/reference-types.md) .</span><span class="sxs-lookup"><span data-stu-id="33ec3-259">For more information, see the programming guide article on [Delegates](../delegates/index.md) and the language reference article on the [delegate](../../language-reference/builtin-types/reference-types.md) keyword.</span></span>

## <a name="see-also"></a><span data-ttu-id="33ec3-260">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33ec3-260">See also</span></span>

- [<span data-ttu-id="33ec3-261">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="33ec3-261">C# Programming Guide</span></span>](../index.md)
