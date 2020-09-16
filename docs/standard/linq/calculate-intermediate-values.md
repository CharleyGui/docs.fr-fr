---
title: Comment calculer des valeurs intermédiaires-LINQ to XML
description: Calculez les valeurs intermédiaires à utiliser pour le tri, le filtrage et la sélection.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: c37926b93e0dc11255fd27c312679f6286fa7e5d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558117"
---
# <a name="how-to-calculate-intermediate-values-linq-to-xml"></a>Comment calculer des valeurs intermédiaires (LINQ to XML)

Cet article montre comment calculer des valeurs intermédiaires à utiliser pour le tri, le filtrage et la sélection en C# et Visual Basic.

## <a name="example-use-the-let-clause-to-calculate-based-on-element-data"></a>Exemple : utiliser la `let` clause pour calculer en fonction des données d’élément

L’exemple suivant utilise la `let` clause pour calculer des produits de valeurs numériques à partir d’éléments. Il utilise le document XML [exemple de fichier XML : données numériques](sample-xml-file-numerical-data.md).

```csharp
XElement root = XElement.Load("Data.xml");
IEnumerable<decimal> extensions =
    from el in root.Elements("Data")
    let extension = (decimal)el.Element("Quantity") * (decimal)el.Element("Price")
    where extension >= 25
    orderby extension
    select extension;
foreach (decimal ex in extensions)
    Console.WriteLine(ex);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim extensions As IEnumerable(Of Decimal) = _
    From el In root.<Data> _
    Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _
    Where extension > 25 _
    Order By extension _
    Select extension
For Each ex As Decimal In extensions
    Console.WriteLine(ex)
Next
```

Cet exemple produit la sortie suivante :

```output
55.92
73.50
89.99
198.00
435.00
```

## <a name="example-calculate-from-xml-thats-in-a-namespace"></a>Exemple : calculer à partir du code XML qui se trouve dans un espace de noms

L’exemple suivant illustre la même requête que précédemment, mais pour le code XML qui se trouve dans un espace de noms. Elle utilise le document XML [exemple de fichier XML : données numériques dans un espace de noms](sample-xml-file-numerical-data-namespace.md).

Pour plus d’informations, consultez [vue d’ensemble des espaces de noms](namespaces-overview.md).

```csharp
XElement root = XElement.Load("DataInNamespace.xml");
XNamespace ad = "http://www.adatum.com";
IEnumerable<decimal> extensions =
    from el in root.Elements(ad + "Data")
    let extension = (decimal)el.Element(ad + "Quantity") * (decimal)el.Element(ad + "Price")
    where extension >= 25
    orderby extension
    select extension;
foreach (decimal ex in extensions)
    Console.WriteLine(ex);
```

```vb
Imports <xmlns="http://www.adatum.com">

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("DataInNamespace.xml")
        Dim extensions As IEnumerable(Of Decimal) = _
            From el In root.<Data> _
            Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _
            Where extension > 25 _
            Order By extension _
            Select extension
        For Each ex As Decimal In extensions
            Console.WriteLine(ex)
        Next
    End Sub
End Module
```

Cet exemple produit la sortie suivante :

```output
55.92
73.50
89.99
198.00
435.00
```

## <a name="see-also"></a>Voir aussi

- [Requêtes de base (LINQ to XML) (Visual Basic)](./find-element-specific-attribute.md)
