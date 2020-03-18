---
title: Suppression d’éléments, d’attributs et de nœuds d’une arborescence XML (C#)
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: badaa6bab35367d62a73f56c5221cb7d6d4a45f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591260"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a><span data-ttu-id="a8e44-102">Suppression d’éléments, d’attributs et de nœuds d’une arborescence XML (C#)</span><span class="sxs-lookup"><span data-stu-id="a8e44-102">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>

<span data-ttu-id="a8e44-103">Vous pouvez modifier une arborescence XML en supprimant des éléments, des attributs et d’autres types de nœuds.</span><span class="sxs-lookup"><span data-stu-id="a8e44-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>

<span data-ttu-id="a8e44-104">La suppression d'un seul élément ou attribut d'un document XML est simple.</span><span class="sxs-lookup"><span data-stu-id="a8e44-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="a8e44-105">Toutefois, lors de la suppression de collections d’éléments ou d’attributs, vous devez tout d’abord matérialiser une collection dans une liste, puis supprimer les éléments ou attributs de la liste.</span><span class="sxs-lookup"><span data-stu-id="a8e44-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="a8e44-106">La meilleure approche consiste à utiliser la méthode d'extension <xref:System.Xml.Linq.Extensions.Remove%2A>, qui effectuera cette tâche pour vous.</span><span class="sxs-lookup"><span data-stu-id="a8e44-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>

<span data-ttu-id="a8e44-107">Cette opération est nécessaire car la plupart des collections que vous récupérez à partir d’une arborescence XML sont produites à l’aide de l’exécution différée.</span><span class="sxs-lookup"><span data-stu-id="a8e44-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="a8e44-108">Si vous ne les matérialisez pas tout d’abord dans une liste, ou si vous n’utilisez pas les méthodes d’extension, vous risquez de rencontrer une certaine classe de bogues.</span><span class="sxs-lookup"><span data-stu-id="a8e44-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="a8e44-109">Pour plus d’informations, consultez [Bogues liés à l’utilisation combinée de code déclaratif et de code impératif (LINQ to XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a8e44-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>

<span data-ttu-id="a8e44-110">Les méthodes suivantes suppriment des nœuds et des attributs d’une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="a8e44-110">The following methods remove nodes and attributes from an XML tree.</span></span>

|<span data-ttu-id="a8e44-111">Méthode</span><span class="sxs-lookup"><span data-stu-id="a8e44-111">Method</span></span>|<span data-ttu-id="a8e44-112">Description</span><span class="sxs-lookup"><span data-stu-id="a8e44-112">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="a8e44-113">Supprime un objet <xref:System.Xml.Linq.XAttribute> de son parent.</span><span class="sxs-lookup"><span data-stu-id="a8e44-113">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="a8e44-114">Supprime les nœuds enfants d'un objet <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="a8e44-114">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="a8e44-115">Supprime le contenu et les attributs d'un objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="a8e44-115">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="a8e44-116">Supprime les attributs d'un objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="a8e44-116">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="a8e44-117">Supprime l'attribut si vous passez `null` comme valeur.</span><span class="sxs-lookup"><span data-stu-id="a8e44-117">If you pass `null` for value, then removes the attribute.</span></span>|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="a8e44-118">Supprime l'élément enfant si vous passez `null` comme valeur.</span><span class="sxs-lookup"><span data-stu-id="a8e44-118">If you pass `null` for value, then removes the child element.</span></span>|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="a8e44-119">Supprime un objet <xref:System.Xml.Linq.XNode> de son parent.</span><span class="sxs-lookup"><span data-stu-id="a8e44-119">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="a8e44-120">Supprime chaque attribut ou élément dans la collection source de son élément parent.</span><span class="sxs-lookup"><span data-stu-id="a8e44-120">Removes every attribute or element in the source collection from its parent element.</span></span>|

## <a name="example"></a><span data-ttu-id="a8e44-121"> Exemple</span><span class="sxs-lookup"><span data-stu-id="a8e44-121">Example</span></span>

### <a name="description"></a><span data-ttu-id="a8e44-122">Description</span><span class="sxs-lookup"><span data-stu-id="a8e44-122">Description</span></span>

<span data-ttu-id="a8e44-123">Cet exemple illustre trois approches de la suppression d'éléments.</span><span class="sxs-lookup"><span data-stu-id="a8e44-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="a8e44-124">Tout d'abord, il supprime un seul élément.</span><span class="sxs-lookup"><span data-stu-id="a8e44-124">First, it removes a single element.</span></span> <span data-ttu-id="a8e44-125">Ensuite, il récupère une collection d’éléments, les matérialise à l’aide de l’opérateur <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, puis supprime la collection.</span><span class="sxs-lookup"><span data-stu-id="a8e44-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="a8e44-126">Pour finir, il récupère une collection d'éléments et les supprime à l'aide de la méthode d'extension <xref:System.Xml.Linq.Extensions.Remove%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8e44-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>

<span data-ttu-id="a8e44-127">Pour plus d’informations sur l’opérateur <xref:System.Linq.Enumerable.ToList%2A>, consultez [Conversion des types de données (C#)](./converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="a8e44-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](./converting-data-types.md).</span></span>

### <a name="code"></a><span data-ttu-id="a8e44-128">Code</span><span class="sxs-lookup"><span data-stu-id="a8e44-128">Code</span></span>

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

### <a name="comments"></a><span data-ttu-id="a8e44-129">Commentaires</span><span class="sxs-lookup"><span data-stu-id="a8e44-129">Comments</span></span>

<span data-ttu-id="a8e44-130">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="a8e44-130">This code produces the following output:</span></span>

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

<span data-ttu-id="a8e44-131">Notez que le premier élément petit-enfant a été supprimé de `Child1`.</span><span class="sxs-lookup"><span data-stu-id="a8e44-131">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="a8e44-132">Tous les éléments petits-enfants ont été supprimés de `Child2` et de `Child3`.</span><span class="sxs-lookup"><span data-stu-id="a8e44-132">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>
