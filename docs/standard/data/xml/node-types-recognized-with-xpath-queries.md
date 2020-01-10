---
title: Types de nœuds reconnus avec les requêtes XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
ms.openlocfilehash: cc1aa668ccf6fc7f210f48a28cf76b364459c784
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710542"
---
# <a name="node-types-recognized-with-xpath-queries"></a><span data-ttu-id="18d8d-102">Types de nœuds reconnus avec les requêtes XPath</span><span class="sxs-lookup"><span data-stu-id="18d8d-102">Node Types Recognized with XPath Queries</span></span>
<span data-ttu-id="18d8d-103">Les types de nœuds reconnus dans une requête XPath ne sont pas les mêmes que ceux trouvés dans le DOM (Document Object Model).</span><span class="sxs-lookup"><span data-stu-id="18d8d-103">The types of nodes recognized in an XPath query are not the same node types found in the Document Object Model (DOM).</span></span>  
  
## <a name="w3c-xpath-node-types"></a><span data-ttu-id="18d8d-104">Types de nœuds XPath du W3C</span><span class="sxs-lookup"><span data-stu-id="18d8d-104">W3C XPath Node Types</span></span>  
 <span data-ttu-id="18d8d-105">Les types de nœuds reconnus dans une requête XPath ne sont pas les mêmes que ceux trouvés dans le DOM (Document Object Model).</span><span class="sxs-lookup"><span data-stu-id="18d8d-105">The types of nodes recognized in an XPath query are not the types of nodes found in the Document Object Model (DOM).</span></span> <span data-ttu-id="18d8d-106">Les types de nœuds suivants sont les types de nœuds XPath représentés par l'énumération <xref:System.Xml.XPath.XPathNodeType>.</span><span class="sxs-lookup"><span data-stu-id="18d8d-106">The following are the XPath node types represented by the <xref:System.Xml.XPath.XPathNodeType> enumeration.</span></span>  
  
- <xref:System.Xml.XPath.XPathNodeType.All>  
  
- <xref:System.Xml.XPath.XPathNodeType.Attribute>  
  
- <xref:System.Xml.XPath.XPathNodeType.Comment>  
  
- <xref:System.Xml.XPath.XPathNodeType.Element>  
  
- <xref:System.Xml.XPath.XPathNodeType.Namespace>  
  
- <xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>  
  
- <xref:System.Xml.XPath.XPathNodeType.Root>  
  
- <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace>  
  
- <xref:System.Xml.XPath.XPathNodeType.Text>  
  
- <xref:System.Xml.XPath.XPathNodeType.Whitespace>  
  
 <span data-ttu-id="18d8d-107">Ces types de nœuds sont basés sur le modèle de données XPath, dans lequel les nœuds sont dérivés du jeu d’informations XML.</span><span class="sxs-lookup"><span data-stu-id="18d8d-107">These node types are based on the XPath data model, where the nodes are derived from the XML Information Set.</span></span> <span data-ttu-id="18d8d-108">Les types de nœuds <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> et <xref:System.Xml.XPath.XPathNodeType.Whitespace> sont des extensions Microsoft .NET Framework des types de nœuds de base décrits dans le modèle de données XPath.</span><span class="sxs-lookup"><span data-stu-id="18d8d-108">The <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> and <xref:System.Xml.XPath.XPathNodeType.Whitespace> node types are Microsoft .NET Framework extensions to the base node types described in the XPath data model.</span></span>  
  
 <span data-ttu-id="18d8d-109">Le type de nœud d’attribut est utilisé de manière différente dans le modèle de données XPath que dans le DOM.</span><span class="sxs-lookup"><span data-stu-id="18d8d-109">The attribute node type is used differently in the XPath data model than it is in the DOM.</span></span> <span data-ttu-id="18d8d-110">Dans le modèle de données XPath, le nœud d’élément est associé à un ensemble de nœuds d’attribut et le nœud d’élément est le parent de chaque nœud d’attribut.</span><span class="sxs-lookup"><span data-stu-id="18d8d-110">In the XPath data model, the element node has a set of attribute nodes related to it and the element node is the parent of each attribute node.</span></span> <span data-ttu-id="18d8d-111">Toutefois, dans le DOM, le nœud d'élément est le propriétaire et non le parent.</span><span class="sxs-lookup"><span data-stu-id="18d8d-111">However, in the DOM, the element node is the owner and not the parent.</span></span> <span data-ttu-id="18d8d-112">Dans ces deux modèles, les nœuds d'attribut et d'espace de noms ne sont pas considérés comme des nœuds enfants du nœud d'élément.</span><span class="sxs-lookup"><span data-stu-id="18d8d-112">In both models, attribute and namespace nodes are not considered child nodes of the element node.</span></span>  
  
 <span data-ttu-id="18d8d-113">Le type de nœud d’espace de noms a été ajouté au modèle de données XPath et n’est pas un type de nœud DOM reconnu.</span><span class="sxs-lookup"><span data-stu-id="18d8d-113">The namespace node type is an addition to the XPath data model and is not a recognized DOM node type.</span></span>  
  
 <span data-ttu-id="18d8d-114">Pour plus d’informations sur la navigation dans les nœuds d’élément, d’attribut et d’espace de noms, consultez les rubriques [Navigation entre les nœuds d’attribut et d’espace de noms à l’aide de XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) et [Navigation entre les nœuds d’attribut et d’espace de noms à l’aide de XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="18d8d-114">For more information about navigating element, attribute, and namespace nodes, see the [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) and [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18d8d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18d8d-115">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="18d8d-116">Traitement des données XML à l’aide du modèle de données XPath</span><span class="sxs-lookup"><span data-stu-id="18d8d-116">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="18d8d-117">Sélection de données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="18d8d-117">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="18d8d-118">Évaluation d’expressions XPath à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="18d8d-118">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="18d8d-119">Mise en correspondance de nœuds avec XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="18d8d-119">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="18d8d-120">Requêtes et espaces de noms XPath</span><span class="sxs-lookup"><span data-stu-id="18d8d-120">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [<span data-ttu-id="18d8d-121">Expressions XPath compilées</span><span class="sxs-lookup"><span data-stu-id="18d8d-121">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
