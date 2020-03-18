---
title: class, mot clé - Référence C#
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 500160d3bc9280b866e5f5ba24c5edc623e752c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673093"
---
# <a name="class-c-reference"></a><span data-ttu-id="7d2ce-102">class (référence C#)</span><span class="sxs-lookup"><span data-stu-id="7d2ce-102">class (C# Reference)</span></span>

<span data-ttu-id="7d2ce-103">Les classes sont déclarées à l’aide du mot clé `class`, comme l’illustre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="7d2ce-103">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="7d2ce-104">Notes </span><span class="sxs-lookup"><span data-stu-id="7d2ce-104">Remarks</span></span>

<span data-ttu-id="7d2ce-105">Le langage C# ne permet qu'un seul héritage.</span><span class="sxs-lookup"><span data-stu-id="7d2ce-105">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="7d2ce-106">Cela signifie qu’une classe peut uniquement hériter de l’implémentation d’une seule classe de base.</span><span class="sxs-lookup"><span data-stu-id="7d2ce-106">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="7d2ce-107">Toutefois, une classe peut implémenter plusieurs interfaces.</span><span class="sxs-lookup"><span data-stu-id="7d2ce-107">However, a class can implement more than one interface.</span></span> <span data-ttu-id="7d2ce-108">Le tableau suivant répertorie des exemples d’héritage de classe et d’implémentation d’interface :</span><span class="sxs-lookup"><span data-stu-id="7d2ce-108">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="7d2ce-109">Héritage</span><span class="sxs-lookup"><span data-stu-id="7d2ce-109">Inheritance</span></span>|<span data-ttu-id="7d2ce-110"> Exemple</span><span class="sxs-lookup"><span data-stu-id="7d2ce-110">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="7d2ce-111">None</span><span class="sxs-lookup"><span data-stu-id="7d2ce-111">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="7d2ce-112">Unique</span><span class="sxs-lookup"><span data-stu-id="7d2ce-112">Single</span></span>|`class DerivedClass : BaseClass { }`|
|<span data-ttu-id="7d2ce-113">Aucun, implémente deux interfaces</span><span class="sxs-lookup"><span data-stu-id="7d2ce-113">None, implements two interfaces</span></span>|`class ImplClass : IFace1, IFace2 { }`|
|<span data-ttu-id="7d2ce-114">Unique, implémente une seule interface</span><span class="sxs-lookup"><span data-stu-id="7d2ce-114">Single, implements one interface</span></span>|`class ImplDerivedClass : BaseClass, IFace1 { }`|

<span data-ttu-id="7d2ce-115">Les classes que vous déclarez directement dans un espace de noms, non imbriquées dans d’autres classes, peuvent être [public](./public.md) ou [internal](./internal.md).</span><span class="sxs-lookup"><span data-stu-id="7d2ce-115">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](./public.md) or [internal](./internal.md).</span></span> <span data-ttu-id="7d2ce-116">Par défaut, les classes sont `internal`.</span><span class="sxs-lookup"><span data-stu-id="7d2ce-116">Classes are `internal` by default.</span></span>

<span data-ttu-id="7d2ce-117">Les membres de classe, notamment les classes imbriquées, peuvent être [public](public.md), [protected internal](protected-internal.md), [protected](protected.md), [internal](internal.md), [private](private.md) ou [private protected](private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="7d2ce-117">Class members, including nested classes, can be [public](public.md), [protected internal](protected-internal.md), [protected](protected.md), [internal](internal.md), [private](private.md), or [private protected](private-protected.md).</span></span> <span data-ttu-id="7d2ce-118">Par défaut, ils sont `private`.</span><span class="sxs-lookup"><span data-stu-id="7d2ce-118">Members are `private` by default.</span></span>

<span data-ttu-id="7d2ce-119">Pour plus d’informations, consultez [Modificateurs d’accès](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="7d2ce-119">For more information, see [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="7d2ce-120">Vous pouvez déclarer des classes génériques qui ont des paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="7d2ce-120">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="7d2ce-121">Pour plus d’informations, consultez [Classes génériques](../../programming-guide/generics/generic-classes.md).</span><span class="sxs-lookup"><span data-stu-id="7d2ce-121">For more information, see [Generic Classes](../../programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="7d2ce-122">Une classe peut contenir les déclarations des membres suivants :</span><span class="sxs-lookup"><span data-stu-id="7d2ce-122">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="7d2ce-123">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="7d2ce-123">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="7d2ce-124">Constantes</span><span class="sxs-lookup"><span data-stu-id="7d2ce-124">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="7d2ce-125">Champs</span><span class="sxs-lookup"><span data-stu-id="7d2ce-125">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="7d2ce-126">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="7d2ce-126">Finalizers</span></span>](../../programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="7d2ce-127">Méthodes</span><span class="sxs-lookup"><span data-stu-id="7d2ce-127">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="7d2ce-128">Propriétés</span><span class="sxs-lookup"><span data-stu-id="7d2ce-128">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="7d2ce-129">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="7d2ce-129">Indexers</span></span>](../../programming-guide/indexers/index.md)

- [<span data-ttu-id="7d2ce-130">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="7d2ce-130">Operators</span></span>](../operators/index.md)

- [<span data-ttu-id="7d2ce-131">Événements</span><span class="sxs-lookup"><span data-stu-id="7d2ce-131">Events</span></span>](../../programming-guide/events/index.md)

- [<span data-ttu-id="7d2ce-132">Délégués</span><span class="sxs-lookup"><span data-stu-id="7d2ce-132">Delegates</span></span>](../../programming-guide/delegates/index.md)

- [<span data-ttu-id="7d2ce-133">Classes</span><span class="sxs-lookup"><span data-stu-id="7d2ce-133">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="7d2ce-134">Interfaces</span><span class="sxs-lookup"><span data-stu-id="7d2ce-134">Interfaces</span></span>](../../programming-guide/interfaces/index.md)

- [<span data-ttu-id="7d2ce-135">Types de structure</span><span class="sxs-lookup"><span data-stu-id="7d2ce-135">Structure types</span></span>](../builtin-types/struct.md)

- [<span data-ttu-id="7d2ce-136">Types d’énumération</span><span class="sxs-lookup"><span data-stu-id="7d2ce-136">Enumeration types</span></span>](../builtin-types/enum.md)

## <a name="example"></a><span data-ttu-id="7d2ce-137"> Exemple</span><span class="sxs-lookup"><span data-stu-id="7d2ce-137">Example</span></span>

<span data-ttu-id="7d2ce-138">L’exemple suivant explique comment déclarer des champs, des constructeurs et des méthodes de classe.</span><span class="sxs-lookup"><span data-stu-id="7d2ce-138">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="7d2ce-139">Il illustre également l’instanciation d’un objet et l’impression des données d’une instance.</span><span class="sxs-lookup"><span data-stu-id="7d2ce-139">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="7d2ce-140">Dans cet exemple, deux classes sont déclarées.</span><span class="sxs-lookup"><span data-stu-id="7d2ce-140">In this example, two classes are declared.</span></span> <span data-ttu-id="7d2ce-141">La première, `Child`, contient deux champs privés (`name` et `age`), deux constructeurs publics et une méthode publique.</span><span class="sxs-lookup"><span data-stu-id="7d2ce-141">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="7d2ce-142">La deuxième, `StringTest`, contient `Main`.</span><span class="sxs-lookup"><span data-stu-id="7d2ce-142">The second class, `StringTest`, is used to contain `Main`.</span></span>

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a><span data-ttu-id="7d2ce-143">Commentaires</span><span class="sxs-lookup"><span data-stu-id="7d2ce-143">Comments</span></span>

<span data-ttu-id="7d2ce-144">Notez que, dans l’exemple précédant, les champs privés (`name` et `age`) ne sont accessibles que par le biais de la méthode publique de la classe `Child`.</span><span class="sxs-lookup"><span data-stu-id="7d2ce-144">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="7d2ce-145">Par exemple, vous ne pouvez pas imprimer le nom de l’enfant à partir de la méthode `Main` en utilisant une instruction comme celle-ci :</span><span class="sxs-lookup"><span data-stu-id="7d2ce-145">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="7d2ce-146">L’accès aux membres privés de `Child` à partir de `Main` est uniquement possible si `Main` est un membre de la classe.</span><span class="sxs-lookup"><span data-stu-id="7d2ce-146">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="7d2ce-147">Du fait que les types déclarés dans une classe sans modificateur d’accès sont par défaut `private`, les données membres dans cet exemple sont toujours `private` si le mot clé est supprimé.</span><span class="sxs-lookup"><span data-stu-id="7d2ce-147">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="7d2ce-148">Notez enfin que pour l’objet créé à l’aide du constructeur sans paramètre (`child3`), le champ `age` est initialisé par défaut à la valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="7d2ce-148">Finally, notice that for the object created using the parameterless constructor (`child3`), the `age` field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7d2ce-149">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="7d2ce-149">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7d2ce-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d2ce-150">See also</span></span>

- [<span data-ttu-id="7d2ce-151">Référence C</span><span class="sxs-lookup"><span data-stu-id="7d2ce-151">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7d2ce-152">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="7d2ce-152">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7d2ce-153">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="7d2ce-153">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="7d2ce-154">Types de référence</span><span class="sxs-lookup"><span data-stu-id="7d2ce-154">Reference Types</span></span>](./reference-types.md)
