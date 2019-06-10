---
title: 'Procédure : Rechercher des éléments dans un espace de noms (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: cae1c4ac-6cd5-46cf-9b1c-bd85bc9b7ea9
ms.openlocfilehash: 63f3d883964df4a94bb30ad78f50f814562840a4
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690049"
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-c"></a><span data-ttu-id="cb636-102">Procédure : Rechercher des éléments dans un espace de noms (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="cb636-102">How to: Find Elements in a Namespace (XPath-LINQ to XML) (C#)</span></span>

<span data-ttu-id="cb636-103">Les expressions XPath peuvent rechercher des nœuds dans un espace de noms particulier.</span><span class="sxs-lookup"><span data-stu-id="cb636-103">XPath expressions can find nodes in a particular namespace.</span></span> <span data-ttu-id="cb636-104">Les expressions XPath utilisent des préfixes d'espaces de noms pour spécifier des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="cb636-104">XPath expressions use namespace prefixes for specifying namespaces.</span></span> <span data-ttu-id="cb636-105">Pour analyser une expression XPath qui contient des préfixes d'espaces de noms, vous devez passer un objet aux méthodes XPath qui implémente <xref:System.Xml.IXmlNamespaceResolver>.</span><span class="sxs-lookup"><span data-stu-id="cb636-105">To parse an XPath expression that contains namespace prefixes, you must pass an object to the XPath methods that implements <xref:System.Xml.IXmlNamespaceResolver>.</span></span> <span data-ttu-id="cb636-106">Cet exemple utilise <xref:System.Xml.XmlNamespaceManager>.</span><span class="sxs-lookup"><span data-stu-id="cb636-106">This example uses <xref:System.Xml.XmlNamespaceManager>.</span></span>

<span data-ttu-id="cb636-107">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="cb636-107">The XPath expression is:</span></span>

`./aw:*`

## <a name="example"></a><span data-ttu-id="cb636-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="cb636-108">Example</span></span>

<span data-ttu-id="cb636-109">L’exemple suivant lit une arborescence XML qui contient deux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="cb636-109">The following example reads an XML tree that contains two namespaces.</span></span> <span data-ttu-id="cb636-110">Il utilise un objet <xref:System.Xml.XmlReader> pour lire le document XML.</span><span class="sxs-lookup"><span data-stu-id="cb636-110">It uses an <xref:System.Xml.XmlReader> to read the XML document.</span></span> <span data-ttu-id="cb636-111">Il obtient ensuite un objet <xref:System.Xml.XmlNameTable> à partir de l'objet <xref:System.Xml.XmlReader> et un objet<xref:System.Xml.XmlNamespaceManager> à partir de l'objet <xref:System.Xml.XmlNameTable>.</span><span class="sxs-lookup"><span data-stu-id="cb636-111">It then gets an <xref:System.Xml.XmlNameTable> from the <xref:System.Xml.XmlReader>, and an <xref:System.Xml.XmlNamespaceManager> from the <xref:System.Xml.XmlNameTable>.</span></span> <span data-ttu-id="cb636-112">Il utilise l'objet <xref:System.Xml.XmlNamespaceManager> lors de la sélection des éléments.</span><span class="sxs-lookup"><span data-stu-id="cb636-112">It uses the <xref:System.Xml.XmlNamespaceManager> when selecting elements.</span></span>

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

<span data-ttu-id="cb636-113">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="cb636-113">This example produces the following output:</span></span>

```
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
