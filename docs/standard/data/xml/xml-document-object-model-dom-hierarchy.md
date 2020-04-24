---
title: Hiérarchie du DOM XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
ms.openlocfilehash: 1193d7631816fe9fbf7aa1984d79ef8e61d5da80
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709970"
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="da17a-102">Hiérarchie du DOM XML</span><span class="sxs-lookup"><span data-stu-id="da17a-102">XML Document Object Model (DOM) Hierarchy</span></span>
<span data-ttu-id="da17a-103">L’illustration suivante montre la hiérarchie de classes du DOM (Document Object Model) XML et fournit le nom World Wide Web Consortium (W3C) entre parenthèses en même temps que le nom de la classe lorsque cela est pertinent.</span><span class="sxs-lookup"><span data-stu-id="da17a-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="da17a-104">![Hiérarchie&#41; XML Document Object Model &#40;DOM](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="da17a-104">![XML Document Object Model &#40;DOM&#41; hierarchy](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="da17a-105">Hiérarchie du modèle DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="da17a-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="da17a-106">Les classes suivantes n'héritent pas de **XmlNode** :</span><span class="sxs-lookup"><span data-stu-id="da17a-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
- <span data-ttu-id="da17a-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="da17a-107">**XmlImplementation**</span></span>  
  
- <span data-ttu-id="da17a-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="da17a-108">**XmlNamedNodeMap**</span></span>  
  
- <span data-ttu-id="da17a-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="da17a-109">**XmlNodeList**</span></span>  
  
- <span data-ttu-id="da17a-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="da17a-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="da17a-111">La classe **XmlImplementation** est utilisée pour créer un document XML.</span><span class="sxs-lookup"><span data-stu-id="da17a-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="da17a-112">Pour plus d'informations, consultez [Création d'un document XML](../../../../docs/standard/data/xml/xml-document-creation.md).</span><span class="sxs-lookup"><span data-stu-id="da17a-112">For more information, see [XML Document Creation](../../../../docs/standard/data/xml/xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="da17a-113">La classe **XmlNamedNodeMap** gère une collection de nœuds non triée.</span><span class="sxs-lookup"><span data-stu-id="da17a-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="da17a-114">Pour plus d'informations, consultez [Extraction de nœuds non triés par leur nom ou par l'index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span><span class="sxs-lookup"><span data-stu-id="da17a-114">For more information, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="da17a-115">La classe **XmlNodeList** gère une liste triée de nœuds.</span><span class="sxs-lookup"><span data-stu-id="da17a-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="da17a-116">Pour plus d'informations, consultez [Extraction de nœuds triés par l'index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span><span class="sxs-lookup"><span data-stu-id="da17a-116">For more information, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="da17a-117">La classe **XmlNodeChangedEventArgs** gère des gestionnaires d'événements inscrits dans **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="da17a-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="da17a-118">Pour plus d'informations, consultez [Gestion d'événements dans un document XML à l'aide de XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span><span class="sxs-lookup"><span data-stu-id="da17a-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="da17a-119">La classe **XmlLinkedNode** hérite de **XmlNode**.</span><span class="sxs-lookup"><span data-stu-id="da17a-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="da17a-120">Sa fonction consiste à substituer deux méthodes de **XmlNode** : les méthodes **PreviousSibling** et **NextSibling**.</span><span class="sxs-lookup"><span data-stu-id="da17a-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="da17a-121">Les méthodes substituées sont ensuite héritées et utilisées par **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference** et **XmlProcessingInstruction**, qui sont des classes dotées de frères précédents et suivants.</span><span class="sxs-lookup"><span data-stu-id="da17a-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da17a-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da17a-122">See also</span></span>

- [<span data-ttu-id="da17a-123">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="da17a-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
