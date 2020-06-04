---
title: Suppression d’éléments, d’attributs et de nœuds d’une arborescence XML
ms.date: 07/20/2015
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
ms.openlocfilehash: f8be7fe521fb3c2662b105e34fd96fea1d1ac6e7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413403"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a><span data-ttu-id="3053a-102">Suppression d’éléments, d’attributs et de nœuds d’une arborescence XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3053a-102">Removing Elements, Attributes, and Nodes from an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="3053a-103">Vous pouvez modifier une arborescence XML en supprimant des éléments, des attributs et d’autres types de nœuds.</span><span class="sxs-lookup"><span data-stu-id="3053a-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>  
  
 <span data-ttu-id="3053a-104">La suppression d'un seul élément ou attribut d'un document XML est simple.</span><span class="sxs-lookup"><span data-stu-id="3053a-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="3053a-105">Toutefois, lors de la suppression de collections d’éléments ou d’attributs, vous devez tout d’abord matérialiser une collection dans une liste, puis supprimer les éléments ou attributs de la liste.</span><span class="sxs-lookup"><span data-stu-id="3053a-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="3053a-106">La meilleure approche consiste à utiliser la méthode d'extension <xref:System.Xml.Linq.Extensions.Remove%2A>, qui effectuera cette tâche pour vous.</span><span class="sxs-lookup"><span data-stu-id="3053a-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>  
  
 <span data-ttu-id="3053a-107">Cette opération est nécessaire car la plupart des collections que vous récupérez à partir d’une arborescence XML sont produites à l’aide de l’exécution différée.</span><span class="sxs-lookup"><span data-stu-id="3053a-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="3053a-108">Si vous ne les matérialisez pas tout d’abord dans une liste, ou si vous n’utilisez pas les méthodes d’extension, vous risquez de rencontrer une certaine classe de bogues.</span><span class="sxs-lookup"><span data-stu-id="3053a-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="3053a-109">Pour plus d’informations, consultez [code déclaratif mixte/bogues de code impératifs (LINQ to XML) (Visual Basic)](mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3053a-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)](mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="3053a-110">Les méthodes suivantes suppriment des nœuds et des attributs d’une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="3053a-110">The following methods remove nodes and attributes from an XML tree.</span></span>  
  
|<span data-ttu-id="3053a-111">Méthode</span><span class="sxs-lookup"><span data-stu-id="3053a-111">Method</span></span>|<span data-ttu-id="3053a-112">Description</span><span class="sxs-lookup"><span data-stu-id="3053a-112">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="3053a-113">Supprime un objet <xref:System.Xml.Linq.XAttribute> de son parent.</span><span class="sxs-lookup"><span data-stu-id="3053a-113">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="3053a-114">Supprime les nœuds enfants d'un objet <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="3053a-114">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="3053a-115">Supprime le contenu et les attributs d'un objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="3053a-115">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="3053a-116">Supprime les attributs d'un objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="3053a-116">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="3053a-117">Supprime l'attribut si vous passez `null` comme valeur.</span><span class="sxs-lookup"><span data-stu-id="3053a-117">If you pass `null` for value, then removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="3053a-118">Supprime l'élément enfant si vous passez `null` comme valeur.</span><span class="sxs-lookup"><span data-stu-id="3053a-118">If you pass `null` for value, then removes the child element.</span></span>|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="3053a-119">Supprime un objet <xref:System.Xml.Linq.XNode> de son parent.</span><span class="sxs-lookup"><span data-stu-id="3053a-119">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="3053a-120">Supprime chaque attribut ou élément dans la collection source de son élément parent.</span><span class="sxs-lookup"><span data-stu-id="3053a-120">Removes every attribute or element in the source collection from its parent element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3053a-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="3053a-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="3053a-122">Description</span><span class="sxs-lookup"><span data-stu-id="3053a-122">Description</span></span>  
 <span data-ttu-id="3053a-123">Cet exemple illustre trois approches de la suppression d'éléments.</span><span class="sxs-lookup"><span data-stu-id="3053a-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="3053a-124">Tout d'abord, il supprime un seul élément.</span><span class="sxs-lookup"><span data-stu-id="3053a-124">First, it removes a single element.</span></span> <span data-ttu-id="3053a-125">Ensuite, il récupère une collection d’éléments, les matérialise à l’aide de l’opérateur <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, puis supprime la collection.</span><span class="sxs-lookup"><span data-stu-id="3053a-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="3053a-126">Pour finir, il récupère une collection d'éléments et les supprime à l'aide de la méthode d'extension <xref:System.Xml.Linq.Extensions.Remove%2A>.</span><span class="sxs-lookup"><span data-stu-id="3053a-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>  
  
 <span data-ttu-id="3053a-127">Pour plus d’informations sur l' <xref:System.Linq.Enumerable.ToList%2A> opérateur, consultez [conversion des types de données (Visual Basic)](converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="3053a-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (Visual Basic)](converting-data-types.md).</span></span>  
  
### <a name="code"></a><span data-ttu-id="3053a-128">Code</span><span class="sxs-lookup"><span data-stu-id="3053a-128">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="3053a-129">Commentaires</span><span class="sxs-lookup"><span data-stu-id="3053a-129">Comments</span></span>  
 <span data-ttu-id="3053a-130">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="3053a-130">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="3053a-131">Notez que le premier élément petit-enfant a été supprimé de `Child1`.</span><span class="sxs-lookup"><span data-stu-id="3053a-131">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="3053a-132">Tous les éléments petits-enfants ont été supprimés de `Child2` et de `Child3`.</span><span class="sxs-lookup"><span data-stu-id="3053a-132">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3053a-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3053a-133">See also</span></span>

- [<span data-ttu-id="3053a-134">Modification d’arborescences XML (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3053a-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](modifying-xml-trees-linq-to-xml.md)
