---
title: Comment écrire des requêtes avec un filtrage complexe-LINQ to XML
description: Il peut arriver que vous souhaitiez écrire des requêtes LINQ to XML à l'aide de filtres complexes. Par exemple, il se peut que vous deviez rechercher tous les éléments qui ont un élément enfant avec un nom et une valeur spécifiques.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: c5e7f812364e7e96e3a4b8f5515d07a3524ec979
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553809"
---
# <a name="how-to-write-queries-with-complex-filtering-linq-to-xml"></a>Comment écrire des requêtes avec un filtrage complexe (LINQ to XML)

Il peut arriver que vous souhaitiez écrire des requêtes LINQ to XML à l'aide de filtres complexes. Par exemple, il se peut que vous deviez rechercher tous les éléments qui ont un élément enfant avec un nom et une valeur spécifiques. Cet article donne un exemple d’écriture d’une requête avec un filtrage complexe.

## <a name="example-find-with-a-nested-query-in-the-where-clause"></a>Exemple : Rechercher avec une requête imbriquée dans la `Where` clause

Cet exemple montre comment rechercher tous les `PurchaseOrder` éléments qui ont :

- Élément enfant `Address` dont l' `Type` attribut est égal à « Shipping ».
- Élément enfant `State` qui est égal à « NY ».

Il utilise une sous-requête dans la clause `Where` et l'opérateur `Any` retourne `true` si la collection possède des éléments. L’exemple utilise un document XML [exemple de fichier XML : plusieurs commandes fournisseur](sample-xml-file-multiple-purchase-orders.md).

Pour plus d’informations sur l' `Any` opérateur, consultez [opérations de quantificateur (C#)](../../../docs/csharp/programming-guide/concepts/linq/quantifier-operations.md) et [opérations de quantificateur (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).

```csharp
XElement root = XElement.Load("PurchaseOrders.xml");
IEnumerable<XElement> purchaseOrders =
    from el in root.Elements("PurchaseOrder")
    where
        (from add in el.Elements("Address")
        where
            (string)add.Attribute("Type") == "Shipping" &&
            (string)add.Element("State") == "NY"
        select add)
        .Any()
    select el;
foreach (XElement el in purchaseOrders)
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));
```

```vb
Dim root As XElement = XElement.Load("PurchaseOrders.xml")
Dim purchaseOrders As IEnumerable(Of XElement) = _
    From el In root.<PurchaseOrder> _
    Where _
        (From add In el.<Address> _
        Where _
             add.@Type = "Shipping" And _
             add.<State>.Value = "NY" _
        Select add) _
    .Any() _
    Select el
For Each el As XElement In purchaseOrders
    Console.WriteLine(el.@PurchaseOrderNumber)
Next
```

Cet exemple produit la sortie suivante :

```output
99505
```

## <a name="example-find-in-xml-thats-in-a-namespace"></a>Exemple : Rechercher dans du code XML qui se trouve dans un espace de noms

L’exemple suivant illustre la même requête que ci-dessus, mais pour le code XML qui se trouve dans un espace de noms. Pour plus d’informations, consultez [vue d’ensemble des espaces de noms](namespaces-overview.md).

Cet exemple utilise le document XML [exemple de fichier XML : plusieurs commandes fournisseur dans un espace de noms](sample-xml-file-multiple-purchase-orders-namespace.md).

```csharp
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> purchaseOrders =
    from el in root.Elements(aw + "PurchaseOrder")
    where
        (from add in el.Elements(aw + "Address")
         where
             (string)add.Attribute(aw + "Type") == "Shipping" &&
             (string)add.Element(aw + "State") == "NY"
         select add)
        .Any()
    select el;
foreach (XElement el in purchaseOrders)
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));
```

```vb
Imports <xmlns:aw='http://www.adventure-works.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")
        Dim purchaseOrders As IEnumerable(Of XElement) = _
            From el In root.<aw:PurchaseOrder> _
            Where _
                (From add In el.<aw:Address> _
                Where _
                     add.@aw:Type = "Shipping" And _
                     add.<aw:State>.Value = "NY" _
                Select add) _
            .Any() _
            Select el
        For Each el As XElement In purchaseOrders
            Console.WriteLine(el.@aw:PurchaseOrderNumber)
        Next
    End Sub
End Module
```

Cet exemple produit la sortie suivante :

```output
99505
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Opérations de projection (C#)](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [Opérations de quantificateur (C#)](../../csharp/programming-guide/concepts/linq/quantifier-operations.md)
- [Propriété d'axe enfant XML (Visual Basic)](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [Propriété d'axe d'attribut XML (Visual Basic)](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [Propriété de valeur XML (Visual Basic)](../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Opérations de projection (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
- [Opérations de quantificateur (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
