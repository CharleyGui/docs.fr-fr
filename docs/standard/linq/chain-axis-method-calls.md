---
title: Comment chaîner des appels de méthode d’axe-LINQ to XML
description: Découvrez comment utiliser les méthodes XContainer. Elements et extensions. Elements pour rechercher tous les éléments d’un nom spécifié à une profondeur donnée dans l’arborescence.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: 23d3b5a3dacbc56a570a92178cb8e28482907ca1
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553495"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml"></a><span data-ttu-id="72630-103">Guide pratique pour chaîner des appels à des méthode d’axe (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="72630-103">How to chain axis method calls (LINQ to XML)</span></span>

<span data-ttu-id="72630-104">Un schéma courant que vous utiliserez dans votre code consiste à appeler une méthode d’axe, puis à appeler l’un des axes de méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="72630-104">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>

<span data-ttu-id="72630-105">Il existe deux axes avec le nom `Elements` qui retournent une collection d'éléments : la méthode <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> et la méthode <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="72630-105">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="72630-106">Vous pouvez combiner ces deux axes pour rechercher tous les éléments d’un nom spécifié à une profondeur donnée dans l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="72630-106">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>

## <a name="example-retrieve-all-name-elements"></a><span data-ttu-id="72630-107">Exemple : récupérer tous les éléments de nom</span><span class="sxs-lookup"><span data-stu-id="72630-107">Example: Retrieve all name elements</span></span>

<span data-ttu-id="72630-108">Cet exemple utilise <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> et <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> pour récupérer tous les éléments dans tous les éléments `Name` `Address` de tous `PurchaseOrder` les éléments.</span><span class="sxs-lookup"><span data-stu-id="72630-108">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to retrieve all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>

<span data-ttu-id="72630-109">Cet exemple utilise le document XML [exemple de fichier XML : plusieurs commandes fournisseur](sample-xml-file-multiple-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="72630-109">This example uses XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span>

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

```vb
Dim purchaseOrders As XElement = XElement.Load("PurchaseOrders.xml")
Dim names As IEnumerable(Of XElement) = _
    From el In purchaseOrders.<PurchaseOrder>.<Address>.<Name> _
    Select el
For Each e As XElement In names
    Console.WriteLine(e)
Next
```

<span data-ttu-id="72630-110">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="72630-110">This example produces the following output:</span></span>

```xml
<Name>Ellen Adams</Name>
<Name>Tai Yee</Name>
<Name>Cristian Osorio</Name>
<Name>Cristian Osorio</Name>
<Name>Jessica Arnold</Name>
<Name>Jessica Arnold</Name>
```

<span data-ttu-id="72630-111">Cela fonctionne car l'une des implémentations de l'axe `Elements` est en tant que méthode d'extension sur l'objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="72630-111">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="72630-112"><xref:System.Xml.Linq.XElement> dérivant de <xref:System.Xml.Linq.XContainer>, vous pouvez appeler la méthode <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> sur les résultats d'un appel à la méthode <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="72630-112"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>

## <a name="example-retrieve-all-elements-at-a-particular-depth"></a><span data-ttu-id="72630-113">Exemple : récupérer tous les éléments à une profondeur particulière</span><span class="sxs-lookup"><span data-stu-id="72630-113">Example: Retrieve all elements at a particular depth</span></span>

<span data-ttu-id="72630-114">Parfois, vous souhaitez récupérer tous les éléments à une profondeur d’élément spécifique lorsqu’il peut ne pas y avoir d’ancêtres intermédiaires.</span><span class="sxs-lookup"><span data-stu-id="72630-114">Sometimes you want to retrieve all elements at a particular element depth when there may not be intervening ancestors.</span></span> <span data-ttu-id="72630-115">Par exemple, dans le document suivant, vous souhaiterez peut-être récupérer tous les `ConfigParameter` éléments qui sont des enfants de l' `Customer` élément, mais pas le `ConfigParameter` qui est un enfant de l' `Root` élément.</span><span class="sxs-lookup"><span data-stu-id="72630-115">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that's a child of the `Root` element.</span></span>

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

 <span data-ttu-id="72630-116">Pour cela, vous pouvez utiliser l'axe <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> comme suit :</span><span class="sxs-lookup"><span data-stu-id="72630-116">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>

```csharp
XElement root = XElement.Load("Irregular.xml");
IEnumerable<XElement> configParameters =
    root.Elements("Customer").Elements("Config").
    Elements("ConfigParameter");
foreach (XElement cp in configParameters)
    Console.WriteLine(cp);
```

```vb
Dim root As XElement = XElement.Load("Irregular.xml")
Dim configParameters As IEnumerable(Of XElement) = _
    root.<Customer>.<Config>.<ConfigParameter>
For Each cp As XElement In configParameters
    Console.WriteLine(cp)
Next
```

<span data-ttu-id="72630-117">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="72630-117">This example produces the following output:</span></span>

```xml
<ConfigParameter>FirstConfigParameter</ConfigParameter>
<ConfigParameter>SecondConfigParameter</ConfigParameter>
```

## <a name="example-retrieve-elements-for-xml-thats-in-a-namespace"></a><span data-ttu-id="72630-118">Exemple : récupérer des éléments pour du code XML qui se trouve dans un espace de noms</span><span class="sxs-lookup"><span data-stu-id="72630-118">Example: Retrieve elements for XML that's in a namespace</span></span>

<span data-ttu-id="72630-119">L’exemple suivant illustre la même technique pour le code XML qui se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="72630-119">The following example shows the same technique for XML that's in a namespace.</span></span> <span data-ttu-id="72630-120">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="72630-120">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

<span data-ttu-id="72630-121">Cet exemple utilise le document XML [exemple de fichier XML : plusieurs commandes fournisseur dans un espace de noms](sample-xml-file-multiple-purchase-orders-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="72630-121">This example uses XML document [Sample XML file: Multiple purchase orders in a namespace](sample-xml-file-multiple-purchase-orders-namespace.md).</span></span>

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

<span data-ttu-id="72630-122">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="72630-122">This example produces the following output:</span></span>

```xml
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>
```

## <a name="see-also"></a><span data-ttu-id="72630-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72630-123">See also</span></span>

- [<span data-ttu-id="72630-124">Vue d’ensemble des axes LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="72630-124">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
