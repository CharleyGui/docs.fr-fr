---
title: Guide pratique pour rechercher des éléments dans un espace de noms-LINQ to XML
description: Découvrez comment rechercher des éléments dans un espace de noms particulier en utilisant des préfixes d’espaces de noms dans les expressions XPath.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: cae1c4ac-6cd5-46cf-9b1c-bd85bc9b7ea9m
ms.openlocfilehash: d463aed02a9293ca85e77f262ccfb8fdce5976b1
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552348"
---
# <a name="how-to-find-elements-in-a-namespace-linq-to-xml"></a><span data-ttu-id="3194a-103">Comment rechercher des éléments dans un espace de noms (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="3194a-103">How to find elements in a namespace (LINQ to XML)</span></span>

<span data-ttu-id="3194a-104">Utilisez des préfixes d’espaces de noms dans les expressions XPath pour rechercher des nœuds dans un espace de noms particulier.</span><span class="sxs-lookup"><span data-stu-id="3194a-104">Use namespace prefixes in XPath expressions to find nodes in a particular namespace.</span></span> <span data-ttu-id="3194a-105">Pour analyser une expression XPath qui contient des préfixes d’espaces de noms, vous devez passer un objet aux méthodes XPath qui implémentent <xref:System.Xml.IXmlNamespaceResolver> .</span><span class="sxs-lookup"><span data-stu-id="3194a-105">To parse an XPath expression that contains namespace prefixes, you pass an object to the XPath methods that implement <xref:System.Xml.IXmlNamespaceResolver>.</span></span>

## <a name="example-find-purchase-orders-from-a-specific-namespace-in-a-document-that-has-two-namespaces"></a><span data-ttu-id="3194a-106">Exemple : Rechercher des bons de commande à partir d’un espace de noms spécifique dans un document qui a deux espaces de noms</span><span class="sxs-lookup"><span data-stu-id="3194a-106">Example: Find purchase orders from a specific namespace in a document that has two namespaces</span></span>

<span data-ttu-id="3194a-107">L’exemple suivant utilise un <xref:System.Xml.XmlReader> pour lire le document XML [exemple de fichier XML : commandes fournisseur consolidées](sample-xml-file-consolidated-purchase-orders.md), qui ont des bons de commande dans deux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="3194a-107">The following example uses an <xref:System.Xml.XmlReader> to read XML document [Sample XML file: Consolidated purchase orders](sample-xml-file-consolidated-purchase-orders.md), which has purchase orders in two namespaces.</span></span> <span data-ttu-id="3194a-108">Il obtient ensuite un objet <xref:System.Xml.XmlNameTable> à partir de l'objet <xref:System.Xml.XmlReader> et un objet<xref:System.Xml.XmlNamespaceManager> à partir de l'objet <xref:System.Xml.XmlNameTable>.</span><span class="sxs-lookup"><span data-stu-id="3194a-108">It then gets an <xref:System.Xml.XmlNameTable> from the <xref:System.Xml.XmlReader>, and an <xref:System.Xml.XmlNamespaceManager> from the <xref:System.Xml.XmlNameTable>.</span></span> <span data-ttu-id="3194a-109">Il utilise l'objet <xref:System.Xml.XmlNamespaceManager> lors de la sélection des éléments.</span><span class="sxs-lookup"><span data-stu-id="3194a-109">It uses the <xref:System.Xml.XmlNamespaceManager> when selecting elements.</span></span>

<span data-ttu-id="3194a-110">L'expression XPath est la suivante : `./aw:*`</span><span class="sxs-lookup"><span data-stu-id="3194a-110">The XPath expression is: `./aw:*`</span></span>

```csharp
XmlReader reader = XmlReader.Create("ConsolidatedPurchaseOrders.xml");
XElement root = XElement.Load(reader);
XmlNameTable nameTable = reader.NameTable;
XmlNamespaceManager namespaceManager = new XmlNamespaceManager(nameTable);
namespaceManager.AddNamespace("aw", "http://www.adventure-works.com");
IEnumerable<XElement> list1 = root.XPathSelectElements("./aw:*", namespaceManager);
IEnumerable<XElement> list2 =
    from el in root.Elements()
    where el.Name.Namespace == "http://www.adventure-works.com"
    select el;
if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list2)
    Console.WriteLine(el);
```

```vb
Dim reader As XmlReader = _
        XmlReader.Create("ConsolidatedPurchaseOrders.xml")
Dim root As XElement = XElement.Load(reader)
Dim nameTable As XmlNameTable = reader.NameTable
Dim namespaceManager As XmlNamespaceManager = New XmlNamespaceManager(nameTable)
namespaceManager.AddNamespace("aw", "http://www.adventure-works.com")

Dim list1 As IEnumerable(Of XElement) = _
        root.XPathSelectElements("./aw:*", namespaceManager)
Dim list2 As IEnumerable(Of XElement) = _
    From el In root.Elements() _
    Where el.Name.Namespace = "http://www.adventure-works.com" _
    Select el

If list1.Count() = list2.Count() And _
        list1.Intersect(list2).Count() = list1.Count() Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
For Each el As XElement In list2
    Console.WriteLine(el)
Next
```

<span data-ttu-id="3194a-111">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="3194a-111">This example produces the following output:</span></span>

```output
Results are identical
<aw:PurchaseOrder PONumber="11223" Date="2000-01-15" xmlns:aw="http://www.adventure-works.com">
    <aw:ShippingAddress>
      <aw:Name>Chris Preston</aw:Name>
      <aw:Street>123 Main St.</aw:Street>
      <aw:City>Seattle</aw:City>
      <aw:State>WA</aw:State>
      <aw:Zip>98113</aw:Zip>
      <aw:Country>USA</aw:Country>
    </aw:ShippingAddress>
    <aw:BillingAddress>
      <aw:Name>Chris Preston</aw:Name>
      <aw:Street>123 Main St.</aw:Street>
      <aw:City>Seattle</aw:City>
      <aw:State>WA</aw:State>
      <aw:Zip>98113</aw:Zip>
      <aw:Country>USA</aw:Country>
    </aw:BillingAddress>
    <aw:DeliveryInstructions>Ship only complete order.</aw:DeliveryInstructions>
    <aw:Item PartNum="LIT-01">
      <aw:ProductID>Litware Networking Card</aw:ProductID>
      <aw:Qty>1</aw:Qty>
      <aw:Price>20.99</aw:Price>
    </aw:Item>
    <aw:Item PartNum="LIT-25">
      <aw:ProductID>Litware 17in LCD Monitor</aw:ProductID>
      <aw:Qty>1</aw:Qty>
      <aw:Price>199.99</aw:Price>
    </aw:Item>
  </aw:PurchaseOrder>
```

## <a name="see-also"></a><span data-ttu-id="3194a-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3194a-112">See also</span></span>

- [<span data-ttu-id="3194a-113">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3194a-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
