---
title: Comment récupérer une collection d’éléments-LINQ to XML
description: Apprenez à utiliser la méthode XContainer. Elements pour récupérer une collection d’éléments enfants d’un élément.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: e73f608cff13f75f769f77372dc1c09949e00b0e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552412"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml"></a>Comment récupérer une collection d’éléments (LINQ to XML)

Cet article décrit la <xref:System.Xml.Linq.XContainer.Elements%2A> méthode, qui récupère une collection des éléments enfants d’un élément.

## <a name="example-iterate-through-the-child-elements-of-an-element"></a>Exemple : itérer au sein des éléments enfants d’un élément

Cet exemple itère au sein des éléments enfants de l'élément `purchaseOrder`. Il utilise le document XML [exemple de fichier XML : bon de commande standard](sample-xml-file-typical-purchase-order.md).

```csharp
XElement po = XElement.Load("PurchaseOrder.xml");
IEnumerable<XElement> childElements =
    from el in po.Elements()
    select el;
foreach (XElement el in childElements)
    Console.WriteLine("Name: " + el.Name);
```

```vb
Dim po As XElement = XElement.Load("PurchaseOrder.xml")
Dim childElements As IEnumerable(Of XElement)
childElements = _
    From el In po.Elements() _
    Select el
For Each el As XElement In childElements
    Console.WriteLine("Name: " & el.Name.ToString())
Next
```

Cet exemple produit la sortie suivante :

```output
Name: Address
Name: Address
Name: DeliveryNotes
Name: Items
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des axes LINQ to XML](linq-xml-axes-overview.md)
