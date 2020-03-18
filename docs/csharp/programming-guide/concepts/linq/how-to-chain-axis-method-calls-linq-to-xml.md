---
title: Comment enchaîner les appels de méthode d’axe (LINQ à XML) (C)
ms.date: 07/20/2015
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: 56fa5c9e8358883d838b68e99664240aa97f347f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169465"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a><span data-ttu-id="0e630-102">Comment enchaîner les appels de méthode d’axe (LINQ à XML) (C)</span><span class="sxs-lookup"><span data-stu-id="0e630-102">How to chain axis method calls (LINQ to XML) (C#)</span></span>
<span data-ttu-id="0e630-103">Un schéma courant que vous utiliserez dans votre code consiste à appeler une méthode d’axe, puis à appeler l’un des axes de méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="0e630-103">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="0e630-104">Il existe deux axes avec le nom `Elements` qui retournent une collection d'éléments : la méthode <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> et la méthode <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0e630-104">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0e630-105">Vous pouvez combiner ces deux axes pour rechercher tous les éléments d’un nom spécifié à une profondeur donnée dans l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="0e630-105">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e630-106"> Exemple</span><span class="sxs-lookup"><span data-stu-id="0e630-106">Example</span></span>  
 <span data-ttu-id="0e630-107">Cet exemple utilise <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> et <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> pour rechercher tous les éléments `Name` dans tous les éléments `Address` de tous les éléments `PurchaseOrder`.</span><span class="sxs-lookup"><span data-stu-id="0e630-107">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="0e630-108">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0e630-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XElement purchaseOrders = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements("PurchaseOrder")  
        .Elements("Address")  
        .Elements("Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="0e630-109">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0e630-109">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="0e630-110">Cela fonctionne car l'une des implémentations de l'axe `Elements` est en tant que méthode d'extension sur l'objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="0e630-110">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="0e630-111"><xref:System.Xml.Linq.XElement> dérivant de <xref:System.Xml.Linq.XContainer>, vous pouvez appeler la méthode <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> sur les résultats d'un appel à la méthode <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0e630-111"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e630-112"> Exemple</span><span class="sxs-lookup"><span data-stu-id="0e630-112">Example</span></span>  
 <span data-ttu-id="0e630-113">Quelquefois, vous souhaitez récupérer tous les éléments à une profondeur d'élément spécifique lorsqu'il peut y avoir ou ne pas y avoir d'ancêtres intermédiaires.</span><span class="sxs-lookup"><span data-stu-id="0e630-113">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="0e630-114">Par exemple, dans le document suivant, vous pourriez souhaiter récupérer tous les éléments `ConfigParameter` qui sont des enfants de l'élément `Customer`, mais pas le `ConfigParameter` qui est un enfant de l'élément `Root`.</span><span class="sxs-lookup"><span data-stu-id="0e630-114">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
```xml  
<Root>  
  <ConfigParameter>RootConfigParameter</ConfigParameter>  
  <Customer>  
    <Name>Frank</Name>  
    <Config>  
      <ConfigParameter>FirstConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
  <Customer>  
    <Name>Bob</Name>  
    <!--This customer doesn't have a Config element-->  
  </Customer>  
  <Customer>  
    <Name>Bill</Name>  
    <Config>  
      <ConfigParameter>SecondConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
</Root>  
```  
  
 <span data-ttu-id="0e630-115">Pour cela, vous pouvez utiliser l'axe <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> comme suit :</span><span class="sxs-lookup"><span data-stu-id="0e630-115">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 <span data-ttu-id="0e630-116">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0e630-116">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="0e630-117"> Exemple</span><span class="sxs-lookup"><span data-stu-id="0e630-117">Example</span></span>  
 <span data-ttu-id="0e630-118">L'exemple suivant illustre la même technique pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="0e630-118">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="0e630-119">Pour plus d’informations, consultez [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0e630-119">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="0e630-120">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur dans un espace de noms](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="0e630-120">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement purchaseOrders = XElement.Load("PurchaseOrdersInNamespace.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements(aw + "PurchaseOrder")  
        .Elements(aw + "Address")  
        .Elements(aw + "Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="0e630-121">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0e630-121">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e630-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e630-122">See also</span></span>

- [<span data-ttu-id="0e630-123">Axes LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0e630-123">LINQ to XML Axes (C#)</span></span>](linq-to-xml-axes-overview.md)
