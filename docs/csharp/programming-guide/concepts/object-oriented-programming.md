---
title: Programmation orientée objet (C#)
ms.date: 07/20/2015
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 8bf02cbfca30d6dfc29c4e5e6c30a5013931e71b
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398062"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="b4763-102">Programmation orientée objet (C#)</span><span class="sxs-lookup"><span data-stu-id="b4763-102">Object-Oriented Programming (C#)</span></span>

<span data-ttu-id="b4763-103">C# offre une prise en charge complète de la programmation orientée objet, y compris l’encapsulation, l’héritage et le polymorphisme.</span><span class="sxs-lookup"><span data-stu-id="b4763-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

<span data-ttu-id="b4763-104">L’*encapsulation* signifie qu’un groupe de propriétés, méthodes et autres membres corrélés est traité comme une unité ou un objet unique.</span><span class="sxs-lookup"><span data-stu-id="b4763-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>

<span data-ttu-id="b4763-105">L’*héritage* décrit la possibilité de créer des classes à partir d’une classe existante.</span><span class="sxs-lookup"><span data-stu-id="b4763-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>

<span data-ttu-id="b4763-106">Le *polymorphisme* signifie que plusieurs classes peuvent être utilisées de manière interchangeable, même si chacune des classes implémente les mêmes propriétés ou méthodes de manière différente.</span><span class="sxs-lookup"><span data-stu-id="b4763-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

<span data-ttu-id="b4763-107">Cette section décrit les concepts suivants :</span><span class="sxs-lookup"><span data-stu-id="b4763-107">This section describes the following concepts:</span></span>

- [<span data-ttu-id="b4763-108">Classes et objets</span><span class="sxs-lookup"><span data-stu-id="b4763-108">Classes and Objects</span></span>](#Classes)

  - [<span data-ttu-id="b4763-109">Membres de classe</span><span class="sxs-lookup"><span data-stu-id="b4763-109">Class Members</span></span>](#Members)

    - [<span data-ttu-id="b4763-110">Propriétés et champs</span><span class="sxs-lookup"><span data-stu-id="b4763-110">Properties and Fields</span></span>](#Properties)

    - [<span data-ttu-id="b4763-111">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b4763-111">Methods</span></span>](#Methods)

    - [<span data-ttu-id="b4763-112">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="b4763-112">Constructors</span></span>](#Constructors)

    - [<span data-ttu-id="b4763-113">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="b4763-113">Finalizers</span></span>](#Finalizers)

    - [<span data-ttu-id="b4763-114">Événements</span><span class="sxs-lookup"><span data-stu-id="b4763-114">Events</span></span>](#Events)

    - [<span data-ttu-id="b4763-115">Classes imbriquées</span><span class="sxs-lookup"><span data-stu-id="b4763-115">Nested Classes</span></span>](#NestedClasses)

  - [<span data-ttu-id="b4763-116">Modificateurs d’accès et niveaux d’accès</span><span class="sxs-lookup"><span data-stu-id="b4763-116">Access Modifiers and Access Levels</span></span>](#AccessModifiers)

  - [<span data-ttu-id="b4763-117">Instanciation de classes</span><span class="sxs-lookup"><span data-stu-id="b4763-117">Instantiating Classes</span></span>](#InstantiatingClasses)

  - [<span data-ttu-id="b4763-118">Classes et membres statiques</span><span class="sxs-lookup"><span data-stu-id="b4763-118">Static Classes and Members</span></span>](#Static)

  - [<span data-ttu-id="b4763-119">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="b4763-119">Anonymous Types</span></span>](#AnonymousTypes)

- [<span data-ttu-id="b4763-120">Héritage</span><span class="sxs-lookup"><span data-stu-id="b4763-120">Inheritance</span></span>](#Inheritance)

  - [<span data-ttu-id="b4763-121">Substitution de membres</span><span class="sxs-lookup"><span data-stu-id="b4763-121">Overriding Members</span></span>](#Overriding)

- [<span data-ttu-id="b4763-122">Interfaces</span><span class="sxs-lookup"><span data-stu-id="b4763-122">Interfaces</span></span>](#Interfaces)

- [<span data-ttu-id="b4763-123">Génériques</span><span class="sxs-lookup"><span data-stu-id="b4763-123">Generics</span></span>](#Generics)

- [<span data-ttu-id="b4763-124">Délégués</span><span class="sxs-lookup"><span data-stu-id="b4763-124">Delegates</span></span>](#Delegates)

## <a name="Classes"></a> <span data-ttu-id="b4763-125">Classes et objets</span><span class="sxs-lookup"><span data-stu-id="b4763-125">Classes and Objects</span></span>

<span data-ttu-id="b4763-126">Les termes *classe* et *objet* sont parfois employés indifféremment, mais en réalité, les classes décrivent le *type* des objets, alors que les objets sont des *instances* utilisables des classes.</span><span class="sxs-lookup"><span data-stu-id="b4763-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="b4763-127">Cela explique pourquoi l’opération de création d’un objet est appelée *instanciation*.</span><span class="sxs-lookup"><span data-stu-id="b4763-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="b4763-128">Si l'on reprend l'analogie avec un plan de construction, une classe est un plan, et un objet est un bâtiment construit à partir de ce plan.</span><span class="sxs-lookup"><span data-stu-id="b4763-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="b4763-129">Pour définir une classe :</span><span class="sxs-lookup"><span data-stu-id="b4763-129">To define a class:</span></span>

```csharp
class SampleClass
{
}
```

<span data-ttu-id="b4763-130">C# fournit également une version basique de classes, appelée *structures*, qui sont utiles pour créer un grand tableau d’objets sans utiliser trop de mémoire pour cette opération.</span><span class="sxs-lookup"><span data-stu-id="b4763-130">C# also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="b4763-131">Pour définir une structure :</span><span class="sxs-lookup"><span data-stu-id="b4763-131">To define a structure:</span></span>

```csharp
struct SampleStruct
{
}
```

<span data-ttu-id="b4763-132">Pour plus d'informations, voir :</span><span class="sxs-lookup"><span data-stu-id="b4763-132">For more information, see:</span></span>

- [<span data-ttu-id="b4763-133">class</span><span class="sxs-lookup"><span data-stu-id="b4763-133">class</span></span>](../../../csharp/language-reference/keywords/class.md)

- [<span data-ttu-id="b4763-134">struct</span><span class="sxs-lookup"><span data-stu-id="b4763-134">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)

### <a name="Members"></a> <span data-ttu-id="b4763-135">Membres de classe</span><span class="sxs-lookup"><span data-stu-id="b4763-135">Class Members</span></span>

<span data-ttu-id="b4763-136">Chaque classe peut avoir différents *membres de classe* : des propriétés qui décrivent les données de classe, des méthodes qui définissent le comportement de classe et des événements qui permettent la communication entre les différents objets et classes.</span><span class="sxs-lookup"><span data-stu-id="b4763-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="Properties"></a> <span data-ttu-id="b4763-137">Propriétés et champs</span><span class="sxs-lookup"><span data-stu-id="b4763-137">Properties and Fields</span></span>

<span data-ttu-id="b4763-138">Les propriétés et les champs sont des informations contenues dans un objet.</span><span class="sxs-lookup"><span data-stu-id="b4763-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="b4763-139">Les champs sont similaires aux variables, car ils peuvent être lus ou définis directement.</span><span class="sxs-lookup"><span data-stu-id="b4763-139">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="b4763-140">Pour définir un champ :</span><span class="sxs-lookup"><span data-stu-id="b4763-140">To define a field:</span></span>

```csharp
class SampleClass
{
    public string sampleField;
}
```

<span data-ttu-id="b4763-141">Les propriétés comportent des procédures Get et Set qui apportent davantage de contrôle sur le mode de définition ou de retour des valeurs.</span><span class="sxs-lookup"><span data-stu-id="b4763-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="b4763-142">C# vous permet de créer un champ privé pour le stockage de la valeur de propriété, ou d’utiliser des propriétés implémentées automatiquement qui créent ce champ de façon automatique en arrière-plan et fournissent la logique de base des procédures de propriété.</span><span class="sxs-lookup"><span data-stu-id="b4763-142">C# allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="b4763-143">Pour définir une propriété implémentée automatiquement :</span><span class="sxs-lookup"><span data-stu-id="b4763-143">To define an auto-implemented property:</span></span>

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

<span data-ttu-id="b4763-144">Si vous devez exécuter des opérations supplémentaires pour la lecture et l'écriture de la valeur de propriété, définissez un champ pour le stockage de la valeur de propriété et fournissez la logique de base pour son stockage et son extraction :</span><span class="sxs-lookup"><span data-stu-id="b4763-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```csharp
class SampleClass
{
    private int _sample;
    public int Sample
    {
        // Return the value stored in a field.
        get { return _sample; }
        // Store the value in the field.
        set { _sample = value; }
    }
}
```

<span data-ttu-id="b4763-145">La plupart des propriétés disposent de méthodes ou de procédures destinées à la fois à définir et à obtenir la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="b4763-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="b4763-146">Toutefois, vous pouvez créer des propriétés en lecture seule ou en écriture seule pour empêcher qu'elles soient modifiées ou lues.</span><span class="sxs-lookup"><span data-stu-id="b4763-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="b4763-147">En C#, vous pouvez omettre la méthode de propriété `get` ou `set`.</span><span class="sxs-lookup"><span data-stu-id="b4763-147">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="b4763-148">Toutefois, les propriétés implémentées automatiquement ne peuvent pas être en lecture seule ni en écriture seule.</span><span class="sxs-lookup"><span data-stu-id="b4763-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="b4763-149">Pour plus d'informations, voir :</span><span class="sxs-lookup"><span data-stu-id="b4763-149">For more information, see:</span></span>

- [<span data-ttu-id="b4763-150">get</span><span class="sxs-lookup"><span data-stu-id="b4763-150">get</span></span>](../../../csharp/language-reference/keywords/get.md)

- [<span data-ttu-id="b4763-151">set</span><span class="sxs-lookup"><span data-stu-id="b4763-151">set</span></span>](../../../csharp/language-reference/keywords/set.md)

#### <a name="Methods"></a> <span data-ttu-id="b4763-152">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b4763-152">Methods</span></span>

<span data-ttu-id="b4763-153">Une *méthode* correspond à une action qu’un objet peut effectuer.</span><span class="sxs-lookup"><span data-stu-id="b4763-153">A *method* is an action that an object can perform.</span></span>

<span data-ttu-id="b4763-154">Pour définir une méthode de classe :</span><span class="sxs-lookup"><span data-stu-id="b4763-154">To define a method of a class:</span></span>

```csharp
class SampleClass
{
    public int sampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

<span data-ttu-id="b4763-155">Une classe peut avoir plusieurs implémentations, ou *surcharges*, de la même méthode qui diffèrent du point de vue du nombre de paramètres ou des types de paramètres.</span><span class="sxs-lookup"><span data-stu-id="b4763-155">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="b4763-156">Pour surcharger une méthode :</span><span class="sxs-lookup"><span data-stu-id="b4763-156">To overload a method:</span></span>

```csharp
public int sampleMethod(string sampleParam) {};
public int sampleMethod(int sampleParam) {}
```

<span data-ttu-id="b4763-157">Dans la plupart des cas, vous déclarez une méthode dans une définition de classe.</span><span class="sxs-lookup"><span data-stu-id="b4763-157">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="b4763-158">Toutefois, C# prend également en charge des *méthodes d’extension*, qui vous permettent d’ajouter des méthodes à une classe existante hors de la définition réelle de la classe.</span><span class="sxs-lookup"><span data-stu-id="b4763-158">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="b4763-159">Pour plus d'informations, voir :</span><span class="sxs-lookup"><span data-stu-id="b4763-159">For more information, see:</span></span>

- [<span data-ttu-id="b4763-160">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b4763-160">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="b4763-161">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="b4763-161">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)

#### <a name="Constructors"></a> <span data-ttu-id="b4763-162">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="b4763-162">Constructors</span></span>

<span data-ttu-id="b4763-163">Les constructeurs sont des méthodes de classe qui s'exécutent automatiquement lorsqu'un objet d'un type donné est créé.</span><span class="sxs-lookup"><span data-stu-id="b4763-163">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="b4763-164">Les constructeurs initialisent habituellement les données membres du nouvel objet.</span><span class="sxs-lookup"><span data-stu-id="b4763-164">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="b4763-165">Un constructeur ne peut s'exécuter qu'une seule fois lorsqu'une classe est créée.</span><span class="sxs-lookup"><span data-stu-id="b4763-165">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="b4763-166">En outre, le code figurant dans le constructeur s'exécute toujours avant tout autre code dans une classe.</span><span class="sxs-lookup"><span data-stu-id="b4763-166">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="b4763-167">Toutefois, vous pouvez créer plusieurs surcharges de constructeur de la même façon que vous le faites pour toute autre méthode.</span><span class="sxs-lookup"><span data-stu-id="b4763-167">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="b4763-168">Pour définir un constructeur pour une classe :</span><span class="sxs-lookup"><span data-stu-id="b4763-168">To define a constructor for a class:</span></span>

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

<span data-ttu-id="b4763-169">Pour plus d'informations, voir :</span><span class="sxs-lookup"><span data-stu-id="b4763-169">For more information, see:</span></span>

<span data-ttu-id="b4763-170">[Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="b4763-170">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span></span>

#### <a name="Finalizers"></a> <span data-ttu-id="b4763-171">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="b4763-171">Finalizers</span></span>

<span data-ttu-id="b4763-172">Les finaliseurs permettent de détruire des instances de classes.</span><span class="sxs-lookup"><span data-stu-id="b4763-172">Finalizers are used to destruct instances of classes.</span></span> <span data-ttu-id="b4763-173">Dans le .NET Framework, le garbage collector gère automatiquement l'allocation et la libération de mémoire pour les objets managés figurant dans votre application.</span><span class="sxs-lookup"><span data-stu-id="b4763-173">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="b4763-174">Toutefois, vous pouvez avoir besoin de finaliseurs pour nettoyer toutes les ressources non managées créées par votre application.</span><span class="sxs-lookup"><span data-stu-id="b4763-174">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="b4763-175">Il ne peut y avoir qu'un seul finaliseur pour une même classe.</span><span class="sxs-lookup"><span data-stu-id="b4763-175">There can be only one finalizers for a class.</span></span>

<span data-ttu-id="b4763-176">Pour plus d’informations sur les finaliseurs et l’opération de garbage collection dans le .NET Framework, consultez [Garbage collection](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="b4763-176">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="Events"></a> <span data-ttu-id="b4763-177">Événements</span><span class="sxs-lookup"><span data-stu-id="b4763-177">Events</span></span>

<span data-ttu-id="b4763-178">Les événements permettent à une classe ou un objet de notifier d'autres classes ou objets lorsqu'une situation intéressante se produit.</span><span class="sxs-lookup"><span data-stu-id="b4763-178">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="b4763-179">La classe qui envoie (ou déclenche) l’événement est appelée *éditeur* et les classes qui reçoivent (ou gèrent) l’événement sont appelées *abonnés*.</span><span class="sxs-lookup"><span data-stu-id="b4763-179">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="b4763-180">Pour plus d’informations sur les événements, leur déclenchement et leur gestion, consultez [Événements](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="b4763-180">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="b4763-181">Pour déclarer un événement dans une classe, utilisez le mot clé [event](../../../csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="b4763-181">To declare an event in a class, use the [event](../../../csharp/language-reference/keywords/event.md) keyword.</span></span>

- <span data-ttu-id="b4763-182">Pour déclencher un événement, appelez le délégué d'événement.</span><span class="sxs-lookup"><span data-stu-id="b4763-182">To raise an event, invoke the event delegate.</span></span>

- <span data-ttu-id="b4763-183">Pour vous abonner à un événement, utilisez l'opérateur `+=` ; pour annuler un abonnement à un événement, utilisez l'opérateur `-=`.</span><span class="sxs-lookup"><span data-stu-id="b4763-183">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>

#### <a name="NestedClasses"></a> <span data-ttu-id="b4763-184">Classes imbriquées</span><span class="sxs-lookup"><span data-stu-id="b4763-184">Nested Classes</span></span>

<span data-ttu-id="b4763-185">Une classe définie à l’intérieur d’une autre classe est dite *imbriquée*.</span><span class="sxs-lookup"><span data-stu-id="b4763-185">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="b4763-186">Par défaut, une classe imbriquée est privée.</span><span class="sxs-lookup"><span data-stu-id="b4763-186">By default, the nested class is private.</span></span>

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

<span data-ttu-id="b4763-187">Pour créer une instance de la classe imbriquée, utilisez le nom de la classe de conteneur suivi d'un point, puis du nom de la classe imbriquée :</span><span class="sxs-lookup"><span data-stu-id="b4763-187">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="AccessModifiers"></a> <span data-ttu-id="b4763-188">Modificateurs d’accès et niveaux d’accès</span><span class="sxs-lookup"><span data-stu-id="b4763-188">Access Modifiers and Access Levels</span></span>

<span data-ttu-id="b4763-189">Toutes les classes et tous les membres de classe peuvent spécifier le niveau d’accès qu’ils fournissent aux autres classes à l’aide des *modificateurs d’accès*.</span><span class="sxs-lookup"><span data-stu-id="b4763-189">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="b4763-190">Les modificateurs d’accès suivants sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="b4763-190">The following access modifiers are available:</span></span>

|<span data-ttu-id="b4763-191">Modificateur C#</span><span class="sxs-lookup"><span data-stu-id="b4763-191">C# Modifier</span></span>|<span data-ttu-id="b4763-192">Définition</span><span class="sxs-lookup"><span data-stu-id="b4763-192">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="b4763-193">public</span><span class="sxs-lookup"><span data-stu-id="b4763-193">public</span></span>](../../../csharp/language-reference/keywords/public.md)|<span data-ttu-id="b4763-194">Tout autre code du même assembly ou d'un autre assembly qui y fait référence peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="b4763-194">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="b4763-195">private</span><span class="sxs-lookup"><span data-stu-id="b4763-195">private</span></span>](../../../csharp/language-reference/keywords/private.md)|<span data-ttu-id="b4763-196">Seul le code de la même classe peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="b4763-196">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="b4763-197">protected</span><span class="sxs-lookup"><span data-stu-id="b4763-197">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)|<span data-ttu-id="b4763-198">Seul le code de la même classe ou d'une classe dérivée peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="b4763-198">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="b4763-199">internal</span><span class="sxs-lookup"><span data-stu-id="b4763-199">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)|<span data-ttu-id="b4763-200">Tout code du même assembly, mais pas d'un autre assembly, peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="b4763-200">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|[<span data-ttu-id="b4763-201">protected internal</span><span class="sxs-lookup"><span data-stu-id="b4763-201">protected internal</span></span>](../../../csharp/language-reference/keywords/protected-internal.md)|<span data-ttu-id="b4763-202">Tout code du même assembly ou toute classe dérivée dans un autre assembly peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="b4763-202">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|
|[<span data-ttu-id="b4763-203">private protected</span><span class="sxs-lookup"><span data-stu-id="b4763-203">private protected</span></span>](../../../csharp/language-reference/keywords/private-protected.md)|<span data-ttu-id="b4763-204">Le code de la même classe ou d'une classe dérivée peut accéder au type ou au membre dans l’assembly de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="b4763-204">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span>|

<span data-ttu-id="b4763-205">Pour plus d’informations, consultez la page [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="b4763-205">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>

### <a name="InstantiatingClasses"></a> <span data-ttu-id="b4763-206">Instanciation de classes</span><span class="sxs-lookup"><span data-stu-id="b4763-206">Instantiating Classes</span></span>

<span data-ttu-id="b4763-207">Pour créer un objet, vous devez instancier une classe ou créer une instance de classe.</span><span class="sxs-lookup"><span data-stu-id="b4763-207">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```csharp
SampleClass sampleObject = new SampleClass();
```

<span data-ttu-id="b4763-208">Après avoir instancié une classe, vous pouvez assigner des valeurs aux propriétés et champs de l'instance et appeler des méthodes de classe.</span><span class="sxs-lookup"><span data-stu-id="b4763-208">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.sampleMethod();
```

<span data-ttu-id="b4763-209">Pour assigner des valeurs aux propriétés pendant le processus d'instanciation de la classe, utilisez des initialiseurs d'objets :</span><span class="sxs-lookup"><span data-stu-id="b4763-209">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```csharp
// Set a property value.
SampleClass sampleObject = new SampleClass
    { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="b4763-210">Pour plus d'informations, voir :</span><span class="sxs-lookup"><span data-stu-id="b4763-210">For more information, see:</span></span>

- [<span data-ttu-id="b4763-211">new, opérateur</span><span class="sxs-lookup"><span data-stu-id="b4763-211">new Operator</span></span>](../../../csharp/language-reference/operators/new-operator.md)

- [<span data-ttu-id="b4763-212">Initialiseurs d’objets et de collections</span><span class="sxs-lookup"><span data-stu-id="b4763-212">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)

### <a name="Static"></a> <span data-ttu-id="b4763-213">Classes et membres statiques</span><span class="sxs-lookup"><span data-stu-id="b4763-213">Static Classes and Members</span></span>

<span data-ttu-id="b4763-214">Un membre statique de la classe est une propriété, une procédure ou un champ que toutes les instances d’une classe partagent.</span><span class="sxs-lookup"><span data-stu-id="b4763-214">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

<span data-ttu-id="b4763-215">Pour définir un membre statique :</span><span class="sxs-lookup"><span data-stu-id="b4763-215">To define a static member:</span></span>

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

<span data-ttu-id="b4763-216">Pour accéder au membre statique, utilisez le nom de la classe sans créer d’objet de cette classe :</span><span class="sxs-lookup"><span data-stu-id="b4763-216">To access the static member, use the name of the class without creating an object of this class:</span></span>

```csharp
Console.WriteLine(SampleClass.SampleString);
```

<span data-ttu-id="b4763-217">Les classes statiques dans C# ont uniquement des membres statiques et ne peuvent pas être instanciées.</span><span class="sxs-lookup"><span data-stu-id="b4763-217">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="b4763-218">Les membres statiques ne peuvent pas non plus accéder aux propriétés, champs ou méthodes non statiques</span><span class="sxs-lookup"><span data-stu-id="b4763-218">Static members also cannot access non-static  properties, fields or methods</span></span>

<span data-ttu-id="b4763-219">Pour plus d’informations, consultez [static](../../../csharp/language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="b4763-219">For more information, see: [static](../../../csharp/language-reference/keywords/static.md).</span></span>

### <a name="AnonymousTypes"></a> <span data-ttu-id="b4763-220">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="b4763-220">Anonymous Types</span></span>

<span data-ttu-id="b4763-221">Les types anonymes vous permettent de créer des objets sans écrire de définition de classe pour le type de données.</span><span class="sxs-lookup"><span data-stu-id="b4763-221">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="b4763-222">À la place, le compilateur se charge de générer une classe.</span><span class="sxs-lookup"><span data-stu-id="b4763-222">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="b4763-223">La classe ne possède pas de nom utilisable et contient les propriétés que vous spécifiez lors de la déclaration de l'objet.</span><span class="sxs-lookup"><span data-stu-id="b4763-223">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="b4763-224">Pour créer une instance de type anonyme :</span><span class="sxs-lookup"><span data-stu-id="b4763-224">To create an instance of an anonymous type:</span></span>

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject =
    new { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="b4763-225">Pour plus d'informations, voir : [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="b4763-225">For more information, see: [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>

## <a name="Inheritance"></a> <span data-ttu-id="b4763-226">Héritage</span><span class="sxs-lookup"><span data-stu-id="b4763-226">Inheritance</span></span>

<span data-ttu-id="b4763-227">Il vous permet de créer une nouvelle classe qui réutilise, étend et modifie le comportement défini dans une autre classe.</span><span class="sxs-lookup"><span data-stu-id="b4763-227">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="b4763-228">La classe dont les membres sont hérités porte le nom de *classe de base* et la classe qui hérite de ces membres porte le nom de *classe dérivée*.</span><span class="sxs-lookup"><span data-stu-id="b4763-228">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="b4763-229">Toutefois, toutes les classes dans C# héritent implicitement de la classe <xref:System.Object> qui prend en charge la hiérarchie de classes .NET et fournit des services de bas niveau à toutes les classes.</span><span class="sxs-lookup"><span data-stu-id="b4763-229">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="b4763-230">C# ne prend pas en charge l’héritage multiple.</span><span class="sxs-lookup"><span data-stu-id="b4763-230">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="b4763-231">Vous pouvez donc spécifier une seule classe de base pour une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="b4763-231">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="b4763-232">Pour hériter d'une classe de base :</span><span class="sxs-lookup"><span data-stu-id="b4763-232">To inherit from a base class:</span></span>

```csharp
class DerivedClass:BaseClass {}
```

<span data-ttu-id="b4763-233">Par défaut, toutes les classes peuvent être héritées.</span><span class="sxs-lookup"><span data-stu-id="b4763-233">By default all classes can be inherited.</span></span> <span data-ttu-id="b4763-234">Toutefois, vous pouvez spécifier si une classe ne doit pas être utilisée comme classe de base ou créer une classe qui peut être utilisée uniquement comme classe de base.</span><span class="sxs-lookup"><span data-stu-id="b4763-234">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="b4763-235">Pour spécifier qu'une classe ne peut pas être utilisée comme classe de base :</span><span class="sxs-lookup"><span data-stu-id="b4763-235">To specify that a class cannot be used as a base class:</span></span>

```csharp
public sealed class A { }
```

<span data-ttu-id="b4763-236">Pour spécifier qu'une classe peut être utilisée uniquement comme classe de base et ne peut pas être instanciée :</span><span class="sxs-lookup"><span data-stu-id="b4763-236">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```csharp
public abstract class B { }
```

<span data-ttu-id="b4763-237">Pour plus d'informations, voir :</span><span class="sxs-lookup"><span data-stu-id="b4763-237">For more information, see:</span></span>

- [<span data-ttu-id="b4763-238">sealed</span><span class="sxs-lookup"><span data-stu-id="b4763-238">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)

- [<span data-ttu-id="b4763-239">abstract</span><span class="sxs-lookup"><span data-stu-id="b4763-239">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)

### <a name="Overriding"></a> <span data-ttu-id="b4763-240">Substitution de membres</span><span class="sxs-lookup"><span data-stu-id="b4763-240">Overriding Members</span></span>

<span data-ttu-id="b4763-241">Par défaut, une classe dérivée hérite de tous les membres de sa classe de base.</span><span class="sxs-lookup"><span data-stu-id="b4763-241">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="b4763-242">Si vous souhaitez modifier le comportement du membre hérité, vous devez le substituer.</span><span class="sxs-lookup"><span data-stu-id="b4763-242">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="b4763-243">Autrement dit, vous pouvez définir une nouvelle implémentation de la méthode, de la propriété ou de l'événement dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="b4763-243">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="b4763-244">Les modificateurs suivants sont utilisés pour contrôler la façon dont les propriétés et les méthodes sont substituées :</span><span class="sxs-lookup"><span data-stu-id="b4763-244">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="b4763-245">Modificateur C#</span><span class="sxs-lookup"><span data-stu-id="b4763-245">C# Modifier</span></span>|<span data-ttu-id="b4763-246">Définition</span><span class="sxs-lookup"><span data-stu-id="b4763-246">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="b4763-247">virtual</span><span class="sxs-lookup"><span data-stu-id="b4763-247">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)|<span data-ttu-id="b4763-248">Autorise la substitution d'un membre de classe dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="b4763-248">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="b4763-249">override</span><span class="sxs-lookup"><span data-stu-id="b4763-249">override</span></span>](../../../csharp/language-reference/keywords/override.md)|<span data-ttu-id="b4763-250">Substitue un membre virtuel (substituable) défini dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="b4763-250">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="b4763-251">abstract</span><span class="sxs-lookup"><span data-stu-id="b4763-251">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)|<span data-ttu-id="b4763-252">Requiert qu'un membre de classe soit substitué dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="b4763-252">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="b4763-253">new, modificateur</span><span class="sxs-lookup"><span data-stu-id="b4763-253">new Modifier</span></span>](../../../csharp/language-reference/keywords/new-modifier.md)|<span data-ttu-id="b4763-254">Masque un membre hérité d'une classe de base.</span><span class="sxs-lookup"><span data-stu-id="b4763-254">Hides a member inherited from a base class</span></span>|

## <a name="Interfaces"></a> <span data-ttu-id="b4763-255">Interfaces</span><span class="sxs-lookup"><span data-stu-id="b4763-255">Interfaces</span></span>

<span data-ttu-id="b4763-256">Tout comme les classes, les interfaces définissent un ensemble de propriétés, méthodes et événements.</span><span class="sxs-lookup"><span data-stu-id="b4763-256">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="b4763-257">Cependant, contrairement aux classes, les interfaces n'assurent pas l'implémentation.</span><span class="sxs-lookup"><span data-stu-id="b4763-257">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="b4763-258">Elles sont implémentées par les classes et définies en tant qu'entités distinctes des classes.</span><span class="sxs-lookup"><span data-stu-id="b4763-258">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="b4763-259">Une interface représente un contrat, dans le sens où une classe qui implémente une interface doit implémenter tous les aspects de cette interface exactement telle qu'elle a été définie.</span><span class="sxs-lookup"><span data-stu-id="b4763-259">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="b4763-260">Pour définir une interface :</span><span class="sxs-lookup"><span data-stu-id="b4763-260">To define an interface:</span></span>

```csharp
interface ISampleInterface
{
    void doSomething();
}
```

<span data-ttu-id="b4763-261">Pour implémenter une interface dans une classe :</span><span class="sxs-lookup"><span data-stu-id="b4763-261">To implement an interface in a class:</span></span>

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.doSomething()
    {
        // Method implementation.
    }
}
```

<span data-ttu-id="b4763-262">Pour plus d'informations, voir :</span><span class="sxs-lookup"><span data-stu-id="b4763-262">For more information, see:</span></span>

[<span data-ttu-id="b4763-263">Interfaces</span><span class="sxs-lookup"><span data-stu-id="b4763-263">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)

[<span data-ttu-id="b4763-264">interface</span><span class="sxs-lookup"><span data-stu-id="b4763-264">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)

## <a name="Generics"></a> <span data-ttu-id="b4763-265">Génériques</span><span class="sxs-lookup"><span data-stu-id="b4763-265">Generics</span></span>

<span data-ttu-id="b4763-266">Les classes, les structs, les interfaces et les méthodes dans le .NET Framework peuvent inclure des *paramètres de type*, qui définissent les types d’objets qu’ils peuvent stocker ou utiliser.</span><span class="sxs-lookup"><span data-stu-id="b4763-266">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="b4763-267">L’exemple le plus commun de génériques est une collection dans laquelle vous pouvez spécifier le type d’objets à stocker dans une collection.</span><span class="sxs-lookup"><span data-stu-id="b4763-267">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="b4763-268">Pour définir une classe générique :</span><span class="sxs-lookup"><span data-stu-id="b4763-268">To define a generic class:</span></span>

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

<span data-ttu-id="b4763-269">Pour créer une instance de classe générique :</span><span class="sxs-lookup"><span data-stu-id="b4763-269">To create an instance of a generic class:</span></span>

```csharp
SampleGeneric<string> sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

<span data-ttu-id="b4763-270">Pour plus d'informations, voir :</span><span class="sxs-lookup"><span data-stu-id="b4763-270">For more information, see:</span></span>

- [<span data-ttu-id="b4763-271">Génériques</span><span class="sxs-lookup"><span data-stu-id="b4763-271">Generics</span></span>](~/docs/standard/generics/index.md)

- [<span data-ttu-id="b4763-272">Génériques</span><span class="sxs-lookup"><span data-stu-id="b4763-272">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)

## <a name="Delegates"></a> <span data-ttu-id="b4763-273">Délégués</span><span class="sxs-lookup"><span data-stu-id="b4763-273">Delegates</span></span>

<span data-ttu-id="b4763-274">Un *délégué* est un type qui définit une signature de méthode et peut fournir une référence à toute méthode avec une signature compatible.</span><span class="sxs-lookup"><span data-stu-id="b4763-274">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="b4763-275">Vous pouvez appeler la méthode par le biais du délégué.</span><span class="sxs-lookup"><span data-stu-id="b4763-275">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="b4763-276">Les délégués sont utilisés pour passer des méthodes comme arguments à d'autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="b4763-276">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="b4763-277">Les gestionnaires d'événements sont tout simplement des méthodes appelées par le biais de délégués.</span><span class="sxs-lookup"><span data-stu-id="b4763-277">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="b4763-278">Pour plus d’informations sur l’utilisation de délégués dans la gestion des événements, consultez [Événements](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="b4763-278">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="b4763-279">Pour créer un délégué :</span><span class="sxs-lookup"><span data-stu-id="b4763-279">To create a delegate:</span></span>

```csharp
public delegate void SampleDelegate(string str);
```

<span data-ttu-id="b4763-280">Pour créer une référence à une méthode qui correspond à la signature spécifiée par le délégué :</span><span class="sxs-lookup"><span data-stu-id="b4763-280">To create a reference to a method that matches the signature specified by the delegate:</span></span>

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

<span data-ttu-id="b4763-281">Pour plus d'informations, voir :</span><span class="sxs-lookup"><span data-stu-id="b4763-281">For more information, see:</span></span>

- [<span data-ttu-id="b4763-282">Délégués</span><span class="sxs-lookup"><span data-stu-id="b4763-282">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)

- [<span data-ttu-id="b4763-283">delegate</span><span class="sxs-lookup"><span data-stu-id="b4763-283">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)

## <a name="see-also"></a><span data-ttu-id="b4763-284">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4763-284">See also</span></span>

- [<span data-ttu-id="b4763-285">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b4763-285">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
