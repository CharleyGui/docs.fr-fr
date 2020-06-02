---
title: Traitement de données XML à l'aide du modèle DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 56b6e9c7-ed82-4a65-a647-7be32c83bcc8
ms.openlocfilehash: 242554cc948ef16972ffd26d5464dae2727ed339
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290835"
---
# <a name="process-xml-data-using-the-dom-model"></a><span data-ttu-id="808d0-102">Traitement de données XML à l'aide du modèle DOM</span><span class="sxs-lookup"><span data-stu-id="808d0-102">Process XML Data Using the DOM Model</span></span>
<span data-ttu-id="808d0-103">Le DOM (Document Object Model) XML traite les données XML comme un ensemble standard d'objets et permet de traiter les données XML en mémoire.</span><span class="sxs-lookup"><span data-stu-id="808d0-103">The XML Document Object Model (DOM) treats XML data as a standard set of objects and is used to process XML data in memory.</span></span> <span data-ttu-id="808d0-104">L'espace de noms `System.Xml` offre une représentation par programme de documents XML, de fragments, de nœuds ou de collections de nœuds.</span><span class="sxs-lookup"><span data-stu-id="808d0-104">The `System.Xml` namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets.</span></span> <span data-ttu-id="808d0-105">Il se base sur les recommandations du W3C (World Wide Web Consortium) sur les modèles objet de document (DOM), niveaux 1 et 2 (noyau).</span><span class="sxs-lookup"><span data-stu-id="808d0-105">It is based on the World Wide Web Consortium (W3C) DOM Level 1 Core and the DOM Level 2 Core recommendations.</span></span>  
  
 <span data-ttu-id="808d0-106">La classe <xref:System.Xml.XmlDocument> représente un document XML.</span><span class="sxs-lookup"><span data-stu-id="808d0-106">The <xref:System.Xml.XmlDocument> class represents an XML document.</span></span> <span data-ttu-id="808d0-107">Elle comprend des membres pour la récupération et la création de tous les autres objets XML.</span><span class="sxs-lookup"><span data-stu-id="808d0-107">It includes members for retrieving and creating all other XML objects.</span></span> <span data-ttu-id="808d0-108">L'objet <xref:System.Xml.XmlDocument> et les classes y afférentes permettent de construire des documents XML, de charger et d'accéder à des données, de modifier des données et de sauvegarder des modifications.</span><span class="sxs-lookup"><span data-stu-id="808d0-108">Using the <xref:System.Xml.XmlDocument>, and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="808d0-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="808d0-109">In This Section</span></span>  
  
- [<span data-ttu-id="808d0-110">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="808d0-110">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)  
  
- [<span data-ttu-id="808d0-111">Types de nœuds XML</span><span class="sxs-lookup"><span data-stu-id="808d0-111">Types of XML Nodes</span></span>](types-of-xml-nodes.md)  
  
- [<span data-ttu-id="808d0-112">Hiérarchie du DOM XML</span><span class="sxs-lookup"><span data-stu-id="808d0-112">XML Document Object Model (DOM) Hierarchy</span></span>](xml-document-object-model-dom-hierarchy.md)  
  
- [<span data-ttu-id="808d0-113">Mappage de la hiérarchie d'objets à des données XML</span><span class="sxs-lookup"><span data-stu-id="808d0-113">Mapping the Object Hierarchy to XML Data</span></span>](mapping-the-object-hierarchy-to-xml-data.md)  
  
- [<span data-ttu-id="808d0-114">Création d'un document XML</span><span class="sxs-lookup"><span data-stu-id="808d0-114">XML Document Creation</span></span>](xml-document-creation.md)  
  
- [<span data-ttu-id="808d0-115">Lecture d'un document XML dans le DOM</span><span class="sxs-lookup"><span data-stu-id="808d0-115">Reading an XML Document into the DOM</span></span>](reading-an-xml-document-into-the-dom.md)  
  
- [<span data-ttu-id="808d0-116">Insertion de nœuds dans un document XML</span><span class="sxs-lookup"><span data-stu-id="808d0-116">Inserting Nodes into an XML Document</span></span>](inserting-nodes-into-an-xml-document.md)  
  
- [<span data-ttu-id="808d0-117">Suppression de nœuds, de contenu et de valeurs d'un document XML</span><span class="sxs-lookup"><span data-stu-id="808d0-117">Removing Nodes, Content, and Values from an XML Document</span></span>](removing-nodes-content-and-values-from-an-xml-document.md)  
  
- [<span data-ttu-id="808d0-118">Modification de nœuds, de contenu et de valeurs dans un document XML</span><span class="sxs-lookup"><span data-stu-id="808d0-118">Modifying Nodes, Content, and Values in an XML Document</span></span>](modifying-nodes-content-and-values-in-an-xml-document.md)  
  
- [<span data-ttu-id="808d0-119">Validation d'un document XML dans le DOM</span><span class="sxs-lookup"><span data-stu-id="808d0-119">Validating an XML Document in the DOM</span></span>](validating-an-xml-document-in-the-dom.md)  
  
- [<span data-ttu-id="808d0-120">Enregistrement et écriture d'un document</span><span class="sxs-lookup"><span data-stu-id="808d0-120">Saving and Writing a Document</span></span>](saving-and-writing-a-document.md)  
  
- [<span data-ttu-id="808d0-121">Sélection de nœuds à l'aide de la navigation XPath</span><span class="sxs-lookup"><span data-stu-id="808d0-121">Select Nodes Using XPath Navigation</span></span>](select-nodes-using-xpath-navigation.md)  
  
- [<span data-ttu-id="808d0-122">Résolution des ressources externes</span><span class="sxs-lookup"><span data-stu-id="808d0-122">Resolving External Resources</span></span>](resolving-external-resources.md)  
  
- [<span data-ttu-id="808d0-123">Comparaison d'objets à l'aide de XmlNameTable</span><span class="sxs-lookup"><span data-stu-id="808d0-123">Object Comparison Using XmlNameTable</span></span>](object-comparison-using-xmlnametable.md)  
  
- [<span data-ttu-id="808d0-124">Collections de nœuds dans NamedNodeMap et NodeList</span><span class="sxs-lookup"><span data-stu-id="808d0-124">Node Collections in NamedNodeMaps and NodeLists</span></span>](node-collections-in-namednodemaps-and-nodelists.md)  
  
- [<span data-ttu-id="808d0-125">Mises à jour dynamiques de NodeList et NamedNodeMap</span><span class="sxs-lookup"><span data-stu-id="808d0-125">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>](dynamic-updates-to-nodelists-and-namednodemaps.md)  
  
- [<span data-ttu-id="808d0-126">Prise en charge des espaces de noms dans le DOM</span><span class="sxs-lookup"><span data-stu-id="808d0-126">Namespace Support in the DOM</span></span>](namespace-support-in-the-dom.md)  
  
- [<span data-ttu-id="808d0-127">Gestion d'événements dans un document XML à l'aide de XmlNodeChangedEventArgs</span><span class="sxs-lookup"><span data-stu-id="808d0-127">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>](event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)  
  
- [<span data-ttu-id="808d0-128">Extension du DOM</span><span class="sxs-lookup"><span data-stu-id="808d0-128">Extending the DOM</span></span>](extending-the-dom.md)  
  
## <a name="related-sections"></a><span data-ttu-id="808d0-129">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="808d0-129">Related Sections</span></span>  
 [<span data-ttu-id="808d0-130">Traitement des données XML à l'aide du modèle de données XPath</span><span class="sxs-lookup"><span data-stu-id="808d0-130">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="808d0-131">Explique le traitement XML à l'aide de la classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="808d0-131">Discusses XML processing using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
