---
title: Utilisation de XML dans un DataSet
ms.date: 03/30/2017
ms.assetid: 35138159-e199-49ec-baf7-1ec6777e171e
ms.openlocfilehash: e133da727887271af3bc5330a5779df4af58a37e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201185"
---
# <a name="using-xml-in-a-dataset"></a><span data-ttu-id="45a0b-102">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="45a0b-102">Using XML in a DataSet</span></span>

<span data-ttu-id="45a0b-103">Avec ADO.NET, vous pouvez remplir un objet <xref:System.Data.DataSet> à partir d'un flux ou d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="45a0b-103">With ADO.NET you can fill a <xref:System.Data.DataSet> from an XML stream or document.</span></span> <span data-ttu-id="45a0b-104">Vous pouvez utiliser le flux ou le document XML pour fournir à l'objet <xref:System.Data.DataSet> soit des données, soit des informations de schéma ou les deux à la fois.</span><span class="sxs-lookup"><span data-stu-id="45a0b-104">You can use the XML stream or document to supply to the <xref:System.Data.DataSet> either data, schema information, or both.</span></span> <span data-ttu-id="45a0b-105">Les informations fournies à partir du flux ou du document XML peuvent être combinées aux données ou aux informations de schéma déjà présentes dans l'objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="45a0b-105">The information supplied from the XML stream or document can be combined with existing data or schema information already present in the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="45a0b-106">ADO.NET vous permet aussi de créer une représentation XML d'un objet <xref:System.Data.DataSet>, avec ou sans son schéma, afin de transporter l'objet <xref:System.Data.DataSet> sur HTTP en vue de son utilisation par une autre application ou une autre plateforme compatible XML.</span><span class="sxs-lookup"><span data-stu-id="45a0b-106">ADO.NET also allows you to create an XML representation of a <xref:System.Data.DataSet>, with or without its schema, in order to transport the <xref:System.Data.DataSet> across HTTP for use by another application or XML-enabled platform.</span></span> <span data-ttu-id="45a0b-107">Dans la représentation XML d'un objet <xref:System.Data.DataSet>, les données sont écrites en XML et le schéma, s'il est inclus inline dans la représentation, est écrit en langage XSD (XML Schema Definition).</span><span class="sxs-lookup"><span data-stu-id="45a0b-107">In an XML representation of a <xref:System.Data.DataSet>, the data is written in XML and the schema, if it is included inline in the representation, is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="45a0b-108">XML et XSD proposent un format pratique pour le transfert du contenu d'un objet <xref:System.Data.DataSet> vers et à partir des clients distants.</span><span class="sxs-lookup"><span data-stu-id="45a0b-108">XML and XML Schema provide a convenient format for transferring the contents of a <xref:System.Data.DataSet> to and from remote clients.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45a0b-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="45a0b-109">In This Section</span></span>  

 [<span data-ttu-id="45a0b-110">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="45a0b-110">DiffGrams</span></span>](diffgrams.md)  
 <span data-ttu-id="45a0b-111">Fournit des informations sur le DiffGram, format XML utilisé pour lire et écrire le contenu d'un objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="45a0b-111">Provides details on the DiffGram, an XML format used to read and write the contents of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="45a0b-112">Chargement d'un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="45a0b-112">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)  
 <span data-ttu-id="45a0b-113">Présente les différentes possibilités à envisager pour le chargement du contenu d'un objet <xref:System.Data.DataSet> à partir d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="45a0b-113">Discusses different options to consider when loading the contents of a <xref:System.Data.DataSet> from an XML document.</span></span>  
  
 [<span data-ttu-id="45a0b-114">Écriture du contenu d'un DataSet comme données XML</span><span class="sxs-lookup"><span data-stu-id="45a0b-114">Writing DataSet Contents as XML Data</span></span>](writing-dataset-contents-as-xml-data.md)  
 <span data-ttu-id="45a0b-115">Explique comment générer le contenu d'un objet <xref:System.Data.DataSet> sous forme de données XML et les différentes options de format XML que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="45a0b-115">Discusses how to generate the contents of a <xref:System.Data.DataSet> as XML data, and the different XML format options you can use.</span></span>  
  
 [<span data-ttu-id="45a0b-116">Chargement des informations de schéma de DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="45a0b-116">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)  
 <span data-ttu-id="45a0b-117">Présente les méthodes <xref:System.Data.DataSet> utilisées pour charger le schéma d'un objet <xref:System.Data.DataSet> à partir de XML.</span><span class="sxs-lookup"><span data-stu-id="45a0b-117">Discusses the <xref:System.Data.DataSet> methods used to load the schema of a <xref:System.Data.DataSet> from XML.</span></span>  
  
 [<span data-ttu-id="45a0b-118">Écriture des informations de schéma de DataSet comme XSD</span><span class="sxs-lookup"><span data-stu-id="45a0b-118">Writing DataSet Schema Information as XSD</span></span>](writing-dataset-schema-information-as-xsd.md)  
 <span data-ttu-id="45a0b-119">Présente les utilisations d'un schéma XML et explique comment en générer un à partir d'un objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="45a0b-119">Discusses the uses for an XML Schema and how to generate one from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="45a0b-120">Synchronisation DataSet et XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="45a0b-120">DataSet and XmlDataDocument Synchronization</span></span>](dataset-and-xmldatadocument-synchronization.md)  
 <span data-ttu-id="45a0b-121">Présente la possibilité fournie par le .NET Framework d’obtenir un accès synchrone aux vues relationnelle et hiérarchique d’un même groupe de données, et explique comment créer une relation synchrone entre un objet <xref:System.Data.DataSet> et un objet <xref:System.Xml.XmlDataDocument>.</span><span class="sxs-lookup"><span data-stu-id="45a0b-121">Discusses the capability available in the .NET Framework of synchronous access to both relational and hierarchical views of a single set of data, and shows how to create a synchronous relationship between a <xref:System.Data.DataSet> and an <xref:System.Xml.XmlDataDocument>.</span></span>  
  
 [<span data-ttu-id="45a0b-122">Imbrication de DataRelations</span><span class="sxs-lookup"><span data-stu-id="45a0b-122">Nesting DataRelations</span></span>](nesting-datarelations.md)  
 <span data-ttu-id="45a0b-123">Explique l'importance des objets <xref:System.Data.DataRelation> imbriqués lorsqu'il s'agit de représenter le contenu d'un objet <xref:System.Data.DataSet> sous forme de données XML, et décrit la façon de les créer.</span><span class="sxs-lookup"><span data-stu-id="45a0b-123">Discusses the importance of nested <xref:System.Data.DataRelation> objects when representing the contents of a <xref:System.Data.DataSet> as XML data, and describes how to create them.</span></span>  
  
 [<span data-ttu-id="45a0b-124">Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="45a0b-124">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="45a0b-125">Décrit la structure relationnelle, ou schéma, d'un objet <xref:System.Data.DataSet> créé à partir d'un schéma XML.</span><span class="sxs-lookup"><span data-stu-id="45a0b-125">Describes the relational structure, or schema, of a <xref:System.Data.DataSet> that is created from XML Schema.</span></span>  
  
 [<span data-ttu-id="45a0b-126">Déduction de la structure relationnelle des DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="45a0b-126">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)  
 <span data-ttu-id="45a0b-127">Décrit la structure relationnelle résultante, ou schéma, d'un objet <xref:System.Data.DataSet> créé par inférence à partir d'éléments XML.</span><span class="sxs-lookup"><span data-stu-id="45a0b-127">Describes the resulting relational structure, or schema, of a <xref:System.Data.DataSet> that is created when inferred from XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="45a0b-128">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="45a0b-128">Related Sections</span></span>  

 [<span data-ttu-id="45a0b-129">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="45a0b-129">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="45a0b-130">Décrit l'architecture et les composants d'ADO.NET ainsi que la façon de les utiliser pour accéder à des sources de données existantes et pour gérer des données d'application.</span><span class="sxs-lookup"><span data-stu-id="45a0b-130">Describes the ADO.NET architecture and components, and how to use them to access existing data sources as well as to manage application data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45a0b-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45a0b-131">See also</span></span>

- [<span data-ttu-id="45a0b-132">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="45a0b-132">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="45a0b-133">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="45a0b-133">ADO.NET Overview</span></span>](../ado-net-overview.md)
