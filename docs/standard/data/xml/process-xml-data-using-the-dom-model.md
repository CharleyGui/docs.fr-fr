---
title: Traitement de données XML à l'aide du modèle DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 56b6e9c7-ed82-4a65-a647-7be32c83bcc8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d34d22d8329f0bc26c1e29653137211bf300d324
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647819"
---
# <a name="process-xml-data-using-the-dom-model"></a><span data-ttu-id="8f824-102">Traitement de données XML à l'aide du modèle DOM</span><span class="sxs-lookup"><span data-stu-id="8f824-102">Process XML Data Using the DOM Model</span></span>
<span data-ttu-id="8f824-103">Le DOM (Document Object Model) XML traite les données XML comme un ensemble standard d'objets et permet de traiter les données XML en mémoire.</span><span class="sxs-lookup"><span data-stu-id="8f824-103">The XML Document Object Model (DOM) treats XML data as a standard set of objects and is used to process XML data in memory.</span></span> <span data-ttu-id="8f824-104">L'espace de noms `System.Xml` offre une représentation par programme de documents XML, de fragments, de nœuds ou de collections de nœuds.</span><span class="sxs-lookup"><span data-stu-id="8f824-104">The `System.Xml` namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets.</span></span> <span data-ttu-id="8f824-105">Il se base sur les recommandations du W3C (World Wide Web Consortium) sur les modèles objet de document (DOM), niveaux 1 et 2 (noyau).</span><span class="sxs-lookup"><span data-stu-id="8f824-105">It is based on the World Wide Web Consortium (W3C) DOM Level 1 Core and the DOM Level 2 Core recommendations.</span></span>  
  
 <span data-ttu-id="8f824-106">La classe <xref:System.Xml.XmlDocument> représente un document XML.</span><span class="sxs-lookup"><span data-stu-id="8f824-106">The <xref:System.Xml.XmlDocument> class represents an XML document.</span></span> <span data-ttu-id="8f824-107">Elle comprend des membres pour la récupération et la création de tous les autres objets XML.</span><span class="sxs-lookup"><span data-stu-id="8f824-107">It includes members for retrieving and creating all other XML objects.</span></span> <span data-ttu-id="8f824-108">L'objet <xref:System.Xml.XmlDocument> et les classes y afférentes permettent de construire des documents XML, de charger et d'accéder à des données, de modifier des données et de sauvegarder des modifications.</span><span class="sxs-lookup"><span data-stu-id="8f824-108">Using the <xref:System.Xml.XmlDocument>, and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8f824-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8f824-109">In This Section</span></span>  
  
- [<span data-ttu-id="8f824-110">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="8f824-110">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)  
  
- [<span data-ttu-id="8f824-111">Types de nœuds XML</span><span class="sxs-lookup"><span data-stu-id="8f824-111">Types of XML Nodes</span></span>](../../../../docs/standard/data/xml/types-of-xml-nodes.md)  
  
- [<span data-ttu-id="8f824-112">Hiérarchie du modèle DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="8f824-112">XML Document Object Model (DOM) Hierarchy</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md)  
  
- [<span data-ttu-id="8f824-113">Mappage de la hiérarchie d’objets à des données XML</span><span class="sxs-lookup"><span data-stu-id="8f824-113">Mapping the Object Hierarchy to XML Data</span></span>](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)  
  
- [<span data-ttu-id="8f824-114">Création d’un document XML</span><span class="sxs-lookup"><span data-stu-id="8f824-114">XML Document Creation</span></span>](../../../../docs/standard/data/xml/xml-document-creation.md)  
  
- [<span data-ttu-id="8f824-115">Lecture d’un document XML dans le DOM</span><span class="sxs-lookup"><span data-stu-id="8f824-115">Reading an XML Document into the DOM</span></span>](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md)  
  
- [<span data-ttu-id="8f824-116">Insertion de nœuds dans un document XML</span><span class="sxs-lookup"><span data-stu-id="8f824-116">Inserting Nodes into an XML Document</span></span>](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md)  
  
- [<span data-ttu-id="8f824-117">Suppression de nœuds, de contenu et de valeurs d’un document XML</span><span class="sxs-lookup"><span data-stu-id="8f824-117">Removing Nodes, Content, and Values from an XML Document</span></span>](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md)  
  
- [<span data-ttu-id="8f824-118">Modification de nœuds, de contenu et de valeurs dans un document XML</span><span class="sxs-lookup"><span data-stu-id="8f824-118">Modifying Nodes, Content, and Values in an XML Document</span></span>](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md)  
  
- [<span data-ttu-id="8f824-119">Validation d’un document XML dans le DOM</span><span class="sxs-lookup"><span data-stu-id="8f824-119">Validating an XML Document in the DOM</span></span>](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
  
- [<span data-ttu-id="8f824-120">Enregistrement et écriture d’un document</span><span class="sxs-lookup"><span data-stu-id="8f824-120">Saving and Writing a Document</span></span>](../../../../docs/standard/data/xml/saving-and-writing-a-document.md)  
  
- [<span data-ttu-id="8f824-121">Sélection de nœuds à l’aide de la navigation XPath</span><span class="sxs-lookup"><span data-stu-id="8f824-121">Select Nodes Using XPath Navigation</span></span>](../../../../docs/standard/data/xml/select-nodes-using-xpath-navigation.md)  
  
- [<span data-ttu-id="8f824-122">Résolution des ressources externes</span><span class="sxs-lookup"><span data-stu-id="8f824-122">Resolving External Resources</span></span>](../../../../docs/standard/data/xml/resolving-external-resources.md)  
  
- [<span data-ttu-id="8f824-123">Comparaison d’objets à l’aide de XmlNameTable</span><span class="sxs-lookup"><span data-stu-id="8f824-123">Object Comparison Using XmlNameTable</span></span>](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md)  
  
- [<span data-ttu-id="8f824-124">Collections de nœuds dans NamedNodeMap et NodeList</span><span class="sxs-lookup"><span data-stu-id="8f824-124">Node Collections in NamedNodeMaps and NodeLists</span></span>](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md)  
  
- [<span data-ttu-id="8f824-125">Mises à jour dynamiques de NodeList et NamedNodeMap</span><span class="sxs-lookup"><span data-stu-id="8f824-125">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>](../../../../docs/standard/data/xml/dynamic-updates-to-nodelists-and-namednodemaps.md)  
  
- [<span data-ttu-id="8f824-126">Prise en charge des espaces de noms dans le DOM</span><span class="sxs-lookup"><span data-stu-id="8f824-126">Namespace Support in the DOM</span></span>](../../../../docs/standard/data/xml/namespace-support-in-the-dom.md)  
  
- [<span data-ttu-id="8f824-127">Gestion d’événements dans un document XML à l’aide de XmlNodeChangedEventArgs</span><span class="sxs-lookup"><span data-stu-id="8f824-127">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)  
  
- [<span data-ttu-id="8f824-128">Extension du DOM</span><span class="sxs-lookup"><span data-stu-id="8f824-128">Extending the DOM</span></span>](../../../../docs/standard/data/xml/extending-the-dom.md)  
  
## <a name="related-sections"></a><span data-ttu-id="8f824-129">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="8f824-129">Related Sections</span></span>  
 [<span data-ttu-id="8f824-130">Traitement des données XML à l’aide du modèle de données XPath</span><span class="sxs-lookup"><span data-stu-id="8f824-130">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="8f824-131">Explique le traitement XML à l'aide de la classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="8f824-131">Discusses XML processing using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
