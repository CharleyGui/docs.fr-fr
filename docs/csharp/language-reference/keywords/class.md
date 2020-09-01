---
description: class, mot clé - Référence C#
title: class, mot clé - Référence C#
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 67c9c4be55cce25edf9ecb84b257a8523f193bec
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142113"
---
# <a name="class-c-reference"></a><span data-ttu-id="454bf-103">class (référence C#)</span><span class="sxs-lookup"><span data-stu-id="454bf-103">class (C# Reference)</span></span>

<span data-ttu-id="454bf-104">Les classes sont déclarées à l’aide du mot clé `class`, comme l’illustre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="454bf-104">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="454bf-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="454bf-105">Remarks</span></span>

<span data-ttu-id="454bf-106">Le langage C# ne permet qu'un seul héritage.</span><span class="sxs-lookup"><span data-stu-id="454bf-106">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="454bf-107">Cela signifie qu’une classe peut uniquement hériter de l’implémentation d’une seule classe de base.</span><span class="sxs-lookup"><span data-stu-id="454bf-107">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="454bf-108">Toutefois, une classe peut implémenter plusieurs interfaces.</span><span class="sxs-lookup"><span data-stu-id="454bf-108">However, a class can implement more than one interface.</span></span> <span data-ttu-id="454bf-109">Le tableau suivant répertorie des exemples d’héritage de classe et d’implémentation d’interface :</span><span class="sxs-lookup"><span data-stu-id="454bf-109">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="454bf-110">Héritage</span><span class="sxs-lookup"><span data-stu-id="454bf-110">Inheritance</span></span>|<span data-ttu-id="454bf-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="454bf-111">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="454bf-112">Aucune</span><span class="sxs-lookup"><span data-stu-id="454bf-112">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="454bf-113">Unique</span><span class="sxs-lookup"><span data-stu-id="454bf-113">Single</span></span>|`class DerivedClass : BaseClass { }`|
|<span data-ttu-id="454bf-114">Aucun, implémente deux interfaces</span><span class="sxs-lookup"><span data-stu-id="454bf-114">None, implements two interfaces</span></span>|`class ImplClass : IFace1, IFace2 { }`|
|<span data-ttu-id="454bf-115">Unique, implémente une seule interface</span><span class="sxs-lookup"><span data-stu-id="454bf-115">Single, implements one interface</span></span>|`class ImplDerivedClass : BaseClass, IFace1 { }`|

<span data-ttu-id="454bf-116">Les classes que vous déclarez directement dans un espace de noms, non imbriquées dans d’autres classes, peuvent être [public](./public.md) ou [internal](./internal.md).</span><span class="sxs-lookup"><span data-stu-id="454bf-116">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](./public.md) or [internal](./internal.md).</span></span> <span data-ttu-id="454bf-117">Par défaut, les classes sont `internal`.</span><span class="sxs-lookup"><span data-stu-id="454bf-117">Classes are `internal` by default.</span></span>

<span data-ttu-id="454bf-118">Les membres de classe, notamment les classes imbriquées, peuvent être [public](public.md), [protected internal](protected-internal.md), [protected](protected.md), [internal](internal.md), [private](private.md) ou [private protected](private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="454bf-118">Class members, including nested classes, can be [public](public.md), [protected internal](protected-internal.md), [protected](protected.md), [internal](internal.md), [private](private.md), or [private protected](private-protected.md).</span></span> <span data-ttu-id="454bf-119">Par défaut, ils sont `private`.</span><span class="sxs-lookup"><span data-stu-id="454bf-119">Members are `private` by default.</span></span>

<span data-ttu-id="454bf-120">Pour plus d’informations, consultez [Modificateurs d’accès](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="454bf-120">For more information, see [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="454bf-121">Vous pouvez déclarer des classes génériques qui ont des paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="454bf-121">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="454bf-122">Pour plus d’informations, consultez [Classes génériques](../../programming-guide/generics/generic-classes.md).</span><span class="sxs-lookup"><span data-stu-id="454bf-122">For more information, see [Generic Classes](../../programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="454bf-123">Une classe peut contenir les déclarations des membres suivants :</span><span class="sxs-lookup"><span data-stu-id="454bf-123">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="454bf-124">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="454bf-124">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="454bf-125">Constantes</span><span class="sxs-lookup"><span data-stu-id="454bf-125">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="454bf-126">Fields</span><span class="sxs-lookup"><span data-stu-id="454bf-126">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="454bf-127">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="454bf-127">Finalizers</span></span>](../../programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="454bf-128">Méthodes</span><span class="sxs-lookup"><span data-stu-id="454bf-128">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="454bf-129">Propriétés</span><span class="sxs-lookup"><span data-stu-id="454bf-129">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="454bf-130">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="454bf-130">Indexers</span></span>](../../programming-guide/indexers/index.md)

- [<span data-ttu-id="454bf-131">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="454bf-131">Operators</span></span>](../operators/index.md)

- [<span data-ttu-id="454bf-132">Événements</span><span class="sxs-lookup"><span data-stu-id="454bf-132">Events</span></span>](../../programming-guide/events/index.md)

- [<span data-ttu-id="454bf-133">Délégués</span><span class="sxs-lookup"><span data-stu-id="454bf-133">Delegates</span></span>](../../programming-guide/delegates/index.md)

- [<span data-ttu-id="454bf-134">Classes</span><span class="sxs-lookup"><span data-stu-id="454bf-134">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="454bf-135">Interfaces</span><span class="sxs-lookup"><span data-stu-id="454bf-135">Interfaces</span></span>](../../programming-guide/interfaces/index.md)

- [<span data-ttu-id="454bf-136">Types de structure</span><span class="sxs-lookup"><span data-stu-id="454bf-136">Structure types</span></span>](../builtin-types/struct.md)

- [<span data-ttu-id="454bf-137">Types d'énumération</span><span class="sxs-lookup"><span data-stu-id="454bf-137">Enumeration types</span></span>](../builtin-types/enum.md)

## <a name="example"></a><span data-ttu-id="454bf-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="454bf-138">Example</span></span>

<span data-ttu-id="454bf-139">L’exemple suivant explique comment déclarer des champs, des constructeurs et des méthodes de classe.</span><span class="sxs-lookup"><span data-stu-id="454bf-139">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="454bf-140">Il illustre également l’instanciation d’un objet et l’impression des données d’une instance.</span><span class="sxs-lookup"><span data-stu-id="454bf-140">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="454bf-141">Dans cet exemple, deux classes sont déclarées.</span><span class="sxs-lookup"><span data-stu-id="454bf-141">In this example, two classes are declared.</span></span> <span data-ttu-id="454bf-142">La première, `Child`, contient deux champs privés (`name` et `age`), deux constructeurs publics et une méthode publique.</span><span class="sxs-lookup"><span data-stu-id="454bf-142">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="454bf-143">La deuxième, `StringTest`, contient `Main`.</span><span class="sxs-lookup"><span data-stu-id="454bf-143">The second class, `StringTest`, is used to contain `Main`.</span></span>

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a><span data-ttu-id="454bf-144">Commentaires</span><span class="sxs-lookup"><span data-stu-id="454bf-144">Comments</span></span>

<span data-ttu-id="454bf-145">Notez que, dans l’exemple précédant, les champs privés (`name` et `age`) ne sont accessibles que par le biais de la méthode publique de la classe `Child`.</span><span class="sxs-lookup"><span data-stu-id="454bf-145">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="454bf-146">Par exemple, vous ne pouvez pas imprimer le nom de l’enfant à partir de la méthode `Main` en utilisant une instruction comme celle-ci :</span><span class="sxs-lookup"><span data-stu-id="454bf-146">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="454bf-147">L’accès aux membres privés de `Child` à partir de `Main` est uniquement possible si `Main` est un membre de la classe.</span><span class="sxs-lookup"><span data-stu-id="454bf-147">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="454bf-148">Du fait que les types déclarés dans une classe sans modificateur d’accès sont par défaut `private`, les données membres dans cet exemple sont toujours `private` si le mot clé est supprimé.</span><span class="sxs-lookup"><span data-stu-id="454bf-148">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="454bf-149">Notez enfin que pour l’objet créé à l’aide du constructeur sans paramètre (`child3`), le champ `age` est initialisé par défaut à la valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="454bf-149">Finally, notice that for the object created using the parameterless constructor (`child3`), the `age` field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="454bf-150">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="454bf-150">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="454bf-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="454bf-151">See also</span></span>

- [<span data-ttu-id="454bf-152">Référence C#</span><span class="sxs-lookup"><span data-stu-id="454bf-152">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="454bf-153">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="454bf-153">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="454bf-154">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="454bf-154">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="454bf-155">Types référence</span><span class="sxs-lookup"><span data-stu-id="454bf-155">Reference Types</span></span>](./reference-types.md)
