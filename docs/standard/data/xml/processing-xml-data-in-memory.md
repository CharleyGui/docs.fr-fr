---
title: Traitement de données XML en mémoire
ms.date: 03/30/2017
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
ms.openlocfilehash: 878e008f5c7c3a018389e8666263269162989812
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686915"
---
# <a name="processing-xml-data-in-memory"></a><span data-ttu-id="2043e-102">Traitement de données XML en mémoire</span><span class="sxs-lookup"><span data-stu-id="2043e-102">Processing XML Data In-Memory</span></span>

<span data-ttu-id="2043e-103">Microsoft .NET Framework comprend trois modèles pour le traitement des données XML : la classe <xref:System.Xml.XmlDocument>, la classe <xref:System.Xml.XPath.XPathDocument>, [LINQ to XML (C#)](../../linq/linq-xml-overview.md) et [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2043e-103">The Microsoft .NET Framework includes three models for processing XML data: the <xref:System.Xml.XmlDocument> class, the <xref:System.Xml.XPath.XPathDocument> class, and [LINQ to XML (C#)](../../linq/linq-xml-overview.md) and [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md).</span></span>  
  
 <span data-ttu-id="2043e-104">La classe <xref:System.Xml.XmlDocument> implémente les recommandations du W3C relatives aux modèles objet de document (DOM), niveaux 1 et 2 (noyau).</span><span class="sxs-lookup"><span data-stu-id="2043e-104">The <xref:System.Xml.XmlDocument> class implements the W3C document object model (DOM) level 1 core and the core DOM level 2 recommendations.</span></span> <span data-ttu-id="2043e-105">Le DOM est une représentation sous la forme d'une arborescence (cache) en mémoire d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="2043e-105">The DOM is an in-memory (cache) tree representation of an XML document.</span></span> <span data-ttu-id="2043e-106">L'objet <xref:System.Xml.XmlDocument> et les classes y afférentes permettent de construire des documents XML, de charger et d'accéder à des données, de modifier des données et d'enregistrer des modifications.</span><span class="sxs-lookup"><span data-stu-id="2043e-106">With the <xref:System.Xml.XmlDocument> and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
 <span data-ttu-id="2043e-107">La classe <xref:System.Xml.XPath.XPathDocument> est un magasin de données en mémoire en lecture seule basé sur le modèle de données XPath.</span><span class="sxs-lookup"><span data-stu-id="2043e-107">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory data store that is based on the XPath data model.</span></span> <span data-ttu-id="2043e-108">La classe <xref:System.Xml.XPath.XPathNavigator> propose plusieurs options de modification et fonctionnalités de navigation à l'aide d'un modèle de curseur entre des documents XML contenus dans la classe <xref:System.Xml.XPath.XPathDocument> en lecture seule ainsi que dans la classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="2043e-108">The <xref:System.Xml.XPath.XPathNavigator> class offers several editing options and navigation capabilities using a cursor model over XML documents contained in the read-only <xref:System.Xml.XPath.XPathDocument> class as well as the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="2043e-109">[LINQ to XML](../../linq/linq-xml-overview.md) est un modèle introduit dans .NET Framework version 3.5 pour le traitement des données XML.</span><span class="sxs-lookup"><span data-stu-id="2043e-109">[LINQ to XML](../../linq/linq-xml-overview.md) is a model introduced in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="2043e-110">Il s’agit d’un modèle en mémoire qui tire parti de [LINQ (Language-Integrated Query)](../../../csharp/programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="2043e-110">It's an in-memory model that leverages [Language-Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).</span></span> <span data-ttu-id="2043e-111">LINQ étend la syntaxe des langages C# et Visual Basic pour fournir de nouvelles capacités de requête.</span><span class="sxs-lookup"><span data-stu-id="2043e-111">LINQ extends the language syntax of C# and Visual Basic to provide new query capabilities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2043e-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="2043e-112">In This Section</span></span>  

 [<span data-ttu-id="2043e-113">Traitement de données XML à l'aide du modèle DOM</span><span class="sxs-lookup"><span data-stu-id="2043e-113">Process XML Data Using the DOM Model</span></span>](process-xml-data-using-the-dom-model.md)  
 <span data-ttu-id="2043e-114">Explique l'utilisation de l'objet <xref:System.Xml.XmlDocument> et des classes y afférentes pour le traitement de données XML.</span><span class="sxs-lookup"><span data-stu-id="2043e-114">Discusses using the <xref:System.Xml.XmlDocument>, and its related classes to process XML data.</span></span>  
  
 [<span data-ttu-id="2043e-115">Traitement des données XML à l'aide du modèle de données XPath</span><span class="sxs-lookup"><span data-stu-id="2043e-115">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="2043e-116">Explique l'utilisation des classes <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument> et <xref:System.Xml.XPath.XPathNavigator> pour le traitement de données XML.</span><span class="sxs-lookup"><span data-stu-id="2043e-116">Discusses using the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, and <xref:System.Xml.XPath.XPathNavigator> classes to process XML data.</span></span>  
  
 [<span data-ttu-id="2043e-117">Traitement des données XML à l'aide de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="2043e-117">Process XML Data Using LINQ to XML</span></span>](process-xml-data-using-linq-to-xml.md)  
 <span data-ttu-id="2043e-118">Fournit une brève vue d'ensemble de LINQ to XML et indique des liens vers la documentation LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="2043e-118">Provides a brief overview of LINQ to XML and provides links to the LINQ to XML documentation.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2043e-119">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="2043e-119">Related Sections</span></span>  

 [<span data-ttu-id="2043e-120">Documents et données XML</span><span class="sxs-lookup"><span data-stu-id="2043e-120">XML Documents and Data</span></span>](index.md)
