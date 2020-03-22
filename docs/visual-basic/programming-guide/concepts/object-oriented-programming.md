---
title: Programmation orientée objet
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: 3739919273f4cdd285d519c414c542f1a82a16d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400686"
---
# <a name="object-oriented-programming-visual-basic"></a><span data-ttu-id="4368c-102">Programmation orientée objet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4368c-102">Object-oriented programming (Visual Basic)</span></span>

<span data-ttu-id="4368c-103">Visual Basic fournit un soutien complet pour la programmation orientée objet, y compris l’encapsulation, l’héritage et le polymorphisme.</span><span class="sxs-lookup"><span data-stu-id="4368c-103">Visual Basic provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

 <span data-ttu-id="4368c-104">L’*encapsulation* signifie qu’un groupe de propriétés, méthodes et autres membres corrélés est traité comme une unité ou un objet unique.</span><span class="sxs-lookup"><span data-stu-id="4368c-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>

 <span data-ttu-id="4368c-105">L’*héritage* décrit la possibilité de créer des classes à partir d’une classe existante.</span><span class="sxs-lookup"><span data-stu-id="4368c-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>

 <span data-ttu-id="4368c-106">Le *polymorphisme* signifie que plusieurs classes peuvent être utilisées de manière interchangeable, même si chacune des classes implémente les mêmes propriétés ou méthodes de manière différente.</span><span class="sxs-lookup"><span data-stu-id="4368c-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

 <span data-ttu-id="4368c-107">Cette section décrit les concepts suivants :</span><span class="sxs-lookup"><span data-stu-id="4368c-107">This section describes the following concepts:</span></span>

- [<span data-ttu-id="4368c-108">Classes et objets</span><span class="sxs-lookup"><span data-stu-id="4368c-108">Classes and objects</span></span>](#classes-and-objects)
  - [<span data-ttu-id="4368c-109">Membres de classe</span><span class="sxs-lookup"><span data-stu-id="4368c-109">Class members</span></span>](#class-members)
    - [<span data-ttu-id="4368c-110">Propriétés et champs</span><span class="sxs-lookup"><span data-stu-id="4368c-110">Properties and fields</span></span>](#properties-and-fields)
    - [<span data-ttu-id="4368c-111">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4368c-111">Methods</span></span>](#methods)
    - [<span data-ttu-id="4368c-112">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="4368c-112">Constructors</span></span>](#constructors)
    - [<span data-ttu-id="4368c-113">Destructeurs</span><span class="sxs-lookup"><span data-stu-id="4368c-113">Destructors</span></span>](#destructors)
    - [<span data-ttu-id="4368c-114">Événements</span><span class="sxs-lookup"><span data-stu-id="4368c-114">Events</span></span>](#events)
    - [<span data-ttu-id="4368c-115">Classes imbriquées</span><span class="sxs-lookup"><span data-stu-id="4368c-115">Nested classes</span></span>](#nested-classes)
  - [<span data-ttu-id="4368c-116">Modifier d’accès et niveaux d’accès</span><span class="sxs-lookup"><span data-stu-id="4368c-116">Access modifiers and access levels</span></span>](#access-modifiers-and-access-levels)
    - [<span data-ttu-id="4368c-117">Cours instantanés</span><span class="sxs-lookup"><span data-stu-id="4368c-117">Instantiating classes</span></span>](#instantiating-classes)
    - [<span data-ttu-id="4368c-118">Classes et membres partagés</span><span class="sxs-lookup"><span data-stu-id="4368c-118">Shared classes and members</span></span>](#shared-classes-and-members)
    - [<span data-ttu-id="4368c-119">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="4368c-119">Anonymous types</span></span>](#anonymous-types)
- [<span data-ttu-id="4368c-120">Héritage</span><span class="sxs-lookup"><span data-stu-id="4368c-120">Inheritance</span></span>](#inheritance)
  - [<span data-ttu-id="4368c-121">Membres dominants</span><span class="sxs-lookup"><span data-stu-id="4368c-121">Overriding members</span></span>](#overriding-members)
- [<span data-ttu-id="4368c-122">Interfaces</span><span class="sxs-lookup"><span data-stu-id="4368c-122">Interfaces</span></span>](#interfaces)
- [<span data-ttu-id="4368c-123">Génériques</span><span class="sxs-lookup"><span data-stu-id="4368c-123">Generics</span></span>](#generics)
- [<span data-ttu-id="4368c-124">Délégués</span><span class="sxs-lookup"><span data-stu-id="4368c-124">Delegates</span></span>](#delegates)

## <a name="classes-and-objects"></a><span data-ttu-id="4368c-125">Classes et objets</span><span class="sxs-lookup"><span data-stu-id="4368c-125">Classes and objects</span></span>

<span data-ttu-id="4368c-126">Les termes *classe* et *objet* sont parfois employés indifféremment, mais en réalité, les classes décrivent le *type* des objets, alors que les objets sont des *instances* utilisables des classes.</span><span class="sxs-lookup"><span data-stu-id="4368c-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="4368c-127">Cela explique pourquoi l’opération de création d’un objet est appelée *instanciation*.</span><span class="sxs-lookup"><span data-stu-id="4368c-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="4368c-128">Si l'on reprend l'analogie avec un plan de construction, une classe est un plan, et un objet est un bâtiment construit à partir de ce plan.</span><span class="sxs-lookup"><span data-stu-id="4368c-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="4368c-129">Pour définir une classe :</span><span class="sxs-lookup"><span data-stu-id="4368c-129">To define a class:</span></span>

```vb
Class SampleClass
End Class
```

<span data-ttu-id="4368c-130">Visual Basic fournit également une version légère des classes *appelées structures* qui sont utiles lorsque vous avez besoin de créer un grand éventail d’objets et ne veulent pas consommer trop de mémoire pour cela.</span><span class="sxs-lookup"><span data-stu-id="4368c-130">Visual Basic also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="4368c-131">Pour définir une structure :</span><span class="sxs-lookup"><span data-stu-id="4368c-131">To define a structure:</span></span>

```vb
Structure SampleStructure
End Structure
```

<span data-ttu-id="4368c-132">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="4368c-132">For more information, see:</span></span>

- [<span data-ttu-id="4368c-133">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="4368c-133">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="4368c-134">Structure, instruction</span><span class="sxs-lookup"><span data-stu-id="4368c-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a><span data-ttu-id="4368c-135">Membres de classe</span><span class="sxs-lookup"><span data-stu-id="4368c-135">Class members</span></span>

<span data-ttu-id="4368c-136">Chaque classe peut avoir différents *membres de classe* : des propriétés qui décrivent les données de classe, des méthodes qui définissent le comportement de classe et des événements qui permettent la communication entre les différents objets et classes.</span><span class="sxs-lookup"><span data-stu-id="4368c-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="4368c-137">Propriétés et champs</span><span class="sxs-lookup"><span data-stu-id="4368c-137">Properties and fields</span></span>

<span data-ttu-id="4368c-138">Les propriétés et les champs sont des informations contenues dans un objet.</span><span class="sxs-lookup"><span data-stu-id="4368c-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="4368c-139">Les champs sont similaires aux variables, car ils peuvent être lus ou définis directement.</span><span class="sxs-lookup"><span data-stu-id="4368c-139">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="4368c-140">Pour définir un champ :</span><span class="sxs-lookup"><span data-stu-id="4368c-140">To define a field:</span></span>

```vb
Class SampleClass
    Public SampleField As String
End Class
```

<span data-ttu-id="4368c-141">Les propriétés comportent des procédures Get et Set qui apportent davantage de contrôle sur le mode de définition ou de retour des valeurs.</span><span class="sxs-lookup"><span data-stu-id="4368c-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="4368c-142">Visual Basic vous permet soit de créer un champ privé pour stocker la valeur de la propriété ou d’utiliser ce que l’on appelle les propriétés auto-mises en œuvre qui créent ce champ automatiquement dans les coulisses et de fournir la logique de base pour les procédures de propriété.</span><span class="sxs-lookup"><span data-stu-id="4368c-142">Visual Basic allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="4368c-143">Pour définir une propriété implémentée automatiquement :</span><span class="sxs-lookup"><span data-stu-id="4368c-143">To define an auto-implemented property:</span></span>

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

<span data-ttu-id="4368c-144">Si vous devez exécuter des opérations supplémentaires pour la lecture et l'écriture de la valeur de propriété, définissez un champ pour le stockage de la valeur de propriété et fournissez la logique de base pour son stockage et son extraction :</span><span class="sxs-lookup"><span data-stu-id="4368c-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```vb
Class SampleClass
    Private m_Sample As String
    Public Property Sample() As String
        Get
            ' Return the value stored in the field.
            Return m_Sample
        End Get
        Set(ByVal Value As String)
            ' Store the value in the field.
            m_Sample = Value
        End Set
    End Property
End Class
```

<span data-ttu-id="4368c-145">La plupart des propriétés disposent de méthodes ou de procédures destinées à la fois à définir et à obtenir la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="4368c-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="4368c-146">Toutefois, vous pouvez créer des propriétés en lecture seule ou en écriture seule pour empêcher qu'elles soient modifiées ou lues.</span><span class="sxs-lookup"><span data-stu-id="4368c-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="4368c-147">En Visual Basic, vous pouvez utiliser les mots clés `ReadOnly` et `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="4368c-147">In Visual Basic you can use `ReadOnly` and `WriteOnly` keywords.</span></span> <span data-ttu-id="4368c-148">Toutefois, les propriétés implémentées automatiquement ne peuvent pas être en lecture seule ni en écriture seule.</span><span class="sxs-lookup"><span data-stu-id="4368c-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="4368c-149">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="4368c-149">For more information, see:</span></span>

- [<span data-ttu-id="4368c-150">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="4368c-150">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="4368c-151">Get, instruction</span><span class="sxs-lookup"><span data-stu-id="4368c-151">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="4368c-152">Définir l’énoncé</span><span class="sxs-lookup"><span data-stu-id="4368c-152">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="4368c-153">Readonly</span><span class="sxs-lookup"><span data-stu-id="4368c-153">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="4368c-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="4368c-154">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)

#### <a name="methods"></a><span data-ttu-id="4368c-155">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4368c-155">Methods</span></span>

 <span data-ttu-id="4368c-156">Une *méthode* est une action que peut effectuer un objet.</span><span class="sxs-lookup"><span data-stu-id="4368c-156">A *method* is an action that an object can perform.</span></span>

> [!NOTE]
> <span data-ttu-id="4368c-157">En Visual Basic, il existe deux façons de créer une méthode : l'instruction `Sub` est utilisée si la méthode ne retourne pas de valeur ; l'instruction `Function` est utilisée si une méthode retourne une valeur.</span><span class="sxs-lookup"><span data-stu-id="4368c-157">In Visual Basic, there are two ways to create a method: the `Sub` statement is used if the method does not return a value; the `Function` statement is used if a method returns a value.</span></span>

<span data-ttu-id="4368c-158">Pour définir une méthode de classe :</span><span class="sxs-lookup"><span data-stu-id="4368c-158">To define a method of a class:</span></span>

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

<span data-ttu-id="4368c-159">Une classe peut avoir plusieurs implémentations, ou *surcharges*, de la même méthode qui diffèrent du point de vue du nombre de paramètres ou des types de paramètres.</span><span class="sxs-lookup"><span data-stu-id="4368c-159">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="4368c-160">Pour surcharger une méthode :</span><span class="sxs-lookup"><span data-stu-id="4368c-160">To overload a method:</span></span>

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

<span data-ttu-id="4368c-161">Dans la plupart des cas, vous déclarez une méthode dans une définition de classe.</span><span class="sxs-lookup"><span data-stu-id="4368c-161">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="4368c-162">Cependant, Visual Basic prend également en charge les *méthodes d’extension* qui vous permettent d’ajouter des méthodes à une classe existante en dehors de la définition réelle de la classe.</span><span class="sxs-lookup"><span data-stu-id="4368c-162">However, Visual Basic also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="4368c-163">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="4368c-163">For more information, see:</span></span>

- [<span data-ttu-id="4368c-164">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="4368c-164">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="4368c-165">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="4368c-165">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="4368c-166">Overloads</span><span class="sxs-lookup"><span data-stu-id="4368c-166">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="4368c-167">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="4368c-167">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="4368c-168">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="4368c-168">Constructors</span></span>

<span data-ttu-id="4368c-169">Les constructeurs sont des méthodes de classe qui s'exécutent automatiquement lorsqu'un objet d'un type donné est créé.</span><span class="sxs-lookup"><span data-stu-id="4368c-169">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="4368c-170">Les constructeurs initialisent habituellement les données membres du nouvel objet.</span><span class="sxs-lookup"><span data-stu-id="4368c-170">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="4368c-171">Un constructeur ne peut s'exécuter qu'une seule fois lorsqu'une classe est créée.</span><span class="sxs-lookup"><span data-stu-id="4368c-171">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="4368c-172">En outre, le code figurant dans le constructeur s'exécute toujours avant tout autre code dans une classe.</span><span class="sxs-lookup"><span data-stu-id="4368c-172">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="4368c-173">Toutefois, vous pouvez créer plusieurs surcharges de constructeur de la même façon que vous le faites pour toute autre méthode.</span><span class="sxs-lookup"><span data-stu-id="4368c-173">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="4368c-174">Pour définir un constructeur pour une classe :</span><span class="sxs-lookup"><span data-stu-id="4368c-174">To define a constructor for a class:</span></span>

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

<span data-ttu-id="4368c-175">Pour plus d’informations, voir: [Durée de vie de l’objet: Comment les objets sont créés et détruits](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="4368c-175">For more information, see: [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

#### <a name="destructors"></a><span data-ttu-id="4368c-176">Destructeurs</span><span class="sxs-lookup"><span data-stu-id="4368c-176">Destructors</span></span>

<span data-ttu-id="4368c-177">Les destructeurs permettent de détruire les instances des classes.</span><span class="sxs-lookup"><span data-stu-id="4368c-177">Destructors are used to destruct instances of classes.</span></span> <span data-ttu-id="4368c-178">Dans le .NET Framework, le garbage collector gère automatiquement l'allocation et la libération de mémoire pour les objets managés figurant dans votre application.</span><span class="sxs-lookup"><span data-stu-id="4368c-178">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="4368c-179">Toutefois, vous pouvez avoir besoin de destructeurs pour nettoyer toutes les ressources non managées créées par votre application.</span><span class="sxs-lookup"><span data-stu-id="4368c-179">However, you may still need destructors to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="4368c-180">Il ne peut y avoir qu'un seul destructeur pour une même classe.</span><span class="sxs-lookup"><span data-stu-id="4368c-180">There can be only one destructor for a class.</span></span>

<span data-ttu-id="4368c-181">Pour plus d’informations sur les destructeurs et l’opération de garbage collection dans le .NET Framework, consultez [Garbage collection](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="4368c-181">For more information about destructors and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="4368c-182">Événements</span><span class="sxs-lookup"><span data-stu-id="4368c-182">Events</span></span>

<span data-ttu-id="4368c-183">Les événements permettent à une classe ou un objet de notifier d'autres classes ou objets lorsqu'une situation intéressante se produit.</span><span class="sxs-lookup"><span data-stu-id="4368c-183">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="4368c-184">La classe qui envoie (ou relance) l’événement s’appelle *l’éditeur* et les classes qui reçoivent (ou manipulent) l’événement sont appelés *abonnés*.</span><span class="sxs-lookup"><span data-stu-id="4368c-184">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="4368c-185">Pour plus d’informations sur les événements, leur déclenchement et leur gestion, consultez [Événements](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="4368c-185">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="4368c-186">Pour déclarer les événements, utilisez [l’énoncé d’événement](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4368c-186">To declare events, use the [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>

- <span data-ttu-id="4368c-187">Pour soulever des événements, utilisez [l’énoncé RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4368c-187">To raise events, use the [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span></span>

- <span data-ttu-id="4368c-188">Pour spécifier les gestionnaires d’événements en utilisant une manière déclarative, utilisez la déclaration [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) et la clause [Poignées.](../../../visual-basic/language-reference/statements/handles-clause.md)</span><span class="sxs-lookup"><span data-stu-id="4368c-188">To specify event handlers using a declarative way, use the [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) statement and the [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span>

- <span data-ttu-id="4368c-189">Pour être en mesure d’ajouter, de supprimer et de modifier dynamiquement le gestionnaire d’événements associé à un événement, utilisez [l’instruction AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md) et [l’énoncé RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md) avec [l’opérateur AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="4368c-189">To be able to dynamically add, remove, and change the event handler associated with an event, use the [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) and [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) together with the [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md).</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="4368c-190">Classes imbriquées</span><span class="sxs-lookup"><span data-stu-id="4368c-190">Nested classes</span></span>

<span data-ttu-id="4368c-191">Une classe définie à l’intérieur d’une autre classe est dite *imbriquée*.</span><span class="sxs-lookup"><span data-stu-id="4368c-191">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="4368c-192">Par défaut, une classe imbriquée est privée.</span><span class="sxs-lookup"><span data-stu-id="4368c-192">By default, the nested class is private.</span></span>

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

<span data-ttu-id="4368c-193">Pour créer une instance de la classe imbriquée, utilisez le nom de la classe de conteneur suivi d'un point, puis du nom de la classe imbriquée :</span><span class="sxs-lookup"><span data-stu-id="4368c-193">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="4368c-194">Modifier d’accès et niveaux d’accès</span><span class="sxs-lookup"><span data-stu-id="4368c-194">Access modifiers and access levels</span></span>

<span data-ttu-id="4368c-195">Toutes les classes et tous les membres de classe peuvent spécifier le niveau d’accès qu’ils fournissent aux autres classes à l’aide des *modificateurs d’accès*.</span><span class="sxs-lookup"><span data-stu-id="4368c-195">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="4368c-196">Les modificateurs d’accès suivants sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="4368c-196">The following access modifiers are available:</span></span>

|<span data-ttu-id="4368c-197">Modificateur Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4368c-197">Visual Basic Modifier</span></span>|<span data-ttu-id="4368c-198">Définition</span><span class="sxs-lookup"><span data-stu-id="4368c-198">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="4368c-199">Public</span><span class="sxs-lookup"><span data-stu-id="4368c-199">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)|<span data-ttu-id="4368c-200">Tout autre code du même assembly ou d'un autre assembly qui y fait référence peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="4368c-200">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="4368c-201">Privé</span><span class="sxs-lookup"><span data-stu-id="4368c-201">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)|<span data-ttu-id="4368c-202">Seul le code de la même classe peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="4368c-202">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="4368c-203">Protégé</span><span class="sxs-lookup"><span data-stu-id="4368c-203">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)|<span data-ttu-id="4368c-204">Seul le code de la même classe ou d'une classe dérivée peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="4368c-204">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="4368c-205">Ami</span><span class="sxs-lookup"><span data-stu-id="4368c-205">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)|<span data-ttu-id="4368c-206">Tout code du même assembly, mais pas d'un autre assembly, peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="4368c-206">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|`Protected Friend`|<span data-ttu-id="4368c-207">Tout code du même assembly ou toute classe dérivée dans un autre assembly peut accéder au type ou au membre.</span><span class="sxs-lookup"><span data-stu-id="4368c-207">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|

<span data-ttu-id="4368c-208">Pour plus d’informations, voir [niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="4368c-208">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="4368c-209">Cours instantanés</span><span class="sxs-lookup"><span data-stu-id="4368c-209">Instantiating classes</span></span>

<span data-ttu-id="4368c-210">Pour créer un objet, vous devez instancier une classe ou créer une instance de classe.</span><span class="sxs-lookup"><span data-stu-id="4368c-210">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```vb
Dim sampleObject as New SampleClass()
```

<span data-ttu-id="4368c-211">Après avoir instancié une classe, vous pouvez assigner des valeurs aux propriétés et champs de l'instance et appeler des méthodes de classe.</span><span class="sxs-lookup"><span data-stu-id="4368c-211">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

<span data-ttu-id="4368c-212">Pour assigner des valeurs aux propriétés pendant le processus d'instanciation de la classe, utilisez des initialiseurs d'objets :</span><span class="sxs-lookup"><span data-stu-id="4368c-212">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="4368c-213">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="4368c-213">For more information, see:</span></span>

- [<span data-ttu-id="4368c-214">Nouvel opérateur</span><span class="sxs-lookup"><span data-stu-id="4368c-214">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="4368c-215">Initialiseurs d'objets : types nommés et anonymes</span><span class="sxs-lookup"><span data-stu-id="4368c-215">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a><span data-ttu-id="4368c-216">Classes et membres partagés</span><span class="sxs-lookup"><span data-stu-id="4368c-216">Shared classes and members</span></span>

 <span data-ttu-id="4368c-217">Un membre partagé de la classe est un bien, une procédure ou un domaine qui est partagé par tous les cas d’une classe.</span><span class="sxs-lookup"><span data-stu-id="4368c-217">A shared member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

 <span data-ttu-id="4368c-218">Définir un membre partagé :</span><span class="sxs-lookup"><span data-stu-id="4368c-218">To define a shared member:</span></span>

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 <span data-ttu-id="4368c-219">Pour accéder au membre partagé, utilisez le nom de la classe sans créer un objet de cette classe :</span><span class="sxs-lookup"><span data-stu-id="4368c-219">To access the shared member, use the name of the class without creating an object of this class:</span></span>

```vb
MsgBox(SampleClass.SampleString)
```

 <span data-ttu-id="4368c-220">Les modules partagés dans Visual Basic n’ont partagé que des membres et ne peuvent pas être instantanés.</span><span class="sxs-lookup"><span data-stu-id="4368c-220">Shared modules in Visual Basic have shared members only and cannot be instantiated.</span></span> <span data-ttu-id="4368c-221">Les membres partagés ne peuvent pas non plus accéder à des propriétés, des champs ou des méthodes non partagés</span><span class="sxs-lookup"><span data-stu-id="4368c-221">Shared members also cannot access non-shared properties, fields or methods</span></span>

 <span data-ttu-id="4368c-222">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="4368c-222">For more information, see:</span></span>

- [<span data-ttu-id="4368c-223">Partagé</span><span class="sxs-lookup"><span data-stu-id="4368c-223">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="4368c-224">Module, instruction</span><span class="sxs-lookup"><span data-stu-id="4368c-224">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a><span data-ttu-id="4368c-225">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="4368c-225">Anonymous types</span></span>

<span data-ttu-id="4368c-226">Les types anonymes vous permettent de créer des objets sans écrire de définition de classe pour le type de données.</span><span class="sxs-lookup"><span data-stu-id="4368c-226">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="4368c-227">À la place, le compilateur se charge de générer une classe.</span><span class="sxs-lookup"><span data-stu-id="4368c-227">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="4368c-228">La classe ne possède pas de nom utilisable et contient les propriétés que vous spécifiez lors de la déclaration de l'objet.</span><span class="sxs-lookup"><span data-stu-id="4368c-228">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="4368c-229">Pour créer une instance de type anonyme :</span><span class="sxs-lookup"><span data-stu-id="4368c-229">To create an instance of an anonymous type:</span></span>

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="4368c-230">Pour plus d’informations, consultez [Types anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="4368c-230">For more information, see: [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="4368c-231">Héritage</span><span class="sxs-lookup"><span data-stu-id="4368c-231">Inheritance</span></span>

<span data-ttu-id="4368c-232">Il vous permet de créer une nouvelle classe qui réutilise, étend et modifie le comportement défini dans une autre classe.</span><span class="sxs-lookup"><span data-stu-id="4368c-232">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="4368c-233">La classe dont les membres sont hérités porte le nom de *classe de base* et la classe qui hérite de ces membres porte le nom de *classe dérivée*.</span><span class="sxs-lookup"><span data-stu-id="4368c-233">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="4368c-234">Cependant, toutes les classes de Visual <xref:System.Object> Basic héritent implicitement de la classe qui soutient la hiérarchie de classe .NET et fournit des services de bas niveau à toutes les classes.</span><span class="sxs-lookup"><span data-stu-id="4368c-234">However, all classes in Visual Basic implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="4368c-235">Visual Basic ne prend pas en charge l’héritage multiple.</span><span class="sxs-lookup"><span data-stu-id="4368c-235">Visual Basic doesn't support multiple inheritance.</span></span> <span data-ttu-id="4368c-236">Vous pouvez donc spécifier une seule classe de base pour une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="4368c-236">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="4368c-237">Pour hériter d'une classe de base :</span><span class="sxs-lookup"><span data-stu-id="4368c-237">To inherit from a base class:</span></span>

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

<span data-ttu-id="4368c-238">Par défaut, toutes les classes peuvent être héritées.</span><span class="sxs-lookup"><span data-stu-id="4368c-238">By default all classes can be inherited.</span></span> <span data-ttu-id="4368c-239">Toutefois, vous pouvez spécifier si une classe ne doit pas être utilisée comme classe de base ou créer une classe qui peut être utilisée uniquement comme classe de base.</span><span class="sxs-lookup"><span data-stu-id="4368c-239">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="4368c-240">Pour spécifier qu'une classe ne peut pas être utilisée comme classe de base :</span><span class="sxs-lookup"><span data-stu-id="4368c-240">To specify that a class cannot be used as a base class:</span></span>

```vb
NotInheritable Class SampleClass
End Class
```

<span data-ttu-id="4368c-241">Pour spécifier qu'une classe peut être utilisée uniquement comme classe de base et ne peut pas être instanciée :</span><span class="sxs-lookup"><span data-stu-id="4368c-241">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```vb
MustInherit Class BaseClass
End Class
```

<span data-ttu-id="4368c-242">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="4368c-242">For more information, see:</span></span>

- [<span data-ttu-id="4368c-243">Inherits (instruction)</span><span class="sxs-lookup"><span data-stu-id="4368c-243">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="4368c-244">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="4368c-244">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="4368c-245">MustInherit</span><span class="sxs-lookup"><span data-stu-id="4368c-245">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a><span data-ttu-id="4368c-246">Membres dominants</span><span class="sxs-lookup"><span data-stu-id="4368c-246">Overriding members</span></span>

<span data-ttu-id="4368c-247">Par défaut, une classe dérivée hérite de tous les membres de sa classe de base.</span><span class="sxs-lookup"><span data-stu-id="4368c-247">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="4368c-248">Si vous souhaitez modifier le comportement du membre hérité, vous devez le substituer.</span><span class="sxs-lookup"><span data-stu-id="4368c-248">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="4368c-249">Autrement dit, vous pouvez définir une nouvelle implémentation de la méthode, de la propriété ou de l'événement dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="4368c-249">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="4368c-250">Les modificateurs suivants sont utilisés pour contrôler la façon dont les propriétés et les méthodes sont substituées :</span><span class="sxs-lookup"><span data-stu-id="4368c-250">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="4368c-251">Modificateur Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4368c-251">Visual Basic Modifier</span></span>|<span data-ttu-id="4368c-252">Définition</span><span class="sxs-lookup"><span data-stu-id="4368c-252">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="4368c-253">Overridable</span><span class="sxs-lookup"><span data-stu-id="4368c-253">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)|<span data-ttu-id="4368c-254">Autorise la substitution d'un membre de classe dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="4368c-254">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="4368c-255">Remplace</span><span class="sxs-lookup"><span data-stu-id="4368c-255">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)|<span data-ttu-id="4368c-256">Substitue un membre virtuel (substituable) défini dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="4368c-256">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="4368c-257">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="4368c-257">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)|<span data-ttu-id="4368c-258">Empêche un membre d'être substitué dans une classe qui hérite.</span><span class="sxs-lookup"><span data-stu-id="4368c-258">Prevents a member from being overridden in an inheriting class.</span></span>|
|[<span data-ttu-id="4368c-259">MustOverride</span><span class="sxs-lookup"><span data-stu-id="4368c-259">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)|<span data-ttu-id="4368c-260">Requiert qu'un membre de classe soit substitué dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="4368c-260">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="4368c-261">Shadows</span><span class="sxs-lookup"><span data-stu-id="4368c-261">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)|<span data-ttu-id="4368c-262">Masque un membre hérité d'une classe de base.</span><span class="sxs-lookup"><span data-stu-id="4368c-262">Hides a member inherited from a base class</span></span>|

## <a name="interfaces"></a><span data-ttu-id="4368c-263">Interfaces</span><span class="sxs-lookup"><span data-stu-id="4368c-263">Interfaces</span></span>

<span data-ttu-id="4368c-264">Tout comme les classes, les interfaces définissent un ensemble de propriétés, méthodes et événements.</span><span class="sxs-lookup"><span data-stu-id="4368c-264">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="4368c-265">Cependant, contrairement aux classes, les interfaces n'assurent pas l'implémentation.</span><span class="sxs-lookup"><span data-stu-id="4368c-265">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="4368c-266">Elles sont implémentées par les classes et définies en tant qu'entités distinctes des classes.</span><span class="sxs-lookup"><span data-stu-id="4368c-266">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="4368c-267">Une interface représente un contrat, dans le sens où une classe qui implémente une interface doit implémenter tous les aspects de cette interface exactement telle qu'elle a été définie.</span><span class="sxs-lookup"><span data-stu-id="4368c-267">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="4368c-268">Pour définir une interface :</span><span class="sxs-lookup"><span data-stu-id="4368c-268">To define an interface:</span></span>

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

<span data-ttu-id="4368c-269">Pour implémenter une interface dans une classe :</span><span class="sxs-lookup"><span data-stu-id="4368c-269">To implement an interface in a class:</span></span>

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

<span data-ttu-id="4368c-270">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="4368c-270">For more information, see:</span></span>

- [<span data-ttu-id="4368c-271">Interfaces</span><span class="sxs-lookup"><span data-stu-id="4368c-271">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [<span data-ttu-id="4368c-272">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="4368c-272">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="4368c-273">Implements (instruction)</span><span class="sxs-lookup"><span data-stu-id="4368c-273">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)

## <a name="generics"></a><span data-ttu-id="4368c-274">Génériques</span><span class="sxs-lookup"><span data-stu-id="4368c-274">Generics</span></span>

<span data-ttu-id="4368c-275">Les classes, les structures, les interfaces et les méthodes en .NET peuvent inclure des paramètres de *type* qui définissent les types d’objets qu’ils peuvent stocker ou utiliser.</span><span class="sxs-lookup"><span data-stu-id="4368c-275">Classes, structures, interfaces and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="4368c-276">L’exemple le plus commun de génériques est une collection dans laquelle vous pouvez spécifier le type d’objets à stocker dans une collection.</span><span class="sxs-lookup"><span data-stu-id="4368c-276">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="4368c-277">Pour définir une classe générique :</span><span class="sxs-lookup"><span data-stu-id="4368c-277">To define a generic class:</span></span>

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

<span data-ttu-id="4368c-278">Pour créer une instance de classe générique :</span><span class="sxs-lookup"><span data-stu-id="4368c-278">To create an instance of a generic class:</span></span>

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

<span data-ttu-id="4368c-279">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="4368c-279">For more information, see:</span></span>

- [<span data-ttu-id="4368c-280">Génériques</span><span class="sxs-lookup"><span data-stu-id="4368c-280">Generics</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="4368c-281">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4368c-281">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a><span data-ttu-id="4368c-282">Délégués</span><span class="sxs-lookup"><span data-stu-id="4368c-282">Delegates</span></span>

 <span data-ttu-id="4368c-283">Un *délégué* est un type qui définit une signature de méthode et peut fournir une référence à toute méthode avec une signature compatible.</span><span class="sxs-lookup"><span data-stu-id="4368c-283">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="4368c-284">Vous pouvez appeler la méthode par le biais du délégué.</span><span class="sxs-lookup"><span data-stu-id="4368c-284">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="4368c-285">Les délégués sont utilisés pour passer des méthodes comme arguments à d'autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="4368c-285">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="4368c-286">Les gestionnaires d'événements sont tout simplement des méthodes appelées par le biais de délégués.</span><span class="sxs-lookup"><span data-stu-id="4368c-286">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="4368c-287">Pour plus d’informations sur l’utilisation de délégués dans la gestion des événements, consultez [Événements](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="4368c-287">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="4368c-288">Pour créer un délégué :</span><span class="sxs-lookup"><span data-stu-id="4368c-288">To create a delegate:</span></span>

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

<span data-ttu-id="4368c-289">Pour créer une référence à une méthode qui correspond à la signature spécifiée par le délégué :</span><span class="sxs-lookup"><span data-stu-id="4368c-289">To create a reference to a method that matches the signature specified by the delegate:</span></span>

```vb
Class SampleClass
    ' Method that matches the SampleDelegate signature.
    Sub SampleSub(ByVal str As String)
        ' Add code here.
    End Sub
    ' Method that instantiates the delegate.
    Sub SampleDelegateSub()
        Dim sd As SampleDelegate = AddressOf SampleSub
        sd("Sample string")
    End Sub
End Class
```

<span data-ttu-id="4368c-290">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="4368c-290">For more information, see:</span></span>

- [<span data-ttu-id="4368c-291">Délégués</span><span class="sxs-lookup"><span data-stu-id="4368c-291">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="4368c-292">Delegate (instruction)</span><span class="sxs-lookup"><span data-stu-id="4368c-292">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="4368c-293">AddressOf (opérateur)</span><span class="sxs-lookup"><span data-stu-id="4368c-293">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a><span data-ttu-id="4368c-294">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4368c-294">See also</span></span>

- [<span data-ttu-id="4368c-295">Guide de programmation Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4368c-295">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
