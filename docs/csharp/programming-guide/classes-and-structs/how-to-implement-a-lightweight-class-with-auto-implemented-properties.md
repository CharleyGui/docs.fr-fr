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
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a>Comment implémenter une classe Lightweight avec des propriétés implémentées automatiquement (Guide de programmation C#)

Cet exemple montre comment créer une classe légère immuable qui sert uniquement à encapsuler un jeu de propriétés implémentées automatiquement. Utilisez ce type de construction à la place d'un struct quand vous devez utiliser une sémantique de type de référence.

Vous pouvez rendre une propriété immuable de deux manières :

- Vous pouvez déclarer l’accesseur [set](../../language-reference/keywords/set.md) comme étant [private](../../language-reference/keywords/private.md).  La propriété peut uniquement être définie dans le type, mais elle est immuable pour les consommateurs.

  Quand vous déclarez un accesseur `set` privé, vous ne pouvez pas utiliser un initialiseur d'objet pour initialiser la propriété. Vous devez utiliser un constructeur ou une méthode de fabrique.
- Vous pouvez déclarer uniquement l’accesseur [Get](../../language-reference/keywords/get.md) , ce qui rend la propriété immuable partout sauf dans le constructeur du type.

L’exemple suivant montre comment une propriété avec uniquement l’accesseur Get diffère de celle avec Get et Private Set.

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

## <a name="example"></a>Exemple

L'exemple suivant montre deux façons d'implémenter une classe immuable qui possède des propriétés implémentées automatiquement. Chaque façon déclare l'une des propriétés avec un `set` privé et l'autre avec un `get` uniquement.  La première classe utilise un constructeur uniquement pour initialiser les propriétés et la deuxième classe utilise une méthode de fabrique statique qui appelle un constructeur.

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

Le compilateur crée des champs de stockage pour chaque propriété implémentée automatiquement. Les champs ne sont pas accessibles directement à partir du code source.

## <a name="see-also"></a>Voir aussi

- [Propriétés](./properties.md)
- [modélis](../../language-reference/builtin-types/struct.md)
- [Initialiseurs d’objets et de collections](./object-and-collection-initializers.md)
