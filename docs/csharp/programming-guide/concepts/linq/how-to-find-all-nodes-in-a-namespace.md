---
title: Comment trouver tous les nœuds dans un espace nominant (C)
ms.date: 07/20/2015
ms.assetid: 3a38b913-a53e-4d0e-a19d-8782bffd3364
ms.openlocfilehash: 408f4207798720428d0dd3821d33fd3edf2f897e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141182"
---
# <a name="how-to-find-all-nodes-in-a-namespace-c"></a><span data-ttu-id="2ae30-102">Comment trouver tous les nœuds dans un espace nominant (C)</span><span class="sxs-lookup"><span data-stu-id="2ae30-102">How to find all nodes in a namespace (C#)</span></span>
<span data-ttu-id="2ae30-103">Vous pouvez filtrer sur l'espace de noms de chaque élément ou attribut afin de rechercher les nœuds dans cet espace de noms particulier.</span><span class="sxs-lookup"><span data-stu-id="2ae30-103">You can filter on the namespace of each element or attribute to find all nodes in that particular namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ae30-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="2ae30-104">Example</span></span>  
 <span data-ttu-id="2ae30-105">L’exemple suivant crée une arborescence XML avec deux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="2ae30-105">The following example creates an XML tree with two namespaces.</span></span> <span data-ttu-id="2ae30-106">Il itère ensuite au sein de l'arborescence et imprime les noms de tous les éléments et attributs dans l'un de ces espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="2ae30-106">It then iterates through the tree and prints the names of all the elements and attributes in one of those namespaces.</span></span>  
  
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
  
 <span data-ttu-id="2ae30-107">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2ae30-107">This code produces the following output:</span></span>  
  
```output  
Nodes in the http://www.adventure-works.com namespace  
{http://www.adventure-works.com}Child3  
{http://www.adventure-works.com}GrandChild2  
```  
  
## <a name="example"></a><span data-ttu-id="2ae30-108"> Exemple</span><span class="sxs-lookup"><span data-stu-id="2ae30-108">Example</span></span>  
 <span data-ttu-id="2ae30-109">Le fichier XML auquel accède cette requête contient des commandes fournisseur dans deux espaces de noms différents.</span><span class="sxs-lookup"><span data-stu-id="2ae30-109">The XML file accessed by the following query contains purchase orders in two different namespaces.</span></span> <span data-ttu-id="2ae30-110">La requête crée une nouvelle arborescence avec uniquement les éléments de l’un des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="2ae30-110">The query creates a new tree with just the elements in one of the namespaces.</span></span>  
  
 <span data-ttu-id="2ae30-111">Cet exemple utilise le document XML suivant : [Exemple de fichiers XML : Commandes fournisseur consolidées](./sample-xml-file-consolidated-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="2ae30-111">This example uses the following XML document: [Sample XML File: Consolidated Purchase Orders](./sample-xml-file-consolidated-purchase-orders.md).</span></span>  
  
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
  
 <span data-ttu-id="2ae30-112">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2ae30-112">This code produces the following output:</span></span>  
  
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
