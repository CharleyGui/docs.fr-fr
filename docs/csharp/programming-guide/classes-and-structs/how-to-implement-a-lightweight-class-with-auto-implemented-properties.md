---
title: Comment implémenter une classe Lightweight avec des propriétés implémentées automatiquement-Guide de programmation C#
description: Découvrez comment créer une classe légère immuable en C# qui encapsule des propriétés implémentées automatiquement. Il existe deux approches d’implémentation.
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
ms.openlocfilehash: 39e191ce3b113b483fe93d70a0cadf02a7bee915
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099372"
---
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="789bb-104">Comment implémenter une classe Lightweight avec des propriétés implémentées automatiquement (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="789bb-104">How to implement a lightweight class with auto-implemented properties (C# Programming Guide)</span></span>

<span data-ttu-id="789bb-105">Cet exemple montre comment créer une classe légère immuable qui sert uniquement à encapsuler un jeu de propriétés implémentées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="789bb-105">This example shows how to create an immutable lightweight class that serves only to encapsulate a set of auto-implemented properties.</span></span> <span data-ttu-id="789bb-106">Utilisez ce type de construction à la place d'un struct quand vous devez utiliser une sémantique de type de référence.</span><span class="sxs-lookup"><span data-stu-id="789bb-106">Use this kind of construct instead of a struct when you must use reference type semantics.</span></span>

<span data-ttu-id="789bb-107">Vous pouvez rendre une propriété immuable de deux manières :</span><span class="sxs-lookup"><span data-stu-id="789bb-107">You can make an immutable property in two ways:</span></span>

- <span data-ttu-id="789bb-108">Vous pouvez déclarer l’accesseur [set](../../language-reference/keywords/set.md) comme étant [private](../../language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="789bb-108">You can declare the [set](../../language-reference/keywords/set.md) accessor to be [private](../../language-reference/keywords/private.md).</span></span>  <span data-ttu-id="789bb-109">La propriété peut uniquement être définie dans le type, mais elle est immuable pour les consommateurs.</span><span class="sxs-lookup"><span data-stu-id="789bb-109">The property is only settable within the type, but it is immutable to consumers.</span></span>

  <span data-ttu-id="789bb-110">Quand vous déclarez un accesseur `set` privé, vous ne pouvez pas utiliser un initialiseur d'objet pour initialiser la propriété.</span><span class="sxs-lookup"><span data-stu-id="789bb-110">When you declare a private `set` accessor, you cannot use an object initializer to initialize the property.</span></span> <span data-ttu-id="789bb-111">Vous devez utiliser un constructeur ou une méthode de fabrique.</span><span class="sxs-lookup"><span data-stu-id="789bb-111">You must use a constructor or a factory method.</span></span>
- <span data-ttu-id="789bb-112">Vous pouvez déclarer uniquement l’accesseur [Get](../../language-reference/keywords/get.md) , ce qui rend la propriété immuable partout sauf dans le constructeur du type.</span><span class="sxs-lookup"><span data-stu-id="789bb-112">You can declare only the [get](../../language-reference/keywords/get.md) accessor, which makes the property immutable everywhere except in the type's constructor.</span></span>

<span data-ttu-id="789bb-113">L’exemple suivant montre comment une propriété avec uniquement l’accesseur Get diffère de celle avec Get et Private Set.</span><span class="sxs-lookup"><span data-stu-id="789bb-113">The following example shows how a property with only get accessor differs than one with get and private set.</span></span>

```csharp
class Contact
{
    public string Name { get; }
    public string Address { get; private set; }

    public Contact(string contactName, string contactAddress)
    {
        // Both properties are accessible in the constructor.
        Name = contactName;
        Address = contactAddress;
    }

    // Name isn't assignable here. This will generate a compile error.
    //public void ChangeName(string newName) => Name = newName;

    // Address is assignable here.
    public void ChangeAddress(string newAddress) => Address = newAddress
}
```

## <a name="example"></a><span data-ttu-id="789bb-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="789bb-114">Example</span></span>

<span data-ttu-id="789bb-115">L'exemple suivant montre deux façons d'implémenter une classe immuable qui possède des propriétés implémentées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="789bb-115">The following example shows two ways to implement an immutable class that has auto-implemented properties.</span></span> <span data-ttu-id="789bb-116">Chaque façon déclare l'une des propriétés avec un `set` privé et l'autre avec un `get` uniquement.</span><span class="sxs-lookup"><span data-stu-id="789bb-116">Each way declares one of the properties with a private `set` and one of the properties with a `get` only.</span></span>  <span data-ttu-id="789bb-117">La première classe utilise un constructeur uniquement pour initialiser les propriétés et la deuxième classe utilise une méthode de fabrique statique qui appelle un constructeur.</span><span class="sxs-lookup"><span data-stu-id="789bb-117">The first class uses a constructor only to initialize the properties, and the second class uses a static factory method that calls a constructor.</span></span>

```csharp
// This class is immutable. After an object is created,
// it cannot be modified from outside the class. It uses a
// constructor to initialize its properties.
class Contact
{
    // Read-only property.
    public string Name { get; }

    // Read-write property with a private set accessor.
    public string Address { get; private set; }

    // Public constructor.
    public Contact(string contactName, string contactAddress)
    {
        Name = contactName;
        Address = contactAddress;
    }
}

// This class is immutable. After an object is created,
// it cannot be modified from outside the class. It uses a
// static method and private constructor to initialize its properties.
public class Contact2
{
    // Read-write property with a private set accessor.
    public string Name { get; private set; }

    // Read-only property.
    public string Address { get; }

    // Private constructor.
    private Contact2(string contactName, string contactAddress)
    {
        Name = contactName;
        Address = contactAddress;
    }

    // Public factory method.
    public static Contact2 CreateContact(string name, string address)
    {
        return new Contact2(name, address);
    }
}

public class Program
{
    static void Main()
    {
        // Some simple data sources.
        string[] names = {"Terry Adams","Fadi Fakhouri", "Hanying Feng",
                            "Cesar Garcia", "Debra Garcia"};
        string[] addresses = {"123 Main St.", "345 Cypress Ave.", "678 1st Ave",
                                "12 108th St.", "89 E. 42nd St."};

        // Simple query to demonstrate object creation in select clause.
        // Create Contact objects by using a constructor.
        var query1 = from i in Enumerable.Range(0, 5)
                    select new Contact(names[i], addresses[i]);

        // List elements cannot be modified by client code.
        var list = query1.ToList();
        foreach (var contact in list)
        {
            Console.WriteLine("{0}, {1}", contact.Name, contact.Address);
        }

        // Create Contact2 objects by using a static factory method.
        var query2 = from i in Enumerable.Range(0, 5)
                        select Contact2.CreateContact(names[i], addresses[i]);

        // Console output is identical to query1.
        var list2 = query2.ToList();

        // List elements cannot be modified by client code.
        // CS0272:
        // list2[0].Name = "Eugene Zabokritski";

        // Keep the console open in debug mode.
        Console.WriteLine("Press any key to exit.");
        Console.ReadKey();
    }
}

/* Output:
    Terry Adams, 123 Main St.
    Fadi Fakhouri, 345 Cypress Ave.
    Hanying Feng, 678 1st Ave
    Cesar Garcia, 12 108th St.
    Debra Garcia, 89 E. 42nd St.
*/
```

<span data-ttu-id="789bb-118">Le compilateur crée des champs de stockage pour chaque propriété implémentée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="789bb-118">The compiler creates backing fields for each auto-implemented property.</span></span> <span data-ttu-id="789bb-119">Les champs ne sont pas accessibles directement à partir du code source.</span><span class="sxs-lookup"><span data-stu-id="789bb-119">The fields are not accessible directly from source code.</span></span>

## <a name="see-also"></a><span data-ttu-id="789bb-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="789bb-120">See also</span></span>

- [<span data-ttu-id="789bb-121">Propriétés</span><span class="sxs-lookup"><span data-stu-id="789bb-121">Properties</span></span>](./properties.md)
- [<span data-ttu-id="789bb-122">modélis</span><span class="sxs-lookup"><span data-stu-id="789bb-122">struct</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="789bb-123">Initialiseurs d’objets et de collections</span><span class="sxs-lookup"><span data-stu-id="789bb-123">Object and Collection Initializers</span></span>](./object-and-collection-initializers.md)
