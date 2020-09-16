---
title: Comment rechercher un élément avec un attribut spécifique-LINQ to XML
description: Découvrez comment rechercher un élément dont l’attribut a une valeur spécifique.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
ms.openlocfilehash: a1569f8a91e980f12ecc1801e00d6414711833d0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535459"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-linq-to-xml"></a>Comment rechercher un élément avec un attribut spécifique (LINQ to XML)

Cet article fournit des exemples de recherche d’un élément dont l’attribut a une valeur spécifique.

## <a name="example-find-an-element-whose-attribute-has-a-specific-value"></a>Exemple : Rechercher un élément dont l’attribut a une valeur spécifique

L’exemple suivant montre comment Rechercher l' `Address` élément qui a un `Type` attribut avec la valeur « Billing ». L’exemple utilise un document XML [exemple de fichier XML : commande fournisseur typique](sample-xml-file-typical-purchase-order.md).

```csharp
XElement root = XElement.Load("PurchaseOrder.xml");
IEnumerable<XElement> address =
    from el in root.Elements("Address")
    where (string)el.Attribute("Type") == "Billing"
    select el;
foreach (XElement el in address)
    Console.WriteLine(el);
```

```vb
Dim root As XElement = XElement.Load("PurchaseOrder.xml")
Dim address As IEnumerable(Of XElement) = _
    From el In root.<Address> _
    Where el.@Type = "Billing" _
    Select el
For Each el As XElement In address
    Console.WriteLine(el)
Next
```

Cet exemple produit la sortie suivante :

```xml
<Address Type="Billing">
  <Name>Tai Yee</Name>
  <Street>8 Oak Avenue</Street>
  <City>Old Town</City>
  <State>PA</State>
  <Zip>95819</Zip>
  <Country>USA</Country>
</Address>
```

## <a name="example-find-an-element-in-xml-thats-in-a-namespace"></a>Exemple : Rechercher un élément dans du code XML qui se trouve dans un espace de noms

L’exemple suivant illustre la même requête, mais pour le code XML qui se trouve dans un espace de noms. Elle utilise un document XML [exemple de fichier XML : commande fournisseur typique dans un espace de noms](sample-xml-file-typical-purchase-order-namespace.md).

Pour plus d’informations sur les espaces de noms, consultez [vue d’ensemble des espaces](namespaces-overview.md)de noms.

```csharp
XElement root = XElement.Load("PurchaseOrderInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> address =
    from el in root.Elements(aw + "Address")
    where (string)el.Attribute(aw + "Type") == "Billing"
    select el;
foreach (XElement el in address)
    Console.WriteLine(el);
```

```vb
Imports <xmlns:aw='http://www.adventure-works.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("PurchaseOrderInNamespace.xml")
        Dim address As IEnumerable(Of XElement) = _
            From el In root.<aw:Address> _
            Where el.@aw:Type = "Billing" _
            Select el
        For Each el As XElement In address
            Console.WriteLine(el)
        Next
    End Sub
End Module
```

Cet exemple produit la sortie suivante ::

```xml
<aw:Address aw:Type="Billing" xmlns:aw="http://www.adventure-works.com">
  <aw:Name>Tai Yee</aw:Name>
  <aw:Street>8 Oak Avenue</aw:Street>
  <aw:City>Old Town</aw:City>
  <aw:State>PA</aw:State>
  <aw:Zip>95819</aw:Zip>
  <aw:Country>USA</aw:Country>
</aw:Address>
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Vue d’ensemble des opérateurs de requête standard (C#)](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Opérations de projection (C#)](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [Requêtes de base (LINQ to XML) (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)
- [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Opérations de projection (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
