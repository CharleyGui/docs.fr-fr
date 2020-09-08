---
title: Récupération d’un seul élément enfant-LINQ to XML
description: Récupère le premier élément enfant ayant un nom spécifié. Vous pouvez utiliser XContainer. Element en C# et la notation d’indexeur de tableau dans Visual Basic.
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: e557e82e4e5891d6890a0efb4973796050b75349
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553653"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml"></a>Comment récupérer un seul élément enfant (LINQ to XML)

Cet article explique comment récupérer un seul élément enfant, le premier élément enfant portant un nom spécifié. En C#, vous effectuez cette opération avec la <xref:System.Xml.Linq.XContainer.Element%2A> méthode. Dans Visual Basic vous le faites avec la notation d’indexeur de tableau.

## <a name="example-retrieve-the-first-element-that-has-a-specified-name"></a>Exemple : récupérer le premier élément qui porte un nom spécifié

L’exemple suivant récupère le premier `DeliveryNotes` élément du document XML dans exemple de [fichier XML : commande fournisseur typique](sample-xml-file-typical-purchase-order.md).

```csharp
XElement po = XElement.Load("PurchaseOrder.xml");
XElement e = po.Element("DeliveryNotes");
Console.WriteLine(e);
```

```vb
Dim po As XElement = XElement.Load("PurchaseOrder.xml")
Dim e As XElement = po.<DeliveryNotes>(0)
Console.WriteLine(e)
```

Cet exemple produit la sortie suivante :

```xml
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>
```

## <a name="example-retrieve-from-xml-thats-in-a-namespace"></a>Exemple : récupérer à partir du code XML qui se trouve dans un espace de noms

L’exemple suivant fait la même chose que l’exemple ci-dessus, mais pour le code XML qui se trouve dans un espace de noms. Elle utilise le document XML [exemple de fichier XML : commande fournisseur typique dans un espace de noms](sample-xml-file-typical-purchase-order-namespace.md). Pour plus d’informations sur les espaces de noms, consultez [vue d’ensemble des espaces](namespaces-overview.md)de noms.

```csharp
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
XElement e = po.Element(aw + "DeliveryNotes");
Console.WriteLine(e);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")
        Dim e As XElement = po.<aw:DeliveryNotes>(0)
        Console.WriteLine(e)
    End Sub
End Module
```

Cet exemple produit la sortie suivante :

```xml
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des axes LINQ to XML](linq-xml-axes-overview.md)
