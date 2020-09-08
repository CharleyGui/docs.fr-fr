---
title: Comment projeter un type anonyme-LINQ to XML
description: Vous pouvez projeter vers un type anonyme au lieu de créer un type uniquement pour une utilisation dans la projection. Cet article fournit un exemple pour C# et Visual Basic.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 5851492f075068337c60316664138dd09c97443b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553271"
---
# <a name="how-to-project-an-anonymous-type-linq-to-xml"></a>Comment projeter un type anonyme (LINQ to XML)

Dans certains cas, vous souhaiterez peut-être projeter une requête vers un nouveau type, mais la requête serait votre seule utilisation pour le nouveau type. Au lieu de créer le type, vous pouvez projeter vers un type anonyme. Les types anonymes offrent un moyen pratique d’encapsuler un jeu de propriétés en lecture seule dans un objet sans avoir à définir explicitement un type d’abord. Si vous écrivez une requête qui crée un objet d’un type anonyme dans la `select` clause, la requête retourne un <xref:System.Collections.IEnumerable> du type.

L’exemple suivant illustre la création d’un objet d’un type anonyme qui est initialisé avec deux propriétés, `Amount` et `Message` .

```csharp
var v = new { Amount = 108, Message = "Hello" };
```

```vb
Dim v = New With { .Amount = 108, .Message = "Hello" };
```

Le type de chaque propriété est déduit par le compilateur. Le nom du type est généré par le compilateur et n’est pas disponible au niveau du code source.

Pour plus d’informations sur les types anonymes, consultez :

- [Types anonymes (Guide de programmation C#)](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [Types anonymes (Visual Basic)](../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)

## <a name="example-project-an-anonymous-type-by-creating-objects-in-the-select-clause"></a>Exemple : projeter un type anonyme en créant des objets dans la `select` clause

Dans cet exemple, la clause `select` projette un type anonyme. L'exemple utilise ensuite `var` pour créer l'objet `IEnumerable`. Dans la boucle `foreach`, la variable d'itération devient une instance du type anonyme créé dans l'expression de la requête.

Cet exemple utilise le document XML [exemple de fichier XML : Customers et Orders](sample-xml-file-customers-orders.md).

```csharp
XElement custOrd = XElement.Load("CustomersOrders.xml");
var custList =
    from el in custOrd.Element("Customers").Elements("Customer")
    select new {
        CustomerID = (string)el.Attribute("CustomerID"),
        CompanyName = (string)el.Element("CompanyName"),
        ContactName = (string)el.Element("ContactName")
    };
foreach (var cust in custList)
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName);
```

```vb
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")
Dim custList = _
    From el In custOrd.<Customers>.<Customer> _
    Select New With { _
        .CustomerID = el.@<CustomerID>, _
        .CompanyName = el.<CompanyName>.Value, _
        .ContactName = el.<ContactName>.Value _
    }
For Each cust In custList
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName)
Next
```

Cet exemple produit la sortie suivante :

```output
GREAL:Great Lakes Food Market:Howard Snyder
HUNGC:Hungry Coyote Import Store:Yoshi Latimer
LAZYK:Lazy K Kountry Store:John Steel
LETSS:Let's Stop N Shop:Jaime Yorres
```

## <a name="see-also"></a>Voir aussi

- [Types anonymes (Guide de programmation C#)](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [Types anonymes (Visual Basic)](../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
