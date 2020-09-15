---
title: Recherche d’un élément enfant-LINQ to XML
description: Cet article compare l’axe des éléments enfants XPath à la <xref:System.Xml.Linq.XContainer.Element%2A> méthode LINQ to XML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4fa6182d-6196-4ed1-9c9e-82949ff89c71
ms.openlocfilehash: 908cf230027b3092e6e7bbaffb1d7e6af8c061ec
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553856"
---
# <a name="how-to-find-a-child-element-linq-to-xml"></a><span data-ttu-id="144d9-103">Comment rechercher un élément enfant (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="144d9-103">How to find a child element (LINQ to XML)</span></span>

<span data-ttu-id="144d9-104">Cet article compare l’axe des éléments enfants XPath à la <xref:System.Xml.Linq.XContainer.Element%2A> méthode LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="144d9-104">This article compares the XPath child element axis to the LINQ to XML <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>

## <a name="example-find-a-child-element-in-an-xml-document"></a><span data-ttu-id="144d9-105">Exemple : Rechercher un élément enfant dans un document XML</span><span class="sxs-lookup"><span data-stu-id="144d9-105">Example: Find a child element in an XML document</span></span>

<span data-ttu-id="144d9-106">Cet exemple recherche l’élément enfant `DeliveryNotes` dans le document XML [exemple de fichier XML : plusieurs commandes fournisseur](sample-xml-file-multiple-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="144d9-106">This example finds the child element `DeliveryNotes` in XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span>

<span data-ttu-id="144d9-107">L'expression XPath est `DeliveryNotes`.</span><span class="sxs-lookup"><span data-stu-id="144d9-107">The XPath expression is `DeliveryNotes`.</span></span>

```csharp
XDocument cpo = XDocument.Load("PurchaseOrders.xml");
XElement po = cpo.Root.Element("PurchaseOrder");

// LINQ to XML query
XElement el1 = po.Element("DeliveryNotes");

// XPath expression
XElement el2 = po.XPathSelectElement("DeliveryNotes");
// same as "child::DeliveryNotes"
// same as "./DeliveryNotes"

if (el1 == el2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(el1);
```

```vb
Dim cpo As XDocument = XDocument.Load("PurchaseOrders.xml")
Dim po As XElement = cpo.Root.<PurchaseOrder>.FirstOrDefault

'LINQ to XML query
Dim el1 As XElement = po.<DeliveryNotes>.FirstOrDefault

' XPath expression
Dim el2 As XElement = po.XPathSelectElement("DeliveryNotes")
' same as "child::DeliveryNotes"
' same as "./DeliveryNotes"

If el1 Is el2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(el1)
```

<span data-ttu-id="144d9-108">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="144d9-108">This example produces the following output:</span></span>

```output
Results are identical
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>
```

## <a name="see-also"></a><span data-ttu-id="144d9-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="144d9-109">See also</span></span>

- [<span data-ttu-id="144d9-110">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="144d9-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)