---
title: 'Procédure : Implémenter une classe Lightweight avec des propriétés implémentées automatiquement - Guide de programmation C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
ms.openlocfilehash: f9884f353e58ff6119e3bc3b95aa55f0f60d0ad5
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398499"
---
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="a39b0-102">Procédure : Implémenter une classe Lightweight avec des propriétés implémentées automatiquement (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="a39b0-102">How to: Implement a Lightweight Class with Auto-Implemented Properties (C# Programming Guide)</span></span>

<span data-ttu-id="a39b0-103">Cet exemple montre comment créer une classe légère immuable qui sert uniquement à encapsuler un jeu de propriétés implémentées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="a39b0-103">This example shows how to create an immutable lightweight class that serves only to encapsulate a set of auto-implemented properties.</span></span> <span data-ttu-id="a39b0-104">Utilisez ce type de construction à la place d'un struct quand vous devez utiliser une sémantique de type de référence.</span><span class="sxs-lookup"><span data-stu-id="a39b0-104">Use this kind of construct instead of a struct when you must use reference type semantics.</span></span>

<span data-ttu-id="a39b0-105">Vous pouvez rendre une propriété immuable de deux manières :</span><span class="sxs-lookup"><span data-stu-id="a39b0-105">You can make an immutable property in two ways:</span></span>
- <span data-ttu-id="a39b0-106">Vous pouvez déclarer l’accesseur [set](../../../csharp/language-reference/keywords/set.md) comme étant [private](../../../csharp/language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="a39b0-106">You can declare the [set](../../../csharp/language-reference/keywords/set.md) accessor to be [private](../../../csharp/language-reference/keywords/private.md).</span></span>  <span data-ttu-id="a39b0-107">La propriété peut uniquement être définie dans le type, mais elle est immuable pour les consommateurs.</span><span class="sxs-lookup"><span data-stu-id="a39b0-107">The property is only settable within the type, but it is immutable to consumers.</span></span>

  <span data-ttu-id="a39b0-108">Quand vous déclarez un accesseur `set` privé, vous ne pouvez pas utiliser un initialiseur d'objet pour initialiser la propriété.</span><span class="sxs-lookup"><span data-stu-id="a39b0-108">When you declare a private `set` accessor, you cannot use an object initializer to initialize the property.</span></span> <span data-ttu-id="a39b0-109">Vous devez utiliser un constructeur ou une méthode de fabrique.</span><span class="sxs-lookup"><span data-stu-id="a39b0-109">You must use a constructor or a factory method.</span></span>
- <span data-ttu-id="a39b0-110">Vous pouvez déclarer uniquement l’accesseur [get](../../../csharp/language-reference/keywords/get.md), ce qui rend la propriété immuable partout, sauf dans le constructeur du type.</span><span class="sxs-lookup"><span data-stu-id="a39b0-110">You can declare only the [get](../../../csharp/language-reference/keywords/get.md) accessor, which makes the property immutable everywhere except in the type’s constructor.</span></span>

## <a name="example"></a><span data-ttu-id="a39b0-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="a39b0-111">Example</span></span>

<span data-ttu-id="a39b0-112">L'exemple suivant montre deux façons d'implémenter une classe immuable qui possède des propriétés implémentées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="a39b0-112">The following example shows two ways to implement an immutable class that has auto-implemented properties.</span></span> <span data-ttu-id="a39b0-113">Chaque façon déclare l'une des propriétés avec un `set` privé et l'autre avec un `get` uniquement.</span><span class="sxs-lookup"><span data-stu-id="a39b0-113">Each way declares one of the properties with a private `set` and one of the properties with a `get` only.</span></span>  <span data-ttu-id="a39b0-114">La première classe utilise un constructeur uniquement pour initialiser les propriétés et la deuxième classe utilise une méthode de fabrique statique qui appelle un constructeur.</span><span class="sxs-lookup"><span data-stu-id="a39b0-114">The first class uses a constructor only to initialize the properties, and the second class uses a static factory method that calls a constructor.</span></span>

```csharp
// This class is immutable. After an object is created,
// it cannot be modified from outside the class. It uses a
// constructor to initialize its properties.
class Contact
{
    // Read-only properties.
    public string Name { get; }
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
    // Read-only properties.
    public string Name { get; private set; }
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

<span data-ttu-id="a39b0-115">Le compilateur crée des champs de stockage pour chaque propriété implémentée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="a39b0-115">The compiler creates backing fields for each auto-implemented property.</span></span> <span data-ttu-id="a39b0-116">Les champs ne sont pas accessibles directement à partir du code source.</span><span class="sxs-lookup"><span data-stu-id="a39b0-116">The fields are not accessible directly from source code.</span></span>

## <a name="see-also"></a><span data-ttu-id="a39b0-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a39b0-117">See also</span></span>

- [<span data-ttu-id="a39b0-118">Propriétés</span><span class="sxs-lookup"><span data-stu-id="a39b0-118">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [<span data-ttu-id="a39b0-119">struct</span><span class="sxs-lookup"><span data-stu-id="a39b0-119">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)
- [<span data-ttu-id="a39b0-120">Initialiseurs d’objets et de collections</span><span class="sxs-lookup"><span data-stu-id="a39b0-120">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
