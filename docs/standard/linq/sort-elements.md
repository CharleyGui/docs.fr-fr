---
title: Comment trier des éléments-LINQ to XML
description: Découvrez comment écrire une requête qui trie ses résultats.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 0e93add12e39c71c7312036917d42dd53450b712
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550068"
---
# <a name="how-to-sort-elements-linq-to-xml"></a>Comment trier des éléments (LINQ to XML)

Vous pouvez trier vos résultats lorsque vous interrogez XML. Cet article fournit deux exemples : le premier trie les résultats pour le code XML qui *n’est pas* dans un espace de noms et le second effectue le même tri, mais pour le code XML qui *se trouve* dans un espace de noms.

## <a name="example-write-a-query-that-sorts-its-results"></a>Exemple : écrire une requête qui trie ses résultats

Cet exemple montre comment écrire une requête qui trie ses résultats. Il utilise le document XML [exemple de fichier XML : données numériques](sample-xml-file-numerical-data.md).

```csharp
XElement root = XElement.Load("Data.xml");
IEnumerable<decimal> prices =
    from el in root.Elements("Data")
    let price = (decimal)el.Element("Price")
    orderby price
    select price;
foreach (decimal el in prices)
    Console.WriteLine(el);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim prices As IEnumerable(Of Decimal) = _
    From el In root.<Data> _
    Let price = Convert.ToDecimal(el.<Price>.Value) _
    Order By (price) _
    Select price
For Each el As Decimal In prices
    Console.WriteLine(el)
Next
```

Cet exemple produit la sortie suivante :

```output
0.99
4.95
6.99
24.50
29.00
66.00
89.99
```

## <a name="example-write-a-query-in-a-namespace-that-sorts-its-results"></a>Exemple : écrire une requête dans un espace de noms qui trie ses résultats

L’exemple suivant illustre la même requête pour du code XML qui se trouve dans un espace de noms. Il utilise le document XML [exemple de fichier XML : données numériques dans un espace de noms](sample-xml-file-numerical-data-namespace.md).

Pour plus d’informations, consultez [vue d’ensemble des espaces de noms](namespaces-overview.md).

```csharp
XElement root = XElement.Load("DataInNamespace.xml");
XNamespace aw = "http://www.adatum.com";
IEnumerable<decimal> prices =
    from el in root.Elements(aw + "Data")
    let price = (decimal)el.Element(aw + "Price")
    orderby price
    select price;
foreach (decimal el in prices)
    Console.WriteLine(el);
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("DataInNamespace.xml")
        Dim prices As IEnumerable(Of Decimal) = _
            From el In root.<Data> _
            Let price = Convert.ToDecimal(el.<Price>.Value) _
            Order By (price) _
            Select price
        For Each el As Decimal In prices
            Console.WriteLine(el)
        Next
    End Sub
End Module
```

Cet exemple produit la sortie suivante :

```output
0.99
4.95
6.99
24.50
29.00
66.00
89.99
```

## <a name="see-also"></a>Voir aussi

- [Tri des données (C#)](../../csharp/programming-guide/concepts/linq/sorting-data.md)
- [Tri des données (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/sorting-data.md)
- [Requêtes de base (LINQ to XML) (Visual Basic)](./find-element-specific-attribute.md)
