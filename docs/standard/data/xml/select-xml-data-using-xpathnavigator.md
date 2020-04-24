---
title: Sélection de données XML à l'aide de XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
ms.openlocfilehash: 99b6b3b6959abf4c8adc313364ad641249bd9bc3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710165"
---
# <a name="select-xml-data-using-xpathnavigator"></a><span data-ttu-id="0fcae-102">Sélection de données XML à l'aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0fcae-102">Select XML Data Using XPathNavigator</span></span>
<span data-ttu-id="0fcae-103">La classe <xref:System.Xml.XPath.XPathNavigator> offre un ensemble de méthodes permettant de sélectionner une collection de nœuds dans un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> à l’aide d’une expression XPath.</span><span class="sxs-lookup"><span data-stu-id="0fcae-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="0fcae-104">Une fois la collection de nœuds sélectionnée, vous pouvez y effectuer des itérations.</span><span class="sxs-lookup"><span data-stu-id="0fcae-104">Once selected, you can iterate over the selected set of nodes.</span></span>  
  
## <a name="xpathnavigator-selection-methods"></a><span data-ttu-id="0fcae-105">Méthodes de sélection de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0fcae-105">XPathNavigator Selection Methods</span></span>  
 <span data-ttu-id="0fcae-106">La classe <xref:System.Xml.XPath.XPathNavigator> offre un ensemble de méthodes permettant de sélectionner une collection de nœuds dans un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> à l’aide d’une expression XPath.</span><span class="sxs-lookup"><span data-stu-id="0fcae-106">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="0fcae-107">La classe <xref:System.Xml.XPath.XPathNavigator> fournit également un ensemble de méthodes optimisées permettant une sélection plus rapide des nœuds ancêtres, enfants et descendants qu'avec une expression XPath.</span><span class="sxs-lookup"><span data-stu-id="0fcae-107">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of optimized methods for selecting ancestor, child and descendant nodes faster than using an XPath expression.</span></span> <span data-ttu-id="0fcae-108">La collection de nœuds sélectionnée est retournée dans un objet <xref:System.Xml.XPath.XPathNodeIterator> ou dans un objet <xref:System.Xml.XPath.XPathNavigator> si un seul nœud est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="0fcae-108">The selected set of nodes is returned in an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
### <a name="selecting-nodes-using-xpath-expressions"></a><span data-ttu-id="0fcae-109">Sélection de nœuds à l’aide d’expressions XPath</span><span class="sxs-lookup"><span data-stu-id="0fcae-109">Selecting Nodes Using XPath Expressions</span></span>  
 <span data-ttu-id="0fcae-110">Pour sélectionner une collection de nœuds à l’aide d’une expression XPath, utilisez l’une des méthodes de sélection suivantes.</span><span class="sxs-lookup"><span data-stu-id="0fcae-110">To select a set of nodes using an XPath expression, use one of the following selection methods.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="0fcae-111">Lorsqu'elles sont appelées, ces méthodes retournent une collection de nœuds dans laquelle vous pouvez vous déplacer librement à l'aide d'un objet <xref:System.Xml.XPath.XPathNodeIterator> ou d'un objet <xref:System.Xml.XPath.XPathNavigator> si un seul nœud est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="0fcae-111">When called, these methods return a set of nodes that you can navigate freely using an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
 <span data-ttu-id="0fcae-112">La navigation avec un objet <xref:System.Xml.XPath.XPathNodeIterator> n'affecte pas la position de l'objet <xref:System.Xml.XPath.XPathNavigator> utilisé pour le créer.</span><span class="sxs-lookup"><span data-stu-id="0fcae-112">Navigating with an <xref:System.Xml.XPath.XPathNodeIterator> object does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span> <span data-ttu-id="0fcae-113">L'objet <xref:System.Xml.XPath.XPathNavigator> retourné par les méthodes <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> est positionné sur le nœud unique retourné et n'affecte pas non plus la position de l'objet<xref:System.Xml.XPath.XPathNavigator> utilisé pour le créer.</span><span class="sxs-lookup"><span data-stu-id="0fcae-113">The <xref:System.Xml.XPath.XPathNavigator> object returned from the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> methods is positioned on the single returned node and also does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span>  
  
 <span data-ttu-id="0fcae-114">L'exemple suivant illustre la création d'un objet <xref:System.Xml.XPath.XPathNavigator> à partir d'un objet <xref:System.Xml.XPath.XPathDocument>, l'utilisation de la méthode <xref:System.Xml.XPath.XPathNavigator.Select%2A> pour sélectionner des nœuds dans l'objet <xref:System.Xml.XPath.XPathDocument> et l'utilisation de l'objet <xref:System.Xml.XPath.XPathNodeIterator> pour itérer sur les nœuds sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="0fcae-114">The following example shows the creation of an <xref:System.Xml.XPath.XPathNavigator> object from an <xref:System.Xml.XPath.XPathDocument> object, the use of the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method to select nodes in the <xref:System.Xml.XPath.XPathDocument> object, and the use of the <xref:System.Xml.XPath.XPathNodeIterator> object to iterate over the selected nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim nodes As XPathNodeIterator = navigator.Select("/bookstore/book")  
  
While nodes.MoveNext()  
    Console.WriteLine(nodes.Current.Name)  
End While  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathNodeIterator nodes = navigator.Select("/bookstore/book");  
  
while(nodes.MoveNext())  
{  
    Console.WriteLine(nodes.Current.Name);  
}  
```  
  
 <span data-ttu-id="0fcae-115">L'exemple prend le fichier `books.xml` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="0fcae-115">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a><span data-ttu-id="0fcae-116">Méthodes de sélection optimisées</span><span class="sxs-lookup"><span data-stu-id="0fcae-116">Optimized Selection Methods</span></span>  
 <span data-ttu-id="0fcae-117">Les méthodes <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> et <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> représentent des expressions XPath couramment utilisées pour extraire des nœuds enfants, descendants et ancêtres.</span><span class="sxs-lookup"><span data-stu-id="0fcae-117">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class represent XPath expressions commonly used to retrieve child, descendant, and ancestor nodes.</span></span> <span data-ttu-id="0fcae-118">Ces méthodes sont optimisées pour offrir de meilleures performances et sont plus rapides que les expressions XPath correspondantes.</span><span class="sxs-lookup"><span data-stu-id="0fcae-118">These methods are optimized for performance and are faster than their corresponding XPath expressions.</span></span> <span data-ttu-id="0fcae-119">Les méthodes <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> et <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> sélectionnent des nœuds ancêtres, enfants et descendants d'après une valeur <xref:System.Xml.XPath.XPathNodeType> ou d'après le nom local et l'URI d'espace de noms des nœuds à sélectionner.</span><span class="sxs-lookup"><span data-stu-id="0fcae-119">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods selects ancestor, child, and descendant nodes based on an <xref:System.Xml.XPath.XPathNodeType> value or the local name and namespace URI of the nodes to select.</span></span> <span data-ttu-id="0fcae-120">Les nœuds ancêtres, enfants et descendants sélectionnés sont retournés dans un objet <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="0fcae-120">The selected ancestor, child, and descendant nodes are returned in an <xref:System.Xml.XPath.XPathNodeIterator> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fcae-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fcae-121">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="0fcae-122">Traitement des données XML à l'aide du modèle de données XPath</span><span class="sxs-lookup"><span data-stu-id="0fcae-122">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="0fcae-123">Évaluation d’expressions XPath à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0fcae-123">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="0fcae-124">Mise en correspondance de nœuds avec XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0fcae-124">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="0fcae-125">Types de nœuds reconnus avec les requêtes XPath</span><span class="sxs-lookup"><span data-stu-id="0fcae-125">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="0fcae-126">Requêtes et espaces de noms XPath</span><span class="sxs-lookup"><span data-stu-id="0fcae-126">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [<span data-ttu-id="0fcae-127">Expressions XPath compilées</span><span class="sxs-lookup"><span data-stu-id="0fcae-127">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
