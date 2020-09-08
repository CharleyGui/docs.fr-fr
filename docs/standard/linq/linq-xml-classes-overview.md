---
title: Vue d’ensemble des classes LINQ to XML
description: Cet article fournit une liste des classes de LINQ to XML, avec les descriptions de chacune d’elles.
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 83258425b464d8547def5cce6a3e8da19ef21966
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553351"
---
# <a name="linq-to-xml-classes-overview"></a><span data-ttu-id="01371-103">Vue d’ensemble des classes LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="01371-103">LINQ to XML classes overview</span></span>

<span data-ttu-id="01371-104">Cet article fournit une liste des classes de LINQ to XML dans l' <xref:System.Xml.Linq> espace de noms, ainsi qu’une brève description de chacune d’elles.</span><span class="sxs-lookup"><span data-stu-id="01371-104">This article provides a list of the LINQ to XML classes in the <xref:System.Xml.Linq> namespace, and a short description of each.</span></span>

## <a name="linq-to-xml-classes"></a><span data-ttu-id="01371-105">Classes LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="01371-105">LINQ to XML classes</span></span>

### <a name="xattribute-class"></a><span data-ttu-id="01371-106">XAttribute (classe)</span><span class="sxs-lookup"><span data-stu-id="01371-106">XAttribute class</span></span>

<span data-ttu-id="01371-107"><xref:System.Xml.Linq.XAttribute> représente un attribut XML.</span><span class="sxs-lookup"><span data-stu-id="01371-107"><xref:System.Xml.Linq.XAttribute> represents an XML attribute.</span></span> <span data-ttu-id="01371-108">Pour obtenir des informations détaillées et des exemples, consultez [vue d’ensemble des classes XAttribute](xattribute-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="01371-108">For detailed information and examples, see [XAttribute class overview](xattribute-class-overview.md).</span></span>

### <a name="xcdata-class"></a><span data-ttu-id="01371-109">XCData, classe</span><span class="sxs-lookup"><span data-stu-id="01371-109">XCData class</span></span>

<span data-ttu-id="01371-110"><xref:System.Xml.Linq.XCData> représente un nœud de texte CDATA.</span><span class="sxs-lookup"><span data-stu-id="01371-110"><xref:System.Xml.Linq.XCData> represents a CDATA text node.</span></span>

### <a name="xcomment-class"></a><span data-ttu-id="01371-111">XComment, classe</span><span class="sxs-lookup"><span data-stu-id="01371-111">XComment class</span></span>

<span data-ttu-id="01371-112"><xref:System.Xml.Linq.XComment> représente un commentaire XML.</span><span class="sxs-lookup"><span data-stu-id="01371-112"><xref:System.Xml.Linq.XComment> represents an XML comment.</span></span>

### <a name="xcontainer-class"></a><span data-ttu-id="01371-113">Classe XContainer</span><span class="sxs-lookup"><span data-stu-id="01371-113">XContainer class</span></span>

<span data-ttu-id="01371-114"><xref:System.Xml.Linq.XContainer> est une classe de base abstraite pour tous les nœuds pouvant comporter des nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="01371-114"><xref:System.Xml.Linq.XContainer> is an abstract base class for all nodes that can have child nodes.</span></span> <span data-ttu-id="01371-115">Les classes suivantes dérivent de la classe <xref:System.Xml.Linq.XContainer> :</span><span class="sxs-lookup"><span data-stu-id="01371-115">The following classes derive from the <xref:System.Xml.Linq.XContainer> class:</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XDocument>

### <a name="xdeclaration-class"></a><span data-ttu-id="01371-116">XDeclaration, classe</span><span class="sxs-lookup"><span data-stu-id="01371-116">XDeclaration class</span></span>

<span data-ttu-id="01371-117"><xref:System.Xml.Linq.XDeclaration> représente une déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="01371-117"><xref:System.Xml.Linq.XDeclaration> represents an XML declaration.</span></span> <span data-ttu-id="01371-118">Une déclaration XML est utilisée pour déclarer la version XML et l'encodage d'un document.</span><span class="sxs-lookup"><span data-stu-id="01371-118">An XML declaration is used to declare the XML version and the encoding of a document.</span></span> <span data-ttu-id="01371-119">Une déclaration XML spécifie également si le document XML est autonome.</span><span class="sxs-lookup"><span data-stu-id="01371-119">In addition, an XML declaration specifies whether the XML document is stand-alone.</span></span> <span data-ttu-id="01371-120">Si un document est autonome, il n'existe aucune déclaration de marque externe, que ce soit dans un DTD externe ou dans une entité de paramètre externe référencée à partir du sous-ensemble interne.</span><span class="sxs-lookup"><span data-stu-id="01371-120">If a document is stand-alone, there are no external markup declarations, either in an external DTD, or in an external parameter entity referenced from the internal subset.</span></span>

### <a name="xdocument-class"></a><span data-ttu-id="01371-121">XDocument (classe)</span><span class="sxs-lookup"><span data-stu-id="01371-121">XDocument class</span></span>

<span data-ttu-id="01371-122"><xref:System.Xml.Linq.XDocument> représente un document XML.</span><span class="sxs-lookup"><span data-stu-id="01371-122"><xref:System.Xml.Linq.XDocument> represents an XML document.</span></span> <span data-ttu-id="01371-123">Pour obtenir des informations détaillées et des exemples, consultez [vue d’ensemble de la classe XDocument](xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="01371-123">For detailed information and examples, see [XDocument class overview](xdocument-class-overview.md).</span></span>

### <a name="xdocumenttype-class"></a><span data-ttu-id="01371-124">XDocumentType, classe</span><span class="sxs-lookup"><span data-stu-id="01371-124">XDocumentType class</span></span>

<span data-ttu-id="01371-125"><xref:System.Xml.Linq.XDocumentType> représente une définition DTD (Document Type Definition) XML.</span><span class="sxs-lookup"><span data-stu-id="01371-125"><xref:System.Xml.Linq.XDocumentType> represents an XML Document Type Definition (DTD).</span></span>

### <a name="xelement-class"></a><span data-ttu-id="01371-126">XElement (classe)</span><span class="sxs-lookup"><span data-stu-id="01371-126">XElement class</span></span>

<span data-ttu-id="01371-127"><xref:System.Xml.Linq.XElement> représente un élément XML.</span><span class="sxs-lookup"><span data-stu-id="01371-127"><xref:System.Xml.Linq.XElement> represents an XML element.</span></span> <span data-ttu-id="01371-128">Pour obtenir des informations détaillées et des exemples, consultez [vue d’ensemble de la classe XElement](xelement-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="01371-128">For detailed information and examples, see [XElement class overview](xelement-class-overview.md).</span></span>

### <a name="xname-class"></a><span data-ttu-id="01371-129">XName (classe)</span><span class="sxs-lookup"><span data-stu-id="01371-129">XName class</span></span>

<span data-ttu-id="01371-130"><xref:System.Xml.Linq.XName> représente des noms d'éléments (<xref:System.Xml.Linq.XElement>) et d'attributs (<xref:System.Xml.Linq.XAttribute>).</span><span class="sxs-lookup"><span data-stu-id="01371-130"><xref:System.Xml.Linq.XName> represents names of elements (<xref:System.Xml.Linq.XElement>) and attributes (<xref:System.Xml.Linq.XAttribute>).</span></span> <span data-ttu-id="01371-131">Pour obtenir des informations détaillées et des exemples, consultez [vue d’ensemble de la classe XDocument](xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="01371-131">For detailed information and examples, see [XDocument class overview](xdocument-class-overview.md).</span></span>

<span data-ttu-id="01371-132">LINQ to XML est conçu pour rendre les noms XML aussi simples que possible.</span><span class="sxs-lookup"><span data-stu-id="01371-132">LINQ to XML is designed to make XML names as straightforward as possible.</span></span> <span data-ttu-id="01371-133">En raison de leur complexité, les noms XML sont souvent considérés comme un article avancé dans XML.</span><span class="sxs-lookup"><span data-stu-id="01371-133">Due to their complexity, XML names are often considered to be an advanced article in XML.</span></span> <span data-ttu-id="01371-134">En fait, cette complexité provient non pas des espaces de noms, que les développeurs utilisent régulièrement dans la programmation, mais des préfixes d'espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="01371-134">Arguably, this complexity comes not from namespaces, which developers use regularly in programming, but from namespace prefixes.</span></span> <span data-ttu-id="01371-135">Les préfixes d'espaces de noms peuvent être utiles pour réduire le nombre de frappes au clavier nécessaires lors de la saisie de code XML ou pour améliorer la lisibilité du code XML.</span><span class="sxs-lookup"><span data-stu-id="01371-135">Namespace prefixes can be useful to reduce the keystrokes required when you input XML, or to make XML easier to read.</span></span> <span data-ttu-id="01371-136">Toutefois, les préfixes sont souvent simplement un raccourci pour l’utilisation de l’espace de noms XML complet, et ne sont pas nécessaires dans la plupart des cas.</span><span class="sxs-lookup"><span data-stu-id="01371-136">However, prefixes are often just a shortcut for using the full XML namespace, and aren't required in most cases.</span></span> <span data-ttu-id="01371-137">LINQ to XML simplifie les noms XML en résolvant tous les préfixes à leur espace de noms XML correspondant.</span><span class="sxs-lookup"><span data-stu-id="01371-137">LINQ to XML simplifies XML names by resolving all prefixes to their corresponding XML namespace.</span></span> <span data-ttu-id="01371-138">Les préfixes sont disponibles, s’ils sont requis, à l’aide de la <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="01371-138">Prefixes are available, if they're required, through the <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> method.</span></span>

<span data-ttu-id="01371-139">Il est possible, si nécessaire, de contrôler les préfixes d’espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="01371-139">it's possible, if necessary, to control namespace prefixes.</span></span> <span data-ttu-id="01371-140">Dans certains cas, si vous travaillez avec d’autres systèmes XML, tels que XSLT ou XAML, vous devez contrôler les préfixes d’espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="01371-140">In some circumstances, if you're working with other XML systems, such as XSLT or XAML, you need to control namespace prefixes.</span></span> <span data-ttu-id="01371-141">Par exemple, si vous avez une expression XPath qui utilise des préfixes d'espaces de noms et qui est incorporée dans une feuille de style XSLT, vous devez vous assurer que votre document XML est sérialisé avec des préfixes d'espaces de noms qui correspondent à ceux utilisés dans l'expression XPath.</span><span class="sxs-lookup"><span data-stu-id="01371-141">For example, if you have an XPath expression that uses namespace prefixes and is embedded in an XSLT stylesheet, you must make sure that your XML document is serialized with namespace prefixes that match those used in the XPath expression.</span></span>

### <a name="xnamespace-class"></a><span data-ttu-id="01371-142">XNamespace, classe</span><span class="sxs-lookup"><span data-stu-id="01371-142">XNamespace class</span></span>

<span data-ttu-id="01371-143"><xref:System.Xml.Linq.XNamespace> représente un espace de noms pour un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="01371-143"><xref:System.Xml.Linq.XNamespace> represents a namespace for an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="01371-144">Les espaces de noms sont un composant d'un objet <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="01371-144">Namespaces are a component of an <xref:System.Xml.Linq.XName>.</span></span>

### <a name="xnode-class"></a><span data-ttu-id="01371-145">XNode, classe</span><span class="sxs-lookup"><span data-stu-id="01371-145">XNode class</span></span>

<span data-ttu-id="01371-146"><xref:System.Xml.Linq.XNode> est une classe abstraite qui représente les nœuds d'une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="01371-146"><xref:System.Xml.Linq.XNode> is an abstract class that represents the nodes of an XML tree.</span></span> <span data-ttu-id="01371-147">Les classes suivantes dérivent de la classe <xref:System.Xml.Linq.XNode> :</span><span class="sxs-lookup"><span data-stu-id="01371-147">The following classes derive from the <xref:System.Xml.Linq.XNode> class:</span></span>

- <xref:System.Xml.Linq.XText>
- <xref:System.Xml.Linq.XContainer>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XDocumentType>

### <a name="xnodedocumentordercomparer-class"></a><span data-ttu-id="01371-148">XNodeDocumentOrderComparer, classe</span><span class="sxs-lookup"><span data-stu-id="01371-148">XNodeDocumentOrderComparer class</span></span>

<span data-ttu-id="01371-149"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> fournit la fonctionnalité permettant de comparer des nœuds pour ce qui est de l'ordre des documents.</span><span class="sxs-lookup"><span data-stu-id="01371-149"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> provides functionality to compare nodes for their document order.</span></span>

### <a name="xnodeequalitycomparer-class"></a><span data-ttu-id="01371-150">XNodeEqualityComparer, classe</span><span class="sxs-lookup"><span data-stu-id="01371-150">XNodeEqualityComparer class</span></span>

<span data-ttu-id="01371-151"><xref:System.Xml.Linq.XNodeEqualityComparer> fournit la fonctionnalité permettant de comparer des nœuds pour ce qui est de l'égalité des valeurs.</span><span class="sxs-lookup"><span data-stu-id="01371-151"><xref:System.Xml.Linq.XNodeEqualityComparer> provides functionality to compare nodes for value equality.</span></span>

### <a name="xobject-class"></a><span data-ttu-id="01371-152">XObject, classe</span><span class="sxs-lookup"><span data-stu-id="01371-152">XObject class</span></span>

<span data-ttu-id="01371-153"><xref:System.Xml.Linq.XObject> est une classe de base abstraite de <xref:System.Xml.Linq.XNode> et <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="01371-153"><xref:System.Xml.Linq.XObject> is an abstract base class of <xref:System.Xml.Linq.XNode> and <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="01371-154">Elle fournit des fonctionnalités d'annotation et d'événement.</span><span class="sxs-lookup"><span data-stu-id="01371-154">It provides annotation and event functionality.</span></span>

### <a name="xobjectchange-class"></a><span data-ttu-id="01371-155">XObjectChange, classe</span><span class="sxs-lookup"><span data-stu-id="01371-155">XObjectChange class</span></span>

<span data-ttu-id="01371-156"><xref:System.Xml.Linq.XObjectChange> spécifie le type d'événement lorsqu'un événement est déclenché pour un objet <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="01371-156"><xref:System.Xml.Linq.XObjectChange> specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>

### <a name="xobjectchangeeventargs-class"></a><span data-ttu-id="01371-157">XObjectChangeEventArgs, classe</span><span class="sxs-lookup"><span data-stu-id="01371-157">XObjectChangeEventArgs class</span></span>

<span data-ttu-id="01371-158"><xref:System.Xml.Linq.XObjectChangeEventArgs> fournit des données pour les événements <xref:System.Xml.Linq.XObject.Changing> et <xref:System.Xml.Linq.XObject.Changed>.</span><span class="sxs-lookup"><span data-stu-id="01371-158"><xref:System.Xml.Linq.XObjectChangeEventArgs> provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>

### <a name="xprocessinginstruction-class"></a><span data-ttu-id="01371-159">XProcessingInstruction, classe</span><span class="sxs-lookup"><span data-stu-id="01371-159">XProcessingInstruction class</span></span>

<span data-ttu-id="01371-160"><xref:System.Xml.Linq.XProcessingInstruction> représente une instruction de traitement XML.</span><span class="sxs-lookup"><span data-stu-id="01371-160"><xref:System.Xml.Linq.XProcessingInstruction> represents an XML processing instruction.</span></span> <span data-ttu-id="01371-161">Une instruction de traitement communique des informations à une application qui traite le code XML.</span><span class="sxs-lookup"><span data-stu-id="01371-161">A processing instruction communicates information to an application that processes the XML.</span></span>

### <a name="xtext-class"></a><span data-ttu-id="01371-162">XText, classe</span><span class="sxs-lookup"><span data-stu-id="01371-162">XText class</span></span>

<span data-ttu-id="01371-163"><xref:System.Xml.Linq.XText> représente un nœud de texte.</span><span class="sxs-lookup"><span data-stu-id="01371-163"><xref:System.Xml.Linq.XText> represents a text node.</span></span> <span data-ttu-id="01371-164">Dans la plupart des cas, vous n’êtes pas obligé d’utiliser cette classe.</span><span class="sxs-lookup"><span data-stu-id="01371-164">In most cases, you don't have to use this class.</span></span> <span data-ttu-id="01371-165">Cette classe est utilisée principalement pour du contenu mixte.</span><span class="sxs-lookup"><span data-stu-id="01371-165">This class is primarily used for mixed content.</span></span>
