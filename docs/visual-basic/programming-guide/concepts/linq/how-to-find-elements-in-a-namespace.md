---
title: 'Procédure : Rechercher des éléments dans un espace de noms (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c7cb3b77-3424-4b54-9efa-4dc715948e41
ms.openlocfilehash: 98afdd7fc67895eaad5703cfb32c2b4000deb87f
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250113"
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="6915d-102">Procédure : Rechercher des éléments dans un espace de noms (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6915d-102">How to: Find Elements in a Namespace (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="6915d-103">Les expressions XPath peuvent rechercher des nœuds dans un espace de noms particulier.</span><span class="sxs-lookup"><span data-stu-id="6915d-103">XPath expressions can find nodes in a particular namespace.</span></span> <span data-ttu-id="6915d-104">Les expressions XPath utilisent des préfixes d'espaces de noms pour spécifier des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="6915d-104">XPath expressions use namespace prefixes for specifying namespaces.</span></span> <span data-ttu-id="6915d-105">Pour analyser une expression XPath qui contient des préfixes d'espaces de noms, vous devez passer un objet aux méthodes XPath qui implémente <xref:System.Xml.IXmlNamespaceResolver>.</span><span class="sxs-lookup"><span data-stu-id="6915d-105">To parse an XPath expression that contains namespace prefixes, you must pass an object to the XPath methods that implements <xref:System.Xml.IXmlNamespaceResolver>.</span></span> <span data-ttu-id="6915d-106">Cet exemple utilise <xref:System.Xml.XmlNamespaceManager>.</span><span class="sxs-lookup"><span data-stu-id="6915d-106">This example uses <xref:System.Xml.XmlNamespaceManager>.</span></span>  
  
 <span data-ttu-id="6915d-107">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="6915d-107">The XPath expression is:</span></span>  
  
 `./aw:*`  
  
## <a name="example"></a><span data-ttu-id="6915d-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="6915d-108">Example</span></span>  
 <span data-ttu-id="6915d-109">L’exemple suivant lit une arborescence XML qui contient deux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="6915d-109">The following example reads an XML tree that contains two namespaces.</span></span> <span data-ttu-id="6915d-110">Il utilise un objet <xref:System.Xml.XmlReader> pour lire le document XML.</span><span class="sxs-lookup"><span data-stu-id="6915d-110">It uses an <xref:System.Xml.XmlReader> to read the XML document.</span></span> <span data-ttu-id="6915d-111">Il obtient ensuite un objet <xref:System.Xml.XmlNameTable> à partir de l'objet <xref:System.Xml.XmlReader> et un objet<xref:System.Xml.XmlNamespaceManager> à partir de l'objet <xref:System.Xml.XmlNameTable>.</span><span class="sxs-lookup"><span data-stu-id="6915d-111">It then gets an <xref:System.Xml.XmlNameTable> from the <xref:System.Xml.XmlReader>, and an <xref:System.Xml.XmlNamespaceManager> from the <xref:System.Xml.XmlNameTable>.</span></span> <span data-ttu-id="6915d-112">Il utilise l'objet <xref:System.Xml.XmlNamespaceManager> lors de la sélection des éléments.</span><span class="sxs-lookup"><span data-stu-id="6915d-112">It uses the <xref:System.Xml.XmlNamespaceManager> when selecting elements.</span></span>  
  
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
  
 <span data-ttu-id="6915d-113">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="6915d-113">This example produces the following output:</span></span>  
  
```console
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
  
## <a name="see-also"></a><span data-ttu-id="6915d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6915d-114">See also</span></span>

- [<span data-ttu-id="6915d-115">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6915d-115">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
