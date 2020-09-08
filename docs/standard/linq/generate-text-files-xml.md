---
title: Comment générer des fichiers texte à partir d’un fichier XML-LINQ to XML
description: Vous pouvez utiliser C# et Visual Basic pour générer un fichier texte de valeurs séparées par des virgules (CSV) à partir d’un fichier XML. Cet article fournit un exemple.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 9ad283f7-7cac-42ff-bf32-92aa866e6883
ms.openlocfilehash: 2650d223d542b3582fa8cd2a00f4b880ef04e5dc
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552425"
---
# <a name="how-to-generate-text-files-from-xml-linq-to-xml"></a>Comment générer des fichiers texte à partir de XML (LINQ to XML)

Cet article fournit un exemple qui montre comment utiliser C# et Visual Basic pour générer un fichier texte de valeurs séparées par des virgules (CSV) à partir d’un fichier XML.

## <a name="example-generate-a-csv-file-from-an-xml-document"></a>Exemple : génération d’un fichier CSV à partir d’un document XML

Cet exemple génère un fichier CSV à partir d’un document XML [exemple de fichier XML : clients et commandes](sample-xml-file-customers-orders.md).

La version C# utilise la syntaxe de méthode et l' `Aggregate` opérateur pour générer le fichier dans une expression unique. Pour plus d’informations, consultez syntaxe [de requête et syntaxe de méthode dans LINQ (C#)](../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).

La version Visual Basic utilise du code procédural pour agréger la collection de chaînes en une seule chaîne.

```csharp
XElement custOrd = XElement.Load("CustomersOrders.xml");
string csv =
    (from el in custOrd.Element("Customers").Elements("Customer")
    select
        String.Format("{0},{1},{2},{3},{4},{5},{6},{7},{8},{9}{10}",
            (string)el.Attribute("CustomerID"),
            (string)el.Element("CompanyName"),
            (string)el.Element("ContactName"),
            (string)el.Element("ContactTitle"),
            (string)el.Element("Phone"),
            (string)el.Element("FullAddress").Element("Address"),
            (string)el.Element("FullAddress").Element("City"),
            (string)el.Element("FullAddress").Element("Region"),
            (string)el.Element("FullAddress").Element("PostalCode"),
            (string)el.Element("FullAddress").Element("Country"),
            Environment.NewLine
        )
    )
    .Aggregate(
        new StringBuilder(),
        (sb, s) => sb.Append(s),
        sb => sb.ToString()
    );
Console.WriteLine(csv);
```

```vb
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")
Dim strCollection As IEnumerable(Of String) = _
    From el In custOrd.<Customers>.<Customer> _
    Select _
        String.Format("{0},{1},{2},{3},{4},{5},{6},{7},{8},{9}{10}", _
            el.@CustomerID, _
            el.<CompanyName>.Value, _
            el.<ContactName>.Value, _
            el.<ContactTitle>.Value, _
            el.<Phone>.Value, _
            el.<FullAddress>.<Address>.Value, _
            el.<FullAddress>.<City>.Value, _
            el.<FullAddress>.<Region>.Value, _
            el.<FullAddress>.<PostalCode>.Value, _
            el.<FullAddress>.<Country>.Value, _
            Environment.NewLine _
        )
Dim sb As StringBuilder = New StringBuilder()
For Each str As String In strCollection
    sb.Append(str)
Next
Console.WriteLine(sb.ToString())
```

Cet exemple produit la sortie suivante :

```output
GREAL,Great Lakes Food Market,Howard Snyder,Marketing Manager,(503) 555-7555,2732 Baker Blvd.,Eugene,OR,97403,USA
HUNGC,Hungry Coyote Import Store,Yoshi Latimer,Sales Representative,(503) 555-6874,City Center Plaza 516 Main St.,Elgin,OR,97827,USA
LAZYK,Lazy K Kountry Store,John Steel,Marketing Manager,(509) 555-7969,12 Orchestra Terrace,Walla Walla,WA,99362,USA
LETSS,Let's Stop N Shop,Jaime Yorres,Owner,(415) 555-5938,87 Polk St. Suite 5,San Francisco,CA,94117,USA
```

## <a name="see-also"></a>Voir aussi

- [Syntaxe de requête et syntaxe de méthode dans LINQ (C#)](../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
