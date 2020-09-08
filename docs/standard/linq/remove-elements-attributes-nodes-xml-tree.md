---
title: Supprimer des éléments, des attributs et des nœuds d’une arborescence XML-LINQ to XML
description: Découvrez comment supprimer des éléments, des attributs et d’autres types de nœuds d’une arborescence XML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: 1a7c10892ccf1baaab7dde700266a134abe727de
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553694"
---
# <a name="remove-elements-attributes-and-nodes-from-an-xml-tree-linq-to-xml"></a><span data-ttu-id="3f58a-103">Supprimer des éléments, des attributs et des nœuds d’une arborescence XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="3f58a-103">Remove elements, attributes, and nodes from an XML tree (LINQ to XML)</span></span>

<span data-ttu-id="3f58a-104">Vous pouvez modifier une arborescence XML en supprimant des éléments, des attributs et d’autres types de nœuds.</span><span class="sxs-lookup"><span data-stu-id="3f58a-104">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>

<span data-ttu-id="3f58a-105">La suppression d'un seul élément ou attribut d'un document XML est simple.</span><span class="sxs-lookup"><span data-stu-id="3f58a-105">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="3f58a-106">Toutefois, lors de la suppression de collections d’éléments ou d’attributs, vous devez tout d’abord matérialiser une collection dans une liste, puis supprimer les éléments ou attributs de la liste.</span><span class="sxs-lookup"><span data-stu-id="3f58a-106">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="3f58a-107">La meilleure approche consiste à utiliser la <xref:System.Xml.Linq.Extensions.Remove%2A> méthode d’extension pour effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="3f58a-107">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method to do this.</span></span>

<span data-ttu-id="3f58a-108">La principale raison d’utiliser cette approche est que la plupart des collections que vous récupérez à partir d’une arborescence XML sont générés à l’aide de l’exécution différée.</span><span class="sxs-lookup"><span data-stu-id="3f58a-108">The main reason to use this approach is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="3f58a-109">Si vous ne les matérialisez pas tout d’abord dans une liste, ou si vous n’utilisez pas les méthodes d’extension, vous risquez de rencontrer une certaine classe de bogues.</span><span class="sxs-lookup"><span data-stu-id="3f58a-109">If you don't first materialize them into a list, or if you don't use the extension methods, you may encounter a certain class of bugs.</span></span> <span data-ttu-id="3f58a-110">Pour plus d’informations, consultez [bogues de code déclaratifs/impératifs mixtes](mixed-declarative-imperative-code-bugs.md).</span><span class="sxs-lookup"><span data-stu-id="3f58a-110">For more information, see [Mixed declarative/imperative code bugs](mixed-declarative-imperative-code-bugs.md).</span></span>

<span data-ttu-id="3f58a-111">Les méthodes suivantes suppriment des nœuds et des attributs d’une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="3f58a-111">The following methods remove nodes and attributes from an XML tree.</span></span>

|<span data-ttu-id="3f58a-112">Méthode</span><span class="sxs-lookup"><span data-stu-id="3f58a-112">Method</span></span>|<span data-ttu-id="3f58a-113">Description</span><span class="sxs-lookup"><span data-stu-id="3f58a-113">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="3f58a-114">Supprime un <xref:System.Xml.Linq.XAttribute> de son parent.</span><span class="sxs-lookup"><span data-stu-id="3f58a-114">Remove an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="3f58a-115">Supprimez les nœuds enfants d’un <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="3f58a-115">Remove the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="3f58a-116">Supprimer le contenu et les attributs d’un <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="3f58a-116">Remove content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="3f58a-117">Supprimez les attributs d’un <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="3f58a-117">Remove the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="3f58a-118">Supprimez l’attribut si vous transmettez la valeur `null` .</span><span class="sxs-lookup"><span data-stu-id="3f58a-118">Remove the attribute if you pass the value `null`.</span></span>|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="3f58a-119">Supprimez l’élément enfant si vous transmettez la valeur `null` .</span><span class="sxs-lookup"><span data-stu-id="3f58a-119">Remove the child element if you pass the value `null`.</span></span>|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="3f58a-120">Supprime un <xref:System.Xml.Linq.XNode> de son parent.</span><span class="sxs-lookup"><span data-stu-id="3f58a-120">Remove an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="3f58a-121">Supprimez chaque attribut ou élément de la collection source de son élément parent.</span><span class="sxs-lookup"><span data-stu-id="3f58a-121">Remove every attribute or element in the source collection from its parent element.</span></span>|

## <a name="example-remove-a-single-element-and-remove-a-collection-of-elements-in-two-ways"></a><span data-ttu-id="3f58a-122">Exemple : supprimer un seul élément et supprimer une collection d’éléments de deux manières</span><span class="sxs-lookup"><span data-stu-id="3f58a-122">Example: Remove a single element, and remove a collection of elements in two ways</span></span>

<span data-ttu-id="3f58a-123">Cet exemple illustre trois approches de la suppression d'éléments.</span><span class="sxs-lookup"><span data-stu-id="3f58a-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="3f58a-124">Tout d'abord, il supprime un seul élément.</span><span class="sxs-lookup"><span data-stu-id="3f58a-124">First, it removes a single element.</span></span> <span data-ttu-id="3f58a-125">Ensuite, il récupère une collection d’éléments, les matérialise à l’aide de l' <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> opérateur, puis supprime la collection.</span><span class="sxs-lookup"><span data-stu-id="3f58a-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and then removes the collection.</span></span> <span data-ttu-id="3f58a-126">Pour finir, il récupère une collection d'éléments et les supprime à l'aide de la méthode d'extension <xref:System.Xml.Linq.Extensions.Remove%2A>.</span><span class="sxs-lookup"><span data-stu-id="3f58a-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>

<span data-ttu-id="3f58a-127">Pour plus d’informations sur l' <xref:System.Linq.Enumerable.ToList%2A> opérateur, consultez [conversion des types de données (C#)](../../csharp/programming-guide/concepts/linq/converting-data-types.md) et conversion des types de [données (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="3f58a-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](../../csharp/programming-guide/concepts/linq/converting-data-types.md) and [Converting Data Types (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span></span>

```csharp
XElement root = XElement.Parse(@"<Root>
    <Child1>
        <GrandChild1/>
        <GrandChild2/>
        <GrandChild3/>
    </Child1>
    <Child2>
        <GrandChild4/>
        <GrandChild5/>
        <GrandChild6/>
    </Child2>
    <Child3>
        <GrandChild7/>
        <GrandChild8/>
        <GrandChild9/>
    </Child3>
</Root>");
root.Element("Child1").Element("GrandChild1").Remove();
root.Element("Child2").Elements().ToList().Remove();
root.Element("Child3").Elements().Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1>
            <GrandChild1/>
            <GrandChild2/>
            <GrandChild3/>
        </Child1>
        <Child2>
            <GrandChild4/>
            <GrandChild5/>
            <GrandChild6/>
        </Child2>
        <Child3>
            <GrandChild7/>
            <GrandChild8/>
            <GrandChild9/>
        </Child3>
    </Root>
root.<Child1>.<GrandChild1>.Remove()
root.<Child2>.Elements().ToList().Remove()
root.<Child3>.Elements().Remove()
Console.WriteLine(root)
```

<span data-ttu-id="3f58a-128">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="3f58a-128">This example produces the following output:</span></span>

```xml
<Root>
  <Child1>
    <GrandChild2 />
    <GrandChild3 />
  </Child1>
  <Child2 />
  <Child3 />
</Root>
```

<span data-ttu-id="3f58a-129">Le premier élément petit-enfant a été supprimé de `Child1` , et tous les éléments petits-enfants ont été supprimés de `Child2` et de `Child3` .</span><span class="sxs-lookup"><span data-stu-id="3f58a-129">The first grandchild element was removed from `Child1`, and all grandchildren elements were removed from `Child2` and from `Child3`.</span></span>
