---
title: Comment filtrer sur des noms d’éléments (LINQ to XML)C#()
ms.date: 07/20/2015
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: 74efb19ef5ec77ca29145d27a8e5aa977530b68b
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141267"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a><span data-ttu-id="07d2a-102">Comment filtrer sur des noms d’éléments (LINQ to XML)C#()</span><span class="sxs-lookup"><span data-stu-id="07d2a-102">How to filter on element names (LINQ to XML) (C#)</span></span>
<span data-ttu-id="07d2a-103">Lorsque vous appelez l'une des méthodes qui retournent <xref:System.Collections.Generic.IEnumerable%601> de collections <xref:System.Xml.Linq.XElement>, vous pouvez filtrer sur le nom de l'élément.</span><span class="sxs-lookup"><span data-stu-id="07d2a-103">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07d2a-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="07d2a-104">Example</span></span>  
 <span data-ttu-id="07d2a-105">Cet exemple récupère une collection des descendants filtrée de sorte à contenir uniquement les descendants avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="07d2a-105">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="07d2a-106">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : commande fournisseur typique (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="07d2a-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 <span data-ttu-id="07d2a-107">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="07d2a-107">This code produces the following output:</span></span>  
  
```output  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="07d2a-108">Les autres méthodes qui retournent <xref:System.Collections.Generic.IEnumerable%601> de collections <xref:System.Xml.Linq.XElement> suivent le même modèle.</span><span class="sxs-lookup"><span data-stu-id="07d2a-108">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="07d2a-109">Leurs signatures sont semblables à <xref:System.Xml.Linq.XContainer.Elements%2A> et <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="07d2a-109">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="07d2a-110">Voici la liste complète des méthodes qui ont des signatures de méthodes semblables :</span><span class="sxs-lookup"><span data-stu-id="07d2a-110">The following is the complete list of methods that have similar method signatures:</span></span>  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="07d2a-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="07d2a-111">Example</span></span>  
 <span data-ttu-id="07d2a-112">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="07d2a-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="07d2a-113">Pour plus d’informations, consultez [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="07d2a-113">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="07d2a-114">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : commande fournisseur typique dans un espace de noms](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="07d2a-114">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 <span data-ttu-id="07d2a-115">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="07d2a-115">This code produces the following output:</span></span>  
  
```output  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="07d2a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07d2a-116">See also</span></span>

- [<span data-ttu-id="07d2a-117">Axes LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="07d2a-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
