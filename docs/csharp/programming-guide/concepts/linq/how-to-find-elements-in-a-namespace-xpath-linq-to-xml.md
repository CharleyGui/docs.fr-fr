---
title: Guide pratique pour rechercher des éléments dans un espace de noms (XPath-LINQ to XML) (C#)
description: Découvrez comment rechercher des éléments dans un espace de noms à l’aide d’une expression XPath. Consultez un exemple qui lit une arborescence XML contenant deux espaces de noms.
ms.date: 07/20/2015
ms.assetid: cae1c4ac-6cd5-46cf-9b1c-bd85bc9b7ea9
ms.openlocfilehash: 3bf15c4183e3ca339fa7090c21baff83526e37d3
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303229"
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-c"></a>Guide pratique pour rechercher des éléments dans un espace de noms (XPath-LINQ to XML) (C#)

Les expressions XPath peuvent rechercher des nœuds dans un espace de noms particulier. Les expressions XPath utilisent des préfixes d’espaces de noms pour spécifier des espaces de noms. Pour analyser une expression XPath qui contient des préfixes d'espaces de noms, vous devez passer un objet aux méthodes XPath qui implémente <xref:System.Xml.IXmlNamespaceResolver>. Cet exemple utilise <xref:System.Xml.XmlNamespaceManager>.

L’expression XPath est la suivante :

`./aw:*`

## <a name="example"></a>Exemple

L’exemple suivant lit une arborescence XML qui contient deux espaces de noms. Il utilise un objet <xref:System.Xml.XmlReader> pour lire le document XML. Il obtient ensuite un objet <xref:System.Xml.XmlNameTable> à partir de l'objet <xref:System.Xml.XmlReader> et un objet<xref:System.Xml.XmlNamespaceManager> à partir de l'objet <xref:System.Xml.XmlNameTable>. Il utilise l'objet <xref:System.Xml.XmlNamespaceManager> lors de la sélection des éléments.

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

Cet exemple produit la sortie suivante :

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
