---
title: Comment filtrer sur des noms d’éléments-LINQ to XML
description: Apprenez à filtrer sur le nom de l’élément lorsque vous appelez une méthode qui retourne un IEnumerable de XElement.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: 1f831fe0008c94b3956e93f3ced7176d8c0bf34e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552384"
---
# <a name="how-to-filter-on-element-names-linq-to-xml"></a><span data-ttu-id="2c32b-103">Guide pratique pour filtrer sur des noms d’élément (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="2c32b-103">How to filter on element names (LINQ to XML)</span></span>

<span data-ttu-id="2c32b-104">Lorsque vous appelez l'une des méthodes qui retournent <xref:System.Collections.Generic.IEnumerable%601> de collections <xref:System.Xml.Linq.XElement>, vous pouvez filtrer sur le nom de l'élément.</span><span class="sxs-lookup"><span data-stu-id="2c32b-104">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>

## <a name="example-retrieve-descendants-filtered-to-a-specified-name"></a><span data-ttu-id="2c32b-105">Exemple : récupérer les descendants filtrés avec un nom spécifié</span><span class="sxs-lookup"><span data-stu-id="2c32b-105">Example: Retrieve descendants filtered to a specified name</span></span>

<span data-ttu-id="2c32b-106">Cet exemple récupère une collection de descendants filtrés pour contenir uniquement les descendants avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="2c32b-106">This example retrieves a collection of descendants that's filtered to contain only descendants with the specified name.</span></span>

<span data-ttu-id="2c32b-107">Cet exemple utilise le document XML [exemple de fichier XML : commande fournisseur typique](sample-xml-file-typical-purchase-order.md).</span><span class="sxs-lookup"><span data-stu-id="2c32b-107">This example uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

```csharp
XElement po = XElement.Load("PurchaseOrder.xml");
IEnumerable<XElement> items =
    from el in po.Descendants("ProductName")
    select el;
foreach(XElement prdName in items)
    Console.WriteLine(prdName.Name + ":" + (string) prdName);
```

```vb
Dim po As XElement = XElement.Load("PurchaseOrder.xml")
Dim items As IEnumerable(Of XElement) = _
    From el In po...<ProductName> _
    Select el
For Each prdName As XElement In items
    Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)
Next
```

<span data-ttu-id="2c32b-108">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2c32b-108">This example produces the following output:</span></span>

```output
ProductName:Lawnmower
ProductName:Baby Monitor
```

<span data-ttu-id="2c32b-109">Les autres méthodes qui retournent <xref:System.Collections.Generic.IEnumerable%601> de collections <xref:System.Xml.Linq.XElement> suivent le même modèle.</span><span class="sxs-lookup"><span data-stu-id="2c32b-109">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="2c32b-110">Leurs signatures sont semblables à <xref:System.Xml.Linq.XContainer.Elements%2A> et <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="2c32b-110">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="2c32b-111">Voici la liste complète des méthodes qui ont des signatures de méthodes semblables :</span><span class="sxs-lookup"><span data-stu-id="2c32b-111">The following is the complete list of methods that have similar method signatures:</span></span>

- <xref:System.Xml.Linq.XNode.Ancestors%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>

## <a name="example-retrieve-from-xml-thats-in-a-namespace"></a><span data-ttu-id="2c32b-112">Exemple : récupérer à partir du code XML qui se trouve dans un espace de noms</span><span class="sxs-lookup"><span data-stu-id="2c32b-112">Example: Retrieve from XML that's in a namespace</span></span>

<span data-ttu-id="2c32b-113">L’exemple suivant illustre la même requête pour du code XML qui se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="2c32b-113">The following example shows the same query for XML that's in a namespace.</span></span> <span data-ttu-id="2c32b-114">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2c32b-114">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

<span data-ttu-id="2c32b-115">L’exemple utilise un document XML [exemple de fichier XML : commande fournisseur typique dans un espace de noms](sample-xml-file-typical-purchase-order-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="2c32b-115">The example uses XML document [Sample XML file: Typical purchase order in a namespace](sample-xml-file-typical-purchase-order-namespace.md).</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");
IEnumerable<XElement> items =
    from el in po.Descendants(aw + "ProductName")
    select el;
foreach (XElement prdName in items)
    Console.WriteLine(prdName.Name + ":" + (string)prdName);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")
        Dim items As IEnumerable(Of XElement) = _
            From el In po...<aw:ProductName> _
            Select el
        For Each prdName As XElement In items
            Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)
        Next
    End Sub
End Module
```

<span data-ttu-id="2c32b-116">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2c32b-116">This example produces the following output:</span></span>

```output
{http://www.adventure-works.com}ProductName:Lawnmower
{http://www.adventure-works.com}ProductName:Baby Monitor
```

## <a name="see-also"></a><span data-ttu-id="2c32b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c32b-117">See also</span></span>

- [<span data-ttu-id="2c32b-118">Vue d’ensemble des axes LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="2c32b-118">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
