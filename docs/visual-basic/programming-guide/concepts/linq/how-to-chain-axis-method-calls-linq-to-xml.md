---
title: 'Procédure : chaîner des appels à des méthodes d’axe (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: e4e22942-39bd-460f-b3c0-9f09e53d3aa9
ms.openlocfilehash: 51396c9aaffb43badf405600251ed5cb06198dc3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375133"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-visual-basic"></a><span data-ttu-id="5c634-102">Comment : chaîner des appels de méthode d’axe (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c634-102">How to: Chain Axis Method Calls (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="5c634-103">Un schéma courant que vous utiliserez dans votre code consiste à appeler une méthode d’axe, puis à appeler l’un des axes de méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="5c634-103">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="5c634-104">Il existe deux axes avec le nom `Elements` qui retournent une collection d'éléments : la méthode <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> et la méthode <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5c634-104">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5c634-105">Vous pouvez combiner ces deux axes pour rechercher tous les éléments d’un nom spécifié à une profondeur donnée dans l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="5c634-105">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c634-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="5c634-106">Example</span></span>  
 <span data-ttu-id="5c634-107">Cet exemple utilise <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> et <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> pour rechercher tous les éléments `Name` dans tous les éléments `Address` de tous les éléments `PurchaseOrder`.</span><span class="sxs-lookup"><span data-stu-id="5c634-107">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="5c634-108">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5c634-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim purchaseOrders As XElement = XElement.Load("PurchaseOrders.xml")  
Dim names As IEnumerable(Of XElement) = _  
    From el In purchaseOrders.<PurchaseOrder>.<Address>.<Name> _  
    Select el  
For Each e As XElement In names  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="5c634-109">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="5c634-109">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="5c634-110">Cela fonctionne car l'une des implémentations de l'axe `Elements` est en tant que méthode d'extension sur l'objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="5c634-110">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="5c634-111"><xref:System.Xml.Linq.XElement> dérivant de <xref:System.Xml.Linq.XContainer>, vous pouvez appeler la méthode <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> sur les résultats d'un appel à la méthode <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5c634-111"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c634-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="5c634-112">Example</span></span>  
 <span data-ttu-id="5c634-113">Quelquefois, vous souhaitez récupérer tous les éléments à une profondeur d'élément spécifique lorsqu'il peut y avoir ou ne pas y avoir d'ancêtres intermédiaires.</span><span class="sxs-lookup"><span data-stu-id="5c634-113">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="5c634-114">Par exemple, dans le document suivant, vous pourriez souhaiter récupérer tous les éléments `ConfigParameter` qui sont des enfants de l'élément `Customer`, mais pas le `ConfigParameter` qui est un enfant de l'élément `Root`.</span><span class="sxs-lookup"><span data-stu-id="5c634-114">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
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
  
 <span data-ttu-id="5c634-115">Pour cela, vous pouvez utiliser l'axe <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> comme suit :</span><span class="sxs-lookup"><span data-stu-id="5c634-115">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Irregular.xml")  
Dim configParameters As IEnumerable(Of XElement) = _  
    root.<Customer>.<Config>.<ConfigParameter>  
For Each cp As XElement In configParameters  
    Console.WriteLine(cp)  
Next  
```  
  
 <span data-ttu-id="5c634-116">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="5c634-116">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="5c634-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="5c634-117">Example</span></span>  
 <span data-ttu-id="5c634-118">L'exemple suivant illustre la même technique pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="5c634-118">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="5c634-119">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5c634-119">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="5c634-120">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur dans un espace de noms](sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="5c634-120">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim purchaseOrders As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim names As IEnumerable(Of XElement) = _  
            From el In purchaseOrders.<aw:PurchaseOrder>.<aw:Address>.<aw:Name> _  
            Select el  
        For Each e As XElement In names  
            Console.WriteLine(e)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="5c634-121">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="5c634-121">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c634-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c634-122">See also</span></span>

- [<span data-ttu-id="5c634-123">Axes LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c634-123">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)
