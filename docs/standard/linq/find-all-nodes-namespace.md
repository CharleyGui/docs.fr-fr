---
title: Comment rechercher tous les nœuds dans un espace de noms-LINQ to XML
description: Vous pouvez filtrer sur l'espace de noms de chaque élément ou attribut afin de rechercher les nœuds dans cet espace de noms particulier.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3a38b913-a53e-4d0e-a19d-8782bffd3364
ms.openlocfilehash: 2041afc3e061aa89e9be5832c9d6fd5bab7a38d8
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552373"
---
# <a name="how-to-find-all-nodes-in-a-namespace-linq-to-xml"></a><span data-ttu-id="9dc65-103">Comment rechercher tous les nœuds dans un espace de noms (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="9dc65-103">How to find all nodes in a namespace (LINQ to XML)</span></span>

<span data-ttu-id="9dc65-104">Vous pouvez filtrer sur l'espace de noms de chaque élément ou attribut afin de rechercher les nœuds dans cet espace de noms particulier.</span><span class="sxs-lookup"><span data-stu-id="9dc65-104">You can filter on the namespace of each element or attribute to find all nodes in that particular namespace.</span></span>

## <a name="example-create-an-xml-tree-with-two-namespaces-and-print-contents-of-one"></a><span data-ttu-id="9dc65-105">Exemple : créer une arborescence XML avec deux espaces de noms et imprimer le contenu d’un</span><span class="sxs-lookup"><span data-stu-id="9dc65-105">Example: Create an XML tree with two namespaces, and print contents of one</span></span>

<span data-ttu-id="9dc65-106">L’exemple suivant crée une arborescence XML avec deux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="9dc65-106">The following example creates an XML tree with two namespaces.</span></span> <span data-ttu-id="9dc65-107">Il itère ensuite au sein de l'arborescence et imprime les noms de tous les éléments et attributs dans l'un de ces espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="9dc65-107">It then iterates through the tree and prints the names of all the elements and attributes in one of those namespaces.</span></span>

```csharp
string markup = @"<aw:Root xmlns:aw='http://www.adventure-works.com' xmlns:fc='www.fourthcoffee.com'>
  <fc:Child1>abc</fc:Child1>
  <fc:Child2>def</fc:Child2>
  <aw:Child3>ghi</aw:Child3>
  <fc:Child4>
    <fc:GrandChild1>jkl</fc:GrandChild1>
    <aw:GrandChild2>mno</aw:GrandChild2>
  </fc:Child4>
</aw:Root>";
XElement xmlTree = XElement.Parse(markup);
Console.WriteLine("Nodes in the http://www.adventure-works.com namespace");
IEnumerable<XElement> awElements =
    from el in xmlTree.Descendants()
    where el.Name.Namespace == "http://www.adventure-works.com"
    select el;
foreach (XElement el in awElements)
    Console.WriteLine(el.Name.ToString());
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1
    Sub Main()
        Dim xmlTree As XElement = _
            <aw:Root>
                <fc:Child1>abc</fc:Child1>
                <fc:Child2>def</fc:Child2>
                <aw:Child3>ghi</aw:Child3>
                <fc:Child4>
                    <fc:GrandChild1>jkl</fc:GrandChild1>
                    <aw:GrandChild2>mno</aw:GrandChild2>
                </fc:Child4>
            </aw:Root>
        Console.WriteLine("Nodes in the http://www.adventure-works.com namespace")
        Dim awElements As IEnumerable(Of XElement) = _
            From el In xmlTree.Descendants() _
            Where (el.Name.Namespace = GetXmlNamespace(aw)) _
            Select el
        For Each el As XElement In awElements
            Console.WriteLine(el.Name.ToString())
        Next
    End Sub
End Module
```

<span data-ttu-id="9dc65-108">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="9dc65-108">This example produces the following output:</span></span>

```output
Nodes in the http://www.adventure-works.com namespace
{http://www.adventure-works.com}Child3
{http://www.adventure-works.com}GrandChild2
```

## <a name="example-create-an-xml-tree-from-one-of-two-namespaces-contained-in-a-file"></a><span data-ttu-id="9dc65-109">Exemple : créer une arborescence XML à partir de l’un des deux espaces de noms contenus dans un fichier</span><span class="sxs-lookup"><span data-stu-id="9dc65-109">Example: Create an XML tree from one of two namespaces contained in a file</span></span>

<span data-ttu-id="9dc65-110">Exemple de fichier XML de document XML [: commandes fournisseur consolidées](sample-xml-file-consolidated-purchase-orders.md) contient des commandes fournisseur dans deux espaces de noms différents.</span><span class="sxs-lookup"><span data-stu-id="9dc65-110">XML document [Sample XML file: Consolidated purchase orders](sample-xml-file-consolidated-purchase-orders.md) contains purchase orders in two different namespaces.</span></span> <span data-ttu-id="9dc65-111">La requête suivante crée une arborescence à partir des éléments de l’un d’eux.</span><span class="sxs-lookup"><span data-stu-id="9dc65-111">The following query creates a new tree from the elements of one of them.</span></span>

```csharp
XDocument cpo = XDocument.Load("ConsolidatedPurchaseOrders.xml");
XNamespace aw = "http://www.adventure-works.com";
XElement newTree = new XElement("Root",
    from el in cpo.Root.Elements()
    where el.Name.Namespace == aw
    select el
);
Console.WriteLine(newTree);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim cpo As XDocument = XDocument.Load("ConsolidatedPurchaseOrders.xml")
        Dim newTree As XElement = _
            <Root>
                <%= From el In cpo.Root.Elements() _
                    Where el.Name.Namespace = GetXmlNamespace(aw) _
                    Select el %>
            </Root>
        Console.WriteLine(newTree)
    End Sub
End Module
```

<span data-ttu-id="9dc65-112">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="9dc65-112">This example produces the following output:</span></span>

```xml
<Root>
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
</Root>
```
