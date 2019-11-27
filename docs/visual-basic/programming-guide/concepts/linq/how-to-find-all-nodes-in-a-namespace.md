---
title: 'Comment : rechercher tous les nœuds dans un espace de noms'
ms.date: 07/20/2015
ms.assetid: b735d7da-5727-48a3-ab57-a16378adc32e
ms.openlocfilehash: f6bc38140bc2ea43393133d78c798469d26671c5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352970"
---
# <a name="how-to-find-all-nodes-in-a-namespace-visual-basic"></a><span data-ttu-id="f4568-102">Comment : Rechercher tous les nœuds dans un espace de noms (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4568-102">How to: Find All Nodes in a Namespace (Visual Basic)</span></span>
<span data-ttu-id="f4568-103">Vous pouvez filtrer sur l'espace de noms de chaque élément ou attribut afin de rechercher les nœuds dans cet espace de noms particulier.</span><span class="sxs-lookup"><span data-stu-id="f4568-103">You can filter on the namespace of each element or attribute to find all nodes in that particular namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4568-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="f4568-104">Example</span></span>  
 <span data-ttu-id="f4568-105">L’exemple suivant crée une arborescence XML avec deux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="f4568-105">The following example creates an XML tree with two namespaces.</span></span> <span data-ttu-id="f4568-106">Il itère ensuite au sein de l'arborescence et imprime les noms de tous les éléments et attributs dans l'un de ces espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="f4568-106">It then iterates through the tree and prints the names of all the elements and attributes in one of those namespaces.</span></span>  
  
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
  
 <span data-ttu-id="f4568-107">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f4568-107">This code produces the following output:</span></span>  
  
```console  
Nodes in the http://www.adventure-works.com namespace  
{http://www.adventure-works.com}Child3  
{http://www.adventure-works.com}GrandChild2  
```  
  
## <a name="example"></a><span data-ttu-id="f4568-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="f4568-108">Example</span></span>  
 <span data-ttu-id="f4568-109">Le fichier XML auquel accède cette requête contient des commandes fournisseur dans deux espaces de noms différents.</span><span class="sxs-lookup"><span data-stu-id="f4568-109">The XML file accessed by the following query contains purchase orders in two different namespaces.</span></span> <span data-ttu-id="f4568-110">La requête crée une nouvelle arborescence avec uniquement les éléments de l’un des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="f4568-110">The query creates a new tree with just the elements in one of the namespaces.</span></span>  
  
 <span data-ttu-id="f4568-111">Cet exemple utilise le document XML suivant : [Exemple de fichiers XML : Commandes fournisseur consolidées](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="f4568-111">This example uses the following XML document: [Sample XML File: Consolidated Purchase Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md).</span></span>  
  
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
  
 <span data-ttu-id="f4568-112">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f4568-112">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f4568-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4568-113">See also</span></span>

- [<span data-ttu-id="f4568-114">Requêtes de base (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4568-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
