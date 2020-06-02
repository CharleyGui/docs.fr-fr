---
title: Sélection, évaluation et mise en correspondance de données XML à l’aide de XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 46e059f8-4dc8-4185-9236-784be95228ed
ms.openlocfilehash: 1418e768db2f5f860ec40cf4e1351b4ec4a14a08
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282205"
---
# <a name="selecting-evaluating-and-matching-xml-data-using-xpathnavigator"></a><span data-ttu-id="3cf8d-102">Sélection, évaluation et mise en correspondance de données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3cf8d-102">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>
<span data-ttu-id="3cf8d-103">La classe <xref:System.Xml.XPath.XPathNavigator> fournit des méthodes de sélection de nœuds dans un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> à l'aide d'une requête XPath, d'évaluation et d'examen des résultats d'une expression XPath et détermine si un nœud d'un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> correspond à une expression XPath donnée.</span><span class="sxs-lookup"><span data-stu-id="3cf8d-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object matches a given XPath expression.</span></span> <span data-ttu-id="3cf8d-104">Ces concepts relatifs, entre autres, à la sélection, l'évaluation et la mise en correspondance de nœuds dans un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> sont décrits dans les rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="3cf8d-104">These and other concepts that relate to selecting, evaluating and matching nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object are described in the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3cf8d-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="3cf8d-105">In This Section</span></span>  
 [<span data-ttu-id="3cf8d-106">Sélection de données XML à l'aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3cf8d-106">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="3cf8d-107">Décrit l’ensemble des méthodes de la classe <xref:System.Xml.XPath.XPathNavigator> permettant de sélectionner une collection de nœuds dans un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> à l’aide d’une expression XPath.</span><span class="sxs-lookup"><span data-stu-id="3cf8d-107">Describes the set of <xref:System.Xml.XPath.XPathNavigator> class methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span>  
  
 [<span data-ttu-id="3cf8d-108">Évaluation d’expressions XPath à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3cf8d-108">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)  
 <span data-ttu-id="3cf8d-109">Décrit la méthode <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> permettant d’évaluer une expression XPath.</span><span class="sxs-lookup"><span data-stu-id="3cf8d-109">Describes the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to evaluate an XPath expression.</span></span>  
  
 [<span data-ttu-id="3cf8d-110">Mise en correspondance de nœuds avec XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3cf8d-110">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)  
 <span data-ttu-id="3cf8d-111">Décrit la méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> permettant de déterminer si un nœud correspond à une expression XPath.</span><span class="sxs-lookup"><span data-stu-id="3cf8d-111">Describes the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to determine if a node matches an XPath expression.</span></span>  
  
 [<span data-ttu-id="3cf8d-112">Types de nœuds reconnus avec les requêtes XPath</span><span class="sxs-lookup"><span data-stu-id="3cf8d-112">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)  
 <span data-ttu-id="3cf8d-113">Décrit les types de nœuds reconnus dans une requête XPath.</span><span class="sxs-lookup"><span data-stu-id="3cf8d-113">Describes the types of nodes recognized in an XPath query.</span></span>  
  
 [<span data-ttu-id="3cf8d-114">Requêtes et espaces de noms XPath</span><span class="sxs-lookup"><span data-stu-id="3cf8d-114">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)  
 <span data-ttu-id="3cf8d-115">Décrit l’utilisation d’espaces de noms dans une requête XPath.</span><span class="sxs-lookup"><span data-stu-id="3cf8d-115">Describes the use of namespaces in an XPath query.</span></span>  
  
 [<span data-ttu-id="3cf8d-116">Expressions XPath compilées</span><span class="sxs-lookup"><span data-stu-id="3cf8d-116">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)  
 <span data-ttu-id="3cf8d-117">Décrit la classe <xref:System.Xml.XPath.XPathExpression> qui représente une requête XPath compilée.</span><span class="sxs-lookup"><span data-stu-id="3cf8d-117">Describes the <xref:System.Xml.XPath.XPathExpression> class that represents a compiled XPath query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cf8d-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cf8d-118">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="3cf8d-119">Traitement des données XML à l'aide du modèle de données XPath</span><span class="sxs-lookup"><span data-stu-id="3cf8d-119">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="3cf8d-120">Lecture de données XML à l’aide de XPathDocument et XmlDocument</span><span class="sxs-lookup"><span data-stu-id="3cf8d-120">Reading XML Data using XPathDocument and XmlDocument</span></span>](reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="3cf8d-121">Accès à des données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3cf8d-121">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="3cf8d-122">Modification de données XML à l'aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3cf8d-122">Editing XML Data using XPathNavigator</span></span>](editing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="3cf8d-123">Validation de schéma à l'aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3cf8d-123">Schema Validation using XPathNavigator</span></span>](schema-validation-using-xpathnavigator.md)
