---
title: Ajout d’éléments, d’attributs et de nœuds à une arborescence XML (C#)
description: Découvrez les méthodes permettant d’ajouter du contenu, comme des éléments, des attributs, des commentaires, des instructions de traitement et du texte, à une arborescence XML existante.
ms.date: 07/20/2015
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 78a84401494e2d4280799632fa42dc95574e3e10
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105559"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a><span data-ttu-id="326a8-103">Ajout d’éléments, d’attributs et de nœuds à une arborescence XML (C#)</span><span class="sxs-lookup"><span data-stu-id="326a8-103">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>
<span data-ttu-id="326a8-104">Vous pouvez ajouter du contenu (éléments, attributs, commentaires, instructions de traitement, texte et CData) à une arborescence XML existante.</span><span class="sxs-lookup"><span data-stu-id="326a8-104">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="326a8-105">Méthodes pour ajouter du contenu</span><span class="sxs-lookup"><span data-stu-id="326a8-105">Methods for Adding Content</span></span>  
 <span data-ttu-id="326a8-106">Les méthodes suivantes ajoutent du contenu enfant à un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> :</span><span class="sxs-lookup"><span data-stu-id="326a8-106">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="326a8-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="326a8-107">Method</span></span>|<span data-ttu-id="326a8-108">Description</span><span class="sxs-lookup"><span data-stu-id="326a8-108">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="326a8-109">Ajoute du contenu à la fin du contenu enfant de l'objet <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="326a8-109">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="326a8-110">Ajoute du contenu au début du contenu enfant de l'objet <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="326a8-110">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="326a8-111">Les méthodes suivantes ajoutent du contenu en tant que nœuds frères d'un objet <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="326a8-111">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="326a8-112">Le nœud le plus courant auquel vous ajoutez du contenu frère est <xref:System.Xml.Linq.XElement>, bien que vous puissiez ajouter du contenu frère valide à d'autres types de nœuds tels que <xref:System.Xml.Linq.XText> ou <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="326a8-112">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="326a8-113">Méthode</span><span class="sxs-lookup"><span data-stu-id="326a8-113">Method</span></span>|<span data-ttu-id="326a8-114">Description</span><span class="sxs-lookup"><span data-stu-id="326a8-114">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="326a8-115">Ajoute du contenu après l'objet <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="326a8-115">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="326a8-116">Ajoute du contenu avant l'objet <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="326a8-116">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="326a8-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="326a8-117">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="326a8-118">Description</span><span class="sxs-lookup"><span data-stu-id="326a8-118">Description</span></span>  
 <span data-ttu-id="326a8-119">L'exemple suivant crée deux arborescences XML, puis modifie l'une des arborescences.</span><span class="sxs-lookup"><span data-stu-id="326a8-119">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="326a8-120">Code</span><span class="sxs-lookup"><span data-stu-id="326a8-120">Code</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",
    new XElement("Element1", 1),  
    new XElement("Element2", 2),  
    new XElement("Element3", 3),  
    new XElement("Element4", 4),  
    new XElement("Element5", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child2", 2),  
    new XElement("Child3", 3),  
    new XElement("Child4", 4),  
    new XElement("Child5", 5)  
);  
xmlTree.Add(new XElement("NewChild", "new content"));  
xmlTree.Add(  
    from el in srcTree.Elements()  
    where (int)el > 3  
    select el  
);  
// Even though Child9 does not exist in srcTree, the following statement will not  
// throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"));  
Console.WriteLine(xmlTree);  
```  
  
### <a name="comments"></a><span data-ttu-id="326a8-121">Commentaires</span><span class="sxs-lookup"><span data-stu-id="326a8-121">Comments</span></span>  
 <span data-ttu-id="326a8-122">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="326a8-122">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
  <Child4>4</Child4>  
  <Child5>5</Child5>  
  <NewChild>new content</NewChild>  
  <Element4>4</Element4>  
  <Element5>5</Element5>  
</Root>  
```  
  